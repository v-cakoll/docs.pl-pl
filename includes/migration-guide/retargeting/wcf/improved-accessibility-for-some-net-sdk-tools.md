### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Ulepszone ułatwień dostępu dla niektórych narzędzi zestawu .NET SDK

|   |   |
|---|---|
|Szczegóły|W zestawie SDK 4.7.1 Framework .NET ulepszono narzędzia SvcConfigEditor.exe i SvcTraceViewer.exe napraw problemy z dostępem zróżnicowane. Większość tych były niewielkie problemy, jak nazwa nie jest zdefiniowany lub niektórych wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie. Gdy wielu użytkowników nie byłoby znać te nieprawidłowe wartości, klienci korzystający z ułatwieniami technologii, takich jak czytniki znajdzie te narzędzia zestawu SDK dostęp. Oczywiście te poprawki zmienić niektóre zachowania poprzedniej, takich jak kolejność fokus klawiatury. Aby pobrać wszystkie, dostępność naprawia w tych narzędzi, można następujące do pliku app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|Przekierowania|

