---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="263e7-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="263e7-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="263e7-103">Moduł PeerMaintainer wykonuje określonej operacji (szczegółowe informacje zawarte w treści wiadomości śledzenia).</span><span class="sxs-lookup"><span data-stu-id="263e7-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="263e7-104">Opis</span><span class="sxs-lookup"><span data-stu-id="263e7-104">Description</span></span>  
 <span data-ttu-id="263e7-105">Ślad występuje w ciągu różne operacje PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="263e7-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="263e7-106">PeerMaintainer jest to wewnętrzny składnik węzeł równorzędny.</span><span class="sxs-lookup"><span data-stu-id="263e7-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="263e7-107">Co minutę lub co 32 komunikatów odebranych, wysyła wiadomość LinkUtility z jej sąsiadami dane statystyczne o ile komunikatów są wymieniane i ile są przydatne (z systemem innym niż — duplikatów, untampered).</span><span class="sxs-lookup"><span data-stu-id="263e7-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="263e7-108">Dzięki temu można ustalić określonego sąsiada łącze narzędzia.</span><span class="sxs-lookup"><span data-stu-id="263e7-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="263e7-109">Co około pięciu minut, Element utrzymujący sprawdza stan sąsiedniego połączenia.</span><span class="sxs-lookup"><span data-stu-id="263e7-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="263e7-110">Jeśli liczba połączeń sąsiada przekracza wielkość idealne, Element utrzymujący oczyszcza poza przydatne najmniej połączeń.</span><span class="sxs-lookup"><span data-stu-id="263e7-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="263e7-111">Jeśli nie ma wystarczającej liczby połączeń, Element utrzymujący uzyskuje nowe połączenia.</span><span class="sxs-lookup"><span data-stu-id="263e7-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263e7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="263e7-112">See Also</span></span>  
 [<span data-ttu-id="263e7-113">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="263e7-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="263e7-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="263e7-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="263e7-115">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="263e7-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
