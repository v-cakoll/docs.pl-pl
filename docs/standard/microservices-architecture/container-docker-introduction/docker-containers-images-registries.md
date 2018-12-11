---
title: Kontenery platformy docker, obrazy i rejestry
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Kontenery platformy docker, obrazy i rejestry
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: f10d7d03bbf88ed8f7a89a5d3919a39b3c124ae0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130237"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="2977f-103">Kontenery platformy docker, obrazy i rejestry</span><span class="sxs-lookup"><span data-stu-id="2977f-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="2977f-104">Korzystając z platformy Docker, deweloper tworzy i pakiety aplikacji lub usługi, on i jego zależności do obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="2977f-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="2977f-105">Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.</span><span class="sxs-lookup"><span data-stu-id="2977f-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="2977f-106">Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2977f-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="2977f-107">Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.</span><span class="sxs-lookup"><span data-stu-id="2977f-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="2977f-108">Deweloperzy należy przechowywać obrazy w rejestrze, który działa jako biblioteka obrazów i nie jest wymagana podczas wdrażania do produkcji koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="2977f-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="2977f-109">Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców zapewnienia różne kolekcje obrazów, włącznie z rejestrami [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="2977f-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="2977f-110">Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2977f-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="2977f-111">Rysunek 2 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="2977f-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="2977f-112">Zawiera również wiele ofert rejestru od dostawców.</span><span class="sxs-lookup"><span data-stu-id="2977f-112">It also shows the multiple registry offerings from vendors.</span></span>

![Podstawowe Taksonomia na platformie Docker: Rejestr przypomina bookshelf, w którym obrazy są przechowywane i dostępny do ściągnięcia do tworzenia kontenerów do uruchamiania usługi lub aplikacji sieci web.](./media/image5.PNG)

<span data-ttu-id="2977f-117">**Rysunek 2 – 4**.</span><span class="sxs-lookup"><span data-stu-id="2977f-117">**Figure 2-4**.</span></span> <span data-ttu-id="2977f-118">Taksonomia usługi Docker terminy i pojęcia</span><span class="sxs-lookup"><span data-stu-id="2977f-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="2977f-119">Umieszczenie obrazów w rejestrze pozwala przechowywać bitów statyczne i niezmienne aplikacji, wraz ze wszystkimi jego zależnościami na poziomie framework.</span><span class="sxs-lookup"><span data-stu-id="2977f-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="2977f-120">Tych obrazów może następnie być wersjonowane i wdrażane w wielu środowiskach i stanowić jednostki spójne wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="2977f-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="2977f-121">Rejestry obrazu prywatnego albo hostowanych lokalnie lub w chmurze, są zalecane, gdy:</span><span class="sxs-lookup"><span data-stu-id="2977f-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="2977f-122">Obrazów nie może być publicznie udostępniany z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="2977f-122">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="2977f-123">Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej.</span><span class="sxs-lookup"><span data-stu-id="2977f-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="2977f-124">Na przykład, jeśli środowisko produkcyjne platformy Azure w chmurze, prawdopodobnie chcesz przechowywać obrazy w [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienia sieci minimalnej.</span><span class="sxs-lookup"><span data-stu-id="2977f-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="2977f-125">W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2977f-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2977f-126">[Poprzednie](docker-terminology.md)
>[dalej](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="2977f-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>