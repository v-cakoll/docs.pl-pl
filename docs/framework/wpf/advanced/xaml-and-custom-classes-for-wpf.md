---
title: XAML i klasy niestandardowe
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 8dab7310826357d7fbe434002298032b8722e5b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744429"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>Klasy XAML i niestandardowe dla WPF
Język XAML zgodnie z implementacją w strukturach środowiska uruchomieniowego języka wspólnego (CLR) obsługuje możliwość definiowania niestandardowej klasy lub struktury w dowolnym języku środowiska uruchomieniowego języka wspólnego (CLR), a następnie uzyskiwania dostępu do tej klasy przy użyciu znacznika XAML. Można użyć mieszanki typów zdefiniowanych przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]i typów niestandardowych w tym samym pliku znaczników, zazwyczaj przez mapowanie typów niestandardowych na prefiks przestrzeni nazw XAML. W tym temacie omówiono wymagania, które Klasa niestandardowa musi spełniać, aby można było używać ich jako elementu XAML.  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Klasy niestandardowe w aplikacjach lub zestawach  
 Klasy niestandardowe, które są używane w języku XAML, można definiować na dwa różne sposoby: w ramach kodu lub innego kodu, który tworzy podstawową aplikację [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], lub jako klasę w osobnym zestawie, na przykład plik wykonywalny lub DLL używany jako Biblioteka klas. Każdy z tych podejścia ma szczególne zalety i wady.  
  
- Zaletą tworzenia biblioteki klas jest to, że wszystkie takie klasy niestandardowe mogą być współużytkowane przez wiele różnych możliwych aplikacji. Oddzielna Biblioteka sprawia również, że problemy z przechowywaniem wersji aplikacji są łatwiejsze do kontroli i upraszczają tworzenie klasy, w której zamierzone użycie klasy jest elementem głównym na stronie XAML.  
  
- Zaletą definiowania klas niestandardowych w aplikacji jest to, że ta technika jest stosunkowo lekkim i minimalizuje problemy związane z wdrażaniem i testowaniem, które są wykonywane po wprowadzeniu oddzielnych zestawów wykraczających poza główny plik wykonywalny aplikacji.  
  
- Niezależnie od tego, czy zdefiniowano w tym samym lub innym zestawie, klasy niestandardowe muszą być mapowane między przestrzenią nazw CLR i przestrzenią nazw XML, aby można było ich używać w języku XAML jako elementy. Zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Wymagania dotyczące klasy niestandardowej jako elementu XAML  
 Aby można było utworzyć wystąpienie jako element obiektu, Klasa musi spełniać następujące wymagania:  
  
- Klasa niestandardowa musi być publiczna i obsługiwać domyślnego (bezparametrowego) konstruktora publicznego. (Zobacz poniższą sekcję, aby poznać informacje o strukturach).  
  
- Klasa niestandardowa nie może być klasą zagnieżdżoną. Klasy zagnieżdżone i "kropka" w ich ogólnej składni użycia środowiska CLR zakłócają inne funkcje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i/lub XAML, takie jak dołączone właściwości.  
  
 Oprócz włączenia składni elementu obiektu, definicja obiektu również umożliwia składnię elementu właściwości dla wszystkich innych właściwości publicznych, które pobierają ten obiekt jako typ wartości. Jest to spowodowane tym, że obiekt może teraz być skonkretyzowany jako element obiektu i może wypełniać wartość właściwości, takiej właściwości.  
  
