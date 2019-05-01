---
title: Oczekiwano instrukcji „Optional”
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 71a25784f357a7e596093b314ed5b3d721d6f92c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946591"
---
# <a name="optional-expected"></a><span data-ttu-id="8b5a2-102">Oczekiwano instrukcji „Optional”</span><span class="sxs-lookup"><span data-stu-id="8b5a2-102">'Optional' expected</span></span>
<span data-ttu-id="8b5a2-103">Opcjonalny argument w deklaracji procedury następuje wymaganego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="8b5a2-104">Każdy argument po opcjonalnym również musi być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="8b5a2-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="8b5a2-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8b5a2-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8b5a2-106">To correct this error</span></span>  
  
1. <span data-ttu-id="8b5a2-107">Jeśli argument ma być wymagane, przenieś go poprzedzać pierwszy argument opcjonalne na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="8b5a2-108">Jeśli argument jest opcjonalny, użyj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5a2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5a2-109">See also</span></span>

- [<span data-ttu-id="8b5a2-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="8b5a2-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
