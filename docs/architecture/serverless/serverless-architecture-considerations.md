---
title: Zagadnienia dotyczące architektury bezserwerowej — aplikacje bezserwerowe
description: Poznaj wyzwania związane z projektowaniem aplikacji bezserwerowych, od zarządzania stanem i trwałego magazynu po skalowanie, rejestrowanie, śledzenie i diagnostykę.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522427"
---
# <a name="serverless-architecture-considerations"></a>Zagadnienia dotyczące architektury bezserwerowej

Przyjęcie architektury bezserwerowej wiąże się z pewnymi wyzwaniami. W tej sekcji omówiono niektóre z bardziej typowych zagadnień, o które należy pamiętać. Wszystkie te wyzwania mają rozwiązania. Podobnie jak w przypadku wszystkich wyborów architektury, decyzja, aby przejść bez serwerów powinny być podejmowane dopiero po dokładnym rozważeniu plusy i minusy. W zależności od potrzeb aplikacji może zdecydować, że implementacja bezserwerowa nie jest właściwym rozwiązaniem dla niektórych składników.

## <a name="managing-state"></a>Zarządzanie stanem

Funkcje bezserwerowe, podobnie jak w ogóle w mikrousługach, są domyślnie bezstanowe. Unikanie stanu umożliwia bezserwerowe być efemeryczny, skalować w sposób skalowany w sposób skalowany i zapewnić odporność bez centralnego punktu awarii. W pewnych okolicznościach procesy biznesowe wymagają stanu. Jeśli proces wymaga stanu, masz dwie opcje. Można przyjąć model inny niż bezserwerowy lub wchodzić w interakcje z oddzielną usługą, która zapewnia stan. Dodawanie stanu może skomplikować rozwiązanie i utrudnić skalowanie i potencjalnie utworzyć pojedynczy punkt awarii. Dokładnie zastanów się, czy twoja funkcja absolutnie wymaga stanu. Jeśli odpowiedź brzmi "tak", należy określić, czy nadal warto zaimplementować ją bez serwerów.

Istnieje kilka rozwiązań do przyjęcia stanu bez naruszania korzyści z bezserwerowych. Niektóre z bardziej popularnych rozwiązań obejmują:

- Korzystanie z tymczasowego magazynu danych lub rozproszonej pamięci podręcznej, takiej jak Redis
- Stan przechowywania w bazie danych, takiej jak SQL lub CosmosDB
- Stan obsługi za pomocą aparatu przepływu pracy, takiego jak trwałe funkcje

Najważniejsze jest to, że należy zdawać sobie sprawę z potrzeby zarządzania stanem w ramach procesów, które rozważasz do wdrożenia z bezserwerowych.

## <a name="long-running-processes"></a>Długotrwałe procesy

Wiele korzyści z bezserwerowych polegać na procesach jest ulotne. Krótkie czasy uruchamiania ułatwiają dostawcy bezserwerowe zwalnianie zasobów w miarę końców funkcji i udostępnianie funkcji między hostami. Większość dostawców chmury ogranicza całkowity czas działania funkcji do około 10 minut. Jeśli proces może potrwać dłużej, można rozważyć alternatywną implementację.

Istnieje kilka wyjątków i rozwiązań. Jednym z rozwiązań może być podzielić proces na mniejsze składniki, które indywidualnie zajmują mniej czasu. Jeśli proces działa długo z powodu zależności, można również rozważyć asynchroniczny przepływ pracy przy użyciu rozwiązania, takich jak trwałe funkcje. Trwałe funkcje wstrzymywają i utrzymują stan procesu, gdy oczekuje na zakończenie procesu zewnętrznego. Obsługa asynchroniczna skraca czas rzeczywistego procesu.

## <a name="startup-time"></a>Czas uruchamiania

Jednym z potencjalnych problemów z implementacjami bezserwerowych jest czas uruchamiania. Aby oszczędzać zasoby, wielu dostawców bezserwerowych tworzy infrastrukturę "na żądanie". Gdy funkcja bezserwerowa jest wyzwalana po pewnym czasie, zasoby do obsługi funkcji może być konieczne utworzenie lub ponowne uruchomienie. W niektórych sytuacjach zimne starty mogą powodować kilkusekundowe opóźnienia. Czas uruchamiania różni się w zależności od dostawcy i poziomów usług. Istnieje kilka metod adres czasu uruchamiania, jeśli jest to ważne, aby zminimalizować dla powodzenia aplikacji.

