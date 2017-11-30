---
title: "Przegląd Szablonowanie danych"
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
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 91ab838ec543e2cc17e380ee9ec0d629989a003e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-templating-overview"></a>Przegląd Szablonowanie danych
Model tworzenia szablonów danych WPF zapewnia dużą elastyczność w celu zdefiniowania prezentacja danych. Formantów WPF ma wbudowaną funkcję obsługi dostosowywania prezentacji danych. W tym temacie przedstawiono najpierw sposób definiowania <xref:System.Windows.DataTemplate> , a następnie wprowadza inne funkcje tworzenia szablonów danych, takie jak wyboru szablonów na podstawie niestandardowej logiki i obsługę wyświetlania danych hierarchicznej.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie skupiono się na funkcji tworzenia szablonów danych i nie jest wprowadzenie pojęcia dotyczące powiązania danych. Informacje o pojęciach powiązania danych podstawowych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>jest prezentacji danych i jeden z wielu funkcje oferowane przez model stylami i tworzenia szablonów WPF. Wprowadzenie WPF stylami i tworzenia szablonów modelu, np. sposób użycia <xref:System.Windows.Style> można ustawić właściwości formantów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md) tematu.  
  
 Ponadto jest ważne zrozumieć `Resources`, które są zasadniczo obiektów co włączyć takie jak <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> się do ponownego użycia. Aby uzyskać więcej informacji dotyczących zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Podstawowe informacje dotyczące tworzenia szablonów danych  
  
 Aby zademonstrować Dlaczego <xref:System.Windows.DataTemplate> jest ważne, Przejdźmy przykład powiązania danych. W tym przykładzie mamy <xref:System.Windows.Controls.ListBox> który jest powiązany z listą `Task` obiektów. Każdy `Task` obiekt ma `TaskName` (ciąg), `Description` (ciąg), `Priority` (int) i właściwość typu `TaskType`, która jest `Enum` z wartościami `Home` i `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez DataTemplate  
 Bez <xref:System.Windows.DataTemplate>, naszych <xref:System.Windows.Controls.ListBox> obecnie wygląda podobnie do następującej:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Dzieje się to, co oznacza, że bez żadnych specjalnych instrukcji <xref:System.Windows.Controls.ListBox> przez domyślny wywołania `ToString` podczas próby wyświetlenia obiektów w kolekcji. W związku z tym jeśli `Task` obiekt zastąpienia `ToString` metody, a następnie <xref:System.Windows.Controls.ListBox> Wyświetla reprezentację ciągu każdego obiektu źródłowego w źródłowej kolekcji.  
  
 Na przykład jeśli `Task` klasy zastąpienia `ToString` metody w ten sposób gdzie `name` to pole dla `TaskName` właściwości:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Następnie przy użyciu <xref:System.Windows.Controls.ListBox> wygląda podobnie do następującego:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Jednak to ograniczająca i sztywne. Ponadto są wiązane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, nie można zastąpić `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definiowanie DataTemplate proste  
 Rozwiązanie jest określenie <xref:System.Windows.DataTemplate>. Jedną z metod w tym celu jest skonfigurowanie <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwość <xref:System.Windows.Controls.ListBox> do <xref:System.Windows.DataTemplate>. Określ w Twojej <xref:System.Windows.DataTemplate> staje się visual strukturę obiektu danych. Następujące <xref:System.Windows.DataTemplate> jest dość proste. Udostępniamy możliwość sprawowania instrukcje, które pojawia się jako trzy <xref:System.Windows.Controls.TextBlock> elementów w obrębie <xref:System.Windows.Controls.StackPanel>. Każdy <xref:System.Windows.Controls.TextBlock> elementu jest powiązany z właściwością `Task` klasy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Przykłady w tym temacie danych to kolekcja [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów. Są wiązane [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, podstawowe pojęcia są takie same, ale istnieje niewielka różnica składni. Na przykład zamiast `Path=TaskName`, należy ustawić <xref:System.Windows.Data.Binding.XPath%2A> do `@TaskName` (Jeśli `TaskName` jest atrybutem Twojej [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] węzła).  
  
 Teraz naszych <xref:System.Windows.Controls.ListBox> wygląda podobnie do następującego:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Tworzenie DataTemplate jako zasób  
 W powyższym przykładzie zdefiniowanego <xref:System.Windows.DataTemplate> wbudowanego. Jest to częściej można zdefiniować w sekcji zasobów, dlatego może być obiekt wielokrotnego użytku, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Teraz można używać `myTaskTemplate` jako zasób, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Ponieważ `myTaskTemplate` jest zasobem, można go teraz używać na inne formanty, które mają właściwości, która przyjmuje <xref:System.Windows.DataTemplate> typu. Jak pokazano powyżej, aby uzyskać <xref:System.Windows.Controls.ItemsControl> obiekty, takie jak <xref:System.Windows.Controls.ListBox>, jest <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości. Aby uzyskać <xref:System.Windows.Controls.ContentControl> obiektów jest <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Właściwość DataType  
 <xref:System.Windows.DataTemplate> Klasa ma <xref:System.Windows.DataTemplate.DataType%2A> właściwość, która jest bardzo podobny do <xref:System.Windows.Style.TargetType%2A> właściwość <xref:System.Windows.Style> klasy. Dlatego zamiast określania `x:Key` dla <xref:System.Windows.DataTemplate> w powyższym przykładzie można wykonaj następujące czynności:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 To <xref:System.Windows.DataTemplate> pobiera automatycznie stosowane do wszystkich `Task` obiektów. Należy pamiętać, że w takim przypadku `x:Key` jest ustawiane niejawnie. W związku z tym po przypisaniu to <xref:System.Windows.DataTemplate> `x:Key` wartości, są zastępowanie niejawne `x:Key` i <xref:System.Windows.DataTemplate> nie będą stosowane automatycznie.  
  
 Są wiązane <xref:System.Windows.Controls.ContentControl> do kolekcji `Task` obiektów, <xref:System.Windows.Controls.ContentControl> nie korzysta z powyższych <xref:System.Windows.DataTemplate> automatycznie. Jest to spowodowane powiązania w <xref:System.Windows.Controls.ContentControl> potrzebuje dodatkowych informacji w celu rozróżnienia czy chcesz powiązać całą kolekcję lub pojedyncze obiekty. Jeśli Twoje <xref:System.Windows.Controls.ContentControl> służy do śledzenia wybór <xref:System.Windows.Controls.ItemsControl> typu, możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Controls.ContentControl> powiązanie z "`/`" Aby wskazać, że jesteś zainteresowany w bieżącym elemencie. Na przykład zobacz [powiązania w kolekcji i wyświetlania informacji na podstawie zaznaczenia](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). W przeciwnym razie należy określić <xref:System.Windows.DataTemplate> jawnie ustawiając <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
 <xref:System.Windows.DataTemplate.DataType%2A> Właściwości jest szczególnie przydatne w przypadku <xref:System.Windows.Data.CompositeCollection> różnych typów obiektów danych. Na przykład zobacz [zaimplementować kolekcja CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Dodawanie więcej do DataTemplate  
 Obecnie dane są wyświetlane z niezbędnymi informacjami, ale ostatecznie jest udoskonalić. Ta funkcja pozwala poprawić na prezentacji, dodając <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>i niektóre <xref:System.Windows.Controls.TextBlock> elementy, które opisują danych, który jest wyświetlany.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Poniższy zrzut ekranu przedstawia <xref:System.Windows.Controls.ListBox> z tym zmodyfikowane <xref:System.Windows.DataTemplate>:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Firma Microsoft może ustawić <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> do <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox> się upewnić, że szerokość elementy zajmuje całe miejsce:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Z <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ustawioną właściwość <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> teraz wygląda podobnie do następującej:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Umożliwia zastosowanie wartości właściwości DataTriggers  
 Bieżącej prezentacji nie Powiedz nam czy `Task` jest macierzystego zadania lub pakietu office. Należy pamiętać, że `Task` obiekt ma `TaskType` właściwości typu `TaskType`, która jest wyliczenie z wartościami `Home` i `Work`.  
  
 W poniższym przykładzie <xref:System.Windows.DataTrigger> ustawia <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu o nazwie `border` do `Yellow` Jeśli `TaskType` jest właściwość `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Teraz naszej aplikacji wygląda następująco. Macierzysty zadania są wyświetlane z żółtym obramowania i office zadania są wyświetlane z Akwamaryna obramowania:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 W tym przykładzie <xref:System.Windows.DataTrigger> używa <xref:System.Windows.Setter> można ustawić wartości właściwości. Klasy wyzwalacza również mieć <xref:System.Windows.TriggerBase.EnterActions%2A> i <xref:System.Windows.TriggerBase.ExitActions%2A> właściwości, które umożliwiają uruchomienie zbiór akcji, takich jak animacji. Ponadto istnieje również <xref:System.Windows.MultiDataTrigger> klasy, która pozwala na zastosowanie zmian na podstawie wielu właściwości powiązanych z danymi wartości.  
  
 To alternatywny sposób osiągnąć ten sam efekt można powiązać <xref:System.Windows.Controls.Border.BorderBrush%2A> właściwości `TaskType` właściwości i użycia konwertera wartości do zwrócenia kolor na podstawie `TaskType` wartości. Tworzenie za pomocą konwertera celowi jest nieco bardziej efektywne pod względem wydajności. Ponadto tworzenie własnych konwertera zapewnia większą elastyczność, ponieważ są dostarczanie własną logikę. Ostatecznie techniki wybierzesz zależy od danego scenariusza i swoich preferencji. Aby dowiedzieć się, jak napisać konwerter, zobacz <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co należy w szablonie danych?  
 W poprzednim przykładzie, możemy umieścić wyzwalacza w <xref:System.Windows.DataTemplate> przy użyciu <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> właściwości. <xref:System.Windows.Setter> Wyzwalacza ustawia wartości właściwości elementu ( <xref:System.Windows.Controls.Border> element) znajduje się w <xref:System.Windows.DataTemplate>. Jednak jeśli właściwości który Twojej `Setters` dotyczy nie są właściwościami elementów, które znajdują się w bieżącej <xref:System.Windows.DataTemplate>, może być odpowiedniejsze można ustawić właściwości, za pomocą <xref:System.Windows.Style> to <xref:System.Windows.Controls.ListBoxItem> klasy (Jeśli jest to powiązania kontrolki — <xref:System.Windows.Controls.ListBox>). Na przykład, jeśli chcesz z <xref:System.Windows.Trigger> do animowania <xref:System.Windows.UIElement.Opacity%2A> wartości elementu, gdy wskaźnik myszy wskazuje element zdefiniujesz Wyzwalacze w ramach <xref:System.Windows.Controls.ListBoxItem> stylu. Na przykład zobacz [wprowadzenie do stylów i tworzenia szablonów przykładowa](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
 Ogólnie rzecz biorąc, należy pamiętać, że <xref:System.Windows.DataTemplate> są stosowane do każdego z wygenerowany <xref:System.Windows.Controls.ListBoxItem> (Aby uzyskać więcej informacji na temat jak i gdzie faktycznie jest stosowane, zobacz <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> strony.). Twoje <xref:System.Windows.DataTemplate> dotyczy tylko z prezentacji i wyglądu obiektów danych. W większości przypadków wszystkie aspekty prezentacji, takie jak jakie elementu wygląda po zaznaczeniu lub jak <xref:System.Windows.Controls.ListBox> określa elementy, nie należą do definicji <xref:System.Windows.DataTemplate>. Na przykład zobacz [stylami i tworzenia szablonów ItemsControl](#DataTemplating_ItemsControl) sekcji.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Wybieranie DataTemplate, na podstawie właściwości obiektu danych  
 W [Właściwość DataType](#Styling_DataType) sekcji omówiono zdefiniować szablony różnych danych dla różnych danych obiektów. Jest szczególnie przydatne, jeśli masz <xref:System.Windows.Data.CompositeCollection> różnych typów lub kolekcji z elementów o różnych typach. W [Użyj DataTriggers się wartości właściwości](#DataTrigger_to_Apply_Property_Values) sekcji, firma Microsoft wykazały, że mając kolekcji tego samego typu obiektów danych można utworzyć <xref:System.Windows.DataTemplate> , a następnie użyj wyzwalaczy, aby zastosować zmiany na podstawie wartości właściwości Każdy obiekt danych. Jednak wyzwalacze pozwalają na stosowanie wartości właściwości lub uruchomić animacji, ale ich nie zapewniają elastyczność odtworzenie struktury obiektów danych. Niektóre scenariusze mogą wymagać utworzyć inną <xref:System.Windows.DataTemplate> danych obiektów, które są tego samego typu, ale ma inne właściwości.  
  
 Na przykład, jeśli `Task` obiekt ma `Priority` wartość `1`, warto nadać mu dwóch zupełnie różnych wygląd służyć jako alert dla siebie. W takim przypadku utworzysz <xref:System.Windows.DataTemplate> wyświetlania o wysokim priorytecie `Task` obiektów. Dodajmy następujące <xref:System.Windows.DataTemplate> do sekcji zasobów:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Zwróć uwagę, w tym przykładzie użyto <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> właściwości. Zasoby zdefiniowane w tej sekcji są współużytkowane przez elementy wewnątrz <xref:System.Windows.DataTemplate>.  
  
 Umożliwiają określanie logiki, aby wybrać <xref:System.Windows.DataTemplate> do użycia na podstawie `Priority` wartość obiektu danych, Utwórz podklasę <xref:System.Windows.Controls.DataTemplateSelector> i zastąpić <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metody. W poniższym przykładzie <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda zawiera logikę do zwrócenia odpowiedni szablon na podstawie wartości z `Priority` właściwości. Szablon do zwrócenia zostanie znaleziony w zasobów obejmujące <xref:System.Windows.Window> elementu.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Firma Microsoft może następnie zadeklarować `TaskListDataTemplateSelector` jako zasób:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Aby korzystać z zasobów selektor szablonu, przypisz go do <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> właściwość <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> Wywołania <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metody `TaskListDataTemplateSelector` dla poszczególnych elementów w źródłowej kolekcji. Wywołanie przekazuje obiekt danych jako parametru elementu. <xref:System.Windows.DataTemplate> Zwracany przez metodę jest następnie stosowany do tego obiektu danych.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Z selektorem szablonu w miejscu <xref:System.Windows.Controls.ListBox> pojawi się teraz w następujący sposób:  
  
 ![Zrzut ekranu przedstawiający przykład tworzenia szablonów danych](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  
  
 Zakończenie naszych dyskusji w tym przykładzie. Pełny przykład, zobacz [wprowadzenie do danych przykładowych tworzenia szablonów](http://go.microsoft.com/fwlink/?LinkID=160009).  
  
<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Style i tworzenia szablonów ItemsControl  
 Mimo że <xref:System.Windows.Controls.ItemsControl> nie jest tylko typ formantu, który można użyć <xref:System.Windows.DataTemplate> , jest to bardzo typowy scenariusz, aby powiązać <xref:System.Windows.Controls.ItemsControl> do kolekcji. W [co należy w szablonie danych](#what_belongs_in_datatemplate) sekcji omówiono który definicji z <xref:System.Windows.DataTemplate> powinien mieć tylko dane z prezentacji danych. Aby dowiedzieć się, gdy nie nadaje się do użycia <xref:System.Windows.DataTemplate> ważne jest, aby poznać inne właściwości stylu i szablon udostępniane przez <xref:System.Windows.Controls.ItemsControl>. Poniższy przykład zaprojektowano w celu zilustrowania funkcja każdego z tych właściwości. <xref:System.Windows.Controls.ItemsControl> w tym przykładzie jest powiązana do tej samej `Tasks` kolekcji, co w poprzednim przykładzie. Pokaz celów, style i szablony, w tym przykładzie są wszystkie zadeklarowane w wierszach.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Poniżej przedstawiono zrzut ekranu przykładu, gdy jest on renderowany:  
  
 ![Zrzut ekranu ItemsControl](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Należy pamiętać, że zamiast <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, można użyć <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Zapoznaj się z poprzedniej sekcji, na przykład. Podobnie, zamiast <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, istnieje możliwość użycia <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Dwa inne powiązane styl właściwości <xref:System.Windows.Controls.ItemsControl> które nie są wyświetlane tutaj są <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> i <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Obsługa danych hierarchicznych  
 Do tej pory mają tylko Analizujemy sposób powiązania i wyświetlania jednej kolekcji. Czasami masz kolekcję, która zawiera inne kolekcje. <xref:System.Windows.HierarchicalDataTemplate> Klasy jest przeznaczony do użycia z <xref:System.Windows.Controls.HeaderedItemsControl> typów do wyświetlania tych danych. W poniższym przykładzie `ListLeagueList` znajduje się lista `League` obiektów. Każdy `League` obiekt ma `Name` i Kolekcja `Division` obiektów. Każdy `Division` ma `Name` i Kolekcja `Team` obiektów, a każdy `Team` obiekt ma `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 W przykładzie pokazano, że podczas korzystania z <xref:System.Windows.HierarchicalDataTemplate>, można łatwo wyświetlić dane listy, który zawiera inne listy. Poniżej przedstawiono zrzut ekranu przykładu.  
  
 ![Zrzut ekranu przedstawiający przykładowy obiekt HierarchicalDataTemplate przykład](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Znajdź elementy generowane DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Przegląd szablonów i styl nagłówka kolumny w widoku GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)
