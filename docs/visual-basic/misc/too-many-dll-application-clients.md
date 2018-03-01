---
title: "Zbyt wielu klientów aplikacji DLL"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="792f1-102">Zbyt wielu klientów aplikacji DLL</span><span class="sxs-lookup"><span data-stu-id="792f1-102">Too many DLL application clients</span></span>
<span data-ttu-id="792f1-103">Biblioteki dołączanej (dynamicznie DLL) dla [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] może obsłużyć tylko dostępu przy ograniczonej liczby aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="792f1-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="792f1-104">Aplikacja i inne aplikacje, które są [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hostów (niektóre z nich mogą być używane przez aplikację) są próby uzyskania dostępu do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteki DLL w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="792f1-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="792f1-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="792f1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="792f1-106">Zmniejsz liczbę otwartych aplikacji dostęp do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="792f1-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792f1-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="792f1-107">See Also</span></span>  
 [<span data-ttu-id="792f1-108">Error — typy</span><span class="sxs-lookup"><span data-stu-id="792f1-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
