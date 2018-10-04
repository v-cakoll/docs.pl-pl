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
ms.openlocfilehash: 435789e0d1bc601a9eb51488254407fefd334e05
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778052"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate
<a name="introduction"></a> A <xref:System.Windows.Controls.ControlTemplate> określa struktury wizualnej i zachowanie visual kontrolki. Można dostosować wygląd kontrolki, zapewniając it nowej <xref:System.Windows.Controls.ControlTemplate>. Po utworzeniu <xref:System.Windows.Controls.ControlTemplate>, Zastąp wyglądu istniejącej kontrolki bez zmiany jego działanie. Na przykład, można zwiększyć przycisków w aplikacji round zamiast domyślnego prostokątnego kształtu, ale nadal zgłosi przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 W tym temacie opisano różne części <xref:System.Windows.Controls.ControlTemplate>, przedstawia tworzenie prostej <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>i wyjaśnia, jak zrozumieć kontrakt formantu kontrolki tak, aby dostosować jego wygląd. Ponieważ tworzysz <xref:System.Windows.Controls.ControlTemplate> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz zmienić wygląd formantu bez pisania kodu. Projektanta, takich jak Microsoft Expression Blend, umożliwia również tworzenie szablonów kontrolek niestandardowych. W tym temacie przedstawiono przykłady w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , aby dostosować wygląd <xref:System.Windows.Controls.Button> i wyświetla pełny przykład na końcu tego tematu. Aby uzyskać więcej informacji o używaniu Expression Blend, zobacz [tworzenie stylów dla formantu obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Pokazują następujące ilustracje <xref:System.Windows.Controls.Button> , który używa <xref:System.Windows.Controls.ControlTemplate> utworzonego w tym temacie.  
  
 ![Przycisk za pomocą szablonu kontrolki niestandardowej. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Przycisk, który używa szablonu kontrolki niestandardowej  
  
 ![Przycisk z ciemnoczerwonym obramowaniem. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Przycisk, który używa szablonu kontrolki niestandardowej, a ma wskaźnik myszy nad nią  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz, jak utworzyć i korzystać z formantów i stylów, zgodnie z opisem w [formantów](../../../../docs/framework/wpf/controls/index.md). Kwestie omówione w tym temacie dotyczą elementów, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, z wyjątkiem <xref:System.Windows.Controls.UserControl>. Nie można zastosować <xref:System.Windows.Controls.ControlTemplate> do <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Kiedy należy utworzyć ControlTemplate  
 Formanty mają wiele właściwości, takie jak <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, i <xref:System.Windows.Controls.Control.FontFamily%2A>, które można ustawić, aby określić różne aspekty wyglądu kontrolki, ale zmiany wprowadzone przez ustawienie tych właściwości są ograniczone. Na przykład można ustawić <xref:System.Windows.Controls.Control.Foreground%2A> właściwości na niebieski i <xref:System.Windows.Controls.Control.FontStyle%2A> do italic na <xref:System.Windows.Controls.CheckBox>.  
  
 Bez możliwości, aby utworzyć nowy <xref:System.Windows.Controls.ControlTemplate> dla formantów, wszystkie kontrolki w każdym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— musi tego samego wygląd ogólny może ograniczyć możliwość tworzenia aplikacji za pomocą niestandardowy wygląd i działanie aplikacji opartej na. Domyślnie każdy <xref:System.Windows.Controls.CheckBox> ma podobnej charakterystyce. Na przykład zawartość <xref:System.Windows.Controls.CheckBox> jest zawsze po prawej stronie Wskaźnik zaznaczenia i zaznaczenie jest zawsze używana w celu wskazania, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone.  
  
 Możesz utworzyć <xref:System.Windows.Controls.ControlTemplate> gdy zachodzi potrzeba dostosowania wyglądu formantu poza wykona jakie Ustawianie innych właściwości w formancie. W przykładzie <xref:System.Windows.Controls.CheckBox>, załóżmy, zawartość pole wyboru, aby być powyżej Wskaźnik zaznaczenia i chcesz, aby znak X, aby wskazać, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone. Należy określić te zmiany w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.CheckBox>.  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.CheckBox> używającej domyślny <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Pole wyboru przy użyciu domyślnego szablonu kontrolki. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Zaznacz pole wyboru, która korzysta z domyślnego szablonu kontrolki  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.CheckBox> , który używa niestandardowego <xref:System.Windows.Controls.ControlTemplate> umieścić zawartość <xref:System.Windows.Controls.CheckBox> powyżej Wskaźnik zaznaczenia i wyświetla X po <xref:System.Windows.Controls.CheckBox> jest zaznaczone.  
  
 ![Pole wyboru przy użyciu szablonu kontrolki niestandardowej. ](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Zaznacz pole wyboru, który używa szablonu kontrolki niestandardowej  
  
 <xref:System.Windows.Controls.ControlTemplate> Dla <xref:System.Windows.Controls.CheckBox> w tym przykładzie jest dość złożone, więc w tym temacie używany prostsze przykładem tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Zmiana Visual struktura kontrolki  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], formant jest często złożonego <xref:System.Windows.FrameworkElement> obiektów. Po utworzeniu <xref:System.Windows.Controls.ControlTemplate>, możesz połączyć <xref:System.Windows.FrameworkElement> obiekty do kompilacji jednego formantu. A <xref:System.Windows.Controls.ControlTemplate> musi mieć tylko jedną <xref:System.Windows.FrameworkElement> jako element główny. Element główny zwykle zawiera inne <xref:System.Windows.FrameworkElement> obiektów. Kombinacja obiekty tworzą struktury wizualnej formantu.  
  
 Poniższy przykład tworzy niestandardowy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Tworzy strukturę visual <xref:System.Windows.Controls.Button>. W tym przykładzie nie zmienia wyglądu przycisku po umieszczeniu wskaźnika myszy lub kliknij ją. Zmiana wyglądu przycisku, gdy jest on w innym stanie została omówiona w dalszej części tego tematu.  
  
 W tym przykładzie struktury efektów wizualnych składa się z następujących elementów:  
  
-   A <xref:System.Windows.Controls.Border> o nazwie `RootElement` służy jako szablon głównego <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> czyli element podrzędny `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> wyświetlającą zawartości przycisku. <xref:System.Windows.Controls.ContentPresenter> Umożliwia dowolnego typu obiektu, który ma być wyświetlane.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachowanie funkcji właściwości kontrolki za pomocą TemplateBinding  
 Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>, nadal można użyć właściwości publiczne, aby zmienić wygląd formantu. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników powiązania właściwości elementu, który znajduje się w <xref:System.Windows.Controls.ControlTemplate> na właściwość publiczną, która jest zdefiniowana przez kontrolkę. Kiedy używasz [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), włączyć we właściwościach formantu jako parametry szablonu. Oznacza to, gdy właściwość kontrolki jest ustawiona, ta wartość jest przekazywane do elementu, który ma [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) na nim.  
  
 Poniższy przykład jest powtarzany część poprzedni przykład, który używa [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników można powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publiczne, które są zdefiniowane przez przycisk.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 W tym przykładzie <xref:System.Windows.Controls.Grid> ma jego <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> powiązane właściwości szablonu <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Ponieważ <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> jest szablonu powiązane, możesz utworzyć wiele przycisków, które używały tych samych <xref:System.Windows.Controls.ControlTemplate> i ustaw <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> różne wartości na przycisku. Jeśli <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> została szablonu nie jest powiązana z właściwością elementu w <xref:System.Windows.Controls.ControlTemplate>, ustawiając <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> przycisku, czy nie mają wpływu na wygląd.  
  
 Należy pamiętać, nazwy dwóch właściwości nie muszą być identyczne. W powyższym przykładzie <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Controls.Button> szablonu jest powiązany z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Controls.ContentPresenter>. Dzięki temu zawartości przycisku, który został umieszczony w poziomie. <xref:System.Windows.Controls.ContentPresenter> nie ma właściwości o nazwie `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> może być powiązana z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Podczas szablonu można powiązać właściwości, należy pamiętać, że właściwości źródłowe i docelowe są tego samego typu.  
  
 <xref:System.Windows.Controls.Control> Klasa definiuje kilka właściwości, które mogą być używane przez szablonu kontrolki, aby mieć wpływ na kontrolki, gdy są ustawione. Sposób, w jaki <xref:System.Windows.Controls.ControlTemplate> używa właściwości zależy od właściwości. <xref:System.Windows.Controls.ControlTemplate> Należy użyć właściwości w jednej z następujących sposobów:  
  
-   Element <xref:System.Windows.Controls.ControlTemplate> szablon wiąże się do właściwości.  
  
-   Element <xref:System.Windows.Controls.ControlTemplate> dziedziczy właściwości z elementem nadrzędnym <xref:System.Windows.FrameworkElement>.  
  
 Poniższa tabela zawiera listę właściwości wizualnego dziedziczone przez kontrolki z poziomu <xref:System.Windows.Controls.Control> klasy. Wskazuje także czy domyślny szablon kontrolki kontrolki używa wartości właściwość dziedziczona, lub jeśli musi być szablonu powiązane.  
  
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
  
 W tabeli wymieniono tylko właściwości wizualnego odziedziczone <xref:System.Windows.Controls.Control> klasy. Oprócz właściwości wymienione w tabeli, formant może również dziedziczyć <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, i <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> z elementu nadrzędnego w ramach właściwości.  
  
 Ponadto jeśli <xref:System.Windows.Controls.ContentPresenter> znajduje się w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> będzie automatycznie wiązany <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości. Podobnie <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ItemsControl> będzie automatycznie wiązany <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.ItemsPresenter> właściwości.  
  
 Poniższy przykład tworzy dwa przyciski, które używają <xref:System.Windows.Controls.ControlTemplate> zdefiniowane w poprzednim przykładzie. Przykład ustawia <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, i <xref:System.Windows.Controls.Control.FontSize%2A> właściwości dla każdego przycisku. Ustawienie <xref:System.Windows.Controls.Control.Background%2A> właściwość ma efektu, ponieważ jest on powiązany w szablonie <xref:System.Windows.Controls.ControlTemplate>. Mimo że <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.FontSize%2A> właściwości nie są częścią szablonu powiązane, ich ustawienie ma wpływ, ponieważ ich wartości są dziedziczone.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Poprzedni przykład generuje dane wyjściowe, która jest podobna do poniższej ilustracji.  
  
 ![Dwa przyciski, niebieski jednego i jeden purpurowy. ](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dwa przyciski, za pomocą różnych kolorów tła  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Zmienianie wyglądu formantu w zależności od jego stanu  
 Różnica między przycisku z jej domyślny wygląd i przycisku w poprzednim przykładzie polega na tym, że przycisk domyślny kliknięcia zmienia się po w różnych stanach. Na przykład przycisk domyślny wygląd zmienia się po naciśnięciu przycisku, lub gdy wskaźnik myszy znajduje się nad przyciskiem. Mimo że <xref:System.Windows.Controls.ControlTemplate> nie zmienia funkcjonalność formantu, zmienia zachowanie visual formantu. Zachowanie programu visual opisuje wygląd kontrolki, gdy jest on w pewnego stanu. Aby zrozumieć różnicę między funkcjonalności i wizualne zachowanie kontrolki, należy wziąć pod uwagę w przykładzie przycisku. Funkcje przycisku jest podniesienie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie po kliknięciu przycisku zachowanie visual jest jednak aby zmienić jego wygląd, gdy jest on wskazywał lub naciśnięciu.  
  
 Możesz użyć <xref:System.Windows.VisualState> obiektów, aby określić wygląd formantu, gdy jest on w pewnego stanu. A <xref:System.Windows.VisualState> zawiera <xref:System.Windows.Media.Animation.Storyboard> zmienia się wygląd elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate>. Nie masz do pisania jakiegokolwiek kodu, aby być fakt, że od logiki formantu zmieni stan za pomocą <xref:System.Windows.VisualStateManager>. Gdy formant przechodzi do stanu, który jest określony przez <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Media.Animation.Storyboard> rozpoczyna się. Gdy formant opuszcza stan <xref:System.Windows.Media.Animation.Storyboard> zatrzymuje.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.VisualState> zmienia się wygląd <xref:System.Windows.Controls.Button> gdy wskaźnik myszy znajduje się nad nią. <xref:System.Windows.Media.Animation.Storyboard> Zmienia kolor obramowania przycisku, zmieniając kolor `BorderBrush`. Jeśli odwołujesz się do <xref:System.Windows.Controls.ControlTemplate> przykład na początku tego tematu, będzie przypominać, który `BorderBrush` nazywa się <xref:System.Windows.Media.SolidColorBrush> przypisany do <xref:System.Windows.Controls.Border.Background%2A> z <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Kontrolka jest odpowiedzialny za Definiowanie stanów jako część jej kontrakt formantu, która została omówiona szczegółowo w temacie [Dostosowywanie inne formanty, rozumiejąc kontrakt formantu](#customizing_other_controls_by_understanding_the_control_contract) w dalszej części tego tematu. Poniższa tabela zawiera listę stanów, które są określone dla <xref:System.Windows.Controls.Button>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalny|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|  
|Naciśnięto|CommonStates|Użytkownik naciśnie kontrolkę.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Kontrolka nie ma fokusu.|  
  
 <xref:System.Windows.Controls.Button> Definiuje dwie grupy stanów: `CommonStates` grupa zawiera `Normal`, `MouseOver`, `Pressed`, i `Disabled` stanów. `FocusStates` Grupa zawiera `Focused` i `Unfocused` stanów. Stanów w tej samej grupie stanów wzajemnie się wykluczają. Kontrolka jest zawsze dokładnie jeden stan dla każdej grupy. Na przykład <xref:System.Windows.Controls.Button> może używać fokusu, nawet wtedy, gdy wskaźnik myszy nie jest nad nim, dlatego <xref:System.Windows.Controls.Button> w `Focused` może być w stanie w `MouseOver`, `Pressed`, lub `Normal` stanu.  
  
 Możesz dodać <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.VisualStateGroup> obiektów. Możesz dodać <xref:System.Windows.VisualStateGroup> obiekty do <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość. W poniższym przykładzie zdefiniowano <xref:System.Windows.VisualState> obiektów dla `Normal`, `MouseOver`, i `Pressed` stany, które są w `CommonStates` grupy. <xref:System.Windows.VisualState.Name%2A> Każdego <xref:System.Windows.VisualState> jest zgodna z nazwą w powyższej tabeli. `Disabled` Stanu i Stany w `FocusStates` grupy zostaną pominięte, aby zachować krótki przykład, ale są one uwzględnione w całej przykładzie na końcu tego tematu.  
  
> [!NOTE]
>  Pamiętaj ustawić <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość w katalogu głównym <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Poprzedni przykład generuje dane wyjściowe podobne do poniższych ilustracjach.  
  
 ![Przycisk za pomocą szablonu kontrolki niestandardowej. ](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Przycisk, który używa szablonu kontrolki niestandardowej w normalnym stanie.  
  
 ![Przycisk z ciemnoczerwonym obramowaniem. ](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Przycisk, który używa szablonu kontrolki niestandardowej w myszy nad stanu  
  
 ![Obramowanie jest niewidoczne po naciśnięciu przycisku. ](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Przycisk, który używa szablonu kontrolki niestandardowej w stanie po naciśnięciu  
  
 Aby znaleźć stanów wizualnych dla kontrolki, które są dołączone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Podczas przechodzenia między stanami, określając zachowanie kontrolki  
 W powyższym przykładzie wyglądu przycisku także ulega zmianie po użytkownik go kliknie, ale jeśli przycisk jest wciśnięty, aby uzyskać pełną sekundę, użytkownik nie widzi efekt. Domyślnie Animacja przyjmuje jedną sekundę nastąpi. Ponieważ użytkownicy mogą kliknąć i zwolnieniu przycisku w znacznie krótszym czasie, wizualną opinię nie będzie skuteczna, jeśli pozostawisz <xref:System.Windows.Controls.ControlTemplate> w stanie domyślnym.  
  
 Możesz określić ilość czasu potrzebnego animacji do bezproblemowego przejścia formantu z jednego stanu do innego, dodając <xref:System.Windows.VisualTransition> obiekty do <xref:System.Windows.Controls.ControlTemplate>. Po utworzeniu <xref:System.Windows.VisualTransition>, należy określić co najmniej jeden z następujących czynności:  
  
-   Czas przejścia między Stanami wystąpić.  
  
-   Dodatkowe zmiany wyglądu kontrolki, które występują w momencie przejścia.  
  
-   Które stany <xref:System.Windows.VisualTransition> jest stosowany do.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Określanie czasu trwania przejścia  
 Można określić, jak długo trwa przejście przez ustawienie <xref:System.Windows.VisualTransition.GeneratedDuration%2A> właściwości. W poprzednim przykładzie przedstawiono <xref:System.Windows.VisualState> określająca, czy obramowanie przycisku staje się przezroczyste, po kliknięciu przycisku, ale animacji trwa zbyt długo, można zaobserwować, jeśli przycisk jest szybkie naciśnięcia, a. Możesz użyć <xref:System.Windows.VisualTransition> można określić ilość czasu zajmuje kontrolki, do którego nastąpi przejście do stanu po naciśnięciu. W poniższym przykładzie określono, że kontrolka ma jednej setnej części sekundy, aby przejść do stanu po naciśnięciu.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Określanie zmian wyglądu formantu podczas przejścia  
 <xref:System.Windows.VisualTransition> Zawiera <xref:System.Windows.Media.Animation.Storyboard> , która rozpoczyna się kontrolka przejścia między stanami. Na przykład można określić, że niektórych animacji występuje, gdy kontrolka przechodzi z `MouseOver` do stanu `Normal` stanu. Poniższy przykład tworzy <xref:System.Windows.VisualTransition> określający, że gdy użytkownik przesuwa wskaźnik myszy poza przycisk, obramowanie przycisku zmienia się na niebieski, a następnie na żółty, a następnie na czarny w wersji 1.5 w ciągu kilku sekund.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Określanie, gdy jest stosowany obiekt VisualTransition  
 Element <xref:System.Windows.VisualTransition> można ograniczyć do dotyczą tylko w określonych stanach lub mogą być stosowane dowolny czas przejścia sterowania między stanami. W powyższym przykładzie <xref:System.Windows.VisualTransition> jest stosowana, gdy kontrolka przechodzi z `MouseOver` do stanu `Normal` stanu; w przykładzie wcześniej <xref:System.Windows.VisualTransition> jest stosowana, gdy kontrolka przechodzi w stan `Pressed` stanu. Gdy ograniczanie <xref:System.Windows.VisualTransition> jest stosowany przez ustawienie <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A> właściwości. W poniższej tabeli opisano poziomy ograniczenie najbardziej restrykcyjne do najmniej restrykcyjna.  
  
|Typ ograniczenia|Wartość atrybutu z|Wartość atrybutu do|  
|-------------------------|-------------------|-----------------|  
|Z określonego stanu do innego określonego stanu|Nazwa <xref:System.Windows.VisualState>|Nazwa <xref:System.Windows.VisualState>|  
|Z dowolny stan do określonego stanu|Nie ustawiono|Nazwa <xref:System.Windows.VisualState>|  
|Z określonego stanu na dowolny stan|Nazwa <xref:System.Windows.VisualState>|Nie ustawiono|  
|Z dowolny stan do dowolnego innego stanu|Nie ustawiono|Nie ustawiono|  
  
 Masz wiele <xref:System.Windows.VisualTransition> obiekty w <xref:System.Windows.VisualStateGroup> odwołujące się do takiego samego stanu, ale będą używane w kolejności, który określa poprzedniej tabeli. W poniższym przykładzie występują dwa <xref:System.Windows.VisualTransition> obiektów. Gdy kontrolka przechodzi z `Pressed` do stanu `MouseOver` stanu, <xref:System.Windows.VisualTransition> ma obydwa <xref:System.Windows.VisualTransition.From%2A> i <xref:System.Windows.VisualTransition.To%2A> zestaw jest używany. Gdy kontrolka przechodzi ze stanu, który nie jest `Pressed` do `MouseOver` stanu jest używany inny stan.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Ma <xref:System.Windows.VisualStateGroup.Transitions%2A> właściwość, która zawiera <xref:System.Windows.VisualTransition> obiekty, które są stosowane do <xref:System.Windows.VisualState> obiekty w <xref:System.Windows.VisualStateGroup>. Jako <xref:System.Windows.Controls.ControlTemplate> Autor, możesz mogą zawierać dowolne <xref:System.Windows.VisualTransition> ma. Jednak jeśli <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A> właściwości są ustawione na nazwy stanu, które nie znajdują się w <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> jest ignorowana.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.VisualStateGroup> dla `CommonStates`. W przykładzie zdefiniowano <xref:System.Windows.VisualTransition> dla każdego z następujących przycisku przejścia.  
  
-   Aby `Pressed` stanu.  
  
-   Aby `MouseOver` stanu.  
  
-   Z `Pressed` do stanu `MouseOver` stanu.  
  
-   Z `MouseOver` do stanu `Normal` stanu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Dostosowywanie innych formantów dzięki zrozumieniu kontrakt formantu  
 Formant, który używa <xref:System.Windows.Controls.ControlTemplate> do określenia jego struktury efektów wizualnych (przy użyciu <xref:System.Windows.FrameworkElement> obiektów) i zachowanie visual (przy użyciu <xref:System.Windows.VisualState> obiektów) korzysta z modelu kontroli części. Wiele elementów sterujących, które są dołączone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 użyć tego modelu. Części, <xref:System.Windows.Controls.ControlTemplate> autor musi być znane są przekazywane za pośrednictwem kontrakt formantu. Gdy już poznasz części kontrakt formantu, można dostosować wygląd żadnego formantu, który korzysta z modelu kontroli części.  
  
 Kontrakt formantu ma trzy elementy:  
  
-   Elementy wizualne, których używa logiki formantu.  
  
-   Stany i grupy, której każdy stan kontrolki.  
  
-   Właściwości publiczne, które wizualnie wpływają na formant.  
  
### <a name="visual-elements-in-the-control-contract"></a>Elementy wizualne w kontrakcie kontroli  
 Czasami od logiki formantu wchodzi w interakcję z <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate>. Na przykład formant może obsługiwać zdarzenia z jednego z jego elementów. Gdy formant spodziewa się znaleźć określonego <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate>, go, musi przekazać te informacje do <xref:System.Windows.Controls.ControlTemplate> autora. Kontrolka używa <xref:System.Windows.TemplatePartAttribute> do ich typ elementu, który jest oczekiwany, a co powinno być nazwa elementu. <xref:System.Windows.Controls.Button> Nie ma <xref:System.Windows.FrameworkElement> części w jej kontrakt formantu, ale inne formanty, takie jak <xref:System.Windows.Controls.ComboBox>, czy.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.TemplatePartAttribute> obiekty, które są określone na <xref:System.Windows.Controls.ComboBox> klasy. Logika <xref:System.Windows.Controls.ComboBox> spodziewa się znaleźć <xref:System.Windows.Controls.TextBox> o nazwie `PART_EditableTextBox` i <xref:System.Windows.Controls.Primitives.Popup> o nazwie `PART_Popup` w jego <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 W poniższym przykładzie pokazano uproszczony <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ComboBox> zawierającej elementy, które są określone przez <xref:System.Windows.TemplatePartAttribute> obiektów na <xref:System.Windows.Controls.ComboBox> klasy.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stany w kontrakcie kontroli  
 Stany kontrolki są również częścią kontrakt formantu. Przykład tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> pokazuje, jak określić sposób wyświetlania <xref:System.Windows.Controls.Button> w zależności od jego stany. Możesz utworzyć <xref:System.Windows.VisualState> dla każdego określony stan i umieścić wszystkie <xref:System.Windows.VisualState> obiekty udziału <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> w <xref:System.Windows.VisualStateGroup>, zgodnie z opisem w [Zmienianie wyglądu formantu w zależności od jego stanu](#changing_the_appearance_of_a_control_depending_on_its_state) wcześniej w tym temat. Formanty innych firm, należy określić stanów przy użyciu <xref:System.Windows.TemplateVisualStateAttribute>, co pozwala projektanta narzędzi, takich jak Expression Blend, aby uwidocznić stanami formantu do tworzenia szablonów kontrolek.  
  
 Aby znaleźć kontrakt formantu dla formantów, które są dołączone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Właściwości w kontrakt formantu  
 Właściwości publiczne, które wizualnie wpływają na formant znajdują się również w kontrakcie kontroli. Można ustawić te właściwości, aby zmienić wygląd formantu bez tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>. Można również użyć [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników można powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publiczne, które są definiowane przez <xref:System.Windows.Controls.Button>.  
  
 Poniższy przykład zawiera kontrakt formantu przycisku.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>, często najłatwiej zaczynają się od istniejącej <xref:System.Windows.Controls.ControlTemplate> i wprowadzać zmiany. Możesz wykonać jedną z następujących czynności, aby zmienić istniejącego <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Za pomocą projektanta, takich jak Expression Blend, która zapewnia graficzny interfejs użytkownika do tworzenia szablonów kontrolek. Aby uzyskać więcej informacji, zobacz [tworzenie stylów dla formantu obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Pobierz domyślny <xref:System.Windows.Controls.ControlTemplate> i go edytować. Aby znaleźć domyślne szablony kontrolek, które są dołączone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [motywy WPF domyślne](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletny przykład  
 W poniższym przykładzie pokazano pełne <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> , opisanej w tym temacie.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
