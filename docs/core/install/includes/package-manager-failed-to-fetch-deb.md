---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920656"
---

<span data-ttu-id="3dddb-101">Podczas instalowania pakietu .NET Core może zostać `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`wyświetlony błąd podobny do .</span><span class="sxs-lookup"><span data-stu-id="3dddb-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="3dddb-102">Ogólnie rzecz biorąc ten błąd oznacza, że kanał informacyjny pakietu dla .NET Core jest uaktualniany z nowszych wersji pakietu i że należy spróbować ponownie później.</span><span class="sxs-lookup"><span data-stu-id="3dddb-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="3dddb-103">Podczas uaktualniania kanał informacyjny pakietu nie powinien być niedostępny dłużej niż 30 minut.</span><span class="sxs-lookup"><span data-stu-id="3dddb-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="3dddb-104">Jeśli ten błąd jest stale wyświetlany przez ponad 30 <https://github.com/dotnet/core/issues>minut, zgłoś problem w .</span><span class="sxs-lookup"><span data-stu-id="3dddb-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
