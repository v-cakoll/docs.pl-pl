---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379232"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>Przewijanie w widoku drzewa w WPF lub ListBox zgrupowane w VirtualizingStackPanel może doprowadzić do aplikacji nie odpowiada

|   |   |
|---|---|
|Szczegóły|Przewijanie WPF w programie .NET Framework 4.5 <xref:System.Windows.Controls.TreeView?displayProperty=name> w zwirtualizowanych stack panel może spowodować aplikacja przestanie odpowiadać, jeśli istnieją marginesy w okienku ekranu (między elementami w <xref:System.Windows.Controls.TreeView?displayProperty=name>, na przykład, lub w elemencie ItemsPresenter). Ponadto w niektórych przypadkach różnych wielkości elementów w widoku może spowodować niestabilność, nawet jeśli nie mają żadnych marginesy.|
|Sugestia|Po uaktualnieniu do programu .NET Framework 4.5.1 można uniknąć tego błędu. Alternatywnie marginesy można usunąć z kolekcji widoku (takich jak <xref:System.Windows.Controls.TreeView?displayProperty=name>s) w ramach zwirtualizowanych stosu paneli, jeśli wszystkie zawarte elementy mają taki sam rozmiar.|
|Scope|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
