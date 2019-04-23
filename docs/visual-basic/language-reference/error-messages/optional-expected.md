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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341884"
---
# <a name="optional-expected"></a><span data-ttu-id="41b78-102">Oczekiwano instrukcji „Optional”</span><span class="sxs-lookup"><span data-stu-id="41b78-102">'Optional' expected</span></span>
<span data-ttu-id="41b78-103">Opcjonalny argument w deklaracji procedury następuje wymaganego argumentu.</span><span class="sxs-lookup"><span data-stu-id="41b78-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="41b78-104">Każdy argument po opcjonalnym również musi być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="41b78-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="41b78-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="41b78-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41b78-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="41b78-106">To correct this error</span></span>  
  
1. <span data-ttu-id="41b78-107">Jeśli argument ma być wymagane, przenieś go poprzedzać pierwszy argument opcjonalne na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="41b78-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="41b78-108">Jeśli argument jest opcjonalny, użyj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="41b78-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b78-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b78-109">See also</span></span>

- [<span data-ttu-id="41b78-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="41b78-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
