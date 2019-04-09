---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628790bb8229dc519589c122235f07a38ba57c1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100239"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="e1b8f-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="e1b8f-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="e1b8f-103">`raceOnRCWCleanup` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) jest używany, gdy wykonywane jest wywołanie, aby zwolnić go przy użyciu polecenia takiego jak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metody.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e1b8f-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="e1b8f-104">Symptoms</span></span>  
 <span data-ttu-id="e1b8f-105">Naruszenia zasad dostępu ani uszkodzeń pamięci podczas lub po uwolnieniu RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> lub podobnej metody.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e1b8f-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e1b8f-106">Cause</span></span>  
 <span data-ttu-id="e1b8f-107">RCW jest używana w innym wątku lub zwalnianie stosu wątku.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="e1b8f-108">Nie można zwolnić RCW, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e1b8f-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e1b8f-109">Resolution</span></span>  
 <span data-ttu-id="e1b8f-110">Nie zwolnienia RCW, która może być używany w bieżącym lub w innych wątków.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e1b8f-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e1b8f-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="e1b8f-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e1b8f-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e1b8f-113">Output</span></span>  
 <span data-ttu-id="e1b8f-114">Komunikat z opisem błędu.</span><span class="sxs-lookup"><span data-stu-id="e1b8f-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e1b8f-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e1b8f-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1b8f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1b8f-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e1b8f-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e1b8f-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e1b8f-118">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="e1b8f-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
