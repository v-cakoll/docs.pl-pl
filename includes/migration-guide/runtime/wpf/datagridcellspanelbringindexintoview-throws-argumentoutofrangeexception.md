---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665225"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView zgłasza trwa wyjątku ArgumentOutOfRangeException

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> będzie działać asynchronicznie, gdy włączona jest wirtualizacja kolumny, ale szerokości kolumn, które nie zostały jeszcze nieustalona.  Jeśli kolumny zostaną usunięte przed asynchronicznego praca będzie wykonywana, <xref:System.ArgumentOutOfRangeException?displayProperty=name> mogą wystąpić.|
|Sugestia|Jeden z następujących czynności:<ol><li>Uaktualnianie do programu .NET Framework 4.7.</li><li>Zainstaluj obsługi najnowszej poprawki dla programu .NET Framework 4.6.2.</li><li>Należy unikać usuwanie kolumn do czasu odpowiedzi asynchronicznych <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> zostało zakończone.</li></ol>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
