---
title: Aplikacje bazujące na projektowanie w kontenerach i Mikrousługach
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Aplikacje bazujące na projektowanie w kontenerach i Mikrousługach
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f7933cc25a5fde13113d0c9c278e9bd1730d4f9d
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085975"
---
# <a name="architecting-container--and-microservice-based-applications"></a>Projektowanie aplikacji oparte na kontenerach i Mikrousługach

*Mikrousługi oferują wiele korzyści, ale także podnieść ogromna nowe wyzwania. Wzorce architektury Mikrousług są podstawowe filary, podczas tworzenia aplikacji opartych na mikrousługach.*

Wcześniej w tym przewodniku przedstawiono podstawowe pojęcia dotyczące kontenerów i platformy Docker. To było minimalną ilość informacji, że potrzebujesz, aby rozpocząć pracę z kontenerami. Mimo że, nawet wtedy, gdy kontenery są enablers i doskonałe rozwiązanie dla mikrousług, nie są wymagane w przypadku architektury mikrousługi i wiele pojęć architektury w tej sekcji architekturę można stosować bez kontenerów, zbyt. Jednak te wskazówki koncentruje się na przecięciu zarówno z powodu znaczenia wprowadzenie już kontenerów.

Aplikacje dla przedsiębiorstw mogą być złożone i często składają się z wielu usług, zamiast pojedynczej aplikacji opartych na usługach. W tych przypadkach należy zrozumieć dodatkowe podejściach architektonicznych, takie jak mikrousługi i niektórych wzorców projektowych driven (DDD) oraz koncepcjami dotyczącymi organizowania kontenerów. Należy pamiętać, że w tym rozdziale opisano nie tylko mikrousług, kontenerów, ale wszystkie konteneryzowanych aplikacji, jak również.

## <a name="container-design-principles"></a>Zasady projektowania kontenera

W modelu kontenera wystąpienia obrazu kontenera reprezentuje pojedynczego procesu. Definiując obraz kontenera jako granica procesu, można utworzyć w nim elementów podstawowych, które mogą służyć do skalowania procesu lub do przetwarzania wsadowego, jego.

Podczas projektowania obraz kontenera zostanie wyświetlony [punktu wejścia](https://docs.docker.com/engine/reference/builder/) definicję w pliku Dockerfile. Definiuje proces, którego okres istnienia określa okres istnienia kontenera. Po zakończeniu procesu, kończy się cyklu życia kontenera. Kontenery może reprezentować długotrwałe procesy takie jak serwery sieci web, ale można również reprezentują krótkotrwałe procesy, takie jak zadania usługi batch, które wcześniej może zostały zaimplementowane jako Azure [WebJobs](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources).

Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i koordynatora przejmuje. Jeśli koordynatora został skonfigurowany do zachowania pięć wystąpień i zawiedzie, koordynatora utworzy innego wystąpienia kontenera w celu zastąpienia procesu nie powiodło się. W ramach zadania usługi batch proces zostanie uruchomiony przy użyciu parametrów. Po zakończeniu tego procesu roboczego zostało ukończone. Niniejsze wskazówki awarii rozwijaną koordynatorów później.

Może się okazać scenariusz, w którym ma się wiele procesów w jeden kontener. W tym scenariuszu ponieważ może istnieć tylko jeden wpis punktu na kontener, może uruchomić skrypt w kontenerze, który uruchamia programy tyle zgodnie z potrzebami. Na przykład, można użyć [nadzorca](http://supervisord.org/) lub podobnego narzędzia, aby zadbać o uruchamianie wielu procesów w jednym kontenerze. Jednak mimo że można znaleźć architektur, zawierających wiele procesów na kontener, takie podejście nie jest bardzo często.


>[!div class="step-by-step"]
[Poprzednie](../net-core-net-framework-containers/official-net-docker-images.md)
[dalej](containerize-monolithic-applications.md)
