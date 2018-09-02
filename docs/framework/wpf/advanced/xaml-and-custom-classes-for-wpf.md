---
title: Klasy XAML i niestandardowe dla WPF
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: acf3ba12a9a7e6ba9a8e378892098f5f265a23d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461803"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>Klasy XAML i niestandardowe dla WPF
XAML zaimplementowanego w [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] struktury obsługuje możliwość definiowania niestandardowej klasy lub struktury w dowolnym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] języka, a następnie dostęp przy użyciu znaczników XAML. Możesz użyć kombinacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]— określone typy i swoje niestandardowe w ramach tego samego pliku znaczników, zwykle przez mapowanie typów niestandardowych do prefiksu przestrzeni nazw XAML. W tym temacie omówiono wymagania które muszą spełniać klasę niestandardową, może być używany jako XAML element.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Klasy niestandardowe w aplikacji lub zespołów  
 Klasy niestandardowe, które są używane w XAML można zdefiniować na dwa różne sposoby: w związanym z kodem lub innego kodu, który tworzy podstawowy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji lub jako klasy w oddzielnych zestawu, na przykład pliku wykonywalnego lub biblioteki DLL używane jako bibliotekę klas. Każda z tych metod ma określoną zalety i wady.  
  
-   Zaletą tworzenia biblioteki klas jest, że niestandardowych klas mogą być współużytkowane przez wiele aplikacji możliwe. Odrębnych bibliotek również sprawia, że problemy z wersjonowaniem aplikacji jest łatwiejsze do kontroli i upraszcza tworzenie klasy, gdzie jest użycie klasy zamierzony jako element główny strony XAML.  
  
-   Zaletą definiowania niestandardowych klas w aplikacji jest, że ta technika jest stosunkowo lekkie i minimalizuje wdrażania i testowania problemy występujące podczas wprowadzania oddzielne zestawy poza głównym plik wykonywalny aplikacji.  
  
