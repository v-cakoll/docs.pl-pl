### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm korzysta z SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 Windows Communication Foundation używa skrót SHA256 do generowania losowego nazw dla nazwanych potoków. W programie .NET Framework 4.7 i wcześniejszych wersjach on skrótu SHA1.|
|Sugestia|Jeśli napotkasz problem ze zgodnością z tej zmiany w programie .NET Framework 4.7.1 lub później, użytkownik może zrezygnować go, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|środowisko uruchomieniowe|

