---
title: '|= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 2abfbcbabb4229049c97aa6827abef3a053d6992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7f76a-102">|= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7f76a-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="7f76a-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="7f76a-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f76a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f76a-104">Remarks</span></span>  
 <span data-ttu-id="7f76a-105">Za pomocą wyrażenia `|=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="7f76a-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="7f76a-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="7f76a-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="7f76a-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="7f76a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="7f76a-108">[ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) dokonuje logicznego OR operacji na całkowite operandy i logiczne lub argumentów bool.</span><span class="sxs-lookup"><span data-stu-id="7f76a-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="7f76a-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7f76a-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f76a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f76a-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7f76a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f76a-111">See Also</span></span>  
 [<span data-ttu-id="7f76a-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="7f76a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f76a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7f76a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f76a-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="7f76a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
