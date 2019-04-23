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
ms.openlocfilehash: e2c8712837dab17f70be32617711c1bad9349508
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086081"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` Zarządzanego Asystenta debugowania (MDA) jest uaktywniony jako ostrzeżenie informujące, że witryny wywołania, w ramach wykresu wywołań ograniczonego wykonania region (CER) odwołuje się do docelowego wirtualnego, oznacza to, wywołanie wirtualne metodą wirtualną innego niż końcowa lub za pomocą wywołania interfejs. Środowisko uruchomieniowe języka wspólnego (CLR) nie można przewidzieć metoda przeznaczenia tych wywołań z pośrednich analizy języka i metadanych, które są wyłącznie. W rezultacie drzewo wywołań nie można przygotować jako część wykresu CER i przerwań wątku, w tym poddrzewie nie mogą zostać automatycznie zablokowane. To zdarzenie MDA ostrzega o przypadkach, gdzie CER może być konieczne można rozszerzyć za pomocą jawnych wywołań <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> metoda po dodatkowe informacje wymagane do obliczenia cel wywołania jest znany w czasie wykonywania.  
  
## <a name="symptoms"></a>Symptomy  
 CERs, których nie jest uruchomiony, gdy wątek został przerwany lub domeny aplikacji jest zwalniana.  
  
## <a name="cause"></a>Przyczyna  
 CER zawiera wywołanie metody wirtualnej, którego nie można przygotować automatycznie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Wywołaj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
