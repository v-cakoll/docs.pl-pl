### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>Wartość domyślna WCF MsmqSecureHashAlgorithm jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 komunikat domyślny algorytm programu WCF dla wiadomości usługi Msmq podpisywania jest SHA256. W programie .NET Framework 4.7 i wcześniejszych wersjach komunikat domyślny algorytm podpisywania jest SHA1.|
|Sugestia|Jeśli wystąpią problemy ze zgodnością z tą zmianą w programie .NET Framework 4.7.1 lub później, użytkownik może zrezygnować zmianę, dodając następujący wiersz do <code>&lt;runtime&gt;</code>sekcji w pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|

