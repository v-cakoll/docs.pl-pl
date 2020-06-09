---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578054"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="e406a-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="e406a-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="e406a-103">Wiadomość została odrzucona przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e406a-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e406a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e406a-104">Description</span></span>  
 <span data-ttu-id="e406a-105">Ten ślad wskazuje, że wiadomość usługi MSMQ została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="e406a-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="e406a-106">Komunikaty usługi MSMQ można odrzucić, gdy Windows Communication Foundation (WCF) (używane z usługą Msmqbinding lub MsmqIntegrationBinding) nie może ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="e406a-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="e406a-107">Takie komunikaty nazywa się skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="e406a-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="e406a-108">Trująca wiadomość jest odrzucana, gdy `ReceiveErrorHandling` Właściwość w sieci msmqbinding lub MsmqIntegrationBinding jest ustawiona na `Reject` .</span><span class="sxs-lookup"><span data-stu-id="e406a-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="e406a-109">Odrzucony komunikat jest dostarczany z powrotem do [kolejki utraconych wiadomości](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)nadawcy.</span><span class="sxs-lookup"><span data-stu-id="e406a-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="e406a-110">Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="e406a-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="e406a-111">Aby uzyskać więcej informacji na temat tego, co oznacza komunikat odrzucony w usłudze MSMQ, zobacz [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="e406a-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e406a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e406a-112">See also</span></span>

- [<span data-ttu-id="e406a-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="e406a-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="e406a-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="e406a-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e406a-115">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="e406a-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="e406a-116">Obsługa komunikatów trujących</span><span class="sxs-lookup"><span data-stu-id="e406a-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="e406a-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="e406a-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
