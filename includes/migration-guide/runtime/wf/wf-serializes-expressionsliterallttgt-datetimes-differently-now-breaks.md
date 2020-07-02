---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620408"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>Funkcja WF serializować wyrażenia. literały &lt; T &gt; datetimes są teraz inaczej (dzieli Niestandardowe analizatory języka XAML)

#### <a name="details"></a>Szczegóły

Skojarzony <xref:System.Windows.Markup.ValueSerializer> obiekt spowoduje przekonwertowanie <xref:System.DateTime?displayProperty=fullName> obiektu lub, <xref:System.DateTimeOffset?displayProperty=fullName> którego sekunda i <xref:System.DateTime.Millisecond?displayProperty=fullName> składniki są inne niż zero i (dla <xref:System.DateTime?displayProperty=fullName> wartości), których <xref:System.DateTime.Kind> Właściwość nie została określona jako składnia elementu właściwości zamiast ciągu. Ta zmiana umożliwia <xref:System.DateTime?displayProperty=fullName> i <xref:System.DateTimeOffset?displayProperty=fullName> wartości, które mają być okrężne. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.

#### <a name="suggestion"></a>Sugestia

Ta zmiana umożliwia <xref:System.DateTime?displayProperty=fullName> i <xref:System.DateTimeOffset?displayProperty=fullName> wartości, które mają być okrężne. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
