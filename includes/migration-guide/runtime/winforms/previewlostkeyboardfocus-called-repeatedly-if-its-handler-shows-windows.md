### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus jest nazywana wielokrotnie, jeśli jego obsługa Wyświetla okno formularzy systemu Windows

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5, wywoływania <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> obsługi spowoduje ponowne uruchomienie po zamknięciu okna komunikatu może spowodować nieskończoną pętlę komunikatów programu obsługi.|
|Sugestia|Dostępne są dwie opcje w celu obejścia tego problemu:<ol><li>Można go uniknąć przez wywołanie metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Można go uniknąć przez wyświetlanie pola komunikatu z <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> obsługi zdarzeń (w przeciwieństwie do <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> obsługi zdarzeń).</li></ol>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

