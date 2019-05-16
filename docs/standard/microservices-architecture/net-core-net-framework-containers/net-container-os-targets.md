---
title: Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Jakiego systemu operacyjnego docelowo z kontenerami .NET
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639083"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="08def-103">Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET</span><span class="sxs-lookup"><span data-stu-id="08def-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="08def-104">Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez firmy Docker i różnice między .NET Framework i .NET Core, powinien dotyczyć określonego systemu operacyjnego i określonych wersji, w zależności od tego, w ramach, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="08def-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="08def-105">Dla Windows można użyć systemu Windows Server Core lub Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="08def-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="08def-106">Te wersje Windows zawierają różne charakterystyki (usługi IIS w systemie Windows Server Core i server samodzielnie hostowanej sieci web, takich jak Kestrel w systemie Nano Server), które mogą być wymagane przez program .NET Framework lub .NET Core, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="08def-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="08def-107">W przypadku systemu Linux dystrybucje wielu są dostępne i jest obsługiwany w oficjalne obrazy Docker w programie .NET (na przykład Debian).</span><span class="sxs-lookup"><span data-stu-id="08def-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="08def-108">W rysunek 3-1 można zobaczyć możliwe wersji systemu operacyjnego, w zależności od programu .NET framework używane.</span><span class="sxs-lookup"><span data-stu-id="08def-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Podczas wdrażania starszych aplikacji .NET Framework ma pod kątem systemu Windows Server Core, zgodne ze starszych aplikacji i usług IIS, ma większy obraz.](./media/image1.png)

<span data-ttu-id="08def-113">**Rysunek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="08def-113">**Figure 3-1.**</span></span> <span data-ttu-id="08def-114">Systemy operacyjne pod kątem w zależności od wersji programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="08def-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="08def-115">Można również utworzyć obraz platformy Docker w przypadkach, gdzie chcesz użyć innego dystrybucja systemu Linux lub którego obraz z wersjami, które nie są obsługiwane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="08def-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="08def-116">Na przykład utworzyć obraz przy użyciu platformy ASP.NET Core uruchomionych na tradycyjnych .NET Framework i systemie Windows Server Core, która jest nie tak typowe platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="08def-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="08def-117">Po dodaniu nazwy obrazu do pliku Dockerfile, można wybrać system operacyjny i wersję, w zależności od tag, którego używasz, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="08def-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="08def-118">Obraz</span><span class="sxs-lookup"><span data-stu-id="08def-118">Image</span></span></th>
<th><span data-ttu-id="08def-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="08def-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="08def-120">MCR.microsoft.com/DotNet/Core/Runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="08def-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span></td>
<td><span data-ttu-id="08def-121">Architektura wielu platformy .NET core 2.2: Obsługa systemu Linux i Windows Nano Server, w zależności od hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="08def-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="08def-122">MCR.microsoft.com/DotNet/Core/ASPNET:2.2</span><span class="sxs-lookup"><span data-stu-id="08def-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span></td>
<td><p><span data-ttu-id="08def-123">Architektura wielu platformy ASP.NET Core 2.2: Obsługa systemu Linux i Windows Nano Server, w zależności od hosta platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="08def-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="08def-124">Obraz aspnetcore ma kilka optymalizacji dla platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="08def-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="08def-125">MCR.microsoft.com/DotNet/Core/ASPNET:2.2-Alpine</span><span class="sxs-lookup"><span data-stu-id="08def-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span></td>
<td><span data-ttu-id="08def-126">.NET core 2.2 tylko do środowiska uruchomieniowego na Alpine dystrybucja systemu Linux</span><span class="sxs-lookup"><span data-stu-id="08def-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="08def-127">MCR.microsoft.com/DotNet/Core/ASPNET:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="08def-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span></td>
<td><span data-ttu-id="08def-128">.NET core 2.2 tylko do środowiska uruchomieniowego na serwerze Windows Nano Server (Windows Server w wersji 1803)</span><span class="sxs-lookup"><span data-stu-id="08def-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> <span data-ttu-id="08def-129">[Poprzednie](container-framework-choice-factors.md)
> [dalej](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="08def-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
