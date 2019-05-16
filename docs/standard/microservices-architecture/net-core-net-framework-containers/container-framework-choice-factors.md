---
title: Tabela decyzji. .NET Framework na potrzeby platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Tabela decyzji, .NET Framework na potrzeby platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639181"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="2507f-104">Tabela decyzji: korzystanie z programu .NET Framework z platformą Docker</span><span class="sxs-lookup"><span data-stu-id="2507f-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="2507f-105">W poniższej tabeli decyzji podsumowano, czy ma być używany program .NET Framework lub .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2507f-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="2507f-106">Należy pamiętać, że dla kontenerów systemu Linux, należy opartych na systemie Linux hostów platformy Docker (maszyn wirtualnych lub serwerach) i dla kontenerów Windows należy systemu Windows Server na podstawie hostów platformy Docker (maszyn wirtualnych lub serwerach).</span><span class="sxs-lookup"><span data-stu-id="2507f-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2507f-107">Rozwoju maszyny zostaną uruchomione jeden host platformy Docker, Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="2507f-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="2507f-108">Wszystkie powiązane mikrousług, który chcesz uruchomić i przetestować ze sobą w jednym rozwiązaniu będzie musiał ją uruchomić na tę samą platformę kontenerów.</span><span class="sxs-lookup"><span data-stu-id="2507f-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="2507f-109"><strong>Architektura / typ aplikacji</strong></span><span class="sxs-lookup"><span data-stu-id="2507f-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="2507f-110"><strong>Kontenery systemu Linux</strong></span><span class="sxs-lookup"><span data-stu-id="2507f-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="2507f-111"><strong>Kontenery Windows</strong></span><span class="sxs-lookup"><span data-stu-id="2507f-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="2507f-112">Mikrousług w kontenerach</span><span class="sxs-lookup"><span data-stu-id="2507f-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="2507f-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-113">.NET Core</span></span></td>
<td><span data-ttu-id="2507f-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2507f-115">Monolityczną aplikację</span><span class="sxs-lookup"><span data-stu-id="2507f-115">Monolithic app</span></span></td>
<td><span data-ttu-id="2507f-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="2507f-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-117">.NET Framework</span></span></p>
<p><span data-ttu-id="2507f-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2507f-119">Najlepsze w swojej klasie, wydajności i skalowalności</span><span class="sxs-lookup"><span data-stu-id="2507f-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="2507f-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-120">.NET Core</span></span></td>
<td><span data-ttu-id="2507f-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2507f-122">Migrowanie starszych aplikacji ("pole brown") systemu Windows Server do kontenerów</span><span class="sxs-lookup"><span data-stu-id="2507f-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="2507f-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2507f-124">Nowych wdrożeń opartych na kontenerach ("pole zielony")</span><span class="sxs-lookup"><span data-stu-id="2507f-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="2507f-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-125">.NET Core</span></span></td>
<td><span data-ttu-id="2507f-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2507f-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="2507f-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="2507f-129">.NET core (zalecane)</span><span class="sxs-lookup"><span data-stu-id="2507f-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="2507f-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2507f-131">ASP.NET 4 (MVC 5, Web API 2 i formularzy sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2507f-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="2507f-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2507f-133">Usługi SignalR</span><span class="sxs-lookup"><span data-stu-id="2507f-133">SignalR services</span></span></td>
<td><span data-ttu-id="2507f-134">.NET core 2.1 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="2507f-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="2507f-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-135">.NET Framework</span></span></p>
<p><span data-ttu-id="2507f-136">.NET core 2.1 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="2507f-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="2507f-137">Usługi WCF, WF i innych platform starszej wersji</span><span class="sxs-lookup"><span data-stu-id="2507f-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="2507f-138">Usługi WCF w programie .NET Core (tylko Biblioteka klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="2507f-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="2507f-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-139">.NET Framework</span></span></p>
<p><span data-ttu-id="2507f-140">Usługi WCF w programie .NET Core (tylko Biblioteka klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="2507f-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="2507f-141">Użycie usług platformy Azure</span><span class="sxs-lookup"><span data-stu-id="2507f-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="2507f-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-142">.NET Core</span></span></p>
<p><span data-ttu-id="2507f-143">(po pewnym czasie wszystkich usług platformy Azure zapewni client SDK dla platformy .NET Core)</span><span class="sxs-lookup"><span data-stu-id="2507f-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="2507f-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2507f-144">.NET Framework</span></span></p>
<p><span data-ttu-id="2507f-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2507f-145">.NET Core</span></span></p>
<p><span data-ttu-id="2507f-146">(po pewnym czasie wszystkich usług platformy Azure zapewni client SDK dla platformy .NET Core)</span><span class="sxs-lookup"><span data-stu-id="2507f-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="2507f-147">[Poprzednie](net-framework-container-scenarios.md)
>[dalej](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="2507f-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
