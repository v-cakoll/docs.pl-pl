---
title: Kontenery platformy docker, obrazy i rejestry
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: af235280c985d20f9e6a2ee6096edbe6c3aad63a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53142752"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery platformy docker, obrazy i rejestry

Korzystając z platformy Docker, tworzenie aplikacji lub usługi i pakietu on i jego zależności do obrazu kontenera. Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker. Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.

Obrazy są przechowywane w rejestrze, która działa jako biblioteka obrazów. Konieczne jest zarejestrowanie podczas wdrażania do produkcji koordynatorów. Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców udostępnia rejestrów dla różnych kolekcji obrazów. Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.

Rysunek 1 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników. Zawiera również wiele ofert rejestru od dostawców.

![](./media/image4.png)

Rysunek 1-4: Taksonomia usługi Docker terminy i pojęcia

Umieszczając obrazów w rejestrze, można przechowywać bitów statyczne i niezmienne aplikacji, w tym wszystkie zależności, na poziomie framework. Możesz następnie wersji i wdrożyć obrazy w wielu środowiskach i ten sposób zapewnia spójne wdrażanie jednostki.

Rejestry obrazów prywatnych, hostowanych lokalnie lub w chmurze, są zalecane w następujących sytuacjach:

-   Obrazów nie może być publicznie udostępniany z powodu poufności.

-   Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej. Na przykład jeśli środowisko produkcyjne platformy Azure, prawdopodobnie chcesz przechowywać obrazy w usłudze Azure Container Registry tak, aby opóźnienia sieci minimalnej. W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.

>[!div class="step-by-step"]
>[Poprzednie](docker-terminology.md)
>[dalej](Docker-application-lifecycle/index.md)