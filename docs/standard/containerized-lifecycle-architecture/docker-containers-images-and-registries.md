---
title: Kontenery docker, obrazy i rejestrów
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 43b76f738fa4b7c89423a5b9fac7ef91f40880c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="97a72-103">Kontenery docker, obrazy i rejestrów</span><span class="sxs-lookup"><span data-stu-id="97a72-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="97a72-104">Korzystając z Docker, tworzenia aplikacji lub usługi i pakietu go i jego zależności w obrazie kontenera.</span><span class="sxs-lookup"><span data-stu-id="97a72-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="97a72-105">Obraz jest statyczny reprezentację aplikacji lub usługi i konfiguracji oraz zależności.</span><span class="sxs-lookup"><span data-stu-id="97a72-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="97a72-106">Aby uruchomić aplikację lub usługę, obraz aplikacji zostanie uruchomiony, aby utworzyć kontener, który zostanie uruchomiona na hoście Docker.</span><span class="sxs-lookup"><span data-stu-id="97a72-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="97a72-107">Kontenery początkowo są testowane w środowisko projektowe lub komputera.</span><span class="sxs-lookup"><span data-stu-id="97a72-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="97a72-108">Obrazy są przechowywane w rejestrze, która działa jako biblioteki obrazów.</span><span class="sxs-lookup"><span data-stu-id="97a72-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="97a72-109">Konieczne jest zarejestrowanie podczas wdrażania orchestrators produkcji.</span><span class="sxs-lookup"><span data-stu-id="97a72-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="97a72-110">Docker przechowuje rejestr publiczny za pomocą [Centrum Docker](https://hub.docker.com/); innych dostawców Podaj rejestrów dla różnych kolekcji obrazów.</span><span class="sxs-lookup"><span data-stu-id="97a72-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="97a72-111">Alternatywnie przedsiębiorstwa mogą mieć prywatnych rejestru lokalnymi własnych obrazów Docker.</span><span class="sxs-lookup"><span data-stu-id="97a72-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="97a72-112">Rysunek 1-4 przedstawiono, jak obrazy i rejestrów w Docker odnoszą się do innych składników.</span><span class="sxs-lookup"><span data-stu-id="97a72-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="97a72-113">Zawiera także wiele ofert rejestru od dostawców.</span><span class="sxs-lookup"><span data-stu-id="97a72-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="97a72-114">Rysunek 1-4 taksonomii Docker terminy i pojęcia</span><span class="sxs-lookup"><span data-stu-id="97a72-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="97a72-115">Umieszczenie obrazów w rejestrze, można przechowywać bitów statycznych i modyfikować aplikacji, w tym wszystkie ich zależności na poziomie framework.</span><span class="sxs-lookup"><span data-stu-id="97a72-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="97a72-116">Możesz następnie można wersji i wdrażania obrazów w środowiskach wielu i w związku z tym jednostki spójne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="97a72-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="97a72-117">Rejestry prywatnej obrazu obsługiwanego lokalnie lub w chmurze, zaleca się w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="97a72-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="97a72-118">Obrazów nie może być udostępniany publicznie z powodu poufności.</span><span class="sxs-lookup"><span data-stu-id="97a72-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="97a72-119">Chcesz, aby minimalna sieci opóźnienia między obrazów i środowiska wdrażania wybrany.</span><span class="sxs-lookup"><span data-stu-id="97a72-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="97a72-120">Na przykład jeśli Azure znajduje się w środowisku produkcyjnym, prawdopodobnie chcesz przechowywać obrazów w rejestrze kontenera platformy Azure, dzięki czemu jest minimalnego opóźnienia sieci.</span><span class="sxs-lookup"><span data-stu-id="97a72-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="97a72-121">W podobny sposób w przypadku środowiska produkcyjnego w infrastrukturze lokalnej, możesz mieć lokalnymi Docker zaufane rejestru dostępne w ramach tej samej sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="97a72-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="97a72-122">[Poprzednie] (docker-terminology.md) [dalej] (Docker aplikacji-cyklu życia/index.md)</span><span class="sxs-lookup"><span data-stu-id="97a72-122">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
