---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804692"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Instrukcji IL, nie są dozwolone w regionie try

|   |   |
|---|---|
|Szczegóły|W przeciwieństwie do kompilatora just-in-time JIT64 elementach RyuJIT (używane w programie .NET Framework 4.6) nie zezwala na IL ret instrukcji w regionie try. Zwracanie z regionu spróbuj jest zabroniona przez specyfikację ECMA-335, a nie znane zarządzanych kompilator generuje taki IL. Jednak kompilatora JIT64 będzie wykonywać takie IL, jeśli jest ona generowana za pomocą odbicia emisji.|
|Sugestia|Jeśli aplikacja generuje IL, która obejmuje ret opcode w regionie, spróbuj, aplikacji mogą odnosić się do programu .NET Framework 4.5 do używania starego JIT i uniknąć tego podziału. Alternatywnie wygenerowanego IL może zostać zaktualizowany do zwracania po try region.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|
