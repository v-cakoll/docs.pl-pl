---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 663c06251f7a52a60b32e2f5cc3c47663436c66b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="43348-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="43348-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="43348-103">Usługa protokołu WS-AT odebrała komunikat Prepared lub Replay od nierozpoznanego uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="43348-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="43348-104">Zwrócono błąd do uczestnika, deklaruje, że dane wyjściowe transakcji są wątpliwe.</span><span class="sxs-lookup"><span data-stu-id="43348-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="43348-105">Opis</span><span class="sxs-lookup"><span data-stu-id="43348-105">Description</span></span>  
 <span data-ttu-id="43348-106">Śledzone podczas lokalnego Menedżera transakcji odbiera komunikat Prepared lub Replay od Volatile rejestracji, który ma już przypominania.</span><span class="sxs-lookup"><span data-stu-id="43348-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="43348-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="43348-107">Troubleshooting</span></span>  
 <span data-ttu-id="43348-108">Zbadaj możliwych przyczyn opóźnień komunikaty pochodzące z uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="43348-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43348-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43348-109">See Also</span></span>  
 [<span data-ttu-id="43348-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="43348-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="43348-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="43348-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="43348-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="43348-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
