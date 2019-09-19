---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052678"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="63049-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="63049-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="63049-103">Asystent `illegalPrepareConstrainedRegion` debugowania zarządzanego (MDA) jest uaktywniany, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> gdy wywołanie metody nie poprzedza `try` bezpośrednio instrukcji programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="63049-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="63049-104">To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło `try`, które nie umożliwia generowania kodu między wywołaniem i, takimi jak komentarze.</span><span class="sxs-lookup"><span data-stu-id="63049-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="63049-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="63049-105">Symptoms</span></span>  
 <span data-ttu-id="63049-106">Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków (`finally` lub `catch`).</span><span class="sxs-lookup"><span data-stu-id="63049-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="63049-107">W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.</span><span class="sxs-lookup"><span data-stu-id="63049-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="63049-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="63049-108">Cause</span></span>  
 <span data-ttu-id="63049-109">Wzorzec przygotowania dla programu CER nie działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="63049-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="63049-110">Jest to zdarzenie błędu.</span><span class="sxs-lookup"><span data-stu-id="63049-110">This is an error event.</span></span> <span data-ttu-id="63049-111">/ / `catch` `filter` `finally` / `fault` Wywołanie metody używane do oznaczania procedur obsługi wyjątków, które wprowadza CER w swoich blokach, musi być używane bezpośrednio przed <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> `try` instrukcja.</span><span class="sxs-lookup"><span data-stu-id="63049-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="63049-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="63049-112">Resolution</span></span>  
 <span data-ttu-id="63049-113">Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> jest wykonywane bezpośrednio `try` przed instrukcją.</span><span class="sxs-lookup"><span data-stu-id="63049-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="63049-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="63049-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="63049-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="63049-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="63049-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="63049-116">Output</span></span>  
 <span data-ttu-id="63049-117">MDA Wyświetla nazwę metody wywołującej <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.</span><span class="sxs-lookup"><span data-stu-id="63049-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="63049-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="63049-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="63049-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="63049-119">Example</span></span>  
 <span data-ttu-id="63049-120">Poniższy przykład kodu demonstruje wzorzec, który powoduje aktywowanie tego MDA.</span><span class="sxs-lookup"><span data-stu-id="63049-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63049-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63049-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="63049-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="63049-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="63049-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="63049-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
