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
# <a name="tools-to-help-with-porting-to-net-core"></a>Narzędzia pomagające przenosić kod na platformę .NET Core

Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:

- [Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — łańcucha narzędzi, który może generować raport dotyczący sposobu, w jaki przenośny kod jest między .NET Framework i .NET Core:
  - Jako [Narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
- Analizator [interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) — Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla C# interfejsów API na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.

Ponadto możesz próbować przenieść mniejsze rozwiązania lub pojedyncze projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) .

> [!WARNING] 
> CsprojToVs2017 jest narzędziem innej firmy. Nie ma gwarancji, że będzie ona działała we wszystkich projektach i może spowodować drobne zmiany w zachowaniu, od którego zależy. CsprojToVs2017 powinien być używany jako _punkt wyjścia_ , który automatyzuje podstawowe elementy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migrowania formatów plików projektu.
