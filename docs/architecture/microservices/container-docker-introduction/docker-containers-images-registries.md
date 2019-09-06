---
title: Kontenery, obrazy i rejestry platformy Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Kontenery, obrazy i rejestry platformy Docker
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296200"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="e2f14-103">Kontenery, obrazy i rejestry platformy Docker</span><span class="sxs-lookup"><span data-stu-id="e2f14-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="e2f14-104">W przypadku korzystania z platformy Docker deweloper tworzy aplikację lub usługę oraz umieszcza pakiety i ich zależności w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="e2f14-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="e2f14-105">Obraz jest statyczną reprezentacją aplikacji lub usługi oraz jej konfiguracji i zależności.</span><span class="sxs-lookup"><span data-stu-id="e2f14-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="e2f14-106">Aby uruchomić aplikację lub usługę, zostanie utworzone wystąpienie obrazu aplikacji w celu utworzenia kontenera, który będzie działać na hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e2f14-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="e2f14-107">Kontenery są wstępnie testowane w środowisku deweloperskim lub komputerze.</span><span class="sxs-lookup"><span data-stu-id="e2f14-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="e2f14-108">Deweloperzy powinni przechowywać obrazy w rejestrze, który działa jako biblioteka obrazów i jest zbędny podczas wdrażania w programie Orchestrator produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="e2f14-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="e2f14-109">Platforma Docker utrzymuje rejestr publiczny za pośrednictwem narzędzia [Docker Hub](https://hub.docker.com/). inni dostawcy dostarczają rejestry dla różnych kolekcji obrazów, w tym [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="e2f14-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="e2f14-110">Alternatywnie przedsiębiorstwa mogą lokalnie korzystać z prywatnego rejestru dla własnych obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e2f14-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="e2f14-111">Rysunek 2-4 pokazuje, jak obrazy i rejestry w Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="e2f14-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="e2f14-112">Przedstawiono w nim także oferty wielu rejestrów od dostawców.</span><span class="sxs-lookup"><span data-stu-id="e2f14-112">It also shows the multiple registry offerings from vendors.</span></span>

![Taksonomia podstawowa w platformie Docker: Rejestr jest taki jak Bookshelf, gdzie obrazy są przechowywane i dostępne do kompilowania w celu tworzenia kontenerów do uruchamiania usług lub aplikacji sieci Web.](./media/image5.PNG)

<span data-ttu-id="e2f14-117">**Rysunek 2-4**.</span><span class="sxs-lookup"><span data-stu-id="e2f14-117">**Figure 2-4**.</span></span> <span data-ttu-id="e2f14-118">Taksonomia warunków i koncepcji platformy Docker</span><span class="sxs-lookup"><span data-stu-id="e2f14-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="e2f14-119">Umieszczenie obrazów w rejestrze umożliwia przechowywanie statycznych i niezmiennych bitów aplikacji, łącznie ze wszystkimi ich zależnościami na poziomie struktury.</span><span class="sxs-lookup"><span data-stu-id="e2f14-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="e2f14-120">Te obrazy mogą następnie być w wersji i wdrożone w wielu środowiskach, a tym samym zapewnić spójną jednostkę wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e2f14-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="e2f14-121">Prywatne rejestry obrazów, hostowane lokalnie lub w chmurze, są zalecane w przypadku:</span><span class="sxs-lookup"><span data-stu-id="e2f14-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="e2f14-122">Obrazy nie mogą być udostępniane publicznie z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="e2f14-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="e2f14-123">Potrzebujesz minimalnych opóźnień sieci między obrazami i wybranym środowiskiem wdrażania.</span><span class="sxs-lookup"><span data-stu-id="e2f14-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="e2f14-124">Na przykład jeśli środowisko produkcyjne jest w chmurze platformy Azure, prawdopodobnie chcesz przechowywać obrazy w [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienie sieci było minimalne.</span><span class="sxs-lookup"><span data-stu-id="e2f14-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="e2f14-125">W podobny sposób, jeśli środowisko produkcyjne działa lokalnie, w tej samej sieci lokalnej może być dostępny lokalny rejestr platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="e2f14-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e2f14-126">[Poprzedni](docker-terminology.md)Następny
>[](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="e2f14-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
