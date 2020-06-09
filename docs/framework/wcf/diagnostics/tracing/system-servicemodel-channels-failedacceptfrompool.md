---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582585"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="7ed9c-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="7ed9c-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="7ed9c-103">Próba ponownego użycia połączenia w puli nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7ed9c-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="7ed9c-104">Zostanie podjęta kolejna próba w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="7ed9c-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7ed9c-105">Opis</span><span class="sxs-lookup"><span data-stu-id="7ed9c-105">Description</span></span>  
 <span data-ttu-id="7ed9c-106">Ten ślad informacyjny wskazuje, że wystąpił błąd podczas próby ponownego użycia połączenia w puli.</span><span class="sxs-lookup"><span data-stu-id="7ed9c-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="7ed9c-107">Może się tak zdarzyć, ponieważ połączenie w puli nie jest zgodne, gotowe lub nadal aktywne.</span><span class="sxs-lookup"><span data-stu-id="7ed9c-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="7ed9c-108">Dodatkowe próby ponownego użycia innych połączeń w puli są wykonywane w ramach danego limitu czasu, a nowe połączenie jest tworzone w przypadku braku możliwości użycia połączeń.</span><span class="sxs-lookup"><span data-stu-id="7ed9c-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed9c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ed9c-109">See also</span></span>

- [<span data-ttu-id="7ed9c-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7ed9c-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="7ed9c-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7ed9c-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7ed9c-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7ed9c-112">Administration and Diagnostics</span></span>](../index.md)
