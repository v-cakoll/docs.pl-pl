---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620125"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Elementy. Clear nie usuwa duplikatów z SelectedItems

#### <a name="details"></a>Szczegóły

Załóżmy, że selektor (z włączoną obsługą wielu zaznaczeń) ma duplikaty w <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> kolekcji — ten sam element występuje więcej niż jeden raz.  Usunięcie tych elementów ze źródła danych (np. przez wywoływanie elementów. Clear) nie powiodło się usunięcie ich z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> ; tylko pierwsze wystąpienie zostanie usunięte. Ponadto kolejne użycie <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (np. SelectedItems. Clear ()) może napotkać problemy, takie jak <xref:System.ArgumentException?displayProperty=fullName> , ponieważ <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> zawiera elementy, które nie znajdują się już w źródle danych.

#### <a name="suggestion"></a>Sugestia

Uaktualnij, jeśli to możliwe, aby .NET Framework 4.6.2.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
