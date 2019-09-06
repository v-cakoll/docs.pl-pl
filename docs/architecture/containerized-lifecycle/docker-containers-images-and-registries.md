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
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="33996-103">Kontenery, obrazy i rejestry platformy Docker</span><span class="sxs-lookup"><span data-stu-id="33996-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="33996-104">W przypadku korzystania z platformy Docker można utworzyć aplikację lub usługę oraz spakować ją wraz z jej zależnościami na obraz kontenera.</span><span class="sxs-lookup"><span data-stu-id="33996-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="33996-105">Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.</span><span class="sxs-lookup"><span data-stu-id="33996-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="33996-106">Aby uruchomić aplikację lub usługę, zostanie utworzone wystąpienie obrazu aplikacji w celu utworzenia kontenera, który będzie działać na hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="33996-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="33996-107">Kontenery są wstępnie testowane w środowisku deweloperskim lub komputerze.</span><span class="sxs-lookup"><span data-stu-id="33996-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="33996-108">Obrazy są przechowywane w rejestrze, który działa jako biblioteka obrazów.</span><span class="sxs-lookup"><span data-stu-id="33996-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="33996-109">W przypadku wdrażania w programie Orchestrator w środowisku produkcyjnym potrzebny jest rejestr.</span><span class="sxs-lookup"><span data-stu-id="33996-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="33996-110">Platforma Docker utrzymuje rejestr publiczny za pośrednictwem narzędzia [Docker Hub](https://hub.docker.com/). inni dostawcy dostarczają rejestry dla różnych kolekcji obrazów, w tym [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="33996-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="33996-111">Alternatywnie przedsiębiorstwa mogą lokalnie korzystać z prywatnego rejestru dla własnych obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="33996-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="33996-112">Rysunek 1-4 pokazuje, jak obrazy i rejestry w Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="33996-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="33996-113">Przedstawiono w nim także oferty wielu rejestrów od dostawców.</span><span class="sxs-lookup"><span data-stu-id="33996-113">It also shows the multiple registry offerings from vendors.</span></span>

![Taksonomia podstawowa w platformie Docker: Rejestr jest taki jak Bookshelf, gdzie obrazy są przechowywane i dostępne do kompilowania w celu tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web.](./media/image4.png)

<span data-ttu-id="33996-118">**Rysunek 1-4**.</span><span class="sxs-lookup"><span data-stu-id="33996-118">**Figure 1-4**.</span></span> <span data-ttu-id="33996-119">Taksonomia warunków i koncepcji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="33996-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="33996-120">Umieszczając obrazy w rejestrze, można przechowywać statyczne i niezmienne bity aplikacji, w tym wszystkie ich zależności, na poziomie platformy.</span><span class="sxs-lookup"><span data-stu-id="33996-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="33996-121">Następnie można zainstalować i wdrożyć obrazy w wielu środowiskach, a tym samym zapewnić spójną jednostkę wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="33996-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="33996-122">Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane w przypadku:</span><span class="sxs-lookup"><span data-stu-id="33996-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="33996-123">Obrazy nie mogą być udostępniane publicznie z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="33996-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="33996-124">Potrzebujesz minimalnych opóźnień sieci między obrazami i wybranym środowiskiem wdrażania.</span><span class="sxs-lookup"><span data-stu-id="33996-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="33996-125">Na przykład jeśli środowisko produkcyjne jest platformą Azure, prawdopodobnie chcesz przechowywać obrazy w [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienie sieci było minimalne.</span><span class="sxs-lookup"><span data-stu-id="33996-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="33996-126">W podobny sposób, jeśli środowisko produkcyjne działa lokalnie, w tej samej sieci lokalnej może być dostępny lokalny rejestr platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="33996-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="33996-127">[Poprzedni](docker-terminology.md)Następny
>[](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="33996-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
