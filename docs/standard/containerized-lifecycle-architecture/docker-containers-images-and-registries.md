---
title: Kontenery, obrazy i rejestry platformy Docker
description: Dowiedz się, kluczową rolę, że rejestrów odtworzyć ogólny w sposób platformy Docker, wdrażania aplikacji.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641326"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

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
