---
title: CS3024 ostrzeżenia kompilatora
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: c4c2f915d6172e3c30fc32c5c57fe9921c3f915d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280348"
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="e1348-102">CS3024 ostrzeżenia kompilatora</span><span class="sxs-lookup"><span data-stu-id="e1348-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="e1348-103">Typ ograniczenia "type" nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="e1348-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="e1348-104">Kompilator generuje to ostrzeżenie, ponieważ użycie specyfikacją CLS typu jako ograniczenia typu ogólnego może uniemożliwić kod napisany w przypadku niektórych języków do korzystania z klasy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="e1348-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="e1348-105">Aby wyeliminować to ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="e1348-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="e1348-106">Użyj zgodnych ze specyfikacją CLS typu dla ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="e1348-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1348-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1348-107">Example</span></span>  
 <span data-ttu-id="e1348-108">Poniższy przykład generuje CS3024 w wielu lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="e1348-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1348-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1348-109">See Also</span></span>  
 [<span data-ttu-id="e1348-110">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="e1348-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
