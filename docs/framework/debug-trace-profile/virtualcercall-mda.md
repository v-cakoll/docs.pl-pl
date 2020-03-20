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
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181711"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="f9065-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="f9065-102">virtualCERCall MDA</span></span>
<span data-ttu-id="f9065-103">Zarządzany `virtualCERCall` asystent debugowania (MDA) jest aktywowany jako ostrzeżenie wskazujące, że lokacja wywołania w ramach wykresu wywołania regionu ograniczonego wykonywania (CER) odnosi się do wirtualnego obiektu docelowego, czyli wirtualnego wywołania niekonfekcyjnej metody wirtualnej lub wywołania przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f9065-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="f9065-104">Środowisko wykonawcze języka wspólnego (CLR) nie można przewidzieć metody docelowej tych wywołań z pośredniego języka i analizy metadanych sam.</span><span class="sxs-lookup"><span data-stu-id="f9065-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="f9065-105">W rezultacie drzewa wywołań nie można przygotować jako część wykresu CER i przerywanie wątku w tym poddrzewie nie może być automatycznie blokowane.</span><span class="sxs-lookup"><span data-stu-id="f9065-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="f9065-106">Ten obiekt MDA ostrzega o przypadkach, w których cer może <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> wymagać rozszerzenia przy użyciu jawnych wywołań metody, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9065-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f9065-107">Objawy</span><span class="sxs-lookup"><span data-stu-id="f9065-107">Symptoms</span></span>  
 <span data-ttu-id="f9065-108">CeRs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="f9065-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f9065-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f9065-109">Cause</span></span>  
 <span data-ttu-id="f9065-110">Cer zawiera wywołanie metody wirtualnej, która nie może być przygotowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f9065-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f9065-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f9065-111">Resolution</span></span>  
 <span data-ttu-id="f9065-112">Zadzwoń <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> do metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="f9065-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f9065-113">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="f9065-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="f9065-114">To MDA nie ma wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="f9065-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f9065-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f9065-115">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f9065-116">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="f9065-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f9065-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9065-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9065-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9065-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f9065-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f9065-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f9065-120">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f9065-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
