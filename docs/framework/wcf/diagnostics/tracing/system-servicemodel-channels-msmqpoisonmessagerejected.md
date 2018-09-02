---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 27402017e5e79194578719fd0c921dfc1e047b80
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407920"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="f9bb3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f9bb3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="f9bb3-103">Zarządzanie skażonymi komunikatami odrzucone.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9bb3-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f9bb3-104">Description</span></span>  
 <span data-ttu-id="f9bb3-105">Śledzenie wskazuje, że zarządzanie skażonymi komunikatami został napotkany i następnie odrzucenia.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="f9bb3-106">W takim przypadku `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="f9bb3-107">Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="f9bb3-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="f9bb3-108">Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkId=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="f9bb3-109">Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bb3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9bb3-110">See Also</span></span>  
 [<span data-ttu-id="f9bb3-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f9bb3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f9bb3-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f9bb3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f9bb3-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f9bb3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="f9bb3-114">Obsługa komunikatów poison</span><span class="sxs-lookup"><span data-stu-id="f9bb3-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="f9bb3-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f9bb3-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
