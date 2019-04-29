---
title: Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 0619db618abd562bda86836bdd41bbcd6caee0f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649897"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="67c64-102">Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”</span><span class="sxs-lookup"><span data-stu-id="67c64-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="67c64-103">`Class` Służy do inicjowania `Class` Blokuj; dlatego tylko może występować na początku bloku, odpowiadającą jej instrukcją `End Class` instrukcji blok końcowy.</span><span class="sxs-lookup"><span data-stu-id="67c64-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="67c64-104">Albo masz nadmiarowe `Class` instrukcji lub użytkownik nie zakończył swojej `Class` blokowania z `End Class`.</span><span class="sxs-lookup"><span data-stu-id="67c64-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="67c64-105">**Identyfikator błędu:** BC30481</span><span class="sxs-lookup"><span data-stu-id="67c64-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67c64-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="67c64-106">To correct this error</span></span>  
  
- <span data-ttu-id="67c64-107">Zlokalizuj i usuń niepotrzebne `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="67c64-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="67c64-108">Zawrzeć `Class` bloku odpowiadającą jej instrukcją `End Class`.</span><span class="sxs-lookup"><span data-stu-id="67c64-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c64-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67c64-109">See also</span></span>

- [<span data-ttu-id="67c64-110">Koniec \<— słowo kluczowe > — instrukcja</span><span class="sxs-lookup"><span data-stu-id="67c64-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="67c64-111">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="67c64-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
