---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238029"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected powiązania problem z observablecollection —&lt;T&gt;. Przenieś

|   |   |
|---|---|
|Szczegóły|Wywoływanie <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> lub <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> w kolekcji, powiązany z <xref:System.Windows.Controls.ListBox?displayProperty=name> z elementami zaznaczonymi może spowodować nieregularne zachowanie w przyszłości zaznaczenie lub unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> elementów.|
|Sugestia|Wywoływanie <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> i <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> zamiast <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> spowoduje obejścia tego problemu. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Scope|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
