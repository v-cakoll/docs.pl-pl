---
title: Nie można załadować informacji dla klasy „<classname>”
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 42f31df7f4bc849374d8beb09e17394c3cdd5ec4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318204"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="c01a5-102">Nie można załadować informacji dla klasy\<nazwa_klasy > "</span><span class="sxs-lookup"><span data-stu-id="c01a5-102">Unable to load information for class '\<classname>'</span></span>
<span data-ttu-id="c01a5-103">Odwołano się do klasy, która nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c01a5-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="c01a5-104">**Identyfikator błędu:** BC30712</span><span class="sxs-lookup"><span data-stu-id="c01a5-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c01a5-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c01a5-105">To correct this error</span></span>  
  
1. <span data-ttu-id="c01a5-106">Sprawdź, czy klasa jest zdefiniowana i że nazwa został poprawnie wpisany.</span><span class="sxs-lookup"><span data-stu-id="c01a5-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2. <span data-ttu-id="c01a5-107">Wypróbuj, uzyskiwanie dostępu do jednego z elementów członkowskich zadeklarowanych w module.</span><span class="sxs-lookup"><span data-stu-id="c01a5-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="c01a5-108">W niektórych przypadkach środowisko debugowania nie można zlokalizować elementów członkowskich, ponieważ moduły, w której są deklarowane nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="c01a5-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01a5-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c01a5-109">See also</span></span>

- [<span data-ttu-id="c01a5-110">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c01a5-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
