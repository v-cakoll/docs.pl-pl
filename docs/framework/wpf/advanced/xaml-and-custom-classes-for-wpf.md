---
title: XAML i klasy niestandardowe
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 4cd0ba7fa03d2578f4477c3ccf53188fbbea2dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186263"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>Klasy XAML i niestandardowe dla WPF
XAML zaimplementowane w common language runtime (CLR) struktury obsługuje możliwość definiowania niestandardowej klasy lub struktury w dowolnym języku wspólnego środowiska wykonawczego (CLR) języka, a następnie dostęp do tej klasy przy użyciu znaczników XAML. Można użyć mieszaniny [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]typów zdefiniowanych i typów niestandardowych w tym samym pliku znaczników, zazwyczaj mapując typy niestandardowe do prefiksu obszaru nazw XAML. W tym temacie omówiono wymagania, które klasa niestandardowa musi spełniać, aby być użytecznym jako element XAML.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>
## <a name="custom-classes-in-applications-or-assemblies"></a>Niestandardowe klasy w aplikacjach lub zestawach  
 Niestandardowe klasy, które są używane w XAML można zdefiniować na dwa różne sposoby: w ramach kodu lub innego kodu, który tworzy aplikację podstawową [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] lub jako klasa w oddzielnym zestawie, takich jak plik wykonywalny lub biblioteka DLL używana jako biblioteka klas. Każde z tych podejść ma szczególne zalety i wady.  
  
- Zaletą tworzenia biblioteki klas jest, że takie klasy niestandardowe mogą być współużytkowane w wielu różnych możliwych aplikacji. Oddzielna biblioteka ułatwia również kontrolowanie problemów z przechowywaniem wersji aplikacji i upraszcza tworzenie klasy, w której zamierzone użycie klasy jest elementem głównym na stronie XAML.  
  
- Zaletą definiowania klas niestandardowych w aplikacji jest to, że ta technika jest stosunkowo lekki i minimalizuje problemy z wdrażaniem i testowaniem napotkane podczas wprowadzania oddzielnych zestawów poza głównym plikiem wykonywalnym aplikacji.  
  
