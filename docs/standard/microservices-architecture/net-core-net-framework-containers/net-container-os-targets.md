---
title: Jakiego systemu operacyjnego do docelowego z kontenerami .NET
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jakiego systemu operacyjnego do docelowego z kontenerami .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: fca5cf280d5abb85da78413a6eed463a2ffe6a88
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104882"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="19986-103">Jakiego systemu operacyjnego do docelowego z kontenerami .NET</span><span class="sxs-lookup"><span data-stu-id="19986-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="19986-104">Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez Docker i różnice między .NET Framework i .NET Core, docelowych określonego systemu operacyjnego i określonych wersji zależnie od używanego.</span><span class="sxs-lookup"><span data-stu-id="19986-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="19986-105">W systemie Windows można użyć systemu Windows Server Core lub serwerze Nano systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="19986-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="19986-106">Te wersje systemu Windows zawierają różne charakterystyki (usługi IIS w systemie Windows Server Core a serwerem sieci web hostowania samoobsługowego, takich jak Kestrel Nano Server), które mogą być wymagane odpowiednio przez .NET Framework lub .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19986-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="19986-107">Dla systemu Linux wiele dystrybucjach są dostępne i obsługiwane w oficjalnego obrazy usługi .NET Docker (na przykład Debian).</span><span class="sxs-lookup"><span data-stu-id="19986-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="19986-108">W rysunku 3-1 spowoduje możliwe wersji systemu operacyjnego, w zależności od używane w programie .NET framework.</span><span class="sxs-lookup"><span data-stu-id="19986-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="19986-109">**Rysunek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="19986-109">**Figure 3-1.**</span></span> <span data-ttu-id="19986-110">Systemy operacyjne, na docelowy w zależności od wersji programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="19986-110">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="19986-111">Można też utworzyć własny obraz Docker w przypadkach, której chcesz użyć innego distro Linux lub miejscu obrazu z wersji nie jest obsługiwane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="19986-111">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="19986-112">Na przykład może utworzyć obrazu z platformy ASP.NET Core systemem tradycyjne .NET Framework i Server Core systemu Windows, czyli scenariusza nie tak typowe dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="19986-112">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="19986-113">Nazwa obrazu należy dodać do pliku plik Dockerfile, można wybrać system operacyjny i wersję, w zależności od tag, którego używasz, na przykład:</span><span class="sxs-lookup"><span data-stu-id="19986-113">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="19986-114">Microsoft /**dotnet:2.1 — środowisko uruchomieniowe**</span><span class="sxs-lookup"><span data-stu-id="19986-114">microsoft/**dotnet:2.1-runtime**</span></span>

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   <span data-ttu-id="19986-115">Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe**</span><span class="sxs-lookup"><span data-stu-id="19986-115">microsoft/**dotnet:2.1-aspnetcore-runtime**</span></span>
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   <span data-ttu-id="19986-116">Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe-alpine**</span><span class="sxs-lookup"><span data-stu-id="19986-116">microsoft/**dotnet:2.1-aspnetcore-runtime-alpine**</span></span> 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   <span data-ttu-id="19986-117">Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe-nanoserver-1803**</span><span class="sxs-lookup"><span data-stu-id="19986-117">microsoft/**dotnet:2.1-aspnetcore-runtime-nanoserver-1803**</span></span> 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
<span data-ttu-id="19986-118">[Poprzednie](container-framework-choice-factors.md)
[dalej](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="19986-118">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
