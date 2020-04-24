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
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646459"
---
# <a name="data-templating-overview"></a>Przegląd Szablonowanie danych
Model szablonów danych WPF zapewnia dużą elastyczność definiowania prezentacji danych. Kontrolki WPF mają wbudowane funkcje do obsługi dostosowywania prezentacji danych. W tym temacie najpierw pokazano, jak zdefiniować, <xref:System.Windows.DataTemplate> a następnie wprowadza inne funkcje tworzenia szablonów danych, takie jak wybór szablonów opartych na logice niestandardowej i obsługa wyświetlania danych hierarchicznych.

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne
 W tym temacie koncentruje się na funkcji tworzenia szablonów danych i nie jest wprowadzenie pojęcia powiązania danych. Aby uzyskać informacje na temat podstawowych pojęć dotyczących powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).

 <xref:System.Windows.DataTemplate>jest o prezentacji danych i jest jedną z wielu funkcji oferowanych przez WPF stylizacja i szablonów modelu. Aby zapoznać się z wprowadzeniem modelu stylów i szablonów <xref:System.Windows.Style> WPF, takich jak sposób używania a do ustawiania właściwości formantu, zobacz [stylowanie i szablony tematu.](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

 Ponadto ważne jest, aby `Resources`zrozumieć , które są <xref:System.Windows.Style> zasadniczo, co umożliwia obiekty, takie jak i <xref:System.Windows.DataTemplate> być wielokrotnego użytku. Aby uzyskać więcej informacji na temat zasobów, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>Podstawowe informacje o tworzenie danych

 Aby zademonstrować, dlaczego <xref:System.Windows.DataTemplate> jest ważne, przejdźmy przez przykład wiązania danych. W tym przykładzie <xref:System.Windows.Controls.ListBox> mamy, który jest `Task` powiązany z listą obiektów. Każdy `Task` obiekt `TaskName` `Description` ma (ciąg), (ciąg), (int) `Priority` i `TaskType`właściwość typu `Enum` , `Home` `Work`która jest z wartościami i .

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>Bez tablicy ilościowej
 Bez <xref:System.Windows.DataTemplate>, <xref:System.Windows.Controls.ListBox> nasz obecnie wygląda tak:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 Co się dzieje jest to, że <xref:System.Windows.Controls.ListBox> bez żadnych `ToString` konkretnych instrukcji, domyślnie wywołania podczas próby wyświetlenia obiektów w kolekcji. W związku z `Task` tym jeśli `ToString` obiekt zastępuje <xref:System.Windows.Controls.ListBox> metodę, a następnie wyświetla reprezentację ciągu każdego obiektu źródłowego w kolekcji podstawowej.

 Na przykład jeśli `Task` klasa zastępuje `ToString` metodę w ten `name` sposób, gdzie `TaskName` jest pole właściwości:

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 Następnie <xref:System.Windows.Controls.ListBox> wygląda następująco:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 Jest to jednak ograniczenie i nieelastyczne. Ponadto, jeśli są związane z danymi XML, nie będzie `ToString`można zastąpić .

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>Definiowanie prostej tabliczki danych
 Rozwiązaniem jest zdefiniowanie <xref:System.Windows.DataTemplate>pliku . Jednym ze sposobów, aby <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> to zrobić, jest ustawienie właściwości na <xref:System.Windows.Controls.ListBox> . <xref:System.Windows.DataTemplate> To, co <xref:System.Windows.DataTemplate> określisz w strukturze wizualnej obiektu danych. Poniżej <xref:System.Windows.DataTemplate> jest dość proste. Dajemy instrukcje, że każdy <xref:System.Windows.Controls.TextBlock> element pojawia <xref:System.Windows.Controls.StackPanel>się jako trzy elementy w . Każdy <xref:System.Windows.Controls.TextBlock> element jest powiązany `Task` z właściwością klasy.

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 Podstawowe dane dla przykładów w tym temacie jest kolekcja obiektów CLR. Jeśli są wiążące z danymi XML, podstawowe pojęcia są takie same, ale istnieje niewielka różnica składni. Na przykład zamiast , `Path=TaskName`można ustawić <xref:System.Windows.Data.Binding.XPath%2A> `@TaskName` (jeśli `TaskName` jest atrybutem węzła XML).

 Teraz <xref:System.Windows.Controls.ListBox> wygląda następująco:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>Tworzenie tablicy datatemplate jako zasobu
 W powyższym przykładzie <xref:System.Windows.DataTemplate> zdefiniowaliśmy inline. Jest bardziej powszechne, aby zdefiniować go w sekcji zasobów, dzięki czemu może być obiekt wielokrotnegoużynia, jak w poniższym przykładzie:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Teraz można `myTaskTemplate` użyć jako zasobu, jak w poniższym przykładzie:

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 Ponieważ `myTaskTemplate` jest zasobem, można go teraz używać na innych <xref:System.Windows.DataTemplate> formantów, które mają właściwość, która przyjmuje typ. Jak pokazano powyżej, dla <xref:System.Windows.Controls.ItemsControl> obiektów, takich jak <xref:System.Windows.Controls.ListBox>, jest to właściwość. <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> Dla <xref:System.Windows.Controls.ContentControl> obiektów jest <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwością.

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>Właściwość DataType
 Klasa <xref:System.Windows.DataTemplate> ma <xref:System.Windows.DataTemplate.DataType%2A> właściwość, która jest <xref:System.Windows.Style.TargetType%2A> bardzo <xref:System.Windows.Style> podobna do właściwości klasy. W związku z tym zamiast `x:Key` określania for w powyższym <xref:System.Windows.DataTemplate> przykładzie, można wykonać następujące czynności:

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 Zostanie <xref:System.Windows.DataTemplate> to automatycznie zastosowane `Task` do wszystkich obiektów. Należy zauważyć, że `x:Key` w tym przypadku jest ustawiona niejawnie. W związku z tym <xref:System.Windows.DataTemplate> `x:Key` jeśli przypisać tę wartość, `x:Key` są <xref:System.Windows.DataTemplate> zastępowanie niejawne i nie zostaną zastosowane automatycznie.

 Jeśli są wiążące <xref:System.Windows.Controls.ContentControl> do `Task` kolekcji <xref:System.Windows.Controls.ContentControl> obiektów, nie <xref:System.Windows.DataTemplate> używa powyższe automatycznie. Jest to spowodowane powiązanie na <xref:System.Windows.Controls.ContentControl> potrzeby więcej informacji, aby odróżnić, czy chcesz powiązać z całą kolekcję lub poszczególnych obiektów. Jeśli <xref:System.Windows.Controls.ContentControl> śledzisz wybór <xref:System.Windows.Controls.ItemsControl> typu, możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Controls.ContentControl> powiązania na`/`" ", aby wskazać, że jesteś zainteresowany bieżącym elementem. Na przykład zobacz [Powiązanie z kolekcją i wyświetlanie informacji na podstawie zaznaczenia](how-to-bind-to-a-collection-and-display-information-based-on-selection.md). W przeciwnym razie należy <xref:System.Windows.DataTemplate> określić jawnie, ustawiając <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwość.

 Właściwość <xref:System.Windows.DataTemplate.DataType%2A> jest szczególnie przydatna, <xref:System.Windows.Data.CompositeCollection> gdy masz różnych typów obiektów danych. Na przykład zobacz [Implementowanie compositecollection](how-to-implement-a-compositecollection.md).

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>Dodawanie więcej do tablicy datatemplate
 Obecnie dane pojawiają się z niezbędnymi informacjami, ale na pewno jest miejsce na poprawę. Poprawmy prezentację, dodając a <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Grid>a <xref:System.Windows.Controls.TextBlock> i niektóre elementy opisujące wyświetlane dane.

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Poniższy zrzut <xref:System.Windows.Controls.ListBox> ekranu pokazuje <xref:System.Windows.DataTemplate>z tym zmodyfikowanym:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 Możemy ustawić <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.HorizontalAlignment.Stretch> na, <xref:System.Windows.Controls.ListBox> aby upewnić się, że szerokość elementów zajmuje całą przestrzeń:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 Z <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości ustawioną <xref:System.Windows.HorizontalAlignment.Stretch> <xref:System.Windows.Controls.ListBox> na , teraz wygląda tak:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>Stosowanie wartości właściwości za pomocą funkcji DataTriggers
 Obecna prezentacja nie mówi `Task` nam, czy jest to zadanie domowe, czy zadanie biurowe. Należy pamiętać, `Task` że `TaskType` obiekt `TaskType`ma właściwość typu , która `Home` `Work`jest wyliczeniem z wartościami i .

 W <xref:System.Windows.DataTrigger> poniższym przykładzie <xref:System.Windows.Controls.Border.BorderBrush%2A> ustawia element `border` o `Yellow` nazwie, jeśli `TaskType` właściwość jest `TaskType.Home`.

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 Nasza aplikacja wygląda teraz następująco. Zadania domowe są wyświetlane z żółtym obramowaniem, a zadania biurowe są wyświetlane z obramowaniem wodnym:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 W tym <xref:System.Windows.DataTrigger> przykładzie <xref:System.Windows.Setter> używa a, aby ustawić wartość właściwości. Klasy wyzwalacza mają <xref:System.Windows.TriggerBase.EnterActions%2A> <xref:System.Windows.TriggerBase.ExitActions%2A> również właściwości i, które umożliwiają uruchomienie zestawu akcji, takich jak animacje. Ponadto istnieje również <xref:System.Windows.MultiDataTrigger> klasa, która umożliwia stosowanie zmian na podstawie wielu wartości właściwości związanych z danymi.

 Alternatywnym sposobem osiągnięcia tego samego efektu jest powiązanie <xref:System.Windows.Controls.Border.BorderBrush%2A> właściwości z `TaskType` właściwością i użycie `TaskType` konwertera wartości do zwrócenia koloru na podstawie wartości. Tworzenie powyższego efektu za pomocą konwertera jest nieco bardziej wydajne pod względem wydajności. Ponadto tworzenie własnego konwertera zapewnia większą elastyczność, ponieważ dostarczasz własną logikę. Ostatecznie, która technika wybrać zależy od scenariusza i preferencji. Aby uzyskać informacje na temat pisania <xref:System.Windows.Data.IValueConverter>konwertera, zobacz .

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>Co należy do tablicy datatemplate?

W poprzednim przykładzie umieściliśmy wyzwalacz w <xref:System.Windows.DataTemplate> użyciu <xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType> właściwości. Wyzwalacz <xref:System.Windows.Setter> ustawia wartość właściwości elementu <xref:System.Windows.Controls.Border> (elementu), który znajduje się <xref:System.Windows.DataTemplate>w . Jednak jeśli właściwości, które `Setters` dotyczą nie są właściwości elementów, które <xref:System.Windows.DataTemplate>znajdują się w bieżącym, może być <xref:System.Windows.Style> bardziej odpowiednie <xref:System.Windows.Controls.ListBoxItem> do ustawiania właściwości przy użyciu, który jest dla klasy (jeśli formant, który są wiążące <xref:System.Windows.Controls.ListBox>jest ). Na przykład, jeśli <xref:System.Windows.Trigger> chcesz, aby <xref:System.Windows.UIElement.Opacity%2A> animowanie wartości elementu, gdy mysz wskazuje element, <xref:System.Windows.Controls.ListBoxItem> należy zdefiniować wyzwalacze w stylu. Na przykład zobacz [wprowadzenie do przykładu styliwania i tworzenia szablonów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

 Ogólnie rzecz biorąc należy <xref:System.Windows.DataTemplate> pamiętać, że jest stosowany <xref:System.Windows.Controls.ListBoxItem> do każdego z wygenerowanych (aby uzyskać więcej <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> informacji na temat sposobu i miejsca jego rzeczywistego zastosowania, zobacz stronę.). Twoje <xref:System.Windows.DataTemplate> dotyczy tylko prezentacji i wyglądu obiektów danych. W większości przypadków wszystkie inne aspekty prezentacji, takie jak to, jak <xref:System.Windows.Controls.ListBox> wygląda element, gdy jest wybrany lub jak <xref:System.Windows.DataTemplate>określa elementy, nie należą do definicji pliku . Na przykład zobacz [Stylowanie i tworzenie szablonów ItemsControl](#DataTemplating_ItemsControl) sekcji.

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Wybieranie tablicy danych na podstawie właściwości obiektu danych
 W sekcji [Właściwość DataType](#Styling_DataType) omówiliśmy, że można zdefiniować różne szablony danych dla różnych obiektów danych. Jest to szczególnie przydatne, <xref:System.Windows.Data.CompositeCollection> gdy masz różnych typów lub kolekcji z elementami różnych typów. W [użyj DataTriggers do apply property values](#DataTrigger_to_Apply_Property_Values) sekcji, wykazaliśmy, że jeśli masz kolekcję <xref:System.Windows.DataTemplate> tego samego typu obiektów danych można utworzyć, a następnie użyć wyzwalaczy do stosowania zmian na podstawie wartości właściwości każdego obiektu danych. Jednak wyzwalacze umożliwiają stosowanie wartości właściwości lub uruchamianie animacji, ale nie dają one elastyczności do rekonstrukcji struktury obiektów danych. Niektóre scenariusze mogą wymagać <xref:System.Windows.DataTemplate> utworzenia innego dla obiektów danych, które są tego samego typu, ale mają różne właściwości.

 Na przykład, `Task` gdy obiekt `Priority` ma `1`wartość , można nadać mu zupełnie inny wygląd, aby służyć jako alert dla siebie. W takim przypadku należy <xref:System.Windows.DataTemplate> utworzyć dla wyświetlania `Task` obiektów o wysokim priorytecie. Dodajmy następujące elementy <xref:System.Windows.DataTemplate> do sekcji zasobów:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

W tym przykładzie używa [DataTemplate.Resources](xref:System.Windows.FrameworkTemplate.Resources%2A) właściwości. Zasoby zdefiniowane w tej sekcji są <xref:System.Windows.DataTemplate>współużytkowane przez elementy w programie .

 Aby podać logikę, aby wybrać, <xref:System.Windows.DataTemplate> który ma być używany na podstawie `Priority` wartości obiektu danych, należy utworzyć podklasę <xref:System.Windows.Controls.DataTemplateSelector> i zastąpić <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metodę. W poniższym przykładzie metoda zawiera logikę, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> aby zwrócić `Priority` odpowiedni szablon na podstawie wartości właściwości. Szablon do zwrócenia znajduje się w zasobach <xref:System.Windows.Window> elementu otaczającego.

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 Następnie możemy zadeklarować `TaskListDataTemplateSelector` jako zasób:

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 Aby użyć zasobu selektora szablonów, przypisz <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> go do właściwości programu <xref:System.Windows.Controls.ListBox>. Wywołanie <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> metody `TaskListDataTemplateSelector` dla każdego z elementów w podstawowej kolekcji. Wywołanie przekazuje obiekt danych jako parametr elementu. Ten, <xref:System.Windows.DataTemplate> który jest zwracany przez metodę jest następnie stosowany do tego obiektu danych.

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 Po umieszczeniu selektora szablonów teraz pojawia się <xref:System.Windows.Controls.ListBox> w następujący sposób:

 ![Przykładowy zrzut ekranu z szablonami danych](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

Kończy się to naszą dyskusją na temat tego przykładu. Aby uzyskać pełną próbkę, zobacz [Wprowadzenie do przykładu tworzenia szablonów danych](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro).

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>Stylowanie i tworzenie szablonów elementówControl
 Mimo że <xref:System.Windows.Controls.ItemsControl> nie jest jedynym typem <xref:System.Windows.DataTemplate> formantu, który można użyć with, jest to bardzo typowy scenariusz do powiązania <xref:System.Windows.Controls.ItemsControl> do kolekcji. W sekcji [Co należy w dataTemplate](#what_belongs_in_datatemplate) omówiliśmy, że <xref:System.Windows.DataTemplate> definicja należy dotyczyć tylko prezentacji danych. Aby wiedzieć, kiedy nie nadaje się <xref:System.Windows.DataTemplate> do korzystania z niego, ważne jest, <xref:System.Windows.Controls.ItemsControl>aby zrozumieć inny styl i właściwości szablonu dostarczone przez . Poniższy przykład jest przeznaczony do zilustrowania funkcji każdej z tych właściwości. W <xref:System.Windows.Controls.ItemsControl> tym przykładzie jest `Tasks` powiązany z tej samej kolekcji, jak w poprzednim przykładzie. W celach demonstracyjnych style i szablony w tym przykładzie są zadeklarowane w linii.

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 Poniżej znajduje się zrzut ekranu przykładu, gdy jest renderowany:

 ![Przykładowy zrzut ekranu z elementami ItemsControl](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 Należy zauważyć, że <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>zamiast używać programu <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, można użyć pliku . Zapoznaj się z poprzednią sekcją, aby uzyskać przykład. Podobnie, zamiast używać programu <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, masz możliwość użycia <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>pliku .

 Dwie inne właściwości związane ze <xref:System.Windows.Controls.ItemsControl> stylem, które <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>nie są wyświetlane w tym miejscu, to i .

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>Obsługa danych hierarchicznych
 Do tej pory przyjrzeliśmy się tylko, jak powiązać i wyświetlić jedną kolekcję. Czasami masz kolekcję, która zawiera inne kolekcje. Klasa <xref:System.Windows.HierarchicalDataTemplate> jest przeznaczona do <xref:System.Windows.Controls.HeaderedItemsControl> użycia z typami do wyświetlania takich danych. W poniższym `ListLeagueList` przykładzie znajduje `League` się lista obiektów. Każdy `League` obiekt `Name` ma i `Division` zbiór obiektów. Każdy `Division` ma `Name` i zbiór `Team` obiektów, `Team` a każdy `Name`obiekt ma .

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 Przykład pokazuje, że za <xref:System.Windows.HierarchicalDataTemplate>pomocą programu , można łatwo wyświetlić dane listy, które zawierają inne listy. Poniżej znajduje się zrzut ekranu przykładu.

 ![Przykładowy zrzut ekranu z tablicą z danymi hierarchicznymi](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>Zobacz też

- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [Znajdź elementy generowane przez tablicę danych](how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView — style i szablony nagłówków kolumn — omówienie](../controls/gridview-column-header-styles-and-templates-overview.md)
