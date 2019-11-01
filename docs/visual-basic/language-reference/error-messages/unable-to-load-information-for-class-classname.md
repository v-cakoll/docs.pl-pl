---
title: Nie można załadować informacji dla klasy „<classname>”
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: b3ef2aa5e25d61f005159e06852e23c2c036fd54
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198183"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="58aef-102">Nie można załadować informacji dla klasy "\<ClassName >"</span><span class="sxs-lookup"><span data-stu-id="58aef-102">Unable to load information for class '\<classname>'</span></span>
<span data-ttu-id="58aef-103">Wykonano odwołanie do klasy, która jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="58aef-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="58aef-104">**Identyfikator błędu:** BC30712</span><span class="sxs-lookup"><span data-stu-id="58aef-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58aef-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="58aef-105">To correct this error</span></span>  
  
1. <span data-ttu-id="58aef-106">Sprawdź, czy Klasa jest zdefiniowana i czy nazwa została wpisana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="58aef-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2. <span data-ttu-id="58aef-107">Spróbuj uzyskać dostęp do jednego z elementów członkowskich zadeklarowanych w module.</span><span class="sxs-lookup"><span data-stu-id="58aef-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="58aef-108">W niektórych przypadkach środowisko debugowania nie może zlokalizować elementów członkowskich, ponieważ moduły, w których są zadeklarowane, nie zostały jeszcze załadowane.</span><span class="sxs-lookup"><span data-stu-id="58aef-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58aef-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58aef-109">See also</span></span>

- [<span data-ttu-id="58aef-110">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58aef-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
