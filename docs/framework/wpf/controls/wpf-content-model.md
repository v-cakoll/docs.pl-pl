---
title: Model zawartości WPF
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: 751cbcc3a3b70f0937a8fe84c0fad5d8771a32ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718159"
---
# <a name="wpf-content-model"></a>Model zawartości WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest to platforma prezentacji, która zawiera wiele kontrolek i typy kontroli którego podstawowym celem jest do wyświetlania różnych typów zawartości. Aby określić, które określają, aby używać lub które określają, które ma być z, należy poznać rodzaje obiektów, które najlepiej wyświetlić określonego formantu.  
  
 Ten temat zawiera podsumowanie model zawartości dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli i typy kontroli. Model zawartości w tym artykule opisano zawartość, mogą być używane w kontrolce. Ten temat zawiera także właściwości zawartości dla każdego modelu zawartości. Właściwość zawartości ma właściwości, która jest używana do przechowywania zawartości obiektu.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Klasy, które zawierają dowolne zawartości  
 Niektóre kontrolki mogą zawierać obiekt dowolnego typu, na przykład ciąg, <xref:System.DateTime> obiektu lub <xref:System.Windows.UIElement> oznacza to kontener dla dodatkowych elementów. Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartości <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma cztery klas, które może zawierać dowolną zawartość. Poniższa tabela zawiera listę klas, które dziedziczą z <xref:System.Windows.Controls.Control>.  
  
