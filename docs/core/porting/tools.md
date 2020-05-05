---
title: Narzędzia do przenoszenia do platformy .NET Core
description: Dowiedz się więcej na temat niektórych narzędzi, których można użyć do przenoszenia do programu .NET Core
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795589"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="2878d-103">Narzędzia pomagające przenosić kod na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="2878d-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="2878d-104">Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:</span><span class="sxs-lookup"><span data-stu-id="2878d-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="2878d-105">[Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — łańcucha narzędzi, który może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2878d-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="2878d-106">Jako [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="2878d-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="2878d-107">Jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="2878d-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="2878d-108">Analizator [interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="2878d-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>
- <span data-ttu-id="2878d-109">[try-Convert](https://www.nuget.org/packages/try-convert/) -narzędzie globalne platformy .NET Core, które może przekonwertować projekt lub całe rozwiązanie do zestawu .NET SDK, w tym przenieść aplikacje klasyczne do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2878d-109">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="2878d-110">Nie jest to zalecane, jeśli istnieje bardziej skomplikowana kompilacja (na przykład zadania niestandardowe, obiekty docelowe lub Importy), która odrzuca wiele typów projektów niezgodnych z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2878d-110">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
