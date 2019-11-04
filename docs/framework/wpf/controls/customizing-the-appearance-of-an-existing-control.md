---
title: Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 6d7401f9614e663351968dc6a2f85548735a176d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460421"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> określa strukturę wizualizacji i wizualne zachowanie kontrolki. Możesz dostosować wygląd kontrolki, nadając jej nową <xref:System.Windows.Controls.ControlTemplate>. Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>zastępujesz wygląd istniejącej kontrolki bez zmiany jej funkcjonalności. Na przykład można sprawić, aby przyciski w aplikacji były zaokrąglane zamiast domyślnego kształtu kwadratowego, ale przycisk nadal wywołuje zdarzenie <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

 W tym temacie wyjaśniono różne części <xref:System.Windows.Controls.ControlTemplate>, zademonstrowano tworzenie prostego <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>i wyjaśniono, jak zrozumieć umowę kontrolną kontrolki, aby można było dostosować jej wygląd. Ze względu na to, że tworzysz <xref:System.Windows.Controls.ControlTemplate> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można zmienić wygląd formantu bez pisania kodu. Można również użyć projektanta, takiego jak Blend for Visual Studio, do tworzenia szablonów kontrolek niestandardowych. W tym temacie przedstawiono przykłady w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], które dostosowują wygląd <xref:System.Windows.Controls.Button> i przedstawiono pełny przykład na końcu tematu. Aby uzyskać więcej informacji o korzystaniu z Blend for Visual Studio, zobacz [Określanie stylu kontrolki, która obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).

 Na poniższych ilustracjach przedstawiono <xref:System.Windows.Controls.Button>, która używa <xref:System.Windows.Controls.ControlTemplate> utworzonego w tym temacie.

 ![Przycisk z szablonem kontrolki niestandardowej.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Przycisk, który używa szablonu kontrolki niestandardowej

 ![Przycisk z czerwonym obramowaniem.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Przycisk, który używa niestandardowego szablonu kontrolki i ma wskaźnik myszy nad nim

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne
 W tym temacie założono, że rozumiesz, jak tworzyć i używać kontrolek i stylów, jak opisano w [kontrolkach](index.md). Koncepcje omówione w tym temacie dotyczą elementów, które dziedziczą z klasy <xref:System.Windows.Controls.Control>, z wyjątkiem <xref:System.Windows.Controls.UserControl>. Nie można zastosować <xref:System.Windows.Controls.ControlTemplate> do <xref:System.Windows.Controls.UserControl>.

<a name="when_you_should_create_a_controltemplate"></a>
## <a name="when-you-should-create-a-controltemplate"></a>Kiedy należy utworzyć ControlTemplate
 Kontrolki mają wiele właściwości, takich jak <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>i <xref:System.Windows.Controls.Control.FontFamily%2A>, które można ustawić w celu określenia różnych aspektów wyglądu kontrolki, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone. Na przykład możesz ustawić właściwość <xref:System.Windows.Controls.Control.Foreground%2A> na niebieską i <xref:System.Windows.Controls.Control.FontStyle%2A> na kursywę w <xref:System.Windows.Controls.CheckBox>.

 Bez możliwości tworzenia nowych <xref:System.Windows.Controls.ControlTemplate> dla kontrolek wszystkie kontrolki w każdej aplikacji opartej na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]będą miały ten sam wygląd ogólny, co ograniczy możliwość tworzenia aplikacji z niestandardowym wyglądem i działaniem. Domyślnie każda <xref:System.Windows.Controls.CheckBox> ma podobne cechy. Na przykład zawartość <xref:System.Windows.Controls.CheckBox> jest zawsze z prawej strony wskaźnika wyboru, a znacznik wyboru jest zawsze używany, aby wskazać, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone.

 Tworzysz <xref:System.Windows.Controls.ControlTemplate>, gdy chcesz dostosować wygląd kontrolki poza ustawieniem, jakie inne właściwości kontrolki będą wykonywać. W przykładzie <xref:System.Windows.Controls.CheckBox>Załóżmy, że chcesz, aby zawartość pola wyboru była większa niż wskaźnik wyboru, i chcesz, aby znak X wskazywał, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone. Te zmiany należy określić w <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox>.

 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.CheckBox>, która używa <xref:System.Windows.Controls.ControlTemplate>domyślnej.

 ![Pole wyboru z domyślnym szablonem formantu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Pole wyboru używające domyślnego szablonu kontrolki

 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.CheckBox>, które używają niestandardowych <xref:System.Windows.Controls.ControlTemplate> do umieszczania zawartości <xref:System.Windows.Controls.CheckBox> powyżej wskaźnika wyboru i wyświetlania X po zaznaczeniu <xref:System.Windows.Controls.CheckBox>.

 ![Pole wyboru z szablonem niestandardowej kontrolki.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Pole wyboru, które używa szablonu kontrolki niestandardowej

 <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.CheckBox> w tym przykładzie jest stosunkowo skomplikowany, więc w tym temacie jest wykorzystywany prostszy przykład tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.

<a name="changing_the_visual_structure_of_a_control"></a>
## <a name="changing-the-visual-structure-of-a-control"></a>Zmiana struktury wizualnej kontrolki
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], formant jest często złożonymi obiektami <xref:System.Windows.FrameworkElement>. Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>należy połączyć obiekty <xref:System.Windows.FrameworkElement> w celu utworzenia jednej kontrolki. <xref:System.Windows.Controls.ControlTemplate> musi mieć tylko jeden <xref:System.Windows.FrameworkElement> jako element główny. Element główny zwykle zawiera inne obiekty <xref:System.Windows.FrameworkElement>. Kombinacja obiektów tworzy strukturę wizualizacji formantu.

 Poniższy przykład tworzy <xref:System.Windows.Controls.ControlTemplate> niestandardowe dla <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> tworzy strukturę wizualizacji <xref:System.Windows.Controls.Button>. Ten przykład nie zmienia wyglądu przycisku po przesunięciu wskaźnika myszy nad nim lub kliknięciem. Zmiana wyglądu przycisku, gdy znajduje się on w innym stanie, omówiono w dalszej części tego tematu.

 W tym przykładzie struktura wizualizacji składa się z następujących części:

- <xref:System.Windows.Controls.Border> o nazwie `RootElement`, który służy jako główny <xref:System.Windows.FrameworkElement>szablonu.

- <xref:System.Windows.Controls.Grid>, który jest elementem podrzędnym `RootElement`.

- <xref:System.Windows.Controls.ContentPresenter>, który wyświetla zawartość przycisku. <xref:System.Windows.Controls.ContentPresenter> włącza każdy typ obiektu do wyświetlenia.

 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]

### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachowanie funkcji właściwości kontrolki przy użyciu Szablonubinding
 Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>nadal można użyć właściwości publicznych do zmiany wyglądu kontrolki. Rozszerzenie " [TemplateBinding](../advanced/templatebinding-markup-extension.md) " tworzy powiązanie właściwości elementu znajdującego się w <xref:System.Windows.Controls.ControlTemplate> z właściwością publiczną, która jest zdefiniowana przez formant. W przypadku użycia [szablonubinding](../advanced/templatebinding-markup-extension.md)należy włączyć właściwości kontrolki, aby działały jako parametry szablonu. Oznacza to, że po ustawieniu właściwości kontrolki ta wartość jest przenoszona do elementu, który ma element [TemplateBinding](../advanced/templatebinding-markup-extension.md) .

 W poniższym przykładzie jest powtarzana część poprzedniego przykładu, która używa rozszerzenia [TemplateBinding](../advanced/templatebinding-markup-extension.md) , aby powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> właściwości publicznych, które są zdefiniowane przez przycisk.

 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]

 W tym przykładzie <xref:System.Windows.Controls.Grid> ma szablon właściwości <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> powiązany z <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Ponieważ <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> jest powiązany z szablonem, można utworzyć wiele przycisków, które używają tej samej <xref:System.Windows.Controls.ControlTemplate> i ustawić <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> na różne wartości na każdym przycisku. Jeśli <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> nie jest powiązany szablonem z właściwością elementu w <xref:System.Windows.Controls.ControlTemplate>, ustawienie <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> przycisku nie będzie miało wpływu na wygląd przycisku.

 Należy zauważyć, że nazwy dwóch właściwości nie muszą być identyczne. W poprzednim przykładzie właściwość <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Button> jest związana z szablonem <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.ContentPresenter>. Umożliwia to rozmieszczenie zawartości przycisku w poziomie. <xref:System.Windows.Controls.ContentPresenter> nie ma właściwości o nazwie `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> można powiązać z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Po powiązaniu szablonu z właściwością upewnij się, że właściwości docelowy i źródłowy są tego samego typu.

 Klasa <xref:System.Windows.Controls.Control> definiuje kilka właściwości, które muszą być używane przez szablon formantu, aby mieć wpływ na kontrolkę, gdy są ustawione. Sposób, w jaki <xref:System.Windows.Controls.ControlTemplate> używa właściwości, zależy od właściwości. <xref:System.Windows.Controls.ControlTemplate> musi używać właściwości w jeden z następujących sposobów:

- Element w szablonie <xref:System.Windows.Controls.ControlTemplate> jest powiązany z właściwością.

- Element w <xref:System.Windows.Controls.ControlTemplate> dziedziczy właściwość z <xref:System.Windows.FrameworkElement>nadrzędnego.

 W poniższej tabeli wymieniono właściwości wizualne dziedziczone przez formant z klasy <xref:System.Windows.Controls.Control>. Wskazuje również, czy domyślny szablon kontrolki kontrolki używa dziedziczonej wartości właściwości, czy też musi być powiązany z szablonem.

|Właściwość|Metoda użycia|
|--------------|------------------|
|<xref:System.Windows.Controls.Control.Background%2A>|Powiązanie szablonu|
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|Powiązanie szablonu|
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|Powiązanie szablonu|
|<xref:System.Windows.Controls.Control.FontFamily%2A>|Dziedziczenie właściwości lub powiązanie szablonu|
|<xref:System.Windows.Controls.Control.FontSize%2A>|Dziedziczenie właściwości lub powiązanie szablonu|
|<xref:System.Windows.Controls.Control.FontStretch%2A>|Dziedziczenie właściwości lub powiązanie szablonu|
|<xref:System.Windows.Controls.Control.FontWeight%2A>|Dziedziczenie właściwości lub powiązanie szablonu|
|<xref:System.Windows.Controls.Control.Foreground%2A>|Dziedziczenie właściwości lub powiązanie szablonu|
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|Powiązanie szablonu|
|<xref:System.Windows.Controls.Control.Padding%2A>|Powiązanie szablonu|
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|Powiązanie szablonu|

 W tabeli wymieniono tylko właściwości wizualne dziedziczone z klasy <xref:System.Windows.Controls.Control>. Poza właściwościami wymienionymi w tabeli, formant może również odziedziczyć właściwości <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>i <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> z elementu struktury nadrzędnej.

 Ponadto, jeśli <xref:System.Windows.Controls.ContentPresenter> znajduje się w <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> zostanie automatycznie powiązane z właściwościami <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A>. Podobnie <xref:System.Windows.Controls.ItemsPresenter>, która znajduje się w <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ItemsControl> zostanie automatycznie powiązane z właściwościami <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.ItemsPresenter>.

 Poniższy przykład tworzy dwa przyciski, które używają <xref:System.Windows.Controls.ControlTemplate> zdefiniowanego w poprzednim przykładzie. Przykład ustawia właściwości <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>i <xref:System.Windows.Controls.Control.FontSize%2A> na każdym przycisku. Ustawienie właściwości <xref:System.Windows.Controls.Control.Background%2A> ma wpływ, ponieważ jest powiązany z szablonem w <xref:System.Windows.Controls.ControlTemplate>. Mimo że właściwości <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.FontSize%2A> nie są powiązane z szablonem, ustawienie ich ma wpływ, ponieważ ich wartości są dziedziczone.

 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]

 Powyższy przykład generuje dane wyjściowe podobne do poniższej ilustracji.

 ![Dwa przyciski, jeden niebieski i jeden purpurowy.](./media/ndp-buttontwo.png "NDP_ButtonTwo")
Dwa przyciski z różnymi kolorami tła

<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Zmiana wyglądu kontrolki w zależności od jej stanu
 Różnica między przyciskiem z domyślnym wyglądem i przyciskiem w powyższym przykładzie polega na tym, że przycisk domyślny zmienia się, gdy jest on w różnych stanach. Na przykład wygląd przycisku domyślnego zmienia się po naciśnięciu przycisku lub po umieszczeniu wskaźnika myszy nad przyciskiem. Mimo że <xref:System.Windows.Controls.ControlTemplate> nie zmienia funkcjonalności kontrolki, zmienia zachowanie wizualizacji formantu. Zachowanie wizualne zawiera opis wyglądu kontrolki, gdy jest ona w określonym stanie. Aby zrozumieć różnicę między funkcjonalnością a zachowaniem wizualnym kontrolki, należy wziąć pod uwagę przykład przycisku. Funkcja przycisku ma na celu wygenerowanie zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> po kliknięciu, ale zachowanie wizualizacji przycisku ma na celu zmianę jego wyglądu, gdy zostanie wskazywane lub naciśnięte.

 Użyj <xref:System.Windows.VisualState> obiektów, aby określić wygląd kontrolki, gdy jest ona w określonym stanie. <xref:System.Windows.VisualState> zawiera <xref:System.Windows.Media.Animation.Storyboard>, który zmienia wygląd elementów znajdujących się w <xref:System.Windows.Controls.ControlTemplate>. Nie trzeba pisać żadnego kodu, ponieważ logika kontrolki zmienia stan przy użyciu <xref:System.Windows.VisualStateManager>. Gdy kontrolka przejdzie do stanu, który jest określony przez właściwość <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>, rozpocznie się <xref:System.Windows.Media.Animation.Storyboard>. Gdy kontrolka opuszcza stan, <xref:System.Windows.Media.Animation.Storyboard> zostanie zatrzymana.

 Poniższy przykład pokazuje <xref:System.Windows.VisualState>, które zmieniają wygląd <xref:System.Windows.Controls.Button>, gdy wskaźnik myszy znajduje się nad nim. <xref:System.Windows.Media.Animation.Storyboard> zmienia kolor obramowania przycisku, zmieniając kolor `BorderBrush`. Jeśli odwołujesz się do <xref:System.Windows.Controls.ControlTemplate> przykładu na początku tego tematu, spowoduje to odwołanie, że `BorderBrush` jest nazwą <xref:System.Windows.Media.SolidColorBrush>, która jest przypisana do <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border>.

 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]

 Kontrolka jest odpowiedzialna za Definiowanie stanów w ramach umowy dotyczącej kontroli, która jest szczegółowo omówiona w temacie [Dostosowywanie innych kontrolek przez zrozumienie kontraktu kontroli](#customizing_other_controls_by_understanding_the_control_contract) w dalszej części tego tematu. W poniższej tabeli wymieniono Stany, które są określone dla <xref:System.Windows.Controls.Button>.

|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|
|----------------------|---------------------------|-----------------|
|Typow|CommonStates|Stan domyślny.|
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|
|Styczn|CommonStates|Kontrolka zostanie naciśnięty.|
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|
|Fokus|FocusStates|Kontrolka ma fokus.|
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|

 <xref:System.Windows.Controls.Button> definiuje dwie grupy stanów: Grupa `CommonStates` zawiera Stany `Normal`, `MouseOver`, `Pressed`i `Disabled`. Grupa `FocusStates` zawiera Stany `Focused` i `Unfocused`. Stany w tej samej grupie Stanów wykluczają się wzajemnie. Kontrolka zawsze znajduje się w dokładnie jednym stanie na grupę. Na przykład <xref:System.Windows.Controls.Button> może mieć fokus nawet wtedy, gdy wskaźnik myszy nie znajduje się nad nim, więc <xref:System.Windows.Controls.Button> w stanie `Focused` może być w `MouseOver`, `Pressed`lub `Normal`.

 Dodawanie <xref:System.Windows.VisualState> obiektów do obiektów <xref:System.Windows.VisualStateGroup>. Dodano <xref:System.Windows.VisualStateGroup> obiektów do właściwości dołączonej <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>. W poniższym przykładzie zdefiniowano <xref:System.Windows.VisualState> obiektów dla Stanów `Normal`, `MouseOver`i `Pressed`, które znajdują się w grupie `CommonStates`. <xref:System.Windows.VisualState.Name%2A> każdej <xref:System.Windows.VisualState> jest zgodna z nazwą w powyższej tabeli. Stan `Disabled` i Stany w grupie `FocusStates` są pomijane w celu zachowania przykładu, ale znajdują się one w całym przykładzie na końcu tego tematu.

> [!NOTE]
> Upewnij się, że właściwość dołączona <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> została ustawiona na <xref:System.Windows.FrameworkElement> głównej <xref:System.Windows.Controls.ControlTemplate>.

 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]

 Powyższy przykład generuje dane wyjściowe podobne do poniższych ilustracji.

 ![Przycisk z szablonem kontrolki niestandardowej.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")
Przycisk, który używa szablonu kontrolki niestandardowej w normalnym stanie

 ![Przycisk z czerwonym obramowaniem.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")
Przycisk, który używa niestandardowego szablonu kontrolki w wskaźniku myszy nad stanem

 ![Obramowanie jest przezroczyste na przycisku naciśniętym.](./media/ndp-buttonpressed.png "NDP_ButtonPressed")
Przycisk, który używa szablonu kontrolki niestandardowej w stanie naciśniętym

 Aby znaleźć Stany wizualne dla formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Style i szablony kontrolek](control-styles-and-templates.md).

<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Określanie zachowania kontrolki podczas przejścia między Stanami
 W poprzednim przykładzie wygląd przycisku zmienia się również wtedy, gdy użytkownik kliknie go, ale jeśli przycisk nie zostanie wciśnięty przez cały czas, użytkownik nie zobaczy efektu. Domyślnie animacja zajmuje jedną sekundę. Ze względu na to, że użytkownicy mogą klikać i zwalniać przycisk w znacznie krótszym czasie, opinie wizualne nie będą obowiązywać, Jeśli pozostawisz <xref:System.Windows.Controls.ControlTemplate> w stanie domyślnym.

 Można określić ilość czasu, przez który ma następować animację, aby bezproblemowo przeszedł formant z jednego stanu do innego przez dodanie <xref:System.Windows.VisualTransition> obiektów do <xref:System.Windows.Controls.ControlTemplate>. Podczas tworzenia <xref:System.Windows.VisualTransition>należy określić co najmniej jedną z następujących czynności:

- Czas trwania przejścia między Stanami.

- Dodatkowe zmiany dotyczące wyglądu kontrolki, która występuje w momencie przejścia.

- Do którego są stosowane <xref:System.Windows.VisualTransition>.

### <a name="specifying-the-duration-of-a-transition"></a>Określanie czasu trwania przejścia
 Możesz określić czas trwania przejścia przez ustawienie właściwości <xref:System.Windows.VisualTransition.GeneratedDuration%2A>. W poprzednim przykładzie jest <xref:System.Windows.VisualState>, które określa, że obramowanie przycisku staje się przezroczyste po naciśnięciu przycisku, ale animacja jest zbyt długa, aby można było zauważyć, że przycisk jest szybko wciśnięty i wydawany. Można użyć <xref:System.Windows.VisualTransition>, aby określić ilość czasu, przez jaki formant przechodzi do stanu naciśniętego. Poniższy przykład określa, że kontrolka przyjmuje jedną setną część sekundy, aby przejść do stanu naciśniętego.

 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]

### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Określanie zmian wyglądu kontrolki podczas przejścia
 <xref:System.Windows.VisualTransition> zawiera <xref:System.Windows.Media.Animation.Storyboard>, który rozpoczyna się, gdy kontrolka przechodzi między Stanami. Na przykład można określić, że określona animacja ma być wykonywana, gdy kontrolka przechodzi ze stanu `MouseOver` do stanu `Normal`. Poniższy przykład tworzy <xref:System.Windows.VisualTransition>, który określa, że gdy użytkownik przesuwa wskaźnik myszy z przycisku, obramowanie przycisku zmieni się na niebieski, a następnie na żółty, a następnie na czerń w ciągu 1,5 sekund.

 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]

### <a name="specifying-when-a-visualtransition-is-applied"></a>Określanie, kiedy VisualTransition jest stosowany
 <xref:System.Windows.VisualTransition> może być ograniczone do zastosowania tylko do określonych stanów lub można go zastosować za każdym razem, gdy kontrolka przechodzi między Stanami. W poprzednim przykładzie <xref:System.Windows.VisualTransition> jest stosowany, gdy kontrolka przechodzi ze stanu `MouseOver` do stanu `Normal`; w przykładzie przed tym <xref:System.Windows.VisualTransition> jest stosowany, gdy formant przechodzi do stanu `Pressed`. Gdy <xref:System.Windows.VisualTransition> jest stosowany, należy ustawić właściwości <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A>. W poniższej tabeli opisano poziomy ograniczeń od najbardziej restrykcyjne do najmniej restrykcyjne.

|Typ ograniczenia|Wartość z|Wartość do|
|-------------------------|-------------------|-----------------|
|Od określonego stanu do innego określonego stanu|Nazwa <xref:System.Windows.VisualState>|Nazwa <xref:System.Windows.VisualState>|
|Od dowolnego stanu do określonego stanu|Nie ustawiono|Nazwa <xref:System.Windows.VisualState>|
|Od określonego stanu do dowolnego stanu|Nazwa <xref:System.Windows.VisualState>|Nie ustawiono|
|Z dowolnego stanu do dowolnego innego stanu|Nie ustawiono|Nie ustawiono|

 Można mieć wiele obiektów <xref:System.Windows.VisualTransition> w <xref:System.Windows.VisualStateGroup>, które odwołują się do tego samego stanu, ale będą używane w kolejności, w jakiej określono w poprzedniej tabeli. W poniższym przykładzie istnieją dwa <xref:System.Windows.VisualTransition> obiektów. Gdy kontrolka przechodzi ze stanu `Pressed` do stanu `MouseOver`, używany jest <xref:System.Windows.VisualTransition>, który ma zarówno <xref:System.Windows.VisualTransition.From%2A>, jak i <xref:System.Windows.VisualTransition.To%2A>. Gdy kontrolka przechodzi ze stanu, który nie jest `Pressed` do stanu `MouseOver`, używany jest drugi stan.

 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]

 <xref:System.Windows.VisualStateGroup> ma właściwość <xref:System.Windows.VisualStateGroup.Transitions%2A>, która zawiera <xref:System.Windows.VisualTransition> obiekty, które mają zastosowanie do obiektów <xref:System.Windows.VisualState> w <xref:System.Windows.VisualStateGroup>. Jako autor <xref:System.Windows.Controls.ControlTemplate> możesz dołączyć dowolny <xref:System.Windows.VisualTransition>. Jeśli jednak właściwości <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A> są ustawione na nazwy stanów, które nie znajdują się w <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> zostanie zignorowana.

 Poniższy przykład pokazuje <xref:System.Windows.VisualStateGroup> `CommonStates`. W przykładzie zdefiniowano <xref:System.Windows.VisualTransition> dla każdego z poniższych przejść przycisku.

- Do stanu `Pressed`.

- Do stanu `MouseOver`.

- Ze stanu `Pressed` `MouseOver`.

- Ze stanu `MouseOver` `Normal`.

 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]

<a name="customizing_other_controls_by_understanding_the_control_contract"></a>
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Dostosowywanie innych kontrolek przez zrozumienie kontraktu kontroli
 Kontrolka, która używa <xref:System.Windows.Controls.ControlTemplate> do określenia swojej struktury wizualizacji (przy użyciu obiektów <xref:System.Windows.FrameworkElement>) i zachowań wizualizacji (za pomocą obiektów <xref:System.Windows.VisualState>) używa modelu sterowania częściami. Wiele kontrolek, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 używa tego modelu. Części, których autor <xref:System.Windows.Controls.ControlTemplate> musi wiedzieć, są przekazywane przez kontrakt kontroli. W przypadku zrozumienia części kontraktu kontroli można dostosować wygląd dowolnej kontrolki, która używa modelu sterowania częściami.

 Kontrakt kontrolny ma trzy elementy:

- Elementy wizualizacji, których używa logika kontrolki.

- Stany formantu i grupy, do których należy każdy stan.

- Właściwości publiczne, które wizualnie wpływają na kontrolkę.

### <a name="visual-elements-in-the-control-contract"></a>Elementy wizualne w umowie kontroli
 Czasami logika kontrolki współdziała z <xref:System.Windows.FrameworkElement>, który znajduje się w <xref:System.Windows.Controls.ControlTemplate>. Na przykład kontrolka może obsłużyć zdarzenie jednego z jego elementów. Gdy formant oczekuje na znalezienie określonego <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate>, musi przekazać te informacje do autora <xref:System.Windows.Controls.ControlTemplate>. Formant używa <xref:System.Windows.TemplatePartAttribute> do przekazywania typu oczekiwanego elementu i nazwy elementu, który ma być. <xref:System.Windows.Controls.Button> nie ma części <xref:System.Windows.FrameworkElement> w umowie kontroli, ale inne kontrolki, takie jak <xref:System.Windows.Controls.ComboBox>, robią.

 W poniższym przykładzie przedstawiono <xref:System.Windows.TemplatePartAttribute> obiektów, które są określone w klasie <xref:System.Windows.Controls.ComboBox>. Logika <xref:System.Windows.Controls.ComboBox> oczekuje znalezienia <xref:System.Windows.Controls.TextBox> o nazwie `PART_EditableTextBox` i <xref:System.Windows.Controls.Primitives.Popup> o nazwie `PART_Popup` w <xref:System.Windows.Controls.ControlTemplate>.

 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]

 W poniższym przykładzie przedstawiono uproszczony <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ComboBox>, który zawiera elementy, które są określone przez <xref:System.Windows.TemplatePartAttribute> obiektów w klasie <xref:System.Windows.Controls.ComboBox>.

 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]

### <a name="states-in-the-control-contract"></a>Stany w umowie kontroli
 Stany formantu są również częścią kontraktu kontroli. Przykład tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> pokazuje, jak określić wygląd <xref:System.Windows.Controls.Button> w zależności od jego stanu. Tworzysz <xref:System.Windows.VisualState> dla każdego określonego stanu i umieścisz wszystkie obiekty <xref:System.Windows.VisualState>, które współużytkują <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> w <xref:System.Windows.VisualStateGroup>, zgodnie z opisem w temacie [zmiana wyglądu kontrolki w zależności od jej stanu](#changing_the_appearance_of_a_control_depending_on_its_state) we wcześniejszej części tego tematu. Kontrolki innych firm powinny określać Stany przy użyciu <xref:System.Windows.TemplateVisualStateAttribute>, co umożliwia narzędziom projektanta, takim jak [Projektant XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio) w programie Visual Studio i Blend for Visual Studio, uwidocznienie Stanów formantu na potrzeby tworzenia szablonów kontroli.

 Aby znaleźć umowę kontroli dla formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Style i szablony kontrolek](control-styles-and-templates.md).

### <a name="properties-in-the-control-contract"></a>Właściwości w kontrakcie kontrolnym
 Właściwości publiczne, które wizualnie wpływają na kontrolkę, są również zawarte w umowie kontroli. Można ustawić te właściwości, aby zmienić wygląd formantu bez tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>. Można również użyć rozszerzenia [TemplateBinding](../advanced/templatebinding-markup-extension.md) znaczników, aby powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publicznych, które są zdefiniowane przez <xref:System.Windows.Controls.Button>.

 Poniższy przykład pokazuje kontrakt kontrolny dla przycisku.

 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]

 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>często najłatwiej zacząć od istniejącej <xref:System.Windows.Controls.ControlTemplate> i wprowadzać w niej zmiany. Aby zmienić istniejący <xref:System.Windows.Controls.ControlTemplate>, można wykonać jedną z następujących czynności:

- Użyj projektanta, takiego jak Blend for Visual Studio, który udostępnia graficzny interfejs użytkownika służący do tworzenia szablonów kontrolek. Aby uzyskać więcej informacji, zobacz [Określanie stylu kontrolki, która obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).

- Pobierz domyślną <xref:System.Windows.Controls.ControlTemplate> i edytuj ją. Aby znaleźć domyślne szablony kontrolek, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [domyślne motywy WPF](https://go.microsoft.com/fwlink/?LinkID=158252).

<a name="complete_example"></a>
## <a name="complete-example"></a>Kompletny przykład
 Poniższy przykład pokazuje kompletny <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>, który został omówiony w tym temacie.

 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
