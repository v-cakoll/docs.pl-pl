---
title: '|= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 18246d013275c8d6c8ad7e05409387457afc3442
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171520"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c1f6e-102">|= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c1f6e-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="c1f6e-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="c1f6e-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1f6e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1f6e-104">Remarks</span></span>  
 <span data-ttu-id="c1f6e-105">Za pomocą wyrażenia `|=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="c1f6e-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="c1f6e-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="c1f6e-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="c1f6e-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="c1f6e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="c1f6e-108">[ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) dokonuje logicznego OR operacji na całkowite operandy i logiczne lub argumentów bool.</span><span class="sxs-lookup"><span data-stu-id="c1f6e-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="c1f6e-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c1f6e-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f6e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1f6e-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c1f6e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1f6e-111">See Also</span></span>  
 [<span data-ttu-id="c1f6e-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="c1f6e-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c1f6e-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1f6e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c1f6e-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c1f6e-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
