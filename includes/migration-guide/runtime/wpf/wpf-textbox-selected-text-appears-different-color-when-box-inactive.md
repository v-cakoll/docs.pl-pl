### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Pole tekstowe WPF wybrany tekst jest wyświetlany inny kolor, gdy pole tekstowe jest nieaktywny

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5, gdy formant pola tekstowego WPF jest nieaktywny (nie ma fokusu), pojawi się zaznaczony tekst wewnątrz pola innym kolorze niż gdy formant jest aktywny.|
|Sugestia|Poprzednie zachowanie (.NET Framework 4.0) mogą zostać przywrócone przez ustawienie <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwości <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

