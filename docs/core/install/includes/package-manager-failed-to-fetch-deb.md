---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920656"
---

<span data-ttu-id="1468a-101">Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span><span class="sxs-lookup"><span data-stu-id="1468a-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="1468a-102">Ogólnie mówiąc, ten błąd oznacza, że źródło danych pakietu dla platformy .NET Core jest uaktualniane z nowszymi wersjami pakietów i należy spróbować ponownie później.</span><span class="sxs-lookup"><span data-stu-id="1468a-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="1468a-103">Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez ponad 30 minut.</span><span class="sxs-lookup"><span data-stu-id="1468a-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="1468a-104">Jeśli ten błąd będzie ciągle wyświetlany przez ponad 30 minut, należy rozwiązać problem w <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="1468a-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
