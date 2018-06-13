---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475754"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="f296f-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="f296f-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="f296f-103">Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="f296f-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f296f-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f296f-104">Description</span></span>  
 <span data-ttu-id="f296f-105">Śledzenie poziomu ten błąd wskazuje, wystąpił błąd podczas zamykania pul połączeń używanych przez buforowania funkcji Windows Communication Foundation (WCF) dla połączeń.</span><span class="sxs-lookup"><span data-stu-id="f296f-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="f296f-106">Jedną z możliwych przyczyn tego jest zamknięcie połączenia z puli nie powiodło się lub zestawu puli połączeń w ramach limitu czasu zamykania.</span><span class="sxs-lookup"><span data-stu-id="f296f-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="f296f-107">Wszystkie pozostałe niezamknięty połączenia w tej puli są przerywane, gdy ten wyjątek; niezamknięty połączeń w innych pulach zostały porzucone.</span><span class="sxs-lookup"><span data-stu-id="f296f-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f296f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f296f-108">See Also</span></span>  
 [<span data-ttu-id="f296f-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f296f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f296f-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f296f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f296f-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f296f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
