---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a134a60656c6ee237203b69e1bce40656f13d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="5a0d0-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="5a0d0-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="5a0d0-103">Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="5a0d0-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a0d0-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5a0d0-104">Description</span></span>  
 <span data-ttu-id="5a0d0-105">Wskazuje śledzenia poziomu ten błąd wystąpił błąd podczas zamykania pul połączeń używanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]przez funkcję puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="5a0d0-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="5a0d0-106">Jedną z możliwych przyczyn tego jest zamknięcie połączenia z puli nie powiodło się lub zestawu puli połączeń w ramach limitu czasu zamykania.</span><span class="sxs-lookup"><span data-stu-id="5a0d0-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="5a0d0-107">Wszystkie pozostałe niezamknięty połączenia w tej puli są przerywane, gdy ten wyjątek; niezamknięty połączeń w innych pulach zostały porzucone.</span><span class="sxs-lookup"><span data-stu-id="5a0d0-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0d0-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a0d0-108">See Also</span></span>  
 [<span data-ttu-id="5a0d0-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5a0d0-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5a0d0-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5a0d0-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5a0d0-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5a0d0-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
