### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpieczenia komunikatów usługi WCF jest teraz można używać TLS1.1 i TLS1.2

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.7, klienci mogą skonfigurować TLS1.1 lub TLS1.2 w ramach zabezpieczeń komunikatów usługi WCF oprócz SSL3.0 i TLS1.0 w ustawieniach konfiguracji aplikacji.|
|Sugestia|W 4.7 Framework .NET Obsługa TLS1.1 i TLS1.2 w ramach zabezpieczeń komunikatów usługi WCF jest domyślnie wyłączona. Możesz je włączyć, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowania|

