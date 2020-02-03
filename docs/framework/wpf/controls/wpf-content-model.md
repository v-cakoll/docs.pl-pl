---
title: Model zawartości
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
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738280"
---
# <a name="wpf-content-model"></a>Model zawartości WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest platformą prezentacji, która udostępnia wiele kontrolek i typy podobne do kontroli, których głównym celem jest wyświetlanie różnych typów zawartości. Aby określić, która kontrolka ma być używana lub która z nich pochodzi, należy zrozumieć rodzaje obiektów, które mogą być wyświetlane dla konkretnej kontrolki.  
  
 Ten temat zawiera podsumowanie modelu zawartości dla formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i typów przypominających o kontrolkach. Model zawartości opisuje zawartość, która może być używana w formancie. W tym temacie wymieniono również właściwości zawartości dla każdego modelu zawartości. Właściwość Content jest właściwością, która jest używana do przechowywania zawartości obiektu.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Klasy, które zawierają dowolną zawartość  
 Niektóre kontrolki mogą zawierać obiekt dowolnego typu, takich jak ciąg, obiekt <xref:System.DateTime> lub <xref:System.Windows.UIElement>, który jest kontenerem dla dodatkowych elementów. Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i jakiś tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartość <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma cztery klasy, które mogą zawierać dowolną zawartość. Poniższa tabela zawiera listę klas, które dziedziczą z <xref:System.Windows.Controls.Control>.  
  
