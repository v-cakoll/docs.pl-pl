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
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232387"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4be85-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4be85-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="4be85-103">`+` Operator może działać jako jednoargumentowy lub binarny.</span><span class="sxs-lookup"><span data-stu-id="4be85-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4be85-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4be85-104">Remarks</span></span>  
 <span data-ttu-id="4be85-105">Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="4be85-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="4be85-106">Wynik jednoargumentowy `+` operacja na typ liczbowy jest po prostu wartość operandu.</span><span class="sxs-lookup"><span data-stu-id="4be85-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="4be85-107">Binarny `+` operatory są wstępnie zdefiniowane dla typów liczbowych i.</span><span class="sxs-lookup"><span data-stu-id="4be85-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="4be85-108">Dla liczbowych typów i oblicza sumę dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="4be85-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="4be85-109">Kiedy jeden lub obydwa operandy są typu ciąg i łączy ciągów reprezentujących argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="4be85-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="4be85-110">Typy delegatów udostępniają dane binarne `+` operatora, który wykonuje łączenie delegatów.</span><span class="sxs-lookup"><span data-stu-id="4be85-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="4be85-111">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `+` binarnej i `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="4be85-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="4be85-112">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="4be85-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="4be85-113">Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="4be85-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4be85-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4be85-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4be85-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4be85-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4be85-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4be85-116">See Also</span></span>

- [<span data-ttu-id="4be85-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4be85-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4be85-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4be85-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4be85-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4be85-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="4be85-120">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4be85-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
