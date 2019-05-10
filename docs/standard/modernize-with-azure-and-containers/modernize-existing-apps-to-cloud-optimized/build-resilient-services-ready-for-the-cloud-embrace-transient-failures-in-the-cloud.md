---
title: Kompilowanie odpornych usług gotowych do chmury. Obsługa przejściowych błędów w chmurze
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kompilowanie odpornych usług gotowych do chmury. Obsługa przejściowych błędów w chmurze
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 7af5e189ea930f9eac8aadab2ba1497f43f8d2b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614510"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Tworzenie odpornych usług gotowych do pracy w chmurze: Obsługa przejściowych błędów w chmurze

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Odporność to nie jest o unikanie błędów, ale akceptowanie fakt, że wystąpią błędy i następnie odpowiadać ich w sposób, który pozwala uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu pełnej funkcjonalności po wystąpieniu awarii.

Aplikacja jest gotowa dla chmury, gdy co najmniej implementuje model oparty na oprogramowaniu odporności, a nie modelu oparte na sprzęcie. Aplikacja w chmurze musi wykorzystywać częściowe błędy, które na pewno zostanie przeprowadzona. Projektujesz lub częściowo refaktoryzacji aplikacji umożliwiającego osiągnięcie odporności, z błędami częściowe oczekiwane. Powinny zostać tak zaprojektowane do radzenia sobie z błędami częściowych, takich jak awarie przejściowe problemy z siecią i węzłów lub awarii w chmurze maszyn wirtualnych. Nawet kontenerów jest przenoszony do innego węzła w klastrze usługi orchestrator może powodować sporadyczne błędy krótki w ramach aplikacji.

## <a name="handling-partial-failure"></a>Obsługa częściowych niepowodzeń

W aplikacji opartej na chmurze istnieje ryzyko wszechobecnym częściowych niepowodzeń. Na przykład wystąpienie jedną witrynę sieci Web lub kontener może się nie powieść lub może być niedostępny lub nie odpowiada przez krótki czas. Lub pojedynczej maszyny Wirtualnej lub serwera mógł ulec awarii.

Ponieważ klientów i usług są oddzielne procesy, usługi może nie móc reagować w odpowiednim czasie na żądanie klienta. Usługa może być przeciążona i wolniej odpowiadał na żądania lub może nie być dostępne przez krótki czas ze względu na problemy z siecią.

Na przykład należy wziąć pod uwagę monolitycznych .NET, który uzyskuje dostęp do bazy danych w usłudze Azure SQL Database. Jeśli baza danych Azure SQL lub dowolnej innej usługi innych firm nie odpowiada na krótki czas (Azure SQL database może być przeniesiony do innego węzła lub serwera i nie odpowiadać przez kilka sekund), gdy użytkownik próbuje wykonać żadnych działań, aplikacja może ulec awarii i Pokaż w wyjątku, w tym momencie.

Podobny scenariusz może wystąpić w aplikacji, która korzysta z usług HTTP. Sieci lub samej usługi mogą nie być dostępne w chmurze podczas krótkich, przejściowy błąd.

Odporna aplikacja jest podobny do przedstawionego w rysunek 4 – 9, powinny implementować technik, takich jak "ponawiają próby z wykorzystaniem wykładniczego wycofywania", aby umożliwić aplikacji do obsługi błędów przejściowych w zasobach. Należy również użyć "wyłączniki" w swoich aplikacjach. Wyłącznik zatrzymuje aplikację z próby uzyskania dostępu do zasobu, gdy jest ona rzeczywiście długotrwałą awarię. Przy użyciu wyłącznika, aplikacji pozwala uniknąć zdolnemu odmowa usługi dla samej siebie.

![Błędy częściowe obsługiwane przez ponawiają próby z wykorzystaniem wykładniczego wycofywania](./media/image9.png)

> **Rysunek 4 – 9.** Błędy częściowe obsługiwane przez ponawiają próby z wykorzystaniem wykładniczego wycofywania

Można użyć tych technik, zarówno w zasobach HTTP, jak i zasobów bazy danych. W rysunek 4 – 9, aplikacja opiera się na architekturze 3-warstwowej, więc należy tych technik na poziomie usług (HTTP) i na poziomie warstwy danych (TCP). W aplikacji monolitycznej, który używa tylko jednej aplikacji warstwy oprócz bazy danych (nie dodatkowych usług lub mikrousług) Obsługa błędów przejściowych na poziomie połączenia bazy danych może być wystarczająca. W tym scenariuszu szczególną konfigurację połączenia z bazą danych jest wymagana.

Podczas implementowania odporne na błędy wiadomości, do których dostęp do bazy danych, w zależności od wersji programu .NET, którego używasz, może być prosta (na przykład [przy użyciu platformy Entity Framework 6 lub nowszym](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Jest to kwestia konfigurowania połączenia z bazą danych). Lub może być konieczne użycie dodatkowych bibliotek, takich jak [blok aplikacji obsługi błędów przejściowych](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (w przypadku wcześniejszych wersji programu .NET), lub nawet implementować własne biblioteki.

Podczas implementowania ponownych prób HTTP i wyłączniki, zalecenie dla platformy .NET jest użycie [Polly](https://github.com/App-vNext/Polly) biblioteki, która jest przeznaczony dla .NET Framework 4.0, .NET Framework 4.5 i .NET Standard 1.1, które obsługuje platformy .NET Core.

Aby dowiedzieć się, jak zaimplementować strategie dotyczące obsługi częściowych niepowodzeń w chmurze, zobacz następujące odwołania.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Implementowanie odpornych na błędy komunikacji do obsługi częściowych niepowodzeń**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework odporności, a następnie spróbuj ponownie logika połączenia (w wersji 6 i nowsze)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Blok obsługi błędów przejściowych w aplikacji**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Biblioteki Polly odporne na błędy komunikacji HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[dalej](modernize-your-apps-with-monitoring-and-telemetry.md)