### <a name="structures"></a>Struktury  
 Struktury zdefiniowane jako typy niestandardowe są zawsze w języku XAML w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Wynika to z faktu, że kompilatory CLR niejawnie tworzą Konstruktor bez parametrów dla struktury, która inicjuje wszystkie wartości właściwości do ich wartości domyślnych. W niektórych przypadkach domyślne zachowanie konstrukcji i/lub użycie elementu obiektu dla struktury nie jest pożądane. Może to być spowodowane tym, że struktura jest przeznaczona do wypełniania wartości i funkcji koncepcyjnie jako Unia, gdzie zawarte wartości mogą mieć wzajemnie wykluczające się interpretacje i dlatego żadna z jej właściwości nie jest w trakcie. Przykładem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takiej struktury jest <xref:System.Windows.GridLength>. Ogólnie rzecz biorąc, takie struktury powinny implementować konwerter typów, aby wartości mogły być wyrażone w postaci atrybutu, przy użyciu konwencji ciągów, które tworzą różne interpretacje lub tryby wartości struktury. Struktura powinna również ujawniać podobne zachowanie konstrukcji kodu za pomocą konstruktora bez parametrów.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Wymagania dotyczące właściwości niestandardowej klasy jako atrybutów XAML  
 Właściwości muszą odwoływać się do typu przez wartość (na przykład podstawowy) lub użyć klasy dla typu, który ma Konstruktor bez parametrów lub dedykowany konwerter typów, do którego może uzyskać dostęp procesor XAML. W implementacji języka XAML CLR procesory języka XAML mogą znaleźć takie konwertery za pomocą natywnej obsługi dla elementów podstawowych języka lub przez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do typu lub składowej w definicjach typów zapasowych  
  
 Alternatywnie właściwość może odwoływać się do typu klasy abstrakcyjnej lub interfejsu. Dla klas abstrakcyjnych lub interfejsów oczekiwana jest analiza XAML, ponieważ wartość właściwości musi być uzupełniona wystąpieniami klasy praktycznej, które implementują interfejs, lub wystąpień typów, które pochodzą od klasy abstrakcyjnej.  
  
 Właściwości można zadeklarować w klasie abstrakcyjnej, ale można ją ustawić tylko dla praktycznych klas, które pochodzą z klasy abstrakcyjnej. Wynika to z faktu, że utworzenie elementu obiektu dla klasy w ogóle wymaga publicznego konstruktora bez parametrów w klasie.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Składnia atrybutu enabled z funkcją TypeConverter  
 Jeśli podajesz dedykowany konwerter typu z atrybutami na poziomie klasy, zastosowana konwersja typu włącza składnię atrybutu dla każdej właściwości, która musi utworzyć wystąpienie tego typu. Konwerter typów nie pozwala na użycie elementu obiektu dla typu; tylko obecność konstruktora bez parametrów dla tego typu umożliwia użycie elementu obiektu. W związku z tym właściwości, które są włączone dla konwertera typów, zazwyczaj nie mogą być używane w składni właściwości, chyba że sam typ obsługuje składnię elementu obiektu. Wyjątkiem jest to, że można określić składnię elementu właściwości, ale element właściwości zawiera ciąg. To użycie jest naprawdę równoważne z użyciem składni atrybutów, a takie użycie nie jest wspólne, chyba że istnieje potrzeba bardziej niezawodnej obsługi białej przestrzeni wartości atrybutu. Na przykład, poniżej przedstawiono użycie elementu właściwości, które przyjmuje ciąg, i równoważne użycie atrybutu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Przykłady właściwości, w których składnia atrybutu jest dozwolona, ale składnia elementu właściwości, która zawiera element obiektu, jest niedozwolona w języku XAML, są różne właściwości, które przyjmują typ <xref:System.Windows.Input.Cursor>. Klasa <xref:System.Windows.Input.Cursor> ma dedykowany konwerter typów <xref:System.Windows.Input.CursorConverter>, ale nie uwidacznia konstruktora bez parametrów, więc Właściwość <xref:System.Windows.FrameworkElement.Cursor%2A> może być ustawiana tylko za pośrednictwem składni atrybutu, mimo że rzeczywisty typ <xref:System.Windows.Input.Cursor> jest typem referencyjnym.  
  
