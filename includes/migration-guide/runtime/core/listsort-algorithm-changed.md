---
ms.openlocfilehash: d4859629fe3922b71cc90664e1e3304cdb312bae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235598"
---
### <a name="listsort-algorithm-changed"></a>Algorytm List.Sort zmienione

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=name>firmy algorytmu sortowania został zmieniony (jako sortowania zamiast sortowania szybkie). <xref:System.Collections.Generic.List%601?displayProperty=name>firmy nigdy nie było stabilne sortowanie, ale ta zmiana może spowodować, że różne scenariusze sortowania w sposób niestabilny. To po prostu oznacza, że elementy równoważne mogą sortować w różnych zleceniach w kolejnych wywołaniach interfejsu API.|
|Sugestia|Ponieważ starego algorytmu sortowania została również niestabilne (chociaż są w nieco inny sposób), powinna to być żaden kod, który zależy od elementów równoważnych zawsze sortowanie w określonej kolejności. W przypadku wystąpienia elementu kodu, zależności i być się przy użyciu starego zachowania tego kod powinien zostać zaktualizowany w taki sposób, aby użyć modułu porównującego, który będzie sposób deterministyczny sortowanie elementów w odpowiedni sposób.|
|Zakres|Przezroczyste|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
