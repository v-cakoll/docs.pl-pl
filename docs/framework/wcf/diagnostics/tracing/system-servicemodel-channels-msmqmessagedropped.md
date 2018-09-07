---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 07bef8b391a03f2c011e1d1a7c7fb4fad908e022
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067808"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="af1da-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="af1da-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="af1da-103">Usługa MSMQ porzucić komunikatu.</span><span class="sxs-lookup"><span data-stu-id="af1da-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="af1da-104">Opis</span><span class="sxs-lookup"><span data-stu-id="af1da-104">Description</span></span>  
 <span data-ttu-id="af1da-105">Śledzenia wskazuje, że wiadomości usługi MSMQ został porzucony.</span><span class="sxs-lookup"><span data-stu-id="af1da-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="af1da-106">Gdy (używany z NetMsmqBinding lub MsmqIntegrationBinding) Windows Communication Foundation (WCF) nie będzie mógł je przetworzyć można porzucić wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="af1da-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="af1da-107">Takie wiadomości są określane jako skażone komunikaty.</span><span class="sxs-lookup"><span data-stu-id="af1da-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="af1da-108">Zarządzanie skażonymi komunikatami zostało porzucone, kiedy `ReceiveErrorHandling` NetMsmqBinding lub MsmqIntegrationBinding zostaje ustalona `Drop`.</span><span class="sxs-lookup"><span data-stu-id="af1da-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="af1da-109">Porzucone komunikat zostanie usunięty z kolejki i nie jest już możliwe do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="af1da-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="af1da-110">Zobacz [obsługi komunikatów Poison](https://go.microsoft.com/fwlink/?LinkID=99546) więcej informacji na temat po wiadomości stają się zanieczyszczone oraz sposób konfigurowania usługi odpowiednio je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="af1da-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1da-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af1da-111">See Also</span></span>  
 [<span data-ttu-id="af1da-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="af1da-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="af1da-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="af1da-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="af1da-114">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="af1da-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="af1da-115">Obsługa komunikatów poison</span><span class="sxs-lookup"><span data-stu-id="af1da-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
