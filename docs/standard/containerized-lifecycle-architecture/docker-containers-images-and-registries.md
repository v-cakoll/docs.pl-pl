---
title: Kontenery platformy docker, obrazy i rejestry
description: Dowiedz się, kluczową rolę, że rejestrów odtworzyć ogólny w sposób platformy Docker, wdrażania aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a2e20e09561a5cc91aa29059fb8d19a14205bb5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221202"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="f6951-103">Kontenery platformy docker, obrazy i rejestry</span><span class="sxs-lookup"><span data-stu-id="f6951-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="f6951-104">Korzystając z platformy Docker, tworzenie aplikacji lub usługi i pakietu on i jego zależności do obrazu kontenera.</span><span class="sxs-lookup"><span data-stu-id="f6951-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="f6951-105">Obraz jest statyczny reprezentacja tych aplikacji lub usług i konfiguracji i zależności.</span><span class="sxs-lookup"><span data-stu-id="f6951-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="f6951-106">Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony do utworzenia kontenera, która zostanie uruchomiona na hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f6951-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="f6951-107">Kontenery są początkowo przetestowane w środowisku projektowym lub komputera.</span><span class="sxs-lookup"><span data-stu-id="f6951-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="f6951-108">Obrazy są przechowywane w rejestrze, która działa jako biblioteka obrazów.</span><span class="sxs-lookup"><span data-stu-id="f6951-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="f6951-109">Konieczne jest zarejestrowanie podczas wdrażania do produkcji koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="f6951-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="f6951-110">Docker przechowuje rejestru publicznego za pośrednictwem [usługi Docker Hub](https://hub.docker.com/); innych dostawców udostępnia rejestrów dla różnych kolekcji obrazów.</span><span class="sxs-lookup"><span data-stu-id="f6951-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="f6951-111">Alternatywnie przedsiębiorstwa mogą mieć prywatnego rejestru lokalnego do ich własnych obrazów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f6951-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="f6951-112">Rysunek 1 – 4 pokazano, jak obrazy i rejestry na platformie Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="f6951-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="f6951-113">Zawiera również wiele ofert rejestru od dostawców.</span><span class="sxs-lookup"><span data-stu-id="f6951-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="f6951-114">Rysunek 1-4: Taksonomia usługi Docker terminy i pojęcia</span><span class="sxs-lookup"><span data-stu-id="f6951-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="f6951-115">Umieszczając obrazów w rejestrze, można przechowywać bitów statyczne i niezmienne aplikacji, w tym wszystkie zależności, na poziomie framework.</span><span class="sxs-lookup"><span data-stu-id="f6951-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="f6951-116">Możesz następnie wersji i wdrożyć obrazy w wielu środowiskach i ten sposób zapewnia spójne wdrażanie jednostki.</span><span class="sxs-lookup"><span data-stu-id="f6951-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="f6951-117">Rejestry obrazów prywatnych, hostowanych lokalnie lub w chmurze, są zalecane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="f6951-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="f6951-118">Obrazów nie może być publicznie udostępniany z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="f6951-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="f6951-119">Chcesz mieć minimalne opóźnienie między obrazów i środowiska wdrażania wybranej.</span><span class="sxs-lookup"><span data-stu-id="f6951-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="f6951-120">Na przykład jeśli środowisko produkcyjne platformy Azure, prawdopodobnie chcesz przechowywać obrazy w usłudze Azure Container Registry tak, aby opóźnienia sieci minimalnej.</span><span class="sxs-lookup"><span data-stu-id="f6951-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="f6951-121">W podobny sposób w przypadku środowiska produkcyjnego w środowisku lokalnym, możesz chcieć mieć lokalną Docker Trusted Registry dostępne w ramach tej samej sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f6951-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f6951-122">[Poprzednie](docker-terminology.md)
>[dalej](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="f6951-122">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
