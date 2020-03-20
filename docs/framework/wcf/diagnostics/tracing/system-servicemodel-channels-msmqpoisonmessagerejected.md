---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674813"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="0f382-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="0f382-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="0f382-103">Zatruta wiadomość odrzucona.</span><span class="sxs-lookup"><span data-stu-id="0f382-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f382-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0f382-104">Description</span></span>  

 <span data-ttu-id="0f382-105">Ślad wskazuje, że wiadomość trucizny została napotkana, a następnie odrzucona.</span><span class="sxs-lookup"><span data-stu-id="0f382-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="0f382-106">Dzieje się `ReceiveErrorHandling` tak, gdy właściwość na NetMsmqBinding lub MsmqIntegrationBinding jest ustawiona na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="0f382-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="0f382-107">Odrzucona wiadomość zostanie dostarczona z powrotem do [kolejki utraconych wiadomości nadawcy](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span><span class="sxs-lookup"><span data-stu-id="0f382-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="0f382-108">Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="0f382-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="0f382-109">Aby uzyskać więcej informacji na temat tego, co oznacza odrzucona wiadomość w programie MSMQ, zobacz [MQMarkMessageRejed .](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="0f382-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f382-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f382-110">See also</span></span>

- [<span data-ttu-id="0f382-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0f382-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0f382-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0f382-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0f382-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0f382-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="0f382-114">Obsługa zatruć-message</span><span class="sxs-lookup"><span data-stu-id="0f382-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="0f382-115">[MQMarkMessageZasunięty](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="0f382-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
