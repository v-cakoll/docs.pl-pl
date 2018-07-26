### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text mogą być poza synchronizacja za powodu powiązania danych

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach <xref:System.Windows.Controls.TextBox.Text> właściwość odzwierciedla poprzednią wartość wartości właściwości z danymi, jeśli właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.|
|Sugestia|Nie powinno to mieć żadnego negatywnego wpływu. Jednakże można przywrócić poprzednie zachowanie przez ustawienie <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> właściwość <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

