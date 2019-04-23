---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: afe84db3d4df8914ff1ed001b064439d581ead89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085398"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="19499-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="19499-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="19499-103">Występuje, gdy usługa nie można bezpiecznie zamknąć i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="19499-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="19499-104">Opis</span><span class="sxs-lookup"><span data-stu-id="19499-104">Description</span></span>  
 <span data-ttu-id="19499-105">Ten błąd pojawia się tylko w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="19499-105">This error code only appears in the log file.</span></span> <span data-ttu-id="19499-106">Zazwyczaj wskazuje to błąd programistyczny, na przykład podczas próby zamknięcia usługi po przerwaniu została już wywołana.</span><span class="sxs-lookup"><span data-stu-id="19499-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="19499-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="19499-107">Troubleshooting</span></span>  
 <span data-ttu-id="19499-108">Sprawdź kod źródłowy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19499-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19499-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19499-109">See also</span></span>

- [<span data-ttu-id="19499-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="19499-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="19499-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="19499-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="19499-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="19499-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
