---
title: '&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722923"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="60261-102">&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="60261-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="60261-103">`Is` Operator porównania określa, czy dwie zmienne do obiektu odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="60261-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="60261-104">To porównanie nie jest zdefiniowany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="60261-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="60261-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="60261-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60261-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="60261-106">To correct this error</span></span>  
  
-   <span data-ttu-id="60261-107">Użyj operatora porównania arytmetyczne odpowiednie lub `Like` operator do porównywania dwóch typów wartości.</span><span class="sxs-lookup"><span data-stu-id="60261-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60261-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60261-108">See also</span></span>
- [<span data-ttu-id="60261-109">Is, operator</span><span class="sxs-lookup"><span data-stu-id="60261-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="60261-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="60261-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="60261-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="60261-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
