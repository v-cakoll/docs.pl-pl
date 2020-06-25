---
title: Tworzenie szablonu w WPF — .NET Desktop
description: Dowiedz się, jak utworzyć szablon formantu i odwołać się do niego w Windows Presentation Foundation i .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325722"
---
# <a name="create-a-template-for-a-control"></a>Tworzenie szablonu dla kontrolki

Za pomocą Windows Presentation Foundation (WPF) można dostosować strukturę i zachowanie istniejącej kontrolki przy użyciu własnego szablonu wielokrotnego użytku. Szablony mogą być stosowane globalnie do aplikacji, okien i stron lub bezpośrednio do kontrolek. Większość scenariuszy, które wymagają utworzenia nowej kontrolki, może być objęta tworzeniem nowego szablonu dla istniejącej kontrolki.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

W tym artykule opisano tworzenie nowej <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> kontrolki.

## <a name="when-to-create-a-controltemplate"></a>Kiedy należy utworzyć ControlTemplate

Kontrolki mają wiele właściwości, takich jak <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Control.Foreground%2A> , i <xref:System.Windows.Controls.Control.FontFamily%2A> . Te właściwości kontrolują różne aspekty wyglądu kontrolki, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone. Na przykład możesz ustawić <xref:System.Windows.Controls.Control.Foreground%2A> Właściwość na niebieską i <xref:System.Windows.Controls.Control.FontStyle%2A> kursywę w <xref:System.Windows.Controls.CheckBox> . Jeśli chcesz dostosować wygląd kontrolki poza tym, co ustawienie innych właściwości kontrolki może zrobić, Utwórz <xref:System.Windows.Controls.ControlTemplate> .

W większości interfejsów użytkownika przycisk ma ten sam wygląd ogólny: prostokąt z tekstem. Jeśli chcesz utworzyć przycisk zaokrąglony, można utworzyć nową kontrolkę, która dziedziczy po przycisku lub ponownie tworzy funkcję przycisku. Ponadto Nowa kontrolka użytkownika zapewni cykliczną wizualizację.

Można uniknąć tworzenia nowych kontrolek przez dostosowanie układu wizualizacji istniejącej kontrolki. Za pomocą przycisku zaokrąglonego utworzysz <xref:System.Windows.Controls.ControlTemplate> z żądanym układem wizualizacji.

Z drugiej strony, jeśli potrzebujesz kontrolki z nową funkcją, różnymi właściwościami i nowymi ustawieniami, utworzysz nowy <xref:System.Windows.Controls.UserControl> .

## <a name="prerequisites"></a>Wymagania wstępne

Utwórz nową aplikację WPF i w *MainWindow. XAML* (lub innym wybranym oknie) ustaw następujące właściwości dla **\<Window>** elementu:

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

Ustaw zawartość **\<Window>** elementu na następujący kod XAML:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Na końcu plik *MainWindow. XAML* powinien wyglądać podobnie do poniższego:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Jeśli aplikacja zostanie uruchomiona, wygląda następująco:

