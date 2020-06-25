---
title: Style i szablony
description: Dowiedz się więcej o zasobach XAML w Windows Presentation Foundation (WPF) dla platformy .NET Core. Informacje o typach zasobów XAML związanych ze stylami i motywami.
author: adegeo
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: faa54e0a3c827717114ca6ca4f033c1c4c3acfa8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325773"
---
# <a name="styles-and-templates-in-wpf"></a>Style i szablony w WPF

Windows Presentation Foundation (WPF) style i tworzenia szablonów zapoznaj się z zestawem funkcji, które umożliwiają deweloperom i projektantom tworzenie atrakcyjnych wizualnie efektów i spójnego wyglądu ich produktów. Podczas dostosowywania wyglądu aplikacji należy użyć silnego stylu i modelu tworzenia szablonów, który umożliwia konserwację i udostępnianie wyglądu w ramach i między aplikacjami. WPF udostępnia ten model.

Inną funkcją modelu stylów WPF jest separacja prezentacji i logiki. Projektanci mogą korzystać z wyglądu aplikacji, używając tylko języka XAML w tym samym czasie, gdy deweloperzy pracują na logice programowania przy użyciu języka C# lub Visual Basic.

To omówienie koncentruje się na stylu i tworzenia szablonów aspektach aplikacji i nie omawia żadnych koncepcji dotyczących powiązań danych. Aby uzyskać informacje o powiązaniu danych, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).

