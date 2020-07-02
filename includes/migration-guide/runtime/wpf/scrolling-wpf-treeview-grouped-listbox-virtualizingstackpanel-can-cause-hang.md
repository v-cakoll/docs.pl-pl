---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622149"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>Przewijanie drzewa WPF lub zgrupowane pole listy w VirtualizingStackPanel może spowodować zawieszenie

#### <a name="details"></a>Szczegóły

W .NET Framework v 4.5, przewinięcie WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> w zwirtualizowanym panelu stosu może spowodować zawieszenie, jeśli w okienku ekranu pojawią się marginesy (między elementami na <xref:System.Windows.Controls.TreeView?displayProperty=fullName> przykład lub w elemencie ItemsPresenter). Ponadto w niektórych przypadkach różne elementy w widoku mogą spowodować niestabilność nawet wtedy, gdy nie ma marginesów.

#### <a name="suggestion"></a>Sugestia

Tę usterkę można uniknąć przez uaktualnienie do .NET Framework 4.5.1. Alternatywnie marginesy mogą być usuwane z kolekcji widoku (na przykład <xref:System.Windows.Controls.TreeView?displayProperty=fullName> s) w zwirtualizowanych panelach stosu, jeśli wszystkie zawarte elementy mają ten sam rozmiar.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
