### <a name="certificate-eku-oid-validation"></a>Sprawdzanie poprawności identyfikator OID EKU certyfikatu

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6 <xref:System.Net.Security.SslStream> lub <xref:System.Net.ServicePointManager> klasy sprawdzania poprawności identyfikator (OID) obiektu rozszerzone użycie klucza (EKU). Rozszerzenie rozszerzone użycie klucza (EKU) jest zbiorem identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza. Identyfikator OID EKU weryfikacji używa certyfikatu zdalnego wywołania zwrotne aby upewnić się, że zdalny certyfikat ma prawidłowe identyfikatory OID do zamierzonego celu.|
|Sugestia|Jeśli ta zmiana jest niepożądane, można wyłączyć sprawdzania poprawności identyfikator OID EKU certyfikatu, dodając następujące przełączyć się do [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) z sieci plik konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] To ustawienie jest dostępne tylko w przypadku zgodności z poprzednimi wersjami. W przeciwnym razie jego użycie nie jest zalecane.</blockquote> |
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

