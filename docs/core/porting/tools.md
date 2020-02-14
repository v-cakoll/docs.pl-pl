---
title: Narzędzia do przenoszenia do platformy .NET Core
description: Dowiedz się więcej na temat niektórych narzędzi, których można użyć do przenoszenia do programu .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 3b71c31b4f26b278b2bd1088adc8e9f64d28ab7b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215192"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="bc774-103">Narzędzia pomagające przenosić kod na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc774-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="bc774-104">Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:</span><span class="sxs-lookup"><span data-stu-id="bc774-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="bc774-105">[Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — łańcucha narzędzi, który może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bc774-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="bc774-106">Jako [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="bc774-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="bc774-107">Jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="bc774-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="bc774-108">Analizator [interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla C# interfejsów API na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="bc774-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="bc774-109">Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) .</span><span class="sxs-lookup"><span data-stu-id="bc774-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="bc774-110">CsprojToVs2017 jest narzędziem innej firmy.</span><span class="sxs-lookup"><span data-stu-id="bc774-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="bc774-111">Nie ma gwarancji, że będzie ona działała we wszystkich projektach i może spowodować drobne zmiany w zachowaniu, od którego zależy.</span><span class="sxs-lookup"><span data-stu-id="bc774-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="bc774-112">CsprojToVs2017 powinien być używany jako _punkt wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane.</span><span class="sxs-lookup"><span data-stu-id="bc774-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="bc774-113">Nie jest to gwarantowane rozwiązanie do migrowania formatów plików projektu.</span><span class="sxs-lookup"><span data-stu-id="bc774-113">It is not a guaranteed solution to migrating project file formats.</span></span>
