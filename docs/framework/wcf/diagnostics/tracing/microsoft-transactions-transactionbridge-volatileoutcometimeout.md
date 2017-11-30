---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1992a209bb58c0a0d6f181eb2f1ec546d50372ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="0d25f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="0d25f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="0d25f-103">Usługa protokołu WS-AT upłynął limit czasu oczekiwania na odpowiedź na komunikat wynikowy od nietrwałego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="0d25f-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="0d25f-104">Jeśli uczestnik powróci, wynik transakcji może być wątpliwe.</span><span class="sxs-lookup"><span data-stu-id="0d25f-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0d25f-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0d25f-105">Description</span></span>  
 <span data-ttu-id="0d25f-106">Śledzone uczestnika nietrwałego postanowiła Zatwierdź lub Przerwij, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="0d25f-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0d25f-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0d25f-107">Troubleshooting</span></span>  
 <span data-ttu-id="0d25f-108">Upewnij się, że wszystkie osoby uczestniczące w niej Volatile są w stanie odpowiedzieć w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="0d25f-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="0d25f-109">Domyślny okres czasu wynosi 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="0d25f-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="0d25f-110">Jeśli jest to za mało, zwiększyć `VolatileOutcomeDelay` czasomierza zasady dla usługi WS-AT.</span><span class="sxs-lookup"><span data-stu-id="0d25f-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d25f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d25f-111">See Also</span></span>  
 [<span data-ttu-id="0d25f-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0d25f-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0d25f-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0d25f-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0d25f-114">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0d25f-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
