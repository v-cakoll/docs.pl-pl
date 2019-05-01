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
ms.openlocfilehash: bb35a4d47f583aad710e178bdb12cb9adf6321e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017686"
---
# <a name="control-authoring-overview"></a>Przegląd Autorstwo formantów
Możliwość rozszerzania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] model kontroli znacząco zmniejsza potrzebę tworzenia nowego formantu. Jednak w niektórych przypadkach może być nadal należy utworzyć formant niestandardowy. W tym temacie omówiono funkcje, które zminimalizować potrzebę tworzenia formantu niestandardowego i innej kontrolki tworzenia modeli w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Również w tym temacie pokazano, jak utworzyć nowy formant.  

<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Alternatywy dla zapisywania nowego formantu  
 W przeszłości Jeśli chcesz uzyskać dostosowane środowisko z istniejącej kontrolki ograniczały użytkowników do zmiany standardowe właściwości kontrolki, takie jak kolor tła, szerokość obramowania i rozmiar czcionki. Dalej rozszerzać wygląd i zachowanie kontrolki poza tych wstępnie zdefiniowanych parametrów, należy utworzyć nowy formant, zwykle przez dziedziczenie z istniejącej kontrolki i zastąpienie metody, które są odpowiedzialne za narysowanie formantu.  Mimo że nadal jest opcją, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia użytkownikowi dostosowywanie istniejących kontrolek przy użyciu rozbudowanych model zawartości, style, szablonów i wyzwalacze. Poniższa lista zawiera przykłady, jak te funkcje mogą być używane w taki sposób, aby tworzyć niestandardowe i spójne środowiska bez konieczności tworzenia nowego formantu.  
  
- **Sformatowana zawartość.** Wiele standardowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty obsługują sformatowanej zawartości. Na przykład właściwość content <xref:System.Windows.Controls.Button> typu <xref:System.Object>, więc teoretycznie niczego mogą być wyświetlane na <xref:System.Windows.Controls.Button>.  Aby wyświetlić obraz i tekst przycisku, można dodać obraz i <xref:System.Windows.Controls.TextBlock> do <xref:System.Windows.Controls.StackPanel> i przypisać <xref:System.Windows.Controls.StackPanel> do <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości. Ponieważ formanty można wyświetlić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy wizualne i dowolne dane, jest mniej wymagane, aby utworzyć nową kontrolkę lub zmodyfikować istniejącą kontrolkę do obsługi złożonych wizualizacji. Aby uzyskać więcej informacji na temat modelu zawartości dla <xref:System.Windows.Controls.Button> i innej zawartości modeli w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [Model zawartości WPF](wpf-content-model.md).  
  
- **Style.** A <xref:System.Windows.Style> to zbiór wartości, które reprezentują właściwości formantu. Przy użyciu stylów, można utworzyć wielokrotnego użytku reprezentacja kontroli żądany wygląd i zachowanie, bez konieczności pisania nowego formantu. Załóżmy na przykład chcesz wyświetlić wszystkie swoje <xref:System.Windows.Controls.TextBlock> kontrolki ma czerwony, Arial czcionki o rozmiarze czcionki 14. Można utworzyć styl jako zasób i odpowiednio ustawić odpowiednie właściwości. Następnie każdy <xref:System.Windows.Controls.TextBlock> sytuacja: dodajesz do Twojej aplikacji będą mieć tego samego wygląd.  
  
- **Szablony danych.** A <xref:System.Windows.DataTemplate> pozwala dostosować sposób wyświetlania danych w formancie. Na przykład <xref:System.Windows.DataTemplate> może służyć do określenia, jak dane są wyświetlane w <xref:System.Windows.Controls.ListBox>.  Aby na przykład, zobacz [Przegląd Szablonowanie danych](../data/data-templating-overview.md).  Oprócz Dostosowywanie wyglądu danych <xref:System.Windows.DataTemplate> może zawierać elementy interfejsu użytkownika, który zapewnia dużą elastyczność w niestandardowych interfejsów użytkownika.  Na przykład za pomocą <xref:System.Windows.DataTemplate>, możesz utworzyć <xref:System.Windows.Controls.ComboBox> , w której każdy element zawiera pole wyboru.  
  
