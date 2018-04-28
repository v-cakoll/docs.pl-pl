### <a name="resizing-a-grid-can-hang"></a>Zmiana rozmiaru Siatka może zostać zawieszone.

|   |   |
|---|---|
|Szczegóły|Pętla nieskończona mogą wystąpić podczas układ <code>T:System.Windows.Controls.Grid</code> w następujących okolicznościach:<ul><li>Definicje wierszy zawierać dwa *-wiersze z obu deklarowanie MinHeight i MaxHeight.</li><li>Treść *-wierszy nie może przekraczać odpowiednich MaxHeight</li><li>Pierwszy MinHeight przekracza dostępne wysokość siatki (oraz innych stałej lub Auto wierszy)</li><li>Aplikacja jest przeznaczony dla platformy .net 4.7 lub zdecyduje się algorytm 4,7 alokacji przez ustawienie <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Pętla się również stanie z więcej niż dwa wiersze, lub w przypadku analogiczne do kolumny. Problem został rozwiązany w .net 4.7.1.|
|Sugestia|Uaktualnij platformę .net 4.7.1.  Alternatywnie Jeśli nie ma potrzeby algorytm 4,7 alokacji służy następujące ustawienia konfiguracji:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

