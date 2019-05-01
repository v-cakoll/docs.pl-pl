---
title: Kontenery, obrazy i rejestry platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Kontenery platformy docker, obrazy i rejestry
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: f10d7d03bbf88ed8f7a89a5d3919a39b3c124ae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025547"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

Korzystając z platformy Docker, deweloper tworzy i pakiety aplikacji lub usługi, on i jego zależności do obrazu kontenera. Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker. Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.

Deweloperzy należy przechowywać obrazy w rejestrze, który działa jako biblioteka obrazów i nie jest wymagana podczas wdrażania do produkcji koordynatorów. Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców zapewnienia różne kolekcje obrazów, włącznie z rejestrami [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.

Rysunek 2 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników. Zawiera również wiele ofert rejestru od dostawców.

![Podstawowe Taksonomia na platformie Docker: Rejestr przypomina bookshelf, w którym obrazy są przechowywane i dostępny do ściągnięcia do tworzenia kontenerów do uruchamiania usługi lub aplikacji sieci web. Istnieją prywatnego platformy Docker rejestrów lokalnych i w chmurze publicznej. Usługi docker Hub jest rejestru publicznego obsługiwane przez platformę Docker, wzdłuż rozwiązania Docker Trusted Registry przeznaczonych dla przedsiębiorstw, platforma Azure oferuje usługi Azure Container Registry. Usługi AWS, Google i innych również mieć rejestry kontenerów.](./media/image5.PNG)

**Rysunek 2 – 4**. Taksonomia usługi Docker terminy i pojęcia

Umieszczenie obrazów w rejestrze pozwala przechowywać bitów statyczne i niezmienne aplikacji, wraz ze wszystkimi jego zależnościami na poziomie framework. Tych obrazów może następnie być wersjonowane i wdrażane w wielu środowiskach i stanowić jednostki spójne wdrażanie.

Rejestry obrazu prywatnego albo hostowanych lokalnie lub w chmurze, są zalecane, gdy:

- Obrazów nie może być publicznie udostępniany z powodu poufności.

- Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej. Na przykład, jeśli środowisko produkcyjne platformy Azure w chmurze, prawdopodobnie chcesz przechowywać obrazy w [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienia sieci minimalnej. W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.

>[!div class="step-by-step"]
>[Poprzednie](docker-terminology.md)
>[dalej](../net-core-net-framework-containers/index.md)