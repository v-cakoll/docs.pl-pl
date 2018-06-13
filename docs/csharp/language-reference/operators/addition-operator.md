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
ms.openlocfilehash: d4a269c07e0d6dc2ac6a6a101f200653c6ea7a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267410"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="13ef6-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="13ef6-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="13ef6-103">`+` Operator może działać jako jednoargumentowy lub operator binarny.</span><span class="sxs-lookup"><span data-stu-id="13ef6-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13ef6-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13ef6-104">Remarks</span></span>  
 <span data-ttu-id="13ef6-105">Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="13ef6-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="13ef6-106">Wynik jednoargumentowy `+` operacji na typ liczbowy jest tylko wartość argumentu operacji.</span><span class="sxs-lookup"><span data-stu-id="13ef6-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="13ef6-107">Binarny `+` operatory są wstępnie zdefiniowane dla typu liczbowego i ciąg.</span><span class="sxs-lookup"><span data-stu-id="13ef6-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="13ef6-108">Dla numeryczne typy + oblicza sumę dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="13ef6-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="13ef6-109">Jeśli jeden lub obydwa argumenty operacji są typu ciąg + łączy reprezentacji ciągu argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="13ef6-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="13ef6-110">Typy delegatów również udostępniać dane binarne `+` operatora, który wykonuje łączenia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="13ef6-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="13ef6-111">Typy definiowane przez użytkownika można przeciążać jednoargumentowego `+` i binarne `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="13ef6-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="13ef6-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="13ef6-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="13ef6-113">Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="13ef6-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ef6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef6-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="13ef6-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13ef6-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13ef6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef6-116">See Also</span></span>  
 [<span data-ttu-id="13ef6-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="13ef6-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="13ef6-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13ef6-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="13ef6-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="13ef6-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="13ef6-120">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="13ef6-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