|Klasa, która zawiera dowolną zawartość|Zawartość|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Pojedynczy dowolny obiekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Nagłówek i jeden element, z których oba są dowolnymi obiektami.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekcja dowolnych obiektów.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Nagłówek i Kolekcja elementów, z których wszystkie są dowolnymi obiektami.|  
  
 Kontrolki dziedziczące z tych klas mogą zawierać ten sam typ zawartości i traktują zawartość w taki sam sposób. Na poniższej ilustracji przedstawiono jeden formant z każdego modelu zawartości, który zawiera obraz i jakiś tekst:  
  
 ![Zrzut ekranu, który pokazuje cztery różne kontrolki, jeden z każdego modelu zawartości.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Kontrolki zawierające pojedynczy dowolny obiekt  
 Klasa <xref:System.Windows.Controls.ContentControl> zawiera jedną część dowolnej zawartości. Jej właściwość content ma <xref:System.Windows.Controls.ContentControl.Content%2A>. Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.ContentControl> i używają modelu zawartości:  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 Na poniższej ilustracji przedstawiono cztery przyciski, których <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiona na ciąg, obiekt <xref:System.DateTime>, <xref:System.Windows.Shapes.Rectangle>i <xref:System.Windows.Controls.Panel>, który zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>:  
  
 ![Zrzut ekranu przedstawiający cztery przyciski z różnymi typami zawartości.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Aby zapoznać się z przykładem sposobu ustawiania właściwości <xref:System.Windows.Controls.ContentControl.Content%2A>, zobacz <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Kontrolki zawierające nagłówek i pojedynczy dowolny obiekt  
 Klasa <xref:System.Windows.Controls.HeaderedContentControl> dziedziczy po <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość z nagłówkiem. Dziedziczy właściwość content, <xref:System.Windows.Controls.ContentControl.Content%2A>z <xref:System.Windows.Controls.ContentControl> i definiuje Właściwość <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, która jest typu <xref:System.Object>; w związku z tym oba mogą być dowolnym obiektem.  
  
 Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.HeaderedContentControl> i używają modelu zawartości:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Na poniższej ilustracji przedstawiono dwa obiekty <xref:System.Windows.Controls.TabItem>. Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiekty jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jest ustawiona na <xref:System.Windows.Controls.StackPanel>, która zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> jest ustawiona na <xref:System.Windows.Controls.StackPanel>, która zawiera <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.Label>. Druga <xref:System.Windows.Controls.TabItem> zawiera ciąg w <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![Kontrolka TabControl używająca różnych typów we właściwości nagłówka.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Aby zapoznać się z przykładem sposobu tworzenia obiektów <xref:System.Windows.Controls.TabItem>, zobacz <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Kontrolki zawierające kolekcję dowolnych obiektów  
 Klasa <xref:System.Windows.Controls.ItemsControl> dziedziczy po <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy. Jego właściwości zawartości są <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> jest zwykle używany do wypełniania <xref:System.Windows.Controls.ItemsControl> za pomocą zbierania danych. Jeśli nie chcesz używać kolekcji w celu wypełnienia <xref:System.Windows.Controls.ItemsControl>, możesz dodać elementy przy użyciu właściwości <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.ItemsControl> i używają modelu zawartości:  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.ListBox> zawierający następujące typy elementów:  
  
- Ciąg.  
  
- Obiekt <xref:System.DateTime>.  
  
- Klasa <xref:System.Windows.UIElement>.  
  
- <xref:System.Windows.Controls.Panel>, który zawiera <xref:System.Windows.Shapes.Ellipse> i <xref:System.Windows.Controls.TextBlock>.  
  
 ![Zrzut ekranu przedstawiający pole listy z czterema typami zawartości.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Kontrolki zawierające nagłówek i kolekcję dowolnych obiektów  
 Klasa <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczy po <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy oraz nagłówek. Dziedziczy <xref:System.Windows.Controls.ItemsControl> właściwości zawartości, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>i <xref:System.Windows.Controls.ItemsControl.Items%2A>i definiuje Właściwość <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>, która może być dowolnym obiektem.  
  
 Następujące kontrolki dziedziczą z <xref:System.Windows.Controls.HeaderedItemsControl> i używają modelu zawartości:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Klasy, które zawierają kolekcję obiektów UIElement  
 Klasy <xref:System.Windows.Controls.Panel> umieszczają i układają obiekty podrzędne <xref:System.Windows.UIElement>. Jej właściwość content ma <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Następujące klasy dziedziczą z klasy <xref:System.Windows.Controls.Panel> i używają jej modelu zawartości:  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 Aby uzyskać więcej informacji, zobacz [panele — Omówienie](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Klasy, które wpływają na wygląd elementu UIElement  
 Klasa <xref:System.Windows.Controls.Decorator> stosuje efekty wizualne na lub wokół pojedynczego <xref:System.Windows.UIElement>podrzędnego. Jej właściwość content ma <xref:System.Windows.Controls.Decorator.Child%2A>. Następujące klasy dziedziczą z <xref:System.Windows.Controls.Decorator> i używają modelu zawartości:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.TextBox>, która ma (jest dekoracyjna) <xref:System.Windows.Controls.Border> wokół niego.  
  
 ![Pole tekstowe z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock, który ma obramowanie  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Klasy, które zapewniają wizualną opinię na temat UIElement  
 Klasa <xref:System.Windows.Documents.Adorner> dostarcza użytkownikowi podpowiedzi do wizualizacji. Na przykład użyj <xref:System.Windows.Documents.Adorner>, aby dodać uchwyty funkcjonalne do elementów lub podać informacje o stanie formantu. Klasa <xref:System.Windows.Documents.Adorner> udostępnia strukturę, która umożliwia tworzenie własnych modułów definiowania układu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie udostępnia żadnych zaimplementowanych modułów definiowania układu. Aby uzyskać więcej informacji, zobacz Moduły [definiowania](adorners-overview.md)układu.  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Klasy, które umożliwiają użytkownikom wprowadzanie tekstu  
 WPF udostępnia trzy podstawowe kontrolki, które umożliwiają użytkownikom wprowadzanie tekstu. Każdy formant Wyświetla tekst inaczej. W poniższej tabeli wymieniono te trzy kontrolki związane z tekstem, ich możliwości podczas wyświetlania tekstu oraz ich właściwości, które zawierają tekst kontrolki.  
  
|formant|Tekst jest wyświetlany jako|Właściwość zawartości|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Zwykły tekst|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Tekst sformatowany|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Tekst ukryty (znaki są maskowane)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Klasy, w których jest wyświetlany tekst  
 Do wyświetlania zwykłego lub sformatowanego tekstu można użyć kilku klas. Możesz użyć <xref:System.Windows.Controls.TextBlock>, aby wyświetlić małe ilości tekstu. Aby wyświetlić duże ilości tekstu, Użyj kontrolek <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 <xref:System.Windows.Controls.TextBlock> ma dwie właściwości zawartości: <xref:System.Windows.Controls.TextBlock.Text%2A> i <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Gdy chcesz wyświetlić tekst, który używa spójnego formatowania, właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> jest często najlepszym wyborem. Jeśli planujesz użyć innego formatowania w tekście, użyj właściwości <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Właściwość <xref:System.Windows.Controls.TextBlock.Inlines%2A> jest kolekcją obiektów <xref:System.Windows.Documents.Inline>, które określają sposób formatowania tekstu.  
  
 Poniższa tabela zawiera listę właściwości zawartości dla klas <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
|formant|Właściwość zawartości|Typ właściwości zawartości|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> implementuje interfejs <xref:System.Windows.Documents.IDocumentPaginatorSource>; w związku z tym wszystkie trzy klasy mogą przyjmować <xref:System.Windows.Documents.FlowDocument> jako zawartość.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Klasy, które formatują tekst  
 <xref:System.Windows.Documents.TextElement> i powiązane klasy umożliwiają formatowanie tekstu. obiekty <xref:System.Windows.Documents.TextElement> zawierają i formatują tekst w obiektach <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Documents.FlowDocument>. Dwa podstawowe typy obiektów <xref:System.Windows.Documents.TextElement> są <xref:System.Windows.Documents.Block> elementów i <xref:System.Windows.Documents.Inline> elementów. Element <xref:System.Windows.Documents.Block> reprezentuje blok tekstu, taki jak akapit lub lista. Element <xref:System.Windows.Documents.Inline> reprezentuje część tekstu w bloku. Wiele klas <xref:System.Windows.Documents.Inline> określa formatowanie tekstu, do którego są stosowane. Każda <xref:System.Windows.Documents.TextElement> ma własny model zawartości. Aby uzyskać więcej informacji, zobacz [Omówienie modelu zawartości TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane](../advanced/index.md)
