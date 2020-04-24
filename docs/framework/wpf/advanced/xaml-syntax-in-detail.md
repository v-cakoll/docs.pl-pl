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
ms.openlocfilehash: 5f8bb862ce443fd7397036b10f69cda65a6960bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646147"
---
# <a name="xaml-syntax-in-detail"></a>Szczegóły składni XAML
W tym temacie zdefiniowano terminy, które są używane do opisywania elementów składni XAML. Terminy te są często używane w pozostałej części tej dokumentacji, zarówno dla dokumentacji WPF w szczególności i dla innych struktur, które używają XAML lub podstawowe pojęcia XAML włączone przez obsługę języka XAML na poziomie System.Xaml. W tym temacie rozwija się podstawowa terminologia wprowadzona w temacie [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>Specyfikacja języka XAML  
 Zdefiniowana w tym miejscu terminologia składni XAML jest również zdefiniowana lub odwołuje się do specyfikacji języka XAML. XAML jest językiem opartym na języku XML i następuje lub rozszerza reguły strukturalne XML. Niektóre terminologii są współużytkowane lub są oparte na terminologii powszechnie używanej podczas opisywania języka XML lub modelu obiektu dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat specyfikacji języka XAML, pobierz [ \[plik MS-XAML\] ](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) z Centrum pobierania Microsoft.  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML i CLR  
 XAML jest językiem znaczników. Środowisko wykonawcze języka wspólnego (CLR), zgodnie z implikowaną nazwą, umożliwia wykonywanie środowiska uruchomieniowego. XAML nie jest sam w sobie jednym ze wspólnych języków, który jest bezpośrednio używane przez środowisko uruchomieniowe CLR. Zamiast tego można myśleć xaml jako obsługi własnego systemu typu. System analizy XAML, który jest używany przez WPF jest zbudowany na CLR i systemu typu CLR. Typy XAML są mapowane do typów CLR, aby utworzyć wystąpienie reprezentacji czasu wykonywania, gdy jest analizowany kod XAML dla WPF. Z tego powodu pozostała część dyskusji na temat składni w tym dokumencie będzie zawierać odwołania do systemu typu CLR, nawet jeśli równoważne dyskusje składni w specyfikacji języka XAML nie. (Na poziomie specyfikacji języka XAML typy XAML mogą być mapowane do dowolnego innego systemu typu, który nie musi być CLR, ale wymagałoby to utworzenia i użycia innego analizatora XAML).  
  
#### <a name="members-of-types-and-class-inheritance"></a>Elementy członkowskie typów i dziedziczenie klas  
 Właściwości i zdarzenia, które pojawiają się jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy członkowskie XAML typu są często dziedziczone z typów podstawowych. Rozważmy na przykład: `<Button Background="Blue" .../>`. Właściwość <xref:System.Windows.Controls.Control.Background%2A> nie jest natychmiast zadeklarowane właściwości w <xref:System.Windows.Controls.Button> klasie, jeśli były do zapoznania się z definicji klasy, wyniki odbicia lub dokumentacji. Zamiast tego <xref:System.Windows.Controls.Control.Background%2A> jest dziedziczona <xref:System.Windows.Controls.Control> z klasy podstawowej.  
  
 Zachowanie dziedziczenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas elementów XAML jest znaczącym odejściem od interpretacji znaczników XML wymuszonych schematem. Dziedziczenie klas może stać się złożone, szczególnie gdy pośrednie klasy podstawowe są abstrakcyjne lub gdy zaangażowane są interfejsy. Jest to jeden z powodów, że zestaw elementów XAML i ich dopuszczalne atrybuty jest trudne do przedstawienia dokładnie i całkowicie przy użyciu typów schematów, które są zwykle używane do programowania XML, takich jak format DTD lub XSD. Innym powodem jest to, że rozszerzalność i funkcje mapowania typów samego języka XAML wykluczają kompletność jakiejkolwiek stałej reprezentacji dopuszczalnych typów i elementów członkowskich.  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>Składnia elementu obiektu  
 *Składnia elementu obiektu* to składnia znaczników XAML, która występuje w wyniku wystąpienia klasy lub struktury CLR przez zadeklarowanie elementu XML. Ta składnia przypomina składnię elementu innych języków znaczników, takich jak HTML. Składnia elementu obiektu zaczyna się od\<nawiasu kątowego z lewej strony ( ), po którym natychmiast pojawi się nazwa typu tworzonej klasy lub struktury. Zero lub więcej spacji może być zgodne z nazwą typu, a zero lub więcej atrybutów może być również zadeklarowane w elemencie obiektu, z jedną lub kilkoma spacjami oddzielającymi każdą parę atrybutów name="value". Na koniec jedna z następujących elementów musi być spełniony:  
  
- Element i znacznik muszą być zamknięte ukośnikiem (/), po którym następuje bezpośrednio nawias kątowy (>).  
  
- Znacznik otwierający musi być uzupełniony nawiasem pod kątem prostym (>). Inne elementy obiektu, elementy właściwości lub tekst wewnętrzny mogą podążać za znacznikiem otwierającym. Dokładnie, jaka zawartość może być zawarta w tym miejscu jest zazwyczaj ograniczona przez model obiektu elementu. Równoważny znacznik zamknięcia dla elementu obiektu musi również istnieć w prawidłowym zagnieżdżaniu i równowadze z innymi parami znaczników otwierania i zamykania.  
  
 XAML zaimplementowany przez .NET ma zestaw reguł, które mapują elementy obiektów na typy, atrybuty we właściwości lub zdarzenia oraz przestrzenie nazw XAML do obszarów nazw CLR plus zestaw. Dla WPF I .NET, elementy obiektu XAML mapują do typów .NET, zgodnie z definicją w zestawach, do których istnieje odwołanie, a atrybuty są mapowane do elementów członkowskich tych typów. Podczas odwoływania się do typu CLR w XAML, masz również dostęp do odziedziczonych elementów członkowskich tego typu.  
  
 Na przykład poniższy przykład jest składnią elementu obiektu, która <xref:System.Windows.Controls.Button> tworzenia wystąpienia nowego <xref:System.Windows.FrameworkElement.Name%2A> wystąpienia klasy, a także określa atrybut i wartość dla tego atrybutu:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Poniższy przykład jest składnią elementu obiektu, która zawiera również składnię właściwości zawartości XAML. Tekst wewnętrzny zawarty w nim będzie <xref:System.Windows.Controls.TextBox> używany do ustawiania <xref:System.Windows.Controls.TextBox.Text%2A>właściwości zawartości XAML, .  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modele zawartości  
 Klasa może obsługiwać użycie jako element obiektu XAML pod względem składni, ale ten element będzie działać poprawnie tylko w aplikacji lub na stronie, gdy jest umieszczony w oczekiwanej pozycji ogólnego modelu zawartości lub drzewa elementów. Na przykład <xref:System.Windows.Controls.MenuItem> a zazwyczaj powinien być umieszczany <xref:System.Windows.Controls.Primitives.MenuBase> tylko jako dziecko <xref:System.Windows.Controls.Menu>klasy pochodnej, takiej jak . Modele zawartości dla określonych elementów są dokumentowane jako część uwag [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na stronach klas dla formantów i innych klas, które mogą być używane jako elementy XAML.  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>Właściwości elementów obiektu  
 Właściwości w XAML są ustawiane przez różne możliwe składni. Składnia, która może być używana dla określonej właściwości będzie się różnić w zależności od podstawowych cech systemu typu właściwości, które są ustawiane.  
  
 Ustawiając wartości właściwości, można dodać operacje lub właściwości do obiektów, które istnieją na wykresie obiektu czasu wykonywania. Początkowy stan utworzonego obiektu z elementu obiektu jest oparty na zachowaniu konstruktora bez parametrów. Zazwyczaj aplikacja będzie używać czegoś innego niż całkowicie domyślne wystąpienie danego obiektu.  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>Składnia atrybutów (właściwości)  
 Składnia atrybutów to składnia znaczników XAML, która ustawia wartość właściwości, deklarując atrybut na istniejącym elemencie obiektu. Nazwa atrybutu musi być zgodna z nazwą elementu członkowskiego CLR właściwości klasy, która wspiera odpowiedni element obiektu. Po nazwie atrybutu następuje operator przypisania (=). Wartość atrybutu musi być ciągiem ujętym w cudzysłowach.  
  
> [!NOTE]
> Cudzysłowów przemiennych można użyć do umieszczenia znaku cudzysłowu dosłownego w atrybucie. Na przykład można użyć pojedynczych cudzysłowów jako środka do deklarowania ciągu, który zawiera znak cudzysłowu w nim. Niezależnie od tego, czy używasz cudzysłowów jedno- czy podwójnych, należy użyć pasującej pary do otwierania i zamykania ciągu wartości atrybutu. Istnieją również sekwencje ucieczki lub inne techniki dostępne do pracy wokół ograniczeń znaków nałożonych przez dowolną składnię XAML. Zobacz [Jednostki znaków XML i XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Aby można było ustawić za pomocą składni atrybutów, właściwość musi być publiczna i musi być zapisywalna. Wartość właściwości w systemie typu kopii zapasowej musi być typem wartości lub musi być typem odwołania, który może być wystąpienia lub odwołuje się przez procesor XAML podczas uzyskiwania dostępu do odpowiedniego typu kopii zapasowej.  
  
 W przypadku zdarzeń WPF XAML zdarzenie, do którego odwołuje się nazwa atrybutu, musi być publiczne i mieć pełnomocnika publicznego.  
  
 Właściwość lub zdarzenie musi być członkiem klasy lub struktury, który jest tworzone przez element zawierający obiekt.  
  
### <a name="processing-of-attribute-values"></a>Przetwarzanie wartości atrybutów  
 Wartość ciągu zawarta w cudzysłowie otwierającym i zamykającym jest przetwarzana przez procesor XAML. W przypadku właściwości domyślne zachowanie przetwarzania jest określane przez typ podstawowej właściwości CLR.  
  
 Wartość atrybutu jest wypełniana przez jedną z następujących wartości, przy użyciu tej kolejności przetwarzania:  
  
1. Jeśli procesor XAML napotka nawias klamrowy lub element obiektu, który wywodzi się z <xref:System.Windows.Markup.MarkupExtension>, wówczas odwołanie rozszerzenie znaczników jest oceniane najpierw, a nie przetwarzanie wartości jako ciąg, a obiekt zwrócony przez rozszerzenie znaczników jest używany jako wartość. W wielu przypadkach obiekt zwracany przez rozszerzenie znaczników będzie odwołaniem do istniejącego obiektu lub wyrażeniem, które odraża ocenę do czasu wykonywania i nie jest nowo utworzonym obiektem.  
  
2. Jeśli właściwość jest zadeklarowana z przypisanym <xref:System.ComponentModel.TypeConverter>lub typ wartości <xref:System.ComponentModel.TypeConverter>tej właściwości jest zadeklarowany z przypisanym, wartość ciągu atrybutu jest przesyłana do konwertera typu jako dane wejściowe konwersji, a konwerter zwróci nowe wystąpienie obiektu.  
  
3. Jeśli nie <xref:System.ComponentModel.TypeConverter>ma, podejmowana jest bezpośrednia konwersja do typu właściwości. Ten końcowy poziom jest bezpośrednią konwersją na wartość natywną analizatora między typami pierwotnymi języka XAML lub sprawdzaniem nazw nazwanych stałych w wyliczeniu (analizator analizujący następnie uzyskuje dostęp do pasujących wartości).  
  
#### <a name="enumeration-attribute-values"></a>Wartości atrybutów wyliczenia  
 Wyliczenia w XAML są przetwarzane wewnętrznie przez analizatory XAML, a elementy członkowskie wyliczenia powinny być określone przez określenie nazwy ciągu jednej z nazwanych stałych wyliczenia.  
  
 Dla wartości wyliczenia nonflag zachowanie natywne jest przetwarzanie ciągu wartości atrybutu i rozwiązać go do jednej z wartości wyliczenia. Nie należy określać wyliczenia w formacie *Wyliczenie*. *Wartość*, tak jak w kodzie. Zamiast tego należy określić tylko *Wartość*, a *wyliczenie* jest wywnioskowane przez typ właściwości, którą ustawiasz. Jeśli określisz atrybut w *wyliczenia*. *Formularz wartości,* nie zostanie poprawnie rozpoznany.  
  
 Dla wyliczenia flagwise zachowanie jest <xref:System.Enum.Parse%2A?displayProperty=nameWithType> oparte na metodzie. Można określić wiele wartości dla wyliczenia flagowego, oddzielając każdą wartość przecinkiem. Jednak nie można połączyć wartości wyliczenia, które nie są flagwise. Na przykład nie można użyć składni przecinka, <xref:System.Windows.Trigger> aby spróbować utworzyć, który działa na wielu warunkach wyliczenia nonflag:  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Flagowe wyliczenia, które obsługują atrybuty, które są ustawione w XAML są rzadkie w WPF. Jednak jednym z takich wyliczania jest <xref:System.Windows.Media.StyleSimulations>. Można na przykład użyć składni atrybutu rozdzielane przecinkami flagwise, aby zmodyfikować przykład <xref:System.Windows.Documents.Glyphs> podany w Remarks for the Class; `StyleSimulations = "BoldSimulation"` może `StyleSimulations = "BoldSimulation,ItalicSimulation"`stać się . <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>jest inną właściwością, w której można określić więcej niż jedną wartość wyliczenia. Jednak ta właściwość dzieje się specjalny <xref:System.Windows.Input.ModifierKeys> przypadek, ponieważ wyliczenie obsługuje własny konwerter typu. Konwerter typów modyfikatorów używa znaku plus (+) jako ogranicznika, a nie przecinka (,). Ta konwersja obsługuje bardziej tradycyjną składnię reprezentującą kombinacje klawiszy w programowaniu systemu Microsoft Windows, takie jak "Ctrl+Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Odwołania do właściwości i nazwy elementu członkowskiego zdarzenia  
 Podczas określania atrybutu, można odwołać się do dowolnej właściwości lub zdarzenia, które istnieje jako element członkowski typu CLR, który wystąpił dla elementu obiektu zawierającego.  
  
 Można też odwołać się do dołączonej właściwości lub dołączonego zdarzenia, niezależnie od elementu zawierającego obiekt. (Dołączone właściwości są omówione w nadchodzącej sekcji.  
  
 Można również nazwać dowolne zdarzenie z dowolnego obiektu, który jest dostępny za pośrednictwem domyślnego obszaru nazw przy użyciu *typeName*. *zdarzenie* częściowo kwalifikowana nazwa; ta składnia obsługuje dołączanie programów obsługi dla kierowanych zdarzeń, gdzie program obsługi jest przeznaczony do obsługi routingu zdarzeń z elementów podrzędnych, ale element nadrzędny nie ma również tego zdarzenia w tabeli elementów członkowskich. Ta składnia przypomina składnię dołączonego zdarzenia, ale zdarzenie w tym miejscu nie jest zdarzeniem dołączonym do rzeczywistości. Zamiast tego odwołujesz się do zdarzenia o nazwie kwalifikowanej. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń trasowych](routed-events-overview.md).  
  
 W niektórych scenariuszach nazwy właściwości są czasami dostarczane jako wartość atrybutu, a nie nazwę atrybutu. Ta nazwa właściwości może również zawierać kwalifikatory, takie jak właściwość określona w formularzu *ownerType*. *dependencyPropertyName*. Ten scenariusz jest typowy podczas pisania stylów lub szablonów w języku XAML. Reguły przetwarzania nazw właściwości podane jako wartość atrybutu są różne i są regulowane przez typ właściwości są ustawiane lub przez zachowania określonych podsystemów WPF. Aby uzyskać szczegółowe informacje, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
 Innym użyciem dla nazw właściwości jest, gdy wartość atrybutu opisuje relację właściwości-właściwości. Ta funkcja jest używana do wiązania danych i elementów <xref:System.Windows.PropertyPath> docelowych scenorysu i jest włączona przez klasę i jej konwerter typu. Aby uzyskać pełniejszy opis semantyki odnośnika, zobacz [Składnia XAML](propertypath-xaml-syntax.md)programu PropertyPath .  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>Składnia elementu właściwości  
 *Składnia elementu właściwości* jest składnią, która różni się nieco od podstawowych reguł składni XML dla elementów. W języku XML wartość atrybutu jest ciągiem de facto, a jedyną możliwą odmianą jest format kodowania ciągów. W języku XAML można przypisać inne elementy obiektu jako wartość właściwości. Ta funkcja jest włączona przez składnię elementu właściwości. Zamiast właściwości jest określony jako atrybut w tagu elementu, właściwość jest określona przy użyciu tagu elementu otwarcia w *elementTypeName*. *formę propertyName,* wartość właściwości jest określona w obrębie, a następnie element właściwości jest zamknięty.  
  
 W szczególności składnia zaczyna się od lewego nawiasu kątowego (\<), a następnie natychmiast nazwa typu klasy lub struktury, w której znajduje się składnia elementu właściwości. Po tym następuje natychmiast pojedyncza kropka (.), a następnie nazwa właściwości, a następnie nawias kątowy (>). Podobnie jak w odniesieniu do składni atrybutów, ta właściwość musi istnieć w zadeklarowanych publicznych elementów członkowskich określonego typu. Wartość, która ma być przypisana do właściwości znajduje się w elemencie właściwości. Zazwyczaj wartość jest podana jako jeden lub więcej elementów obiektu, ponieważ określenie obiektów jako wartości jest scenariusz, który składnia elementu właściwości jest przeznaczony do adresowania. Na koniec równoważny tag zamykający określający ten sam *elementTypeName*. *propertyName* połączenie musi być pod warunkiem, w odpowiednim zagnieżdżania i równowagi z innymi znacznikami elementów.  
  
 Na przykład poniżej znajduje się składnia <xref:System.Windows.FrameworkElement.ContextMenu%2A> elementu <xref:System.Windows.Controls.Button>właściwości właściwości .  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Wartość w elemencie właściwości może być również podana jako tekst wewnętrzny, w przypadkach, <xref:System.String>gdy określony typ właściwości jest typem wartości pierwotnej, takim jak , lub wyliczenie, w którym określono nazwę. Te dwa użycia są nieco rzadkie, ponieważ każdy z tych przypadków można również użyć prostszą składni atrybutu. Jednym ze scenariuszy wypełniania elementu właściwości ciągiem jest dla właściwości, które nie są właściwością zawartości XAML, ale nadal są używane do reprezentacji tekstu interfejsu użytkownika, a określone elementy odstępu, takie jak kanały wiersza, muszą być wyświetlane w tym tekście interfejsu użytkownika. Składnia atrybutów nie może zachować podawania wierszy, ale składnia elementu właściwości może, o ile aktywna jest znacząca ochrona odstępu (aby uzyskać szczegółowe informacje, zobacz [Przetwarzanie odstępów w języku XAML](../../../desktop-wpf/xaml-services/white-space-processing.md)). Innym scenariuszem jest tak, że [x:Uid dyrektywy](../../../desktop-wpf/xaml-services/xuid-directive.md) mogą być stosowane do elementu właściwości, a tym samym oznaczyć wartość w ramach jako wartość, która powinna być zlokalizowana w danych wyjściowych WPF BAML lub przez inne techniki.  
  
 Element właściwości nie jest reprezentowany w drzewie logicznym WPF. Element właściwości jest tylko określoną składnią ustawiania właściwości i nie jest elementem, który ma wystąpienie lub obiekt, który go tworzy. (Aby uzyskać szczegółowe informacje na temat koncepcji drzewa logicznego, zobacz [Drzewa w WPF](trees-in-wpf.md).)  
  
 Dla właściwości, w których obsługiwane są zarówno składnia atrybutu, jak i elementu właściwości, dwie składnię zazwyczaj mają ten sam wynik, chociaż subtelności, takie jak obsługa odstępu, mogą się nieznacznie różnić w zależności od składni.  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>Składnia kolekcji  
 Specyfikacja XAML wymaga implementacji procesora XAML do identyfikowania właściwości, w których typ wartości jest kolekcją. Implementacja procesora XAML w programie .NET jest oparta na kodzie zarządzanym i programie CLR i identyfikuje typy kolekcji za pośrednictwem jednego z następujących:  
  
- Typ implementuje <xref:System.Collections.IList>.  
  
- Typ implementuje <xref:System.Collections.IDictionary>.  
  
- Typ pochodzi <xref:System.Array> od (aby uzyskać więcej informacji na temat tablic w XAML, zobacz [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
 Jeśli typ właściwości jest kolekcją, typ kolekcji wywnioskowane nie musi być określony w znacznikach jako element obiektu. Zamiast tego elementy, które mają stać się elementami w kolekcji są określone jako jeden lub więcej elementów podrzędnych elementu właściwości. Każdy taki element jest oceniany do obiektu podczas ładowania `Add` i dodaje do kolekcji, wywołując metodę dorozumianej kolekcji. Na przykład <xref:System.Windows.Style.Triggers%2A> właściwość <xref:System.Windows.Style> przyjmuje typ <xref:System.Windows.TriggerCollection>kolekcji specjalistyczne , który implementuje <xref:System.Collections.IList>. Nie jest konieczne tworzenie wystąpienia <xref:System.Windows.TriggerCollection> elementu obiektu w znacznikach. Zamiast tego należy określić <xref:System.Windows.Trigger> jeden lub `Style.Triggers` więcej elementów <xref:System.Windows.Trigger> jako elementy w elemencie właściwości, gdzie (lub klasy <xref:System.Windows.TriggerCollection>pochodnej) jest typem oczekiwanym jako typ elementu dla silnie wpisanych i niejawnych .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Właściwość może być zarówno typ kolekcji i właściwości zawartości XAML dla tego typu i typy pochodne, co zostało omówione w następnej sekcji tego tematu.  
  
 Element niejawnej kolekcji tworzy element członkowski w reprezentacji drzewa logicznego, mimo że nie pojawia się w znacznikach jako element. Zazwyczaj konstruktor typu nadrzędnego wykonuje wystąpienie dla kolekcji, która jest jedną z jego właściwości, a początkowo pusta kolekcja staje się częścią drzewa obiektów.  
  
> [!NOTE]
> Ogólne interfejsy listy i<xref:System.Collections.Generic.IList%601> słownika ( i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane do wykrywania kolekcji. Jednak można użyć <xref:System.Collections.Generic.List%601> klasy jako klasy podstawowej, <xref:System.Collections.IList> ponieważ implementuje <xref:System.Collections.Generic.Dictionary%602> bezpośrednio lub jako klasy <xref:System.Collections.IDictionary> podstawowej, ponieważ implementuje bezpośrednio.  
  
 Na stronach .NET Reference dla typów kolekcji ta składnia z zamierzonym pominięciem elementu obiektu dla kolekcji jest od czasu do czasu zanotowywalna w sekcjach składni XAML jako składnia niejawnej kolekcji.  
  
 Z wyjątkiem elementu głównego, każdy element obiektu w pliku XAML, który jest zagnieżdżony jako element podrzędny innego elementu jest naprawdę elementem, który jest jednym lub obu następujących przypadkach: element członkowski właściwości kolekcji niejawnej jego elementu nadrzędnego lub element, który określa wartość właściwości zawartości XAML dla elementu nadrzędnego (właściwości zawartości XAML zostaną omówione w nadchodzącej sekcji). Innymi słowy relacja elementów nadrzędnych i elementów podrzędnych na stronie znaczników jest naprawdę pojedynczy obiekt w katalogu głównym, a każdy element obiektu pod katalogiem głównym jest albo pojedyncze wystąpienie, które zapewnia wartość właściwości elementu nadrzędnego lub jeden z elementów w kolekcji, który jest również wartością właściwości typu kolekcji nadrzędnego. Ta koncepcja pojedynczego katalogu głównego jest wspólna dla xml i jest często wzmocniona zachowaniem interfejsów API, które ładują kod XAML, taki jak <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Poniższy przykład jest składnią z elementem<xref:System.Windows.Media.GradientStopCollection>obiektu dla kolekcji ( ) określonym jawnie.  
  
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
  
 Należy zauważyć, że nie zawsze jest możliwe jawnie zadeklarować kolekcji. Na przykład próba jawnego zadeklarowania <xref:System.Windows.TriggerCollection> w <xref:System.Windows.Style.Triggers%2A> wcześniej pokazanym przykładzie zakończy się niepowodzeniem. Jawnie deklarując kolekcji wymaga, że klasa kolekcji musi <xref:System.Windows.TriggerCollection> obsługiwać konstruktora bez parametrów i nie ma konstruktora bez parametrów.  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>Właściwości zawartości XAML  
 Składnia zawartości XAML jest składnią, która jest włączona <xref:System.Windows.Markup.ContentPropertyAttribute> tylko w klasach, które określają jako część ich deklaracji klasy. Odwołuje <xref:System.Windows.Markup.ContentPropertyAttribute> się do nazwy właściwości, która jest właściwością zawartości dla tego typu elementu (w tym klas pochodnych). Podczas przetwarzania przez procesor XAML wszystkie elementy podrzędne lub tekst wewnętrzny, które znajdują się między tagami otwierania i zamykania elementu obiektu, zostaną przypisane jako wartość właściwości zawartości XAML dla tego obiektu. Możesz określić jawne elementy właściwości właściwości dla właściwości zawartości, ale to użycie nie jest ogólnie wyświetlane w sekcjach składni XAML w odwołaniu .NET. Technika jawna/szczegółowa ma okazjonalną wartość dla jasności znaczników lub jako element stylu znaczników, ale zazwyczaj intencją właściwości zawartości jest usprawnienie znaczników, tak aby elementy, które są intuicyjnie powiązane jako nadrzędny element podrzędny, mogą być zagnieżdżone bezpośrednio. Tagi elementów właściwości dla innych właściwości elementu nie są przypisywane jako "zawartość" na ścisłej definicji języka XAML; są one przetwarzane wcześniej w kolejności przetwarzania analizatora XAML i nie są uważane za "zawartość".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Wartości właściwości zawartości XAML muszą być ciągłe  
 Wartość właściwości zawartości XAML musi być podana całkowicie przed lub całkowicie po innych elementów właściwości w tym elemencie obiektu. Jest to prawdą, czy wartość właściwości zawartości XAML jest określona jako ciąg lub jako jeden lub więcej obiektów. Na przykład następujące znaczniki nie analizuje:  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Jest to niezgodne z prawem, ponieważ jeśli ta składnia zostały wyraźnie dokonane przy użyciu składni elementu właściwości dla właściwości zawartości, a następnie właściwość zawartości zostanie ustawiona dwa razy:  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobnie nielegalnym przykładem jest, jeśli właściwość zawartości jest kolekcją, a elementy podrzędne są przeplatane elementami właściwości:  
  
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
## <a name="content-properties-and-collection-syntax-combined"></a>Właściwości zawartości i składnia kolekcji połączone  
 Aby zaakceptować więcej niż jeden element obiektu jako zawartość, typ właściwości content musi być szczególnie typem kolekcji. Podobnie jak składnia elementu właściwości dla typów kolekcji, procesor XAML musi identyfikować typy, które są typami kolekcji. Jeśli element ma właściwość zawartości XAML i typ właściwości zawartości XAML jest kolekcją, typ dorozumianej kolekcji nie musi być określony w znacznikach jako element obiektu, a właściwość zawartości XAML nie musi być określona jako element właściwości. W związku z tym model zawartości widoczne w znacznikach może teraz mieć więcej niż jeden element podrzędny przypisany jako zawartość. Poniżej znajduje się składnia <xref:System.Windows.Controls.Panel> zawartości dla klasy pochodnej. Wszystkie <xref:System.Windows.Controls.Panel> klasy pochodne ustanawiają właściwość <xref:System.Windows.Controls.Panel.Children%2A>zawartości XAML <xref:System.Windows.Controls.UIElementCollection>jako , która wymaga wartości typu .  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Należy zauważyć, że ani <xref:System.Windows.Controls.Panel.Children%2A> element właściwości <xref:System.Windows.Controls.UIElementCollection> dla lub element dla jest wymagane w znaczników. Jest to funkcja projektu XAML, dzięki czemu rekursywnie zawarte elementy, które definiują [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są bardziej intuicyjnie reprezentowane jako drzewo zagnieżdżonych elementów z bezpośrednimi relacjami elementu nadrzędnego i podrzędnego, bez interwencji tagów elementów właściwości lub obiektów kolekcji. W rzeczywistości <xref:System.Windows.Controls.UIElementCollection> nie można określić jawnie w znacznikach jako element obiektu, zgodnie z projektem. Ponieważ jego tylko zamierzone zastosowanie <xref:System.Windows.Controls.UIElementCollection> jest jako niejawna kolekcja, nie udostępnia publicznych bez parametrów konstruktora i w związku z tym nie można utworzyć wystąpienia jako element obiektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Mieszanie elementów właściwości i elementów obiektów w obiekcie z właściwością content  
 Specyfikacja XAML deklaruje, że procesor XAML może wymusić, że elementy obiektu, które są używane do wypełnienia właściwości zawartości XAML w elemencie obiektu musi być ciągły i nie mogą być mieszane. To ograniczenie dotyczące mieszania elementów właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i zawartości jest wymuszane przez procesory XAML.  
  
 Element obiektu podrzędnego może mieć jako pierwszy natychmiastowy znacznik w elemencie obiektu. Następnie można wprowadzić elementy właściwości. Lub można określić jeden lub więcej elementów właściwości, a następnie zawartość, a następnie więcej elementów właściwości. Ale gdy element właściwości następuje zawartość, nie można wprowadzić żadnych dalszych zawartości, można dodać tylko elementy właściwości.  
  
 To wymaganie kolejności zawartości / elementu właściwości nie ma zastosowania do tekstu wewnętrznego używanego jako zawartość. Jednak nadal jest to dobry styl znaczników, aby zachować tekst wewnętrzny ciągły, ponieważ znaczne białe znaki będą trudne do wykrycia wizualnie w znacznikach, jeśli elementy właściwości są przeplatane tekstem wewnętrznym.  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>Przestrzeń nazw XAML  
 Żaden z poprzednich przykładów składni nie określił obszaru nazw XAML innego niż domyślny obszar nazw XAML. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typowych aplikacjach domyślna przestrzeń nazw XAML jest określona jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obszar nazw. Można określić obszary nazw XAML inne niż domyślny obszar nazw XAML i nadal używać podobnej składni. Ale wtedy w dowolnym miejscu, gdzie klasa ma nazwę, która nie jest dostępna w domyślnym obszarze nazw XAML, nazwa tej klasy musi być poprzedzona prefiksem obszaru nazw XAML mapowanym do odpowiedniego obszaru nazw CLR. Na przykład `<custom:Example/>` jest składnia elementu obiektu do wystąpienia `Example` wystąpienia klasy, gdzie obszar nazw CLR zawierający tę klasę (i ewentualnie informacje o zestawie `custom` zewnętrznym, który zawiera typy kopii) został wcześniej mapowane do prefiksu.  
  
 Aby uzyskać więcej informacji na temat obszarów nazw XAML, zobacz [XAML Obszary nazw i Mapowanie obszaru nazw dla WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>Rozszerzenia struktury znaczników  
 XAML definiuje jednostkę programowania rozszerzenia znaczników, która umożliwia ucieczkę od normalnego procesora XAML obsługi wartości atrybutów ciągu lub elementów obiektu i odracza przetwarzania do klasy zapasowej. Znak identyfikujący rozszerzenie znaczników do procesora XAML podczas korzystania ze składni atrybutów jest otwierającym nawiasem klamrowym ({), po którym następuje dowolny znak inny niż zamykający nawias klamrowy (}). Pierwszy ciąg po otwierającym nawiasie klamrowy musi odwoływać się do klasy, która zapewnia zachowanie określonego rozszerzenia, gdzie odwołanie może pominąć podciąg "Rozszerzenie", jeśli ten podciąg jest częścią prawdziwej nazwy klasy. Następnie może pojawić się pojedyncza spacja, a następnie każdy kolejny znak jest używany jako dane wejściowe przez implementację rozszerzenia, aż do napotkania zamykającego nawiasu klamrowego.  
  
 Implementacja .NET XAML <xref:System.Windows.Markup.MarkupExtension> używa klasy abstrakcyjnej jako podstawy dla wszystkich rozszerzeń znaczników obsługiwanych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inne struktury lub technologie. Rozszerzenia znaczników, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] które w szczególności implementuje często mają na celu zapewnienie środków do odwoływania się do innych istniejących obiektów lub do odroczonego odwołania do obiektów, które będą oceniane w czasie wykonywania. Na przykład proste powiązanie danych WPF jest `{Binding}` realizowane przez określenie rozszerzenia znaczników zamiast wartości, która zwykle przyjmuje określoną właściwość. Wiele rozszerzeń znaczników WPF włączyć składni atrybutu właściwości, gdzie składnia atrybutu nie byłoby w przeciwnym razie możliwe. Na przykład <xref:System.Windows.Style> obiekt jest stosunkowo złożonym typem, który zawiera zagnieżdżoną serię obiektów i właściwości. Style w WPF są zazwyczaj definiowane <xref:System.Windows.ResourceDictionary>jako zasób w , a następnie odwołuje się za pośrednictwem jednego z dwóch rozszerzeń znaczników WPF, które żądają zasobu. Rozszerzenie znaczników odracza ocenę wartości właściwości do wyszukiwania zasobów i umożliwia <xref:System.Windows.FrameworkElement.Style%2A> podanie wartości <xref:System.Windows.Style>właściwości, przybranie typu, w składni atrybutu, jak w poniższym przykładzie:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 W `StaticResource` tym miejscu <xref:System.Windows.StaticResourceExtension> identyfikuje klasę zapewniającą implementację rozszerzenia znaczników. Następny ciąg `MyStyle` jest używany jako dane wejściowe dla konstruktora nie-domyślnego, <xref:System.Windows.StaticResourceExtension> gdzie <xref:System.Windows.ResourceKey>parametr zaczerpnięty z ciągu rozszerzenia deklaruje żądany . `MyStyle`oczekuje się, że będzie to <xref:System.Windows.Style> wartość [x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) zdefiniowanej jako zasób. [Użycie rozszerzenia znaczników statycznych](staticresource-markup-extension.md) wymaga, aby zasób <xref:System.Windows.Style> był używany do dostarczania wartości właściwości za pośrednictwem statycznej logiki wyszukiwania zasobów w czasie ładowania.  
  
 Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md). Aby uzyskać odwołanie do rozszerzeń znaczników i innych funkcji programowania XAML włączonych w ogólnej implementacji XAML .NET, zobacz [obszar nazw XAML (x:) Funkcje językowe](../../../desktop-wpf/xaml-services/namespace-language-features.md). W przypadku rozszerzeń znaczników specyficznych dla WPF zobacz [Rozszerzenia WPF XAML](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>Dołączone właściwości  
 Dołączone właściwości są koncepcją programowania wprowadzoną w języku XAML, zgodnie z której właściwości mogą być własnością i definiowane przez określony typ, ale ustawione jako atrybuty lub elementy właściwości na dowolnym elemencie. Podstawowy scenariusz, dla którego są przeznaczone dołączone właściwości, jest włączenie elementów podrzędnych w strukturze znaczników do raportowania informacji do elementu nadrzędnego bez konieczności szeroko udostępnionego modelu obiektu we wszystkich elementach. Z drugiej strony dołączone właściwości mogą być używane przez elementy nadrzędne do raportowania informacji do elementów podrzędnych. Aby uzyskać więcej informacji na temat celu dołączonych właściwości i sposobu tworzenia własnych dołączonych właściwości, zobacz [Omówienie załączonych właściwości](attached-properties-overview.md).  
  
 Dołączone właściwości używają składni, która powierzchownie przypomina składnię elementu właściwości, w tym można również określić *typeName*. *nazwa właściwości.* Istnieją dwie ważne różnice:  
  
- Można użyć *typeName*. *nazwami łączenia,* nawet podczas ustawiania dołączonej właściwości za pomocą składni atrybutów. Dołączone właściwości są jedynym przypadkiem, w którym kwalifikująca nazwę właściwości jest wymaganiem w składni atrybutu.  
  
- Można również użyć składni elementu właściwości dla dołączonych właściwości. Jednak dla typowej składni elementu *właściwości, typeName* określić jest element obiektu, który zawiera element właściwości. Jeśli odnosisz się do dołączonej właściwości, *typeName* jest klasą definiującą dołączoną właściwość, a nie element zawierający obiekt.  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>Dołączone zdarzenia  
 Dołączone zdarzenia są inną koncepcją programowania wprowadzoną w języku XAML, gdzie zdarzenia mogą być definiowane przez określony typ, ale programy obsługi mogą być dołączone do dowolnego elementu obiektu. W implementacji WOF często typ, który definiuje dołączone zdarzenie jest typu statycznego, który definiuje usługę, a czasami te dołączone zdarzenia są udostępniane przez routowane alias zdarzeń w typach, które uwidaczniają usługi. Programy obsługi dołączonych zdarzeń są określane za pomocą składni atrybutów. Podobnie jak w przypadku dołączonych zdarzeń, składnia atrybutu jest rozwijana dla dołączonych zdarzeń, aby zezwolić na *typeName*. *użycie eventName,* gdzie *typeName* jest `Add` `Remove` klasą, która zapewnia i akcesory obsługi zdarzeń dla dołączonej infrastruktury zdarzeń, a *eventName* jest nazwą zdarzenia.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomia elementu głównego XAML  
 W poniższej tabeli przedstawiono typowy element główny XAML w podziale, przedstawiający określone atrybuty elementu głównego:  
  
|||  
|-|-|  
|`<Page`|Otwieranie elementu obiektu elementu głównego|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Domyślna[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]( ) przestrzeń nazw XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Przestrzeń nazw XAML języka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklaracja klasy częściowej, która łączy znaczniki z dowolnym kodem zdefiniowanym dla klasy częściowej|  
|`>`|Koniec elementu obiektu dla katalogu głównego. Obiekt nie jest jeszcze zamknięty, ponieważ element zawiera elementy podrzędne|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>Opcjonalne i nierekomercyjne użycie XAML  
 W poniższych sekcjach opisano użycia XAML, które są technicznie obsługiwane przez procesory XAML, ale które generują szczegółowość lub inne problemy estetyczne, które zakłócają pliki XAML, które są czytelne dla człowieka podczas tworzenia aplikacji zawierających źródła XAML.  
  
### <a name="optional-property-element-usages"></a>Opcjonalne użycie elementu właściwości  
 Opcjonalne użycie elementu właściwości obejmują jawnie zapisywanie właściwości zawartości elementu, które procesor XAML uważa za niejawne. Na przykład podczas deklarowania zawartości <xref:System.Windows.Controls.Menu>, można wybrać jawnie <xref:System.Windows.Controls.ItemsControl.Items%2A> zadeklarować <xref:System.Windows.Controls.Menu> `<Menu.Items>` kolekcję jako tag elementu <xref:System.Windows.Controls.MenuItem> `<Menu.Items>`właściwości i umieścić każdy wewnątrz , zamiast używać niejawnego zachowania procesora XAML, że wszystkie elementy podrzędne a <xref:System.Windows.Controls.Menu> musi być <xref:System.Windows.Controls.MenuItem> i są umieszczane w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji. Czasami opcjonalne użycia mogą pomóc wizualnie wyjaśnić strukturę obiektu, jak reprezentowane w znacznikach. Czasami jawne użycie elementu właściwości można uniknąć znaczników, który jest technicznie funkcjonalny, ale wizualnie mylące, takich jak zagnieżdżone rozszerzenia znaczników w wartości atrybutu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Atrybuty kwalifikowane typu TypeName.memberName  
 *TypName*. Formularz *memberName* dla atrybutu faktycznie działa bardziej uniwersalnie niż tylko przypadek zdarzenia kierowanego. Ale w innych sytuacjach, że forma jest zbędna i należy go unikać, choćby ze względu na styl znaczników i czytelność. W poniższym przykładzie każde z trzech <xref:System.Windows.Controls.Control.Background%2A> odwołań do atrybutu są całkowicie równoważne:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`działa, ponieważ kwalifikowane wyszukiwanie <xref:System.Windows.Controls.Button> dla tej<xref:System.Windows.Controls.Control.Background%2A> właściwości na zakończy <xref:System.Windows.Controls.Button> się pomyślnie (został odziedziczony z Control) i jest klasą elementu obiektu lub klasy podstawowej. `Control.Background`działa, <xref:System.Windows.Controls.Control> ponieważ klasa <xref:System.Windows.Controls.Control.Background%2A> faktycznie <xref:System.Windows.Controls.Control> definiuje <xref:System.Windows.Controls.Button> i jest klasą podstawową.  
  
 Jednak następujący *typName*. przykład formularza *memberName* nie działa i w związku z tym jest pokazany skomentował:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>jest inną klasą <xref:System.Windows.Controls.Control>pochodną , `Label.Background` a <xref:System.Windows.Controls.Label> jeśli został określony w elemencie obiektu, to użycie byłoby działać. Jednak ponieważ <xref:System.Windows.Controls.Label> nie jest klasą <xref:System.Windows.Controls.Button>lub klasą podstawową , określone `Label.Background` zachowanie procesora XAML jest następnie przetwarzać jako dołączona właściwość. `Label.Background`nie jest dostępna właściwości dołączone, a to użycie kończy się niepowodzeniem.  
  
### <a name="basetypenamemembername-property-elements"></a>BaseTypeName.memberName Elementy właściwości  
 W sposób analogiczny do sposobu, w jaki *typeName*. Formularz *memberName* działa dla składni atrybutów, *baseTypeName*. składnia *elementu elementu* właściwości. Na przykład działa następująca składnia:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 W tym miejscu element `Control.Background` właściwości został podany, mimo `Button`że element właściwości został zawarty w .  
  
 Ale tak jak *typeName*. formularz *memberName* dla atrybutów, *baseTypeName*. *Nazwa elementu memberName* jest złym stylem w znacznikach i należy go unikać.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Przestrzeń nazw XAML (x:) Funkcje językowe](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [TypeConverters i XAML](typeconverters-and-xaml.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
