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
ms.openlocfilehash: 49ba4e7ca0b8ed2e433053130bc9ca2742c72ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217193"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` zarządzanego asystenta debugowania (MDA) jest uaktywniana jako ostrzeżenie wskazujące, że lokacja wywołania w ramach wykresu wywołania ograniczonego wykonania (CER) odnosi się do wirtualnego elementu docelowego, czyli wywołania wirtualnego do niekońcowej metody wirtualnej lub wywołania przy użyciu interfejsu. Środowisko uruchomieniowe języka wspólnego (CLR) nie może przewidzieć metody docelowej tych wywołań z poziomu języka pośredniego i analizy metadanych. W związku z tym drzewo wywołań nie może zostać przygotowane jako część wykresu CER, a przerwania wątku w tym poddrzewie nie mogą zostać automatycznie zablokowane. To zdarzenie powoduje ostrzeganie o przypadkach, w których może być konieczne rozszerzenie CER, za pomocą jawnych wywołań metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.  
  
## <a name="symptoms"></a>Objawy  
 CERs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji jest zwolniona.  
  
## <a name="cause"></a>Przyczyna  
 CER zawiera wywołanie metody wirtualnej, która nie może zostać przygotowana automatycznie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Wywołaj <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> dla metody wirtualnej.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
  
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
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