|Klasa, która zawiera dowolną zawartość|Zawartość|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Dowolnego pojedynczego obiektu.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Nagłówek i pojedynczy element, które są dowolne obiekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekcja dowolnych obiektów.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Nagłówek i kolekcji elementów, które są dowolne obiekty.|  
  
 Formanty, które dziedziczą z tych klas może zawierać ten sam typ zawartości i traktować zawartość w taki sam sposób. Poniższa ilustracja przedstawia jeden formant z każdego modelu zawartości, który zawiera obraz i tekst.  
  
 ![Przycisk, GroupBox, obiekty, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Formanty, które zawierają dowolnego pojedynczego obiektu  
 <xref:System.Windows.Controls.ContentControl> Klasa zawiera pojedynczy dowolną zawartość. Jego właściwość zawartości ma <xref:System.Windows.Controls.ContentControl.Content%2A>. Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ContentControl> i używać jej modelu zawartości:  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 Poniższa ilustracja przedstawia cztery przyciski, którego <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiony na ciąg <xref:System.DateTime> obiektu <xref:System.Windows.Shapes.Rectangle>, a <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.  
  
 ![Cztery przyciski](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Cztery przyciski, które mają różne typy zawartości  
  
 Aby uzyskać przykład sposobu ustawiania <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości, zobacz <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Formanty, które zawiera nagłówek i dowolnego pojedynczego obiektu  
 <xref:System.Windows.Controls.HeaderedContentControl> Klasa dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość przy użyciu nagłówka. Dziedziczy właściwości zawartości <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> i definiuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> właściwość, która jest typu <xref:System.Object>; w związku z tym, jednocześnie może być dowolnego obiektu.  
  
 Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedContentControl> i używać jej modelu zawartości:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 Na poniższej ilustracji przedstawiono dwie <xref:System.Windows.Controls.TabItem> obiektów. Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiektów jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> Ustawiono <xref:System.Windows.Controls.StackPanel> zawierający <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>. Drugi <xref:System.Windows.Controls.TabItem> zawiera ciąg <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl, który używa różnych typów we właściwości nagłówka  
  
 Aby uzyskać przykład sposobu tworzenia <xref:System.Windows.Controls.TabItem> obiekty, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Formanty, które zawiera kolekcję obiektów dowolnego  
 <xref:System.Windows.Controls.ItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiektów i innych elementów. Jej właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> zazwyczaj używany do wypełnienia <xref:System.Windows.Controls.ItemsControl> ze zbieraniem danych. Jeśli nie chcesz używać kolekcji, aby wypełnić <xref:System.Windows.Controls.ItemsControl>, można dodać elementy przy użyciu <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.  
  
 Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.ItemsControl> i używać jej modelu zawartości:  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.ListBox> zawiera następujące typy elementów:  
  
-   Ciąg.  
  
-   Element <xref:System.DateTime> obiektu.  
  
-   A <xref:System.Windows.UIElement>.  
  
-   A <xref:System.Windows.Controls.Panel> zawierający <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.  
  
 ![Pola listy z czterema typami zawartości](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
ListBox, który zawiera wiele typów obiektów  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Formanty, które zawiera nagłówek i kolekcji dowolnych obiektów  
 <xref:System.Windows.Controls.HeaderedItemsControl> Klasa dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiektów, lub innych elementów i nagłówek. Dziedziczy <xref:System.Windows.Controls.ItemsControl> zawartości właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, i <xref:System.Windows.Controls.ItemsControl.Items%2A>, i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwości, które mogą być dowolnego obiektu.  
  
 Następujące elementy sterujące dziedziczyć <xref:System.Windows.Controls.HeaderedItemsControl> i używać jej modelu zawartości:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Klasy zawierające kolekcję obiektów element interfejsu użytkownika  
 <xref:System.Windows.Controls.Panel> Klas umieszcza i rozmieszcza podrzędnych <xref:System.Windows.UIElement> obiektów. Jego właściwość zawartości ma <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> klasy i użyć jej w modelu zawartości:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd panele](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Klasy, które wpływają na wygląd element interfejsu użytkownika  
 <xref:System.Windows.Controls.Decorator> Klasa ma zastosowanie efektów wizualnych lub wokół pojedynczy element podrzędny <xref:System.Windows.UIElement>. Jego właściwość zawartości ma <xref:System.Windows.Controls.Decorator.Child%2A>. Następujące klasy dziedziczą <xref:System.Windows.Controls.Decorator> i używać jej modelu zawartości:  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.TextBox> zawierający (zostanie nadany) <xref:System.Windows.Controls.Border> wokół niej.  
  
 ![Pole tekstowe z czarnym obramowaniem](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
Blok tekstu, który ma obramowanie  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Klasy, które zapewniają wizualną opinię na temat element interfejsu użytkownika  
 <xref:System.Windows.Documents.Adorner> Klasa udostępnia podpowiedzi wizualne dla użytkownika. Na przykład użyć <xref:System.Windows.Documents.Adorner> dodawania funkcjonalności dojść do elementów lub podać informacje o kontrolce stanie. <xref:System.Windows.Documents.Adorner> Klasa udostępnia strukturę, dzięki czemu można tworzyć własne moduły definiowania układu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie zapewnia żadnych zaimplementowano moduły definiowania układu. Aby uzyskać więcej informacji, zobacz [Przegląd moduły indeksowania układu](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Klasy, które umożliwiają użytkownikom wprowadzanie tekstu  
 WPF zawiera trzy kontrolki podstawowej, które umożliwiają użytkownikom wprowadzanie tekstu. Tekst jest wyświetlany w każdej kontrolce inaczej. W poniższej tabeli przedstawiono te trzy związane z tekstem kontrolki, ich możliwości, gdy są wyświetlane, tekstu i ich właściwości, które zawierają tekst kontrolki.  
  
|Formant|Tekst jest wyświetlany jako|Właściwość zawartości|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Zwykły tekst|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Tekst sformatowany|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Tekst (znaki są maskowane) ukryty|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Klasy zawierające tekst  
 Kilka klas może służyć do wyświetlania tekstu zwykłego lub sformatowany. Możesz użyć <xref:System.Windows.Controls.TextBlock> do wyświetlenia niewielkich ilości tekstu. Aby wyświetlić dużych ilości tekstu, należy użyć <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, lub <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrolki.  
  
 <xref:System.Windows.Controls.TextBlock> Ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Gdy chcesz wyświetlić tekst, który używa spójnego formatowania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość jest często najlepszym rozwiązaniem. Jeśli planujesz korzystanie z innego formatowania przez cały tekst, użyj <xref:System.Windows.Controls.TextBlock.Inlines%2A> właściwości. <xref:System.Windows.Controls.TextBlock.Inlines%2A> Właściwości to zbiór <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.  
  
 W poniższej tabeli wymieniono właściwość zawartości dla <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.  
  
|Formant|Właściwość zawartości|Typ właściwości zawartości|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejs; w związku z tym, może zająć wszystkich trzech klasach <xref:System.Windows.Documents.FlowDocument> jako zawartość.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Klasy, które formatowania tekstu  
 <xref:System.Windows.Documents.TextElement> i jej klasy pokrewne pozwalają do formatowania tekstu. <xref:System.Windows.Documents.TextElement> obiekty zawierają i formatowanie tekstu w <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument> obiektów. Dwa podstawowe typy <xref:System.Windows.Documents.TextElement> obiekty są <xref:System.Windows.Documents.Block> elementy i <xref:System.Windows.Documents.Inline> elementów. A <xref:System.Windows.Documents.Block> element reprezentuje blok tekstu, np. akapitu lub listy. <xref:System.Windows.Documents.Inline> Element reprezentuje fragment tekstu w bloku. Wiele <xref:System.Windows.Documents.Inline> klasy określić formatowanie tekstu, do której są stosowane. Każdy <xref:System.Windows.Documents.TextElement> ma swój własny model zawartości. Aby uzyskać więcej informacji, zobacz [omówienie modelu zawartości TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zaawansowane](../../../../docs/framework/wpf/advanced/index.md)
