---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858499"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Uzyskiwanie dostępu do wybranych elementów WPF DataGrid z obsługi zdarzenia DataGrid's UnloadingRow może spowodować nullReferenceException

|   |   |
|---|---|
|Szczegóły|Z powodu błędu w programie .NET Framework 4.5 programy obsługi zdarzeń dla <xref:System.Windows.Controls.DataGrid> zdarzeń <xref:System.NullReferenceException?displayProperty=name> obejmujących usunięcie wiersza może spowodować, że mają zostać odrzucone, jeśli uzyskują dostęp do <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> właściwości.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