- Niektórzy dostawcy umożliwiają użytkownikom płacenie za poziomy usług, które gwarantują, że infrastruktura jest "zawsze na".
- Zaimplementuj mechanizm keep-alive (ping punktu końcowego, aby utrzymać go "obudzić").
- Użyj aranżacji, takich jak Kubernetes z podejściem funkcji konteneryzowanych (host jest już uruchomiony, więc przędzenia nowych wystąpień jest bardzo szybki).

## <a name="database-updates-and-migrations"></a>Aktualizacje i migracje bazy danych

Zaletą kodu bezserwerowego jest to, że można zwolnić nowe funkcje bez konieczności ponownego wdrażania całej aplikacji. Ta zaleta może stać się wadą, gdy istnieje relacyjna baza danych zaangażowanych. Zmiany w schemach bazy danych są trudne do zsynchronizowania z aktualizacjami bezserwerowych. Dodatkowe wyzwania pojawiają się, gdy coś pójdzie nie tak, a zmiany muszą zostać wycofane. Integralność danych jest jednym z powodów, że najlepszym rozwiązaniem dla mikrousług i funkcji bezserwerowych jest, że są one właścicielem własnych danych. Istnieje możliwość wdrożenia zmian jako pojedynczej jednostki obliczeń i danych. W rzeczywistości wiele starszych systemów posiada dużą bazę danych zaplecza, która musi zostać uzgodniona z architekturą bezserwerową.

Popularnym podejściem do rozwiązywania wersji schematu jest nigdy nie modyfikować istniejących właściwości i kolumn, ale zamiast tego dodać nowe informacje. Rozważmy na przykład zmianę, aby przejść z flagi "ukończone" logicznej dla listy dozrobienia do "daty ukończonej". Zamiast usuwać stare pole, zmiana bazy danych:

1. Dodaj nowe pole "data ukończona".
1. Przekształć "ukończone" pole logiczne w funkcję obliczaną, która ocenia, czy ukończona data jest po bieżącej dacie.
1. Dodaj wyzwalacz, aby ustawić ukończoną datę na bieżącą datę, gdy ukończony wartość logiczna jest ustawiona na true.

Sekwencja zmian gwarantuje, że starszy kod będzie nadal działał "tak jak jest", podczas gdy nowsze funkcje bezserwerowe mogą korzystać z nowego pola.

Aby uzyskać więcej informacji na temat danych w architekturach bezserwerowych, zobacz [Wyzwania i rozwiązania dotyczące zarządzania danymi rozproszonymi.](../microservices/architect-microservice-container-applications/distributed-data-management.md)

## <a name="scaling"></a>Skalowanie

Jest to powszechne błędne przekonanie, że bezserwerowe oznacza "nie ma serwera". W rzeczywistości jest to "mniej serwera". Fakt, że istnieje infrastruktura podkładowa jest ważne, aby zrozumieć, jeśli chodzi o skalowanie. Większość platform bezserwerowych zapewniają zestaw formantów do obsługi, jak infrastruktura powinna skalować po zwiększeniu gęstości zdarzeń. Możesz wybierać spośród wielu opcji, ale twoja strategia może się różnić w zależności od funkcji. Ponadto funkcje są zazwyczaj uruchamiane w ramach powiązanego hosta, dzięki czemu funkcje na tym samym hoście mają te same opcje skalowania. W związku z tym konieczne jest zorganizowanie i strategize, które funkcje są hostowane razem na podstawie wymagań skali.

Reguły często określają sposób skalowania w górę (zwiększenie zasobów hosta) i skalowanie w górę (zwiększenie liczby wystąpień hosta) na podstawie różnych parametrów. Wyzwalacze dla skali mogą obejmować harmonogram, szybkość żądań, wykorzystanie procesora CPU i użycie pamięci. Wyższa wydajność często wiąże się z większymi kosztami. Tańsze podejścia oparte na konsumpcji mogą nie być skalowane tak szybko, gdy wskaźnik żądań nagle wzrośnie. Istnieje kompromis między płaceniem z góry "kosztów ubezpieczenia" w porównaniu do płacenia ściśle "jak idziesz" i ryzykując wolniejsze odpowiedzi z powodu nagłego wzrostu popytu.

## <a name="monitoring-tracing-and-logging"></a>Monitorowanie, śledzenie i rejestrowanie

