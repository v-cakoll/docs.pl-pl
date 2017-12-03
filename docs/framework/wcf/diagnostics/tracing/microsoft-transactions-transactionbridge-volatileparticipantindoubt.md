---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98ce61e4a46f8853e61e0ef44fdc78cf3e94431a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="8552c-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="8552c-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="8552c-103">Usługa protokołu WS-AT odebrała komunikat Prepared lub Replay od nierozpoznanego uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="8552c-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="8552c-104">Zwrócono błąd do uczestnika, deklaruje, że dane wyjściowe transakcji są wątpliwe.</span><span class="sxs-lookup"><span data-stu-id="8552c-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8552c-105">Opis</span><span class="sxs-lookup"><span data-stu-id="8552c-105">Description</span></span>  
 <span data-ttu-id="8552c-106">Śledzone podczas lokalnego Menedżera transakcji odbiera komunikat Prepared lub Replay od Volatile rejestracji, który ma już przypominania.</span><span class="sxs-lookup"><span data-stu-id="8552c-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8552c-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8552c-107">Troubleshooting</span></span>  
 <span data-ttu-id="8552c-108">Zbadaj możliwych przyczyn opóźnień komunikaty pochodzące z uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="8552c-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8552c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8552c-109">See Also</span></span>  
 [<span data-ttu-id="8552c-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8552c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8552c-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8552c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8552c-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8552c-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
