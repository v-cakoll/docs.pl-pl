---
title: "TreeView — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e5f6b3d0a185754bc0d8d8ee726ca13443ccdc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-overview"></a>TreeView — Przegląd
<xref:System.Windows.Controls.TreeView> Kontrola zapewnia sposób wyświetlania informacji w strukturę hierarchiczną przy użyciu zwijanej węzłów. W tym temacie przedstawiono <xref:System.Windows.Controls.TreeView> i <xref:System.Windows.Controls.TreeViewItem> formanty i zawiera proste przykłady ich użycia.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>Co to jest element TreeView?  
 <xref:System.Windows.Controls.TreeView>jest <xref:System.Windows.Controls.ItemsControl> który zagnieżdżony elementów za pomocą <xref:System.Windows.Controls.TreeViewItem> kontrolki. Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Tworzenie elementu TreeView  
 <xref:System.Windows.Controls.TreeView> Formant zawiera hierarchię <xref:System.Windows.Controls.TreeViewItem> kontrolki. A <xref:System.Windows.Controls.TreeViewItem> formant jest <xref:System.Windows.Controls.HeaderedItemsControl> mający <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji.  
  
 Jeśli definiujesz <xref:System.Windows.Controls.TreeView> za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można oznaczyć <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości <xref:System.Windows.Controls.TreeViewItem> kontroli i elementy wchodzące w skład jego kolekcja. Poprzedniej ilustracji przedstawiono tę metodę.  
  
 Można również określić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako danych źródła, a następnie określ <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> i <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do definiowania <xref:System.Windows.Controls.TreeViewItem> zawartości.  
  
 Do definiowania układu <xref:System.Windows.Controls.TreeViewItem> sterowania, można również użyć <xref:System.Windows.HierarchicalDataTemplate> obiektów. Aby uzyskać więcej informacji i przykład zobacz [SelectedValue Użyj właściwości SelectedValuePath i SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Jeśli element nie jest <xref:System.Windows.Controls.TreeViewItem> kontroli, jest automatycznie załączony przez <xref:System.Windows.Controls.TreeViewItem> decyduje o <xref:System.Windows.Controls.TreeView> formant jest wyświetlany.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozwijanie i zwijanie TreeViewItem  
 Jeśli użytkownik rozwija <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwość jest ustawiona na `true`. Można również rozwinąć lub zwinąć <xref:System.Windows.Controls.TreeViewItem> bez udziału użytkownika bezpośrednio przez ustawienie <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwości `true` (expand) lub `false` (zwijanie). Gdy ta właściwość ulegnie zmianie, <xref:System.Windows.Controls.TreeViewItem.Expanded> lub <xref:System.Windows.Controls.TreeViewItem.Collapsed> zdarzenie.  
  
 Podczas <xref:System.Windows.FrameworkElement.BringIntoView%2A> wywoływana jest metoda <xref:System.Windows.Controls.TreeViewItem> kontroli, <xref:System.Windows.Controls.TreeViewItem> a jego elementem nadrzędnym <xref:System.Windows.Controls.TreeViewItem> rozwiń kontrolki. Jeśli <xref:System.Windows.Controls.TreeViewItem> nie jest widoczny, czy częściowo widoczne <xref:System.Windows.Controls.TreeView> Przewija, aby go wyświetlić.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Wybór TreeViewItem  
 Gdy użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> sterowania, wybierz ją, <xref:System.Windows.Controls.TreeViewItem.Selected> wystąpi zdarzenie, a jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `true`. <xref:System.Windows.Controls.TreeViewItem> Staje się również <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView> formantu. Z drugiej strony, gdy zmieni się zaznaczenie z <xref:System.Windows.Controls.TreeViewItem> kontroli, jego <xref:System.Windows.Controls.TreeViewItem.Unselected> zdarzenie i jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość <xref:System.Windows.Controls.TreeView> formantu jest właściwością tylko do odczytu; w związku z tym nie można jawnie ustawić go. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość jest ustawiona, gdy użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> kontroli lub gdy <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `true` na <xref:System.Windows.Controls.TreeViewItem> formantu.  
  
 Użyj <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości w celu określenia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> z <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Aby uzyskać więcej informacji, zobacz [SelectedValue Użyj właściwości SelectedValuePath i SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Program obsługi zdarzeń można zarejestrować na <xref:System.Windows.Controls.TreeView.SelectedItemChanged> zdarzeń w celu określenia, gdy zaznaczony <xref:System.Windows.Controls.TreeViewItem> zmiany. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Jest podany w zdarzeniu określa obsługi <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, co jest ustawieniem poprzedniej i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, który jest bieżącym zaznaczeniu. Każda wartość może być `null` Jeśli aplikacji lub użytkownik nie wprowadził poprzedniego lub bieżącego zaznaczenia.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView — styl  
 Domyślny styl <xref:System.Windows.Controls.TreeView> kontroli umieszcza wewnątrz <xref:System.Windows.Controls.StackPanel> obiekt, który zawiera <xref:System.Windows.Controls.ScrollViewer> formantu. Podczas ustawiania <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.Controls.TreeView>, te wartości są używane do rozmiaru <xref:System.Windows.Controls.StackPanel> obiekt, który wyświetla <xref:System.Windows.Controls.TreeView>. Jeśli zawartość wyświetlaną jest większy niż obszar wyświetlania <xref:System.Windows.Controls.ScrollViewer> wyświetla automatycznie, dzięki czemu można przewijać <xref:System.Windows.Controls.TreeView> zawartości.  
  
 Aby dostosować wygląd <xref:System.Windows.Controls.TreeViewItem> kontrolować, ustaw <xref:System.Windows.FrameworkElement.Style%2A> właściwości do niestandardowego <xref:System.Windows.Style>.  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.FontSize%2A> wartości właściwości <xref:System.Windows.Controls.TreeViewItem> formantu przy użyciu <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Dodawanie obrazów i innej zawartości do elementów TreeView  
 Może zawierać więcej niż jeden obiekt <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości <xref:System.Windows.Controls.TreeViewItem>. Aby dołączyć wiele obiektów w <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości, należy ująć obiektów wewnątrz formantu układu, takich jak <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.StackPanel>.  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> z <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.TextBlock> że są ujęte w <xref:System.Windows.Controls.DockPanel> formantu.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.Image> i <xref:System.Windows.Controls.TextBlock> ujęte w <xref:System.Windows.Controls.DockPanel> formantu. Można użyć <xref:System.Windows.DataTemplate> można ustawić <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> lub <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> dla <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [Model zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