- Niezależnie od tego, czy zdefiniowano w tym samym, czy w innym zestawie, niestandardowe klasy muszą być mapowane między przestrzenią nazw CLR a przestrzenią nazw XML, aby były używane w języku XAML jako elementy. Zobacz [XAML obszarów nazw i mapowanie obszaru nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Wymagania dotyczące klasy niestandardowej jako elementu XAML  
 Aby można było utworzyć wystąpienie jako element obiektu, klasa musi spełniać następujące wymagania:  
  
- Klasa niestandardowa musi być publiczna i obsługiwać domyślny (bez parametrów) konstruktor publiczny. (Zobacz poniższą sekcję, aby zapoznać się z uwagami dotyczącymi struktur).  
  
- Klasa niestandardowa nie może być klasą zagnieżdżoną. Klasy zagnieżdżone i "kropka" w ich ogólnej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składni użycia CLR zakłócają działanie innych i/lub funkcji XAML, takich jak dołączone właściwości.  
  
 Oprócz włączania składni elementu obiektu definicja obiektu umożliwia również składnię elementu właściwości dla innych właściwości publicznych, które przyjmują ten obiekt jako typ wartości. Dzieje się tak, ponieważ obiekt może teraz zostać sytące jako element obiektu i może wypełnić wartość elementu właściwości takiej właściwości.  
  
### <a name="structures"></a>Struktury  
 Struktury zdefiniowane jako typy niestandardowe są zawsze w stanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] być konstruowane w języku XAML w pliku . Dzieje się tak, ponieważ kompilatory CLR niejawnie tworzą konstruktor bez parametrów dla struktury, która inicjuje wszystkie wartości właściwości do ich wartości domyślnych. W niektórych przypadkach domyślne zachowanie konstrukcji i/lub użycie elementu obiektu dla struktury nie jest pożądane. Może to być spowodowane strukturą jest przeznaczony do wypełniania wartości i funkcji koncepcyjnie jako unii, gdzie zawarte wartości mogą mieć wzajemnie wykluczające się interpretacje, a zatem żadna z jego właściwości są settable. Przykładem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takiej struktury <xref:System.Windows.GridLength>jest . Ogólnie rzecz biorąc takie struktury należy zaimplementować konwerter typu, tak aby wartości mogą być wyrażone w formie atrybutu, przy użyciu konwencji ciągów, które tworzą różne interpretacje lub tryby wartości struktury. Struktura powinna również uwidaczniać podobne zachowanie dla konstrukcji kodu za pośrednictwem konstruktora bez parametrów.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Wymagania dotyczące właściwości klasy niestandardowej jako atrybutów XAML  
 Właściwości muszą odwoływać się do typu według wartości (na przykład pierwotnego) lub użyć klasy dla typu, który ma konstruktora bez parametrów lub konwertera typu dedykowanego, do którego procesor XAML może uzyskać dostęp. W implementacji XAML CLR procesory XAML znajdują takie konwertery za pośrednictwem natywnej <xref:System.ComponentModel.TypeConverterAttribute> obsługi elementów pierwotnych języka lub poprzez zastosowanie do typu lub elementu członkowskiego w definicjach typów kopii zapasowych  
  
 Alternatywnie właściwość może odwoływać się do typu klasy abstrakcyjnej lub interfejsu. W przypadku klas abstrakcyjnych lub interfejsów oczekiwanie na analizowanie XAML jest, że wartość właściwości musi być wypełniona praktycznych wystąpień klasy, które implementują interfejs lub wystąpień typów, które pochodzą z klasy abstrakcyjnej.  
  
 Właściwości mogą być zadeklarowane w klasie abstrakcyjnej, ale można ustawić tylko na klasy praktyczne, które pochodzą z klasy abstrakcyjnej. Jest to spowodowane tworzeniem elementu obiektu dla klasy w ogóle wymaga publicznych bez parametrów konstruktora w klasie.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Składnia atrybutów typeconverter  
 Jeśli podasz dedykowany, przypisany konwerter typu na poziomie klasy, zastosowana konwersja typu włącza składnię atrybutów dla dowolnej właściwości, która musi utworzyć wystąpienie tego typu. Konwerter typów nie włącza użycia elementu obiektu typu; tylko obecność konstruktora bez parametrów dla tego typu umożliwia użycie elementu obiektu. W związku z tym właściwości, które są włączone konwerter typu są zazwyczaj nie nadaje się do użytecznego w składni właściwości, chyba że sam typ obsługuje również składnię elementu obiektu. Wyjątek od tego jest, że można określić składnię elementu właściwości, ale mają element właściwości zawierają ciąg. To użycie jest naprawdę zasadniczo równoważne użycia składni atrybutu i takie użycie nie jest wspólne, chyba że istnieje potrzeba bardziej niezawodne obsługi odstępu wartości atrybutu. Na przykład następujące jest użycie elementu właściwości, który przyjmuje ciąg i równoważne użycie atrybutu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Przykłady właściwości, w których składnia atrybutu jest dozwolona, ale składnia elementu właściwości zawierająca element obiektu jest <xref:System.Windows.Input.Cursor> niedozwolona za pośrednictwem xaml, są różne właściwości, które przyjmują typ. Klasa <xref:System.Windows.Input.Cursor> ma konwerter <xref:System.Windows.Input.CursorConverter>typu dedykowanego , ale nie udostępnia <xref:System.Windows.FrameworkElement.Cursor%2A> konstruktora bez parametrów, więc właściwość <xref:System.Windows.Input.Cursor> można ustawić tylko za pomocą składni atrybutów, nawet jeśli typ rzeczywisty jest typem odwołania.  
  
### <a name="per-property-type-converters"></a>Konwertery typu na właściwość  
 Alternatywnie sama właściwość może zadeklarować konwerter typu na poziomie właściwości. Umożliwia to "mini language", który wystąpienia obiektów typu właściwości wbudowanej, przetwarzając przychodzące wartości ciągu <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> atrybutu jako dane wejściowe dla operacji na podstawie odpowiedniego typu. Zazwyczaj odbywa się to w celu zapewnienia akcesor wygody, a nie jako jedyny sposób, aby włączyć ustawienie właściwości w XAML. Jednak istnieje również możliwość użycia konwerterów typów dla atrybutów, w których mają być używane istniejące typy CLR, które nie dostarczają konstruktora bez parametrów lub konwertera przypisanego typu. Przykłady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu API są pewne <xref:System.Globalization.CultureInfo> właściwości, które przyjmują typ. W takim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przypadku użyto istniejącego <xref:System.Globalization.CultureInfo> typu Microsoft .NET Framework, aby lepiej adres zgodności i migracji <xref:System.Globalization.CultureInfo> scenariuszy, które były używane we wcześniejszych wersjach struktur, ale typ nie obsługuje niezbędnych konstruktorów lub konwersji typu na poziomie typu, aby być używane jako wartość właściwości XAML bezpośrednio.  
  
 Za każdym razem, gdy udostępniasz właściwość, która ma użycie XAML, szczególnie jeśli jesteś autorem formantu, należy zdecydowanie rozważyć kopię zapasową tej właściwości z właściwością zależności. Jest to szczególnie ważne, jeśli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] używasz istniejącej implementacji procesora XAML, ponieważ można zwiększyć wydajność przy użyciu <xref:System.Windows.DependencyProperty> kopii zapasowej. Właściwość zależności będzie uwidaczniać funkcje systemu właściwości dla właściwości, które użytkownicy będą oczekiwać dla właściwości dostępne XAML. Obejmuje to funkcje, takie jak animacja, powiązanie danych i obsługa stylu. Aby uzyskać więcej informacji, zobacz [Właściwości zależności niestandardowych](custom-dependency-properties.md) oraz [właściwości ładowania i zależności XAML.](xaml-loading-and-dependency-properties.md)  
  
