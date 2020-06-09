---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602053"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="0f22c-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="0f22c-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="0f22c-103">Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="0f22c-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f22c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0f22c-104">Description</span></span>  
 <span data-ttu-id="0f22c-105">Ten ślad poziomu błędu wskazuje, że wystąpił błąd podczas zamykania pul połączeń używanych przez funkcję puli połączeń Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0f22c-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="0f22c-106">Jedną z możliwych przyczyn jest to nieudane zamknięcie połączenia w puli lub zestaw połączeń w puli w ramach CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="0f22c-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="0f22c-107">Gdy ten wyjątek jest zgłaszany, wszystkie pozostałe niezamknięte połączenia w tej puli są przerywane; niezamknięte połączenia w innych pulach są porzucane.</span><span class="sxs-lookup"><span data-stu-id="0f22c-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f22c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f22c-108">See also</span></span>

- [<span data-ttu-id="0f22c-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0f22c-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="0f22c-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0f22c-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0f22c-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0f22c-111">Administration and Diagnostics</span></span>](../index.md)
