---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091690"
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
