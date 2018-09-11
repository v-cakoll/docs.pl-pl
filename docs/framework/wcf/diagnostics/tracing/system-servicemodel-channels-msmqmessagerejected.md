---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 0addf987eac62c750a3c418e1b1c431d3f9bc1b0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266618"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="fe1c0-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="fe1c0-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="fe1c0-103">Usługa MSMQ odrzucił komunikat.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fe1c0-104">Opis</span><span class="sxs-lookup"><span data-stu-id="fe1c0-104">Description</span></span>  
 <span data-ttu-id="fe1c0-105">Ślad wskazuje, że wiadomości usługi MSMQ została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="fe1c0-106">Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można odrzucić wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="fe1c0-107">Takie wiadomości są określane jako skażone komunikaty.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="fe1c0-108">Zarządzanie skażonymi komunikatami zostanie odrzucone po `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Reject`.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="fe1c0-109">Odrzucone komunikat jest dostarczany do nadawcy [kolejki utraconych wiadomości](https://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="fe1c0-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="fe1c0-110">Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="fe1c0-111">Zobacz [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) dodatkowe szczegóły dotyczące odrzuconych komunikatów oznacza w usłudze MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fe1c0-111">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1c0-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe1c0-112">See Also</span></span>  
 [<span data-ttu-id="fe1c0-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="fe1c0-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fe1c0-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe1c0-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fe1c0-115">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="fe1c0-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="fe1c0-116">Obsługa komunikatów poison</span><span class="sxs-lookup"><span data-stu-id="fe1c0-116">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="fe1c0-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="fe1c0-117">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkID=99548)
