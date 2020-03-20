---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802478"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView rzuca ArgumentOutOfRangeException

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>będzie działać asynchronicznie, gdy wirtualizacja kolumn jest włączona, ale szerokości kolumn nie zostały jeszcze określone.  Jeśli kolumny są usuwane przed wykonaniem pracy <xref:System.ArgumentOutOfRangeException?displayProperty=name> asynchronicznej, może wystąpić wystąpienie.|
|Sugestia|Dowolna z następujących czynności:<ol><li>Uaktualnienie do programu .NET Framework 4.7.</li><li>Zainstaluj najnowszą poprawkę obsługi dla platformy .NET Framework 4.6.2.</li><li>Należy unikać usuwania kolumn, dopóki odpowiedź <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> asynchroniza do została zakończona.</li></ol>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
