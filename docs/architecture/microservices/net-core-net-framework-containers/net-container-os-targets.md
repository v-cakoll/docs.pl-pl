---
title: Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | System operacyjny, który ma być przeznaczony dla kontenerów platformy .NET
ms.date: 01/07/2019
ms.openlocfilehash: 7380889374e69ca4d3c981a401af703c19263de5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039691"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="f9461-103">Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET</span><span class="sxs-lookup"><span data-stu-id="f9461-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="f9461-104">Mając na względy różnorodność systemów operacyjnych obsługiwanych przez platformę Docker i różnice między .NET Framework i .NET Core, należy wskazać określony system operacyjny i konkretne wersje w zależności od używanej platformy.</span><span class="sxs-lookup"><span data-stu-id="f9461-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="f9461-105">W przypadku systemu Windows można użyć systemu Windows Server Core lub Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="f9461-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="f9461-106">Te wersje systemu Windows zapewniają różne cechy (IIS w systemie Windows Server Core oraz samodzielny serwer sieci Web, taki jak Kestrel na serwerze nano Server), który może być odpowiednio wymagany przez .NET Framework lub .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9461-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="f9461-107">W przypadku systemu Linux dostępne są wiele dystrybucje i są obsługiwane w oficjalnych obrazach platformy Docker .NET (na przykład Debian).</span><span class="sxs-lookup"><span data-stu-id="f9461-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="f9461-108">Na rysunku 3-1 można zobaczyć ewentualną wersję systemu operacyjnego w zależności od używanego programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9461-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![W przypadku wdrażania starszych aplikacji .NET Framework musisz mieć system Windows Server Core, który jest zgodny ze starszymi aplikacjami i usługami IIS, ma większy obraz.](./media/image1.png)

<span data-ttu-id="f9461-113">**Rysunek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="f9461-113">**Figure 3-1.**</span></span> <span data-ttu-id="f9461-114">Systemy operacyjne przeznaczone do celów w zależności od wersji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9461-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="f9461-115">Możesz również utworzyć własny obraz platformy Docker w przypadku, gdy chcesz użyć innego dystrybucji systemu Linux lub jeśli chcesz, aby obraz z wersjami nie został dostarczony przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f9461-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="f9461-116">Można na przykład utworzyć obraz z ASP.NET Core uruchomionym na tradycyjnych .NET Framework i Windows Server Core, który jest scenariuszem nietypowym dla platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f9461-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="f9461-117">Po dodaniu nazwy obrazu do pliku pliku dockerfile można wybrać system operacyjny i wersję w zależności od użytego tagu, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="f9461-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="f9461-118">Obraz</span><span class="sxs-lookup"><span data-stu-id="f9461-118">Image</span></span> | <span data-ttu-id="f9461-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="f9461-119">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="f9461-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="f9461-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span> | <span data-ttu-id="f9461-121">Architektura .NET Core 2,2: Obsługuje systemy Linux i Windows nano Server w zależności od hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f9461-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="f9461-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="f9461-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span> | <span data-ttu-id="f9461-123">Obsługa wieloarchitektur ASP.NET Core 2,2: Obsługuje systemy Linux i Windows nano Server w zależności od hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="f9461-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="f9461-124">Obraz aspnetcore ma kilka optymalizacji dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9461-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="f9461-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="f9461-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span> | <span data-ttu-id="f9461-126">Środowisko uruchomieniowe programu .NET Core 2,2 — tylko w systemie Linux Alpine dystrybucji</span><span class="sxs-lookup"><span data-stu-id="f9461-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span> |
| <span data-ttu-id="f9461-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="f9461-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span> | <span data-ttu-id="f9461-128">Środowisko uruchomieniowe programu .NET Core 2,2 — tylko w systemie Windows nano Server (system Windows Server w wersji 1803)</span><span class="sxs-lookup"><span data-stu-id="f9461-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span> |

> [!div class="step-by-step"]
> <span data-ttu-id="f9461-129">[Poprzedni](container-framework-choice-factors.md)Następny
> [](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="f9461-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
