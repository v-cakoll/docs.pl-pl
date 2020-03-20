---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237615"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="24042-101">Ulepszenia algorytmu przydzielania miejsca w wierszach gwiazd siatki</span><span class="sxs-lookup"><span data-stu-id="24042-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="24042-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="24042-102">Details</span></span>|<span data-ttu-id="24042-103">Naprawiono błąd w [algorytmie przydzielania rozmiarów do)](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)w wprowadzonym <xref:System.Windows.Controls.Grid> w .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="24042-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="24042-104">W niektórych przypadkach, takich <code>Height=&quot;Auto&quot;</code> jak Grid z zawierającym puste wiersze, wiersze zostały rozmieszczone w niewłaściwym położeniu, prawdopodobnie poza Grid całkowicie.</span><span class="sxs-lookup"><span data-stu-id="24042-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="24042-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="24042-105">Suggestion</span></span>|<span data-ttu-id="24042-106">Aby aplikacja korzystać z tych zmian, należy uruchomić na .NET Framework 4.8 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="24042-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="24042-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="24042-107">Scope</span></span>|<span data-ttu-id="24042-108">Duży</span><span class="sxs-lookup"><span data-stu-id="24042-108">Major</span></span>|
|<span data-ttu-id="24042-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="24042-109">Version</span></span>|<span data-ttu-id="24042-110">4.8</span><span class="sxs-lookup"><span data-stu-id="24042-110">4.8</span></span>|
|<span data-ttu-id="24042-111">Typ</span><span class="sxs-lookup"><span data-stu-id="24042-111">Type</span></span>|<span data-ttu-id="24042-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="24042-112">Runtime</span></span>|
