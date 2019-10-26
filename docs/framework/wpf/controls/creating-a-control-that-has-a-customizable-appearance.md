---
title: Tworzenie formantu, którego wygląd można dostosować
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: c98035ef0b4ea1add22b09fb9927bcd49c00cd9b
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920041"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Tworzenie formantu, którego wygląd można dostosować

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] daje możliwość tworzenia formantu, którego wygląd można dostosować. Na przykład można zmienić wygląd <xref:System.Windows.Controls.CheckBox> wykraczający poza ustawienia, które zostaną utworzone przez utworzenie nowej <xref:System.Windows.Controls.ControlTemplate>. Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.CheckBox>, które korzystają z domyślnej <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.CheckBox>, która używa niestandardowych <xref:System.Windows.Controls.ControlTemplate>.

![Pole wyboru z domyślnym szablonem formantu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")
Pole wyboru używające domyślnego szablonu kontrolki

![Pole wyboru z szablonem niestandardowej kontrolki.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")
Pole wyboru, które używa szablonu kontrolki niestandardowej

Jeśli podczas tworzenia kontrolki korzystasz z modelu części i Stanów, wygląd kontrolki zostanie dostosowany. Narzędzia projektanta, takie jak Blend for Visual Studio obsługują model części i Stanów, dlatego w przypadku zastosowania tego modelu formant zostanie dostosowywalny w tych typach aplikacji.  W tym temacie omówiono części i Stany modelu oraz sposób ich użycia podczas tworzenia własnej kontrolki. W tym temacie przedstawiono przykład kontrolki niestandardowej, `NumericUpDown`, do zilustrowania charakteru tego modelu.  Kontrolka `NumericUpDown` wyświetla wartość liczbową, którą użytkownik może zwiększyć lub zmniejszyć, klikając przyciski kontrolki.  Na poniższej ilustracji przedstawiono formant `NumericUpDown`, który został omówiony w tym temacie.

![NumericUpDown kontrolkę niestandardową.](./media/ndp-numericupdown.png "NDP_NumericUPDown")
Niestandardowa kontrolka NumericUpDown

Ten temat zawiera następujące sekcje:

- [Wymagania wstępne](#prerequisites)

- [Części i Stany — model](#parts_and_states_model)

- [Definiowanie struktury wizualizacji i wizualnego zachowania kontrolki w ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)

- [Korzystanie z części ControlTemplate w kodzie](#using_parts_of_the_controltemplate_in_code)

- [Udostępnianie kontraktu kontroli](#providing_the_control_contract)

- [Pełny przykład](#complete_example)

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie przyjęto założenie, że wiesz, jak utworzyć nowy <xref:System.Windows.Controls.ControlTemplate> dla istniejącej kontrolki, dobrze zapoznaj się z elementami kontraktu kontrolki, a także zrozumieć koncepcje omówione w temacie [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

> [!NOTE]
> Aby utworzyć kontrolkę, która może mieć dostosowany wygląd, należy utworzyć kontrolkę, która dziedziczy z klasy <xref:System.Windows.Controls.Control> lub jednej z jej podklas innych niż <xref:System.Windows.Controls.UserControl>.  Formant, który dziedziczy po <xref:System.Windows.Controls.UserControl> jest formantem, który można szybko utworzyć, ale nie używa <xref:System.Windows.Controls.ControlTemplate> i nie można dostosować jego wyglądu.

<a name="parts_and_states_model"></a>

## <a name="parts-and-states-model"></a>Części i Stany — model

Model części i Stany określa sposób definiowania struktury wizualizacji i wizualnych zachowań kontrolki. Aby postępować zgodnie z modelem części i Stanów, należy wykonać następujące czynności:

- Zdefiniuj strukturę wizualizacji i zachowanie wizualizacji w <xref:System.Windows.Controls.ControlTemplate> formantu.

- Wykonaj pewne najlepsze rozwiązania, gdy logika kontrolki współdziała z częściami szablonu kontrolki.

- Podaj kontrakt kontroli, aby określić, co należy uwzględnić w <xref:System.Windows.Controls.ControlTemplate>.

Gdy zdefiniujesz strukturę wizualizacji i zachowanie wizualizacji w <xref:System.Windows.Controls.ControlTemplate> kontrolki, autorzy aplikacji mogą zmienić strukturę wizualizacji i wizualną zachowanie kontrolki, tworząc nowy <xref:System.Windows.Controls.ControlTemplate> zamiast pisać kod.   Musisz podać kontrakt kontroli, który informuje autorów aplikacji, które <xref:System.Windows.FrameworkElement> obiekty i Stany, które mają być zdefiniowane w <xref:System.Windows.Controls.ControlTemplate>. Podczas pracy z częściami w <xref:System.Windows.Controls.ControlTemplate> należy przestrzegać pewnych najlepszych rozwiązań, aby kontrola prawidłowo obsługiwała niekompletny <xref:System.Windows.Controls.ControlTemplate>.  Jeśli przestrzegasz tych trzech zasad, autorzy aplikacji będą mogli tworzyć <xref:System.Windows.Controls.ControlTemplate> dla kontrolki równie łatwo, jak w przypadku formantów dostarczanych z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  W poniższej sekcji opisano szczegółowo wszystkie te zalecenia.

<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>

## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definiowanie struktury wizualizacji i wizualnego zachowania kontrolki w ControlTemplate

Podczas tworzenia kontrolki niestandardowej przy użyciu modelu części i Stanów należy zdefiniować strukturę wizualizacji i zachowanie wizualizacji formantu w <xref:System.Windows.Controls.ControlTemplate> zamiast w jego logice.  Struktura wizualizacji formantu jest złożona <xref:System.Windows.FrameworkElement> obiektów, które tworzą formant.  Zachowanie wizualizacji jest sposobem, w jaki formant pojawia się, gdy jest w określonym stanie.   Aby uzyskać więcej informacji na temat tworzenia <xref:System.Windows.Controls.ControlTemplate>, który określa strukturę wizualizacji i wizualne zachowanie kontrolki, zobacz [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

W przykładzie formantu `NumericUpDown`, struktura wizualizacji zawiera dwie kontrolki <xref:System.Windows.Controls.Primitives.RepeatButton> i <xref:System.Windows.Controls.TextBlock>.  Jeśli dodasz te kontrolki w kodzie kontrolki `NumericUpDown`, na przykład, nie można zmieniać pozycji tych kontrolek.  Zamiast definiować strukturę wizualizacji i zachowanie wizualizacji kontrolki w kodzie, należy ją zdefiniować w <xref:System.Windows.Controls.ControlTemplate>.  Następnie Deweloper aplikacji, aby dostosować pozycję przycisków i <xref:System.Windows.Controls.TextBlock> i określić, jakie zachowanie występuje, gdy `Value` jest ujemna, ponieważ <xref:System.Windows.Controls.ControlTemplate> może zostać zamieniony.

W poniższym przykładzie pokazano strukturę wizualizacji `NumericUpDown` kontrolki, która obejmuje <xref:System.Windows.Controls.Primitives.RepeatButton> do zwiększenia `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> do zmniejszenia `Value`oraz <xref:System.Windows.Controls.TextBlock> wyświetlania `Value`.

[!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]

Wizualne zachowanie kontrolki `NumericUpDown` polega na tym, że wartość jest czcionką czerwoną, jeśli jest ujemna.  Jeśli zmienisz <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> w kodzie, gdy `Value` jest ujemna, `NumericUpDown` będzie zawsze wyświetlać czerwoną wartość ujemną. Należy określić zachowanie wizualizacji kontrolki w <xref:System.Windows.Controls.ControlTemplate> przez dodanie obiektów <xref:System.Windows.VisualState> do <xref:System.Windows.Controls.ControlTemplate>.  W poniższym przykładzie przedstawiono <xref:System.Windows.VisualState> obiektów dla `Positive` i `Negative` Stanów.  `Positive` i `Negative` wzajemnie się wykluczają (formant jest zawsze dokładnie w jednym z dwóch), więc przykład umieszcza obiekty <xref:System.Windows.VisualState> w jednym <xref:System.Windows.VisualStateGroup>.  Gdy formant przechodzi w stan `Negative`, <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> zmieni kolor na czerwony.  Gdy kontrolka jest w stanie `Positive`, <xref:System.Windows.Controls.TextBlock.Foreground%2A> powraca do oryginalnej wartości.  Definiowanie <xref:System.Windows.VisualState> obiektów w <xref:System.Windows.Controls.ControlTemplate> jest dokładniej omówione w sekcji [Dostosowywanie wyglądu istniejącej kontrolki przez utworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

> [!NOTE]
> Upewnij się, że właściwość dołączona <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> została ustawiona na <xref:System.Windows.FrameworkElement> głównej <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

<a name="using_parts_of_the_controltemplate_in_code"></a>

## <a name="using-parts-of-the-controltemplate-in-code"></a>Korzystanie z części ControlTemplate w kodzie

Autor <xref:System.Windows.Controls.ControlTemplate> może pominąć <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState> obiektów, celowo całkowicie lub przez pomyłkę, ale logika kontrolki może potrzebować tych części do prawidłowego działania. Model części i Stanów określa, że formant powinien być odporny na <xref:System.Windows.Controls.ControlTemplate>, w którym brakuje obiektów <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState>.  Kontrolka nie powinna zgłosić wyjątku ani zgłosić błędu, jeśli brakuje <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>lub <xref:System.Windows.VisualStateGroup> w <xref:System.Windows.Controls.ControlTemplate>. W tej sekcji opisano zalecane rozwiązania dotyczące współpracy z obiektami <xref:System.Windows.FrameworkElement> i zarządzania stanami.

### <a name="anticipate-missing-frameworkelement-objects"></a>Przewidywanie brakujących obiektów FrameworkElement

Podczas definiowania <xref:System.Windows.FrameworkElement> obiektów w <xref:System.Windows.Controls.ControlTemplate>, logika kontrolki może być konieczna do korzystania z niektórych z nich.  Na przykład formant `NumericUpDown` subskrybuje zdarzenie "<xref:System.Windows.Controls.Primitives.ButtonBase.Click>", aby zwiększyć lub zmniejszyć `Value` i ustawi właściwość <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock> na `Value`. Jeśli niestandardowa <xref:System.Windows.Controls.ControlTemplate> pomija <xref:System.Windows.Controls.TextBlock> lub przyciski, możliwe jest, że formant utraci część jego funkcjonalności, ale należy upewnić się, że formant nie powoduje błędu. Na przykład jeśli <xref:System.Windows.Controls.ControlTemplate> nie zawiera przycisków do zmiany `Value`, `NumericUpDown` utraci tę funkcjonalność, ale aplikacja używająca <xref:System.Windows.Controls.ControlTemplate> będzie nadal działać.

Poniższe praktyki zapewnią, że kontrolka odpowiednio reaguje na brakujące <xref:System.Windows.FrameworkElement> obiekty:

1. Dla każdego <xref:System.Windows.FrameworkElement> należy ustawić atrybut `x:Name`, który należy odwołać w kodzie.

2. Zdefiniuj właściwości prywatne dla każdej <xref:System.Windows.FrameworkElement>, z którą chcesz korzystać.

3. Subskrybuj i Anuluj subskrypcję wszystkich zdarzeń, które są obsługiwane przez kontrolkę we właściwości <xref:System.Windows.FrameworkElement> ustaw metodę dostępu.

4. Ustaw <xref:System.Windows.FrameworkElement> właściwości zdefiniowane w kroku 2 w metodzie <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>. Jest to Najwcześniejsza, że <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate> jest dostępny dla kontrolki. Użyj `x:Name` <xref:System.Windows.FrameworkElement>, aby pobrać go z <xref:System.Windows.Controls.ControlTemplate>.

5. Przed uzyskaniem dostępu do elementów członkowskich Sprawdź, czy <xref:System.Windows.FrameworkElement> nie `null`.  Jeśli jest `null`, nie zgłaszaj błędu.

W poniższych przykładach pokazano, jak formant `NumericUpDown` współdziała z obiektami <xref:System.Windows.FrameworkElement> zgodnie z zaleceniami z powyższej listy.

W przykładzie, który definiuje wizualną strukturę formantu `NumericUpDown` w <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton>, który zwiększa `Value`, ma atrybut `x:Name` ustawiony na `UpButton`.  Poniższy przykład deklaruje właściwość o nazwie `UpButtonElement`, która reprezentuje <xref:System.Windows.Controls.Primitives.RepeatButton>, który jest zadeklarowany w <xref:System.Windows.Controls.ControlTemplate>. Metoda dostępu `set` najpierw anuluje subskrypcję dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku, jeśli `UpDownElement` nie `null`, ustawia właściwość, a następnie subskrybuje zdarzenie <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. Istnieje również zdefiniowana właściwość, ale nie jest ona wyświetlana w tym miejscu dla innych <xref:System.Windows.Controls.Primitives.RepeatButton>o nazwie `DownButtonElement`.

[!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
[!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]

Poniższy przykład pokazuje <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> formantu `NumericUpDown`.  W przykładzie zastosowano metodę <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>, aby pobrać obiekty <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  Należy zauważyć, że przykład chroni przed przypadkami, w których <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> odnajduje <xref:System.Windows.FrameworkElement> o określonej nazwie, która nie jest oczekiwanym typem. Najlepszym rozwiązaniem jest również Ignorowanie elementów, które mają określone `x:Name`, ale mają nieprawidłowy typ.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Postępując zgodnie z zasadami opisanymi w poprzednich przykładach, upewnij się, że kontrolka będzie nadal działać, gdy w <xref:System.Windows.Controls.ControlTemplate> brakuje <xref:System.Windows.FrameworkElement>.

### <a name="use-the-visualstatemanager-to-manage-states"></a>Zarządzanie Stanami za pomocą VisualStateManager

<xref:System.Windows.VisualStateManager> śledzi Stany kontrolki i wykonuje logikę niezbędną do przejścia między Stanami. Po dodaniu <xref:System.Windows.VisualState> obiektów do <xref:System.Windows.Controls.ControlTemplate>należy dodać je do <xref:System.Windows.VisualStateGroup> i dodać <xref:System.Windows.VisualStateGroup> do właściwości dołączonej <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>, aby <xref:System.Windows.VisualStateManager> uzyskać do nich dostęp.

Poniższy przykład powtarza poprzedni przykład, który pokazuje <xref:System.Windows.VisualState> obiekty, które odpowiadają `Positive` i `Negative` Stanów formantu. <xref:System.Windows.Media.Animation.Storyboard> w `Negative`<xref:System.Windows.VisualState> powoduje <xref:System.Windows.Controls.TextBlock.Foreground%2A> <xref:System.Windows.Controls.TextBlock> czerwony.   Gdy formant `NumericUpDown` jest w stanie `Negative`, rozpocznie się seria ujęć w stanie `Negative`.  Następnie <xref:System.Windows.Media.Animation.Storyboard> w stanie `Negative` zatrzyma się, gdy kontrolka powróci do stanu `Positive`.  <xref:System.Windows.VisualState> `Positive`nie musi zawierać <xref:System.Windows.Media.Animation.Storyboard>, ponieważ gdy <xref:System.Windows.Media.Animation.Storyboard> dla `Negative` zatrzyma się, <xref:System.Windows.Controls.TextBlock.Foreground%2A> powraca do oryginalnego koloru.

[!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]

Należy zauważyć, że <xref:System.Windows.Controls.TextBlock> ma nazwę, ale <xref:System.Windows.Controls.TextBlock> nie znajduje się w umowie kontroli dla `NumericUpDown`, ponieważ logika kontrolki nigdy nie odwołuje się do <xref:System.Windows.Controls.TextBlock>.  Elementy, do których odwołuje się <xref:System.Windows.Controls.ControlTemplate>, mają nazwy, ale nie muszą być częścią kontraktu kontroli, ponieważ nowe <xref:System.Windows.Controls.ControlTemplate> dla formantu mogą nie musi odwoływać się do tego elementu.  Na przykład osoba, która tworzy nowe <xref:System.Windows.Controls.ControlTemplate> dla `NumericUpDown` może zdecydować, że `Value` jest ujemna, zmieniając <xref:System.Windows.Controls.Control.Foreground%2A>.  W takim przypadku ani kod, ani <xref:System.Windows.Controls.ControlTemplate> nie odwołuje się do <xref:System.Windows.Controls.TextBlock> według nazwy.

Logika kontrolki jest odpowiedzialna za zmianę stanu formantu. Poniższy przykład pokazuje, że formant `NumericUpDown` wywołuje metodę <xref:System.Windows.VisualStateManager.GoToState%2A>, aby przejść do stanu `Positive`, gdy `Value` jest równa 0 lub większa, a `Negative` stanie, gdy `Value` jest mniejsza niż 0.

[!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
[!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]

Metoda <xref:System.Windows.VisualStateManager.GoToState%2A> wykonuje logikę niezbędną do odpowiedniego uruchamiania i zatrzymywania scenorysów. Gdy kontrolka wywołuje <xref:System.Windows.VisualStateManager.GoToState%2A>, aby zmienić jej stan, <xref:System.Windows.VisualStateManager> wykonuje następujące czynności:

- Jeśli <xref:System.Windows.VisualState>, do której ma <xref:System.Windows.Media.Animation.Storyboard>, rozpocznie się tworzenie scenorysu. Następnie, jeśli <xref:System.Windows.VisualState>, z której pochodzi formant, ma <xref:System.Windows.Media.Animation.Storyboard>, zostanie zakończona seria ujęć.

- Jeśli kontrolka jest już w stanie, który jest określony, <xref:System.Windows.VisualStateManager.GoToState%2A> nie przyjmuje żadnej akcji i zwraca `true`.

- Jeśli określony stan nie istnieje w <xref:System.Windows.Controls.ControlTemplate> `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> nie przyjmuje żadnej akcji i zwróci `false`.

#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Najlepsze rozwiązania dotyczące pracy z VisualStateManager

Zaleca się wykonanie następujących czynności, aby zachować stan formantu:

- Użyj właściwości do śledzenia stanu.

- Utwórz metodę pomocnika do przejścia między Stanami.

Kontrolka `NumericUpDown` używa swojej właściwości `Value` do śledzenia, czy jest w stanie `Positive` czy `Negative`.  Kontrolka `NumericUpDown` definiuje także `Focused` i `UnFocused` Stanów, które śledzą Właściwość <xref:System.Windows.UIElement.IsFocused%2A>. Jeśli używasz Stanów, które nie są naturalnie zgodne z właściwością kontrolki, możesz zdefiniować właściwość prywatną do śledzenia stanu.

Pojedyncza Metoda, która aktualizuje wszystkie Stany scentralizowanie wywołań do <xref:System.Windows.VisualStateManager> i utrzymuje łatwość zarządzania kodem. Poniższy przykład przedstawia metodę pomocnika `NumericUpDown` kontrolki, `UpdateStates`. Gdy `Value` jest większa lub równa 0, <xref:System.Windows.Controls.Control> jest w stanie `Positive`.  Gdy `Value` jest mniejsza niż 0, formant jest w stanie `Negative`.  Gdy <xref:System.Windows.UIElement.IsFocused%2A> jest `true`, formant jest w stanie `Focused`. w przeciwnym razie jest w stanie `Unfocused`.  Formant może wywoływać `UpdateStates`, gdy musi zmienić jego stan, niezależnie od tego, jakie zmiany stanu.

[!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
[!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]

Jeśli przekażesz nazwę stanu do <xref:System.Windows.VisualStateManager.GoToState%2A>, gdy kontrolka jest już w tym stanie, <xref:System.Windows.VisualStateManager.GoToState%2A> nic nie robi, więc nie musisz sprawdzać bieżącego stanu formantu.  Na przykład jeśli `Value` zmiany z jednej liczby ujemnej na inną liczbę ujemną, scenorys dla stanu `Negative` nie zostanie przerwany i użytkownik nie zobaczy zmiany w kontrolce.

<xref:System.Windows.VisualStateManager> używa obiektów <xref:System.Windows.VisualStateGroup> do określenia stanu, który ma zostać zakończony po wywołaniu <xref:System.Windows.VisualStateManager.GoToState%2A>. Formant jest zawsze w jednym stanie dla każdego <xref:System.Windows.VisualStateGroup>, który jest zdefiniowany w jego <xref:System.Windows.Controls.ControlTemplate> i pozostawia stan tylko wtedy, gdy przejdzie do innego stanu z tego samego <xref:System.Windows.VisualStateGroup>. Na przykład <xref:System.Windows.Controls.ControlTemplate> kontrolki `NumericUpDown` definiuje `Positive` i `Negative`obiekty<xref:System.Windows.VisualState> w jednej <xref:System.Windows.VisualStateGroup>, a `Focused` i `Unfocused`<xref:System.Windows.VisualState> obiekty w innym. (`Focused` i `Unfocused`<xref:System.Windows.VisualState> zdefiniowane w sekcji [kompletny przykład](#complete_example) w tym temacie, gdy formant przechodzi ze stanu `Positive` do stanu `Negative` lub na odwrót, formant pozostaje w `Focused` lub `Unfocused` Państwu.

Istnieją trzy typowe miejsca, w których można zmienić stan kontrolki:

- Gdy <xref:System.Windows.Controls.ControlTemplate> zostanie zastosowana do <xref:System.Windows.Controls.Control>.

- Zmiana właściwości.

- Gdy wystąpi zdarzenie.

W poniższych przykładach pokazano, jak w takich przypadkach zaktualizować stan kontrolki `NumericUpDown`.

Należy zaktualizować stan formantu w metodzie <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>, tak aby formant pojawiał się w poprawnym stanie w przypadku zastosowania <xref:System.Windows.Controls.ControlTemplate>. Poniższy przykład wywołuje `UpdateStates` w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>, aby upewnić się, że formant znajduje się w odpowiednich Stanach.  Załóżmy na przykład, że tworzysz kontrolkę `NumericUpDown`, a następnie ustawisz jej <xref:System.Windows.Controls.Control.Foreground%2A> na zieloną i `Value` do-5.  Jeśli `UpdateStates` nie zostanie wywołana, gdy <xref:System.Windows.Controls.ControlTemplate> zostanie zastosowana do kontrolki `NumericUpDown`, formant nie jest w stanie `Negative`, a wartość jest zielona zamiast czerwony.  Musisz wywołać `UpdateStates`, aby umieścić formant w stanie `Negative`.

[!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
[!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]

Często trzeba zaktualizować Stany kontrolki, gdy właściwość zostanie zmieniona. Poniższy przykład pokazuje całą metodę `ValueChangedCallback`. Ponieważ `ValueChangedCallback` jest wywoływana, gdy `Value` zmiany, metoda wywołuje `UpdateStates` w przypadku, `Value` zmieniono wartość dodatnią na ujemną lub odwrotnie. Możliwe jest Wywołaj `UpdateStates`, gdy `Value` zmiany, ale pozostanie dodatnie lub ujemne, ponieważ w takim przypadku kontrolka nie zmieni Stanów.

[!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
[!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]

W przypadku wystąpienia zdarzenia może być również konieczne zaktualizowanie stanu. Poniższy przykład pokazuje, że `NumericUpDown` wywołuje `UpdateStates` <xref:System.Windows.Controls.Control>, aby obsłużyć zdarzenie <xref:System.Windows.UIElement.GotFocus>.

[!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
[!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]

<xref:System.Windows.VisualStateManager> ułatwia zarządzanie Stanami formantu. Za pomocą <xref:System.Windows.VisualStateManager>upewnij się, że formant prawidłowo przechodzi między Stanami.  Jeśli zgodnie z zaleceniami opisanymi w tej sekcji nie można pracować z <xref:System.Windows.VisualStateManager>, kod kontrolki pozostanie do odczytu i utrzymania.

<a name="providing_the_control_contract"></a>

## <a name="providing-the-control-contract"></a>Udostępnianie kontraktu kontroli

Podajesz kontrakt kontrolny, dzięki czemu <xref:System.Windows.Controls.ControlTemplate> autorzy wiedzą, co należy umieścić w szablonie. Kontrakt kontrolny ma trzy elementy:

- Elementy wizualizacji, których używa logika kontrolki.

- Stany formantu i grupy, do których należy każdy stan.

- Właściwości publiczne, które wizualnie wpływają na kontrolkę.

Ktoś, który tworzy nowe <xref:System.Windows.Controls.ControlTemplate> musi wiedzieć, jakie obiekty <xref:System.Windows.FrameworkElement> są używane przez logikę kontrolki, co oznacza każdy obiekt i jego nazwę. Autor <xref:System.Windows.Controls.ControlTemplate> musi znać nazwę każdego możliwego stanu, w którym może być formant, a który <xref:System.Windows.VisualStateGroup> stanie.

Powracanie do `NumericUpDown` przykładu, kontrolka oczekuje <xref:System.Windows.Controls.ControlTemplate> do posiadania następujących <xref:System.Windows.FrameworkElement> obiektów:

- <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `UpButton`.

- <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `DownButton.`

 Kontrolka może być w następujących stanach:

- W `ValueStates`<xref:System.Windows.VisualStateGroup>

  - `Positive`

  - `Negative`

- W `FocusStates`<xref:System.Windows.VisualStateGroup>

  - `Focused`

  - `Unfocused`

Aby określić, które obiekty <xref:System.Windows.FrameworkElement> oczekiwać przez formant, należy użyć <xref:System.Windows.TemplatePartAttribute>, która określa nazwę i typ oczekiwanych elementów.  Aby określić możliwe stany formantu, należy użyć <xref:System.Windows.TemplateVisualStateAttribute>, który określa nazwę stanu, a który <xref:System.Windows.VisualStateGroup> należy do.  Umieść <xref:System.Windows.TemplatePartAttribute> i <xref:System.Windows.TemplateVisualStateAttribute> w definicji klasy formantu.

Każda właściwość publiczna wpływająca na wygląd kontrolki jest również częścią kontraktu kontroli.

W poniższym przykładzie określono obiekt <xref:System.Windows.FrameworkElement> i Stany dla kontrolki `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
[!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]

<a name="complete_example"></a>

## <a name="complete-example"></a>Kompletny przykład

Poniższy przykład to cały <xref:System.Windows.Controls.ControlTemplate> formantu `NumericUpDown`.

[!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]

Poniższy przykład pokazuje logikę dla `NumericUpDown`.

[!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
[!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
