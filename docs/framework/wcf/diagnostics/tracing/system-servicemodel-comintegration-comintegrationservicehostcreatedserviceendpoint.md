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
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="10a03-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="10a03-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="10a03-103">Nie można przenieść ani usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="10a03-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="10a03-104">Opis</span><span class="sxs-lookup"><span data-stu-id="10a03-104">Description</span></span>  
 <span data-ttu-id="10a03-105">Śledzenie wskazuje wystąpił błąd podczas próby przenoszenia, usunąć lub odrzucić wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="10a03-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="10a03-106">Wiadomości usługi MSMQ są zatrudnieni przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (w przypadku użycia z NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="10a03-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="10a03-107">Ta śledzenia nie jest świadczy o ogólny błąd systemu.</span><span class="sxs-lookup"><span data-stu-id="10a03-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="10a03-108">Jednak wskazuje, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="10a03-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="10a03-109">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="10a03-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a03-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10a03-110">See Also</span></span>  
 [<span data-ttu-id="10a03-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="10a03-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="10a03-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="10a03-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="10a03-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="10a03-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
