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
ms.openlocfilehash: 1352876b79e103d20d08382ab088f7777c6fe2ae
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401568"
---
# <a name="custom-dependency-properties"></a>Niestandardowe właściwości zależności

W tym temacie opisano przyczyny, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dla których deweloperzy aplikacji i autorzy składników mogą chcieć utworzyć niestandardową właściwość zależności, oraz opisano kroki implementacji, a także niektóre opcje implementacji, które mogą zwiększyć wydajność. użyteczność lub uniwersalność właściwości.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zależności w klasach, i zapoznaj się z tematem [Omówienie właściwości zależności](dependency-properties-overview.md) . Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak pisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co to jest właściwość zależności?

W przeciwnym razie można włączyć właściwość środowiska uruchomieniowego języka wspólnego (CLR) do obsługi stylów, powiązań danych, dziedziczenia, animacji i wartości domyślnych, implementując ją jako właściwość zależności. Właściwości zależności to właściwości, które są zarejestrowane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemie właściwości przez <xref:System.Windows.DependencyProperty.Register%2A> wywołanie metody (lub <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> <xref:System.Windows.DependencyProperty> ) i które są obsługiwane przez pole identyfikatora. Właściwości zależności mogą być używane tylko przez <xref:System.Windows.DependencyObject> typy, ale <xref:System.Windows.DependencyObject> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są dość duże w hierarchii klas, dzięki czemu większość klas dostępnych w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może obsługiwać właściwości zależności. Aby uzyskać więcej informacji na temat właściwości zależności i niektórych terminologii i Konwencji używanych do opisywania ich w [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]tym artykule, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Przykłady właściwości zależności

Przykłady właściwości zależności, które są implementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w klasach <xref:System.Windows.Controls.Control.Background%2A> obejmują Właściwość <xref:System.Windows.FrameworkElement.Width%2A> , właściwość i <xref:System.Windows.Controls.TextBox.Text%2A> właściwość, między wieloma innymi. Każda właściwość zależności udostępniona przez klasę ma odpowiednie publiczne pole statyczne typu <xref:System.Windows.DependencyProperty> uwidocznione na tej samej klasie. To jest identyfikator właściwości zależności. Identyfikator jest nazwany przy użyciu konwencji: Nazwa właściwości zależności z dołączoną do niej ciągiem `Property` . Na przykład odpowiednie <xref:System.Windows.DependencyProperty> pole identyfikatora <xref:System.Windows.Controls.Control.Background%2A> dla właściwości to <xref:System.Windows.Controls.Control.BackgroundProperty>. Identyfikator przechowuje informacje o właściwości zależności podczas rejestracji, a następnie identyfikator jest później używany do innych operacji obejmujących właściwość zależności, takich jak wywołanie <xref:System.Windows.DependencyObject.SetValue%2A>.

Jak wspomniano we właściwościach [zależności](dependency-properties-overview.md), wszystkie właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (z wyjątkiem większości dołączonych właściwości) są również właściwościami CLR ze względu na implementację "otoka". Z tego względu kod można pobrać lub ustawić właściwości zależności przez wywołanie metod dostępu CLR, które definiują otoki w taki sam sposób, jak w przypadku innych właściwości środowiska CLR. Jako odbiorca ustanowionych właściwości zależności nie są zwykle używane <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>, które są punktem połączenia z systemem właściwości bazowe. Zamiast tego istniejąca implementacja właściwości CLR zostanie <xref:System.Windows.DependencyObject.GetValue%2A> już wywołana i <xref:System.Windows.DependencyObject.SetValue%2A> w ramach implementacji otoki `get` i `set` w ramach tej właściwości, odpowiednio przy użyciu pola identyfikatora. Jeśli samodzielnie implementujesz niestandardową właściwość zależności, będziesz definiować otokę w podobny sposób.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Kiedy należy zaimplementować właściwość zależności?

