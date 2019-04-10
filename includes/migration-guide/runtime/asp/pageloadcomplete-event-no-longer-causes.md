---
ms.openlocfilehash: 02a3c1b5a9693535feeab56d9b0f7c9d360749ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235731"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Zdarzenie Page.LoadComplete nie powoduje już kontroli System.Web.UI.WebControls.EntityDataSource wywołania wiązania danych

|   |   |
|---|---|
|Szczegóły|<xref:System.Web.UI.Page.LoadComplete> Zdarzeń nie powoduje już <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> kontroli wywołania wiązania danych w celu utworzenia/zaktualizowania/usunięcia parametrów. Tej zmiany eliminuje do bazy danych, zapobiega resetowaniu wartości formantów oraz tworzy zachowanie zgodne z innymi formantami danych, takich jak <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> i <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Ta zmiana powoduje różne zachowanie w mało prawdopodobnym przypadku, w którym aplikacje polegają na wywoływaniu powiązań danych w <xref:System.Web.UI.Page.LoadComplete> zdarzeń.|
|Sugestia|W przypadku potrzeby wiązania danych ręcznie wywołać powiązań danych w starszej w tle po zdarzeniu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
