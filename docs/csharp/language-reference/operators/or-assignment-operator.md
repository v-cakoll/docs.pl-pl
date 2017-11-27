---
title: "|= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6c2f4-102">|= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6c2f4-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="6c2f4-103">Operator przypisania OR.</span><span class="sxs-lookup"><span data-stu-id="6c2f4-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c2f4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c2f4-104">Remarks</span></span>  
 <span data-ttu-id="6c2f4-105">Za pomocą wyrażenia `|=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="6c2f4-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="6c2f4-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="6c2f4-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="6c2f4-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="6c2f4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6c2f4-108">[&#124; operator](../../../csharp/language-reference/operators/or-operator.md) dokonuje logicznego OR operacji na całkowite operandy i logiczne lub argumentów bool.</span><span class="sxs-lookup"><span data-stu-id="6c2f4-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="6c2f4-109">`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6c2f4-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c2f4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c2f4-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6c2f4-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c2f4-111">See Also</span></span>  
 [<span data-ttu-id="6c2f4-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6c2f4-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6c2f4-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6c2f4-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c2f4-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="6c2f4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
