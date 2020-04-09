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
# <a name="tools-to-help-with-porting-to-net-core"></a>Narzędzia pomagające przenosić kod na platformę .NET Core

Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:

- [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) — toolchain, który może wygenerować raport, jak przenośny kod jest między .NET Framework i .NET Core:
  - Jako [narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozszerzenie programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Analizator interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — analizator Roslyn, który wykrywa potencjalne zagrożenia zgodności dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.

Ponadto można spróbować przenieść mniejsze rozwiązania lub poszczególne projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)

> [!WARNING]
> CsprojToVs2017 jest narzędziem innej firmy. Nie ma żadnej gwarancji, że będzie działać dla wszystkich projektów i może spowodować subtelne zmiany w zachowaniu, które zależą od. CsprojToVs2017 powinny być używane jako _punkt wyjścia,_ który automatyzuje podstawowe rzeczy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migracji formatów plików projektu.
