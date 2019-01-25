---
title: '&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bdbf8df5942e9df4b9696aeea4e3492121efe21a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746315"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="d07b5-102">&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="d07b5-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="d07b5-103">`Module` instrukcje musi znajdować się w górnej części pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed innych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="d07b5-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="d07b5-104">**Identyfikator błędu:** BC30617</span><span class="sxs-lookup"><span data-stu-id="d07b5-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d07b5-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d07b5-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d07b5-106">Przenieś `Module` instrukcji na górze pliku deklaracji ani źródła przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d07b5-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07b5-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d07b5-107">See also</span></span>
- [<span data-ttu-id="d07b5-108">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="d07b5-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
