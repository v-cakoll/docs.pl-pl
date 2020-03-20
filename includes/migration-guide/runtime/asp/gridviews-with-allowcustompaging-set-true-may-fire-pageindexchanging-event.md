---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858474"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews z AllowCustomPaging ustawiony na true może odpalić PageIndexChanging zdarzenia po opuszczeniu ostatniej strony widoku

|   |   |
|---|---|
|Szczegóły|Błąd w .NET Framework 4.5 powoduje, <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> <xref:System.Web.UI.WebControls.GridView?displayProperty=name>że czasami nie <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>uruchamia się dla s, które zostały włączone .|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework. Jako obejście, aplikacja może zrobić wyraźne BindGrid <code>Page_Load</code> na każdym, który <xref:System.Web.UI.WebControls.GridView?displayProperty=name> trafi te warunki<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> (jest <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>na ostatniej stronie i Last różni się od ). Alternatywnie aplikacja może być modyfikowana, aby umożliwić stronicowanie (zamiast niestandardowego stronicowania), ponieważ ten scenariusz nie wykazuje problemu.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
