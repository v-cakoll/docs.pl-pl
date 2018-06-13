---
title: Przegląd Autorstwo formantów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: a6c2c796819924cdbd15d6eefffe10a607bad9bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558086"
---
# <a name="control-authoring-overview"></a>Przegląd Autorstwo formantów
Możliwość rozszerzania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] model kontroli, znacznie ogranicza potrzebę tworzenia nowego formantu. Jednak w niektórych przypadkach może nadal należy utworzyć niestandardowego formantu. W tym temacie opisano funkcje, co minimalizuje konieczność tworzenia kontrolki niestandardowej, a inny formant tworzenia modeli w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. W tym temacie przedstawiono również sposób tworzenia nowego formantu.  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Alternatywy dla zapisywania nowych formantu  
 W przeszłości Jeśli chcesz uzyskać dostosowane środowisko z istniejącej kontrolce było zmieniać standardowe właściwości formantu, takie jak kolor, szerokość obramowania i rozmiar czcionki. Jeśli zamierza rozszerzyć wyglądu i zachowania formantu poza tych wstępnie zdefiniowanych parametrów, należy utworzyć nową kontrolkę, zwykle dziedziczenie z istniejącego formantu i przesłaniania metody odpowiedzialne za narysowanie formantu.  Mimo że nadal jest dostępną opcją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia użytkownikowi dostosowywanie istniejących formantów przy użyciu zaawansowanych modelu zawartości, style, szablonów i wyzwalaczy. Poniżej przedstawiono przykłady jak te funkcje mogą służyć do tworzenia niestandardowych i spójne środowiska bez konieczności tworzenia nowego formantu.  
  
