---
title: "+ Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b15d5d1a304569b92b2f811a9ea714e4b30d60d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f443f-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f443f-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="f443f-103">`+` Operator może działać jako jednoargumentowy lub operator binarny.</span><span class="sxs-lookup"><span data-stu-id="f443f-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f443f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f443f-104">Remarks</span></span>  
 <span data-ttu-id="f443f-105">Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów numerycznych.</span><span class="sxs-lookup"><span data-stu-id="f443f-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="f443f-106">Wynik jednoargumentowy `+` operacji na typ liczbowy jest tylko wartość argumentu operacji.</span><span class="sxs-lookup"><span data-stu-id="f443f-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="f443f-107">Binarny `+` operatory są wstępnie zdefiniowane dla typu liczbowego i ciąg.</span><span class="sxs-lookup"><span data-stu-id="f443f-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="f443f-108">Dla numeryczne typy + oblicza sumę dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="f443f-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="f443f-109">Jeśli jeden lub obydwa argumenty operacji są typu ciąg + łączy reprezentacji ciągu argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="f443f-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="f443f-110">Typy delegatów również udostępniać dane binarne `+` operatora, który wykonuje łączenia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="f443f-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="f443f-111">Typy definiowane przez użytkownika można przeciążać jednoargumentowego `+` i binarne `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="f443f-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="f443f-112">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="f443f-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="f443f-113">Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="f443f-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f443f-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f443f-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f443f-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f443f-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f443f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f443f-116">See Also</span></span>  
 [<span data-ttu-id="f443f-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f443f-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f443f-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f443f-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f443f-119">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="f443f-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f443f-120">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f443f-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