Ważne jest zapoznanie się z zasobami, które umożliwiają ponownie używanie stylów i szablonów. Aby uzyskać więcej informacji o zasobach, zobacz [zasoby XAML](xaml-resources-define.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>Przykład

Przykładowy kod podany w tym omówieniu jest oparty na [prostej aplikacji do przeglądania zdjęć](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) pokazanej na poniższej ilustracji.

![Styl elementu ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

Ten prosty przykład fotografii używa stylów i tworzenia szablonów, aby utworzyć wizualnie atrakcyjny interfejs użytkownika. Przykład ma dwa <xref:System.Windows.Controls.TextBlock> elementy i <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z listą obrazów.

Pełny przykład można znaleźć w artykule [wprowadzenie do stylu i przykład tworzenia szablonów](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="styles"></a>Style

Można traktować <xref:System.Windows.Style> jako wygodny sposób zastosowania zestawu wartości właściwości do wielu elementów. Możesz użyć stylu dla dowolnego elementu, który pochodzi od lub <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> takich jak <xref:System.Windows.Window> lub <xref:System.Windows.Controls.Button> .

Najbardziej typowym sposobem deklarowania stylu jest jako zasób w `Resources` sekcji w pliku XAML. Ponieważ style są zasobami, przestrzegają one tych samych reguł określania zakresu, które mają zastosowanie do wszystkich zasobów. Umieść po prostu, gdzie deklarujesz styl, ma wpływ na miejsce, w którym można zastosować styl. Na przykład, Jeśli zadeklarujesz styl w głównym elemencie pliku XAML definicji aplikacji, styl może być używany w dowolnym miejscu w aplikacji.

Na przykład poniższy kod XAML deklaruje dwa style dla `TextBlock` , jeden automatycznie zastosowany do wszystkich `TextBlock` elementów i inne, które muszą być jawnie przywoływane.

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

Oto przykład stylów zadeklarowanych powyżej.

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![Style — bloki tekstu](./media/styles-and-templates-overview/stylingintro-textblocks.png)

Aby uzyskać więcej informacji, zobacz [Tworzenie stylu kontrolki](styles-templates-create-apply-style.md).

## <a name="controltemplates"></a>Elementy ControlTemplates

W WPF <xref:System.Windows.Controls.ControlTemplate> formant definiuje wygląd formantu. Można zmienić strukturę i wygląd kontrolki, definiując nowe <xref:System.Windows.Controls.ControlTemplate> i przypisując je do kontrolki. W wielu przypadkach szablony zapewniają wystarczającą elastyczność, dzięki czemu nie trzeba pisać własnych formantów niestandardowych.

Każdy formant ma przypisany do właściwości [Control. Template](xref:System.Windows.Controls.Control.Template) szablon domyślny. Szablon łączy wizualną prezentację formantu z możliwościami kontrolki. Ponieważ definiujesz szablon w języku XAML, można zmienić wygląd kontrolki bez pisania kodu. Każdy szablon jest przeznaczony dla konkretnej kontrolki, takiej jak <xref:System.Windows.Controls.Button> .

Często deklarujesz szablon jako zasób w `Resources` sekcji pliku XAML. Podobnie jak w przypadku wszystkich zasobów, mają zastosowanie reguły określania zakresu.

Szablony formantów są znacznie większe niż style. Wynika to z faktu, że szablon kontrolki ponownie zapisuje wygląd całej kontrolki, a styl po prostu stosuje zmiany właściwości do istniejącej kontrolki. Jednak ponieważ szablon kontrolki jest stosowany przez ustawienie właściwości [Control. Template](xref:System.Windows.Controls.Control.Template) , można użyć stylu do definiowania lub ustawiania szablonu.

Projektanci zwykle umożliwiają utworzenie kopii istniejącego szablonu i zmodyfikowanie go. Na przykład w projektancie programu Visual Studio WPF zaznacz `CheckBox` kontrolkę, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Edytuj szablon**  >  **Utwórz kopię**. To polecenie generuje *styl definiujący szablon*.

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

Edytowanie kopii szablonu to doskonały sposób, aby dowiedzieć się, jak działają szablony. Zamiast tworzyć nowy pusty szablon, można łatwiej edytować kopię i zmieniać kilka aspektów prezentacji wizualnej.

Aby zapoznać się z przykładem, zobacz [Tworzenie szablonu dla kontrolki](../themes/how-to-create-apply-template.md).

### <a name="templatebinding"></a>TemplateBinding

Być może zauważono, że zasób szablonu zdefiniowany w poprzedniej sekcji używa [rozszerzenia znaczników TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md). A `TemplateBinding` to zoptymalizowana postać powiązania dla scenariuszy szablonów, analogiczne do powiązania złożonego z `{Binding RelativeSource={RelativeSource TemplatedParent}}` . `TemplateBinding`przydaje się do powiązania części szablonu z właściwościami formantu. Na przykład każda kontrolka ma <xref:System.Windows.Controls.Control.BorderThickness> Właściwość. Użyj elementu, `TemplateBinding` Aby określić, który element w szablonie ma wpływ to ustawienie kontroli.

### <a name="contentcontrol-and-itemscontrol"></a>Elementu ContentControl i ItemsControl

Jeśli obiekt <xref:System.Windows.Controls.ContentPresenter> jest zadeklarowany w <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl> , <xref:System.Windows.Controls.ContentPresenter> zostanie automatycznie powiązany z <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.Content%2A> właściwościami i. Analogicznie, to jest w ramach programu, <xref:System.Windows.Controls.ItemsPresenter> <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> zostanie automatycznie powiązane z <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> właściwościami i.

## <a name="datatemplates"></a>Szablony datatemplates

W tej przykładowej aplikacji istnieje <xref:System.Windows.Controls.ListBox> formant, który jest powiązany z listą zdjęć.

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

Obecnie wygląda to następująco <xref:System.Windows.Controls.ListBox> .

![ListBox przed zastosowaniem szablonu](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

Większość formantów ma pewien typ zawartości i ta zawartość często pochodzi z danych, do których są powiązane. W tym przykładzie dane są listą zdjęć. W programie WPF należy użyć <xref:System.Windows.DataTemplate> do zdefiniowania wizualnej reprezentacji danych. W zasadzie zawartość umieszczona <xref:System.Windows.DataTemplate> w programie decyduje o tym, jak wyglądają dane w renderowanej aplikacji.

W naszej przykładowej aplikacji każdy `Photo` obiekt niestandardowy ma `Source` właściwość String, która określa ścieżkę pliku obrazu. Obecnie obiekty fotograficzne są wyświetlane jako ścieżki plików.

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

Aby zdjęcia pojawiły się jako obrazy, tworzysz <xref:System.Windows.DataTemplate> jako zasób.

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

Zauważ, że <xref:System.Windows.DataTemplate.DataType%2A> Właściwość jest podobna do <xref:System.Windows.Style.TargetType%2A> właściwości <xref:System.Windows.Style> . Jeśli <xref:System.Windows.DataTemplate> znajduje się w sekcji Resources (zasoby), podczas określania <xref:System.Windows.DataTemplate.DataType%2A> właściwości do typu i pomijania `x:Key` , <xref:System.Windows.DataTemplate> zostanie zastosowana za każdym razem, gdy ten typ zostanie wyświetlony. Zawsze masz opcję przypisywania <xref:System.Windows.DataTemplate> za pomocą `x:Key` a, a następnie ustaw ją jako `StaticResource` dla właściwości, które przyjmują <xref:System.Windows.DataTemplate> typy, takich jak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> Właściwość lub <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> Właściwość.

Zasadniczo, <xref:System.Windows.DataTemplate> w powyższym przykładzie definiuje, że za każdym razem `Photo` , gdy istnieje obiekt, powinien pojawić się jako <xref:System.Windows.Controls.Image> wewnątrz <xref:System.Windows.Controls.Border> . Dzięki temu <xref:System.Windows.DataTemplate> Nasza aplikacja wygląda teraz następująco.

![Obraz Zdjęcia](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

Model tworzenia szablonów danych udostępnia inne funkcje. Na przykład, Jeśli wyświetlasz dane kolekcji zawierające inne kolekcje przy użyciu <xref:System.Windows.Controls.HeaderedItemsControl> typu, takiego jak <xref:System.Windows.Controls.Menu> lub <xref:System.Windows.Controls.TreeView> , istnieje <xref:System.Windows.HierarchicalDataTemplate> . Inna funkcja tworzenia szablonów danych to <xref:System.Windows.Controls.DataTemplateSelector> , co umożliwia wybranie <xref:System.Windows.DataTemplate> użycia na podstawie logiki niestandardowej. Aby uzyskać więcej informacji, zobacz [Omówienie usługi Data tworzenia szablonów](../../framework/wpf/data/data-templating-overview.md), która zapewnia bardziej szczegółowe omówienie różnych funkcji tworzenia szablonów danych.

## <a name="triggers"></a>Wyzwalacze

Wyzwalacz ustawia właściwości lub uruchamia akcje, takie jak animacja, gdy zmienia się wartość właściwości lub gdy zdarzenie jest zgłaszane. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> , i <xref:System.Windows.DataTemplate> wszystkie mają `Triggers` Właściwość, która może zawierać zestaw wyzwalaczy. Istnieje kilka typów wyzwalaczy.

### <a name="propertytriggers"></a>PropertyTriggers

A <xref:System.Windows.Trigger> , który ustawia wartości właściwości lub uruchamia akcje na podstawie wartości właściwości, jest nazywany wyzwalaczem właściwości.

Aby zademonstrować sposób używania wyzwalaczy właściwości, można wprowadzać każdy <xref:System.Windows.Controls.ListBoxItem> częściowo przezroczysty, chyba że jest zaznaczone. Następujący styl ustawia <xref:System.Windows.UIElement.Opacity%2A> wartość <xref:System.Windows.Controls.ListBoxItem> do `0.5` . Gdy <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> Właściwość jest `true` , <xref:System.Windows.UIElement.Opacity%2A> jest ustawiona na `1.0` .

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

W tym przykładzie używa <xref:System.Windows.Trigger> do ustawiania wartości właściwości, ale należy pamiętać, że <xref:System.Windows.Trigger> Klasa ma również <xref:System.Windows.TriggerBase.EnterActions%2A> właściwości i <xref:System.Windows.TriggerBase.ExitActions%2A> , które umożliwiają wyzwalaczowi wykonywanie akcji.

Zauważ, że <xref:System.Windows.FrameworkElement.MaxHeight%2A> Właściwość <xref:System.Windows.Controls.ListBoxItem> jest ustawiona na `75` . Na poniższej ilustracji trzeci element to wybrany element.

![Styl elementu ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>Eventtriggers i Scenorysy

Inny typ wyzwalacza to <xref:System.Windows.EventTrigger> , który uruchamia zestaw akcji na podstawie wystąpienia zdarzenia. Na przykład następujące <xref:System.Windows.EventTrigger> obiekty określają, że gdy wskaźnik myszy zostanie przesunięty do <xref:System.Windows.Controls.ListBoxItem> , <xref:System.Windows.FrameworkElement.MaxHeight%2A> Właściwość jest animowany do wartości `90` w ciągu `0.2` drugiego okresu. Gdy wskaźnik myszy zostanie przesunięty z elementu, właściwość wraca do oryginalnej wartości w ciągu `1` sekundy. Należy zauważyć, że nie jest konieczne określenie <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wartości dla <xref:System.Windows.ContentElement.MouseLeave> animacji. Dzieje się tak, ponieważ animacja jest w stanie śledzić oryginalną wartość.

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

Aby uzyskać więcej informacji, zobacz [Omówienie scenorysów](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

Na poniższej ilustracji mysz wskazuje trzeci element.

![Przykładowy zrzut ekranu z stylem](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>Wielowyzwalacze, DataTriggers i MultiDataTriggers

Oprócz <xref:System.Windows.Trigger> i, istnieją <xref:System.Windows.EventTrigger> Inne typy wyzwalaczy. <xref:System.Windows.MultiTrigger>umożliwia ustawienie wartości właściwości na podstawie wielu warunków. Używasz <xref:System.Windows.DataTrigger> i <xref:System.Windows.MultiDataTrigger> gdy właściwość warunku jest powiązany z danymi.

## <a name="visual-states"></a>Stany wizualne

Kontrolki są zawsze w określonym **stanie**. Na przykład, gdy wskaźnik myszy przesuwa się nad powierzchnią kontrolki, formant jest uznawany za wspólny w stanie `MouseOver` . Kontrolka bez określonego stanu jest traktowana jako wspólna `Normal` . Stany są podzielone na grupy, a poprzednio wymienione Stany są częścią grupy Stanów `CommonStates` . Większość formantów ma dwie grupy stanów: `CommonStates` i `FocusStates` . Dla każdej grupy Stanów zastosowanej do kontrolki zawsze w jednym stanie każdej grupy, takiej jak `CommonStates.MouseOver` i `FocusStates.Unfocused` . Jednak kontrolka nie może znajdować się w dwóch różnych stanach w ramach tej samej grupy, takiej jak `CommonStates.Normal` i `CommonStates.Disabled` . Poniżej znajduje się tabela Stanów, która rozpoznaje i używa.

| Nazwa stanu wizualnego | Nazwa element VisualStateGroup | Opis |
| ---------------- | --------------------- | ----------- |
| Normalne           | CommonStates          | Stan domyślny. |
| MouseOver        | CommonStates          | Wskaźnik myszy znajduje się nad kontrolką. |
| Naciśnięte          | CommonStates          | Kontrolka zostanie naciśnięty. |
| Disabled (Wyłączony)         | CommonStates          | Kontrolka jest wyłączona. |
| Ustawiono fokus          | FocusStates           | Kontrolka ma fokus. |
| Bez fokusu        | FocusStates           | Kontrolka nie ma fokusu. |

Definiując a <xref:System.Windows.VisualStateManager?displayProperty=fullName> na element główny szablonu kontrolki, można wyzwolić animacje, gdy kontrolka przechodzi do określonego stanu. `VisualStateManager`Deklaruje, które kombinacje <xref:System.Windows.VisualStateGroup> i <xref:System.Windows.VisualState> do oglądania. Gdy kontrolka przejdzie do stanu czujka, animacja zdefiniowana przez `VisaulStateManager` jest uruchamiana.

Na przykład poniższy kod XAML przeczujuje `CommonStates.MouseOver` stan w celu animowania koloru wypełnienia elementu o nazwie `backgroundElement` . Gdy kontrolka powróci do `CommonStates.Normal` stanu, kolor wypełnienia elementu o nazwie `backgroundElement` zostanie przywrócony.

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

Aby uzyskać więcej informacji na temat scenorysów, zobacz [Omówienie scenorysów](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

## <a name="shared-resources-and-themes"></a>Udostępnione zasoby i motywy

Typowa aplikacja WPF może mieć wiele zasobów interfejsu użytkownika, które są stosowane w całej aplikacji. Zbiorczo ten zestaw zasobów może być traktowany jako motyw aplikacji. WPF zapewnia obsługę zasobów interfejsu użytkownika pakietu jako motywu przy użyciu słownika zasobów, który jest hermetyzowany jako <xref:System.Windows.ResourceDictionary> Klasa.

Motywy WPF są definiowane przy użyciu stylu i mechanizmu tworzenia szablonów, który jest udostępniany przez WPF do dostosowywania wizualizacji dowolnego elementu.

Zasoby motywów WPF są przechowywane w osadzonych słownikach zasobów. Te słowniki zasobów muszą być osadzone w podpisanym zestawie i mogą być osadzone w tym samym zestawie co sam kod lub w zestawie równoległym. W przypadku PresentationFramework.dll zestawu, który zawiera formanty WPF, zasoby motywu znajdują się w szeregu równoległych zestawów.

Motyw jest ostatnim miejscem, aby wyglądać podczas wyszukiwania stylu elementu. Zazwyczaj wyszukiwanie rozpocznie się, przeszukiwanie drzewa elementów dla odpowiedniego zasobu, a następnie wyszukanie w kolekcji zasobów aplikacji i zakończenie zapytania do systemu. Dzięki temu deweloperzy aplikacji mogą ponownie zdefiniować styl dla każdego obiektu na poziomie drzewa lub aplikacji przed osiągnięciem motywu.

Słowniki zasobów można definiować jako pojedyncze pliki, które umożliwiają ponowne użycie motywu w wielu aplikacjach. Można również tworzyć motywy do wymiany przez definiowanie wielu słowników zasobów, które udostępniają te same typy zasobów, ale z różnymi wartościami. Zalecanym podejściem do nakładania się aplikacji jest ponowne zdefiniowanie tych stylów lub innych zasobów na poziomie aplikacji.

Aby udostępnić zestaw zasobów, w tym style i szablony, między aplikacjami, można utworzyć plik XAML i zdefiniować <xref:System.Windows.ResourceDictionary> zawierający odwołanie do `shared.xaml` pliku.

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

Jest to współużytkowanie `shared.xaml` , które definiuje, <xref:System.Windows.ResourceDictionary> który zawiera zestaw stylów i zasobów pędzla, co umożliwia kontrolowanie spójnego wyglądu formantów w aplikacji.

Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../../framework/wpf/advanced/merged-resource-dictionaries.md).

Jeśli tworzysz motyw dla kontrolki niestandardowej, zapoznaj się z sekcją **Definiowanie zasobów na poziomie motywu** w temacie [Omówienie tworzenia kontrolek](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level).

## <a name="see-also"></a>Zobacz też

- [Pakuj URI w WPF](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [Instrukcje: znajdowanie elementów generowanych przez element ControlTemplate](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Znajdowanie elementów generowanych przez szablon](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
