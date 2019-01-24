---
title: Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574719"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="d10f2-102">Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja</span><span class="sxs-lookup"><span data-stu-id="d10f2-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="d10f2-103">Jeden wiersz `If` instrukcja zawiera kilka instrukcji oddzielone dwukropkiem (:), z których jedna jest `End` instrukcji w bloku kontroli, poza jednym wierszem `If`.</span><span class="sxs-lookup"><span data-stu-id="d10f2-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="d10f2-104">Jeden wiersz `If` nie należy używać instrukcji `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d10f2-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="d10f2-105">**Identyfikator błędu:** BC32005</span><span class="sxs-lookup"><span data-stu-id="d10f2-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d10f2-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d10f2-106">To correct this error</span></span>  
  
-   <span data-ttu-id="d10f2-107">Przenieś jeden wiersz `If` instrukcji poza blok sterowania, który zawiera `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d10f2-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10f2-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d10f2-108">See also</span></span>
- [<span data-ttu-id="d10f2-109">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="d10f2-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
