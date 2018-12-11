---
title: virtualCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df3e14b14078a4d484dd18f3bb59f5fcfee55411
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129237"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="c37f8-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="c37f8-102">virtualCERCall MDA</span></span>
<span data-ttu-id="c37f8-103">`virtualCERCall` Zarządzanego Asystenta debugowania (MDA) jest uaktywniony jako ostrzeżenie informujące, że witryny wywołania, w ramach wykresu wywołań ograniczonego wykonania region (CER) odwołuje się do docelowego wirtualnego, oznacza to, wywołanie wirtualne metodą wirtualną innego niż końcowa lub za pomocą wywołania interfejs.</span><span class="sxs-lookup"><span data-stu-id="c37f8-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="c37f8-104">Środowisko uruchomieniowe języka wspólnego (CLR) nie można przewidzieć metoda przeznaczenia tych wywołań z pośrednich analizy języka i metadanych, które są wyłącznie.</span><span class="sxs-lookup"><span data-stu-id="c37f8-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="c37f8-105">W rezultacie drzewo wywołań nie można przygotować jako część wykresu CER i przerwań wątku, w tym poddrzewie nie mogą zostać automatycznie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="c37f8-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="c37f8-106">To zdarzenie MDA ostrzega o przypadkach, gdzie CER może być konieczne można rozszerzyć za pomocą jawnych wywołań <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda po dodatkowe informacje wymagane do obliczenia cel wywołania jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c37f8-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c37f8-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="c37f8-107">Symptoms</span></span>  
 <span data-ttu-id="c37f8-108">CERs, których nie jest uruchomiony, gdy wątek został przerwany lub domeny aplikacji jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="c37f8-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c37f8-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c37f8-109">Cause</span></span>  
 <span data-ttu-id="c37f8-110">CER zawiera wywołanie metody wirtualnej, którego nie można przygotować automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c37f8-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c37f8-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c37f8-111">Resolution</span></span>  
 <span data-ttu-id="c37f8-112">Wywołaj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c37f8-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c37f8-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c37f8-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="c37f8-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c37f8-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c37f8-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c37f8-115">Output</span></span>  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="c37f8-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c37f8-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c37f8-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="c37f8-117">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c37f8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c37f8-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c37f8-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c37f8-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c37f8-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="c37f8-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
