---
title: Zbyt wielu klientów aplikacji biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
ms.openlocfilehash: e20f780e2029b382fa90473e1b762fc76604df98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922242"
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="3cc71-102">Zbyt wielu klientów aplikacji biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="3cc71-102">Too many DLL application clients</span></span>
<span data-ttu-id="3cc71-103">Biblioteka dołączana dynamicznie (DLL) dla języka Visual Basic tylko może obsłużyć dostępu przez ograniczoną liczbę aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="3cc71-103">The dynamic-link library (DLL) for Visual Basic can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="3cc71-104">Aplikacja i inne aplikacje, które są hostami języka Visual Basic (niektóre z nich mogą być używane przez aplikację) są wszystkie próby uzyskania dostępu do biblioteki DLL Visual Basic w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3cc71-104">Your application and other applications that are Visual Basic hosts (some of which may be accessed by your application) are all attempting to access the Visual Basic DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3cc71-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3cc71-105">To correct this error</span></span>  
  
- <span data-ttu-id="3cc71-106">Zmniejsz liczbę otwartych aplikacji dostęp do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3cc71-106">Reduce the number of open applications accessing Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc71-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cc71-107">See also</span></span>

- [<span data-ttu-id="3cc71-108">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="3cc71-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
