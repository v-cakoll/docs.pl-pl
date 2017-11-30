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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8550c30f74968d4f58d9a2fd1deac69bf9d3abe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="a2e50-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="a2e50-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="a2e50-103">Występuje, gdy usługi nie można bezpiecznie zamknąć i zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="a2e50-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a2e50-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a2e50-104">Description</span></span>  
 <span data-ttu-id="a2e50-105">Ten błąd jest wyświetlany tylko w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="a2e50-105">This error code only appears in the log file.</span></span> <span data-ttu-id="a2e50-106">Zwykle oznacza to błąd programistyczny, na przykład podczas próby zamknięcia usługi po przerwaniu została już wywołana.</span><span class="sxs-lookup"><span data-stu-id="a2e50-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a2e50-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="a2e50-107">Troubleshooting</span></span>  
 <span data-ttu-id="a2e50-108">Sprawdź kodu źródłowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2e50-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e50-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2e50-109">See Also</span></span>  
 [<span data-ttu-id="a2e50-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a2e50-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a2e50-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="a2e50-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a2e50-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a2e50-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
