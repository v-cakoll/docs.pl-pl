---
title: Zagadnienia dotyczące architektury bezserwerowej — aplikacje bezserwerowe
description: Zapoznaj się z wyzwaniami dotyczącymi tworzenia aplikacji bezserwerowych, od zarządzania stanami i trwałego magazynu do skalowania, rejestrowania, śledzenia i diagnostyki.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ecbffbbd435b4926608e4def519fdaddddab688d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676746"
---
# <a name="serverless-architecture-considerations"></a>Zagadnienia dotyczące architektury bezserwerowej

Przyjęcie architektury bezserwerowej wiąże się z pewnymi wyzwaniami. W tej części przedstawiono kilka typowych zagadnień, z którymi należy się zapoznać. Wszystkie te wyzwania mają rozwiązania. Podobnie jak w przypadku wszystkich opcji architektury, decyzja o bezproblemowym przejściu do serwera powinna być podejmowana dopiero po starannym uwzględnieniu specjalistów i wad. W zależności od potrzeb aplikacji możesz zdecydować, że implementacja bezserwerowa nie jest odpowiednim rozwiązaniem dla niektórych składników.

## <a name="managing-state"></a>Zarządzanie stanem

Funkcje bezserwerowe, podobnie jak w przypadku mikrousług, są domyślnie bezstanowe. Uniknięcie stanu powoduje, że serwer nie będzie miał charakteru tymczasowych, do skalowania w poziomie i zapewnienia odporności bez centralnego punktu awarii. W pewnych okolicznościach procesy biznesowe wymagają stanu. Jeśli proces wymaga stanu, dostępne są dwie opcje. Możesz przyjąć model inny niż serwer lub korzystać z osobnej usługi, która zapewnia stan. Dodanie stanu może spowodować skomplikowanie rozwiązania i utrudnić jego skalowanie i potencjalnie utworzyć single point of failure. Należy uważnie rozważyć, czy funkcja absolutnie wymaga stanu. Jeśli odpowiedź ma wartość "tak", należy określić, czy nadal ma sens zaimplementowanie jej z użyciem bezserwerowej.

Istnieje kilka rozwiązań do przyjęcia stanu bez naruszania korzyści związanych z serwerem. Oto niektóre z najpopularniejszych rozwiązań:

* Korzystanie z tymczasowego magazynu danych lub rozproszonej pamięci podręcznej, takich jak Redis
* Stan magazynu w bazie danych, na przykład SQL lub CosmosDB
* Obsługa stanu za pomocą aparatu przepływu pracy, takiego jak funkcje trwałe

Dolna linia polega na tym, że należy zwrócić uwagę na konieczność zarządzania stanami w ramach procesów, które są rozważane, aby wdrożyć je bezserwerowo.

## <a name="long-running-processes"></a>Długotrwałe procesy

Wiele zalet bezserwerowych jest zależnych od procesów tymczasowych. Krótkie czasy wykonywania ułatwiają dostawcy bezserwerowym zwolnienie zasobów jako funkcje końcowe i udostępniające funkcje między hostami. Większość dostawców chmury ogranicza łączny czas działania funkcji do około 10 minut. Jeśli proces może trwać dłużej, można rozważyć alternatywną implementację.

Istnieje kilka wyjątków i rozwiązań. Jednym z rozwiązań może być przerwanie procesu w mniejszych składnikach, które indywidualnie trwają krócej. Jeśli proces jest długotrwały ze względu na zależności, można także wziąć pod uwagę asynchroniczny przepływ pracy przy użyciu rozwiązania, takiego jak funkcje trwałe. Trwałe funkcje wstrzymują i utrzymują stan procesu, oczekując na zakończenie procesu zewnętrznego. Obsługa asynchroniczna skraca czas rzeczywistego uruchamiania procesu.

## <a name="startup-time"></a>Czas uruchamiania

Jednym z potencjalnych problemów dotyczących implementacji bezserwerowych jest czas uruchamiania. Aby zaoszczędzić zasoby, wielu dostawców bezserwerowych tworzy infrastrukturę "na żądanie". Gdy funkcja bezserwerowa jest wyzwalana po upływie okresu czasu, może być konieczne utworzenie lub ponowne uruchomienie zasobów do hostowania funkcji. W niektórych sytuacjach zimny start może powodować opóźnienia kilku sekund. Czas uruchamiania zależy od dostawców i poziomów usług. Istnieje kilka metod rozwiązywania czasu uruchamiania, jeśli ważne jest, aby zminimalizować w przypadku powodzenia aplikacji.

