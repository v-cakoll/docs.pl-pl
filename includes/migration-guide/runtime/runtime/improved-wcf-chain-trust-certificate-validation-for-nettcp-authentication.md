### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Ulepszone WCF łańcuch zaufania weryfikacji certyfikatu uwierzytelniania certyfikatu usługi Net.Tcp

|   |   |
|---|---|
|Szczegóły|.NET framework 4.7.2 zwiększa łańcuch zaufania certyfikatów weryfikacji przy użyciu uwierzytelniania certyfikatu z zabezpieczeniami transportu z programem WCF. Dzięki temu usprawnieniu certyfikaty klienta, które są używane do uwierzytelniania na serwerze musi być skonfigurowana do uwierzytelniania klientów.  Podobnie certyfikaty serwera, które są w celu uwierzytelniania serwera musi być skonfigurowana do uwierzytelniania serwera. Z tą zmianą Jeśli certyfikat główny jest wyłączone, weryfikacji łańcucha certyfikatu kończy się niepowodzeniem. Te same zmiany zostało przesłane do programu .NET Framework 3.5 i nowszych wersjach za pośrednictwem zabezpieczeń systemu Windows również zbiorczy. Więcej informacji można znaleźć [tutaj](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ta zmiana jest domyślnie włączona i może być wyłączone przez ustawienia konfiguracji.|
|Sugestia|<ul><li>Sprawdź, czy Twoje certyfikacji serwera i klienta jest wymagany identyfikator OID EKU. Jeśli nie, aktualizacja Twojego certyfikacji.</li><li>Sprawdź, czy certyfikat główny jest nieprawidłowy. Jeśli tak, zaktualizuj certyfikat główny.</li><li>Jak rezygnacji z zmiany: Jeśli nie można zaktualizować certyfikat, z następującymi ustawieniami konfiguracji można obejść istotne zmiany tymczasowo, jednak Rezygnacja z zmiany system pozostanie narażone na problem z zabezpieczeniami.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|

