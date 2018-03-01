---
title: "public (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 197ef4a2a8544d439b0c34ec14bb7752b760ea06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="public-c-reference"></a><span data-ttu-id="6461b-102">public (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6461b-102">public (C# Reference)</span></span>
<span data-ttu-id="6461b-103">`public` — Słowo kluczowe jest modyfikator dostępu dla typów i członków typu.</span><span class="sxs-lookup"><span data-stu-id="6461b-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="6461b-104">Dostęp publiczny jest najbardziej ograniczająca poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="6461b-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="6461b-105">Nie ma żadnych ograniczeń na dostęp do publicznych członków, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6461b-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="6461b-106">Zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6461b-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6461b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6461b-107">Example</span></span>  
 <span data-ttu-id="6461b-108">W poniższym przykładzie są deklarowane jako dwie klasy, `PointTest` i `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="6461b-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="6461b-109">Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="6461b-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="6461b-110">Jeśli zmienisz `public` poziom dostępu do [prywatnej](../../../csharp/language-reference/keywords/private.md) lub [chronione](../../../csharp/language-reference/keywords/protected.md), otrzymasz komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="6461b-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="6461b-111">"PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="6461b-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6461b-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6461b-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6461b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6461b-113">See Also</span></span>  
 [<span data-ttu-id="6461b-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6461b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6461b-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6461b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6461b-116">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="6461b-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="6461b-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6461b-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6461b-118">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="6461b-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="6461b-119">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="6461b-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="6461b-120">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6461b-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="6461b-121">prywatne</span><span class="sxs-lookup"><span data-stu-id="6461b-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="6461b-122">chronione</span><span class="sxs-lookup"><span data-stu-id="6461b-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="6461b-123">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="6461b-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
