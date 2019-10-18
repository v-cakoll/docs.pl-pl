---
title: Narzędzia do przenoszenia do platformy .NET Core
description: Dowiedz się więcej na temat niektórych narzędzi, których można użyć do przenoszenia do programu .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 0478719617741946768cfe8e220a1dd402667998
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521349"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="90bd8-103">Narzędzia pomagające przenosić kod na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="90bd8-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="90bd8-104">Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:</span><span class="sxs-lookup"><span data-stu-id="90bd8-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="90bd8-105">[Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — łańcucha narzędzi, który może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i .NET Core: jako [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="90bd8-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="90bd8-106">Analizator [interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla C# interfejsów API na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="90bd8-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="90bd8-107">Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) .</span><span class="sxs-lookup"><span data-stu-id="90bd8-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="90bd8-108">CsprojToVs2017 jest narzędziem innej firmy.</span><span class="sxs-lookup"><span data-stu-id="90bd8-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="90bd8-109">Nie ma gwarancji, że będzie ona działała we wszystkich projektach i może spowodować drobne zmiany w zachowaniu, od którego zależy.</span><span class="sxs-lookup"><span data-stu-id="90bd8-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="90bd8-110">CsprojToVs2017 powinien być używany jako _punkt wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane.</span><span class="sxs-lookup"><span data-stu-id="90bd8-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="90bd8-111">Nie jest to gwarantowane rozwiązanie do migrowania formatów plików projektu.</span><span class="sxs-lookup"><span data-stu-id="90bd8-111">It is not a guaranteed solution to migrating project file formats.</span></span>
