---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804762"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>Nie jest renderowana HtmlTextWriter `<br/>` element poprawnie

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z <code>&lt;BR /&gt;</code> element poprawnie powoduje wstawienie tylko jednego <code>&lt;BR /&gt;</code> (zamiast dwóch)|
|Sugestia|Jeśli aplikacja była uzależniona od nadmiarowe <code>&lt;BR /&gt;</code> tagu <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinien zostać wywołany po raz drugi. Należy pamiętać, że ta zmiana zachowania ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4.6 lub nowszy, więc innym rozwiązaniem jest pod kątem poprzedniej wersji programu .NET Framework, aby pobrać stare zachowanie.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
