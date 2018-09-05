---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: b821034731514362a3725c390e02542b536f0a59
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542222"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="cf278-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="cf278-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="cf278-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="cf278-103">A cyclic operation has failed.</span></span> <span data-ttu-id="cf278-104">Operacje cykliczne cyklu i dlatego nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="cf278-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="cf278-105">Na przykład obiekt A może próbować dziedziczyć obiekt B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="cf278-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf278-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cf278-106">To correct this error</span></span>  
  
-   <span data-ttu-id="cf278-107">Gdy dziedziczy, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="cf278-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf278-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf278-108">See Also</span></span>  
 [<span data-ttu-id="cf278-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="cf278-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="cf278-110">Podstawy debugowania: punkty przerwania</span><span class="sxs-lookup"><span data-stu-id="cf278-110">Debugging Basics: Breakpoints</span></span>](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
