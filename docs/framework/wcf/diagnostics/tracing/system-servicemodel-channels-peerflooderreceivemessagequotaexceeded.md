---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596093"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="7eb88-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="7eb88-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="7eb88-103">Szybkość odbierania komunikatów przychodzących jest zbyt wysoka.</span><span class="sxs-lookup"><span data-stu-id="7eb88-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7eb88-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7eb88-104">Description</span></span>  
 <span data-ttu-id="7eb88-105">Ten ślad występuje podczas próby przetworzenia komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="7eb88-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="7eb88-106">Nie można przesłać komunikatu do określonego sąsiada, ponieważ został przekroczony limit przydziału ustawiony dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="7eb88-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="7eb88-107">Dzieje się tak, gdy nieodpowiadający sąsiad nie może wyczyścić zaległości komunikatów oczekujących dla tego sąsiada.</span><span class="sxs-lookup"><span data-stu-id="7eb88-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7eb88-108">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="7eb88-108">Troubleshooting</span></span>  
 <span data-ttu-id="7eb88-109">Zmniejsz szybkość, z jaką komunikaty są wysyłane w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="7eb88-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb88-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7eb88-110">See also</span></span>

- [<span data-ttu-id="7eb88-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7eb88-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="7eb88-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7eb88-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7eb88-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7eb88-113">Administration and Diagnostics</span></span>](../index.md)
