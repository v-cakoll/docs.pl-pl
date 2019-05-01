---
title: Szczegóły składni XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: bf4118c6e811f409715b7b6684851b8b3e8bbb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981373"
---
# <a name="xaml-syntax-in-detail"></a>Szczegóły składni XAML
W tym temacie opisano terminy, które są używane do opisywania elementy składni XAML. Te warunki są często stosowane w pozostałej części tej dokumentacji, zarówno dla dokumentacji WPF specjalnie i dla innych platform, które używają XAML lub włączane przez obsługę języka XAML na poziomie System.Xaml podstawowe pojęcia dotyczące XAML. W tym temacie omówiono w podstawowej terminologii opisanymi w temacie [Przegląd XAML (WPF)](xaml-overview-wpf.md).  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specyfikacja języka XAML  
 Terminologia składni XAML, które są zdefiniowane w tym miejscu jest również zdefiniowana lub odwołania w specyfikacji języka XAML. XAML jest językiem oparte na języku XML i następuje lub rozszerza strukturalnych reguł XML. Niektóre terminologii został udostępniony z lub opiera się na terminologii często używane podczas opisywania język XML lub XML document object model.  
  
 Aby uzyskać więcej informacji na temat specyfikacji języka XAML, Pobierz [ \[MS-XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525) z Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML i środowiska CLR  
 XAML jest językiem znaczników. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Jak dorozumianych według jego nazwy, włącza środowisko uruchomieniowe wykonywania. XAML nie jest samodzielnie jednym z języków, które bezpośrednio jest używane przez środowisko uruchomieniowe CLR. Zamiast tego można traktować XAML jako obsługujące swój własny system typów. Określony system analizy XAML, który jest używany przez WPF jest oparta na CLR i system typów CLR. Typy XAML są mapowane na typy CLR do utworzenia wystąpienia reprezentację w czasie wykonywania, gdy zostanie przeanalizowany XAML dla programu WPF. Z tego powodu w pozostałej części dyskusję na temat składni, w tym dokumencie będzie zawierać odwołania do typu CLR systemu, nawet, jeśli nie obsługują dyskusje równoważny składni w specyfikacji języka XAML. (Na poziomie specyfikacji języka XAML, typy XAML mógłby być mapowany na innym systemie typu, który nie ma być środowiska CLR, ale wymagałoby stworzeniem i używaniem inny analizator XAML).  
  
#### <a name="members-of-types-and-class-inheritance"></a>Członkowie typów i dziedziczenia klas  
 Właściwości i zdarzenia jako są wyświetlane jako elementy członkowskie XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu często są dziedziczone z typów podstawowych. Rozważmy na przykład w tym przykładzie: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Właściwość nie jest właściwością natychmiast zadeklarowane na <xref:System.Windows.Controls.Button> klasy, gdyby Spójrz na definicji klasy, wyniki odbicia lub dokumentacji. Zamiast tego <xref:System.Windows.Controls.Control.Background%2A> jest dziedziczony z podstawy <xref:System.Windows.Controls.Control> klasy.  
  
 Zachowanie dziedziczenia klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów XAML jest znaczący opuszczenia wymuszane schematu interpretacji znaczników XML. Dziedziczenie klas może stać się skomplikowane, szczególnie w przypadku, gdy pośredni klasy bazowe są klasami abstrakcyjnymi lub interfejsy. To jest jedną z przyczyn zbiór elementów XAML i ich atrybutów dopuszczalne jest trudne do reprezentowania dokładnie i całkowicie przy użyciu typów schematu są zwykle używane do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] programowania, takie jak format DTD lub XSD. Kolejny powód jest tym rozszerzalności i mapowania typów funkcji języka XAML, sama wyklucza kompletności wszystkie stałych reprezentację dopuszczalna typów i elementów członkowskich.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Składnia elementu obiektu  
 *Składnia elementu obiektu* jest składnia znaczników XAML, która tworzy wystąpienie klasy CLR lub struktury przez zadeklarowanie — element XML. Ta składnia przypomina składnię innych języków znaczników, takich jak HTML. Składnia elementu obiektu, który rozpoczyna się od lewego nawiasu ostrego (\<), a następnie natychmiast Nazwa typu klasy lub struktury, które są tworzone. Zero lub więcej spacji po nazwie typu i zero lub więcej atrybutów może również być zadeklarowany w elemencie obiektu z jedną lub więcej spacji, oddzielając nazwy atrybutu = para "value". Na koniec jedną z następujących muszą być spełnione:  
  
- Element i tagów muszą być zamknięte przez ukośnikiem (/) od razu następuje prawego nawiasu ostrego (>).  
  
