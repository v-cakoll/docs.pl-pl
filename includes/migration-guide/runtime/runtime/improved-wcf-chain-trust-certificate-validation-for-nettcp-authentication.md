### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Ulepszone WCF łańcuch zaufania weryfikację certyfikatu do uwierzytelniania certyfikatów Net.Tcp

|   |   |
|---|---|
|Szczegóły|.NET framework 4.7.2 zwiększa łańcuchu zaufania certyfikatu weryfikacji przy użyciu uwierzytelniania certyfikatów zabezpieczeń transportu za pomocą programu WCF. Dzięki temu usprawnieniu certyfikaty klienta, które są używane do uwierzytelniania na serwerze musi być skonfigurowany do uwierzytelniania klientów.  Podobnie certyfikaty serwera, które służą do uwierzytelniania serwera musi być skonfigurowany do uwierzytelniania serwera. Dzięki tej zmianie Jeśli certyfikat główny jest wyłączona, weryfikacji łańcucha certyfikatu kończy się niepowodzeniem. Tym samym również zmiany w .NET Framework 3.5 i nowsze wersje za pośrednictwem zabezpieczeń Windows zbiorczy. Więcej informacji można znaleźć [tutaj](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ta zmiana jest domyślnie włączona i może być wyłączone przez ustawienia konfiguracji.|
|Sugestia|<ul><li>Sprawdź, czy certyfikat serwera i klienta jest wymagany identyfikator obiektu rozszerzenia EKU. Jeśli nie, zaktualizuj certyfikat.</li><li>Sprawdź, czy certyfikat główny jest nieprawidłowy. Jeśli tak, zaktualizuj certyfikat główny.</li><li>Jak zrezygnować z zmiany: Jeśli nie można zaktualizować certyfikat, można obejść tymczasowo istotną zmianę, za pomocą następujących ustawień konfiguracji, jednak Rezygnacja z zmiany spowoduje, że system narażone na problem z zabezpieczeniami.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|

