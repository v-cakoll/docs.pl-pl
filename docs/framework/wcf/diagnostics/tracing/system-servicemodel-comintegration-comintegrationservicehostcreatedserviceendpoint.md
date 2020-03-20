---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674789"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="50895-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="50895-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="50895-103">Nie można przenieść ani usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="50895-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="50895-104">Opis</span><span class="sxs-lookup"><span data-stu-id="50895-104">Description</span></span>  
 <span data-ttu-id="50895-105">Śledzenie wskazuje, że wystąpił błąd podczas próby przeniesienia, usunięcia lub odrzucenia wiadomości MSMQ.</span><span class="sxs-lookup"><span data-stu-id="50895-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="50895-106">Wiadomości MSMQ są używane przez Windows Communication Foundation (WCF) (gdy są używane z NetMsmqBinding lub MsmqIntegrationBinding). Ten ślad jest związany z wybraną wartością `ReceiveErrorHandling` właściwości w netmsmqBinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="50895-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="50895-107">Ten ślad nie wskazuje na ogólną awarię systemu.</span><span class="sxs-lookup"><span data-stu-id="50895-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="50895-108">Jednak wskazuje, że wybrana dyspozycja wiadomości trująca nie powiodła się dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="50895-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="50895-109">Aby uzyskać więcej informacji o tym, kiedy wiadomości stają się zatrute i jak skonfigurować usługę do ich właściwego obchodzenia się z nimi, zobacz [Obsługa trujących wiadomości](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="50895-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50895-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50895-110">See also</span></span>

- [<span data-ttu-id="50895-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="50895-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="50895-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="50895-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="50895-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="50895-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
