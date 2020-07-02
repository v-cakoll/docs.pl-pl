---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615646"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nie renderuje `<br/>` poprawnie elementu

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z `<BR />` elementem spowoduje poprawne wstawienie tylko jednego `<BR />` (zamiast dwóch)

#### <a name="suggestion"></a>Sugestia

Jeśli aplikacja zależała od dodatkowych `<BR />` tagów, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> należy wywołać ją drugi raz. Należy zauważyć, że to zachowanie ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4,6 lub nowszej, więc kolejną opcją jest docelowa Poprzednia wersja .NET Framework w celu uzyskania starego zachowania.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
