---
title: Pierwsze osiem znaków nazwa dziennika niestandardowego są znaczące
ms.date: 07/20/2015
ms.assetid: db2a0252-9ddd-4e93-a239-6a690cc09557
ms.openlocfilehash: 26ba0c0813fa4e1c1c371114dfbac073da888ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62023237"
---
# <a name="only-the-first-eight-characters-of-a-custom-log-name-are-significant"></a><span data-ttu-id="9a145-102">Pierwsze osiem znaków nazwa dziennika niestandardowego są znaczące</span><span class="sxs-lookup"><span data-stu-id="9a145-102">Only the first eight characters of a custom log name are significant</span></span>
<span data-ttu-id="9a145-103">Podczas sprawdzania dostępności nazwy dzienników zdarzeń, aby zapewnić unikatowość, są traktowane jako pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="9a145-103">When checking event log names for uniqueness, only the first eight characters are considered.</span></span> <span data-ttu-id="9a145-104">Konflikt mogą wynikać z dzienników zdarzeń, które udostępniać swoje pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="9a145-104">A conflict may result from event logs that share their first eight characters.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a145-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9a145-105">To correct this error</span></span>  
  
- <span data-ttu-id="9a145-106">Nazwij w dzienniku zdarzeń w którym są unikatowe pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="9a145-106">Give the event log a name in which the first eight characters are unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a145-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a145-107">See also</span></span>

- <span data-ttu-id="9a145-108">[Instrukcje: Tworzenie i usuwanie niestandardowych dzienników zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9a145-108">[How to: Create and Remove Custom Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>
- <span data-ttu-id="9a145-109">[Administrowanie usługą dzienników zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9a145-109">[Administering Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
