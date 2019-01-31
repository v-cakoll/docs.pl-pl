---
title: Element „Is” wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości „<typename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: fbd0011e76ccecc605b0355025b7ca131e44724e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263937"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="c5d38-102">"Is" wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości "\<typename >"</span><span class="sxs-lookup"><span data-stu-id="c5d38-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="c5d38-103">`Is` Operator porównania określa, czy dwie zmienne do obiektu odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c5d38-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="c5d38-104">To porównanie nie jest zdefiniowany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="c5d38-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="c5d38-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="c5d38-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5d38-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c5d38-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c5d38-107">Użyj operatora porównania arytmetyczne odpowiednie lub `Like` operator do porównywania dwóch typów wartości.</span><span class="sxs-lookup"><span data-stu-id="c5d38-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d38-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5d38-108">See also</span></span>
- [<span data-ttu-id="c5d38-109">Is, operator</span><span class="sxs-lookup"><span data-stu-id="c5d38-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="c5d38-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="c5d38-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="c5d38-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="c5d38-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
