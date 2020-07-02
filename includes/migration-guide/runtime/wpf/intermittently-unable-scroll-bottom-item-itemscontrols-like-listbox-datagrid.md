---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622119"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Sporadycznie nie można przewijać do ostatniego elementu w ItemsControls (na przykład ListBox i DataGrid) przy użyciu niestandardowych szablonów datatemplates

#### <a name="details"></a>Szczegóły

W niektórych przypadkach usterka w .NET Framework 4,5 powoduje, że w <xref:System.Windows.Controls.ListBox?displayProperty=fullName> <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> przypadku korzystania z niestandardowych szablonów datatemplates ItemsControls (np., itp.). W przypadku próby przeprowadzenia przewijania po raz drugi (po przeprowadzeniu przewijania kopii zapasowej) działanie zostanie wykonane.

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4.5.2 i może zostać rozwiązany przez uaktualnienie do tej wersji (lub nowszej) .NET Framework. Alternatywnie użytkownicy nadal mogą przeciągać paski przewijania do elementów końcowych w tych kolekcjach, ale może być konieczne dwukrotne wykonanie tej czynności.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
