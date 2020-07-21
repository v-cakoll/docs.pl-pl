---
title: Niezawodność
description: Informacje o niezawodności w programie .NET. Ochrona przed wyjątkami asynchronicznymi w hostach wykonywanych w programie .NET, takich jak SQL Server.
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: ce9ffbb7f58c2f5dc016c56c0e2ce13b45c30f26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474257"
---
# <a name="reliability"></a><span data-ttu-id="70c39-104">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="70c39-104">Reliability</span></span>
<span data-ttu-id="70c39-105">Ważne jest, aby kod wykonywany w środowiskach serwerów, takich jak SQL Server chronić przed wyjątkami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="70c39-105">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="70c39-106">Niezawodność, zgodnie z opisem w tym miejscu, nie jest specyficzna dla SQL Server, ale do pisania niezawodnego kodu dla dowolnego hosta wykonywanego w środowisku .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="70c39-106">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="70c39-107">Jednak SQL Server to pierwsza usługa, która korzysta z nowych funkcji zapewniających niezawodność w wersji 2,0, więc jest używana jako przykład.</span><span class="sxs-lookup"><span data-stu-id="70c39-107">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="70c39-108">Kod działający w SQL Server musi obsłużyć bardziej rygorystyczne wytyczne dotyczące niezawodności niż inne środowiska serwera.</span><span class="sxs-lookup"><span data-stu-id="70c39-108">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="70c39-109">Jest to spowodowane ciągłą operacją SQL Server na granicy zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="70c39-109">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="70c39-110"><xref:System.OutOfMemoryException>i <xref:System.Threading.ThreadAbortException> wyjątki nie są rzadko w środowisku SQL serverm.</span><span class="sxs-lookup"><span data-stu-id="70c39-110"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="70c39-111">Ogólnie rzecz biorąc, te wytyczne mają mniej informacji na temat niezawodności i więcej na umożliwienie w pełni zaufanego kodu zarządzanego, aby zapewnić bezproblemowy niepowodzenie podczas <xref:System.AppDomain> odtwarzania, który jest głównym sposobem, w jaki serwer utrzymuje spójność i dostępność.</span><span class="sxs-lookup"><span data-stu-id="70c39-111">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70c39-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="70c39-112">In This Section</span></span>  
 [<span data-ttu-id="70c39-113">Atrybuty ochrony hosta i programowanie SQL Server</span><span class="sxs-lookup"><span data-stu-id="70c39-113">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="70c39-114">Opisuje, w jaki sposób <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest używany przez SQL Server w celu ograniczenia wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="70c39-114">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="70c39-115">Najlepsze rozwiązania dotyczące niezawodności</span><span class="sxs-lookup"><span data-stu-id="70c39-115">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="70c39-116">Zawiera wytyczne dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.</span><span class="sxs-lookup"><span data-stu-id="70c39-116">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="70c39-117">Ograniczone regiony wykonania</span><span class="sxs-lookup"><span data-stu-id="70c39-117">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="70c39-118">Opisuje funkcję i zachowanie regionów ograniczonego wykonywania (CERs).</span><span class="sxs-lookup"><span data-stu-id="70c39-118">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70c39-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="70c39-119">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
