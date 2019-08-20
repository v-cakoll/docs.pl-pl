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
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="09512-102">Ostrzeżenie kompilatora CS3024</span><span class="sxs-lookup"><span data-stu-id="09512-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="09512-103">Typ ograniczenia "Type" jest niezgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="09512-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="09512-104">Kompilator wystawia to ostrzeżenie, ponieważ użycie typu niezgodnego ze specyfikacją CLS jako ograniczenia typu ogólnego może spowodować, że kod zapisany w niektórych językach będzie używać klasy generycznej.</span><span class="sxs-lookup"><span data-stu-id="09512-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="09512-105">Aby wyeliminować to ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="09512-105">To eliminate this warning</span></span>  
  
1. <span data-ttu-id="09512-106">Użyj typu zgodnego ze specyfikacją CLS dla ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="09512-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09512-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="09512-107">Example</span></span>  
 <span data-ttu-id="09512-108">Poniższy przykład generuje CS3024 w kilku lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="09512-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09512-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09512-109">See also</span></span>

- [<span data-ttu-id="09512-110">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="09512-110">Constraints on Type Parameters</span></span>](../programming-guide/generics/constraints-on-type-parameters.md)
