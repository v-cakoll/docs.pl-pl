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
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949295"
---
# <a name="reliability"></a><span data-ttu-id="fa048-102">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="fa048-102">Reliability</span></span>
<span data-ttu-id="fa048-103">Należy pamiętać, że kodu wykonywanego w środowisku serwerów, takich jak SQL Server ochronę przed wyjątki asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="fa048-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="fa048-104">Niezawodność, zgodnie z opisem w tym miejscu nie jest specyficzne dla programu SQL Server, ale do pisania niezawodne kodu dla każdego hosta w .NET Framework w wersji 2.0 środowiska.</span><span class="sxs-lookup"><span data-stu-id="fa048-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="fa048-105">Program SQL Server jest jednak pierwszej usługi tworzenie rozległe Użyj nowych funkcji niezawodność w wersji 2.0, dzięki czemu jest ona używana jako przykład.</span><span class="sxs-lookup"><span data-stu-id="fa048-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="fa048-106">Kod uruchomiony w programie SQL Server muszą radzić sobie z bardziej rygorystyczne wytyczne niezawodność niż innych środowisk serwera.</span><span class="sxs-lookup"><span data-stu-id="fa048-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="fa048-107">Jest to spowodowane działania stały programu SQL Server na urządzeniach brzegowych zużycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="fa048-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="fa048-108"><xref:System.OutOfMemoryException> i <xref:System.Threading.ThreadAbortException> wyjątki nie są niczym niezwykłym w środowisku programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fa048-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="fa048-109">Te wytyczne są ogólnie rzecz biorąc mniej ukierunkowane na niezawodność i więcej w umożliwiając całkowicie zaufanym zarządzanemu kodowi elegancko nie powieść się face z <xref:System.AppDomain>— poziom odtwarzania, który jest podstawowym sposobem server zachowuje spójności i dostępności.</span><span class="sxs-lookup"><span data-stu-id="fa048-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa048-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fa048-110">In This Section</span></span>  
 [<span data-ttu-id="fa048-111">Atrybuty ochrony hosta i programowanie SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa048-111">SQL Server Programming and Host Protection Attributes</span></span>](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="fa048-112">W tym artykule opisano sposób, w jaki <xref:System.Security.Permissions.HostProtectionAttribute> atrybut jest używany przez program SQL Server, aby ograniczyć wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fa048-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="fa048-113">Najlepsze rozwiązania dotyczące niezawodności</span><span class="sxs-lookup"><span data-stu-id="fa048-113">Reliability Best Practices</span></span>](../../../docs/framework/performance/reliability-best-practices.md)  
 <span data-ttu-id="fa048-114">Wskazówki dotyczące pisania kodu, który spełnia wymagania dotyczące niezawodności.</span><span class="sxs-lookup"><span data-stu-id="fa048-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="fa048-115">Ograniczone regiony wykonania</span><span class="sxs-lookup"><span data-stu-id="fa048-115">Constrained Execution Regions</span></span>](../../../docs/framework/performance/constrained-execution-regions.md)  
 <span data-ttu-id="fa048-116">Zawiera opis funkcji i zachowania ograniczone regiony wykonania (CERs).</span><span class="sxs-lookup"><span data-stu-id="fa048-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa048-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="fa048-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
