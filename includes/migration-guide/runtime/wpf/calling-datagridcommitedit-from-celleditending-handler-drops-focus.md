---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803206"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Wywołanie DataGrid.CommitEdit z programu obsługi CellEditEnding spada fokus

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.DataGrid.CommitEdit> Wywołanie z <xref:System.Windows.Controls.DataGrid?displayProperty=name>jednego <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> z programów <xref:System.Windows.Controls.DataGrid?displayProperty=name> obsługi zdarzeń powoduje utratę fokusu.|
|Sugestia|Ten błąd został naprawiony w .NET Framework 4.5.2, dzięki czemu można go uniknąć, uaktualniając program .NET Framework. Alternatywnie można tego uniknąć, wyraźnie wybierając <xref:System.Windows.Controls.DataGrid?displayProperty=name> ponownie po <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>wywołaniu .|
|Zakres|Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
