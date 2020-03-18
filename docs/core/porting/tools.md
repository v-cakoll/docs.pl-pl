---
title: Narzędzia do przenoszenia do .NET Core
description: Dowiedz się więcej o niektórych narzędziach, za pomocą których można przenieść się do programu .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157521"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Narzędzia pomagające przenosić kod na platformę .NET Core

Narzędzia wymienione w tym artykule mogą okazać się przydatne podczas przenoszenia:

- [Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) — pęk narzędzi, który może generować raport o tym, jak przenośny jest kod między .NET Framework i .NET Core:
  - Jako [narzędzie wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases)
  - Jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
- [Analizator interfejsu API .NET](../../standard/analyzers/api-analyzer.md) — analizator Roslyn, który wykrywa potencjalne zagrożenia ze zgodnością dla interfejsów API języka C# na różnych platformach i wykrywa wywołania przestarzałych interfejsów API.

Ponadto można próbować przenieść mniejsze rozwiązania lub poszczególne projekty do formatu pliku projektu .NET Core za pomocą narzędzia [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)

> [!WARNING]
> CsprojToVs2017 to narzędzie innej firmy. Nie ma gwarancji, że będzie działać dla wszystkich projektów i może spowodować subtelne zmiany w zachowaniu, które zależą od. CsprojToVs2017 powinien być używany jako _punkt wyjścia,_ który automatyzuje podstawowe rzeczy, które mogą być zautomatyzowane. Nie jest to gwarantowane rozwiązanie do migracji formatów plików projektu.
