---
title: Ostrzeżenie kompilatora CS3024
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 6147fc1aafc06d7c844cfc39eafebbd737d89610
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601961"
---
# <a name="compiler-warning-cs3024"></a>Ostrzeżenie kompilatora CS3024
Typ ograniczenia "Type" jest niezgodny ze specyfikacją CLS.  
  
 Kompilator wystawia to ostrzeżenie, ponieważ użycie typu niezgodnego ze specyfikacją CLS jako ograniczenia typu ogólnego może spowodować, że kod zapisany w niektórych językach będzie używać klasy generycznej.  
  
### <a name="to-eliminate-this-warning"></a>Aby wyeliminować to ostrzeżenie  
  
1. Użyj typu zgodnego ze specyfikacją CLS dla ograniczenia typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje CS3024 w kilku lokalizacjach:  
  
```csharp  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Ograniczenia dotyczące parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md)
