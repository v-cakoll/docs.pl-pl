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
ms.openlocfilehash: f15490417d54121c750e2ea918820c5cb717002e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468327"
---
# <a name="custom-dependency-properties"></a>Niestandardowe właściwości zależności

W tym temacie opisano przyczyny, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programistom autorzy składnika może zajść potrzeba utworzenia zależności niestandardowej właściwości i w tym artykule opisano kroki implementacji, a także niektóre opcje implementacji, które może poprawić wydajność, użyteczność lub wszechstronność właściwości.

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne

W tym temacie założono, że rozumiesz właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, a po ich przeczytaniu [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) tematu. Aby można było wykonać instrukcje opisane w przykładach w tym temacie, należy również mieć świadomość [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wiedzieć, jak napisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.

<a name="whatis"></a>
## <a name="what-is-a-dependency-property"></a>Co to jest właściwość zależności?

Można włączyć, co byłoby [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości do obsługi stylów, powiązań danych, dziedziczenie, animacji i wartości domyślne, wdrażając go jako właściwość zależności. Właściwości zależności są właściwościami, które są zarejestrowane w usłudze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu, wywołując <xref:System.Windows.DependencyProperty.Register%2A> — metoda (lub <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), i które są objęte <xref:System.Windows.DependencyProperty> pole identyfikatora. Właściwości zależności, które mogą być używane tylko przez <xref:System.Windows.DependencyObject> typów, ale <xref:System.Windows.DependencyObject> jest bardzo duże w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy hierarchii, dzięki czemu większość klas dostępne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może obsługiwać właściwości zależności. Aby uzyskać więcej informacji na temat właściwości zależności i niektóre terminy i Konwencji używanych do opisywania je w tym [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).

<a name="example_dp"></a>
## <a name="examples-of-dependency-properties"></a>Przykłady właściwości zależności

Przykłady właściwości zależności, które są implementowane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy mają <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.Controls.TextBox.Text%2A> właściwości wśród wielu innych. Każda właściwość zależności, udostępnianych przez klasę ma odpowiednie publiczne pole statyczne typu <xref:System.Windows.DependencyProperty> widoczne na tej samej klasy. Jest to identyfikator dla właściwości zależności. Identyfikator nosi nazwę przy użyciu Konwencji: Nazwa właściwości zależności z ciągiem `Property` dołączone do niego. Na przykład odpowiednie <xref:System.Windows.DependencyProperty> pole identyfikatora dla <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.Control.BackgroundProperty>. Identyfikator przechowuje informacje o właściwości zależności, ponieważ został on zarejestrowany i identyfikator jest następnie używany w dalszej części na inne operacje dotyczące właściwości zależności, takich jak wywoływanie <xref:System.Windows.DependencyObject.SetValue%2A>.

Jak wspomniano w [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), wszystkie właściwości zależności w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (z wyjątkiem właściwości najbardziej dołączone) są również [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości ze względu na implementację "otoki". W związku z kodu, można uzyskać lub ustawić właściwości zależności, wywołując [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] metod dostępu, które definiują otoki w taki sam sposób, w których możesz użyć innych [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości. Jako użytkownik właściwości ustalonych zależności nie zwykle jest używana <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A>, które są punkt połączenia z podstawowym systemie właściwości. Zamiast istniejącą implementację programu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwości mają już wywołana <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> w ramach `get` i `set` otoki implementacji właściwości, korzystając z pola Identyfikator odpowiednio . W przypadku wdrażania właściwość zależności niestandardowej samodzielnie, następnie będzie zdefiniowanie jest otoki w podobny sposób.

<a name="backing_with_dp"></a>
## <a name="when-should-you-implement-a-dependency-property"></a>Kiedy należy implementować właściwość zależności

Podczas implementacji właściwości w klasie, tak długo, jak klasa pochodzi od klasy <xref:System.Windows.DependencyObject>, istnieje możliwość kopii Twoja własność z <xref:System.Windows.DependencyProperty> identyfikator i w związku z tym się właściwość zależności. Posiadanie Twoja własność jest właściwość zależności nie zawsze jest konieczne lub właściwe i będzie zależeć od wymagań scenariusza. Czasami typowych technik zapisywania kopii usługi właściwość z polem prywatnego jest odpowiednie. Jednakże, należy zaimplementować Twoja własność jako właściwość zależności zawsze wtedy, gdy chcesz, aby Twoja własność do obsługi co najmniej jeden z następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] możliwości:

-   Chcesz, aby Twoje właściwości można ustawić w stylu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).

-   Chcesz, aby Twoje właściwość obsługuje powiązanie danych. Aby uzyskać więcej informacji na temat właściwości zależności powiązania danych, zobacz [powiązywanie właściwości dwóch formantów](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).

-   Chcesz, aby Twoje właściwości do ustawienia z odwołaniem do zasobu dynamicznego. Aby uzyskać więcej informacji, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

-   Chcesz automatycznie dziedziczy wartości właściwości z elementu nadrzędnego w drzewie elementów. W tym przypadku zarejestrowanie <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody, nawet jeśli można również utworzyć otokę właściwości dla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dostępu. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

-   Chcesz, aby Twoje animatable właściwości. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).

-   Chcesz system właściwości raportu, gdy poprzednią wartość właściwości został zmieniony przez akcje wykonywane przez system właściwości środowiska i użytkownika lub przez czytanie i korzystanie ze stylów. Za pomocą metadanych właściwości modelu, Twoja własność można określić metodę wywołania zwrotnego, który zostanie wywołany, każdym razem, gdy system właściwości określa, że ostatecznie zmieniono wartość właściwości. Innym pojęciem jest przekształcenie wartości właściwości. Aby uzyskać więcej informacji, zobacz [zależność wartości wywołania zwrotnego i walidacji](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).

-   Chcesz używać konwencji ustanowionych metadane są również używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesy, takie jak raportowanie czy zmiana wartości właściwości powinny wymagać system układu, aby przeskładać wizualizacji dla elementu. Lub aby móc korzystać z zastąpień metadanych tak, aby w klasach pochodnych można zmienić na podstawie metadanych cechami, takimi jak wartość domyślna.

-   Chcesz obsługują właściwości formantu niestandardowego do odbierania projektanta WPF w usłudze Visual Studio, takie jak **właściwości** okna do edycji. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

Podczas badania tych scenariuszy należy również rozważyć, czy dany scenariusz można osiągnąć przez zastępowanie metadanych istniejącej właściwości zależności, a nie Implementowanie całkowicie nową właściwość. Czy jest możliwe zastąpienie metadanych zależy od danego scenariusza, jak blisko tego scenariusza podobny implementacji w istniejących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy i właściwości zależności. Aby uzyskać więcej informacji na temat Zastępowanie metadanych właściwości istniejących zobacz [metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

<a name="checklist"></a>
## <a name="checklist-for-defining-a-dependency-property"></a>Lista kontrolna dotycząca Definiowanie właściwości zależności

Definiowanie właściwości zależności składa się z czterech różnych pojęcia. Te pojęcia nie są zawsze strict kroki procedur, ponieważ niektóre z nich znajdą się łączonych jako pojedynczej linii kodu w implementacji:

-   (Opcjonalnie) Utwórz właściwość metadane dla właściwości zależności.

-   Zarejestruj nazwy właściwości w systemie właściwości, określając typ właściciela i typ wartości właściwości. Jeśli używane, również określić metadane właściwości.

-   Zdefiniuj <xref:System.Windows.DependencyProperty> identyfikator `public` `static` `readonly` na typ właściciela.

-   Zdefiniuj [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość "otoki", którego nazwa jest zgodna z nazwą właściwości zależności. Implementowanie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość "otoki" `get` i `set` metod dostępu do łączenia z właściwości zależności, które określi ją.

<a name="registering"></a>
### <a name="registering-the-property-with-the-property-system"></a>Rejestrowanie właściwości w systemie właściwości

Aby Twoja własność właściwość zależności musisz zarejestrować tę właściwość do tabeli obsługiwanego przez system właściwości i nadaj mu unikatowy identyfikator, który jest używany jako kwalifikator dla późniejszych operacji systemu właściwości. Te operacje mogą być operacji wewnętrznych lub własnego kodu właściwości systemu podczas wywoływania [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Aby zarejestrować właściwość, należy wywołać <xref:System.Windows.DependencyProperty.Register%2A> metody w treści klasy (wewnątrz klasy, ale poza wszystkie definicje elementów członkowskich). Pole identyfikatora również odbywa się przy <xref:System.Windows.DependencyProperty.Register%2A> wywołania metody, jako wartość zwracaną. Przyczyna, <xref:System.Windows.DependencyProperty.Register%2A> wywołanie jest wykonywane poza innego członka definicji jest, ponieważ umożliwia to wartość zwracana przypisać i utworzyć `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty> jako część swojej klasy. To pole staje się na identyfikator swojej właściwości zależności.

[!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>
### <a name="dependency-property-name-conventions"></a>Konwencje nazw właściwości zależności

Brak ustanowionych konwencji nazewnictwa dotyczące właściwości zależności, które należy wykonać we wszystkich ale wyjątkowych okolicznościach.

Właściwości zależności, sama mają nazwy podstawowe, "AquariumGraphic", jak w poniższym przykładzie jest podawana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tej nazwy musi być unikatowa w obrębie każdego typu rejestrowania. Właściwości zależności dziedziczone typy podstawowe są traktowane jako już jako część rejestrowania typu Nie można ponownie zarejestrować nazwy właściwości dziedziczonych. Istnieje jednak technika Dodawanie klasy jako właściciel właściwości zależności, nawet wtedy, gdy nie jest dziedziczony tę właściwość zależności; Aby uzyskać więcej informacji, zobacz [metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

Podczas tworzenia pola Identyfikator nadaj nazwę tego pola, nazwa właściwości zarejestrowanej oraz sufiks `Property`. To pole jest identyfikatora właściwości zależności, a zostanie on użyty później jako dane wejściowe na potrzeby <xref:System.Windows.DependencyObject.SetValue%2A> i <xref:System.Windows.DependencyObject.GetValue%2A> wywołania wprowadzisz w otoki, wszelkie inne kodu dostępu do właściwość, według własnego kodu przez dostępu zewnętrznego kodu możesz zezwolić , przez system właściwości i potencjalnie przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorów.

> [!NOTE]
> Definiowanie właściwości zależności w treści klasy jest typowa implementacja, ale jest również możliwość zdefiniowania właściwości zależności w konstruktorze klasy statycznej. Takie podejście może mieć sens, jeśli potrzebujesz więcej niż jeden wiersz kodu, aby zainicjować właściwość zależności.

<a name="wrapper1"></a>
### <a name="implementing-the-wrapper"></a>Implementowanie "Otoki"

Twoja implementacja otoki powinny wywoływać <xref:System.Windows.DependencyObject.GetValue%2A> w `get` implementacji i <xref:System.Windows.DependencyObject.SetValue%2A> w `set` implementacji (oryginalne wywołanie rejestracji i pola są wyświetlane w tym miejscu zbyt dla jasności).

W wszystkie elementy oprócz wyjątkowych okolicznościach, z implementacjami otoki należy wykonać tylko <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> akcji, odpowiednio. Przyczyną jest omówione w temacie [właściwości zależności i ładowania XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).

Wszystkich istniejących właściwości publicznej zależności, które znajdują się na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy użyć tego modelu implementacji otoki prostego; większość złożoność działania właściwości zależności jest to zachowanie systemu właściwości lub jest jest implementowane za pomocą innych pojęć, takich jak wymuszenia lub właściwość Zmienianie wywołań zwrotnych za pomocą metadanych właściwości modelu.

[!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Ponownie, zgodnie z Konwencją nazwa właściwości otoki musi być taka sama jak nazwa, zaznaczona, a podana jako pierwszy parametr <xref:System.Windows.DependencyProperty.Register%2A> wywołania, który zarejestrował właściwość. Jeśli Twoja własność nie jest zgodna z Konwencją, niekoniecznie Wyłącz wszystkie możliwe zastosowania, ale będą napotykać kilka istotnych kwestii:

-   Niektóre aspekty — style i szablony nie będą działać.

-   Większość narzędzi i projektanci muszą polegać na konwencji nazewnictwa do serializacji prawidłowo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], lub w celu zapewnienia środowiska projektowego pomocy na poziomie poszczególnych właściwości.

-   Bieżąca implementacja parametru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego całkowicie pomija otoki i opiera się na konwencji nazewnictwa, podczas przetwarzania wartości atrybutów. Aby uzyskać więcej informacji, zobacz [właściwości zależności i ładowania XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>
### <a name="property-metadata-for-a-new-dependency-property"></a>Metadane właściwości dla nowej właściwości zależności

Podczas rejestrowania właściwości zależności rejestracji za pośrednictwem systemu właściwości tworzy obiekt metadanych, który przechowuje właściwość właściwości. Wiele z tych cech mają wartości domyślne, które są ustawione, jeśli właściwość jest zarejestrowany prostymi sygnaturami z <xref:System.Windows.DependencyProperty.Register%2A>. Inne sygnatur <xref:System.Windows.DependencyProperty.Register%2A> pozwalają na określenie, jak zarejestrować właściwości metadanych. Najbardziej typowe metadane dla właściwości zależności jest ciągowych wartość domyślną, która jest stosowana na nowe wystąpienia, które należy użyć właściwości.

Podczas tworzenia właściwości zależności, która istnieje w klasie pochodnej z <xref:System.Windows.FrameworkElement>, można użyć bardziej wyspecjalizowane klasy metadanych <xref:System.Windows.FrameworkPropertyMetadata> zamiast base <xref:System.Windows.PropertyMetadata> klasy. Konstruktor <xref:System.Windows.FrameworkPropertyMetadata> klasa ma kilka sygnatur, w której można określić różne cechy metadanych w połączeniu. Jeśli chcesz określić wartość domyślną tylko za pomocą podpisu, która przyjmuje jeden parametr typu <xref:System.Object>. Przekaż ten parametru obiektu jako wartość domyślna typu dla swojej właściwości (wartość domyślna, pod warunkiem musi być typem, udostępniane jako `propertyType` parametru w <xref:System.Windows.DependencyProperty.Register%2A> wywołania).

Aby uzyskać <xref:System.Windows.FrameworkPropertyMetadata>, można również określić flagi opcji metadanych dla usługi właściwości. Te flagi są konwertowane na osobne właściwości metadanych właściwości modelu po rejestracji i są używane do komunikowania się niektórych warunkowych do innych procesów, takich jak aparat układu.

#### <a name="setting-appropriate-metadata-flags"></a>Ustawienie flagi odpowiednie metadane

-   Jeśli właściwość (lub zmiany w jego wartość) ma wpływ na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], a w szczególności ma wpływ na sposób system układu należy rozmiaru lub renderowanie z elementu na stronie ustawić jedną lub więcej z następujących flag: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> oznacza, że zmiana ta właściwość wymaga zmiany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, w którym obiektu zawierającego wymagać więcej lub mniej miejsca nadrzędnym. Na przykład właściwość "Szerokość" powinny mieć ten zestaw flag.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> oznacza, że zmiana ta właściwość wymaga zmiany [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderowania, które zwykle nie wymaga zmian w dedykowanym obszarze, ale wskazują, że położenie w obrębie przestrzeni została zmieniona. Na przykład właściwości "Wyrównania" powinny mieć ten zestaw flag.

    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> Wskazuje, że wystąpił niektórych innych zmian, który nie ma wpływu na układ i miary, ale wymagają innego renderowania. Przykładem może być właściwością, która zmienia kolor istniejącego elementu, na przykład "Tła".

    -   Te flagi są często używane jako protokół w metadanych dla własnych implementacji zastąpienie właściwości systemowych lub układ wywołań zwrotnych. Na przykład może być <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> wywołania zwrotnego, który będzie wybierany <xref:System.Windows.UIElement.InvalidateArrange%2A> Jeśli dowolnej właściwości wystąpienia raporty zmiana wartości i ma <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` w metadanych.

-   Niektóre właściwości może wpłynąć na charakterystykę renderowania zawierającego elementu nadrzędnego, w sposób niż zmiany w wymagany rozmiar wymienionych powyżej. Na przykład <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> właściwość używana w modelu dokument przepływu, gdzie zmiany tej właściwości można zmienić ogólną renderowania dokument przepływu, który zawiera akapitu. Użyj <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> lub <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> do identyfikowania podobnych przypadków własne właściwości.

-   Domyślnie właściwości zależności obsługuje powiązanie danych. Powiązanie danych, w przypadkach, można wyłączyć celowo, których nie realistyczny scenariusz dla powiązania danych lub w przypadku, gdy wydajność w powiązaniu danych dla dużego obiektu jest rozpoznawany jako problem.

-   Domyślnie powiązanie danych <xref:System.Windows.Data.Binding.Mode%2A> ma domyślnie wartość właściwości zależności <xref:System.Windows.Data.BindingMode.OneWay>. Powiązanie można zawsze zmienić <xref:System.Windows.Data.BindingMode.TwoWay> na wystąpienie obiektu binding; Aby uzyskać szczegółowe informacje, zobacz [określić kierunek łączenia](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md). Ale Autor właściwość zależności, można wybrać się właściwości użyj <xref:System.Windows.Data.BindingMode.TwoWay> tryb powiązania domyślnie. Na przykład istniejąca właściwość zależności <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scenariusz dla tej właściwości jest to, że <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> ustawienie logikę i składania z <xref:System.Windows.Controls.MenuItem> wchodzić w interakcje ze stylem motyw domyślny. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Logiki właściwość używa powiązanie danych natywnie w celu zapewnienia stanu właściwości zgodnie z innych wywołań metod i właściwości stanu. Inna właściwość przykładu, który wiąże <xref:System.Windows.Data.BindingMode.TwoWay> domyślnie jest <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

-   Dziedziczenie właściwości we właściwości zależności niestandardowej można również włączyć, ustawiając <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> flagi. Dziedziczenie właściwości jest przydatne w przypadku scenariusza, w którym elementy nadrzędne i podrzędne elementy mają właściwość wspólną i sens dla elementu podrzędnego elementy, które mają tę wartość określonej właściwości ustawić taką samą wartość, ponieważ element nadrzędny, ustaw ją. Przykład właściwości dziedziczonych <xref:System.Windows.FrameworkElement.DataContext%2A>, która jest używana do wiązania Procedura włączania ważne elementy główne szczegóły, aby obejrzeć prezentację danych. Podejmując <xref:System.Windows.FrameworkElement.DataContext%2A> dziedziczona, wszystkie elementy podrzędne dziedziczą tego kontekstu danych również. Ze względu na przejęcie wartości właściwości można określić kontekst danych w katalogu głównym strony lub aplikacji, a nie powinny być respecify go dla powiązania w wszystkie elementy podrzędne możliwe. <xref:System.Windows.FrameworkElement.DataContext%2A> jest również dobrym przykładem, aby zilustrować, że dziedziczenie przesłaniać wartość domyślną, ale zawsze można ustawić lokalnie na dowolny element podrzędny określonego; Aby uzyskać więcej informacji, zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dziedziczenie wartości właściwości ma maksymalną wydajność, koszty i dlatego należy używać oszczędnie; Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

-   Ustaw <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> flagę wskazującą, jeśli wykryto lub używane przez usługi rejestrowania nawigacji swoje właściwości zależności. Na przykład <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> właściwości; dowolnego elementu wybranego w wyborze utrwalone kontroli, gdy Historia rejestrowanie jest przejście.

<a name="RODP"></a>
## <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu

Można zdefiniować właściwości zależności tylko do odczytu. Scenariusze związane z dlaczego może zdefiniować swoje właściwość jako tylko do odczytu są jednak nieco inny, ponieważ procedurę rejestrowania ich w systemie właściwości i udostępnianie identyfikatora. Aby uzyskać więcej informacji, zobacz [właściwości zależności tylko do odczytu](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).

<a name="CTDP"></a>
## <a name="collection-type-dependency-properties"></a>Właściwości zależności typu kolekcji

Właściwości zależności typu kolekcji ma kilka problemów z implementacją dodatkowe wziąć pod uwagę. Aby uzyskać więcej informacji, zobacz [właściwości zależności typu kolekcji](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).

<a name="SecurityC"></a>
## <a name="dependency-property-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń właściwości zależności

Właściwości zależności powinien być zadeklarowany jako publiczny właściwości. Pola identyfikatora właściwości zależności powinien być zadeklarowany jako publiczny pola statyczne. Nawet wtedy, gdy użytkownik podejmie próbę zadeklarować innych poziomów dostępu (takich jak chroniony), właściwości zależności można uzyskać za pomocą identyfikatora w połączeniu z systemu właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Nawet pole identyfikatora chroniony jest potencjalnie dostępne ze względu na określenie metadanych raportowania lub wartość [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] będących częścią właściwości systemu, takie jak <xref:System.Windows.LocalValueEnumerator>. Aby uzyskać więcej informacji, zobacz [zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

<a name="DPCtor"></a>
## <a name="dependency-properties-and-class-constructors"></a>Właściwości zależności i Konstruktory klasy

Jest zasadniczo podczas programowania kodu zarządzanego (często wymuszane przez narzędzi analizy kodu, takich jak FxCop), który klasy konstruktorów nie powinien wywoływać metod wirtualnych. Jest to spowodowane Konstruktory mogą być wywoływane jako podstawowy inicjowania konstruktora klasy pochodnej i wprowadzając metodę wirtualną za pomocą konstruktora mogą pojawić się w stanie niekompletne inicjowania wystąpienia obiektu podczas konstruowania. Po utworzeniu klasy pochodnej z dowolną klasę pochodzącą od <xref:System.Windows.DependencyObject>, należy pamiętać, że sam system właściwość wywołuje i udostępnia metody wirtualne wewnętrznie. Te metody wirtualne są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości usług systemowych. Zastępowanie metody umożliwia klas pochodnych do wzięcia udziału w określaniu wartości. Aby uniknąć potencjalnych problemów za pomocą inicjowania środowiska uruchomieniowego, nie należy ustawiać zależności wartości właściwości konstruktorów klas, chyba że zostaną wykonane wzorca bardzo szczegółowych konstruktora. Aby uzyskać więcej informacji, zobacz [bezpieczne wzorce konstruktora dependencyobjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Zobacz też

- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
- [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
- [Właściwości zależności typu kolekcji](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)
- [Zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
- [Ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
- [Bezpieczne wzorce konstruktora dla obiektów DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)