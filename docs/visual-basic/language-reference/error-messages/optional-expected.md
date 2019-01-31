---
title: Oczekiwano instrukcji „Optional”
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 0ad0d0890b73103a0678b13409a24190329d37d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266337"
---
# <a name="optional-expected"></a><span data-ttu-id="5ee66-102">Oczekiwano instrukcji „Optional”</span><span class="sxs-lookup"><span data-stu-id="5ee66-102">'Optional' expected</span></span>
<span data-ttu-id="5ee66-103">Opcjonalny argument w deklaracji procedury następuje wymaganego argumentu.</span><span class="sxs-lookup"><span data-stu-id="5ee66-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="5ee66-104">Każdy argument po opcjonalnym również musi być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5ee66-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="5ee66-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="5ee66-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ee66-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5ee66-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="5ee66-107">Jeśli argument ma być wymagane, przenieś go poprzedzać pierwszy argument opcjonalne na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="5ee66-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="5ee66-108">Jeśli argument jest opcjonalny, użyj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5ee66-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee66-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee66-109">See also</span></span>
- [<span data-ttu-id="5ee66-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="5ee66-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
