---
title: TreeView — Przegląd
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187370"
---
# <a name="treeview-overview"></a>TreeView — Przegląd
Formant <xref:System.Windows.Controls.TreeView> umożliwia wyświetlanie informacji w strukturze hierarchicznej przy użyciu węzłów zwijanych. W tym temacie <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.TreeViewItem> przedstawiono i formanty i zawiera proste przykłady ich użycia.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>Co to jest TreeView?  
 <xref:System.Windows.Controls.TreeView>jest <xref:System.Windows.Controls.ItemsControl> to, która zagnieżdża elementy przy użyciu <xref:System.Windows.Controls.TreeViewItem> formantów. Poniższy przykład <xref:System.Windows.Controls.TreeView>tworzy .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>Tworzenie widoku drzewa  
 Formant <xref:System.Windows.Controls.TreeView> zawiera hierarchię <xref:System.Windows.Controls.TreeViewItem> formantów. Formant <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.HeaderedItemsControl> jest, który <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> ma <xref:System.Windows.Controls.ItemsControl.Items%2A> i kolekcji.  
  
 Jeśli definiujesz za <xref:System.Windows.Controls.TreeView> pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programu , można <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> jawnie <xref:System.Windows.Controls.TreeViewItem> zdefiniować zawartość formantu i elementów, które tworzą jego kolekcji. Na poprzedniej ilustracji przedstawiono tę metodę.  
  
 Można również <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> określić jako źródło danych, <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> a następnie <xref:System.Windows.Controls.TreeViewItem> określić i zdefiniować zawartość.  
  
 Aby zdefiniować układ <xref:System.Windows.Controls.TreeViewItem> formantu, <xref:System.Windows.HierarchicalDataTemplate> można również użyć obiektów. Aby uzyskać więcej informacji i przykład, zobacz [Użyj SelectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Jeśli element nie <xref:System.Windows.Controls.TreeViewItem> jest formantem, jest automatycznie <xref:System.Windows.Controls.TreeViewItem> łączony przez formant, gdy <xref:System.Windows.Controls.TreeView> formant jest wyświetlany.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Rozwijanie i zwijanie treeViewItem  
 Jeśli użytkownik rozwinie <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> właściwość `true`jest ustawiona na . Można również rozwinąć <xref:System.Windows.Controls.TreeViewItem> lub zwinąć bez <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> żadnych `true` akcji użytkownika `false` bezpośredniego, ustawiając właściwość na (rozwiń) lub (zwiń). Po zmianie tej <xref:System.Windows.Controls.TreeViewItem.Expanded> właściwości <xref:System.Windows.Controls.TreeViewItem.Collapsed> występuje zdarzenie lub.  
  
 Gdy <xref:System.Windows.FrameworkElement.BringIntoView%2A> metoda jest wywoływana <xref:System.Windows.Controls.TreeViewItem> na <xref:System.Windows.Controls.TreeViewItem> formancie, i jego nadrzędne <xref:System.Windows.Controls.TreeViewItem> formanty rozwijać. Jeśli <xref:System.Windows.Controls.TreeViewItem> a nie jest widoczny lub częściowo <xref:System.Windows.Controls.TreeView> widoczny, przewinie, aby był widoczny.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>Wybór treeViewItem  
 Gdy <xref:System.Windows.Controls.TreeViewItem> użytkownik kliknie formant, <xref:System.Windows.Controls.TreeViewItem.Selected> aby go zaznaczyć, zdarzenie występuje, a jego <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest ustawiona na `true`. Staje <xref:System.Windows.Controls.TreeViewItem> się <xref:System.Windows.Controls.TreeView.SelectedItem%2A> również <xref:System.Windows.Controls.TreeView> kontroli. Z drugiej strony, gdy <xref:System.Windows.Controls.TreeViewItem> zaznaczenie <xref:System.Windows.Controls.TreeViewItem.Unselected> zmieni się <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> z formantu, występuje jego zdarzenie, a jego właściwość jest ustawiona na `false`.  
  
 Właściwość <xref:System.Windows.Controls.TreeView.SelectedItem%2A> w <xref:System.Windows.Controls.TreeView> formancie jest właściwością tylko do odczytu; w związku z tym nie można go jawnie ustawić. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Właściwość jest ustawiana, jeśli <xref:System.Windows.Controls.TreeViewItem> użytkownik kliknie formant lub gdy <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> właściwość jest `true` ustawiona <xref:System.Windows.Controls.TreeViewItem> na formancie.  
  
 Użyj <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> właściwości, aby <xref:System.Windows.Controls.TreeView.SelectedValue%2A> określić a <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Aby uzyskać więcej informacji, zobacz [Użyj selectedValue, SelectedValuePath i SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Można zarejestrować program obsługi <xref:System.Windows.Controls.TreeView.SelectedItemChanged> zdarzeń w zdarzeniu <xref:System.Windows.Controls.TreeViewItem> w celu określenia, kiedy wybrane zmiany. Program <xref:System.Windows.RoutedPropertyChangedEventArgs%601> obsługi zdarzeń, który jest <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>dostarczany do programu obsługi zdarzeń <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>określa , który jest poprzedni wybór i , który jest bieżącym zaznaczeniem. Wartość może być, `null` jeśli aplikacja lub użytkownik nie dokonał poprzedniego lub bieżącego wyboru.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>Styl treeView  
 Domyślny styl <xref:System.Windows.Controls.TreeView> formantu umieszcza <xref:System.Windows.Controls.StackPanel> go wewnątrz <xref:System.Windows.Controls.ScrollViewer> obiektu, który zawiera formant. Po ustawieniu <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> i właściwości <xref:System.Windows.Controls.TreeView>dla , wartości te <xref:System.Windows.Controls.StackPanel> są używane <xref:System.Windows.Controls.TreeView>do rozmiaru obiektu, który wyświetla . Jeśli wyświetlana zawartość jest większa niż <xref:System.Windows.Controls.ScrollViewer> obszar wyświetlania, zostanie wyświetlona <xref:System.Windows.Controls.TreeView> automatycznie, aby użytkownik mógł przewijać zawartość.  
  
 Aby dostosować wygląd formantu, <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.FrameworkElement.Style%2A> ustaw właściwość <xref:System.Windows.Style>na niestandardową .  
  
 W poniższym przykładzie <xref:System.Windows.Controls.Control.Foreground%2A> pokazano, jak <xref:System.Windows.Controls.TreeViewItem> ustawić wartości <xref:System.Windows.FrameworkElement.Style%2A>i <xref:System.Windows.Controls.Control.FontSize%2A> właściwości formantu za pomocą .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>Dodawanie obrazów i innej zawartości do elementów TreeView  
 W <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> zawartości pliku <xref:System.Windows.Controls.TreeViewItem>. Aby uwzględnić <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> wiele obiektów w zawartości, łącz obiekty <xref:System.Windows.Controls.Panel> wewnątrz <xref:System.Windows.Controls.StackPanel>formantu układu, takiego jak a lub .  
  
 Poniższy przykład pokazuje, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> jak <xref:System.Windows.Controls.TreeViewItem> zdefiniować <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBlock> jako a i które <xref:System.Windows.Controls.DockPanel> są ujęte w formancie.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Poniższy przykład pokazuje, <xref:System.Windows.DataTemplate> jak zdefiniować, który zawiera <xref:System.Windows.Controls.Image> i a, <xref:System.Windows.Controls.TextBlock> które są ujęte w formancie. <xref:System.Windows.Controls.DockPanel> Za pomocą <xref:System.Windows.DataTemplate> a można <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ustawić <xref:System.Windows.Controls.TreeViewItem>lub dla .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Tematy in jakże](treeview-how-to-topics.md)
- [Model zawartości WPF](wpf-content-model.md)
