---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620441"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Dostęp do wybranych elementów programu WPF DataGrid z procedury obsługi zdarzenia UnloadingRow elementu DataGrid może spowodować wystąpienie elementu NullReferenceException

#### <a name="details"></a>Szczegóły

Ze względu na usterkę w .NET Framework 4,5, obsługa zdarzeń dla <xref:System.Windows.Controls.DataGrid> zdarzeń obejmujących usunięcie wiersza może spowodować, że <xref:System.NullReferenceException?displayProperty=fullName> zostanie wygenerowany, jeśli uzyskują dostęp do <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> właściwości lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> .

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
