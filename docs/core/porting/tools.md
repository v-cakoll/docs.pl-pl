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
# <a name="tools-to-help-with-porting-to-net-core"></a>Narzędzia ułatwiające wykonywanie eksportowanie do programu .NET Core

Narzędzia wymienione w tym artykule, które są przydatne podczas przenoszenia może się okazać:

* [Narzędzia .NET portability Analyzer](../../standard/analyzers/portability-analyzer.md), łańcuch narzędzi, który można wygenerować raportu dotyczącego sposobu przenośny kod jest między .NET Framework i .NET Core:  Jako [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) jako [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)
* [Analizator interfejsu API platformy .NET](../../standard/analyzers/api-analyzer.md) -analizatora Roslyn, który umożliwia odnalezienie potencjalnych problemów zagrożenie dla C# interfejsów API na różnych platformach i wykrywa wywołania interfejsów API przestarzałych.

Ponadto, możesz spróbować rozwiązań mniejszych portu lub poszczególnych projektów do formatu pliku projektu .NET Core za pomocą [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) narzędzia.

> [!WARNING] 
> CsprojToVs2017 to narzędzia innych firm. Nie ma żadnej gwarancji, która będzie działać w przypadku wszystkich swoich projektach i może spowodować, że wprowadzono subtelne zmiany w zachowaniu, który, na których polegasz. CsprojToVs2017 powinien być używany jako _punkt początkowy_ który automatyzuje podstawowe czynności, które można zautomatyzować. Nie jest gwarantowana rozwiązania do migrowania formatów plików projektu.
