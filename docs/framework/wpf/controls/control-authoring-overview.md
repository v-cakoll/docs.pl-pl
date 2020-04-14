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
ms.openlocfilehash: 2326520039085beb5f5294e23db67b67f9d7d7da
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243274"
---
# <a name="control-authoring-overview"></a>Omówienie tworzenia formantu

Rozszerzalność modelu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sterowania znacznie zmniejsza potrzebę tworzenia nowego formantu. Jednak w niektórych przypadkach może być nadal konieczne utworzenie formantu niestandardowego. W tym temacie omówiono funkcje, które minimalizują potrzebę tworzenia formantu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]niestandardowego i różnych modeli tworzenia formantów w pliku . W tym temacie pokazano również, jak utworzyć nowy formant.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternatywy dla pisania nowego formantu

Historycznie, jeśli chcesz uzyskać dostosowane środowisko z istniejącego formantu, były ograniczone do zmiany standardowych właściwości formantu, takich jak kolor tła, szerokość obramowania i rozmiar czcionki. Jeśli chcesz rozszerzyć wygląd lub zachowanie formantu poza te wstępnie zdefiniowane parametry, należy utworzyć nowy formant, zwykle dziedzicząc z istniejącego formantu i zastępując metodę odpowiedzialną za rysowanie formantu.  Mimo że nadal jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to opcja, umożliwia dostosowanie istniejących formantów przy użyciu jego modelu zawartości rozszerzonej, stylów, szablonów i wyzwalaczy. Na poniższej liście przedstawiono przykłady, jak te funkcje mogą służyć do tworzenia niestandardowych i spójnych środowisk bez konieczności tworzenia nowego formantu.

- **Bogata zawartość.** Wiele standardowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantów obsługuje bogatą zawartość. Na przykład właściwość zawartości <xref:System.Windows.Controls.Button> jest <xref:System.Object>typu, więc teoretycznie wszystko może <xref:System.Windows.Controls.Button>być wyświetlane na .  Aby przycisk wyświetlał obraz i tekst, można dodać <xref:System.Windows.Controls.TextBlock> obraz <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.StackPanel> a <xref:System.Windows.Controls.ContentControl.Content%2A> i przypisać go do właściwości. Ponieważ formanty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą wyświetlać elementy wizualne i dowolne dane, istnieje mniejsza potrzeba utworzenia nowego formantu lub zmodyfikowania istniejącego formantu w celu obsługi złożonej wizualizacji. Aby uzyskać więcej informacji <xref:System.Windows.Controls.Button> na temat modelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawartości i innych modeli zawartości w obszarze , zobacz [Model zawartości WPF](wpf-content-model.md).

- **Style.** A <xref:System.Windows.Style> jest kolekcją wartości, które reprezentują właściwości formantu. Za pomocą stylów, można utworzyć reprezentację wielokrotnego użycia żądanego wyglądu i zachowania formantu bez pisania nowego formantu. Załóżmy na przykład, że <xref:System.Windows.Controls.TextBlock> chcesz, aby wszystkie formanty miały czerwoną czcionkę Arial o rozmiarze czcionki 14. Można utworzyć styl jako zasób i odpowiednio ustawić odpowiednie właściwości. Następnie <xref:System.Windows.Controls.TextBlock> każdy, który można dodać do aplikacji będzie miał taki sam wygląd.

- **Szablony danych.** A <xref:System.Windows.DataTemplate> umożliwia dostosowanie sposobu wyświetlania danych w formancie. Na przykład <xref:System.Windows.DataTemplate> a może służyć do określenia, jak <xref:System.Windows.Controls.ListBox>dane są wyświetlane w .  Na przykład zobacz [Omówienie tworzenia szablonów danych](../data/data-templating-overview.md).  Oprócz dostosowywania wyglądu danych, <xref:System.Windows.DataTemplate> a może zawierać elementy interfejsu użytkownika, co zapewnia dużą elastyczność w niestandardowych interfejsów użytkownika.  Na przykład za <xref:System.Windows.DataTemplate>pomocą programu , <xref:System.Windows.Controls.ComboBox> można utworzyć pole wyboru, w którym każdy element zawiera pole wyboru.

