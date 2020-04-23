---
title: Style i szablony
description: Dowiedz się więcej o zasobach XAML w programie Windows Presentation Foundation (WPF) dla platformy .NET Core. Opis typów zasobów XAML związanych ze stylami i motywami.
author: thraka
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f845e739ec3cae502d1e4fd6631f987c5364a42e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071886"
---
# <a name="styles-and-templates-in-wpf"></a>Style i szablony w wytęzianych w filtrze WPF

Styl i szablony programu Windows Presentation Foundation (WPF) odnoszą się do zestawu funkcji, które umożliwiają deweloperom i projektantom tworzenie atrakcyjnych wizualnie efektów i spójnego wyglądu produktu. Podczas dostosowywania wyglądu aplikacji, chcesz silny styl i szablonów modelu, który umożliwia utrzymanie i udostępnianie wyglądu w aplikacjach i między nimi. WPF WPF udostępnia tego modelu.

Inną cechą modelu stylizacji WPF jest oddzielenie prezentacji i logiki. Projektanci mogą pracować nad wyglądem aplikacji przy użyciu tylko XAML w tym samym czasie, że deweloperzy pracują nad logiką programowania przy użyciu języka C# lub Visual Basic.

Ten przegląd koncentruje się na stylowanie i templating aspektów aplikacji i nie omawia żadnych pojęć wiązania danych. Aby uzyskać informacje na temat powiązania danych, zobacz [Omówienie powiązania danych](../data/data-binding-overview.md).

