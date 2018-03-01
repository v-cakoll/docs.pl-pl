---
title: "Operator /= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2c74a-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2c74a-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="2c74a-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="2c74a-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c74a-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c74a-104">Remarks</span></span>  
 <span data-ttu-id="2c74a-105">Za pomocą wyrażenia `/=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="2c74a-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="2c74a-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="2c74a-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="2c74a-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="2c74a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="2c74a-108">[/ — Operator](../../../csharp/language-reference/operators/division-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania podziału.</span><span class="sxs-lookup"><span data-stu-id="2c74a-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="2c74a-109">`/=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [/ — operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2c74a-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2c74a-110">Na wszystkich złożone operatory przypisania niejawnie przeciążanie operatora binarnego overloads równoważne przydział złożony.</span><span class="sxs-lookup"><span data-stu-id="2c74a-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c74a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c74a-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2c74a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c74a-112">See Also</span></span>  
 [<span data-ttu-id="2c74a-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2c74a-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2c74a-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2c74a-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2c74a-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="2c74a-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
