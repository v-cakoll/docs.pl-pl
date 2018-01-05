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
ms.workload: dotnet
ms.openlocfilehash: 0dbfd04ed20a92a2ecf827ef3d6aa4f378eb6a15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="5829e-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="5829e-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="5829e-103">Usługa protokołu WS-AT odebrała komunikat Prepared lub Replay od nierozpoznanego uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="5829e-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="5829e-104">Zwrócono błąd do uczestnika, deklaruje, że dane wyjściowe transakcji są wątpliwe.</span><span class="sxs-lookup"><span data-stu-id="5829e-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5829e-105">Opis</span><span class="sxs-lookup"><span data-stu-id="5829e-105">Description</span></span>  
 <span data-ttu-id="5829e-106">Śledzone podczas lokalnego Menedżera transakcji odbiera komunikat Prepared lub Replay od Volatile rejestracji, który ma już przypominania.</span><span class="sxs-lookup"><span data-stu-id="5829e-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5829e-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="5829e-107">Troubleshooting</span></span>  
 <span data-ttu-id="5829e-108">Zbadaj możliwych przyczyn opóźnień komunikaty pochodzące z uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="5829e-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5829e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5829e-109">See Also</span></span>  
 [<span data-ttu-id="5829e-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5829e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5829e-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5829e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5829e-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5829e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
