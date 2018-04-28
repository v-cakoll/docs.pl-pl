### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException w kodu z ImageSourceConverter.ConvertFrom obsługi wyjątków

|   |   |
|---|---|
|Szczegóły|Wystąpił błąd w kodu dla obsługi wyjątków <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> spowodowane przez niepoprawny <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany zamiast zamierzone wyjątek (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> lub <xref:System.IO.FileNotFoundException?displayProperty=name>). Ta zmiana poprawia tego błędu, aby metoda teraz zgłasza wyjątek prawo. Dzięki domyślne wszystkich aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 i poniżej będzie zgłaszać <xref:System.NullReferenceException?displayProperty=name> dla deweloperów korzystających z platformy .NET Framework 4.7 zachowania zgodności i powyżej powinna zostać wyświetlona prawo wyjątków.|
|Sugestia|Deweloperów, którzy chcą, aby powrócić do pobierania <xref:System.NullReferenceException?displayProperty=name> po przeznaczonych dla platformy .NET Framework 4.7 bądź nowsza można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

