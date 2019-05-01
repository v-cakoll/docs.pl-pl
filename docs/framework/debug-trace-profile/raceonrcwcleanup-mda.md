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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791578"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="8ced6-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="8ced6-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="8ced6-103">`raceOnRCWCleanup` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) jest używany, gdy wykonywane jest wywołanie, aby zwolnić go przy użyciu polecenia takiego jak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metody.</span><span class="sxs-lookup"><span data-stu-id="8ced6-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8ced6-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="8ced6-104">Symptoms</span></span>  
 <span data-ttu-id="8ced6-105">Naruszenia zasad dostępu ani uszkodzeń pamięci podczas lub po uwolnieniu RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> lub podobnej metody.</span><span class="sxs-lookup"><span data-stu-id="8ced6-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8ced6-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="8ced6-106">Cause</span></span>  
 <span data-ttu-id="8ced6-107">RCW jest używana w innym wątku lub zwalnianie stosu wątku.</span><span class="sxs-lookup"><span data-stu-id="8ced6-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="8ced6-108">Nie można zwolnić RCW, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="8ced6-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8ced6-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8ced6-109">Resolution</span></span>  
 <span data-ttu-id="8ced6-110">Nie zwolnienia RCW, która może być używany w bieżącym lub w innych wątków.</span><span class="sxs-lookup"><span data-stu-id="8ced6-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8ced6-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8ced6-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="8ced6-112">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="8ced6-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8ced6-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8ced6-113">Output</span></span>  
 <span data-ttu-id="8ced6-114">Komunikat z opisem błędu.</span><span class="sxs-lookup"><span data-stu-id="8ced6-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8ced6-115">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8ced6-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ced6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ced6-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8ced6-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="8ced6-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8ced6-118">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="8ced6-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
