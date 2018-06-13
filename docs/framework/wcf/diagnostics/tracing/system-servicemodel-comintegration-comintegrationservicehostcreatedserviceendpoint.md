---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487909"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="5e200-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="5e200-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="5e200-103">Nie można przenieść ani usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5e200-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e200-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5e200-104">Description</span></span>  
 <span data-ttu-id="5e200-105">Śledzenie wskazuje wystąpił błąd podczas próby przenoszenia, usunąć lub odrzucić wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e200-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="5e200-106">Wiadomości usługi MSMQ są wykorzystywane przez Windows Communication Foundation (WCF) (w przypadku użycia z NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="5e200-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="5e200-107">Ta śledzenia nie jest świadczy o ogólny błąd systemu.</span><span class="sxs-lookup"><span data-stu-id="5e200-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="5e200-108">Jednak wskazuje, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5e200-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="5e200-109">Zobacz [obsługi wiadomości Poison](http://go.microsoft.com/fwlink/?LinkID=99546) więcej szczegółów na kiedy zaczynają skażone wiadomości i konfigurowania usługi do odpowiednią obsługę.</span><span class="sxs-lookup"><span data-stu-id="5e200-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e200-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e200-110">See Also</span></span>  
 [<span data-ttu-id="5e200-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5e200-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5e200-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5e200-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5e200-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5e200-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