- **Szablony kontrolek.** Wiele kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyj <xref:System.Windows.Controls.ControlTemplate> do zdefiniowania kontrolki struktury i wygląd, który oddziela wyglądu formantu z funkcji kontroli. Znacznie można zmienić wygląd kontrolki poprzez zmianę definicji jego <xref:System.Windows.Controls.ControlTemplate>.  Na przykład załóżmy, że chcesz, aby formant, który wygląda jak sygnalizatora. Ten formant ma prosty interfejs użytkownika i funkcje.  Kontrolka jest trzy koła, tylko jeden z nich może być włączone w danym momencie. Po niektórych odbicie, należy być może należy pamiętać, że <xref:System.Windows.Controls.RadioButton> oferuje funkcje tylko jeden zaznaczony w danym momencie, ale domyślny wygląd <xref:System.Windows.Controls.RadioButton> nothing wygląda światła na sygnalizatora.  Ponieważ <xref:System.Windows.Controls.RadioButton> używa szablonu kontrolki do definiowania jego wygląd można łatwo zmienić definicję <xref:System.Windows.Controls.ControlTemplate> zgodnie z wymaganiami, kontrolki i używaj przycisków radiowych umożliwia Twojej sygnalizatora.  
  
    > [!NOTE]
    >  Mimo że <xref:System.Windows.Controls.RadioButton> służy <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> nie wystarcza, w tym przykładzie.  <xref:System.Windows.DataTemplate> Definiuje wygląd elementów zawartości formantu. W przypadku właściwości <xref:System.Windows.Controls.RadioButton>, zawartość jest, niezależnie od rodzaju pojawia się po prawej stronie koła, która wskazuje, czy <xref:System.Windows.Controls.RadioButton> jest zaznaczone.  W przykładzie sygnalizatora przycisku radiowego musi mieć po prostu być circle, który może "dostarczone." Ponieważ wygląd potrzebę sygnalizatora jest więc inny niż domyślny wygląd <xref:System.Windows.Controls.RadioButton>, należy go ponownie zdefiniować <xref:System.Windows.Controls.ControlTemplate>.  Ogólnie rzecz biorąc <xref:System.Windows.DataTemplate> służy do definiowania zawartości lub danych kontrolkę i a <xref:System.Windows.Controls.ControlTemplate> służy do definiowania struktury formantu.  
  
- **Wyzwalacze.** A <xref:System.Windows.Trigger> dynamicznie zmieniać wygląd i zachowanie kontrolki bez tworzenia nowego formantu. Załóżmy na przykład, posiadasz wiele <xref:System.Windows.Controls.ListBox> formantów w aplikacji i elementy w każdym <xref:System.Windows.Controls.ListBox> jest pogrubiony i czerwony, gdy są zaznaczone. Twoje pierwsze instinct może być utworzyć klasę, która dziedziczy po elemencie <xref:System.Windows.Controls.ListBox> i zastąpić <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metodę, aby zmienić wygląd wybranego elementu, ale lepszym rozwiązaniem jest dodanie wyzwalacza do styl <xref:System.Windows.Controls.ListBoxItem> zmienia się wygląd wybrany element. Wyzwalacz umożliwia zmianę wartości właściwości lub podjąć działania w oparciu o wartość właściwości. <xref:System.Windows.EventTrigger> Umożliwia akcje, kiedy wystąpi zdarzenie.  
  
 Aby uzyskać więcej informacji na temat style, szablonów i wyzwalaczy, zobacz [Tworzenie szablonów i stylów](styling-and-templating.md).  
  
 Ogólnie rzecz biorąc Jeśli formant odzwierciedla funkcjonalność istniejącej kontrolki, ale formant będzie wyglądać inaczej, najpierw rozważ, czy można użyć dowolnej z metod opisanych w tej sekcji w celu zmiany wyglądu istniejącej kontrolki.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Modele do tworzenia kontrolki  
 Rozbudowane model zawartości, style, szablonów i wyzwalacze zminimalizować zapotrzebowanie na tworzenie nowego formantu. Jednakże jeśli musisz utworzyć nowy formant, ważne jest zrozumienie innej kontrolki tworzenia modeli w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia trzy modele ogólne do tworzenia kontrolek, z których każdy zawiera inny zestaw funkcji i stopień elastyczności. Podstawowej klasy są trzy modele <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, i <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>Wyprowadzanie z elementu UserControl  
 Najprostszym sposobem utworzenia formantu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest pochodną <xref:System.Windows.Controls.UserControl>. Podczas kompilowania formantu dziedziczy <xref:System.Windows.Controls.UserControl>, Dodaj istniejące składniki do <xref:System.Windows.Controls.UserControl>nazwy składników i odwoływać się do obsługi zdarzeń w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Następnie można odwoływać się do nazwanych elementów i definiowanie procedury obsługi zdarzeń w kodzie. Ten model programowania jest bardzo podobny do modelu używany do programowania aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Jeśli skompilowany poprawnie, <xref:System.Windows.Controls.UserControl> mogą korzystać z zalet sformatowanej zawartości, style i wyzwalacze. Jednakże jeśli formant dziedziczy z <xref:System.Windows.Controls.UserControl>, osób, które używają formantu nie będzie można użyć <xref:System.Windows.DataTemplate> lub <xref:System.Windows.Controls.ControlTemplate> do dostosowania jego wyglądu.  Zachodzi konieczność dziedziczyć <xref:System.Windows.Controls.Control> klasy lub jednej z jej klas pochodnych (inne niż <xref:System.Windows.Controls.UserControl>) można utworzyć kontrolki niestandardowej, która obsługuje szablony.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>Korzyści wynikające z elementu UserControl  
 Należy wziąć pod uwagę pochodząca od <xref:System.Windows.Controls.UserControl> wszystkie następujące zastosowania:  
  
