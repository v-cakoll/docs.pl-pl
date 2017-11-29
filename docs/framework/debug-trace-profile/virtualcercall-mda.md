---
title: virtualCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f0c06eef7524c18e252ade9122d8c9cb3c2f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="33cad-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="33cad-102">virtualCERCall MDA</span></span>
<span data-ttu-id="33cad-103">`virtualCERCall` Zarządzany Asystent debugowania (MDA) została aktywowana jako ostrzeżenie informujące, że witryny wywołania wykresu wywołań (CER) region ograniczonego wykonania odwołuje się do wirtualnego docelowych, oznacza to, wirtualnych wywołanie metody wirtualnej innej niż końcowa lub przy użyciu wywołania interfejs.</span><span class="sxs-lookup"><span data-stu-id="33cad-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="33cad-104">Środowisko uruchomieniowe języka wspólnego (CLR) nie można przewidzieć metody docelowej telefonów z pośredniego wyłącznie analizy metadanych i języka.</span><span class="sxs-lookup"><span data-stu-id="33cad-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="33cad-105">W związku z tym nie można przygotować drzewo wywołań jako część wykresu CER i przerwań wątku, w tym poddrzewie nie mogą zostać automatycznie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="33cad-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="33cad-106">To zdarzenie MDA ostrzega o przypadkach, gdy CER może być konieczne można rozszerzyć za pomocą jawnego wywołania <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody po dodatkowe informacje wymagane do obliczenia w celu wywołania jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="33cad-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="33cad-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="33cad-107">Symptoms</span></span>  
 <span data-ttu-id="33cad-108">CERs, które nie działają, gdy wątek został przerwany lub domena aplikacji nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="33cad-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="33cad-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="33cad-109">Cause</span></span>  
 <span data-ttu-id="33cad-110">CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="33cad-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="33cad-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="33cad-111">Resolution</span></span>  
 <span data-ttu-id="33cad-112">Wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="33cad-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="33cad-113">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="33cad-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="33cad-114">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="33cad-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="33cad-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="33cad-115">Output</span></span>  
  
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
  
## <a name="configuration"></a><span data-ttu-id="33cad-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="33cad-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="33cad-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="33cad-117">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="33cad-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33cad-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="33cad-119">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="33cad-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="33cad-120">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="33cad-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
