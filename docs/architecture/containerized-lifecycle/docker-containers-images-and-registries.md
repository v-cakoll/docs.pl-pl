---
title: Kontenery, obrazy i rejestry platformy Docker
description: Poznaj rolę klucza, którą rejestry odgrywają ogólnie w programie Docker w celu wdrożenia aplikacji.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295659"
---
# <a name="docker-containers-images-and-registries"></a>Kontenery, obrazy i rejestry platformy Docker

W przypadku korzystania z platformy Docker można utworzyć aplikację lub usługę oraz spakować ją wraz z jej zależnościami na obraz kontenera. Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.

Aby uruchomić aplikację lub usługę, zostanie utworzone wystąpienie obrazu aplikacji w celu utworzenia kontenera, który będzie działać na hoście platformy Docker. Kontenery są wstępnie testowane w środowisku deweloperskim lub komputerze.

Obrazy są przechowywane w rejestrze, który działa jako biblioteka obrazów. W przypadku wdrażania w programie Orchestrator w środowisku produkcyjnym potrzebny jest rejestr. Platforma Docker utrzymuje rejestr publiczny za pośrednictwem narzędzia [Docker Hub](https://hub.docker.com/). inni dostawcy dostarczają rejestry dla różnych kolekcji obrazów, w tym [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Alternatywnie przedsiębiorstwa mogą lokalnie korzystać z prywatnego rejestru dla własnych obrazów platformy Docker.

Rysunek 1-4 pokazuje, jak obrazy i rejestry w Docker odnoszą się do innych składników. Przedstawiono w nim także oferty wielu rejestrów od dostawców.

![Taksonomia podstawowa w platformie Docker: Rejestr jest taki jak Bookshelf, gdzie obrazy są przechowywane i dostępne do kompilowania w celu tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web. Istnieją prywatne rejestry platformy Docker lokalnie i w chmurze publicznej. Usługa Docker Hub jest rejestrem publicznym obsługiwanym przez platformę Docker oraz z zaufanym rejestrem platformy Docker rozwiązanie klasy korporacyjnej, platforma Azure oferuje Azure Container Registry. AWS, Google i inne również mają rejestry kontenerów.](./media/image4.png)

**Rysunek 1-4**. Taksonomia warunków i koncepcji platformy Docker

Umieszczając obrazy w rejestrze, można przechowywać statyczne i niezmienne bity aplikacji, w tym wszystkie ich zależności, na poziomie platformy. Następnie można zainstalować i wdrożyć obrazy w wielu środowiskach, a tym samym zapewnić spójną jednostkę wdrożenia.

Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane w przypadku:

- Obrazy nie mogą być udostępniane publicznie z powodu poufności.

- Potrzebujesz minimalnych opóźnień sieci między obrazami i wybranym środowiskiem wdrażania. Na przykład jeśli środowisko produkcyjne jest platformą Azure, prawdopodobnie chcesz przechowywać obrazy w [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienie sieci było minimalne. W podobny sposób, jeśli środowisko produkcyjne działa lokalnie, w tej samej sieci lokalnej może być dostępny lokalny rejestr platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](docker-terminology.md)Następny
>[](road-to-modern-applications-based-on-containers.md)
