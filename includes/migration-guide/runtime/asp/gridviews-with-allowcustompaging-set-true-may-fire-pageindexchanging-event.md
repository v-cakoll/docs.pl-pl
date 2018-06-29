### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews z Wartość AllowCustomPaging o wartości true może wyzwalać zdarzeń PageIndexChanging podczas opuszczania ostatnia strona widoku

|   |   |
|---|---|
|Szczegóły|Powoduje usterki w programie .NET Framework 4.5 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> czasami nie uruchomienie dla <xref:System.Web.UI.WebControls.GridView?displayProperty=name>, które mają włączone <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework. Jako obejście, aplikację można wykonać jawne BindGrid na dowolnym <code>Page_Load</code> który czy trafień tych warunków ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> jest na ostatniej stronie i ostatnich<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> różni się od <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatywnie aplikacji można zmodyfikować umożliwia stronicowania (zamiast stronicowania niestandardowego), w tym scenariuszu nie przedstawiać problemu.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

