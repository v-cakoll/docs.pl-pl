### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>Jeśli element elemencie addressHeader ma wartość null elementu AddressHeaderCollection WCF teraz zgłasza ArgumentException

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> zgłasza konstruktora <xref:System.ArgumentException> po spełnieniu jednego z elementów <code>null</code>. W programie .NET Framework 4.7 i wcześniejszych wersjach nie jest wyjątek.|
|Sugestia|Jeśli wystąpią problemy ze zgodnością z tą zmianą na .NET Framework 4.7.1 lub nowszej wersji, użytkownik może zrezygnować z go, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|

