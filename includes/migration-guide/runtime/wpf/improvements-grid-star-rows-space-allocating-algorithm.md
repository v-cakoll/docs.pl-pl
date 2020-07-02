---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622096"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="4e4f8-101">Ulepszenia siatki z gwiazdkami — przydzielenie algorytmu w przestrzeni wierszy</span><span class="sxs-lookup"><span data-stu-id="4e4f8-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="4e4f8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4e4f8-102">Details</span></span>

<span data-ttu-id="4e4f8-103">Rozwiązano usterkę w [algorytmie przydzielania rozmiarów do](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)programu w ramach <xref:System.Windows.Controls.Grid> wprowadzenia w .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="4e4f8-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="4e4f8-104">W niektórych przypadkach, takich jak siatka <code>Height=&quot;Auto&quot;</code> zawierająca puste wiersze, wiersze były ułożone w niewłaściwej pozycji, prawdopodobnie poza siatką.</span><span class="sxs-lookup"><span data-stu-id="4e4f8-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e4f8-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4e4f8-105">Suggestion</span></span>

<span data-ttu-id="4e4f8-106">Aby aplikacja mogła korzystać z tych zmian, należy ją uruchomić w .NET Framework 4,8 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="4e4f8-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="4e4f8-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4e4f8-107">Name</span></span>    | <span data-ttu-id="4e4f8-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e4f8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4e4f8-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="4e4f8-109">Scope</span></span>   |<span data-ttu-id="4e4f8-110">Duży</span><span class="sxs-lookup"><span data-stu-id="4e4f8-110">Major</span></span>|
|<span data-ttu-id="4e4f8-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="4e4f8-111">Version</span></span>|<span data-ttu-id="4e4f8-112">4,8</span><span class="sxs-lookup"><span data-stu-id="4e4f8-112">4.8</span></span>|
|<span data-ttu-id="4e4f8-113">Typ</span><span class="sxs-lookup"><span data-stu-id="4e4f8-113">Type</span></span>|<span data-ttu-id="4e4f8-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4e4f8-114">Runtime</span></span>|
