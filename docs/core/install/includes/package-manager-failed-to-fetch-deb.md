---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602979"
---

<span data-ttu-id="6dd8a-101">Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` .</span><span class="sxs-lookup"><span data-stu-id="6dd8a-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="6dd8a-102">Ten błąd może oznaczać, że kanał informacyjny pakietu dla platformy .NET Core jest uaktualniany z nowszymi wersjami pakietu i należy spróbować ponownie później.</span><span class="sxs-lookup"><span data-stu-id="6dd8a-102">This error could mean that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="6dd8a-103">Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez ponad 30 minut.</span><span class="sxs-lookup"><span data-stu-id="6dd8a-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="6dd8a-104">Jeśli ten błąd będzie ciągle wyświetlany przez ponad 30 minut, należy rozwiązać problem o <https://github.com/dotnet/core/issues> .</span><span class="sxs-lookup"><span data-stu-id="6dd8a-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
