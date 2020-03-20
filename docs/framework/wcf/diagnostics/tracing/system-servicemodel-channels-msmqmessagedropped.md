---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674799"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="65481-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="65481-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="65481-103">Usługa MSMQ upuściła wiadomość.</span><span class="sxs-lookup"><span data-stu-id="65481-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="65481-104">Opis</span><span class="sxs-lookup"><span data-stu-id="65481-104">Description</span></span>  
 <span data-ttu-id="65481-105">Śledzenie wskazuje, że komunikat usługi MSMQ został porzucony.</span><span class="sxs-lookup"><span data-stu-id="65481-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="65481-106">Komunikaty usługi MSMQ mogą zostać usunięte, gdy program Windows Communication Foundation (WCF) (używany z programem NetMsmqBinding lub MsmqIntegrationBinding) nie jest w stanie ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="65481-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="65481-107">Takie wiadomości są określane jako wiadomości trucizny.</span><span class="sxs-lookup"><span data-stu-id="65481-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="65481-108">Komunikat o trucinie `ReceiveErrorHandling` jest odrzucany, gdy właściwość na NetMsmqBinding `Drop`lub MsmqIntegrationBinding jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="65481-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="65481-109">Porzucona wiadomość jest usuwana z kolejki i nie można jej już odzyskać.</span><span class="sxs-lookup"><span data-stu-id="65481-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="65481-110">Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="65481-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65481-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65481-111">See also</span></span>

- [<span data-ttu-id="65481-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="65481-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="65481-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="65481-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="65481-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="65481-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="65481-115">Obsługa zatruć-message</span><span class="sxs-lookup"><span data-stu-id="65481-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