- Otwierający tag, należy wykonać prawego nawiasu ostrego (>). Inne elementy obiektu, elementy właściwości lub tekst wewnętrzny wykonać otwierający tag. Dokładnie zawartość może być zawarte w tym miejscu jest zwykle ograniczony przez model obiektów elementu. Odpowiednik tagu zamykającego elementu obiektu należy również objęte zagnieżdżanie właściwe i równoważyć z innych par tagu otwierającym i zamykającym.  
  
 XAML jako implementowany przez .NET zawiera zestaw reguł, które elementy obiektu mapy na typy i atrybuty do właściwości lub zdarzenia i XAML przestrzeni nazw z przestrzeni nazw CLR, a także zestaw. Dla platformy WPF i .NET Framework XAML elementów obiektu mapowania [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] zestawów występujących w odwołaniu typów zgodnie z definicją w i atrybutów mapowania członków z tych typów. Gdy odwołujesz się do typu CLR w XAML, masz dostęp do dziedziczone składowe tego typu, jak również.  
  
 Na przykład, poniższy przykład jest składnia elementu obiektu, który tworzy nowe wystąpienie klasy <xref:System.Windows.Controls.Button> klasy, a także określa <xref:System.Windows.FrameworkElement.Name%2A> atrybut i wartości dla tego atrybutu:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Poniższy przykład jest składnia elementu obiektu, który również uwzględnia Składnia właściwości zawartości XAML. Tekst wewnętrzny zawartych w będzie służyć do ustawiania <xref:System.Windows.Controls.TextBox> właściwość zawartości XAML, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modele zawartości  
 Klasa może obsługiwać użycia jako element obiektu XAML w kontekście składni, ale ten element będzie działać tylko prawidłowo w aplikacji lub strony, gdy znajduje się w oczekiwanej pozycji drzewo ogólnej zawartości modelu lub elementu. Na przykład <xref:System.Windows.Controls.MenuItem> zwykle tylko będzie umieszczona jako element podrzędny elementu <xref:System.Windows.Controls.Primitives.MenuBase> klasy pochodnej, takich jak <xref:System.Windows.Controls.Menu>. Zawartość, modele dla określonych elementów są udokumentowane w ramach uwagi na stronach klasy dla kontrolek i innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas, które mogą być używane jako elementów XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Właściwości elementów obiektu  
 Właściwości w XAML są ustawiane przez różne możliwe składni. Składnia, która może służyć do określonej właściwości różnią się na podstawie podstawowej charakterystyki systemu typu właściwości, czy ustawienie.  
  
 Przez ustawienie wartości właściwości, Dodaj funkcje lub właściwości do obiektów występujących na grafie obiektu w czasie wykonywania. Początkowy stan utworzony obiekt z elementu obiektu opiera się na domyślne zachowanie konstruktora. Zazwyczaj aplikacja użyje się coś innego niż wystąpienie domyślne całkowicie dowolnego danego obiektu.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Składnia atrybutów (właściwości)  
 Składnią atrybutu jest składnia znaczników XAML, która ustawia wartości dla właściwości od zadeklarowania atrybutu dla istniejącego elementu obiektu. Nazwa atrybutu musi odpowiadać nazwie elementu członkowskiego CLR właściwości klasy, która będzie tworzyć kopię elementu odpowiedniego obiektu. Nazwa atrybutu następuje operatora przypisania (=). Wartość atrybutu musi być ciąg ujęty w cudzysłów.  
  
