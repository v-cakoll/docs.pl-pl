---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238029"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected problem wiązania z&lt;ObservableCollection T&gt;. Przenieść

|   |   |
|---|---|
|Szczegóły|<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> Wywołanie <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> lub na kolekcji powiązanej <xref:System.Windows.Controls.ListBox?displayProperty=name> z wybranych elementów może prowadzić do <xref:System.Windows.Controls.ListBox?displayProperty=name> niekonsekwentnego zachowania z przyszłego wyboru lub odsebranego elementu.|
|Sugestia|<xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> Wywołanie <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> i <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> zamiast obejść ten problem. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
