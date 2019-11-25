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
ms.openlocfilehash: 1ac8964f915206205d5c9e6ab782fcaa59bf2a99
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975720"
---
# <a name="control-authoring-overview"></a>Przegląd Autorstwo formantów

Rozszerzalność modelu sterowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] znacznie zmniejsza konieczność utworzenia nowej kontrolki. Jednak w niektórych przypadkach nadal może być konieczne utworzenie kontrolki niestandardowej. W tym temacie omówiono funkcje, które minimalizują potrzebę tworzenia kontrolek niestandardowych i różnych modeli tworzenia formantów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. W tym temacie pokazano również, jak utworzyć nową kontrolkę.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternatywy do napisania nowej kontrolki

Historycznie, jeśli chcesz uzyskać dostosowane środowisko z istniejącej kontrolki, możesz zmienić standardowe właściwości kontrolki, takie jak kolor tła, Szerokość obramowania i rozmiar czcionki. Jeśli chcesz zwiększyć wygląd lub zachowanie kontrolki poza tymi wstępnie zdefiniowanymi parametrami, musisz utworzyć nową kontrolkę, zazwyczaj przez dziedziczenie z istniejącej kontrolki i zastępowanie metody odpowiedzialnej za rysowanie formantu.  Mimo że nadal jest to opcja, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia dostosowanie istniejących kontrolek przy użyciu rozbudowanego modelu zawartości, stylów, szablonów i wyzwalaczy. Poniższa lista zawiera przykłady zastosowania tych funkcji do tworzenia niestandardowych i spójnych środowisk bez konieczności tworzenia nowej kontrolki.

- **Zawartość rozbudowana.** Wiele standardowych formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje rozbudowaną zawartość. Na przykład właściwość content <xref:System.Windows.Controls.Button> jest typu <xref:System.Object>, dlatego teoretycznie wszystko można wyświetlić w <xref:System.Windows.Controls.Button>.  Aby przycisk wyświetlał obraz i tekst, można dodać obraz i <xref:System.Windows.Controls.TextBlock> do <xref:System.Windows.Controls.StackPanel> i przypisać <xref:System.Windows.Controls.StackPanel> do właściwości <xref:System.Windows.Controls.ContentControl.Content%2A>. Ponieważ kontrolki mogą wyświetlać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy wizualne i dowolne dane, istnieje mniej potrzeba utworzenia nowej kontrolki lub zmodyfikowania istniejącej kontrolki do obsługi złożonej wizualizacji. Aby uzyskać więcej informacji na temat modelu zawartości dla <xref:System.Windows.Controls.Button> i innych modeli zawartości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz artykuł [model zawartości WPF](wpf-content-model.md).

- **Style.** <xref:System.Windows.Style> to zbiór wartości, które reprezentują właściwości kontrolki. Za pomocą stylów można utworzyć reprezentację do wielokrotnego użytku dla żądanego wyglądu i zachowania kontrolki bez konieczności pisania nowej kontrolki. Załóżmy na przykład, że chcesz, aby wszystkie kontrolki <xref:System.Windows.Controls.TextBlock> miały czcionkę Red, Arial o rozmiarze 14. Styl można utworzyć jako zasób i odpowiednio ustawić odpowiednie właściwości. Następnie każdy <xref:System.Windows.Controls.TextBlock> dodawany do aplikacji będzie miał ten sam wygląd.

- **Szablony danych.** <xref:System.Windows.DataTemplate> pozwala dostosować sposób wyświetlania danych w formancie. Na przykład <xref:System.Windows.DataTemplate> może służyć do określenia sposobu wyświetlania danych w <xref:System.Windows.Controls.ListBox>.  Aby zapoznać się z przykładem, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).  Oprócz dostosowywania wyglądu danych <xref:System.Windows.DataTemplate> mogą zawierać elementy interfejsu użytkownika, co zapewnia dużą elastyczność interfejsów użytkownika niestandardowych.  Na przykład przy użyciu <xref:System.Windows.DataTemplate>można utworzyć <xref:System.Windows.Controls.ComboBox>, w którym każdy element zawiera pole wyboru.

