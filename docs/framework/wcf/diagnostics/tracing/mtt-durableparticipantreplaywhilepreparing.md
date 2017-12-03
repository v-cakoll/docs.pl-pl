---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830a55a9f82c38b0a58783c49d3f58f64d5afdb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="66857-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="66857-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="66857-103">Usługa protokołu WS-AT odebrał komunikat powtarzania od trwałego uczestnika, który nie odpowiada na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="66857-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="66857-104">W rezultacie transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="66857-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="66857-105">Opis</span><span class="sxs-lookup"><span data-stu-id="66857-105">Description</span></span>  
 <span data-ttu-id="66857-106">Śledzone, gdy zostaje otrzymany komunikat powtarzania, gdy nadal przygotowuje trwałego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="66857-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="66857-107">Jest to niedozwolone komunikatu dla tego stanu i transakcja ma być przerwane.</span><span class="sxs-lookup"><span data-stu-id="66857-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="66857-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="66857-108">Troubleshooting</span></span>  
 <span data-ttu-id="66857-109">Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) odzyskał sprawność po awarii, jednak jest nieznany wynik transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="66857-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66857-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66857-110">See Also</span></span>  
 [<span data-ttu-id="66857-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="66857-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="66857-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="66857-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="66857-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="66857-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
