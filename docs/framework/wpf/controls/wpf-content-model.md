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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187404"
---
# <a name="wpf-content-model"></a>Model zawartości WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]to platforma prezentacji, która udostępnia wiele formantów i typów podobnych do kontroli, których głównym celem jest wyświetlanie różnych typów zawartości. Aby określić, który formant do użycia lub który formant pochodzi od, należy zrozumieć rodzaje obiektów określonego formantu najlepiej wyświetlić.  
  
 W tym temacie podsumowano [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model zawartości dla typów formantów i formantów. Model zawartości opisuje, jaka zawartość może być używana w formancie. W tym temacie wymieniono również właściwości zawartości dla każdego modelu zawartości. Właściwość content jest właściwością, która jest używana do przechowywania zawartości obiektu.  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>Klasy, które zawierają dowolną zawartość  
 Niektóre formanty mogą zawierać obiekt dowolnego typu, <xref:System.DateTime> takich jak <xref:System.Windows.UIElement> ciąg, obiekt lub kontener dla dodatkowych elementów. Na przykład <xref:System.Windows.Controls.Button> może zawierać obraz i niektóre tekst; lub <xref:System.Windows.Controls.CheckBox> może zawierać wartość <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ma cztery klasy, które mogą zawierać dowolną zawartość. W poniższej tabeli wymieniono <xref:System.Windows.Controls.Control>klasy, które dziedziczą po .  
  
|Klasa zawierająca dowolną zawartość|Zawartość|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Pojedynczy dowolny obiekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Nagłówek i pojedynczy element, z których oba są dowolne obiekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekcja dowolnych obiektów.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Nagłówek i kolekcja elementów, z których wszystkie są dowolne obiekty.|  
  
 Formanty, które dziedziczą z tych klas może zawierać ten sam typ zawartości i traktować zawartość w taki sam sposób. Na poniższej ilustracji przedstawiono jeden formant z każdego modelu zawartości, który zawiera obraz i tekst:  
  
 ![Zrzut ekranu przedstawiający cztery różne kontrolki, po jednym z każdego modelu zawartości.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Formanty zawierające pojedynczy dowolny obiekt  
 Klasa <xref:System.Windows.Controls.ContentControl> zawiera pojedynczy fragment dowolnej zawartości. Jego właściwość <xref:System.Windows.Controls.ContentControl.Content%2A>zawartości jest . Następujące formanty <xref:System.Windows.Controls.ContentControl> dziedziczą z jego modelu zawartości i używają go:  
  
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
  
 Na poniższej ilustracji <xref:System.Windows.Controls.ContentControl.Content%2A> przedstawiono cztery przyciski, <xref:System.Windows.Shapes.Rectangle>których jest <xref:System.Windows.Controls.Panel> ustawiony <xref:System.Windows.Shapes.Ellipse> na <xref:System.Windows.Controls.TextBlock>ciąg, <xref:System.DateTime> obiekt, , i , który zawiera i a :  
  
 ![Zrzut ekranu przedstawiający cztery przyciski z różnymi typami zawartości.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Na przykład jak ustawić <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość, <xref:System.Windows.Controls.ContentControl>zobacz .  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Formanty zawierające nagłówek i pojedynczy dowolny obiekt  
 Klasa <xref:System.Windows.Controls.HeaderedContentControl> dziedziczy <xref:System.Windows.Controls.ContentControl> i wyświetla zawartość z nagłówkiem. <xref:System.Windows.Controls.ContentControl.Content%2A>Dziedziczy właściwość zawartości, <xref:System.Windows.Controls.ContentControl> z i <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> definiuje właściwość, <xref:System.Object>która jest typu; w związku z tym oba mogą być dowolnego obiektu.  
  
 Następujące formanty <xref:System.Windows.Controls.HeaderedContentControl> dziedziczą z jego modelu zawartości i używają go:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Na poniższej <xref:System.Windows.Controls.TabItem> ilustracji przedstawiono dwa obiekty. Pierwszy <xref:System.Windows.Controls.TabItem> ma <xref:System.Windows.UIElement> obiekty <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jako <xref:System.Windows.Controls.ContentControl.Content%2A>i . Jest <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ustawiona <xref:System.Windows.Controls.StackPanel> na a, który zawiera <xref:System.Windows.Shapes.Ellipse> i . <xref:System.Windows.Controls.TextBlock> Jest <xref:System.Windows.Controls.ContentControl.Content%2A> ustawiona <xref:System.Windows.Controls.StackPanel> na a, który zawiera i <xref:System.Windows.Controls.TextBlock> . <xref:System.Windows.Controls.Label> Drugi <xref:System.Windows.Controls.TabItem> ma ciąg w <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i <xref:System.Windows.Controls.TextBlock> w <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl, który używa różnych typów w Header właściwości.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Aby uzyskać przykład tworzenia <xref:System.Windows.Controls.TabItem> obiektów, <xref:System.Windows.Controls.HeaderedContentControl>zobacz .  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Formanty zawierające kolekcję dowolnych obiektów  
 Klasa <xref:System.Windows.Controls.ItemsControl> dziedziczy <xref:System.Windows.Controls.Control> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy. Jego właściwości zawartości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>są i . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>jest zwykle używany do wypełniania <xref:System.Windows.Controls.ItemsControl> z kolekcji danych. Jeśli nie chcesz używać kolekcji do wypełniania <xref:System.Windows.Controls.ItemsControl>programu , można <xref:System.Windows.Controls.ItemsControl.Items%2A> dodać elementy przy użyciu właściwości.  
  
 Następujące formanty <xref:System.Windows.Controls.ItemsControl> dziedziczą z jego modelu zawartości i używają go:  
  
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
  
 Na poniższej <xref:System.Windows.Controls.ListBox> ilustracji przedstawiono element zawierający następujące typy elementów:  
  
- Ciąg.  
  
- Obiekt <xref:System.DateTime>.  
  
- Klasa <xref:System.Windows.UIElement>.  
  
- A, <xref:System.Windows.Controls.Panel> który <xref:System.Windows.Shapes.Ellipse> zawiera <xref:System.Windows.Controls.TextBlock>i .  
  
 ![Zrzut ekranu przedstawiający ListBox z czterema typami zawartości.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Formanty zawierające nagłówek i zbiór dowolnych obiektów  
 Klasa <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczy <xref:System.Windows.Controls.ItemsControl> i może zawierać wiele elementów, takich jak ciągi, obiekty lub inne elementy i nagłówek. Dziedziczy właściwości <xref:System.Windows.Controls.ItemsControl> zawartości i <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, <xref:System.Windows.Controls.ItemsControl.Items%2A>i definiuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> właściwość, która może być dowolny obiekt.  
  
 Następujące formanty <xref:System.Windows.Controls.HeaderedItemsControl> dziedziczą z jego modelu zawartości i używają go:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Klasy, które zawierają kolekcję obiektów UIElement  
 Klasa <xref:System.Windows.Controls.Panel> umieszcza i rozmieszcza obiekty podrzędne. <xref:System.Windows.UIElement> Jego właściwość <xref:System.Windows.Controls.Panel.Children%2A>zawartości jest .  
  
 Następujące klasy dziedziczą <xref:System.Windows.Controls.Panel> z klasy i używają jej modelu zawartości:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Omówienie paneli](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Klasy, które wpływają na wygląd UIElement  
 Klasa <xref:System.Windows.Controls.Decorator> stosuje efekty wizualne na lub <xref:System.Windows.UIElement>wokół jednego dziecka . Jego właściwość <xref:System.Windows.Controls.Decorator.Child%2A>zawartości jest . Następujące klasy dziedziczą z <xref:System.Windows.Controls.Decorator> jego modelu zawartości i używają go:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Na poniższej <xref:System.Windows.Controls.TextBox> ilustracji przedstawiono, że <xref:System.Windows.Controls.Border> ma (jest ozdobiony) wokół niego.  
  
 ![TextBox z czarnym obramowaniem](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock z obramowaniem  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Klasy, które zapewniają wizualną opinię o UIElement  
 Klasa <xref:System.Windows.Documents.Adorner> zawiera wizualne wskazówki dla użytkownika. Na przykład <xref:System.Windows.Documents.Adorner> użyj, aby dodać dojścia funkcjonalne do elementów lub podać informacje o stanie formantu. Klasa <xref:System.Windows.Documents.Adorner> zapewnia strukturę, dzięki czemu można utworzyć własne adorners. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nie zapewnia żadnych wdrożonych adorners. Aby uzyskać więcej informacji, zobacz [Adorners Overview](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>Klasy, które umożliwiają użytkownikom wprowadzanie tekstu  
 WPF WPF zapewnia trzy podstawowe formanty, które umożliwiają użytkownikom wprowadzanie tekstu. Każdy formant wyświetla tekst w inny sposób. W poniższej tabeli wymieniono te trzy formanty związane z tekstem, ich możliwości podczas wyświetlania tekstu i ich właściwości, które zawierają tekst formantu.  
  
|Kontrola|Tekst jest wyświetlany jako|Właściwość zawartości|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Zwykły tekst|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Sformatowany tekst|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Ukryty tekst (znaki są maskowane)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>Klasy, które wyświetlają twój tekst  
 Kilka klas może służyć do wyświetlania zwykłego lub sformatowanego tekstu. Można użyć <xref:System.Windows.Controls.TextBlock> do wyświetlania niewielkich ilości tekstu. Jeśli chcesz wyświetlić duże ilości tekstu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>użyj <xref:System.Windows.Controls.FlowDocumentScrollViewer> przycisku , lub formantów.  
  
 Ma <xref:System.Windows.Controls.TextBlock> dwie właściwości <xref:System.Windows.Controls.TextBlock.Text%2A> zawartości: <xref:System.Windows.Controls.TextBlock.Inlines%2A>i . Jeśli chcesz wyświetlić tekst, który używa <xref:System.Windows.Controls.TextBlock.Text%2A> spójnego formatowania, właściwość jest często najlepszym wyborem. Jeśli planujesz używać innego formatowania w całym <xref:System.Windows.Controls.TextBlock.Inlines%2A> tekście, użyj właściwości. Właściwość <xref:System.Windows.Controls.TextBlock.Inlines%2A> jest kolekcją <xref:System.Windows.Documents.Inline> obiektów, które określają sposób formatowania tekstu.  
  
 W poniższej tabeli <xref:System.Windows.Controls.FlowDocumentReader>wymieniono właściwość zawartości dla , <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer> klasy.  
  
|Kontrola|Właściwość zawartości|Typ właściwości zawartości|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 Implementuje <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.IDocumentPaginatorSource> interfejs; w związku z tym wszystkie <xref:System.Windows.Documents.FlowDocument> trzy klasy mogą przyjmować jako zawartość.  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>Klasy, które formatuje tekst  
 <xref:System.Windows.Documents.TextElement>i powiązane z nim klasy umożliwiają formatowanie tekstu. <xref:System.Windows.Documents.TextElement>obiekty zawierają i <xref:System.Windows.Controls.TextBlock> formatuje tekst w i <xref:System.Windows.Documents.FlowDocument> obiekty. Dwa podstawowe typy <xref:System.Windows.Documents.TextElement> <xref:System.Windows.Documents.Block> obiektów <xref:System.Windows.Documents.Inline> są elementami i elementami. Element <xref:System.Windows.Documents.Block> reprezentuje blok tekstu, taki jak akapit lub lista. Element <xref:System.Windows.Documents.Inline> reprezentuje część tekstu w bloku. Wiele <xref:System.Windows.Documents.Inline> klas określa formatowanie tekstu, do którego są stosowane. Każdy <xref:System.Windows.Documents.TextElement> ma swój własny model zawartości. Aby uzyskać więcej informacji, zobacz [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane](../advanced/index.md)
