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
ms.openlocfilehash: 8784d6980d3edb1bbdd7b39a81e7e33bfec81242
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039600"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="56855-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="56855-102">virtualCERCall MDA</span></span>
<span data-ttu-id="56855-103">`virtualCERCall` zarządzanego asystenta debugowania (MDA) jest uaktywniana jako ostrzeżenie wskazujące, że lokacja wywołania w ramach wykresu wywołania ograniczonego wykonania (CER) odnosi się do wirtualnego elementu docelowego, czyli wywołania wirtualnego do niekońcowej metody wirtualnej lub wywołania przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56855-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="56855-104">Środowisko uruchomieniowe języka wspólnego (CLR) nie może przewidzieć metody docelowej tych wywołań z poziomu języka pośredniego i analizy metadanych.</span><span class="sxs-lookup"><span data-stu-id="56855-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="56855-105">W związku z tym drzewo wywołań nie może zostać przygotowane jako część wykresu CER, a przerwania wątku w tym poddrzewie nie mogą zostać automatycznie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="56855-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="56855-106">To zdarzenie powoduje ostrzeganie o przypadkach, w których może być konieczne rozszerzenie CER, za pomocą jawnych wywołań metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="56855-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="56855-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="56855-107">Symptoms</span></span>  
 <span data-ttu-id="56855-108">CERs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji jest zwolniona.</span><span class="sxs-lookup"><span data-stu-id="56855-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="56855-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="56855-109">Cause</span></span>  
 <span data-ttu-id="56855-110">CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="56855-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="56855-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="56855-111">Resolution</span></span>  
 <span data-ttu-id="56855-112">Wywołaj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="56855-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="56855-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="56855-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="56855-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="56855-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="56855-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="56855-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="56855-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="56855-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="56855-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="56855-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56855-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56855-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="56855-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="56855-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="56855-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="56855-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
