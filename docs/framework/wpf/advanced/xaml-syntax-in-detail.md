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
ms.openlocfilehash: d98141c0ad96ef1bd3958ae8d3166aedde76f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549480"
---
# <a name="xaml-syntax-in-detail"></a>Szczegóły składni XAML
W tym temacie opisano terminy, które służą do opisywania elementy składni języka XAML. Te warunki są często używane w dalszej części tej dokumentacji, zarówno dla dokumentacji WPF w szczególności i dla innych platform, które używają XAML lub podstawowe pojęcia języka XAML, aby włączyć obsługę języka XAML na poziomie System.Xaml. W tym temacie omówiono w podstawowej terminologii wprowadzone w temacie [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>Specyfikacja języka XAML  
 Terminologia składni języka XAML zdefiniowane w tym miejscu jest również zdefiniowana lub przywołać w specyfikacji języka XAML. XAML to język oparte na języku XML i następuje lub rozszerza strukturalnych reguł XML. Niektóre terminologii został udostępniony z lub opiera się na terminologii najczęściej używanych podczas opisywania języka XML lub modelu obiektu dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat specyfikacji języka XAML, Pobierz [ \[MS XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525) z Microsoft Download Center.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML i środowiska CLR  
 XAML to język znaczników. [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], Jako domyślnych według jego nazwy, umożliwia wykonanie środowiska wykonawczego. XAML nie jest samodzielnie jednym z typowych języków, które bezpośrednio jest używane przez środowisko uruchomieniowe CLR. Zamiast tego można traktować XAML jako obsługujące własny system typu. Określonym systemie analizy XAML, który jest używany przez WPF jest oparty na systemie typu CLR i środowiska CLR. Typy XAML są mapowane na typy CLR można utworzyć wystąpienia reprezentację w czasie wykonywania, gdy zostanie przeanalizowany XAML dla WPF. Z tego powodu w pozostałej części dyskusji składni, w tym dokumencie będzie zawierać odwołania do system typów CLR, nawet gdy nie dyskusji składni równoważnym w specyfikacji języka XAML. (Na poziomie specyfikacji języka XAML, typów XAML może być mapowane na inne systemy typu, który nie ma być CLR, ale wymagałyby tworzenia i używania innego analizatora języka XAML).  
  
#### <a name="members-of-types-and-class-inheritance"></a>Elementy członkowskie typów i dziedziczenie klas  
 Właściwości i zdarzeń po ich są wyświetlane jako elementy członkowskie XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typu często są dziedziczone z typów podstawowych. Rozważmy na przykład w tym przykładzie: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> Właściwość nie jest właściwością natychmiast zadeklarowane na <xref:System.Windows.Controls.Button> klasy, gdyby przyjrzeć się definicji klasy, wyniki odbicia lub dokumentacją. Zamiast tego <xref:System.Windows.Controls.Control.Background%2A> jest dziedziczona z podstawowym <xref:System.Windows.Controls.Control> klasy.  
  
 Zachowanie dziedziczenia klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów XAML jest znacząco różni od wymuszane schematu interpretacji znaczników XML. Dziedziczenie klas może być skomplikowane, szczególnie w przypadku, gdy pośredni klasy podstawowe są klasami abstrakcyjnymi lub interfejsy. Jest to powodem, dla którego zbiór elementów XAML i ich atrybuty dopuszczalne jest trudne do reprezentowania dokładnie i całkowicie przy użyciu typów schematów zwykle używane w przypadku [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] programowania, takich jak format DTD lub XSD. Inną przyczyną jest tym rozszerzalności i mapowanie typu funkcji języka XAML, sama wyklucza kompletności wszystkie usunięte reprezentację dopuszczalne typy i składniki.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Składnia elementu obiektu  
 *Obiekt składni elementu* jest składnia znacznika XAML, tworzącym CLR klasy lub struktury przez zadeklarowanie — element XML. Ta składnia jest podobny do składni elementu innych języków znaczników, takich jak HTML. Składnia elementu obiektu, który rozpoczyna się od lewego nawiasu ostrego (\<), a następnie natychmiast nazwę typu klasy lub struktury, w której jest tworzone wystąpienie. Zero lub więcej spacji po nazwie typu i zero lub więcej atrybutów może również być zadeklarowany w elemencie obiektu z co najmniej jedną spację, oddzielając nazwy atrybutu = pary "value". Na koniec jedną z następujących muszą być spełnione:  
  
-   Element i znaczników muszą być zamknięte przez ukośnikiem (/) bezpośrednio po prawego nawiasu ostrego (>).  
  
-   Otwierający tag musi wykonać prawego nawiasu ostrego (>). Inne elementy obiektu, elementy właściwości lub tekst wewnętrzny wykonać otwierający tag. Dokładnie zawartość może być zawartych w tym miejscu zwykle jest ograniczane przez model obiektów elementu. Odpowiednik tagu zamykającego elementu obiektu musi również istnieje odpowiednie zagnieżdżanie i zrównoważenia z innych parami otwierający i zamykający tag.  
  
 XAML zaimplementowanego .NET jest zestaw reguł, które mapują elementy obiektów na typy i atrybuty do właściwości lub zdarzenia i przestrzeń nazw z przestrzeni nazw CLR plus zestawu. WPF i .NET Framework XAML elementów obiektu mapowania na [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] typów zgodnie z definicją w zestawy, do których odwołuje się i atrybuty mapowanie członków z tych typów. Odwołanie do typu CLR w języku XAML, należy mieć dostęp do dziedziczone elementy członkowskie tego typu również.  
  
 Na przykład w poniższym przykładzie jest składni elementu obiektu, który tworzy nowe wystąpienie klasy <xref:System.Windows.Controls.Button> klasy, a także określa <xref:System.Windows.FrameworkElement.Name%2A> atrybut i wartość tego atrybutu:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Poniższy przykład jest składni elementu obiektu, który również uwzględnia składni właściwości zawartości XAML. Tekst wewnętrzny zawartych w będzie użyty do ustawienia <xref:System.Windows.Controls.TextBox> właściwości zawartości XAML, <xref:System.Windows.Controls.TextBox.Text%2A>.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>Modele zawartości  
 Klasa może obsługiwać użycie jako element object XAML w zakresie składni, ale ten element będzie działać tylko prawidłowo w aplikacji lub strony, gdy znajduje się w oczekiwanej pozycji ogólnej zawartości drzewa modelu lub elementu. Na przykład <xref:System.Windows.Controls.MenuItem> powinien zwykle można umieścić wyłącznie jako element podrzędny <xref:System.Windows.Controls.Primitives.MenuBase> pochodnej klasy, takich jak <xref:System.Windows.Controls.Menu>. Zawartości modeli dla określonych elementów są udokumentowane jako część uwagi na stronach klasy dla formantów i innych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, które mogą służyć jako elementy XAML.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Właściwości elementów obiektu  
 Właściwości w języku XAML są ustawiane przez różne możliwe składni. Składni, które mogą służyć do określonej właściwości różnią się na podstawie podstawowej charakterystyk system typu właściwości, które konfigurujesz.  
  
 Przez ustawienie wartości właściwości, należy dodać funkcje lub właściwości do obiektów istniejących w czasie wykonywania wykres obiektu. Początkowy stan utworzony obiekt z elementu obiektu jest oparta na zachowanie konstruktora domyślnego. Zwykle aplikacja będzie korzystać z inną niż całkowicie domyślnego wystąpienia dowolnego danego obiektu.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Składnia atrybutu (właściwości)  
 Składnia atrybutu jest składnia znacznika XAML, która ustawia wartości właściwości przez zadeklarowanie atrybut na istniejący element object. Nazwa atrybutu musi odpowiadać nazwie elementu członkowskiego CLR właściwości klasy, aby utworzyć kopię zapasową elementu odpowiedniego obiektu. Nazwa atrybutu następuje operator przypisania (=). Wartość atrybutu musi być ciągiem ujętym w cudzysłów.  
  
> [!NOTE]
>  Cudzysłowy przemiennych umożliwia umieść literału znaku cudzysłowu w ciągu atrybutu. Na przykład służy apostrofy jako środek do deklarowania ciąg, który zawiera znak podwójnego cudzysłowu w niej. Czy korzystasz z pojedynczym lub podwójnym cudzysłowie, należy użyć parę pasującego do otwierania i zamykania ciągu wartości atrybutu. Brak dostępnych również sekwencji unikowych lub innych technik dotyczące obejścia znak ograniczeń narzuconych przez dowolnego określonej składni języka XAML. Zobacz [jednostki znaków XML i XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 Aby można było ustawić za pomocą składni atrybutu, właściwość muszą być publiczne i musi być zapisywalny. Wartość właściwości w systemie zapasowy typ musi być typem wartości lub musi być typem referencyjnym, który można utworzyć wystąpienia lub odwołuje się procesora XAML podczas uzyskiwania dostępu do odpowiedniego tworzenie kopii typu.  
  
 Dla zdarzeń WPF XAML zdarzeń, który jest określany jako nazwa atrybutu musi być publiczny i posiadać Delegat publiczny.  
  
 Właściwość lub zdarzenie musi być elementem członkowskim klasy lub struktury, który jest uruchomiony przez zawierającego element object.  
  
### <a name="processing-of-attribute-values"></a>Przetwarzanie wartości atrybutów  
 Wartość ciągu zawartych w otwierający i zamykający cudzysłów są przetwarzane przez procesor XAML. W przypadku właściwości domyślnego zachowania przetwarzania zależy od typu podstawowego właściwości CLR.  
  
 Wartość atrybutu jest wypełniana przez jedną z następujących czynności, za pomocą następującej kolejności przetwarzania:  
  
1.  Jeśli procesor XAML napotkał nawias klamrowy lub elementu obiekt pochodzący z <xref:System.Windows.Markup.MarkupExtension>, następnie rozszerzenie znaczników przywoływanego jest szacowana jako pierwsza zamiast przetwarzania wartość jako ciąg i obiekcie zwracanym przez rozszerzenie znaczników jest używany jako wartość. W wielu przypadkach obiekcie zwracanym przez rozszerzenie znaczników będzie odwołanie do obiektu lub wyrażenie, które różni się oceny czasu wykonywania, a nie jest obiektem nowo skonkretyzowanym.  
  
2.  Jeśli właściwość jest zadeklarowana z atrybutami <xref:System.ComponentModel.TypeConverter>, lub jest zadeklarowany jako typ wartości właściwości z atrybutami <xref:System.ComponentModel.TypeConverter>, wartość ciągu atrybutu jest przesyłany do usługi konwertera typu jako dane wejściowe konwersji i zwraca konwerter nowe wystąpienie obiektu.  
  
3.  W przypadku nie <xref:System.ComponentModel.TypeConverter>, próbą bezpośredniego konwersji na typ właściwości. Ten poziom końcowego jest bezpośrednie konwersji na wartość native analizatora składni między typów pierwotnych języka XAML lub sprawdzania nazw stałe nazwane w wyliczeniu (analizator następnie uzyskuje dostęp do dopasowania wartości).  
  
#### <a name="enumeration-attribute-values"></a>Wartości atrybutów — wyliczenie  
 Wyliczeń w języku XAML są bardzo przetwarzane przez analizatory składni języka XAML i elementy członkowskie wyliczenia powinien być określony przez określenie nazwy ciągu jednej stałe nazwane wyliczenia.  
  
 Dla wartości wyliczenia nonflag natywnego zachowanie to ciąg wartości atrybutu przetwarzać i rozwiązać go do jednej z wartości wyliczenia. Nie określaj wyliczenia w formacie *wyliczenie*. *Wartość*, tak jak w kodzie. Zamiast tego można określić tylko *wartość*, i *wyliczenie* jest wywnioskowany typ właściwości ustawieniu. Jeśli określisz atrybutu w *wyliczenie*. *Wartość* formularza, go nie rozpozna poprawnie.  
  
 Dla wyliczenia flagwise zachowanie jest oparta na <xref:System.Enum.Parse%2A?displayProperty=nameWithType> metody. Można określić wiele wartości wyliczenia flagwise, Oddziel poszczególne wartości przecinkami. Nie można jednak łączyć wartości wyliczenia, które nie są flagwise. Na przykład nie można użyć składni przecinkami próbuje utworzyć <xref:System.Windows.Trigger> działający na wiele warunków wyliczenie nonflag:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 Flagwise wyliczenia, które obsługują atrybuty, które są można ustawić w języku XAML są rzadko na platformie WPF. Jednak jest jedno takie wyliczenie <xref:System.Windows.Media.StyleSimulations>. Można na przykład użyć składni atrybutu flagwise rozdzielana przecinkami można zmodyfikować w przykładzie przedstawionym w uwagi dla <xref:System.Windows.Documents.Glyphs> klasy; `StyleSimulations = "BoldSimulation"` może stać się `StyleSimulations = "BoldSimulation,ItalicSimulation"`. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> jest inna właściwość, w którym można określić więcej niż jedną wartość wyliczenia. Jednak ta właściwość się nie dzieje się w szczególnych przypadkach, ponieważ <xref:System.Windows.Input.ModifierKeys> wyliczenie obsługuje własny typ konwertera. Konwerter typu dla Modyfikatory używa znak plus (+) jako ogranicznik zamiast przecinka (,). Ta konwersja obsługuje bardziej tradycyjnej składni do reprezentowania kombinacje klawiszy w programowaniu Windows firmy Microsoft, takich jak "Ctrl + Alt".  
  
### <a name="properties-and-event-member-name-references"></a>Właściwości i zdarzenia odwołania do nazwy elementu członkowskiego  
 Podczas określania atrybutu, możesz odwoływać się żadnych właściwości lub zdarzenia, która istnieje jako element członkowski typu CLR, który można utworzyć wystąpienia zawierający element object.  
  
 Lub może odwoływać się dołączona właściwość lub dołączony zdarzeń, niezależnie od zawierającego element object. (Dołączone właściwości są omówione w następnej sekcji).  
  
 Możesz też nazwać wszystkie zdarzenia z dowolnych obiektów, który jest dostępny za pośrednictwem domyślnej przestrzeni nazw przy użyciu *typeName*. *Zdarzenie* częściowo kwalifikowanej nazwy; tej składni obsługuje dołączanie obsługi kierowane zdarzenia których program obsługi jest przeznaczona do obsługi zdarzeń routingu z elementów podrzędnych, ale element nadrzędny nie również ma zdarzenie w tabeli elementów członkowskich. Ta składnia przypomina składni dołączone zdarzenie, ale zdarzeń, w tym miejscu nie jest spełniony, dołączone zdarzenie. Zamiast tego odwołuje się zdarzenia o kwalifikowanej nazwie. Aby uzyskać więcej informacji, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 W niektórych scenariuszach nazw właściwości czasami są dostarczane jako wartość atrybutu, a nie nazwa atrybutu. Nazwa tej właściwości może również zawierać kwalifikatorów, takie jak właściwości określone w formie *ownerType*. *dependencyPropertyName*. Ten scenariusz jest typowy podczas pisania szablonów lub style w języku XAML. Przetwarzanie reguł dla dostarczonych jako wartość atrybutu nazwy właściwości są różne, a są regulowane przez typ właściwości ustawiany lub zachowania określonego podsystemów WPF. Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Użycie innej nazwy właściwości jest, gdy wartość atrybutu opisuje relację właściwość właściwości. Ta funkcja służy do wiązania danych i obiektów docelowych scenorysu i jest włączana przez <xref:System.Windows.PropertyPath> klasy i jej konwerter typów. Aby uzyskać bardziej szczegółowy opis semantyki wyszukiwania, zobacz [składnia PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Składni elementu właściwości  
 *Składni elementu właściwości* jest składnię, która diverges nieco z podstawowych reguł składni XML dla elementów. W kodzie XML wartość atrybutu jest faktyczne ciąg, z odmiany to tylko możliwe jest, który format kodowania ciąg jest używany. W języku XAML można przypisać inne elementy obiektu jako wartość właściwości. Ta możliwość jest włączona w składni elementu właściwości. Zamiast właściwości określany jako atrybut w tagu elementu, właściwość zostanie określona przy użyciu elementu otwierający tag w *elementTypeName*. *propertyName* formularza, wartość właściwości jest określone w, a następnie zamknięciu elementu właściwości.  
  
 W szczególności składnia rozpoczyna się od lewego nawiasu ostrego (\<), a następnie natychmiast nazwę typu klasy lub struktury, zawarty w składni elementu właściwości. To następuje natychmiast przez pojedynczego znaku kropki (.), następnie według nazwy właściwości, następnie prawego nawiasu ostrego (>). Podobnie jak w przypadku Składnia atrybutu tej właściwości musi istnieć w zadeklarowane publiczne elementy członkowskie określonego typu. Wartość do przypisania do właściwości znajduje się wewnątrz elementu właściwości. Zazwyczaj wartość znajduje się w co najmniej jeden element obiektu, ponieważ określanie obiektów jako wartości jest scenariusz tej składni elementu właściwości jest przeznaczony do adresu. Na koniec tagu zamykającego równoważne, które są takie same określenie *elementTypeName*. *propertyName* musi być wprowadzona kombinacja w odpowiednich zagnieżdżenia i saldo z innych tagów elementu.  
  
 Na przykład poniżej przedstawiono składni elementu właściwości dla <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Wartość w elemencie właściwości można podać tekst wewnętrzny w przypadkach, gdy jest określony typ właściwości jest typem pierwotnym wartości takich jak <xref:System.String>, lub określoną nazwę wyliczenia. Te dwie metody użycia są nieco rzadko, ponieważ każdy z tych przypadkach można użyć również prostsze Składnia atrybutu. Jest jeden scenariusz wypełniania elementu właściwości na ciąg dla właściwości, które nie są właściwości zawartości XAML, ale wciąż są używane do reprezentacji tekście interfejsu użytkownika i określonego odstępy elementów, takich jak znaki wysuwu wiersza są wymagane do pojawiają się w tekście interfejsu użytkownika. Składnia atrybutu nie można zachować znaki wysuwu wiersza, ale składni elementu właściwości można tak długo, jak zachowywania znaczące światła jest aktywne (Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)). Inny scenariusz jest, aby [x: Uid — dyrektywa](../../../../docs/framework/xaml-services/x-uid-directive.md) można zastosować do elementu właściwości i w związku z tym oznaczyć wartości w ramach jako wartość, która powinna być lokalizowany na platformie WPF output BAML lub innych technik.  
  
 Element właściwości nie jest reprezentowany w drzewie logicznym WPF. Element właściwości jest po prostu określonej składni do ustawiania właściwości i nie jest element, który ma dany obiekt wspierającą lub wystąpienia. (Aby uzyskać szczegółowe informacje dotyczące pojęcia drzewa logicznego, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).)  
  
 Dla właściwości, w którym obsługiwane są zarówno atrybut, jak i właściwość składni elementu dwa składni mają zwykle takiego samego wyniku, mimo że precyzyjnie, takich jak obsługa odstępu mogą się nieco różnić między składni.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Składnia kolekcji  
 Specyfikacja języka XAML wymaga implementacji procesora XAML, aby określić właściwości, której typ wartości jest kolekcją. Ogólne implementacji procesora XAML w programie .NET jest oparta na kodu zarządzanego i środowiska CLR i identyfikuje typy kolekcji za pomocą jednego z następujących czynności:  
  
-   Typ implementuje <xref:System.Collections.IList>.  
  
-   Typ implementuje <xref:System.Collections.IDictionary>.  
  
-   Typ pochodzi z <xref:System.Array> (Aby uzyskać więcej informacji dotyczących tablic w języku XAML, zobacz [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
 Jeśli typ właściwości jest kolekcją, typu wywnioskowane kolekcji nie muszą mieścić się w znaczniku jako elementu obiektu. Zamiast tego elementów, które mają stać się elementów w kolekcji są określone jako jeden lub więcej elementów podrzędnych elementu właściwości. Każdy taki element jest oceniane do obiektu podczas ładowania i dodać do kolekcji, wywołując `Add` metody domyślnych kolekcji. Na przykład <xref:System.Windows.Style.Triggers%2A> właściwość <xref:System.Windows.Style> przyjmuje typ kolekcji specjalne <xref:System.Windows.TriggerCollection>, który implementuje <xref:System.Collections.IList>. Nie jest konieczne do utworzenia wystąpienia <xref:System.Windows.TriggerCollection> element object w znaczniku. Zamiast tego należy określić jedną lub więcej <xref:System.Windows.Trigger> elementy jako elementy w `Style.Triggers` elementu właściwości, gdzie <xref:System.Windows.Trigger> (lub klasy pochodnej) jest w typ oczekiwany typ elementu silnie typizowaną i niejawne <xref:System.Windows.TriggerCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Właściwość może być typem kolekcji i właściwości zawartości XAML dla tego typu i pochodnych typów, które opisano w następnej sekcji tego tematu.  
  
 Element kolekcji niejawne tworzy element członkowski w reprezentacji drzewa logicznego nawet, jeśli nie ma w znaczniku jako elementu. Zazwyczaj wykonuje wystąpienia konstruktora w typie elementu nadrzędnego dla kolekcji, które jest jednym z jego właściwości, a początkowo pusta kolekcja staje się częścią drzewa obiektów.  
  
> [!NOTE]
>  Interfejsy ogólne listy i słownika (<xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602>) nie są obsługiwane dla kolekcji wykrywania. Można jednak użyć <xref:System.Collections.Generic.List%601> klasy jako klasę podstawową, ponieważ implementuje on <xref:System.Collections.IList> bezpośrednio, lub <xref:System.Collections.Generic.Dictionary%602> jako klasę podstawową, ponieważ implementuje on <xref:System.Collections.IDictionary> bezpośrednio.  
  
 Na stronach dokumentacja platformy .NET dla typów kolekcji tej składni z pominięciem zamierzonego element object dla kolekcji co pewien czas jest rejestrowany w sekcjach składni języka XAML jako niejawne składni kolekcji.  
  
 Z wyjątkiem elementu głównego, co element object w pliku XAML, który jest zagnieżdżony jako element podrzędny innego elementu jest naprawdę element, który jest co najmniej jednej z następujących przypadków: element członkowski właściwości niejawnej kolekcji jego elementu nadrzędnego , lub element, który określa wartość właściwości zawartości XAML dla elementu nadrzędnego (XAML zawartości właściwości zostanie omówiona w następnej sekcji). Innymi słowy, elementy nadrzędne i podrzędne elementy na stronie znaczników jest naprawdę pojedynczego obiektu w katalogu głównym, a każdy element obiektu poniżej poziomu głównego pojedynczego wystąpienia, która udostępnia wartości właściwości elementu nadrzędnego, albo jeden z elementów w obrębie kolumny Zaznaczenie, który jest również wartości właściwości typu kolekcji nadrzędnej. To pojęcie jednym elementem głównym z XML i jest często wzmocnione zachowania interfejsów API, które obciążenia XAML, takich jak <xref:System.Windows.Markup.XamlReader.Load%2A>.  
  
 Poniższy przykład jest składnia z elementem obiektu dla kolekcji (<xref:System.Windows.Media.GradientStopCollection>) jawnie określona.  
  
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
  
 Należy pamiętać, że nie zawsze jest możliwe jawnie deklarować kolekcji. Na przykład próby zadeklarować <xref:System.Windows.TriggerCollection> jawnie w pokazano wcześniej <xref:System.Windows.Style.Triggers%2A> przykład nie powiedzie się. Jawne zadeklarowanie kolekcji wymaga, aby Klasa kolekcji musi obsługiwać konstruktora domyślnego i <xref:System.Windows.TriggerCollection> nie ma konstruktora domyślnego.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>Właściwości zawartości XAML  
 Składnia zawartości XAML jest składnię, która jest włączona tylko dla klas, które określają <xref:System.Windows.Markup.ContentPropertyAttribute> jako część ich deklaracji klasy. <xref:System.Windows.Markup.ContentPropertyAttribute> Odwołuje się do nazwy właściwości, która jest właściwość zawartości dla tego typu elementu (w tym klasy pochodne). Podczas przetwarzania przez procesor XAML, wszystkie elementy podrzędne lub tekst wewnętrzny, które znajdują się pomiędzy otwierającym, a zamykającym tagiem elementu obiekt zostanie przypisany do wartości właściwości zawartości XAML dla tego obiektu. Możesz określić elementy jawne właściwości dla właściwości content, ale to użycie nie ma zazwyczaj w sekcjach składni języka XAML w odwołaniu .NET. Jawne/verbose technika ma wartość okazjonalne dla jasności znaczników lub jako styl znaczników, ale zwykle celem właściwość content uprościć kod znaczników, tak aby elementy powiązane intuicyjnie jako nadrzędny podrzędny, które mogą być zagnieżdżane bezpośrednio. Właściwość elementu tagi dla innych właściwości w elemencie nie są przypisani jako "zawartość" strict definicji języka XAML; są przetwarzane wcześniej w kolejności przetwarzania analizatora języka XAML, a nie są uznawane za jako "zawartość".  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>Wartości właściwości zawartości XAML musi mieć postać ciągłą  
 Wartość właściwości zawartości XAML należy całkowicie przed lub całkowicie po innych elementów właściwości w elemencie tego obiektu. Jest to możliwe, czy określona jest wartość właściwości zawartości XAML, jak ciąg lub co najmniej jeden obiekt. Na przykład następujący kod nie analizy:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Jest to niedozwolone zasadniczo ponieważ ta składnia jawnego dokonane przy użyciu składni elementu właściwości dla właściwości content, następnie zawartości będzie można ustawić właściwości dwa razy:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Podobnie niedozwolony przykładem jest, jeśli właściwość content jest kolekcją, a elementy podrzędne są oraz elementy właściwości:  
  
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
## <a name="content-properties-and-collection-syntax-combined"></a>Właściwości zawartości i połączeniu składni kolekcji  
 Aby zaakceptować więcej niż element pojedynczy obiekt jako zawartość, typ właściwości zawartości w szczególności należy typ kolekcji. Podobnie jak w składni elementu właściwości dla typów kolekcji, procesor XAML musi określać typy, które są typy kolekcji. Jeśli element ma właściwości zawartości XAML, typ właściwości zawartości XAML jest kolekcją, dorozumianych kolekcji nie muszą być określone w znaczniku jako elementu obiektu i właściwości zawartości XAML nie musi być określone jako el właściwości ement. W związku z tym jawnego modelu zawartości w znaczniku teraz może mieć więcej niż jeden element podrzędny przypisany jako zawartości. Poniżej przedstawiono składnię zawartości <xref:System.Windows.Controls.Panel> klasy. Wszystkie <xref:System.Windows.Controls.Panel> właściwości zawartości XAML, należy ustanowić klas pochodnych <xref:System.Windows.Controls.Panel.Children%2A>, która wymaga wartości typu <xref:System.Windows.Controls.UIElementCollection>.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Należy pamiętać, że żaden element właściwości dla <xref:System.Windows.Controls.Panel.Children%2A> ani elementu <xref:System.Windows.Controls.UIElementCollection> jest wymagany w znaczniku. Jest to funkcja projektu języka XAML, aby rekursywnie zawiera elementy, które definiują [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są bardziej intuicyjne reprezentowana jako drzewo elementów zagnieżdżonych relacje element natychmiastowego nadrzędny podrzędny, bez interwencji tagów elementu właściwości lub Kolekcja obiektów. W rzeczywistości <xref:System.Windows.Controls.UIElementCollection> nie można określić jawnie w znaczniku jako elementu obiektu zgodnie z projektem. Ponieważ jest tylko przeznaczeniem jako niejawne kolekcji <xref:System.Windows.Controls.UIElementCollection> nie ujawniać publicznego konstruktora domyślnego i dlatego nie można utworzyć wystąpienia jako elementu obiektu.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Mieszanie elementy właściwości i obiektu w obiekcie z właściwością zawartości  
 Specyfikacja języka XAML deklaruje, że procesor XAML może wymusić elementy obiektu, które są używane do wypełnienia właściwości zawartości XAML w obrębie elementu obiektu musi być ciągłe i nie można łączyć. To ograniczenie przed mieszanie elementy właściwości i zawartość jest wymuszana przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesorów XAML.  
  
 Element podrzędny obiekt może mieć jako pierwszego znacznika natychmiastowego w elemencie obiektu. Następnie możesz wprowadzić elementów właściwości. Alternatywnie można określić co najmniej jeden element właściwości zawartości, a następnie więcej elementów właściwości. Jednak po elemencie właściwości następuje zawartości, nie wolno wprowadzać żadnych dalszych zawartości, można dodać tylko elementy właściwości.  
  
 Ta zawartość / właściwości elementu kolejności wymóg nie ma zastosowania do tekst wewnętrzny używany jako zawartości. Jednak nadal jest styl znacznika dobrej przechowywać tekst wewnętrzny ciągłej, ponieważ znaczące światła będzie trudne do wykrycia wizualnie w znaczniku, jeśli elementy właściwości są naprzemiennie z tekstu wewnętrznego.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>Przestrzeń nazw XAML  
 Żaden z powyższych przykładach składni określony przestrzeni nazw XAML innych niż domyślna przestrzeń nazw XAML. W przypadku typowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, wartość domyślna przestrzeń nazw XAML jest określone jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przestrzeni nazw. Można określić przestrzeń nazw XAML innych niż domyślna przestrzeń nazw XAML i nadal używać składni podobne. Ale następnie dowolne miejsce gdzie klasy ma nazwę, która nie jest dostępny w ramach domyślnej przestrzeni nazw XAML, że nazwa klasy musi być poprzedzony prefiksu przestrzeni nazw XAML jako mapowany na odpowiedni przestrzeń nazw środowiska CLR. Na przykład `<custom:Example/>` jest składnia elementu obiektu można utworzyć wystąpienia elementu `Example` klasy, w którym przestrzeń nazw środowiska CLR zawierający tej klasy (i prawdopodobnie informacje zestawu zewnętrznych, które zawiera typy zapasowy) wcześniej została zmapowana na `custom` prefiks.  
  
 Aby uzyskać więcej informacji dotyczących przestrzeni nazw XAML, zobacz [przestrzeń nazw XAML i Namespace mapowanie WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 XAML definiuje rozszerzenie znacznika programowania jednostka, która umożliwia ucieczki z normalnym Obsługa procesora XAML wartości atrybutów ciąg lub obiekt elementów i różni się przetwarzania do klasy zapasowego. Znak, który identyfikuje rozszerzenie znacznika procesor XAML, gdy przy użyciu składni atrybutu jest otwierającym nawiasie klamrowym ({}), a następnie znaków innych niż zamykający nawias klamrowy (}). Pierwszy ciąg po otwierającym nawiasie klamrowym musi odwoływać się klasy, która udostępnia rozszerzenie zachowanie określonego rozszerzenia, gdy odwołanie może pominąć podciąg "" Jeśli podciąg tego jest częścią nazwy klasy wartość true. Pojedyncze spacje mogą być wyświetlane, a następnie każdy następnej znak jest używany jako dane wejściowe przez implementację rozszerzenia dopóki napotkano zamykający nawias klamrowy.  
  
 Implementacja .NET XAML używa <xref:System.Windows.Markup.MarkupExtension> klasy abstrakcyjnej podstawę dla wszystkich rozszerzeń znaczników obsługiwane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oraz inne platformy lub technologii. Rozszerzenia znaczników który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] specjalnie implementuje są często mają na celu dostarczenie oznacza odwoływać się do innych istniejących obiektów lub odroczonego odwołuje się do obiektów, które zostanie obliczone w czasie wykonywania. Na przykład proste powiązanie danych WPF to osiągnąć, określając `{Binding}` — rozszerzenie znaczników zamiast wartość, która zwykle zajmie określonej właściwości. Włączyć wiele rozszerzeń znaczników WPF Składnia atrybutu dla właściwości, w którym Składnia atrybutu w przeciwnym razie będzie niemożliwe. Na przykład <xref:System.Windows.Style> obiekt jest dość złożone typu, który zawiera szereg zagnieżdżonych obiektów i właściwości. Style na platformie WPF są zazwyczaj definiowane jako zasób w <xref:System.Windows.ResourceDictionary>i następnie odwoływać się za pomocą jednego z dwóch rozszerzenia znaczników WPF, które żądają zasobu. Rozszerzenie znacznika różni się obliczania wartości właściwości do wyszukiwania zasobów i umożliwia podanie wartości <xref:System.Windows.FrameworkElement.Style%2A> właściwości, biorąc typu <xref:System.Windows.Style>w atrybutu składni, jak w poniższym przykładzie:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 W tym miejscu `StaticResource` identyfikuje <xref:System.Windows.StaticResourceExtension> klasa dostarcza implementację rozszerzenia znaczników. Ciąg dalej `MyStyle` jest używany jako dane wejściowe dla innych niż domyślne <xref:System.Windows.StaticResourceExtension> konstruktora, gdzie parametr pobrane z ciągu rozszerzenia deklaruje żądany <xref:System.Windows.ResourceKey>. `MyStyle` powinien być [x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) wartość <xref:System.Windows.Style> definiowany jako zasób. [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) użycia żądań, że zasób służyć do zapewnienia <xref:System.Windows.Style> wartość właściwości przy użyciu logiki wyszukiwania zasobów statycznych w czasie ładowania.  
  
 Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md). Odwołania do rozszerzenia znaczników i innych XAML programowania Funkcje włączane w ogólne implementacji .NET XAML, zobacz [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md). Dla rozszerzenia znaczników dla określonych WPF, zobacz [WPF XAML rozszerzenia](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Dołączone właściwości  
 Dołączone właściwości są pojęcie programowania wprowadzono w języku XAML, zgodnie z którymi właściwości można własnością i wynika z określonego typu, ale ustawione jako właściwość elementów lub atrybutów w dowolnym elemencie. Scenariusz podstawowy czy dołączone właściwości są przeznaczone dla jest umożliwienie elementy podrzędne w strukturze znaczników informacji raportu, aby element nadrzędny bez konieczności model obiektowy często udostępnione przez wszystkie elementy. Z drugiej strony można używać właściwości dołączonych przez elementy nadrzędne informacji raportu, aby elementy podrzędne. Aby uzyskać więcej informacji dotyczących przeznaczenia dołączone właściwości oraz sposobu tworzenia własnych dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Dołączone właściwości należy użyć składni, pozornie podobny składni elementu właściwości, w tym również określić *typeName*. *propertyName* kombinacji. Istnieją dwie ważne różnice:  
  
-   Można użyć *typeName*. *propertyName* kombinacja nawet wtedy, gdy ustawienie dołączona właściwość za pomocą składni atrybutu. Dołączone właściwości są tylko wówczas, gdzie kwalifikowanie nazwa właściwości jest wymagany w składni atrybutu.  
  
-   Umożliwia także składni elementu właściwości dołączonych właściwości. Niemniej jednak w przypadku składni elementu właściwości typowe *typeName* wskazuje element obiekt zawierający element właściwości. Jeśli odnosi się do właściwości dołączonej, a następnie *typeName* jest klasa, która definiuje dołączona właściwość nie zawierające element object.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Dołączone zdarzenia  
 Dołączone zdarzenia są innego koncepcji programowania wprowadzono w języku XAML, gdzie można definiować zdarzenia w określonym typie, ale obsługi może dołączyć w dowolnym elemencie obiektu. W implementacji WOF często typu, który definiuje dołączone zdarzenie jest typem statyczny, który definiuje usługę, a czasami tych dołączone zdarzenia są udostępniane przez alias kierowanego zdarzenia w typach, które udostępniają usługi. Programy obsługi dla dołączone zdarzenia są określane za pomocą składni atrybutu. Zgodnie z dołączone zdarzenia Składnia atrybutu jest rozwinięta dla dołączone zdarzenia umożliwić *typeName*. *eventName* użycia, gdzie *typeName* jest klasa, która zapewnia `Add` i `Remove` metod dostępu do programu obsługi zdarzeń dla infrastruktury dołączone zdarzenie i *eventName* jest nazwą zdarzenia.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>Anatomia elementu głównego XAML  
 W poniższej tabeli przedstawiono typowe elementu głównego XAML podziale, przedstawiający określone atrybuty elementu głównego:  
  
|||  
|-|-|  
|`<Page`|Element object otwarcia elementu głównego|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Wartość domyślna ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) przestrzeni nazw XAML|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|Przestrzeń nazw XAML dla języka XAML|  
|`x:Class="ExampleNamespace.ExampleCode"`|Deklaracji częściowej klasy, która łączy znaczników do dowolnego kodem zdefiniowanej dla klasy częściowej|  
|`>`|Końcowy element object dla katalogu głównego. Obiekt nie jest jeszcze zamknięty, ponieważ element zawiera elementy podrzędne|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>Opcjonalne i Nonrecommended XAML użycia  
 W poniższych sekcjach opisano użycia XAML technicznie obsługiwanych przez procesorów XAML, ale który produkcji szczegółowości lub inne problemy estetycznych zakłócać plików XAML pozostałych zrozumiałą dla użytkownika, kiedy Twoje programować aplikacje, które zawierają źródła XAML .  
  
### <a name="optional-property-element-usages"></a>Opcjonalna właściwość elementu użycia  
 Opcjonalna właściwość elementu użycia obejmują jawnie wypisywanie zawartości właściwości elementu czy procesora XAML uwzględnia niejawne. Na przykład gdy zadeklarować zawartość <xref:System.Windows.Controls.Menu>, można wybrać jawnie deklarować <xref:System.Windows.Controls.ItemsControl.Items%2A> Kolekcja <xref:System.Windows.Controls.Menu> jako `<Menu.Items>` tagu elementu właściwości oraz miejsce każde <xref:System.Windows.Controls.MenuItem> w `<Menu.Items>`, a nie niż przy użyciu niejawnego zachowanie procesora XAML który wszystkie elementy podrzędne <xref:System.Windows.Controls.Menu> musi być <xref:System.Windows.Controls.MenuItem> i są umieszczane w <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji. Czasami opcjonalne użycia może pomóc wizualnie wyjaśnienie struktury obiekt reprezentowany w znaczniku. Lub czasami użycie elementu jawną właściwość można uniknąć kod znaczników, który jest technicznie funkcjonalności, ale wizualnie skomplikowana, np. rozszerzenia znaczników zagnieżdżonych w wartości atrybutu.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Pełna typeName.memberName kwalifikowana atrybutów  
 *TypeName*. *memberName* tworzą dla atrybutu rzeczywiście działa powszechnie więcej niż tylko wielkością liter kierowanego zdarzenia. W innych sytuacjach formularza jest zbędny, ale nie należy go, jeśli tylko ze względu na styl znaczników i czytelności. W poniższym przykładzie odwołania do każdego z trzech <xref:System.Windows.Controls.Control.Background%2A> atrybutu są całkowicie równoważne:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` działa, ponieważ kwalifikowaną wyszukiwania dla tej właściwości na <xref:System.Windows.Controls.Button> zakończy się pomyślnie (<xref:System.Windows.Controls.Control.Background%2A> została odziedziczona z kontroli) i <xref:System.Windows.Controls.Button> jest klasa elementu obiekt lub klasa bazowa. `Control.Background` działa, ponieważ <xref:System.Windows.Controls.Control> klasa faktycznie definiuje <xref:System.Windows.Controls.Control.Background%2A> i <xref:System.Windows.Controls.Control> jest <xref:System.Windows.Controls.Button> klasy podstawowej.  
  
 Jednak następujące *typeName*. *memberName* przykład formularza nie działa i jest wyświetlany w związku z tym komentarze:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> jest innej klasy pochodnej z <xref:System.Windows.Controls.Control>, i ma określony `Label.Background` w <xref:System.Windows.Controls.Label> object element, to użycie będą działały. Jednak ponieważ <xref:System.Windows.Controls.Label> nie jest klasa lub klasa podstawowa <xref:System.Windows.Controls.Button>, określonego zachowania procesora XAML jest następnie przetwarzanie `Label.Background` jako dołączona właściwość. `Label.Background` nie jest dostępne właściwości dołączonej i użycia nie powiedzie się.  
  
### <a name="basetypenamemembername-property-elements"></a>Elementy właściwości baseTypeName.memberName  
 W sposób analogiczny, jak *typeName*. *memberName* formularza działa w przypadku Składnia atrybutu *baseTypeName*. *memberName* składni działa w przypadku składni elementu właściwości. Na przykład działa następującej składni:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 W tym miejscu podano jako elementu właściwości `Control.Background` mimo że zawarte w elemencie właściwości `Button`.  
  
 Ale podobnie jak *typeName*. *memberName* formularza dla atrybutów, *baseTypeName*. *memberName* jest niska styl znaczników, i należy go unikać.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Przestrzeń nazw XAML (x:) — funkcje językowe](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozszerzenia WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters i XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [Klasy XAML i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
