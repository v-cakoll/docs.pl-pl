---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804668"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectiontmove"></a>ListBoxItem IsSelected powiązania problem z observablecollection —\<T >. Przenieś

|   |   |
|---|---|
|Szczegóły|Wywoływanie <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> lub <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> w kolekcji, powiązany z <xref:System.Windows.Controls.ListBox?displayProperty=name> z elementami zaznaczonymi może spowodować nieregularne zachowanie w przyszłości zaznaczenie lub unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> elementów.|
|Sugestia|Wywoływanie <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> i <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> zamiast <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> spowoduje obejścia tego problemu. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
