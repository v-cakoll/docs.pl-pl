---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 68217023a980891200c18b5536ef902574d36257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="5f8fe-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="5f8fe-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="5f8fe-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-103">A cyclic operation has failed.</span></span> <span data-ttu-id="5f8fe-104">Operacje cykliczne cyklu i z tego powodu nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="5f8fe-105">Na przykład obiekt A może próbować dziedziczyć B obiektu, który z kolei dziedziczy obiektu A.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f8fe-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5f8fe-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5f8fe-107">Podczas dziedziczenia, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8fe-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f8fe-108">See Also</span></span>  
 [<span data-ttu-id="5f8fe-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="5f8fe-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="5f8fe-110">Podstawy debugowania: punkty przerwania</span><span class="sxs-lookup"><span data-stu-id="5f8fe-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
