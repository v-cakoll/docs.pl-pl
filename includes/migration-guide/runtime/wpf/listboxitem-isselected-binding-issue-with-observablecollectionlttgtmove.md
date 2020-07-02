---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620453"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>Problem z powiązaniem IsSelected ListBoxItem z ObservableCollection &lt; T &gt; . Przenieś

#### <a name="details"></a>Szczegóły

Wywołanie <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> lub <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> w kolekcji powiązanej <xref:System.Windows.Controls.ListBox?displayProperty=fullName> z zaznaczonymi elementami może prowadzić do nieprawidłowych zachowań z przyszłym wyborem lub usunięciem zaznaczenia <xref:System.Windows.Controls.ListBox?displayProperty=fullName> elementów.

#### <a name="suggestion"></a>Sugestia

Wywołanie <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> i <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> zamiast obejścia <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> tego problemu. Alternatywnie ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
