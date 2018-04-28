### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged zdarzeń i właściwości SelectedContent

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7.1, <xref:System.Windows.Controls.TabControl> aktualizuje wartość jego <xref:System.Windows.Controls.TabControl.SelectedContent> właściwości przed zgłoszeniem <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzeń, gdy jego zaznaczenie zostanie zmienione. W programie .NET Framework 4.7 i wcześniejszych wersjach aktualizacja do SelectedContent się stało po zdarzeniu.|
|Sugestia|Aplikacje dla środowiska .NET Framework 4.7.1 lub nowszym można zrezygnować z tego zmienić i zachowanie starszej wersji, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> sekcji pliku konfiguracji aplikacji:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacji przeznaczonych dla platformy .NET Framework 4.7 lub wcześniej, ale są uruchomione w programie .NET Framework 4.7.1 lub nowszym można włączyć nowe zachowanie, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku .configuration aplikacji:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