Podczas implementowania właściwości w klasie, tak długo, jak Klasa pochodzi z <xref:System.Windows.DependencyObject>, istnieje możliwość utworzenia kopii zapasowej właściwości <xref:System.Windows.DependencyProperty> z identyfikatorem i w związku z tym, aby uczynić ją właściwością zależności. Właściwość zależności nie zawsze jest konieczna lub odpowiednia i będzie zależeć od potrzeb scenariusza. Czasami zwykle jest to typowa technika tworzenia kopii zapasowej właściwości przy użyciu pola prywatnego. Należy jednak zaimplementować właściwość jako właściwość zależności za każdym razem, gdy właściwość ma obsługiwać co najmniej jedną z następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] możliwości:

- Chcesz, aby właściwość była settable w stylu. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).

- Chcesz, aby Twoja Właściwość obsługiwała powiązanie danych. Aby uzyskać więcej informacji na temat właściwości zależności powiązań danych, zobacz [Powiązywanie właściwości dwóch kontrolek](../data/how-to-bind-the-properties-of-two-controls.md).

- Właściwość ma być ustawiana na wartość settable z odwołaniem do zasobu dynamicznego. Aby uzyskać więcej informacji, zobacz [zasoby XAML](xaml-resources.md).

- Chcesz automatycznie dziedziczyć wartość właściwości z elementu nadrzędnego w drzewie elementów. W takim przypadku należy zarejestrować się przy <xref:System.Windows.DependencyProperty.RegisterAttached%2A> użyciu metody, nawet jeśli zostanie również utworzona otoka właściwości dla dostępu CLR. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).

- Właściwość ma być animowana. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

- Ten system właściwości ma raportować, gdy Poprzednia wartość właściwości została zmieniona przez akcje podejmowane przez system właściwości, środowisko lub użytkownika albo przez odczytanie i użycie stylów. Za pomocą metadanych właściwości, właściwość może określić metodę wywołania zwrotnego, która będzie wywoływana za każdym razem, gdy system właściwości ustali, że wartość właściwości została ostatecznie zmieniona. Koncepcja pokrewna to wartość właściwości. Aby uzyskać więcej informacji, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md).

- Chcesz użyć ustalonych Konwencji metadanych, które są również używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesy, takie jak raportowanie, czy zmiana wartości właściwości powinna wymagać od systemu układu przetworzenia wizualizacji dla elementu. Lub chcesz mieć możliwość użycia zastąpień metadanych, aby klasy pochodne mogły zmieniać właściwości oparte na metadanych, takie jak wartość domyślna.

- Chcesz, aby właściwości kontrolki niestandardowej otrzymywały wsparcie projektanta Visual Studio WPF, takie jak edytowanie okna **Właściwości** . Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).

