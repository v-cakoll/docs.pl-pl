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
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
Zarządzany `virtualCERCall` asystent debugowania (MDA) jest aktywowany jako ostrzeżenie wskazujące, że lokacja wywołania w ramach wykresu wywołania regionu ograniczonego wykonywania (CER) odnosi się do wirtualnego obiektu docelowego, czyli wirtualnego wywołania niekonfekcyjnej metody wirtualnej lub wywołania przy użyciu interfejsu. Środowisko wykonawcze języka wspólnego (CLR) nie można przewidzieć metody docelowej tych wywołań z pośredniego języka i analizy metadanych sam. W rezultacie drzewa wywołań nie można przygotować jako część wykresu CER i przerywanie wątku w tym poddrzewie nie może być automatycznie blokowane. Ten obiekt MDA ostrzega o przypadkach, w których cer może <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> wymagać rozszerzenia przy użyciu jawnych wywołań metody, gdy dodatkowe informacje wymagane do obliczenia obiektu docelowego wywołania są znane w czasie wykonywania.  
  
## <a name="symptoms"></a>Objawy  
 CeRs, które nie są uruchamiane, gdy wątek zostanie przerwany lub domena aplikacji zostanie zwolniona.  
  
## <a name="cause"></a>Przyczyna  
 Cer zawiera wywołanie metody wirtualnej, która nie może być przygotowana automatycznie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zadzwoń <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> do metody wirtualnej.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To MDA nie ma wpływu na CLR.  
  
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
  
## <a name="configuration"></a>Konfigurowanie  
  
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
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
