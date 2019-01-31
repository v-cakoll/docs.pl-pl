---
title: Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 367da8e7c9fd8c14a16a09b1f023e7637d78309d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259560"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="662ce-102">Wiodący znak „.” lub „!” może wystąpić tylko wewnątrz instrukcji „With”</span><span class="sxs-lookup"><span data-stu-id="662ce-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="662ce-103">Kropka (.) lub wykrzyknika (!) nie jest w obrębie `With` bloku odbywa się bez wyrażenie po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="662ce-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="662ce-104">Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie, określając element, który zawiera element członkowski.</span><span class="sxs-lookup"><span data-stu-id="662ce-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="662ce-105">Musi występować bezpośrednio po lewej stronie metody dostępu lub jako obiekt docelowy `With` bloku, zawierającego dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="662ce-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="662ce-106">**Identyfikator błędu:** BC30157</span><span class="sxs-lookup"><span data-stu-id="662ce-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="662ce-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="662ce-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="662ce-108">Upewnij się, że `With` bloku jest poprawnie sformatowana.</span><span class="sxs-lookup"><span data-stu-id="662ce-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="662ce-109">W przypadku nie `With` zablokować, Dodaj wyrażenie po lewej stronie metodę dostępu, która ocenia do elementu zdefiniowanego zawierający element członkowski.</span><span class="sxs-lookup"><span data-stu-id="662ce-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662ce-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="662ce-110">See also</span></span>
- [<span data-ttu-id="662ce-111">Znaki specjalne w kodzie</span><span class="sxs-lookup"><span data-stu-id="662ce-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="662ce-112">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="662ce-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
