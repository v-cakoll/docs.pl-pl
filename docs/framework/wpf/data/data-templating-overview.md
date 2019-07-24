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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400659"
---
# <a name="data-templating-overview"></a>Przegląd Szablonowanie danych
Model tworzenia szablonów danych WPF zapewnia dużą elastyczność definiowania prezentacji danych. Formanty WPF mają wbudowaną funkcję do obsługi dostosowywania prezentacji danych. W tym temacie najpierw pokazano, jak zdefiniować <xref:System.Windows.DataTemplate> i a następnie wprowadzić inne funkcje tworzenia szablonów danych, takie jak wybór szablonów oparty na logiki niestandardowej i obsługa wyświetlania danych hierarchicznych.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten temat koncentruje się na funkcjach tworzenia szablonów danych i nie stanowi wprowadzenia koncepcji związanych z wiązaniem danych. Aby uzyskać informacje o podstawowych pojęciach dotyczących powiązań danych, zobacz [Omówienie powiązań danych](data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>zawiera informacje o prezentacji danych i jest jedną z wielu funkcji udostępnianych przez style WPF i model tworzenia szablonów. Aby uzyskać informacje na temat wprowadzenia stylu WPF i modelu tworzenia szablonów, takich jak używanie <xref:System.Windows.Style> do ustawiania właściwości w kontrolkach, zobacz temat [Style i tworzenia szablonów](../controls/styling-and-templating.md) .  
  
 Ponadto ważne jest, aby zrozumieć `Resources`, które są zasadniczo, co pozwala na wielokrotne użycie obiektów, takich jak <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate> . Aby uzyskać więcej informacji o zasobach, zobacz [zasoby XAML](../advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Podstawowe informacje dotyczące tworzenia szablonówi danych  
  
 Aby zademonstrować, dlaczego <xref:System.Windows.DataTemplate> jest ważne, przejdźmy na przykład powiązania danych. W tym przykładzie <xref:System.Windows.Controls.ListBox> mamy powiązanie z `Task` listą obiektów. Każdy `Task` obiekt `Priority` `TaskType` `Home` `Enum` `Work`ma `TaskName` (ciąg),(ciąg),a(int)iwłaściwośćtypu,którajest`Description` z wartościami i.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Bez szablonu DataTemplate  
 Bez, nasz <xref:System.Windows.Controls.ListBox> aktualnie wygląda następująco: <xref:System.Windows.DataTemplate>  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Dzieje się tak, że nie trzeba wykonywać żadnych określonych instrukcji, <xref:System.Windows.Controls.ListBox> domyślnie wywołania `ToString` podczas próby wyświetlenia obiektów w kolekcji. W związku z tym `Task` , jeśli obiekt `ToString` przesłania metodę, a <xref:System.Windows.Controls.ListBox> następnie wyświetla ciąg reprezentujący każdy obiekt źródłowy w źródłowej kolekcji.  
  
 Na przykład, `Task` Jeśli Klasa `ToString` przesłania metodę w ten sposób, gdzie `name` to pole `TaskName` właściwości:  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 <xref:System.Windows.Controls.ListBox> Następnie wygląda następująco:  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Jednak ograniczanie i elastyczność. Ponadto w przypadku tworzenia powiązań z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi nie można przesłonić. `ToString`  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Definiowanie prostego szablonu DataTemplate  
 Rozwiązaniem jest zdefiniowanie <xref:System.Windows.DataTemplate>. Jednym ze sposobów jest ustawienie <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>na. Zawartość, którą określisz <xref:System.Windows.DataTemplate> , zmieni się na strukturę wizualizacji obiektu danych. Poniżej przedstawiono <xref:System.Windows.DataTemplate> stosunkowo proste. Podajemy instrukcje, że każdy element pojawia się <xref:System.Windows.Controls.TextBlock> jako trzy elementy <xref:System.Windows.Controls.StackPanel>w. Każdy <xref:System.Windows.Controls.TextBlock> element jest powiązany z właściwością `Task` klasy.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Dane bazowe dla przykładów w tym temacie są kolekcją obiektów CLR. Jeśli tworzysz powiązanie z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi, podstawowe koncepcje są takie same, ale istnieje niewielka różnica składni. `Path=TaskName`Na przykład zamiast ma być ustawiony `@TaskName` <xref:System.Windows.Data.Binding.XPath%2A> na (Jeśli `TaskName` jest atrybutem [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] węzła).  
  
 Teraz nasz <xref:System.Windows.Controls.ListBox> wygląd wygląda następująco:  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Tworzenie szablonu DataTemplate jako zasobu  
 W powyższym przykładzie zdefiniowano <xref:System.Windows.DataTemplate> wbudowaną. Jest to bardziej powszechne, aby zdefiniować go w sekcji Resources, aby mógł być obiektem wielokrotnego użytku, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Teraz można użyć `myTaskTemplate` jako zasobu, jak w poniższym przykładzie:  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Ponieważ `myTaskTemplate` jest zasobem, można go teraz używać w innych kontrolkach, które mają właściwość <xref:System.Windows.DataTemplate> przyjmującą typ. Jak pokazano powyżej, w <xref:System.Windows.Controls.ItemsControl> przypadku obiektów, takich <xref:System.Windows.Controls.ListBox>jak, jest <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to właściwość. W <xref:System.Windows.Controls.ContentControl> przypadku obiektów <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> jest to właściwość.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>Właściwość DataType  
 Klasa ma właściwość, która <xref:System.Windows.Style.TargetType%2A> jest bardzo podobna <xref:System.Windows.Style> do właściwości klasy. <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.DataTemplate> W związku z tym zamiast określania `x:Key` wartości w powyższym przykładzie można wykonać następujące czynności: <xref:System.Windows.DataTemplate>  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Zostanie ona zastosowana automatycznie do `Task` wszystkich obiektów. <xref:System.Windows.DataTemplate> Należy pamiętać, że w tym `x:Key` przypadku jest to ustawiane niejawnie. W związku z tym, jeśli <xref:System.Windows.DataTemplate> przypiszesz `x:Key` tę wartość, <xref:System.Windows.DataTemplate> zastępujesz `x:Key` niejawną, a nie zostanie ona zastosowana automatycznie.  
  
 Jeśli tworzysz powiązanie <xref:System.Windows.Controls.ContentControl> z `Task` kolekcją obiektów, program <xref:System.Windows.Controls.ContentControl> nie używa powyższych <xref:System.Windows.DataTemplate> informacji automatycznie. Jest to spowodowane tym, że powiązanie <xref:System.Windows.Controls.ContentControl> na potrzeby potrzeb dodatkowych informacji pozwalające określić, czy chcesz powiązać z całą kolekcją, czy z pojedynczymi obiektami. <xref:System.Windows.Controls.ContentControl> Jeśli śledzi wybór <xref:System.Windows.Controls.ItemsControl> typu`/`, można <xref:System.Windows.Controls.ContentControl> ustawić właściwość powiązania na "", aby wskazać, że interesuje <xref:System.Windows.Data.Binding.Path%2A> Cię bieżący element. Aby zapoznać się z przykładem, zobacz [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). W przeciwnym razie należy określić <xref:System.Windows.DataTemplate> jawnie przez <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ustawienie właściwości.  
  
 Właściwość jest szczególnie przydatna w przypadku <xref:System.Windows.Data.CompositeCollection> różnych typów obiektów danych. <xref:System.Windows.DataTemplate.DataType%2A> Aby zapoznać się z przykładem, zobacz [implementacja złożonego](how-to-implement-a-compositecollection.md)obiektu.  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Dodawanie więcej do szablonu DataTemplate  
 Obecnie dane pojawiają się wraz z niezbędnymi informacjami, ale jest to w nieskończoność do poprawy. Ulepszamy prezentację <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Grid>, dodając, a i niektóre <xref:System.Windows.Controls.TextBlock> elementy opisujące dane, które są wyświetlane.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Poniższy zrzut ekranu przedstawia <xref:System.Windows.Controls.ListBox> z tą modyfikacją: <xref:System.Windows.DataTemplate>  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Można ustawić <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> na wartość na, <xref:System.Windows.Controls.ListBox> aby upewnić się, że szerokość elementów przyjmuje całe miejsce:  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Gdy <xref:System.Windows.HorizontalAlignment.Stretch> <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> Właściwośćjestustawionana,terazwyglądanastępująco:<xref:System.Windows.Controls.ListBox>  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Używanie wyzwalaczy DataTriggers do stosowania wartości właściwości  
 Bieżąca prezentacja nie informuje nas o `Task` tym, czy jest to zadanie główne czy zadanie pakietu Office. Należy pamiętać, `Task` że obiekt `TaskType` ma właściwość typu `TaskType`, która jest wyliczeniem z wartościami `Home` i `Work`.  
  
 <xref:System.Windows.DataTrigger> W poniższym przykładzie <xref:System.Windows.Controls.Border.BorderBrush%2A> ustawia `border` elemento`Yellow` nazwie na, jeśli `TaskType.Home`właściwość jest. `TaskType`  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Nasza aplikacja wygląda teraz następująco. Zadania główne są wyświetlane z żółtym obramowaniem, a zadania pakietu Office są wyświetlane z obramowaniem akwamaryna:  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 W tym przykładzie <xref:System.Windows.DataTrigger> <xref:System.Windows.Setter> używa do ustawiania wartości właściwości. Klasy wyzwalaczy mają <xref:System.Windows.TriggerBase.EnterActions%2A> również właściwości i <xref:System.Windows.TriggerBase.ExitActions%2A> , które umożliwiają uruchamianie zestawu akcji, takich jak animacje. Ponadto istnieje również <xref:System.Windows.MultiDataTrigger> Klasa, która pozwala na zastosowanie zmian w oparciu o wiele wartości właściwości powiązanych z danymi.  
  
 Alternatywnym sposobem osiągnięcia tego samego efektu jest powiązanie <xref:System.Windows.Controls.Border.BorderBrush%2A> właściwości `TaskType` z właściwością i użycie konwertera wartości w celu zwrócenia koloru na podstawie `TaskType` wartości. Tworzenie powyższego efektu przy użyciu konwertera jest nieco bardziej wydajne w zakresie wydajności. Ponadto Tworzenie własnego konwertera zapewnia większą elastyczność, ponieważ dostarczasz własną logikę. Na końcu wybrana technika zależy od Twojego scenariusza i preferencji. Informacje o sposobach pisania konwertera znajdują się <xref:System.Windows.Data.IValueConverter>w temacie.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Co należy do szablonu DataTemplate?  

W poprzednim przykładzie został umieszczony wyzwalacz w <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>użyciu.<xref:System.Windows.DataTemplate.Triggers%2A> wartość. Wyzwalacz ustawia wartość właściwości elementu <xref:System.Windows.Controls.Border> (elementu <xref:System.Windows.DataTemplate>), który znajduje się w. <xref:System.Windows.Setter> Jeśli jednak właściwości, z `Setters` którymi się znajdują, nie są właściwościami elementów, które znajdują się w bieżącym <xref:System.Windows.DataTemplate>, może być bardziej odpowiednie do <xref:System.Windows.Style> ustawiania właściwości przy użyciu <xref:System.Windows.Controls.ListBoxItem> klasy, która jest klasą (Jeśli formant, który jest powiązany, <xref:System.Windows.Controls.ListBox>to a). Jeśli na przykład chcesz <xref:System.Windows.Trigger> <xref:System.Windows.UIElement.Opacity%2A> animować wartość elementu, gdy wskaźnik myszy wskazuje element, definiujesz Wyzwalacze w <xref:System.Windows.Controls.ListBoxItem> stylu. Aby zapoznać się z przykładem, zobacz [wprowadzenie do stylu i przykładu tworzenia szablonów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).
  
 Ogólnie rzecz biorąc, pamiętaj, że <xref:System.Windows.DataTemplate> jest stosowana do każdego z wygenerowanych <xref:System.Windows.Controls.ListBoxItem> (Aby uzyskać więcej informacji na temat sposobu i miejsca, w którym jest <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> faktycznie stosowana, zobacz stronę). <xref:System.Windows.DataTemplate> Dotyczy tylko prezentacji i wyglądu obiektów danych. W większości przypadków wszystkie inne aspekty prezentacji, takie jak element wygląda na to, kiedy jest zaznaczone, lub jak <xref:System.Windows.Controls.ListBox> układają elementy, nie należą do definicji. <xref:System.Windows.DataTemplate> Aby zapoznać się z przykładem, zobacz sekcję [Style i tworzenia szablonów ItemsControl](#DataTemplating_ItemsControl) .  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Wybieranie szablonu danych na podstawie właściwości obiektu dane  
 W sekcji [Właściwości DataType](#Styling_DataType) omawiamy, że można definiować różne szablony danych dla różnych obiektów danych. Jest to szczególnie przydatne w przypadku, gdy <xref:System.Windows.Data.CompositeCollection> istnieje różne typy lub kolekcje z elementami różnych typów. W sekcji [Użyj DataTriggers do zastosowania wartości właściwości](#DataTrigger_to_Apply_Property_Values) wykazałeś, że jeśli masz kolekcję tego samego typu obiektów danych, możesz utworzyć <xref:System.Windows.DataTemplate> a następnie użyć wyzwalaczy, aby zastosować zmiany na podstawie wartości właściwości każdego obiektu danych. Wyzwalacze umożliwiają jednak stosowanie wartości właściwości lub uruchamianie animacji, ale nie pozwalają na odtworzenie struktury obiektów danych. Niektóre scenariusze mogą wymagać utworzenia innego <xref:System.Windows.DataTemplate> dla obiektów danych, które są tego samego typu, ale mają różne właściwości.  
  
 Na przykład, gdy `Task` obiekt `Priority` ma wartość `1`, możesz chcieć nadać mu zupełnie inny wygląd, który będzie używany jako alert dla siebie. W takim przypadku należy utworzyć <xref:System.Windows.DataTemplate> do wyświetlania obiektów o wysokim priorytecie. `Task` Dodajmy następujące elementy <xref:System.Windows.DataTemplate> do sekcji Resources:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Zauważ, że w <xref:System.Windows.DataTemplate>tym przykładzie używamy.<xref:System.Windows.FrameworkTemplate.Resources%2A> wartość. Zasoby zdefiniowane w tej sekcji są udostępniane przez elementy w obrębie <xref:System.Windows.DataTemplate>.  
  
 Aby określić logikę do wyboru <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.DataTemplateSelector> , która ma być używana `Priority` na podstawie wartości obiektu danych, należy utworzyć <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> podklasę i zastąpić metodę. W poniższym przykładzie <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> Metoda udostępnia logikę do zwrócenia odpowiedniego szablonu na podstawie wartości `Priority` właściwości. Szablon do zwrócenia znajduje się w zasobach <xref:System.Windows.Window> elementu obejmujących.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Następnie można zadeklarować `TaskListDataTemplateSelector` jako zasób:  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Aby użyć zasobu selektora szablonów, przypisz go do <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> właściwości. <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListBox> Wywołuje<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metodę dla`TaskListDataTemplateSelector` każdego elementu w kolekcji źródłowej. Wywołanie przekazuje obiekt danych jako parametr elementu. Wartość <xref:System.Windows.DataTemplate> zwracana przez metodę jest następnie stosowana do tego obiektu danych.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Po dokonaniu <xref:System.Windows.Controls.ListBox> wyboru szablonu teraz pojawia się w następujący sposób:  
  
 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

Zakończymy nasze omówienie tego przykładu. Pełny przykład można znaleźć w artykule [wprowadzenie do danych tworzenia szablonów Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Style i tworzenia szablonów ItemsControl  
 Mimo że nie <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ItemsControl> jest jedynym typem formantu, którego można używać z, jest to bardzo typowy scenariusz powiązania z <xref:System.Windows.Controls.ItemsControl> kolekcją. W obszarze [co należy](#what_belongs_in_datatemplate) do sekcji DataTemplate omówione, że definicja elementu <xref:System.Windows.DataTemplate> powinna dotyczyć tylko prezentacji danych. Aby dowiedzieć się, kiedy nie jest to odpowiednie do użycia <xref:System.Windows.DataTemplate> , ważne jest zrozumienie różnych właściwości stylu i szablonu dostarczonych <xref:System.Windows.Controls.ItemsControl>przez. Poniższy przykład został zaprojektowany w celu zilustrowania funkcji każdej z tych właściwości. W tym przykładzie jest to powiązane z tą samą `Tasks` kolekcją, jak w poprzednim przykładzie. <xref:System.Windows.Controls.ItemsControl> W celach demonstracyjnych, style i szablony w tym przykładzie są zadeklarowane wewnętrznie.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Poniżej znajduje się zrzut ekranu przedstawiający przykład podczas renderowania:  
  
 ![Przykładowy zrzut ekranu ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Należy pamiętać, że zamiast korzystać <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>z programu, można <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>użyć. Na przykład zapoznaj się z poprzednią sekcją. Podobnie zamiast korzystać z programu <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, można <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>skorzystać z opcji.  
  
 Dwie inne właściwości powiązane z stylem, <xref:System.Windows.Controls.ItemsControl> które nie są wyświetlane w tym <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> miejscu <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>, to i.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Obsługa danych hierarchicznych  
 Do tej pory udałomy się tylko doprowadzić do tworzenia i wyświetlania pojedynczej kolekcji. Czasami kolekcja zawiera inne kolekcje. Klasa jest przeznaczona do użycia z <xref:System.Windows.Controls.HeaderedItemsControl> typami do wyświetlania takich danych. <xref:System.Windows.HierarchicalDataTemplate> W poniższym przykładzie `ListLeagueList` jest `League` listą obiektów. Każdy `League` obiekt makolekcję`Division` obiektów i. `Name` Każdy `Division` z nich `Name` ma kolekcję `Team` obiektów i każdy `Team` obiekt ma `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 W przykładzie pokazano, że przy użyciu programu <xref:System.Windows.HierarchicalDataTemplate>można łatwo wyświetlić dane listy zawierające inne listy. Poniżej znajduje się zrzut ekranu przedstawiający przykład.  
  
 ![Przykładowy zrzut ekranu HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [GridView — style i szablony nagłówków kolumn — omówienie](../controls/gridview-column-header-styles-and-templates-overview.md)