> [!NOTE]
>  Przemienne cudzysłowów służy do umieszczenia na literalny znak cudzysłowu w ciągu atrybutu. Na przykład można użyć apostrofy jako środek do deklarowania ciąg, który zawiera znaku podwójnego cudzysłowu, znajdujący się w nim. Czy korzystasz z pojedynczym lub podwójnym cudzysłowie, należy użyć pasującą parę dla otwierające i zamykające ciągu wartości atrybutu. Istnieją również sekwencje ucieczki lub innych technik dotyczące obejścia ograniczeń dla znaków nałożonych przez dowolnego określonego składnia XAML. Zobacz [jednostki znaków XML i XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby można było, można skonfigurować za pomocą składni atrybutów, właściwości muszą być publiczne i musi być zapisywalny. Wartość właściwości w systemie typów zapasowy musi być typem wartości lub musi być typu odwołania, które mogą być tworzone lub przywoływany przez procesor XAML podczas uzyskiwania dostępu do odpowiedniego kopii typu.  
  
 Dla WPF XAML zdarzeń zdarzenia, które jest przywoływane jako nazwa atrybutu musi być publiczne i mieć Delegat publiczny.  
  
 Właściwość lub zdarzenie musi należeć do klasy lub struktury, który zostanie uruchomiony przez element zawierający obiekt.  
  
### <a name="processing-of-attribute-values"></a>Przetwarzanie wartości atrybutów  
 Wartość ciągu, zawartych w otwierające i zamykające znaki cudzysłowu są przetwarzane przez procesor XAML. W przypadku właściwości domyślnego zachowania przetwarzania zależy od typu podstawowego właściwości CLR.  
  
 Wartość atrybutu jest wypełniana przez jedną z następujących czynności, za pomocą tego kolejność przetwarzania:  
  
1. Jeśli procesor XAML napotka nawiasu klamrowego lub element obiektu, który pochodzi od klasy <xref:System.Windows.Markup.MarkupExtension>, następnie rozszerzenie znaczników odwołania jest stosowana jako pierwsza zamiast przetwarzania wartość jako ciąg i Obiekt zwrócony przez rozszerzenie znaczników jest używany jako wartość. W wielu przypadkach obiektu zwróconego przez rozszerzenie znaczników będzie odwołanie do istniejącego obiektu lub wyrażenie, który odracza oceny do czasu wykonywania, a nie jest obiektem nowo utworzona.  
  
2. Jeśli właściwość jest zadeklarowana za pomocą opartego na atrybutach <xref:System.ComponentModel.TypeConverter>, lub typ wartości tej właściwości jest zadeklarowany z atrybutami <xref:System.ComponentModel.TypeConverter>, wartość ciągu atrybutu jest przesyłany do usługi konwertera typów wejście konwersji i zwróci konwerter nowe wystąpienie obiektu.  
  
3. Jeśli ma nie <xref:System.ComponentModel.TypeConverter>, podejmowana jest próba to bezpośrednia konwersji na typ właściwości. Ten poziom ostatecznego jest to bezpośrednia konwersji wartość native analizatora między typów pierwotnych języka XAML lub wyboru dla nazw nazwanych stałych wyliczenia (analizator następnie uzyskuje dostęp do dopasowania wartości).  
  
#### <a name="enumeration-attribute-values"></a>Wyliczanie wartości atrybutów  
 Wyliczenia w XAML są przetwarzane wewnętrznie przez analizatory składni XAML i elementy członkowskie wyliczenia powinien być określony przez określenie nazwy ciągu jednego nazwanych stałych wyliczenia.  
  
 W przypadku wartości wyliczenia nonflag natywnych zachowaniem jest przetwarzania ciągu wartości atrybutu, a następnie Rozwiąż ją do jednej z wartości wyliczenia. Nie określaj wyliczenia w formacie *wyliczenie*. *Wartość*, tak jak w kodzie. Zamiast tego można określić tylko *wartość*, i *wyliczenie* jest wnioskowany przez typ właściwości to ustawienie. Jeśli określisz atrybut w *wyliczenie*. *Wartość* formularza, go nie działają prawidłowo.  
  
 Dla wyliczenia flagwise zachowanie zależy od <xref:System.Enum.Parse%2A?displayProperty=nameWithType> metody. Można określić wiele wartości wyliczenia flagwise, Oddziel poszczególne wartości przecinkami. Jednak nie można połączyć wartości wyliczenia, które nie są flagwise. Na przykład nie można użyć składni przecinkami próbuje utworzyć <xref:System.Windows.Trigger> działającego na wielu warunków wyliczenie nonflag:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Flagwise wyliczenia, obsługujące atrybuty, które są do ustawienia w XAML są rzadkie na platformie WPF. Jednak jest jeden taki wyliczenie <xref:System.Windows.Media.StyleSimulations>. Można na przykład użyj składni rozdzielonych przecinkami flagwise atrybutu do modyfikowania podany w uwagi, na przykład <xref:System.Windows.Documents.Glyphs> klasy; `StyleSimulations = "BoldSimulation"` może stać się `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> jest inna właściwość, w którym można określić więcej niż jedną wartość wyliczenia. Jednak ta właściwość ma miejsce w szczególnych przypadkach, ponieważ <xref:System.Windows.Input.ModifierKeys> wyliczenie obsługuje swój własny konwertera typów. Konwerter typu dla Modyfikatory używa znak plus (+) jako ogranicznika, a nie przecinka (,). Ta konwersja obsługuje bardziej tradycyjny składni do reprezentowania kombinacje klawiszy w programowaniu Windows firmy Microsoft, takich jak "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Właściwości i zdarzenia odwołania do nazwy elementu członkowskiego  
 Podczas określania atrybutów, można odwoływać się wszystkie właściwości lub zdarzenia, który istnieje jako element członkowski typu CLR, który skonkretyzowany zawierającego element obiektu.  
  
 Ewentualnie można odwoływać się do dołączoną właściwość lub dołączone zdarzenie, niezależnie od elementu obiektu zawierającego. (Dołączone właściwości zostały omówione w następnej sekcji).  
  
 Możesz też nazwać dowolne zdarzenie, z dowolnego obiektu, który jest dostępny za pośrednictwem domyślnej przestrzeni nazw za pomocą *typeName*. *Zdarzenie* częściowo kwalifikowane nazwy; ta składnia obsługuje dołączanie programy obsługi zdarzeń trasowanych gdzie program obsługi jest przeznaczona do obsługi zdarzenia, routing z elementów podrzędnych, ale element nadrzędny nie również ma tego zdarzenia w swojej tabeli elementów członkowskich. Ta składnia przypomina składnię dołączone zdarzenie, ale zdarzeń w tym miejscu nie jest spełniony, dołączone zdarzenie. Zamiast tego odwołuje się zdarzenie o kwalifikowanej nazwie. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
 W niektórych scenariuszach nazwy właściwości czasami są dostarczane jako wartość atrybutu, a nie nazwa atrybutu. Nazwa tej właściwości może również obejmować kwalifikatorów, takich jak właściwości określone w formie *ownerType*. *dependencyPropertyName*. Ten scenariusz jest typowy podczas zapisywania style lub szablony w XAML. Przetwarzanie reguł dla nazw właściwości podana jako wartość atrybutu różnią się i są zarządzane przez typ właściwości ustawiany lub zachowania określonego podsystemu WPF. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../controls/styling-and-templating.md).  
  
 Użycie innej nazwy właściwości jest, gdy wartość atrybutu w tym artykule opisano relację właściwość właściwości. Ta funkcja jest używana do wiązania danych i dla celów scenorysu i został włączony przez <xref:System.Windows.PropertyPath> klasa i jej konwertera typów. Aby uzyskać bardziej szczegółowy opis semantyka wyszukiwania, zobacz [PropertyPath, składnia XAML](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Składnia elementu właściwości  
 *Składnia elementu właściwości* używa składni, która diverges nieco od podstawowych reguł dotyczących składni XML dla elementów. W pliku XML wartość atrybutu jest ciągiem de facto, za pomocą jedyną możliwą odmiany trwa jaki format kodowania ciąg jest używany. W XAML można przypisać inne elementy obiektu jako wartość właściwości. Ta funkcja jest włączona, składnia elementu właściwości. Zamiast właściwości określany jako atrybut w tagu elementu, właściwość jest określony, przy użyciu elementu otwierający tag w *elementTypeName*. *propertyName* formularza, wartość właściwości jest określona w ramach, a następnie zamknięto element właściwości.  
  
 W szczególności składnia zaczyna się od lewego nawiasu ostrego (\<), a następnie natychmiast Nazwa typu klasy lub struktury, zawarty w składni elementu właściwości. To następuje natychmiast przez pojedynczą kropką (.), następnie według nazwy właściwości, następnie prawego nawiasu ostrego (>). Podobnie jak w przypadku składni atrybutów, ta właściwość musi istnieć w ramach zadeklarowany publiczne elementy członkowskie określonego typu. Wartość do przypisania do właściwości jest zawarty w elemencie właściwości. Zazwyczaj wartość otrzymuje jedno lub więcej elementów obiektu, ponieważ określenie obiektów jako wartości jest scenariusz tej składni elementu właściwości jest przeznaczona do adresu. Na koniec tag zamykający równoważne, które są takie same określanie *elementTypeName*. *propertyName* połączenie musi być podana w odpowiednich zagnieżdżanie i równowagi z innych tagów elementu.  
  
 Na przykład poniżej przedstawiono składnię elementu właściwości <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Wartość w elemencie właściwości można również nadać jako tekst wewnętrzny, w przypadkach, gdy jest określony typ właściwości jest typu wartości pierwotnej, takich jak <xref:System.String>, lub wyliczeniem, której nazwa jest określona. Te dwa sposoby użycia są dość rzadko, ponieważ każdy z tych przypadków można również użyć prostsze składni atrybutów. Jeden scenariusz do wypełniania elementu właściwości przy użyciu parametrów jest dla właściwości, które nie są właściwość zawartości XAML, ale nadal są używane do reprezentacji tekst interfejsu użytkownika, a poszczególne elementy odstępu, takie jak znaki wysuwu wiersza są wymagane do pojawiają się w tym tekście interfejsu użytkownika. Składnia atrybutu nie można zachować znaki wysuwu wiersza, ale można składni elementu właściwości, tak długo, jak znaczące zachowywanie białych jest aktywna (Aby uzyskać więcej informacji, zobacz [biały znak przetwarzanie w XAML](../../xaml-services/whitespace-processing-in-xaml.md)). Inny scenariusz polega na tak, aby [x: Uid — dyrektywa](../../xaml-services/x-uid-directive.md) można zastosować do elementu właściwości i tym samym Oznacz wartości w, zgodnie z wartością, który powinien być zlokalizowany w WPF danych wyjściowych BAML lub innych technik.  
  
 Element właściwości nie jest uwzględniona w drzewie logicznym WPF. Element właściwości jest po prostu specjalna składnia do ustawiania właściwości i nie jest element, który ma wystąpień lub wspierającą obiektu. (Aby uzyskać szczegółowe informacje dotyczące koncepcji drzewo logiczne, zobacz [drzewa w WPF](trees-in-wpf.md).)  
  
 W przypadku których są obsługiwane zarówno atrybut, jak i właściwość składnia elementu właściwości dwóch składni ogólnie ma ten sam wynik, ale precyzyjnie, takie jak obsługa białych mogą się nieznacznie różnić składni.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Składnia kolekcji  
 Specyfikacja XAML wymaga implementacji procesora XAML, aby zidentyfikować właściwości, których typ wartości jest kolekcją. Ogólne implementacji procesora XAML na platformie .NET opiera się na kodzie zarządzanym i środowiska CLR i identyfikuje typy kolekcji za pomocą jednego z następujących czynności:  
  
- Typ implementuje <xref:System.Collections.IList>.  
  
- Typ implementuje <xref:System.Collections.IDictionary>.  
  
- Typ pochodzi z <xref:System.Array> (Aby uzyskać więcej informacji na temat tablic w XAML, zobacz [x: Array — rozszerzenie znaczników](../../xaml-services/x-array-markup-extension.md).)  
  
 Jeśli typ właściwości to kolekcja, następnie typu wywnioskowanego kolekcji nie musi być określona w znaczników jako elementu obiektu. Zamiast tego elementów, które mają stać się elementów w kolekcji są określane jako jeden lub więcej elementów podrzędnych elementu właściwości. Każdego takiego elementu jest oceniany na obiekt podczas ładowania i dodawane do kolekcji, wywołując `Add` metody dorozumianych kolekcji. Na przykład <xref:System.Windows.Style.Triggers%2A> właściwość <xref:System.Windows.Style> przyjmuje typ kolekcji wyspecjalizowane <xref:System.Windows.TriggerCollection>, który implementuje <xref:System.Collections.IList>. Nie jest konieczne do utworzenia wystąpienia <xref:System.Windows.TriggerCollection> element obiektu w znaczniku. Zamiast tego należy określić co najmniej jedną <xref:System.Windows.Trigger> elementów jako elementów w obrębie `Style.Triggers` elementu właściwości, gdzie <xref:System.Windows.Trigger> (lub klasę pochodną) jest typu oczekiwanego typu elementu dla silnie typizowanym i niejawne <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Właściwość może być typem kolekcji i właściwość zawartości XAML dla tego typu i pochodne typy, która została omówiona w następnej sekcji tego tematu.  
  
 Element niejawnej kolekcji tworzy członka w reprezentacji drzewo logiczne, nawet jeśli nie ma w znacznikach jako element. Zazwyczaj konstruktora obiektu nadrzędnego typu wykonuje utworzyć wystąpienia dla kolekcji, która jest jednym z jej właściwości i początkowo pusta kolekcja staje się częścią drzewa obiektów.  
  
> [!NOTE]
>  Interfejsy ogólne listy i słownika (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane przez wykrywanie kolekcji. Można jednak użyć <xref:System.Collections.Generic.List%601> klasy jako klasę bazową, ponieważ implementuje <xref:System.Collections.IList> bezpośrednio lub <xref:System.Collections.Generic.Dictionary%602> jako klasa bazowa, ponieważ implementuje <xref:System.Collections.IDictionary> bezpośrednio.  
  
 Dla typów kolekcji na stronach dokumentacja platformy .NET tej składni, z pominięciem zamierzonego element obiektu dla kolekcji co pewien czas jest rejestrowany w sekcjach składnia XAML jako niejawne składni kolekcji.  
  
 Z wyjątkiem element główny każdego elementu obiektu w pliku XAML, który jest zagnieżdżona jako element podrzędny innego elementu jest naprawdę element, który jest jedno lub oba z następujących przypadków: członkiem niejawnej kolekcji własności odpowiedniego elementu nadrzędnego , lub element, który określa wartość właściwości zawartości XAML dla elementu nadrzędnego (XAML zawartości, właściwości, które zostanie omówiona w następnej sekcji). Innymi słowy relacja elementów nadrzędnych i elementy podrzędne na stronie znaczników jest naprawdę pojedynczego obiektu w katalogu głównym, a każdy element obiektu poniżej katalogu głównego jest pojedyncze wystąpienie, które udostępnia wartość właściwości elementu nadrzędnego, albo jeden z elementów w obrębie kolumna Zaznaczenie, który jest również wartość właściwości typu kolekcji nadrzędnej. To pojęcie z jednym elementem głównym jest wspólny z danymi XML i jest często wzmocnione zachowanie interfejsów API, które załadować XAML, takich jak <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Poniższy przykład jest składnia elementu obiektu dla kolekcji (<xref:System.Windows.Media.GradientStopCollection>) jawnie określony.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Należy pamiętać, że nie zawsze jest możliwe jawnie deklarować kolekcji. Na przykład, próba zadeklarować <xref:System.Windows.TriggerCollection> jawnie, w jak pokazano wcześniej <xref:System.Windows.Style.Triggers%2A> przykład może zakończyć się niepowodzeniem. Jawnie deklarowanie kolekcji wymaga, że klasa kolekcji musi obsługiwać domyślnego konstruktora, a <xref:System.Windows.TriggerCollection> nie ma domyślnego konstruktora.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Właściwości zawartości XAML  
 Składnia zawartości XAML jest składni, w którym włączono tylko w klasach, które określają <xref:System.Windows.Markup.ContentPropertyAttribute> jako części swojej deklaracji klasy. <xref:System.Windows.Markup.ContentPropertyAttribute> Odwołuje się do nazwy właściwości, który jest właściwość zawartości dla tego typu elementu (w tym klas pochodnych). Podczas przetwarzania przez procesor XAML, wszystkie elementy podrzędne lub tekst wewnętrzny, które znajdują się pomiędzy otwierającym, a zamykającym tagiem elementu obiektu zostanie przypisany jako wartość właściwości zawartości XAML dla tego obiektu. Możesz określić właściwości jawne elementy zawartości właściwości, ale to użycie nie jest zwykle wyświetlany w sekcji składni XAML w dokumentacji platformy .NET. Jawne/verbose technika ma okazjonalne wartość dla jasności znaczników lub jako styl znaczników, ale zazwyczaj celem właściwość content usprawniające znaczników, tak aby elementy, które są związane z intuicyjnie jako nadrzędny podrzędny, które mogą być zagnieżdżane bezpośrednio. Tagi element właściwości dla innych właściwości w elemencie nie są przypisane jako "treści" na ścisłym definicji języka XAML; one są przetwarzane wcześniej w kolejności przetwarzania analizatora XAML i nie są uwzględniane jako "zawartość".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Wartości właściwości zawartości XAML muszą być ciągłe  
 Wartość właściwości zawartości XAML podaje się całkowicie przed lub w całości po innych elementów właściwości w elemencie tego obiektu. Ta zasada obowiązuje, czy wartość właściwości zawartości XAML jest określony jako ciągu lub jako co najmniej jeden obiekt. Na przykład następujące znaczniki nie analizuje:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Jest to niedozwolone zasadniczo ponieważ gdy ta składnia wprowadzono jawne przy użyciu składni elementu właściwości dla właściwości zawartości, następnie właściwość zawartości będzie miał ustawienie dwa razy:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Przykład podobnie niedozwolone jest właściwość content jest kolekcją, elementy podrzędne są grupową właściwości elementów:  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>Właściwości zawartości i składnię kolekcji, w połączeniu  
 Aby zaakceptować więcej niż element pojedynczy obiekt jako zawartość, typ właściwości zawartości specjalnie należy typem kolekcji. Podobnie jak w składni elementu właściwości dla kolekcji typów, procesor XAML należy określić typy, które są typy kolekcji. Jeśli element ma właściwości zawartości XAML, typ właściwości zawartości XAML jest kolekcją, dorozumianych kolekcji nie muszą być określone w znacznikach jako elementu obiektu i właściwość zawartości XAML nie musi być określona jako el właściwości ement. W związku z tym jawnego modelu zawartości w znaczniku teraz może mieć więcej niż jeden element podrzędny przypisany jako zawartość. Poniżej przedstawiono składnię zawartości <xref:System.Windows.Controls.Panel> klasy pochodnej. Wszystkie <xref:System.Windows.Controls.Panel> klasy pochodne ustanowić właściwości zawartości XAML można <xref:System.Windows.Controls.Panel.Children%2A>, która wymaga wartości typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Należy pamiętać, że żaden element właściwości dla <xref:System.Windows.Controls.Panel.Children%2A> ani element dla <xref:System.Windows.Controls.UIElementCollection> jest wymagany w znaczniku. Jest to funkcja projektowania XAML aby rekursywnie zawiera elementy, które definiują [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są bardziej intuicyjne reprezentowana jako drzewo elementów zagnieżdżonych z relacjami element natychmiastowego nadrzędny podrzędny, bez interwencji tagów elementu właściwości lub Obiekty kolekcji. W rzeczywistości <xref:System.Windows.Controls.UIElementCollection> nie może być określona wyraźnie w znaczników jako elementu obiektu zgodnie z projektem. Ponieważ jedynym przeznaczeniem jest jako niejawnej kolekcji <xref:System.Windows.Controls.UIElementCollection> nie ujawnia publicznego konstruktora domyślnego i dlatego nie można utworzyć wystąpienia jako elementu obiektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Łączenie elementów właściwości i elementów obiektu w obiekcie z właściwością zawartości  
 Specyfikacja XAML deklaruje, że procesor XAML mogą zostać wymuszone, muszą być ciągłe elementów obiektu, które są używane do wypełnienia właściwość zawartości XAML w obrębie elementu obiektu, a nie mogą być mieszane. To ograniczenie względem łączenie elementów właściwości i zawartość jest wymuszana przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesorów XAML.  
  
 Możesz mieć element podrzędny obiektu jako pierwszego natychmiastowego kod znaczników w obrębie elementu obiektu. Następnie możesz wprowadzić elementów właściwości. Lub można określić jeden lub więcej elementów właściwości zawartości, a następnie więcej elementów właściwości. Jednak po prvek Vlastnosti poniżej zawartości, nie wolno wprowadzać żadnych dalszych zawartości, można dodać tylko elementy właściwości.  
  
 Ta zawartość / wymaganie kolejności element właściwości nie ma zastosowania do tekst wewnętrzny używany jako zawartości. Jednak nadal jest styl znaczników dobre zapewnienie tekst wewnętrzny ciągłego, ponieważ istotnych białych będzie trudne do wykrycia wizualnie w znaczniku, jeśli właściwość elementy są grupową tekst wewnętrzny.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Przestrzeń nazw XAML  
 Żaden z powyższych przykładach składni określona przestrzeń nazw XAML innej niż domyślna przestrzeń nazw XAML. W przypadku typowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, wartość domyślna przestrzeń nazw XAML jest określony jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw. Można określić XAML przestrzenie nazw, innym niż domyślna przestrzeń nazw XAML i nadal używać podobnej składni. Jednak następnie wszędzie gdzie klasa nosi, który nie jest dostępny w ramach domyślnej przestrzeni nazw XAML, nazwa tej klasy musi być poprzedzona z prefiks przestrzeni nazw XAML jako mapowany do odpowiedniego przestrzeń nazw środowiska CLR. Na przykład `<custom:Example/>` jest składnia elementu obiektu do utworzenia wystąpienia wystąpienie `Example` klasy, w którym przestrzeń nazw środowiska CLR zawierający klasy (i prawdopodobnie informacje zestawu zewnętrznego, które zawiera typy zapasowy) został poprzednio zamapowany na `custom` prefiks.  
  
 Aby uzyskać więcej informacji na temat przestrzeni nazw XAML, zobacz [przestrzeni nazw XAML i Namespace mapowania dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 XAML definiuje programowania jednostka, która umożliwia znaku ucieczki z normalnym XAML procesora obsługi ciąg wartości atrybutów lub elementów obiektu i odracza przetwarzania do klasy zapasowy rozszerzenia znaczników. Znak, który identyfikuje rozszerzenie znaczników w XAML procesor, gdy za pomocą składni atrybutów jest otwierający nawias klamrowy ({}), następuje dowolny znak inny niż zamykający nawias klamrowy (}). Pierwszy ciąg po otwierającym nawiasie klamrowym musi odwoływać się klasę, która zapewnia zachowanie określonego rozszerzenia, w których odwołanie może pominąć podciąg "Rozszerzenia", jeśli podciąg jest częścią nazwy klasy wartość true. Dzięki temu pojedyncza spacja może pojawić się, a następnie każdego następnego znaku jest używany jako dane wejściowe przez implementację rozszerzenia aż do napotkania zamykający nawias klamrowy.  
  
 Implementacja XAML .NET używa <xref:System.Windows.Markup.MarkupExtension> abstrakcyjna klasa jako podstawa dla rozszerzenia znaczników, obsługiwane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oraz innych platform lub technologii. Rozszerzenia znaczników, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] specjalnie implementuje często mają stanowić sposób odwoływać się do innych istniejących obiektów lub odroczone odwołuje się do obiektów, które będą oceniane w czasie wykonywania. Na przykład proste powiązanie danych WPF odbywa się przez określenie `{Binding}` — rozszerzenie znaczników zamiast wartość, która normalnie zajęłoby określonej właściwości. Włącz wiele rozszerzeń struktury znaczników WPF Składnia atrybutu dla właściwości, w którym składni atrybutów nie byłoby to możliwe. Na przykład <xref:System.Windows.Style> obiekt jest dość złożone typu, który zawiera zagnieżdżony szeregu obiektów i właściwości. Style na platformie WPF są zazwyczaj definiowane jako zasób w <xref:System.Windows.ResourceDictionary>i następnie odwoływać się za pomocą jednego z dwóch rozszerzenia znaczników WPF, wysyłających żądanie dotyczące zasobów. Rozszerzenie znaczników odracza obliczanie wartości właściwości do wyszukiwania zasobów i umożliwia zapewnienie wartość <xref:System.Windows.FrameworkElement.Style%2A> właściwość, biorąc typu <xref:System.Windows.Style>w atrybutu składni, jak w poniższym przykładzie:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 W tym miejscu `StaticResource` identyfikuje <xref:System.Windows.StaticResourceExtension> klasy dostarcza implementację rozszerzenia znaczników. Ciąg dalej `MyStyle` jest używany jako dane wejściowe dla innych niż domyślne <xref:System.Windows.StaticResourceExtension> konstruktora, gdzie parametr pobrane z parametrów rozszerzenia deklaruje żądany <xref:System.Windows.ResourceKey>. `MyStyle` oczekuje się [x: Key](../../xaml-services/x-key-directive.md) wartość <xref:System.Windows.Style> definiowany jako zasób. [Staticresource — rozszerzenie znaczników](staticresource-markup-extension.md) użycia żądań, że zasób służyć do zapewnienia <xref:System.Windows.Style> wartość właściwości przy użyciu logiki wyszukiwania zasobów statycznych w czasie ładowania.  
  
 Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md). Aby uzyskać odwołanie rozszerzenia znaczników i innych XAML programowania funkcje dostępne w ogólne implementacji .NET, XAML, zobacz [Namespace XAML (x:) Funkcje języka](../../xaml-services/xaml-namespace-x-language-features.md). Rozszerzenia znaczników charakterystyczne dla WPF, zobacz [WPF XAML rozszerzenia](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Dołączone właściwości  
 Właściwości dołączone są koncepcji programowania, wprowadzona w XAML, zgodnie z którą właściwości może być właścicielem i zdefiniowane przez określonego typu, ale ustawiony jako atrybutów lub elementów właściwości dowolnego elementu. Podstawowy scenariusz, dołączone właściwości są przeznaczone do jest umożliwienie elementy podrzędne w strukturze znaczników do informacji w raporcie na element nadrzędny bez konieczności model obiektowy szerokim zakresie udostępnionym dla wszystkich elementów. Z drugiej strony dołączone właściwości mogą być używane przez elementy nadrzędne informacji raportu, aby elementy podrzędne. Aby uzyskać więcej informacji na temat celem dołączone właściwości oraz tworzyć własne dołączonych właściwości, zobacz [Przegląd właściwości dołączonych](attached-properties-overview.md).  
  
 Dołączone właściwości użyj składni, która przypomina pozornie składni elementu właściwości, w tym również określić *typeName*. *propertyName* kombinacji. Istnieją dwie ważne różnice:  
  
- Możesz użyć *typeName*. *propertyName* kombinacji nawet wtedy, gdy ustawienie dołączoną właściwość za pomocą składni atrybutów. Właściwości dołączone są tylko wówczas, gdy kwalifikowania nazwy właściwości jest wymagany w składni atrybutów.  
  
- Umożliwia także składni elementu właściwości przypadku dołączonych właściwości. Jednak w przypadku składni elementu typowe właściwości *typeName* określasz, jest elementem obiektu, który zawiera element właściwości. Jeśli odwołujesz się do dołączoną właściwość, a następnie *typeName* jest klasa, która definiuje dołączona właściwość nie zawierającego element obiektu.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Dołączone zdarzenia  
 Zdarzenia dołączone są innego koncepcji programowania, wprowadzona w XAML, gdzie zdarzenia można zdefiniować w określonym typie, ale obsługi może być podłączona w dowolnym elemencie obiektu. W implementacji WOF często typ, który definiuje dołączone zdarzenie jest typem statycznych, który definiuje usługę, a czasami te dołączone zdarzenia są uwidocznione przez alias zdarzenie trasowane, typy, które udostępniają usługi. Programy obsługi dla zdarzenia dołączone są określane za pomocą składni atrybutów. Zgodnie z z dołączone zdarzenia składni atrybutów podzielonego dla dołączone zdarzenia umożliwić *typeName*. *eventName* użycia, gdzie *typeName* jest klasa, która zapewnia `Add` i `Remove` metod dostępu programu obsługi zdarzeń dla infrastruktury dołączone zdarzenie i *eventName* jest nazwa zdarzenia.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomia Element główny XAML  
 W poniższej tabeli przedstawiono typowe XAML element główny podzielone, przedstawiający określone atrybuty elementu głównego:  
  
|||  
|-|-|  
|`<Page`|Otwieranie elementu obiektu głównego|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Wartość domyślna ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) przestrzeń nazw XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Przestrzeń nazw XAML dla języka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklaracja klasy częściowej, która łączy znaczników wszelkie związane z kodem zdefiniowane dla klasy częściowej|  
|`>`|Końcowy element obiektu głównego. Obiekt nie jest jeszcze zamknięty, ponieważ element zawiera elementy podrzędne|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Opcjonalne i Nonrecommended XAML użycia  
 W poniższych sekcjach opisano użycia XAML z technicznego punktu widzenia obsługiwane przez procesory XAML, ale która generuje poziom szczegółowości lub inne estetycznych problemy, które zakłócają pozostałe czytelny dla człowieka, podczas tworzenia aplikacji, które zawierają źródła XAML pliki XAML.  
  
### <a name="optional-property-element-usages"></a>Opcjonalna właściwość elementu użycia  
 Opcjonalna właściwość elementu użycia obejmują jawnie wypisywanie zawartości właściwości elementu czy procesor XAML uwzględnia niejawne. Na przykład, kiedy Deklarujesz zawartość <xref:System.Windows.Controls.Menu>, można jawnie deklarować <xref:System.Windows.Controls.ItemsControl.Items%2A> zbiór <xref:System.Windows.Controls.Menu> jako `<Menu.Items>` tagu elementu właściwości, a miejsce każdego <xref:System.Windows.Controls.MenuItem> w ramach `<Menu.Items>`, a niż użycie niejawnej zachowanie procesora XAML, wszystkie elementy podrzędne elementu <xref:System.Windows.Controls.Menu> musi być <xref:System.Windows.Controls.MenuItem> i są umieszczane w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji. Czasami opcjonalne użycia może pomóc wizualnie wyjaśnienie struktury obiektu reprezentowane w znaczniku. Lub czasami użycie elementu właściwości jawne można uniknąć znaczników, który jest technicznie funkcjonalności, ale wizualnie mylące, takie jak rozszerzenia znaczników zagnieżdżone w obrębie wartość atrybutu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Pełna typeName.memberName kwalifikowana atrybutów  
 *TypeName*. *memberName* tworzą dla atrybutu faktycznie działa więcej niż tylko wielkością liter zdarzenia trasowanego powszechnie. Ale w innych sytuacjach formularza jest zbędny, a nie należy go, jeśli tylko do celów styl znaczników i czytelności. W poniższym przykładzie odwołania do każdego z trzech <xref:System.Windows.Controls.Control.Background%2A> atrybutu są całkowicie równoważne:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` działa, ponieważ kwalifikowaną wyszukiwania dla tej właściwości na <xref:System.Windows.Controls.Button> zakończy się pomyślnie (<xref:System.Windows.Controls.Control.Background%2A> został odziedziczony z kontrolki) i <xref:System.Windows.Controls.Button> jest klasa elementu obiekt lub klasa bazowa. `Control.Background` działa, ponieważ <xref:System.Windows.Controls.Control> klasa faktycznie definiuje <xref:System.Windows.Controls.Control.Background%2A> i <xref:System.Windows.Controls.Control> jest <xref:System.Windows.Controls.Button> klasy bazowej.  
  
 Jednak następujące *typeName*. *memberName* przykład użycia elementu form nie działa i jest wyświetlany związku z tym komentarzem:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> jest innej klasy pochodnej z <xref:System.Windows.Controls.Control>, a jeśli Gdybyśmy ustawili `Label.Background` w ramach <xref:System.Windows.Controls.Label> element obiektu to użycie będą działały. Jednak ponieważ <xref:System.Windows.Controls.Label> nie jest klasa lub klasa bazowa <xref:System.Windows.Controls.Button>, określonego zachowania procesora XAML jest następnie przetwarzanie `Label.Background` jako dołączona właściwość. `Label.Background` nie jest dostępna dołączoną właściwość, a to użycie nie powiedzie się.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName właściwości elementów  
 W analogiczny sposób jak *typeName*. *memberName* formularz działa w przypadku składni atrybutów *baseTypeName*. *memberName* składni działa w przypadku składni elementu właściwości. Na przykład działa w następującej składni:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 W tym miejscu podano element właściwości jako `Control.Background` mimo, że element właściwości zawarte w `Button`.  
  
 Podobnie jak w przypadku, ale *typeName*. *memberName* formularz dla atrybutów, *baseTypeName*. *memberName* jest niska stylu w znacznikach i należy jej unikać.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Namespace XAML (x:) Funkcje językowe](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [TypeConverters i XAML](typeconverters-and-xaml.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
