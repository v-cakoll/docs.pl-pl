---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620137"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>Widok GridView z AllowCustomPaging ustawioną na wartość true może spowodować uruchomienie zdarzenia PageIndexChanging przy opuszczaniu końcowej strony widoku

#### <a name="details"></a>Szczegóły

Usterka w .NET Framework 4,5 powoduje <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> , że czasami nie jest uruchamiane dla <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> s, które zostały włączone <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework. Jako obejście, aplikacja może wykonać jawną BindGrid na dowolnym <code>Page_Load</code> , który mógłby trafić w te warunki ( <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> znajduje się na ostatniej stronie, a Ostatnia <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> jest inna niż <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ). Alternatywnie można zmodyfikować aplikację w taki sposób, aby zezwalała na stronicowanie (zamiast niestandardowego stronicowania), ponieważ ten scenariusz nie pokazuje problemu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
