---
title: Obsługa błędów działań w WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774026"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="27883-102">Obsługa błędów działań w WF</span><span class="sxs-lookup"><span data-stu-id="27883-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="27883-103">Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="27883-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="27883-104">Aby uzyskać więcej informacji, zobacz [wyjątki](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="27883-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="27883-105">Działania obsługi błędu</span><span class="sxs-lookup"><span data-stu-id="27883-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="27883-106">Ponownie zgłasza ostatni wyjątek zgłoszony z poziomu `TryCatch` działania.</span><span class="sxs-lookup"><span data-stu-id="27883-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="27883-107">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="27883-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="27883-108">Implementuje obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="27883-108">Implements exception handling.</span></span>|
