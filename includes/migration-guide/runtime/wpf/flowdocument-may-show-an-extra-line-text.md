---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981688"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument mogą być wyświetlane dodatkowy wiersz tekstu

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach <xref:System.Windows.Documents.FlowDocument> elementu wyświetli dodatkowy wiersz tekstu, podczas uruchamiania na .NET Framework 4.5, w porównaniu do sposobu wyświetlania po uruchomieniu na .NET Framework 4.0. Istnieją żadne znane przypadki zmiany powodujące dowolny tekst, które mają być wyświetlane nieprawidłowo lub illegibly, ale może spowodować, że tekst wyświetlany, który wcześniej został pominięty <xref:System.Windows.Documents.FlowDocument>jego wyświetlania.|
|Sugestia|W niektórych przypadkach zmniejszając właściwość PageHeight elementu wyświetlana przez jeden można przywrócić poprzedniego liczba wierszy wyświetlanych.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|
