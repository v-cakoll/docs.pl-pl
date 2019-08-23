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
ms.openlocfilehash: 63a0b724b71c4a4901c2dedcf502045a75ec405c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933729"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> Określa strukturę wizualizacji i wizualne zachowanie kontrolki. Możesz dostosować wygląd kontrolki, nadając jej nową <xref:System.Windows.Controls.ControlTemplate>. Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>, należy zastąpić wygląd istniejącej kontrolki bez zmiany jej funkcjonalności. Na przykład można sprawić, aby przyciski w aplikacji były zaokrąglane zamiast domyślnego kształtu kwadratowego, ale przycisk nadal zgłasza <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie.  
  
 W tym temacie objaśniono różne części programu <xref:System.Windows.Controls.ControlTemplate>, demonstruje Tworzenie prostego <xref:System.Windows.Controls.ControlTemplate> dla a <xref:System.Windows.Controls.Button>i wyjaśniono, jak zrozumieć umowę kontroli kontrolki, aby można było dostosować jej wygląd. Ze względu na to [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], że tworzysz wprogramie,możeszzmienićwyglądformantubezpisaniakodu.<xref:System.Windows.Controls.ControlTemplate> Do tworzenia szablonów formantów niestandardowych można także użyć projektanta, takiego jak Microsoft Expression Blend. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tym temacie przedstawiono przykłady, które dostosowują wygląd <xref:System.Windows.Controls.Button> i zawiera pełny przykład na końcu tematu. Aby uzyskać więcej informacji o używaniu wyrażeń Blend, zobacz [Określanie stylu kontrolki, która obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
 Poniższe ilustracje pokazują <xref:System.Windows.Controls.Button> , że program używa <xref:System.Windows.Controls.ControlTemplate> programu, który został utworzony w tym temacie.  
  
 ![Przycisk z szablonem kontrolki niestandardowej.](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
Przycisk, który używa szablonu kontrolki niestandardowej  
  
 ![Przycisk z czerwonym obramowaniem.](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
Przycisk, który używa niestandardowego szablonu kontrolki i ma wskaźnik myszy nad nim  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz, jak tworzyć i używać kontrolek i [](index.md)stylów, jak opisano w kontrolkach. Koncepcje omówione w tym temacie mają zastosowanie do elementów, które dziedziczą z <xref:System.Windows.Controls.Control> klasy, z wyjątkiem. <xref:System.Windows.Controls.UserControl> Nie można zastosować <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.UserControl>do.  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>Kiedy należy utworzyć ControlTemplate  
 Kontrolki mają wiele właściwości, takich <xref:System.Windows.Controls.Border.Background%2A>jak <xref:System.Windows.Controls.Control.Foreground%2A>,, <xref:System.Windows.Controls.Control.FontFamily%2A>i, które można ustawić w celu określenia różnych aspektów wyglądu kontrolki, ale zmiany, które można wprowadzić, ustawiając te właściwości, są ograniczone. Na przykład możesz ustawić <xref:System.Windows.Controls.Control.Foreground%2A> właściwość na niebieską i <xref:System.Windows.Controls.Control.FontStyle%2A> kursywę w <xref:System.Windows.Controls.CheckBox>.  
  
 Bez możliwości tworzenia nowego <xref:System.Windows.Controls.ControlTemplate> dla kontrolek, wszystkie kontrolki w każdej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacji opartej na systemie mają taki sam wygląd ogólny, co ograniczy możliwość tworzenia aplikacji z niestandardowym wyglądem i działaniem. Domyślnie każdy <xref:System.Windows.Controls.CheckBox> ma podobne cechy. Na przykład zawartość <xref:System.Windows.Controls.CheckBox> jest zawsze z prawej strony wskaźnika wyboru, a znacznik wyboru jest zawsze używany, aby wskazać, <xref:System.Windows.Controls.CheckBox> że jest zaznaczone.  
  
 Tworzysz, gdy chcesz dostosować wygląd kontrolki poza ustawieniem, jakie inne właściwości kontrolki będą wykonywać. <xref:System.Windows.Controls.ControlTemplate> Na przykład <xref:System.Windows.Controls.CheckBox>, Załóżmy, że chcesz, aby zawartość pola wyboru była nad wskaźnikiem wyboru, i chcesz, aby znak X wskazywał <xref:System.Windows.Controls.CheckBox> , że jest zaznaczone. Należy określić te zmiany w programie <xref:System.Windows.Controls.ControlTemplate>. <xref:System.Windows.Controls.CheckBox>  
  
 Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.CheckBox> , która z nich korzysta domyślnie. <xref:System.Windows.Controls.ControlTemplate>  
  
 ![Pole wyboru z domyślnym szablonem formantu.](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
Pole wyboru używające domyślnego szablonu kontrolki  
  
 Poniższa ilustracja przedstawia <xref:System.Windows.Controls.CheckBox> , który używa niestandardowych <xref:System.Windows.Controls.ControlTemplate> do <xref:System.Windows.Controls.CheckBox> umieszczania zawartości powyżej wskaźnika <xref:System.Windows.Controls.CheckBox> wyboru i wyświetla symbol X, gdy jest zaznaczone.  
  
 ![Pole wyboru z szablonem niestandardowej kontrolki.](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
Pole wyboru, które używa szablonu kontrolki niestandardowej  
  
 Dla elementu <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>wtymprzykładzie jest stosunkowo skomplikowany, więc w tym temacie jest wykorzystywany prostszy przykład tworzenia dla a. <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.ControlTemplate>  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>Zmiana struktury wizualnej kontrolki  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie formant jest często obiektami złożonymi <xref:System.Windows.FrameworkElement> . Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate>, należy połączyć <xref:System.Windows.FrameworkElement> obiekty w celu utworzenia jednej kontrolki. Element <xref:System.Windows.Controls.ControlTemplate> A musi mieć tylko <xref:System.Windows.FrameworkElement> jeden z nich jako jego głównego elementu. Element główny zwykle zawiera inne <xref:System.Windows.FrameworkElement> obiekty. Kombinacja obiektów tworzy strukturę wizualizacji formantu.  
  
 Poniższy przykład tworzy niestandardowe <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button>dla. <xref:System.Windows.Controls.ControlTemplate> Tworzy strukturę wizualizacji <xref:System.Windows.Controls.Button>. Ten przykład nie zmienia wyglądu przycisku po przesunięciu wskaźnika myszy nad nim lub kliknięciem. Zmiana wyglądu przycisku, gdy znajduje się on w innym stanie, omówiono w dalszej części tego tematu.  
  
 W tym przykładzie struktura wizualizacji składa się z następujących części:  
  
- Nazwa, która służy jako katalog główny <xref:System.Windows.FrameworkElement>szablonu. `RootElement` <xref:System.Windows.Controls.Border>  
  
- A <xref:System.Windows.Controls.Grid> jest`RootElement`elementem podrzędnym.  
  
- A <xref:System.Windows.Controls.ContentPresenter> , który wyświetla zawartość przycisku. <xref:System.Windows.Controls.ContentPresenter> Włącza każdy typ obiektu do wyświetlenia.  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>Zachowanie funkcji właściwości kontrolki przy użyciu Szablonubinding  
 Podczas tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>programu nadal można użyć właściwości publicznych do zmiany wyglądu kontrolki. Rozszerzenie [](../advanced/templatebinding-markup-extension.md) "TemplateBinding" tworzy powiązanie właściwości elementu, który znajduje się w <xref:System.Windows.Controls.ControlTemplate> właściwości publicznej zdefiniowanej przez kontrolkę. W przypadku użycia [szablonubinding](../advanced/templatebinding-markup-extension.md)należy włączyć właściwości kontrolki, aby działały jako parametry szablonu. Oznacza to, że po ustawieniu właściwości kontrolki ta wartość jest przenoszona do elementu, który ma element TemplateBinding. [](../advanced/templatebinding-markup-extension.md)  
  
 W poniższym przykładzie powtórzono część poprzedniego przykładu, która używa rozszerzenia [TemplateBinding](../advanced/templatebinding-markup-extension.md) , aby powiązać właściwości elementów, które znajdują się we <xref:System.Windows.Controls.ControlTemplate> właściwościach publicznych, które są zdefiniowane przez przycisk.  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 W tym przykładzie <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> ma przypisany <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>szablon właściwości. Ponieważ <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> jest powiązany z szablonem, można utworzyć wiele przycisków, które używają <xref:System.Windows.Controls.ControlTemplate> tego samego i <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> ustawić na różne wartości na każdym przycisku. Jeśli <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> szablon nie został powiązany z właściwością elementu <xref:System.Windows.Controls.ControlTemplate>w, ustawienie <xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType> przycisku nie będzie miało wpływu na wygląd przycisku.  
  
 Należy zauważyć, że nazwy dwóch właściwości nie muszą być identyczne. W poprzednim przykładzie <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> Właściwość <xref:System.Windows.Controls.Button> szablonu <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType> jest powiązana <xref:System.Windows.Controls.ContentPresenter>z właściwością. Umożliwia to rozmieszczenie zawartości przycisku w poziomie. <xref:System.Windows.Controls.ContentPresenter>nie ma właściwości o nazwie `HorizontalContentAlignment`, ale <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType> można ją powiązać z <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>. Po powiązaniu szablonu z właściwością upewnij się, że właściwości docelowy i źródłowy są tego samego typu.  
  
 <xref:System.Windows.Controls.Control> Klasa definiuje kilka właściwości, które muszą być używane przez szablon formantu, aby mieć wpływ na kontrolkę, gdy są ustawione. <xref:System.Windows.Controls.ControlTemplate> Sposób użycia właściwości zależy od właściwości. Właściwość <xref:System.Windows.Controls.ControlTemplate> musi być używana w jeden z następujących sposobów:  
  
- Element w szablonie jest <xref:System.Windows.Controls.ControlTemplate> powiązany z właściwością.  
  
- Element w <xref:System.Windows.Controls.ControlTemplate> elemencie dziedziczy właściwość z elementu nadrzędnego <xref:System.Windows.FrameworkElement>.  
  
 Poniższa tabela zawiera listę właściwości wizualnych dziedziczonych przez formant z <xref:System.Windows.Controls.Control> klasy. Wskazuje również, czy domyślny szablon kontrolki kontrolki używa dziedziczonej wartości właściwości, czy też musi być powiązany z szablonem.  
  
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
  
 W tabeli wymieniono tylko właściwości wizualizacji dziedziczone z <xref:System.Windows.Controls.Control> klasy. Poza właściwościami wymienionymi w tabeli, formant może również odziedziczyć <xref:System.Windows.FrameworkElement.DataContext%2A>właściwości, <xref:System.Windows.FrameworkElement.Language%2A>i <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> z elementu nadrzędnego struktury.  
  
 Ponadto <xref:System.Windows.Controls.ContentPresenter> , jeśli znajduje się <xref:System.Windows.Controls.ControlTemplate> w <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ContentPresenter> zostanie automatycznie powiązane <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> z właściwościami i <xref:System.Windows.Controls.ContentControl.Content%2A> . Analogicznie, <xref:System.Windows.Controls.ItemsPresenter> to jest <xref:System.Windows.Controls.ControlTemplate> w <xref:System.Windows.Controls.ItemsControl> ramach programu, zostanie automatycznie powiązane <xref:System.Windows.Controls.ItemsControl.Items%2A> z właściwościami <xref:System.Windows.Controls.ItemsPresenter> i.  
  
 Poniższy przykład tworzy dwa przyciski, które używają <xref:System.Windows.Controls.ControlTemplate> zdefiniowanego w poprzednim przykładzie. Przykład ustawia <xref:System.Windows.Controls.Control.Background%2A>właściwości, <xref:System.Windows.Controls.Control.Foreground%2A>, i <xref:System.Windows.Controls.Control.FontSize%2A> na każdym przycisku. Ustawienie właściwości ma wpływ, ponieważ jest powiązany z szablonem <xref:System.Windows.Controls.ControlTemplate>w. <xref:System.Windows.Controls.Control.Background%2A> Mimo że właściwości <xref:System.Windows.Controls.Control.FontSize%2A>inie są powiązane z szablonem, ustawienie ma efekt, ponieważ ich wartości są dziedziczone. <xref:System.Windows.Controls.Control.Foreground%2A>  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 Powyższy przykład generuje dane wyjściowe podobne do poniższej ilustracji.  
  
 ![Dwa przyciski, jeden niebieski i jeden purpurowy.](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
Dwa przyciski z różnymi kolorami tła  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>Zmiana wyglądu kontrolki w zależności od jej stanu  
 Różnica między przyciskiem z domyślnym wyglądem i przyciskiem w powyższym przykładzie polega na tym, że przycisk domyślny zmienia się, gdy jest on w różnych stanach. Na przykład wygląd przycisku domyślnego zmienia się po naciśnięciu przycisku lub po umieszczeniu wskaźnika myszy nad przyciskiem. <xref:System.Windows.Controls.ControlTemplate> Chociaż nie zmienia funkcjonalności formantu, zmienia zachowanie wizualizacji formantu. Zachowanie wizualne zawiera opis wyglądu kontrolki, gdy jest ona w określonym stanie. Aby zrozumieć różnicę między funkcjonalnością a zachowaniem wizualnym kontrolki, należy wziąć pod uwagę przykład przycisku. Funkcja przycisku ma na celu podnoszenie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia po kliknięciu, ale zachowanie wizualizacji przycisku ma na celu zmianę jego wyglądu po wskazaniu lub naciśnięciu.  
  
 Obiekty służą <xref:System.Windows.VisualState> do określania wyglądu kontrolki, gdy jest ona w określonym stanie. A <xref:System.Windows.VisualState> zawiera<xref:System.Windows.Media.Animation.Storyboard> zmiany wyglądu<xref:System.Windows.Controls.ControlTemplate>elementów znajdujących się w. Nie trzeba pisać żadnego kodu, ponieważ logika kontrolki zmienia stan przy użyciu <xref:System.Windows.VisualStateManager>. Gdy kontrolka przejdzie do stanu, który jest określony <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> przez właściwość <xref:System.Windows.Media.Animation.Storyboard> , rozpocznie się. Gdy kontrolka opuszcza stan, <xref:System.Windows.Media.Animation.Storyboard> zostaje zatrzymana.  
  
 Poniższy przykład pokazuje <xref:System.Windows.VisualState> , że zmienia wygląd <xref:System.Windows.Controls.Button> , gdy wskaźnik myszy znajduje się nad nim. Zmienia kolor obramowania przycisku, zmieniając kolor `BorderBrush`. <xref:System.Windows.Media.Animation.Storyboard> Jeśli odwołujesz się <xref:System.Windows.Controls.ControlTemplate> do przykładu na początku tego tematu, będzie `BorderBrush` to nazwa <xref:System.Windows.Media.SolidColorBrush> przypisana do <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Controls.Border>obiektu.  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 Kontrolka jest odpowiedzialna za Definiowanie stanów w ramach umowy dotyczącej kontroli, która jest szczegółowo omówiona w temacie [Dostosowywanie innych kontrolek przez zrozumienie kontraktu kontroli](#customizing_other_controls_by_understanding_the_control_contract) w dalszej części tego tematu. W poniższej tabeli wymieniono Stany, które są określone dla <xref:System.Windows.Controls.Button>.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy znajduje się nad kontrolką.|  
|Naciśnięto|CommonStates|Kontrolka zostanie naciśnięty.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Kontrolka ma fokus.|  
|Bez fokusu|FocusStates|Kontrolka nie ma fokusu.|  
  
 `MouseOver` `Normal` `CommonStates` `Disabled` Definiuje dwie grupy stanów: grupa zawiera Stany,, `Pressed`i. <xref:System.Windows.Controls.Button> Grupa zawiera Stany`Unfocused` i `Focused`. `FocusStates` Stany w tej samej grupie Stanów wykluczają się wzajemnie. Kontrolka zawsze znajduje się w dokładnie jednym stanie na grupę. Na przykład <xref:System.Windows.Controls.Button> może mieć fokus nawet wtedy, gdy wskaźnik myszy nie znajduje się nad nim, <xref:System.Windows.Controls.Button> więc `Focused` stan może być w `MouseOver`, `Pressed`, lub `Normal` .  
  
 Dodaj <xref:System.Windows.VisualState> obiekty do <xref:System.Windows.VisualStateGroup> obiektów. Dodaj <xref:System.Windows.VisualStateGroup> obiekty<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> do dołączonej właściwości. W poniższym przykładzie zdefiniowano <xref:System.Windows.VisualState> obiekty `Normal`dla, `MouseOver` `Pressed` i Stanów, które są wszystkie w grupie.`CommonStates` Każda <xref:System.Windows.VisualState.Name%2A> z nich <xref:System.Windows.VisualState> jest zgodna z nazwą w powyższej tabeli. Stan i Stany `FocusStates` w grupie są pomijane w celu zachowania przykładu, ale znajdują się one w całym przykładzie na końcu tego tematu. `Disabled`  
  
> [!NOTE]
> Upewnij się, że właściwość <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType> Attached została ustawiona w katalogu <xref:System.Windows.FrameworkElement> głównym <xref:System.Windows.Controls.ControlTemplate>.  
  
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
 W poprzednim przykładzie wygląd przycisku zmienia się również wtedy, gdy użytkownik kliknie go, ale jeśli przycisk nie zostanie wciśnięty przez cały czas, użytkownik nie zobaczy efektu. Domyślnie animacja zajmuje jedną sekundę. Ze względu na to, że użytkownicy mogą klikać i zwalniać przycisk w znacznie krótszym czasie, opinie wizualne nie będą obowiązywać <xref:System.Windows.Controls.ControlTemplate> , Jeśli pozostawisz w stanie domyślnym.  
  
 Można określić czas, w którym ma nastąpić animacja, aby bezproblemowo przeszedł formant z jednego stanu do innego przez dodanie <xref:System.Windows.VisualTransition> obiektów <xref:System.Windows.Controls.ControlTemplate>do. Podczas tworzenia <xref:System.Windows.VisualTransition>należy określić co najmniej jedną z następujących czynności:  
  
- Czas trwania przejścia między Stanami.  
  
- Dodatkowe zmiany dotyczące wyglądu kontrolki, która występuje w momencie przejścia.  
  
- Które Stany <xref:System.Windows.VisualTransition> są stosowane do.  
  
### <a name="specifying-the-duration-of-a-transition"></a>Określanie czasu trwania przejścia  
 Możesz określić czas trwania przejścia przez ustawienie <xref:System.Windows.VisualTransition.GeneratedDuration%2A> właściwości. Powyższy przykład ma wartość <xref:System.Windows.VisualState> , która określa, że obramowanie przycisku staje się przezroczyste po naciśnięciu przycisku, ale animacja jest zbyt długa, aby można było zauważyć, że przycisk jest szybko wciśnięty i wydawany. Możesz użyć, <xref:System.Windows.VisualTransition> aby określić ilość czasu, przez jaki formant przechodzi do naciśniętego stanu. Poniższy przykład określa, że kontrolka przyjmuje jedną setną część sekundy, aby przejść do stanu naciśniętego.  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>Określanie zmian wyglądu kontrolki podczas przejścia  
 <xref:System.Windows.VisualTransition> Zawiera,któryrozpoczynasię,gdykontrolka<xref:System.Windows.Media.Animation.Storyboard> przechodzi między Stanami. Na przykład można określić, że określona animacja ma być wykonywana, gdy kontrolka przechodzi ze `MouseOver` stanu `Normal` do stanu. Poniższy przykład tworzy obiekt <xref:System.Windows.VisualTransition> , który określa, że gdy użytkownik przesuwa wskaźnik myszy z przycisku, obramowanie przycisku zmieni się na niebiesko, a następnie do żółtego, a następnie do czerni w 1,5 sekund.  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>Określanie, kiedy VisualTransition jest stosowany  
 <xref:System.Windows.VisualTransition> Może być ograniczone do zastosowania tylko do określonych stanów lub może być stosowane zawsze, gdy kontrolka przechodzi między Stanami. W poprzednim <xref:System.Windows.VisualTransition> przykładzie, jest stosowane, gdy kontrolka przechodzi `MouseOver` ze stanu do `Normal` stanu <xref:System.Windows.VisualTransition> ; w tym przykładzie przed tym, jest stosowana, gdy kontrolka przechodzi do `Pressed` stanu. Gdy jest stosowany <xref:System.Windows.VisualTransition.To%2A> , <xref:System.Windows.VisualTransition> należy określić właściwości i. <xref:System.Windows.VisualTransition.From%2A> W poniższej tabeli opisano poziomy ograniczeń od najbardziej restrykcyjne do najmniej restrykcyjne.  
  
|Typ ograniczenia|Wartość z|Wartość do|  
|-------------------------|-------------------|-----------------|  
|Od określonego stanu do innego określonego stanu|Nazwa<xref:System.Windows.VisualState>|Nazwa<xref:System.Windows.VisualState>|  
|Od dowolnego stanu do określonego stanu|Nie ustawiono|Nazwa<xref:System.Windows.VisualState>|  
|Od określonego stanu do dowolnego stanu|Nazwa<xref:System.Windows.VisualState>|Nie ustawiono|  
|Z dowolnego stanu do dowolnego innego stanu|Nie ustawiono|Nie ustawiono|  
  
 Można mieć wiele <xref:System.Windows.VisualTransition> obiektów <xref:System.Windows.VisualStateGroup> w odniesieniu do tego samego stanu, ale zostaną one użyte w kolejności, w jakiej określono w poprzedniej tabeli. W poniższym przykładzie istnieją dwa <xref:System.Windows.VisualTransition> obiekty. Gdy kontrolka przechodzi ze `Pressed` stanu `MouseOver` do stanu, <xref:System.Windows.VisualTransition> zostanie użyta opcja, która <xref:System.Windows.VisualTransition.From%2A> ma <xref:System.Windows.VisualTransition.To%2A> oba elementy i. Gdy kontrolka przechodzi ze stanu, który nie `Pressed` `MouseOver` jest stanem, jest używany inny stan.  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualState> Zawierawłaściwość,<xref:System.Windows.VisualStateGroup>która zawiera <xref:System.Windows.VisualTransition> obiekty, które mają zastosowanie do obiektów w obiekcie. <xref:System.Windows.VisualStateGroup.Transitions%2A> <xref:System.Windows.VisualStateGroup> Jako autor możesz dowolnie <xref:System.Windows.VisualTransition>dołączać. <xref:System.Windows.Controls.ControlTemplate> Jeśli <xref:System.Windows.VisualTransition.To%2A> jednak właściwości i <xref:System.Windows.VisualTransition.From%2A> są ustawione na nazwy stanów <xref:System.Windows.VisualStateGroup>, które nie znajdują się w, <xref:System.Windows.VisualTransition> wartość jest ignorowana.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.VisualStateGroup> `CommonStates`dla. W przykładzie zdefiniowano <xref:System.Windows.VisualTransition> dla każdego przycisku następujące przejścia.  
  
- `Pressed` Do stanu.  
  
- `MouseOver` Do stanu.  
  
- `Pressed` Ze stanu`MouseOver` do stanu.  
  
- `MouseOver` Ze stanu`Normal` do stanu.  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>Dostosowywanie innych kontrolek przez zrozumienie kontraktu kontroli  
 Kontrolka, która używa <xref:System.Windows.Controls.ControlTemplate> do określenia struktury wizualizacji (za pomocą <xref:System.Windows.FrameworkElement> obiektów) i zachowań wizualizacji (za <xref:System.Windows.VisualState> pomocą obiektów) używa modelu sterowania częściami. Wiele z formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4, korzysta z tego modelu. Części, których <xref:System.Windows.Controls.ControlTemplate> autor musi wiedzieć, są przekazywane przez umowę kontroli. W przypadku zrozumienia części kontraktu kontroli można dostosować wygląd dowolnej kontrolki, która używa modelu sterowania częściami.  
  
 Kontrakt kontrolny ma trzy elementy:  
  
- Elementy wizualizacji, których używa logika kontrolki.  
  
- Stany formantu i grupy, do których należy każdy stan.  
  
- Właściwości publiczne, które wizualnie wpływają na kontrolkę.  
  
### <a name="visual-elements-in-the-control-contract"></a>Elementy wizualne w umowie kontroli  
 Czasami logika kontrolki współdziała z obiektem <xref:System.Windows.FrameworkElement> , który znajduje się <xref:System.Windows.Controls.ControlTemplate>w. Na przykład kontrolka może obsłużyć zdarzenie jednego z jego elementów. Gdy formant oczekuje na znalezienie określonego <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate>w, musi <xref:System.Windows.Controls.ControlTemplate> przekazać te informacje do autora. Formant używa <xref:System.Windows.TemplatePartAttribute> do przekazywania typu oczekiwanego elementu i nazwy elementu, który ma być. Element nie ma <xref:System.Windows.FrameworkElement> części w umowie kontroli, ale inne <xref:System.Windows.Controls.ComboBox>kontrolki, takie jak, do. <xref:System.Windows.Controls.Button>  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.TemplatePartAttribute> obiekty, które są określone <xref:System.Windows.Controls.ComboBox> w klasie. Logika <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.TextBox> oczekuje znalezienia nazwanych `PART_EditableTextBox` i <xref:System.Windows.Controls.Primitives.Popup> nazwanych `PART_Popup` w <xref:System.Windows.Controls.ControlTemplate>elemencie.  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 Poniższy przykład pokazuje uproszczony <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> dla, który zawiera elementy <xref:System.Windows.TemplatePartAttribute> , które są określone <xref:System.Windows.Controls.ComboBox> przez obiekty w klasie.  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>Stany w umowie kontroli  
 Stany formantu są również częścią kontraktu kontroli. Przykład tworzenia a <xref:System.Windows.Controls.ControlTemplate> dla programu <xref:System.Windows.Controls.Button> pokazuje, jak <xref:System.Windows.Controls.Button> określić wygląd w zależności od jego Stanów. <xref:System.Windows.VisualState> <xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> <xref:System.Windows.VisualStateGroup> [](#changing_the_appearance_of_a_control_depending_on_its_state) Tworzysz dla każdego określonego stanu i umieścisz wszystkie obiekty, które współużytkują w, zgodnie z opisem w temacie Zmiana wyglądu kontrolki w zależności od jej stanu we wcześniejszej części tego tematu. <xref:System.Windows.VisualState> Kontrolki innych firm powinny określać Stany przy użyciu <xref:System.Windows.TemplateVisualStateAttribute>programu, który umożliwia narzędziom projektanta, takim jak Expression Blend, Uwidacznianie Stanów formantów na potrzeby tworzenia szablonów kontroli.  
  
 Aby znaleźć umowę kontroli dla formantów, które są dołączone do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Style i szablony kontrolek](control-styles-and-templates.md).  
  
### <a name="properties-in-the-control-contract"></a>Właściwości w kontrakcie kontrolnym  
 Właściwości publiczne, które wizualnie wpływają na kontrolkę, są również zawarte w umowie kontroli. Można ustawić te właściwości, aby zmienić wygląd formantu bez tworzenia nowego <xref:System.Windows.Controls.ControlTemplate>. Można również użyć rozszerzenia [TemplateBinding](../advanced/templatebinding-markup-extension.md) , aby powiązać właściwości elementów, które znajdują się we <xref:System.Windows.Controls.ControlTemplate> właściwościach publicznych, które <xref:System.Windows.Controls.Button>są zdefiniowane przez.  
  
 Poniższy przykład pokazuje kontrakt kontrolny dla przycisku.  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 Podczas tworzenia programu <xref:System.Windows.Controls.ControlTemplate>często najłatwiejszym rozwiązaniem jest rozpoczęcie od istniejącego <xref:System.Windows.Controls.ControlTemplate> i wprowadzenie do niego zmian. Aby zmienić istniejący <xref:System.Windows.Controls.ControlTemplate>element, można wykonać jedną z następujących czynności:  
  
- Użyj projektanta, takiego jak Expression Blend, który udostępnia graficzny interfejs użytkownika do tworzenia szablonów formantów. Aby uzyskać więcej informacji, zobacz [Określanie stylu kontrolki, która obsługuje szablony](https://go.microsoft.com/fwlink/?LinkId=161153).  
  
- Pobierz wartość domyślną <xref:System.Windows.Controls.ControlTemplate> i edytuj ją. Aby znaleźć domyślne szablony kontrolek, które są dołączone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]do programu, zobacz [domyślne motywy WPF](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy przykład przedstawia zakończenie <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> , który został omówiony w tym temacie.  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów i stylów](styling-and-templating.md)
