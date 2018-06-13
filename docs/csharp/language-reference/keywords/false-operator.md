---
title: false — Operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f2001d92e99476131d6f03e13f0bc12104f638b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218261"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="c8da8-102">false — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c8da8-102">false Operator (C# Reference)</span></span>
<span data-ttu-id="c8da8-103">Zwraca [bool](../../../csharp/language-reference/keywords/bool.md) wartość `true` do wskazywania operand `false` i zwraca `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="c8da8-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="c8da8-104">Przed C# 2.0 `true` i `false` operatory były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="c8da8-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="c8da8-105">Jednak język teraz udostępnia wbudowaną obsługę dla typów wartości null, a w miarę możliwości należy używać tych zamiast przeładowanie `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="c8da8-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="c8da8-106">Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8da8-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="c8da8-107">O wartości null wartości logiczne, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` ponieważ jedną lub obie wartości może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="c8da8-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="c8da8-108">Masz przeciążenia obu `true` i `false` operatorom oddzielnie poprawnie Obsługa wartości zerowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c8da8-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="c8da8-109">Poniższy przykład przedstawia sposób przeciążenia i użyj `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="c8da8-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 <span data-ttu-id="c8da8-110">Typ, który overloads `true` i `false` operatorów można używać do kontrolowania wyrażenie w [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), i [ Aby uzyskać](../../../csharp/language-reference/keywords/for.md) instrukcje i [wyrażenia warunkowe](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c8da8-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="c8da8-111">Jeśli typ definiuje operator `false`, również muszą definiować operator [true](../../../csharp/language-reference/keywords/true.md).</span><span class="sxs-lookup"><span data-stu-id="c8da8-111">If a type defines operator `false`, it must also define operator [true](../../../csharp/language-reference/keywords/true.md).</span></span>  
  
 <span data-ttu-id="c8da8-112">Typem bezpośrednio nie mogą przeciążać operatory logiczne warunkowe [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), ale sam efekt można osiągnąć przez przeładowanie operatorów logicznych regularne operatory i `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="c8da8-112">A type cannot directly overload the conditional logical operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c8da8-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c8da8-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8da8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8da8-114">See Also</span></span>  
 [<span data-ttu-id="c8da8-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c8da8-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c8da8-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c8da8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c8da8-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c8da8-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c8da8-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c8da8-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c8da8-119">true</span><span class="sxs-lookup"><span data-stu-id="c8da8-119">true</span></span>](../../../csharp/language-reference/keywords/true.md)
