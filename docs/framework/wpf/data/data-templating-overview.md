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
ms.openlocfilehash: 40d5ac257fa412afeb81b324d99604c0c1f5e878
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974889"
---
# <a name="data-templating-overview"></a>Przegląd Szablonowanie danych
Model tworzenia szablonów danych WPF zapewnia dużą elastyczność definiowania prezentacji danych. Formanty WPF mają wbudowaną funkcję do obsługi dostosowywania prezentacji danych. W tym temacie najpierw przedstawiono sposób definiowania <xref:System.Windows.DataTemplate> a następnie wprowadzono inne funkcje tworzenia szablonówymi danych, takie jak wybór szablonów oparty na logiki niestandardowej i obsługa wyświetlania danych hierarchicznych.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne
 Ten temat koncentruje się na funkcjach tworzenia szablonów danych i nie stanowi wprowadzenia koncepcji związanych z wiązaniem danych. Aby uzyskać informacje o podstawowych pojęciach dotyczących powiązań danych, zobacz [Omówienie powiązań danych](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate> jest informacje o prezentacji danych i jest jedną z wielu funkcji udostępnianych przez style WPF i model tworzenia szablonów. Aby uzyskać informacje na temat wprowadzenia stylu WPF i modelu tworzenia szablonów, takich jak używanie <xref:System.Windows.Style> do ustawiania właściwości w kontrolkach, zobacz temat [Style i tworzenia szablonów](../controls/styling-and-templating.md) .

 Ponadto ważne jest, aby zrozumieć `Resources`, które zasadniczo umożliwiają wielokrotne użycie obiektów, takich jak <xref:System.Windows.Style> i <xref:System.Windows.DataTemplate>. Aby uzyskać więcej informacji o zasobach, zobacz [zasoby XAML](../advanced/xaml-resources.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Podstawowe informacje dotyczące tworzenia szablonówi danych

 Aby zademonstrować, dlaczego <xref:System.Windows.DataTemplate> jest ważne, przejdźmy na przykład powiązania danych. W tym przykładzie mamy <xref:System.Windows.Controls.ListBox>, która jest powiązana z listą `Task` obiektów. Każdy obiekt `Task` ma `TaskName` (String), `Description` (ciąg), `Priority` (int) i właściwość typu `TaskType`, która jest `Enum` z wartościami `Home` i `Work`.

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Bez szablonu DataTemplate
 Bez <xref:System.Windows.DataTemplate>nasz <xref:System.Windows.Controls.ListBox> obecnie wygląda następująco:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Dzieje się tak, że bez żadnych konkretnych instrukcji <xref:System.Windows.Controls.ListBox> domyślnie wywołania `ToString` podczas próby wyświetlenia obiektów w kolekcji. W związku z tym, jeśli obiekt `Task` przesłania metodę `ToString`, <xref:System.Windows.Controls.ListBox> Wyświetla reprezentację ciągu każdego obiektu źródłowego w kolekcji źródłowej.

 Na przykład, jeśli Klasa `Task` przesłania metodę `ToString` w ten sposób, gdzie `name` jest polem dla właściwości `TaskName`:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Następnie <xref:System.Windows.Controls.ListBox> wygląda następująco:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Jednak ograniczanie i elastyczność. Ponadto, jeśli tworzysz powiązanie z danymi XML, nie można przesłonić `ToString`.

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Definiowanie prostego szablonu DataTemplate
 Rozwiązaniem jest zdefiniowanie <xref:System.Windows.DataTemplate>. Jednym ze sposobów jest ustawienie właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ListBox> na <xref:System.Windows.DataTemplate>. Elementy określone w <xref:System.Windows.DataTemplate> staną się strukturą wizualizacji obiektu danych. Poniższe <xref:System.Windows.DataTemplate> są dość proste. Wyrażamy instrukcje, że każdy element pojawia się jako trzy <xref:System.Windows.Controls.TextBlock> elementy w <xref:System.Windows.Controls.StackPanel>. Każdy element <xref:System.Windows.Controls.TextBlock> jest powiązany z właściwością klasy `Task`.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Dane bazowe dla przykładów w tym temacie są kolekcją obiektów CLR. W przypadku powiązań z danymi XML podstawowe koncepcje są takie same, ale istnieje niewielka różnica składni. Na przykład zamiast `Path=TaskName`, należy ustawić <xref:System.Windows.Data.Binding.XPath%2A> na `@TaskName` (jeśli `TaskName` jest atrybutem węzła XML).

 Teraz nasza <xref:System.Windows.Controls.ListBox> wygląda następująco:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Tworzenie szablonu DataTemplate jako zasobu
 W powyższym przykładzie zdefiniowano <xref:System.Windows.DataTemplate> w tekście. Jest to bardziej powszechne, aby zdefiniować go w sekcji Resources, aby mógł być obiektem wielokrotnego użytku, jak w poniższym przykładzie:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Teraz można użyć `myTaskTemplate` jako zasobu, jak w poniższym przykładzie:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Ponieważ `myTaskTemplate` jest zasobem, można go teraz używać w innych kontrolkach, które mają właściwość, która przyjmuje typ <xref:System.Windows.DataTemplate>. Jak pokazano powyżej, dla <xref:System.Windows.Controls.ItemsControl> obiektów, takich jak <xref:System.Windows.Controls.ListBox>, jest to właściwość <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>. Dla <xref:System.Windows.Controls.ContentControl> obiektów jest to właściwość <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>Właściwość DataType
 Klasa <xref:System.Windows.DataTemplate> ma właściwość <xref:System.Windows.DataTemplate.DataType%2A>, która jest bardzo podobna do właściwości <xref:System.Windows.Style.TargetType%2A> klasy <xref:System.Windows.Style>. W związku z tym zamiast określania `x:Key` dla <xref:System.Windows.DataTemplate> w powyższym przykładzie można wykonać następujące czynności:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Ta <xref:System.Windows.DataTemplate> jest automatycznie stosowana do wszystkich obiektów `Task`. Należy zauważyć, że w tym przypadku `x:Key` jest ustawiana niejawnie. W związku z tym, Jeśli przypiszesz tę <xref:System.Windows.DataTemplate> wartość `x:Key`, zastąpi niejawne `x:Key` i <xref:System.Windows.DataTemplate> nie zostanie zastosowana automatycznie.

 Jeśli powiążesz <xref:System.Windows.Controls.ContentControl> z kolekcją obiektów `Task`, <xref:System.Windows.Controls.ContentControl> nie użyje powyższych <xref:System.Windows.DataTemplate> automatycznie. Wynika to z faktu, że powiązanie na <xref:System.Windows.Controls.ContentControl> wymaga więcej informacji w celu rozróżnienia, czy chcesz powiązać z całą kolekcją, czy z pojedynczymi obiektami. Jeśli <xref:System.Windows.Controls.ContentControl> śledzi wybór typu <xref:System.Windows.Controls.ItemsControl>, można ustawić właściwość <xref:System.Windows.Data.Binding.Path%2A> powiązania <xref:System.Windows.Controls.ContentControl> na "`/`", aby wskazać, że interesuje Cię bieżący element. Aby zapoznać się z przykładem, zobacz [Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). W przeciwnym razie należy określić <xref:System.Windows.DataTemplate> jawnie przez ustawienie właściwości <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>.

 Właściwość <xref:System.Windows.DataTemplate.DataType%2A> jest szczególnie przydatna, gdy istnieje <xref:System.Windows.Data.CompositeCollection> różnych typów obiektów danych. Aby zapoznać się z przykładem, zobacz [implementacja złożonego](how-to-implement-a-compositecollection.md)obiektu.

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Dodawanie więcej do szablonu DataTemplate
 Obecnie dane pojawiają się wraz z niezbędnymi informacjami, ale jest to w nieskończoność do poprawy. Ulepszamy prezentację poprzez dodanie <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>i niektórych <xref:System.Windows.Controls.TextBlock> elementów, które opisują dane, które są wyświetlane.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Poniższy zrzut ekranu przedstawia <xref:System.Windows.Controls.ListBox> z tym zmodyfikowanym <xref:System.Windows.DataTemplate>:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Można ustawić <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> na <xref:System.Windows.HorizontalAlignment.Stretch> <xref:System.Windows.Controls.ListBox>, aby upewnić się, że szerokość elementów przyjmuje całe miejsce:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 Po ustawieniu właściwości <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> na <xref:System.Windows.HorizontalAlignment.Stretch>, <xref:System.Windows.Controls.ListBox> wygląda teraz następująco:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Używanie wyzwalaczy DataTriggers do stosowania wartości właściwości
 Bieżąca prezentacja nie informuje nas o tym, czy `Task` to zadanie główne czy zadanie pakietu Office. Należy pamiętać, że obiekt `Task` ma właściwość `TaskType` typu `TaskType`, która jest wyliczeniem z wartościami `Home` i `Work`.

 W poniższym przykładzie <xref:System.Windows.DataTrigger> ustawia <xref:System.Windows.Controls.Border.BorderBrush%2A> elementu o nazwie `border` do `Yellow`, jeśli właściwość `TaskType` jest `TaskType.Home`.

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Nasza aplikacja wygląda teraz następująco. Zadania główne są wyświetlane z żółtym obramowaniem, a zadania pakietu Office są wyświetlane z obramowaniem akwamaryna:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 W tym przykładzie <xref:System.Windows.DataTrigger> używa <xref:System.Windows.Setter> do ustawiania wartości właściwości. Klasy wyzwalaczy mają również właściwości <xref:System.Windows.TriggerBase.EnterActions%2A> i <xref:System.Windows.TriggerBase.ExitActions%2A>, które umożliwiają uruchamianie zestawu akcji, takich jak animacje. Ponadto istnieje również Klasa <xref:System.Windows.MultiDataTrigger>, która pozwala na zastosowanie zmian w oparciu o wiele wartości właściwości powiązanych z danymi.

 Alternatywnym sposobem osiągnięcia tego samego efektu jest powiązanie właściwości <xref:System.Windows.Controls.Border.BorderBrush%2A> z właściwością `TaskType` i użycie konwertera wartości w celu zwrócenia koloru na podstawie wartości `TaskType`. Tworzenie powyższego efektu przy użyciu konwertera jest nieco bardziej wydajne w zakresie wydajności. Ponadto Tworzenie własnego konwertera zapewnia większą elastyczność, ponieważ dostarczasz własną logikę. Na końcu wybrana technika zależy od Twojego scenariusza i preferencji. Informacje o sposobach pisania konwertera znajdują się w temacie <xref:System.Windows.Data.IValueConverter>.

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>Co należy do szablonu DataTemplate?

W poprzednim przykładzie został umieszczony wyzwalacz w <xref:System.Windows.DataTemplate> przy użyciu właściwości <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType>. <xref:System.Windows.Setter> wyzwalacza ustawia wartość właściwości elementu (elementu <xref:System.Windows.Controls.Border>) znajdującego się w <xref:System.Windows.DataTemplate>. Jeśli jednak właściwości, których `Setters` są zainteresowani, nie są właściwościami elementów, które znajdują się w bieżącym <xref:System.Windows.DataTemplate>, może być bardziej odpowiednie do ustawiania właściwości przy użyciu <xref:System.Windows.Style>, który jest dla klasy <xref:System.Windows.Controls.ListBoxItem> (jeśli formant, który jest powiązany, jest <xref:System.Windows.Controls.ListBox>). Na przykład jeśli chcesz, aby <xref:System.Windows.Trigger> animować wartość <xref:System.Windows.UIElement.Opacity%2A> elementu, gdy mysz wskazuje element, zdefiniuj Wyzwalacze w <xref:System.Windows.Controls.ListBoxItem> stylu. Aby zapoznać się z przykładem, zobacz [wprowadzenie do stylu i przykładu tworzenia szablonów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

 Ogólnie rzecz biorąc, należy pamiętać, że <xref:System.Windows.DataTemplate> jest stosowana do każdego z wygenerowanych <xref:System.Windows.Controls.ListBoxItem> (Aby uzyskać więcej informacji na temat sposobu i miejsca, w którym jest faktycznie stosowana, zobacz stronę <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>). <xref:System.Windows.DataTemplate> jest objęta tylko prezentacją i wyglądem obiektów danych. W większości przypadków wszystkie inne aspekty prezentacji, takie jak wygląd elementu, jeśli jest zaznaczone, lub sposób, w jaki <xref:System.Windows.Controls.ListBox> ustalają elementy, nie należą do definicji <xref:System.Windows.DataTemplate>. Aby zapoznać się z przykładem, zobacz sekcję [Style i tworzenia szablonów ItemsControl](#DataTemplating_ItemsControl) .

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Wybieranie szablonu danych na podstawie właściwości obiektu dane
 W sekcji [Właściwości DataType](#Styling_DataType) omawiamy, że można definiować różne szablony danych dla różnych obiektów danych. Jest to szczególnie przydatne w przypadku <xref:System.Windows.Data.CompositeCollection> różnych typów lub kolekcji z elementami różnych typów. W sekcji [Użyj DataTriggers do zastosowania wartości właściwości](#DataTrigger_to_Apply_Property_Values) wykazałeś, że jeśli masz kolekcję tego samego typu obiektów danych, możesz utworzyć <xref:System.Windows.DataTemplate> a następnie użyć wyzwalaczy, aby zastosować zmiany na podstawie wartości właściwości każdego obiektu danych. Wyzwalacze umożliwiają jednak stosowanie wartości właściwości lub uruchamianie animacji, ale nie pozwalają na odtworzenie struktury obiektów danych. Niektóre scenariusze mogą wymagać utworzenia innego <xref:System.Windows.DataTemplate> dla obiektów danych, które są tego samego typu, ale mają różne właściwości.

 Na przykład, gdy obiekt `Task` ma `Priority` wartość `1`, warto nadać mu zupełnie inny wygląd, który będzie używany jako alert dla siebie. W takim przypadku utworzysz <xref:System.Windows.DataTemplate> do wyświetlania obiektów `Task` o wysokim priorytecie. Dodajmy następujące <xref:System.Windows.DataTemplate> do sekcji Resources:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

Ten przykład używa właściwości [DataTemplate. resources](xref:System.Windows.FrameworkTemplate.Resources%2A) . Zasoby zdefiniowane w tej sekcji są udostępniane przez elementy w ramach <xref:System.Windows.DataTemplate>.

 Aby określić, które <xref:System.Windows.DataTemplate> użyć na podstawie `Priority` wartości obiektu danych, Utwórz podklasę <xref:System.Windows.Controls.DataTemplateSelector> i Zastąp metodę <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>. W poniższym przykładzie metoda <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> zapewnia logikę do zwrócenia odpowiedniego szablonu na podstawie wartości właściwości `Priority`. Szablon do zwrócenia znajduje się w zasobach <xref:System.Windows.Window> elementu.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Następnie możemy zadeklarować `TaskListDataTemplateSelector` jako zasób:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Aby użyć zasobu selektora szablonów, przypisz go do właściwości <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ListBox>. <xref:System.Windows.Controls.ListBox> wywołuje metodę <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> `TaskListDataTemplateSelector` dla każdego elementu w kolekcji źródłowej. Wywołanie przekazuje obiekt danych jako parametr elementu. <xref:System.Windows.DataTemplate>, który jest zwracany przez metodę, zostanie następnie zastosowany do tego obiektu danych.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Po dokonaniu wyboru szablonu <xref:System.Windows.Controls.ListBox> teraz pojawia się w następujący sposób:

 ![Zrzut ekranu przedstawiający przykładowy tworzenia szablonów danych](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Zakończymy nasze omówienie tego przykładu. Pełny przykład można znaleźć w artykule [wprowadzenie do danych tworzenia szablonów Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Style i tworzenia szablonów ItemsControl
 Mimo że <xref:System.Windows.Controls.ItemsControl> nie jest jedynym typem formantu, którego można użyć <xref:System.Windows.DataTemplate> z, jest to bardzo typowy scenariusz, aby powiązać <xref:System.Windows.Controls.ItemsControl> z kolekcją. W obszarze [co należy do sekcji DataTemplate](#what_belongs_in_datatemplate) omówione, że definicja <xref:System.Windows.DataTemplate> powinna dotyczyć tylko prezentacji danych. Aby dowiedzieć się, kiedy nie jest to odpowiednie do używania <xref:System.Windows.DataTemplate>, ważne jest zrozumienie różnych właściwości stylu i szablonu dostarczonych przez <xref:System.Windows.Controls.ItemsControl>. Poniższy przykład został zaprojektowany w celu zilustrowania funkcji każdej z tych właściwości. <xref:System.Windows.Controls.ItemsControl> w tym przykładzie jest powiązany z tą samą kolekcją `Tasks`, jak w poprzednim przykładzie. W celach demonstracyjnych, style i szablony w tym przykładzie są zadeklarowane wewnętrznie.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Poniżej znajduje się zrzut ekranu przedstawiający przykład podczas renderowania:

 ![Przykładowy zrzut ekranu ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Należy pamiętać, że zamiast używać <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, można użyć <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Na przykład zapoznaj się z poprzednią sekcją. Podobnie, zamiast używać <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, można skorzystać z <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.

 Dwie inne właściwości powiązane z stylem <xref:System.Windows.Controls.ItemsControl>, które nie są wyświetlane w tym miejscu, są <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> i <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Obsługa danych hierarchicznych
 Do tej pory udałomy się tylko doprowadzić do tworzenia i wyświetlania pojedynczej kolekcji. Czasami kolekcja zawiera inne kolekcje. Klasa <xref:System.Windows.HierarchicalDataTemplate> została zaprojektowana tak, aby była używana z typami <xref:System.Windows.Controls.HeaderedItemsControl> do wyświetlania takich danych. W poniższym przykładzie `ListLeagueList` jest listą obiektów `League`. Każdy obiekt `League` ma `Name` i kolekcję obiektów `Division`. Każda `Division` ma `Name` i kolekcję obiektów `Team`, a każdy obiekt `Team` ma `Name`.

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 W przykładzie pokazano, że przy użyciu <xref:System.Windows.HierarchicalDataTemplate>można łatwo wyświetlić dane listy zawierającej inne listy. Poniżej znajduje się zrzut ekranu przedstawiający przykład.

 ![Przykładowy zrzut ekranu HierarchicalDataTemplate](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView — style i szablony nagłówków kolumn — omówienie](../controls/gridview-column-header-styles-and-templates-overview.md)
