### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>Nie jest renderowana HtmlTextWriter `<br/>` element poprawnie

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6, wywoływania <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z <code>&lt;BR /&gt;</code> element poprawnie powoduje wstawienie tylko jeden <code>&lt;BR /&gt;</code> (zamiast dwóch)|
|Sugestia|Jeśli aplikacja była uzależniona od nadmiarowe <code>&lt;BR /&gt;</code> tagu <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinna być wywoływana po raz drugi. Należy pamiętać, że ta zmiana zachowania wpływa tylko na aplikacje, które dla środowiska .NET Framework 4.6 lub nowszy, więc inną opcją jest pod kątem poprzedniej wersji programu .NET Framework, aby pobrać stare zachowanie.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

