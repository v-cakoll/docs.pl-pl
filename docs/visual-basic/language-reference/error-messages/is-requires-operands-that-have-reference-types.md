---
title: "&#39; jest &#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28d017a566fdc1e55cb53ce907641d6bccfb354c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="dc38e-102">&#39; jest &#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="dc38e-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="dc38e-103">`Is` Operator porównania określa, czy dwie zmienne obiektu odwoływać się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dc38e-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="dc38e-104">To porównanie nie jest zdefiniowany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="dc38e-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="dc38e-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="dc38e-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dc38e-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dc38e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="dc38e-107">Użycie operatora porównania arytmetyczne odpowiednie lub `Like` operatora, aby porównać dwa typy wartości.</span><span class="sxs-lookup"><span data-stu-id="dc38e-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc38e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc38e-108">See Also</span></span>  
 [<span data-ttu-id="dc38e-109">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="dc38e-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="dc38e-110">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="dc38e-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="dc38e-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="dc38e-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
