---
title: "Nie można załadować informacji o klasie &#39; &lt;classname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords: BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6f8d53b802e70bbbe2d5a6c70d34884b49b4024
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unable-to-load-information-for-class-39ltclassnamegt39"></a><span data-ttu-id="9281b-102">Nie można załadować informacji o klasie &#39; &lt;classname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="9281b-102">Unable to load information for class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="9281b-103">Odwołanie zostało przesłane do klasy, która nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="9281b-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="9281b-104">**Identyfikator błędu:** BC30712</span><span class="sxs-lookup"><span data-stu-id="9281b-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9281b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9281b-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9281b-106">Sprawdź, czy ta klasa jest zdefiniowana i prawidłowo wpisana nazwa.</span><span class="sxs-lookup"><span data-stu-id="9281b-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2.  <span data-ttu-id="9281b-107">Spróbuj, uzyskiwanie dostępu do jednego z elementów członkowskich zadeklarowany w module.</span><span class="sxs-lookup"><span data-stu-id="9281b-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="9281b-108">W niektórych przypadkach debugowania środowiska nie można zlokalizować elementów członkowskich, ponieważ moduły, w którym je zadeklarowano nie zostały jeszcze załadowane.</span><span class="sxs-lookup"><span data-stu-id="9281b-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9281b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9281b-109">See Also</span></span>  
 [<span data-ttu-id="9281b-110">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9281b-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
