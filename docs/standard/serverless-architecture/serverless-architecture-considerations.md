---
title: Zagadnienia dotyczące architektury bezserwerowej — aplikacje niekorzystające z serwera
description: Poznaj wyzwania związane z architektury aplikacji bez użycia serwera, z rozwiązaniem do zarządzania stanem i z magazynu trwałego do skalowania, rejestrowanie, śledzenie i Diagnostyka.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8b0b5241e6bae0bb4c77451e500b6c623c206fbf
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404958"
---
# <a name="serverless-architecture-considerations"></a>Zagadnienia dotyczące architektury bezserwerowej

Przyjęcie architektury bezserwerowej występują pewne wyzwania. W tej sekcji przedstawiono niektóre typowe zagadnienia, należy pamiętać o. Wszystkie te problemy mają rozwiązania. Podobnie jak w przypadku wszystkich rozwiązań architektury, należy tylko po dokładnego rozważenia zalet i wad decyzja o przejdź na architekturę bezserwerową. W zależności od potrzeb aplikacji mogą zdecydować, że implementacja bez użycia serwera nie jest właściwe rozwiązanie dla pewnych składników.

## <a name="managing-state"></a>Stan zarządzania

Funkcje bezserwerowe, podobnie jak w przypadku mikrousług, ogólnie rzecz biorąc, są bezstanowe domyślnie. Unikanie stanu umożliwia bez użycia serwera być efemeryczne skalowania w poziomie i aby zapewnić odporność, bez centralny punkt awarii. W niektórych przypadkach procesy biznesowe wymagają stanu. Jeśli dany proces wymaga stanu, masz dwie opcje. Przyjmij model innych niż bez użycia serwera lub interakcji z osobną usługą, który zawiera stan. Dodawanie stanu mogą skomplikować rozwiązania być trudniejsze do skali i utworzyć pojedynczy punkt awarii. Starannie rozważ, czy funkcja wymaga absolutnie stanu. Jeśli odpowiedź znajduje się "pozycja tak", należy określić, czy nadal warto wdrożyć ją z rozwiązaniami bezserwerowymi.

Istnieje kilka rozwiązań do przyjęcia stanu bez narażania zalety bez użycia serwera. Więcej popularnych rozwiązań, należą:

* Magazyn danych tymczasowych lub rozproszonej pamięci podręcznej, takich jak pamięci podręcznej Redis
* Stan Store w bazie danych, takich jak SQL lub bazy danych cosmos DB
* Obsługa stanu za pomocą aparatu przepływu pracy, takich jak funkcje trwałe

Mierzenie jest, należy pamiętać o potrzebę wszelkie zarządzanie stanem w procesach, które rozważasz do wdrożenia przy użyciu bezserwerowej.

## <a name="long-running-processes"></a>Długotrwałe procesy

Liczne zalety bez użycia serwera zależy od procesów jest tymczasowych. Krótki czas wykonywania ułatwiają dostawcę bez użycia serwera zwolnić zasoby, jak działa funkcje zakończenia i udziału na hostach. Większość dostawców rozwiązań w chmurze ograniczyć całkowity czas trwania funkcji można uruchomić na około 10 minut. Jeśli proces może trwać dłużej, warto rozważyć alternatywnej implementacji.

Istnieje kilka wyjątków i rozwiązań. Jedno rozwiązanie może być podziału procesu na mniejsze składniki, które indywidualnie zająć mniej czasu, aby uruchomić. Jeśli proces działa długo ze względu na zależności, należy również rozważyć asynchronicznego przepływu pracy przy użyciu rozwiązania, takiego jak funkcje trwałe. Trwałe funkcje wstrzymać i obsługi stanu procesu, gdy trwa oczekiwanie na zakończenie procesu zewnętrznego. Obsługa asynchronicznego skróci czas rzeczywisty proces jest uruchamiany.

## <a name="startup-time"></a>Czas uruchamiania

Jeden możliwy problem dotyczący z implementacjami bez użycia serwera to czas uruchamiania. Aby oszczędzać zasoby, wielu dostawców bez użycia serwera tworzenie infrastruktury "na żądanie." Po wyzwoleniu funkcję niewymagającą użycia serwera po upływie określonego czasu zasoby do obsługi funkcji może być konieczne można utworzyć ani ponownego uruchomienia. W niektórych sytuacjach zimnych startów może spowodować opóźnienia kilka sekund. Czas uruchamiania różni się w różnych dostawców i poziomów usług. Istnieje kilka metod czas uruchamiania adres jeśli ważne jest, aby zminimalizować do poprawnego działania aplikacji.

