---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802462"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Awaria selektora podczas usuwania elementu z niestandardowej kolekcji INCC

|   |   |
|---|---|
|Szczegóły|Może <code>T:System.InvalidOperationException</code> wystąpić w następującym scenariuszu:<ul><li>ItemsSource for <code>T:System.Windows.Controls.Primitives.Selector</code> a jest kolekcją z <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>niestandardową implementacją .</li><li>Wybrany element zostanie usunięty z kolekcji.</li><li>Has <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (wskazując nieznaną pozycję).</li></ul>Oklena wywoławcza wyjątku rozpoczyna się w system.Windows.Threading.Dispatcher.VerifyAccess() w: System.Windows.DependencyObject.GetValue(DependencyProperty dp) w: System.Windows.Controls.Primitives.Selector.GetIsSelected(Dependency DependencyObject element)Ten wyjątek może wystąpić w .NET Framework 4.5, jeśli aplikacja ma więcej niż jeden wątek dyspozytora. W .NET Framework 4.7 wyjątek może również wystąpić w aplikacjach z jednym wątku dyspozytora. Problem został rozwiązany w .NET Framework 4.7.1.|
|Sugestia|Uaktualnienie do programu .NET Framework 4.7.1.|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
