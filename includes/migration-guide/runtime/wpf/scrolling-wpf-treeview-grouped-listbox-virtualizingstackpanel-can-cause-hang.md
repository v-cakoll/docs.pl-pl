### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Przewijanie WPF TreeView lub ListBox zgrupowane w VirtualizingStackPanel może spowodować zawieszenie

|   |   |
|---|---|
|Szczegóły|W wersji .NET Framework 4.5 przewijanie WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> w stosie zwirtualizowanych panelu może spowodować zawiesza się, jeśli istnieją marginesy w okienka ekranu (między elementami w <xref:System.Windows.Controls.TreeView?displayProperty=name>, na przykład lub w elemencie ItemsPresenter). Ponadto w niektórych przypadkach różne elementy o rozmiarze w widoku może spowodować niestabilność, nawet jeśli nie mają żadnych marginesów.|
|Sugestia|Tego błędu można uniknąć przez uaktualnienie do systemu .NET Framework 4.5.1. Alternatywnie marginesy można usunąć z kolekcji widoku (takich jak <xref:System.Windows.Controls.TreeView?displayProperty=name>s) w zwirtualizowanych stosu panele, jeśli wszystkie elementy mają taki sam rozmiar.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|