- Chcesz skompilować Twoją kontrolą, podobnie jak sposób kompilowania aplikacji.  
  
- Formant składa się tylko z istniejących składników.  
  
- Nie potrzebujesz do obsługi złożonych dostosowań.  
  
### <a name="deriving-from-control"></a>Wyprowadzanie z formantu  
 Wyprowadzanie z <xref:System.Windows.Controls.Control> klasa jest model wykorzystywany przez większość istniejących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki. Podczas tworzenia kontrolki dziedziczy <xref:System.Windows.Controls.Control> klasy, należy zdefiniować wygląd przy użyciu szablonów. W ten sposób można oddzielić logikę operacyjne od wizualnej reprezentacji. Można także zapewnić oddzielenie interfejsu użytkownika i logiki przy użyciu poleceń i powiązań zamiast zdarzenia i unikanie odwołujący się elementów w <xref:System.Windows.Controls.ControlTemplate> zawsze, gdy jest to możliwe.  Jeśli interfejs użytkownika i logikę kontrolki są prawidłowo odłączony, kontrolki użytkownika można ponownie zdefiniować formantu <xref:System.Windows.Controls.ControlTemplate> do dostosowania jego wyglądu. Chociaż tworzenie niestandardowego <xref:System.Windows.Controls.Control> nie jest tak proste, jak tworzenie <xref:System.Windows.Controls.UserControl>, niestandardowe <xref:System.Windows.Controls.Control> zapewnia większą elastyczność.  
  
#### <a name="benefits-of-deriving-from-control"></a>Korzyści wynikające z formantu  
 Należy wziąć pod uwagę pochodząca od <xref:System.Windows.Controls.Control> zamiast <xref:System.Windows.Controls.UserControl> klasy, jeśli dowolny z następujących warunków:  
  
- Należy zdefiniować wygląd kontrolki dawać możliwość dostosowania za pośrednictwem <xref:System.Windows.Controls.ControlTemplate>.  
  
- Chcesz, aby Twoją kontrolą w celu obsługi różnych kompozycji.  
  