- **Szablony kontrolek.** Wiele kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać <xref:System.Windows.Controls.ControlTemplate> do definiowania struktury i wyglądu kontrolki, która oddziela wygląd formantu od funkcjonalności formantu. Można radykalnie zmienić wygląd kontrolki przez ponowne zdefiniowanie jej <xref:System.Windows.Controls.ControlTemplate>.  Załóżmy na przykład, że chcesz, aby formant wyglądał jak Sygnalizator uliczny. Ten formant ma prosty interfejs użytkownika i jego funkcje.  Kontrolka jest trzema kołami, tylko jeden z nich może być wciśnięty w czasie. Po pewnym odbiciu możesz zastanowić się, że <xref:System.Windows.Controls.RadioButton> oferuje funkcje tylko jednego z nich, ale domyślny wygląd <xref:System.Windows.Controls.RadioButton> nie wygląda podobnie jak w przypadku sygnalizatorów sygnalizatora.  Ponieważ <xref:System.Windows.Controls.RadioButton> używa szablonu kontrolki do definiowania jego wyglądu, można łatwo ponownie zdefiniować <xref:System.Windows.Controls.ControlTemplate> w celu dopasowania do wymagań kontrolki i użyć przycisków radiowych, aby utworzyć Wskaźnik sygnalizatora.

  > [!NOTE]
  > Mimo że <xref:System.Windows.Controls.RadioButton> może używać <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> w tym przykładzie nie jest wystarczający.  <xref:System.Windows.DataTemplate> definiuje wygląd zawartości kontrolki. W przypadku <xref:System.Windows.Controls.RadioButton>zawartość jest wyświetlana na prawo od okręgu, który wskazuje, czy <xref:System.Windows.Controls.RadioButton> jest zaznaczone.  W przykładzie sygnalizatora ulicznego przycisk radiowy musi być kółkiem, który może "rozjaśnić". Ponieważ wymagania dotyczące wyglądu dla sygnalizatora ulicznego różnią się od domyślnego wyglądu <xref:System.Windows.Controls.RadioButton>, konieczne jest ponowne zdefiniowanie <xref:System.Windows.Controls.ControlTemplate>.  Ogólnie rzecz biorąc <xref:System.Windows.DataTemplate> jest używany do definiowania zawartości (lub danych) kontrolki, a <xref:System.Windows.Controls.ControlTemplate> jest używany do definiowania sposobu, w jaki formant jest strukturalny.

- **Wyzwalacze.** <xref:System.Windows.Trigger> pozwala dynamicznie zmieniać wygląd i zachowanie kontrolki bez tworzenia nowej kontrolki. Załóżmy na przykład, że masz wiele kontrolek <xref:System.Windows.Controls.ListBox> w aplikacji i chcesz, aby elementy w każdym <xref:System.Windows.Controls.ListBox> były pogrubione i czerwone, gdy są zaznaczone. Pierwszym instinctem może być utworzenie klasy, która dziedziczy po <xref:System.Windows.Controls.ListBox> i zastąpienie metody <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> w celu zmiany wyglądu wybranego elementu, ale lepszym rozwiązaniem jest dodanie wyzwalacza do stylu <xref:System.Windows.Controls.ListBoxItem>, który zmienia wygląd wybranego elementu. Wyzwalacz pozwala zmieniać wartości właściwości lub podejmować działania na podstawie wartości właściwości. <xref:System.Windows.EventTrigger> umożliwia podejmowanie akcji w przypadku wystąpienia zdarzenia.

Aby uzyskać więcej informacji na temat stylów, szablonów i wyzwalaczy, zobacz [Style i tworzenia szablonów](styling-and-templating.md).

Ogólnie rzecz biorąc, jeśli formant odzwierciedla funkcjonalność istniejącej kontrolki, ale chcesz, aby formant wyglądał inaczej, należy najpierw rozważyć, czy można użyć dowolnej metody omówionej w tej sekcji, aby zmienić wygląd istniejącej kontrolki.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modele dla tworzenia formantów

