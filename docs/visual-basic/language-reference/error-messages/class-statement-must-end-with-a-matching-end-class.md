---
title: Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 559595e9902ec2f0a19fd6b13e2c89fa1c2b52d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602416"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="1f4ea-102">Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”</span><span class="sxs-lookup"><span data-stu-id="1f4ea-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="1f4ea-103">`Class` Służy do inicjowania `Class` Blokuj; dlatego tylko może występować na początku bloku, odpowiadającą jej instrukcją `End Class` instrukcji blok końcowy.</span><span class="sxs-lookup"><span data-stu-id="1f4ea-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="1f4ea-104">Albo masz nadmiarowe `Class` instrukcji lub użytkownik nie zakończył swojej `Class` blokowania z `End Class`.</span><span class="sxs-lookup"><span data-stu-id="1f4ea-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="1f4ea-105">**Identyfikator błędu:** BC30481</span><span class="sxs-lookup"><span data-stu-id="1f4ea-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f4ea-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1f4ea-106">To correct this error</span></span>  
  
- <span data-ttu-id="1f4ea-107">Zlokalizuj i usuń niepotrzebne `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1f4ea-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="1f4ea-108">Zawrzeć `Class` bloku odpowiadającą jej instrukcją `End Class`.</span><span class="sxs-lookup"><span data-stu-id="1f4ea-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4ea-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f4ea-109">See also</span></span>

- [<span data-ttu-id="1f4ea-110">Koniec \<— słowo kluczowe > — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f4ea-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="1f4ea-111">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f4ea-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
