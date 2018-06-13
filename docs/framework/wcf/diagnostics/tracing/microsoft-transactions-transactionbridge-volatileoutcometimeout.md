---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475634"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="78076-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="78076-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="78076-103">Usługa protokołu WS-AT upłynął limit czasu oczekiwania na odpowiedź na komunikat wynikowy od nietrwałego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="78076-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="78076-104">Jeśli uczestnik powróci, wynik transakcji może być wątpliwe.</span><span class="sxs-lookup"><span data-stu-id="78076-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="78076-105">Opis</span><span class="sxs-lookup"><span data-stu-id="78076-105">Description</span></span>  
 <span data-ttu-id="78076-106">Śledzone uczestnika nietrwałego postanowiła Zatwierdź lub Przerwij, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="78076-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="78076-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="78076-107">Troubleshooting</span></span>  
 <span data-ttu-id="78076-108">Upewnij się, że wszystkie osoby uczestniczące w niej Volatile są w stanie odpowiedzieć w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="78076-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="78076-109">Domyślny okres czasu wynosi 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="78076-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="78076-110">Jeśli jest to za mało, zwiększyć `VolatileOutcomeDelay` czasomierza zasady dla usługi WS-AT.</span><span class="sxs-lookup"><span data-stu-id="78076-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78076-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78076-111">See Also</span></span>  
 [<span data-ttu-id="78076-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="78076-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="78076-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="78076-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="78076-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="78076-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