Bogaty model zawartości, style, szablony i wyzwalacze minimalizują potrzebę tworzenia nowej kontrolki. Jeśli jednak trzeba utworzyć nową kontrolkę, ważne jest, aby zrozumieć różne modele tworzenia formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia trzy ogólne modele do tworzenia kontrolki, z których każdy zapewnia inny zestaw funkcji i poziom elastyczności. Klasy bazowe dla trzech modeli są <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>i <xref:System.Windows.FrameworkElement>.

### <a name="deriving-from-usercontrol"></a>Wyprowadzanie z obiektu UserControl

Najprostszym sposobem utworzenia formantu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest uzyskanie od <xref:System.Windows.Controls.UserControl>. Podczas tworzenia kontrolki, która dziedziczy po <xref:System.Windows.Controls.UserControl>, należy dodać istniejące składniki do <xref:System.Windows.Controls.UserControl>, nazwać składniki i procedury obsługi zdarzeń referencyjnych w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Następnie można odwoływać się do nazwanych elementów i zdefiniować programy obsługi zdarzeń w kodzie. Ten model programistyczny jest bardzo podobny do modelu używanego do tworzenia aplikacji w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

W przypadku poprawnego skompilowania <xref:System.Windows.Controls.UserControl> może skorzystać z zalet bogatej zawartości, stylów i wyzwalaczy. Jeśli jednak formant dziedziczy po <xref:System.Windows.Controls.UserControl>, osoby, które używają Twojego formantu, nie będą mogły użyć <xref:System.Windows.DataTemplate> lub <xref:System.Windows.Controls.ControlTemplate> do dostosowania jego wyglądu.  Konieczne jest wyjęcie z klasy <xref:System.Windows.Controls.Control> lub jednej z jej klas pochodnych (innych niż <xref:System.Windows.Controls.UserControl>), aby utworzyć formant niestandardowy, który obsługuje szablony.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Zalety wyprowadzania z elementu UserControl

Należy rozważyć wyprowadzanie z <xref:System.Windows.Controls.UserControl>, jeśli są spełnione wszystkie z następujących warunków:

- Chcesz utworzyć kontrolkę podobnie jak w przypadku kompilowania aplikacji.

- Kontrolka składa się tylko z istniejących składników.

- Nie musisz obsługiwać złożonych dostosowań.

### <a name="deriving-from-control"></a>Wyprowadzanie z kontroli

Wyprowadzanie z klasy <xref:System.Windows.Controls.Control> jest modelem używanym przez większość istniejących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolek. Podczas tworzenia kontrolki, która dziedziczy z klasy <xref:System.Windows.Controls.Control>, można zdefiniować jej wygląd przy użyciu szablonów. Dzięki temu można oddzielić logikę operacyjną od reprezentacji wizualnej. Możesz również zapewnić rozdzielenie interfejsu użytkownika i logiki przy użyciu poleceń i powiązań zamiast zdarzeń i unikając odwoływania się do elementów w <xref:System.Windows.Controls.ControlTemplate>, jeśli jest to możliwe.  Jeśli interfejs użytkownika i logika kontrolki są prawidłowo oddzielone, użytkownik kontrolki może ponownie zdefiniować <xref:System.Windows.Controls.ControlTemplate> formantu, aby dostosować jego wygląd. Chociaż Kompilowanie niestandardowych <xref:System.Windows.Controls.Control> nie jest tak proste jak Kompilowanie <xref:System.Windows.Controls.UserControl>, niestandardowe <xref:System.Windows.Controls.Control> zapewnia największą elastyczność.

#### <a name="benefits-of-deriving-from-control"></a>Zalety wynikające z kontroli

Należy rozważyć wyprowadzanie z <xref:System.Windows.Controls.Control>, zamiast korzystać z klasy <xref:System.Windows.Controls.UserControl>, jeśli istnieją następujące zastosowania:

- Chcesz, aby wygląd kontrolki był dostosowywany za pośrednictwem <xref:System.Windows.Controls.ControlTemplate>.

- Chcesz, aby formant obsługiwał różne motywy.

### <a name="deriving-from-frameworkelement"></a>Wyprowadzanie z FrameworkElement

