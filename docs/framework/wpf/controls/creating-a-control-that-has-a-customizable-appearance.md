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
ms.openlocfilehash: 9f539e7dbb105591375857122d738fddd87f6776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Tworzenie formantu, którego wygląd można dostosować
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia możliwość tworzenia można dostosować, którego wygląd formantu. Na przykład można zmienić wygląd <xref:System.Windows.Controls.CheckBox> poza jakiego ustawienie właściwości będzie zrobić, tworząc nowe <xref:System.Windows.Controls.ControlTemplate>. Na poniższej ilustracji pokazano <xref:System.Windows.Controls.CheckBox> używające domyślnego <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.CheckBox> używającej niestandardowego <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Pole wyboru przy użyciu domyślnego szablonu kontroli. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Pole wyboru, które korzysta z domyślnego szablonu formantu  
  
 ![Pole wyboru przy użyciu szablonu niestandardowego formantu. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Pole wyboru, które używa szablonu formantu niestandardowego  
  
 Po wykonaniu części i stanów modelu, gdy formant zostanie utworzony, wygląd formantu, będzie można dostosowywać. Narzędzia projektanta, takich jak Microsoft Expression Blend obsługuje części i stanów modelu, tak więc po wykonaniu tego modelu formantu będzie można dostosować w przypadku tych typów aplikacji.  W tym temacie omówiono części i stanów modelu oraz sposób po nim, podczas tworzenia własnego formantu. W tym temacie używa przykład kontrolkę niestandardową `NumericUpDown`, aby zilustrować założeń tego modelu.  `NumericUpDown` Kontroli Wyświetla wartość numeryczną, który użytkownik można zwiększyć lub zmniejszyć, klikając przyciski formantu.  Na poniższej ilustracji pokazano `NumericUpDown` kontrolkę, która została szczegółowo opisana w tym temacie.  
  
 ![Numericupdown — formant niestandardowy. ] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
Niestandardowe kontrolki NumericUpDown  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Wymagania wstępne](#prerequisites)  
  
-   [Części i stanów modelu](#parts_and_states_model)  
  
-   [Definiowanie struktury Visual i zachowanie Visual formantu w ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Przy użyciu części ControlTemplate w kodzie](#using_parts_of_the_controltemplate_in_code)  
  
-   [Zapewnienie kontroli kontraktu](#providing_the_control_contract)  
  
-   [Pełny przykład](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że wiesz, jak utworzyć nową <xref:System.Windows.Controls.ControlTemplate> istniejącego formantu, zapoznali się z co to są elementy na kontrakt kontroli i zrozumieć kwestie omówione w [Dostosowywanie wyglądu formant przez Tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Aby utworzyć formant, który może mieć dostosować wygląd, należy utworzyć kontrolkę, która dziedziczy po <xref:System.Windows.Controls.Control> klasy lub jednej z jego podklas innych niż <xref:System.Windows.Controls.UserControl>.  Formant, który dziedziczy <xref:System.Windows.Controls.UserControl> jest formant, który można szybko tworzyć, ale nie używa <xref:System.Windows.Controls.ControlTemplate> i nie dostosowania jego wyglądu.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Części i stanów modelu  
 Model części i stanów określa sposób definiowania struktury visual i zachowania visual formantu. Wykonać części i stanów modelu, należy wykonać następujące czynności:  
  
-   Zdefiniuj visual struktury i wizualne działanie w <xref:System.Windows.Controls.ControlTemplate> formantu.  
  
-   Wykonania niektórych najlepsze rozwiązania w przypadku formantu logiki współdziała z części kontroli szablonu.  
  
-   Podaj kontrakt sterowania, aby określić, powinny być uwzględnione w <xref:System.Windows.Controls.ControlTemplate>.  
  
 Podczas definiowania struktury visual i wizualne działanie w <xref:System.Windows.Controls.ControlTemplate> formantu, autorzy aplikacji można zmienić struktury visual i zachowanie visual formantu, tworząc nowe <xref:System.Windows.Controls.ControlTemplate> zamiast pisania kodu.   Należy podać autorów kontraktu formant, który określa, że aplikacja, która <xref:System.Windows.FrameworkElement> obiektów i stanów powinien być zdefiniowany w <xref:System.Windows.Controls.ControlTemplate>. Należy stosować najlepsze rozwiązania podczas interakcji z części <xref:System.Windows.Controls.ControlTemplate> tak, aby prawidłowo formantu obsługuje niekompletną <xref:System.Windows.Controls.ControlTemplate>.  Jeśli wykonujesz te trzy zasady, autorzy aplikacji będzie można utworzyć <xref:System.Windows.Controls.ControlTemplate> dla formantu tylko ich łatwo można formantów dostarczane z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Poniższa sekcja zawiera każdego z tych zaleceń szczegółowo.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definiowanie struktury Visual i zachowanie Visual formantu w ControlTemplate  
 Podczas tworzenia niestandardowego formantu przy użyciu części i stanów modelu, zdefiniuj formantu visual struktury i wizualne działanie w jego <xref:System.Windows.Controls.ControlTemplate> zamiast w swojej logiki.  Struktury visual formantu jest złożone z <xref:System.Windows.FrameworkElement> obiektów, które tworzą formantu.  Zachowanie visual jest sposób wyświetlania formantu, gdy jest on w stanie niektórych.   Aby uzyskać więcej informacji o tworzeniu <xref:System.Windows.Controls.ControlTemplate> , który określa visual struktury i zachowanie visual formantu, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
 W przykładzie `NumericUpDown` kontroli, struktura visual zawiera dwie <xref:System.Windows.Controls.Primitives.RepeatButton> formantów i <xref:System.Windows.Controls.TextBlock>.  Jeśli dodasz tych kontrolek w kodzie `NumericUpDown` formantu — w jego konstruktora, na przykład pozycji tych kontrolek będzie aspektów.  Zamiast definiować visual strukturę i zachowanie visual formantu w jego kod, należy zdefiniować w <xref:System.Windows.Controls.ControlTemplate>.  Aby dostosować położenie przycisków następnie Deweloper aplikacji i <xref:System.Windows.Controls.TextBlock> i określ, jakie zachowanie podczas `Value` jest ujemna. ponieważ <xref:System.Windows.Controls.ControlTemplate> można zastąpić.  
  
 W poniższym przykładzie przedstawiono struktury visual `NumericUpDown` formant, który zawiera <xref:System.Windows.Controls.Primitives.RepeatButton> zwiększające `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> zmniejszyć `Value`, a <xref:System.Windows.Controls.TextBlock> do wyświetlenia `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Zachowanie visual `NumericUpDown` formant jest, czy wartość jest czcionką czerwony, gdy jest ujemna.  Jeśli zmienisz <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> w przypadku kodu `Value` jest ujemna, `NumericUpDown` zawsze będzie widoczna wartość ujemną czerwony. Określ zachowanie visual formantu w <xref:System.Windows.Controls.ControlTemplate> przez dodanie <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.Controls.ControlTemplate>.  W poniższym przykładzie przedstawiono <xref:System.Windows.VisualState> obiektów na `Positive` i `Negative` stanów.  `Positive` i `Negative` są wzajemnie (formant jest zawsze w dokładnie jeden z dwóch), więc umieszcza przykładzie <xref:System.Windows.VisualState> obiektów w ramach jednej <xref:System.Windows.VisualStateGroup>.  Gdy formant przechodzi do `Negative` stanu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> zmienia kolor na czerwony.  Gdy formant jest w `Positive` stanu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> zwraca do jej oryginalnej wartości.  Definiowanie <xref:System.Windows.VisualState> obiekty w <xref:System.Windows.Controls.ControlTemplate> opisane w [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Należy ustawić <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość w katalogu głównym <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Przy użyciu części ControlTemplate w kodzie  
 A <xref:System.Windows.Controls.ControlTemplate> Autor może pominąć <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState> obiekty, celowo lub przez pomyłkę, ale logiki formantu może być konieczne części działać prawidłowo. Model części i stanów określa, że formant powinien być odporny na <xref:System.Windows.Controls.ControlTemplate> której brakuje <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState> obiektów.  Formant powinien nie zgłoszenie wyjątku lub raport błędu, jeśli <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, lub <xref:System.Windows.VisualStateGroup> brakuje <xref:System.Windows.Controls.ControlTemplate>. W tej sekcji opisano najważniejsze wskazówki dotyczące interakcji z <xref:System.Windows.FrameworkElement> obiektów i zarządzanie nimi Stany.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Przewidywać Brak FrameworkElement obiektów  
 Podczas definiowania <xref:System.Windows.FrameworkElement> obiekty w <xref:System.Windows.Controls.ControlTemplate>, logiki formantu może być konieczne do interakcji z niektóre z nich.  Na przykład `NumericUpDown` kontroli subskrybuje przycisków <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń, aby zwiększyć lub zmniejszyć `Value` i ustawia <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość <xref:System.Windows.Controls.TextBlock> do `Value`. Jeśli niestandardowego <xref:System.Windows.Controls.ControlTemplate> pomija <xref:System.Windows.Controls.TextBlock> lub przyciski, dopuszcza się, że formant utraci niektórych jej funkcji, ale należy upewnić się, że formant nie powoduje błąd. Na przykład jeśli <xref:System.Windows.Controls.ControlTemplate> nie zawiera przycisk, aby zmienić `Value`, `NumericUpDown` utraci te funkcje, ale aplikacji, która używa <xref:System.Windows.Controls.ControlTemplate> będzie kontynuował działanie.  
  
 Zapewnia następujące rozwiązania formantu odpowiada prawidłowo brakuje <xref:System.Windows.FrameworkElement> obiektów:  
  
1.  Ustaw `x:Name` atrybutu dla każdej <xref:System.Windows.FrameworkElement> potrzebne do odwołania w kodzie.  
  
2.  Definiowanie właściwości prywatne dla każdego <xref:System.Windows.FrameworkElement> potrzebne do interakcji z.  
  
3.  Subskrybowanie i anulowanie subskrypcji wszelkie zdarzenia, które obsługuje formantu w <xref:System.Windows.FrameworkElement> właściwości ustawione przez metody dostępu.  
  
4.  Ustaw <xref:System.Windows.FrameworkElement> właściwości zdefiniowane w kroku 2 <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metody. Jest to najmniej który <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate> jest dostępny do formantu. Użyj `x:Name` z <xref:System.Windows.FrameworkElement> go z <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Sprawdź, czy <xref:System.Windows.FrameworkElement> nie jest `null` przed uzyskaniem dostępu do jego elementów członkowskich.  Jeśli jest `null`, będą zgłaszać błąd.  
  
 W poniższych przykładach pokazano sposób `NumericUpDown` kontroli współdziała z <xref:System.Windows.FrameworkElement> obiekty zgodnie z zaleceniami w powyższej listy.  
  
 W tym przykładzie, który definiuje strukturę visual `NumericUpDown` kontroli w <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> , która zwiększa `Value` ma jego `x:Name` ustawić atrybutu `UpButton`.  Poniższy przykład deklaruje właściwość o nazwie `UpButtonElement` reprezentujący <xref:System.Windows.Controls.Primitives.RepeatButton> zadeklarowanego w <xref:System.Windows.Controls.ControlTemplate>. `set` Akcesor najpierw cofnięć subskrypcji na przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń Jeśli `UpDownElement` nie jest `null`, następnie ustawia właściwość, a następnie subskrybuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Istnieje również właściwość zdefiniowana, ale nie jest tutaj widoczny, dla pozostałych <xref:System.Windows.Controls.Primitives.RepeatButton>o nazwie `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> dla `NumericUpDown` formantu.  W przykładzie użyto <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodę, aby pobrać <xref:System.Windows.FrameworkElement> obiektów z <xref:System.Windows.Controls.ControlTemplate>.  Należy zauważyć, że w tym przykładzie chroni przed przypadków, gdy <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> znajdzie <xref:System.Windows.FrameworkElement> o określonej nazwie, która nie jest oczekiwanego typu. Istnieje również najlepszym rozwiązaniem, aby zignorować elementów, które mają określony `x:Name` , ale są nieprawidłowego typu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Wykonując rozwiązania, które przedstawiono w poprzednich przykładach, upewnieniu się, czy formant będzie nadal uruchomiony, jeśli <xref:System.Windows.Controls.ControlTemplate> brakuje <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Umożliwia zarządzanie stanów VisualStateManager  
 <xref:System.Windows.VisualStateManager> Przechowuje informacje o stanach formantu i wykonuje logiki niezbędne do przejścia między stanami. Po dodaniu <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.Controls.ControlTemplate>, dodaj je do <xref:System.Windows.VisualStateGroup> i Dodaj <xref:System.Windows.VisualStateGroup> do <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość, aby <xref:System.Windows.VisualStateManager> ma dostęp do nich.  
  
 Poniższy przykład powtarza poprzedni przykład, który pokazuje <xref:System.Windows.VisualState> obiektów, które odpowiada `Positive` i `Negative` stanów formantu. <xref:System.Windows.Media.Animation.Storyboard> w `Negative` <xref:System.Windows.VisualState> włącza <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> czerwony.   Gdy `NumericUpDown` formant jest w `Negative` stanu scenorysu w `Negative` rozpoczyna się stan.  Następnie przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w `Negative` stanu zatrzymuje, gdy formant powróci do `Positive` stanu.  `Positive` <xref:System.Windows.VisualState> Nie musi zawierać <xref:System.Windows.Media.Animation.Storyboard> ponieważ podczas <xref:System.Windows.Media.Animation.Storyboard> dla `Negative` zatrzymuje, <xref:System.Windows.Controls.TextBlock.Foreground%2A> zwraca oryginalnego koloru.  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Należy pamiętać, że <xref:System.Windows.Controls.TextBlock> podano nazwę, ale <xref:System.Windows.Controls.TextBlock> nie jest w kontrakcie kontroli dla `NumericUpDown` ponieważ logiki formantu nigdy nie odwołuje się do <xref:System.Windows.Controls.TextBlock>.  Elementy, które są używane w <xref:System.Windows.Controls.ControlTemplate> mają nazwy, ale nie muszą być częścią kontraktu kontroli, ponieważ nowy <xref:System.Windows.Controls.ControlTemplate> dla formantu nie może być konieczne odwołania tego elementu.  Na przykład osoby, która tworzy nowy <xref:System.Windows.Controls.ControlTemplate> dla `NumericUpDown` może zdecydować, które nie wskazują, że `Value` jest ujemna, zmieniając <xref:System.Windows.Controls.Control.Foreground%2A>.  W takim przypadku żaden kod ani <xref:System.Windows.Controls.ControlTemplate> odwołania <xref:System.Windows.Controls.TextBlock> według nazwy.  
  
 Logika formantu jest odpowiedzialny za zmianą stanu formantu. W poniższym przykładzie pokazano, że `NumericUpDown` kontrolować wywołania <xref:System.Windows.VisualStateManager.GoToState%2A> metody, aby przejść do `Positive` Jeśli `Value` jest mniejsza od 0 i `Negative` Jeśli `Value` jest mniejszy niż 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Metoda przeprowadza niezbędne do uruchamiania i zatrzymywania scenorys odpowiednio logiki. Gdy formant wymaga <xref:System.Windows.VisualStateManager.GoToState%2A> zmiany jego stanu <xref:System.Windows.VisualStateManager> wykonuje następujące czynności:  
  
-   Jeśli <xref:System.Windows.VisualState> czy zamierza formantu ma <xref:System.Windows.Media.Animation.Storyboard>, rozpoczyna się scenorysu. Następnie, jeśli <xref:System.Windows.VisualState> czy kontrolka jest pochodzi z ma <xref:System.Windows.Media.Animation.Storyboard>, zakończenia scenorysu.  
  
-   Jeśli formant jest już w stanie, który jest określony, <xref:System.Windows.VisualStateManager.GoToState%2A> Brak działania i zwraca `true`.  
  
-   Jeśli stan, który jest określony, nie istnieje w <xref:System.Windows.Controls.ControlTemplate> z `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> Brak działania i zwraca `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Najlepsze rozwiązania dotyczące pracy z VisualStateManager  
 Zalecane jest wykonanie następujących czynności, aby zachować stanów formantu:  
  
-   Użyj właściwości w celu śledzenia stanu.  
  
-   Tworzenie metody pomocnika do przejścia między stanami.  
  
 `NumericUpDown` Kontrolować używa jej `Value` właściwość, aby sprawdzić, czy jest on `Positive` lub `Negative` stanu.  `NumericUpDown` Definiuje również kontroli `Focused` i `UnFocused` stany, które ścieżki <xref:System.Windows.UIElement.IsFocused%2A> właściwości. Jeśli używasz stanów, które nie odpowiadają naturalnie właściwości formantu, można zdefiniować właściwości prywatnej śledzenie stanu.  
  
 Pojedynczej metody, która aktualizuje wszystkie stany centralizuje wywołań <xref:System.Windows.VisualStateManager> i zachowuje swój kod zarządzany. W poniższym przykładzie przedstawiono `NumericUpDown` metody pomocnika formantu `UpdateStates`. Gdy `Value` jest większa niż lub równa 0, <xref:System.Windows.Controls.Control> w `Positive` stanu.  Gdy `Value` jest mniejszy niż 0, znajduje się kontrolka `Negative` stanu.  Gdy <xref:System.Windows.UIElement.IsFocused%2A> jest `true`, znajduje się kontrolka `Focused` stanu; w przeciwnym razie jest w `Unfocused` stanu.  Formant może wywołać `UpdateStates` zawsze, gdy zachodzi potrzeba zmiany jego stanu, niezależnie od tego, jakie stan zmieni się.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 W przypadku przekazania nazwę stanu, aby <xref:System.Windows.VisualStateManager.GoToState%2A> gdy formant jest już w tym stanie <xref:System.Windows.VisualStateManager.GoToState%2A> nie działa, więc nie trzeba Sprawdź, czy bieżący stan formantu.  Na przykład jeśli `Value` zmienia się z jednego ujemną innego ujemną, scenorysu dla `Negative` stanu nie zostało przerwane i użytkownik nie zobaczą zmiany w formancie.  
  
 <xref:System.Windows.VisualStateManager> Używa <xref:System.Windows.VisualStateGroup> obiektów, aby określić, które stanu, aby zakończyć działanie podczas wywoływania <xref:System.Windows.VisualStateManager.GoToState%2A>. Formant zawsze znajduje się na jeden stan dla każdego <xref:System.Windows.VisualStateGroup> zdefiniowanego w jego <xref:System.Windows.Controls.ControlTemplate> i tylko pozostawia stanie, gdy jej przechodzi w stan innego z tej samej <xref:System.Windows.VisualStateGroup>. Na przykład <xref:System.Windows.Controls.ControlTemplate> z `NumericUpDown` definiuje kontroli `Positive` i `Negative` <xref:System.Windows.VisualState> obiektów w jednym <xref:System.Windows.VisualStateGroup> i `Focused` i `Unfocused` <xref:System.Windows.VisualState> obiektów w innym. (Widoczny `Focused` i `Unfocused` <xref:System.Windows.VisualState> zdefiniowane w [pełny przykład](#complete_example) w tym temacie, gdy formant przechodzi z `Positive` stan `Negative` stanu, albo na odwrót formant pozostanie w jednym `Focused` lub `Unfocused` stanu.  
  
 Istnieją trzy typowe miejsca, gdzie może zmienić stan formantu:  
  
-   Gdy <xref:System.Windows.Controls.ControlTemplate> jest stosowany do <xref:System.Windows.Controls.Control>.  
  
-   Podczas zmiany właściwości.  
  
-   Gdy wystąpi zdarzenie.  
  
 W poniższych przykładach pokazano, aktualizowania stanu `NumericUpDown` kontroli w tych przypadkach.  
  
 Należy zaktualizować stanu formantu w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> — metoda tak, aby ten formant jest widoczny w poprawny stan, kiedy <xref:System.Windows.Controls.ControlTemplate> została zastosowana. Następujące przykładowe wywołania `UpdateStates` w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> aby upewnić się, że formant jest w Stanach odpowiednie.  Załóżmy na przykład, aby utworzyć `NumericUpDown` kontroli, a następnie ustaw jego <xref:System.Windows.Controls.Control.Foreground%2A> zielony i `Value` do -5.  Jeśli nie zostanie wywołana `UpdateStates` podczas <xref:System.Windows.Controls.ControlTemplate> jest stosowany do `NumericUpDown` formantu, formantu nie znajduje się w `Negative` stanu i wartość jest zielony zamiast czerwony.  Należy wywołać `UpdateStates` mają zostać umieszczone w formancie `Negative` stanu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Często wymaga zaktualizowania stanów formantu podczas zmiany właściwości. Poniższy przykład przedstawia całą `ValueChangedCallback` metody. Ponieważ `ValueChangedCallback` jest wywoływane, gdy `Value` zmienia wywołania metody `UpdateStates` w przypadku `Value` zmieniła się z dodatnie ujemny lub odwrotnie. Można wywołać `UpdateStates` podczas `Value` zmiany, ale pozostaje dodatnie lub ujemne, ponieważ w takim przypadku formantu nie spowoduje zmiany stanów.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Może być konieczne również zaktualizować stanów, gdy wystąpi zdarzenie. W poniższym przykładzie pokazano, że `NumericUpDown` wywołania `UpdateStates` na <xref:System.Windows.Controls.Control> do obsługi <xref:System.Windows.UIElement.GotFocus> zdarzeń.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Pomaga w zarządzaniu stanów formantu. Za pomocą <xref:System.Windows.VisualStateManager>, upewnij się, że formant poprawnie przejścia między stanami.  Jeśli należy postępować zgodnie z zaleceniami opisane w tej sekcji do pracy z <xref:System.Windows.VisualStateManager>, kod formantu będzie można odczytać i łatwy w obsłudze.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Zapewnienie kontroli kontraktu  
 Podaj kontrakt sterowania, aby <xref:System.Windows.Controls.ControlTemplate> autorów wiedzą, jakie można umieścić w szablonie. Kontrakt formantu ma trzy elementy:  
  
-   Elementy wizualne, które używa logiki formantu.  
  
-   Stany formantu i grupy, do której należy każdy stan.  
  
-   Właściwości publiczne, które wizualnie wpływają na formantu.  
  
 Osoby, która tworzy nowy <xref:System.Windows.Controls.ControlTemplate> musi wiedzieć, jaki <xref:System.Windows.FrameworkElement> logika formantu używa obiektów, co typ każdego obiektu jest, i jakie jego nazwa jest. A <xref:System.Windows.Controls.ControlTemplate> Autor również musi znać nazwę możliwe stany mogą należeć do formantu i które <xref:System.Windows.VisualStateGroup> jest stan.  
  
 Powrót do `NumericUpDown` oczekuje formantu przykład <xref:System.Windows.Controls.ControlTemplate> mają następujące <xref:System.Windows.FrameworkElement> obiektów:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `UpButton`.  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `DownButton.`  
  
 Formant może być w następujących stanów:  
  
-   W `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   W `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Aby określić, co <xref:System.Windows.FrameworkElement> oczekuje formantu obiektów, możesz użyć <xref:System.Windows.TemplatePartAttribute>, który określa nazwę i typ oczekiwanych elementów.  Aby określić możliwe stany formantu, należy użyć <xref:System.Windows.TemplateVisualStateAttribute>, który określa nazwę stanu, które <xref:System.Windows.VisualStateGroup> on należy.  Umieść <xref:System.Windows.TemplatePartAttribute> i <xref:System.Windows.TemplateVisualStateAttribute> w definicji klasy formantu.  
  
 Właściwość publiczna, która wpływa na wygląd formantu jest również częścią kontraktu formantu.  
  
 W poniższym przykładzie <xref:System.Windows.FrameworkElement> obiekt i stanów `NumericUpDown` formantu.  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy przykład dotyczy całego <xref:System.Windows.Controls.ControlTemplate> dla `NumericUpDown` formantu.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 W poniższym przykładzie pokazano logikę `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
