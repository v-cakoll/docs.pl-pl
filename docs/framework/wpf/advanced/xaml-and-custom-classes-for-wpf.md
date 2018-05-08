---
title: Klasy XAML i niestandardowe dla WPF
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 35c4e23298a8af9fdba92b7e4b6231c08861cc72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-and-custom-classes-for-wpf"></a>Klasy XAML i niestandardowe dla WPF
XAML zgodnie z implementacją w [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] struktury obsługuje możliwość definiowania niestandardowych klasy lub struktury w żadnym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] język, a następnie dostępu które przy użyciu znaczników XAML. Można użyć kombinację [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-zdefiniowanych typów i z typów niestandardowych w ramach tego samego pliku znaczników, zazwyczaj przez mapowanie typów niestandardowych do prefiksu przestrzeni nazw XAML. W tym temacie omówiono wymagania, które muszą spełniać klasy niestandardowej, może być używany jako XAML element.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Klas niestandardowych w aplikacji lub zestawów  
 Klas niestandardowych, które są używane w języku XAML można zdefiniować na dwa różne sposoby: w ramach CodeBehind lub inny kod, który spowoduje utworzenie podstawowego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikację, lub jako klasa w oddzielnych zestawu, na przykład plik wykonywalny lub biblioteki DLL używane jako biblioteki klas. Każdy z tych metod ma konkretnego zalety i wady.  
  
-   Zaletą tworzenia biblioteki klas jest, że niestandardowe klasy może być współużytkowana przez wiele różnych możliwości aplikacji. Odrębnych bibliotek również ułatwia problemy z wersjonowaniem aplikacji do formantu i upraszcza tworzenie klasy, gdzie jest użycie klasy przeznaczone jako element główny na strony XAML.  
  
-   Zaletą definiowania klas niestandardowych w aplikacji jest, że ta metoda jest stosunkowo lekkie i minimalizuje wdrażania i testowania problemów napotykanych podczas wprowadzania oddzielne zestawy poza głównym plik wykonywalny aplikacji.  
  
-   Czy zdefiniowany w zestawie tego samego lub innego, niestandardowe klasy muszą być mapowane w między przestrzeń nazw środowiska CLR i przestrzeni nazw XML, aby można używać w języku XAML jako elementy. Zobacz [przestrzeń nazw XAML i Namespace mapowania dla WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Wymagania dotyczące niestandardowej klasy jako XAML Element  
 Aby można było można utworzyć wystąpienia jako elementu obiektu, klasa musi spełniać następujące wymagania:  
  
-   Niestandardowe klasy musi być publiczny i obsługuje domyślnego (bezparametrowego) konstruktora publicznego. (Patrz poniżej sekcji, aby uzyskać informacje dotyczące struktury).  
  
-   Niestandardowe klasy nie może być klasą zagnieżdżoną. Klasy zagnieżdżone i "kropki (.)" w ich ogólna składnia użycia CLR kolidować z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i/lub XAML — funkcje takie jak dołączone właściwości.  
  
 Oprócz włączenia składni elementu obiektu, definicja obiektu umożliwia także składni elementu właściwości innych publicznych właściwości, które przyjmują tego obiektu, ponieważ typ wartości. Jest to spowodowane teraz można wdrożyć jako elementu obiektu i wpisać wartość właściwości elementu takich właściwości obiektu.  
  
### <a name="structures"></a>Struktury  
 Struktury zdefiniowane jako typów niestandardowych są zawsze może być skonstruowany w XAML w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Jest to spowodowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kompilatory niejawnie utworzyć domyślnego konstruktora dla struktury, która inicjuje wszystkich wartości właściwości do wartości domyślnych. W niektórych przypadkach domyślna konstrukcji zachowania i/lub obiekt użycie elementu dla struktury nie jest pożądane. Może to być spowodowane struktury jest przeznaczona do wypełnienia wartości i funkcji z koncepcyjnie jako Unii, w którym wartości zawarte może mieć interpretacje wykluczają się wzajemnie, a zatem żadna z jego właściwości nie jest do ustawienia. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z przykładami takich struktury <xref:System.Windows.GridLength>. Ogólnie rzecz biorąc te struktury powinien implementować konwertera typów, tak, aby wartości może zostać wyrażona w formie atrybutu, wykorzystując konwencje ciągu utworzyć inną interpretacje lub tryby konstrukcji wartości. Struktura również powinny ujawniać podobne zachowanie dla konstrukcji kodu za pomocą konstruktora domyślnego z systemem innym niż.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Wymagania dotyczące właściwości klasy niestandardowej jako atrybuty XAML  
 Właściwości musi odwoływać się do typu i wartości (na przykład elementu podstawowego) lub użyj klasy dla typu, który ma domyślny konstruktor lub konwerter dedykowanych typu, który procesor XAML mogą uzyskiwać dostęp do. W implementacji środowiska CLR XAML procesorów XAML albo znaleźć takie konwertery za pośrednictwem macierzystą obsługę elementów podstawowych języka lub poprzez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do typu lub elementu członkowskiego przy tworzeniu kopii definicji typu  
  
 Można również właściwość może odwoływać się typu klasy abstrakcyjnej lub interfejsu. Klasy abstrakcyjne lub interfejsów oczekuje dla analizowanie zawartości XAML się, że wartość właściwości musi być wypełniona z wystąpień klasy praktyczne, które implementują interfejs lub wystąpień typów wyprowadzonych z klasy abstrakcyjnej.  
  
 Właściwości mogą być deklarowane na klasę abstrakcyjną, ale można ustawić tylko w klasach praktyczne, wyprowadzonych z klasy abstrakcyjnej. Jest to spowodowane tworzenie cały element object dla klasy wymaga publicznego konstruktora domyślnego w klasie.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Składnia atrybutu włączone TypeConverter  
 Jeśli podasz konwertera typów dedykowane, oparte na atrybutach na poziomie klasy konwersji typu zastosowane umożliwia Składnia atrybutu dla każdej właściwości, które należy utworzyć wystąpienia typu. Konwerter typów nie obsługuje użycia elementu obiektów tego typu; obecność konstruktora domyślnego dla tego typu umożliwia użycie elementu obiektu. W związku z tym właściwości, które są włączone konwerter typów ogólnie rzecz biorąc nie są w składni właściwości, chyba że samego typu obsługuje również składni elementu obiektu. Wyjątkiem jest Określ składni elementu właściwości, ale ma element właściwości zawiera ciąg. Wykorzystanie odpowiada rzeczywiście zasadniczo użycie składni atrybutu, a takie użycia nie jest typowe, jeśli zachodzi potrzeba obsługi bardziej niezawodne odstępu wartości atrybutu. Na przykład następujące czynności jest użycie elementu właściwości, który pobiera ciąg, a równoważny użycie atrybutu:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Przykłady właściwości, gdy atrybut składnia jest dozwolona, ale składni elementu właściwości, który zawiera element obiektu jest niedozwolone przy użyciu języka XAML są różne właściwości, które przyjmują <xref:System.Windows.Input.Cursor> typu. <xref:System.Windows.Input.Cursor> Klasa ma konwertera typów dedykowanych <xref:System.Windows.Input.CursorConverter>, ale nie ujawnia konstruktora domyślnego więc <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości można ustawić tylko za pomocą składni atrybutu mimo że rzeczywiste <xref:System.Windows.Input.Cursor> typ jest typem referencyjnym.  
  
### <a name="per-property-type-converters"></a>Konwertery typu dla właściwości  
 Alternatywnie samej właściwości mogą zadeklarować konwertera typów, na poziomie właściwości. Dzięki temu "mini język", który tworzy obiekty typu wbudowanej właściwości przez przetwarzanie przychodzących wartości ciągu atrybutu jako dane wejściowe dla <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> operacji na podstawie odpowiedniego typu. Zazwyczaj wykonywane na zapewnienie dostępu wygody, a nie w umożliwiające ustawienie właściwości w języku XAML. Jednak istnieje również możliwość użycia konwertery typu dla atrybutów, w której chcesz użyć istniejącego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typy, które nie zostanie podana domyślnego konstruktora lub konwertera typu atrybutami. Przykłady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu API są niektóre właściwości, które przyjmują <xref:System.Globalization.CultureInfo> typu. W takim przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyć istniejącego Microsoft .NET Framework <xref:System.Globalization.CultureInfo> typu w celu lepszego rozwiązania zgodność i migracja scenariusze, które były używane w starszych wersjach struktur, ale <xref:System.Globalization.CultureInfo> typ nie obsługuje niezbędnych Konstruktory lub konwersja typu poziomu typu może być używany jako wartość właściwości XAML bezpośrednio.  
  
 Zawsze, gdy ujawnić właściwości, która ma użycie XAML, zwłaszcza w przypadku, gdy autor kontroli, zdecydowanie warto kopii tej właściwości z właściwością zależności. Jest to szczególnie istotne, jeśli używasz istniejącej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementacji procesora XAML, ponieważ może poprawić wydajność przy użyciu <xref:System.Windows.DependencyProperty> kopii. Powoduje to udostępnienie właściwości funkcji systemu z właściwości, które użytkownicy będą oczekiwać na dostępne właściwości XAML właściwości zależności. W tym funkcje, takie jak animacji, powiązania danych i Obsługa stylów. Aby uzyskać więcej informacji, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) i [ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Zapisywanie i przypisywanie konwertera typów  
 Czasami trzeba będzie zapisu niestandardowego <xref:System.ComponentModel.TypeConverter> klasy, aby zapewnić konwersji typu dla danego typu właściwości. Aby uzyskać instrukcje na temat dziedziczyć i utworzyć konwerter typu, który może obsługiwać użycia języka XAML i sposób stosowania <xref:System.ComponentModel.TypeConverterAttribute>, zobacz [TypeConverters i języka XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Wymagania dotyczące Składnia atrybutu XAML zdarzeń programu obsługi zdarzeń klasy niestandardowej  
 Może być używany jako [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia, zdarzenia musi być udostępniany jako zdarzenie publiczne dla klasy, która obsługuje domyślnego konstruktora lub na abstrakcyjnego klasy, gdy zdarzenie jest dostępny w klasach pochodnych. Aby mogły być łatwo jako kierowanego zdarzenia, używane z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń powinny implementować jawne `add` i `remove` metody, które Dodawanie i usuwanie programów obsługi dla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] podpisu zdarzenia i przekazuje te programy obsługi, aby <xref:System.Windows.UIElement.AddHandler%2A>i <xref:System.Windows.UIElement.RemoveHandler%2A> metody. Te metody Dodaj lub usuń programy obsługi w magazynie obsługi kierowanego zdarzenia w wystąpieniu, które zdarzenie jest dołączony do.  
  
> [!NOTE]
>  Można zarejestrować obsługi bezpośrednio kierowane zdarzenia przy użyciu <xref:System.Windows.UIElement.AddHandler%2A>oraz do definiowania celowo nie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, który ujawnia kierowanego zdarzenia. To jest zwykle niezalecane, ponieważ zdarzenie nie dają Składnia atrybutu XAML Dołączanie programów obsługi i wynikowa klasy oferuje mniej przejrzyste wyświetlanie XAML funkcji tego typu.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zapisywanie właściwości kolekcji  
 Właściwości, które przyjmują typem kolekcji ma składnię języka XAML, która umożliwia określenie obiektów, które są dodawane do kolekcji. Ta składnia ma dwie ważne funkcje.  
  
-   Obiekt, który jest obiektem kolekcji nie musi być określone w składni elementu obiekt. Obecności tego typu kolekcji jest niejawnie, przy każdym Określ właściwość w języku XAML, który pobiera typ kolekcji.  
  
-   Elementy podrzędne w znaczniku właściwości kolekcji są przetwarzane na uzyskanie członkostwa w kolekcji. Zwykle dostęp do kodu do elementów członkowskich kolekcji odbywa się za pośrednictwem listy/słownika metody takie jak `Add`, lub za pośrednictwem indeksatora. Ale składni języka XAML nie obsługuje metody lub indeksatorów (wyjątek: XAML 2009 może obsługiwać metody, ale przy użyciu języka XAML 2009 ogranicza możliwości użycia WPF; zobacz [XAML 2009 — funkcje językowe](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Kolekcje są oczywiście często wymagane do tworzenia drzewa elementów i konieczne w celu wypełnienia kolekcjach w języku XAML deklaratywne. W związku z tym elementy podrzędne właściwości kolekcji są przetwarzane przez dodanie ich do kolekcji, która jest wartością typu właściwości kolekcji.  
  
 Implementacja usługi XAML .NET Framework, a tym samym procesora WPF XAML używa następującej definicji dla co stanowi właściwości kolekcji. Typ właściwości właściwości muszą implementować jeden z następujących czynności:  
  
-   Implementuje <xref:System.Collections.IList>.  
  
-   Implementuje <xref:System.Collections.IDictionary> lub jego ogólny odpowiednik (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Pochodną <xref:System.Array> (Aby uzyskać więcej informacji dotyczących tablic w języku XAML, zobacz [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implementuje <xref:System.Windows.Markup.IAddChild> (zdefiniowane przez interfejs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Każdy z tych typów CLR ma `Add` metodę, która jest używana przez procesor XAML do dodawania elementów w źródłowej kolekcji podczas tworzenia wykresu obiektu.  
  
> [!NOTE]
>  Ogólnego `List` i `Dictionary` interfejsów (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane dla kolekcji wykrywania przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML. Można jednak użyć <xref:System.Collections.Generic.List%601> klasy jako klasę podstawową, ponieważ implementuje on <xref:System.Collections.IList> bezpośrednio, lub <xref:System.Collections.Generic.Dictionary%602> jako klasę podstawową, ponieważ implementuje on <xref:System.Collections.IDictionary> bezpośrednio.  
  
 W deklaracji właściwości, która przyjmuje kolekcji, należy zachować ostrożność jak wartości tej właściwości został zainicjowany w nowych wystąpień tego typu. Jeśli nie są implementacja właściwości jako właściwość zależności, następnie mających właściwość, użyj pola zapasowy, która wywołuje konstruktor typów kolekcji jest odpowiedni. Jeśli Twoje właściwość jest właściwością zależności, następnie konieczne może zainicjować właściwości kolekcji jako część domyślnego konstruktora typu. To dlatego właściwości zależności przyjmuje wartość domyślną z metadanych i zazwyczaj nie chcesz początkowej wartości właściwości kolekcji jako statyczny udostępnionego kolekcję. Należy wystąpienie kolekcji, na każdym zawierające wystąpienie typu. Aby uzyskać więcej informacji, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Typ kolekcji niestandardowych można zaimplementować dla właściwości z kolekcji. Ze względu na sposób postępowania właściwości niejawnej kolekcji typ kolekcji niestandardowe trzeba podawać domyślnego konstruktora, aby używać w języku XAML niejawnie. Opcjonalnie można jednak podać domyślnego konstruktora dla typu kolekcji. Może to być zastanowić rozwiązaniem. Jeśli nie podasz konstruktora domyślnego nie można jawnie deklarować kolekcji jako elementu obiektu. Niektóre autorów znaczników może preferować jawne kolekcji jako styl znaczników. Ponadto konstruktora domyślnego upraszcza wymagania inicjowania podczas tworzenia nowych obiektów, które danego typu kolekcji jako wartość właściwości.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarowanie właściwości zawartości XAML  
 Języka XAML wprowadzono pojęcie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] właściwości content. Każda klasa, który jest używany w składni obiekt może mieć dokładnie jedną właściwość zawartości XAML. Aby zadeklarować właściwości jako właściwość content XAML dla klasy, należy zastosować <xref:System.Windows.Markup.ContentPropertyAttribute> jako część definicji klasy. Określ nazwę danego właściwości zawartości XAML, jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> w atrybucie. Właściwość jest określony jako ciąg o nazwie, nie jako konstrukcja odbicia takich jak <xref:System.Reflection.PropertyInfo>.  
  
 Można określić właściwości kolekcji właściwość zawartości XAML. Powoduje to użycie tej właściwości, według której object element może mieć jeden lub więcej elementów podrzędnych, bez interwencji elementy obiektu kolekcji lub tagów właściwości elementu. Te elementy są następnie traktowane jako wartość właściwości zawartości XAML i dodane do wystąpienia kolekcji zapasowego.  
  
 Niektóre istniejące właściwości zawartości XAML używają tego typu właściwości `Object`. Dzięki temu XAML zawartości, właściwości, które może podjąć pierwotne wartości, takich jak <xref:System.String> oraz pobieranie wartości obiektu jedno odwołanie. Po wykonaniu tego modelu z danym typem jest odpowiedzialny za określenie typu, a także obsługę możliwych typów. Typowe przyczyny <xref:System.Object> zawartości typu służy do obsługi zarówno prostym sposobem dodawania zawartości obiektu jako ciąg (który odbiera traktowania prezentacji domyślne) lub zawartości, która określa prezentacji z systemem innym niż domyślny obiekt zaawansowane metody dodawania lub dodatkowe dane.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializacja XAML  
 Dla niektórych scenariuszy, np. Jeśli autor sterowania, można również upewnić się, że wszystkie reprezentację obiektu, który można wdrożyć w języku XAML również może być Zserializowany do równoważne znaczników XAML. Serializacja wymagania nie zostały opisane w tym temacie. Zobacz [kontrolować omówienie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md) i [Element drzewa i serializacja](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
