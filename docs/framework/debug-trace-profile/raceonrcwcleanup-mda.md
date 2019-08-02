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
ms.openlocfilehash: e6400986d58fcb5f11d06e371a1b58f5256f4c62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629364"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="c7b27-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="c7b27-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="c7b27-103">Asystent debugowania <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że w środowisku uruchomieniowym (otoka), gdy wywołanie do wydania jest używane, za pomocą polecenia, takiego jak metoda. [](../../../docs/standard/native-interop/runtime-callable-wrapper.md) `raceOnRCWCleanup`</span><span class="sxs-lookup"><span data-stu-id="c7b27-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c7b27-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="c7b27-104">Symptoms</span></span>  
 <span data-ttu-id="c7b27-105">Naruszenia zasad dostępu lub uszkodzenia pamięci w trakcie lub po zwolnieniu otoki RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody lub podobnej.</span><span class="sxs-lookup"><span data-stu-id="c7b27-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c7b27-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c7b27-106">Cause</span></span>  
 <span data-ttu-id="c7b27-107">Otoka RCW jest używana w innym wątku lub na stosie wolnego wątku.</span><span class="sxs-lookup"><span data-stu-id="c7b27-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="c7b27-108">Nie można zwolnić otoki RCW, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="c7b27-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c7b27-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c7b27-109">Resolution</span></span>  
 <span data-ttu-id="c7b27-110">Nie zwalniaj otoki RCW, która może być używana w bieżącym lub w innych wątkach.</span><span class="sxs-lookup"><span data-stu-id="c7b27-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7b27-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c7b27-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7b27-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c7b27-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7b27-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c7b27-113">Output</span></span>  
 <span data-ttu-id="c7b27-114">Komunikat z opisem błędu.</span><span class="sxs-lookup"><span data-stu-id="c7b27-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c7b27-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c7b27-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7b27-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7b27-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c7b27-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c7b27-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c7b27-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="c7b27-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
