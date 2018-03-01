---
title: "&#39; AddressOf &#39; Argument musi być nazwą metody (bez nawiasów)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="5e521-102">&#39; AddressOf &#39; Argument musi być nazwą metody (bez nawiasów)</span><span class="sxs-lookup"><span data-stu-id="5e521-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="5e521-103">`AddressOf` Operator tworzy procedury wystąpienia delegata, który odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="5e521-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="5e521-104">Składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5e521-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="5e521-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="5e521-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="5e521-106">Dodaje nawiasy następujący argument `AddressOf`, gdy nie są jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="5e521-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="5e521-107">**Identyfikator błędu:** BC30577</span><span class="sxs-lookup"><span data-stu-id="5e521-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e521-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5e521-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="5e521-109">Usuń nawiasy następujący argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="5e521-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="5e521-110">Upewnij się, że argument jest nazwą metody.</span><span class="sxs-lookup"><span data-stu-id="5e521-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e521-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e521-111">See Also</span></span>  
 [<span data-ttu-id="5e521-112">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="5e521-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="5e521-113">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="5e521-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