- **Szablony sterowania.** Wiele formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyciu <xref:System.Windows.Controls.ControlTemplate> do definiowania struktury i wyglądu formantu, który oddziela wygląd formantu od funkcji formantu. Można drastycznie zmienić wygląd formantu, <xref:System.Windows.Controls.ControlTemplate>definiując jego .  Załóżmy na przykład, że chcesz formantu, który wygląda jak światło stopu. Ten formant ma prosty interfejs użytkownika i funkcje.  Formant to trzy okręgi, z których tylko jeden może być podświetlony naraz. Po pewnym refleksji, można <xref:System.Windows.Controls.RadioButton> sobie sprawę, że oferuje funkcjonalność tylko jeden jest wybierany w czasie, ale domyślny wygląd <xref:System.Windows.Controls.RadioButton> nie wygląda jak światła na światłach.  Ponieważ <xref:System.Windows.Controls.RadioButton> używa szablonu formantu do definiowania jego wyglądu, łatwo jest ponownie <xref:System.Windows.Controls.ControlTemplate> zdefiniować, aby dopasować go do wymagań formantu, i użyć przycisków radiowych, aby zrobić stoplight.

  > [!NOTE]
  > Chociaż <xref:System.Windows.Controls.RadioButton> można użyć <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> a nie jest wystarczające w tym przykładzie.  Definiuje <xref:System.Windows.DataTemplate> wygląd zawartości formantu. W przypadku <xref:System.Windows.Controls.RadioButton>, zawartość jest cokolwiek pojawia się po prawej stronie <xref:System.Windows.Controls.RadioButton> okręgu, który wskazuje, czy jest zaznaczona.  W przykładzie światła stopu przycisk radiowy musi być tylko okrągem, który może "zapalić się". Ponieważ wymóg wyglądu dla światła stopu jest tak <xref:System.Windows.Controls.RadioButton>różny niż domyślny <xref:System.Windows.Controls.ControlTemplate>wygląd , konieczne jest ponowne zdefiniowanie .  Ogólnie rzecz <xref:System.Windows.DataTemplate> biorąc a jest używany do definiowania zawartości (lub danych) formantu, a a <xref:System.Windows.Controls.ControlTemplate> służy do definiowania struktury formantu.

- **Wyzwalaczy.** A <xref:System.Windows.Trigger> umożliwia dynamiczną zmianę wyglądu i zachowania formantu bez tworzenia nowego formantu. Załóżmy na przykład, że masz wiele <xref:System.Windows.Controls.ListBox> formantów w aplikacji i chcesz elementy w każdym z nich <xref:System.Windows.Controls.ListBox> być pogrubiony i czerwony, gdy są one zaznaczone. Pierwszym instynktem może być utworzenie klasy, <xref:System.Windows.Controls.ListBox> która dziedziczy <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> i zastępuje metodę zmiany wyglądu wybranego elementu, ale lepszym podejściem <xref:System.Windows.Controls.ListBoxItem> jest dodanie wyzwalacza do stylu a, który zmienia wygląd wybranego elementu. Wyzwalacz umożliwia zmianę wartości właściwości lub podejmowania akcji na podstawie wartości właściwości. An <xref:System.Windows.EventTrigger> umożliwia wykonywanie akcji w przypadku wystąpienia zdarzenia.

Aby uzyskać więcej informacji o stylach, szablonach i wyzwalaczach, zobacz [Stylowanie i tworzenie szablonów](styling-and-templating.md).

Ogólnie rzecz biorąc, jeśli formant odzwierciedla funkcjonalność istniejącego formantu, ale chcesz, aby formant wyglądał inaczej, należy najpierw rozważyć, czy można użyć dowolnej z metod omówionych w tej sekcji, aby zmienić wygląd istniejącego formantu.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modele do tworzenia formantu

