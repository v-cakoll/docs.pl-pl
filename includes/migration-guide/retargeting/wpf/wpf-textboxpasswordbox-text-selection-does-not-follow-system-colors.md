### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Zaznaczenie tekstu pole tekstowe/PasswordBox WPF nie jest zgodna z kolorów systemu

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.7.1 i wcześniejszych wersjach, WPF <code>System.Windows.Controls.TextBox</code> i <code>System.Windows.Controls.PasswordBox</code> może renderować obraz tylko w warstwie modułu definiowania układu kodu zaznaczonego tekstu. W niektórych kompozycji systemu, to czy occlude tekstu, dzięki czemu trudny do odczytania.  W programie .NET Framework 4.7.2 i nowszym, deweloperzy mają opcję włączania schemat renderowania wybór oparty moduł definiowania układu kodu, który pozwala uniknąć tego problemu.|
|Sugestia|Deweloper, który chce korzystać z tej zmiany należy odpowiednio ustawione następujące flagi AppContext.  Aby korzystać z tej funkcji, zainstalowanej wersji .NET Framework musi być 4.7.2 lub nowszej. Włączone wybór oparty moduł definiowania układu kodu, użyj następujących flagi AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Przekierowania|

