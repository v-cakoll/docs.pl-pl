---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="cd84c-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="cd84c-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="cd84c-103">Szybkość odbierania przychodzących komunikatów jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="cd84c-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd84c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="cd84c-104">Description</span></span>  
 <span data-ttu-id="cd84c-105">Ślad występuje podczas próby przetworzenia wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="cd84c-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="cd84c-106">Nie można przesłać dalej wiadomości do określonych sąsiada, ponieważ przekroczono limit przydziału określony dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="cd84c-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="cd84c-107">Dzieje się tak w przypadku niepowodzenia wyczyść zaległości komunikatów oczekujących dla tego sąsiada sąsiada nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="cd84c-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cd84c-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="cd84c-108">Troubleshooting</span></span>  
 <span data-ttu-id="cd84c-109">Zmniejsz szybkość, z jaką komunikaty wewnątrz siatki.</span><span class="sxs-lookup"><span data-stu-id="cd84c-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd84c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd84c-110">See Also</span></span>  
 [<span data-ttu-id="cd84c-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cd84c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cd84c-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="cd84c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cd84c-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="cd84c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
