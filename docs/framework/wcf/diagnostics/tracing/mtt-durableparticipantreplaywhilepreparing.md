---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 3b51a100677221866186b2e24f34396c012d11c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603134"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="32c66-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="32c66-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="32c66-103">Usługa protokołu WS-AT odebrała komunikat powtarzania z trwałego uczestnika nie odpowiedział na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="32c66-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="32c66-104">W związku z tym transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="32c66-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="32c66-105">Opis</span><span class="sxs-lookup"><span data-stu-id="32c66-105">Description</span></span>  
 <span data-ttu-id="32c66-106">Śledzone, jeśli powtarzania wiadomość zostaje odebrana, gdy uczestnik trwałe nadal trwa przygotowywanie.</span><span class="sxs-lookup"><span data-stu-id="32c66-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="32c66-107">Ten komunikat ma charakter niedozwolony dla tego stanu i transakcja zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="32c66-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="32c66-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="32c66-108">Troubleshooting</span></span>  
 <span data-ttu-id="32c66-109">Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) została odzyskana po awarii, chociaż jest on ustalić wyniku transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="32c66-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c66-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32c66-110">See also</span></span>
- [<span data-ttu-id="32c66-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="32c66-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="32c66-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="32c66-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="32c66-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="32c66-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
