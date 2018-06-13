---
title: '&amp; Operator (odwołanie w C#)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267883"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="775d1-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="775d1-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="775d1-103">`&` Operator może działać jako jednoargumentowy lub operator binarny.</span><span class="sxs-lookup"><span data-stu-id="775d1-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="775d1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="775d1-104">Remarks</span></span>  
 <span data-ttu-id="775d1-105">Jednoargumentowego `&` adres jej argument zwraca (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).</span><span class="sxs-lookup"><span data-stu-id="775d1-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="775d1-106">Binarny `&` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="775d1-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="775d1-107">Dla typu całkowitego typy & oblicza logiczne i bitowe dla argumentów.</span><span class="sxs-lookup"><span data-stu-id="775d1-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="775d1-108">Dla `bool` operandy & oblicza logiczny i z argumentów; wynik jest `true` tylko wtedy, gdy są obie argumentów `true`.</span><span class="sxs-lookup"><span data-stu-id="775d1-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="775d1-109">Plik binarny `&` operator ocenia oba operatory niezależnie od pierwszego obiektu, w przeciwieństwie do wartości [operator warunkowy i](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="775d1-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="775d1-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="775d1-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="775d1-111">Typy definiowane przez użytkownika można przeciążać plik binarny `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="775d1-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="775d1-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="775d1-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="775d1-113">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="775d1-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="775d1-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="775d1-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="775d1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="775d1-115">See Also</span></span>  
 [<span data-ttu-id="775d1-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="775d1-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="775d1-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="775d1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="775d1-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="775d1-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
