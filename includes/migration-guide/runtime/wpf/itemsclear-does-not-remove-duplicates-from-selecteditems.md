---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857537"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear nie usuwa duplikatów z selecteditems

|   |   |
|---|---|
|Szczegóły|Załóżmy, że selektor (z włączoną <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> wielokrotnością zaznaczenia) ma duplikaty w swojej kolekcji — ten sam element pojawia się więcej niż raz.  Usunięcie tych elementów ze źródła danych (np. wywołanie Items.Clear) <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>nie może ich usunąć; tylko pierwsza instancja jest usuwana. Ponadto późniejsze <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> użycie (np. selecteditems.Clear()) może napotkać problemy, takie jak <xref:System.ArgumentException?displayProperty=name>, ponieważ <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> zawiera elementy, które nie znajdują się już w źródle danych.|
|Sugestia|Uaktualnij, jeśli to możliwe, do programu .NET Framework 4.6.2.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
