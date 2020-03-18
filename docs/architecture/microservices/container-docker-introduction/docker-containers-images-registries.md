---
title: Kontenery, obrazy i rejestry platformy Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Kontenery docker, obrazy i rejestry
ms.date: 08/31/2018
ms.openlocfilehash: 3b643a3bf4ca3ce1b8ba3fc40cd2f3ad8bbe5ffb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73737770"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

Korzystając z platformy Docker, deweloper tworzy aplikację lub usługę i pakuje ją i jego zależności do obrazu kontenera. Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, obraz aplikacji jest tworzony w celu utworzenia kontenera, który będzie uruchomiony na hoście platformy Docker. Kontenery są początkowo testowane w środowisku programistycznym lub komputerze.

Deweloperzy powinni przechowywać obrazy w rejestrze, który działa jako biblioteka obrazów i jest potrzebny podczas wdrażania do koordynatorów produkcji. Platforma Docker utrzymuje rejestr publiczny za pośrednictwem [centrum docker;](https://hub.docker.com/) inni dostawcy udostępniają rejestry dla różnych kolekcji obrazów, w tym [rejestru kontenerów azure](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą mieć prywatny rejestr lokalnie dla własnych obrazów platformy Docker.

Rysunek 2-4 pokazuje, jak obrazy i rejestry w platformie Docker odnoszą się do innych składników. Pokazuje również wiele ofert rejestru od dostawców.

![Diagram przedstawiający taksonomię podstawową w platformie Docker.](./media/docker-containers-images-registries/taxonomy-of-docker-terms-and-concepts.png)

**Rysunek 2-4**. Taksonomia terminów i koncepcji platformy Docker

Rejestr jest jak półka, na której obrazy są przechowywane i dostępne do ściągnięcia do tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web. Istnieją prywatne rejestry platformy Docker lokalnie i w chmurze publicznej. Docker Hub to rejestr publiczny obsługiwany przez platformę Docker, wzdłuż zaufanego rejestru platformy Docker, rozwiązanie klasy korporacyjnej, platforma Azure oferuje rejestr kontenerów platformy Azure. AWS, Google i inni mają również rejestry kontenerów.

Umieszczanie obrazów w rejestrze umożliwia przechowywanie statycznych i niezmiennych bitów aplikacji, w tym wszystkich ich zależności na poziomie struktury. Te obrazy mogą być następnie wersjonowane i wdrażane w wielu środowiskach i w związku z tym zapewniają spójną jednostkę wdrażania.

Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane, gdy:

- Twoje zdjęcia nie mogą być udostępniane publicznie ze względu na poufność.

- Chcesz mieć minimalne opóźnienie sieci między obrazami a wybranym środowiskiem wdrażania. Na przykład jeśli środowisko produkcyjne jest chmura platformy Azure, prawdopodobnie chcesz przechowywać obrazy w [usłudze Azure Container Registry,](https://azure.microsoft.com/services/container-registry/) aby opóźnienie sieci było minimalne. Podobnie jeśli środowisko produkcyjne jest lokalne, można mieć lokalny rejestr zaufany platformy Docker dostępny w tej samej sieci lokalnej.

>[!div class="step-by-step"]
>[Poprzedni](docker-terminology.md)
>[następny](../net-core-net-framework-containers/index.md)