Kontrolki, które pochodzą od <xref:System.Windows.Controls.UserControl> lub <xref:System.Windows.Controls.Control>, polegają na tworzeniu istniejących elementów. W wielu scenariuszach jest to akceptowalne rozwiązanie, ponieważ każdy obiekt, który dziedziczy po <xref:System.Windows.FrameworkElement> może znajdować się w <xref:System.Windows.Controls.ControlTemplate>. Jednak istnieją sytuacje, w których wygląd kontrolki wymaga więcej niż funkcjonalności prostej składowej elementu. Dla tych scenariuszy należy wybrać składnik oparty na <xref:System.Windows.FrameworkElement>.

Istnieją dwie standardowe metody tworzenia składników opartych na <xref:System.Windows.FrameworkElement>: Render bezpośredni i kompozycja elementów niestandardowych. Renderowanie bezpośrednie polega na zastępowaniu metody <xref:System.Windows.UIElement.OnRender%2A> <xref:System.Windows.FrameworkElement> i udostępnieniu <xref:System.Windows.Media.DrawingContext> operacji, które jawnie definiują wizualizacje składnika. Jest to metoda używana przez <xref:System.Windows.Controls.Image> i <xref:System.Windows.Controls.Border>. Kompozycja elementu niestandardowego obejmuje użycie obiektów typu <xref:System.Windows.Media.Visual>, aby zredagować wygląd składnika. Aby zapoznać się z przykładem, zobacz [Używanie obiektów użycie DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> jest przykładem kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], która korzysta ze składowych elementów niestandardowych. Istnieje również możliwość mieszania bezpośredniego renderowania i niestandardowego kompozycji elementów w tej samej kontrolce.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Korzyści wynikające z wytworzenia z elementu FrameworkElement

Należy rozważyć wyprowadzanie z <xref:System.Windows.FrameworkElement>, jeśli którykolwiek z następujących ma zastosowanie:

- Chcesz mieć precyzyjną kontrolę nad wyglądem kontrolki poza tym, co jest obsługiwane przez prostą kompozycję elementów.

- Chcesz zdefiniować wygląd formantu przez zdefiniowanie własnej logiki renderowania.

- Chcesz tworzyć istniejące elementy w sposób, który wykracza poza możliwości <xref:System.Windows.Controls.UserControl> i <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Podstawowe informacje dotyczące tworzenia formantów

Jak wspomniano wcześniej, jedną z najbardziej zaawansowanych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest możliwość przekroczenia ustawień podstawowych właściwości kontrolki, aby zmienić jej wygląd i zachowanie, ale nadal nie trzeba tworzyć kontrolki niestandardowej. Opcje stylów, powiązań danych i wyzwalacza są możliwe przez system właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i system zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W poniższych sekcjach opisano niektóre praktyki, które należy wykonać, niezależnie od modelu używanego do tworzenia kontrolki niestandardowej, tak aby użytkownicy kontrolki niestandardowej mogli korzystać z tych funkcji w taki sam sposób jak w przypadku kontrolki, która jest dołączona do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

### <a name="use-dependency-properties"></a>Użyj właściwości zależności

Gdy właściwość jest właściwością zależności, można wykonać następujące czynności:

- Ustaw właściwość w stylu.

- Powiąż Właściwość ze źródłem danych.

- Użyj zasobu dynamicznego jako wartości właściwości.

- Animuj właściwość.

Jeśli chcesz, aby właściwość kontrolki obsługiwała jakąkolwiek z tych funkcji, należy zaimplementować ją jako właściwość zależności. W poniższym przykładzie zdefiniowano właściwość zależności o nazwie `Value`, wykonując następujące czynności:

- Zdefiniuj <xref:System.Windows.DependencyProperty> identyfikator o nazwie `ValueProperty` jako pole `public` `static` `readonly`.

- Zarejestruj nazwę właściwości w systemie właściwości, wywołując <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aby określić następujące elementy:

  - Nazwa właściwości.

  - Typ właściwości.

  - Typ, który jest właścicielem właściwości.

  - Metadane właściwości. Metadane zawierają wartość domyślną właściwości, <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>.

