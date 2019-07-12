---
ms.openlocfilehash: e8fcd496b9c1921753ad0e1c2632f29bc5036956
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802478"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView zgłasza trwa wyjątku ArgumentOutOfRangeException

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> będzie działać asynchronicznie, gdy włączona jest wirtualizacja kolumny, ale szerokości kolumn, które nie zostały jeszcze nieustalona.  Jeśli kolumny zostaną usunięte przed asynchronicznego praca będzie wykonywana, <xref:System.ArgumentOutOfRangeException?displayProperty=name> mogą wystąpić.|
|Sugestia|Jeden z następujących czynności:<ol><li>Uaktualnianie do programu .NET Framework 4.7.</li><li>Zainstaluj obsługi najnowszej poprawki dla programu .NET Framework 4.6.2.</li><li>Należy unikać usuwanie kolumn do czasu odpowiedzi asynchronicznych <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> zostało zakończone.</li></ol>|
|Scope|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

