---
title: '&amp; Operator (odwołanie w C#)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f26305bfa1e8c9ba45493ad2ab4937d554590911
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="b110a-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b110a-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="b110a-103">`&` Operator może działać jako jednoargumentowy lub operator binarny.</span><span class="sxs-lookup"><span data-stu-id="b110a-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b110a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b110a-104">Remarks</span></span>  
 <span data-ttu-id="b110a-105">Jednoargumentowego `&` adres jej argument zwraca (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).</span><span class="sxs-lookup"><span data-stu-id="b110a-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="b110a-106">Binarny `&` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="b110a-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="b110a-107">Dla typu całkowitego typy & oblicza logiczne i bitowe dla argumentów.</span><span class="sxs-lookup"><span data-stu-id="b110a-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="b110a-108">Dla `bool` operandy & oblicza logiczny i z argumentów; wynik jest `true` tylko wtedy, gdy są obie argumentów `true`.</span><span class="sxs-lookup"><span data-stu-id="b110a-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="b110a-109">Plik binarny `&` operator ocenia oba operatory niezależnie od pierwszego obiektu, w przeciwieństwie do wartości [operator warunkowy i](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="b110a-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="b110a-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b110a-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="b110a-111">Typy definiowane przez użytkownika można przeciążać plik binarny `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b110a-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b110a-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b110a-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="b110a-113">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="b110a-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b110a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b110a-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b110a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b110a-115">See Also</span></span>  
 [<span data-ttu-id="b110a-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b110a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b110a-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b110a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b110a-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b110a-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
