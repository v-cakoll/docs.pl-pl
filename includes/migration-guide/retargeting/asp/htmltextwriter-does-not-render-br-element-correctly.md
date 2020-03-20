---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804534"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nie `<br/>` renderuje elementu poprawnie

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> wywołanie i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> <code>&lt;BR /&gt;</code> element poprawnie wstawić tylko jeden <code>&lt;BR /&gt;</code> (zamiast dwóch)|
|Sugestia|Jeśli aplikacja zależała od <code>&lt;BR /&gt;</code> dodatkowego tagu, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinna zostać wywołana po raz drugi. Należy zauważyć, że ta zmiana zachowania dotyczy tylko aplikacji, które są przeznaczone dla programu .NET Framework 4.6 lub nowszego, więc inną opcją jest kierowanie poprzedniej wersji programu .NET Framework w celu uzyskania starego zachowania.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
