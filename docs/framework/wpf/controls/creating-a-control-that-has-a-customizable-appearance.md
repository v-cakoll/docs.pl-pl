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
ms.openlocfilehash: bb82921070cb5040cd279830bafd3d0e718d1374
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372714"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>Tworzenie formantu, którego wygląd można dostosować
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia możliwość tworzenia formantu, którego wygląd można dostosować. Na przykład można zmienić wygląd <xref:System.Windows.Controls.CheckBox> po przekroczeniu którego ustawienia właściwości wykona się przez utworzenie nowego <xref:System.Windows.Controls.ControlTemplate>. Poniższa ilustracja przedstawia <xref:System.Windows.Controls.CheckBox> używającej domyślny <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.CheckBox> , który używa niestandardowego <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Pole wyboru przy użyciu domyślnego szablonu kontrolki. ](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaznacz pole wyboru, która korzysta z domyślnego szablonu kontrolki  
  
 ![Pole wyboru przy użyciu szablonu kontrolki niestandardowej. ](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaznacz pole wyboru, który używa szablonu kontrolki niestandardowej  
  
 Jeśli stosujesz części i stanów modelu, po utworzeniu kontrolki, wygląd formantu będzie można dostosowywać. Narzędzia projektanta, takich jak Microsoft Expression Blend obsługuje części i stanów modelu, więc po wykonaniu tego modelu kontroli nad będą dostosowywane w tych typów aplikacji.  W tym temacie omówiono części i stanów modelu oraz sposób prześledzonych, tworząc własny formant. W tym temacie używany jest przykład formantu niestandardowego, `NumericUpDown`, aby zilustrować filozofia tego modelu.  `NumericUpDown` Kontrolka Wyświetla wartość liczbowa, w której użytkownik może zwiększyć lub zmniejszyć, klikając przyciski formantu.  Poniższa ilustracja przedstawia `NumericUpDown` formant, który jest omówione w tym temacie.  
  
 ![Numericupdown — formant niestandardowy. ](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
Niestandardowy formant NumericUpDown  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Wymagania wstępne](#prerequisites)  
  
-   [Części i stanów modelu](#parts_and_states_model)  
  
-   [Definiowanie struktury wizualnej i zachowanie Visual kontrolki w ControlTemplate](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [Przy użyciu części ControlTemplate w kodzie](#using_parts_of_the_controltemplate_in_code)  
  
-   [Zapewnianie kontrakt formantu](#providing_the_control_contract)  
  
-   [Kompletny przykład](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że wiesz, jak utworzyć nową <xref:System.Windows.Controls.ControlTemplate> istniejącego formantu, którzy znają co to są elementy na kontrakt formantu i zrozumieć kwestie omówione w [Dostosowywanie wyglądu istniejącego formantu przez Tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Aby utworzyć formant, który może mieć jego wygląd dostosowane, należy utworzyć formant, który dziedziczy z <xref:System.Windows.Controls.Control> klasy lub jednej z jej podklasach innych niż <xref:System.Windows.Controls.UserControl>.  Kontrolka, która dziedziczy po elemencie <xref:System.Windows.Controls.UserControl> jest formant, który można szybko tworzyć, ale nie używa <xref:System.Windows.Controls.ControlTemplate> i nie dostosowania jego wyglądu.  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>Części i stanów modelu  
 Części i Stany model Określa, jak Definiowanie struktury wizualnej i zachowanie visual kontrolki. Aby skorzystać z części i stanów modelu, należy wykonać następujące:  
  
-   Definiowanie struktury wizualnej i zachowanie visual <xref:System.Windows.Controls.ControlTemplate> formantu.  
  
-   Należy wykonać niektóre najlepsze rozwiązania, podczas kontroli nad logika interakcji z części szablonu kontrolki.  
  
-   Podaj kontrakt formantu, aby określić, jakie powinny być uwzględnione w <xref:System.Windows.Controls.ControlTemplate>.  
  
 Kiedy definiujesz struktury wizualnej i zachowanie visual <xref:System.Windows.Controls.ControlTemplate> kontrolki, autorzy aplikacji można zmienić struktury efektów wizualnych i wizualne zachowanie kontroli nad przez utworzenie nowego <xref:System.Windows.Controls.ControlTemplate> zamiast pisania kodu.   Należy podać autorów kontrakt formantu, który informuje aplikację, która <xref:System.Windows.FrameworkElement> obiektów i Stany powinien być zdefiniowany w <xref:System.Windows.Controls.ControlTemplate>. Należy przestrzegać najważniejsze wskazówki podczas interakcji z części w <xref:System.Windows.Controls.ControlTemplate> tak, aby formant poprawnie obsługuje niepełnego <xref:System.Windows.Controls.ControlTemplate>.  Jeśli wykonasz te trzy zasady, autorzy aplikacji będzie można utworzyć <xref:System.Windows.Controls.ControlTemplate> kontrolki po prostu równie łatwo, jak one można formantów dostarczane z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  W poniższej sekcji omówiono każdy z tych zaleceń szczegółowo.  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>Definiowanie struktury wizualnej i zachowanie Visual kontrolki w ControlTemplate  
 Tworząc niestandardową kontrolkę za pomocą części i stanów modelu, Definiowanie struktury wizualnej i zachowanie visual kontrolki jego <xref:System.Windows.Controls.ControlTemplate> zamiast w swojej logiki.  Struktura visual kontrolki jest złożone z <xref:System.Windows.FrameworkElement> obiekty, które tworzą formantu.  Zachowanie visual jest sposób ten formant jest widoczny, gdy jest on w pewnego stanu.   Aby uzyskać więcej informacji o tworzeniu <xref:System.Windows.Controls.ControlTemplate> , który określa struktury wizualnej i zachowanie visual formantu, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
 W przykładzie `NumericUpDown` kontroli struktury efektów wizualnych zawiera dwie <xref:System.Windows.Controls.Primitives.RepeatButton> kontrolek i <xref:System.Windows.Controls.TextBlock>.  Jeśli dodasz te kontrolki w kodzie `NumericUpDown` kontroli — w jego konstruktorze, na przykład położenie te kontrolki będą aspektów.  Zamiast Definiowanie struktury wizualnej i zachowanie visual formantu w jej kodzie, należy zdefiniować w <xref:System.Windows.Controls.ControlTemplate>.  Następnie Deweloper aplikacji można dostosować położenie przycisków i <xref:System.Windows.Controls.TextBlock> i określić, jakie zachowanie podczas `Value` jest negatywna, ponieważ <xref:System.Windows.Controls.ControlTemplate> można zastąpić.  
  
 Poniższy przykład pokazuje strukturę visual `NumericUpDown` formant, który zawiera <xref:System.Windows.Controls.Primitives.RepeatButton> zwiększyć `Value`, <xref:System.Windows.Controls.Primitives.RepeatButton> zmniejszyć `Value`, a <xref:System.Windows.Controls.TextBlock> do wyświetlenia `Value`.  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 Zachowanie visual `NumericUpDown` formant jest, czy wartość jest czcionką czerwony, gdy jest ujemna.  Jeśli zmienisz <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> w kodzie, gdy `Value` jest ujemna, `NumericUpDown` będzie zawsze wyświetlana z czerwonym wartości ujemnej. Określ visual zachowanie kontrolki <xref:System.Windows.Controls.ControlTemplate> , dodając <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.Controls.ControlTemplate>.  W poniższym przykładzie przedstawiono <xref:System.Windows.VisualState> obiektów dla `Positive` i `Negative` stanów.  `Positive` i `Negative` są wzajemnie się wykluczają (formant jest zawsze w dokładnie jeden z dwóch), dlatego umieszcza przykład <xref:System.Windows.VisualState> obiektów w jednym <xref:System.Windows.VisualStateGroup>.  Gdy kontrolka przechodzi w stan `Negative` stanu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> zmieni kolor na czerwony.  Gdy kontrolka jest w `Positive` stanu, <xref:System.Windows.Controls.TextBlock.Foreground%2A> zwracanie do niego oryginalną wartość.  Definiowanie <xref:System.Windows.VisualState> obiekty w <xref:System.Windows.Controls.ControlTemplate> jest opisane w dalszych [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
> [!NOTE]
>  Pamiętaj ustawić <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość w katalogu głównym <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>Przy użyciu części ControlTemplate w kodzie  
 A <xref:System.Windows.Controls.ControlTemplate> Autor może pominąć <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState> obiektów, celowo lub przez pomyłkę, ale logiki kontroli nad potrzebować te części, aby działać prawidłowo. Model części i Stany Określa, że formant powinien być odporny na <xref:System.Windows.Controls.ControlTemplate> której brakuje <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.VisualState> obiektów.  Kontrolki powinny nie zgłoszenie wyjątku lub raport błędu, jeśli <xref:System.Windows.FrameworkElement>, <xref:System.Windows.VisualState>, lub <xref:System.Windows.VisualStateGroup> brakuje <xref:System.Windows.Controls.ControlTemplate>. W tej sekcji opisano zalecane praktyki do interakcji z <xref:System.Windows.FrameworkElement> obiektów i zarządzanie nimi Stany.  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>Przewidywanie, brak FrameworkElement — obiekty  
 Podczas definiowania <xref:System.Windows.FrameworkElement> obiekty w <xref:System.Windows.Controls.ControlTemplate>, kontroli nad logiki może być konieczne do interakcji z niektórych z nich.  Na przykład `NumericUpDown` kontroli subskrybuje przycisków <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, aby zwiększyć lub zmniejszyć `Value` i ustawia <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość <xref:System.Windows.Controls.TextBlock> do `Value`. Jeśli niestandardowa <xref:System.Windows.Controls.ControlTemplate> pomija <xref:System.Windows.Controls.TextBlock> lub przyciski, jest dopuszczalne, że formant utraci niektóre swoje funkcje, ale należy upewnić się, formant nie powoduje błąd. Na przykład jeśli <xref:System.Windows.Controls.ControlTemplate> nie zawiera przycisk, aby zmienić `Value`, `NumericUpDown` traci tę funkcję, ale aplikację, która używa <xref:System.Windows.Controls.ControlTemplate> będą nadal działać.  
  
 Następujące rozwiązania w zakresie zapewni kontroli nad odpowiada prawidłowo z brakującym <xref:System.Windows.FrameworkElement> obiektów:  
  
1.  Ustaw `x:Name` atrybutu dla każdej <xref:System.Windows.FrameworkElement> potrzebnych do odwołania w kodzie.  
  
2.  Zdefiniuj właściwości prywatny dla każdego <xref:System.Windows.FrameworkElement> , które muszą wchodzić w interakcje z.  
  
3.  Subskrybowanie i anulowanie subskrypcji z wszelkie zdarzenia, które obsługuje formant, w <xref:System.Windows.FrameworkElement> właściwości ustawione przez metody dostępu.  
  
4.  Ustaw <xref:System.Windows.FrameworkElement> właściwości, które zostały zdefiniowane w kroku 2 w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metody. Jest to najbliższej sposobności, <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate> jest dostępna dla kontrolki. Użyj `x:Name` z <xref:System.Windows.FrameworkElement> można pobrać go z <xref:System.Windows.Controls.ControlTemplate>.  
  
5.  Sprawdź, czy <xref:System.Windows.FrameworkElement> nie `null` przed uzyskaniem dostępu do składowych.  Jeśli jest `null`, zgłasza błąd.  
  
 W poniższych przykładach pokazano sposób, w jaki `NumericUpDown` kontroli wchodzi w interakcję z <xref:System.Windows.FrameworkElement> obiekty zgodnie z zaleceniami z powyższej listy.  
  
 W przykładzie, który definiuje strukturę visual `NumericUpDown` w kontrolce <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.Primitives.RepeatButton> , która zwiększa `Value` ma jego `x:Name` ustawioną wartość atrybutu `UpButton`.  Poniższy przykład deklaruje właściwość o nazwie `UpButtonElement` reprezentujący <xref:System.Windows.Controls.Primitives.RepeatButton> zadeklarowanego w <xref:System.Windows.Controls.ControlTemplate>. `set` Akcesor najpierw anulowań subskrypcji na przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń Jeśli `UpDownElement` nie `null`, następnie ustawia właściwości i następnie subskrybuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń. Istnieje również właściwość zdefiniowana, ale nie jest tutaj widoczny, dla siebie <xref:System.Windows.Controls.Primitives.RepeatButton>, co jest nazywane `DownButtonElement`.  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> dla `NumericUpDown` kontroli.  W przykładzie użyto <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> metodę, aby uzyskać <xref:System.Windows.FrameworkElement> obiekty <xref:System.Windows.Controls.ControlTemplate>.  Należy zauważyć, że przykład chroni przed przypadków, gdy <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> znajdzie <xref:System.Windows.FrameworkElement> o określonej nazwie, który nie jest oczekiwanego typu. Warto również najlepszym rozwiązaniem, aby zignorować elementy, które mają określony `x:Name` , ale jest nieprawidłowego typu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Korzystając z rozwiązań, które są wyświetlane w poprzednich przykładach, można zapewnić, że formant będą w dalszym ciągu uruchamiać, gdy <xref:System.Windows.Controls.ControlTemplate> brakuje <xref:System.Windows.FrameworkElement>.  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>Użyj VisualStateManager do zarządzania Stanami  
 <xref:System.Windows.VisualStateManager> Śledzi stanów kontrolki i wykonuje logikę niezbędną do przejścia między stanami. Po dodaniu <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.Controls.ControlTemplate>, dodać je do <xref:System.Windows.VisualStateGroup> i Dodaj <xref:System.Windows.VisualStateGroup> do <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość tak, aby <xref:System.Windows.VisualStateManager> dostępu do nich.  
  
 Poniższy przykład jest powtarzany poprzedniego przykładu, który pokazuje <xref:System.Windows.VisualState> obiektów, które odpowiada `Positive` i `Negative` stanów kontrolki. <xref:System.Windows.Media.Animation.Storyboard> w `Negative` <xref:System.Windows.VisualState> włącza <xref:System.Windows.Controls.TextBlock.Foreground%2A> z <xref:System.Windows.Controls.TextBlock> czerwony.   Gdy `NumericUpDown` kontrolka znajduje się w `Negative` stan scenorysu w `Negative` rozpoczyna się w stanie.  A następnie <xref:System.Windows.Media.Animation.Storyboard> w `Negative` stanu zatrzymuje, gdy sterowanie powraca do `Positive` stanu.  `Positive` <xref:System.Windows.VisualState> Nie musi zawierać <xref:System.Windows.Media.Animation.Storyboard> ponieważ gdy <xref:System.Windows.Media.Animation.Storyboard> dla `Negative` zatrzymaniu <xref:System.Windows.Controls.TextBlock.Foreground%2A> powróci do oryginalnego koloru.  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 Należy pamiętać, że <xref:System.Windows.Controls.TextBlock> jest nadawana nazwa, ale <xref:System.Windows.Controls.TextBlock> nie jest w kontrakcie kontroli dla `NumericUpDown` ponieważ nigdy nie odwołuje się od logiki formantu <xref:System.Windows.Controls.TextBlock>.  Elementy, które odwołują się <xref:System.Windows.Controls.ControlTemplate> mają nazwy, ale nie muszą być częścią kontraktu kontroli, ponieważ nowy <xref:System.Windows.Controls.ControlTemplate> dla formantu nie może być konieczne odwoływać się do tego elementu.  Na przykład osoba, która tworzy nową <xref:System.Windows.Controls.ControlTemplate> dla `NumericUpDown` mogą zdecydować się na nie wskazują, że `Value` jest ujemna, zmieniając <xref:System.Windows.Controls.Control.Foreground%2A>.  W tym przypadku, żaden kod ani <xref:System.Windows.Controls.ControlTemplate> odwołania <xref:System.Windows.Controls.TextBlock> według nazwy.  
  
 Od logiki formantu jest odpowiedzialny za zmieniają stan kontrolki. Poniższy przykład pokazuje, że `NumericUpDown` kontrolować wywołania <xref:System.Windows.VisualStateManager.GoToState%2A> metodę, aby przejść do `Positive` Jeśli `Value` jest mniejsza od 0 i `Negative` Jeśli `Value` jest mniejszy niż 0.  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> Metoda wykonuje logikę niezbędną do uruchamiania i zatrzymywania scenorysy odpowiednio. Kiedy wywołuje kontrolki <xref:System.Windows.VisualStateManager.GoToState%2A> zmiany jego stanu <xref:System.Windows.VisualStateManager> wykonuje następujące czynności:  
  
-   Jeśli <xref:System.Windows.VisualState> czy zamierza kontrolki ma <xref:System.Windows.Media.Animation.Storyboard>, rozpoczyna się scenorysu. Następnie, jeśli <xref:System.Windows.VisualState> że kontrolki pochodzi z ma <xref:System.Windows.Media.Animation.Storyboard>, kończy się scenorysu.  
  
-   Jeśli formant znajduje się już w stanie, który jest określony, <xref:System.Windows.VisualStateManager.GoToState%2A> nie podejmuje żadnych działań i zwraca `true`.  
  
-   Jeśli stan, który jest określony, nie istnieje w <xref:System.Windows.Controls.ControlTemplate> z `control`, <xref:System.Windows.VisualStateManager.GoToState%2A> nie podejmuje żadnych działań i zwraca `false`.  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>Najlepsze rozwiązania dotyczące pracy z VisualStateManager  
 Zaleca się wykonanie następujących czynności, aby zachować stany kontroli nad:  
  
-   Używaj właściwości, aby śledzić jego stan.  
  
-   Tworzenie metody pomocnika do przejścia między stanami.  
  
 `NumericUpDown` Kontrolować używa jej `Value` właściwości w celu sprawdzenia, czy jest on `Positive` lub `Negative` stanu.  `NumericUpDown` Definiuje również kontroli `Focused` i `UnFocused` stany, które śledzi <xref:System.Windows.UIElement.IsFocused%2A> właściwości. Jeśli używasz stanów, które nie odpowiadają naturalnie właściwości formantu, można zdefiniować właściwości prywatnej do śledzenia stanu.  
  
 Pojedyncza metoda, która aktualizuje wszystkie stany centralizuje wywołania <xref:System.Windows.VisualStateManager> i przechowuje kod zarządzany. W poniższym przykładzie przedstawiono `NumericUpDown` metody pomocnika kontrolki `UpdateStates`. Gdy `Value` jest większa niż lub równa 0, <xref:System.Windows.Controls.Control> znajduje się w `Positive` stanu.  Gdy `Value` jest mniejszy niż 0, kontrolka jest w `Negative` stanu.  Gdy <xref:System.Windows.UIElement.IsFocused%2A> jest `true`, kontrolka jest w `Focused` stanu; w przeciwnym razie jest `Unfocused` stanu.  Formant może wywołać `UpdateStates` zawsze, gdy trzeba zmienić jego stan, niezależnie od tego, jaki stan zmieni się.  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 W przypadku przekazania nazwę stanu, aby <xref:System.Windows.VisualStateManager.GoToState%2A> gdy kontrolka jest już w tym stanie <xref:System.Windows.VisualStateManager.GoToState%2A> nie działa, więc nie trzeba sprawdzić bieżący stan kontrolki.  Na przykład jeśli `Value` zmieni się z jednego ujemna inną liczbę ujemną scenorys dla `Negative` stanu nie zostało przerwane i użytkownik nie będzie widział zmian w formancie.  
  
 <xref:System.Windows.VisualStateManager> Używa <xref:System.Windows.VisualStateGroup> obiektów, aby określić, których stan, aby zakończyć pracę podczas wywoływania <xref:System.Windows.VisualStateManager.GoToState%2A>. Kontrolka jest zawsze w jednym stanie dla każdego <xref:System.Windows.VisualStateGroup> zdefiniowanego w jego <xref:System.Windows.Controls.ControlTemplate> i pozostawia stan tylko, gdy przejdzie do innego stanu z tej samej <xref:System.Windows.VisualStateGroup>. Na przykład <xref:System.Windows.Controls.ControlTemplate> z `NumericUpDown` definiuje kontroli `Positive` i `Negative` <xref:System.Windows.VisualState> obiekty w jednym <xref:System.Windows.VisualStateGroup> i `Focused` i `Unfocused` <xref:System.Windows.VisualState> obiektów w innej. (Możesz zobaczyć `Focused` i `Unfocused` <xref:System.Windows.VisualState> zdefiniowane w [kompletny przykład](#complete_example) w tym temacie, gdy kontrolka przechodzi z `Positive` do stanu `Negative` stanu, lub na odwrót formant pozostanie w jednym `Focused` lub `Unfocused` stanu.  
  
 Istnieją trzy typowe miejsca, gdzie mogą ulec zmianie stanu formantu:  
  
-   Gdy <xref:System.Windows.Controls.ControlTemplate> jest stosowany do <xref:System.Windows.Controls.Control>.  
  
-   Podczas zmiany właściwości.  
  
-   Gdy wystąpi zdarzenie.  
  
 W poniższych przykładach pokazano, aktualizowanie stanu `NumericUpDown` kontroli w tych przypadkach.  
  
 Należy zaktualizować stanu formantu w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> metoda tak, aby formant ma być wyświetlany prawidłowo Jeśli <xref:System.Windows.Controls.ControlTemplate> jest stosowany. Poniższy przykład wywołuje `UpdateStates` w <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> aby upewnić się, czy kontrolka jest odpowiednie stany.  Na przykład załóżmy, że utworzono `NumericUpDown` sterowania, a następnie ustaw jego <xref:System.Windows.Controls.Control.Foreground%2A> do zielonego i `Value` do -5.  Jeśli nie zostanie wywołana `UpdateStates` podczas <xref:System.Windows.Controls.ControlTemplate> jest stosowany do `NumericUpDown` formantu, formant nie znajduje się w `Negative` stanu i wartość jest zielona zamiast czerwony.  Należy wywołać `UpdateStates` należy umieścić formant w `Negative` stanu.  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 Często muszą zaktualizować stanów kontrolki, gdy zmiany właściwości. W poniższym przykładzie przedstawiono cały `ValueChangedCallback` metody. Ponieważ `ValueChangedCallback` jest wywoływana, gdy `Value` zmienia wywołania metody `UpdateStates` w przypadku, gdy `Value` zmieniła się z dodatnie, ujemne lub odwrotnie. Można wywołać `UpdateStates` podczas `Value` zmienia, ale pozostaje dodatnie lub ujemne, ponieważ w takim przypadku kontrolka nie spowoduje zmiany stanów.  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 Również może być konieczne zaktualizowanie stanów, po wystąpieniu zdarzenia. Poniższy przykład pokazuje, że `NumericUpDown` wywołania `UpdateStates` na <xref:System.Windows.Controls.Control> do obsługi <xref:System.Windows.UIElement.GotFocus> zdarzeń.  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> Ułatwia zarządzanie stanami formantu. Za pomocą <xref:System.Windows.VisualStateManager>, upewnij się, że formant poprawnie przejścia między stanami.  Jeśli stosujesz zalecenia opisane w tej sekcji do pracy z <xref:System.Windows.VisualStateManager>, kod kontroli nad będzie czytelny i łatwy w obsłudze.  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>Zapewnianie kontrakt formantu  
 Należy podać kontrakt formantu, aby <xref:System.Windows.Controls.ControlTemplate> autorzy będzie wiadomo, jakie można umieścić w szablonie. Kontrakt formantu ma trzy elementy:  
  
-   Elementy wizualne, których używa logiki formantu.  
  
-   Stany i grupy, której każdy stan kontrolki.  
  
-   Właściwości publiczne, które wizualnie wpływają na formant.  
  
 Osoba, która tworzy nową <xref:System.Windows.Controls.ControlTemplate> musi wiedzieć, jakie <xref:System.Windows.FrameworkElement> obiektów używa logiki formantu, jaki typ każdego obiektu jest i jakie jego nazwa jest. A <xref:System.Windows.Controls.ControlTemplate> autor musi także znać nazwę kontrolki mogą znajdować się w możliwe stany i które <xref:System.Windows.VisualStateGroup> jest.  
  
 Wracając do `NumericUpDown` oczekuje, że kontrolka przykład <xref:System.Windows.Controls.ControlTemplate> mieć następujące <xref:System.Windows.FrameworkElement> obiektów:  
  
-   A <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `UpButton`.  
  
-   Element <xref:System.Windows.Controls.Primitives.RepeatButton> o nazwie `DownButton.`  
  
 Formant może być w jednym z następujących stanów:  
  
-   W `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   W `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 Umożliwiające określenie, co <xref:System.Windows.FrameworkElement> oczekuje, że kontrolka obiektów, należy użyć <xref:System.Windows.TemplatePartAttribute>, który określa nazwę i typ oczekiwany elementów.  Aby określić możliwe stany kontrolkę, należy użyć <xref:System.Windows.TemplateVisualStateAttribute>, który określa nazwę stanu, które <xref:System.Windows.VisualStateGroup> należy ona do.  Umieść <xref:System.Windows.TemplatePartAttribute> i <xref:System.Windows.TemplateVisualStateAttribute> w definicji klasy kontrolki.  
  
 Właściwość publiczna, która wpływa na wygląd kontrolki jest również częścią kontrakt formantu.  
  
 W poniższym przykładzie określono <xref:System.Windows.FrameworkElement> obiektu i Stany `NumericUpDown` kontroli.  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy przykład dotyczy całego <xref:System.Windows.Controls.ControlTemplate> dla `NumericUpDown` kontroli.  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 W poniższym przykładzie pokazano logikę `NumericUpDown`.  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>Zobacz także
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
