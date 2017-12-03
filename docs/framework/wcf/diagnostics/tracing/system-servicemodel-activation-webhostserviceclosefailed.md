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
ms.openlocfilehash: 1761ef66bf2aedf2d4382558ba70bf1956af0f3e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="8ceb0-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="8ceb0-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="8ceb0-103">Występuje, gdy usługi nie można bezpiecznie zamknąć i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="8ceb0-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ceb0-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8ceb0-104">Description</span></span>  
 <span data-ttu-id="8ceb0-105">Ten błąd jest wyświetlany tylko w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="8ceb0-105">This error code only appears in the log file.</span></span> <span data-ttu-id="8ceb0-106">Zwykle oznacza to błąd programistyczny, na przykład podczas próby zamknięcia usługi po przerwaniu została już wywołana.</span><span class="sxs-lookup"><span data-stu-id="8ceb0-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8ceb0-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8ceb0-107">Troubleshooting</span></span>  
 <span data-ttu-id="8ceb0-108">Sprawdź kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ceb0-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ceb0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ceb0-109">See Also</span></span>  
 [<span data-ttu-id="8ceb0-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8ceb0-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8ceb0-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8ceb0-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8ceb0-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8ceb0-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
