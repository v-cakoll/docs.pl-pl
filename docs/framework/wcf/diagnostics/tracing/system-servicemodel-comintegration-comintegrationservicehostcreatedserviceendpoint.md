---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 474895e7fbcf1b9ed7ad7da6d28313ae4894f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="882e6-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="882e6-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="882e6-103">Nie można przenieść ani usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="882e6-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="882e6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="882e6-104">Description</span></span>  
 <span data-ttu-id="882e6-105">Śledzenie wskazuje wystąpił błąd podczas próby przenoszenia, usunąć lub odrzucić wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="882e6-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="882e6-106">Wiadomości usługi MSMQ są zatrudnieni przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (w przypadku użycia z NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="882e6-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="882e6-107">Ta śledzenia nie jest świadczy o ogólny błąd systemu.</span><span class="sxs-lookup"><span data-stu-id="882e6-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="882e6-108">Jednak wskazuje, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="882e6-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="882e6-109">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="882e6-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882e6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="882e6-110">See Also</span></span>  
 [<span data-ttu-id="882e6-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="882e6-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="882e6-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="882e6-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="882e6-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="882e6-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
