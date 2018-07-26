---
title: chronionych wewnętrznych (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244861"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="ad074-102">chronionych wewnętrznych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ad074-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="ad074-103">`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="ad074-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="ad074-104">Chronionych wewnętrznych składowych jest możliwy z bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="ad074-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="ad074-105">Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ad074-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="ad074-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad074-106">Example</span></span>  
 <span data-ttu-id="ad074-107">Chronionych wewnętrznych elementu członkowskiego klasy bazowej jest dostępna z dowolnego typu w ramach własnego zestawu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ad074-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="ad074-108">Jest również dostępna w klasie pochodnej znajduje się w innym zestawie, tylko wtedy, gdy dostęp odbywa się za pośrednictwem zmiennej o typie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="ad074-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="ad074-109">Na przykład rozważmy następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="ad074-109">For example, consider the following code segment:</span></span>  

```csharp
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
  
```csharp  
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
 <span data-ttu-id="ad074-110">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="ad074-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="ad074-111">Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz inną klasę `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="ad074-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="ad074-112">`BaseClass` jest właścicielem wewnętrzny elementu członkowskiego chronionego `myValue`, który jest dostępny po `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="ad074-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="ad074-113">W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` wystąpi błąd, podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ad074-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="ad074-114">Składowe struktury nie mogą być `protected internal` ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="ad074-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ad074-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ad074-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad074-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad074-116">See Also</span></span>  
 <span data-ttu-id="ad074-117">[Odwołanie w C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ad074-118">[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ad074-119">[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ad074-120">[Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="ad074-121">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="ad074-122">[Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="ad074-123">[Publiczne](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="ad074-124">[Prywatne](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="ad074-125">[Wewnętrzne](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="ad074-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="ad074-126">[Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="ad074-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