![Okno WPF z dwoma niestylowymi przyciskami](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Utwórz ControlTemplate

Najbardziej typowym sposobem deklarowania elementu <xref:System.Windows.Controls.ControlTemplate> jest jako zasobu w `Resources` sekcji w pliku XAML. Ponieważ szablony są zasobami, przestrzegają one tych samych reguł określania zakresu, które mają zastosowanie do wszystkich zasobów. Umieść po prostu, gdzie deklarujesz szablon, ma wpływ na miejsce, w którym można zastosować szablon. Na przykład, Jeśli zadeklarujesz szablon w głównym elemencie pliku XAML definicji aplikacji, szablon może być używany w dowolnym miejscu w aplikacji. Jeśli zdefiniujesz szablon w oknie, tylko kontrolki w tym oknie mogą używać szablonu.

Aby rozpocząć od, Dodaj `Window.Resources` element do pliku *MainWindow. XAML* :

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Utwórz nowy **\<ControlTemplate>** z zestawem następujących właściwości:

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

Ten szablon kontrolki będzie prosty:

- element główny formantu, a<xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Shapes.Ellipse>Aby narysować zaokrąglony wygląd przycisku
- a, <xref:System.Windows.Controls.ContentPresenter> Aby wyświetlić zawartość przycisku określonego przez użytkownika

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

Podczas tworzenia nowego programu <xref:System.Windows.Controls.ControlTemplate> nadal można użyć właściwości publicznych do zmiany wyglądu kontrolki. Rozszerzenie " [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) " tworzy powiązanie właściwości elementu, który znajduje się w <xref:System.Windows.Controls.ControlTemplate> Właściwości publicznej zdefiniowanej przez kontrolkę. W przypadku użycia [szablonubinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)należy włączyć właściwości kontrolki, aby działały jako parametry szablonu. Oznacza to, że po ustawieniu właściwości kontrolki ta wartość jest przenoszona do elementu, który ma element [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) .

### <a name="ellipse"></a>Elipsa

Zauważ, że **:::no-loc text="Fill":::** **:::no-loc text="Stroke":::** właściwości i **\<Ellipse>** elementu są powiązane z kontrolką <xref:System.Windows.Controls.Control.Foreground> i <xref:System.Windows.Controls.Control.Background> właściwościami.

### <a name="contentpresenter"></a>ContentPresenter

[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)Element zostanie również dodany do szablonu. Ponieważ ten szablon jest przeznaczony dla przycisku, weź pod uwagę, że przycisk dziedziczy z <xref:System.Windows.Controls.ContentControl> . Przycisk przedstawia zawartość elementu. Można ustawić dowolne elementy wewnątrz przycisku, np. zwykły tekst, lub nawet inną kontrolkę. Oba z poniższych elementów są prawidłowymi przyciskami:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

W obu powyższych przykładach tekst i pole wyboru są ustawiane jako właściwość [Button. Content](xref:System.Windows.Controls.ContentControl.Content) . Niezależnie od tego, co jest ustawione jako zawartość może być prezentowane za pomocą **\<ContentPresenter>** , co jest szablonem.

Jeśli <xref:System.Windows.Controls.ControlTemplate> zostanie zastosowany do <xref:System.Windows.Controls.ContentControl> typu, takiego jak `Button` , <xref:System.Windows.Controls.ContentPresenter> jest wyszukiwany w drzewie elementów. Jeśli `ContentPresenter` zostanie znaleziony, szablon automatycznie wiąże właściwość kontrolki <xref:System.Windows.Controls.ContentControl.Content> z `ContentPresenter` .

## <a name="use-the-template"></a>Korzystanie z szablonu

Znajdź przyciski, które zostały zadeklarowane na początku tego artykułu.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Ustaw właściwość drugiego przycisku <xref:System.Windows.Controls.Control.Template> na `roundbutton` zasób:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Jeśli uruchomisz projekt i przyjrzyjsz się wynikowi, zobaczysz, że przycisk ma zaokrąglone tło.

![Okno WPF z jednym szablonem przycisku owalne](media/create-apply-template/styled-button.png)

Być może zauważono, że przycisk nie jest okrąg, ale jest skośny. Ze względu na sposób **\<Ellipse>** działania elementu, zawsze rozszerza się, aby wypełnić dostępne miejsce. Zmień okrąg, zmieniając **:::no-loc text="width":::** wartości przycisku i **:::no-loc text="height":::** właściwości na tę samą wartość:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF z jednym cyklicznym przyciskiem szablonu](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Dodawanie wyzwalacza

Mimo że przycisk z zastosowanym szablonem wygląda inaczej, zachowuje się tak samo jak każdy inny przycisk. Jeśli naciśniesz przycisk, zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.ButtonBase.Click> . Można jednak zauważyć, że po przesunięciu wskaźnika myszy nad przycisk, wizualizacje przycisku nie są zmieniane. Te interakcje wizualne są definiowane przez szablon.

Przy użyciu dynamicznych zdarzeń i systemów właściwości, które zapewnia WPF, można obejrzeć określoną właściwość dla wartości, a następnie w razie potrzeby ponownie styl szablonu. W tym przykładzie zobaczysz <xref:System.Windows.UIElement.IsMouseOver> Właściwość przycisku. Gdy wskaźnik myszy znajduje się nad kontrolką, styl **\<Ellipse>** z nowym kolorem. Ten typ wyzwalacza jest znany jako *PropertyTrigger*.

Aby to działało, należy dodać nazwę do elementu, do którego można się **\<Ellipse>** odwołać. Nadaj jej nazwę **backgroundelement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Następnie Dodaj nową <xref:System.Windows.Trigger> do kolekcji [ControlTemplate. triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) . Wyzwalacz będzie obserwować `IsMouseOver` zdarzenie dla wartości `true` .

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Następnie Dodaj do elementu, **\<Setter>** **\<Trigger>** który zmienia właściwość **Fill** elementu **\<Ellipse>** na nowy kolor.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Uruchom projekt. Zauważ, że po przesunięciu wskaźnika myszy nad przycisk, kolorem **\<Ellipse>** zmian.

![wskaźnik myszy jest przesuwany nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Użyj stanu wizualnego

Stany wizualne są definiowane i wyzwalane przez kontrolkę. Na przykład, gdy wskaźnik myszy zostanie przesunięty nad formantem, `CommonStates.MouseOver` stan zostanie wyzwolony. Można animować zmiany właściwości w zależności od bieżącego stanu formantu. W poprzedniej sekcji, użyto **\<PropertyTrigger>** do zmiany pierwszego planu przycisku do `AliceBlue` momentu, gdy `IsMouseOver` Właściwość była `true` . Zamiast tego należy utworzyć stan wizualizacji, który Animuj zmianę tego koloru, zapewniając bezproblemowe przejście. Aby uzyskać więcej informacji na temat *VisualStates*, zobacz [Style i szablony w WPF](../fundamentals/styles-templates-overview.md#visual-states).

Aby skonwertować **\<PropertyTrigger>** do animowanego stanu wizualnego, najpierw usuń **\<ControlTemplate.Triggers>** element z szablonu.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Następnie w **\<Grid>** katalogu głównym szablonu kontrolki Dodaj **\<VisualStateManager.VisualStateGroups>** element z **\<VisualStateGroup>** dla elementu `CommonStates` . Zdefiniuj dwa stany `Normal` i `MouseOver` .

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Wszelkie animacje zdefiniowane w elemencie **\<VisualState>** są stosowane w momencie wyzwolenia tego stanu. Utwórz animacje dla każdego stanu. Animacje są umieszczane wewnątrz **\<Storyboard>** elementu. Aby uzyskać więcej informacji na temat scenorysów, zobacz [Omówienie scenorysów](../../framework/wpf/graphics-multimedia/storyboards-overview.md).

- Normalne

  Ten stan Animuj wypełnienie elipsy, przywracając go do `Background` koloru formantu.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  Ten stan pozwala animować kolor elipsy `Background` do nowego koloru: `Yellow` .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

**\<ControlTemplate>** Powinien teraz wyglądać podobnie do poniższego.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Uruchom projekt. Należy zauważyć, że po przesunięciu wskaźnika myszy nad przycisk, kolorem **\<Ellipse>** animacji.

![wskaźnik myszy jest przesuwany nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Następne kroki

- [Tworzenie stylu kontrolki w WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Style i szablony w WPF](../fundamentals/styles-templates-overview.md)
- [Przegląd zasobów XAML](../fundamentals/xaml-resources-define.md)
