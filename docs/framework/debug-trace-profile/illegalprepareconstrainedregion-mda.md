---
title: illegalPrepareConstrainedRegion MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez illegalPrepareConstrainedRegion, który jest wywoływany, gdy wywołanie PrepareConstrainedRegions nie poprzedza instrukcji try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051288"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="e8a35-103">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="e8a35-103">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="e8a35-104">`illegalPrepareConstrainedRegion`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> wywołanie metody nie poprzedza bezpośrednio instrukcji programu `try` obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e8a35-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="e8a35-105">To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło, które nie umożliwia generowania kodu między wywołaniem i `try` , takimi jak komentarze.</span><span class="sxs-lookup"><span data-stu-id="e8a35-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e8a35-106">Objawy</span><span class="sxs-lookup"><span data-stu-id="e8a35-106">Symptoms</span></span>  
 <span data-ttu-id="e8a35-107">Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków ( `finally` lub `catch` ).</span><span class="sxs-lookup"><span data-stu-id="e8a35-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="e8a35-108">W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.</span><span class="sxs-lookup"><span data-stu-id="e8a35-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e8a35-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="e8a35-109">Cause</span></span>  
 <span data-ttu-id="e8a35-110">Wzorzec przygotowania dla programu CER nie działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e8a35-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="e8a35-111">Jest to zdarzenie błędu.</span><span class="sxs-lookup"><span data-stu-id="e8a35-111">This is an error event.</span></span> <span data-ttu-id="e8a35-112"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Wywołanie metody używane do oznaczania procedur obsługi wyjątków, które wprowadza CER w swoich `catch` / `finally` / `fault` / `filter` blokach, musi być używane bezpośrednio przed `try` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="e8a35-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e8a35-113">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="e8a35-113">Resolution</span></span>  
 <span data-ttu-id="e8a35-114">Upewnij się, że wywołanie jest <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> wykonywane bezpośrednio przed `try` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="e8a35-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e8a35-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e8a35-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="e8a35-116">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="e8a35-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e8a35-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e8a35-117">Output</span></span>  
 <span data-ttu-id="e8a35-118">MDA Wyświetla nazwę metody wywołującej <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.</span><span class="sxs-lookup"><span data-stu-id="e8a35-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e8a35-119">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="e8a35-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="e8a35-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8a35-120">Example</span></span>  
 <span data-ttu-id="e8a35-121">Poniższy przykład kodu demonstruje wzorzec, który powoduje aktywowanie tego MDA.</span><span class="sxs-lookup"><span data-stu-id="e8a35-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8a35-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8a35-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="e8a35-123">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e8a35-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e8a35-124">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="e8a35-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
