---
title: Przegląd Szablonowanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 58d723ccf86e4195674c132f9fb1b76f689f57b2
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055342"
---
# <a name="data-templating-overview"></a>Przegląd Szablonowanie danych
Model szablonowanie danych WPF zapewnia dużą elastyczność, aby zdefiniować prezentację danych. Formanty WPF posiada wbudowanej funkcji obsługującej Dostosowywanie prezentacji danych. W tym temacie najpierw pokazano, jak zdefiniować <xref:System.Windows.DataTemplate> i następnie wprowadza inne funkcje szablonów dane, takie jak wybór szablony na podstawie logiki niestandardowej i pomoc techniczna dotycząca wyświetlania danych hierarchicznych.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten temat koncentruje się na funkcjach szablonowanie danych i nie jest wprowadzenie koncepcji powiązań danych. Aby uzyskać informacje o pojęciach dotyczących wiązania danych podstawowych, zobacz [Data Binding Overview](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> dotyczy prezentacji danych i jest jednym z wielu funkcji, dostarczonych przez model Tworzenie szablonów i stylów WPF. Wprowadzenie WPF Tworzenie szablonów i stylów modelu, takie jak używać <xref:System.Windows.Style> można ustawić właściwości formantów, zobacz [Tworzenie szablonów i stylów](../controls/styling-and-templating.md) tematu.  
  
 Ponadto jest ważne, aby zrozumieć `Resources`, które są zasadniczo co Włącz obiektów takich jak <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> się do ponownego użycia. Aby uzyskać więcej informacji na temat zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Podstawowe informacje o danych szablonów  
  
 Aby zademonstrować Dlaczego <xref:System.Windows.DataTemplate> jest ważna, Przejdźmy przykład powiązania danych. W tym przykładzie mamy <xref:System.Windows.Controls.ListBox> , jest powiązany z listy `Task` obiektów. Każdy `Task` obiekt ma `TaskName` (ciąg) `Description` (ciąg) `Priority` (int) i właściwość typu `TaskType`, czyli `Enum` wartościami `Home` i `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez DataTemplate  
 Bez <xref:System.Windows.DataTemplate>, nasze <xref:System.Windows.Controls.ListBox> obecnie wygląda następująco:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Co się dzieje jest fakt, że bez żadnych szczególnych instrukcji <xref:System.Windows.Controls.ListBox> przez domyślną funkcję wywołania `ToString` podczas próby wyświetlenia obiektów w kolekcji. W związku z tym jeśli `Task` obiektu zastąpienia `ToString` metody, a następnie <xref:System.Windows.Controls.ListBox> wyświetlany jest ciąg reprezentujący każdego obiektu źródłowego w kolekcji źródłowej.  
  
 Na przykład jeśli `Task` klasy zastąpienia `ToString` metody w ten sposób gdzie `name` jest polem dla `TaskName` właściwości:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 A następnie <xref:System.Windows.Controls.ListBox> wygląda podobnie do następującego:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Dotyczy to jednak ograniczającą i sztywny. Ponadto jeśli dokonywane jest wiązanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych, nie będziesz mieć możliwości do zastąpienia `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definiowanie prostych DataTemplate  
 Rozwiązanie polega na zdefiniowaniu <xref:System.Windows.DataTemplate>. Jest jednym ze sposobów, aby to zrobić, można ustawić <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwość <xref:System.Windows.Controls.ListBox> do <xref:System.Windows.DataTemplate>. Określ w swojej <xref:System.Windows.DataTemplate> staje się struktura visual obiektu danych. Następujące <xref:System.Windows.DataTemplate> jest dość prosta. Udostępniamy możliwość instrukcji, które każdy element jest wyświetlany jako trzy <xref:System.Windows.Controls.TextBlock> elementów w obrębie <xref:System.Windows.Controls.StackPanel>. Każdy <xref:System.Windows.Controls.TextBlock> element jest powiązana z właściwością `Task` klasy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Dane bazowe dla przykłady w tym temacie jest kolekcją [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obiektów. Jeśli dokonywane jest wiązanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane podstawowe pojęcia są takie same, ale istnieje niewielkie różnice składniowe. Na przykład, zamiast `Path=TaskName`, należy ustawić <xref:System.Windows.Data.Binding.XPath%2A> do `@TaskName` (Jeśli `TaskName` to atrybut usługi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] węzła).  
  
 Obecnie nasz <xref:System.Windows.Controls.ListBox> wygląda podobnie do następującego:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Tworzenie DataTemplate jako zasób  
 W powyższym przykładzie zdefiniowaliśmy <xref:System.Windows.DataTemplate> wbudowanego. Jest to bardziej powszechne, aby zdefiniować w sekcji zasobów, aby mogło być ono obiekt wielokrotnego użytku, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Teraz możesz używać `myTaskTemplate` jako zasób, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Ponieważ `myTaskTemplate` jest zasobem, możesz go użyć na innych kontrolek, które mają właściwość, która przyjmuje <xref:System.Windows.DataTemplate> typu. Jak pokazano powyżej, aby uzyskać <xref:System.Windows.Controls.ItemsControl> obiekty, takie jak <xref:System.Windows.Controls.ListBox>, jest <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości. Aby uzyskać <xref:System.Windows.Controls.ContentControl> obiektów, jest <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Właściwość DataType obiektu  
 <xref:System.Windows.DataTemplate> Klasa ma <xref:System.Windows.DataTemplate.DataType%2A> właściwość, która jest bardzo podobny do <xref:System.Windows.Style.TargetType%2A> właściwość <xref:System.Windows.Style> klasy. Dlatego zamiast określania `x:Key` dla <xref:System.Windows.DataTemplate> w powyższym przykładzie można wykonaj następujące czynności:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 To <xref:System.Windows.DataTemplate> automatycznie stosowane do wszystkich `Task` obiektów. Należy pamiętać, że w tym przypadku `x:Key` ustawiono niejawnie. W związku z tym jeśli zostaną przypisane te <xref:System.Windows.DataTemplate> `x:Key` wartości są zastępowanie niejawny `x:Key` i <xref:System.Windows.DataTemplate> nie będą stosowane automatycznie.  
  
 Jeśli dokonywane jest wiązanie <xref:System.Windows.Controls.ContentControl> do kolekcji `Task` obiektów <xref:System.Windows.Controls.ContentControl> nie korzysta z powyższych <xref:System.Windows.DataTemplate> automatycznie. Jest to spowodowane wiązania w <xref:System.Windows.Controls.ContentControl> potrzebuje więcej informacji, aby odróżnić, czy chcesz powiązać z całej kolekcji lub poszczególnych obiektów. Jeśli Twoje <xref:System.Windows.Controls.ContentControl> służy do śledzenia wybór <xref:System.Windows.Controls.ItemsControl> typu, można ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Controls.ContentControl> powiązanie z "`/`" Aby wskazać, że jesteś zainteresowany bieżącego elementu. Aby uzyskać przykład, zobacz [powiązania z kolekcją i wyświetlanie informacji na podstawie wybranych](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). W przeciwnym razie należy określić <xref:System.Windows.DataTemplate> jawnie ustawiając <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości.  
  
 <xref:System.Windows.DataTemplate.DataType%2A> Właściwość jest szczególnie użyteczna w przypadku, gdy masz <xref:System.Windows.Data.CompositeCollection> różnych typów obiektów danych. Aby uzyskać przykład, zobacz [implementować CompositeCollection](how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Dodawanie więcej do DataTemplate  
 Obecnie dane są wyświetlane niezbędne informacje, ale zdecydowanie się udoskonalić. Możemy poprawić na prezentacji, dodając <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>ale niektóre <xref:System.Windows.Controls.TextBlock> elementy, które opisują dane, które są wyświetlane.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Poniższy zrzut ekranu przedstawia <xref:System.Windows.Controls.ListBox> z tym zmodyfikowane <xref:System.Windows.DataTemplate>:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Firma Microsoft można ustawić <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> do <xref:System.Windows.HorizontalAlignment.Stretch> na <xref:System.Windows.Controls.ListBox> się upewnić, że szerokość elementy zajmuje całe miejsce:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Za pomocą <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwością <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> teraz wygląda następująco:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Umożliwia stosowanie wartości właściwości DataTriggers  
 Bieżącej prezentacji nie Powiedz nam, czy `Task` jest głównym zadania lub pakietu office. Należy pamiętać, że `Task` obiekt ma `TaskType` właściwości typu `TaskType`, który jest wyliczenie z wartościami `Home` i `Work`.  
  
 W poniższym przykładzie <xref:System.Windows.DataTrigger> ustawia <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu o nazwie `border` do `Yellow` Jeśli `TaskType` właściwość `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Obecnie nasza aplikacja wygląda podobnie do poniższego. Głównego zadania są wyświetlane z żółte obramowanie i zadania pakietu office są wyświetlane z obramowaniem Akwamaryna:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 W tym przykładzie <xref:System.Windows.DataTrigger> używa <xref:System.Windows.Setter> można ustawić wartości właściwości. Klasy wyzwalacza również mieć <xref:System.Windows.TriggerBase.EnterActions%2A> i <xref:System.Windows.TriggerBase.ExitActions%2A> właściwości, które umożliwiają uruchomienie zestaw akcji, takich jak animacji. Ponadto dostępna jest również <xref:System.Windows.MultiDataTrigger> klasy, która pozwala na zastosowanie zmian na podstawie wielu powiązanych z danymi wartości właściwości.  
  
 Alternatywny sposób, aby osiągnąć ten sam efekt jest, aby powiązać <xref:System.Windows.Controls.Border.BorderBrush%2A> właściwości `TaskType` właściwość i użycia konwertera wartości do zwrócenia kolor na podstawie `TaskType` wartości. Tworzenie za pomocą konwertera celowi jest nieco bardziej efektywne pod względem wydajności. Ponadto tworzenie własnych konwerter zapewnia większą elastyczność, ponieważ jest dostarczenie własnej logiki. Ostatecznie techniki, które możesz wybrać jest zależny od scenariusza i preferencje. Aby dowiedzieć się, jak napisać konwertera, zobacz <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co to jest powiązana DataTemplate?  

W poprzednim przykładzie, możemy umieścić wyzwalacza w ramach <xref:System.Windows.DataTemplate> przy użyciu <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> Właściwość. <xref:System.Windows.Setter> Wyzwalacza ustawia wartości właściwości elementu ( <xref:System.Windows.Controls.Border> elementu) znajduje się w <xref:System.Windows.DataTemplate>. Jednak jeśli właściwości, Twoje `Setters` są zainteresowani nie są właściwości elementów, które znajdują się w bieżącej <xref:System.Windows.DataTemplate>, może być bardziej odpowiednie do ustawiania właściwości, za pomocą <xref:System.Windows.Style> to <xref:System.Windows.Controls.ListBoxItem> klasy (Jeśli formant, w której dokonywane jest wiązanie jest <xref:System.Windows.Controls.ListBox>). Na przykład, jeśli chcesz, aby Twoje <xref:System.Windows.Trigger> animować <xref:System.Windows.UIElement.Opacity%2A> wartość elementu, gdy wskaźnik myszy wskazuje element, zdefiniujesz Wyzwalacze w ramach <xref:System.Windows.Controls.ListBoxItem> stylu. Aby uzyskać przykład, zobacz [wprowadzenie do przykładowych szablonów i stylów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Ogólnie rzecz biorąc, należy pamiętać, że <xref:System.Windows.DataTemplate> są stosowane do każdego z wygenerowanym <xref:System.Windows.Controls.ListBoxItem> (Aby uzyskać więcej informacji na temat jak i gdzie jest ona rzeczywiście stosowane zobacz <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> strony.). Twoje <xref:System.Windows.DataTemplate> dotyczy tylko z prezentacji i wyglądu obiektów danych. W większości przypadków wszystkie inne aspekty prezentacją, czyli jakich element Dzieję, gdy jest ono zaznaczone lub w sposób, w jaki <xref:System.Windows.Controls.ListBox> przygotowuje się do elementów, nie należą do definicji <xref:System.Windows.DataTemplate>. Aby uzyskać przykład, zobacz [ItemsControl Tworzenie szablonów i stylów](#DataTemplating_ItemsControl) sekcji.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Wybieranie DataTemplate, na podstawie właściwości obiektu danych  
 W [Właściwość DataType obiektu](#Styling_DataType) sekcji opisano sposób zdefiniowania różnych danych szablonów obiektów danych. Jest szczególnie przydatne, gdy masz <xref:System.Windows.Data.CompositeCollection> o różnych typach lub kolekcje z elementami o różnych typach. W [Użyj DataTriggers stosowanie wartości właściwości](#DataTrigger_to_Apply_Property_Values) sekcji, firma Microsoft wykazały, że w przypadku kolekcji tego samego typu obiektów danych można utworzyć <xref:System.Windows.DataTemplate> , a następnie użyć wyzwalaczy, aby zastosować zmiany na podstawie wartości właściwości Każdy obiekt danych. Jednak wyzwalacze umożliwiają stosowanie wartości właściwości lub uruchomienie animacji, ale nie zapewniają elastyczność, aby odtworzyć strukturę obiektów danych. Niektórych scenariuszach może być konieczna utworzyć inną <xref:System.Windows.DataTemplate> danych obiektów, które są tego samego typu, ale ma inne właściwości.  
  
 Na przykład, gdy `Task` obiekt ma `Priority` wartość `1`, warto nadać mu zupełnie inny wygląd, która będzie służyć jako alert dla siebie. W takim przypadku należy utworzyć <xref:System.Windows.DataTemplate> wyświetlania o wysokim priorytecie `Task` obiektów. Dodajmy następujące <xref:System.Windows.DataTemplate> do sekcji zasobów:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Zwróć uwagę, w tym przykładzie użyto <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> Właściwość. Zasoby zdefiniowane w tej sekcji są współużytkowane przez elementy w ramach <xref:System.Windows.DataTemplate>.  
  
 Umożliwiają określanie wartości logiki, aby wybrać, które <xref:System.Windows.DataTemplate> do użycia na podstawie `Priority` wartość obiektu danych, Utwórz podklasę <xref:System.Windows.Controls.DataTemplateSelector> i zastąpić <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metody. W poniższym przykładzie <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metoda udostępnia logikę do zwrócenia odpowiedniego szablonu na podstawie wartości z `Priority` właściwości. Szablon do zwrócenia zostanie znaleziony w zasoby obejmujące <xref:System.Windows.Window> elementu.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Firma Microsoft następnie może zadeklarować `TaskListDataTemplateSelector` jako zasób:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Aby korzystać z zasobów selektor szablonu, należy przypisać ją do <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> właściwość <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> Wywołania <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metody `TaskListDataTemplateSelector` dla każdego z elementów w kolekcji źródłowej. Wywołanie przekazuje obiekt danych jako parametru elementu. <xref:System.Windows.DataTemplate> Zwracanym przez metodę jest następnie stosowane do tego obiektu danych.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Za pomocą selektora szablonu w miejscu <xref:System.Windows.Controls.ListBox> wygląda teraz następująco:  
  
 ![Zrzut ekranu przykładu szablonowanie danych](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Zakończenie naszej dyskusji w tym przykładzie. Aby uzyskać pełny przykład, zobacz [wprowadzenie do próbki Szablonowanie danych](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Tworzenie szablonów elementu ItemsControl i stylów  
 Mimo że <xref:System.Windows.Controls.ItemsControl> nie jest tylko typ formantu, którego można używać <xref:System.Windows.DataTemplate> , jest to bardzo typowy scenariusz, aby powiązać <xref:System.Windows.Controls.ItemsControl> do kolekcji. W [co to jest powiązana DataTemplate](#what_belongs_in_datatemplate) sekcji omówiono, definicji usługi <xref:System.Windows.DataTemplate> powinny być tylko zaniepokojona prezentację danych. Aby dowiedzieć się, gdy nie nadaje się do użycia <xref:System.Windows.DataTemplate> jest ważne poznać różne właściwości stylów i szablonów, dostarczonych przez <xref:System.Windows.Controls.ItemsControl>. Poniższy przykład jest przeznaczony do zilustrowania funkcji każdego z tych właściwości. <xref:System.Windows.Controls.ItemsControl> w tym przykładzie jest powiązany do tej samej `Tasks` kolekcji, co w poprzednim przykładzie. Demonstracyjne celów, style i szablony, w tym przykładzie są wszystkie wbudowane zadeklarowane.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Poniżej przedstawiono zrzut ekranu przykładu, gdy jest on renderowany:  
  
 ![Zrzut ekranu przykładu elementu ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Należy pamiętać, że zamiast <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, możesz użyć <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Zapoznaj się z poprzedniej sekcji, aby uzyskać przykład. Podobnie, zamiast <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, masz możliwość użycia <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Dwie inne stylu związane właściwości <xref:System.Windows.Controls.ItemsControl> , nie są wyświetlane w tym miejscu są <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> i <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Obsługa danych hierarchicznych  
 Do tej pory mają tylko zobaczyliśmy, jak powiązać i wyświetlić jedną kolekcję. Czasami masz kolekcję zawierającą inne kolekcje. <xref:System.Windows.HierarchicalDataTemplate> Klasa jest przeznaczona do użycia z <xref:System.Windows.Controls.HeaderedItemsControl> typów do wyświetlenia tych danych. W poniższym przykładzie `ListLeagueList` znajduje się lista `League` obiektów. Każdy `League` obiekt ma `Name` i kolekcji `Division` obiektów. Każdy `Division` ma `Name` i kolekcji `Team` obiektów i każdy `Team` obiekt ma `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 W przykładzie pokazano, że przy użyciu <xref:System.Windows.HierarchicalDataTemplate>, można łatwo wyświetlić dane z listy, który zawiera inne listy. Poniżej przedstawiono zrzut ekranu przykładu.  
  
 ![Zrzut ekranu przykładu przykładowy obiekt HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Przegląd Wiązanie danych](data-binding-overview.md)
- [Przegląd Style nagłówka kolumn i szablonów GridView](../controls/gridview-column-header-styles-and-templates-overview.md)
