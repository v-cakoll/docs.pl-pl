---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b433e5e3c0a961098f82ad601d127290b1d6bd73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="047be-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="047be-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="047be-103">Usługa MSMQ odrzucone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="047be-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="047be-104">Opis</span><span class="sxs-lookup"><span data-stu-id="047be-104">Description</span></span>  
 <span data-ttu-id="047be-105">Ślad wskazuje, że wiadomości MSMQ został odrzucony.</span><span class="sxs-lookup"><span data-stu-id="047be-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="047be-106">Wiadomości usługi MSMQ może być odrzucone po [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (używany z NetMsmqBinding lub MsmqIntegrationBinding) nie może ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="047be-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="047be-107">Takie komunikaty są określane jako skażone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="047be-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="047be-108">Trująca wiadomość zostało odrzucone po `ReceiveErrorHandling` ma ustawioną właściwość NetMsmqBinding lub MsmqIntegrationBinding `Reject`.</span><span class="sxs-lookup"><span data-stu-id="047be-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="047be-109">Odrzucone wiadomości jest dostarczany do nadawcy [kolejki utraconych wiadomości](http://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="047be-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="047be-110">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="047be-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="047be-111">Zobacz [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) uzyskać więcej informacji dotyczących komunikatów odrzuconych oznacza w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="047be-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047be-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="047be-112">See Also</span></span>  
 [<span data-ttu-id="047be-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="047be-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="047be-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="047be-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="047be-115">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="047be-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="047be-116">Poison komunikat — Obsługa</span><span class="sxs-lookup"><span data-stu-id="047be-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="047be-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="047be-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
