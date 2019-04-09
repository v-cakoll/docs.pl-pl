---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075538"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="45c17-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="45c17-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="45c17-103">Usługa protokołu WS-AT odebrała komunikat powtarzania z trwałego uczestnika nie odpowiedział na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="45c17-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="45c17-104">W związku z tym transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="45c17-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="45c17-105">Opis</span><span class="sxs-lookup"><span data-stu-id="45c17-105">Description</span></span>  
 <span data-ttu-id="45c17-106">Śledzone, jeśli powtarzania wiadomość zostaje odebrana, gdy uczestnik trwałe nadal trwa przygotowywanie.</span><span class="sxs-lookup"><span data-stu-id="45c17-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="45c17-107">Ten komunikat ma charakter niedozwolony dla tego stanu i transakcja zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="45c17-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="45c17-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="45c17-108">Troubleshooting</span></span>  
 <span data-ttu-id="45c17-109">Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) została odzyskana po awarii, chociaż jest on ustalić wyniku transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="45c17-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c17-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45c17-110">See also</span></span>

- [<span data-ttu-id="45c17-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="45c17-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="45c17-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="45c17-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="45c17-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="45c17-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
