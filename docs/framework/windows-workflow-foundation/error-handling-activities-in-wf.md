---
title: Obsługa błędów działań w WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707680"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="7255c-102">Obsługa błędów działań w WF</span><span class="sxs-lookup"><span data-stu-id="7255c-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="7255c-103">Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="7255c-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="7255c-104">Aby uzyskać więcej informacji, zobacz [wyjątki](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="7255c-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="7255c-105">Działania obsługi błędu</span><span class="sxs-lookup"><span data-stu-id="7255c-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="7255c-106">Ponownie zgłasza ostatni wyjątek zgłoszony z poziomu `TryCatch` działania.</span><span class="sxs-lookup"><span data-stu-id="7255c-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="7255c-107">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7255c-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="7255c-108">Implementuje obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7255c-108">Implements exception handling.</span></span>|