Bogaty model zawartości, style, szablony i wyzwalacze minimalizują potrzebę utworzenia nowego formantu. Jeśli jednak konieczne jest utworzenie nowego formantu, ważne jest, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zrozumieć różne modele tworzenia formantu w . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera trzy ogólne modele tworzenia formantu, z których każdy zapewnia inny zestaw funkcji i poziom elastyczności. Klasy podstawowe dla trzech <xref:System.Windows.Controls.UserControl>modeli <xref:System.Windows.Controls.Control>to <xref:System.Windows.FrameworkElement>, i .

### <a name="deriving-from-usercontrol"></a>Wyprowadzenie z usercontrol

Najprostszym sposobem utworzenia formantu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest <xref:System.Windows.Controls.UserControl>wyprowadzenie z pliku . Podczas tworzenia formantu, <xref:System.Windows.Controls.UserControl>który dziedziczy z <xref:System.Windows.Controls.UserControl>, można dodać istniejące składniki do [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], nazwa składników i obsługi zdarzeń odwołania w . Następnie można odwołać się do nazwanych elementów i zdefiniować programy obsługi zdarzeń w kodzie. Ten model rozwoju jest bardzo podobny do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]modelu używanego do tworzenia aplikacji w .

Jeśli został prawidłowo <xref:System.Windows.Controls.UserControl> zbudowany, a może korzystać z zalet bogatej zawartości, stylów i wyzwalaczy. Jeśli jednak formant zostanie <xref:System.Windows.Controls.UserControl>odziedziczony po osobach korzystających z <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ControlTemplate> formantu, nie będzie można użyć ani dostosować jej wyglądu.  Konieczne jest wyprowadzenie <xref:System.Windows.Controls.Control> z klasy lub jednej z <xref:System.Windows.Controls.UserControl>jej klas pochodnych (innych niż ) w celu utworzenia formantu niestandardowego, który obsługuje szablony.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Korzyści wynikające z usercontrol

Należy rozważyć <xref:System.Windows.Controls.UserControl> wyprowadzenie z, jeśli wszystkie z poniższych stosuje się:

- Chcesz utworzyć formant podobnie jak tworzenie aplikacji.

- Formant składa się tylko z istniejących składników.

- Nie musisz obsługiwać skomplikowanych dostosowywania.

### <a name="deriving-from-control"></a>Wyprowadzenie z kontroli

Pochodna z <xref:System.Windows.Controls.Control> klasy jest model używany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] większość istniejących formantów. Podczas tworzenia formantu, który <xref:System.Windows.Controls.Control> dziedziczy z klasy, można zdefiniować jego wygląd przy użyciu szablonów. W ten sposób należy oddzielić logikę operacyjną od reprezentacji wizualnej. Można również zapewnić oddzielenie interfejsu użytkownika i logiki przy użyciu poleceń i powiązań zamiast zdarzeń <xref:System.Windows.Controls.ControlTemplate> i unikanie odwoływania się do elementów w każdym przypadku, gdy jest to możliwe.  Jeśli interfejs użytkownika i logika formantu są prawidłowo oddzielone od produkcji, użytkownik <xref:System.Windows.Controls.ControlTemplate> formantu można ponownie zdefiniować formantu, aby dostosować jego wygląd. Chociaż budowanie <xref:System.Windows.Controls.Control> niestandardowego nie jest <xref:System.Windows.Controls.UserControl>tak proste, jak budowanie, zwyczaj <xref:System.Windows.Controls.Control> zapewnia największą elastyczność.

#### <a name="benefits-of-deriving-from-control"></a>Korzyści wynikające z kontroli

Należy rozważyć <xref:System.Windows.Controls.Control> wyprowadzenie <xref:System.Windows.Controls.UserControl> z zamiast używać klasy, jeśli zastosowanie ma którakolwiek z następujących czynności:

- Chcesz, aby wygląd formantu można <xref:System.Windows.Controls.ControlTemplate>było dostosować za pomocą pliku .

- Chcesz, aby twoja kontrola obsługiwała różne motywy.

### <a name="deriving-from-frameworkelement"></a>Wywodzący się z frameworkelement

