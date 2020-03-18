---
title: Kontenery, obrazy i rejestry platformy Docker
description: Dowiedz się kluczową rolę, jaką rejestry odgrywają ogólnie w sposób docker wdrażania aplikacji.
ms.date: 02/15/2019
ms.openlocfilehash: bfef21cab7be89abaf33b89366d7cff2115a7cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72770927"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

Korzystając z platformy Docker, należy utworzyć aplikację lub usługę i spakować ją i jego zależności do obrazu kontenera. Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji jest tworzony w celu utworzenia kontenera, który będzie uruchomiony na hoście platformy Docker. Kontenery są początkowo testowane w środowisku programistycznym lub komputerze.

Obrazy są przechowywane w rejestrze, który działa jako biblioteka obrazów. Należy rejestru podczas wdrażania do koordynatorów produkcji. Platforma Docker utrzymuje rejestr publiczny za pośrednictwem [centrum docker;](https://hub.docker.com/) inni dostawcy udostępniają rejestry dla różnych kolekcji obrazów, w tym [rejestru kontenerów azure](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą mieć prywatny rejestr lokalnie dla własnych obrazów platformy Docker.

Rysunek 1-4 pokazuje, jak obrazy i rejestry w platformie Docker odnoszą się do innych składników. Pokazuje również wiele ofert rejestru od dostawców.

![Diagram przedstawiający taksonomię podstawową w platformie Docker.](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

**Rysunek 1-4**. Taksonomia terminów i koncepcji platformy Docker

Rejestr jest jak półka, na której obrazy są przechowywane i dostępne do ściągnięcia do tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web. Istnieją prywatne rejestry platformy Docker lokalnie i w chmurze publicznej. Docker Hub to rejestr publiczny obsługiwany przez platformę Docker, wzdłuż zaufanego rejestru platformy Docker, rozwiązanie klasy korporacyjnej, platforma Azure oferuje rejestr kontenerów platformy Azure. AWS, Google i inni mają również rejestry kontenerów.

Umieszczając obrazy w rejestrze, można przechowywać statyczne i niezmienne bity aplikacji, w tym wszystkie ich zależności, na poziomie struktury. Następnie można wersji i wdrażania obrazów w wielu środowiskach, a tym samym zapewnić spójną jednostkę wdrażania.

Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane, gdy:

- Twoje zdjęcia nie mogą być udostępniane publicznie ze względu na poufność.

- Chcesz mieć minimalne opóźnienie sieci między obrazami a wybranym środowiskiem wdrażania. Na przykład jeśli środowisko produkcyjne jest platforma Azure, prawdopodobnie chcesz przechowywać obrazy w [usłudze Azure Container Registry,](https://azure.microsoft.com/services/container-registry/) aby opóźnienie sieci było minimalne. Podobnie jeśli środowisko produkcyjne jest lokalne, można mieć lokalny rejestr zaufany platformy Docker dostępny w tej samej sieci lokalnej.

>[!div class="step-by-step"]
>[Poprzedni](docker-terminology.md)
>[następny](road-to-modern-applications-based-on-containers.md)
