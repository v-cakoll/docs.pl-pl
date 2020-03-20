---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674776"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="dea9a-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="dea9a-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="dea9a-103">Usługa MSMQ odrzuciła tę wiadomość.</span><span class="sxs-lookup"><span data-stu-id="dea9a-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dea9a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="dea9a-104">Description</span></span>  
 <span data-ttu-id="dea9a-105">Ten ślad wskazuje, że komunikat usługi MSMQ został odrzucony.</span><span class="sxs-lookup"><span data-stu-id="dea9a-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="dea9a-106">Komunikaty usługi MSMQ można odrzucić, gdy program Windows Communication Foundation (WCF) (używany z programem NetMsmqBinding lub MsmqIntegrationBinding) nie jest w stanie ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="dea9a-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="dea9a-107">Takie wiadomości są określane jako wiadomości trucizny.</span><span class="sxs-lookup"><span data-stu-id="dea9a-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="dea9a-108">Komunikat poison zostanie odrzucony, `ReceiveErrorHandling` gdy właściwość na NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="dea9a-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="dea9a-109">Odrzucona wiadomość zostanie dostarczona z powrotem do [kolejki utraconych wiadomości nadawcy](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span><span class="sxs-lookup"><span data-stu-id="dea9a-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="dea9a-110">Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="dea9a-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="dea9a-111">Aby uzyskać więcej informacji na temat tego, co oznacza odrzucona wiadomość w programie MSMQ, zobacz [MQMarkMessageRejed .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="dea9a-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea9a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dea9a-112">See also</span></span>

- [<span data-ttu-id="dea9a-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="dea9a-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="dea9a-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="dea9a-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dea9a-115">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="dea9a-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="dea9a-116">Obsługa zatruć-message</span><span class="sxs-lookup"><span data-stu-id="dea9a-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="dea9a-117">[MQMarkMessageZasunięty](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="dea9a-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
