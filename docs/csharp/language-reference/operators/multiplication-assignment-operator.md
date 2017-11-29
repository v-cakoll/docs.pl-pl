---
title: "Operator *= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1f335-102">Operator *= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1f335-102">*= Operator (C# Reference)</span></span>
<span data-ttu-id="1f335-103">Operator przypisania mnożenia danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="1f335-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f335-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f335-104">Remarks</span></span>  
 <span data-ttu-id="1f335-105">Za pomocą wyrażenia `*=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="1f335-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="1f335-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="1f335-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="1f335-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="1f335-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1f335-108">[* — Operator](../../../csharp/language-reference/operators/multiplication-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania mnożenia.</span><span class="sxs-lookup"><span data-stu-id="1f335-108">The [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="1f335-109">`*=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [* — operator](../../../csharp/language-reference/operators/multiplication-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1f335-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f335-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f335-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1f335-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f335-111">See Also</span></span>  
 [<span data-ttu-id="1f335-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="1f335-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1f335-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1f335-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1f335-114">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="1f335-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
