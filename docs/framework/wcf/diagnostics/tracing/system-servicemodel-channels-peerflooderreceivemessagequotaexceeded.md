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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="cc047-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="cc047-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="cc047-103">Szybkość odbierania przychodzących komunikatów jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="cc047-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc047-104">Opis</span><span class="sxs-lookup"><span data-stu-id="cc047-104">Description</span></span>  
 <span data-ttu-id="cc047-105">Ślad występuje podczas próby przetworzenia wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="cc047-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="cc047-106">Nie można przesłać dalej wiadomości do określonych sąsiada, ponieważ przekroczono limit przydziału określony dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="cc047-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="cc047-107">Dzieje się tak w przypadku niepowodzenia wyczyść zaległości komunikatów oczekujących dla tego sąsiada sąsiada nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="cc047-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cc047-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="cc047-108">Troubleshooting</span></span>  
 <span data-ttu-id="cc047-109">Zmniejsz szybkość, z jaką komunikaty wewnątrz siatki.</span><span class="sxs-lookup"><span data-stu-id="cc047-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc047-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc047-110">See Also</span></span>  
 [<span data-ttu-id="cc047-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cc047-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cc047-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="cc047-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cc047-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="cc047-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
