---
title: Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: fca42f91f803a6b12535badcb25cc05cc3d23f6b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598467"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="37c83-102">Nie można ukończyć operacji, ponieważ katalog docelowy znajduje się w katalogu źródłowym</span><span class="sxs-lookup"><span data-stu-id="37c83-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="37c83-103">Cykliczne operacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="37c83-103">A cyclic operation has failed.</span></span> <span data-ttu-id="37c83-104">Operacje cykliczne cyklu i dlatego nie można ukończyć.</span><span class="sxs-lookup"><span data-stu-id="37c83-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="37c83-105">Na przykład obiekt A może próbować dziedziczyć obiekt B, który z kolei dziedziczy z obiektu A.</span><span class="sxs-lookup"><span data-stu-id="37c83-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37c83-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="37c83-106">To correct this error</span></span>  
  
- <span data-ttu-id="37c83-107">Gdy dziedziczy, upewnij się, że nie istnieją żadne odwołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="37c83-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c83-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37c83-108">See also</span></span>

- [<span data-ttu-id="37c83-109">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="37c83-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="37c83-110">Używanie punktów przerwania w debugerze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="37c83-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
