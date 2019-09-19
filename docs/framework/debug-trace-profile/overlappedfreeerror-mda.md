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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70d31bc187cabe49351e86a20023e2ec65e87b94
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052401"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="ac5e9-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="ac5e9-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="ac5e9-103">Asystent `overlappedFreeError` debugowania zarządzanego (MDA) jest uaktywniany, <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> gdy metoda jest wywoływana przed ukończeniem operacji nakładania się.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ac5e9-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="ac5e9-104">Symptoms</span></span>  
 <span data-ttu-id="ac5e9-105">Naruszenia dostępu lub uszkodzenie sterty zebranych przez elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ac5e9-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ac5e9-106">Cause</span></span>  
 <span data-ttu-id="ac5e9-107">Nakładająca się struktura została zwolniona przed ukończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="ac5e9-108">Funkcja, która używa nakładającego się wskaźnika, może później pisać do struktury, po jej zwolnieniu.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="ac5e9-109">Może to spowodować uszkodzenie sterty, ponieważ inny obiekt może teraz zajmować ten region.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="ac5e9-110">To zdarzenie MDA może nie reprezentować błędu, jeśli nakładająca się operacja nie została pomyślnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ac5e9-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ac5e9-111">Resolution</span></span>  
 <span data-ttu-id="ac5e9-112">Przed wywołaniem <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody upewnij się, że operacja we/wy z nakładającą się strukturą została ukończona.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ac5e9-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ac5e9-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="ac5e9-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ac5e9-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ac5e9-115">Output</span></span>  
 <span data-ttu-id="ac5e9-116">Poniżej przedstawiono przykładowe dane wyjściowe dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="ac5e9-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ac5e9-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac5e9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac5e9-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ac5e9-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ac5e9-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ac5e9-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="ac5e9-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
