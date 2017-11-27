---
title: "&amp;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="a5b68-102">&amp;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a5b68-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="a5b68-103">& — Operator może działać jako jednoargumentowy lub operator binarny.</span><span class="sxs-lookup"><span data-stu-id="a5b68-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5b68-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5b68-104">Remarks</span></span>  
 <span data-ttu-id="a5b68-105">Operator & jednoargumentowy zwraca adres jej argument operacji (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).</span><span class="sxs-lookup"><span data-stu-id="a5b68-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="a5b68-106">Dane binarne & operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="a5b68-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="a5b68-107">Dla typu całkowitego typy & oblicza logiczne i bitowe dla argumentów.</span><span class="sxs-lookup"><span data-stu-id="a5b68-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="a5b68-108">Dla `bool` operandy & oblicza logiczny i z argumentów; wynik jest `true` tylko wtedy, gdy są obie argumentów `true`.</span><span class="sxs-lookup"><span data-stu-id="a5b68-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="a5b68-109">`&` Operator ocenia oba operatory niezależnie od pierwszego elementu wartości.</span><span class="sxs-lookup"><span data-stu-id="a5b68-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="a5b68-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a5b68-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="a5b68-111">Typy definiowane przez użytkownika można przeciążać plik binarny `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="a5b68-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a5b68-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a5b68-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="a5b68-113">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="a5b68-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5b68-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5b68-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a5b68-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b68-115">See Also</span></span>  
 [<span data-ttu-id="a5b68-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a5b68-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a5b68-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5b68-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a5b68-118">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="a5b68-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
