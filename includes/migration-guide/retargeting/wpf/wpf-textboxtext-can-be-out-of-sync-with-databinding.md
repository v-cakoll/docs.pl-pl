### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text mogą być poza synchronizacja z wiązania danych

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach <xref:System.Windows.Controls.TextBox.Text> właściwość odzwierciedla poprzedniej wartości wartości właściwości z danymi, jeśli właściwość jest modyfikowany podczas wiązania z danymi operacji zapisu.|
|Sugestia|Nie powinno to mieć żadnego negatywnego wpływu. Jednak można przywrócić poprzednie ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> właściwości <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

