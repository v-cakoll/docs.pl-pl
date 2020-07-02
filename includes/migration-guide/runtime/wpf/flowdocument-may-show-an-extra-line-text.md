---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620430"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument może wyświetlić dodatkowy wiersz tekstu

#### <a name="details"></a>Szczegóły

W niektórych przypadkach <xref:System.Windows.Documents.FlowDocument> element będzie wyświetlał dodatkowy wiersz tekstu podczas uruchamiania na .NET Framework 4,5 w porównaniu do sposobu, w jaki jest wyświetlany, gdy jest uruchamiany na .NET Framework 4,0. Nie istnieją znane przypadki zmiany, które powodują słabą i nieillegibly tekstu, ale może to spowodować, że tekst jest wyświetlany wcześniej z <xref:System.Windows.Documents.FlowDocument> widoku.

#### <a name="suggestion"></a>Sugestia

W niektórych przypadkach zmniejszenie właściwości PageHeight elementu wyświetlanego przez jedną może przywrócić poprzednią liczbę wyświetlanych wierszy.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
