---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237615"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="a0ed5-101">Ulepszenia przydzielanie algorytm obszarze star wierszy siatki</span><span class="sxs-lookup"><span data-stu-id="a0ed5-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a0ed5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a0ed5-102">Details</span></span>|<span data-ttu-id="a0ed5-103">Usunięto usterkę w [algorytm rozmiarów do przydzielania](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="a0ed5-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="a0ed5-104">W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.</span><span class="sxs-lookup"><span data-stu-id="a0ed5-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="a0ed5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a0ed5-105">Suggestion</span></span>|<span data-ttu-id="a0ed5-106">Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="a0ed5-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="a0ed5-107">Scope</span><span class="sxs-lookup"><span data-stu-id="a0ed5-107">Scope</span></span>|<span data-ttu-id="a0ed5-108">Duży</span><span class="sxs-lookup"><span data-stu-id="a0ed5-108">Major</span></span>|
|<span data-ttu-id="a0ed5-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="a0ed5-109">Version</span></span>|<span data-ttu-id="a0ed5-110">4.8</span><span class="sxs-lookup"><span data-stu-id="a0ed5-110">4.8</span></span>|
|<span data-ttu-id="a0ed5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a0ed5-111">Type</span></span>|<span data-ttu-id="a0ed5-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a0ed5-112">Runtime</span></span>|
