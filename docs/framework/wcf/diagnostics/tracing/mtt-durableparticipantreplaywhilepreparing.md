---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="96c0d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="96c0d-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="96c0d-103">Usługa protokołu WS-AT odebrał komunikat powtarzania od trwałego uczestnika, który nie odpowiada na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="96c0d-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="96c0d-104">W rezultacie transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="96c0d-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="96c0d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="96c0d-105">Description</span></span>  
 <span data-ttu-id="96c0d-106">Śledzone, gdy zostaje otrzymany komunikat powtarzania, gdy nadal przygotowuje trwałego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="96c0d-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="96c0d-107">Jest to niedozwolone komunikatu dla tego stanu i transakcja ma być przerwane.</span><span class="sxs-lookup"><span data-stu-id="96c0d-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="96c0d-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="96c0d-108">Troubleshooting</span></span>  
 <span data-ttu-id="96c0d-109">Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) odzyskał sprawność po awarii, jednak jest nieznany wynik transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="96c0d-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c0d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96c0d-110">See Also</span></span>  
 [<span data-ttu-id="96c0d-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="96c0d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="96c0d-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="96c0d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="96c0d-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="96c0d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
