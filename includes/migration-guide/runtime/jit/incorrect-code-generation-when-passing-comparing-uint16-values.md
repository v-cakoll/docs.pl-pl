---
ms.openlocfilehash: b23909c53b451b4b18bf0ccdf59f51e7c8e3114f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802449"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Generowanie kodu niepoprawny podczas przekazywanie i porównywanie wartości UInt16

|   |   |
|---|---|
|Szczegóły|Z powodu zmian wprowadzonych w programie .NET Framework 4.7, w niektórych przypadkach kod wygenerowany przez kompilator JIT w aplikacje działające na .NET Framework 4.7 niepoprawnie porównuje dwa <code>T:System.UInt16</code> wartości. Aby uzyskać więcej informacji, zobacz [11508 # problemu: Ciche Generowanie nieprawidłowego kodu podczas przekazywanie i porównywanie ushort args](https://github.com/dotnet/coreclr/issues/11508) w witrynie GitHub.com.|
|Sugestia|Jeśli wystąpią problemy w porównaniu z 16-bitowych wartości bez znaku w programie .NET Framework 4.7, uaktualnienie do programu .NET Framework 4.7.1.|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