Analizując te scenariusze, należy również rozważyć, czy można osiągnąć swój scenariusz, zastępując metadane istniejącej właściwości zależności, a nie implementując całkowicie nową właściwość. Określa, czy zastępowanie metadanych jest praktyczne, zależy od danego scenariusza i jak ściśle ten scenariusz jest podobny do implementacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] we właściwościach zależności i klas. Aby uzyskać więcej informacji na temat zastępowania metadanych dla istniejących właściwości, zobacz [metadane właściwości zależności](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Lista kontrolna służąca do definiowania właściwości zależności

Definiowanie właściwości zależności obejmuje cztery różne koncepcje. Te pojęcia nie są koniecznie rygorystycznych kroków proceduralnych, ponieważ niektóre z nich są łączone jako pojedyncze wiersze kodu w implementacji:

- Obowiązkowe Utwórz metadane właściwości dla właściwości zależności.

- Zarejestruj nazwę właściwości w systemie właściwości, określając typ właściciela i typ wartości właściwości. Określ także metadane właściwości, jeśli są używane.

- <xref:System.Windows.DependencyProperty> Zdefiniuj identyfikator `public` jako`static` pole typu`readonly` właściciel.

- Zdefiniuj Właściwość "otoka" środowiska CLR, której nazwa jest zgodna z nazwą właściwości zależności. Zaimplementuj Właściwość `get` "otoka" środowiska CLR `set` i metody dostępu, aby połączyć się z właściwością zależności, która ją wykonuje.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Rejestrowanie właściwości przy użyciu systemu właściwości

Aby właściwość była właściwością zależności, należy zarejestrować tę właściwość w tabeli utrzymywanej przez system właściwości i nadać jej unikatowy identyfikator, który jest używany jako kwalifikator dla późniejszych operacji systemu właściwości. Te operacje mogą być operacjami wewnętrznymi lub własnym kodem wywołującym interfejsy API systemu właściwości. Aby zarejestrować właściwość, należy wywołać <xref:System.Windows.DependencyProperty.Register%2A> metodę w treści klasy (wewnątrz klasy, ale poza wszystkimi definicjami elementów członkowskich). Pole identyfikatora jest również udostępniane przez <xref:System.Windows.DependencyProperty.Register%2A> wywołanie metody jako wartość zwracaną. Powodem, że <xref:System.Windows.DependencyProperty.Register%2A> wywołanie jest wykonywane poza innymi definicjami elementów członkowskich, jest użycie tej wartości zwracanej do przypisania i `readonly` `public` `static` utworzenia pola typu <xref:System.Windows.DependencyProperty> jako części klasy. To pole jest identyfikatorem właściwości zależności.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konwencje nazw właściwości zależności

Istnieją ustalone konwencje nazewnictwa dotyczące właściwości zależności, które należy wykonać we wszystkich, ale wyjątkowych okolicznościach.

Sama właściwość zależności będzie miała podstawową nazwę "AquariumGraphic", jak w tym przykładzie, która jest podawana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A>. Ta nazwa musi być unikatowa w obrębie każdego typu rejestrowania. Właściwości zależności dziedziczone za pomocą typów podstawowych są uznawane za należące już do typu rejestrowania; nie można ponownie zarejestrować nazw dziedziczonych właściwości. Istnieje jednak technika dodawania klasy jako właściciela właściwości zależności nawet wtedy, gdy ta właściwość zależności nie jest dziedziczona; Aby uzyskać szczegółowe informacje, zobacz [metadane właściwości zależności](dependency-property-metadata.md).

Po utworzeniu pola identyfikatora Nazwij to pole za pomocą nazwy właściwości, która została zarejestrowana, oraz sufiksu `Property`. To pole jest identyfikatorem właściwości zależności i będzie używane później jako dane wejściowe dla <xref:System.Windows.DependencyObject.SetValue%2A> wywołań i <xref:System.Windows.DependencyObject.GetValue%2A> wywoływanych w otokach, przez każdy inny dostęp kodu do właściwości przez własny kod, przez dowolny dostęp do kodu zewnętrznego. , przez system właściwości i potencjalnie przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesory.

> [!NOTE]
> Definiowanie właściwości zależności w treści klasy jest typową implementacją, ale można również zdefiniować właściwość zależności w konstruktorze statycznym klasy. Takie podejście może mieć sens, jeśli potrzebujesz więcej niż jednego wiersza kodu w celu zainicjowania właściwości zależności.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementacja "otoki"

Implementacja otoki powinna być <xref:System.Windows.DependencyObject.GetValue%2A> wywoływana `get` w `set` implementacji, a <xref:System.Windows.DependencyObject.SetValue%2A> w implementacji (oryginalne połączenie i pole rejestracji są wyświetlane w tym miejscu również na potrzeby przejrzystości).

We wszystkich ale wyjątkowych okolicznościach implementacje otoki powinny odpowiednio wykonywać tylko <xref:System.Windows.DependencyObject.GetValue%2A> akcje <xref:System.Windows.DependencyObject.SetValue%2A> i. Przyczyna tego problemu została omówiona w temacie [Właściwości ładowania i zależności języka XAML](xaml-loading-and-dependency-properties.md).

Wszystkie istniejące właściwości zależności publicznej, które są dostępne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasach, używają tego prostego modelu implementacji otoki; większość złożoności działania właściwości zależności jest zależne od zachowania systemu właściwości lub jest implementowane przy użyciu innych koncepcji, takich jak wymuszone lub zmiany właściwości wywołania zwrotnego za poorednictwem metadanych właściwości.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Ponownie zgodnie z Konwencją nazwa właściwości otoki musi być taka sama jak nazwa wybrana i określona jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A> wywołania, które zarejestrował właściwość. Jeśli właściwość nie jest zgodna z Konwencją, nie należy wyłączać wszystkich możliwych użycia, ale wystąpi kilka istotnych problemów:

- Niektóre aspekty stylów i szablonów nie będą działały.

- Większość narzędzi i projektantów musi opierać się na konwencjach nazewnictwa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aby prawidłowo serializować, lub aby zapewnić pomoc dla środowiska projektanta na poziomie właściwości.

- Bieżąca implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego całkowicie pomija otoke i opiera się na konwencji nazewnictwa podczas przetwarzania wartości atrybutów. Aby uzyskać więcej informacji, zobacz temat [Właściwości ładowania i zależności XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadane właściwości dla nowej właściwości zależności

Po zarejestrowaniu właściwości zależności Rejestracja za pomocą systemu właściwości tworzy obiekt metadanych, który przechowuje charakterystyki właściwości. Wiele z tych cech ma ustawione wartości domyślne, jeśli właściwość jest zarejestrowana przy użyciu prostych podpisów <xref:System.Windows.DependencyProperty.Register%2A>. Inne podpisy <xref:System.Windows.DependencyProperty.Register%2A> umożliwiają określenie metadanych, które mają być rejestrowane podczas rejestrowania właściwości. Najczęstszymi metadanymi podaną dla właściwości zależności jest nadanie im wartości domyślnej stosowanej w nowych wystąpieniach, które używają właściwości.

Jeśli tworzysz właściwość zależności, która istnieje w klasie <xref:System.Windows.FrameworkElement>pochodnej, można użyć bardziej wyspecjalizowanej klasy <xref:System.Windows.FrameworkPropertyMetadata> metadanych zamiast klasy bazowej <xref:System.Windows.PropertyMetadata> . Konstruktor dla <xref:System.Windows.FrameworkPropertyMetadata> klasy ma kilka podpisów, w których można określić różne charakterystyki metadanych. Jeśli chcesz określić tylko wartość domyślną, Użyj podpisu, który przyjmuje jeden parametr typu <xref:System.Object>. Przekaż ten parametr obiektu jako wartość domyślną specyficzną dla danej właściwości (podana wartość domyślna musi być typem dostarczonym jako `propertyType` parametr <xref:System.Windows.DependencyProperty.Register%2A> w wywołaniu).

Dla <xref:System.Windows.FrameworkPropertyMetadata>programu można także określić flagi opcji metadanych dla właściwości. Te flagi są konwertowane na właściwości dyskretne w metadanych właściwości po rejestracji i są używane do komunikowania pewnych warunków z innymi procesami, takimi jak aparat układu.

#### <a name="setting-appropriate-metadata-flags"></a>Ustawianie odpowiednich flag metadanych

- Jeśli właściwość (lub zmiany w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]jej wartości) wpływa na, a w szczególności ma wpływ na to, w jaki sposób system układu ma rozmiar lub renderuje element na stronie, należy ustawić co najmniej jedną z następujących flag: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>wskazuje, że zmiana tej właściwości wymaga zmiany w celu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, gdzie obiekt zawierający może wymagać więcej lub mniej miejsca w obrębie elementu nadrzędnego. Na przykład właściwość "width" powinna mieć ustawioną tę flagę.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>wskazuje, że zmiana tej właściwości wymaga zmiany w celu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, która zwykle nie wymaga zmiany w dedykowanym miejscu, ale wskazuje, że pozycjonowanie w miejscu zostało zmienione. Na przykład właściwość "Alignment" powinna mieć tę flagę.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>wskazuje, że wystąpiła inna zmiana, która nie ma wpływu na układ i miarę, ale wymaga innego renderowania. Przykładem może być właściwość, która zmienia kolor istniejącego elementu, na przykład "background".

  - Te flagi są często używane jako protokół w metadanych dla własnych implementacji przesłonięcia systemu właściwości lub wywołania zwrotnego układu. <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> Na przykład może istnieć wywołanie zwrotne, które zostanie wywołane <xref:System.Windows.UIElement.InvalidateArrange%2A> , jeśli jakakolwiek Właściwość wystąpienia zgłasza zmianę wartości i ma <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> tak jak `true` w metadanych.

- Niektóre właściwości mogą mieć wpływ na charakterystykę renderowania zawierającego element nadrzędny, w powyższych sposób i poza zmiany w wymaganym rozmiarze wymienionym powyżej. Przykładem jest <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> Właściwość użyta w modelu dokumentu przepływu, gdzie zmiany tej właściwości mogą zmienić ogólne renderowanie dokumentu przepływu, który zawiera akapit. Użyj <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> lub<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> , aby zidentyfikować podobne przypadki we własnych właściwościach.

- Domyślnie właściwości zależności obsługują powiązanie danych. Można celowo wyłączyć powiązanie danych, w przypadku gdy nie istnieje realistyczny scenariusz dla powiązania danych lub w przypadku, gdy wydajność w powiązaniu danych dla dużego obiektu jest rozpoznawana jako problem.

- Domyślnie powiązanie <xref:System.Windows.Data.Binding.Mode%2A> danych dla właściwości zależności ma <xref:System.Windows.Data.BindingMode.OneWay>wartość domyślną. Można zawsze zmienić powiązanie na <xref:System.Windows.Data.BindingMode.TwoWay> wystąpienie powiązania. Aby uzyskać szczegółowe informacje, zobacz [Określanie kierunku powiązania](../data/how-to-specify-the-direction-of-the-binding.md). Ale jako autor właściwości zależności można wybrać opcję domyślnego użycia <xref:System.Windows.Data.BindingMode.TwoWay> trybu powiązania. Przykładem istniejącej właściwości zależności jest <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scenariusz dla tej właściwości polega na <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> tym, że <xref:System.Windows.Controls.MenuItem> logika ustawienia i przedniego praca z domyślnym stylem motywu. Logika <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> właściwości używa powiązania danych natywnie do utrzymania stanu właściwości zgodnie z innymi właściwościami stanu i wywołaniami metod. Inna Przykładowa właściwość, która <xref:System.Windows.Data.BindingMode.TwoWay> domyślnie tworzy powiązanie <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>, to.

- Dziedziczenie właściwości można także włączyć we właściwości zależności niestandardowej przez ustawienie <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> flagi. Dziedziczenie właściwości jest przydatne w przypadku scenariusza, w którym elementy nadrzędne i podrzędne mają wspólną właściwość, i mają sens dla elementów podrzędnych, aby mieć ustawioną taką samą wartość właściwości, co ustawienie nadrzędne. Przykładową właściwością dziedziczenia <xref:System.Windows.FrameworkElement.DataContext%2A>jest, która jest używana na potrzeby operacji wiązania w celu włączenia ważnego scenariusza wzorca szczegółowości dla prezentacji danych. <xref:System.Windows.FrameworkElement.DataContext%2A> Dzięki dziedziczeniu wszystkie elementy podrzędne dziedziczą również ten kontekst danych. Ze względu na dziedziczenie wartości właściwości można określić kontekst danych na stronie lub w katalogu głównym aplikacji, a nie trzeba go ponownie określić dla powiązań we wszystkich możliwych elementach podrzędnych. <xref:System.Windows.FrameworkElement.DataContext%2A>jest również dobrym przykładem, aby zilustrować, że dziedziczenie przesłania wartość domyślną, ale zawsze można ją ustawić lokalnie dla każdego określonego elementu podrzędnego. Aby uzyskać szczegółowe informacje, zobacz [Używanie wzorca master-detail z danymi hierarchicznymi](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dziedziczenie wartości właściwości ma możliwy koszt wydajności i dlatego powinno być używane oszczędnie. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).

- Ustaw flagę, <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> aby wskazać, czy właściwość zależności ma zostać wykryta lub użyta przez usługi rejestrowania nawigacji. Przykładem jest <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> Właściwość; wszelkie elementy wybrane w kontrolce wyboru powinny być utrwalane, gdy historia rejestrowania jest przechodzenie.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu

Można zdefiniować właściwość zależności, która jest tylko do odczytu. Jednak scenariusze, dla których można zdefiniować właściwość jako tylko do odczytu, różnią się w zależności od procedury rejestrowania ich w systemie właściwości i ujawniania identyfikatora. Aby uzyskać więcej informacji, zobacz [właściwości zależności tylko do odczytu](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji

Właściwości zależności typu kolekcji zawierają kilka dodatkowych problemów z implementacją, które należy wziąć pod uwagę. Aby uzyskać szczegółowe informacje, zobacz [właściwości zależności typu kolekcji](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń właściwości zależności

Właściwości zależności powinny być deklarowane jako właściwości publiczne. Pola identyfikatora właściwości zależności powinny być deklarowane jako publiczne pola statyczne. Nawet jeśli podjęto próbę zadeklarować inne poziomy dostępu (na przykład chronione), do właściwości zależności można zawsze uzyskać dostęp za pomocą identyfikatora w połączeniu z interfejsami API systemu właściwości. Nawet pole identyfikatora chronionego jest potencjalnie dostępne ze względu na raportowanie metadanych lub interfejsy API określania wartości, które są częścią systemu właściwości <xref:System.Windows.LocalValueEnumerator>, na przykład. Aby uzyskać więcej informacji, zobacz temat [Ochrona właściwości zależności](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Właściwości zależności i konstruktory klas

Istnieje ogólna zasada programowania kodu zarządzanego (często wymuszane przez narzędzia do analizy kodu, takie jak FxCop), które konstruktory klas nie powinny wywoływanie metod wirtualnych. Wynika to z faktu, że konstruktory mogą być wywoływane jako podstawowe inicjujące Konstruktor klasy pochodnej i wprowadzanie metody wirtualnej za pomocą konstruktora może wystąpić z niekompletnym stanem inicjalizacji konstruowanego wystąpienia obiektu. Gdy pochodzą z klasy, która już pochodzi z <xref:System.Windows.DependencyObject>, należy pamiętać, że system właściwości wywołuje i udostępnia metody wirtualne wewnętrznie. Te metody wirtualne są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług systemu właściwości. Zastąpienie metod umożliwia klasom pochodnym uczestnictwo w wyznaczania wartości. Aby uniknąć potencjalnych problemów z inicjalizacją środowiska uruchomieniowego, nie należy ustawiać wartości właściwości zależności w konstruktorach klas, chyba że jest on zgodny z bardzo specyficznym wzorcem konstruktora. Aby uzyskać szczegółowe informacje, zobacz [bezpieczne wzorce konstruktorów dla DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Właściwości zależności typu kolekcji](collection-type-dependency-properties.md)
- [Zabezpieczenia właściwości zależności](dependency-property-security.md)
- [Ładowanie XAML i właściwości zależności](xaml-loading-and-dependency-properties.md)
- [Bezpieczne wzorce konstruktora dla obiektów DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
