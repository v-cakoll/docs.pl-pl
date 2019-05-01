---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950465"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="4537e-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="4537e-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="4537e-103">Moduł PeerMaintainer wykonuje określoną operację (szczegóły zawartych w treści komunikatu śledzenia).</span><span class="sxs-lookup"><span data-stu-id="4537e-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="4537e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="4537e-104">Description</span></span>  
 <span data-ttu-id="4537e-105">Ślad występuje podczas wykonywania różnych operacji PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="4537e-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="4537e-106">PeerMaintainer jest składnikiem wewnętrznego węzeł równorzędny.</span><span class="sxs-lookup"><span data-stu-id="4537e-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="4537e-107">Co minutę lub co 32 komunikaty odbierane, wysyła wiadomość LinkUtility dla swoich sąsiadów ze statystykami o ile komunikaty są wymieniane i ile są przydatne (innych niż duplikatów, untampered).</span><span class="sxs-lookup"><span data-stu-id="4537e-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="4537e-108">Dzięki temu można ustalić określonego sąsiada łącze narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4537e-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="4537e-109">Co około pięciu minut, Element utrzymujący sprawdza kondycję sąsiada połączeń.</span><span class="sxs-lookup"><span data-stu-id="4537e-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="4537e-110">Jeśli liczba połączeń sąsiada przekracza kwotę idealne, Element utrzymujący oczyszcza off najmniej przydatne połączeń.</span><span class="sxs-lookup"><span data-stu-id="4537e-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="4537e-111">Jeśli nie ma wystarczającej liczby połączeń, Element utrzymujący uzyskuje nowe połączenia.</span><span class="sxs-lookup"><span data-stu-id="4537e-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4537e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4537e-112">See also</span></span>

- [<span data-ttu-id="4537e-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="4537e-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4537e-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="4537e-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4537e-115">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="4537e-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
