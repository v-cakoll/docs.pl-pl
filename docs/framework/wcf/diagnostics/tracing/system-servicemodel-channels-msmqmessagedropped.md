---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6218948e89288e76034d7c3f032f3c585e286c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570541"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="b8d15-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="b8d15-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="b8d15-103">Usługa MSMQ porzucić komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b8d15-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b8d15-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b8d15-104">Description</span></span>  
 <span data-ttu-id="b8d15-105">Śledzenia wskazuje, że wiadomości usługi MSMQ został porzucony.</span><span class="sxs-lookup"><span data-stu-id="b8d15-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="b8d15-106">Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można porzucić wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b8d15-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="b8d15-107">Takie wiadomości są określane jako skażone komunikaty.</span><span class="sxs-lookup"><span data-stu-id="b8d15-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="b8d15-108">Zarządzanie skażonymi komunikatami zostało porzucone, kiedy `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Drop`.</span><span class="sxs-lookup"><span data-stu-id="b8d15-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="b8d15-109">Porzucone komunikat zostanie usunięty z kolejki i nie jest już możliwe do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="b8d15-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="b8d15-110">Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="b8d15-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d15-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8d15-111">See also</span></span>
- [<span data-ttu-id="b8d15-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="b8d15-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b8d15-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b8d15-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b8d15-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="b8d15-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="b8d15-115">Obsługa komunikatów poison</span><span class="sxs-lookup"><span data-stu-id="b8d15-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