* Niektórzy dostawcy umożliwiają użytkownikom płatność za poziomy usług, które gwarantują infrastrukturę "zawsze włączone".
* Zaimplementuj mechanizm Keep-Alive (Wyślij polecenie ping do punktu końcowego, aby zachować jego wartość "aktywny").
* Używaj aranżacji, takiej jak Kubernetes, z podejściem do funkcji kontenera (host jest już uruchomiony, dzięki czemu nowe wystąpienia są niezwykle szybkie).

## <a name="database-updates-and-migrations"></a>Aktualizacje i migracje bazy danych

Zaletą bezserwerowego kodu jest możliwość zwolnienia nowych funkcji bez konieczności ponownego wdrażania całej aplikacji. Ta korzyść może stać się wadą, gdy istnieje relacyjna baza danych. Zmiany w schematach bazy danych są trudne do synchronizowania z aktualizacjami bez serwera. Dodatkowe wyzwania są powodowane, gdy wystąpią problemy, a zmiany muszą zostać wycofane. Integralność danych jest jednym z powodów, że najlepszym rozwiązaniem dla mikrousług i funkcji bezserwerowych jest posiadanie własnych danych. Można wdrożyć zmiany jako pojedynczą jednostkę obliczeniową i dane. Rzeczywistość polega na tym, że w wielu starszych systemach jest dostępna duża baza danych zaplecza, która musi być uzgodniona z architekturą bezserwerową.

Popularnym podejściem do rozwiązywania wersji schematu jest nigdy nie modyfikować istniejących właściwości i kolumn, ale zamiast tego Dodaj nowe informacje. Rozważmy na przykład zmianę przechodzenia z flagi "ukończone" z wartością "ukończony" na listę zadań do wykonania na "Data ukończenia". Zamiast usuwać stare pole, zmiana bazy danych będzie:

1. Dodaj nowe pole "Data zakończenia".
1. Przekształć pole Boolean "ukończony" na obliczaną funkcję, która oblicza, czy data zakończenia przypada po dacie bieżącej.
1. Dodaj wyzwalacz, aby ustawić datę ukończenia na bieżącą datę, gdy ukończona wartość logiczna jest ustawiona na wartość true.

Sekwencja zmian zapewnia, że starszy kod będzie nadal działać "w stanie takim, w jakim nowsze funkcje bezserwerowe mogą korzystać z nowego pola.

