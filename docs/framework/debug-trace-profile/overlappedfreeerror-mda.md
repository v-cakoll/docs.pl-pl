---
title: overlappedFreeError MDA
description: Zapoznaj się z asystentem debugowania zarządzanego w programie overlappedFreeError (MDA) w programie .NET, który może aktywować w przypadku naruszeń dostępu lub uszkodzenia sterty zebranych przez elementy bezużyteczne.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 9be33c59723ecb2743f2bc610d7fb69d24ff388c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803921"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="e4b8c-103">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="e4b8c-103">overlappedFreeError MDA</span></span>
<span data-ttu-id="e4b8c-104">`overlappedFreeError`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> Metoda jest wywoływana przed ukończeniem operacji nakładania się.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e4b8c-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="e4b8c-105">Symptoms</span></span>  
 <span data-ttu-id="e4b8c-106">Naruszenia dostępu lub uszkodzenie sterty zebranych przez elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e4b8c-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e4b8c-107">Cause</span></span>  
 <span data-ttu-id="e4b8c-108">Nakładająca się struktura została zwolniona przed ukończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="e4b8c-109">Funkcja, która używa nakładającego się wskaźnika, może później pisać do struktury, po jej zwolnieniu.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="e4b8c-110">Może to spowodować uszkodzenie sterty, ponieważ inny obiekt może teraz zajmować ten region.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="e4b8c-111">To zdarzenie MDA może nie reprezentować błędu, jeśli nakładająca się operacja nie została pomyślnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e4b8c-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e4b8c-112">Resolution</span></span>  
 <span data-ttu-id="e4b8c-113">Przed wywołaniem metody upewnij się, że operacja we/wy z nakładającą się strukturą została ukończona <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> .</span><span class="sxs-lookup"><span data-stu-id="e4b8c-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e4b8c-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e4b8c-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="e4b8c-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e4b8c-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e4b8c-116">Output</span></span>  
 <span data-ttu-id="e4b8c-117">Poniżej przedstawiono przykładowe dane wyjściowe dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="e4b8c-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="e4b8c-118">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="e4b8c-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4b8c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4b8c-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e4b8c-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e4b8c-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e4b8c-121">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="e4b8c-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
