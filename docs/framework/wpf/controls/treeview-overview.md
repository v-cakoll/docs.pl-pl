---
title: TreeView — Przegląd
description: Dowiedz się, w jaki sposób formant TreeView Windows Presentation Foundation wyświetla informacje w strukturze hierarchicznej za pomocą węzłów, w tym prostych przykładów.
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164535"
---
# <a name="treeview-overview"></a>TreeView — Przegląd
<xref:System.Windows.Controls.TreeView>Kontrolka zapewnia sposób wyświetlania informacji w strukturze hierarchicznej za pomocą zwijanych węzłów. W tym temacie przedstawiono <xref:System.Windows.Controls.TreeView> formanty i i <xref:System.Windows.Controls.TreeViewItem> przedstawiono proste przykłady ich użycia.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Co to jest widok TreeView?  
 <xref:System.Windows.Controls.TreeView>jest <xref:System.Windows.Controls.ItemsControl> zagnieżdżał elementy przy użyciu <xref:System.Windows.Controls.TreeViewItem> kontrolek. Poniższy przykład tworzy <xref:System.Windows.Controls.TreeView> .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Tworzenie drzewa TreeView  
 <xref:System.Windows.Controls.TreeView>Kontrolka zawiera hierarchię <xref:System.Windows.Controls.TreeViewItem> formantów. <xref:System.Windows.Controls.TreeViewItem>Kontrolka jest z <xref:System.Windows.Controls.HeaderedItemsControl> <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcją i.  
  
 Jeśli definiujesz za <xref:System.Windows.Controls.TreeView> pomocą, można [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jawnie zdefiniować <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartość <xref:System.Windows.Controls.TreeViewItem> kontrolki i elementy, które składają się na swoją kolekcję. Na poprzedniej ilustracji przedstawiono tę metodę.  
  
 Można również określić <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jako źródło danych, a następnie określić <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> i <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> zdefiniować <xref:System.Windows.Controls.TreeViewItem> zawartość.  
  
 Aby zdefiniować układ <xref:System.Windows.Controls.TreeViewItem> kontrolki, można również użyć <xref:System.Windows.HierarchicalDataTemplate> obiektów. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Korzystanie z SelectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Jeśli element nie jest <xref:System.Windows.Controls.TreeViewItem> kontrolką, jest on automatycznie otoczony przez <xref:System.Windows.Controls.TreeViewItem> kontrolkę, gdy <xref:System.Windows.Controls.TreeView> kontrolka jest wyświetlana.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozwijanie i zwijanie elementu TreeViewItem  
 Jeśli użytkownik rozwinie obiekt <xref:System.Windows.Controls.TreeViewItem> , <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> Właściwość jest ustawiona na `true` . Możesz również rozwinąć lub zwinąć <xref:System.Windows.Controls.TreeViewItem> bez żadnej akcji użytkownika bezpośredniego przez ustawienie <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwości na `true` (rozwiń) lub `false` (Zwiń). Gdy ta właściwość ulegnie zmianie, <xref:System.Windows.Controls.TreeViewItem.Expanded> wystąpi <xref:System.Windows.Controls.TreeViewItem.Collapsed> zdarzenie lub.  
  
 Gdy <xref:System.Windows.FrameworkElement.BringIntoView%2A> Metoda jest wywoływana na <xref:System.Windows.Controls.TreeViewItem> kontrolce, <xref:System.Windows.Controls.TreeViewItem> i jej <xref:System.Windows.Controls.TreeViewItem> kontrolki nadrzędne rozszerzają się. Jeśli element <xref:System.Windows.Controls.TreeViewItem> nie jest widoczny lub częściowo widoczny, <xref:System.Windows.Controls.TreeView> przewija, aby był widoczny.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem zaznaczenie  
 Gdy użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> formant, aby go zaznaczyć, <xref:System.Windows.Controls.TreeViewItem.Selected> wystąpi zdarzenie, a jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> Właściwość jest ustawiona na `true` . Jest to <xref:System.Windows.Controls.TreeViewItem> również <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> formant. Na odwrót, gdy zaznaczenie zostanie zmienione z <xref:System.Windows.Controls.TreeViewItem> kontrolki, <xref:System.Windows.Controls.TreeViewItem.Unselected> wystąpi jego zdarzenie, a jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> Właściwość jest ustawiona na `false` .  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Właściwość <xref:System.Windows.Controls.TreeView> kontrolki jest właściwością tylko do odczytu, dlatego nie można jej jawnie ustawić. <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Właściwość jest ustawiana, jeśli użytkownik kliknie <xref:System.Windows.Controls.TreeViewItem> kontrolkę lub gdy <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> Właściwość jest ustawiona na `true` <xref:System.Windows.Controls.TreeViewItem> kontrolkę.  
  
 Użyj <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości, aby określić a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> <xref:System.Windows.Controls.TreeView.SelectedItem%2A> . Aby uzyskać więcej informacji, zobacz [Korzystanie z SelectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Można zarejestrować procedurę obsługi zdarzeń dla zdarzenia, <xref:System.Windows.Controls.TreeView.SelectedItemChanged> Aby określić, kiedy wybrane <xref:System.Windows.Controls.TreeViewItem> zmiany zostały wprowadzone. , <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Który jest dostarczany do programu obsługi zdarzeń określa <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> , który jest poprzednim wyborem, i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> , który jest bieżącym wyborem. Każda wartość może być `null` , jeśli aplikacja lub użytkownik nie wykonał wcześniej lub bieżącego wyboru.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Styl widoku TreeView  
 Domyślny styl <xref:System.Windows.Controls.TreeView> kontrolki umieszcza go wewnątrz <xref:System.Windows.Controls.StackPanel> obiektu, który zawiera <xref:System.Windows.Controls.ScrollViewer> kontrolkę. Po ustawieniu <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> właściwości i dla elementu <xref:System.Windows.Controls.TreeView> , te wartości są używane do zmiany rozmiaru <xref:System.Windows.Controls.StackPanel> obiektu, w którym jest wyświetlany <xref:System.Windows.Controls.TreeView> . Jeśli zawartość do wyświetlenia jest większa niż obszar wyświetlania, zostanie <xref:System.Windows.Controls.ScrollViewer> automatycznie wyświetlona, aby użytkownik mógł przewijać <xref:System.Windows.Controls.TreeView> zawartość.  
  
 Aby dostosować wygląd <xref:System.Windows.Controls.TreeViewItem> kontrolki, ustaw <xref:System.Windows.FrameworkElement.Style%2A> Właściwość na niestandardową <xref:System.Windows.Style> .  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A> wartości właściwości i dla <xref:System.Windows.Controls.TreeViewItem> kontrolki przy użyciu <xref:System.Windows.FrameworkElement.Style%2A> .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Dodawanie obrazów i innych treści do elementów TreeView  
 W zawartości elementu można uwzględnić więcej niż jeden obiekt <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> . Aby dołączyć wiele obiektów do <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości, należy ująć obiekty wewnątrz kontrolki układu, np <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.StackPanel> . lub.  
  
 Poniższy przykład pokazuje, jak zdefiniować a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> jako <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.TextBlock> , które są zawarte w <xref:System.Windows.Controls.DockPanel> kontrolce.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.DataTemplate> , który zawiera <xref:System.Windows.Controls.Image> a i <xref:System.Windows.Controls.TextBlock> , które są ujęte w <xref:System.Windows.Controls.DockPanel> kontrolce. Można użyć, <xref:System.Windows.DataTemplate> Aby ustawić <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> lub <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> dla <xref:System.Windows.Controls.TreeViewItem> .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [— Tematy porad](treeview-how-to-topics.md)
- [Model zawartości WPF](wpf-content-model.md)