Formanty, <xref:System.Windows.Controls.UserControl> które <xref:System.Windows.Controls.Control> wynikają z tworzenia istniejących elementów lub na nich polegają. W wielu scenariuszach jest to akceptowalne rozwiązanie, ponieważ <xref:System.Windows.FrameworkElement> każdy obiekt, który dziedziczy z może być w <xref:System.Windows.Controls.ControlTemplate>. Jednak istnieją chwile, gdy wygląd formantu wymaga więcej niż funkcjonalność kompozycji elementu prostego. W przypadku tych scenariuszy oparcie składnika jest <xref:System.Windows.FrameworkElement> właściwym wyborem.

Istnieją dwie standardowe metody <xref:System.Windows.FrameworkElement>tworzenia składników opartych na: renderowanie bezpośrednie i niestandardowa kompozycja elementu. Renderowanie bezpośrednie obejmuje zastępowanie <xref:System.Windows.UIElement.OnRender%2A> metody <xref:System.Windows.FrameworkElement> i <xref:System.Windows.Media.DrawingContext> dostarczanie operacji, które jawnie definiują wizualizacje składników. Jest to metoda <xref:System.Windows.Controls.Image> używana <xref:System.Windows.Controls.Border>przez i . Kompozycja elementu niestandardowego polega <xref:System.Windows.Media.Visual> na użyciu obiektów typu do tworzenia wyglądu komponentu. Na przykład zobacz [Korzystanie z drawingvisual Objects](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>jest przykładem formantu, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] który używa kompozycji elementu niestandardowego. Możliwe jest również mieszanie renderowania bezpośredniego i niestandardowej kompozycji elementu w tej samej kontroli.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Korzyści wynikające z FrameworkElement

Należy rozważyć <xref:System.Windows.FrameworkElement> wyprowadzenie z, jeśli zastosowanie ma którakolwiek z poniższych następujących właściwości:

- Chcesz mieć dokładną kontrolę nad wyglądem kontroli poza to, co jest dostarczane przez prosty skład elementu.

- Chcesz zdefiniować wygląd formantu, definiując własną logikę renderowania.

- Chcesz skomponować istniejące elementy w nowatorski sposób, który wykracza poza to, co jest możliwe z <xref:System.Windows.Controls.UserControl> i <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Podstawy tworzenia formantu

Jak wspomniano wcześniej, jedną z najpotężniejszych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji jest możliwość wykraczania poza ustawienie podstawowych właściwości formantu, aby zmienić jego wygląd i zachowanie, ale nadal nie trzeba tworzyć kontrolki niestandardowej. Funkcje stylizacji, powiązania danych i wyzwalacza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są możliwe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dzięki systemowi właściwości i systemowi zdarzeń. W poniższych sekcjach opisano niektóre praktyki, które należy stosować, niezależnie od modelu używanego do tworzenia formantu niestandardowego, aby użytkownicy formantu niestandardowego mogli korzystać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tych funkcji tak samo, jak w przypadku formantu dołączonego do .

### <a name="use-dependency-properties"></a>Używanie właściwości zależności

Gdy właściwość jest właściwością zależności, można wykonać następujące czynności:

- Ustaw właściwość w stylu.

- Powiąż właściwość ze źródłem danych.

- Użyj zasobu dynamicznego jako wartości właściwości.

- Animować właściwość.

Jeśli chcesz właściwość formantu do obsługi dowolnej z tych funkcji, należy zaimplementować go jako właściwość zależności. Poniższy przykład definiuje właściwość `Value` zależności o nazwie, wykonując następujące czynności:

- <xref:System.Windows.DependencyProperty> Zdefiniuj `ValueProperty` identyfikator `public` `static` `readonly` o nazwie jako pole.

- Zarejestruj nazwę właściwości w systemie właściwości, wywołując <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aby określić następujące elementy:

  - Nazwa właściwości.

  - Typ właściwości.

  - Typ, który jest właścicielem właściwości.

  - Metadane dla właściwości. Metadane zawierają domyślną wartość właściwości, <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback>a i .

