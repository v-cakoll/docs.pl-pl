---
title: prywatne chronione (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: ee36cc713dd5fdb90ae20ef992f8e75eca09597d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="1017b-102">prywatne chronione (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1017b-102">private protected (C# Reference)</span></span>
<span data-ttu-id="1017b-103">`private protected` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1017b-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="1017b-104">Prywatny chroniony element członkowski jest dostępny przez typy pochodzące z zawierający klasy, ale tylko w obrębie zawierający go zestaw.</span><span class="sxs-lookup"><span data-stu-id="1017b-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="1017b-105">Porównanie `private protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1017b-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="1017b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1017b-106">Example</span></span>  
 <span data-ttu-id="1017b-107">Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w zawierający go zestaw, tylko wtedy, gdy statycznych typu zmiennej typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1017b-107">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="1017b-108">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="1017b-108">For example, consider the following code segment:</span></span>  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="1017b-109">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="1017b-109">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="1017b-110">Pierwszy plik zawiera klasę podstawową publicznego `BaseClass`i typu pochodnego w `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="1017b-110">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="1017b-111">`BaseClass` właścicielem prywatny chroniony element członkowski, `myValue`, który `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="1017b-111">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="1017b-112">Pierwsza próba uzyskania dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="1017b-112">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="1017b-113">Jednak próba używać go jako dziedziczonego elementu członkowskiego w `DerivedClass1` powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="1017b-113">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="1017b-114">W drugim pliku, próba uzyskania dostępu do `myValue` jako dziedziczonego elementu członkowskiego z `DerivedClass2` spowoduje błąd, są one dostępne przez typy pochodne w zestaw1 wyłącznie.</span><span class="sxs-lookup"><span data-stu-id="1017b-114">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="1017b-115">Członkowie struktury nie mogą być `private protected` ponieważ struktury nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="1017b-115">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1017b-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1017b-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1017b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1017b-117">See Also</span></span>  
 <span data-ttu-id="1017b-118">[Odwołanie w C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1017b-119">[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1017b-120">[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1017b-121">[Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="1017b-122">[Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="1017b-123">[Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="1017b-124">[Publiczna](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="1017b-125">[Prywatne](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="1017b-126">[wewnętrzny](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="1017b-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="1017b-127">[Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="1017b-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
