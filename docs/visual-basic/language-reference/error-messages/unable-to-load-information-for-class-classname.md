---
title: Nie można załadować informacji dla klasy „<classname>”
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 91f754366441cb984edf23f2c2dca4fa5c542a8e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279529"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="13700-102">Nie można załadować informacji dla klasy\<nazwa_klasy > "</span><span class="sxs-lookup"><span data-stu-id="13700-102">Unable to load information for class '\<classname>'</span></span>
<span data-ttu-id="13700-103">Odwołano się do klasy, która nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="13700-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="13700-104">**Identyfikator błędu:** BC30712</span><span class="sxs-lookup"><span data-stu-id="13700-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13700-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="13700-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="13700-106">Sprawdź, czy klasa jest zdefiniowana i że nazwa został poprawnie wpisany.</span><span class="sxs-lookup"><span data-stu-id="13700-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2.  <span data-ttu-id="13700-107">Wypróbuj, uzyskiwanie dostępu do jednego z elementów członkowskich zadeklarowanych w module.</span><span class="sxs-lookup"><span data-stu-id="13700-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="13700-108">W niektórych przypadkach środowisko debugowania nie można zlokalizować elementów członkowskich, ponieważ moduły, w której są deklarowane nie został jeszcze załadowany.</span><span class="sxs-lookup"><span data-stu-id="13700-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13700-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13700-109">See also</span></span>
- [<span data-ttu-id="13700-110">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13700-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
