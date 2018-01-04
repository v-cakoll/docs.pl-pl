---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df0f983d646ea89eeef338b9742843e9fa50487b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="40d60-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="40d60-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="40d60-103">Próba ponownego użycia połączenia z puli nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="40d60-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="40d60-104">Podejmowana jest kolejna przed upływem określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="40d60-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="40d60-105">Opis</span><span class="sxs-lookup"><span data-stu-id="40d60-105">Description</span></span>  
 <span data-ttu-id="40d60-106">Ślad informacyjną wskazuje wystąpił błąd podczas próby ponownego użycia połączenia z puli.</span><span class="sxs-lookup"><span data-stu-id="40d60-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="40d60-107">Może się to zdarzyć, ponieważ połączenie z puli nie jest zgodne, gotowe lub nadal aktywne.</span><span class="sxs-lookup"><span data-stu-id="40d60-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="40d60-108">Dodatkowe ponowne połączenia z innymi puli prób w ciągu danego limitu czasu i tworzenia nowego połączenia w przypadku, gdy nie można używać są znaleziono połączeń.</span><span class="sxs-lookup"><span data-stu-id="40d60-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d60-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40d60-109">See Also</span></span>  
 [<span data-ttu-id="40d60-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="40d60-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="40d60-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="40d60-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="40d60-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="40d60-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
