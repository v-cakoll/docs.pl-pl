---
title: Pierwsze osiem znaków nazwa dziennika niestandardowego są znaczące
ms.date: 07/20/2015
ms.assetid: db2a0252-9ddd-4e93-a239-6a690cc09557
ms.openlocfilehash: a5b87dcb345a65d75469e61a6da2ba10172d8109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503195"
---
# <a name="only-the-first-eight-characters-of-a-custom-log-name-are-significant"></a><span data-ttu-id="12287-102">Pierwsze osiem znaków nazwa dziennika niestandardowego są znaczące</span><span class="sxs-lookup"><span data-stu-id="12287-102">Only the first eight characters of a custom log name are significant</span></span>
<span data-ttu-id="12287-103">Podczas sprawdzania dostępności nazwy dzienników zdarzeń, aby zapewnić unikatowość, są traktowane jako pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="12287-103">When checking event log names for uniqueness, only the first eight characters are considered.</span></span> <span data-ttu-id="12287-104">Konflikt mogą wynikać z dzienników zdarzeń, które udostępniać swoje pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="12287-104">A conflict may result from event logs that share their first eight characters.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12287-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="12287-105">To correct this error</span></span>  
  
-   <span data-ttu-id="12287-106">Nazwij w dzienniku zdarzeń w którym są unikatowe pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="12287-106">Give the event log a name in which the first eight characters are unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12287-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12287-107">See also</span></span>
- [<span data-ttu-id="12287-108">Instrukcje: Tworzenie i usuwanie niestandardowych dzienników zdarzeń</span><span class="sxs-lookup"><span data-stu-id="12287-108">How to: Create and Remove Custom Event Logs</span></span>](https://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
- [<span data-ttu-id="12287-109">Administrowanie usługą dzienników zdarzeń</span><span class="sxs-lookup"><span data-stu-id="12287-109">Administering Event Logs</span></span>](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)