- Zdefiniuj właściwość otoki CLR o nazwie `Value`, która jest taka sama jak nazwa użyta do zarejestrowania właściwości zależności, implementując `get` właściwości i metody dostępu `set`. Należy zauważyć, że metody dostępu `get` i `set` tylko wywołują <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>. Zaleca się, aby metody dostępu do właściwości zależności nie zawierały dodatkowej logiki, ponieważ klienci i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą ominąć metod dostępu i <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Na przykład gdy właściwość jest powiązana ze źródłem danych, metoda dostępu `set` właściwości nie jest wywoływana.  Zamiast dodawać dodatkową logikę do metod dostępu get i Set, należy użyć delegatów <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>i <xref:System.Windows.PropertyChangedCallback>, aby odpowiedzieć na lub sprawdzić wartość podczas zmiany.  Aby uzyskać więcej informacji na temat tych wywołań zwrotnych, zobacz [wywołania zwrotne właściwości zależności i walidacja](../advanced/dependency-property-callbacks-and-validation.md).

- Zdefiniuj metodę dla <xref:System.Windows.CoerceValueCallback> o nazwie `CoerceValue`. `CoerceValue` zapewnia, że `Value` jest większe lub równe `MinValue` i mniejsze lub równe `MaxValue`.

- Zdefiniuj metodę dla <xref:System.Windows.PropertyChangedCallback>o nazwie `OnValueChanged`. `OnValueChanged` tworzy obiekt <xref:System.Windows.RoutedPropertyChangedEventArgs%601> i przygotowuje się do podniesienia `ValueChanged` kierowanego zdarzenia. Zdarzenia kierowane zostały omówione w następnej sekcji.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Korzystanie z zdarzeń kierowanych

Podobnie jak właściwości zależności zwiększają koncepcję właściwości CLR z dodatkową funkcjonalnością, zdarzenia kierowane zwiększają koncepcję standardowych zdarzeń CLR. Podczas tworzenia nowej kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest również dobrym sposobem wdrożenia zdarzenia jako zdarzenia kierowanego, ponieważ routowane zdarzenie obsługuje następujące zachowanie:

- Zdarzenia mogą być obsługiwane na obiekcie nadrzędnym wielu kontrolek. Jeśli zdarzenie jest zdarzeniem propagacji, jeden element nadrzędny w drzewie elementu może subskrybować zdarzenie. Następnie autorzy aplikacji mogą używać jednego programu obsługi, aby odpowiedzieć na zdarzenie wielu kontrolek. Na przykład jeśli formant jest częścią każdego elementu w <xref:System.Windows.Controls.ListBox> (ponieważ jest zawarty w <xref:System.Windows.DataTemplate>), Deweloper aplikacji może zdefiniować procedurę obsługi zdarzeń dla zdarzenia kontrolki w <xref:System.Windows.Controls.ListBox>. Za każdym razem, gdy wystąpi zdarzenie na dowolnym z formantów, wywoływana jest procedura obsługi zdarzeń.

- Zdarzenia trasowane mogą być używane w <xref:System.Windows.EventSetter>, co umożliwia deweloperom aplikacji określenie obsługi zdarzenia w ramach stylu.

- Zdarzenia trasowane mogą być używane w <xref:System.Windows.EventTrigger>, co jest przydatne w przypadku animowania właściwości przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

W poniższym przykładzie zdefiniowano zdarzenie trasowane, wykonując następujące czynności:

- Zdefiniuj <xref:System.Windows.RoutedEvent> identyfikator o nazwie `ValueChangedEvent` jako pole `public` `static` `readonly`.

- Zarejestruj zdarzenie kierowane, wywołując metodę <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>. W przykładzie określono następujące informacje podczas wywoływania <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:

  - Nazwa zdarzenia jest `ValueChanged`.

  - Strategia routingu jest <xref:System.Windows.RoutingStrategy.Bubble>, co oznacza, że program obsługi zdarzeń na źródle (obiekt, który wywołuje zdarzenie) jest wywoływany jako pierwszy, a następnie procedury obsługi zdarzeń w elementach nadrzędnych źródła są wywoływane po powodzeniu, rozpoczynając od programu obsługi zdarzeń na najbliższym element nadrzędny.

  - Typ procedury obsługi zdarzeń jest <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, skonstruowany przy użyciu typu <xref:System.Decimal>.

  - Typ właściciela zdarzenia jest `NumericUpDown`.

