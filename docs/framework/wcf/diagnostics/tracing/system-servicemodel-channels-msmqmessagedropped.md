---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601920"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="441e1-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="441e1-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="441e1-103">Wiadomość została porzucona przez usługę MSMQ.</span><span class="sxs-lookup"><span data-stu-id="441e1-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="441e1-104">Opis</span><span class="sxs-lookup"><span data-stu-id="441e1-104">Description</span></span>  
 <span data-ttu-id="441e1-105">Śledzenie wskazuje, że komunikat usługi MSMQ został porzucony.</span><span class="sxs-lookup"><span data-stu-id="441e1-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="441e1-106">Komunikaty usługi MSMQ można porzucić, gdy Windows Communication Foundation (WCF) (używane z usługą Msmqbinding lub MsmqIntegrationBinding) nie może ich przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="441e1-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="441e1-107">Takie komunikaty nazywa się skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="441e1-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="441e1-108">Trująca wiadomość jest usuwana, gdy `ReceiveErrorHandling` Właściwość w sieci msmqbinding lub MsmqIntegrationBinding jest ustawiona na `Drop` .</span><span class="sxs-lookup"><span data-stu-id="441e1-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="441e1-109">Usunięty komunikat jest usuwany z kolejki i nie jest już możliwy do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="441e1-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="441e1-110">Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="441e1-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441e1-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="441e1-111">See also</span></span>

- [<span data-ttu-id="441e1-112">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="441e1-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="441e1-113">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="441e1-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="441e1-114">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="441e1-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="441e1-115">Obsługa komunikatów trujących</span><span class="sxs-lookup"><span data-stu-id="441e1-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
