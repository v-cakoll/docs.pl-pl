---
title: '&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583815"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="c6d51-102">&#39;AddressOf&#39; operand musi być nazwą metody (bez nawiasów)</span><span class="sxs-lookup"><span data-stu-id="c6d51-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="c6d51-103">`AddressOf` Operator tworzy procedury wystąpienia delegata, który odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="c6d51-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="c6d51-104">Składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="c6d51-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="c6d51-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="c6d51-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="c6d51-106">Dodaje nawiasy następujący argument `AddressOf`, gdy nie są jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="c6d51-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="c6d51-107">**Identyfikator błędu:** BC30577</span><span class="sxs-lookup"><span data-stu-id="c6d51-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6d51-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c6d51-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c6d51-109">Usuń nawiasy następujący argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="c6d51-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="c6d51-110">Upewnij się, że argument jest nazwą metody.</span><span class="sxs-lookup"><span data-stu-id="c6d51-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d51-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6d51-111">See Also</span></span>  
 [<span data-ttu-id="c6d51-112">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="c6d51-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="c6d51-113">Delegaci</span><span class="sxs-lookup"><span data-stu-id="c6d51-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
