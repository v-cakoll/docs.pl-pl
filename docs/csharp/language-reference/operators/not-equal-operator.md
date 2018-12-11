---
title: '! = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237821"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b5078-102">!= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b5078-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="b5078-103">Operator nierówności (`!=`) zwraca wartość false, jeśli jego operandy są takie same wartości true w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="b5078-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="b5078-104">Operatory nierówności są wstępnie zdefiniowane dla wszystkich typów, w tym ciągi i obiekty.</span><span class="sxs-lookup"><span data-stu-id="b5078-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="b5078-105">Typy definiowane przez użytkownika mogą przeciążać operator `!=`.</span><span class="sxs-lookup"><span data-stu-id="b5078-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5078-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5078-106">Remarks</span></span>  
 <span data-ttu-id="b5078-107">Dla wstępnie zdefiniowanych typów wartości, operator nierówności (`!=`) zwraca wartość true, jeśli wartości argumentów są różne, wartość false w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="b5078-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="b5078-108">Dla odwołania do typów innych niż `string`, `!=` zwraca wartość true, jeśli jego dwa operandy odnoszą się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="b5078-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="b5078-109">Aby uzyskać `string` typu `!=` porównuje wartości ciągów.</span><span class="sxs-lookup"><span data-stu-id="b5078-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="b5078-110">Typy wartości zdefiniowanej przez użytkownika może doprowadzić do przeciążenia `!=` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b5078-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b5078-111">Ty też typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `!=` zachowuje się jak opisano powyżej dla obu typów referencyjnych wstępnie zdefiniowanych i zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5078-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="b5078-112">Jeśli `!=` jest przeciążona, [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) musi również być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="b5078-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="b5078-113">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="b5078-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5078-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5078-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b5078-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5078-115">See Also</span></span>

- [<span data-ttu-id="b5078-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b5078-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b5078-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b5078-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b5078-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b5078-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
