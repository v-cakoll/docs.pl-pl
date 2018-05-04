### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpieczenia transportu WCF obsługuje certyfikaty przechowywane przy użyciu CNG

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji .NET Framework 4.6.2 obiektu docelowego, zabezpieczenia transportu WCF obsługuje certyfikaty przechowywane przy użyciu biblioteki Kryptografia systemu Windows (CNG). Ta obsługa jest ograniczona do certyfikatów przy użyciu klucza publicznego, który ma długość wykładnika nie więcej niż 32-bitowy. Gdy aplikacja jest przeznaczony dla programu .NET Framework 4.6.2, ta funkcja jest domyślnie. We wcześniejszych wersjach programu .NET Framework, próbę użycia X509 certyfikaty z CSG dostawcy magazynu kluczy zgłasza wyjątek.|
|Sugestia|Aplikacje, które docelowej platformy .NET Framework 4.6.1 i wcześniejszych, ale są uruchomione w programie .NET Framework 4.6.2 można włączyć obsługę certyfikatów CNG, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Można to również zrobić programowo z następującym kodem:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Należy zauważyć, że z powodu tej zmiany, Obsługa kodu, który jest zależny od próba zainicjowania komunikacji zabezpieczonej przy użyciu certyfikatu CNG niepowodzenie żadnych wyjątków nie będą wykonywane.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Przekierowania|