* Niektórzy dostawcy umożliwiają użytkownikom do zapłacenia za poziomy usług, które gwarantuje, że infrastruktura jest "zawsze włączone".
* Zaimplementować mechanizm utrzymywania aktywności (ping punktu końcowego, aby utrzymać ją "wznowione").
* Aranżacji, takich jak Kubernetes za pomocą podejścia konteneryzowanych — funkcja (host już działa, uruchamiając nowe wystąpienia jest bardzo szybkie).

## <a name="database-updates-and-migrations"></a>Aktualizacje bazy danych i migracji

Zaletą kod bez użycia serwera jest, że można zwolnić nowe funkcje bez konieczności ponownego wdrożenia całej aplikacji. Ta korzyść może stać się niekorzystne, jeśli zaangażowanych jest relacyjnej bazy danych. Zmiany schematy bazy danych są trudne do synchronizacji z aktualizacjami bez użycia serwera. Dodatkowe problemy są powodowane gdy coś pójdzie źle i zmiany muszą zostać wycofane. Integralność danych jest jednym z powodów będący najlepszym rozwiązaniem dla mikrousługi i funkcje nieużywające serwera sobie z własnymi danymi. Istnieje możliwość wdrożyć zmiany jako pojedyncza jednostka mocy obliczeniowej i danych. Rzeczywistość jest wyposażone w wiele systemów starszych dużej bazy danych zaplecza, które muszą być zgodne z architekturą bezserwerową.

Popularne podejście do rozwiązywania schematu przechowywania wersji jest nigdy nie modyfikują istniejących właściwości i kolumn, ale zamiast tego Dodaj nowe informacje. Na przykład, należy wziąć pod uwagę zmiany można przenieść z wartością logiczną "ukończone" flagi dla listy zadań do wykonania "Data ukończenia". Zamiast usuwania starego pola, spowoduje zmianę w bazie danych:

1. Dodaj pole Nowy "Data ukończone".
1. Przekształć "ukończone" pola logicznych obliczona funkcja, która ocenia, czy data ukończenia jest po bieżącej dacie.
1. Dodawanie wyzwalacza do zestawu Data ukończenia na bieżącą datę, kiedy ukończone logiczna jest ustawiona na wartość true.

Sekwencji zmian zapewnia, że starszego kodu w dalszym ciągu działanie "w jakim jest" w trakcie nowsze funkcje niewymagające użycia serwera korzystać z zalet nowego pola.

