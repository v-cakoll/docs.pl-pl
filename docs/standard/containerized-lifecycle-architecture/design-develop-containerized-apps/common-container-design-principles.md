---
title: "Wspólne zasady projektowania kontenera"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7186ae3b768384fe5c6b269578de8db5ef6064c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="common-container-design-principles"></a>Wspólne zasady projektowania kontenera

Wyprzedzeniem wprowadzenie do procesu tworzenia dostępnych jest kilka podstawowych pojęć, warto zauważyć w odniesieniu do sposobu korzystania kontenerów.

## <a name="container-equals-a-process"></a>Kontener jest równe procesu

W modelu kontenera kontener reprezentuje jednego procesu. Definiując kontener jako granica procesu, rozpoczęciem tworzenia podstawowych używane do skalowania, lub wyłącz partii, procesów. Po uruchomieniu kontenera Docker zobaczysz [punktu wejścia](https://docs.docker.com/engine/reference/builder/#/entrypoint) definicji. Definiuje proces i okresem istnienia kontenera. Po zakończeniu tego procesu, kończy się cyklu życia kontenera. Brak procesy długotrwałe, takie jak serwery sieci web i krótkim okresie procesy, takie jak zadania wsadowego, które może być zaimplementowany jako Microsoft Azure [Webjob](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/). Jeśli proces zakończy się niepowodzeniem, kończy się kontenera i orchestrator ma. Jeśli poinstruowano orchestrator w celu zachowania pięć uruchomionych wystąpień i zawiedzie, orchestrator utworzy innego kontenera, aby zastąpić procesu nie powiodło się. Proces jest uruchomiony w ramach zadania wsadowego parametrów. Po zakończeniu tego procesu, praca jest ukończona.

Może się okazać scenariusz, w którym ma wiele procesów uruchomionych w jeden kontener. Architektura dokumentów, nigdy nie jest nigdy "," nie ma zawsze jako "zawsze". W scenariuszach wymagających wielu procesów, jest użycie wspólnego wzorca [przełożonego](http://supervisord.org/).


>[!div class="step-by-step"]
[Poprzednie] (projekt docker-applications.md) [dalej] (wbudowanymi applications.md)
