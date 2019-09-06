---
title: Tabela decyzji. .NET Framework do użycia przez platformę Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Tabela decyzji, .NET Frameworks do użycia dla platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296535"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="a2b68-104">Tabela decyzji: korzystanie z programu .NET Framework z platformą Docker</span><span class="sxs-lookup"><span data-stu-id="a2b68-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="a2b68-105">Poniższa tabela decyzji zawiera podsumowanie, czy należy używać .NET Framework, czy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2b68-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="a2b68-106">Należy pamiętać, że w przypadku kontenerów systemu Linux wymagane są hosty platformy Docker oparte na systemie Linux (maszyny wirtualne lub serwery), które są wymagane w przypadku kontenerów platformy Docker opartych na programie Windows Server (maszyn wirtualnych lub serwerach).</span><span class="sxs-lookup"><span data-stu-id="a2b68-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2b68-107">Na maszynach deweloperskich zostanie uruchomiony jeden host platformy Docker (Linux lub Windows).</span><span class="sxs-lookup"><span data-stu-id="a2b68-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="a2b68-108">Powiązane mikrousługi, które mają zostać uruchomione i przetestowane razem w jednym rozwiązaniu, będą musiały działać na tej samej platformie kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a2b68-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="a2b68-109"><strong>Typ architektury/aplikacji</strong></span><span class="sxs-lookup"><span data-stu-id="a2b68-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="a2b68-110"><strong>Kontenery systemu Linux</strong></span><span class="sxs-lookup"><span data-stu-id="a2b68-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="a2b68-111"><strong>Kontenery systemu Windows</strong></span><span class="sxs-lookup"><span data-stu-id="a2b68-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="a2b68-112">Mikrousługi na kontenerach</span><span class="sxs-lookup"><span data-stu-id="a2b68-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="a2b68-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-113">.NET Core</span></span></td>
<td><span data-ttu-id="a2b68-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2b68-115">Aplikacja monolityczna</span><span class="sxs-lookup"><span data-stu-id="a2b68-115">Monolithic app</span></span></td>
<td><span data-ttu-id="a2b68-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="a2b68-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-117">.NET Framework</span></span></p>
<p><span data-ttu-id="a2b68-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2b68-119">Najlepsza w klasie wydajność i skalowalność</span><span class="sxs-lookup"><span data-stu-id="a2b68-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="a2b68-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-120">.NET Core</span></span></td>
<td><span data-ttu-id="a2b68-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2b68-122">Migracja starszej wersji systemu Windows Server ("brązowy-Field") do kontenerów</span><span class="sxs-lookup"><span data-stu-id="a2b68-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="a2b68-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2b68-124">Nowy projekt oparty na kontenerach ("zielony-pole")</span><span class="sxs-lookup"><span data-stu-id="a2b68-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="a2b68-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-125">.NET Core</span></span></td>
<td><span data-ttu-id="a2b68-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2b68-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="a2b68-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="a2b68-129">.NET Core (zalecane)</span><span class="sxs-lookup"><span data-stu-id="a2b68-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="a2b68-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2b68-131">ASP.NETe 4 (MVC 5, Web API 2 i Web Forms)</span><span class="sxs-lookup"><span data-stu-id="a2b68-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="a2b68-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2b68-133">Usługi sygnalizujące</span><span class="sxs-lookup"><span data-stu-id="a2b68-133">SignalR services</span></span></td>
<td><span data-ttu-id="a2b68-134">.NET Core 2,1 lub nowsza wersja</span><span class="sxs-lookup"><span data-stu-id="a2b68-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="a2b68-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-135">.NET Framework</span></span></p>
<p><span data-ttu-id="a2b68-136">.NET Core 2,1 lub nowsza wersja</span><span class="sxs-lookup"><span data-stu-id="a2b68-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="a2b68-137">WCF, WF i inne starsze platformy</span><span class="sxs-lookup"><span data-stu-id="a2b68-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="a2b68-138">WCF w programie .NET Core (tylko Biblioteka klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="a2b68-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="a2b68-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-139">.NET Framework</span></span></p>
<p><span data-ttu-id="a2b68-140">WCF w programie .NET Core (tylko Biblioteka klienta WCF)</span><span class="sxs-lookup"><span data-stu-id="a2b68-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="a2b68-141">Użycie usług platformy Azure</span><span class="sxs-lookup"><span data-stu-id="a2b68-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="a2b68-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-142">.NET Core</span></span></p>
<p><span data-ttu-id="a2b68-143">(ostatecznie wszystkie usługi platformy Azure będą dostarczać zestawy SDK klienta dla platformy .NET Core)</span><span class="sxs-lookup"><span data-stu-id="a2b68-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="a2b68-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2b68-144">.NET Framework</span></span></p>
<p><span data-ttu-id="a2b68-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2b68-145">.NET Core</span></span></p>
<p><span data-ttu-id="a2b68-146">(ostatecznie wszystkie usługi platformy Azure będą dostarczać zestawy SDK klienta dla platformy .NET Core)</span><span class="sxs-lookup"><span data-stu-id="a2b68-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="a2b68-147">[Poprzedni](net-framework-container-scenarios.md)Następny
>[](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="a2b68-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
