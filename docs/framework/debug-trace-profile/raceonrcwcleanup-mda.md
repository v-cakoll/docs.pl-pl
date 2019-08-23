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
ms.openlocfilehash: ca3b28d0d27af0a752de894f5856b76939b01e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967238"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="5a6a8-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="5a6a8-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="5a6a8-103">Asystent debugowania <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że w środowisku uruchomieniowym (otoka), gdy wywołanie do wydania jest używane, za pomocą polecenia, takiego jak metoda. [](../../standard/native-interop/runtime-callable-wrapper.md) `raceOnRCWCleanup`</span><span class="sxs-lookup"><span data-stu-id="5a6a8-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5a6a8-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="5a6a8-104">Symptoms</span></span>  
 <span data-ttu-id="5a6a8-105">Naruszenia zasad dostępu lub uszkodzenia pamięci w trakcie lub po zwolnieniu otoki RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody lub podobnej.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5a6a8-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="5a6a8-106">Cause</span></span>  
 <span data-ttu-id="5a6a8-107">Otoka RCW jest używana w innym wątku lub na stosie wolnego wątku.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="5a6a8-108">Nie można zwolnić otoki RCW, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5a6a8-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="5a6a8-109">Resolution</span></span>  
 <span data-ttu-id="5a6a8-110">Nie zwalniaj otoki RCW, która może być używana w bieżącym lub w innych wątkach.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5a6a8-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5a6a8-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="5a6a8-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5a6a8-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5a6a8-113">Output</span></span>  
 <span data-ttu-id="5a6a8-114">Komunikat z opisem błędu.</span><span class="sxs-lookup"><span data-stu-id="5a6a8-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5a6a8-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5a6a8-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a6a8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a6a8-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5a6a8-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="5a6a8-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5a6a8-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="5a6a8-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
