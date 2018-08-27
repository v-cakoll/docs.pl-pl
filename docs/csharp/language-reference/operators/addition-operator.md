---
title: + Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930715"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cb8bd-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb8bd-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="cb8bd-103">`+` Operator może działać jako jednoargumentowy lub binarny.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb8bd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb8bd-104">Remarks</span></span>  
 <span data-ttu-id="cb8bd-105">Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="cb8bd-106">Wynik jednoargumentowy `+` operacja na typ liczbowy jest po prostu wartość operandu.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="cb8bd-107">Binarny `+` operatory są wstępnie zdefiniowane dla typów liczbowych i.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="cb8bd-108">Dla liczbowych typów i oblicza sumę dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="cb8bd-109">Kiedy jeden lub obydwa operandy są typu ciąg i łączy ciągów reprezentujących argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="cb8bd-110">Typy delegatów udostępniają dane binarne `+` operatora, który wykonuje łączenie delegatów.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="cb8bd-111">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `+` binarnej i `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="cb8bd-112">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="cb8bd-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="cb8bd-113">Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="cb8bd-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb8bd-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb8bd-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb8bd-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb8bd-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8bd-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb8bd-116">See Also</span></span>

- [<span data-ttu-id="cb8bd-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb8bd-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cb8bd-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cb8bd-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cb8bd-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="cb8bd-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="cb8bd-120">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb8bd-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
