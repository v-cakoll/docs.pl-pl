---
ms.openlocfilehash: 778b6973b0a08e89471f9a4aa31a077da2d30c16
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858641"
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

