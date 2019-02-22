---
title: Kontenery platformy docker, obrazy i rejestry
description: Dowiedz się, kluczową rolę, że rejestrów odtworzyć ogólny w sposób platformy Docker, wdrażania aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e69490734a03cf58bf8534bc9e31110a11d44c58
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583319"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="b561f-103">Kontenery platformy docker, obrazy i rejestry</span><span class="sxs-lookup"><span data-stu-id="b561f-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="b561f-104">Korzystając z platformy Docker, tworzenie aplikacji lub usługi i pakietu on i jego zależności do obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="b561f-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="b561f-105">Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.</span><span class="sxs-lookup"><span data-stu-id="b561f-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="b561f-106">Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b561f-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="b561f-107">Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.</span><span class="sxs-lookup"><span data-stu-id="b561f-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="b561f-108">Obrazy są przechowywane w rejestrze, która działa jako biblioteka obrazów.</span><span class="sxs-lookup"><span data-stu-id="b561f-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="b561f-109">Konieczne jest zarejestrowanie podczas wdrażania do produkcji koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="b561f-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="b561f-110">Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców zapewnienia różne kolekcje obrazów, włącznie z rejestrami [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="b561f-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="b561f-111">Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="b561f-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="b561f-112">Rysunek 1 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="b561f-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="b561f-113">Zawiera również wiele ofert rejestru od dostawców.</span><span class="sxs-lookup"><span data-stu-id="b561f-113">It also shows the multiple registry offerings from vendors.</span></span>

![Podstawowe Taksonomia na platformie Docker: Rejestr przypomina bookshelf, w którym obrazy są przechowywane i dostępny do ściągnięcia do tworzenia kontenerów do uruchamiania usługi lub aplikacji sieci web.](./media/image4.png)

<span data-ttu-id="b561f-118">**Rysunek 1 – 4**.</span><span class="sxs-lookup"><span data-stu-id="b561f-118">**Figure 1-4**.</span></span> <span data-ttu-id="b561f-119">Taksonomia usługi Docker terminy i pojęcia</span><span class="sxs-lookup"><span data-stu-id="b561f-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="b561f-120">Umieszczając obrazów w rejestrze, można przechowywać bitów statyczne i niezmienne aplikacji, w tym wszystkie zależności, na poziomie framework.</span><span class="sxs-lookup"><span data-stu-id="b561f-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="b561f-121">Możesz następnie wersji i wdrożyć obrazy w wielu środowiskach i ten sposób zapewnia spójne wdrażanie jednostki.</span><span class="sxs-lookup"><span data-stu-id="b561f-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="b561f-122">Rejestry obrazu prywatnego albo hostowanych lokalnie lub w chmurze, są zalecane, gdy:</span><span class="sxs-lookup"><span data-stu-id="b561f-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="b561f-123">Obrazów nie może być publicznie udostępniany z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="b561f-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="b561f-124">Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej.</span><span class="sxs-lookup"><span data-stu-id="b561f-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="b561f-125">Na przykład, jeśli środowisko produkcyjne platformy Azure, prawdopodobnie chcesz przechowywać swoje obrazy w [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry/) tak, aby opóźnienia sieci jest minimalny.</span><span class="sxs-lookup"><span data-stu-id="b561f-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="b561f-126">W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b561f-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b561f-127">[Poprzednie](docker-terminology.md)
>[dalej](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="b561f-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