Aby uzyskać więcej informacji o danych w architektur bez użycia serwera, zobacz [problemy i rozwiązania dotyczące rozproszonego zarządzania danymi](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Skalowanie

To powszechne nieporozumienie bez użycia serwera oznacza "nie serwera." W rzeczywistości jest "mniej server". Fakt, że jest infrastruktury zapasowy ważne jest, aby zrozumieć, jeśli chodzi o skalowania. Najbardziej bezserwerowej platformy zawierają zestaw formantów do obsługi, jak powinny być skalowane infrastruktury, gdy przyrost zdarzeń. Można wybierać spośród wielu opcji, ale strategii mogą się różnić w zależności od funkcji. Ponadto funkcje są zazwyczaj uruchamiane w obszarze hostem powiązane, tak, aby funkcje na tym samym hoście mają te same opcje skalowania. Dlatego jest niezbędne do organizowania i ułożeniu dla niego strategii jakie funkcje są obsługiwane razem na podstawie skali wymagań.

Reguły często określają sposób skalowania w górę (zwiększyć zasoby hosta) i skalowalnego w poziomie (zwiększenie liczby wystąpień hosta) na podstawie różnych parametrów. Wyzwalacze dla skale może obejmować harmonogramu, żądań, użycie procesora CPU i użycie pamięci. Często wyższej wydajności są obciążone kosztami większa. Mniej kosztowne, na podstawie użycia metod nie mogą skalować, szybko gdy liczba żądań nagle wraz ze wzrostem. Istnieje zależność między płacenia się frontonu "koszt ubezpieczenia" i płacić wyłącznie "jak Przejdź do" i zagrażających wolniejsze odpowiedzi z powodu nagły wzrost zapotrzebowania.

## <a name="monitoring-tracing-and-logging"></a>Monitorowanie i śledzenie i rejestrowanie

Często zapomina aspektów DevOps jest monitorowanie aplikacji po jej wdrożeniu. Należy mieć strategii do monitorowania funkcje niewymagające użycia serwera. Największe wyzwanie jest często korelacji, rozpoznawaniu, gdy użytkownik wywołuje wiele funkcji w ramach tej samej interakcji. Najbardziej bezserwerowej platformy zezwala na konsoli, rejestrowanie, które mogą być importowane do narzędzi innych firm. Dostępne są również opcje Automatyzacja zbierania danych telemetrycznych, generowanie i śledzić identyfikatorów korelacji i monitorować konkretne akcje, aby uzyskać szczegółowe informacje. System Azure oferuje zaawansowane [usługi Application Insights platformy](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) monitorowania i analizy.

## <a name="inter-service-dependencies"></a>Komunikacja między usługami zależności

Architektura bezserwerowa może obejmować funkcje, które zależą od innych funkcji. W rzeczywistości nie jest niczym niezwykłym w architektura bezserwerowa mieć wiele usług, które wywołują się nawzajem jako część interakcji lub transakcji rozproszonej. Aby uniknąć silne sprzężenia, zalecane jest, że usługi nie odwołują się do siebie nawzajem bezpośrednio. Gdy punkt końcowy usługi wymaga wprowadzenia zmian, bezpośrednie odwołania może spowodować głównych refaktoryzacji. Sugerowane rozwiązanie jest zapewnienie mechanizmu odnajdywania usługi, takie jak rejestru, który zapewnia odpowiedni punkt końcowy dla typu żądania. Innym rozwiązaniem jest korzystanie z usług obsługi wiadomości, takich jak kolejki i tematy do komunikacji między usługami.

## <a name="managing-failure-and-providing-resiliency"></a>Zarządzanie awarii i zapewnianie odporności

Należy również wziąć pod uwagę *wzorzec wyłącznika*: Jeśli z jakiegoś powodu usługa zakończy się niepowodzeniem, nie jest zalecane wielokrotne wywoływanie tej usługi. Zamiast tego nosi nazwę alternatywną usługę lub zwrócił komunikat, dopóki nie zostanie ponownie nawiązane kondycję usług zależnych. Architektura bezserwerowa należy wziąć pod uwagę strategii rozwiązywania i zarządzania nimi zależności komunikacja między usługami.

Aby kontynuować wzorzec wyłącznika, usługi, należy zapewnić odporność na uszkodzenia i odporny na błędy. Odporność na uszkodzenia odwołuje się do możliwości aplikacji, aby kontynuować, nawet po nieoczekiwanych wyjątków lub występują nieprawidłowe stany. Odporność na uszkodzenia jest zazwyczaj funkcją sam kod i jak zapisane na obsługę wyjątków. Odporność odnosi się do sposobu stanie aplikacji znajduje się na odzyskiwanie po awarii. Odporność często jest zarządzane przez platformę bez użycia serwera. Platforma powinno być możliwe nad ułatwieniem nowe wystąpienie funkcję niewymagającą użycia serwera, gdy istniejący nie powiodło się. Platforma powinny być również inteligentnego zatrzymać uruchamiając nowe wystąpienia, gdy każde nowe wystąpienie nie powiedzie się.

Aby uzyskać więcej informacji, zobacz [Implementowanie wzorca wyłącznika](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Przechowywanie wersji i zielony i niebieski wdrożeń

Główną zaletą bez użycia serwera jest możliwość uaktualnienia określoną funkcję bez konieczności ponownego wdrożenia całej aplikacji. Dotyczącymi uaktualniania zakończy się powodzeniem funkcje muszą być poddany kontroli wersji, tak, aby je podczas wywoływania usługi są kierowane do poprawnej wersji kodu. Ważne jest również strategię wdrażania nowych wersji. Typowym podejściem jest użycie "zielony i niebieski wdrożeń." Zielonego wdrożenia jest bieżącą funkcję. Nowa wersja "niebieski" jest wdrażana w środowisku produkcyjnym i przetestowany. Podczas testowania przebiegów, wersji zielonego i niebieskiego zostały zamienione, nowa wersja jest dostępna na żywo. Jeśli zostaną napotkane problemy, może być zamienione ponownie. Obsługa wersjonowania i wdrażania zielony i niebieski wymaga kombinacji tworzenia funkcji w celu uwzględnienia zmiany wersji i pracy z platformą bez użycia serwera do obsługi wdrożenia. Jedno z możliwych podejść jest użycie serwerów proxy, które są opisane w [./azure-functions.md](Azure serverless platform) rozdziale.

>[!div class="step-by-step"]
[Poprzednie](serverless-architecture.md)
[dalej](serverless-design-examples.md)