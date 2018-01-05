---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2b0dc75e8e8748e25c1faf28150e0c156a20ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="f8ece-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="f8ece-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="f8ece-103">Występuje, gdy usługi nie można bezpiecznie zamknąć i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="f8ece-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8ece-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f8ece-104">Description</span></span>  
 <span data-ttu-id="f8ece-105">Ten błąd jest wyświetlany tylko w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="f8ece-105">This error code only appears in the log file.</span></span> <span data-ttu-id="f8ece-106">Zwykle oznacza to błąd programistyczny, na przykład podczas próby zamknięcia usługi po przerwaniu została już wywołana.</span><span class="sxs-lookup"><span data-stu-id="f8ece-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f8ece-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="f8ece-107">Troubleshooting</span></span>  
 <span data-ttu-id="f8ece-108">Sprawdź kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8ece-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ece-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8ece-109">See Also</span></span>  
 [<span data-ttu-id="f8ece-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f8ece-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f8ece-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f8ece-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f8ece-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f8ece-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