- Zadeklaruj zdarzenie publiczne o nazwie `ValueChanged` i zawiera deklaracje metody dostępu zdarzenia. Przykład wywołuje <xref:System.Windows.UIElement.AddHandler%2A> w deklaracji metody dostępu `add` i <xref:System.Windows.UIElement.RemoveHandler%2A> w deklaracji metody dostępu `remove` do korzystania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług zdarzeń.

- Utwórz chronioną metodę wirtualną o nazwie `OnValueChanged`, która wywołuje zdarzenie `ValueChanged`.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń kierowanych](../advanced/routed-events-overview.md) i [Tworzenie niestandardowego zdarzenia kierowanego](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Użyj powiązania

Aby oddzielić interfejs użytkownika formantu od jego logiki, należy rozważyć użycie powiązania danych. Jest to szczególnie ważne w przypadku definiowania wyglądu kontrolki przy użyciu <xref:System.Windows.Controls.ControlTemplate>. W przypadku używania powiązania danych można wyeliminować konieczność odwoływania się do określonych części interfejsu użytkownika z kodu. Dobrym pomysłem jest uniknięcie odwoływania się do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate>, ponieważ gdy kod odwołuje się do elementów, które znajdują się w <xref:System.Windows.Controls.ControlTemplate> i <xref:System.Windows.Controls.ControlTemplate> został zmieniony, element, do którego istnieje odwołanie, musi być uwzględniony w nowym <xref:System.Windows.Controls.ControlTemplate>.

Poniższy przykład aktualizuje <xref:System.Windows.Controls.TextBlock> kontrolki `NumericUpDown`, przypisując do niej nazwę i odwołując się do pola tekstowego według nazwy w kodzie.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Poniższy przykład używa powiązania, aby wykonać to samo.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Projektowanie dla projektantów

Aby uzyskać pomoc techniczną dla formantów WPF w programie WPF Designer dla programu Visual Studio (na przykład edytowania właściwości z okno Właściwości), postępuj zgodnie z poniższymi wskazówkami.  Aby uzyskać więcej informacji na temat programowania dla projektanta WPF, zobacz [Design XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Właściwości zależności

Upewnij się, że wdrożono `get` CLR i metody dostępu `set` zgodnie z wcześniejszym opisem w artykule "Używanie właściwości zależności". Projektanci mogą używać otoki do wykrywania obecności właściwości zależności, ale takich jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i klienci formantu, nie muszą wywoływać metod dostępu podczas pobierania lub ustawiania właściwości.

#### <a name="attached-properties"></a>Dołączone właściwości

Załączone właściwości należy zaimplementować w niestandardowych kontrolkach, korzystając z następujących wskazówek:

- `public` `static` `readonly` <xref:System.Windows.DependencyProperty> metody *PropertyName*`Property`, która została utworzona przy użyciu metod <xref:System.Windows.DependencyProperty.RegisterAttached%2A>. Nazwa właściwości, która jest przenoszona do <xref:System.Windows.DependencyProperty.RegisterAttached%2A> musi być zgodna z parametrem *PropertyName*.

- Zaimplementuj parę `public` `static` metody CLR o nazwach `Set`*PropertyName* i `Get`*PropertyName*. Obie metody powinny akceptować klasę pochodną <xref:System.Windows.DependencyProperty> jako ich pierwszy argument. Metoda `Set`*PropertyName* również akceptuje argument, którego typ jest zgodny z typem danych zarejestrowanych dla właściwości. Metoda `Get`*PropertyName* powinna zwracać wartość tego samego typu. Jeśli brakuje metody `Set`*PropertyName* , właściwość jest oznaczona jako tylko do odczytu.

- `Set` *PropertyName* i `Get`*PropertyName* musi być bezpośrednio kierowane do <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> metod w docelowym obiekcie zależności. Projektanci mogą uzyskać dostęp do dołączonej właściwości, wywołując przez otokę metody lub wykonując bezpośrednie wywołanie do docelowego obiektu zależności.

Aby uzyskać więcej informacji o dołączanych właściwościach, zobacz temat [dołączone właściwości przegląd](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definiowanie i używanie zasobów udostępnionych

Możesz dołączyć swój formant w tym samym zestawie, w którym znajduje się aplikacja, lub spakować formant w osobnym zestawie, który może być używany w wielu aplikacjach. W większości przypadków informacje omówione w tym temacie dotyczą niezależnie od używanej metody.  Należy jednak pamiętać o jednej różnicy.  Po umieszczeniu formantu w tym samym zestawie, w którym znajduje się aplikacja, możesz dodać zasoby globalne do pliku App. XAML. Ale zestaw, który zawiera tylko kontrolki, nie ma skojarzonego z nim obiektu <xref:System.Windows.Application>, więc plik App. XAML nie jest dostępny.

Gdy aplikacja szuka zasobu, sprawdza trzy poziomy w następującej kolejności:

1. Poziom elementu.

   System rozpoczyna się od elementu, który odwołuje się do zasobu, a następnie przeszukuje zasoby logicznego elementu nadrzędnego i tak dalej, aż do osiągnięcia elementu głównego.

2. Poziom aplikacji.

   Zasoby zdefiniowane przez obiekt <xref:System.Windows.Application>.

3. Poziom motywu.

   Słowniki na poziomie motywu są przechowywane w podfolderze o nazwie motywy.  Pliki w folderze motywy odpowiadają kompozycjom.  Na przykład możesz mieć interfejs Aero. NormalColor. XAML, Luna. NormalColor. XAML, Royale. NormalColor. XAML i tak dalej.  Można również mieć plik o nazwie Generic. XAML.  Gdy system wyszukuje zasób na poziomie motywów, najpierw szuka go w pliku specyficznym dla motywu, a następnie szuka go w ogólnym języku XAML.

Gdy formant znajduje się w zestawie, który jest oddzielony od aplikacji, należy umieścić zasoby globalne na poziomie elementu lub na poziomie motywu. Obie metody mają swoje zalety.

#### <a name="defining-resources-at-the-element-level"></a>Definiowanie zasobów na poziomie elementu

Zasoby udostępnione można definiować na poziomie elementu przez utworzenie niestandardowego słownika zasobów i scalenie go ze słownikiem zasobów formantu.  Korzystając z tej metody, można nazwać dowolny plik zasobów i może znajdować się w tym samym folderze co kontrolki. Zasoby na poziomie elementu mogą również używać prostych ciągów jako kluczy. Poniższy przykład tworzy plik zasobów <xref:System.Windows.Media.LinearGradientBrush> o nazwie Dictionary1. XAML.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Po zdefiniowaniu słownika należy go scalić z słownikiem zasobów formantu.  Można to zrobić za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu.

Poniższy przykład Scala słownik zasobów przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Wadą tego podejścia jest to, że obiekt <xref:System.Windows.ResourceDictionary> jest tworzony przy każdym odwoływaniu się do niego.  Na przykład jeśli masz 10 niestandardowych kontrolek w bibliotece i Scal udostępnione słowniki zasobów dla każdej kontrolki przy użyciu języka XAML, utworzysz 10 identycznych obiektów <xref:System.Windows.ResourceDictionary>.  Można tego uniknąć, tworząc klasę statyczną, która scala zasoby w kodzie i zwraca wynikowy <xref:System.Windows.ResourceDictionary>.

Poniższy przykład tworzy klasę, która zwraca współużytkowany <xref:System.Windows.ResourceDictionary>.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Poniższy przykład Scala zasób udostępniony z zasobami kontrolki niestandardowej w konstruktorze formantu przed wywołaniem `InitializeComponent`.  Ponieważ `SharedDictionaryManager.SharedDictionary` jest właściwością statyczną, <xref:System.Windows.ResourceDictionary> jest tworzony tylko raz. Ze względu na to, że słownik zasobów został wyscalany przed wywołaniem `InitializeComponent`, zasoby są dostępne dla formantu w jego pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definiowanie zasobów na poziomie motywu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia tworzenie zasobów dla różnych motywów systemu Windows.  Jako autor kontrolki możesz zdefiniować zasób dla określonego motywu, aby zmienić wygląd formantu w zależności od tego, jaki motyw jest używany. Na przykład wygląd <xref:System.Windows.Controls.Button> w klasycznym motywie systemu Windows (motyw domyślny dla systemu Windows 2000) różni się od <xref:System.Windows.Controls.Button> w motywie Luna systemu Windows (motyw domyślny dla systemu Windows XP), ponieważ <xref:System.Windows.Controls.Button> używa innego <xref:System.Windows.Controls.ControlTemplate> dla każdego motywu.

Zasoby specyficzne dla motywu są przechowywane w słowniku zasobów z określoną nazwą pliku. Te pliki muszą znajdować się w folderze o nazwie `Themes`, który jest podfolderem folderu, który zawiera kontrolkę. W poniższej tabeli wymieniono pliki słownika zasobów i motyw, które są skojarzone z każdym plikiem:

|Nazwa pliku słownika zasobów|Motyw systemu Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasyczne systemy Windows 9X/2000 Szukaj w systemie Windows XP|
|`Luna.NormalColor.xaml`|Domyślny niebieski motyw w systemie Windows XP|
|`Luna.Homestead.xaml`|Motyw oliwy w systemie Windows XP|
|`Luna.Metallic.xaml`|Motyw Silver w systemie Windows XP|
|`Royale.NormalColor.xaml`|Motyw domyślny w systemie Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Motyw domyślny w systemie Windows Vista|

Nie trzeba definiować zasobów dla każdego motywu. Jeśli zasób nie jest zdefiniowany dla określonego motywu, formant sprawdza `Classic.xaml` dla zasobu. Jeśli zasób nie jest zdefiniowany w pliku, który odnosi się do bieżącego motywu lub w `Classic.xaml`, formant używa zasobu generycznego, który znajduje się w pliku słownika zasobów o nazwie `generic.xaml`.  Plik `generic.xaml` znajduje się w tym samym folderze co pliki słowników zasobów specyficznych dla motywu. Chociaż `generic.xaml` nie odpowiada określonemu motywowi systemu Windows, nadal jest to słownik poziomu motywu.

Kontrolka niestandardowa NumericUpDown [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) lub [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) z obsługą języka i automatyzacji interfejsu użytkownika zawiera dwa słowniki zasobów dla kontrolki `NumericUpDown`: jeden jest w pliku Generic. XAML, a drugi to w Luna. NormalColor. XAML. 

Po umieszczeniu <xref:System.Windows.Controls.ControlTemplate> w dowolnym pliku słowników zasobów specyficznych dla motywu należy utworzyć statyczny Konstruktor dla kontrolki i wywołać metodę <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> na <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, jak pokazano w poniższym przykładzie.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definiowanie i odwoływanie się do kluczy dla zasobów motywu

Podczas definiowania zasobu na poziomie elementu można przypisać ciąg jako klucz i uzyskać dostęp do zasobu za pośrednictwem ciągu. Podczas definiowania zasobu na poziomie motywu należy użyć <xref:System.Windows.ComponentResourceKey> jako klucza.  W poniższym przykładzie zdefiniowano zasób w pliku Generic. XAML.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Poniższy przykład odwołuje się do zasobu, określając <xref:System.Windows.ComponentResourceKey> jako klucz.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Określanie lokalizacji zasobów motywu

Aby znaleźć zasoby dla kontrolki, aplikacja hostingu musi wiedzieć, że zestaw zawiera zasoby dotyczące kontroli. Można to zrobić, dodając <xref:System.Windows.ThemeInfoAttribute> do zestawu, który zawiera kontrolkę. <xref:System.Windows.ThemeInfoAttribute> ma właściwość <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>, która określa lokalizację zasobów ogólnych, oraz Właściwość <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>, która określa lokalizację zasobów specyficznych dla motywu.

Poniższy przykład ustawia właściwości <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> i <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> do <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, aby określić, że zasoby ogólne i specyficzne dla motywu znajdują się w tym samym zestawie, w którym znajduje się kontrolka.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Zobacz także

- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Pakowanie URI w WPF](../app-development/pack-uris-in-wpf.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
