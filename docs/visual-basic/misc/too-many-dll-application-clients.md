---
title: Zbyt wielu klientów aplikacji biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
ms.openlocfilehash: 3a0fe2d84c2fe6d080e4b555501fdbe7d5ee57e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619995"
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="c5dcc-102">Zbyt wielu klientów aplikacji biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="c5dcc-102">Too many DLL application clients</span></span>
<span data-ttu-id="c5dcc-103">Biblioteka dołączana dynamicznie (DLL) dla języka Visual Basic tylko może obsłużyć dostępu przez ograniczoną liczbę aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="c5dcc-103">The dynamic-link library (DLL) for Visual Basic can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="c5dcc-104">Aplikacja i inne aplikacje, które są hostami języka Visual Basic (niektóre z nich mogą być używane przez aplikację) są wszystkie próby uzyskania dostępu do biblioteki DLL Visual Basic w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c5dcc-104">Your application and other applications that are Visual Basic hosts (some of which may be accessed by your application) are all attempting to access the Visual Basic DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5dcc-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c5dcc-105">To correct this error</span></span>  
  
- <span data-ttu-id="c5dcc-106">Zmniejsz liczbę otwartych aplikacji dostęp do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c5dcc-106">Reduce the number of open applications accessing Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dcc-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5dcc-107">See also</span></span>

- [<span data-ttu-id="c5dcc-108">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="c5dcc-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
