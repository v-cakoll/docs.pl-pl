---
title: chronionych wewnętrznych (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a2a649f0fdb924c26380e7261bd935be736f0665
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="7e551-102">chronionych wewnętrznych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7e551-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="7e551-103">`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7e551-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="7e551-104">Chroniony element członkowski wewnętrznego jest dostępny, z bieżącego zestawu lub typów pochodzących od klasy zawierającego.</span><span class="sxs-lookup"><span data-stu-id="7e551-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="7e551-105">Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7e551-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="7e551-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e551-106">Example</span></span>  
 <span data-ttu-id="7e551-107">Wewnętrzny chroniony element członkowski klasy podstawowej jest dostępna z dowolnego typu, w ramach zawierający go zestaw.</span><span class="sxs-lookup"><span data-stu-id="7e551-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="7e551-108">Jest również dostępna w klasie pochodnej, która znajduje się w innym zestawie tylko wtedy, gdy występuje dostęp za pośrednictwem zmiennej typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7e551-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="7e551-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="7e551-109">For example, consider the following code segment:</span></span>  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="7e551-110">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="7e551-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="7e551-111">Pierwszy plik zawiera klasę podstawową publicznego `BaseClass`, a inna klasa `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="7e551-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="7e551-112">`BaseClass` właścicielem członka chronionego wewnętrzny `myValue`, który jest dostępny po `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="7e551-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="7e551-113">W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` utworzy wystąpił błąd podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7e551-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="7e551-114">Członkowie struktury nie mogą być `protected internal` ponieważ struktury nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="7e551-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7e551-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7e551-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e551-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e551-116">See Also</span></span>  
 <span data-ttu-id="7e551-117">[Odwołanie w C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7e551-118">[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7e551-119">[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="7e551-120">[Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="7e551-121">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="7e551-122">[Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="7e551-123">[Publiczna](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="7e551-124">[Prywatne](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="7e551-125">[wewnętrzny](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="7e551-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="7e551-126">[Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="7e551-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