- Zdefiniuj właściwość `Value`otoki CLR o nazwie , która jest tą samą nazwą, która jest używana do rejestrowania właściwości zależności, implementując właściwości `get` i `set` akcesory. Należy `get` pamiętać, `set` że i <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> akcesory tylko wywołać i odpowiednio. Zaleca się, że akcesory właściwości zależności nie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawierają dodatkowej logiki, ponieważ klienci i można pominąć akcesorów i wywołania <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Na przykład gdy właściwość jest powiązana ze źródłem danych, `set` akcesor właściwości nie jest wywoływana.  Zamiast dodawać dodatkową logikę do akcesorów get i set, użyj programu <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>i <xref:System.Windows.PropertyChangedCallback> delegatów, aby odpowiedzieć na lub sprawdzić wartość, gdy się zmieni.  Aby uzyskać więcej informacji na temat tych wywołań zwrotnych, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności](../advanced/dependency-property-callbacks-and-validation.md).

- Zdefiniuj <xref:System.Windows.CoerceValueCallback> `CoerceValue`metodę dla nazwanego . `CoerceValue`zapewnia, `Value` że jest większa `MinValue` lub równa i `MaxValue`mniejsza lub równa .

- Zdefiniuj <xref:System.Windows.PropertyChangedCallback>metodę `OnValueChanged`dla , o nazwie . `OnValueChanged`tworzy <xref:System.Windows.RoutedPropertyChangedEventArgs%601> obiekt i przygotowuje się `ValueChanged` do podniesienia kierowanego zdarzenia. Kierowane zdarzenia są omówione w następnej sekcji.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Aby uzyskać więcej informacji, zobacz [Niestandardowe właściwości zależności](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Korzystanie z kierowanych zdarzeń

Podobnie jak właściwości zależności rozszerzyć pojęcie właściwości CLR z dodatkowych funkcji, kierowane zdarzenia rozszerzyć pojęcie standardowych zdarzeń CLR. Podczas tworzenia nowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu, jest również dobrym rozwiązaniem, aby zaimplementować zdarzenie jako kierowane zdarzenie, ponieważ kierowane zdarzenie obsługuje następujące zachowanie:

- Zdarzenia mogą być obsługiwane na element nadrzędny wielu formantów. Jeśli zdarzenie jest zdarzenie propagacji, pojedynczy element nadrzędny w drzewie elementów można subskrybować zdarzenia. Następnie autorzy aplikacji można użyć jednego programu obsługi, aby odpowiedzieć na zdarzenie wielu formantów. Na przykład jeśli formant jest częścią każdego <xref:System.Windows.Controls.ListBox> elementu w a (ponieważ jest on zawarty w <xref:System.Windows.DataTemplate>), deweloper aplikacji można <xref:System.Windows.Controls.ListBox>zdefiniować program obsługi zdarzeń dla zdarzenia formantu w . Za każdym razem, gdy zdarzenie występuje na dowolnym formancie, program obsługi zdarzeń jest wywoływana.

- Kierowane zdarzenia mogą być <xref:System.Windows.EventSetter>używane w programie , który umożliwia deweloperom aplikacji określenie obsługi zdarzenia w stylu.

- Kierowane zdarzenia mogą być <xref:System.Windows.EventTrigger>używane w programie , który jest [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]przydatny do animowania właściwości za pomocą programu . Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

Poniższy przykład definiuje kierowane zdarzenie, wykonując następujące czynności:

- <xref:System.Windows.RoutedEvent> Zdefiniuj `ValueChangedEvent` identyfikator `public` `static` `readonly` o nazwie jako pole.

- Zarejestruj kierowane zdarzenie, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> wywołując metodę. W przykładzie określono następujące informacje <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>podczas wywołania:

  - Nazwa zdarzenia to `ValueChanged`.

  - Strategia routingu <xref:System.Windows.RoutingStrategy.Bubble>jest , co oznacza, że program obsługi zdarzeń w źródle (obiekt, który wywołuje zdarzenie) jest wywoływana najpierw, a następnie programy obsługi zdarzeń na element nadrzędny źródła są wywoływane po kolei, począwszy od obsługi zdarzeń na najbliższy element nadrzędny.

  - Typ programu obsługi zdarzeń <xref:System.Windows.RoutedPropertyChangedEventHandler%601>jest , <xref:System.Decimal> skonstruowany z typem.

  - Typem właścicielem zdarzenia jest `NumericUpDown`.

- Deklaruj `ValueChanged` zdarzenie publiczne o nazwie i zawiera deklaracje akcesor zdarzeń. Przykład wywołuje <xref:System.Windows.UIElement.AddHandler%2A> w `add` deklaracji akcesora i <xref:System.Windows.UIElement.RemoveHandler%2A> w deklaracji `remove` akcesora do korzystania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług zdarzeń.

- Utwórz chronione, wirtualną metodę o nazwie, `OnValueChanged` która wywołuje `ValueChanged` zdarzenie.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń trasowych](../advanced/routed-events-overview.md) i [tworzenie niestandardowego zdarzenia kierowanego](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Użyj powiązania

Aby oddzielić interfejs użytkownika formantu od jego logiki, należy rozważyć użycie powiązania danych. Jest to szczególnie ważne w przypadku zdefiniowania wyglądu formantu za pomocą pliku <xref:System.Windows.Controls.ControlTemplate>. Podczas korzystania z powiązania danych, może być w stanie wyeliminować potrzebę odwoływania się do określonych części interfejsu użytkownika z kodu. Jest to dobry pomysł, aby uniknąć odwoływania <xref:System.Windows.Controls.ControlTemplate> się do elementów, które <xref:System.Windows.Controls.ControlTemplate> są <xref:System.Windows.Controls.ControlTemplate> w, ponieważ gdy kod odwołuje się do <xref:System.Windows.Controls.ControlTemplate>elementów, które są w i jest zmieniany, element, do którego istnieje odwołanie, musi zostać uwzględniony w nowym .

Poniższy przykład <xref:System.Windows.Controls.TextBlock> aktualizuje `NumericUpDown` formantu, przypisując nazwę do niego i odwołując się do pola tekstowego za pomocą nazwy w kodzie.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

W poniższym przykładzie użyto powiązania, aby osiągnąć to samo.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Projekt dla projektantów

Aby otrzymać obsługę niestandardowych formantów WPF w WPF Designer dla programu Visual Studio (na przykład edycji właściwości z właściwości okna), postępuj zgodnie z tymi wskazówkami.  Aby uzyskać więcej informacji na temat tworzenia dla Projektanta WPF, zobacz [Projektowanie XAML w programie Visual Studio.](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)

#### <a name="dependency-properties"></a>Właściwości zależności

Pamiętaj, aby zaimplementować CLR `get` i `set` akcesory, jak opisano wcześniej, w "Użyj właściwości zależności." Projektanci mogą używać otoki do wykrywania obecności właściwości zależności, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ale oni, jak i klienci formantu, nie są wymagane do wywoływania akcesorów podczas uzyskiwania lub ustawiania właściwości.

#### <a name="attached-properties"></a>Dołączone właściwości

Załączone właściwości należy zaimplementować w formantach niestandardowych przy użyciu następujących wskazówek:

- `public` `Property` <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Mieć formularz *PropertyName,* który został creating przy użyciu metody. `static` `readonly` <xref:System.Windows.DependencyProperty> Nazwa właściwości, która <xref:System.Windows.DependencyProperty.RegisterAttached%2A> jest przekazywana do musi odpowiadać *PropertyName*.

- Zaimplementuj `public` `static` parę `Set`metod CLR o nazwie *PropertyName* i `Get` *PropertyName*. Obie metody powinny akceptować <xref:System.Windows.DependencyProperty> klasę pochodną jako pierwszy argument. `Set` *Właściwość metoda* akceptuje również argument, którego typ pasuje do zarejestrowanego typu danych dla właściwości. `Get` *Właściwość metoda* powinna zwracać wartość tego samego typu. `Set`Jeśli brak metody *PropertyName,* właściwość jest oznaczona jako tylko do odczytu.

- `Set`*PropertyName* `Get`i *PropertyName* musi kierować bezpośrednio do <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> metody na obiekt zależności docelowej, odpowiednio. Projektanci mogą uzyskać dostęp do dołączonej właściwości, wywołując za pośrednictwem otoki metody lub dokonując bezpośredniego wywołania obiektu zależności docelowej.

Aby uzyskać więcej informacji na temat dołączonych właściwości, zobacz [Omówienie załączonych właściwości](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definiowanie i używanie zasobów udostępnionych

Formant można dołączyć do tego samego zestawu co aplikacja lub można spakować formant w oddzielnym zestawie, który może być używany w wielu aplikacjach. W przeważającej części informacje omówione w tym temacie mają zastosowanie niezależnie od używanej metody.  Jest jednak jedna różnica, na którą warto zwrócić uwagę.  Po umieszczeniu formantu w tym samym zestawie co aplikacja, można dodać zasoby globalne do pliku App.xaml. Ale zestaw, który zawiera tylko <xref:System.Windows.Application> formanty nie ma obiektu skojarzonego z nim, więc plik App.xaml nie jest dostępny.

Gdy aplikacja szuka zasobu, patrzy na trzech poziomach w następującej kolejności:

1. Poziom elementu.

   System rozpoczyna się od elementu, który odwołuje się do zasobu, a następnie przeszukuje zasoby logicznego elementu nadrzędnego i tak dalej, aż do osiągnięcia elementu głównego.

2. Poziom aplikacji.

   Zasoby zdefiniowane <xref:System.Windows.Application> przez obiekt.

3. Poziom motywu.

   Słowniki na poziomie motywu są przechowywane w podfolderze o nazwie Motywy.  Pliki w folderze Motywy odpowiadają motywom.  Na przykład może być Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml i tak dalej.  Można również mieć plik o nazwie generic.xaml.  Gdy system szuka zasobu na poziomie motywów, najpierw wyszukuje go w pliku specyficznym dla motywu, a następnie wyszukuje go w pliku generic.xaml.

Gdy formant znajduje się w zestawie, który jest oddzielony od aplikacji, należy umieścić zasoby globalne na poziomie elementu lub na poziomie motywu. Obie metody mają swoje zalety.

#### <a name="defining-resources-at-the-element-level"></a>Definiowanie zasobów na poziomie elementu

Zasoby udostępnione można zdefiniować na poziomie elementu, tworząc niestandardowy słownik zasobów i łącząc go ze słownikiem zasobów formantu.  Korzystając z tej metody, można nazwać plik zasobu, co chcesz, i może być w tym samym folderze, co formanty. Zasoby na poziomie elementu można również użyć prostych ciągów jako klucze. Poniższy przykład <xref:System.Windows.Media.LinearGradientBrush> tworzy plik zasobów o nazwie Dictionary1.xaml.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Po zdefiniowaniu słownika należy scalić go ze słownikiem zasobów formantu.  Można to zrobić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] za pomocą kodu lub kodu.

Poniższy przykład scala słownik zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]przy użyciu programu .

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Wadą tego podejścia jest <xref:System.Windows.ResourceDictionary> to, że obiekt jest tworzony za każdym razem, gdy odwołujesz się do niego.  Na przykład jeśli masz 10 formantów niestandardowych w bibliotece i scalić słowniki zasobów udostępnionych dla każdego formantu przy użyciu XAML, należy utworzyć 10 identycznych <xref:System.Windows.ResourceDictionary> obiektów.  Można tego uniknąć, tworząc klasę statyczną, która scala zasoby w <xref:System.Windows.ResourceDictionary>kodzie i zwraca wynikowy .

