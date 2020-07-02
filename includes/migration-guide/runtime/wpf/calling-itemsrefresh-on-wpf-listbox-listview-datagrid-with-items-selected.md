---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620418"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Wywoływanie elementów. Refresh na liście rozwijanej WPF, ListView lub DataGrid z zaznaczonymi elementami może spowodować, że zduplikowane elementy będą widoczne w elemencie

#### <a name="details"></a>Szczegóły

W .NET Framework 4,5, wywołujący element ListBox. Items. Refresh z kodu, podczas gdy elementy są wybrane w, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> mogą spowodować duplikowanie wybranych elementów na liście. Podobny problem występuje w systemie <xref:System.Windows.Controls.ListView?displayProperty=fullName> i <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> . Ten problem został rozwiązany w .NET Framework 4,6.

#### <a name="suggestion"></a>Sugestia

Problem ten może obejść przez programowe usunięcie zaznaczenia elementów przed wywołaniem <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> , a następnie ponowne wybranie ich po zakończeniu wywołania. Alternatywnie ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
