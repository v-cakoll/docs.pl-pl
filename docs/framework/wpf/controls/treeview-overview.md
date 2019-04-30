---
title: TreeView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: c0967aa506b087120c776389c2891ec9e0b0b64d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761406"
---
# <a name="treeview-overview"></a>TreeView — Przegląd
<xref:System.Windows.Controls.TreeView> Kontroli zapewnia sposób wyświetlania informacji w strukturze hierarchicznej przy użyciu zwijany węzłów. W tym temacie przedstawiono <xref:System.Windows.Controls.TreeView> i <xref:System.Windows.Controls.TreeViewItem> kontroluje i zawiera proste przykłady ich użycia.  

<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>Co to jest TreeView?  
 <xref:System.Windows.Controls.TreeView> jest <xref:System.Windows.Controls.ItemsControl> , zagnieżdżony elementów za pomocą <xref:System.Windows.Controls.TreeViewItem> kontrolki. Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>Tworzenie TreeView  
 <xref:System.Windows.Controls.TreeView> Kontrolka zawiera hierarchię <xref:System.Windows.Controls.TreeViewItem> kontrolki. A <xref:System.Windows.Controls.TreeViewItem> formant jest <xref:System.Windows.Controls.HeaderedItemsControl> zawierający <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji.  
  
 Jeśli definiujesz <xref:System.Windows.Controls.TreeView> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można jawnie określić <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości <xref:System.Windows.Controls.TreeViewItem> kontroli i elementy, które tworzą swojej kolekcji. Poprzednie ilustracja przedstawia tę metodę.  
  
 Można również określić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> danych źródła, a następnie określ <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> i <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> do definiowania <xref:System.Windows.Controls.TreeViewItem> zawartości.  
  
 Aby zdefiniować układ <xref:System.Windows.Controls.TreeViewItem> kontrolki, można również użyć <xref:System.Windows.HierarchicalDataTemplate> obiektów. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Użyj SelectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Jeśli element nie jest <xref:System.Windows.Controls.TreeViewItem> formantu, jest automatycznie załączony przez <xref:System.Windows.Controls.TreeViewItem> decyduje o <xref:System.Windows.Controls.TreeView> jest wyświetlany formantu.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozwijanie i zwijanie TreeViewItem  
 Jeśli użytkownik rozwija <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwość jest ustawiona na `true`. Można również rozwinąć lub zwinąć <xref:System.Windows.Controls.TreeViewItem> bez interwencji ze strony użytkownika bezpośrednich, ustawiając <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwości `true` (expand) lub `false` (Zwiń). Gdy ta właściwość ulegnie zmianie, <xref:System.Windows.Controls.TreeViewItem.Expanded> lub <xref:System.Windows.Controls.TreeViewItem.Collapsed> wystąpi zdarzenie.  
  
 Gdy <xref:System.Windows.FrameworkElement.BringIntoView%2A> metoda jest wywoływana w <xref:System.Windows.Controls.TreeViewItem> kontrolki, <xref:System.Windows.Controls.TreeViewItem> oraz jego element nadrzędny <xref:System.Windows.Controls.TreeViewItem> rozwiń kontrolki. Jeśli <xref:System.Windows.Controls.TreeViewItem> nie jest widoczny czy częściowo widoczny <xref:System.Windows.Controls.TreeView> Przewija, aby była widoczna.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>Wybór TreeViewItem  
 Kiedy użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> formantu, aby ją zaznaczyć, <xref:System.Windows.Controls.TreeViewItem.Selected> wystąpi zdarzenie, a jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `true`. <xref:System.Windows.Controls.TreeViewItem> Staje się również <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView> kontroli. Z drugiej strony, gdy zmieni się zaznaczenie z <xref:System.Windows.Controls.TreeViewItem> kontrolki, jego <xref:System.Windows.Controls.TreeViewItem.Unselected> wystąpi zdarzenie i jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość <xref:System.Windows.Controls.TreeView> kontroli jest właściwością tylko do odczytu; w związku z tym, nie można jawnie ustawić go. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość jest ustawiona, jeśli użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> kontroli lub <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `true` na <xref:System.Windows.Controls.TreeViewItem> kontroli.  
  
 Użyj <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości w celu określenia <xref:System.Windows.Controls.TreeView.SelectedValue%2A> z <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Aby uzyskać więcej informacji, zobacz [Użyj SelectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Program obsługi zdarzeń można zarejestrować na <xref:System.Windows.Controls.TreeView.SelectedItemChanged> zdarzeń w celu ustalenia, kiedy wybranego <xref:System.Windows.Controls.TreeViewItem> zmiany. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Jest podany w zdarzeniu kod obsługi wyjątku Określa <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, co jest ustawieniem poprzedniej i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, czyli bieżące zaznaczenie. Te wartości mogą być `null` Jeśli aplikacji lub użytkownik nie wprowadził poprzedniego lub bieżącego zaznaczenia.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView — Style  
 Domyślny styl <xref:System.Windows.Controls.TreeView> kontroli umieszcza go w programie <xref:System.Windows.Controls.StackPanel> obiekt, który zawiera <xref:System.Windows.Controls.ScrollViewer> kontroli. Po ustawieniu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości <xref:System.Windows.Controls.TreeView>, te wartości są używane do rozmiaru <xref:System.Windows.Controls.StackPanel> obiekt, który wyświetla <xref:System.Windows.Controls.TreeView>. Jeśli zawartość wyświetlaną jest większy niż obszaru wyświetlania <xref:System.Windows.Controls.ScrollViewer> automatycznie wyświetla, dzięki czemu użytkownik może przewijać <xref:System.Windows.Controls.TreeView> zawartości.  
  
 Aby dostosować wygląd <xref:System.Windows.Controls.TreeViewItem> , ustaw <xref:System.Windows.FrameworkElement.Style%2A> właściwości do niestandardowego <xref:System.Windows.Style>.  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.FontSize%2A> wartości właściwości <xref:System.Windows.Controls.TreeViewItem> kontroli przy użyciu <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Dodawanie obrazów i innej zawartości do elementów widoku drzewa  
 Może zawierać więcej niż jeden obiekt w <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości <xref:System.Windows.Controls.TreeViewItem>. Obejmujący wiele obiektów w <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości, należy ująć obiektów wewnątrz kontrolkę układu, takich jak <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.StackPanel>.  
  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> z <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.TextBlock> , są ujęte w <xref:System.Windows.Controls.DockPanel> kontroli.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.DataTemplate> zawierający <xref:System.Windows.Controls.Image> i <xref:System.Windows.Controls.TextBlock> ujęte w <xref:System.Windows.Controls.DockPanel> kontroli. Możesz użyć <xref:System.Windows.DataTemplate> można ustawić <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> lub <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> dla <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Tematy z instrukcjami](treeview-how-to-topics.md)
- [Model zawartości WPF](wpf-content-model.md)
