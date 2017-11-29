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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a00a6a06fd5214f1f65bdb6369839d717078da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="0d19c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="0d19c-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="0d19c-103">Usługa protokołu WS-AT odebrał komunikat powtarzania od trwałego uczestnika, który nie odpowiada na przygotowanie.</span><span class="sxs-lookup"><span data-stu-id="0d19c-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="0d19c-104">W rezultacie transakcja została przerwana.</span><span class="sxs-lookup"><span data-stu-id="0d19c-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0d19c-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0d19c-105">Description</span></span>  
 <span data-ttu-id="0d19c-106">Śledzone, gdy zostaje otrzymany komunikat powtarzania, gdy nadal przygotowuje trwałego uczestnika.</span><span class="sxs-lookup"><span data-stu-id="0d19c-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="0d19c-107">Jest to niedozwolone komunikatu dla tego stanu i transakcja ma być przerwane.</span><span class="sxs-lookup"><span data-stu-id="0d19c-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0d19c-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0d19c-108">Troubleshooting</span></span>  
 <span data-ttu-id="0d19c-109">Ten komunikat o błędzie może indiate, że trwałego uczestnika (w tym TransactionManagers podrzędnego) odzyskał sprawność po awarii, jednak jest nieznany wynik transakcji i jego stan żądania.</span><span class="sxs-lookup"><span data-stu-id="0d19c-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d19c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d19c-110">See Also</span></span>  
 [<span data-ttu-id="0d19c-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0d19c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0d19c-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0d19c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0d19c-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0d19c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
