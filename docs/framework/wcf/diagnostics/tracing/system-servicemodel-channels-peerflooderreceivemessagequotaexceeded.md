---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 5c1e6c51ffd5aeafe65a67c8989f554ebf0824d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478920"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="626db-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="626db-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="626db-103">Szybkość odbierania przychodzących komunikatów jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="626db-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="626db-104">Opis</span><span class="sxs-lookup"><span data-stu-id="626db-104">Description</span></span>  
 <span data-ttu-id="626db-105">Ślad występuje podczas próby przetworzenia wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="626db-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="626db-106">Nie można przesłać dalej wiadomości do określonych sąsiada, ponieważ przekroczono limit przydziału określony dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="626db-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="626db-107">Dzieje się tak w przypadku niepowodzenia wyczyść zaległości komunikatów oczekujących dla tego sąsiada sąsiada nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="626db-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="626db-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="626db-108">Troubleshooting</span></span>  
 <span data-ttu-id="626db-109">Zmniejsz szybkość, z jaką komunikaty wewnątrz siatki.</span><span class="sxs-lookup"><span data-stu-id="626db-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626db-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="626db-110">See Also</span></span>  
 [<span data-ttu-id="626db-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="626db-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="626db-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="626db-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="626db-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="626db-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
