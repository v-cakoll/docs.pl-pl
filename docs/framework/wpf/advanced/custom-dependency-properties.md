---
title: Niestandardowe właściwości zależności
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: e4117d7add2a34d6d989d9222e7688361cf6b379
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646356"
---
# <a name="custom-dependency-properties"></a>Niestandardowe właściwości zależności

W tym temacie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] opisano powody, dla których deweloperzy aplikacji i autorzy składników mogą chcieć utworzyć właściwość zależności niestandardowej i opisano kroki implementacji, a także niektóre opcje implementacji, które mogą poprawić wydajność, użyteczność lub wszechstronność właściwości.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie przyjęto założenie, że rozumiesz właściwości zależności z perspektywy konsumenta istniejących właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasach i przeczytałeś temat [Omówienie właściwości zależności.](dependency-properties-overview.md) Aby postępować zgodnie z przykładami w tym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temacie, należy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również zrozumieć i wiedzieć, jak pisać aplikacje.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co to jest właściwość zależności?

Można włączyć, co w przeciwnym razie byłoby właściwość wspólnego środowiska wykonawczego języka (CLR) do obsługi stylizacji, powiązania danych, dziedziczenia, animacje i wartości domyślne, implementując go jako właściwość zależności. Właściwości zależności są właściwości, które są [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zarejestrowane w <xref:System.Windows.DependencyProperty.Register%2A> systemie <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>właściwości przez wywołanie <xref:System.Windows.DependencyProperty> metody (lub ), i które są wspierane przez pole identyfikatora. Właściwości zależności mogą być używane <xref:System.Windows.DependencyObject> tylko <xref:System.Windows.DependencyObject> przez typy, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ale jest dość wysoka w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hierarchii klas, więc większość klas dostępnych w może obsługiwać właściwości zależności. Aby uzyskać więcej informacji na temat właściwości zależności oraz niektórych terminologii i konwencji używanych do opisywania ich w tym zestawie SDK, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Przykłady właściwości zależności

Przykłady właściwości zależności, które są [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementowane <xref:System.Windows.Controls.Control.Background%2A> na klasy <xref:System.Windows.FrameworkElement.Width%2A> obejmują właściwość, właściwość i <xref:System.Windows.Controls.TextBox.Text%2A> właściwość, wśród wielu innych. Każda właściwość zależności widoczna przez klasę ma odpowiednie <xref:System.Windows.DependencyProperty> publiczne pole statyczne typu udostępniane w tej samej klasie. Jest to identyfikator właściwości zależności. Identyfikator jest nazwany przy użyciu konwencji: nazwa właściwości zależności `Property` z dołączonym do niego ciągiem. Na przykład odpowiednim <xref:System.Windows.DependencyProperty> polem identyfikatora <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.BackgroundProperty>właściwości jest . Identyfikator przechowuje informacje o właściwości zależności, ponieważ została zarejestrowana, a identyfikator jest następnie używany później dla innych <xref:System.Windows.DependencyObject.SetValue%2A>operacji dotyczących właściwości zależności, takich jak wywołanie .

Jak wspomniano w [przeglądzie właściwości zależności,](dependency-properties-overview.md)wszystkie właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zależności w (z wyjątkiem większości dołączonych właściwości) są również właściwości CLR ze względu na implementację "otoki". W związku z tym z kodu, można uzyskać lub ustawić właściwości zależności, wywołując akcesory CLR, które definiują otoki w taki sam sposób, w jaki można użyć innych właściwości CLR. Jako konsument ustalonych właściwości zależności zazwyczaj nie używasz <xref:System.Windows.DependencyObject> metod <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>i , które są punktem połączenia z podstawowym systemem właściwości. Zamiast istniejącej implementacji właściwości CLR będzie <xref:System.Windows.DependencyObject.GetValue%2A> już <xref:System.Windows.DependencyObject.SetValue%2A> wywoływane i w ramach `get` i `set` otoki implementacji właściwości, przy użyciu pola identyfikator odpowiednio. Jeśli samodzielnie implementujesz właściwość zależności niestandardowej, następnie będzie definiowanie otoki w podobny sposób.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Kiedy należy zaimplementować właściwość zależności?

Po zaimplementowanie właściwości w klasie, tak <xref:System.Windows.DependencyObject>długo, jak klasa pochodzi od <xref:System.Windows.DependencyProperty> , masz możliwość tworzenia kopii zapasowych właściwości z identyfikatorem, a tym samym, aby uczynić ją właściwością zależności. Posiadanie właściwości być właściwości zależności nie zawsze jest konieczne lub odpowiednie i będzie zależeć od potrzeb scenariusza. Czasami typowa technika tworzenia kopii nieruchomości z prywatnym polem jest odpowiednia. Jednak należy zaimplementować właściwość jako właściwość zależności, gdy chcesz, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aby właściwość obsługiwała co najmniej jedną z następujących możliwości:

- Chcesz, aby twoja właściwość była ustawiona w stylu. Aby uzyskać więcej informacji, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

- Chcesz, aby twoja właściwość obsługiwała powiązanie danych. Aby uzyskać więcej informacji na temat właściwości zależności wiązania danych, zobacz [Powiąż właściwości dwóch formantów](../data/how-to-bind-the-properties-of-two-controls.md).

- Chcesz, aby właściwość była ustawiona za pomocą dynamicznego odwołania do zasobu. Aby uzyskać więcej informacji, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Chcesz dziedziczyć wartość właściwości automatycznie z elementu nadrzędnego w drzewie elementów. W takim przypadku zarejestruj <xref:System.Windows.DependencyProperty.RegisterAttached%2A> się za pomocą metody, nawet jeśli utworzysz również otokę właściwości dla dostępu CLR. Aby uzyskać więcej informacji, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).

- Chcesz, aby twoja nieruchomość była animatowalna. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

- System właściwości ma raportować, gdy poprzednia wartość właściwości została zmieniona przez akcje podejmowane przez system właściwości, środowisko lub użytkownika lub przez odczyt i używanie stylów. Za pomocą metadanych właściwości, właściwość można określić metodę wywołania zwrotnego, które będą wywoływane za każdym razem, gdy system właściwości określa, że wartość właściwości została ostatecznie zmieniona. Pokrewna koncepcja jest przymus wartości właściwości. Aby uzyskać więcej informacji, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności](dependency-property-callbacks-and-validation.md).

