### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Domyślny algorytm wyznaczania wartości skrótu dla WPF PackageDigitalSignatureManager jest teraz SHA256

|   |   |
|---|---|
|Szczegóły|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> Udostępnia funkcje w podpisach cyfrowych w odniesieniu do pakietów WPF.  W programie .NET Framework 4.7 i wcześniejszych wersjach, domyślny algorytm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) używany do podpisywania części pakietu zostało SHA1.  Ze względów bezpieczeństwa ostatnie z SHA1, SHA256 została zmieniona to ustawienie domyślne w programie .NET Framework 4.7.1.  Ta zmiana wpływa na wszystkich pakietów podpisywania, tym dokumenty XPS.|
|Sugestia|Deweloper, który chce korzystać z tej zmiany podczas określania wartości docelowej wersji struktury poniżej .NET Framework 4.7.1 lub dewelopera, który wymaga poprzednie funkcjonalności, podczas gdy przeznaczonych dla platformy .NET Framework 4.7.1 lub większa można ustawić następujące flagi AppContext odpowiednio.  Wartość true spowoduje SHA1 używany jako domyślny algorytm; FALSE powoduje SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

