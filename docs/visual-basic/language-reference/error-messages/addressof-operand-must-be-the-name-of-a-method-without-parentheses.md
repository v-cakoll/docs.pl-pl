---
title: Operand „AddressOf" musi być nazwą metody (bez nawiasów)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323827"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="8ec86-102">Operand „AddressOf" musi być nazwą metody (bez nawiasów)</span><span class="sxs-lookup"><span data-stu-id="8ec86-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="8ec86-103">`AddressOf` Operator tworzy wystąpienie delegata procedury, która odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="8ec86-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="8ec86-104">Składnia jest następująca.</span><span class="sxs-lookup"><span data-stu-id="8ec86-104">The syntax is as follows.</span></span>  
  
 `AddressOf` `procedurename`  
  
 <span data-ttu-id="8ec86-105">Dodaje nawiasy wokół następujący argument `AddressOf`, których nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="8ec86-105">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="8ec86-106">**Identyfikator błędu:** BC30577</span><span class="sxs-lookup"><span data-stu-id="8ec86-106">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ec86-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8ec86-107">To correct this error</span></span>  
  
1. <span data-ttu-id="8ec86-108">Usuń nawiasy wokół następujący argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="8ec86-108">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="8ec86-109">Upewnij się, że argument jest nazwa metody.</span><span class="sxs-lookup"><span data-stu-id="8ec86-109">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec86-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ec86-110">See also</span></span>

- [<span data-ttu-id="8ec86-111">Operator AddressOf</span><span class="sxs-lookup"><span data-stu-id="8ec86-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="8ec86-112">Delegaty</span><span class="sxs-lookup"><span data-stu-id="8ec86-112">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