- Chcesz użyć ustalonych konwencji metadanych, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są również używane przez procesy, takie jak raportowanie, czy zmiana wartości właściwości powinna wymagać od systemu układu ponownego komponowania wizualizacji elementu. Lub chcesz mieć możliwość korzystania z zastąpienia metadanych, dzięki czemu klasy pochodne można zmienić właściwości oparte na metadanych, takie jak wartość domyślna.

- Chcesz właściwości formantu niestandardowego, aby odbierać visual studio WPF Designer wsparcia, takich jak **właściwości** edycji okna. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).

Podczas badania tych scenariuszy, należy również rozważyć, czy można osiągnąć scenariusz, zastępując metadane istniejącej właściwości zależności, a nie implementując całkowicie nową właściwość. Czy zastąpienie metadanych jest praktyczne zależy od scenariusza i jak ściśle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ten scenariusz przypomina implementacji w istniejących właściwości zależności i klas. Aby uzyskać więcej informacji na temat zastępowania metadanych istniejących właściwości, zobacz [Metadane właściwości zależności](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Lista kontrolna definiowania właściwości zależności

Definiowanie właściwości zależności składa się z czterech różnych pojęć. Pojęcia te nie są koniecznie ścisłe kroki proceduralne, ponieważ niektóre z nich kończy się łączone jako pojedyncze wiersze kodu w implementacji:

- (Opcjonalnie) Utwórz metadane właściwości dla właściwości zależności.

- Zarejestruj nazwę właściwości w systemie właściwości, określając typ właściciela i typ wartości właściwości. Należy również określić metadane właściwości, jeśli jest używana.

- Zdefiniuj <xref:System.Windows.DependencyProperty> `public` `static` `readonly` identyfikator jako pole typu właściciela.

- Zdefiniuj właściwość "otoka" CLR, której nazwa odpowiada nazwie właściwości zależności. Zaimplementuj właściwości "otoki" CLR `get` i `set` akcesory, aby połączyć się z właściwością zależności, która ją wspiera.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Rejestracja nieruchomości w systemie nieruchomości

Aby właściwość była właściwością zależności, należy zarejestrować tę właściwość w tabeli obsługiwanej przez system właściwości i nadać jej unikatowy identyfikator, który jest używany jako kwalifikator dla późniejszych operacji systemu właściwości. Te operacje mogą być operacje wewnętrzne lub własny kod wywoływania interfejsów API systemu właściwości. Aby zarejestrować właściwość, <xref:System.Windows.DependencyProperty.Register%2A> należy wywołać metodę w treści klasy (wewnątrz klasy, ale poza definicje elementów członkowskich). Pole identyfikatora jest również <xref:System.Windows.DependencyProperty.Register%2A> dostarczane przez wywołanie metody jako wartość zwracaną. Powodem, <xref:System.Windows.DependencyProperty.Register%2A> dla którego wywołanie jest wykonywane poza innymi definicjami elementów `public` `static` `readonly` członkowskich, <xref:System.Windows.DependencyProperty> jest użycie tej wartości zwracanej do przypisania i utworzenia pola typu jako części klasy. To pole staje się identyfikatorem właściwości zależności.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konwencje nazwy właściwości zależności

Istnieją ustanowione konwencje nazewnictwa dotyczące właściwości zależności, które należy wykonać we wszystkich, ale wyjątkowych okolicznościach.

Sama właściwość zależności będzie miała podstawową nazwę "AquariumGraphic", jak w tym przykładzie, która jest podana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A>. Ta nazwa musi być unikatowa w ramach każdego typu rejestracji. Właściwości zależności dziedziczone za pośrednictwem typów podstawowych są uważane za już część typu rejestracji; nazwy właściwości dziedziczonych nie mogą być ponownie zarejestrowane. Istnieje jednak technika dodawania klasy jako właściciela właściwości zależności, nawet wtedy, gdy właściwość zależności nie jest dziedziczona; aby uzyskać szczegółowe informacje, zobacz [Metadane właściwości zależności](dependency-property-metadata.md).

Podczas tworzenia pola identyfikatora nazwij to pole nazwą właściwości podczas jego rejestracji `Property`oraz sufiksem . To pole jest identyfikatorem właściwości zależności i będzie ono używane później <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject.GetValue%2A> jako dane wejściowe dla i wywołań, które zostaną wprowadzone w otokach, przez inny dostęp do kodu do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] właściwości przez własny kod, przez dowolny dostęp do kodu zewnętrznego, na który zezwolisz, przez system właściwości i potencjalnie przez procesory.

