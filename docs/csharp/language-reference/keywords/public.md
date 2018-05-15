---
title: public (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: abf7219359c108108b1ce3a3fde3dc10f9a8732d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="public-c-reference"></a><span data-ttu-id="7aa65-102">public (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7aa65-102">public (C# Reference)</span></span>
<span data-ttu-id="7aa65-103">`public` — Słowo kluczowe jest modyfikator dostępu dla typów i członków typu.</span><span class="sxs-lookup"><span data-stu-id="7aa65-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="7aa65-104">Dostęp publiczny jest najbardziej ograniczająca poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="7aa65-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="7aa65-105">Nie ma żadnych ograniczeń na dostęp do publicznych członków, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7aa65-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="7aa65-106">Zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7aa65-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aa65-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7aa65-107">Example</span></span>  
 <span data-ttu-id="7aa65-108">W poniższym przykładzie są deklarowane jako dwie klasy, `PointTest` i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7aa65-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="7aa65-109">Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7aa65-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="7aa65-110">Jeśli zmienisz `public` poziom dostępu do [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [chronione](../../../csharp/language-reference/keywords/protected.md), otrzymasz komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="7aa65-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="7aa65-111">"PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="7aa65-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7aa65-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7aa65-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7aa65-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7aa65-113">See Also</span></span>  
 [<span data-ttu-id="7aa65-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="7aa65-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7aa65-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7aa65-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7aa65-116">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="7aa65-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="7aa65-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7aa65-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7aa65-118">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="7aa65-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="7aa65-119">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="7aa65-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="7aa65-120">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7aa65-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="7aa65-121">private</span><span class="sxs-lookup"><span data-stu-id="7aa65-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="7aa65-122">protected</span><span class="sxs-lookup"><span data-stu-id="7aa65-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="7aa65-123">internal</span><span class="sxs-lookup"><span data-stu-id="7aa65-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