### <a name="per-property-type-converters"></a>Konwertery typu dla właściwości  
 Alternatywnie właściwość może deklarować konwerter typów na poziomie właściwości. Umożliwia to "język mini", który tworzy wystąpienia obiektów typu właściwości w tekście, przez przetwarzanie przychodzących wartości ciągu atrybutu jako danych wejściowych dla operacji <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> na podstawie odpowiedniego typu. Zwykle jest to konieczne, aby zapewnić wygodną metodę dostępu, a nie jako jedyne środki umożliwiające ustawienie właściwości w języku XAML. Można jednak używać konwerterów typów dla atrybutów, w których mają być używane istniejące typy CLR, które nie dostarczają konstruktora bez parametrów lub konwertera typu z atrybutami. Przykłady z interfejsu API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to pewne właściwości, które pobierają typ <xref:System.Globalization.CultureInfo>. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać istniejących Microsoft .NET Framework <xref:System.Globalization.CultureInfo> typu, aby lepiej spełnić wymagania dotyczące zgodności i migracji, które były używane we wcześniejszych wersjach platform, ale typ <xref:System.Globalization.CultureInfo> nie obsługiwał wymaganych konstruktorów lub konwersji typu na poziomie typu, aby można było używać ich bezpośrednio jako wartość właściwości XAML.  
  
 Za każdym razem, gdy użytkownik uwidacznia właściwość, która ma użycie języka XAML, szczególnie jeśli jesteś autorem kontrolki, należy zdecydowanie rozważyć wykonanie kopii zapasowej tej właściwości przy użyciu właściwości zależności. Jest to szczególnie istotne, jeśli używasz istniejącej implementacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] procesora XAML, ponieważ można poprawić wydajność przy użyciu <xref:System.Windows.DependencyProperty> kopii zapasowej. Właściwość zależności będzie uwidaczniać funkcje systemu właściwości właściwości, które użytkownicy będą oczekiwać na Właściwość dostępne dla języka XAML. Obejmuje to takie funkcje jak animacja, powiązanie danych i obsługa stylów. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md) i [ładowanie XAML i właściwości zależności](xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Pisanie i przypisywanie konwertera typów  
 Czasami trzeba będzie napisać niestandardową klasę pochodną <xref:System.ComponentModel.TypeConverter>, aby zapewnić konwersję typu dla typu właściwości. Aby uzyskać instrukcje dotyczące sposobu, w jaki można utworzyć konwerter typu, który może obsługiwać użycie kodu XAML i jak zastosować <xref:System.ComponentModel.TypeConverterAttribute>, zobacz [TypeConverters and XAML](typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Wymagania dotyczące składni atrybutu programu obsługi zdarzeń XAML w zdarzeniach klasy niestandardowej  
 Aby można było używać go jako zdarzenia CLR, zdarzenie musi być uwidocznione jako zdarzenie publiczne dla klasy, która obsługuje Konstruktor bez parametrów lub klasy abstrakcyjnej, w której można uzyskać dostęp do tego zdarzenia w klasach pochodnych. Aby można było używać wygodnie jako zdarzenia trasowanego, zdarzenie CLR powinno implementować jawne `add` i `remove` metod, które dodają i usuwają programy obsługi dla sygnatury zdarzeń środowiska CLR i przekazują te procedury obsługi do metod <xref:System.Windows.UIElement.AddHandler%2A> i <xref:System.Windows.UIElement.RemoveHandler%2A>. Te metody umożliwiają dodanie lub usunięcie programów obsługi do magazynu obsługi zdarzeń kierowanych na wystąpienie, do którego jest dołączone zdarzenie.  
  
> [!NOTE]
> Można zarejestrować programy obsługi bezpośrednio dla zdarzeń kierowanych przy użyciu <xref:System.Windows.UIElement.AddHandler%2A>i celowo nie definiować zdarzenia CLR, które ujawnia zdarzenie kierowane. Nie jest to ogólnie zalecane, ponieważ zdarzenie nie będzie włączać składni atrybutu XAML w celu dołączania obsługi, a klasa będąca wynikiem będzie oferować mniej przezroczysty widok XAML możliwości tego typu.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zapisywanie właściwości kolekcji  
 Właściwości, które pobierają typ kolekcji, mają składnię XAML, która umożliwia określenie obiektów, które są dodawane do kolekcji. Ta składnia ma dwie istotne funkcje.  
  
- Obiekt, który jest obiektem kolekcji, nie musi być określony w składni elementu obiektu. Obecność tego typu kolekcji jest niejawna za każdym razem, gdy określisz właściwość w języku XAML, która przyjmuje typ kolekcji.  
  
- Elementy podrzędne właściwości kolekcji w znacznikach są przetwarzane, aby stać się elementami członkowskimi kolekcji. Zwykle dostęp do kodu do elementów członkowskich kolekcji odbywa się za pomocą metod list/dictionary, takich jak `Add`, lub za pomocą indeksatora. Chociaż składnia języka XAML nie obsługuje metod ani indeksatorów (wyjątek: XAML 2009 może obsługiwać metody, ale użycie języka XAML 2009 ogranicza możliwe użycie platformy WPF; zobacz [xaml 2009 Language Features](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md)). Kolekcje są oczywiście bardzo typowym wymaganiem do tworzenia drzewa elementów i potrzebujesz pewnego sposobu wypełniania tych kolekcji w deklaratywnym języku XAML. W związku z tym elementy podrzędne właściwości kolekcji są przetwarzane przez dodanie ich do kolekcji, która jest wartością typu właściwości kolekcji.  
  
 Implementacja usług .NET Framework XAML i w ten sposób procesor WPF XAML używa następującej definicji dla co stanowi Właściwość kolekcji. Typ właściwości właściwości musi implementować jedną z następujących wartości:  
  
- Implementuje <xref:System.Collections.IList>.  
  
- Implementuje <xref:System.Collections.IDictionary> lub odpowiednik ogólny (<xref:System.Collections.Generic.IDictionary%602>).  
  
- Wynika z <xref:System.Array> (Aby uzyskać więcej informacji na temat tablic w języku XAML, zobacz [X:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)).  
  
- Implementuje <xref:System.Windows.Markup.IAddChild> (interfejs zdefiniowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Każdy z tych typów w środowisku CLR ma metodę `Add`, która jest używana przez procesor XAML do dodawania elementów do kolekcji bazowej podczas tworzenia grafu obiektów.  
  
> [!NOTE]
> Ogólne interfejsy `List` i `Dictionary` (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane na potrzeby wykrywania kolekcji przez procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML. Można jednak użyć klasy <xref:System.Collections.Generic.List%601> jako klasy bazowej, ponieważ implementuje ona <xref:System.Collections.IList> bezpośrednio lub <xref:System.Collections.Generic.Dictionary%602> jako klasę bazową, ponieważ implementuje <xref:System.Collections.IDictionary> bezpośrednio.  
  
 Podczas deklarowania właściwości pobierającej kolekcję należy zachować ostrożność, jak ta wartość właściwości jest inicjowana w nowych wystąpieniach typu. Jeśli właściwość nie jest wdrażana jako właściwość zależności, właściwość Użyj pola zapasowego, które wywołuje Konstruktor typów kolekcji, jest odpowiedni. Jeśli właściwość jest właściwością zależności, może być konieczne zainicjowanie właściwości kolekcji jako części domyślnego konstruktora typów. Wynika to z faktu, że właściwość dependency przyjmuje swoją wartość domyślną z metadanych, a zwykle nie chcesz, aby początkowa wartość właściwości kolekcji była statyczną, udostępnioną kolekcją. Dla każdego wystąpienia typu zawierającego istnieje wystąpienie kolekcji. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
 Można zaimplementować niestandardowy typ kolekcji dla właściwości kolekcji. Ze względu na niejawne traktowanie właściwości kolekcji niestandardowa typ kolekcji nie musi podawać konstruktora bez parametrów, aby można go było używać w języku XAML niejawnie. Można jednak opcjonalnie dostarczyć Konstruktor bez parametrów dla typu kolekcji. Może to być wartościowaa. Jeśli nie podasz konstruktora bez parametrów, nie można jawnie zadeklarować kolekcji jako elementu obiektu. Niektórzy autorzy znaczników mogą chcieć zobaczyć jawną kolekcję jako temat stylu znaczników. Ponadto Konstruktor bez parametrów może uprościć wymagania inicjalizacyjne podczas tworzenia nowych obiektów, które używają typu kolekcji jako wartości właściwości.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarowanie właściwości zawartości XAML  
 Język XAML definiuje koncepcję właściwości zawartości [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Każda klasa, która jest użyteczna w składni obiektu, może mieć dokładnie jedną właściwość zawartości XAML. Aby zadeklarować właściwość jako właściwość zawartości XAML dla klasy, Zastosuj <xref:System.Windows.Markup.ContentPropertyAttribute> w ramach definicji klasy. Określ nazwę zamierzonej właściwości zawartości XAML jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> w atrybucie. Właściwość jest określana jako ciąg o nazwie, nie jako konstrukcja odbicia, taka jak <xref:System.Reflection.PropertyInfo>.  
  
 Możesz określić właściwość kolekcji jako właściwość zawartości XAML. Powoduje to użycie tej właściwości, według której element object może mieć co najmniej jeden element podrzędny, bez żadnych elementów obiektu kolekcji lub tagów elementów właściwości. Te elementy są następnie traktowane jako wartość właściwości zawartości XAML i dodawane do wystąpienia kolekcji zapasowej.  
  
 Niektóre istniejące właściwości zawartości XAML używają typu właściwości `Object`. Pozwala to na Właściwość zawartości XAML, która może przyjmować wartości pierwotne, takie jak <xref:System.String>, a także pobieranie pojedynczej wartości obiektu odniesienia. W przypadku korzystania z tego modelu typ jest odpowiedzialny za określenie typu, a także obsługę możliwych typów. Typową przyczyną <xref:System.Object> typu zawartości jest obsługa prostej metody dodawania zawartości obiektu jako ciągu (która otrzymuje domyślne podejście do prezentacji) lub zaawansowanego sposobu dodawania zawartości obiektu, która określa niedomyślną prezentację lub dodatkowe dane.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializowanie XAML  
 W przypadku niektórych scenariuszy, takich jak Jeśli jesteś autorem kontrolki, możesz również upewnić się, że wszelkie reprezentacje obiektów, które można utworzyć w kodzie XAML, można również serializować z powrotem do odpowiadającego znacznika XAML. Wymagania serializacji nie zostały opisane w tym temacie. Zobacz [Omówienie tworzenia](../controls/control-authoring-overview.md) i [drzewa elementów i serializacji](element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Przegląd elementów podstawowych](base-elements-overview.md)
- [Ładowanie XAML i właściwości zależności](xaml-loading-and-dependency-properties.md)
