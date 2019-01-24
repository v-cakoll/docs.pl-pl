---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 22d2605c3c96c0e030f9e435293de42094965cb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627953"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="f34d7-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="f34d7-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="f34d7-103">Próba połączenia z punktem końcowym nazwanego potoku nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="f34d7-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="f34d7-104">Podejmowana jest kolejna próba przed upływem określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f34d7-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f34d7-105">Opis</span><span class="sxs-lookup"><span data-stu-id="f34d7-105">Description</span></span>  
 <span data-ttu-id="f34d7-106">Informacyjny ślad oznacza błąd nawiązać połączenia z punktem końcowym nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="f34d7-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="f34d7-107">Może się to zdarzyć, jeśli punkt końcowy nazwany potok nie zostanie znaleziony lub jest zajęty.</span><span class="sxs-lookup"><span data-stu-id="f34d7-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="f34d7-108">Dodatkowe prób, każda jest oddzielona przez krótki ilość czasu, aż któraś się powiedzie, lub OpenTimeout wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="f34d7-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34d7-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f34d7-109">See also</span></span>
- [<span data-ttu-id="f34d7-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f34d7-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="f34d7-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f34d7-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f34d7-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f34d7-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
