---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235545"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Uzyskiwanie dostępu do elementu DataGrid WPF wybrane elementy z programu obsługi zdarzeń UnloadingRow w elemencie DataGrid mogą powodować obiektu NullReferenceException

|   |   |
|---|---|
|Szczegóły|Z powodu błędów w programie .NET Framework 4.5, programy obsługi zdarzeń dla <xref:System.Windows.Controls.DataGrid> wydarzenia związane z usunięcie wiersza może spowodować, że <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany, jeśli uzyskują oni dostęp do <xref:System.Windows.Controls.DataGrid>firmy <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> właściwości.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
