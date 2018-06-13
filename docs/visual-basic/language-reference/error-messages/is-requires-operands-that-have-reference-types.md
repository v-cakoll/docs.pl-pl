---
title: '&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 07838e62bd6b180f7dece79355ea7aa1d6c4527a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585583"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="6a4b5-102">&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6a4b5-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="6a4b5-103">`Is` Operator porównania określa, czy dwie zmienne obiektu odwoływać się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6a4b5-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="6a4b5-104">To porównanie nie jest zdefiniowany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="6a4b5-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="6a4b5-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="6a4b5-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a4b5-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6a4b5-106">To correct this error</span></span>  
  
-   <span data-ttu-id="6a4b5-107">Użycie operatora porównania arytmetyczne odpowiednie lub `Like` operatora, aby porównać dwa typy wartości.</span><span class="sxs-lookup"><span data-stu-id="6a4b5-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4b5-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a4b5-108">See Also</span></span>  
 [<span data-ttu-id="6a4b5-109">Is, operator</span><span class="sxs-lookup"><span data-stu-id="6a4b5-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="6a4b5-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="6a4b5-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="6a4b5-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="6a4b5-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
