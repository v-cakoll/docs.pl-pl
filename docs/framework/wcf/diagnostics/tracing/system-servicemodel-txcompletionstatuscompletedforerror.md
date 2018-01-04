---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25106bffe6d541a89c786035db3d3266d861fd5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="a5ba9-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="a5ba9-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="a5ba9-103">Transakcja określona dla określonej operacji została wykonana wskutek wystąpienia nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a5ba9-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a5ba9-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a5ba9-104">Description</span></span>  
 <span data-ttu-id="a5ba9-105">Śledzone, gdy wystąpi błąd podczas próby wykonania bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5ba9-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="a5ba9-106">Dzieje się to przed odpowiedzi lub błędów są wysyłane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a5ba9-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a5ba9-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="a5ba9-107">Troubleshooting</span></span>  
 <span data-ttu-id="a5ba9-108">Sprawdź, czy w komunikacie śledzonych komunikat o wyjątku oraz dowolne elementy przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="a5ba9-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ba9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5ba9-109">See Also</span></span>  
 [<span data-ttu-id="a5ba9-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a5ba9-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a5ba9-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="a5ba9-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a5ba9-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a5ba9-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
