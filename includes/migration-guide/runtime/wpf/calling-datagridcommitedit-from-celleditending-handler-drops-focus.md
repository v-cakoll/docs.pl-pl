---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235728"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Wywoływanie DataGrid.CommitEdit z obsługi CellEditEnding spada koncentracji uwagi

|   |   |
|---|---|
|Szczegóły|Wywoływanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=name>firmy <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> powoduje, że procedury obsługi zdarzeń <xref:System.Windows.Controls.DataGrid?displayProperty=name> utratę fokus.|
|Sugestia|Ten błąd został naprawiony w programie .NET Framework 4.5.2, dzięki czemu można uniknąć przez uaktualnienie programu .NET Framework. Alternatywnie można należy unikać ponownie, wybierając jawnie <xref:System.Windows.Controls.DataGrid?displayProperty=name> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
