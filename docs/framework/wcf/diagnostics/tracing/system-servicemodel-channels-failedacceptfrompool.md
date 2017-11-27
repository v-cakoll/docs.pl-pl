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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e50e104816567927f53673f9b1da9c3c5beac3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="b5a0a-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="b5a0a-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="b5a0a-103">Próba ponownego użycia połączenia z puli nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b5a0a-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="b5a0a-104">Podejmowana jest kolejna przed upływem określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="b5a0a-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5a0a-105">Opis</span><span class="sxs-lookup"><span data-stu-id="b5a0a-105">Description</span></span>  
 <span data-ttu-id="b5a0a-106">Ślad informacyjną wskazuje wystąpił błąd podczas próby ponownego użycia połączenia z puli.</span><span class="sxs-lookup"><span data-stu-id="b5a0a-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="b5a0a-107">Może się to zdarzyć, ponieważ połączenie z puli nie jest zgodne, gotowe lub nadal aktywne.</span><span class="sxs-lookup"><span data-stu-id="b5a0a-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="b5a0a-108">Dodatkowe ponowne połączenia z innymi puli prób w ciągu danego limitu czasu i tworzenia nowego połączenia w przypadku, gdy nie można używać są znaleziono połączeń.</span><span class="sxs-lookup"><span data-stu-id="b5a0a-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a0a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5a0a-109">See Also</span></span>  
 [<span data-ttu-id="b5a0a-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="b5a0a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b5a0a-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5a0a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b5a0a-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="b5a0a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
