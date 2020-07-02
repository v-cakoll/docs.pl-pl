---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622377"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel. BringIndexIntoView zgłasza wyjątku ArgumentOutOfRangeException

#### <a name="details"></a>Szczegóły

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>działa asynchronicznie, gdy Wirtualizacja kolumny jest włączona, ale szerokość kolumn nie została jeszcze ustalona.  Jeśli kolumny zostaną usunięte przed wykonaniem asynchronicznej pracy, <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> może wystąpić.

#### <a name="suggestion"></a>Sugestia

Jeden z następujących elementów:<ol><li>Uaktualnij do .NET Framework 4,7.</li><li>Zainstaluj najnowszą poprawkę obsługi dla .NET Framework 4.6.2.</li><li>Należy unikać usuwania kolumn do momentu ukończenia asynchronicznej odpowiedzi <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> .</li></ol>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
