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
ms.openlocfilehash: c2f2104768144da244679e5d0be884d70a3ba6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386655"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` Zarządzany Asystent debugowania (MDA) została aktywowana jako ostrzeżenie informujące, że witryny wywołania wykresu wywołań (CER) region ograniczonego wykonania odwołuje się do wirtualnego docelowych, oznacza to, wirtualnych wywołanie metody wirtualnej innej niż końcowa lub przy użyciu wywołania interfejs. Środowisko uruchomieniowe języka wspólnego (CLR) nie można przewidzieć metody docelowej telefonów z pośredniego wyłącznie analizy metadanych i języka. W związku z tym nie można przygotować drzewo wywołań jako część wykresu CER i przerwań wątku, w tym poddrzewie nie mogą zostać automatycznie zablokowane. To zdarzenie MDA ostrzega o przypadkach, gdy CER może być konieczne można rozszerzyć za pomocą jawnego wywołania <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metody po dodatkowe informacje wymagane do obliczenia w celu wywołania jest znany w czasie wykonywania.  
  
## <a name="symptoms"></a>Symptomy  
 CERs, które nie działają, gdy wątek został przerwany lub domena aplikacji nie jest załadowany.  
  
## <a name="cause"></a>Przyczyna  
 CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
  
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
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
