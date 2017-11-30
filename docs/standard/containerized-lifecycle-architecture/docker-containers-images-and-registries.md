---
title: "Kontenery docker, obrazy i rejestrów"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a>Kontenery docker, obrazy i rejestrów

Korzystając z Docker, tworzenia aplikacji lub usługi i pakietu go i jego zależności w obrazie kontenera. Obraz jest statyczny reprezentację aplikacji lub usługi i konfiguracji oraz zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony, aby utworzyć kontener, który zostanie uruchomiona na hoście Docker. Kontenery początkowo są testowane w środowisko projektowe lub komputera.

Obrazy są przechowywane w rejestrze, która działa jako biblioteki obrazów. Konieczne jest zarejestrowanie podczas wdrażania orchestrators produkcji. Docker przechowuje rejestr publiczny za pomocą [Centrum Docker](https://hub.docker.com/); innych dostawców Podaj rejestrów dla różnych kolekcji obrazów. Alternatywnie przedsiębiorstwa mogą mieć prywatnych rejestru lokalnymi własnych obrazów Docker.

Rysunek 1-4 przedstawiono, jak obrazy i rejestrów w Docker odnoszą się do innych składników. Zawiera także wiele ofert rejestru od dostawców.

![](./media/image4.png)

Rysunek 1-4 taksonomii Docker terminy i pojęcia

Umieszczenie obrazów w rejestrze, można przechowywać bitów statycznych i modyfikować aplikacji, w tym wszystkie ich zależności na poziomie framework. Możesz następnie można wersji i wdrażania obrazów w środowiskach wielu i w związku z tym jednostki spójne wdrożenia.

Rejestry prywatnej obrazu obsługiwanego lokalnie lub w chmurze, zaleca się w następujących sytuacjach:

-   Obrazów nie może być udostępniany publicznie z powodu poufności.

-   Chcesz, aby minimalna sieci opóźnienia między obrazów i środowiska wdrażania wybrany. Na przykład jeśli Azure znajduje się w środowisku produkcyjnym, prawdopodobnie chcesz przechowywać obrazów w rejestrze kontenera platformy Azure, dzięki czemu jest minimalnego opóźnienia sieci. W podobny sposób w przypadku środowiska produkcyjnego w infrastrukturze lokalnej, możesz mieć lokalnymi Docker zaufane rejestru dostępne w ramach tej samej sieci lokalnej.

>[!div class="step-by-step"]
[Poprzednie] (docker-terminology.md) [dalej] (Docker aplikacji-cyklu życia/index.md)
