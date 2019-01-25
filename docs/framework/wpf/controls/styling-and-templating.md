---
title: Tworzenie szablonów i stylów
ms.date: 03/30/2017
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
ms.openlocfilehash: 8bd806d6b0d53d09cfca875f9f8fa844eb73ffdc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549720"
---
# <a name="styling-and-templating"></a>Tworzenie szablonów i stylów
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Tworzenie szablonów i stylów odnoszą się do zestawu funkcji (style, szablony, wyzwalaczy i scenorysów), które umożliwiają deweloperów i projektantów do tworzenia efektów wizualnie atrakcyjne i utworzyć spójny wygląd swojego produktu. Chociaż deweloperów i projektantów lub można dostosować wygląd często na podstawie aplikacji, aplikacji, silne modelu Tworzenie szablonów i stylów jest niezbędne w celu umożliwienia obsługi i udostępnianie pojawienia się wewnątrz i pomiędzy aplikacjami. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia tego modelu.  
  
 Kolejną funkcją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stylu modelu polega na rozdzieleniu prezentacji i logiki. Oznacza to, że projektantów można zmieniać wygląd aplikacji tylko przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tym samym czasie, który deweloperzy pracują na logice programowania przy użyciu C# lub Visual Basic.  
  
 W tym omówieniu koncentruje się na tworzenie szablonów i stylów aspektów aplikacji i nie omówiono w nim wszystkie powiązania pojęcia związane z danymi. Aby uzyskać informacji na temat wiązania danych, zobacz [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Ponadto ważne jest zrozumienie zasoby, które są co Włączanie stylów i szablonów, które mają być używane ponownie. Aby uzyskać więcej informacji na temat zasobów, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Przykładowych szablonów i stylów  
 Przykłady kodu, używany w tym omówieniu opierają się na przykład proste zdjęcie pokazano na poniższej ilustracji:  
  
 ![Różne ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 W tym przykładzie prostego zdjęcie używa Tworzenie szablonów i stylów w celu utworzenia atrakcyjnych wizualnie środowiska użytkownika. Przykład ma dwa <xref:System.Windows.Controls.TextBlock> elementy i <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z listy obrazów. Aby uzyskać pełny przykład, zobacz [wprowadzenie do przykładowych szablonów i stylów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Podstawowe informacje dotyczące stylu  
 Można potraktować <xref:System.Windows.Style> to wygodny sposób, aby zastosować zestaw wartości właściwości do więcej niż jeden element. Na przykład, należy wziąć pod uwagę następujące <xref:System.Windows.Controls.TextBlock> elementów i ich wygląd domyślny:  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Domyślny wygląd można zmienić przez ustawienie właściwości, takie jak <xref:System.Windows.Controls.Control.FontSize%2A> i <xref:System.Windows.Controls.Control.FontFamily%2A>, na każdym <xref:System.Windows.Controls.TextBlock> element bezpośrednio. Jednak jeśli chcesz, aby Twoje <xref:System.Windows.Controls.TextBlock> elementy, aby udostępnić niektóre właściwości, można utworzyć <xref:System.Windows.Style> w `Resources` części usługi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Po ustawieniu <xref:System.Windows.Style.TargetType%2A> z własnego stylu do <xref:System.Windows.Controls.TextBlock> typu, stylu jest stosowane do wszystkich <xref:System.Windows.Controls.TextBlock> elementy w oknie.  
  
 Teraz <xref:System.Windows.Controls.TextBlock> elementy pojawiają się w następujący sposób:  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Rozszerzanie style  
 Chcecie Twojego dwu <xref:System.Windows.Controls.TextBlock> elementy, które udostępniają niektóre wartości właściwości, takie jak <xref:System.Windows.Controls.Control.FontFamily%2A> i wyśrodkowany <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ale ma również tekst "Moje obrazy", aby niektóre dodatkowe właściwości. Możesz to zrobić, tworząc nowy styl, który opiera się na pierwszy stylu, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Należy zauważyć, że jest podany w poprzednim stylu `x:Key`. Aby zastosować styl, należy ustawić <xref:System.Windows.FrameworkElement.Style%2A> właściwość swoje <xref:System.Windows.Controls.TextBlock> do `x:Key` wartość, jak pokazano poniżej:  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 To <xref:System.Windows.Controls.TextBlock> styl ma teraz <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> wartość <xref:System.Windows.HorizontalAlignment.Center>, <xref:System.Windows.Controls.TextBlock.FontFamily%2A> wartość `Comic Sans MS`, <xref:System.Windows.Controls.TextBlock.FontSize%2A> wartość 26, a <xref:System.Windows.Controls.TextBlock.Foreground%2A> wartość <xref:System.Windows.Media.LinearGradientBrush> pokazano w przykładzie. Należy zauważyć, że zastępuje ona <xref:System.Windows.Controls.Control.FontSize%2A> wartość stylu bazowego. Jeśli istnieje więcej niż jedna <xref:System.Windows.Setter> ustawienie tej właściwości w <xref:System.Windows.Style>, <xref:System.Windows.Setter> czyli zadeklarowane ostatni ma pierwszeństwo.  
  
 Poniżej pokazano, co <xref:System.Windows.Controls.TextBlock> elementy teraz wyglądać podobnie jak:  
  
 ![Styled TextBlocks](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 To `TitleText` styl rozszerza styl, który został utworzony dla <xref:System.Windows.Controls.TextBlock> typu. Można także rozszerzyć styl, który ma `x:Key` przy użyciu `x:Key` wartość. Aby uzyskać przykład, zobacz przykładu przewidzianego dla <xref:System.Windows.Style.BasedOn%2A> właściwości.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relacja właściwości TargetType i x: Key — atrybut  
 Jak pokazano w przykładzie pierwsze, ustawienie <xref:System.Windows.Style.TargetType%2A> właściwości `TextBlock` bez przypisywania styl `x:Key` powoduje, że style, które mają być stosowane do wszystkich <xref:System.Windows.Controls.TextBlock> elementów. W tym przypadku `x:Key` niejawnie ustawiono `{x:Type TextBlock}`. Oznacza to, że jeśli jawnie ustawić `x:Key` wartość do żadnego elementu innego niż `{x:Type TextBlock}`, <xref:System.Windows.Style> nie ma zastosowania do wszystkich <xref:System.Windows.Controls.TextBlock> elementy automatycznie. Zamiast tego należy najpierw zastosować styl (przy użyciu `x:Key` wartości) do <xref:System.Windows.Controls.TextBlock> elementów jawnie. Jeśli własnego stylu znajduje się w sekcji zasobów i nie należy ustawiać <xref:System.Windows.Style.TargetType%2A> właściwość własnego stylu, należy podać `x:Key`.  
  
 Oprócz zapewniania wartość domyślną dla `x:Key`, <xref:System.Windows.Style.TargetType%2A> właściwość określa typ, do którego odnoszą się właściwości metody ustawiającej. Jeśli nie określisz <xref:System.Windows.Style.TargetType%2A>, musi kwalifikować się do właściwości w swojej <xref:System.Windows.Setter> obiektów o nazwie klasy przy użyciu składni `Property="ClassName.Property"`. Na przykład, zamiast ustawiać `Property="FontSize"`, należy ustawić <xref:System.Windows.Setter.Property%2A> do `"TextBlock.FontSize"` lub `"Control.FontSize"`.  
  
 Należy również zauważyć tę liczbę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantów składają się z kombinacji innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki. Jeśli tworzysz styl, który ma zastosowanie do wszystkich kontrolek typu, możesz otrzymać nieoczekiwane wyniki. Na przykład, jeśli tworzysz styl przeznaczonego <xref:System.Windows.Controls.TextBlock> wpisać <xref:System.Windows.Window>, styl jest stosowane do wszystkich <xref:System.Windows.Controls.TextBlock> formantów w oknie nawet wtedy, gdy <xref:System.Windows.Controls.TextBlock> jest częścią innej kontrolki, takie jak <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Style i zasoby  
 Można używać stylu dowolnego elementu, która pochodzi od klasy <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Najczęstszym sposobem zadeklarować stylu jest jako zasób w `Resources` sekcji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, jak pokazano w poprzednich przykładach. Ponieważ style są zasoby, przestrzegają one te same reguły określania zakresu, które są stosowane do wszystkich zasobów; gdy Deklarujesz stylu wpływa na której można zastosować styl. Na przykład, jeśli zadeklarować stylu w elemencie głównym definicji aplikacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku styl mogą być używane w dowolnym miejscu w aplikacji. Po utworzeniu aplikacji nawigacji i zadeklarować stylu w jednej aplikacji [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, styl mogą być używane tylko w tym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku. Aby uzyskać więcej informacji na temat określania zakresu reguły dla zasobów, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Ponadto można znaleźć więcej informacji na temat — style i zasobów w [udostępnionych zasobów i motywów](#styling_themes) później w tym omówieniu.  
  
### <a name="setting-styles-programmatically"></a>Programowe Ustawianie stylów  
 Aby przypisać stylu nazwanego elementu programowo, pobiera styl z kolekcji zasobów i przypisać je do elementu <xref:System.Windows.FrameworkElement.Style%2A> właściwości. Należy zauważyć, że elementy w kolekcji zasobów są typu <xref:System.Object>. W związku z tym, należy rzutować pobrane styl <xref:System.Windows.Style> przed przypisaniem go do <xref:System.Windows.FrameworkElement.Style%2A> właściwości. Na przykład, aby ustawić zdefiniowane `TitleText` stylu na <xref:System.Windows.Controls.TextBlock> o nazwie `textblock1`, wykonaj następujące czynności:  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Należy pamiętać, że po zastosowaniu stylu jest zapieczętowany i nie można jej zmienić. Jeśli chcesz dynamicznie zmieniać style, która już została zastosowana, należy utworzyć nowy styl, aby zamienić istniejący. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style.IsSealed%2A> właściwości.  
  
 Można utworzyć obiekt, który wybiera styl do zastosowania na podstawie logiki niestandardowej. Aby uzyskać przykład, zobacz przykładu przewidzianego dla <xref:System.Windows.Controls.StyleSelector> klasy.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Powiązania, dynamiczne zasoby i procedury obsługi zdarzeń  
 Należy zauważyć, że można użyć `Setter.Value` właściwości w celu określenia [— rozszerzenie znaczników powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) lub [dynamicresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Aby uzyskać więcej informacji, zobacz przykłady związane z <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> właściwości.  
  
 Do tej pory to omówienie dotyczy użycia metod ustawiających można ustawić wartości właściwości. Można również określić procedury obsługi zdarzeń w stylu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Szablony danych  
 W tej przykładowej aplikacji znajduje się <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z zdjęcia z listy:  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 To <xref:System.Windows.Controls.ListBox> obecnie wygląda podobnie do następującego:  
  
 ![ListBox — przed zastosowaniem szablonu](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 Większość formantów ma jakiegoś rodzaju zawartości i zawartości często pochodzi z danych, które dokonywane jest wiązanie. W tym przykładzie dane są listy zdjęcia. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], możesz użyć <xref:System.Windows.DataTemplate> do definiowania wizualne reprezentacje danych. Zasadniczo, jakie można umieścić w <xref:System.Windows.DataTemplate> Określa, jak wygląda dane w renderowanym aplikacji.  
  
 W naszej przykładowej aplikacji każdego `Photo` obiekt ma `Source` właściwości typu ciąg, który określa ścieżkę pliku obrazu. Obecnie obiekty zdjęcie są wyświetlane jako ścieżki pliku.  
  
 Zdjęcia są wyświetlane jako obrazy, tworzy się <xref:System.Windows.DataTemplate> jako zasób:  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Należy zauważyć, że <xref:System.Windows.DataTemplate.DataType%2A> właściwość jest bardzo podobny do <xref:System.Windows.Style.TargetType%2A> właściwość <xref:System.Windows.Style>. Jeśli Twoje <xref:System.Windows.DataTemplate> znajduje się w sekcji zasobów, podczas określania <xref:System.Windows.DataTemplate.DataType%2A> właściwość do typu i przypisuje go `x:Key`, <xref:System.Windows.DataTemplate> są stosowane zawsze, gdy typ ten pojawia się. Zawsze istnieje możliwość przypisania <xref:System.Windows.DataTemplate> z `x:Key` i ustawić ją jako `StaticResource` dla właściwości, które przyjmują <xref:System.Windows.DataTemplate> typów, takich jak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości lub <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
 Zasadniczo <xref:System.Windows.DataTemplate> w powyższym przykładzie definiuje, zawsze, gdy występuje `Photo` obiektów i będzie widoczny jako <xref:System.Windows.Controls.Image> w ramach <xref:System.Windows.Controls.Border>. Dzięki temu <xref:System.Windows.DataTemplate>, obecnie nasza aplikacja wygląda w następujący sposób:  
  
 ![Obraz zdjęcia](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Model szablonowanie danych udostępnia inne funkcje. Na przykład w przypadku wyświetlania danych kolekcji, który zawiera inne kolekcje przy użyciu <xref:System.Windows.Controls.HeaderedItemsControl> wpisz na przykład <xref:System.Windows.Controls.Menu> lub <xref:System.Windows.Controls.TreeView>, Brak <xref:System.Windows.HierarchicalDataTemplate>. Kolejną funkcją szablonowanie danych jest <xref:System.Windows.Controls.DataTemplateSelector>, co pozwala na wybór <xref:System.Windows.DataTemplate> do użycia na podstawie logiki niestandardowej. Aby uzyskać więcej informacji, zobacz [Przegląd Szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md), który zapewnia bardziej szczegółowym omówieniem funkcji szablonów innych danych.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Szablony kontrolek  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.ControlTemplate> kontrolki definiuje wygląd formantu. Możesz zmienić strukturę i wyglądu formantu, definiując nowe <xref:System.Windows.Controls.ControlTemplate> dla formantu. W wielu przypadkach daje dostateczną elastyczność, tak aby nie trzeba napisać własne niestandardowe formanty. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Wyzwalacze  
 Wyzwalacz ustawia właściwości lub uruchamia akcje, takie jak animacji, po zmianie wartości właściwości lub gdy zostanie wywołane zdarzenie. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, i <xref:System.Windows.DataTemplate> wszystkie mają `Triggers` właściwość, która może zawierać zestaw wyzwalaczy. Istnieją różne typy wyzwalaczy.  
  
### <a name="property-triggers"></a>Wyzwalacze właściwości  
 A <xref:System.Windows.Trigger> , ustawia właściwość wartości lub uruchamia akcje na podstawie wartości właściwości nosi nazwę wyzwalacza właściwości.  
  
 Aby pokazują, jak użyć wyzwalaczy właściwości, należy wybrać każdy <xref:System.Windows.Controls.ListBoxItem> częściowo przezroczyste, chyba że jest zaznaczona. Następujące stylów ustawia <xref:System.Windows.UIElement.Opacity%2A> wartość <xref:System.Windows.Controls.ListBoxItem> do `0.5`. Gdy <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> właściwość `true`, jednak <xref:System.Windows.UIElement.Opacity%2A> ustawiono `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 W tym przykładzie użyto <xref:System.Windows.Trigger> można ustawić wartości właściwości, ale należy pamiętać, że <xref:System.Windows.Trigger> ma również klasy <xref:System.Windows.TriggerBase.EnterActions%2A> i <xref:System.Windows.TriggerBase.ExitActions%2A> właściwości, które umożliwiają wyzwalacza do wykonania akcji.  
  
 Należy zauważyć, że <xref:System.Windows.FrameworkElement.MaxHeight%2A> właściwość <xref:System.Windows.Controls.ListBoxItem> ustawiono `75`. Na poniższej ilustracji trzeci element jest zaznaczony element:  
  
 ![Różne ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers i scenorysów  
 Inny typ wyzwalacza to <xref:System.Windows.EventTrigger>, co spowoduje włączenie działań w oparciu o wystąpienie zdarzenia. Na przykład następująca <xref:System.Windows.EventTrigger> obiektów określić, że po umieszczeniu wskaźnika myszy <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> właściwość animuje wartości `90` za pośrednictwem `0.2` drugi okres. Gdy wskaźnik myszy porusza się od elementu, właściwości zwracają wartość oryginalną w okresie `1` drugiego. Należy pamiętać, jak nie trzeba określać <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wartość <xref:System.Windows.ContentElement.MouseLeave> animacji. Jest to spowodowane animacji jest w stanie śledzić oryginalną wartość.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Na poniższej ilustracji wskazuje myszą trzeci element:  
  
 ![Zrzut ekranu przedstawiający przykładowy stylów](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers DataTriggers i MultiDataTriggers  
 Oprócz <xref:System.Windows.Trigger> i <xref:System.Windows.EventTrigger>, istnieją inne typy wyzwalaczy. <xref:System.Windows.MultiTrigger> Umożliwia ustawienie wartości właściwości, na podstawie wielu warunków. Możesz użyć <xref:System.Windows.DataTrigger> i <xref:System.Windows.MultiDataTrigger> po właściwości warunku jest powiązany z danymi.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Udostępnione zasoby i motywów  
 Typowa aplikacja Windows Presentation Foundation (WPF) może mieć wiele zasobów interfejsu użytkownika, które są stosowane w całej aplikacji. Zbiorczo ten zestaw zasobów, jest uznawana za motywu dla aplikacji. Windows Presentation Foundation (WPF) zapewnia obsługę dla użytkowników pakietu zasobów interfejsu jako motyw przy użyciu słownik zasobów, które są hermetyzowane jako <xref:System.Windows.ResourceDictionary> klasy.  
  
 Motywy Windows Presentation Foundation (WPF) są definiowane za pomocą Windows Presentation Foundation (WPF) udostępnia mechanizm tworzenia szablonów i stylów dostosowywania wizualizacji dowolnego elementu.  
  
 Zasoby motyw Windows Presentation Foundation (WPF) są przechowywane w słownikach zasobów osadzonych. Te słowniki zasobów muszą być osadzone w zestawie podpisane i albo można osadzić w tym samym zestawie, co sam kod lub zestawów side-by-side. W przypadku PresentationFramework.dll i zestawu, który zawiera formanty Windows Presentation Foundation (WPF), motyw zasoby znajdują się w serii zestawów side-by-side.  
  
 Staje się ostatnie miejsce do wyszukiwania podczas wyszukiwania dla stylu elementu. Zazwyczaj wyszukiwania zostanie najpierw zalet w górę drzewa elementów, wyszukiwanie odpowiedni zasób, a następnie Szukaj w kolekcji zasobów aplikacji, a na koniec zapytania względem systemu. Deweloperzy aplikacji daje szansę na nowo zdefiniować stylu dla dowolnego obiektu na poziomie drzewa lub aplikacji przed osiągnięciem motywu.  
  
 Słowniki zasobów można zdefiniować jako pojedyncze pliki, które umożliwiają użytkownikowi ponowne używanie motywu dla wielu aplikacji. Można również utworzyć motywy swappable przez zdefiniowanie wielu słowniki zasobów, które udostępniają te same typy zasobów, ale z różnymi wartościami. Zmiana definicji tych stylów i innych zasobów na poziomie aplikacji jest zalecane podejście do powłoka aplikacji.  
  
 Aby udostępnić zestaw zasobów, w tym w aplikacjach, style i szablony, można utworzyć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików i definiowania <xref:System.Windows.ResourceDictionary>. Na przykład Przyjrzyj się poniższej ilustracji, który zawiera część [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating):

![Kontrolowanie przykłady szablonów](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Jeśli przyjrzymy się [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki z przykładu, można zauważyć, że wszystkie pliki mają następujące czynności:  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 Jest udostępnianie `shared.xaml`, która definiuje <xref:System.Windows.ResourceDictionary> zawierający zestaw zasobów, styl i pędzla, umożliwiająca kontrolek w przykładzie, aby miał jednolity wygląd.  
  
 Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Jeśli tworzysz motywu dla Ciebie kontrolki niestandardowej, zobacz sekcję biblioteki zewnętrznej kontroli [omówienie tworzenia kontrolek](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
- [Instrukcje: Find ControlTemplate-Generated Elements](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
