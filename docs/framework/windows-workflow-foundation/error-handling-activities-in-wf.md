---
title: Obsługa błędów działań w WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 51431e367f0ec8874588a52cb4dbd76d714768fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="d1f63-102">Obsługa błędów działań w WF</span><span class="sxs-lookup"><span data-stu-id="d1f63-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="d1f63-103"> Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="d1f63-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="d1f63-104">Aby uzyskać więcej informacji, zobacz [wyjątki](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d1f63-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="d1f63-105">Błąd obsługi działań</span><span class="sxs-lookup"><span data-stu-id="d1f63-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="d1f63-106">Ponownie zgłasza wyjątek ostatniego z poziomu `TryCatch` działania.</span><span class="sxs-lookup"><span data-stu-id="d1f63-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="d1f63-107">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d1f63-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="d1f63-108">Implementuje obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d1f63-108">Implements exception handling.</span></span>|
