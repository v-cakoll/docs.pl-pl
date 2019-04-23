---
ms.openlocfilehash: 0887379fb23e9e66c6cc55a3774545162634c3f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804694"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Przewijanie w widoku drzewa w WPF lub ListBox zgrupowane w VirtualizingStackPanel może spowodować zawieszenie

|   |   |
|---|---|
|Szczegóły|W wersji w .NET Framework 4.5., przewijania WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> w zwirtualizowanych stack panel może spowodować zawiesza się, w przypadku marginesów w okienku ekranu (między elementami w <xref:System.Windows.Controls.TreeView?displayProperty=name>, na przykład, lub w elemencie ItemsPresenter). Ponadto w niektórych przypadkach różnych wielkości elementów w widoku może spowodować niestabilność, nawet jeśli nie mają żadnych marginesy.|
|Sugestia|Po uaktualnieniu do programu .NET Framework 4.5.1 można uniknąć tego błędu. Alternatywnie marginesy można usunąć z kolekcji widoku (takich jak <xref:System.Windows.Controls.TreeView?displayProperty=name>s) w ramach zwirtualizowanych stosu paneli, jeśli wszystkie zawarte elementy mają taki sam rozmiar.|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