> [!NOTE]
> Definiowanie właściwości zależności w treści klasy jest typową implementacją, ale jest również możliwe zdefiniowanie właściwości zależności w konstruktorze statycznym klasy. Takie podejście może mieć sens, jeśli potrzebujesz więcej niż jeden wiersz kodu do zainicjowania właściwości zależności.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Wdrażanie "Otoki"

Implementacja otoki <xref:System.Windows.DependencyObject.GetValue%2A> powinna `get` wywołać <xref:System.Windows.DependencyObject.SetValue%2A> w `set` implementacji i w implementacji (oryginalne wywołanie rejestracji i pole są wyświetlane również w tym miejscu dla jasności).

We wszystkich, ale wyjątkowych okolicznościach, implementacje otoki powinny wykonywać tylko <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> działania, odpowiednio. Przyczyna tego jest omówiona w temacie [Właściwości ładowania i zależności XAML](xaml-loading-and-dependency-properties.md).

Wszystkie istniejące właściwości zależności publicznej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które są dostarczane na klasy używają tego prostego modelu implementacji otoki; większość złożoności jak działają właściwości zależności jest z natury zachowanie systemu właściwości lub jest implementowana za pośrednictwem innych pojęć, takich jak przymus lub zmiany właściwości wywołania zwrotne za pośrednictwem metadanych właściwości.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Ponownie, zgodnie z konwencją, nazwa właściwości otoki musi być taka sama jak <xref:System.Windows.DependencyProperty.Register%2A> nazwa wybrana i podana jako pierwszy parametr wywołania, które zarejestrowało właściwość. Jeśli twoja właściwość nie jest zgodna z konwencją, nie musi to koniecznie wyłączyć wszystkie możliwe zastosowania, ale napotkasz kilka istotnych problemów:

