---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 8a0c72cf26ef8434719ff6661ef15a44f51c8740
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217265"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="01107-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="01107-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="01107-103">Asystent debugowania zarządzanego `overlappedFreeError` (MDA) jest uaktywniany po wywołaniu metody <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> przed ukończeniem operacji nakładania się.</span><span class="sxs-lookup"><span data-stu-id="01107-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="01107-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="01107-104">Symptoms</span></span>  
 <span data-ttu-id="01107-105">Naruszenia dostępu lub uszkodzenie sterty zebranych przez elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="01107-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="01107-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="01107-106">Cause</span></span>  
 <span data-ttu-id="01107-107">Nakładająca się struktura została zwolniona przed ukończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="01107-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="01107-108">Funkcja, która używa nakładającego się wskaźnika, może później pisać do struktury, po jej zwolnieniu.</span><span class="sxs-lookup"><span data-stu-id="01107-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="01107-109">Może to spowodować uszkodzenie sterty, ponieważ inny obiekt może teraz zajmować ten region.</span><span class="sxs-lookup"><span data-stu-id="01107-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="01107-110">To zdarzenie MDA może nie reprezentować błędu, jeśli nakładająca się operacja nie została pomyślnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="01107-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="01107-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="01107-111">Resolution</span></span>  
 <span data-ttu-id="01107-112">Przed wywołaniem metody <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> upewnij się, że operacja we/wy z nakładającą się strukturą została zakończona.</span><span class="sxs-lookup"><span data-stu-id="01107-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="01107-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="01107-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="01107-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="01107-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="01107-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="01107-115">Output</span></span>  
 <span data-ttu-id="01107-116">Poniżej przedstawiono przykładowe dane wyjściowe dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="01107-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="01107-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="01107-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01107-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01107-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="01107-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="01107-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="01107-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="01107-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
