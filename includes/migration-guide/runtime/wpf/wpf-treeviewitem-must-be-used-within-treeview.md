---
ms.openlocfilehash: af8cb9435be078351e3430dc8ded3f7cac377948
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620501"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>Element WPF TreeViewItem musi być używany w elemencie TreeView

#### <a name="details"></a>Szczegóły

Wprowadzono zmianę w 4,5, która ogranicza użycie <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> elementów poza <xref:System.Windows.Controls.TreeView?displayProperty=fullName> . Te manifesty w następujących warunkach:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>element Visual webparent nie jest panelem. ( <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> Wygenerowany dla elementu ma <xref:System.Windows.Controls.TreeView?displayProperty=fullName> panel jako jego element nadrzędny)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>Jest elementem podrzędnym <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> działającym jako &quot; host elementów &quot; dla kontrolki listy (ListBox, DataGrid, ListView itp.). Wirtualizacja nie musi być włączona.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>Jest to element-przewijanie ( <code>ScrollUnit=&quot;Item&quot;</code> ).</li><li>Ktoś wywołuje, <code>VirtualizingStackPanel.MakeVisible(v)</code> Aby przewinąć element <code>v</code> do widoku. Można to zrobić jawnie lub niejawnie na wiele sposobów; prawdopodobnie najbardziej typowym sposobem jest kliknięcie przycisku w <code>v</code> celu nadania fokusu klawiaturowym.</li><li>Łańcuch elementów nadrzędnych z <code>v</code> do <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> przebiegów przez <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> .</li></ul>Innymi słowy, jest to widoczne, gdy <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> jest używany poza programem <xref:System.Windows.Controls.TreeView?displayProperty=fullName> , a użytkownik klika element podrzędny w <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> celu przełączenia go do widoku. Jeśli nie <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> ma elementów podrzędnych, które nie są skoncentrowane, ten problem nie będzie widoczny. Przykładem sytuacji, w której jest to natrafiony, jest to <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> , że jest to katalog główny szablonu DataTemplate. Po osiągnięciu tego problemu istnieje InvalidCastException, który występuje w ramach struktury WPF.

#### <a name="suggestion"></a>Sugestia

Poprawka zostanie udostępniona dla tego programu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