- Niektóre aspekty stylów i szablonów nie będą działać.

- Większość narzędzi i projektantów musi polegać na konwencjach nazewnictwa, aby prawidłowo serializować [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]lub zapewnić pomoc środowiska projektanta na poziomie właściwości.

- Bieżąca implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego całkowicie pomija otoki i opiera się na konwencji nazewnictwa podczas przetwarzania wartości atrybutów. Aby uzyskać więcej informacji, zobacz [Właściwości ładowania i zależności XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadane właściwości dla nowej właściwości zależności

Podczas rejestrowania właściwości zależności, rejestracja za pośrednictwem systemu właściwości tworzy obiekt metadanych, który przechowuje właściwości. Wiele z tych cech ma wartości domyślne, które są ustawiane, jeśli właściwość jest zarejestrowana z prostymi <xref:System.Windows.DependencyProperty.Register%2A>podpisami . Inne podpisy <xref:System.Windows.DependencyProperty.Register%2A> umożliwiają określenie metadanych, które mają podczas rejestracji właściwości. Najczęstsze metadane podane dla właściwości zależności jest nadanie im wartość domyślną, która jest stosowana w nowych wystąpień, które używają właściwości.

Jeśli tworzysz właściwość zależności, która istnieje w klasie <xref:System.Windows.FrameworkElement>pochodnej , można użyć <xref:System.Windows.FrameworkPropertyMetadata> bardziej wyspecjalizowane <xref:System.Windows.PropertyMetadata> klasy metadanych, a nie klasy podstawowej. Konstruktor <xref:System.Windows.FrameworkPropertyMetadata> dla klasy ma kilka podpisów, w których można określić różne właściwości metadanych w połączeniu. Jeśli chcesz określić tylko wartość domyślną, użyj podpisu, <xref:System.Object>który przyjmuje pojedynczy parametr typu . Przekaż ten parametr obiektu jako wartość domyślną specyficzne dla typu dla właściwości (podana wartość domyślna musi być typem podanym `propertyType` jako parametr w <xref:System.Windows.DependencyProperty.Register%2A> wywołaniu).

For <xref:System.Windows.FrameworkPropertyMetadata>, można również określić flagi opcji metadanych dla właściwości. Flagi te są konwertowane na właściwości dyskretne na metadanych właściwości po rejestracji i są używane do komunikowania niektórych warunków do innych procesów, takich jak aparat układu.

#### <a name="setting-appropriate-metadata-flags"></a>Ustawianie odpowiednich flag metadanych

- Jeśli właściwość (lub zmiany jej wartości) wpływa [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]na , a w szczególności wpływa na sposób, w jaki system układu <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>powinien <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>rozmiar lub renderować element na stronie, należy ustawić jedną lub więcej z następujących flag: , , .

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>wskazuje, że zmiana tej właściwości wymaga [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zmiany renderowania, gdzie obiekt zawierający może wymagać więcej lub mniej miejsca w obrębie obiektu nadrzędnego. Na przykład właściwość "Szerokość" powinna mieć ustawioną tę flagę.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>wskazuje, że zmiana tej właściwości wymaga [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zmiany do renderowania, które zazwyczaj nie wymaga zmiany w dedykowanej przestrzeni, ale wskazuje, że położenie w przestrzeni uległo zmianie. Na przykład właściwość "Wyrównanie" powinna mieć ustawioną tę flagę.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>wskazuje, że nastąpiła inna zmiana, która nie wpłynie na układ i miarę, ale wymaga innego renderowania. Przykładem może być właściwość, która zmienia kolor istniejącego elementu, takiego jak "Tło".

  - Flagi te są często używane jako protokół w metadanych dla własnych implementacji zastępowania nazw systemu właściwości lub układu wywołania zwrotne. Na przykład może mieć <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> wywołania zwrotnego, który będzie wywoływać, <xref:System.Windows.UIElement.InvalidateArrange%2A> jeśli <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> `true` dowolna właściwość wystąpienia zgłasza zmianę wartości i ma jak w jego metadanych.

- Niektóre właściwości mogą mieć wpływ na właściwości renderowania zawierającego elementu nadrzędnego, w sposób wykraczający poza zmiany wymaganego rozmiaru, o których mowa powyżej. Przykładem <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> jest właściwość używana w modelu dokumentu przepływu, gdzie zmiany w tej właściwości można zmienić ogólne renderowanie dokumentu przepływu, który zawiera akapit. Użyj <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> lub zidentyfikować podobne przypadki we własnych właściwościach.

- Domyślnie właściwości zależności obsługują powiązanie danych. Można celowo wyłączyć powiązanie danych, w przypadkach, gdy nie ma realistycznego scenariusza powiązania danych lub gdy wydajność powiązania danych dla dużego obiektu jest rozpoznawana jako problem.

- Domyślnie powiązanie <xref:System.Windows.Data.Binding.Mode%2A> danych dla właściwości zależności <xref:System.Windows.Data.BindingMode.OneWay>domyślnie ma wartość . Zawsze można zmienić powiązanie na <xref:System.Windows.Data.BindingMode.TwoWay> wystąpienie wiązania; aby uzyskać szczegółowe informacje, zobacz [Określanie kierunku wiązania](../data/how-to-specify-the-direction-of-the-binding.md). Ale jako autor właściwości zależności, można wybrać, <xref:System.Windows.Data.BindingMode.TwoWay> aby właściwość używać trybu wiązania domyślnie. Przykładem istniejącej właściwości zależności <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>jest ; scenariusz dla tej właściwości <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> jest, że logika ustawienia <xref:System.Windows.Controls.MenuItem> i komponowanie interakcji z domyślnym stylu motywu. Logika <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> właściwości używa powiązania danych natywnie do utrzymania stanu właściwości zgodnie z innymi właściwościami stanu i wywołaniami metody. Inną przykładowa właściwość, która wiąże <xref:System.Windows.Data.BindingMode.TwoWay> się domyślnie jest <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Dziedziczenie właściwości można również włączyć we właściwości <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> zależności niestandardowej, ustawiając flagę. Dziedziczenie właściwości jest przydatne w scenariuszu, w którym elementy nadrzędne i elementy podrzędne mają wspólną właściwość i ma sens dla elementów podrzędnych, aby mieć tę wartość określonej właściwości ustawioną na taką samą wartość, jak element nadrzędny. Przykładem właściwości dziedzicznej jest <xref:System.Windows.FrameworkElement.DataContext%2A>, który jest używany do operacji wiązania, aby włączyć ważny scenariusz szczegółów wzorcowych dla prezentacji danych. Poprzez <xref:System.Windows.FrameworkElement.DataContext%2A> dziedziczenie, wszystkie elementy podrzędne dziedziczą ten kontekst danych również. Ze względu na dziedziczenie wartości właściwości można określić kontekst danych na stronie lub katalogu głównym aplikacji i nie trzeba ponownie określić go dla powiązań we wszystkich możliwych elementów podrzędnych. <xref:System.Windows.FrameworkElement.DataContext%2A>jest również dobrym przykładem, aby zilustrować, że dziedziczenie zastępuje wartość domyślną, ale zawsze można ustawić lokalnie na dowolny element podrzędny określonego; aby uzyskać szczegółowe informacje, zobacz [Użyj wzorca szczegółów wzorca z danymi hierarchicznymi](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dziedziczenie wartości właściwości ma możliwy koszt wydajności, a zatem powinny być używane oszczędnie; aby uzyskać szczegółowe informacje, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).

- Ustaw <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> flagę, aby wskazać, czy właściwość zależności powinna być wykrywana lub używana przez usługi rejestrowania nawigacji. Przykładem <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> jest właściwość; każdy element wybrany w formancie wyboru powinien być utrwalony podczas przechodzenia nawigowanie po historii dziennika.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu

Można zdefiniować właściwość zależności, która jest tylko do odczytu. Jednak scenariusze, dlaczego można zdefiniować właściwość jako tylko do odczytu są nieco różne, podobnie jak procedura rejestrowania ich w systemie właściwości i uwidaczniania identyfikatora. Aby uzyskać więcej informacji, zobacz [Właściwości zależności tylko do odczytu](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji

Właściwości zależności typu kolekcji mają pewne dodatkowe problemy z implementacją do rozważenia. Aby uzyskać szczegółowe informacje, zobacz [Właściwości zależności typu kolekcji](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń właściwości zależności

Właściwości zależności powinny być zadeklarowane jako właściwości publiczne. Pola identyfikatora właściwości zależności powinny być zadeklarowane jako publiczne pola statyczne. Nawet jeśli spróbujesz zadeklarować inne poziomy dostępu (takie jak chronione), właściwość zależności zawsze jest dostępna za pośrednictwem identyfikatora w połączeniu z interfejsami API systemu właściwości. Nawet chronione pole identyfikatora jest potencjalnie dostępne z powodu raportowania metadanych lub określania <xref:System.Windows.LocalValueEnumerator>wartości interfejsów API, które są częścią systemu właściwości, takich jak . Aby uzyskać więcej informacji, zobacz [Bezpieczeństwo właściwości zależności](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Właściwości zależności i konstruktory klas

Istnieje ogólna zasada w programowaniu kodu zarządzanego (często wymuszane przez narzędzia analizy kodu, takie jak FxCop), że konstruktory klas nie powinny wywoływać metod wirtualnych. Dzieje się tak, ponieważ konstruktory mogą być wywoływane jako inicjowanie podstawowe konstruktora klasy pochodnej i wprowadzanie metody wirtualnej za pośrednictwem konstruktora może wystąpić w stanie niekompletnego inicjowania wywoływanego wystąpienia obiektu, które jest konstruowane. Po wyprowadzeniu z dowolnej klasy, która już pochodzi od <xref:System.Windows.DependencyObject>, należy pamiętać, że system właściwości sam wywołuje i udostępnia metody wirtualne wewnętrznie. Te metody wirtualne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są częścią usług systemu właściwości. Zastępowanie metod umożliwia klas pochodnych do udziału w określaniu wartości. Aby uniknąć potencjalnych problemów z inicjowania środowiska uruchomieniowego, nie należy ustawiać wartości właściwości zależności w konstruktorach klas, chyba że należy wykonać bardzo określonego wzorca konstruktora. Aby uzyskać szczegółowe informacje, zobacz [Bezpieczne wzorce konstruktora dla dependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Zobacz też

- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Właściwości zależności typu kolekcji](collection-type-dependency-properties.md)
- [Zabezpieczenie właściwości zależności](dependency-property-security.md)
- [Właściwości zależności i ładowania XAML](xaml-loading-and-dependency-properties.md)
- [Bezpieczne wzorce konstruktora DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