-   **Zawartość sformatowana.** Duża liczba standardowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty obsługuje sformatowanego zawartości. Na przykład właściwość content <xref:System.Windows.Controls.Button> jest typu <xref:System.Object>, więc teoretycznie niczego mogą być wyświetlane na <xref:System.Windows.Controls.Button>.  Aby wyświetlić obraz i tekst przycisku, możesz dodać obraz i <xref:System.Windows.Controls.TextBlock> do <xref:System.Windows.Controls.StackPanel> i przypisz <xref:System.Windows.Controls.StackPanel> do <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości. Ponieważ formanty można wyświetlić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów wizualnych i dowolne dane, jest mniej wymagane, aby utworzyć nowy formant lub zmodyfikować formant do obsługi złożonych wizualizacji. Aby uzyskać więcej informacji na temat modelu zawartości dla <xref:System.Windows.Controls.Button> i innej zawartości modeli w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [modelu zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
-   **Style.** A <xref:System.Windows.Style> to zbiór wartości, które reprezentują właściwości formantu. Przy użyciu stylów, można utworzyć wielokrotnego użytku reprezentację żądanego formantu wygląd i zachowanie bez zapisywania nowego formantu. Załóżmy na przykład, że mają wszystkie Twoje <xref:System.Windows.Controls.TextBlock> formanty mają czerwony, Arial czcionki o rozmiarze czcionki 14. Można utworzyć stylu jako zasób i odpowiednio ustaw odpowiednie właściwości. A następnie co <xref:System.Windows.Controls.TextBlock> dodanie do aplikacji będą miały taki sam wygląd.  
  
-   **Szablony danych.** A <xref:System.Windows.DataTemplate> umożliwia dostosowanie sposobu wyświetlania danych w formancie. Na przykład <xref:System.Windows.DataTemplate> może służyć do określenia sposobu wyświetlania danych w <xref:System.Windows.Controls.ListBox>.  Aby na przykład, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  Oprócz Dostosowywanie wyglądu danych, <xref:System.Windows.DataTemplate> mogą zawierać elementy interfejsu użytkownika, które zapewnia dużą elastyczność w niestandardowych UI.  Na przykład za pomocą <xref:System.Windows.DataTemplate>, można utworzyć <xref:System.Windows.Controls.ComboBox> , w którym każdy element zawiera pole wyboru.  
  
-   **Szablony formantu.** Wiele formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyj <xref:System.Windows.Controls.ControlTemplate> do definiowania struktury i wyglądu, która oddziela od funkcji formantu wyglądu formantu formantu. Może znacząco Zmienianie wyglądu formantu przez ponowne definiowanie jej <xref:System.Windows.Controls.ControlTemplate>.  Na przykład załóżmy, że formant, który wygląda jak sygnalizatora. Ten formant ma prosty interfejs użytkownika i funkcje.  Formant jest okręgi trzy, z których tylko jedna może być włączone w czasie. Po niektórych odbicia, użytkownik może należy pamiętać, że <xref:System.Windows.Controls.RadioButton> oferuje funkcje tylko jeden zaznaczony na raz, ale wygląd domyślny <xref:System.Windows.Controls.RadioButton> prawdopodobnie brak świateł na sygnalizatora.  Ponieważ <xref:System.Windows.Controls.RadioButton> używa szablonu kontroli w celu zdefiniowania jej wygląd jest łatwy do ponownego zdefiniowania <xref:System.Windows.Controls.ControlTemplate> do wymagań formantu i używa przycisków radiowych sygnalizatora Twojego.  
  
    > [!NOTE]
    >  Mimo że <xref:System.Windows.Controls.RadioButton> można użyć <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> nie są wystarczające w tym przykładzie.  <xref:System.Windows.DataTemplate> Definiuje wygląd elementów zawartości formantu. W przypadku liczby <xref:System.Windows.Controls.RadioButton>, zawartość jest wyświetlany niezależnie od prawej koło, która wskazuje, czy <xref:System.Windows.Controls.RadioButton> jest zaznaczone.  W tym przykładzie sygnalizatora przycisk radiowy musi składać się koło, które można "podświetlane." Ponieważ wymaganie wygląd sygnalizatora tak różni się od domyślnego wyglądu <xref:System.Windows.Controls.RadioButton>, należy go ponownie zdefiniować <xref:System.Windows.Controls.ControlTemplate>.  Ogólnie rzecz biorąc <xref:System.Windows.DataTemplate> służy do definiowania zawartości (lub danych) z kontroli oraz a <xref:System.Windows.Controls.ControlTemplate> służy do definiowania struktury formantu.  
  
-   **Wyzwalacze.** A <xref:System.Windows.Trigger> umożliwia dynamiczną zmianę wygląd i zachowanie formant bez tworzenia nowego formantu. Na przykład, załóżmy, że istnieje wiele <xref:System.Windows.Controls.ListBox> formantów w aplikacji i elementy w każdym <xref:System.Windows.Controls.ListBox> jako pogrubiony i czerwony po jej wybraniu. Twoje pierwsze instinct może być można utworzyć klasy, która dziedziczy po <xref:System.Windows.Controls.ListBox> i zastąpić <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metodę, aby zmienić wygląd wybranego elementu, ale lepszym rozwiązaniem jest dodanie wyzwalacz do styl <xref:System.Windows.Controls.ListBoxItem> który zmienia wygląd wybrany element. Wyzwalacz można zmienić wartości właściwości lub podjąć działania w zależności od wartości właściwości. <xref:System.Windows.EventTrigger> Umożliwia podjęcie działania po wystąpieniu zdarzenia.  
  
 Aby uzyskać więcej informacji na temat style, szablonów i wyzwalaczy, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Ogólnie rzecz biorąc Jeśli formant odzwierciedla funkcji istniejącego formantu, ale ma wygląd formantu, najpierw warto czy służy dowolnej z metod opisanych w tej sekcji można zmienić wygląd istniejącego formantu.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Modele do tworzenia kontrolki  
 Rozbudowane modelu zawartości, style, szablonów i wyzwalaczy zminimalizować trzeba utworzyć nowy formant. Jednak jeśli trzeba utworzyć nową kontrolkę, ważne jest zrozumienie inny formant tworzenia modeli w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia trzy modele ogólne do tworzenia kontrolek, z których każdy zawiera inny zestaw funkcji i poziom elastyczności. Klasy podstawowej są trzy modele <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, i <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>Wyprowadzanie z UserControl  
 Najprostszym sposobem tworzenia formantu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma dziedziczyć <xref:System.Windows.Controls.UserControl>. Podczas budowania formantu dziedziczy <xref:System.Windows.Controls.UserControl>, dodać istniejące składniki <xref:System.Windows.Controls.UserControl>, nazwa składników i odwołać obsługi zdarzeń w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Następnie można odwoływać się elementy o i zdefiniuj programy obsługi zdarzeń w kodzie. Ten model programowania jest bardzo podobny do modelu używany do tworzenia aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Jeśli utworzony prawidłowo, <xref:System.Windows.Controls.UserControl> można korzystać z zalet bogatej zawartości, style i wyzwalaczy. Jednak jeśli dziedziczy formantu <xref:System.Windows.Controls.UserControl>, osoby, które Użyj swojego formantu nie będzie mógł używać <xref:System.Windows.DataTemplate> lub <xref:System.Windows.Controls.ControlTemplate> do dostosowania jego wyglądu.  Konieczne jest pochodną <xref:System.Windows.Controls.Control> klasy lub jednej z jej klas pochodnych (inne niż <xref:System.Windows.Controls.UserControl>) można utworzyć niestandardowego formantu, który obsługuje szablony.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>Korzyści wynikające z UserControl  
 Należy wziąć pod uwagę pochodny <xref:System.Windows.Controls.UserControl> wszystkie następujące zastosowania:  
  
-   Chcesz skompilować formantu podobnie do sposobu tworzenia aplikacji.  
  
-   Formantu składa się tylko z istniejącymi elementami.  
  
-   Nie należy do obsługi złożonych dostosowań.  
  
### <a name="deriving-from-control"></a>Wyprowadzanie z formantu  
 Wyprowadzanie z <xref:System.Windows.Controls.Control> klasy jest używany przez większość istniejącego modelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki. Podczas tworzenia formantu dziedziczy <xref:System.Windows.Controls.Control> klasy, należy zdefiniować jego wygląd przy użyciu szablonów. W ten sposób można oddzielić od wizualnej reprezentacji operacyjne logiki. Można także zapewnić oddzielenie logiki i interfejsu użytkownika przy użyciu poleceń i powiązań zamiast zdarzenia i unikanie odwołaniem do elementów w <xref:System.Windows.Controls.ControlTemplate> zawsze, gdy jest to możliwe.  Jeśli interfejsu użytkownika i logiki formantu są poprawnie rozdzielonymi, użytkownik formantu można ponownie zdefiniować formantu <xref:System.Windows.Controls.ControlTemplate> do dostosowania jego wyglądu. Mimo że budowania niestandardowego <xref:System.Windows.Controls.Control> nie jest tak proste, jak budynek <xref:System.Windows.Controls.UserControl>, niestandardowego <xref:System.Windows.Controls.Control> zapewnia większą elastyczność.  
  
#### <a name="benefits-of-deriving-from-control"></a>Korzyści wynikające z formantu  
 Należy wziąć pod uwagę pochodny <xref:System.Windows.Controls.Control> zamiast <xref:System.Windows.Controls.UserControl> klasy, jeśli dowolny z następujących warunków:  
  
-   Ma wygląd formantu możliwość dostosowania za pośrednictwem <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Ma formantu do obsługi różnych kompozycji.  
  
### <a name="deriving-from-frameworkelement"></a>Wyprowadzanie z FrameworkElement  
 Formanty, które pochodzą z <xref:System.Windows.Controls.UserControl> lub <xref:System.Windows.Controls.Control> opierają się na tworzenie istniejące elementy. W różnych scenariuszach jest dopuszczalne rozwiązanie, ponieważ każdy obiekt, który dziedziczy <xref:System.Windows.FrameworkElement> może znajdować się w <xref:System.Windows.Controls.ControlTemplate>. Istnieją jednak razy podczas wygląd formantu wymaga więcej niż funkcji prosty element kompozycji. W tych sytuacjach tworzony składnik na <xref:System.Windows.FrameworkElement> jest właściwie.  
  
 Istnieją dwie metody standardowe dla tworzenia <xref:System.Windows.FrameworkElement>— na podstawie składników: bezpośrednie renderowanie i niestandardowych kompozycji elementu. Bezpośrednie renderowania obejmuje zastępowanie <xref:System.Windows.UIElement.OnRender%2A> metody <xref:System.Windows.FrameworkElement> i <xref:System.Windows.Media.DrawingContext> operacje, które jawnie definiować wizualnych składnika. Jest to metoda używana przez <xref:System.Windows.Controls.Image> i <xref:System.Windows.Controls.Border>. Niestandardowy element kompozycji polega na użyciu obiekty typu <xref:System.Windows.Media.Visual> utworzenie wyglądu składnika. Na przykład zobacz [przy użyciu obiektów DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> Przykładem formantu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używający elementu niestandardowego kompozycji. Użytkownik może również mieszać bezpośredniego renderowania i kompozycji elementu niestandardowego, w tym samym formancie.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>Korzyści wynikające z FrameworkElement  
 Należy wziąć pod uwagę pochodny <xref:System.Windows.FrameworkElement> Jeśli dowolny z następujących warunków:  
  
-   Chcesz, aby ścisła kontrola nad wyglądem formantu poza dostarczanych przez element prosty kompozycji.  
  
-   Chcesz zdefiniować wygląd formantu, definiując logiki renderowania.  
  
-   Aby tworzą istniejące elementy w nowych metod, które przekraczają możliwości programu <xref:System.Windows.Controls.UserControl> i <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Formant tworzenia podstawy  
 Jak już wspomniano, jedną z najbardziej zaawansowanych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest możliwość wykracza poza ustawiania podstawowych właściwości formantu, aby zmienić wygląd i zachowanie, ale nadal nie konieczności można utworzyć niestandardowego formantu. Stylów, powiązań danych i funkcji wyzwalacza są możliwe przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń systemu. W poniższych sekcjach opisano niektóre wskazówki, które należy wykonać, niezależnie od tego modelu jest używany do utworzenia kontrolki niestandardowej, dzięki czemu użytkownicy formantu niestandardowego mogą używać tych funkcji, tak samo, jak dla formantu, który jest dołączony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Użyj właściwości zależności  
 Gdy właściwość jest właściwością zależności, możliwe jest wykonanie następujących czynności:  
  
-   Ustaw właściwość w stylu.  
  
-   Powiązanie właściwości ze źródłem danych.  
  
-   Użyj zasobu dynamicznego jako wartość właściwości.  
  
-   We właściwości animacji.  
  
 Jeśli chcesz, aby właściwość formantu do obsługi tej funkcji, należy zaimplementować go jako właściwość zależności. W poniższym przykładzie zdefiniowano właściwość zależności o nazwie `Value` przez wykonanie następujących czynności:  
  
-   Zdefiniuj <xref:System.Windows.DependencyProperty> identyfikatora o nazwie `ValueProperty` jako `public` `static` `readonly` pola.  
  
-   Zarejestrować nazwy właściwości w systemie właściwości przez wywołanie metody <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aby określić następujące:  
  
    -   Nazwa właściwości.  
  
    -   Typ właściwości.  
  
    -   Typ, który jest właścicielem właściwości.  
  
    -   Metadane dla właściwości. Metadane zawiera wartość domyślna właściwości, <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>.  
  
-   Zdefiniuj [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości o nazwie `Value`, która jest tej samej nazwie, które jest używane do rejestrowania właściwości zależności, implementując właściwości `get` i `set` metody dostępu. Należy pamiętać, że `get` i `set` wywoływać tylko metody dostępu <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> odpowiednio. Zaleca się, że metody dostępu właściwości zależności nie zawiera dodatkową logikę, ponieważ klienci i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można pominąć metody dostępu i wywołanie <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Na przykład, gdy właściwość jest powiązana z danych źródłowych, właściwości `set` nie wywołano metody dostępu.  Zamiast opcji dodawania dodatkową logikę do pobierania i metod dostępu set, użyj <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, i <xref:System.Windows.PropertyChangedCallback> delegatów uwzględniał lub sprawdź wartość, gdy zmieni się.  Aby uzyskać więcej informacji o tych wywołań zwrotnych, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Zdefiniuj metodę <xref:System.Windows.CoerceValueCallback> o nazwie `CoerceValue`. `CoerceValue` zapewnia, że `Value` jest większa lub równa `MinValue` i mniejsza niż lub równa `MaxValue`.  
  
-   Zdefiniuj metodę <xref:System.Windows.PropertyChangedCallback>o nazwie `OnValueChanged`. `OnValueChanged` Tworzy <xref:System.Windows.RoutedPropertyChangedEventArgs%601> obiektu i przygotowuje podnieść `ValueChanged` kierowanego zdarzenia. W następnej sekcji omówiono kierowane zdarzenia.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Aby uzyskać więcej informacji, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Użyj kierowane zdarzenia  
 Podobnie jak zależności właściwości rozszerzyć pojęcia [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości o dodatkowe funkcje, kierowane zdarzenia rozszerzyć pojęcie standard [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. Podczas tworzenia nowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontroli, jest również dobrym rozwiązaniem do zaimplementowania wydarzenia jako kierowanego zdarzenia, ponieważ kierowanego zdarzenia obsługuje następujące działania:  
  
-   Zdarzenia można obsługiwać w nadrzędnej wielu formantów. Zdarzenie w przypadku zdarzeń propagacji, pojedynczego elementu nadrzędnego, w drzewie elementu mogą subskrybować zdarzenia. Następnie aplikacja autorzy mogą używać jednej procedury obsługi na odpowiadanie na zdarzenia wielu formantów. Na przykład, jeśli formant jest częścią każdego elementu w <xref:System.Windows.Controls.ListBox> (ponieważ jest ona objęta <xref:System.Windows.DataTemplate>), Deweloper aplikacji można zdefiniować programu obsługi zdarzeń dla zdarzenia tego formantu <xref:System.Windows.Controls.ListBox>. Zawsze, gdy zdarzenie wystąpi na wszystkich kontrolek, nosi nazwę programu obsługi zdarzeń.  
  
-   Kierowane zdarzenia mogą być używane w <xref:System.Windows.EventSetter>, które umożliwia deweloperom aplikacji określenie programu obsługi zdarzeń w stylu.  
  
-   Kierowane zdarzenia mogą być używane w <xref:System.Windows.EventTrigger>, która jest przydatne w przypadku animowania właściwości przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 W poniższym przykładzie zdefiniowano kierowanego zdarzenia, wykonując następujące czynności:  
  
-   Zdefiniuj <xref:System.Windows.RoutedEvent> identyfikatora o nazwie `ValueChangedEvent` jako `public` `static` `readonly` pola.  
  
-   Zarejestruj kierowanego zdarzenia przez wywołanie metody <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> metody. W przykładzie określono następujące informacje, gdy wywołuje <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   Nazwa zdarzenia jest `ValueChanged`.  
  
    -   Strategii routingu jest <xref:System.Windows.RoutingStrategy.Bubble>, co oznacza, że program obsługi zdarzeń w źródle (obiekt, który wywołuje zdarzenie) jest nazywany najpierw, a następnie programów obsługi zdarzeń na elementy nadrzędne źródło nazywane są kolejno, począwszy od programu obsługi zdarzeń w najbardziej element nadrzędny.  
  
    -   Typem obsługi zdarzeń jest <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, skonstruowane z <xref:System.Decimal> typu.  
  
    -   Typ będący właścicielem zdarzenia jest `NumericUpDown`.  
  
-   Deklarowanie publiczne zdarzenie o nazwie `ValueChanged` i zawiera deklaracjach metod dostępu zdarzeń. Przykład wywołania <xref:System.Windows.UIElement.AddHandler%2A> w `add` deklaracja metody dostępu i <xref:System.Windows.UIElement.RemoveHandler%2A> w `remove` deklaracja dostępu do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń usługi.  
  
-   Tworzenie metody chroniony, wirtualny o nazwie `OnValueChanged` który zgłasza `ValueChanged` zdarzeń.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Aby uzyskać więcej informacji, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md) i [Tworzenie niestandardowych kierowane zdarzenia](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Użyj powiązania  
 Rozdzielenie interfejsu użytkownika z formantu od jej logiki, należy rozważyć używanie powiązania danych. Jest to szczególnie ważne w przypadku określenia jej wyglądu formantu przy użyciu <xref:System.Windows.Controls.ControlTemplate>. Użycie wiązania danych, można wyeliminować konieczność odwołania określone elementy interfejsu użytkownika z kodu. Jest dobrym rozwiązaniem, aby uniknąć odwołania do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> ponieważ gdy kod odwołuje się do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.ControlTemplate> została zmieniona, potrzeb elementy mają zostać uwzględnione w nowym <xref:System.Windows.Controls.ControlTemplate>.  
  
 Następujące aktualizacje przykład <xref:System.Windows.Controls.TextBlock> z `NumericUpDown` kontroli, przypisywanie nazwę i odwołuje się do pola tekstowego według nazwy w kodzie.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 W poniższym przykładzie użyto powiązania w celu samo.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Projekt dla projektantów  
 Aby uzyskać pomoc w przypadku kontrolek niestandardowych WPF w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (na przykład właściwość edycji w oknie właściwości), postępuj zgodnie z poniższymi wskazówkami.  Aby uzyskać więcej informacji na temat tworzenia dla [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], zobacz [projektanta WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
#### <a name="dependency-properties"></a>Właściwości zależności  
 Pamiętaj zaimplementować [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` i `set` metod dostępu w sposób opisany w "Zależności Użyj właściwości". Projektanci może używać otoka do wykrycia obecności właściwości zależności, ale, takie jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i klientów formantu, nie są wymagane do wywołania metody dostępu podczas pobierania lub ustawiania właściwości.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Dołączone właściwości należy zaimplementować w formantach niestandardowych, korzystając z następujących wskazówek:  
  
-   Ma `public` `static` `readonly` <xref:System.Windows.DependencyProperty> w postaci *PropertyName* `Property` który tworzenia przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Nazwy właściwości, która została przekazana do <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musi odpowiadać *PropertyName*.  
  
-   Implementowanie para `public` `static` CLR metody o nazwie `Set` *PropertyName* i `Get` *PropertyName*. Obie metody powinna obsługiwać klasę pochodzącą od <xref:System.Windows.DependencyProperty> jako pierwszy argument. `Set` *PropertyName* metoda przyjmuje również argumentem, którego typ jest zgodny z typem danych zarejestrowanych dla właściwości. `Get` *PropertyName* metoda powinna zwrócić wartość tego samego typu. Jeśli `Set` *PropertyName* Brak metody, właściwość jest oznaczona jako tylko do odczytu.  
  
-   `Set` *PropertyName* i `Get` *PropertyName* należy kierować bezpośrednio do <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> odpowiednio metody w zależności docelowy obiekt. Projektanci może uzyskać dostępu do dołączona właściwość przez wywoływanie przez otoki metody lub bezpośrednie wywołania docelowy obiekt zależności.  
  
 Aby uzyskać więcej informacji na dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Definiowanie i użycie wspólnych zasobów  
 W tym samym zestawie co aplikacji można uwzględnić formantu, lub można pakietu formantu w oddzielnych zestawu, który może być używana w wielu aplikacji. W większości przypadków informacje omówione w tym temacie dotyczą niezależnie od używanej metody.  Istnieje jednak jeden różnica warto zauważyć.  Po umieszczeniu formantu w tym samym zestawie co aplikacja jest bezpłatne dodać zasoby globalne w pliku App.xaml. Ale nie ma zestawu, który zawiera tylko formanty <xref:System.Windows.Application> obiektu skojarzone z nią, dlatego nie jest dostępna w pliku App.xaml.  
  
 Gdy aplikacja jest szuka zasobu, analizuje trzy poziomy w następującej kolejności:  
  
1.  Poziom elementu.  
  
     System rozpoczyna się od element, do którego odwołuje się do zasobu i wyszukuje zasobów logiczny obiekt nadrzędny itd aż do osiągnięcia elementu głównego.  
  
2.  Na poziomie aplikacji.  
  
     Zasoby zdefiniowane przez <xref:System.Windows.Application> obiektu.  
  
3.  Poziom motywu.  
  
     Poziom motywu słowniki są przechowywane w podfolderze o nazwie motywów.  Pliki w folderze Kompozycje odpowiadają motywów.  Na przykład może być Aero.NormalColor.xaml, Luna.NormalColor.xaml Royale.NormalColor.xaml i tak dalej.  Można również mieć plik o nazwie generic.xaml.  Gdy system wyszukuje zasobów na poziomie kompozycje, najpierw szuka go w pliku specyficznym dla motywu, a następnie szuka go w generic.xaml.  
  
 W przypadku formantu w zestawie, do którego jest oddzielony od aplikacji, możesz umieścić globalne zasobów na poziomie elementu, lub na poziomie motywu. Obie metody mają swoje zalety.  
  
#### <a name="defining-resources-at-the-element-level"></a>Definiowanie zasobów na poziomie elementu  
 Można zdefiniować udostępnionych zasobów na poziomie elementu, tworząc słownik zasobów niestandardowych i scalana słownik zasobów spod kontroli.  Korzystając z tej metody, można nazwę Twojego pliku zasobu, dowolnych znaków który może być w tym samym folderze co formantów. Zasoby na poziomie elementu, można także użyć prostego ciągi jako klucze. Poniższy przykład tworzy <xref:System.Windows.Media.LinearGradientBrush> plik zasobu o nazwie Dictionary1.xaml.  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Po zdefiniowaniu słownika, należy scalić ją z formantu słownika zasobów.  Można to zrobić za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu.  
  
 Poniższy przykład scala słownik zasobów za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Wadą tego podejścia jest to, że <xref:System.Windows.ResourceDictionary> obiekt jest tworzony za każdym razem, można się odwoływać.  Na przykład, jeśli masz 10 niestandardowe kontrolki w bibliotece i scal słowniki zasobów udostępnionych dla każdego formantu przy użyciu języka XAML, możesz utworzyć 10 identyczne <xref:System.Windows.ResourceDictionary> obiektów.  Można tego uniknąć, tworząc statycznej klasy, która scala zasobów w kodzie i zwraca wynikowy <xref:System.Windows.ResourceDictionary>.  
  
 Poniższy przykład tworzy klasę, która zwraca udostępnionej <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Poniższy przykład scala udostępnionych zasobów z zasobami kontrolki niestandardowej w Konstruktorze formantu przed wywołaniem `InitializeComponent`.  Ponieważ `SharedDictionaryManager.SharedDictionary` jest właściwość statyczna <xref:System.Windows.ResourceDictionary> jest tworzony tylko raz. Ponieważ słownik zasobów została scalona przed `InitializeComponent` została wywołana, zasoby są dostępne do formantu w jego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Definiowanie zasobów na poziomie motywu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pozwala utworzyć zasobów dla różnych kompozycji systemu Windows.  Jako autor formantu należy zdefiniować zasobów dla określonych motywu zmienić wygląd formantu, w zależności od tego, jakie motyw jest używany. Na przykład wygląd <xref:System.Windows.Controls.Button> w Windows Classic motywu (motyw domyślny dla systemu Windows 2000) różni się od <xref:System.Windows.Controls.Button> w motywie Luna systemu Windows (motyw domyślny dla systemu Windows XP) ponieważ <xref:System.Windows.Controls.Button> używa innej <xref:System.Windows.Controls.ControlTemplate> dla każdego motywu.  
  
 Zasoby, które są specyficzne dla motywu są przechowywane w słowniku zasobów z określoną nazwą pliku. Te pliki muszą znajdować się w folderze o nazwie `Themes` oznacza to podfolder folderu, który zawiera kontrolki. W poniższej tabeli wymieniono pliki słownika zasobów i motywu, który jest skojarzony z każdego pliku:  
  
|Nazwa pliku słownika zasobów|Kompozycji systemu Windows|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Systemu Windows 9 x / 2000 Szukaj w systemie Windows XP|  
|`Luna.NormalColor.xaml`|Motyw domyślny niebieski w systemie Windows XP|  
|`Luna.Homestead.xaml`|Motyw oliwek w systemie Windows XP|  
|`Luna.Metallic.xaml`|Motyw srebrny w systemie Windows XP|  
|`Royale.NormalColor.xaml`|Motyw domyślny, w systemie Windows XP Media Center Edition|  
|`Aero.NormalColor.xaml`|Motyw domyślny, w systemie Windows Vista|  
  
 Nie trzeba definiować zasobów dla każdego motywu. Jeśli nie zdefiniowano zasobów dla określonych motywu, następnie formant sprawdza `Classic.xaml` dla zasobu. Jeśli zasób nie jest zdefiniowany w pliku, który odpowiada bieżącego motywu lub w `Classic.xaml`, formantu używa zasobów ogólnych, który znajduje się w pliku słownika zasobów o nazwie `generic.xaml`.  `generic.xaml` Plik znajduje się w tym samym folderze co pliki słowników zasobów specyficznych dla motywów. Mimo że `generic.xaml` nie odpowiada do określonych kompozycji systemu Windows, nadal jest słownik poziom motywu.  
  
 [Numericupdown — formant niestandardowy motyw i przykładowe Obsługa automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=160025) zawiera dwa słownikach zasobów `NumericUpDown` kontroli: jedna jest generic.xaml oraz jeden Luna.NormalColor.xaml.  Możesz uruchomić aplikację i przełączać się między motyw srebrny w systemie Windows XP i innym motyw do widocznej różnicy między szablonami dwóch kontroli. (Jeśli korzystasz z systemu Windows Vista, można zmienić Luna.NormalColor.xaml Aero.NormalColor.xaml i przełączać się między dwoma kompozycje, takie jak Windows Classic motyw domyślny dla systemu Windows Vista.)  
  
 Po umieszczeniu <xref:System.Windows.Controls.ControlTemplate> w żadnym z pliki słowników zasobów specyficznych dla motywów, należy utworzyć Konstruktor statyczny dla formantu i wywołanie <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metoda <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definiowanie i odwołuje się do kluczy dla motywu zasobów  
 Podczas definiowania zasobów na poziomie elementu, można przypisać ciągu jako klucza i dostęp do zasobów za pomocą ciągu. Podczas definiowania zasobów na poziomie motywu, należy użyć <xref:System.Windows.ComponentResourceKey> jako klucz.  W poniższym przykładzie zdefiniowano zasób w generic.xaml.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 Poniższy przykład odwołuje się do zasobu, określając <xref:System.Windows.ComponentResourceKey> jako klucz.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Określanie lokalizacji zasobów motywu  
 Aby znaleźć zasoby formantu, hostingu aplikacji musi wiedzieć, że zestaw zawiera zasoby specyficzne dla formantu. Realizacji tego przez dodanie <xref:System.Windows.ThemeInfoAttribute> do zestawu, który zawiera formant. <xref:System.Windows.ThemeInfoAttribute> Ma <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> właściwość, która określa lokalizację zasoby ogólne i <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> właściwość, która określa lokalizację zasobów specyficznych dla motywów.  
  
 W poniższym przykładzie <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> i <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> właściwości <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, aby określić, że zasobów ogólnych i specyficznych dla motywów znajdują się w tym samym zestawie co formantu.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Zobacz też  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Pakowanie URI w WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)
