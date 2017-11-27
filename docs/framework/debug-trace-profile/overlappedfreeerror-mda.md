---
title: overlappedFreeError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 645c9f6c5a2a693fb2b88b2b2bc1c40501eecde8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="6e294-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="6e294-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="6e294-103">`overlappedFreeError` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> metoda jest wywoływana przed nakładających się operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="6e294-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6e294-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="6e294-104">Symptoms</span></span>  
 <span data-ttu-id="6e294-105">Naruszenia zasad dostępu lub uszkodzenie sterty zbierane pamięci.</span><span class="sxs-lookup"><span data-stu-id="6e294-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6e294-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6e294-106">Cause</span></span>  
 <span data-ttu-id="6e294-107">Nachodzące struktury został zwolniony przed ukończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="6e294-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="6e294-108">Funkcję, która używa wskaźnika może zapisać do struktury później, po został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="6e294-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="6e294-109">Który może spowodować uszkodzenie sterty, ponieważ inny obiekt teraz mogą zajmować tego regionu.</span><span class="sxs-lookup"><span data-stu-id="6e294-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="6e294-110">To zdarzenie MDA może nie reprezentować błędu, jeśli pokrywającej się z inną operacja nie została pomyślnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="6e294-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6e294-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6e294-111">Resolution</span></span>  
 <span data-ttu-id="6e294-112">Upewnij się, że operacji We/Wy przy użyciu nachodzące struktury zostało zakończone przed wywołaniem <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody.</span><span class="sxs-lookup"><span data-stu-id="6e294-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6e294-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6e294-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="6e294-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="6e294-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6e294-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6e294-115">Output</span></span>  
 <span data-ttu-id="6e294-116">Oto przykładowe dane wyjściowe dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="6e294-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="6e294-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6e294-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e294-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e294-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="6e294-119">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="6e294-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="6e294-120">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="6e294-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
