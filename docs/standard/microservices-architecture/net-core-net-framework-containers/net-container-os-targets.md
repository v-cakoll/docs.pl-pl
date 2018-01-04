---
title: Jakiego systemu operacyjnego do docelowego z kontenerami .NET
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jakiego systemu operacyjnego do docelowego z kontenerami .NET"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef7a21efa23be3a5181f08066a093abbb915c20f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="076fb-104">Jakiego systemu operacyjnego do docelowego z kontenerami .NET</span><span class="sxs-lookup"><span data-stu-id="076fb-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="076fb-105">Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez Docker i różnice między .NET Framework i .NET Core, docelowych określonego systemu operacyjnego i określonych wersji zależnie od używanego.</span><span class="sxs-lookup"><span data-stu-id="076fb-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="076fb-106">W systemie Windows można użyć systemu Windows Server Core lub serwerze Nano systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="076fb-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="076fb-107">Te wersje systemu Windows zawierają różne charakterystyki (usługi IIS w systemie Windows Server Core a serwerem sieci web hostowania samoobsługowego, takich jak Kestrel Nano Server), które mogą być wymagane odpowiednio przez .NET Framework lub .NET Core.</span><span class="sxs-lookup"><span data-stu-id="076fb-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="076fb-108">Dla systemu Linux wiele dystrybucjach są dostępne i obsługiwane w oficjalnego obrazy usługi .NET Docker (na przykład Debian).</span><span class="sxs-lookup"><span data-stu-id="076fb-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="076fb-109">W rysunku 3-1 spowoduje możliwe wersji systemu operacyjnego, w zależności od używane w programie .NET framework.</span><span class="sxs-lookup"><span data-stu-id="076fb-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="076fb-110">**Rysunek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="076fb-110">**Figure 3-1.**</span></span> <span data-ttu-id="076fb-111">Systemy operacyjne, na docelowy w zależności od wersji programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="076fb-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="076fb-112">Można też utworzyć własny obraz Docker w przypadkach, której chcesz użyć innego distro Linux lub miejscu obrazu z wersji nie jest obsługiwane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="076fb-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="076fb-113">Na przykład może utworzyć obrazu z platformy ASP.NET Core systemem tradycyjne .NET Framework i Server Core systemu Windows, czyli scenariusza nie tak typowe dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="076fb-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="076fb-114">Nazwa obrazu należy dodać do pliku plik Dockerfile, można wybrać system operacyjny i wersję, w zależności od tag, którego używasz, na przykład:</span><span class="sxs-lookup"><span data-stu-id="076fb-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="076fb-115">Microsoft /**dotnet:2.0.0 — środowisko uruchomieniowe-Joasia**</span><span class="sxs-lookup"><span data-stu-id="076fb-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="076fb-116">Microsoft /**dotnet:2.0.0 — środowisko uruchomieniowe-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="076fb-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="076fb-117">Microsoft /**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="076fb-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="076fb-118">[Poprzednie] (kontener framework wybór factors.md) [dalej] (oficjalne net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="076fb-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
