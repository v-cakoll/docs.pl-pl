---
title: Nie można wykonać operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 46ec7ae452d4f8259d0f8ca3a896d1b29151ed61
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376745"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="2ec70-102">Nie można wykonać operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="2ec70-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="2ec70-103">Operacja cykliczna zakończyła się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2ec70-103">A cyclic operation has failed.</span></span> <span data-ttu-id="2ec70-104">Cykliczny cykl operacji i w związku z tym nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="2ec70-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="2ec70-105">Na przykład obiekt A może próbować dziedziczyć z obiektu B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="2ec70-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ec70-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2ec70-106">To correct this error</span></span>  
  
- <span data-ttu-id="2ec70-107">Podczas dziedziczenia upewnij się, że nie ma odwołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="2ec70-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec70-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ec70-108">See also</span></span>

- [<span data-ttu-id="2ec70-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="2ec70-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="2ec70-110">Używanie punktów przerwania w debugerze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ec70-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
