---
title: Twórz odporne na błędy usługi w chmurze. Obsługa przejściowych błędów w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Twórz odporne na błędy usługi w chmurze. Obsługa przejściowych błędów w chmurze
ms.date: 04/30/2018
ms.openlocfilehash: e6fae8140b55cb0308dca9f4b77e961501b41f8f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "73739397"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Twórz odporne usługi dla chmury: Zastąp błędy przejściowe w chmurze

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Odporność nie ma na uniknięcie niepowodzeń, ale akceptuje fakt, że wystąpią błędy, a następnie odpowiada na nie w taki sposób, aby uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.

Aplikacja jest gotowa do użycia w chmurze, co wymaga co najmniej modelu odporności opartej na oprogramowaniu, a nie modelu sprzętowego. Aplikacja w chmurze musi obejmować częściowe awarie, które wystąpiły. Zaprojektuj lub częściowo refaktoryzacji aplikacji w celu uzyskania odporności z oczekiwanymi częściowymi awariami. Powinna być zaprojektowana tak, aby poradzić sobie ze częściowo niepowodzeńmi, takimi jak przejściowe przestoje i węzły sieci lub awarie maszyn wirtualnych w chmurze. Nawet kontenery przenoszone do innego węzła w klastrze programu Orchestrator mogą spowodować sporadyczne krótkie błędy w aplikacji.

## <a name="handling-partial-failure"></a>Obsługa częściowych niepowodzeń

W aplikacji opartej na chmurze istnieje kiedykolwiek ryzyko częściowej awarii. Na przykład pojedyncze wystąpienie witryny sieci Web lub kontener może kończyć się niepowodzeniem lub może być niedostępna lub nie odpowiadać przez krótki czas. Lub może ulec awarii Pojedyncza maszyna wirtualna lub serwer.

Ponieważ klienci i usługi są oddzielnymi procesami, usługa może nie być w stanie reagować w odpowiednim czasie na żądanie klienta. Usługa może być przeciążona i reagować na żądania lub może być niedostępna przez krótki czas z powodu problemów z siecią.

Rozważmy na przykład monolityczną aplikację .NET, która uzyskuje dostęp do bazy danych w Azure SQL Database. Jeśli baza danych Azure SQL lub jakakolwiek inna usługa nie odpowiada przez krótki czas (baza danych SQL Azure może zostać przeniesiona do innego węzła lub serwera i nie będzie odpowiadać przez kilka sekund), gdy użytkownik spróbuje wykonać dowolną akcję, aplikacja może ulec awarii i w tym samym czasie.

Podobny scenariusz może wystąpić w aplikacji, która korzysta z usług HTTP. Sieć lub sama usługa może być niedostępna w chmurze w trakcie krótkiego, przejściowego błędu.

Odporna na błędy aplikacja, taka jak pokazana na rysunku 4-9, powinna implementować techniki takie jak "ponawianie prób z wykładniczą wycofywania", aby umożliwić aplikacji obsługę błędów przejściowych w zasobach. W aplikacjach należy również używać "wyłączników". Wyłącznik przerywa aplikacji próbuje uzyskać dostęp do zasobu, gdy jest to długotrwałe niepowodzenie. Korzystając z wyłącznika, aplikacja unika wywoływania odmowy usługi do siebie samej.

![Diagram częściowych błędów obsłużonych przez ponowną próbę przy użyciu wykładniczej wycofywania.](./media/build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud/retry-partial-failures.png)

**Rysunek 4-9.** Częściowe błędy obsłużone przez ponowną próbę przy użyciu wykładniczej wycofywania

Tych technik można używać zarówno w przypadku zasobów HTTP, jak i zasobów bazy danych. Na rysunku 4-9 aplikacja jest oparta na architekturze 3-warstwowej, więc te metody są wymagane na poziomie usług (HTTP) i na poziomie warstwy danych (TCP). W aplikacji monolitycznej, która korzysta tylko z jednej warstwy aplikacji oprócz bazy danych (bez dodatkowych usług lub mikrousług), obsługa błędów przejściowych na poziomie połączenia bazy danych może być wystarczająca. W tym scenariuszu wymagana jest tylko określona konfiguracja połączenia z bazą danych.

W przypadku wdrażania odpornego na błędy dostępu do bazy danych, w zależności od używanej wersji platformy .NET, może to być proste (na przykład [Entity Framework 6 lub nowsza](/ef/ef6/fundamentals/connection-resiliency/retry-logic)). Jest to tylko kwestia konfigurowania połączenia z bazą danych. Może być też konieczne użycie dodatkowych bibliotek, takich jak [blok obsługi błędów przejściowych](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (dla wcześniejszych wersji programu .NET), a nawet zaimplementowanie własnej biblioteki.

W przypadku wdrażania ponownych prób HTTP i wyłączników, zalecenie dotyczące platformy .NET polega na użyciu biblioteki [Polly](https://github.com/App-vNext/Polly) , która jest przeznaczona dla .NET Framework 4,0, .NET Framework 4,5 i .NET standard 1,1, która obejmuje obsługę platformy .NET Core.

Aby dowiedzieć się, jak zaimplementować strategie obsługi częściowych awarii w chmurze, zobacz następujące odwołania.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Implementowanie komunikacji odpornej na obsługę częściowej awarii**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework odporność połączenia i logika ponawiania prób (wersja 6 i nowsze)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Blok aplikacji do obsługi błędów przejściowych**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Biblioteka Polly do odpornej komunikacji HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Poprzedni](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[dalej](modernize-your-apps-with-monitoring-and-telemetry.md)
