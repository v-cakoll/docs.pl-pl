---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486772"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="25a4d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="25a4d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="25a4d-103">Usługa protokołu WS-AT odebrała komunikat powtarzania z trwałego uczestnika nie odpowiedział na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="25a4d-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="25a4d-104">W związku z tym transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="25a4d-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="25a4d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="25a4d-105">Description</span></span>  
 <span data-ttu-id="25a4d-106">Śledzone, jeśli powtarzania wiadomość zostaje odebrana, gdy uczestnik trwałe nadal trwa przygotowywanie.</span><span class="sxs-lookup"><span data-stu-id="25a4d-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="25a4d-107">Ten komunikat ma charakter niedozwolony dla tego stanu i transakcja zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="25a4d-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="25a4d-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="25a4d-108">Troubleshooting</span></span>

<span data-ttu-id="25a4d-109">Ten komunikat o błędzie może wskazywać, że trwałego uczestnika (w tym TransactionManagers podrzędnego) została odzyskana po awarii; jednak nie ma pewności o wyniku transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="25a4d-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a4d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25a4d-110">See also</span></span>

- [<span data-ttu-id="25a4d-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="25a4d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="25a4d-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="25a4d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="25a4d-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="25a4d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