Często pomijany aspekt DevOps jest monitorowanie aplikacji po wdrożeniu. Ważne jest, aby mieć strategię monitorowania funkcji bezserwerowych. Największym wyzwaniem jest często korelacji lub rozpoznawania, gdy użytkownik wywołuje wiele funkcji w ramach tej samej interakcji. Większość platform bezserwerowych umożliwia rejestrowanie konsoli, które można zaimportować do narzędzi innych firm. Istnieją również opcje automatyzacji zbierania danych telemetrycznych, generowania i śledzenia identyfikatorów korelacji oraz monitorowania określonych akcji w celu zapewnienia szczegółowych informacji. Platforma Azure udostępnia zaawansowaną [platformę Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) do monitorowania i analizy.

## <a name="inter-service-dependencies"></a>Zależności między służbami

Architektura bezserwerowa może zawierać funkcje, które opierają się na innych funkcjach. W rzeczywistości nie jest rzadkością w architekturze bezserwerowej, aby wiele usług wywoływać siebie w ramach interakcji lub transakcji rozproszonych. Aby uniknąć silnego sprzężenia, zaleca się, aby usługi nie odwoływały się bezpośrednio do siebie. Gdy punkt końcowy dla usługi musi ulec zmianie, bezpośrednie odwołania może spowodować poważne refaktoryzacji. Sugerowanym rozwiązaniem jest zapewnienie mechanizmu odnajdywania usług, takiego jak rejestr, który zapewnia odpowiedni punkt końcowy dla typu żądania. Innym rozwiązaniem jest wykorzystanie usług obsługi wiadomości, takich jak kolejki lub tematy do komunikacji między usługami.

## <a name="managing-failure-and-providing-resiliency"></a>Zarządzanie awariami i zapewnianie odporności

Ważne jest również, aby wziąć pod uwagę *wzorzec wyłącznika*: Jeśli z jakiegoś powodu usługa nadal się nie powiedzie, nie zaleca się wielokrotnego wywoływania tej usługi. Zamiast tego usługa alternatywna jest wywoływana lub komunikat zwracany, dopóki kondycja usługi zależnej zostanie ponownie ustanowiona. Architektura bezserwerowa musi uwzględniać strategię rozwiązywania zależności między służbami i zarządzania nimi.

Aby kontynuować wzorzec wyłącznika, usługi muszą być odporne na uszkodzenia i odporne. Odporność na uszkodzenia odnosi się do możliwości kontynuowania działania aplikacji nawet po napotkaniu nieoczekiwanych wyjątków lub nieprawidłowych stanów. Odporność na uszkodzenia jest zazwyczaj funkcją samego kodu i jak jest zapisywany do obsługi wyjątków. Odporność odnosi się do tego, jak aplikacja jest w stanie odzyskać po awarii. Odporność jest często zarządzana przez platformę bezserwerową. Platforma powinna być w stanie rozkręcić nowe wystąpienie funkcji bezserwerowej, gdy istniejący nie powiedzie się. Platforma powinna być również wystarczająco inteligentna, aby zatrzymać przędzenie nowych wystąpień, gdy każde nowe wystąpienie nie powiedzie się.

Aby uzyskać więcej informacji, zobacz [Implementowanie wzorca wyłącznika](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Przechowywanie wersji i wdrożenia w kolorze zielonym/niebieskim

Główną zaletą bezserwerowej jest możliwość uaktualnienia określonej funkcji bez konieczności ponownego wdrażania całej aplikacji. Aby uaktualnienia zakończyły się pomyślnie, funkcje muszą być wersjonowane, aby usługi wywołujące je były kierowane do poprawnej wersji kodu. Ważna jest również strategia wdrażania nowych wersji. Typowym podejściem jest użycie "zielonych/niebieskich wdrożeń". Zielone wdrożenie jest bieżącą funkcją. Nowa "niebieska" wersja jest wdrażana w środowisku produkcyjnym i testowana. Podczas testowania przebiegów, wersje zielone i niebieskie są wymieniane, więc nowa wersja jest dostępna na żywo. Jeśli wystąpią jakiekolwiek problemy, można je zamienić z powrotem. Obsługa wersji i wdrożeń zielony/niebieski wymaga kombinacji tworzenia funkcji, aby uwzględnić zmiany wersji i pracy z platformą bezserwerową do obsługi wdrożeń. Jednym z możliwych podejść jest użycie serwerów proxy, które są opisane w rozdziale [platformy bezserwerowej platformy platformy platformy platformy platformy platformy platformy Platformy Azure.](azure-functions.md#proxies)

>[!div class="step-by-step"]
>[Poprzedni](serverless-architecture.md)
>[następny](serverless-design-examples.md)
