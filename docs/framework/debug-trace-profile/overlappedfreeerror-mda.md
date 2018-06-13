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
ms.openlocfilehash: 301d36820ed5ae1d6ba1cfd2961221095b02bea6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386408"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="d8b40-102">overlappedFreeError MDA</span><span class="sxs-lookup"><span data-stu-id="d8b40-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="d8b40-103">`overlappedFreeError` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> metoda jest wywoływana przed nakładających się operacja została ukończona.</span><span class="sxs-lookup"><span data-stu-id="d8b40-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d8b40-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="d8b40-104">Symptoms</span></span>  
 <span data-ttu-id="d8b40-105">Naruszenia zasad dostępu lub uszkodzenie sterty zbierane pamięci.</span><span class="sxs-lookup"><span data-stu-id="d8b40-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d8b40-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d8b40-106">Cause</span></span>  
 <span data-ttu-id="d8b40-107">Nachodzące struktury został zwolniony przed ukończeniem operacji.</span><span class="sxs-lookup"><span data-stu-id="d8b40-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="d8b40-108">Funkcję, która używa wskaźnika może zapisać do struktury później, po został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="d8b40-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="d8b40-109">Który może spowodować uszkodzenie sterty, ponieważ inny obiekt teraz mogą zajmować tego regionu.</span><span class="sxs-lookup"><span data-stu-id="d8b40-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="d8b40-110">To zdarzenie MDA może nie reprezentować błędu, jeśli pokrywającej się z inną operacja nie została pomyślnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="d8b40-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d8b40-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d8b40-111">Resolution</span></span>  
 <span data-ttu-id="d8b40-112">Upewnij się, że operacji We/Wy przy użyciu nachodzące struktury zostało zakończone przed wywołaniem <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody.</span><span class="sxs-lookup"><span data-stu-id="d8b40-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d8b40-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d8b40-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="d8b40-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="d8b40-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d8b40-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d8b40-115">Output</span></span>  
 <span data-ttu-id="d8b40-116">Oto przykładowe dane wyjściowe dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="d8b40-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="d8b40-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d8b40-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8b40-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8b40-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d8b40-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d8b40-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d8b40-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="d8b40-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
