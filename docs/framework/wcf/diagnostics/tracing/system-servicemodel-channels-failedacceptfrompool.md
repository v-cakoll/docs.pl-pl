---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156484"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="883bd-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="883bd-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="883bd-103">Próba ponownego użycia połączenia z puli nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="883bd-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="883bd-104">Podejmowana jest kolejna próba przed upływem określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="883bd-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="883bd-105">Opis</span><span class="sxs-lookup"><span data-stu-id="883bd-105">Description</span></span>  
 <span data-ttu-id="883bd-106">Informacyjny ślad wskazuje wystąpił błąd podczas próby ponownego użycia puli połączeń.</span><span class="sxs-lookup"><span data-stu-id="883bd-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="883bd-107">Może się to zdarzyć, ponieważ połączenie z puli nie jest zgodne, gotowe lub nadal aktywne.</span><span class="sxs-lookup"><span data-stu-id="883bd-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="883bd-108">Dodatkowe ponowne użycie innego połączenia puli prób w ciągu danego limitu czasu, a nowe połączenie zostanie utworzona w przypadku, gdy zostaną znalezione żadne można używać połączenia.</span><span class="sxs-lookup"><span data-stu-id="883bd-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883bd-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="883bd-109">See also</span></span>

- [<span data-ttu-id="883bd-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="883bd-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="883bd-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="883bd-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="883bd-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="883bd-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