Ważne jest, aby zrozumieć zasoby, które umożliwiają ponowne korzystanie ze stylów i szablonów. Aby uzyskać więcej informacji o zasobach, zobacz [Zasoby XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Przykład

Przykładowy kod podany w tym przeglądzie jest oparty na [prostej aplikacji do przeglądania zdjęć](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) pokazanej na poniższej ilustracji.

![Stylizowana lista Wyświetl](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Ta prosta próbka zdjęć wykorzystuje styl i szablony, aby stworzyć atrakcyjne wizualnie środowisko użytkownika. Przykład ma <xref:System.Windows.Controls.TextBlock> dwa elementy <xref:System.Windows.Controls.ListBox> i formant, który jest powiązany z listą obrazów.

Aby uzyskać pełną próbkę, zobacz [Wprowadzenie do stylizowania i próbkowania szablonów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Style

Można myśleć <xref:System.Windows.Style> jako wygodny sposób, aby zastosować zestaw wartości właściwości do wielu elementów. Można użyć stylu na dowolnym elemencie, <xref:System.Windows.Window> który <xref:System.Windows.Controls.Button>wywodzi się z <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> takiego jak lub .

Najczęstszym sposobem deklarowania stylu jest jako `Resources` zasób w sekcji w pliku XAML. Ponieważ style są zasobami, są one zgodne z tymi samymi regułami zakresu, które mają zastosowanie do wszystkich zasobów. Mówiąc prościej, gdzie deklarujesz styl wpływa na to, gdzie można zastosować styl. Na przykład jeśli deklarujesz styl w elemencie głównym pliku XAML definicji aplikacji, styl może być używany w dowolnym miejscu w aplikacji.

Na przykład następujący kod XAML deklaruje dwa `TextBlock`style dla , jeden `TextBlock` automatycznie stosowane do wszystkich elementów i inny, który musi być jawnie odwołuje.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Oto przykład stylów zadeklarowanych powyżej używane.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Stylizowane bloki tekstowe](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Aby uzyskać więcej informacji, zobacz [Tworzenie stylu formantu](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>Płyty sterujące

W WPF <xref:System.Windows.Controls.ControlTemplate> WPF formantu definiuje wygląd formantu. Można zmienić strukturę i wygląd formantu, definiując nowy <xref:System.Windows.Controls.ControlTemplate> i przypisując go do formantu. W wielu przypadkach szablony zapewniają wystarczającą elastyczność, dzięki czemu nie trzeba pisać własne formanty niestandardowe.

Każdy formant ma domyślny szablon przypisany do [właściwości Control.Template.](xref:System.Windows.Controls.Control.Template) Szablon łączy wizualną prezentację formantu z możliwościami formantu. Ponieważ definiujesz szablon w XAML, można zmienić wygląd formantu bez pisania kodu. Każdy szablon jest przeznaczony dla określonego <xref:System.Windows.Controls.Button>formantu, takiego jak .

Zazwyczaj deklarujesz szablon jako zasób w `Resources` sekcji pliku XAML. Podobnie jak w przypadku wszystkich zasobów, obowiązują reguły zakresu.

Szablony kontroli są o wiele bardziej zaangażowane niż styl. Dzieje się tak, ponieważ szablon formantu przepisuje wygląd całego formantu, podczas gdy styl po prostu stosuje zmiany właściwości do istniejącego formantu. Jednak ponieważ szablon formantu jest stosowany przez ustawienie [Control.Template](xref:System.Windows.Controls.Control.Template) właściwości, można użyć stylu do definiowania lub ustawiania szablonu.

Projektanci zazwyczaj umożliwiają utworzenie kopii istniejącego szablonu i zmodyfikowanie go. Na przykład w projektancie WPF programu `CheckBox` Visual Studio wybierz formant, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Edytuj szablon** > **Utwórz kopię**. To polecenie generuje *styl definiujący szablon*.

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

Edytowanie kopii szablonu to świetny sposób, aby dowiedzieć się, jak działają szablony. Zamiast tworzyć nowy pusty szablon, łatwiej jest edytować kopię i zmienić kilka aspektów prezentacji wizualnej.

Na przykład zobacz [Tworzenie szablonu formantu](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>Powiązanie szablonów

Być może zauważyłeś, że zasób szablonu zdefiniowany w poprzedniej sekcji używa [rozszerzenia znaczników TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md). A `TemplateBinding` jest zoptymalizowaną formą powiązania dla scenariuszy szablonów, analogiczną do powiązania skonstruowanego za pomocą `{Binding RelativeSource={RelativeSource TemplatedParent}}`programu . `TemplateBinding`jest przydatne dla wiązań części szablonu do właściwości formantu. Na przykład każdy formant ma <xref:System.Windows.Controls.Control.BorderThickness> właściwość. Użyj `TemplateBinding` a, aby zarządzać, który element w szablonie ma wpływ na to ustawienie formantu.

### <a name="contentcontrol-and-itemscontrol"></a>Kontrola zawartości i elementyControl

Jeśli <xref:System.Windows.Controls.ContentPresenter> a jest <xref:System.Windows.Controls.ControlTemplate> zadeklarowany <xref:System.Windows.Controls.ContentControl>w <xref:System.Windows.Controls.ContentPresenter> of, będzie <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> automatycznie <xref:System.Windows.Controls.ContentControl.Content%2A> powiązać z i właściwości. Podobnie, który <xref:System.Windows.Controls.ItemsPresenter> znajduje się <xref:System.Windows.Controls.ControlTemplate> w <xref:System.Windows.Controls.ItemsControl> woli automatycznie powiązać z <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> i <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwości.

## <a name="datatemplates"></a>Tablice z danymi

W tej przykładowej aplikacji <xref:System.Windows.Controls.ListBox> istnieje formant, który jest powiązany z listą zdjęć.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Obecnie <xref:System.Windows.Controls.ListBox> wygląda to następująco.

![ListBox przed zastosowaniem szablonu](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Większość formantów ma jakiś typ zawartości, a zawartość często pochodzi z danych, które są wiązane. W tym przykładzie dane są listą zdjęć. W WPF, należy <xref:System.Windows.DataTemplate> użyć do zdefiniowania wizualnej reprezentacji danych. Zasadniczo to, co <xref:System.Windows.DataTemplate> można umieścić w określa, jak dane wyglądają w renderowanej aplikacji.

W naszej przykładowej `Photo` aplikacji każdy `Source` obiekt niestandardowy ma właściwość ciągu typu, która określa ścieżkę pliku obrazu. Obecnie obiekty zdjęć są wyświetlane jako ścieżki plików.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Aby zdjęcia były wyświetlane jako obrazy, tworzysz <xref:System.Windows.DataTemplate> jako zasób.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Należy zauważyć, że <xref:System.Windows.DataTemplate.DataType%2A> nieruchomość <xref:System.Windows.Style.TargetType%2A> jest <xref:System.Windows.Style>podobna do właściwości . Jeśli <xref:System.Windows.DataTemplate> znajduje się w sekcji zasobów, <xref:System.Windows.DataTemplate.DataType%2A> po określeniu właściwości `x:Key`do <xref:System.Windows.DataTemplate> typu i pominąć , jest stosowany za każdym razem, gdy pojawi się ten typ. Zawsze masz możliwość przypisania <xref:System.Windows.DataTemplate> z `x:Key` an, a `StaticResource` następnie ustawić go <xref:System.Windows.DataTemplate> jako dla <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> właściwości, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> które przyjmują typy, takie jak właściwość lub właściwość.

Zasadniczo <xref:System.Windows.DataTemplate> w powyższym przykładzie definiuje się, `Photo` że gdy istnieje <xref:System.Windows.Controls.Image> obiekt, <xref:System.Windows.Controls.Border>powinien pojawić się jako wewnątrz . Dzięki <xref:System.Windows.DataTemplate>temu nasza aplikacja wygląda teraz tak.

![Zdjęcie](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Model szablonów danych zawiera inne funkcje. Na przykład, jeśli są wyświetlane dane zbierania, <xref:System.Windows.Controls.HeaderedItemsControl> który zawiera <xref:System.Windows.Controls.Menu> inne <xref:System.Windows.Controls.TreeView>kolekcje przy <xref:System.Windows.HierarchicalDataTemplate>użyciu typu, takich jak a lub , istnieje . Inną funkcją tworzenia szablonów <xref:System.Windows.Controls.DataTemplateSelector>danych jest , <xref:System.Windows.DataTemplate> który pozwala wybrać do użycia w oparciu o niestandardową logikę. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia szablonów danych](../../framework/wpf/data/data-templating-overview.md), który zawiera bardziej szczegółowe omówienie różnych funkcji tworzenia szablonów danych.

## <a name="triggers"></a>Wyzwalacze

Wyzwalacz ustawia właściwości lub uruchamia akcje, takie jak animacja, gdy zmienia się wartość właściwości lub gdy zdarzenie jest wywoływane. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>a <xref:System.Windows.DataTemplate> wszystkie `Triggers` mają właściwość, która może zawierać zestaw wyzwalaczy. Istnieje kilka typów wyzwalaczy.

### <a name="propertytriggers"></a>WłaściwościTriggers

A, <xref:System.Windows.Trigger> który ustawia wartości właściwości lub uruchamia akcje na podstawie wartości właściwości jest nazywany wyzwalacz właściwości.

Aby zademonstrować sposób używania wyzwalaczy <xref:System.Windows.Controls.ListBoxItem> właściwości, można zrobić każdy częściowo przezroczysty, chyba że jest zaznaczone. Poniższy styl <xref:System.Windows.UIElement.Opacity%2A> ustawia wartość <xref:System.Windows.Controls.ListBoxItem> `0.5`a do . Gdy <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> właściwość `true`jest , <xref:System.Windows.UIElement.Opacity%2A> jednak `1.0`jest ustawiona na .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

W tym <xref:System.Windows.Trigger> przykładzie użyto do ustawiania <xref:System.Windows.Trigger> wartości właściwości, <xref:System.Windows.TriggerBase.EnterActions%2A> <xref:System.Windows.TriggerBase.ExitActions%2A> ale należy zauważyć, że klasa ma również właściwości i, które umożliwiają wyzwalacz do wykonywania akcji.

Należy zauważyć, <xref:System.Windows.FrameworkElement.MaxHeight%2A> że <xref:System.Windows.Controls.ListBoxItem> właściwość `75`jest ustawiona na . Na poniższej ilustracji trzeci element jest zaznaczonym elementem.

![Stylizowana lista Wyświetl](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTriggers i scenorysy

Innym typem <xref:System.Windows.EventTrigger>wyzwalacza jest , który uruchamia zestaw akcji na podstawie wystąpienia zdarzenia. Na przykład następujące <xref:System.Windows.EventTrigger> obiekty określają, że po <xref:System.Windows.Controls.ListBoxItem>wejściu <xref:System.Windows.FrameworkElement.MaxHeight%2A> wskaźnika myszy do `90` właściwości `0.2` animuje się do wartości z okresu ponad drugiego. Gdy mysz odchodzi od elementu, właściwość zwraca oryginalną `1` wartość w okresie sekundy. Należy zauważyć, jak nie <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> jest konieczne <xref:System.Windows.ContentElement.MouseLeave> określenie wartości animacji. Jest to spowodowane animacji jest w stanie śledzić oryginalną wartość.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Aby uzyskać więcej informacji, zobacz [omówienie scenoki](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Na poniższej ilustracji mysz wskazuje trzeci element.

![Przykładowy zrzut ekranu przedstawiający styl](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers i MultiDataTriggers

Oprócz <xref:System.Windows.Trigger> i <xref:System.Windows.EventTrigger>, istnieją inne rodzaje wyzwalaczy. <xref:System.Windows.MultiTrigger>umożliwia ustawienie wartości właściwości na podstawie wielu warunków. Używasz <xref:System.Windows.DataTrigger> <xref:System.Windows.MultiDataTrigger> i gdy właściwość warunku jest powiązana z danymi.

## <a name="visual-states"></a>Stany wizualne

Formanty są zawsze w określonym **stanie**. Na przykład, gdy mysz przesuwa się nad powierzchnią formantu, formant jest uważany za w stanie . `MouseOver` Formant bez określonego stanu jest uważany `Normal` za w stanie wspólnego. Państwa członkowskie są podzielone na grupy, a wcześniej wymienione `CommonStates`państwa są częścią grupy państwowej. Większość kontrole ma dwie `CommonStates` `FocusStates`grupy państw: i . Z każdej grupy stanów zastosowanej do formantu formant jest zawsze `CommonStates.MouseOver` `FocusStates.Unfocused`w jednym stanie każdej grupy, na przykład i . Jednak formant nie może znajdować się w dwóch różnych `CommonStates.Normal` stanach w tej samej grupie, takich jak i `CommonStates.Disabled`. Oto tabela stanów, które większość formantów rozpoznaje i używa.

| Nazwa visualstate | Nazwa grupy programu VisualStateGroup | Opis |
| ---------------- | --------------------- | ----------- |
| Normalne           | CommonStates (CommonStates)          | Stan domyślny. |
| Mouseover        | CommonStates (CommonStates)          | Wskaźnik myszy jest umieszczony nad formantem. |
| Naciśnięte          | CommonStates (CommonStates)          | Formant jest wciśnięty. |
| Disabled (Wyłączony)         | CommonStates (CommonStates)          | Formant jest wyłączony. |
| Ustawiono fokus          | FocusStates (Stan ostrości)           | Formant ma fokus. |
| Unfocused        | FocusStates (Stan ostrości)           | Formant nie ma fokusu. |

Definiując <xref:System.Windows.VisualStateManager?displayProperty=fullName> na element główny szablonu formantu, można wyzwolić animacje, gdy formant wejdzie w określony stan. Deklaruje, `VisualStateManager` które kombinacje <xref:System.Windows.VisualStateGroup> <xref:System.Windows.VisualState> i oglądać. Gdy formant wchodzi w stan obserwowanego, `VisaulStateManager` uruchamiana jest animacja zdefiniowana przez.

Na przykład następujący kod XAML `CommonStates.MouseOver` obserwuje stan, aby animować `backgroundElement`kolor wypełnienia elementu o nazwie . Gdy formant powraca `CommonStates.Normal` do stanu, kolor wypełnienia `backgroundElement` elementu o nazwie jest przywracany.

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

Aby uzyskać więcej informacji na temat scenochło posmówek, zobacz [Omówienie scenoki .](../../framework/wpf/graphics-multimedia/storyboards-overview.md)

## <a name="shared-resources-and-themes"></a>Zasoby udostępnione i motywy

Typowa aplikacja WPF może mieć wiele zasobów interfejsu użytkownika, które są stosowane w całej aplikacji. Łącznie ten zestaw zasobów można uznać za motyw dla aplikacji. WPF WPF zapewnia obsługę pakowania zasobów interfejsu użytkownika jako motyw przy użyciu <xref:System.Windows.ResourceDictionary> słownika zasobów, który jest hermetyzowany jako klasa.

Motywy WPF są definiowane przy użyciu mechanizmu stylizowania i szablonów, który udostępnia WPF w celu dostosowania wizualizacji dowolnego elementu.

Zasoby motywu WPF są przechowywane w słownikach osadzonych zasobów. Te słowniki zasobów muszą być osadzone w zestawie podpisane i mogą być osadzone w tym samym zestawie co sam kod lub w zestawie side-by-side. W przypadku presentationframework.dll zestaw, który zawiera formanty WPF, zasoby motywu znajdują się w serii zestawów side-by-side.

Motyw staje się ostatnim miejscem, w którym można szukać podczas wyszukiwania stylu elementu. Zazwyczaj wyszukiwanie rozpocznie się od przechodzenia w górę drzewa elementów w poszukiwaniu odpowiedniego zasobu, a następnie poszukaj w kolekcji zasobów aplikacji i wreszcie zapytanie systemu. Daje to deweloperom aplikacji możliwość ponownego zdefiniowania stylu dla dowolnego obiektu na poziomie drzewa lub aplikacji przed osiągnięciem motywu.

Słowniki zasobów można zdefiniować jako pojedyncze pliki, które umożliwiają ponowne użycie motywu w wielu aplikacjach. Można również utworzyć wymienne motywy, definiując wiele słowników zasobów, które zapewniają te same typy zasobów, ale z różnymi wartościami. Ponowne zdefiniowanie tych stylów lub innych zasobów na poziomie aplikacji jest zalecane podejście do skórowania aplikacji.

Aby udostępnić zestaw zasobów, w tym style i szablony, między aplikacjami, <xref:System.Windows.ResourceDictionary> można utworzyć `shared.xaml` plik XAML i zdefiniować, który zawiera odwołanie do pliku.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Jest to udostępnianie `shared.xaml`, który sam <xref:System.Windows.ResourceDictionary> definiuje, który zawiera zestaw zasobów stylu i pędzla, który umożliwia formantów w aplikacji, aby mieć spójny wygląd.

Aby uzyskać więcej informacji, zobacz [Scalone słowniki zasobów](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Jeśli tworzysz motyw dla formantu niestandardowego, zobacz **Definiowanie zasobów w** sekcji poziom motywu w [przeglądzie tworzenia formantu](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).

## <a name="see-also"></a>Zobacz też

- [Pakuj URI w WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Instrukcje: znajdowanie elementów generowanych przez ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Znajdź elementy generowane przez tablicę danych](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
