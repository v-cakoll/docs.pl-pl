---
title: CS3024 ostrzeżenia kompilatora
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: e49c131328f132ae6372167818d084df51ef6c78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511558"
---
# <a name="compiler-warning-cs3024"></a>CS3024 ostrzeżenia kompilatora
Typ ograniczenia "type" nie jest zgodny ze specyfikacją CLS.  
  
 Kompilator generuje to ostrzeżenie, ponieważ korzystanie ze specyfikacją CLS niezgodne ze specyfikacją typu jako ograniczenia typu ogólnego może spowodować, że dla kodu napisanego w przypadku niektórych języków do korzystania z klasy ogólnej.  
  
### <a name="to-eliminate-this-warning"></a>Aby usunąć to ostrzeżenie  
  
1.  Użyj zgodnych ze specyfikacją CLS typu dla ograniczenia typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje CS3024 w kilku miejscach:  
  
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

- [Ograniczenia dotyczące parametrów typu](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
