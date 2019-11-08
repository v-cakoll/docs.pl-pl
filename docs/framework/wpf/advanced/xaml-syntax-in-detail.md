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
ms.openlocfilehash: 10bd924664a469be26174fadf3892ee56aa33856
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740638"
---
# <a name="xaml-syntax-in-detail"></a>Szczegóły składni XAML
Ten temat definiuje warunki, które są używane do opisywania elementów składni języka XAML. Te warunki są często używane w całej pozostałej części tej dokumentacji, zarówno w przypadku dokumentacji WPF, jak i dla innych struktur, które używają języka XAML lub podstawowych pojęć XAML włączonych przez obsługę języka XAML na poziomie system. XAML. W tym temacie opisano podstawową terminologię wprowadzoną w temacie [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specyfikacja języka XAML  
 Terminologia dotycząca składni XAML zdefiniowana tutaj jest również zdefiniowana lub przywoływana w specyfikacji języka XAML. XAML to język oparty na języku XML, który następuje lub rozwija reguły strukturalne XML. Niektóre terminologia są udostępniane z lub opierają się na terminologii często używanej podczas opisywania języka XML lub modelu obiektowego dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat specyfikacji języka XAML, Pobierz [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525) z centrum pobierania Microsoft.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML i CLR  
 XAML jest językiem znaczników. Środowisko uruchomieniowe języka wspólnego (CLR), zgodnie z opisem jego nazwy, włącza wykonywanie w czasie wykonywania. Język XAML nie jest jednym ze wspólnych języków, które są bezpośrednio używane przez środowisko uruchomieniowe CLR. Zamiast tego można traktować kod XAML jako obsługujący własny system typów. Konkretny system analizowania kodu XAML używany przez WPF jest oparty na środowisku CLR i systemie typów CLR. Typy XAML są mapowane na typy CLR w celu utworzenia wystąpienia reprezentacji czasu wykonywania podczas analizowania kodu XAML dla WPF. Z tego powodu pozostała część dyskusji w tym dokumencie będzie zawierać odwołania do systemu typów CLR, mimo że w specyfikacji języka XAML nie są odpowiednie dyskusje składniowe. (Na poziomie specyfikacji języka XAML typy XAML mogą być mapowane na inne systemy typu, które nie muszą być środowiska CLR, ale które wymagają utworzenia i użycia innego parsera XAML).  
  
#### <a name="members-of-types-and-class-inheritance"></a>Elementy członkowskie typów i dziedziczenie klas  
 Właściwości i zdarzenia wyświetlane jako elementy członkowskie XAML typu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są często dziedziczone z typów podstawowych. Rozważmy na przykład ten przykład: `<Button Background="Blue" .../>`. Właściwość <xref:System.Windows.Controls.Control.Background%2A> nie jest bezpośrednio zadeklarowaną właściwością w klasie <xref:System.Windows.Controls.Button>, jeśli chcesz przejrzeć definicję klasy, wyniki odbicia lub dokumentację. Zamiast tego <xref:System.Windows.Controls.Control.Background%2A> jest dziedziczona z klasy podstawowej <xref:System.Windows.Controls.Control>.  
  
 Zachowanie dziedziczenia klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów XAML jest znaczącym wyjściem ze interpretacji języka XML przez wymuszone schemat. Dziedziczenie klasy może stać się skomplikowany, szczególnie w przypadku, gdy pośrednie klasy bazowe są abstrakcyjne lub gdy są wykorzystywane interfejsy. Jest to jedną z przyczyn, że zestaw elementów XAML i ich dopuszczalne atrybuty są trudne do przedstawienia dokładne i całkowicie przy użyciu typów schematów, które są zwykle używane do programowania XML, takie jak DTD lub XSD. Kolejną przyczyną jest to, że rozszerzanie i funkcje mapowania typów w języku XAML wykluczają kompletność wszelkich stałych reprezentacji dozwolonych typów i elementów członkowskich.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Składnia elementu obiektu  
 *Składnia elementu Object* jest składnią znaczników XAML, która tworzy wystąpienie klasy CLR lub struktury przez zadeklarowanie elementu XML. Ta składnia jest podobna do składni elementu innych języków znaczników, takich jak HTML. Składnia elementu obiektu rozpoczyna się od lewego nawiasu kątowego (\<), a następnie bezpośrednio według nazwy typu klasy lub struktury, która jest tworzona. Zero lub więcej spacji może następować po nazwie typu i zero lub więcej atrybutów może być również zadeklarowany dla elementu Object, z co najmniej jedną spacją oddzielającą pary nazwa atrybutu = "value". Na koniec należy wykonać jedną z następujących czynności:  
  
- Element i tag muszą być zamknięte przy użyciu ukośnika (/), a następnie bezpośrednio przez prawy nawias kątowy (>).  
  
- Tag otwierający musi być wykonany przy użyciu prawego nawiasu ostrego (>). Inne elementy obiektu, elementy właściwości lub tekst wewnętrzny mogą następować po tagu otwierającym. Dokładnie zawartość może być zawarta w tym miejscu jest zwykle ograniczone przez model obiektów elementu. Odpowiedni tag zamykający dla elementu Object musi również istnieć w prawidłowym zagnieżdżaniu i zrównoważeniu przy użyciu innych par tagów otwierających i zamykających.  
  
 KOD XAML zaimplementowany przez platformę .NET ma zestaw reguł, które mapują elementy obiektów do typów, atrybutów do właściwości lub zdarzeń oraz przestrzenie nazw XAML do przestrzeni nazw CLR oraz zestawu. W przypadku WPF i .NET elementy obiektów XAML są mapowane na typy .NET zgodnie z definicją w przywoływanych zestawach, a atrybuty są mapowane na elementy członkowskie tych typów. W przypadku odwoływania się do typu CLR w języku XAML masz również dostęp do dziedziczonych elementów członkowskich tego typu.  
  
 Na przykład poniższy przykład to składnia elementu obiektu, która tworzy wystąpienie nowego wystąpienia klasy <xref:System.Windows.Controls.Button>, a także określa atrybut <xref:System.Windows.FrameworkElement.Name%2A> i wartość dla tego atrybutu:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Poniższy przykład jest składnią elementu obiektu, która zawiera również składnię właściwości zawartości XAML. Wewnętrzny tekst zawarty w elemencie zostanie użyty do ustawienia właściwości <xref:System.Windows.Controls.TextBox> zawartości XAML, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modele zawartości  
 Klasa może obsługiwać użycie jako element obiektu XAML pod względem składni, ale ten element będzie działać prawidłowo w aplikacji lub stronie, gdy zostanie umieszczony w oczekiwanym miejscu ogólnego modelu zawartości lub drzewa elementów. Na przykład <xref:System.Windows.Controls.MenuItem> należy zwykle umieścić tylko jako element podrzędny klasy pochodnej <xref:System.Windows.Controls.Primitives.MenuBase>, takiej jak <xref:System.Windows.Controls.Menu>. Modele zawartości dla określonych elementów są udokumentowane jako część uwag na stronach klasy dla formantów i innych klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które mogą być używane jako elementy XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Właściwości elementów obiektów  
 Właściwości w języku XAML są ustawiane przez wiele możliwych składni. Składnia, która może być używana dla konkretnej właściwości, różni się w zależności od charakterystyki systemu typu podstawowego właściwości, która jest ustawiona.  
  
 Ustawiając wartości właściwości, należy dodać funkcje lub cechy do obiektów, tak jak istniejące w grafie obiektu czasu wykonywania. Początkowy stan utworzonego obiektu z elementu Object jest oparty na zachowaniu konstruktora bez parametrów. Zazwyczaj aplikacja będzie używać czegoś innego niż całkowicie domyślne wystąpienie danego obiektu.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Składnia atrybutu (właściwości)  
 Składnia atrybutu jest składnią znaczników XAML, która ustawia wartość właściwości przez zadeklarowanie atrybutu w istniejącym elemencie obiektu. Nazwa atrybutu musi być zgodna z nazwą elementu członkowskiego CLR właściwości klasy, która wykonuje kopię zapasową odpowiedniego elementu obiektu. Po nazwie atrybutu następuje operator przypisania (=). Wartość atrybutu musi być ciągiem ujętym w cudzysłów.  
  
> [!NOTE]
> Możesz użyć przemiennych cudzysłowów, aby umieścić znak cudzysłowu w atrybucie. Na przykład można użyć pojedynczego cudzysłowu jako środka do zadeklarowania ciągu, który zawiera znak cudzysłowu. Bez względu na to, czy są używane pojedyncze, czy podwójne cudzysłowy, należy użyć pasującej pary do otwierania i zamykania ciągu wartości atrybutu. Istnieją także sekwencje unikowe lub inne techniki umożliwiające pracę z ograniczeniami między znakami narzuconymi przez określoną składnię XAML. Zobacz [jednostki znaków XML i XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby można było ustawić za pomocą składni atrybutów, właściwość musi być publiczna i musi mieć możliwość zapisu. Wartość właściwości w systemie typu zapasowego musi być typem wartości lub musi być typem referencyjnym, który może być skonkretyzowany lub przywoływany przez procesor XAML podczas uzyskiwania dostępu do odpowiedniego typu kopii zapasowej.  
  
 Dla zdarzeń języka XAML WPF zdarzenie, do którego odwołuje się nazwa atrybutu, musi być publiczne i mieć publiczny delegat.  
  
 Właściwość lub zdarzenie musi być członkiem klasy lub struktury, która jest tworzona przez zawierający element obiektu.  
  
### <a name="processing-of-attribute-values"></a>Przetwarzanie wartości atrybutów  
 Wartość ciągu znajdująca się w cudzysłowie otwierającym i zamykającym jest przetwarzana przez procesor XAML. Dla właściwości domyślne zachowanie przetwarzania zależy od typu podstawowej właściwości CLR.  
  
 Wartość atrybutu jest wypełniana jedną z następujących, przy użyciu tej kolejności przetwarzania:  
  
1. Jeśli procesor XAML napotka nawias klamrowy lub element obiektu, który pochodzi od <xref:System.Windows.Markup.MarkupExtension>, to rozszerzenie znacznika, do którego występuje odwołanie, jest oceniane jako pierwsze zamiast przetwarzania wartości jako ciąg, a obiekt zwracany przez rozszerzenie znacznika jest używany jako wartość. W wielu przypadkach obiekt zwrócony przez rozszerzenie znacznika będzie odwołaniem do istniejącego obiektu lub wyrażeniem, które odkłada oceny do czasu wykonywania, i nie jest nowo utworzonym obiektem.  
  
2. Jeśli właściwość jest zadeklarowana z atrybutem <xref:System.ComponentModel.TypeConverter>lub typ wartości tej właściwości jest zadeklarowany za pomocą <xref:System.ComponentModel.TypeConverter>z atrybutami, wartość ciągu atrybutu jest przesyłana do konwertera typów jako dane wejściowe konwersji, a konwerter zwróci nowy obiekt np.  
  
3. Jeśli nie ma <xref:System.ComponentModel.TypeConverter>, podejmowana jest próba bezpośredniej konwersji na typ właściwości. Ten ostatni poziom to bezpośrednia konwersja w wartości natywnej analizatora między typami pierwotnymi języka XAML lub sprawdzanie nazw stałych w wyliczenia (analizator uzyskuje dostęp do pasujących wartości).  
  
#### <a name="enumeration-attribute-values"></a>Wartości atrybutów wyliczenia  
 Wyliczenia w języku XAML są przetwarzane wewnętrznie przez analizatory kodu XAML, a elementy członkowskie wyliczenia należy określić, określając nazwę ciągu jednego z nazwanych stałych wyliczeniowych.  
  
 W przypadku wartości wyliczenia nieflagowe zachowanie natywne polega na przetwarzaniu ciągu wartości atrybutu i rozwiązaniu go z jedną z wartości wyliczenia. Nie należy określać wyliczenia w *wyliczeniu*formatu. *Wartość*, jak w kodzie. Zamiast tego należy określić tylko *wartość*, a *Wyliczenie* jest wywnioskowane według typu właściwości, która jest ustawiana. Jeśli określisz atrybut w *wyliczeniu*. Formularz *wartości* nie zostanie poprawnie rozwiązany.  
  
 W przypadku wyliczeń flagwise zachowanie jest oparte na metodzie <xref:System.Enum.Parse%2A?displayProperty=nameWithType>. Można określić wiele wartości dla wyliczenia flagwise, oddzielając poszczególne wartości przecinkami. Nie można jednak łączyć wartości wyliczenia, które nie są flagwise. Na przykład nie można użyć składni przecinka, aby próbować utworzyć <xref:System.Windows.Trigger>, który działa na wielu warunkach wyliczenia braku flagi:  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Wyliczenia flagwise, które obsługują atrybuty, które są w języku XAML, są rzadkie w WPF. Jednak takie Wyliczenie jest <xref:System.Windows.Media.StyleSimulations>. Można na przykład użyć rozdzielanej przecinkami składni atrybutów flagwise, aby zmodyfikować przykład podany w uwagach dla klasy <xref:System.Windows.Documents.Glyphs>; `StyleSimulations = "BoldSimulation"` może stać się `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> to inna właściwość, w której można określić więcej niż jedną wartość wyliczenia. Jednak ta właściwość występuje w specjalnym przypadku, ponieważ Wyliczenie <xref:System.Windows.Input.ModifierKeys> obsługuje swój własny konwerter typów. Konwerter typu dla modyfikatorów używa znaku plus (+) jako ogranicznika, a nie przecinka (,). Ta konwersja obsługuje bardziej tradycyjną składnię do reprezentowania kombinacji klawiszy w programowaniu systemu Microsoft Windows, na przykład "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Odwołania do właściwości i nazwy elementu członkowskiego zdarzenia  
 Podczas określania atrybutu można odwołać się do dowolnej właściwości lub zdarzenia, które istnieje jako element członkowski typu CLR, który został utworzony dla elementu zawierającego obiekt.  
  
 Lub można odwołać się do dołączonej właściwości lub dołączonego zdarzenia, niezależnie od elementu zawierającego obiekt. (Dołączone właściwości zostały omówione w kolejnej sekcji).  
  
 Można również nazwać każde zdarzenie z dowolnego obiektu, który jest dostępny za pośrednictwem domyślnej przestrzeni nazw, przy użyciu *atrybutu TypeName*. częściowo kwalifikowana nazwa *zdarzenia* ; Ta składnia obsługuje dołączanie programów obsługi dla zdarzeń kierowanych, w których program obsługi ma obsługiwać routing zdarzeń z elementów podrzędnych, ale element nadrzędny nie ma także tego zdarzenia w tabeli elementów członkowskich. Ta składnia przypomina załączoną składnię zdarzenia, ale wydarzenie to nie jest zdarzeniem true. Zamiast tego odwołujesz się do zdarzenia z kwalifikowaną nazwą. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 W niektórych scenariuszach nazwy właściwości są czasami podawane jako wartość atrybutu, a nie nazwa atrybutu. Ta nazwa właściwości może również zawierać kwalifikatory, takie jak właściwość określona w formularzu *OwnerType*. *dependencypropertyname*. Ten scenariusz jest typowy podczas pisania stylów lub szablonów w języku XAML. Reguły przetwarzania dla nazw właściwości, które są podane jako wartość atrybutu, są różne i podlegają typowi właściwości ustawianej lub przez zachowania konkretnych podsystemów WPF. Aby uzyskać szczegółowe informacje, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
 Innym sposobem użycia nazw właściwości jest to, kiedy wartość atrybutu opisuje relację właściwości. Ta funkcja jest używana do wiązania danych i dla obiektów docelowych scenorysu i jest włączana przez klasę <xref:System.Windows.PropertyPath> i jej konwerter typów. Aby zapoznać się z bardziej szczegółowym opisem semantyki wyszukiwania, zobacz [składnia języka XAML PropertyPath](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Składnia elementu właściwości  
 *Składnia elementu właściwości* jest składnią nieproporcjonalną od podstawowych reguł składni XML dla elementów. W kodzie XML wartość atrybutu jest ciągiem de facto, z jedyną możliwą odmianą, w której jest używany format kodowania ciągów. W języku XAML można przypisać inne elementy obiektu jako wartość właściwości. Ta funkcja jest włączana przez składnię elementu właściwości. Zamiast właściwości, która jest określona jako atrybut w tagu elementu, właściwość jest określana za pomocą otwierającego znacznika elementu w *elementTypeName*. *PropertyName* , wartość właściwości jest określona w, a następnie element właściwości jest zamknięty.  
  
 W odróżnieniu od, składnia zaczyna się od lewego nawiasu kątowego (\<), a następnie bezpośrednio według nazwy typu klasy lub struktury, w której znajduje się składnia elementu właściwości. Następuje to bezpośrednio przez pojedyncze kropki (.), a następnie według nazwy właściwości, a następnie prawego nawiasu ostrego (>). Podobnie jak w przypadku składni atrybutów, ta właściwość musi istnieć w zadeklarowanych publicznych składowych określonego typu. Wartość, która ma zostać przypisana do właściwości, znajduje się w elemencie właściwości. Zazwyczaj wartość jest podawana jako jeden lub więcej elementów obiektów, ponieważ określenie obiektów jako wartości jest scenariuszem, który jest przeznaczony dla składni elementu właściwości. Na koniec równoważny tag zamykający, który określa ten sam *elementTypeName*. należy podać kombinację *PropertyName* , w odpowiednim zagnieżdżaniu i zrównoważeniu z innymi tagami elementów.  
  
 Na przykład następująca jest składnia elementu właściwości dla właściwości <xref:System.Windows.FrameworkElement.ContextMenu%2A> <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Wartość wewnątrz elementu właściwości można również podać jako tekst wewnętrzny, w przypadkach, gdy określony typ właściwości jest typem wartości pierwotnej, takim jak <xref:System.String>, lub wyliczeniem, w którym określono nazwę. Te dwa użycia są nieco nietypowe, ponieważ każdy z tych przypadków może również używać prostszej składni atrybutów. Jeden z scenariuszy wypełniania elementu właściwości ciągiem jest przeznaczony dla właściwości, które nie są właściwością zawartości XAML, ale nadal są używane do reprezentacji tekstu interfejsu użytkownika, a szczególne elementy białych znaków, takie jak wysuwu wiersza są wymagane do wyświetlania w tym tekście interfejsu użytkownika. Składnia atrybutu nie może zachować instrukcji wysuwu wiersza, ale składnia elementu właściwości może, tak długo, jak znaczące zachowywanie białych miejsc jest aktywne (Aby uzyskać szczegółowe informacje, zobacz [białe przetwarzanie miejsca w języku XAML](../../xaml-services/whitespace-processing-in-xaml.md)). Innym scenariuszem jest to, że [dyrektywę x:UID —](../../xaml-services/x-uid-directive.md) można zastosować do elementu Property i w związku z tym oznaczyć wartość jako wartość, która powinna być zlokalizowana w pozostałej wartości wynikowej programu WPF lub przez inne techniki.  
  
 Element Property nie jest reprezentowany w drzewie logicznym WPF. Element właściwości jest tylko określoną składnią służącą do ustawiania właściwości i nie jest elementem, który ma kopię zapasową wystąpienia lub obiektu. (Aby uzyskać szczegółowe informacje na temat koncepcji drzewa logicznego, zobacz [drzewa w WPF](trees-in-wpf.md)).  
  
 W przypadku właściwości, w których obsługiwana jest zarówno składnia atrybutu, jak i element właściwości, dwie składnie zwykle mają ten sam wynik, chociaż subtleties takich jak obsługa białych znaków może się nieco różnić między składniami.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Składnia kolekcji  
 Specyfikacja XAML wymaga implementacji procesora XAML, aby identyfikować właściwości, w których typ wartości jest kolekcją. Ogólna implementacja procesora XAML w programie .NET opiera się na kodzie zarządzanym i CLR, a ponadto rozpoznaje typy kolekcji przy użyciu jednego z następujących elementów:  
  
- Typ implementuje <xref:System.Collections.IList>.  
  
- Typ implementuje <xref:System.Collections.IDictionary>.  
  
- Typ pochodzi z <xref:System.Array> (Aby uzyskać więcej informacji na temat tablic w języku XAML, zobacz [X:Array Markup Extension](../../xaml-services/x-array-markup-extension.md)).  
  
 Jeśli typ właściwości jest kolekcją, nie trzeba określać typu kolekcji wywnioskowanej w znaczniku jako elementu obiektu. Zamiast tego elementy, które mają zostać elementami w kolekcji, są określone jako jeden lub więcej elementów podrzędnych elementu właściwości. Każdy taki element jest oceniany do obiektu podczas ładowania i dodawany do kolekcji, wywołując metodę `Add` implikowanej kolekcji. Na przykład właściwość <xref:System.Windows.Style.Triggers%2A> <xref:System.Windows.Style> przyjmuje wyspecjalizowany typ kolekcji <xref:System.Windows.TriggerCollection>, który implementuje <xref:System.Collections.IList>. Nie jest konieczne tworzenie wystąpienia <xref:System.Windows.TriggerCollection> elementu obiektu w znaczniku. Zamiast tego należy określić co najmniej jeden <xref:System.Windows.Trigger> elementów jako elementy w elemencie właściwości `Style.Triggers`, gdzie <xref:System.Windows.Trigger> (lub Klasa pochodna) jest typem oczekiwanym jako typ elementu w przypadku silnie wpisanej i niejawnej <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Właściwość może być zarówno typem kolekcji, jak i właściwością zawartości XAML dla tego typu i typów pochodnych, który został omówiony w następnej sekcji tego tematu.  
  
 Niejawny element kolekcji tworzy element członkowski w reprezentacji drzewa logicznego, chociaż nie jest wyświetlany w znaczniku jako element. Zazwyczaj Konstruktor typu nadrzędnego wykonuje Tworzenie wystąpienia kolekcji, która jest jedną z jej właściwości, a początkowo pusta kolekcja jest częścią drzewa obiektów.  
  
> [!NOTE]
> Ogólne interfejsy list i słowników (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane na potrzeby wykrywania kolekcji. Można jednak użyć klasy <xref:System.Collections.Generic.List%601> jako klasy bazowej, ponieważ implementuje ona <xref:System.Collections.IList> bezpośrednio lub <xref:System.Collections.Generic.Dictionary%602> jako klasę bazową, ponieważ implementuje <xref:System.Collections.IDictionary> bezpośrednio.  
  
 Na stronach referencyjnych platformy .NET dla typów kolekcji, ta składnia z świadomym pominięciem elementu Object dla kolekcji jest czasami notowana w sekcjach składni XAML jako niejawna składnia kolekcji.  
  
 Z wyjątkiem elementu głównego, każdy element obiektu w pliku XAML, który jest zagnieżdżony jako element podrzędny innego elementu jest naprawdę elementem, który jest jednym lub obu następujących przypadków: element członkowski niejawnej właściwości kolekcji jego elementu nadrzędnego lub element określający wartość właściwości zawartości XAML dla elementu nadrzędnego (właściwości zawartości XAML zostaną omówione w kolejnej sekcji). Innymi słowy, relacja elementów nadrzędnych i elementów podrzędnych na stronie znaczników jest naprawdę pojedynczym obiektem w katalogu głównym, a każdy element obiektu znajdujący się pod elementem głównym jest pojedynczym wystąpieniem, które udostępnia wartość właściwości nadrzędnego lub jeden z elementów w kolumnie. lection to również wartość właściwości typu kolekcji elementu nadrzędnego. Ta koncepcja jednoelementowa jest często stosowana w języku XML i jest często wzmacniana podczas działania interfejsów API, które ładują kod XAML, taki jak <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Poniższy przykład jest składnią z elementem obiektu dla kolekcji (<xref:System.Windows.Media.GradientStopCollection>) określoną jawnie.  
  
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
  
 Należy pamiętać, że nie zawsze można jawnie zadeklarować kolekcji. Na przykład próba zadeklarować <xref:System.Windows.TriggerCollection> jawnie w pokazanym wcześniej przykładzie <xref:System.Windows.Style.Triggers%2A> się nie powiedzie. Jawne deklarowanie kolekcji wymaga, aby Klasa kolekcji obsługiwała Konstruktor bez parametrów, a <xref:System.Windows.TriggerCollection> nie ma konstruktora bez parametrów.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Właściwości zawartości XAML  
 Składnia zawartości XAML jest składnią, która jest włączona tylko w klasach, które określają <xref:System.Windows.Markup.ContentPropertyAttribute> w ramach ich deklaracji klasy. <xref:System.Windows.Markup.ContentPropertyAttribute> odwołuje się do nazwy właściwości, która jest właściwością zawartości dla tego typu elementu (łącznie z klasami pochodnymi). W przypadku przetworzenia przez procesor XAML wszystkie elementy podrzędne lub tekst wewnętrzny, które znajdują się między tagiem otwierającym i zamykającym elementu obiektu zostanie przypisany do wartości właściwości zawartości XAML dla tego obiektu. Możesz określić jawne elementy właściwości dla właściwości content, ale to użycie nie jest zazwyczaj wyświetlane w sekcjach składni XAML w dokumentacji platformy .NET. Technika Explicit/verbose ma okazjonalną wartość dla jasności adiustacji lub w postaci stylu znaczników, ale zazwyczaj jest to metoda, którą Właściwość zawartości ma na celu uproszczenie adiustacji, tak aby elementy, które są intuicyjnie powiązane jako element nadrzędny-podrzędny, mogły być zagnieżdżone bezpośrednio. Tagi elementu właściwości dla innych właściwości elementu nie są przypisywane jako "zawartość" na ścisłą definicję języka XAML; są one przetwarzane wcześniej w kolejności przetwarzania analizatora XAML i nie są uważane za "zawartość".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Wartości właściwości zawartości XAML muszą być ciągłe  
 Wartość właściwości zawartości XAML musi zostać nadana całkowicie przed lub całkowicie po jakimkolwiek innym elementom właściwości w tym elemencie obiektu. Jest to prawdziwe, czy wartość właściwości zawartości XAML jest określona jako ciąg, czy jako jeden lub więcej obiektów. Na przykład następujące znaczniki nie są analizowane:  
  
```xaml  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Jest to niedozwolone, ponieważ w przypadku, gdy składnia została jawnie wprowadzona przy użyciu składni elementu właściwości dla właściwości content, właściwość content zostanie ustawiona dwukrotnie:  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobnym przykładem jest to, że właściwość content jest kolekcją, a elementy podrzędne są przeplatane z elementami właściwości:  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>Połączone właściwości zawartości i kolekcji  
 Aby zaakceptować więcej niż jeden element obiektu jako zawartość, typ właściwości zawartości musi być określony jako typ kolekcji. Podobnie jak w przypadku składni elementu właściwości dla typów kolekcji, procesor XAML musi identyfikować typy, które są typami kolekcji. Jeśli element ma właściwość zawartości XAML i typ właściwości zawartości XAML jest kolekcją, to implikowany typ kolekcji nie musi być określony w znaczniku jako element obiektu i Właściwość zawartości XAML nie musi być określona jako właściwość El akiety. W związku z tym widoczny model zawartości w znaczniku może teraz mieć więcej niż jeden element podrzędny przypisany jako zawartość. Poniżej znajduje się składnia zawartości dla <xref:System.Windows.Controls.Panel> klasy pochodnej. Wszystkie <xref:System.Windows.Controls.Panel> pochodne klasy określają Właściwość zawartości XAML, która ma być <xref:System.Windows.Controls.Panel.Children%2A>, co wymaga wartości typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Należy zauważyć, że nie jest wymagany element Property elementu <xref:System.Windows.Controls.Panel.Children%2A> ani elementu dla <xref:System.Windows.Controls.UIElementCollection> w znaczniku. Jest to funkcja projektowa języka XAML, dzięki której rekursywnie zawarte elementy, które definiują [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], są bardziej intuicyjnie reprezentowane jako drzewo zagnieżdżonych elementów z bezpośrednimi relacjami elementów nadrzędny-podrzędny, bez naruszania tagów elementów właściwości lub obiekty kolekcji. W rzeczywistości nie można jawnie określić <xref:System.Windows.Controls.UIElementCollection> w znaczniku jako elementu obiektu według konstrukcji. Ponieważ jego jedynym zamierzonym zastosowaniem jest jako kolekcja niejawna, <xref:System.Windows.Controls.UIElementCollection> nie ujawnia publicznego konstruktora bez parametrów i w związku z tym nie można utworzyć wystąpienia jako elementu obiektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Mieszanie elementów właściwości i elementów obiektów w obiekcie z właściwością zawartości  
 Specyfikacja języka XAML deklaruje, że procesor XAML może wymusić, że elementy obiektu, które są używane do wypełniania właściwości zawartości XAML wewnątrz elementu obiektu, muszą być ciągłe i nie mogą być mieszane. To ograniczenie dotyczące mieszania elementów właściwości i zawartości jest wymuszane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesorów XAML.  
  
 Można mieć element podrzędny obiektu jako pierwszy natychmiastowy znacznik w elemencie obiektu. Następnie można wprowadzać elementy właściwości. Lub można określić jeden lub więcej elementów właściwości, a następnie zawartość, a następnie więcej elementów właściwości. Ale gdy element właściwości następuje po zawartości, nie można wprowadzić żadnej dalszej zawartości, można dodać tylko elementy właściwości.  
  
 Ten wymóg porządkowania zawartości/elementu właściwości nie ma zastosowania do tekstu wewnętrznego używanego jako zawartość. Jednak nadal jest dobrym stylem znaczników, aby zachować ciągły tekst wewnętrzny, ponieważ znaczący biały znak jest trudny do wykrycia wizualnie w znaczniku, jeśli elementy właściwości są przeplatane tekstem wewnętrznym.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Przestrzeń nazw XAML  
 Żaden z powyższych przykładów składni nie określił przestrzeni nazw XAML innej niż domyślna przestrzeń nazw XAML. W typowych aplikacjach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] domyślna przestrzeń nazw XAML jest określana jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw. Możesz określić obszary nazw XAML inne niż domyślna przestrzeń nazw XAML i nadal używać podobnej składni. Ale w każdym przypadku, gdy Klasa ma nazwę, która nie jest dostępna w domyślnej przestrzeni nazw języka XAML, nazwa klasy musi być poprzedzona prefiksem przestrzeni nazw XAML jako zamapowana do odpowiedniej przestrzeni nazw środowiska CLR. Na przykład `<custom:Example/>` jest składnią elementu obiektu, aby utworzyć wystąpienie klasy `Example`, gdzie przestrzeń nazw CLR zawierająca tę klasę (a prawdopodobnie informacje o zestawie zewnętrznym, które zawierają typy zapasowe), zostały wcześniej zamapowane na `custom` prefiks.  
  
 Aby uzyskać więcej informacji na temat przestrzeni nazw XAML, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia struktury znaczników  
 XAML definiuje jednostkę programowania rozszerzenia znaczników, która umożliwia wyjście z normalnego obsługi procesora XAML wartości atrybutów ciągów lub elementów obiektów, i rozszerza przetwarzanie do klasy zapasowej. Znak, który identyfikuje rozszerzenie znaczników dla procesora XAML, gdy jest używana składnia atrybutu jest otwierającym nawiasem klamrowym ({), po którym następuje dowolny znak inny niż zamykający nawias klamrowy (}). Pierwszy ciąg po otwierającym nawiasie klamrowym musi odwoływać się do klasy, która zapewnia określone zachowanie rozszerzenia, gdzie odwołanie może pominąć podciąg "rozszerzenie", jeśli podciąg jest częścią prawdziwej nazwy klasy. Po wykonaniu tej operacji może pojawić się pojedyncze miejsce, a następnie każdy pomyślny znak jest używany jako dane wejściowe przez implementację rozszerzenia, aż do momentu zakończenia zamykającego nawiasu klamrowego.  
  
 Implementacja języka XAML platformy .NET używa klasy abstrakcyjnej <xref:System.Windows.Markup.MarkupExtension> jako podstawy dla wszystkich rozszerzeń znaczników obsługiwanych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a także innych struktur lub technologii. Rozszerzenia znaczników, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zaimplementowane, są często przeznaczone do zapewnienia odwołujących się do innych istniejących obiektów lub do wykonywania odroczonych odwołań do obiektów, które będą oceniane w czasie wykonywania. Na przykład proste powiązanie danych WPF jest realizowane przez określenie rozszerzenia znacznika `{Binding}` zamiast wartości, która zwykle przyjmuje dana właściwość. Wiele rozszerzeń znaczników WPF włącza składnię atrybutu dla właściwości, gdzie składnia atrybutu nie może być w innym przypadku możliwa. Na przykład obiekt <xref:System.Windows.Style> jest relatywnie złożonym typem, który zawiera zagnieżdżoną serię obiektów i właściwości. Style w WPF są zwykle definiowane jako zasób w <xref:System.Windows.ResourceDictionary>, a następnie przywoływane przez jeden z dwóch rozszerzeń znaczników WPF, które żądają zasobu. Rozszerzenie znaczników służy do obliczania wartości właściwości do wyszukiwania zasobów i umożliwia udostępnienie wartości właściwości <xref:System.Windows.FrameworkElement.Style%2A>, pobierając <xref:System.Windows.Style>typu, w składni atrybutów, jak w poniższym przykładzie:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 W tym miejscu `StaticResource` identyfikuje klasę <xref:System.Windows.StaticResourceExtension>, która dostarcza implementację rozszerzenia znacznika. Następny ciąg `MyStyle` jest używany jako dane wejściowe dla niedomyślnego konstruktora <xref:System.Windows.StaticResourceExtension>, gdzie parametr pobrany z ciągu rozszerzenia deklaruje żądany <xref:System.Windows.ResourceKey>. oczekiwaną `MyStyle` jest wartość [x:Key](../../xaml-services/x-key-directive.md) <xref:System.Windows.Style> zdefiniowana jako zasób. Użycie [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md) wymaga, aby zasób był używany do udostępniania wartości właściwości <xref:System.Windows.Style> za pomocą logiki wyszukiwania zasobów statycznych w czasie ładowania.  
  
 Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md). Aby uzyskać informacje na temat rozszerzeń znaczników i innych funkcji programowania XAML włączonych w ogólnej implementacji języka XAML platformy .NET, zobacz [przestrzeń nazw XAML (x:) Funkcje językowe](../../xaml-services/xaml-namespace-x-language-features.md). W przypadku rozszerzeń znaczników specyficznych dla platformy WPF zobacz [WPF XAML Extensions](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Dołączone właściwości  
 Dołączone właściwości to koncepcja programowania wprowadzona w języku XAML, w której właściwości mogą być własnością określonego typu, ale są ustawiane jako atrybuty lub elementy właściwości dla dowolnego elementu. Głównym scenariuszem, do którego załączono właściwości, jest włączenie elementów podrzędnych w strukturze znaczników w celu zgłoszenia informacji do elementu nadrzędnego, bez konieczności szerokiego modelu obiektów wspólnych dla wszystkich elementów. Z drugiej strony, dołączone właściwości mogą być używane przez elementy nadrzędne do raportowania informacji do elementów podrzędnych. Aby uzyskać więcej informacji na temat przeznaczenia załączonych właściwości i sposobu tworzenia własnych dołączanych właściwości, zobacz [Omówienie dołączonych właściwości](attached-properties-overview.md).  
  
 Dołączone właściwości używają składni, która jest w pełni podobna do składni elementu właściwości, w tym celu należy również określić *Właściwość TypeName*. kombinacja *PropertyName* . Istnieją dwie istotne różnice:  
  
- Można użyć elementu *TypeName*. połączenie *PropertyName* nawet podczas ustawiania właściwości dołączonej za poorednictwem składni atrybutu. Dołączone właściwości są jedynym przypadkiem, gdzie Kwalifikowanie nazwy właściwości jest wymaganiem w składni atrybutu.  
  
- Można również użyć składni elementu właściwości dla dołączonych właściwości. Jednak dla typowej składni elementu właściwości, określony przez użytkownika *atrybut TypeName* jest elementem obiektu, który zawiera element właściwości. Jeśli odwołujesz się do dołączonej właściwości, właściwość *TypeName* jest klasą, która definiuje załączoną właściwość, a nie element obiektu zawierającego.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Dołączone zdarzenia  
 Dołączone zdarzenia to inne koncepcje programowania wprowadzone w języku XAML, w którym zdarzenia mogą być definiowane przez określony typ, ale programy obsługi mogą być dołączane do dowolnego elementu obiektu. W implementacji WOF często typ, który definiuje dołączone zdarzenie, jest typem statycznym, który definiuje usługę i czasami te dołączone zdarzenia są udostępniane przez alias zdarzenia kierowanego w typach, które uwidaczniają usługę. Procedury obsługi dla dołączonych zdarzeń są określane za poorednictwem składni atrybutów. Podobnie jak w przypadku dołączonych zdarzeń, składnia atrybutu jest rozwinięta dla dołączonych zdarzeń, aby zezwolić na *Właściwość TypeName*. Nazwa *zdarzenia* użycie, gdzie *TypeName* jest klasą, która zapewnia `Add` i `Remove` metody dostępu programu obsługi zdarzeń dla infrastruktury dołączonego zdarzenia, a *EventName* jest nazwą zdarzenia.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomia elementu głównego XAML  
 W poniższej tabeli przedstawiono typowy element główny XAML podzielony w dół, pokazujący konkretne atrybuty elementu głównego:  
  
|||  
|-|-|  
|`<Page`|Otwieranie elementu obiektu głównego elementu|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Domyślna przestrzeń nazw XAML ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Przestrzeń nazw XAML języka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklaracja klasy częściowej, która łączy znaczniki z dowolnym kodem zdefiniowanym dla klasy częściowej|  
|`>`|Koniec elementu obiektu dla katalogu głównego. Obiekt nie jest jeszcze zamknięty, ponieważ element zawiera elementy podrzędne|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Opcjonalne i niezalecane użycia języka XAML  
 W poniższych sekcjach opisano użycie języka XAML, które są technicznie obsługiwane przez procesory XAML, ale w celu uzyskania szczegółowości lub innych problemów estetycznych, które zakłócają pliki XAML, które pozostały do odczytania przez użytkownika podczas tworzenia aplikacji zawierających źródła XAML.  
  
### <a name="optional-property-element-usages"></a>Użycie opcjonalnych elementów właściwości  
 Użycie opcjonalnych elementów właściwości obejmuje jawne zapisanie właściwości zawartości elementu, które procesor XAML traktuje jako niejawne. Na przykład podczas deklarowania zawartości <xref:System.Windows.Controls.Menu>można jawnie zadeklarować kolekcję <xref:System.Windows.Controls.ItemsControl.Items%2A> <xref:System.Windows.Controls.Menu> jako tag elementu `<Menu.Items>` właściwości i umieścić każdy <xref:System.Windows.Controls.MenuItem> w `<Menu.Items>`Zamiast używać niejawnego działania procesora XAML, które wszystkie elementy podrzędne <xref:System.Windows.Controls.Menu> muszą być <xref:System.Windows.Controls.MenuItem> i są umieszczane w kolekcji <xref:System.Windows.Controls.ItemsControl.Items%2A>. Czasami opcjonalne użycia mogą pomóc wizualnie wyjaśnić strukturę obiektów, jak to zostało reprezentowane w znaczniku. Lub czasami jawne użycie elementu właściwości może uniknąć znaczników, które są technicznie funkcjonalne, ale wizualnie mylące, takie jak zagnieżdżone rozszerzenia znaczników w wartości atrybutu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Pełne atrybuty typeName. MemberName  
 *Nazwa*typu. *element MemberName* dla atrybutu faktycznie działa bardziej uniwersalnie niż tylko w przypadku zdarzenia kierowanego. Ale w innych sytuacjach, w których formularz jest zbędny i należy go unikać, jeśli tylko z przyczyn stylu znaczników i czytelności. W poniższym przykładzie wszystkie trzy odwołania do atrybutu <xref:System.Windows.Controls.Control.Background%2A> są całkowicie równoważne:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` działa, ponieważ kwalifikowane wyszukiwanie dla tej właściwości na <xref:System.Windows.Controls.Button> jest pomyślne (<xref:System.Windows.Controls.Control.Background%2A> zostało odziedziczone z kontrolki), a <xref:System.Windows.Controls.Button> jest klasą elementu obiektu lub klasą bazową. `Control.Background` działa, ponieważ Klasa <xref:System.Windows.Controls.Control> rzeczywiście definiuje <xref:System.Windows.Controls.Control.Background%2A> i <xref:System.Windows.Controls.Control> jest <xref:System.Windows.Controls.Button> klasą bazową.  
  
 Jednak następujący *atrybut TypeName*. przykład *elementu MemberName* nie działa i jest w ten sposób pokazywany jako komentarz:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> jest kolejną klasą pochodną <xref:System.Windows.Controls.Control>i jeśli określono `Label.Background` w elemencie <xref:System.Windows.Controls.Label> obiektu, to użycie będzie działało. Jednak ponieważ <xref:System.Windows.Controls.Label> nie jest klasą ani klasą bazową <xref:System.Windows.Controls.Button>, określone zachowanie procesora XAML ma na celu przetworzenie `Label.Background` jako dołączonej właściwości. `Label.Background` nie jest dostępna w dołączonej właściwości i to użycie nie powiedzie się.  
  
### <a name="basetypenamemembername-property-elements"></a>Basename. MemberName — elementy właściwości  
 W analogiczny sposób do metody *TypeName*. *element MemberName* działa w przypadku składni atrybutów, *BaseType*. Składnia *MemberName* działa dla składni elementu właściwości. Na przykład następująca składnia działa:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 W tym miejscu element Property został podany jako `Control.Background`, mimo że element Property został zawarty w `Button`.  
  
 Ale podobnie jak *TypeName*. formularz *MemberName* dla atrybutów, *basename*. *element MemberName* ma słabą styl w znacznikach i należy go unikać.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Przestrzeń nazw XAML (x:) — funkcje językowe](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [TypeConverters i XAML](typeconverters-and-xaml.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
