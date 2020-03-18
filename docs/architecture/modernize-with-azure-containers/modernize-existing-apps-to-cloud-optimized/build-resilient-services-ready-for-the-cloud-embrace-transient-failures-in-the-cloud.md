---
title: Twórz odporne usługi gotowe do pracy w chmurze. Obsługa przejściowych błędów w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Twórz odporne usługi gotowe do pracy w chmurze. Obsługa przejściowych błędów w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711245"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Kompilowanie odpornych usług gotowych do użycia w chmurze: obsługa przejściowych błędów w chmurze

Odporność jest możliwość odzyskania z awarii i nadal działać. Odporność nie polega na unikaniu błędów, ale akceptowaniu faktu, że wystąpią błędy, a następnie reagowaniu na nie w sposób, który pozwala uniknąć przestojów lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonującego po awarii.

Aplikacja jest gotowa do chmury, gdy co najmniej implementuje oparty na oprogramowaniu model odporności, a nie model oparty na sprzęcie. Aplikacja w chmurze musi obejmować częściowe błędy, które z pewnością wystąpią. Zaprojektuj lub częściowo refaktoryzuj aplikację, aby osiągnąć odporność z oczekiwanymi częściowymi awariami. Powinien być zaprojektowany do radzenia sobie z częściowymi awariami, takimi jak przejściowe awarie sieci i węzły lub maszyny wirtualne ulegające awarii w chmurze. Nawet kontenery są przenoszone do innego węzła w klastrze koordynatora może spowodować sporadyczne krótkie błędy w aplikacji.

## <a name="handling-partial-failure"></a>Obsługa częściowych niepowodzeń

W aplikacji opartej na chmurze istnieje stale obecne ryzyko częściowej awarii. Na przykład wystąpienie pojedynczej witryny lub kontener może zakończyć się niepowodzeniem lub może być niedostępne lub nie odpowiada ć przez krótki czas. Lub pojedyncza maszyna wirtualna lub serwer może ulec awarii.

Ponieważ klienci i usługi są oddzielnymi procesami, usługa może nie być w stanie odpowiedzieć w odpowiednim czasie na żądanie klienta. Usługa może być przeciążona i reagować powoli na żądania lub może nie być dostępna przez krótki czas z powodu problemów z siecią.

Rozważmy na przykład monolityczną aplikację .NET, która uzyskuje dostęp do bazy danych w usłudze Azure SQL Database. Jeśli baza danych SQL platformy Azure lub jakakolwiek inna usługa innej firmy nie odpowiada przez krótki czas (baza danych SQL platformy Azure może zostać przeniesiona do innego węzła lub serwera i nie odpowiada przez kilka sekund), gdy użytkownik próbuje wykonać dowolną akcję, aplikacja może ulec awarii i w tym samym momencie.

Podobny scenariusz może wystąpić w aplikacji, która korzysta z usług HTTP. Sieć lub sama usługa może nie być dostępna w chmurze podczas krótkiego, przejściowego błędu.

Odporne aplikacji, takich jak pokazano na rysunku 4-9 należy zaimplementować techniki, takie jak "ponownych prób z wykładniczego wycofywania", aby dać aplikacji możliwość obsługi błędów przejściowych w zasobach. Należy również użyć "wyłączniki" w aplikacjach. Wyłącznik zatrzymuje aplikację przed próbą uzyskania dostępu do zasobu, gdy jest to faktycznie długoterminowej awarii. Za pomocą wyłącznika, aplikacja unika prowokowania odmowy usługi do siebie.

![Diagram częściowych błędów obsługiwane przez ponownych prób z wykładniczego wycofywania.](./media/retry-partial-failures.png)

**Rysunek 4-9.** Częściowe błędy obsługiwane przez ponownych prób z wykładniczym wycofywaniem

Tych technik można używać zarówno w zasobach HTTP, jak i w zasobach bazy danych. Na rysunku 4-9 aplikacja jest oparta na architekturze 3-warstwowej, więc potrzebne są te techniki na poziomie usług (HTTP) i na poziomie warstwy danych (TCP). W aplikacji monolityczne, która używa tylko jednej warstwy aplikacji oprócz bazy danych (bez dodatkowych usług lub mikrousług), obsługa błędów przejściowych na poziomie połączenia bazy danych może wystarczyć. W tym scenariuszu wymagana jest tylko określona konfiguracja połączenia z bazą danych.

Podczas implementowania elastycznej komunikacji, która uzyskuje dostęp do bazy danych, w zależności od używanej wersji .NET, może być proste (na przykład [z entity framework 6 lub nowszej](/ef/ef6/fundamentals/connection-resiliency/retry-logic). To tylko kwestia skonfigurowania połączenia z bazą danych). Lub może być konieczne użycie dodatkowych bibliotek, takich jak [przemijający blok aplikacji obsługi błędów](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (dla wcześniejszych wersji .NET), a nawet zaimplementować własną bibliotekę.

Podczas implementowania ponownych prób http i wyłączników, zalecenie dla .NET jest użycie biblioteki [Polly,](https://github.com/App-vNext/Polly) która jest przeznaczona dla .NET Framework 4.0, .NET Framework 4.5 i .NET Standard 1.1, który zawiera obsługę .NET Core.

Aby dowiedzieć się, jak zaimplementować strategie obsługi błędów częściowych w chmurze, zobacz następujące odwołania.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wdrażanie odpornej komunikacji do obsługi częściowej awarii**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Odporność na połączenie struktury jednostek i logika ponawiania prób (wersja 6 i nowsze wersje)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Blok aplikacji do obsługi błędów przejściowych**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Biblioteka Polly dla odpornej komunikacji HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[następny](modernize-your-apps-with-monitoring-and-telemetry.md)
