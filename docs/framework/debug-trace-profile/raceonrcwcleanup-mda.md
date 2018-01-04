---
title: raceOnRCWCleanup MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33d1c7d91c33c194353af43deed9329b9b4ec841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="9007b-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="9007b-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="9007b-103">`raceOnRCWCleanup` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykrywa, że [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW) jest używane po wywołaniu zwolnij go przy użyciu polecenia takiego jak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metody.</span><span class="sxs-lookup"><span data-stu-id="9007b-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9007b-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="9007b-104">Symptoms</span></span>  
 <span data-ttu-id="9007b-105">Naruszenia zasad dostępu lub uszkodzenie pamięci podczas lub po uwolnieniu przy użyciu otoki RCW <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> lub podobnej metody.</span><span class="sxs-lookup"><span data-stu-id="9007b-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9007b-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9007b-106">Cause</span></span>  
 <span data-ttu-id="9007b-107">Otoka RCW jest używana przez inny wątek lub zwalnianie stosu wątku.</span><span class="sxs-lookup"><span data-stu-id="9007b-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="9007b-108">Nie można zwolnić otoki RCW, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="9007b-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9007b-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9007b-109">Resolution</span></span>  
 <span data-ttu-id="9007b-110">Nie zwolnienia otoki RCW, która może być używany w bieżącym lub w inne wątki.</span><span class="sxs-lookup"><span data-stu-id="9007b-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9007b-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9007b-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="9007b-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9007b-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9007b-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9007b-113">Output</span></span>  
 <span data-ttu-id="9007b-114">Komunikat z opisem błędu.</span><span class="sxs-lookup"><span data-stu-id="9007b-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9007b-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9007b-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9007b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9007b-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9007b-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9007b-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9007b-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="9007b-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
