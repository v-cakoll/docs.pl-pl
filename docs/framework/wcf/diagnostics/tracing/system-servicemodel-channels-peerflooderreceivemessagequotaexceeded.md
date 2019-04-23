---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190902"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="4303d-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="4303d-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="4303d-103">Szybkość odbierania przychodzących komunikatów jest zbyt wysoka.</span><span class="sxs-lookup"><span data-stu-id="4303d-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4303d-104">Opis</span><span class="sxs-lookup"><span data-stu-id="4303d-104">Description</span></span>  
 <span data-ttu-id="4303d-105">Ślad występuje podczas próby przetworzenia przychodzących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4303d-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="4303d-106">Nie można przesłać dalej wiadomość do określonych sąsiada, ponieważ przekroczono limit przydziału, ustaw dla tej sąsiada.</span><span class="sxs-lookup"><span data-stu-id="4303d-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="4303d-107">Dzieje się tak, gdy sąsiada nie odpowiada nie powiedzie się wyczyścić zaległości komunikatów oczekujących dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="4303d-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4303d-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="4303d-108">Troubleshooting</span></span>  
 <span data-ttu-id="4303d-109">Zmniejsz szybkość jaką komunikaty są wysyłane w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="4303d-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4303d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4303d-110">See also</span></span>

- [<span data-ttu-id="4303d-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="4303d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4303d-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="4303d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4303d-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="4303d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
