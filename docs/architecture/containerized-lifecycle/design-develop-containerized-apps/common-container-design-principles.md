---
title: Wspólne zasady projektowania kontenera
description: Naucz się podstawowej zasady dobrego projektowania kontenerów, jest to, że kontener powinien obsługiwać tylko jeden proces.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295330"
---
# <a name="common-container-design-principles"></a>Wspólne zasady projektowania kontenera

Przed przejściem do procesu rozwoju istnieje kilka podstawowych pojęć, o których warto wspomnieć w odniesieniu do sposobu korzystania z kontenerów.

## <a name="container-equals-a-process"></a>Kontener jest równy procesowi

W modelu kontenera kontenera reprezentuje pojedynczy proces. Definiując kontener jako granicę procesu, należy rozpocząć tworzenie elementów pierwotnych używanych do skalowania lub wysypywania procesów. Po uruchomieniu kontenera platformy Docker zobaczysz definicję [ENTRYPOINT.](https://docs.docker.com/engine/reference/builder/#/entrypoint) Definiuje proces i okres istnienia kontenera. Po zakończeniu procesu kończy się cykl życia kontenera. Istnieją długotrwałe procesy, takie jak serwery sieci web i procesy krótkotrwałe, takie jak zadania wsadowe, które mogły zostać zaimplementowane jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Jeśli proces nie powiedzie się, kontener kończy się, a koordynator przejmuje. Jeśli koordynator został poinstruowany, aby zachować pięć wystąpień uruchomiony i jeden nie powiedzie się, koordynator utworzy inny kontener, aby zastąpić proces nie powiodło się. W zadaniu wsadowym proces jest uruchamiany z parametrami. Po zakończeniu procesu praca zostanie zakończona.

Może się okazać scenariusz, w którym chcesz wiele procesów uruchomionych w jednym kontenerze. W każdym dokumencie architektury nigdy nie ma "nigdy", ani nie zawsze istnieje "zawsze". W przypadku scenariuszy wymagających wielu procesów typowym wzorcem jest użycie [inspektora.](http://supervisord.org/)

>[!div class="step-by-step"]
>[Poprzedni](design-docker-applications.md)
>[następny](monolithic-applications.md)
