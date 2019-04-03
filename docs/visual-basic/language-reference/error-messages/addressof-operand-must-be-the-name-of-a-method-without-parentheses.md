---
title: Operand „AddressOf" musi być nazwą metody (bez nawiasów)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: af1ce858108785fa4dac6352c9e80531e86fbb23
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813967"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="13c20-102">Operand „AddressOf" musi być nazwą metody (bez nawiasów)</span><span class="sxs-lookup"><span data-stu-id="13c20-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="13c20-103">`AddressOf` Operator tworzy wystąpienie delegata procedury, która odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="13c20-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="13c20-104">Składnia jest następująca.</span><span class="sxs-lookup"><span data-stu-id="13c20-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="13c20-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="13c20-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="13c20-106">Dodaje nawiasy wokół następujący argument `AddressOf`, których nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="13c20-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="13c20-107">**Identyfikator błędu:** BC30577</span><span class="sxs-lookup"><span data-stu-id="13c20-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13c20-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="13c20-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="13c20-109">Usuń nawiasy wokół następujący argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="13c20-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="13c20-110">Upewnij się, że argument jest nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="13c20-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c20-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13c20-111">See also</span></span>

- [<span data-ttu-id="13c20-112">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="13c20-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="13c20-113">Delegaty</span><span class="sxs-lookup"><span data-stu-id="13c20-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
