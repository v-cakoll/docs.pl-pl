---
title: CS3024 ostrzeżenia kompilatora
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 5d8781117b80dbebe6a01488b8bd66feb12d3e3c
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43252911"
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="c8dbe-102">CS3024 ostrzeżenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="c8dbe-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="c8dbe-103">Typ ograniczenia "type" nie jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c8dbe-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="c8dbe-104">Kompilator generuje to ostrzeżenie, ponieważ korzystanie ze specyfikacją CLS niezgodne ze specyfikacją typu jako ograniczenia typu ogólnego może spowodować, że dla kodu napisanego w przypadku niektórych języków do korzystania z klasy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="c8dbe-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="c8dbe-105">Aby usunąć to ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="c8dbe-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="c8dbe-106">Użyj zgodnych ze specyfikacją CLS typu dla ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="c8dbe-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8dbe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8dbe-107">Example</span></span>  
 <span data-ttu-id="c8dbe-108">Poniższy przykład generuje CS3024 w kilku miejscach:</span><span class="sxs-lookup"><span data-stu-id="c8dbe-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8dbe-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8dbe-109">See Also</span></span>

- [<span data-ttu-id="c8dbe-110">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="c8dbe-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
