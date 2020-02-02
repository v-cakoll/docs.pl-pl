---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920741"
---

<span data-ttu-id="075e8-101">Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span><span class="sxs-lookup"><span data-stu-id="075e8-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="075e8-102">Ogólnie mówiąc, ten błąd oznacza, że źródło danych pakietu dla platformy .NET Core jest uaktualniane z nowszymi wersjami pakietów i należy spróbować ponownie później.</span><span class="sxs-lookup"><span data-stu-id="075e8-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="075e8-103">Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez więcej niż 2 godziny.</span><span class="sxs-lookup"><span data-stu-id="075e8-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="075e8-104">Jeśli ten błąd będzie ciągle wyświetlany przez ponad 2 godziny, należy rozwiązać problem w <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="075e8-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
