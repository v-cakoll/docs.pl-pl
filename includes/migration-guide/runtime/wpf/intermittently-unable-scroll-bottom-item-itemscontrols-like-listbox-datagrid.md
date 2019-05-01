---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649321"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Sporadycznie mógł przewiń do dołu elementu ItemsControls (takie jak pola listy i DataGrid) podczas korzystania z niestandardowych DataTemplates

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach powoduje ItemsControls usterki w programie .NET Framework 4.5 (takich jak <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, itp.) nie przewiń ich najniższy element w przypadku korzystania z niestandardowych DataTemplates. Jeśli przewijania zostanie podjęta po raz drugi (po przewijanie, Utwórz kopię zapasową), będą działać następnie.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.2 i może zostać zlikwidowane przez uaktualnienie do tej wersji (lub nowszy) programu .NET Framework. Alternatywnie użytkownicy nadal można przeciągnąć pasków przewijania do końcowego elementów w tych kolekcjach, ale może być konieczne spróbuj dwa razy to zrobić pomyślnie.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