### <a name="writing-and-attributing-a-type-converter"></a>Pisanie i przypisywanie konwertera typów  
 Od czasu do czasu trzeba <xref:System.ComponentModel.TypeConverter> będzie napisać niestandardową klasę pochodną, aby zapewnić konwersję typu dla typu właściwości. Aby uzyskać instrukcje dotyczące sposobu wyprowadzki i tworzenia konwertera typów, który <xref:System.ComponentModel.TypeConverterAttribute>może obsługiwać użycie XAML, oraz jak zastosować , zobacz [TypeConverters i XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Wymagania dotyczące składni atrybutu obsługi zdarzeń XAML dotyczące zdarzeń klasy niestandardowej  
 Aby być użytecznym jako zdarzenie CLR, zdarzenie musi być widoczne jako zdarzenie publiczne w klasie, która obsługuje konstruktora bez parametrów lub w klasie abstrakcyjnej, gdzie zdarzenie jest dostępne dla klas pochodnych. Aby można było wygodnie używać jako zdarzenia routowane, zdarzenie `add` CLR należy zaimplementować jawne i `remove` metody, które dodają i usuwają programy obsługi dla podpisu zdarzenia CLR i przekazuje te programy obsługi do <xref:System.Windows.UIElement.AddHandler%2A> i <xref:System.Windows.UIElement.RemoveHandler%2A> metod. Te metody dodać lub usunąć programy obsługi do magazynu obsługi zdarzeń kierowane w wystąpieniu, do których jest dołączone zdarzenie.  
  
> [!NOTE]
> Istnieje możliwość rejestrowania programów obsługi bezpośrednio <xref:System.Windows.UIElement.AddHandler%2A>dla kierowanych zdarzeń przy użyciu , a celowo nie zdefiniować zdarzenie CLR, który udostępnia kierowane zdarzenie. Nie jest to ogólnie zalecane, ponieważ zdarzenie nie włączy składni atrybutu XAML do dołączania programów obsługi, a wynikowa klasa zaoferuje mniej przejrzysty widok XAML możliwości tego typu.  
  
<a name="Collection_Properties"></a>
## <a name="writing-collection-properties"></a>Właściwości kolekcji pisania  
 Właściwości, które przyjmują typ kolekcji mają składnię XAML, która umożliwia określenie obiektów, które są dodawane do kolekcji. Ta składnia ma dwie godne uwagi funkcje.  
  
- Obiekt, który jest obiektem kolekcji, nie musi być określony w składni elementu obiektu. Obecność tego typu kolekcji jest niejawna za każdym razem, gdy określisz właściwość w języku XAML, która przyjmuje typ kolekcji.  
  
- Elementy podrzędne właściwości kolekcji w znacznikach są przetwarzane, aby stać się członkami kolekcji. Zwykle dostęp do kodu do członków kolekcji jest wykonywany za pomocą metody `Add`listy/słownika, takie jak , lub za pośrednictwem indeksatora. Ale składnia XAML nie obsługuje metod ani indeksatorów (wyjątek: XAML 2009 może obsługiwać metody, ale przy użyciu XAML 2009 ogranicza możliwe użycia WPF; zobacz [Funkcje języka XAML 2009](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Kolekcje są oczywiście bardzo częstym wymaganiem tworzenia drzewa elementów i potrzebujesz jakiegoś sposobu, aby wypełnić te kolekcje w deklaratywnym XAML. W związku z tym elementy podrzędne właściwości kolekcji są przetwarzane przez dodanie ich do kolekcji, która jest wartością typu właściwości kolekcji.  
  
 Implementacja usług .NET Framework XAML Services, a tym samym procesor WPF XAML używa następującej definicji dla tego, co stanowi właściwość kolekcji. Typ właściwości właściwości musi implementować jedną z następujących czynności:  
  
- Implementuje <xref:System.Collections.IList>.  
  
- Implements <xref:System.Collections.IDictionary> lub odpowiednik<xref:System.Collections.Generic.IDictionary%602>ogólny ( ).  
  
- Pochodzi z <xref:System.Array> (aby uzyskać więcej informacji na temat tablic w XAML, zobacz [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
- Implements <xref:System.Windows.Markup.IAddChild> (interfejs zdefiniowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Każdy z tych typów w `Add` programie CLR ma metodę, która jest używana przez procesor XAML do dodawania elementów do podstawowej kolekcji podczas tworzenia wykresu obiektu.  
  
> [!NOTE]
> Ogólne `List` i `Dictionary` interfejsy<xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IDictionary%602>( i ) nie są [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługiwane do wykrywania kolekcji przez procesor XAML. Jednak można użyć <xref:System.Collections.Generic.List%601> klasy jako klasy podstawowej, <xref:System.Collections.IList> ponieważ implementuje <xref:System.Collections.Generic.Dictionary%602> bezpośrednio lub jako klasy <xref:System.Collections.IDictionary> podstawowej, ponieważ implementuje bezpośrednio.  
  
 Podczas deklarowania właściwości, która przyjmuje kolekcję, należy zachować ostrożność, jak ta wartość właściwości jest inicjowany w nowych wystąpień typu. Jeśli nie implementujesz właściwości jako właściwości zależności, a następnie o właściwość użyć pola zapasowego, który wywołuje konstruktora typu kolekcji jest odpowiedni. Jeśli właściwość jest właściwością zależności, może być konieczne zainicjowanie właściwości kolekcji jako części domyślnego konstruktora typu. Dzieje się tak, ponieważ właściwość zależności pobiera swoją wartość domyślną z metadanych i zazwyczaj nie chcesz, aby wartość początkowa właściwości kolekcji była statyczną, udostępnioną kolekcją. Powinno istnieć wystąpienie kolekcji na każde wystąpienie typu zawierającego. Aby uzyskać więcej informacji, zobacz [Niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
 Można zaimplementować niestandardowy typ kolekcji dla właściwości kolekcji. Ze względu na niejawne traktowanie właściwości kolekcji typ kolekcji niestandardowe nie musi dostarczać konstruktora bez parametrów, aby był używany w XAML niejawnie. Jednak opcjonalnie można podać konstruktora bez parametrów dla typu kolekcji. Może to być wartościowa praktyka. Jeśli nie podasz konstruktora bez parametrów, nie można jawnie zadeklarować kolekcji jako elementu obiektu. Niektórzy autorzy znaczników może wolą, aby zobaczyć jawne kolekcji jako kwestia stylu znaczników. Ponadto konstruktor bez parametrów można uprościć wymagania inicjowania podczas tworzenia nowych obiektów, które używają typu kolekcji jako wartości właściwości.  
  
<a name="XAMLCONtent"></a>
## <a name="declaring-xaml-content-properties"></a>Deklarowanie właściwości zawartości XAML  
 Język XAML definiuje pojęcie właściwości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości. Każda klasa, która jest użyteczna w składni obiektu może mieć dokładnie jedną właściwość zawartości XAML. Aby zadeklarować właściwość jako właściwość zawartości XAML <xref:System.Windows.Markup.ContentPropertyAttribute> dla klasy, należy zastosować jako część definicji klasy. Określ nazwę właściwości zawartości xaml <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> zamierzonego jako atrybutu. Właściwość jest określona jako ciąg według nazwy, <xref:System.Reflection.PropertyInfo>a nie jako konstrukcja odbicia, taka jak .  
  
 Można określić właściwość kolekcji, która ma być właściwością zawartości XAML. Powoduje to użycie dla tej właściwości, przy czym element obiektu może mieć jeden lub więcej elementów podrzędnych, bez żadnych interweniujących elementów obiektu kolekcji lub tagów elementu właściwości. Te elementy są następnie traktowane jako wartość właściwości zawartości XAML i dodawane do wystąpienia kolekcji kopii zapasowej.  
  
 Niektóre istniejące właściwości zawartości XAML używają `Object`typu właściwości . Dzięki temu właściwość zawartości XAML, która może <xref:System.String> przyjmować wartości pierwotne, takie jak a, a także przy jednej wartości obiektu referencyjnego. Jeśli zastosujesz się do tego modelu, typ jest odpowiedzialny za określenie typu, a także obsługę możliwych typów. Typową przyczyną <xref:System.Object> typu zawartości jest obsługa zarówno prostego środka dodawania zawartości obiektu jako ciągu (który otrzymuje domyślne traktowanie prezentacji), jak i zaawansowanego środka dodawania zawartości obiektu, który określa prezentację nieniezykoniową lub dodatkowe dane.  
  
<a name="Serializing"></a>
## <a name="serializing-xaml"></a>Serialowanie XAML  
 W przypadku niektórych scenariuszy, takich jak jeśli jesteś autorem formantu, można również zapewnić, że wszelkie reprezentacji obiektów, które mogą być tworzone w XAML można również serializowany z powrotem do równoważnych znaczników XAML. Wymagania dotyczące serializacji nie są opisane w tym temacie. Zobacz [Omówienie tworzenia formantów](../controls/control-authoring-overview.md) oraz [Drzewo elementów i serializacja](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Przegląd Elementy bazy](base-elements-overview.md)
- [Właściwości zależności i ładowania XAML](xaml-loading-and-dependency-properties.md)
