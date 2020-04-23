---
title: Tworzenie szablonu w WPF - .NET Desktop
description: Dowiedz się, jak utworzyć i odwołać się do szablonu formantu w programie Windows Presentation Foundation i .NET Core.
author: thraka
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
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071249"
---
# <a name="create-a-template-for-a-control"></a>Tworzenie szablonu formantu

Za pomocą programu Windows Presentation Foundation (WPF) można dostosować strukturę wizualną i zachowanie istniejącego formantu za pomocą własnego szablonu wielokrotnegoużycia. Szablony mogą być stosowane globalnie do aplikacji, okien i stron lub bezpośrednio do formantów. Większość scenariuszy, które wymagają utworzenia nowego formantu mogą być objęte zamiast tworzenia nowego szablonu dla istniejącego formantu.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

W tym artykule zapoznajesz się <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.Button> tworzeniem nowego formantu.

## <a name="when-to-create-a-controltemplate"></a>Kiedy utworzyć płytę controltemplate

Formanty mają wiele <xref:System.Windows.Controls.Border.Background%2A>właściwości, takich jak , <xref:System.Windows.Controls.Control.Foreground%2A>i <xref:System.Windows.Controls.Control.FontFamily%2A>. Właściwości te kontrolują różne aspekty wyglądu formantu, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone. Na przykład można ustawić <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.Control.FontStyle%2A> na niebieską i <xref:System.Windows.Controls.CheckBox>kursywą na pliku . Jeśli chcesz dostosować wygląd formantu poza to, co może zrobić ustawienie innych <xref:System.Windows.Controls.ControlTemplate>właściwości formantu, należy utworzyć program .

W większości interfejsów użytkownika przycisk ma ten sam ogólny wygląd: prostokąt z tekstem. Jeśli chcesz utworzyć zaokrąglony przycisk, można utworzyć nowy formant, który dziedziczy z przycisku lub ponownie tworzy funkcjonalność przycisku. Ponadto nowy formant użytkownika zapewni cykliczne wizualizacje.

Można uniknąć tworzenia nowych formantów, dostosowując układ wizualny istniejącego formantu. Za pomocą zaokrąglonego przycisku tworzy się z żądanym układem <xref:System.Windows.Controls.ControlTemplate> wizualnym.

Z drugiej strony, jeśli potrzebujesz formantu z nową funkcjonalnością, różnymi właściwościami <xref:System.Windows.Controls.UserControl>i nowymi ustawieniami, utwórz nowy program .

## <a name="prerequisites"></a>Wymagania wstępne

Utwórz nową aplikację WPF i w *mainwindow.xaml* (lub innym oknie do wyboru) ustaw następujące właściwości w ** \<oknie>** element:

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

Ustaw zawartość elementu ** \<Window>** na następujący kod XAML:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Na końcu plik *MainWindow.xaml* powinien wyglądać podobnie do następującego:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

Po uruchomieniu aplikacji wygląda następująco:

