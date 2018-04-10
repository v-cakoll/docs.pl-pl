---
title: = — Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a717b-102">= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a717b-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="a717b-103">Operator przypisania (`=`) przechowuje wartość jego prawostronny operand w lokalizacji przechowywania, właściwość lub indeksator wskazywane przez jej argument po lewej stronie i zwraca wartość wyniku.</span><span class="sxs-lookup"><span data-stu-id="a717b-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="a717b-104">Argumenty operacji musi być tego samego typu (lub prawostronny operand musi być umożliwiają niejawnej konwersji na typ lewego operandu).</span><span class="sxs-lookup"><span data-stu-id="a717b-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a717b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a717b-105">Remarks</span></span>  
 <span data-ttu-id="a717b-106">Operator przypisania nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="a717b-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="a717b-107">Można jednak zdefiniować operatory niejawnej konwersji typu, które umożliwiają korzystanie z tych typów operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="a717b-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="a717b-108">Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a717b-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a717b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a717b-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a717b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a717b-110">See Also</span></span>  
 [<span data-ttu-id="a717b-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a717b-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a717b-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a717b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a717b-113">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="a717b-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
