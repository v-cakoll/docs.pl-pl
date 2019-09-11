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
ms.openlocfilehash: 3864ae416df0a2516a4dd9e6cf92669f66f27bb1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853984"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="10592-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="10592-102">virtualCERCall MDA</span></span>
<span data-ttu-id="10592-103">Asystent `virtualCERCall` debugowania zarządzanego (MDA) jest uaktywniany jako ostrzeżenie wskazujące, że obiekt wywołania w ramach wykresu wywołania ograniczonego wykonywania (CER) odwołuje się do wirtualnego celu, czyli wywołania wirtualnego do niekońcowej metody wirtualnej lub wywołania przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="10592-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="10592-104">Środowisko uruchomieniowe języka wspólnego (CLR) nie może przewidzieć metody docelowej tych wywołań z poziomu języka pośredniego i analizy metadanych.</span><span class="sxs-lookup"><span data-stu-id="10592-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="10592-105">W związku z tym drzewo wywołań nie może zostać przygotowane jako część wykresu CER, a przerwania wątku w tym poddrzewie nie mogą zostać automatycznie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="10592-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="10592-106">To zdarzenie powoduje ostrzeganie o przypadkach, w których może być konieczne rozszerzenie cer, za pomocą jawnych <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> wywołań metody, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="10592-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="10592-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="10592-107">Symptoms</span></span>  
 <span data-ttu-id="10592-108">CERs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji jest zwolniona.</span><span class="sxs-lookup"><span data-stu-id="10592-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="10592-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="10592-109">Cause</span></span>  
 <span data-ttu-id="10592-110">CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="10592-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="10592-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="10592-111">Resolution</span></span>  
 <span data-ttu-id="10592-112">Wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="10592-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="10592-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="10592-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="10592-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="10592-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="10592-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="10592-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="10592-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="10592-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="10592-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="10592-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10592-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10592-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="10592-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="10592-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="10592-120">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="10592-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
