---
ms.openlocfilehash: bd3b1cc6a98f01d8c40b4cd67002e79a2c4fe714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982239"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="6b574-101">Ulepszenia przydzielanie algorytm obszarze star wierszy siatki</span><span class="sxs-lookup"><span data-stu-id="6b574-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6b574-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6b574-102">Details</span></span>|<span data-ttu-id="6b574-103">Usunięto usterkę w [algorytm rozmiarów do przydzielania \*-wierszy](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="6b574-103">Fixed a bug in the [algorithm for allocating sizes to \*-rows](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="6b574-104">W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.</span><span class="sxs-lookup"><span data-stu-id="6b574-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="6b574-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6b574-105">Suggestion</span></span>|<span data-ttu-id="6b574-106">Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="6b574-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="6b574-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="6b574-107">Scope</span></span>|<span data-ttu-id="6b574-108">Duży</span><span class="sxs-lookup"><span data-stu-id="6b574-108">Major</span></span>|
|<span data-ttu-id="6b574-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="6b574-109">Version</span></span>|<span data-ttu-id="6b574-110">4.8</span><span class="sxs-lookup"><span data-stu-id="6b574-110">4.8</span></span>|
|<span data-ttu-id="6b574-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6b574-111">Type</span></span>|<span data-ttu-id="6b574-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6b574-112">Runtime</span></span>|
