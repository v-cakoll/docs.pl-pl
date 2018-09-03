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
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467377"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="0257b-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0257b-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="0257b-103">`&` Operator może działać jako jednoargumentowy lub binarny.</span><span class="sxs-lookup"><span data-stu-id="0257b-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0257b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0257b-104">Remarks</span></span>  
 <span data-ttu-id="0257b-105">Jednoargumentowy `&` operator zwraca adres jego operandu (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).</span><span class="sxs-lookup"><span data-stu-id="0257b-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="0257b-106">Operatory binarne `&` są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="0257b-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="0257b-107">Dla całkowite typy i oblicza logiczne bitowe AND swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="0257b-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="0257b-108">Dla `bool` operandy & oblicza logicznym i jego operandu; oznacza to wynik jest `true` tylko wtedy, gdy oba jego operandy są `true`.</span><span class="sxs-lookup"><span data-stu-id="0257b-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="0257b-109">Plik binarny `&` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operatora warunkowego i](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="0257b-109">The binary `&` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="0257b-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0257b-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="0257b-111">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0257b-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="0257b-112">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="0257b-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="0257b-113">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="0257b-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0257b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0257b-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0257b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0257b-115">See Also</span></span>

- [<span data-ttu-id="0257b-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0257b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0257b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0257b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0257b-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0257b-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
