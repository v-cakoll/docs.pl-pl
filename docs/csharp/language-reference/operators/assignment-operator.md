---
title: = — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 9cd1af400a9afdb7942a49dee7e7f7bb78387f2d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43477935"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0e3fe-102">= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0e3fe-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="0e3fe-103">Operator przypisania (`=`) przechowuje wartość swojego prawostronnego argumentu operacji w lokalizacji przechowywania, właściwości lub indeksatorze wskazywanym przez jego lewostronny argument, a następnie zwraca wartość jako wynik.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="0e3fe-104">Argumenty operacji muszą być tego samego typu (lub prawostronny argument operacji musi umożliwiać konwersję na typ argumentu lewostronnego).</span><span class="sxs-lookup"><span data-stu-id="0e3fe-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e3fe-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e3fe-105">Remarks</span></span>  
 <span data-ttu-id="0e3fe-106">Operator przypisania nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="0e3fe-107">Można jednak zdefiniować niejawne operatory konwersji typu, które umożliwiają korzystanie z operatora przypisania w połączeniu z tymi typami.</span><span class="sxs-lookup"><span data-stu-id="0e3fe-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="0e3fe-108">Aby uzyskać więcej informacji, zobacz [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0e3fe-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e3fe-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e3fe-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0e3fe-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e3fe-110">See Also</span></span>

- [<span data-ttu-id="0e3fe-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0e3fe-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0e3fe-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0e3fe-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0e3fe-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0e3fe-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