![Okno WPF z dwoma niestyliowanymi przyciskami](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>Tworzenie panelu sterowania

Najczęstszym sposobem deklarowania <xref:System.Windows.Controls.ControlTemplate> a jest jako `Resources` zasób w sekcji w pliku XAML. Ponieważ szablony są zasobami, są one zgodne z tymi samymi regułami zakresu, które mają zastosowanie do wszystkich zasobów. Mówiąc prościej, jeśli zadeklarować szablon wpływa na to, gdzie szablon może być stosowany. Na przykład jeśli deklarujesz szablon w elemencie głównym pliku XAML definicji aplikacji, szablon może być używany w dowolnym miejscu w aplikacji. Jeśli szablon zostanie zdefiniowany w oknie, tylko formanty w tym oknie mogą używać szablonu.

Na początek dodaj `Window.Resources` element do pliku *MainWindow.xaml:*

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

Utwórz nową ** \<>ControlTemplate** z następującymi właściwościami:

|     |     |
| --- | --- |
| **x:Klucz**         | `roundbutton` |
| **TargetType**    | `Button` |

Ten szablon formantu będzie prosty:

- element główny formantu,<xref:System.Windows.Controls.Grid>
- a <xref:System.Windows.Shapes.Ellipse> narysować zaokrąglony wygląd przycisku
- a, <xref:System.Windows.Controls.ContentPresenter> aby wyświetlić zawartość przycisku określoną przez użytkownika

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>Powiązanie szablonów

Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>, nadal można użyć właściwości publicznych, aby zmienić wygląd formantu. Rozszerzenie znaczników [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) wiąże właściwość elementu, który <xref:System.Windows.Controls.ControlTemplate> znajduje się w właściwości publicznej, która jest zdefiniowana przez formant. Korzystając z [funkcji TemplateBinding,](../../framework/wpf/advanced/templatebinding-markup-extension.md)można włączyć właściwości formantu, aby działać jako parametry szablonu. Oznacza to, że gdy właściwość na formancie jest ustawiona, ta wartość jest przekazywana do elementu, który ma [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) na nim.

### <a name="ellipse"></a>Elipsy

Należy **:::no-loc text="Fill":::** zauważyć, **:::no-loc text="Stroke":::** że i właściwości ** \<elipsy>** element są powiązane z <xref:System.Windows.Controls.Control.Foreground> <xref:System.Windows.Controls.Control.Background> formantu i właściwości.

### <a name="contentpresenter"></a>Contentpresenter

Element [ \<>ContentPresenter](xref:System.Windows.Controls.ContentPresenter) jest również dodawany do szablonu. Ponieważ ten szablon jest przeznaczony dla przycisku, należy <xref:System.Windows.Controls.ContentControl>wziąć pod uwagę, że przycisk dziedziczy z . Przycisk przedstawia zawartość elementu. Możesz ustawić wszystko wewnątrz przycisku, takie jak zwykły tekst lub nawet inny formant. Oba z poniższych przycisków są prawidłowe:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

W obu poprzednich przykładach tekst i pole wyboru są ustawione jako [Właściwość Button.Content.](xref:System.Windows.Controls.ContentControl.Content) Cokolwiek jest ustawione, ponieważ zawartość ** \< **może być przedstawiona za pośrednictwem contentpreser>, czyli tego, co robi szablon.

Jeśli <xref:System.Windows.Controls.ControlTemplate> jest stosowany do <xref:System.Windows.Controls.ContentControl> typu, takich `Button`jak <xref:System.Windows.Controls.ContentPresenter> , a jest wyszukiwany w drzewie elementów. Jeśli `ContentPresenter` zostanie znaleziony, szablon automatycznie wiąże <xref:System.Windows.Controls.ContentControl.Content> właściwość formantu z . `ContentPresenter`

## <a name="use-the-template"></a>Korzystanie z szablonu

Znajdź przyciski, które zostały zadeklarowane na początku tego artykułu.

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

Ustaw <xref:System.Windows.Controls.Control.Template> właściwość drugiego przycisku `roundbutton` na zasób:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

Jeśli uruchomisz projekt i spojrzysz na wynik, zobaczysz, że przycisk ma zaokrąglone tło.

![Okno WPF z jednym szablonem owalny przycisk](media/create-apply-template/styled-button.png)

Być może zauważyłeś, że przycisk nie jest okrąg, ale jest pochylony. Ze względu na sposób ** \<działania elementu>elipsy,** zawsze rozszerza się, aby wypełnić dostępne miejsce. Umundurowanie okręgu, zmieniając **:::no-loc text="width":::** przycisk **:::no-loc text="height":::** i właściwości na tę samą wartość:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF z jednym okrągłym przyciskiem szablonu](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>Dodawanie wyzwalacza

Mimo że przycisk z zastosowanym szablonem wygląda inaczej, zachowuje się tak samo jak każdy inny przycisk. Po naciśnięciu przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie zostanie podpalene. Jednak być może zauważyłeś, że po przesunięciu wskaźnika myszy na przycisk wizualizacje przycisku nie zmieniają się. Te interakcje wizualne są zdefiniowane przez szablon.

Za pomocą dynamicznych systemów zdarzeń i właściwości, które zapewnia WPF, można oglądać określonej właściwości dla wartości, a następnie restyle szablonu w razie potrzeby. W tym przykładzie będziesz obserwować właściwości <xref:System.Windows.UIElement.IsMouseOver> przycisku. Gdy mysz jest nad formantem, styl ** \<Elipsy>** z nowym kolorem. Ten typ wyzwalacza jest znany jako *PropertyTrigger*.

Aby to zadziałało, musisz dodać nazwę do ** \<>elipsy,** do której można się odwołać. Nadaj mu nazwę **backgroundElement**.

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

Następnie dodaj nowy <xref:System.Windows.Trigger> do [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) kolekcji. Wyzwalacz będzie `IsMouseOver` obserwował zdarzenie `true`dla wartości .

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

Następnie dodaj ** \<seter>** do ** \<>wyzwalacza,** który zmienia **Fill** właściwości ** \<elipsy>** na nowy kolor.

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

Uruchom projekt. Należy zauważyć, że podczas przesuwania myszy na przycisk, kolor ** \<elipsy>** zmienia.

![mysz przesuwa się nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>Używanie funkcji VisualState

Stany wizualne są definiowane i wyzwalane przez formant. Na przykład, gdy mysz jest przenoszona `CommonStates.MouseOver` na górze formantu, stan jest wyzwalany. Zmiany właściwości można animować na podstawie bieżącego stanu formantu. W poprzedniej sekcji ** \<>PropertyTrigger** został użyty do zmiany pierwszego planu `AliceBlue` przycisku `IsMouseOver` na `true`kiedy właściwość była . Zamiast tego należy utworzyć stan wizualny, który animuje zmianę tego koloru, zapewniając płynne przejście. Aby uzyskać więcej informacji na temat *VisualStates*, zobacz [Style i szablony w WPF](../fundamentals/styles-templates-overview.md#visual-states).

Aby przekonwertować ** \<>PropertyTrigger** na animowany stan wizualny, najpierw usuń element ** \<ControlTemplate.Triggers>** z szablonu.

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

Następnie w ** \<katalogu** głównym>siatki szablonu formantu dodaj element ** \<VisualStateManager.VisualStateGroups>** za pomocą>`CommonStates` ** \<VisualStateGroup** dla . Zdefiniuj dwa stany `Normal` i `MouseOver`.

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

Wszystkie animacje zdefiniowane w ** \<VisualState>** są stosowane, gdy ten stan jest wyzwalany. Tworzenie animacji dla każdego stanu. Animacje są umieszczane wewnątrz ** \<scenorysu>** elementu. Aby uzyskać więcej informacji na temat scenochło posmówek, zobacz [Omówienie scenoki .](../../framework/wpf/graphics-multimedia/storyboards-overview.md)

- Normalne

  Ten stan animuje wypełnienie elipsy, przywracając go `Background` do koloru formantu.

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- Mouseover

  Ten stan animuje `Background` kolor elipsy do `Yellow`nowego koloru: .

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

** \<>ControlTemplate** powinien teraz wyglądać następująco.

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

Uruchom projekt. Należy zauważyć, że podczas przesuwania myszy na przycisk, kolor ** \<elipsy>** animuje.

![mysz przesuwa się nad przyciskiem WPF, aby zmienić kolor wypełnienia](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>Następne kroki

- [Tworzenie stylu formantu w WPF](../fundamentals/styles-templates-create-apply-style.md)
- [Style i szablony w wytęzianych w filtrze WPF](../fundamentals/styles-templates-overview.md)
- [Omówienie zasobów XAML](../fundamentals/xaml-resources-define.md)
