---
title: Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589450"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a><span data-ttu-id="46e01-102">Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja</span><span class="sxs-lookup"><span data-stu-id="46e01-102">Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement</span></span>
<span data-ttu-id="46e01-103">Kropki (.) lub wykrzyknika (!) nie jest który wewnątrz `With` bloku odbywa się bez wyrażenie po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="46e01-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="46e01-104">Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie określające element, który zawiera element członkowski.</span><span class="sxs-lookup"><span data-stu-id="46e01-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="46e01-105">Musi występować od razu po lewej stronie metody dostępu lub jako element docelowy `With` blok zawierający dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="46e01-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="46e01-106">**Identyfikator błędu:** BC30157</span><span class="sxs-lookup"><span data-stu-id="46e01-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46e01-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="46e01-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="46e01-108">Upewnij się, że `With` bloku jest poprawnie sformatowana.</span><span class="sxs-lookup"><span data-stu-id="46e01-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="46e01-109">W przypadku nie `With` bloków, Dodaj wyrażenie w lewo metody dostępu, która ocenia zdefiniowanego elementu zawierający element członkowski.</span><span class="sxs-lookup"><span data-stu-id="46e01-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e01-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46e01-110">See Also</span></span>  
 [<span data-ttu-id="46e01-111">Znaki specjalne w kodzie</span><span class="sxs-lookup"><span data-stu-id="46e01-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [<span data-ttu-id="46e01-112">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="46e01-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
