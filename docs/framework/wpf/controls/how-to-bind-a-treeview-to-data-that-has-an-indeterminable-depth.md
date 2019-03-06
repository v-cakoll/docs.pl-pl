---
title: 'Instrukcje: Powiąż TreeView z danymi, które mają nieokreśloną głębokość'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 6c0361674c4f6f740784a7657e018d5257c6edac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377239"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Instrukcje: Powiąż TreeView z danymi, które mają nieokreśloną głębokość
Może to być czasy, kiedy chcesz powiązać <xref:System.Windows.Controls.TreeView> ze źródłem danych, której głębokość nie jest znany.  Taka sytuacja może wystąpić, jeśli dane są cykliczne pochylone, takich jak system plików, w którym folderów może zawierać foldery, lub struktury organizacyjnej firmy, gdzie pracownicy mają innym pracownikom jako bezpośrednich podwładnych.  
  
 Źródło danych musi mieć obiekt hierarchiczny model. Na przykład `Employee` klasy może zawierać zbiór obiekty pracowników, które mają bezpośrednich podwładnych pracownika. Jeśli dane są reprezentowane w sposób, który nie jest hierarchiczna, należy utworzyć hierarchiczną reprezentację danych.  
  
 Po ustawieniu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> właściwości i, jeśli <xref:System.Windows.Controls.ItemsControl> generuje <xref:System.Windows.Controls.ItemsControl> dla każdego elementu podrzędnego, a następnie element podrzędny <xref:System.Windows.Controls.ItemsControl> używa tych samych <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> jako element nadrzędny. Na przykład jeśli ustawisz <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości powiązanych z danymi <xref:System.Windows.Controls.TreeView>, każdy <xref:System.Windows.Controls.TreeViewItem> czyli wygenerowanego używa <xref:System.Windows.DataTemplate> który został przypisany do <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwość <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> Pozwala na określenie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.TreeViewItem>, lub dowolnego <xref:System.Windows.Controls.HeaderedItemsControl>, na tym szablonie danych. Po ustawieniu <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> właściwość, która wartość jest używana, gdy <xref:System.Windows.HierarchicalDataTemplate> jest stosowany. Za pomocą <xref:System.Windows.HierarchicalDataTemplate>, możesz rekursywnie zestaw <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla każdego <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.TreeView> dane hierarchiczne i używania <xref:System.Windows.HierarchicalDataTemplate> do określenia <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla każdego <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> Tworzy powiązanie z danymi XML, który reprezentuje pracowników w firmie.  Każdy `Employee` element może zawierać innych `Employee` elementy, aby wskazać, który zgłasza, do którego. Ponieważ dane są cykliczne, <xref:System.Windows.HierarchicalDataTemplate> mogą być stosowane do poszczególnych poziomów.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
