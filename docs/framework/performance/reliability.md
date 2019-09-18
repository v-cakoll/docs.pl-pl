---
title: Niezawodność
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb84c6617cdffabfe276895f81e7df2b04bb8bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046235"
---
# <a name="reliability"></a><span data-ttu-id="39170-102">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="39170-102">Reliability</span></span>
<span data-ttu-id="39170-103">Ważne jest, aby kod wykonywany w środowiskach serwerów, takich jak SQL Server chronić przed wyjątkami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="39170-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="39170-104">Niezawodność, zgodnie z opisem w tym miejscu, nie jest specyficzna dla SQL Server, ale do pisania niezawodnego kodu dla dowolnego hosta wykonywanego w środowisku .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="39170-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="39170-105">Jednak SQL Server to pierwsza usługa, która korzysta z nowych funkcji zapewniających niezawodność w wersji 2,0, więc jest używana jako przykład.</span><span class="sxs-lookup"><span data-stu-id="39170-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="39170-106">Kod działający w SQL Server musi obsłużyć bardziej rygorystyczne wytyczne dotyczące niezawodności niż inne środowiska serwera.</span><span class="sxs-lookup"><span data-stu-id="39170-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="39170-107">Jest to spowodowane ciągłą operacją SQL Server na granicy zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="39170-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="39170-108"><xref:System.OutOfMemoryException>i <xref:System.Threading.ThreadAbortException> wyjątki nie są rzadko w środowisku SQL serverm.</span><span class="sxs-lookup"><span data-stu-id="39170-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="39170-109">Ogólnie rzecz biorąc, te wytyczne mają mniej informacji na temat niezawodności i więcej na umożliwienie w pełni zaufanego kodu zarządzanego, aby <xref:System.AppDomain>zapewnić bezproblemowy niepowodzenie podczas odtwarzania, który jest głównym sposobem, w jaki serwer utrzymuje spójność i dostępność.</span><span class="sxs-lookup"><span data-stu-id="39170-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39170-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="39170-110">In This Section</span></span>  
 [<span data-ttu-id="39170-111">Atrybuty ochrony hosta i programowanie SQL Server</span><span class="sxs-lookup"><span data-stu-id="39170-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="39170-112">Opisuje, w <xref:System.Security.Permissions.HostProtectionAttribute> jaki sposób atrybut jest używany przez SQL Server w celu ograniczenia wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="39170-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="39170-113">Najlepsze rozwiązania dotyczące niezawodności</span><span class="sxs-lookup"><span data-stu-id="39170-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="39170-114">Zawiera wytyczne dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.</span><span class="sxs-lookup"><span data-stu-id="39170-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="39170-115">Ograniczone regiony wykonania</span><span class="sxs-lookup"><span data-stu-id="39170-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="39170-116">Opisuje funkcję i zachowanie regionów ograniczonego wykonywania (CERs).</span><span class="sxs-lookup"><span data-stu-id="39170-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="39170-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="39170-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
