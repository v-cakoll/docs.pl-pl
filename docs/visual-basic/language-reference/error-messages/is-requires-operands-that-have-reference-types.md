---
title: Element „Is” wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości „<typename>”.
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: e5acc94a3738fca3a43740bdba727fc843132aa1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402814"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="18d02-102">Element „Is” wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości „\<typename>”.</span><span class="sxs-lookup"><span data-stu-id="18d02-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="18d02-103">`Is`Operator porównania określa, czy dwie zmienne obiektów odwołują się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="18d02-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="18d02-104">To porównanie nie jest zdefiniowane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="18d02-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="18d02-105">**Identyfikator błędu:** BC30020</span><span class="sxs-lookup"><span data-stu-id="18d02-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18d02-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="18d02-106">To correct this error</span></span>  
  
- <span data-ttu-id="18d02-107">Użyj odpowiedniego operatora porównania arytmetycznego lub `Like` operatora, aby porównać dwa typy wartości.</span><span class="sxs-lookup"><span data-stu-id="18d02-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d02-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18d02-108">See also</span></span>

- [<span data-ttu-id="18d02-109">Is, operator</span><span class="sxs-lookup"><span data-stu-id="18d02-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="18d02-110">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="18d02-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="18d02-111">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="18d02-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
