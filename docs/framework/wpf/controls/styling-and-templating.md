---
title: "Tworzenie szablonów i stylów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5bd85383cc27687974fbf3689793a60569a4f97a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="styling-and-templating"></a>Tworzenie szablonów i stylów
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Style i tworzenia szablonów odwoływać się do zestawu funkcji (style, szablony, wyzwalaczy i scenorys), które umożliwiają deweloperów i projektantów do tworzenia efektów wizualny i utworzyć spójny wygląd ich produktu. Chociaż deweloperów i projektantów lub można dostosować wygląd często na podstawie aplikacji przez aplikację, model strong style i tworzenia szablonów jest niezbędne w celu umożliwienia obsługi i udostępnianie wyglądu w ramach i między aplikacjami. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]udostępnia modelu.  
  
 Kolejną funkcją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model stylów jest oddzielenie logiki i prezentacji. Oznacza to, że projektantów można zmieniać wygląd aplikacji tylko przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym samym czasie, który deweloperzy pracować przy użyciu logiki programowania przy użyciu języka C# lub Visual Basic.  
  
 To omówienie koncentruje się na aspektach stylami i tworzenia szablonów, aplikacji i nie omówiono w nim żadnych koncepcji powiązania danych. Aby uzyskać informacje dotyczące powiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Ponadto jest zrozumieć zasoby, które są co włączyć style i szablony zostanie ponownie. Aby uzyskać więcej informacji o zasobach, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Style i przykładowe tworzenia szablonów  
 Przykłady kodu, używany w tym omówieniu są oparte na próbkę proste fotografii pokazano na poniższej ilustracji:  
  
 ![Styl elementu ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 W tym przykładzie prosty fotografii używa stylami i tworzenia szablonów można utworzyć wizualny środowisko użytkownika. Przykład ma dwa <xref:System.Windows.Controls.TextBlock> elementów i <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z listy obrazów. Pełny przykład, zobacz [wprowadzenie do stylów i tworzenia szablonów przykładowa](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Podstawowe informacje dotyczące stylu  
 Można potraktować <xref:System.Windows.Style> to wygodny sposób, aby zastosować zestaw wartości właściwości do więcej niż jeden element. Na przykład, należy wziąć pod uwagę następujące <xref:System.Windows.Controls.TextBlock> elementów i ich wygląd domyślny:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Można zmienić wygląd domyślny przez ustawienie właściwości, takie jak <xref:System.Windows.Controls.Control.FontSize%2A> i <xref:System.Windows.Controls.Control.FontFamily%2A>, na każdym <xref:System.Windows.Controls.TextBlock> element bezpośrednio. Jednak jeśli chcesz z <xref:System.Windows.Controls.TextBlock> elementy, aby udostępnić niektóre właściwości, można utworzyć <xref:System.Windows.Style> w `Resources` części Twojego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Podczas ustawiania <xref:System.Windows.Style.TargetType%2A> Twojego stylu do <xref:System.Windows.Controls.TextBlock> typu, stylu jest stosowane do wszystkich <xref:System.Windows.Controls.TextBlock> elementów w oknie.  
  
 Teraz <xref:System.Windows.Controls.TextBlock> elementy wyglądają następująco:  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Rozszerzanie style  
 Określić ma dwie sieci <xref:System.Windows.Controls.TextBlock> elementy, które udostępniają niektórych wartości właściwości, takie jak <xref:System.Windows.Controls.Control.FontFamily%2A> i wyśrodkowany <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ale ma także tekst "Moje obrazy" niektóre dodatkowe właściwości. Możesz to zrobić przez utworzenie nowego stylu opiera się na pierwszym stylu, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Należy zauważyć, że podano wcześniejszy styl `x:Key`. Aby zastosować styl, należy ustawić <xref:System.Windows.FrameworkElement.Style%2A> właściwości na Twojej <xref:System.Windows.Controls.TextBlock> do `x:Key` wartość, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 To <xref:System.Windows.Controls.TextBlock> ma teraz styl <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> wartość `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> wartość 26, a <xref:System.Windows.Controls.TextBlock.Foreground%2A> wartość <xref:System.Windows.Media.LinearGradientBrush> pokazano w przykładzie. Należy zauważyć, że zastępuje on <xref:System.Windows.Controls.Control.FontSize%2A> wartość stylu bazowego. Jeśli istnieje więcej niż jeden <xref:System.Windows.Setter> ustawienie tej właściwości <xref:System.Windows.Style>, <xref:System.Windows.Setter> czyli zadeklarowane ostatniego ma pierwszeństwo.  
  
 Oto co <xref:System.Windows.Controls.TextBlock> elementy wyglądać tak jak:  
  
 ![Styl obiekty TextBlock](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 To `TitleText` styl rozszerza styl, który został utworzony dla <xref:System.Windows.Controls.TextBlock> typu. Można również rozszerzyć zasięg styl, który ma `x:Key` przy użyciu `x:Key` wartość. Na przykład, zobacz przykład przewidzianych <xref:System.Windows.Style.BasedOn%2A> właściwości.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relacja właściwości TargetType i atrybut x: Key  
 Jak pokazano w pierwszym przykładzie, ustawienie <xref:System.Windows.Style.TargetType%2A> właściwości `TextBlock` bez przypisywanie styl `x:Key` powoduje, że styl, który ma zostać zastosowany do wszystkich <xref:System.Windows.Controls.TextBlock> elementów. W takim przypadku `x:Key` niejawnie ustawiono `{x:Type TextBlock}`. Oznacza to, że jeśli jawnie ustawiona `x:Key` do żadnych innych niż wartości `{x:Type TextBlock}`, <xref:System.Windows.Style> nie została zastosowana do wszystkich <xref:System.Windows.Controls.TextBlock> elementy automatycznie. Zamiast tego należy zastosować styl (przy użyciu `x:Key` wartość) do <xref:System.Windows.Controls.TextBlock> elementy jawnie. Jeśli dany styl znajduje się w sekcji zasobów i nie należy ustawiać <xref:System.Windows.Style.TargetType%2A> właściwości stylu użytkownika, możesz podać `x:Key`.  
  
 Oprócz wartości domyślnej dla `x:Key`, <xref:System.Windows.Style.TargetType%2A> właściwość określa typ, do którego odnoszą się właściwości metody ustawiającej. Jeśli nie określisz <xref:System.Windows.Style.TargetType%2A>, muszą kwalifikować się do właściwości w Twojej <xref:System.Windows.Setter> obiektów o nazwie klasy przy użyciu składni `Property="ClassName.Property"`. Na przykład zamiast ustawienie `Property="FontSize"`, należy ustawić <xref:System.Windows.Setter.Property%2A> do `"TextBlock.FontSize"` lub `"Control.FontSize"`.  
  
 Należy również zauważyć tak wielu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty składają się z kombinacji innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki. Jeśli tworzysz styl, który ma zastosowanie do wszystkich kontrolek typu, może uzyskać nieoczekiwane wyniki. Na przykład, jeśli Tworzenie stylu, którego celem <xref:System.Windows.Controls.TextBlock> wpisz <xref:System.Windows.Window>, styl jest stosowane do wszystkich <xref:System.Windows.Controls.TextBlock> formantów w oknie, nawet wtedy, gdy <xref:System.Windows.Controls.TextBlock> jest częścią innego formantu, takich jak <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Style i zasoby  
 Można użyć stylu w dowolnym elemencie, która jest pochodną <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Typowym sposobem zadeklarować styl jest jako zasób w `Resources` sekcji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, jak pokazano w poprzednich przykładach. Ponieważ zasoby są style, one przestrzegać tego samego zakresu zasady mające zastosowanie do wszystkich zasobów; gdzie można zadeklarować stylu wpływa na której można zastosować styl. Na przykład, jeśli zadeklarować style w elemencie głównym definicji aplikacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, styl mogą być używane w dowolnym miejscu w aplikacji. Po utworzeniu aplikacji nawigacji i deklaruje stylu w jednej z aplikacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, styl mogą być używane tylko w tym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji na temat zakresu reguł dla zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Ponadto można znaleźć więcej informacji na temat style i zasobów w [zasobów udostępnionych i kompozycji](#styling_themes) dalszej części tego przeglądu.  
  
### <a name="setting-styles-programmatically"></a>Ustawianie stylów programowo  
 Aby przypisać nazwanego stylu elementu programowo, pobiera styl z kolekcji zasobów i przypisz je do elementu <xref:System.Windows.FrameworkElement.Style%2A> właściwości. Należy pamiętać, że elementy w kolekcji zasobów są typu <xref:System.Object>. W związku z tym należy rzutować pobrane styl <xref:System.Windows.Style> przed przypisaniem go do <xref:System.Windows.FrameworkElement.Style%2A> właściwości. Na przykład, aby ustawić do zdefiniowanego `TitleText` stylów na <xref:System.Windows.Controls.TextBlock> o nazwie `textblock1`, wykonaj następujące czynności:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Należy pamiętać, że po zastosowaniu stylu jest zapieczętowany i nie można zmienić. Jeśli chcesz dynamicznie Zmień styl, które zostały już zastosowane, należy utworzyć nowego stylu, aby zastąpić istniejący. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style.IsSealed%2A> właściwości.  
  
 Można utworzyć obiektu, który wybiera stylu do zastosowania na podstawie niestandardowej logiki. Na przykład, zobacz przykład przewidzianych <xref:System.Windows.Controls.StyleSelector> klasy.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Powiązania, dynamiczne zasoby i procedury obsługi zdarzeń  
 Należy pamiętać, że można użyć `Setter.Value` właściwości w celu określenia [powiązanie — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) lub [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Aby uzyskać więcej informacji, zobacz przykłady podane dla <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> właściwości.  
  
 Do tej pory ten przegląd omówiono korzystanie z metody ustawiające można ustawić wartości właściwości. Można również określić procedury obsługi zdarzeń w stylu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Szablony danych  
 W tej przykładowej aplikacji, istnieje <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z listy zdjęć:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 To <xref:System.Windows.Controls.ListBox> obecnie wygląda podobnie do następującego:  
  
 ![ListBox przed zastosowaniem szablonu](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Większość formantów mieć pewien typ zawartości, a zawartość często pochodzi z danych, które są powiązanie z. W tym przykładzie dane są na liście zdjęcia. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], możesz użyć <xref:System.Windows.DataTemplate> do definiowania wizualną reprezentację danych. Zasadniczo, co należy umieścić w <xref:System.Windows.DataTemplate> określa wygląd danych w renderowanym aplikacji.  
  
 W naszym przykładowej aplikacji każdej niestandardowej `Photo` obiekt ma `Source` właściwości typu ciąg, który określa ścieżkę pliku obrazu. Obecnie fotografii obiekty są wyświetlane jako ścieżki do pliku.  
  
 Zdjęć, które były wyświetlane jako obrazy, można utworzyć <xref:System.Windows.DataTemplate> jako zasób:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Zwróć uwagę, że <xref:System.Windows.DataTemplate.DataType%2A> właściwości jest bardzo podobny do <xref:System.Windows.Style.TargetType%2A> właściwość <xref:System.Windows.Style>. Jeśli Twoje <xref:System.Windows.DataTemplate> znajduje się w sekcji zasobów w przypadku określenia <xref:System.Windows.DataTemplate.DataType%2A> właściwość do typu i przypisuje go `x:Key`, <xref:System.Windows.DataTemplate> jest stosowana, gdy pojawi się tego typu. Zawsze masz do niego przypisać <xref:System.Windows.DataTemplate> z `x:Key` , a następnie ustaw go jako `StaticResource` dla właściwości, które przyjmują <xref:System.Windows.DataTemplate> typy, takich jak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości lub <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
 Zasadniczo <xref:System.Windows.DataTemplate> w powyższym przykładzie definiuje który zawsze, gdy istnieje `Photo` obiektu, w jakiej powinny pojawić się jako <xref:System.Windows.Controls.Image> w <xref:System.Windows.Controls.Border>. Z tym <xref:System.Windows.DataTemplate>, naszą aplikację teraz wygląda następująco:  
  
 ![Obraz zdjęcie](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Model danych tworzenia szablonów udostępnia inne funkcje. Na przykład w przypadku wyświetlania danych kolekcji, które zawiera inne kolekcje przy użyciu <xref:System.Windows.Controls.HeaderedItemsControl> wpisz na przykład <xref:System.Windows.Controls.Menu> lub <xref:System.Windows.Controls.TreeView>, Brak <xref:System.Windows.HierarchicalDataTemplate>. Inna funkcja tworzenia szablonów danych jest <xref:System.Windows.Controls.DataTemplateSelector>, umożliwia wybór <xref:System.Windows.DataTemplate> do użycia na podstawie niestandardowej logiki. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md), która zapewnia bardziej szczegółowym omówieniem funkcji tworzenia szablonów innych danych.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Szablony formantu  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> formantu definiuje wygląd formantu. Struktura i wyglądu formantu można zmienić, definiując nowy <xref:System.Windows.Controls.ControlTemplate> dla formantu. W wielu przypadkach zapewnia elastyczność za mało, dzięki czemu nie trzeba zapisać Kontrolki niestandardowe. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Wyzwalacze  
 Wyzwalacz ustawia właściwości lub uruchamia akcji, takich jak animacji, gdy wartość właściwości zostanie zmieniona lub gdy zdarzenie jest wywoływane. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, i <xref:System.Windows.DataTemplate> mieć `Triggers` właściwość, która może zawierać zestaw wyzwalaczy. Istnieją różne typy wyzwalaczy.  
  
### <a name="property-triggers"></a>Wyzwalacze właściwości  
 A <xref:System.Windows.Trigger> czy właściwość zestawy wartości lub uruchamiania działania na podstawie wartości właściwości jest wywoływana wyzwalacza właściwości.  
  
 Aby zademonstrować sposób użycia właściwości wyzwalaczy, możesz wprowadzić każdego <xref:System.Windows.Controls.ListBoxItem> częściowo przezroczysty, chyba że jest zaznaczone. Ustawia styl następujące <xref:System.Windows.UIElement.Opacity%2A> wartość <xref:System.Windows.Controls.ListBoxItem> do `0.5`. Gdy <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> właściwość jest `true`, jednak <xref:System.Windows.UIElement.Opacity%2A> ma ustawioną wartość `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 W tym przykładzie użyto <xref:System.Windows.Trigger> można ustawić wartości właściwości, ale należy pamiętać, że <xref:System.Windows.Trigger> klasa ma również <xref:System.Windows.TriggerBase.EnterActions%2A> i <xref:System.Windows.TriggerBase.ExitActions%2A> właściwości umożliwiających wyzwalacz do wykonania akcji.  
  
 Zwróć uwagę, że <xref:System.Windows.FrameworkElement.MaxHeight%2A> właściwość <xref:System.Windows.Controls.ListBoxItem> ma ustawioną wartość `75`. Na poniższej ilustracji trzeci element jest zaznaczony element:  
  
 ![Styl elementu ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers i planów  
 Inny typ wyzwalacza to <xref:System.Windows.EventTrigger>, który uruchamia zestaw działań opartych na wystąpienie zdarzenia. Na przykład następująca <xref:System.Windows.EventTrigger> obiektów określić, że gdy wskaźnik myszy zostanie umieszczony <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> animuje właściwości na wartość `90` za pośrednictwem `0.2` drugi okres. Gdy wskaźnik myszy przesuwa się od elementu, właściwość zwraca wartość oryginalną w danym okresie `1` drugiego. Należy zwrócić uwagę, jak nie jest konieczne określić <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wartość <xref:System.Windows.ContentElement.MouseLeave> animacji. Jest to spowodowane animacji jest w stanie śledzić oryginalnej wartości.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Aby uzyskać więcej informacji, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Na poniższej ilustracji mysz wskazuje trzeci element:  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers i MultiDataTriggers  
 Oprócz <xref:System.Windows.Trigger> i <xref:System.Windows.EventTrigger>, występują inne typy wyzwalaczy. <xref:System.Windows.MultiTrigger>Służy do ustawiania wartości właściwości na podstawie wielu warunków. Możesz użyć <xref:System.Windows.DataTrigger> i <xref:System.Windows.MultiDataTrigger> gdy właściwość warunku jest powiązany z danymi.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Udostępnione zasoby i motywów  
 Typowe [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacje mogą mieć wiele zasobów interfejsu użytkownika, które są stosowane w całej aplikacji. Zbiorczo ten zestaw zasobów, jest uznawana za motyw dla aplikacji. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]zapewnia obsługę użytkownika pakowania zasoby interfejsu użytkownika jako motyw za pomocą słownika zasobów, która jest hermetyzowany jako <xref:System.Windows.ResourceDictionary> klasy.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Motywy są definiowane za pomocą mechanizmu stylami i tworzenia szablonów który [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] przedstawia dostosowywania wizualnych dowolnego elementu.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]motyw zasobów są przechowywane w słownikach zasobów osadzonych. Te słowniki zasobów musi być osadzony w zestawie podpisane i albo można osadzić w tym samym zestawie co kodu lub w zestawie side-by-side. W przypadku PresentationFramework.dll, zestawu, który zawiera [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] formantów, motyw zasoby są w serii side-by-side zestawów.  
  
 Staje się ostatnie miejsce do wyszukiwania przy wyszukiwaniu styl elementu. Zazwyczaj wyszukiwanie będzie rozpocząć przez krótki w górę drzewa element wyszukiwanie odpowiednich zasobów, a następnie Szukaj w kolekcji zasobów aplikacji i koniec wykonywanie zapytań względem systemu. Deweloperzy aplikacji daje możliwość ponownego zdefiniowania stylu dla dowolnego obiektu na poziomie drzewa lub aplikacji przed osiągnięciem motywu.  
  
 Słowniki zasobów można zdefiniować jako pojedyncze pliki, które umożliwiają ponownie wykorzystać motyw dla wielu aplikacji. Można również utworzyć swappable motywów przez zdefiniowanie wielu słowniki zasobów, które zapewniają te same typy zasobów, ale o różnych wartościach. Ponowne definiowanie te style oraz innych zasobów na poziomie aplikacji jest zalecane podejście do ujęć aplikacji.  
  
 Aby udostępnić zestaw zasobów, w tym w aplikacjach, style i szablony, można utworzyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików i zdefiniuj <xref:System.Windows.ResourceDictionary>. Na przykład Spójrz na poniższej ilustracji, który zawiera część [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041):  
  
 ![Kontrolowanie przykłady szablonu](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Jeśli przyjrzymy się [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki z przykładu, można zauważyć, że wszystkie pliki mają następujące:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Jest udostępnianie `shared.xaml`, który definiuje <xref:System.Windows.ResourceDictionary> zawierający zestaw zasobów, styl i pędzla umożliwiającą formantów w próbce będą wyglądały.  
  
 Aby uzyskać więcej informacji, zobacz [scalić słowniki zasobów](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Jeśli tworzysz motyw dla Ciebie kontrolki niestandardowej, zobacz sekcję zewnętrznej biblioteki kontroli [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Identyfikatory URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Porady: znajdowanie elementy wygenerowane ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Znajdź elementy generowane DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
