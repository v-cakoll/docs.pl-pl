---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236596"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Generowanie kodu niepoprawny podczas przekazywanie i porównywanie wartości UInt16

|   |   |
|---|---|
|Szczegóły|Z powodu zmian wprowadzonych w programie .NET Framework 4.7, w niektórych przypadkach kod wygenerowany przez kompilator JIT w aplikacje działające na .NET Framework 4.7 niepoprawnie porównuje dwa <code>T:System.UInt16</code> wartości. Aby uzyskać więcej informacji, zobacz [11508 # problemu: Ciche Generowanie nieprawidłowego kodu podczas przekazywanie i porównywanie ushort args](https://github.com/dotnet/coreclr/issues/11508) w witrynie GitHub.com.|
|Sugestia|Jeśli wystąpią problemy w porównaniu z 16-bitowych wartości bez znaku w programie .NET Framework 4.7, uaktualnienie do programu .NET Framework 4.7.1.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
