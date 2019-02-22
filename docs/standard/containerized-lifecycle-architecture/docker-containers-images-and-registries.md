---
title: Kontenery platformy docker, obrazy i rejestry
description: Dowiedz się, kluczową rolę, że rejestrów odtworzyć ogólny w sposób platformy Docker, wdrażania aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e69490734a03cf58bf8534bc9e31110a11d44c58
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583319"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery platformy docker, obrazy i rejestry

Korzystając z platformy Docker, tworzenie aplikacji lub usługi i pakietu on i jego zależności do obrazu kontenera. Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker. Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.

Obrazy są przechowywane w rejestrze, która działa jako biblioteka obrazów. Konieczne jest zarejestrowanie podczas wdrażania do produkcji koordynatorów. Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców zapewnienia różne kolekcje obrazów, włącznie z rejestrami [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.

Rysunek 1 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników. Zawiera również wiele ofert rejestru od dostawców.

![Podstawowe Taksonomia na platformie Docker: Rejestr przypomina bookshelf, w którym obrazy są przechowywane i dostępny do ściągnięcia do tworzenia kontenerów do uruchamiania usługi lub aplikacji sieci web. Istnieją prywatnego platformy Docker rejestrów w środowisku lokalnym i w chmurze publicznej. Usługi docker Hub jest rejestru publicznego obsługiwane przez platformę Docker, wzdłuż rozwiązania Docker Trusted Registry przeznaczonych dla przedsiębiorstw, platforma Azure oferuje usługi Azure Container Registry. Usługi AWS, Google i innych również mieć rejestry kontenerów.](./media/image4.png)

**Rysunek 1 – 4**. Taksonomia usługi Docker terminy i pojęcia

Umieszczając obrazów w rejestrze, można przechowywać bitów statyczne i niezmienne aplikacji, w tym wszystkie zależności, na poziomie framework. Możesz następnie wersji i wdrożyć obrazy w wielu środowiskach i ten sposób zapewnia spójne wdrażanie jednostki.

Rejestry obrazu prywatnego albo hostowanych lokalnie lub w chmurze, są zalecane, gdy:

- Obrazów nie może być publicznie udostępniany z powodu poufności.

- Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej. Na przykład, jeśli środowisko produkcyjne platformy Azure, prawdopodobnie chcesz przechowywać swoje obrazy w [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienia sieci jest minimalny. W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.

>[!div class="step-by-step"]
>[Poprzednie](docker-terminology.md)
>[dalej](road-to-modern-applications-based-on-containers.md)
