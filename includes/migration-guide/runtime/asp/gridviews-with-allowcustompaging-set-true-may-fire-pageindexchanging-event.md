---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804707"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews z o wartości true Wartość AllowCustomPaging może wyzwalać zdarzenia PageIndexChanging podczas opuszczania ostatnią stronę widoku

|   |   |
|---|---|
|Szczegóły|Powoduje to błąd w .NET Framework 4.5 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> czasami nie ognia dla <xref:System.Web.UI.WebControls.GridView?displayProperty=name>s, które mają włączone <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework. Jako obejście, aplikacja nie dysponuje jawne BindGrid na dowolnym <code>Page_Load</code> , osiągnie tych warunków ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> jest na ostatniej stronie, a ostatni<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> różni się od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatywnie aplikacji można zmodyfikować umożliwia stronicowania (zamiast stronicowanie niestandardowych), ten scenariusz nie przedstawiono tu problem.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
