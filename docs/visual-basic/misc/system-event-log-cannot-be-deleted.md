---
title: Nie można usunąć w dzienniku zdarzeń systemowych
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 3dc4d624bcc0b559e9f61f51c58926588f24ee45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639301"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="65413-102">Nie można usunąć w dzienniku zdarzeń systemowych</span><span class="sxs-lookup"><span data-stu-id="65413-102">System event log cannot be deleted</span></span>
<span data-ttu-id="65413-103">Nastąpiła próba można usunąć dziennika zdarzeń systemu, której nie można usunąć.</span><span class="sxs-lookup"><span data-stu-id="65413-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="65413-104">Dziennik systemu śledzi zdarzenia systemowe, takie jak awarie sprzętu i uruchomienia systemu.</span><span class="sxs-lookup"><span data-stu-id="65413-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65413-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="65413-105">To correct this error</span></span>  
  
-   <span data-ttu-id="65413-106">Należy rozważyć utworzenie aplikacji zapisu do aplikacji lub dziennik niestandardowy, a nie w dzienniku zdarzeń systemowych.</span><span class="sxs-lookup"><span data-stu-id="65413-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="65413-107">Nie należy próbować usunąć w dzienniku zdarzeń systemowych.</span><span class="sxs-lookup"><span data-stu-id="65413-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65413-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65413-108">See Also</span></span>  
 [<span data-ttu-id="65413-109">Administrowanie dzienniki zdarzeń</span><span class="sxs-lookup"><span data-stu-id="65413-109">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="65413-110">Porady: tworzenie i usuwanie dzienników zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="65413-110">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
