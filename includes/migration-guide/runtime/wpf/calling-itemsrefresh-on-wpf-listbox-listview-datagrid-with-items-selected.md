---
ms.openlocfilehash: a14395895c6be586c862d1b49aa6bf6669e4203a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238037"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Wywołanie Items.Refresh na WPF ListBox, ListView lub DataGrid z zaznaczonych elementów może spowodować zduplikowane elementy pojawiają się w elemencie

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5 wywołanie ListBox.Items.Refresh z kodu, gdy elementy są zaznaczone w <xref:System.Windows.Controls.ListBox?displayProperty=name> może spowodować, że wybrane elementy mają być duplikowane na liście. Podobny problem występuje <xref:System.Windows.Controls.ListView?displayProperty=name> <xref:System.Windows.Controls.DataGrid?displayProperty=name>z i . Jest to ustalone w .NET Framework 4.6.|
|Sugestia|Ten problem może być obejść przez programowo unselecting elementów przed <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> wywołano, a następnie ponowne wybranie ich po zakończeniu połączenia. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
