---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589135"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="3928d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="3928d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="3928d-103">Usługa protokołu WS-AT otrzymała komunikat powtarzania od trwałego uczestnika, który nie odpowiedział na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="3928d-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="3928d-104">W związku z tym transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="3928d-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3928d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="3928d-105">Description</span></span>  
 <span data-ttu-id="3928d-106">Śledzone w przypadku odebrania komunikatu powtarzania, gdy trwały uczestnik nadal trwa przygotowywanie.</span><span class="sxs-lookup"><span data-stu-id="3928d-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="3928d-107">Jest to niedozwolony komunikat dla tego stanu i transakcja zostanie przerwana.</span><span class="sxs-lookup"><span data-stu-id="3928d-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3928d-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="3928d-108">Troubleshooting</span></span>

<span data-ttu-id="3928d-109">Otrzymanie tego błędu może wskazywać, że trwały uczestnik (w tym podrzędny TransactionManagers) odzyskał sprawność po awarii; nie należy jednak pamiętać o wyniku transakcji i żądania jego stanu.</span><span class="sxs-lookup"><span data-stu-id="3928d-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3928d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3928d-110">See also</span></span>

- [<span data-ttu-id="3928d-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="3928d-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="3928d-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="3928d-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3928d-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="3928d-113">Administration and Diagnostics</span></span>](../index.md)