Aby uzyskać więcej informacji na temat danych w architekturach bezserwerowych, zobacz [wyzwania i rozwiązania dotyczące rozproszonego zarządzania danymi](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Skalowanie

Jest to typowa koncepcja, która bezserwerowo oznacza "Brak serwera". Jest to fakt "mniej serwera". Fakt, że istnieje infrastruktura zapasowa, jest ważne, aby zrozumieć, Kiedy przejdziesz do skalowania. Większość platform bezserwerowych udostępnia zestaw kontrolek do obsługi skalowalności infrastruktury, gdy zwiększa się gęstość zdarzeń. Można wybrać jedną z wielu opcji, ale strategia może się różnić w zależności od funkcji. Ponadto funkcje są zwykle uruchamiane w ramach pokrewnego hosta, dzięki czemu funkcje na tym samym hoście mają takie same opcje skalowania. W związku z tym konieczna jest organizacja i ułożeniu, które funkcje są hostowane razem na podstawie wymagań dotyczących skali.

Reguły często określają sposób skalowania w górę (zwiększenie zasobów hosta) i skalowanie w poziomie (zwiększenie liczby wystąpień hosta) na podstawie różnych parametrów. Wyzwalacze dla skalowania mogą obejmować harmonogram, szybkości żądań, użycie procesora CPU i użycie pamięci. Wyższa wydajność często odbywa się z większymi kosztami. Mniej kosztowne metody oparte na użyciu mogą nie skalować się jak najszybciej, gdy częstotliwość żądań nagle się zwiększy. Istnieje różnica między zapłaceniem "kosztem ubezpieczenia" i "w miarę jak" i "ryzykowne", z powodu nagłego wzrostu popytu.

## <a name="monitoring-tracing-and-logging"></a>Monitorowanie, śledzenie i rejestrowanie

Często DevOpsm aspektem jest monitorowanie aplikacji po wdrożeniu. Ważne jest, aby mieć strategię monitorowania funkcji bezserwerowych. Największe wyzwanie jest często korelacją lub rozpoznawania, gdy użytkownik wywołuje wiele funkcji w ramach tej samej interakcji. Większość platform bezserwerowych umożliwia rejestrowanie konsoli, które mogą być importowane do narzędzi innych firm. Dostępne są również opcje automatyzacji zbierania danych telemetrycznych, generowania i śledzenia identyfikatorów korelacji oraz monitorowania określonych akcji w celu zapewnienia szczegółowych informacji. Platforma Azure udostępnia zaawansowaną [platformę Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) do monitorowania i analizy.

## <a name="inter-service-dependencies"></a>Zależności między usługami

Architektura bezserwerowa może obejmować funkcje, które korzystają z innych funkcji. W rzeczywistości nierzadko zdarza się, że w architekturze bezserwerowej wiele usług wywołuje siebie nawzajem w ramach interakcji lub transakcji rozproszonej. Aby uniknąć silnego sprzężenia, zaleca się, aby usługi nie odwołują się bezpośrednio do siebie. Gdy punkt końcowy usługi wymaga zmiany, bezpośrednie odwołania mogą skutkować poważnym refaktoryzacją. Sugerowanym rozwiązaniem jest zapewnienie mechanizmu odnajdowania usług, takiego jak rejestr, który zapewnia odpowiedni punkt końcowy dla typu żądania. Innym rozwiązaniem jest wykorzystanie usług przesyłania komunikatów, takich jak kolejki lub tematy, aby komunikować się między usługami.

## <a name="managing-failure-and-providing-resiliency"></a>Zarządzanie awarią i zapewnianie odporności

Ważne jest również, aby wziąć pod uwagę *wzorzec*wyłącznika: Jeśli z jakiegoś powodu usługa nadal nie powiedzie się, nie zaleca się wielokrotnego wywołania tej usługi. Zamiast tego wywoływana jest usługa alternatywna lub komunikat zwracany do momentu ponownego ustanowienia kondycji usługi zależnej. Architektura bezserwerowa musi uwzględniać strategię rozwiązywania zależności między usługami i zarządzania nimi.

Aby kontynuować wzorzec wyłącznika, usługi muszą być odporne na uszkodzenia i odporne na błędy. Odporność na uszkodzenia dotyczy możliwości kontynuowania działania aplikacji nawet po wystąpieniu nieoczekiwanych wyjątków lub napotkaniu nieprawidłowych Stanów. Odporność na uszkodzenia jest zazwyczaj funkcją samego kodu i w jaki sposób jest zapisywana w celu obsługi wyjątków. Odporność odnosi się do sposobu, w jaki aplikacja jest w trakcie odzyskiwania po awarii. Odporność jest często zarządzana przez platformę bezserwerową. Platforma powinna być w stanie uruchamiać nowe wystąpienie funkcji bezserwerowej, gdy istniejąca awaria nie powiedzie się. Platforma powinna być również inteligentnie dostępna, aby zatrzymać nowe wystąpienia, gdy każde nowe wystąpienie nie powiedzie się.

Aby uzyskać więcej informacji, zobacz [implementowanie wzorca](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)wyłącznika.

## <a name="versioning-and-greenblue-deployments"></a>Przechowywanie wersji i zielone/niebieskie wdrożenia

Główną zaletą bezserwerową jest możliwość uaktualnienia określonej funkcji bez konieczności ponownego wdrażania całej aplikacji. Aby uaktualnienia zostały wykonane pomyślnie, funkcje muszą być w wersji, tak aby usługi wywołujące je, były kierowane do odpowiedniej wersji kodu. Jest również ważna strategia wdrażania nowych wersji. Typowym podejściem jest użycie "zielone/niebieskie wdrożenia". Zielone wdrożenie jest bieżącą funkcją. Nowa wersja "niebieska" została wdrożona w środowisku produkcyjnym i przetestowana. Podczas testowania są wymieniane zielone i niebieskie wersje, aby nowa wersja była aktywna. Jeśli wystąpią jakieś problemy, można wymienić je ponownie. Obsługa wersji i wdrożenia zielone/niebieskie wymagają kombinacji tworzenia funkcji w celu uwzględnienia zmian wersji i pracy z platformą bezserwerową do obsługi wdrożeń. Jedną z możliwych metod jest użycie serwerów proxy, które są opisane w rozdziale [platformy](azure-functions.md#proxies) bezserwerowej platformy Azure.

>[!div class="step-by-step"]
>[Poprzedni](serverless-architecture.md)Następny
>[](serverless-design-examples.md)