Poniższy przykład tworzy klasę, <xref:System.Windows.ResourceDictionary>która zwraca udostępnione .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Poniższy przykład scala zasób udostępniony z zasobami formantu niestandardowego `InitializeComponent`w konstruktorze formantu przed wywołaniem .  Ponieważ `SharedDictionaryManager.SharedDictionary` jest właściwością statyczną, <xref:System.Windows.ResourceDictionary> jest tworzony tylko raz. Ponieważ słownik zasobów został scalony przed `InitializeComponent` wywołano, zasoby są [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dostępne dla formantu w jego pliku.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definiowanie zasobów na poziomie motywu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwia tworzenie zasobów dla różnych motywów systemu Windows.  Jako autor formantu można zdefiniować zasób dla określonego motywu, aby zmienić wygląd formantu w zależności od używanego motywu. Na przykład wygląd kompozycji <xref:System.Windows.Controls.Button> Klasycznej systemu Windows (domyślnej kompozycji dla systemu Windows <xref:System.Windows.Controls.Button> 2000) różni się od motywu w kompozycji Windows Luna (domyślnej kompozycji dla systemu Windows XP), ponieważ <xref:System.Windows.Controls.Button> używa on innego <xref:System.Windows.Controls.ControlTemplate> motywu dla każdego motywu.

Zasoby, które są specyficzne dla motywu są przechowywane w słowniku zasobów o określonej nazwie pliku. Pliki te muszą znajdować `Themes` się w folderze o nazwie, który jest podfolderem folderu zawierającego formant. W poniższej tabeli wymieniono pliki słownika zasobów i motyw skojarzony z każdym plikiem:

|Nazwa pliku słownika zasobów|Kompozycja systemu Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasyczny wygląd systemu Windows 9x/2000 w systemie Windows XP|
|`Luna.NormalColor.xaml`|Domyślna niebieska kompozycja w systemie Windows XP|
|`Luna.Homestead.xaml`|Kompozycja Oliwka w systemie Windows XP|
|`Luna.Metallic.xaml`|Kompozycja Srebro w systemie Windows XP|
|`Royale.NormalColor.xaml`|Domyślny motyw w programie Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Domyślny motyw w systemie Windows Vista|

Nie trzeba definiować zasobu dla każdego motywu. Jeśli zasób nie jest zdefiniowany dla `Classic.xaml` określonego motywu, wówczas formant sprawdza zasób. Jeśli zasób nie jest zdefiniowany w pliku odpowiadającym bieżącemu motywowi lub w `Classic.xaml`, formant używa `generic.xaml`zasobu ogólnego, który znajduje się w pliku słownika zasobów o nazwie .  Plik `generic.xaml` znajduje się w tym samym folderze co pliki słownika zasobów specyficzne dla motywu. Chociaż `generic.xaml` nie odpowiada określonej kompozycji systemu Windows, nadal jest to słownik na poziomie motywu.

Formant niestandardowy [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) lub [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown z przykładem obsługi `NumericUpDown` interfejsu użytkownika i automatyzacji interfejsu użytkownika zawiera dwa słowniki zasobów dla formantu: jeden znajduje się w pliku generic.xaml, a drugi w pliku Luna.NormalColor.xaml.

Po umieszczeniu <xref:System.Windows.Controls.ControlTemplate> w dowolnym pliku słownika zasobów specyficzne dla motywu, należy utworzyć konstruktora statycznego dla formantu i wywołać <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metodę na <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak pokazano w poniższym przykładzie.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definiowanie i odwoływanie się do kluczy zasobów motywu

Podczas definiowania zasobu na poziomie elementu, można przypisać ciąg jako jego klucz i uzyskać dostęp do zasobu za pośrednictwem ciągu. Podczas definiowania zasobu na poziomie motywu, <xref:System.Windows.ComponentResourceKey> należy użyć jako klucza.  Poniższy przykład definiuje zasób w generic.xaml.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Poniższy przykład odwołuje się do <xref:System.Windows.ComponentResourceKey> zasobu, określając jako klucz.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Określanie lokalizacji zasobów motywu

Aby znaleźć zasoby dla formantu, aplikacja hostingu musi wiedzieć, że zestaw zawiera zasoby specyficzne dla kontroli. Można to osiągnąć, <xref:System.Windows.ThemeInfoAttribute> dodając do zestawu, który zawiera formant. Ma <xref:System.Windows.ThemeInfoAttribute> <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> właściwość, która określa lokalizację zasobów ogólnych <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> i właściwość, która określa lokalizację zasobów specyficznych dla motywu.

Poniższy przykład <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ustawia <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> właściwości <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>i , aby określić, że ogólne i specyficzne dla motywu zasoby znajdują się w tym samym zestawie co formant.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Zobacz też

- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Pakuj URI w WPF](../app-development/pack-uris-in-wpf.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
