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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="9e819-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="9e819-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="9e819-103">Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="9e819-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e819-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9e819-104">Description</span></span>  
 <span data-ttu-id="9e819-105">Wskazuje śledzenia poziomu ten błąd wystąpił błąd podczas zamykania pul połączeń używanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]przez funkcję puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="9e819-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="9e819-106">Jedną z możliwych przyczyn tego jest zamknięcie połączenia z puli nie powiodło się lub zestawu puli połączeń w ramach limitu czasu zamykania.</span><span class="sxs-lookup"><span data-stu-id="9e819-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="9e819-107">Wszystkie pozostałe niezamknięty połączenia w tej puli są przerywane, gdy ten wyjątek; niezamknięty połączeń w innych pulach zostały porzucone.</span><span class="sxs-lookup"><span data-stu-id="9e819-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e819-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e819-108">See Also</span></span>  
 [<span data-ttu-id="9e819-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="9e819-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9e819-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="9e819-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9e819-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="9e819-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
