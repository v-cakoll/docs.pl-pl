---
title: '&#39;Klasa&#39; instrukcja musi być zakończona odpowiadającą jej instrukcją &#39;End Class&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 4e80ce58048bfa7f2fecc65e7167479df07bf57c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715091"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="193da-102">&#39;Klasa&#39; instrukcja musi być zakończona odpowiadającą jej instrukcją &#39;End Class&#39;</span><span class="sxs-lookup"><span data-stu-id="193da-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="193da-103">`Class` Służy do inicjowania `Class` Blokuj; dlatego tylko może występować na początku bloku, odpowiadającą jej instrukcją `End Class` instrukcji blok końcowy.</span><span class="sxs-lookup"><span data-stu-id="193da-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="193da-104">Albo masz nadmiarowe `Class` instrukcji lub użytkownik nie zakończył swojej `Class` blokowania z `End Class`.</span><span class="sxs-lookup"><span data-stu-id="193da-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="193da-105">**Identyfikator błędu:** BC30481</span><span class="sxs-lookup"><span data-stu-id="193da-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="193da-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="193da-106">To correct this error</span></span>  
  
-   <span data-ttu-id="193da-107">Zlokalizuj i usuń niepotrzebne `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="193da-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="193da-108">Zawrzeć `Class` bloku odpowiadającą jej instrukcją `End Class`.</span><span class="sxs-lookup"><span data-stu-id="193da-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193da-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="193da-109">See also</span></span>
- [<span data-ttu-id="193da-110">Koniec \<— słowo kluczowe > — instrukcja</span><span class="sxs-lookup"><span data-stu-id="193da-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="193da-111">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="193da-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