### <a name="deriving-from-frameworkelement"></a>Wyprowadzanie z elementu FrameworkElement  
 Formanty, które wynikają z <xref:System.Windows.Controls.UserControl> lub <xref:System.Windows.Controls.Control> opierają się na tworzenie istniejące elementy. W wielu sytuacjach jest to dopuszczalne rozwiązanie, ponieważ każdy obiekt, który dziedziczy z <xref:System.Windows.FrameworkElement> mogą znajdować się w <xref:System.Windows.Controls.ControlTemplate>. Istnieją jednak czasy, kiedy wygląd formantu wymaga więcej niż funkcje kompozycji prosty element. W tych scenariuszach bazowanie składnika na <xref:System.Windows.FrameworkElement> jest najlepszym wyborem.  
  
 Istnieją dwie metody standardowego do kompilowania <xref:System.Windows.FrameworkElement>— na podstawie składników: bezpośrednie renderowanie i niestandardowych kompozycji elementu. Bezpośrednie renderowania obejmuje zastępowanie <xref:System.Windows.UIElement.OnRender%2A> metody <xref:System.Windows.FrameworkElement> i zapewniając <xref:System.Windows.Media.DrawingContext> operacje, które jawnie zdefiniować wizualizacji składnika. Jest to metoda posługują się <xref:System.Windows.Controls.Image> i <xref:System.Windows.Controls.Border>. Element niestandardowy kompozycji pociąga za sobą przy użyciu obiektów typu <xref:System.Windows.Media.Visual> do redagowania wygląd danego składnika. Aby uzyskać przykład, zobacz [przy użyciu obiektów DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> Oto przykład kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kompozycji elementu niestandardowego, który używa. Istnieje również możliwość mieszać bezpośrednie renderowania i niestandardowego elementu złożenia w tej samej kontrolki.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>Korzyści wynikające z elementu FrameworkElement  
 Należy wziąć pod uwagę pochodząca od <xref:System.Windows.FrameworkElement> Jeśli dowolny z następujących warunków:  
  
- Chcesz mieć ścisłą kontrolę nad wyglądu kontrolki poza dostarczanych przez prosty element kompozycji.  
  
- Należy zdefiniować wygląd kontrolki, definiując logikę renderowania.  
  
- Chcesz na nowe sposoby, wykraczający poza to, co można zrobić za pomocą narzędzia compose istniejące elementy <xref:System.Windows.Controls.UserControl> i <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Podstawowe informacje dotyczące tworzenia kontrolki  
 Jak już wspomniano, jedną z najbardziej zaawansowanych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest możliwość wykracza poza podstawowe właściwości formantu, aby zmienić wygląd i zachowanie, ale nadal nie musi utworzyć formant niestandardowy. Stylów, powiązań danych i funkcji wyzwalacza są możliwe, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system właściwości i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń. W poniższych sekcjach opisano niektóre rozwiązania, które należy wykonać, niezależnie od tego modelu służy do tworzenia kontrolki niestandardowej, dzięki czemu użytkownicy niestandardową kontrolkę mogą używać tych funkcji, tak samo, jak dla formantu, który jest dołączony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Użyj właściwości zależności  
 Gdy właściwość jest właściwością zależności, możliwe jest wykonanie następujących czynności:  
  
- Ustaw właściwość w stylu.  
  
- Powiąż właściwości ze źródłem danych.  
  
- Użyj dynamicznych zasobów jako wartość właściwości.  
  
- Animowanie właściwości.  
  
 Jeśli chcesz, aby właściwość Twoją kontrolą w celu zapewnienia obsługi tej funkcji, należy zaimplementować go jako właściwość zależności. W poniższym przykładzie zdefiniowano właściwość zależności, o nazwie `Value` , wykonując następujące czynności:  
  
- Zdefiniuj <xref:System.Windows.DependencyProperty> identyfikatora o nazwie `ValueProperty` jako `public` `static` `readonly` pola.  
  
- Zarejestruj nazwy właściwości w systemie właściwości przez wywołanie metody <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aby określić następujące czynności:  
  
    - Nazwa właściwości.  
  
    - Typ właściwości.  
  
    - Typ, który jest właścicielem właściwości.  
  
    - Metadane dla właściwości. Metadane zawierają wartość domyślną właściwości <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>.  
  
- Zdefiniuj [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwość o nazwie `Value`, który ma taką samą nazwę, które jest używane do rejestrowania właściwości zależności poprzez implementację właściwości `get` i `set` metod dostępu. Należy pamiętać, że `get` i `set` wywoływać tylko metody dostępu <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> odpowiednio. Zalecane jest, że metody dostępu właściwości zależności nie zawierają dodatkowej logiki, ponieważ klienci i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można pominąć metody dostępu i wywołania <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Na przykład, gdy właściwość jest powiązana z danych źródłowych, właściwości `set` dostępu nie zostanie wywołana.  Zamiast opcji dodawania dodatkową logikę do pobierania i ustaw metody dostępu, użyj <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, i <xref:System.Windows.PropertyChangedCallback> delegatów odpowiadanie na lub sprawdź wartość, gdy zmienia się.  Aby uzyskać więcej informacji na temat tych wywołań zwrotnych, zobacz [zależność wartości wywołania zwrotnego i walidacji](../advanced/dependency-property-callbacks-and-validation.md).  
  
- Zdefiniuj metodę <xref:System.Windows.CoerceValueCallback> o nazwie `CoerceValue`. `CoerceValue` zapewnia, że `Value` jest większa lub równa `MinValue` i mniejsza niż lub równa `MaxValue`.  
  
- Zdefiniuj metodę <xref:System.Windows.PropertyChangedCallback>o nazwie `OnValueChanged`. `OnValueChanged` Tworzy <xref:System.Windows.RoutedPropertyChangedEventArgs%601> obiektu i przygotowuje podnieść `ValueChanged` zdarzenia trasowanego. Zdarzenia trasowane zostały omówione w następnej sekcji.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](../advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Użyj zdarzenia trasowanego  
 Podobnie jak zależności właściwości rozszerzają pojęcie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości z dodatkowymi funkcjami, zdarzenia trasowane rozszerzają pojęcie standard [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. Podczas tworzenia nowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki, jest również dobrym rozwiązaniem do zaimplementowania zdarzenia jako zdarzenia trasowane, ponieważ zdarzenia trasowanego obsługuje następujące zachowanie:  
  
- Zdarzenia mogą być obsługiwane na element nadrzędny wielu kontrolek. Jeśli zdarzenie jest propagacja zdarzeń, jednego nadrzędnego w drzewie elementów mogą subskrybować zdarzenia. Następnie autorzy aplikacji można użyć jednego programu obsługi w celu zareagowania na zdarzenie wielu kontrolek. Na przykład, jeśli formant jest częścią każdego elementu w <xref:System.Windows.Controls.ListBox> (ponieważ jest on uwzględniony w <xref:System.Windows.DataTemplate>), Deweloper aplikacji można zdefiniować program obsługi zdarzeń dla zdarzenia kontroli nad <xref:System.Windows.Controls.ListBox>. Zawsze, gdy wystąpi zdarzenie na wszystkich formantów, nosi nazwę programu obsługi zdarzeń.  
  
- Zdarzenia trasowane mogą być używane w <xref:System.Windows.EventSetter>, które umożliwia deweloperom aplikacji określenie program obsługi zdarzenia w stylu.  
  
- Zdarzenia trasowane mogą być używane w <xref:System.Windows.EventTrigger>, która jest przydatne w przypadku animowanie właściwości przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
 W poniższym przykładzie zdefiniowano zdarzenia trasowanego, wykonując następujące czynności:  
  
- Zdefiniuj <xref:System.Windows.RoutedEvent> identyfikatora o nazwie `ValueChangedEvent` jako `public` `static` `readonly` pola.  
  
- Rejestrowanie zdarzeń trasowanych przez wywołanie metody <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> metody. W przykładzie określono następujące informacje, kiedy wywołuje <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    - Nazwa zdarzenia jest `ValueChanged`.  
  
    - Strategia routingu jest <xref:System.Windows.RoutingStrategy.Bubble>, co oznacza, że program obsługi zdarzeń w źródle (obiekt, który wywołuje zdarzenie) jest wywoływana najpierw, a następnie procedury obsługi zdarzeń na elementy nadrzędne źródło są nazywane kolejno, począwszy od programu obsługi zdarzeń na najbliższą element nadrzędny.  
  
    - Typem obsługi zdarzeń jest <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, zbudowany z <xref:System.Decimal> typu.  
  
    - Jest właścicielem typ zdarzenia `NumericUpDown`.  
  
- Zadeklaruj zdarzenie publiczne o nazwie `ValueChanged` i zawiera deklaracjach metod dostępu zdarzeń. Przykład wywołuje <xref:System.Windows.UIElement.AddHandler%2A> w `add` deklaracji metody dostępu i <xref:System.Windows.UIElement.RemoveHandler%2A> w `remove` deklaracji metody dostępu do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń usług.  
  
- Utwórz metodę chroniony, wirtualny o nazwie `OnValueChanged` która zgłasza `ValueChanged` zdarzeń.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń kierowane](../advanced/routed-events-overview.md) i [Utwórz niestandardowe zdarzenie kierowane](../advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Użyj powiązań  
 Oddzielenie interfejsu użytkownika formantu od jej logiki, należy wziąć pod uwagę przy użyciu powiązania danych. Jest to szczególnie ważne w przypadku określenia jej wyglądu formantu za pomocą <xref:System.Windows.Controls.ControlTemplate>. Gdy używasz wiązania danych, może być wyeliminować potrzebę odwoływać się do określonych części interfejsu użytkownika z kodu. To dobry pomysł, aby unikać odwoływania się do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> ponieważ gdy kod odwołuje się do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.ControlTemplate> ulegnie zmianie, potrzeb odnośny element do uwzględnienia w nowym <xref:System.Windows.Controls.ControlTemplate>.  
  
 Następujące aktualizacje przykład <xref:System.Windows.Controls.TextBlock> z `NumericUpDown` kontroli, przypisanie nazwy do niego odwołuje się do pola tekstowego według nazwy w kodzie.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 W poniższym przykładzie użyto powiązania, aby osiągnąć ten sam efekt.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Data Binding Overview](../data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Projektowanie pod kątem projektantów  
 Aby uzyskać pomoc techniczną w przypadku kontrolek niestandardowych WPF w [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (na przykład właściwość edytowaniu w programie w oknie dialogowym Właściwości), należy przestrzegać następujących wytycznych.  Aby uzyskać więcej informacji na temat tworzenia dla [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], zobacz [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
#### <a name="dependency-properties"></a>Właściwości zależności  
 Pamiętaj zaimplementować [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` i `set` metod dostępu w sposób opisany w "Zależności Użyj właściwości". Projektanci mogą używać otoki do wykrycia obecności właściwości zależności, ale, takie jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i klientów kontrolki, nie są wymagane do wywołania metody dostępu podczas uzyskiwania lub ustawiania właściwości.  
  
#### <a name="attached-properties"></a>Dołączone właściwości  
 Należy zaimplementować dołączone właściwości kontrolek niestandardowych, korzystając z następujących wskazówek:  
  
- Masz `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formularza *PropertyName* `Property` , tworzenia przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Nazwa właściwości, który jest przekazywany do <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musi odpowiadać *PropertyName*.  
  
- Implementowanie parę `public` `static` CLR metody o nazwie `Set` *PropertyName* i `Get` *PropertyName*. Obie metody powinna obsługiwać klasę pochodną <xref:System.Windows.DependencyProperty> jako swojego pierwszego argumentu. `Set` *PropertyName* metoda akceptuje także argumentem, którego typ jest zgodny z typem danych zarejestrowanych dla właściwości. `Get` *PropertyName* metoda powinna zwrócić wartość tego samego typu. Jeśli `Set` *PropertyName* Brak metoda, właściwość jest oznaczona jako tylko do odczytu.  
  
- `Set` *PropertyName* i `Get` *PropertyName* musi kierować bezpośrednio do <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> metod w zależności docelowego obiektu odpowiednio. Projektanci mogą uzyskiwać dostęp do dołączona właściwość wywoływania przez otoki metody lub wybierając bezpośrednie wywołanie do obiektu docelowego zależności.  
  
 Aby uzyskać więcej informacji na temat dołączone właściwości, zobacz [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Definiowanie i korzystanie z zasobów udostępnionych  
 Może zawierać kontrolki z tego samego zestawu aplikacji, lub można spakować formantu w osobnym zestawie, który może być używany w wielu aplikacjach. W większości przypadków informacje omówione w tym temacie mają zastosowanie niezależnie od używanej metody.  Istnieje jednak jeden różnica warte odnotowania.  Po umieszczeniu formantu z tego samego zestawu jako aplikacja jest bezpłatna dodać zasoby globalne do pliku App.xaml. Jednak zestaw, który zawiera tylko formanty nie <xref:System.Windows.Application> obiekt skojarzony z nim, dlatego nie jest plik App.xaml.  
  
 Jeśli aplikacja wygląda dla zasobu, wygląda na trzech poziomach w następującej kolejności:  
  
1. Poziom elementu.  
  
     System rozpoczyna się od elementu, który odwołuje się do zasobu i wyszukuje zasoby logiczne nadrzędnego itd aż do osiągnięcia elementu głównego.  
  
2. Na poziomie aplikacji.  
  
     Zasoby zdefiniowane przez <xref:System.Windows.Application> obiektu.  
  
3. Poziom motywu.  
  
     Motyw poziomie słowniki są przechowywane w podfolderze o nazwie motywów.  Pliki w folderze motywów odpowiadają motywów.  Na przykład Niewykluczone, że Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml i tak dalej.  Może również mieć plik o nazwie klasie generic.xaml.  Gdy system wyszukuje zasobów na poziomie motywy, najpierw szuka go w pliku specyficznych dla motywów, a następnie szuka go w klasie generic.xaml.  
  
 Jeśli formant znajduje się w zestawie, do którego jest wykonywane niezależnie od aplikacji, możesz umieścić swoje zasoby globalne na poziomie elementu, lub na poziomie motywu. Obie metody mają swoje zalety.  
  
#### <a name="defining-resources-at-the-element-level"></a>Definiowanie zasobów na poziomie elementu  
 Udostępnione zasoby na poziomie elementu, można zdefiniować, tworząc słownika zasobów niestandardowych i scalając kontroli nad słownika zasobów.  Przy użyciu tej metody możesz nazwać Twojego pliku zasobu, dowolnych znaków i może być w tym samym folderze co kontrolki. Zasoby na poziomie elementu, można również użyć zwykłe ciągi jako klucze. Poniższy przykład tworzy <xref:System.Windows.Media.LinearGradientBrush> plik zasobów o nazwie Dictionary1.xaml.  
  
 [!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Po zdefiniowaniu słownika, musisz scalić je z kontroli nad słownika zasobów.  Można to zrobić za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu.  
  
 Poniższy przykład scala słownika zasobów za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Wadą tego podejścia jest to, że <xref:System.Windows.ResourceDictionary> obiekt jest tworzony za każdym razem, możesz odwoływać się do niego.  Na przykład, jeśli masz 10 niestandardowe formanty w bibliotece i scalić słowniki zasobów udostępnionych, dla każdego formantu przy użyciu XAML, możesz utworzyć 10 identyczne <xref:System.Windows.ResourceDictionary> obiektów.  Można tego uniknąć, tworząc klasy statycznej, scala zasoby w kodzie i zwraca wynikowy <xref:System.Windows.ResourceDictionary>.  
  
 Poniższy przykład tworzy klasę, która zwraca wspólny <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Poniższy przykład scala zasobu udostępnionego z zasobami kontrolki niestandardowej w Konstruktorze kontrolki przed wywołaniem `InitializeComponent`.  Ponieważ `SharedDictionaryManager.SharedDictionary` jest właściwość statyczna <xref:System.Windows.ResourceDictionary> jest tworzony tylko jeden raz. Ponieważ słownik zasobów została scalona przed `InitializeComponent` została wywołana, zasoby są dostępne do formantu w jego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.  
  
 [!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Definiowanie zasobów na poziomie motywu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia tworzenie zasobów dla różnych motywy Windows.  Jako autor kontrolki można zdefiniować zasób dla określonych motyw Zmienianie wyglądu formantu w zależności od tego, jakie motyw jest używany. Na przykład wygląd <xref:System.Windows.Controls.Button> w klasycznym Windows motywu (motyw domyślny dla Windows 2000) różni się od <xref:System.Windows.Controls.Button> w motywie Windows Luna (motyw domyślny dla Windows XP) ponieważ <xref:System.Windows.Controls.Button> używa innego <xref:System.Windows.Controls.ControlTemplate> dla każdego motywu.  
  
 Zasoby, które są specyficzne dla motywu są przechowywane w słowniku zasobów z określoną nazwą pliku. Te pliki muszą znajdować się w folderze o nazwie `Themes` oznacza to podfolder folderu, który zawiera formant. W poniższej tabeli wymieniono pliki słownika zasobów i motyw, który jest skojarzony z każdego pliku:  
  
|Nazwa pliku słownika zasobów|Motyw Windows|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Klasyczne Windows 9 x / 2000 Szukaj w Windows XP|  
|`Luna.NormalColor.xaml`|Motyw domyślny, niebieski w systemie Windows XP|  
|`Luna.Homestead.xaml`|Motyw oliwek w systemie Windows XP|  
|`Luna.Metallic.xaml`|Motyw Silver w systemie Windows XP|  
|`Royale.NormalColor.xaml`|Motyw domyślny na Windows XP Media Center Edition|  
|`Aero.NormalColor.xaml`|Motyw domyślny w systemie Windows Vista|  
  
 Nie trzeba zdefiniować zasób dla każdej kompozycji. Jeśli zasób nie został zdefiniowany dla określonych motywu, formant sprawdzi `Classic.xaml` dla zasobu. Jeśli zasób nie został zdefiniowany w pliku, który odpowiada bieżącej kompozycji lub w `Classic.xaml`, kontrolka używa zasobów ogólnych, który znajduje się w pliku słownika zasobów o nazwie `generic.xaml`.  `generic.xaml` Plik znajduje się w tym samym folderze co pliki słowników zasobów specyficznych dla motywów. Mimo że `generic.xaml` nie odnoszą się do określonych motywu Windows, nadal jest słownik poziom motywu.  
  
 [Numericupdown — formant niestandardowy motyw i przykładowe Obsługa automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=160025) zawiera dwa słownikach zasobów `NumericUpDown` kontroli: jeden znajduje się w klasie generic.xaml oraz jeden Luna.NormalColor.xaml.  Można uruchomić aplikację i przełączać się między Silver motywu, Windows XP i innego motywu różnice między szablonami dwie kontrolki. (Jeśli korzystasz z Windows Vista, można zmienić Luna.NormalColor.xaml Aero.NormalColor.xaml i przełączać się między dwoma motywy, takich jak Windows Classic i motyw domyślny system Windows Vista.)  
  
 Po umieszczeniu <xref:System.Windows.Controls.ControlTemplate> we wszystkich plików słowników zasobów specyficznych dla motywów, należy utworzyć Konstruktor statyczny dla formantu i wywołaniu <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metody <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definiowanie i odwołania do kluczy dla motywu zasobów  
 Podczas definiowania zasobów na poziomie elementu, można przypisać ciąg jako klucz, a dostęp do zasobów za pomocą ciągu. Gdy zdefiniujesz zasób na poziomie motywu, należy użyć <xref:System.Windows.ComponentResourceKey> jako klucz.  W poniższym przykładzie zdefiniowano zasób w klasie generic.xaml.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 Poniższy przykład odwołuje się do zasobu, określając <xref:System.Windows.ComponentResourceKey> jako klucz.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Określanie lokalizacji zasobów motywu  
 Aby znaleźć zasoby dla formantu, hostingu aplikacji musi wiedzieć, czy zestaw zawiera zasoby specyficzne dla formantu. Można osiągnąć, dodając <xref:System.Windows.ThemeInfoAttribute> do zestawu, który zawiera formant. <xref:System.Windows.ThemeInfoAttribute> Ma <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> właściwość, która określa lokalizację zasoby ogólne i <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> właściwość, która określa lokalizację zasoby specyficzne dla motywu.  
  
 Poniższy przykład ustawia <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> i <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> właściwości <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, aby określić, czy z tego samego zestawu jako formant zasobów ogólnych i specyficznych dla motywów.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Pakowanie URI w WPF](../app-development/pack-uris-in-wpf.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
