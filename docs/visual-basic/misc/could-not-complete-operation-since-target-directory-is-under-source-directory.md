---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 39373cd368282f3b109b450189561366b9e74484
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200575"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="36115-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="36115-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="36115-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="36115-103">A cyclic operation has failed.</span></span> <span data-ttu-id="36115-104">Operacje cykliczne cyklu i dlatego nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="36115-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="36115-105">Na przykład obiekt A może próbować dziedziczyć obiekt B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="36115-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36115-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="36115-106">To correct this error</span></span>  
  
-   <span data-ttu-id="36115-107">Gdy dziedziczy, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="36115-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36115-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36115-108">See also</span></span>
- [<span data-ttu-id="36115-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="36115-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="36115-110">Używanie punktów przerwania w debugerze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36115-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
