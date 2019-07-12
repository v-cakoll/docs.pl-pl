---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802689"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="9015d-101">Ulepszenia przydzielanie algorytm obszarze star wierszy siatki</span><span class="sxs-lookup"><span data-stu-id="9015d-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9015d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9015d-102">Details</span></span>|<span data-ttu-id="9015d-103">Usunięto usterkę w [algorytm rozmiarów do przydzielania ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9015d-103">Fixed a bug in the [algorithm for allocating sizes to ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="9015d-104">W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.</span><span class="sxs-lookup"><span data-stu-id="9015d-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="9015d-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="9015d-105">Suggestion</span></span>|<span data-ttu-id="9015d-106">Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9015d-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="9015d-107">Scope</span><span class="sxs-lookup"><span data-stu-id="9015d-107">Scope</span></span>|<span data-ttu-id="9015d-108">Duży</span><span class="sxs-lookup"><span data-stu-id="9015d-108">Major</span></span>|
|<span data-ttu-id="9015d-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="9015d-109">Version</span></span>|<span data-ttu-id="9015d-110">4.8</span><span class="sxs-lookup"><span data-stu-id="9015d-110">4.8</span></span>|
|<span data-ttu-id="9015d-111">Typ</span><span class="sxs-lookup"><span data-stu-id="9015d-111">Type</span></span>|<span data-ttu-id="9015d-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9015d-112">Runtime</span></span>|

