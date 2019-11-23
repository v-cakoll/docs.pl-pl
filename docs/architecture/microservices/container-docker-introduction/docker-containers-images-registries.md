---
title: Kontenery, obrazy i rejestry platformy Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Kontenery, obrazy i rejestry platformy Docker
ms.date: 08/31/2018
ms.openlocfilehash: 3b643a3bf4ca3ce1b8ba3fc40cd2f3ad8bbe5ffb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737770"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

W przypadku korzystania z platformy Docker deweloper tworzy aplikację lub usługę oraz umieszcza pakiety i ich zależności w obrazie kontenera. Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, zostanie utworzone wystąpienie obrazu aplikacji w celu utworzenia kontenera, który będzie działać na hoście platformy Docker. Kontenery są wstępnie testowane w środowisku deweloperskim lub komputerze.

Deweloperzy powinni przechowywać obrazy w rejestrze, który działa jako biblioteka obrazów i jest zbędny podczas wdrażania w programie Orchestrator produkcyjnych. Platforma Docker utrzymuje rejestr publiczny za pośrednictwem narzędzia [Docker Hub](https://hub.docker.com/). inni dostawcy dostarczają rejestry dla różnych kolekcji obrazów, w tym [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą lokalnie korzystać z prywatnego rejestru dla własnych obrazów platformy Docker.

Rysunek 2-4 pokazuje, jak obrazy i rejestry w Docker odnoszą się do innych składników. Przedstawiono w nim także oferty wielu rejestrów od dostawców.

![Diagram przedstawiający podstawową taksonomię w platformie Docker.](./media/docker-containers-images-registries/taxonomy-of-docker-terms-and-concepts.png)

**Rysunek 2-4**. Taksonomia warunków i koncepcji platformy Docker

Rejestr jest taki jak Bookshelf, gdzie obrazy są przechowywane i dostępne do kompilowania w celu tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web. Istnieją prywatne rejestry platformy Docker lokalnie i w chmurze publicznej. Usługa Docker Hub jest rejestrem publicznym obsługiwanym przez platformę Docker oraz z zaufanym rejestrem platformy Docker rozwiązanie klasy korporacyjnej, platforma Azure oferuje Azure Container Registry. AWS, Google i inne również mają rejestry kontenerów.

Umieszczenie obrazów w rejestrze umożliwia przechowywanie statycznych i niezmiennych bitów aplikacji, łącznie ze wszystkimi ich zależnościami na poziomie struktury. Te obrazy mogą następnie być w wersji i wdrożone w wielu środowiskach, a tym samym zapewnić spójną jednostkę wdrożenia.

Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane w przypadku:

- Obrazy nie mogą być udostępniane publicznie z powodu poufności.

- Potrzebujesz minimalnych opóźnień sieci między obrazami i wybranym środowiskiem wdrażania. Na przykład jeśli środowisko produkcyjne jest w chmurze platformy Azure, prawdopodobnie chcesz przechowywać obrazy w [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienie sieci było minimalne. W podobny sposób, jeśli środowisko produkcyjne działa lokalnie, w tej samej sieci lokalnej może być dostępny lokalny rejestr platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](docker-terminology.md)
>[Następny](../net-core-net-framework-containers/index.md)
