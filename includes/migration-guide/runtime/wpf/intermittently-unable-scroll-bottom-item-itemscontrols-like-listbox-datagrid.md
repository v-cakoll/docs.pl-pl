---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803152"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Sporadycznie nie można przewinąć do dołu elementu w ItemsControls (jak ListBox i DataGrid) podczas korzystania z niestandardowych DataTemplates

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach błąd w .NET Framework 4.5 powoduje ItemsControls (jak <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, itp.), aby nie przewinąć do dolnego elementu podczas korzystania z niestandardowych dataTemplates. Jeśli próba przewijania zostanie podjęta po raz drugi (po przewinięciu kopii zapasowej w górę), będzie działać wtedy.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.2 i może zostać rozwiązany przez uaktualnienie do tej wersji (lub nowszej wersji) programu .NET Framework. Alternatywnie użytkownicy mogą nadal przeciągać paski przewijania do elementów końcowych w tych kolekcjach, ale może być konieczne wypróbowanie dwa razy, aby to zrobić pomyślnie.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
