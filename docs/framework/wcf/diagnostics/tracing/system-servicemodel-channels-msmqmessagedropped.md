---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2f905c345db89e909920334a7dbb524095bc46b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="8f5dc-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="8f5dc-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="8f5dc-103">Usługa MSMQ porzucony komunikat.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8f5dc-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8f5dc-104">Description</span></span>  
 <span data-ttu-id="8f5dc-105">Śledzenie wskazuje, że wiadomości MSMQ został porzucony.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="8f5dc-106">Wiadomości usługi MSMQ można porzucić kiedy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (używany z NetMsmqBinding lub MsmqIntegrationBinding) nie może ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="8f5dc-107">Takie komunikaty są określane jako skażone wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="8f5dc-108">Trująca wiadomość jest przerywane po `ReceiveErrorHandling` ma ustawioną właściwość NetMsmqBinding lub MsmqIntegrationBinding `Drop`.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="8f5dc-109">Porzucone wiadomości zostanie usunięta z kolejki i nie jest już możliwe do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="8f5dc-110">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="8f5dc-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5dc-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f5dc-111">See Also</span></span>  
 [<span data-ttu-id="8f5dc-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8f5dc-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8f5dc-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8f5dc-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8f5dc-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8f5dc-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="8f5dc-115">Poison komunikat — Obsługa</span><span class="sxs-lookup"><span data-stu-id="8f5dc-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
