---
title: Tworzenie architektury aplikacji opartych na kontenerach i mikrousługach
description: Projektowanie aplikacji opartych na kontenerach i mikrousługach nie jest małe feat i nie powinno być wykonywane w sposób jasny. Zapoznaj się z podstawowymi pojęciami w tym rozdziale.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295519"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Tworzenie architektury aplikacji opartych na kontenerach i mikrousługach

*Mikrousługi oferują znakomite korzyści, ale również powodują ogromne nowe wyzwania. Wzorce architektury mikrousług są podstawowymi filarami podczas tworzenia aplikacji opartej na mikrousługach.*

Wcześniej w tym przewodniku przedstawiono podstawowe pojęcia dotyczące kontenerów i platformy Docker. To było minimalnych informacji, które trzeba wykonać, aby rozpocząć pracę z kontenerami. Chociaż w przypadku kontenerów i doskonałej dopasowania dla mikrousług nie są one obowiązkowe dla architektury mikrousług, a wiele pojęć związanych z architekturą w tej sekcji architektury można zastosować bez kontenerów. Jednak te wskazówki koncentrują się na przecięciu obu elementów ze względu na już wprowadzone znaczenie kontenerów.

Aplikacje dla przedsiębiorstw mogą być złożone i często składają się z wielu usług zamiast pojedynczej aplikacji opartej na usłudze. W takich przypadkach należy poznać dodatkowe podejścia do architektury, takie jak mikrousługi i pewne wzorce projektowania oparte na domenie (DDD) i koncepcje aranżacji kontenerów. Należy zauważyć, że w tym rozdziale opisano nie tylko mikrousługi na kontenerach, ale również w przypadku wszystkich aplikacji kontenerowych.

## <a name="container-design-principles"></a>Zasady projektowania kontenerów

W modelu kontenera wystąpienie obrazu kontenera reprezentuje pojedynczy proces. Definiując obraz kontenera jako granicę procesu, można utworzyć elementy podstawowe, których można użyć do skalowania procesu lub tworzenia wsadowego.

Podczas projektowania obrazu kontenera zobaczysz definicję [punktu wejścia](https://docs.docker.com/engine/reference/builder/#entrypoint) w pliku dockerfile. Definiuje proces, którego okres istnienia steruje okresem istnienia kontenera. Po zakończeniu procesu cykl życia kontenera kończy się. Kontenery mogą reprezentować długotrwałe procesy, takie jak serwery sieci Web, ale mogą również reprezentować procesy krótkoterminowe, takie jak zadania wsadowe, które wcześniej mogły zostać zaimplementowane jako [Zadania WebJob](https://github.com/Azure/azure-webjobs-sdk/wiki)platformy Azure.

Jeśli proces zakończy się niepowodzeniem, kontener kończy się, a koordynator zajmie się. Jeśli program Orchestrator został skonfigurowany tak, aby nadal działały pięć wystąpień i jeden z nich kończy się niepowodzeniem, program Orchestrator utworzy inne wystąpienie kontenera, aby zastąpić proces zakończony niepowodzeniem. W zadaniu wsadowym proces jest uruchamiany z parametrami. Po zakończeniu procesu pracy zostanie zakończona. Te wskazówki przechodzenia do szczegółów w przypadku programów Orchestrator i nowszych wersji.

Możesz znaleźć scenariusz, w którym wiele procesów działa w jednym kontenerze. W tym scenariuszu, ponieważ może istnieć tylko jeden punkt wejścia dla każdego kontenera, można uruchomić skrypt w kontenerze, który uruchamia dowolną liczbę programów w miarę potrzeb. Na przykład można użyć [opiekuna](http://supervisord.org/) lub podobnego narzędzia, aby zadbać o uruchomienie wielu procesów wewnątrz jednego kontenera. Jednak mimo że można znaleźć architektury, które przechowują wiele procesów na kontener, takie podejście nie jest bardzo powszechne.

>[!div class="step-by-step"]
>[Poprzedni](../net-core-net-framework-containers/official-net-docker-images.md)Następny
>[](containerize-monolithic-applications.md)
