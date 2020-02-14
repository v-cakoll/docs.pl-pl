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
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216461"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="ae3dc-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="ae3dc-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="ae3dc-103">Asystent debugowania zarządzanego `illegalPrepareConstrainedRegion` (MDA) jest uaktywniany, gdy wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> nie poprzedza bezpośrednio instrukcji `try` programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="ae3dc-104">To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło, które nie umożliwia generowania kodu między wywołaniem i `try`, takie jak komentarze.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ae3dc-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="ae3dc-105">Symptoms</span></span>  
 <span data-ttu-id="ae3dc-106">Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków (`finally` lub `catch`).</span><span class="sxs-lookup"><span data-stu-id="ae3dc-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="ae3dc-107">W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ae3dc-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ae3dc-108">Cause</span></span>  
 <span data-ttu-id="ae3dc-109">Wzorzec przygotowania dla programu CER nie działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="ae3dc-110">Jest to zdarzenie błędu.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-110">This is an error event.</span></span> <span data-ttu-id="ae3dc-111">Wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> używane do oznaczania procedur obsługi wyjątków jako przedstawiające CER w ich `catch`/`finally`/`fault`/`filter` bloków należy używać bezpośrednio przed instrukcją `try`.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ae3dc-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ae3dc-112">Resolution</span></span>  
 <span data-ttu-id="ae3dc-113">Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> następuje bezpośrednio przed instrukcją `try`.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ae3dc-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ae3dc-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ae3dc-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ae3dc-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ae3dc-116">Output</span></span>  
 <span data-ttu-id="ae3dc-117">MDA Wyświetla nazwę metody wywołującej metodę <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ae3dc-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ae3dc-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ae3dc-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae3dc-119">Example</span></span>  
 <span data-ttu-id="ae3dc-120">Poniższy przykład kodu demonstruje wzorzec, który powoduje aktywowanie tego MDA.</span><span class="sxs-lookup"><span data-stu-id="ae3dc-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae3dc-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae3dc-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="ae3dc-122">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ae3dc-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ae3dc-123">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="ae3dc-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
