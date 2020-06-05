---
title: Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400321"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="850ce-102">Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza</span><span class="sxs-lookup"><span data-stu-id="850ce-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="850ce-103">Jednowierszowa `If` instrukcja zawiera kilka instrukcji rozdzielonych średnikami (:), z których jedna jest `End` instrukcją dla bloku sterowania poza linią jednowierszową `If` .</span><span class="sxs-lookup"><span data-stu-id="850ce-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="850ce-104">Instrukcje jednowierszowe `If` nie używają `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="850ce-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="850ce-105">**Identyfikator błędu:** BC32005</span><span class="sxs-lookup"><span data-stu-id="850ce-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="850ce-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="850ce-106">To correct this error</span></span>  
  
- <span data-ttu-id="850ce-107">Przenieś instrukcję jednowierszową `If` poza blok sterowania, który zawiera `End If` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="850ce-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850ce-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="850ce-108">See also</span></span>

- [<span data-ttu-id="850ce-109">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="850ce-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
