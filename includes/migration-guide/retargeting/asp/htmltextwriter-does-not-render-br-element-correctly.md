---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804534"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>Nie jest renderowana HtmlTextWriter `<br/>` element poprawnie

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z <code>&lt;BR /&gt;</code> element poprawnie powoduje wstawienie tylko jednego <code>&lt;BR /&gt;</code> (zamiast dwóch)|
|Sugestia|Jeśli aplikacja była uzależniona od nadmiarowe <code>&lt;BR /&gt;</code> tagu <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinien zostać wywołany po raz drugi. Należy pamiętać, że ta zmiana zachowania ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4.6 lub nowszy, więc innym rozwiązaniem jest pod kątem poprzedniej wersji programu .NET Framework, aby pobrać stare zachowanie.|
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

