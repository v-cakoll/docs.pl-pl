---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804531"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Instrukcji IL, nie są dozwolone w regionie try

|   |   |
|---|---|
|Szczegóły|W przeciwieństwie do kompilatora just-in-time JIT64 elementach RyuJIT (używane w programie .NET Framework 4.6) nie zezwala na IL ret instrukcji w regionie try. Zwracanie z regionu spróbuj jest zabroniona przez specyfikację ECMA-335, a nie znane zarządzanych kompilator generuje taki IL. Jednak kompilatora JIT64 będzie wykonywać takie IL, jeśli jest ona generowana za pomocą odbicia emisji.|
|Sugestia|Jeśli aplikacja generuje IL, która obejmuje ret opcode w regionie, spróbuj, aplikacji mogą odnosić się do programu .NET Framework 4.5 do używania starego JIT i uniknąć tego podziału. Alternatywnie wygenerowanego IL może zostać zaktualizowany do zwracania po try region.|
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|

