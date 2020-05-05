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
# <a name="tools-to-help-with-porting-to-net-core"></a>Narzędzia pomagające przenosić kod na platformę .NET Core

Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:

- [Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — łańcucha narzędzi, który może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i .NET Core:
  - Jako [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- Analizator [interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.
- [try-Convert](https://www.nuget.org/packages/try-convert/) -narzędzie globalne platformy .NET Core, które może przekonwertować projekt lub całe rozwiązanie do zestawu .NET SDK, w tym przenieść aplikacje klasyczne do platformy .NET Core. Nie jest to zalecane, jeśli istnieje bardziej skomplikowana kompilacja (na przykład zadania niestandardowe, obiekty docelowe lub Importy), która odrzuca wiele typów projektów niezgodnych z platformą .NET Core.
