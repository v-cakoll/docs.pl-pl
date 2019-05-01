---
ms.openlocfilehash: de73145273ad5aa5c19de55525417cfc3305b86d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091688"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Items.Refresh wywoływania na WPF ListBox, ListView lub DataGrid z elementami zaznaczonymi może spowodować zduplikowane elementy pojawią się w elemencie

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5, wywoływanie ListBox.Items.Refresh z kodu, podczas gdy elementy są zaznaczone w <xref:System.Windows.Controls.ListBox?displayProperty=name> może spowodować, że wybrane elementy zostać zduplikowane na liście. Podobny problem występuje w przypadku <xref:System.Windows.Controls.ListView?displayProperty=name> i <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Problem ten został rozwiązany w .NET Framework 4.6.|
|Sugestia|Ten problem może pracować wokół programowo cofając elementów przed <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> nosi nazwę, a następnie ponownie wybierając je, po zakończeniu wywołanie. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
