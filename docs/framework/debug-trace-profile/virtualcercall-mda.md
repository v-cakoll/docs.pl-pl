---
title: virtualCERCall MDA
description: Przejrzyj virtualCERCall Managed Debug Assistant (MDA), który jest wywoływany, jeśli program CER zawiera wywołanie metody wirtualnej, której nie można przygotować automatycznie.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: fab0686b1c7d2fbb1485f6e4b82d008495a553cd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803563"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="9ca14-103">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="9ca14-103">virtualCERCall MDA</span></span>
<span data-ttu-id="9ca14-104">`virtualCERCall`Asystent debugowania zarządzanego (MDA) jest uaktywniany jako ostrzeżenie wskazujące, że lokacja wywołania w ramach wykresu wywołania ograniczonego wykonania (CER) odwołuje się do wirtualnego elementu docelowego, czyli wywołania wirtualnego do niekońcowej metody wirtualnej lub wywołania przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9ca14-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="9ca14-105">Środowisko uruchomieniowe języka wspólnego (CLR) nie może przewidzieć metody docelowej tych wywołań z poziomu języka pośredniego i analizy metadanych.</span><span class="sxs-lookup"><span data-stu-id="9ca14-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="9ca14-106">W związku z tym drzewo wywołań nie może zostać przygotowane jako część wykresu CER, a przerwania wątku w tym poddrzewie nie mogą zostać automatycznie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="9ca14-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="9ca14-107">To zdarzenie powoduje ostrzeganie o przypadkach, w których może być konieczne rozszerzenie CER, za pomocą jawnych wywołań <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9ca14-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9ca14-108">Objawy</span><span class="sxs-lookup"><span data-stu-id="9ca14-108">Symptoms</span></span>  
 <span data-ttu-id="9ca14-109">CERs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji jest zwolniona.</span><span class="sxs-lookup"><span data-stu-id="9ca14-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9ca14-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9ca14-110">Cause</span></span>  
 <span data-ttu-id="9ca14-111">CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9ca14-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9ca14-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9ca14-112">Resolution</span></span>  
 <span data-ttu-id="9ca14-113">Wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="9ca14-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9ca14-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9ca14-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="9ca14-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9ca14-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9ca14-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9ca14-116">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="9ca14-117">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="9ca14-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9ca14-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ca14-118">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ca14-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ca14-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9ca14-120">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9ca14-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9ca14-121">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="9ca14-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
