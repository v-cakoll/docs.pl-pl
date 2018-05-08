### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Element przewijania płaska lista z elementami różnych wysokość pikseli

|   |   |
|---|---|
|Szczegóły|Gdy <xref:System.Windows.Controls.ItemsControl?displayProperty=name> Wyświetla kolekcję przy użyciu wirtualizacji (<code>IsVirtualizing=true</code>) i element przewijania (<code>ScrollUnit=Item</code>), i gdy przewinie formant do wyświetlania elementu, którego wysokość w pikselach różni się od jej sąsiadami <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> przechodzi przez wszystkie elementy w kolekcji. Interfejs użytkownika nie odpowiada podczas tej iteracji; Jeśli kolekcja jest duży, może to być traktowany jako zawieszenie. Występuje iteracji w innych warunkach, nawet w poprzednich wersjach systemu .NET Framework. Na przykład występuje podczas przewijania pikseli (<code>ScrollUnit=Pixel</code>) przypadku napotkania elementu o różnych pikseli wysokości i podczas przewijania elementu hierarchiczne dane (takie jak <xref:System.Windows.Controls.TreeView?displayProperty=name> lub <xref:System.Windows.Controls.ItemsControl?displayProperty=name> grupowanie włączone) przypadku napotkania elementu inną liczbę elementów podrzędnych, niż jej sąsiadami. W przypadku wysokość pikseli przewijanie elementu i różni się iteracji została wprowadzona w programie .NET Framework 4.6.1, aby naprawić błędy w układzie hierarchiczne dane.  Jeśli dane są płaskie (nie hierarchii) i .NET Framework 4.6.2 nie działa on w takim przypadku nie jest wymagana.|
|Sugestia|W przypadku iteracji w programie .NET Framework 4.6.1, ale nie w starszych wersjach — to znaczy, jeśli <xref:System.Windows.Controls.ItemsControl?displayProperty=name> jest element-przewijanie płaska lista z elementami wysokość różne pikseli - istnieją dwa środki zaradcze:<ol><li>Zainstaluj program .NET Framework 4.6.2.</li><li>Zainstaluj poprawkę HR 1605 dla programu .NET Framework 4.6.1.</li></ol>|
|Zakres|Pomocnicza|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

