### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Zdarzenie Page.LoadComplete powoduje już formant System.Web.UI.WebControls.EntityDataSource wywołać powiązanie danych

|   |   |
|---|---|
|Szczegóły|<xref:System.Web.UI.Page.LoadComplete> Zdarzeń nie powoduje, że <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> formantu można wywołać powiązania danych zmiany do tworzenia/aktualizowania/usuwania parametrów. Ta zmiana eliminuje nadmiarowe podróży do bazy danych, uniemożliwia resetowania wartości formantów i tworzy zachowanie jest zgodne z innych formantów danych, takich jak <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> i <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Ta zmiana spowoduje utworzenie inaczej, na wypadek, które aplikacje korzystają z wywołaniem powiązanie danych w <xref:System.Web.UI.Page.LoadComplete> zdarzeń.|
|Sugestia|Jeśli istnieje potrzeba dla wiązania z danymi, ręczne wywoływanie databind w przypadku starszych po tyłu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|

