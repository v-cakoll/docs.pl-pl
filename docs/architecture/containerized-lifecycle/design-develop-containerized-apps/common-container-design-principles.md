---
title: Wspólne zasady projektowania kontenera
description: Zapoznaj się z podstawową zasadą dobrego projektowania kontenerów, że kontener powinien obsługiwać tylko jeden proces.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295330"
---
# <a name="common-container-design-principles"></a>Wspólne zasady projektowania kontenera

Przed rozpoczęciem procesu tworzenia programu istnieje kilka podstawowych koncepcji dotyczących sposobu korzystania z kontenerów.

## <a name="container-equals-a-process"></a>Kontener jest równy procesowi

W modelu kontenera kontener reprezentuje pojedynczy proces. Definiując kontener jako granicę procesu, zaczynasz tworzyć elementy pierwotne służące do skalowania lub tworzenia partii procesów. Po uruchomieniu kontenera Docker zostanie wyświetlona definicja [punktu wejścia](https://docs.docker.com/engine/reference/builder/#/entrypoint) . Definiuje proces i okres istnienia kontenera. Po zakończeniu procesu cykl życia kontenera kończy się. Istnieją długotrwałe procesy, takie jak serwery sieci Web i procesy krótkoterminowe, takie jak zadania wsadowe, które mogły zostać zaimplementowane jako Microsoft Azure [Zadania WebJob](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Jeśli proces zakończy się niepowodzeniem, kontener kończy się, a koordynator zajmie się. Jeśli w programie Orchestrator zawarto zachowanie pięciu wystąpień i jeden z nich nie powiedzie się, program Orchestrator utworzy inny kontener, aby zastąpić proces zakończony niepowodzeniem. W zadaniu wsadowym proces jest uruchamiany z parametrami. Po zakończeniu procesu pracy zostanie zakończona.

Możesz znaleźć scenariusz, w którym wiele procesów działa w jednym kontenerze. W dowolnym dokumencie architektury nigdy nie jest "nigdy", ani nie zawsze jest "zawsze". W przypadku scenariuszy wymagających wielu procesów typowym wzorcem jest użycie [opiekuna](http://supervisord.org/).

>[!div class="step-by-step"]
>[Poprzedni](design-docker-applications.md)
>[Następny](monolithic-applications.md)
