---
title: = — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1bea6-102">= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1bea6-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="1bea6-103">Operator przypisania (`=`) przechowuje wartość jego prawostronny operand w lokalizacji przechowywania, właściwość lub indeksator wskazywane przez jej argument po lewej stronie i zwraca wartość wyniku.</span><span class="sxs-lookup"><span data-stu-id="1bea6-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="1bea6-104">Argumenty operacji musi być tego samego typu (lub prawostronny operand musi być umożliwiają niejawnej konwersji na typ lewego operandu).</span><span class="sxs-lookup"><span data-stu-id="1bea6-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bea6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bea6-105">Remarks</span></span>  
 <span data-ttu-id="1bea6-106">Operator przypisania nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="1bea6-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="1bea6-107">Można jednak zdefiniować operatory niejawnej konwersji typu, które umożliwiają korzystanie z tych typów operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="1bea6-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="1bea6-108">Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1bea6-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bea6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bea6-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1bea6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bea6-110">See Also</span></span>  
 [<span data-ttu-id="1bea6-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="1bea6-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1bea6-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1bea6-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bea6-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1bea6-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
