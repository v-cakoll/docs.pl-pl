---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0af06181ce888fe00203cf1e780257cd142be7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="6321a-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="6321a-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="6321a-103">Do koordynatora, który nie odpowiada, wysłano ponowną próbę komunikatu powtarzania.</span><span class="sxs-lookup"><span data-stu-id="6321a-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6321a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6321a-104">Description</span></span>  
 <span data-ttu-id="6321a-105">Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości powtarzania koordynatorem wyższego poziomu, ponieważ nie otrzymano odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="6321a-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6321a-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="6321a-106">Troubleshooting</span></span>  
 <span data-ttu-id="6321a-107">Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6321a-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="6321a-108">Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6321a-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="6321a-109">Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.</span><span class="sxs-lookup"><span data-stu-id="6321a-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6321a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6321a-110">See Also</span></span>  
 [<span data-ttu-id="6321a-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="6321a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6321a-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="6321a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6321a-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="6321a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
