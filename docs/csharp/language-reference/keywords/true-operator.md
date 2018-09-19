---
title: true — Operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45994588"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="87d3d-102">true — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="87d3d-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="87d3d-103">Zwraca [bool](../../../csharp/language-reference/keywords/bool.md) wartość `true` aby wskazać, że argument ma wartość true i zwraca `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="87d3d-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="87d3d-104">Przed C# w wersji 2.0 `true` i `false` operatorów były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="87d3d-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="87d3d-105">Jednak język teraz udostępnia wbudowaną obsługę typy o wartości zerowalnej i w miarę możliwości należy używać tych zamiast przeciążenia `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="87d3d-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="87d3d-106">Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="87d3d-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="87d3d-107">Za pomocą wartości logicznych dopuszczającego wartość null, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` , ponieważ co najmniej jeden z wartości może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="87d3d-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="87d3d-108">Musisz oba przeciążenia `true` i `false` operatory oddzielnie, aby wykryć wartości null w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="87d3d-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="87d3d-109">Poniższy przykład pokazuje, jak przeciążenia i użyj `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="87d3d-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 <span data-ttu-id="87d3d-110">Typ, który przeciążenia `true` i `false` operatorzy mogą służyć do kontrolowania wyrażenia w [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), i [ Aby uzyskać](../../../csharp/language-reference/keywords/for.md) instrukcji i [wyrażenia warunkowe](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="87d3d-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="87d3d-111">Jeśli typ definiuje operator `true`, również muszą definiować operator [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="87d3d-111">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="87d3d-112">Typ bezpośrednio nie mogą przeciążać operatory logiczne warunkowe ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ale taki sam efekt można osiągnąć przez przeciążenie zwykłych logiczne operatory i operatory `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="87d3d-112">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="87d3d-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="87d3d-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87d3d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87d3d-114">See Also</span></span>

- [<span data-ttu-id="87d3d-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="87d3d-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="87d3d-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="87d3d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="87d3d-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="87d3d-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="87d3d-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="87d3d-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="87d3d-119">false</span><span class="sxs-lookup"><span data-stu-id="87d3d-119">false</span></span>](../../../csharp/language-reference/keywords/false.md)
