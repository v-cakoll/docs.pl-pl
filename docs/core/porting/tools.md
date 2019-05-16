---
title: Narzędzia do przenoszenia do programu .NET Core
description: Dowiedz się więcej o niektórych narzędzi służących do portu i .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: d0b74b5708f31922b72fa0e236c8bbe69ae06217
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632250"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="f5326-103">Narzędzia ułatwiające wykonywanie eksportowanie do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f5326-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="f5326-104">Narzędzia wymienione w tym artykule, które są przydatne podczas przenoszenia może się okazać:</span><span class="sxs-lookup"><span data-stu-id="f5326-104">You may find the tools listed in this article helpful when porting:</span></span>

* <span data-ttu-id="f5326-105">[Narzędzia .NET portability Analyzer](../../standard/analyzers/portability-analyzer.md), łańcuch narzędzi, który można wygenerować raportu dotyczącego sposobu przenośny kod jest między .NET Framework i .NET Core:  Jako [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="f5326-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
* <span data-ttu-id="f5326-106">[Analizator interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) -analizatora Roslyn, który umożliwia odnalezienie potencjalnych problemów zagrożenie dla C# interfejsów API na różnych platformach i wykrywa wywołania interfejsów API przestarzałych.</span><span class="sxs-lookup"><span data-stu-id="f5326-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="f5326-107">Ponadto, możesz spróbować rozwiązań mniejszych portu lub poszczególnych projektów do formatu pliku projektu .NET Core za pomocą [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="f5326-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="f5326-108">CsprojToVs2017 to narzędzia innych firm.</span><span class="sxs-lookup"><span data-stu-id="f5326-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="f5326-109">Nie ma żadnej gwarancji, która będzie działać w przypadku wszystkich swoich projektach i może spowodować, że wprowadzono subtelne zmiany w zachowaniu, który, na których polegasz.</span><span class="sxs-lookup"><span data-stu-id="f5326-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="f5326-110">CsprojToVs2017 powinien być używany jako _punkt początkowy_ który automatyzuje podstawowe czynności, które można zautomatyzować.</span><span class="sxs-lookup"><span data-stu-id="f5326-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="f5326-111">Nie jest gwarantowana rozwiązania do migrowania formatów plików projektu.</span><span class="sxs-lookup"><span data-stu-id="f5326-111">It is not a guaranteed solution to migrating project file formats.</span></span>
