---
title: Zaprojektowanie kontenera i Mikrousługi aplikacji opartych na
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Zaprojektowanie kontenera i Mikrousługi aplikacji opartych na
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 185279cb4df70d9896d7e11c995170e7cd214f73
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106817"
---
# <a name="architecting-container--and-microservice-based-applications"></a>Projektowania aplikacji opartych na kontenera i Mikrousługi

*Mikrousług oferują dużą korzyści, ale także podnieść ogromnych wyzwania. Wzorce architektury Mikrousługi są podstawowych słupków podczas tworzenia aplikacji opartych na mikrousługi.*

Wcześniej w tym przewodniku przedstawiono podstawowe pojęcia dotyczące kontenerów i Docker. Która jest minimalną ilość informacji, aby rozpocząć pracę z kontenerami potrzebne. Niemniej jednak nawet wtedy, gdy kontenery są czynników istnienie i doskonałym rozwiązaniem dla mikrousług, nie są one wymagane w przypadku architektury mikrousługi i wiele pojęć architektury w tej sekcji architektura można go zastosować bez kontenerów, zbyt. Jednak w tych wskazówkach koncentruje się na przecięciu zarówno z powodu już wprowadzone znaczenie kontenerów.

Aplikacje przedsiębiorstwa może być skomplikowane i często składają się z wielu usług zamiast jednej aplikacji opartych na usługach. W tych przypadkach należy zrozumieć dodatkowe architektury podejścia, takie jak mikrousług i niektórych wzorce projektowania Domain-Driven (DDD) oraz pojęcia aranżacji kontenera. Należy pamiętać, że w tym rozdziale opisano mikrousług nie tylko na kontenery, ale wszystkie konteneryzowanych aplikacji, jak również.

## <a name="container-design-principles"></a>Zasady projektowania kontenera

W modelu kontenera wystąpienia obrazu kontenera reprezentuje jednego procesu. Definiując obrazu kontenera jako granica procesu, można utworzyć podstawowych, które mogą być używane do skalowania procesu lub do przetwarzania wsadowego go.

Podczas projektowania obrazu kontenera, zobaczysz [punktu wejścia](https://docs.docker.com/engine/reference/builder/) definicji w plik Dockerfile. Definiuje proces, w której czas życia określa okres istnienia kontenera. Po zakończeniu tego procesu, kończy się cyklu życia kontenera. Kontenery może reprezentować procesy długotrwałe, takich jak serwery sieci web, ale można również reprezentują krótkim okresie procesów, takich jak zadania wsadowego, które wcześniej może została zaimplementowana jako Azure [Webjob](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources).

Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i orchestrator ma. Jeśli skonfigurowano orchestrator do zachowania pięć uruchomionych wystąpień i zawiedzie, orchestrator utworzy inne wystąpienie kontenera, aby zastąpić procesu nie powiodło się. Proces jest uruchomiony w ramach zadania wsadowego parametrów. Po zakończeniu tego procesu, praca jest ukończona. We wskazówkach tych ćwiczeń w dół na orchestrators, później.

Może się okazać scenariusz, w którym ma wiele procesów uruchomionych w jeden kontener. W tym scenariuszu ponieważ może istnieć tylko jeden wpis punktu dla kontenera, może uruchomić skrypt w kontenerze, który uruchamia dowolnej liczby programów. Na przykład można użyć [przełożonego](http://supervisord.org/) lub podobnego narzędzia do obsługi wielu procesów w jeden kontener uruchamianie. Jednak mimo że można znaleźć architektury zawierających wiele procesów na kontenera, podejście nie jest bardzo często.


>[!div class="step-by-step"]
[Poprzednie](../net-core-net-framework-containers/official-net-docker-images.md)
[dalej](containerize-monolithic-applications.md)
