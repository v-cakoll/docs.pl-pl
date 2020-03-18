---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920741"
---

<span data-ttu-id="50de0-101">Podczas instalowania pakietu .NET Core może zostać `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`wyświetlony błąd podobny do .</span><span class="sxs-lookup"><span data-stu-id="50de0-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="50de0-102">Ogólnie rzecz biorąc ten błąd oznacza, że kanał informacyjny pakietu dla .NET Core jest uaktualniany z nowszych wersji pakietu i że należy spróbować ponownie później.</span><span class="sxs-lookup"><span data-stu-id="50de0-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="50de0-103">Podczas uaktualniania kanał informacyjny pakietu nie powinien być niedostępny dłużej niż 2 godziny.</span><span class="sxs-lookup"><span data-stu-id="50de0-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="50de0-104">Jeśli ten błąd jest stale wyświetlany przez ponad 2 <https://github.com/dotnet/core/issues>godziny, zgłać problem w .</span><span class="sxs-lookup"><span data-stu-id="50de0-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
