---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804675"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal\<T > Data/Godzina inaczej, teraz (przerywa niestandardowe analizatory XAML)

|   |   |
|---|---|
|Szczegóły|Skojarzone <xref:System.Windows.Markup.ValueSerializer> przekonwertuje obiekt <xref:System.DateTime?displayProperty=name> lub <xref:System.DateTimeOffset?displayProperty=name> obiektu, którego drugi i <xref:System.DateTime.Millisecond?displayProperty=name> składników jest różna od zera i (dla <xref:System.DateTime?displayProperty=name> wartość) którego <xref:System.DateTime.Kind> właściwość nie jest nieokreślona do elementu właściwości Składnia zamiast ciągu. Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Sugestia|Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
