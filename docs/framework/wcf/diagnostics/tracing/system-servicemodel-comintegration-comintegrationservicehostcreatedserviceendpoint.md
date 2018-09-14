---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7e7bd48d206456af6a5a8662516c4d9c82b3ed2f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615946"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="6baa8-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="6baa8-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="6baa8-103">Nie można przenieść lub usunąć komunikat.</span><span class="sxs-lookup"><span data-stu-id="6baa8-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6baa8-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6baa8-104">Description</span></span>  
 <span data-ttu-id="6baa8-105">Śledzenie wskazuje, czy wystąpił błąd podczas próby przenoszenie, usuwanie lub odrzucić wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6baa8-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="6baa8-106">Wiadomości usługi MSMQ są wykorzystywane przez Windows Communication Foundation (WCF) (jeśli jest używana w NetMsmqBinding lub MsmqIntegrationBinding). Ślad jest powiązany z wybranym wartość `ReceiveErrorHandling` właściwość NetMsmqBinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="6baa8-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="6baa8-107">Ślad nie jest wskaźnikiem wystąpił ogólny błąd systemu.</span><span class="sxs-lookup"><span data-stu-id="6baa8-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="6baa8-108">Jednak oznacza to, że wybrana zanieczyszczonych dyspozycji wiadomości nie powiodło się dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6baa8-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="6baa8-109">Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="6baa8-109">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6baa8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6baa8-110">See Also</span></span>  
 [<span data-ttu-id="6baa8-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="6baa8-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6baa8-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="6baa8-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6baa8-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="6baa8-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
