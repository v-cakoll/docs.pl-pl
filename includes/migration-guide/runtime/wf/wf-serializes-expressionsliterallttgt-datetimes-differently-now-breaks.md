---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379641"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal\<T > Data/Godzina inaczej, teraz (przerywa niestandardowe analizatory XAML)

|   |   |
|---|---|
|Szczegóły|Skojarzone <xref:System.Windows.Markup.ValueSerializer> przekonwertuje obiekt <xref:System.DateTime?displayProperty=name> lub <xref:System.DateTimeOffset?displayProperty=name> obiektu, którego drugi i <xref:System.DateTime.Millisecond?displayProperty=name> składników jest różna od zera i (dla <xref:System.DateTime?displayProperty=name> wartość) którego <xref:System.DateTime.Kind> właściwość nie jest nieokreślona do elementu właściwości Składnia zamiast ciągu. Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Sugestia|Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
