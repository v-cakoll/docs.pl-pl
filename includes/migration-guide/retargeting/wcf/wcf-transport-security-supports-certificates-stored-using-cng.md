### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpieczenia transportu usługi WCF obsługuje certyfikaty przechowywane przy użyciu CNG

|   |   |
|---|---|
|Szczegóły|Zabezpieczenia transportu usługi WCF, począwszy od aplikacji środowiska .NET Framework 4.6.2, obsługuje certyfikaty przechowywane przy użyciu biblioteki kryptografii Windows (CNG). Ta obsługa jest ograniczona do certyfikatów przy użyciu klucza publicznego, zawierającej wykładnika nie więcej niż 32 bity długości. Jeśli aplikacja jest przeznaczony dla .NET Framework 4.6.2, ta funkcja jest domyślnie. We wcześniejszych wersjach programu .NET Framework, próbę użycia X509 certyfikatów przy użyciu CSG zgłasza wyjątek, dostawca magazynu kluczy.|
|Sugestia|Aplikacje, które dla środowiska .NET Framework 4.6.1 i starszych, ale są uruchomione na .NET Framework 4.6.2 można włączyć obsługę certyfikatów CNG, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Można to również zrobić programowo z następującym kodem:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Należy zauważyć, że ze względu na tę zmianę, już nie wykona żadnych kodu, który zależy od próba zainicjowania komunikacji zabezpieczonej przy użyciu certyfikatów CNG, nie powiedzie się obsługi wyjątków.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Trwa przekierowywanie|

