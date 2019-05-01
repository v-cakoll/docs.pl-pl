---
title: Element „Is” wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości „<typename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: b828de196a12128a9f34ee1f9ff1e57fee22c687
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799193"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="6e8c4-102">"Is" wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości "\<typename >"</span><span class="sxs-lookup"><span data-stu-id="6e8c4-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="6e8c4-103">`Is` Operator porównania określa, czy dwie zmienne do obiektu odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6e8c4-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="6e8c4-104">To porównanie nie jest zdefiniowany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="6e8c4-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="6e8c4-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="6e8c4-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e8c4-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6e8c4-106">To correct this error</span></span>  
  
- <span data-ttu-id="6e8c4-107">Użyj operatora porównania arytmetyczne odpowiednie lub `Like` operator do porównywania dwóch typów wartości.</span><span class="sxs-lookup"><span data-stu-id="6e8c4-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8c4-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e8c4-108">See also</span></span>

- [<span data-ttu-id="6e8c4-109">Is, operator</span><span class="sxs-lookup"><span data-stu-id="6e8c4-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="6e8c4-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="6e8c4-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="6e8c4-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="6e8c4-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
