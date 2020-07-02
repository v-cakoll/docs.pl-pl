---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620248"
---
### <a name="listsort-algorithm-changed"></a>Zmieniono algorytm list. Sort

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, <xref:System.Collections.Generic.List%601?displayProperty=fullName> algorytm sortowania został zmieniony (algorytmu sortowanie zamiast szybkiego sortowania). <xref:System.Collections.Generic.List%601?displayProperty=fullName>sortowanie nigdy nie było stabilne, ale ta zmiana może spowodować, że inne scenariusze będą sortowane w niestabilny sposób. Oznacza to po prostu, że równoważne elementy mogą sortować w różnych zamówieniach w kolejnych wywołaniach interfejsu API.

#### <a name="suggestion"></a>Sugestia

Ponieważ stary algorytm sortowania był również niestabilny (choć nieco inaczej), nie powinien być kod, który zależy od elementów równoważnych zawsze sortowanych w określonej kolejności. Jeśli istnieją wystąpienia kodu, w zależności od tego i są cieszymy ze starym zachowaniem, kod ten należy zaktualizować, aby użyć funkcji porównującej, która będzie w sposób jednoznaczny sortować elementy w żądanej kolejności.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Przezroczyste|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
