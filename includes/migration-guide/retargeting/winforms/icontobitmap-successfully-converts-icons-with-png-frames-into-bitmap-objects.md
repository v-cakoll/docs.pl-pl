### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Pomyślnie Icon.ToBitmap konwertuje ikony PNG ramek na obiekty mapy bitowej

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> — metoda konwertuje pomyślnie ikony PNG ramek na obiekty mapy bitowej. W aplikacjach przeznaczonych dla platformy .NET Framework 4.5.2 i wcześniejszych wersjach <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek, jeśli obiekt ikona ma ramki PNG. Ta zmiana wpływa na aplikacje, które są ponownie kompilowana docelową programu .NET Framework 4.6 i implementują specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> który jest zgłaszany, gdy obiekt ikona ma ramki PNG. Gdy uruchomiony w ramach programu .NET Framework 4.6, konwersja zakończy się pomyślnie, <xref:System.ArgumentOutOfRangeException> nie jest już zgłoszono i w związku z tym program obsługi wyjątku nie jest wywoływany.|
|Sugestia|Jeśli to zachowanie jest niepożądane, można zachować poprzednie, dodając następujący element do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli już zawiera plik app.config <code>AppContextSwitchOverrides</code> element, nowa wartość powinny zostać scalone z atrybutem wartości następująco:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

