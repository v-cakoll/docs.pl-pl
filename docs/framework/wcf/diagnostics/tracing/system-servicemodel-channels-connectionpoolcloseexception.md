---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: b2d49910ecbcd67beca83e2fbeabfbcafe6e1dd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628035"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="754e0-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="754e0-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="754e0-103">Wystąpił wyjątek podczas zamykania połączenia w tej puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="754e0-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="754e0-104">Opis</span><span class="sxs-lookup"><span data-stu-id="754e0-104">Description</span></span>  
 <span data-ttu-id="754e0-105">Śledzenie poziomu ten błąd wskazuje, wystąpił błąd podczas zamykania pul połączeń używane przez funkcję buforowanie połączenia z programem Windows Communication Foundation (WCF) firmy.</span><span class="sxs-lookup"><span data-stu-id="754e0-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="754e0-106">Jedną z możliwych przyczyn tego jest powiodło się zamknięcie połączenia z puli lub zbiór puli połączeń w ramach CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="754e0-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="754e0-107">Gdy ten wyjątek jest zgłaszany, wszystkie pozostałe zamknięto połączenia w tej puli zostaną przerwane; Zamknięto połączenia w innych pulach są porzucona.</span><span class="sxs-lookup"><span data-stu-id="754e0-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754e0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="754e0-108">See also</span></span>
- [<span data-ttu-id="754e0-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="754e0-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="754e0-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="754e0-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="754e0-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="754e0-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
