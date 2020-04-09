---
title: Narzędzia do przenoszenia do platformy .NET Core
description: Dowiedz się więcej o narzędziach, za pomocą których można portować do platformy .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 64bad7600d8e17ada83d4bd8bc56762fd1789f43
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989132"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="8a0ad-103">Narzędzia pomagające przenosić kod na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="8a0ad-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="8a0ad-104">Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:</span><span class="sxs-lookup"><span data-stu-id="8a0ad-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="8a0ad-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) — toolchain, który może wygenerować raport, jak przenośny kod jest między .NET Framework i .NET Core:</span><span class="sxs-lookup"><span data-stu-id="8a0ad-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="8a0ad-106">Jako [narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="8a0ad-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="8a0ad-107">Jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="8a0ad-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="8a0ad-108">[Analizator interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — analizator Roslyn, który wykrywa potencjalne zagrożenia zgodności dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="8a0ad-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="8a0ad-109">Ponadto można spróbować przenieść mniejsze rozwiązania lub poszczególne projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)</span><span class="sxs-lookup"><span data-stu-id="8a0ad-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="8a0ad-110">CsprojToVs2017 jest narzędziem innej firmy.</span><span class="sxs-lookup"><span data-stu-id="8a0ad-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="8a0ad-111">Nie ma żadnej gwarancji, że będzie działać dla wszystkich projektów i może spowodować subtelne zmiany w zachowaniu, które zależą od.</span><span class="sxs-lookup"><span data-stu-id="8a0ad-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="8a0ad-112">CsprojToVs2017 powinny być używane jako _punkt wyjścia,_ który automatyzuje podstawowe rzeczy, które mogą być zautomatyzowane.</span><span class="sxs-lookup"><span data-stu-id="8a0ad-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="8a0ad-113">Nie jest to gwarantowane rozwiązanie do migracji formatów plików projektu.</span><span class="sxs-lookup"><span data-stu-id="8a0ad-113">It is not a guaranteed solution to migrating project file formats.</span></span>