-   Czy zdefiniowane w tej samej lub różnych zestawów, niestandardowych klas należy zamapować między przestrzeń nazw środowiska CLR i przestrzeni nazw XML aby możliwe było użycie w XAML jako elementy. Zobacz [przestrzeń nazw XAML i mapowanie Namespace dla WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Wymagania dotyczące niestandardowych klas jako XAML Element  
 Aby móc można utworzyć wystąpienia jako elementu obiektu klasy musi spełniać następujące wymagania:  
  
-   Klasę niestandardową muszą być publiczne i obsługuje domyślnego (bezparametrowego) konstruktora publicznego. (Zobacz następujące sekcji uwag dotyczących struktury).  
  
-   Niestandardowe klasy nie może być klasą zagnieżdżoną. Zagnieżdżonych klasach i "dot" w ich ogólne składni CLR kolidują z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i/lub XAML funkcje, takie jak dołączone właściwości.  
  
 Oprócz włączenia składnia elementu obiektu, definicji obiektu umożliwia także składni elementu właściwości dla innych publicznych właściwości, które przyjmują tego obiektu jako typ wartości. Jest to spowodowane teraz można tworzyć wystąpienia jako elementu obiektu i wpisać wartość elementu właściwości takiej właściwości obiektu.  
  
### <a name="structures"></a>Struktury  
 Struktury, które definiują, ponieważ zawsze mogą być zbudowane w XAML w niestandardowych typów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Jest to spowodowane [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] kompilatory tworzyć niejawnie domyślnego konstruktora dla struktury, która inicjuje wszystkie wartości właściwości do wartości domyślnych. W niektórych przypadkach domyślna konstrukcji zachowanie i/lub obiekt użycie elementu dla struktury nie jest pożądane. Może to być, ponieważ struktura jest przeznaczone do wypełnienia wartości i funkcji z koncepcyjnie jako Unii, w której wartości zawartych może mieć interpretacji wzajemnie się wykluczają, a więc żaden z jej właściwości do ustawienia. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest przykładem takiej struktury <xref:System.Windows.GridLength>. Ogólnie rzecz biorąc te struktury powinny implementować konwertera typów w taki sposób, że wartości mogą być wyrażone w formie atrybutu, za pomocą Konwencji ciągu, tworzone różne interpretacji lub tryby struktury wartości. Struktura również powinny ujawniać zachowanie podobne do tworzenia kodu za pośrednictwem konstruktora innych niż domyślne.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Wymagania dotyczące właściwości klasy niestandardowej jako atrybuty XAML  
 Właściwości, należy odwołać się do typu i wartości (na przykład podstawowy) lub używanie klasy dla typu, który ma domyślny konstruktor lub konwertera typów dedykowane, dostępnej dla procesora XAML. W implementacji XAML CLR procesorów XAML albo znaleźć takie konwertery dzięki natywnej obsłudze elementów podstawowych języka lub poprzez zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do typu lub elementu członkowskiego w kopii definicji typu  
  
 Alternatywnie właściwość może odwoływać się typem klasy abstrakcyjnej lub interfejs. Dla abstrakcyjnych klas lub interfejsów oczekiwania do analizowania XAML jest, że wartość właściwości musi być wypełniona przy użyciu wystąpienia klasy praktycznych, które implementują interfejs lub wystąpień typów wyprowadzonych z klasy abstrakcyjnej.  
  
 Właściwości mogą być deklarowane dla klasy abstrakcyjnej, ale można ustawić tylko w klasach praktycznych, które pochodzą z klasy abstrakcyjnej. Jest to spowodowane tworzenie element obiektu dla tej klasy w ogóle wymaga publicznego konstruktora domyślnego w klasie.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter włączone składni atrybutów  
 Jeśli podasz konwertera typów dedykowaną, opartego na atrybutach na poziomie klasy, konwersja typu zastosowane umożliwia składni atrybutów dla dowolnej właściwości, która potrzebuje do tworzenia wystąpienia tego typu. Konwertera typów nie umożliwia użycie elementu obiektu tego typu; obecność domyślnego konstruktora dla tego typu umożliwia użycie elementu obiektu. W związku z tym właściwości, które są włączone konwertera typów ogólnie rzecz biorąc nie są użyteczne w składni właściwości, chyba że samego typu obsługuje również składnia elementu obiektu. Wyjątkiem jest określenie składni elementu właściwości, ale ma element właściwości zawierają ciąg. To użycie jest naprawdę zasadniczo równoważne użycie składni atrybutu, a takie użycie nie jest powszechne, chyba że istnieje na potrzeby bardziej niezawodna obsługa białych wartości atrybutu. Na przykład Oto użycie elementu właściwości, która przyjmuje ciąg, a użycie atrybutu równoważne:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Przykładem właściwości, gdy atrybut składnia jest dozwolona, ale składni elementu właściwości, który zawiera element z obiektu jest niedozwolona przy użyciu XAML są różne właściwości, które przyjmują <xref:System.Windows.Input.Cursor> typu. <xref:System.Windows.Input.Cursor> Klasa ma konwertera typów dedykowanych <xref:System.Windows.Input.CursorConverter>, ale nie udostępnia domyślnego konstruktora, więc <xref:System.Windows.FrameworkElement.Cursor%2A> właściwość można ustawić tylko przy użyciu składni atrybutów nawet jeśli rzeczywiste <xref:System.Windows.Input.Cursor> typ jest typem referencyjnym.  
  
### <a name="per-property-type-converters"></a>Konwertery typu dla właściwości  
 Alternatywnie samej właściwości może deklarować konwertera typów na poziomie właściwości. Dzięki temu "mini język", który tworzy obiekty typu właściwości w tekście, od przetwarzania przychodzących wartości ciągu atrybutu jako dane wejściowe dla <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> operacji na podstawie odpowiedniego typu. Zwykle jest to realizowane w celu zapewnienia dostępu wygody, a nie, jak jedyny oznacza umożliwiające ustawienie właściwości w XAML. Jednak istnieje również możliwość użycia konwerterów typów dla atrybutów, w której chcesz użyć istniejącej [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typy, które nie zostanie podany, domyślny konstruktor lub konwertera typów opartego na atrybutach. Przykłady z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsu API są określone właściwości, które przyjmują <xref:System.Globalization.CultureInfo> typu. W tym przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używane istniejące Microsoft .NET Framework <xref:System.Globalization.CultureInfo> typ, aby lepiej scenariuszy zgodności i migracji, które były używane w starszych wersjach struktur, ale <xref:System.Globalization.CultureInfo> typ nie obsługuje niezbędnych Konstruktory lub konwersja typu poziomie typu, może być używany jako wartość właściwości XAML w bezpośrednio.  
  
 Zawsze, gdy udostępnisz właściwość, która ma użycie XAML, szczególnie, jeśli jesteś autorem formantu, należy zdecydowanie rozważyć kopii tej właściwości przy użyciu właściwości zależności. Jest to szczególnie istotne, jeśli używasz istniejącego [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementacji procesora XAML, ponieważ może zwiększyć wydajność przy użyciu <xref:System.Windows.DependencyProperty> kopii. Właściwości zależności udostępni właściwości funkcji systemu dla usługi właściwości nadchodzące użytkowników można oczekiwać dla właściwości dostępne XAML. W tym funkcje, takie jak animacji, powiązanie danych oraz obsługę stylów. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) i [właściwości zależności i ładowania XAML](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Pisanie i przypisywanie konwertera typów  
 Czasami musisz napisać niestandardowy <xref:System.ComponentModel.TypeConverter> klasy, aby zapewnić konwersja typu dla danego typu właściwości. Aby uzyskać instrukcje na temat dziedziczyć i utworzyć konwertera typów, który może obsługiwać użycia XAML i jak stosować <xref:System.ComponentModel.TypeConverterAttribute>, zobacz [TypeConverters i XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Wymagania dotyczące Składnia atrybutu XAML zdarzenia programu obsługi zdarzeń klasę niestandardową  
 Może być używany jako [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, zdarzenia muszą być widoczne jako publiczne zdarzenie w klasie, która obsługuje domyślnego konstruktora, lub na abstrakcyjną klasę, której możliwy zdarzenia w klasach pochodnych. Aby możliwe było użycie wygodnie jako zdarzenia trasowane, Twoje [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń powinny implementować jawne `add` i `remove` metody, które Dodawanie i usuwanie programów obsługi dla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] podpisu zdarzenia i przekazuje te programy obsługi, aby <xref:System.Windows.UIElement.AddHandler%2A>i <xref:System.Windows.UIElement.RemoveHandler%2A> metody. Te metody Dodaj lub usuń programy obsługi do magazynu program obsługi zdarzenia trasowanego w wystąpieniu, które zdarzenie jest dołączony do.  
  
> [!NOTE]
>  Można zarejestrować programy obsługi bezpośrednio za pomocą zdarzenia trasowane <xref:System.Windows.UIElement.AddHandler%2A>oraz do definiowania celowo nie [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń, który przedstawia zdarzenia trasowanego. To jest zwykle niezalecane, ponieważ zdarzenie nie umożliwi XAML Składnia atrybutu Dołączanie programów obsługi i klasa wynikowy będzie oferować mniej przejrzystego widoku XAML możliwości tego typu.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Zapisywanie właściwości kolekcji  
 Właściwości, które przyjmują typ kolekcji mają składnia XAML, która pozwala na określenie obiektów, które są dodawane do kolekcji. Ta składnia ma dwie ważne funkcje.  
  
-   Obiekt, który jest obiektem kolekcji nie musi być określona w składni obiektów. Obecności tego typu kolekcji jest niejawne, gdy właściwość zostanie określona w XAML, która przyjmuje typ kolekcji.  
  
-   Elementy podrzędne kolekcji właściwości kod znaczników, są przetwarzane stawali się członkami kolekcji. Normalnie, kodu dostępu do elementów członkowskich kolekcji odbywa się za pośrednictwem listy/słownik metody takie jak `Add`, lub za pośrednictwem indeksatora. Ale składnia XAML nie obsługuje metody lub indeksatorów (wyjątek: XAML 2009 może obsługiwać metody, ale przy użyciu XAML 2009 ogranicza możliwości użycia programu WPF, zobacz [XAML 2009 — funkcje językowe](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). Kolekcje oczywiście są bardzo typowym wymogiem dla tworzenia drzewa elementów i potrzebujesz jakiś sposób, aby wypełnić te kolekcje w programie XAML deklaratywnego. W związku z tym elementy podrzędne elementu właściwości kolekcji są przetwarzane przez dodanie ich do kolekcji, która jest wartością typu właściwości kolekcji.  
  
 Implementacji .NET Framework XAML Services, a tym samym procesora WPF XAML używa następującej definicji dla co stanowi właściwości kolekcji. Właściwość typu właściwości musi implementować jeden z następujących czynności:  
  
-   Implementuje <xref:System.Collections.IList>.  
  
-   Implementuje <xref:System.Collections.IDictionary> lub odpowiednika rodzajowego (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Pochodzi od klasy <xref:System.Array> (Aby uzyskać więcej informacji na temat tablic w XAML, zobacz [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implementuje <xref:System.Windows.Markup.IAddChild> (interfejs zdefiniowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Każdy z tych typów w środowisku CLR ma `Add` metody, która jest używana przez procesor XAML do dodawania elementów do kolekcji źródłowej, podczas tworzenia wykresu obiektu.  
  
> [!NOTE]
>  Ogólny `List` i `Dictionary` interfejsów (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane w przypadku kolekcji wykrywania przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesora XAML. Można jednak użyć <xref:System.Collections.Generic.List%601> klasy jako klasę bazową, ponieważ implementuje <xref:System.Collections.IList> bezpośrednio lub <xref:System.Collections.Generic.Dictionary%602> jako klasa bazowa, ponieważ implementuje <xref:System.Collections.IDictionary> bezpośrednio.  
  
 Kiedy Deklarujesz właściwość z kolekcji, należy zachować ostrożność, jak wartość tej właściwości jest inicjowana w nowych wystąpień tego typu. Przed zaimplementowaniem nie właściwość jako właściwość zależności, następnie właściwość korzystać z polem zapasowym, który wywołuje konstruktora typu kolekcji jest odpowiednie. Jeśli Twoja własność jest właściwość zależności, może być potrzebne do zainicjowania właściwości kolekcji jako część domyślnego konstruktora typu. Jest to spowodowane właściwości zależności przyjmuje wartość domyślną z metadanych i zwykle nie chcesz początkowa wartość właściwości kolekcji jako kolekcji statyczne, udostępniony. Powinna istnieć wystąpienie kolekcji, dla każdego zawierające wystąpienie typu. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Dla właściwości z kolekcji, można zaimplementować niestandardowej kolekcji typów. Ze względu na traktowanie właściwość niejawnej kolekcji niestandardowej kolekcji typów konieczne nie udostępnia domyślnego konstruktora, aby możliwe było użycie niejawnie w XAML. Opcjonalnie może jednak zapewniać domyślnego konstruktora dla typu kolekcji. Może to być rozwiązaniem cenna. O ile nie udostępnia domyślnego konstruktora, nie można jawnie zadeklarować kolekcji jako elementu obiektu. Niektóre autorzy znaczników może preferować jawne kolekcji jako styl znaczników. Ponadto Konstruktor domyślny może uprościć wymagania inicjowania podczas tworzenia nowych obiektów używających typu kolekcji jako wartość właściwości.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Deklarowanie właściwości zawartości XAML  
 Język XAML definiuje pojęcie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości właściwości. Każda klasa, którego można używać w składni obiekt może mieć dokładnie jedną właściwość zawartości XAML. Aby zadeklarować właściwość, która ma być właściwość zawartości XAML dla swojej klasy, należy zastosować <xref:System.Windows.Markup.ContentPropertyAttribute> jako część definicji klasy. Określ nazwę zamierzony właściwość zawartości XAML, jako <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> w atrybucie. Właściwość jest określony jako ciąg według nazwy, a nie jako konstrukcję odbicia takich jak <xref:System.Reflection.PropertyInfo>.  
  
 Można określić właściwości kolekcji właściwość zawartości XAML. Powoduje to wykorzystania dla tej właściwości, według której object element może mieć jeden lub więcej elementów podrzędnych, bez żadnych pośredniczące elementów obiektu kolekcji ani tagów elementu właściwości. Elementy te są następnie traktowane jako wartość właściwości zawartości XAML i dodane do wystąpienia kolekcji zapasowy.  
  
 Niektóre istniejące właściwości zawartości XAML używają tego typu właściwości `Object`. Dzięki temu zawartości, takie jak wartości właściwości, która może przyjąć pierwotne XAML <xref:System.String> oraz biorąc wartość obiektu jedno odwołanie. Wykonanie tego modelu typu jest odpowiedzialny za określenie typu, a także obsługę możliwych typów. Typową przyczyną <xref:System.Object> zawartości, typ służy do obsługi zarówno prostym sposobem dodawania zawartości obiektu jako ciąg (który odbiera traktowania prezentacji domyślne) lub zaawansowanych oznacza dodawanie obiektów zawartości, która określa prezentacji innych niż domyślne lub dodatkowe dane.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serializacja XAML  
 W przypadku niektórych scenariuszy, na przykład jeśli jesteś autorem formantu, możesz również chcieć zapewnić, że wszelkie reprezentację obiektu, który może być utworzone w XAML może również być Zserializowany do równoważne znaczników XAML. Serializacja wymagania nie zostały opisane w tym temacie. Zobacz [kontrolować Przegląd autorstwa](../../../../docs/framework/wpf/controls/control-authoring-overview.md) i [drzewo elementów i serializacja](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Ładowanie XAML i właściwości zależności](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
