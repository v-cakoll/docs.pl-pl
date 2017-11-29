---
title: "Kontenery docker, obrazy i rejestrów"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kontenery docker, obrazy i rejestrów"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="85b61-104">Kontenery docker, obrazy i rejestrów</span><span class="sxs-lookup"><span data-stu-id="85b61-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="85b61-105">Przy użyciu rozwiązania Docker, deweloper tworzy aplikację lub usługę i pakiety go i jego zależności w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="85b61-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="85b61-106">Obraz jest statyczny reprezentację aplikacji lub usługi i konfiguracji oraz zależności.</span><span class="sxs-lookup"><span data-stu-id="85b61-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="85b61-107">Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony, aby utworzyć kontener, który zostanie uruchomiona na hoście Docker.</span><span class="sxs-lookup"><span data-stu-id="85b61-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="85b61-108">Kontenery początkowo są testowane w środowisko projektowe lub komputera.</span><span class="sxs-lookup"><span data-stu-id="85b61-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="85b61-109">Deweloperzy należy przechowywać obrazów w rejestrze, który działa jako biblioteka obrazów, jest potrzebne podczas wdrażania orchestrators produkcji.</span><span class="sxs-lookup"><span data-stu-id="85b61-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="85b61-110">Docker przechowuje rejestr publiczny za pomocą [Centrum Docker](https://hub.docker.com/); innych dostawców Podaj rejestrów dla różnych kolekcji obrazów.</span><span class="sxs-lookup"><span data-stu-id="85b61-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="85b61-111">Alternatywnie przedsiębiorstwa mogą mieć prywatnych rejestru lokalnymi własnych obrazów Docker.</span><span class="sxs-lookup"><span data-stu-id="85b61-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="85b61-112">Rysunek 2-4 przedstawiono, jak obrazy i rejestrów w Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="85b61-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="85b61-113">Zawiera także wiele ofert rejestru od dostawców.</span><span class="sxs-lookup"><span data-stu-id="85b61-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="85b61-114">**Rysunek 2-4**.</span><span class="sxs-lookup"><span data-stu-id="85b61-114">**Figure 2-4**.</span></span> <span data-ttu-id="85b61-115">Taksonomii Docker terminy i pojęcia</span><span class="sxs-lookup"><span data-stu-id="85b61-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="85b61-116">Umieszczanie obrazów w rejestrze pozwala przechowywać bitów statycznych i modyfikować aplikacji, łącznie z ich zależności na poziomie framework.</span><span class="sxs-lookup"><span data-stu-id="85b61-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="85b61-117">Tych obrazów można następnie numerów wersji i wdrożone w wielu środowiskach i stanowić jednostki spójne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="85b61-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="85b61-118">Rejestrów prywatnej obrazu hostowanych lokalnie lub w chmurze, jest zalecana, gdy:</span><span class="sxs-lookup"><span data-stu-id="85b61-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="85b61-119">Obrazów nie może być udostępniany publicznie z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="85b61-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="85b61-120">Chcesz, aby minimalna sieci opóźnienia między obrazów i środowiska wdrażania wybrany.</span><span class="sxs-lookup"><span data-stu-id="85b61-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="85b61-121">Na przykład jeśli chmury Azure znajduje się w środowisku produkcyjnym, prawdopodobnie chcesz przechowywać obrazów w rejestrze kontenera platformy Azure, dzięki czemu jest minimalnego opóźnienia sieci.</span><span class="sxs-lookup"><span data-stu-id="85b61-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="85b61-122">W podobny sposób w przypadku środowiska produkcyjnego w infrastrukturze lokalnej, możesz mieć lokalnymi Docker zaufane rejestru dostępne w ramach tej samej sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="85b61-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="85b61-123">[Poprzednie] (docker-terminology.md) [dalej] (.. /NET-Core-NET-Framework-containers/index.MD)</span><span class="sxs-lookup"><span data-stu-id="85b61-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
