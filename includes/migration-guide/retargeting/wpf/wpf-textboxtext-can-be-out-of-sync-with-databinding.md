### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Właściwość WPF TextBox.Text może być niezsynchronizowana z powodu powiązania danych

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach właściwość <xref:System.Windows.Controls.TextBox.Text> odzwierciedla poprzednią wartość właściwości związanej z danymi, jeśli ta właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.|
|Sugestia|Nie powinno to mieć żadnego negatywnego wpływu. Jednakże można przywrócić poprzednie zachowanie przez ustawienie właściwości <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

