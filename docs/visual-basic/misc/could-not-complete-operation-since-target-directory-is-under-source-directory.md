---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 253e7ff1d457827a2e1cb9f64eae4bfa971a3798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645876"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="411e2-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="411e2-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="411e2-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="411e2-103">A cyclic operation has failed.</span></span> <span data-ttu-id="411e2-104">Operacje cykliczne cyklu i dlatego nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="411e2-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="411e2-105">Na przykład obiekt A może próbować dziedziczyć obiekt B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="411e2-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="411e2-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="411e2-106">To correct this error</span></span>  
  
-   <span data-ttu-id="411e2-107">Gdy dziedziczy, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="411e2-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411e2-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="411e2-108">See also</span></span>
- [<span data-ttu-id="411e2-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="411e2-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="411e2-110">Podstawy debugowania: Punkty przerwania</span><span class="sxs-lookup"><span data-stu-id="411e2-110">Debugging Basics: Breakpoints</span></span>](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
