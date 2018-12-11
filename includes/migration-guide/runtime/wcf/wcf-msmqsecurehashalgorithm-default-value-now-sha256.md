### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>Wartość domyślna WCF MsmqSecureHashAlgorithm jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1 komunikat domyślny algorytm programu WCF dla wiadomości usługi Msmq podpisywania jest algorytm SHA256. W .NET Framework 4.7 i wcześniejszych wersjach komunikat domyślny algorytm podpisywania jest algorytm SHA1.|
|Sugestia|Jeśli napotkasz problemy ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub nowszej, użytkownik może zrezygnować zmiany, dodając następujący wiersz do <code>&lt;runtime&gt;</code>sekcji w pliku app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|

