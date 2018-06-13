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
ms.openlocfilehash: bbdc79fabf8dbe344baae66d718d79ac6375db7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558060"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate
<a name="introduction"></a> A <xref:System.Windows.Controls.ControlTemplate> określa visual strukturę i zachowanie visual formantu. Można dostosować wygląd formantu, zapewniając it nowy <xref:System.Windows.Controls.ControlTemplate>. Po utworzeniu <xref:System.Windows.Controls.ControlTemplate>, Zastąp wygląd formant bez zmieniania jego funkcjonalność. Na przykład możesz wprowadzić przycisków w aplikacji round zamiast domyślnego kwadratu, ale nadal zgłosi przycisku <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  
  
 W tym temacie opisano różne części <xref:System.Windows.Controls.ControlTemplate>, pokazano tworzenie prostego <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>oraz objaśniono sposób zrozumieć kontraktu kontroli formantu, aby dostosować wygląd. Ponieważ tworzenia <xref:System.Windows.Controls.ControlTemplate> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można zmienić wygląd formantu, bez pisania żadnego kodu. Tworzenie szablonów niestandardowych kontroli umożliwia także projektanta, takich jak Microsoft Expression Blend. W tym temacie przedstawiono przykłady w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który dostosowanie wyglądu <xref:System.Windows.Controls.Button> oraz przedstawia pełny przykład na końcu tego tematu. Aby uzyskać więcej informacji o używaniu Expression Blend, zobacz [stylów formantu, który obsługuje szablony](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Pokaż następujące ilustracje <xref:System.Windows.Controls.Button> używającą <xref:System.Windows.Controls.ControlTemplate> utworzonego w tym temacie.  
  
 ![Przycisk za pomocą szablonu kontrolki niestandardowej. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Przycisk, który używa szablonu formantu niestandardowego  
  
 ![Przycisk czerwonym obramowaniem. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Przycisk, który używa szablonu kontrolki niestandardowej, a ma nad nim wskaźnik myszy  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz, jak tworzenie i używanie formantów i style, zgodnie z opisem w [formanty](../../../../docs/framework/wpf/controls/index.md). Kwestie omówione w tym temacie dotyczą elementów, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, z wyjątkiem <xref:System.Windows.Controls.UserControl>. Nie można zastosować <xref:System.Windows.Controls.ControlTemplate> do <xref:System.Windows.Controls.UserControl>.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Kiedy należy utworzyć ControlTemplate  
 Formanty mają wiele właściwości, takie jak <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, i <xref:System.Windows.Controls.Control.FontFamily%2A>, które można ustawić, aby określić różne aspekty wygląd formantu, ale zmiany wprowadzone przez ustawienie tych właściwości są ograniczone. Na przykład można ustawić <xref:System.Windows.Controls.Control.Foreground%2A> właściwości na niebieski i <xref:System.Windows.Controls.Control.FontStyle%2A> do kursywą na <xref:System.Windows.Controls.CheckBox>.  
  
 Bez możliwości tworzenia nowego <xref:System.Windows.Controls.ControlTemplate> dla formantów, wszystkie formanty w każdej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— musi sam wygląd ogólne może ograniczyć możliwość tworzenia aplikacji z niestandardowego wygląd i działanie aplikacji. Domyślnie każdy <xref:System.Windows.Controls.CheckBox> podobnych cechach. Na przykład zawartość <xref:System.Windows.Controls.CheckBox> jest zawsze po prawej stronie wskaźnika wyboru, a znacznik wyboru jest zawsze używana w celu wskazania, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone.  
  
 Możesz utworzyć <xref:System.Windows.Controls.ControlTemplate> umożliwia dostosowanie wyglądu formantu poza jakiego ustawienie innych właściwości w formancie będzie wykonywać. W przykładzie <xref:System.Windows.Controls.CheckBox>, załóżmy, że chcesz zawartość znajdować się nad wskaźnika zaznaczenia pola wyboru, a znak X, aby wskazać, że <xref:System.Windows.Controls.CheckBox> jest zaznaczone. Określ te zmiany w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.CheckBox>.  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Controls.CheckBox> używające domyślnego <xref:System.Windows.Controls.ControlTemplate>.  
  
 ![Pole wyboru przy użyciu domyślnego szablonu kontroli. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Pole wyboru, które korzysta z domyślnego szablonu formantu  
  
 Na poniższej ilustracji pokazano <xref:System.Windows.Controls.CheckBox> używającej niestandardowego <xref:System.Windows.Controls.ControlTemplate> umieścić zawartość <xref:System.Windows.Controls.CheckBox> powyżej wskaźnik selekcji i wyświetla symbol X po <xref:System.Windows.Controls.CheckBox> jest zaznaczone.  
  
 ![Pole wyboru przy użyciu szablonu niestandardowego formantu. ] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Pole wyboru, które używa szablonu formantu niestandardowego  
  
 <xref:System.Windows.Controls.ControlTemplate> Dla <xref:System.Windows.Controls.CheckBox> w tym przykładzie jest dość złożone, dlatego w tym temacie używa prostsze przykładem tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>.  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Zmiana struktury Visual formantu  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], formantu jest często złożonym <xref:System.Windows.FrameworkElement> obiektów. Po utworzeniu <xref:System.Windows.Controls.ControlTemplate>, możesz łączyć <xref:System.Windows.FrameworkElement> obiektów, aby utworzyć jeden formant. A <xref:System.Windows.Controls.ControlTemplate> musi mieć tylko jeden <xref:System.Windows.FrameworkElement> jako jego elementu głównego. Element główny zwykle zawierają inne <xref:System.Windows.FrameworkElement> obiektów. Struktury visual formantu stanowi kombinację obiektów.  
  
 Poniższy przykład tworzy niestandardowy <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button>. <xref:System.Windows.Controls.ControlTemplate> Tworzy struktury visual <xref:System.Windows.Controls.Button>. W tym przykładzie nie zmienia wygląd przycisku, przenieś wskaźnik myszy nad nim lub kliknij ją. Zmiana wyglądu przycisku, gdy jest on w innym stanie omówione w dalszej części tego tematu.  
  
 W tym przykładzie struktury visual składa się z następujących elementów:  
  
-   A <xref:System.Windows.Controls.Border> o nazwie `RootElement` służy jako główny szablonu <xref:System.Windows.FrameworkElement>.  
  
-   A <xref:System.Windows.Controls.Grid> będący elementem podrzędnym `RootElement`.  
  
-   A <xref:System.Windows.Controls.ContentPresenter> wyświetlający zawartości przycisku. <xref:System.Windows.Controls.ContentPresenter> Umożliwia dowolnego typu obiektu, który będzie wyświetlany.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachowanie funkcji właściwości formantu za pomocą TemplateBinding  
 Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>, nadal można użyć właściwości publiczne, aby zmienić wygląd formantu. [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników wiąże właściwość elementu, który znajduje się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publicznej, która jest zdefiniowana przez formant. Jeśli używasz [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), włącz właściwości formantu do działania jako parametry szablonu. Oznacza to, gdy właściwość w formancie jest ustawiona, tej wartości są przekazywane do elementu, który ma [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) na nim.  
  
 Poniższy przykład powtarza część w poprzednim przykładzie, który używa [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników można powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publiczne, które są zdefiniowane za pomocą przycisku.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 W tym przykładzie <xref:System.Windows.Controls.Grid> ma jego <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> powiązane właściwości szablonu <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>. Ponieważ <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> jest szablonu powiązane, możesz utworzyć wiele przycisków używać tego samego <xref:System.Windows.Controls.ControlTemplate> i ustaw <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> różne wartości na każdym przycisku. Jeśli <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> została szablonu nie jest powiązana z właściwością elementu w <xref:System.Windows.Controls.ControlTemplate>, ustawienie <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> przycisku spowoduje nie mają wpływu na wygląd przycisku.  
  
 Należy pamiętać, że nazwy tych dwóch właściwości muszą być identyczne. W powyższym przykładzie <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Controls.Button> szablonu jest powiązany z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Controls.ContentPresenter>. Dzięki temu zawartości przycisku się znajdować w poziomie. <xref:System.Windows.Controls.ContentPresenter> nie ma właściwości o nazwie `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> może być powiązana z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Gdy szablon można powiązać właściwości, należy się upewnić, że właściwości źródłowa i docelowa są tego samego typu.  
  
 <xref:System.Windows.Controls.Control> Klasa definiuje kilka właściwości, które mogą być używane przez szablon formantu mają wpływ na kontrolce po ich ustawieniu. Jak <xref:System.Windows.Controls.ControlTemplate> używa właściwości zależy od właściwości. <xref:System.Windows.Controls.ControlTemplate> Należy użyć właściwości w jednym z następujących sposobów:  
  
-   Element <xref:System.Windows.Controls.ControlTemplate> szablonu jest powiązany z właściwością.  
  
-   Element <xref:System.Windows.Controls.ControlTemplate> dziedziczy właściwości elementu nadrzędnego <xref:System.Windows.FrameworkElement>.  
  
 W poniższej tabeli wymieniono właściwości wizualnego dziedziczone przez kontrolkę z <xref:System.Windows.Controls.Control> klasy. Wskazuje ona także, czy domyślny szablon formantu formantu używa wartości właściwości dziedziczone lub jeśli musi być powiązany szablonu.  
  
|Właściwość|Użycie — metoda|  
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
  
 W tabeli wymieniono tylko visual właściwości odziedziczone z <xref:System.Windows.Controls.Control> klasy. Oprócz właściwości wymienione w tabeli, może również dziedziczą formantu <xref:System.Windows.FrameworkElement.DataContext%2A>, <xref:System.Windows.FrameworkElement.Language%2A>, i <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> właściwości z elementu nadrzędnego framework.  
  
 Ponadto jeśli <xref:System.Windows.Controls.ContentPresenter> w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> będzie automatycznie wiązane z <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> i <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości. Podobnie <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ControlTemplate> z <xref:System.Windows.Controls.ItemsControl> będzie automatycznie wiązane z <xref:System.Windows.Controls.ItemsControl.Items%2A> i <xref:System.Windows.Controls.ItemsPresenter> właściwości.  
  
 Poniższy przykład tworzy dwa przyciski, które używają <xref:System.Windows.Controls.ControlTemplate> zdefiniowane w poprzednim przykładzie. Ustawia przykład <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, i <xref:System.Windows.Controls.Control.FontSize%2A> właściwości na każdym przycisku. Ustawienie <xref:System.Windows.Controls.Control.Background%2A> właściwość ma efektu, ponieważ jest powiązana w szablonie <xref:System.Windows.Controls.ControlTemplate>. Mimo że <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.Control.FontSize%2A> właściwości nie są częścią szablonu powiązane, ich ustawienie ma wpływ, ponieważ ich wartości są dziedziczone.  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Powyższy przykład generuje dane wyjściowe, która jest podobna do poniższej ilustracji.  
  
 ![Dwóch przycisków, niebieski jednego i jeden purpurowy. ] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dwóch przycisków z różnych kolorów tła  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Zmienianie wyglądu formantu w zależności od stanu  
 Różnica między przycisk z jego domyślny wygląd i przycisk w poprzednim przykładzie jest, że przycisk domyślny pisowni zostanie zmieniona, gdy znajduje się w innych stanów. Przycisk domyślny wygląd zmienia się na przykład po naciśnięciu przycisku lub w przypadku, gdy wskaźnik myszy znajduje się nad przyciskiem. Mimo że <xref:System.Windows.Controls.ControlTemplate> nie zmienia funkcje kontroli, zmienić zachowanie visual formantu. Zachowanie visual opisuje wygląd formantu, gdy jest on w stanie niektórych. Aby zrozumieć różnicę między funkcje i zachowanie visual formantu, należy wziąć pod uwagę w przykładzie przycisku. Funkcja przycisku jest podnieść <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie po kliknięciu przycisku zachowanie visual jest jednak zmienić jego wygląd jest wskazywana lub naciśnięciu.  
  
 Możesz użyć <xref:System.Windows.VisualState> obiektów, aby określić wygląd formantu, gdy jest on w stanie niektórych. A <xref:System.Windows.VisualState> zawiera <xref:System.Windows.Media.Animation.Storyboard> zmienia się wygląd elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate>. Nie masz do pisania kodu, aby ustawić to wynikać z formantu logiki zmieni stan za pomocą <xref:System.Windows.VisualStateManager>. Gdy formant przechodzi do stanu, określonej przez <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Media.Animation.Storyboard> rozpoczyna się. Gdy formant kończy stanu, <xref:System.Windows.Media.Animation.Storyboard> zatrzymuje.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.VisualState> który zmienia wygląd <xref:System.Windows.Controls.Button> gdy wskaźnik myszy znajduje się nad nim. <xref:System.Windows.Media.Animation.Storyboard> Zmienia kolor obramowania przycisku przez zmianę koloru `BorderBrush`. Jeśli można odwoływać się do <xref:System.Windows.Controls.ControlTemplate> przykład na początku tego tematu, będzie przypominać, który `BorderBrush` jest nazwą <xref:System.Windows.Media.SolidColorBrush> przypisany do <xref:System.Windows.Controls.Border.Background%2A> z <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Kontrolka jest odpowiedzialny za określenie stany jako część jej kontrakt kontrolki, która została omówiona szczegółowo w [Dostosowywanie inne formanty według Opis kontraktu kontroli](#customizing_other_controls_by_understanding_the_control_contract) dalszej części tego tematu. W poniższej tabeli wymieniono stanów, które są określone dla <xref:System.Windows.Controls.Button>.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad formantem.|  
|Naciśnięto|CommonStates|Formant zostanie naciśnięty.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Formant ma fokus.|  
|Bez fokusu|FocusStates|Formant nie ma fokusa.|  
  
 <xref:System.Windows.Controls.Button> Definiuje dwie grupy stanu: `CommonStates` grupa zawiera `Normal`, `MouseOver`, `Pressed`, i `Disabled` stanów. `FocusStates` Grupa zawiera `Focused` i `Unfocused` stanów. Stanów w tej samej grupie stanów wzajemnie się wykluczają. Formant jest zawsze dokładnie jeden stan dla każdej grupy. Na przykład <xref:System.Windows.Controls.Button> może używać fokusu, nawet wtedy, gdy wskaźnik myszy nie jest nad nim, więc <xref:System.Windows.Controls.Button> w `Focused` może być w stanie w `MouseOver`, `Pressed`, lub `Normal` stanu.  
  
 Możesz dodać <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.VisualStateGroup> obiektów. Możesz dodać <xref:System.Windows.VisualStateGroup> obiekty do <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość. W poniższym przykładzie zdefiniowano <xref:System.Windows.VisualState> obiektów na `Normal`, `MouseOver`, i `Pressed` stany, które są w `CommonStates` grupy. <xref:System.Windows.VisualState.Name%2A> Każdego <xref:System.Windows.VisualState> jest zgodna z nazwą w powyższej tabeli. `Disabled` Stanu i stanów w `FocusStates` grupy zostaną pominięte, aby zachować krótki przykładzie, ale znajdują się w tym przykładzie całego na końcu tego tematu.  
  
> [!NOTE]
>  Należy ustawić <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> dołączona właściwość w katalogu głównym <xref:System.Windows.FrameworkElement> z <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 Powyższy przykład generuje dane wyjściowe podobne do poniższych ilustracjach.  
  
 ![Przycisk za pomocą szablonu kontrolki niestandardowej. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Przycisk, który używa szablonu kontrolki niestandardowej w normalnym stanie.  
  
 ![Przycisk czerwonym obramowaniem. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Przycisk, który używa szablonu kontrolki niestandardowej w wskaźnik myszy nad stanu  
  
 ![Obramowanie jest niewidoczny w naciśniętego przycisku. ] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
Używa szablonu kontrolki niestandardowej w stan naciśnięcia przycisku  
  
 Aby znaleźć stany wizualne dla formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [stylów formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>Określanie zachowania formantu po jego przejścia między Stanami  
 W powyższym przykładzie wygląd przycisku zmienia także po kliknięciu przez użytkownika, ale chyba, że przycisk jest naciśnięty pełną sekundę, użytkownik nie widzi efekt. Domyślnie Animacja przyjmuje jednej sekundzie występuje. Ponieważ użytkownicy są prawdopodobnie kliknij przycisk, a następnie zwolnij przycisk w znacznie krócej, wizualny nie zostaną zastosowane, jeśli pole pozostanie <xref:System.Windows.Controls.ControlTemplate> w stanie domyślnym.  
  
 Możesz określić ilość czasu trwania animacji do płynne przejście formantu z jednego stanu do innego, dodając <xref:System.Windows.VisualTransition> obiekty do <xref:System.Windows.Controls.ControlTemplate>. Po utworzeniu <xref:System.Windows.VisualTransition>, określ co najmniej jeden z następujących czynności:  
  
-   Czas trwania przejścia między Stanami występuje.  
  
-   Dodatkowe zmiany w wygląd formantu, które występują w momencie przejścia.  
  
-   Które stany <xref:System.Windows.VisualTransition> jest stosowany do.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Określanie czasu trwania przejścia  
 Można określić, jak długo trwa przejście przez ustawienie <xref:System.Windows.VisualTransition.GeneratedDuration%2A> właściwości. Powyższy przykład ma <xref:System.Windows.VisualState> Określa, czy obramowania przycisku staje się przezroczysty, gdy przycisk jest naciśnięty, ale animacji trwa zbyt długo, można zaobserwować, jeśli szybko naciśnięty oraz zwalniać przycisku. Można użyć <xref:System.Windows.VisualTransition> Aby określić czas potrzebny do przejścia w stan naciśnięcia formantu. Poniższy przykład określa, czy formant ma jednej setnej sekundy przejść w stan naciśnięcia.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Określanie zmian wygląd formantu podczas przejścia  
 <xref:System.Windows.VisualTransition> Zawiera <xref:System.Windows.Media.Animation.Storyboard> , która rozpoczyna się kontrolka przejścia między stanami. Na przykład określić, że niektórych animacji występuje, gdy formant przechodzi z `MouseOver` stan `Normal` stanu. Poniższy przykład tworzy <xref:System.Windows.VisualTransition> Określa, że gdy użytkownik przesuwa wskaźnik myszy przycisk, obramowanie przycisku zmienia się na niebieski, żółty, a następnie na kolor czarny w 1,5 s.  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Określanie, gdy jest stosowany obiekt VisualTransition  
 A <xref:System.Windows.VisualTransition> można ograniczyć do dotyczą tylko określone stany lub można je stosować wtedy kontroli przejścia między stanami. W powyższym przykładzie <xref:System.Windows.VisualTransition> jest stosowana, gdy formant przechodzi z `MouseOver` stan `Normal` stanu; w przykładzie wcześniej <xref:System.Windows.VisualTransition> jest stosowana, gdy formant przechodzi w stan `Pressed` stanu. Jeśli ograniczysz <xref:System.Windows.VisualTransition> jest stosowany przez ustawienie <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A> właściwości. W poniższej tabeli opisano poziomami ograniczeń z najbardziej restrykcyjne do najmniej restrykcyjna.  
  
|Typ ograniczenia|Wartość z|Wartość do|  
|-------------------------|-------------------|-----------------|  
|Z określonego stanu do innego określonego stanu|Nazwa <xref:System.Windows.VisualState>|Nazwa <xref:System.Windows.VisualState>|  
|Z dowolnego stanu do określonego stanu|Nie ustawiono|Nazwa <xref:System.Windows.VisualState>|  
|Z określonego stanu do dowolnego stanu|Nazwa <xref:System.Windows.VisualState>|Nie ustawiono|  
|Z dowolnego stanu do innego stanu|Nie ustawiono|Nie ustawiono|  
  
 Istnieje wiele <xref:System.Windows.VisualTransition> obiekty w <xref:System.Windows.VisualStateGroup> odwołujące się do tego samego stanu, ale będą stosowane w kolejności, który określa poprzedniej tabeli. W poniższym przykładzie występują dwa <xref:System.Windows.VisualTransition> obiektów. Gdy formant przechodzi z `Pressed` stan `MouseOver` stanu, <xref:System.Windows.VisualTransition> zawiera równocześnie <xref:System.Windows.VisualTransition.From%2A> i <xref:System.Windows.VisualTransition.To%2A> zestaw jest używany. Gdy kontrolka przejścia ze stanu, który nie jest `Pressed` do `MouseOver` stan, służy inny stan.  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> Ma <xref:System.Windows.VisualStateGroup.Transitions%2A> właściwość, która zawiera <xref:System.Windows.VisualTransition> obiektów, które dotyczą <xref:System.Windows.VisualState> obiekty w <xref:System.Windows.VisualStateGroup>. Jako <xref:System.Windows.Controls.ControlTemplate> autora, możesz mogą zawierać <xref:System.Windows.VisualTransition> ma. Jednak jeśli <xref:System.Windows.VisualTransition.To%2A> i <xref:System.Windows.VisualTransition.From%2A> właściwości są ustawione na nazwy stanu, które nie znajdują się w <xref:System.Windows.VisualStateGroup>, <xref:System.Windows.VisualTransition> jest ignorowana.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.VisualStateGroup> dla `CommonStates`. W przykładzie zdefiniowano <xref:System.Windows.VisualTransition> dla każdego z następujących przycisku przejścia.  
  
-   Aby `Pressed` stanu.  
  
-   Aby `MouseOver` stanu.  
  
-   Z `Pressed` stan `MouseOver` stanu.  
  
-   Z `MouseOver` stan `Normal` stanu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Dostosowywanie inne formanty zrozumienie kontraktu formantu  
 Formant, który używa <xref:System.Windows.Controls.ControlTemplate> do określenia jego struktury visual (przy użyciu <xref:System.Windows.FrameworkElement> obiekty) i zachowanie visual (przy użyciu <xref:System.Windows.VisualState> obiektów) wykorzystuje model kontroli części. Wiele formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 używać tego modelu. Części który <xref:System.Windows.Controls.ControlTemplate> autor musi być znane są przekazywane za pośrednictwem umowy formantu. Po zapoznaniu części kontraktu formantu można dostosować wygląd żadnego formantu, który korzysta z części kontroli modelu.  
  
 Kontrakt formantu ma trzy elementy:  
  
-   Elementy wizualne, które używa logiki formantu.  
  
-   Stany formantu i grupy, do której należy każdy stan.  
  
-   Właściwości publiczne, które wizualnie wpływają na formantu.  
  
### <a name="visual-elements-in-the-control-contract"></a>Elementy wizualne w kontrakcie formantu  
 Czasami logiki formantu współdziała z <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate>. Na przykład formant może obsłużyć zdarzenia jednego z jego elementów. Gdy oczekuje formantu można znaleźć określonego <xref:System.Windows.FrameworkElement> w <xref:System.Windows.Controls.ControlTemplate>, należy przekazać te informacje do <xref:System.Windows.Controls.ControlTemplate> autora. Używa kontrolki <xref:System.Windows.TemplatePartAttribute> do ich typ elementu, który jest oczekiwany, a co powinna być nazwa elementu. <xref:System.Windows.Controls.Button> Nie ma <xref:System.Windows.FrameworkElement> części w jej kontrakt sterowania, ale inne formanty, takie jak <xref:System.Windows.Controls.ComboBox>, czy.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.TemplatePartAttribute> obiektów, które są określone na <xref:System.Windows.Controls.ComboBox> klasy. Logika <xref:System.Windows.Controls.ComboBox> oczekuje można znaleźć <xref:System.Windows.Controls.TextBox> o nazwie `PART_EditableTextBox` i <xref:System.Windows.Controls.Primitives.Popup> o nazwie `PART_Popup` w jego <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 W poniższym przykładzie pokazano uproszczony <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ComboBox> zawierającej elementy, które są określone przez <xref:System.Windows.TemplatePartAttribute> obiektów na <xref:System.Windows.Controls.ComboBox> klasy.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stany w kontrakcie formantu  
 Stany formantu są również częścią kontraktu formantu. Przykład tworzenia <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> pokazano, jak określić wygląd <xref:System.Windows.Controls.Button> w zależności od jego stanów. Możesz utworzyć <xref:System.Windows.VisualState> dla każdego określony stan i umieszcza wszystkie <xref:System.Windows.VisualState> obiekty tego udziału <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> w <xref:System.Windows.VisualStateGroup>, zgodnie z opisem w [Zmienianie wyglądu formantu zależnie od jego stan](#changing_the_appearance_of_a_control_depending_on_its_state) wcześniej w tym temat. Formanty innych firm, należy określić stanów przy użyciu <xref:System.Windows.TemplateVisualStateAttribute>, co pozwala projektanta narzędzi, takich jak Expression Blend, do udostępnienia stanów formantu do tworzenia szablonów kontrolki.  
  
 Można znaleźć formantu kontraktu dla formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [stylów formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Właściwości w kontrakcie formantu  
 Właściwości publiczne, wizualnie wpływających na formancie znajdują się również w kontrakcie formantu. Można ustawić te właściwości, aby zmienić wygląd formantu bez tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>. Można również użyć [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) — rozszerzenie znaczników można powiązać właściwości elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> do właściwości publiczne, które są zdefiniowane przez <xref:System.Windows.Controls.Button>.  
  
 W poniższym przykładzie przedstawiono kontraktu formantu przycisku.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>, najłatwiej często zaczyna się od istniejącej <xref:System.Windows.Controls.ControlTemplate> i wprowadzić zmiany. Możesz wybrać jedną z następujących czynności, aby zmienić istniejące <xref:System.Windows.Controls.ControlTemplate>:  
  
-   Za pomocą projektanta, takich jak Expression Blend, która zapewnia graficzny interfejs użytkownika służący do tworzenia szablonów kontrolki. Aby uzyskać więcej informacji, zobacz [stylów formantu, który obsługuje szablony](http://go.microsoft.com/fwlink/?LinkId=161153).  
  
-   Pobierz domyślny <xref:System.Windows.Controls.ControlTemplate> i go edytować. Aby znaleźć domyślne szablony kontroli, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [motywy WPF domyślne](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletny przykład  
 W poniższym przykładzie przedstawiono pełną <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> który omówione w tym temacie.  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
