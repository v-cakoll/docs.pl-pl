### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>SignedXml.GetPublicKey zwraca RSACng na net462 (lub lightup) bez zmiany retargetingu

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, konkretnego typu obiektu zwróconego przez <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> zmienić metody (bez niedoskonałość) z implementacji CryptoServiceProvider implementacji Cng. Jest to spowodowane implementacji zmieniła się z pomocą <code>certificate.PublicKey.Key</code> przy użyciu wewnętrznej <code>certificate.GetAnyPublicKey</code> który przekazuje do <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.|
|Sugestia|Począwszy od aplikacji działających w programie .NET Framework 4.7.1, można użyć implementacji CryptoServiceProvider używany domyślnie w programie .NET Framework 4.6.1 i starszych wersjach, dodając następującej konfiguracji przejdź do [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcji w pliku konfiguracyjnym aplikacji:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|

