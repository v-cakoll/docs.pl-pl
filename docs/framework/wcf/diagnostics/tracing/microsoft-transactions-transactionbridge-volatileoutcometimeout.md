---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 22992b4dfad4b4867adda0fcbbd8ecc5eb67d87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997610"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="64794-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="64794-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="64794-103">Usługa protokołu WS-AT upłynął limit czasu oczekiwania na odpowiedź na komunikat o wyniku z uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="64794-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="64794-104">Wyniku transakcji może być w stanie wątpliwości, jeśli zwróci uczestnika.</span><span class="sxs-lookup"><span data-stu-id="64794-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="64794-105">Opis</span><span class="sxs-lookup"><span data-stu-id="64794-105">Description</span></span>  
 <span data-ttu-id="64794-106">Śledzone, gdy Volatile uczestnika, który zdecydował się na zatwierdzenia lub przerwania, ale nie odpowiedział na żądanie zatwierdzenia lub wycofania w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="64794-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="64794-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="64794-107">Troubleshooting</span></span>  
 <span data-ttu-id="64794-108">Upewnij się, że wszyscy uczestnicy Volatile mogą odpowiadać w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="64794-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="64794-109">Domyślny okres to 180 sekund.</span><span class="sxs-lookup"><span data-stu-id="64794-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="64794-110">Jeśli to za mało, zwiększyć `VolatileOutcomeDelay` zasady WS-AT czasomierza.</span><span class="sxs-lookup"><span data-stu-id="64794-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64794-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64794-111">See also</span></span>

- [<span data-ttu-id="64794-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="64794-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="64794-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="64794-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="64794-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="64794-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
