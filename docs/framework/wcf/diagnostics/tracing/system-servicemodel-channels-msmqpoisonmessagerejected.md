---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="0c52c-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0c52c-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="0c52c-103">Trująca wiadomość została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="0c52c-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0c52c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0c52c-104">Description</span></span>  
 <span data-ttu-id="0c52c-105">Śledzenie wskazuje, że Trująca wiadomość została napotkano i następnie odrzucone.</span><span class="sxs-lookup"><span data-stu-id="0c52c-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="0c52c-106">W takim przypadku `ReceiveErrorHandling` ma ustawioną właściwość NetMsmqBinding lub MsmqIntegrationBinding `Reject`.</span><span class="sxs-lookup"><span data-stu-id="0c52c-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="0c52c-107">Odrzucone wiadomości jest dostarczany do nadawcy [kolejki utraconych wiadomości](http://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="0c52c-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="0c52c-108">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkId=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="0c52c-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="0c52c-109">Zobacz [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) uzyskać więcej informacji dotyczących komunikatów odrzuconych oznacza w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0c52c-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c52c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c52c-110">See Also</span></span>  
 [<span data-ttu-id="0c52c-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0c52c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0c52c-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0c52c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0c52c-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0c52c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="0c52c-114">Poison komunikat — Obsługa</span><span class="sxs-lookup"><span data-stu-id="0c52c-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="0c52c-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0c52c-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
