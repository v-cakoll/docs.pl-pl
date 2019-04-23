---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804698"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear nie powoduje usunięcia duplikaty z SelectedItems

|   |   |
|---|---|
|Szczegóły|Załóżmy, że selektor (z włączono wybór wielokrotny) wykryto duplikaty jego <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kolekcji — ten sam element występuje więcej niż raz.  Usunięcie tych elementów ze źródła danych (np. przez wywołanie Items.Clear) kończy się niepowodzeniem do usunięcia ich z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; tylko pierwsze wystąpienie zostanie usunięte. Ponadto późniejsze użycie <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (np. SelectedItems.Clear()) mogą wystąpić problemy takie jak <xref:System.ArgumentException?displayProperty=name>, ponieważ <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> zawiera elementy, które nie są już w źródle danych.|
|Sugestia|Uaktualnij, jeśli jest to możliwe, .NET Framework 4.6.2.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
