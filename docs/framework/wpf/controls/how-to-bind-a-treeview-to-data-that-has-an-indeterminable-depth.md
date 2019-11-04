---
title: Jak powiązać TreeView z danymi, które mają nieokreśloną głębokość
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458616"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Jak powiązać TreeView z danymi, które mają nieokreśloną głębokość
Mogą wystąpić sytuacje, w których chcesz powiązać <xref:System.Windows.Controls.TreeView> ze źródłem danych, którego głębokość nie jest znana.  Taka sytuacja może wystąpić, gdy dane są rekursywnie, na przykład w systemie plików, gdzie foldery mogą zawierać foldery lub struktura organizacyjna firmy, gdzie pracownicy mają innych pracowników jako raporty bezpośrednie.  
  
 Źródło danych musi mieć hierarchiczny model obiektów. Na przykład Klasa `Employee` może zawierać kolekcję obiektów pracowników, które są bezpośrednimi raportami pracownika. Jeśli dane są reprezentowane w sposób, który nie jest hierarchiczny, należy utworzyć hierarchiczną reprezentację danych.  
  
 Po ustawieniu właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> i jeśli <xref:System.Windows.Controls.ItemsControl> generuje <xref:System.Windows.Controls.ItemsControl> dla każdego elementu podrzędnego, wówczas <xref:System.Windows.Controls.ItemsControl> podrzędne używa tego samego <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> jako elementu nadrzędnego. Na przykład, jeśli ustawisz właściwość <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> na <xref:System.Windows.Controls.TreeView>powiązane z danymi, każdy <xref:System.Windows.Controls.TreeViewItem> wygenerowany używa <xref:System.Windows.DataTemplate> przypisanego do właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> umożliwia określenie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.TreeViewItem>lub dowolnego <xref:System.Windows.Controls.HeaderedItemsControl>w szablonie danych. Po ustawieniu właściwości <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> ta wartość jest używana podczas stosowania <xref:System.Windows.HierarchicalDataTemplate>. Za pomocą <xref:System.Windows.HierarchicalDataTemplate>można rekursywnie ustawić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla każdego <xref:System.Windows.Controls.TreeViewItem> w <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób powiązania <xref:System.Windows.Controls.TreeView> z danymi hierarchicznymi i użycie <xref:System.Windows.HierarchicalDataTemplate> do określenia <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla każdej <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> wiąże się z danymi XML, które reprezentują pracowników w firmie.  Każdy element `Employee` może zawierać inne `Employee` elementy, aby wskazać, którzy raporty są. Ponieważ dane są cykliczne, <xref:System.Windows.HierarchicalDataTemplate> można zastosować do każdego poziomu.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
