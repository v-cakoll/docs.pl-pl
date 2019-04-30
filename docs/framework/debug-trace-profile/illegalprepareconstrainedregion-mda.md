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
ms.openlocfilehash: 23a36d1709f03583ce39af0e7c80bb1ecd7cf809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754391"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="72a59-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="72a59-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="72a59-103">`illegalPrepareConstrainedRegion` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> wywołanie metody nie bezpośrednio poprzedzać `try` instrukcji obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="72a59-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="72a59-104">To ograniczenie jest w MSIL poziomu, więc jest dozwolone do generowania kodu źródło między wywołanie i `try`, takich jak komentarze.</span><span class="sxs-lookup"><span data-stu-id="72a59-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="72a59-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="72a59-105">Symptoms</span></span>  
 <span data-ttu-id="72a59-106">Region ograniczonego wykonania (CER), która nigdy nie jest traktowana jako takie, ale jako prosty bloku obsługi wyjątków (`finally` lub `catch`).</span><span class="sxs-lookup"><span data-stu-id="72a59-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="72a59-107">W konsekwencji regionie nie działa w przypadku warunku braku pamięci lub przerwanie wątku.</span><span class="sxs-lookup"><span data-stu-id="72a59-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="72a59-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="72a59-108">Cause</span></span>  
 <span data-ttu-id="72a59-109">Wzorzec przygotowania CER nie jest prawidłowo zakończony.</span><span class="sxs-lookup"><span data-stu-id="72a59-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="72a59-110">To zdarzenie błędu.</span><span class="sxs-lookup"><span data-stu-id="72a59-110">This is an error event.</span></span> <span data-ttu-id="72a59-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Wywołania metody, używany do oznaczania obsługi wyjątków jako wprowadzenie do CER w ich `catch` / `finally` / `fault` / `filter` bloków musi używać bezpośrednio przed `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="72a59-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="72a59-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="72a59-112">Resolution</span></span>  
 <span data-ttu-id="72a59-113">Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ma miejsce bezpośrednio przed `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="72a59-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="72a59-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="72a59-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="72a59-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="72a59-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="72a59-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="72a59-116">Output</span></span>  
 <span data-ttu-id="72a59-117">MDA Wyświetla nazwę wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat informujący o wywołaniu nie bezpośrednio poprzedzać początku bloku try.</span><span class="sxs-lookup"><span data-stu-id="72a59-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="72a59-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="72a59-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="72a59-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="72a59-119">Example</span></span>  
 <span data-ttu-id="72a59-120">Poniższy przykład kodu demonstruje wzorzec, który powoduje, że to zdarzenie MDA zostanie uaktywniony.</span><span class="sxs-lookup"><span data-stu-id="72a59-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72a59-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72a59-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="72a59-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="72a59-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="72a59-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="72a59-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
