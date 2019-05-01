---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970121"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="bb8fc-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="bb8fc-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="bb8fc-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="bb8fc-103">A cyclic operation has failed.</span></span> <span data-ttu-id="bb8fc-104">Operacje cykliczne cyklu i dlatego nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="bb8fc-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="bb8fc-105">Na przykład obiekt A może próbować dziedziczyć obiekt B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="bb8fc-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb8fc-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bb8fc-106">To correct this error</span></span>  
  
- <span data-ttu-id="bb8fc-107">Gdy dziedziczy, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="bb8fc-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8fc-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb8fc-108">See also</span></span>

- [<span data-ttu-id="bb8fc-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="bb8fc-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="bb8fc-110">Używanie punktów przerwania w debugerze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb8fc-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
