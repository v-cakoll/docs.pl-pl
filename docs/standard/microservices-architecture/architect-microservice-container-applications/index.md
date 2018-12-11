---
title: Tworzenie kontenera i aplikacji opartych na mikrousługach
description: Tworzenie kontenera i aplikacji opartych na mikrousługach jest nie małych feat i nie powinien należy podjąć w niewielkim stopniu. Dowiedz się, podstawowe koncepcje w tym rozdziale.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 6b1d5f7f0ab18e4f1d4b5c2200ac0c6f40c701ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155421"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Tworzenie kontenera i aplikacji opartych na mikrousługach

*Mikrousługi oferują wiele korzyści, ale także podnieść ogromna nowe wyzwania. Wzorce architektury Mikrousług są podstawowe filary, podczas tworzenia aplikacji opartych na mikrousługach.*

Wcześniej w tym przewodniku przedstawiono podstawowe pojęcia dotyczące kontenerów i platformy Docker. To było minimalną ilość informacji, że chcesz rozpocząć pracę z kontenerami. Mimo że, nawet wtedy, gdy kontenery są enablers i doskonałe rozwiązanie dla mikrousług, nie są wymagane w przypadku architektury mikrousługi i wiele pojęć architektury w tej sekcji architekturę można stosować bez kontenerów, zbyt. Jednak te wskazówki koncentruje się na przecięciu zarówno z powodu znaczenia wprowadzenie już kontenerów.

Aplikacje dla przedsiębiorstw mogą być złożone i często składają się z wielu usług, zamiast pojedynczej aplikacji opartych na usługach. W tych przypadkach należy zrozumieć dodatkowe podejściach architektonicznych, takie jak mikrousługi i niektórych wzorców projektowych driven (DDD) oraz koncepcjami dotyczącymi organizowania kontenerów. Należy pamiętać, że w tym rozdziale opisano nie tylko mikrousług, kontenerów, ale wszystkie konteneryzowanych aplikacji, jak również.

## <a name="container-design-principles"></a>Zasady projektowania kontenera

W modelu kontenera wystąpienia obrazu kontenera reprezentuje pojedynczego procesu. Definiując obraz kontenera jako granica procesu, można utworzyć w nim elementów podstawowych, które mogą służyć do skalowania procesu lub do przetwarzania wsadowego, jego.

Podczas projektowania obraz kontenera, zobaczysz [punktu wejścia](https://docs.docker.com/engine/reference/builder/#entrypoint) definicję w pliku Dockerfile. Definiuje proces, którego okres istnienia określa okres istnienia kontenera. Po zakończeniu procesu, kończy się cyklu życia kontenera. Kontenery może reprezentować długotrwałe procesy takie jak serwery sieci web, ale można również reprezentują krótkotrwałe procesy, takie jak zadania usługi batch, które wcześniej może zostały zaimplementowane jako Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i koordynatora przejmuje. Jeśli koordynatora został skonfigurowany do zachowania pięć wystąpień i zawiedzie, koordynatora utworzy innego wystąpienia kontenera w celu zastąpienia procesu nie powiodło się. W ramach zadania usługi batch proces zostanie uruchomiony przy użyciu parametrów. Po zakończeniu tego procesu roboczego zostało ukończone. Niniejsze wskazówki awarii rozwijaną koordynatorów później.

Może się okazać scenariusz, w którym ma się wiele procesów w jeden kontener. W tym scenariuszu ponieważ może istnieć tylko jeden wpis punktu na kontener, może uruchomić skrypt w kontenerze, który uruchamia programy tyle zgodnie z potrzebami. Na przykład, można użyć [nadzorca](http://supervisord.org/) lub podobnego narzędzia, aby zadbać o uruchamianie wielu procesów w jednym kontenerze. Jednak mimo że można znaleźć architektur, zawierających wiele procesów na kontener, takie podejście nie jest bardzo często.

>[!div class="step-by-step"]
>[Poprzednie](../net-core-net-framework-containers/official-net-docker-images.md)
>[dalej](containerize-monolithic-applications.md)