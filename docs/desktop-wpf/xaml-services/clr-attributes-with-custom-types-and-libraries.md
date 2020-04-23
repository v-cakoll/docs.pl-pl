---
title: Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071767"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atrybuty CLR związane z XAML dla typów niestandardowych i bibliotek

W tym temacie opisano atrybuty środowiska wykonawczego języka wspólnego (CLR), które są zdefiniowane przez usługi .NET XAML Services. Opisano w nim również inne atrybuty CLR zdefiniowane w programie .NET, które mają scenariusz związany z XAML dla aplikacji do zestawów lub typów. Przypisywanie zestawów, typów lub elementów członkowskich za pomocą tych atrybutów CLR zapewnia informacje o systemie typu XAML związane z typami. Informacje są dostarczane do dowolnego konsumenta XAML, który używa usług .NET XAML do przetwarzania strumienia węzła XAML bezpośrednio lub za pośrednictwem dedykowanych czytników XAML i modułów zapisu XAML.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atrybuty CLR związane z XAML dla typów niestandardowych i niestandardowych elementów członkowskich

Przy użyciu atrybutów CLR pociąga za sobą, że używasz ogólnego CLR do definiowania typów, w przeciwnym razie takie atrybuty nie są dostępne. Jeśli używasz clr do definiowania tworzenia tekstu, a następnie domyślny kontekst schematu XAML używany przez program .NET XAML Services moduły zapisujące XAML można odczytać atrybucji CLR poprzez odbicie względem zestawów kopii zapasowej.

W poniższych sekcjach opisano atrybuty związane z XAML, które można zastosować do typów niestandardowych lub niestandardowych elementów członkowskich. Każdy atrybut CLR przekazuje informacje, które są istotne dla systemu typu XAML. W ścieżce ładowania przypisane informacje pomagają czytnikowi XAML utworzyć prawidłowy strumień węzła XAML lub pomagają modułowi zapisującego XAML w tworzeniu prawidłowego wykresu obiektów. W ścieżce zapisywania przypisane informacje pomagają czytnikowi XAML utworzyć prawidłowy strumień węzła XAML, który odtwarza informacje o systemie typu XAML; lub deklaruje wskazówki lub wymagania dotyczące serializacji dla modułu zapisującego XAML lub innych konsumentów XAML.

### <a name="ambientattribute"></a>Ambientattribute

**Dokumentacja referencyjna:**<xref:System.Windows.Markup.AmbientAttribute>

**Dotyczy:** Elementy członkowskie klasy, właściwości lub `get` akcesora, które obsługują właściwości dołączane.

**Argumenty:** Brak

<xref:System.Windows.Markup.AmbientAttribute>wskazuje, że właściwość lub wszystkie właściwości, które przyjmują przypisany typ, powinny być interpretowane w ramach pojęcia właściwości otoczenia w języku XAML. Pojęcie otoczenia odnosi się do sposobu, w jaki procesory XAML określają właścicieli typów elementów członkowskich. Właściwość otoczenia jest właściwością, w której wartość ma być dostępna w kontekście analizatora podczas tworzenia wykresu obiektu, ale gdzie typowe wyszukiwanie elementu członkowskiego typu jest zawieszone dla bezpośredniego tworzonego zestawu węzłów XAML.

Pojęcie otoczenia można zastosować do dołączanych elementów członkowskich, które nie są reprezentowane jako <xref:System.AttributeTargets>właściwości pod względem definiowania atrybucji CLR . Użycie atrybucji metody powinny być `get` stosowane tylko dla akcesora, który obsługuje dołączane użycie dla XAML.

### <a name="constructorargumentattribute"></a>Constructorargumentattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**Dotyczy:** Klasa

**Argumenty:** Ciąg, który określa nazwę właściwości, która pasuje do pojedynczego argumentu konstruktora.

<xref:System.Windows.Markup.ConstructorArgumentAttribute>określa, że obiekt może zostać zainicjowany przy użyciu składni konstruktora bez parametrów oraz że właściwość o określonej nazwie dostarcza informacji o konstrukcji. Te informacje są przeznaczone przede wszystkim do serializacji XAML. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>Contentpropertyattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**Dotyczy:** Klasa

**Argumenty:** Ciąg, który określa nazwę elementu członkowskiego przypisanego typu.

<xref:System.Windows.Markup.ContentPropertyAttribute>wskazuje, że właściwość nazwana przez argument powinna służyć jako właściwość zawartości XAML dla tego typu. Definicja właściwości zawartości XAML dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Definicję można zastąpić na określonym typie pochodnym, stosując <xref:System.Windows.Markup.ContentPropertyAttribute> ją do określonego typu pochodnego.

Dla właściwości, która służy jako właściwość zawartości XAML, tagowanie elementu właściwości dla właściwości można pominąć w użyciu XAML. Zazwyczaj należy wyznaczyć właściwości zawartości XAML, które promują usprawnione znaczniki XAML dla modeli zawartości i hermetyzacji. Ponieważ tylko jeden element członkowski może być wyznaczony jako właściwość zawartości XAML, czasami masz wybór projektu, aby w odniesieniu do tego, który z kilku właściwości kontenera typu powinny być wyznaczone jako właściwość zawartości XAML. Inne właściwości kontenera muszą być używane z jawnymi elementami właściwości.

W strumieniu węzła XAML właściwości zawartości `StartMember` XAML nadal generują i `EndMember` węzły, używając nazwy właściwości <xref:System.Xaml.XamlMember>właściwości . Aby ustalić, czy element członkowski jest właściwością zawartości `StartObject` XAML, <xref:System.Xaml.XamlType.ContentProperty%2A>sprawdź <xref:System.Xaml.XamlType> wartość z pozycji i uzyskaj wartość .

### <a name="contentwrapperattribute"></a>Contentwrapperattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**Dotyczy:** Klasa, w szczególności typy kolekcji.

**Argumenty:** A, <xref:System.Type> który określa typ, który ma być używany jako typ otoki zawartości dla zawartości obcej.

<xref:System.Windows.Markup.ContentWrapperAttribute>określa jeden lub więcej typów na typ skojarzonej kolekcji, który będzie używany do zawijania zawartości obcej. Zawartość obca odnosi się do przypadków, w których ograniczenia systemowe typu na typ właściwości zawartości nie przechwytują wszystkich możliwych przypadków zawartości, które będzie obsługiwać użycie XAML dla typu posiadania. Na przykład obsługa XAML dla zawartości określonego typu może obsługiwać <xref:System.Collections.ObjectModel.Collection%601>ciągi w silnie typowo typowym typie . Otoki zawartości są przydatne do migracji wcześniej istniejących konwencji znaczników do koncepcji XAML wartości przypisywanych dla kolekcji, takich jak migrowanie modeli zawartości związanych z tekstem.

Aby określić więcej niż jeden typ otoki zawartości, zastosuj atrybut wiele razy.

### <a name="dependsonattribute"></a>Dependsonattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.DependsOnAttribute>

**Dotyczy:** Właściwość

**Argumenty:** Ciąg, który określa nazwę innego elementu członkowskiego przypisanego typu.

<xref:System.Windows.Markup.DependsOnAttribute>wskazuje, że przypisana właściwość zależy od wartości innej właściwości. Zastosowanie tego atrybutu do definicji właściwości gwarantuje, że właściwości zależne są przetwarzane najpierw w zapisie obiektu XAML. Użycia określić <xref:System.Windows.Markup.DependsOnAttribute> wyjątkowe przypadki właściwości na typy, w których określona kolejność analizowania musi być przestrzegane dla tworzenia prawidłowego obiektu.

Do definicji <xref:System.Windows.Markup.DependsOnAttribute> właściwości można zastosować wiele przypadków.

### <a name="markupextensionreturntypeattribute"></a>Markupextensionreturntypeattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**Dotyczy:** Klasa, która ma być <xref:System.Windows.Markup.MarkupExtension> typem pochodnym.

**Argumenty:** A, <xref:System.Type> który określa najbardziej precyzyjny `ProvideValue` typ oczekiwać <xref:System.Windows.Markup.MarkupExtension>w wyniku przypisane .

Aby uzyskać więcej informacji, zobacz [Rozszerzeń znaczników dla XAML Overview](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>Namescopepropertyattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**Dotyczy:** Klasa

**Argumenty:** Obsługuje dwie formy atrybucji:

- Ciąg, który określa nazwę właściwości na przypisany typ.

- Ciąg, który określa nazwę właściwości i <xref:System.Type> dla typu, który definiuje nazwę nazwanej właściwości. Ten formularz służy do określania dołączanego elementu członkowskiego jako właściwości xaml namescope.

<xref:System.Windows.Markup.NameScopePropertyAttribute>określa właściwość, która zapewnia wartość xaml namescope dla przypisanej klasy. Właściwość xaml namescope ma odwoływać się <xref:System.Windows.Markup.INameScope> do obiektu, który implementuje i przechowuje rzeczywisty identyfikator XAML, jego magazyn i jego zachowanie.

### <a name="runtimenamepropertyattribute"></a>Runtimenamepropertyattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**Dotyczy:** Klasa

**Argumenty:** Ciąg, który określa nazwę właściwości nazwa w czasie wykonywania na przypisany typ.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>zgłasza właściwość przypisanego typu, który jest mapowana do XAML [x:Name Directive](xname-directive.md). Właściwość musi być <xref:System.String> typu i musi być odczyt/zapis.

Definicja dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Definicję można zastąpić na określonym typie pochodnym, stosując <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> ją do określonego typu pochodnego.

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespacePrzywujeczast

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**Dotyczy:** Typy

**Argumenty:** Brak.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>jest stosowany do określonych typów, które mogą pojawić się jako elementy podrzędne <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>w zawartości znaczącej w białej przestrzeni (zawartość posiadana przez kolekcję, która ma ). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>dotyczy głównie ścieżki zapisu, ale jest dostępna w systemie typu XAML <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>w ścieżce obciążenia, sprawdzając . Aby uzyskać więcej informacji, zobacz [Przetwarzanie odstępów w języku XAML](white-space-processing.md).

### <a name="typeconverterattribute"></a>Typeconverterattribute

**Dokumentacja referencyjna:**  <xref:System.ComponentModel.TypeConverterAttribute>

**Dotyczy:** Klasa, właściwość, metoda (jedynym przypadkiem metody `get` prawidłowej XAML jest akcesor, który obsługuje dołączany element członkowski).

**Argumenty:** Z <xref:System.Type> <xref:System.ComponentModel.TypeConverter>.

<xref:System.ComponentModel.TypeConverterAttribute>w kontekście XAML odwołuje <xref:System.ComponentModel.TypeConverter>się do niestandardowego . Zapewnia <xref:System.ComponentModel.TypeConverter> to zachowanie konwersji typów dla typów niestandardowych lub elementów członkowskich tego typu.

Zastosuj <xref:System.ComponentModel.TypeConverterAttribute> atrybut do swojego typu, odwołując się do implementacji konwertera typu. Konwertery typów dla XAML można zdefiniować na klasach, strukturach lub interfejsach. Nie musisz podawać konwersji typów dla wyliczenia, ta konwersja jest włączona natywnie.

Konwerter typów powinien być w stanie przekonwertować z ciągu, który jest używany dla atrybutów lub tekst inicjowania w znacznikach, do zamierzonego typu docelowego. Aby uzyskać więcej informacji, zobacz [TypeConverters i XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

Zamiast stosować do wszystkich wartości typu, zachowanie konwertera typu dla XAML można również ustanowić na określonej właściwości. W takim przypadku <xref:System.ComponentModel.TypeConverterAttribute> stosuje się do definicji właściwości (definicji zewnętrznej, a nie konkretne `get` i `set` definicje).

Zachowanie konwertera typu dla użycia XAML niestandardowego elementu członkowskiego <xref:System.ComponentModel.TypeConverterAttribute> dołączanego można przypisać, stosując do akcesora `get` metody obsługującego użycie XAML.

Podobne <xref:System.ComponentModel.TypeConverter>do <xref:System.ComponentModel.TypeConverterAttribute> , istniał w .NET przed istnieniem XAML i model konwertera typu służył innych celów. Aby odwołać się <xref:System.ComponentModel.TypeConverterAttribute>i użyć, należy w `using` pełni <xref:System.ComponentModel>go zakwalifikować lub dostarczyć oświadczenie dla . Uwzględnij również zestaw systemowy w projekcie.

### <a name="uidpropertyattribute"></a>Atrybut UidPropertyAttribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**Dotyczy:** Klasa

**Argumenty:** Ciąg, który odwołuje się do odpowiedniej właściwości za pomocą nazwy.

Wskazuje właściwość CLR klasy, która aliasuje [x:Uid Dyrektywy](xuid-directive.md).

### <a name="usableduringinitializationattribute"></a>UżytkowyDuringInitializationAttribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**Dotyczy:** Klasa

**Argumenty:** Wartość logiczna. Jeśli jest używany zgodnie z przeznaczeniem atrybutu, `true`wartość powinna być ustawiona na .

Wskazuje, czy typ jest zbudowany z góry na dół podczas tworzenia wykresu obiektu XAML. Jest to zaawansowana koncepcja, która jest prawdopodobnie ściśle związana z definicją modelu programowania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>Valueserializerattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**Dotyczy:** Klasa, właściwość, metoda (jedynym przypadkiem metody `get` prawidłowej XAML jest akcesor, który obsługuje dołączany element członkowski).

**Argumenty:** A, <xref:System.Type> który określa klasę obsługi serializatora wartości do użycia podczas serializacji wszystkich właściwości przypisanego typu lub określonej właściwości przypisanej.

<xref:System.Windows.Markup.ValueSerializer>określa klasę serializacji wartości, która wymaga więcej <xref:System.ComponentModel.TypeConverter> stanu i kontekstu niż robi. <xref:System.Windows.Markup.ValueSerializer>może być skojarzony z dołączanym elementem członkowskim, <xref:System.Windows.Markup.ValueSerializerAttribute> stosując `get` atrybut na statycznej metodzie akcesora dla dołączanego elementu członkowskiego. Serializacja wartości ma również zastosowanie do wyliczeń, interfejsów i struktur, ale nie dla delegatów.

### <a name="whitespacesignificantcollectionattribute"></a>Whitespacesignificantcollectionattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**Dotyczy:** Klasa, w szczególności typy kolekcji, które powinny obsługiwać zawartość mieszaną, gdzie biały znak wokół elementów obiektu może być istotne dla reprezentacji interfejsu użytkownika.

**Argumenty:** Brak.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>wskazuje, że typ kolekcji powinny być przetwarzane jako biały znak istotne przez procesor XAML, co wpływa na budowę węzła węzła XAML węzła węzła węzła węzła węzła węzła węzła węzła węzła w kolekcji. Aby uzyskać więcej informacji, zobacz [Przetwarzanie odstępów w języku XAML](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>Xamldeferloadattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**Dotyczy:** Klasa, właściwość.

**Argumenty:** Obsługuje dwa typy formularzy atrybucji jako ciągi lub typy jako <xref:System.Type>. Zobacz: <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Wskazuje, że klasa lub właściwość ma użycie obciążenia odroczonego dla XAML (takie jak zachowanie szablonu) i zgłasza klasę, która umożliwia zachowanie odroczenia i jego typ miejsca docelowego/zawartości.

### <a name="xamlsetmarkupextensionattribute"></a>Xamlsetmarkupextensionattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**Dotyczy:** Klasa

**Argumenty:** Nazwy wywołania zwrotnego.

Wskazuje, że klasa może użyć rozszerzenia znaczników, aby podać wartość dla jednej lub więcej jego właściwości i odwołuje się do programu obsługi, który moduł zapisujący XAML powinien wywołać przed wykonaniem operacji zestawu rozszerzeń znaczników na dowolnej właściwości klasy.

### <a name="xamlsettypeconverterattribute"></a>Xamlsettypeconverterattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**Dotyczy:** Klasa

**Argumenty:** Nazwy wywołania zwrotnego.

Wskazuje, że klasa może użyć konwertera typów, aby podać wartość dla jednej lub więcej jego właściwości i odwołuje się do programu obsługi, który moduł zapisujący XAML powinien wywołać przed wykonaniem operacji konwertera typów na dowolnej właściwości klasy.

### <a name="xmllangpropertyattribute"></a>Xmllangpropertyattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**Dotyczy:** Klasa

**Argumenty:** Ciąg, który określa nazwę właściwości do aliasu `xml:lang` na przypisany typ.

<xref:System.Windows.Markup.XmlLangPropertyAttribute>zgłasza właściwość przypisanego typu, który `lang` jest mapowana do dyrektywy XML. Właściwość nie musi <xref:System.String> być typu, ale musi być przypisany z ciągu (przypisanie można wykonać przez skojarzenie konwertera typu z typem właściwości lub z określoną właściwością). Właściwość musi być odczytana/zapis.

Scenariusz mapowania `xml:lang` jest tak, że model obiektu środowiska wykonawczego ma dostęp do informacji o języku określonym w języku XML bez specjalnie przetwarzania za pomocą XMLDOM.

Definicja dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Definicję można zastąpić na określonym typie pochodnym, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> dla określonego typu pochodnego, chociaż jest to nietypowy scenariusz.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atrybuty CLR związane z XAML na poziomie zestawu

W poniższych sekcjach opisano atrybuty związane z XAML, które nie są stosowane do typów lub definicji elementów członkowskich, ale zamiast tego są stosowane do zestawów. Te atrybuty są istotne dla ogólnego celu definiowania biblioteki, która zawiera typy niestandardowe do użycia w języku XAML. Niektóre atrybuty nie muszą mieć bezpośredniego wpływu na strumień węzła XAML, ale są przekazywane w strumieniu węzła dla innych konsumentów do użycia. Konsumenci informacji obejmują środowiska projektowe lub procesy serializacji, które wymagają informacji o przestrzeni nazw XAML i skojarzonych informacji o prefiksach. Kontekst schematu XAML (w tym domyślne usługi .NET XAML Services) również używa tych informacji.

### <a name="xmlnscompatiblewithattribute"></a>Xmlnscompatiblewithattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Argumenty:**

- Ciąg określający identyfikator obszaru nazw XAML do podporządkowania.

- Ciąg określający identyfikator obszaru nazw XAML, który może podporządkować obszar nazw XAML z poprzedniego argumentu.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>określa, że obszar nazw XAML może być podporządkowany przez inny obszar nazw XAML. Zazwyczaj podnajmujący obszar nazw XAML jest wskazany <xref:System.Windows.Markup.XmlnsDefinitionAttribute>we uprzednio zdefiniowanym obszarze nazw . Ta technika może służyć do przechowywania wersji słownictwa XAML w bibliotece i aby był zgodny z wcześniej zdefiniowanych znaczników względem wcześniejszego słownictwa wersji.

### <a name="xmlnsdefinitionattribute"></a>Xmlnsdefinitionattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Argumenty:**

- Ciąg określający identyfikator obszaru nazw XAML do zdefiniowania.

- Ciąg, który nazywa obszar nazw CLR. Obszar nazw CLR należy zdefiniować typy publiczne w zestawie i co najmniej jeden z typów obszaru nazw CLR powinny być przeznaczone do użycia XAML.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>określa mapowanie na podstawie na zestaw między przestrzenią nazw XAML a obszarem nazw CLR, który jest następnie używany do rozpoznawania typów przez moduł zapisujący obiekt XAML lub kontekst schematu XAML.

  Więcej niż <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jeden może być stosowany do złożenia. Można to zrobić z dowolnej kombinacji następujących powodów:

- Projekt biblioteki zawiera wiele obszarów nazw CLR dla logicznej organizacji dostępu do interfejsu API w czasie wykonywania; jednak chcesz, aby wszystkie typy w tych obszarach nazw były użyteczne dla XAML, odwołując się do tej samej przestrzeni nazw XAML. W takim przypadku należy <xref:System.Windows.Markup.XmlnsDefinitionAttribute> zastosować kilka <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> atrybutów <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> przy użyciu tej samej wartości, ale różne wartości. Jest to szczególnie przydatne, jeśli definiujesz mapowania dla obszaru nazw XAML, które mają być domyślną przestrzenią nazw XAML w typowym użyciu.

- Projekt biblioteki zawiera wiele obszarów nazw CLR i chcesz celowe oddzielenie przestrzeni nazw XAML między użyciami typów w tych obszarach nazw CLR.

- Definiujesz obszar nazw CLR w zestawie i chcesz, aby był dostępny za pośrednictwem więcej niż jednego obszaru nazw XAML. W tym scenariuszu występuje, gdy obsługujesz wiele słowników z tej samej bazy kodu.

- Obsługa języka XAML jest definiowana w co najmniej jednej przestrzeni nazw CLR. W takim przypadku <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartość `http://schemas.microsoft.com/winfx/2006/xaml`powinna być .

### <a name="xmlnsprefixattribute"></a>Xmlnsprefixattribute

**Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Argumenty:**

- Ciąg określający identyfikator obszaru nazw XAML.

- Ciąg określający zalecany prefiks.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>określa zalecany prefiks do użycia w obszarze nazw XAML. Prefiks jest przydatny podczas pisania elementów i atrybutów w pliku XAML, który jest serializowany przez usługi <xref:System.Xaml.XamlXmlWriter>.NET XAML Services lub gdy biblioteka implementująca XAML współdziała ze środowiskiem projektowym, które ma funkcje edycji XAML.

  Więcej niż <xref:System.Windows.Markup.XmlnsPrefixAttribute> jeden może być stosowany do złożenia. Można to zrobić z dowolnej kombinacji następujących powodów:

- Zestaw definiuje typy dla więcej niż jednej przestrzeni nazw XAML. W takim przypadku należy zdefiniować różne wartości prefiksów dla każdej przestrzeni nazw XAML.

- Obsługujesz wiele słowników i używasz różnych prefiksów dla każdego słownictwa i przestrzeni nazw XAML.

- Definiujesz obsługę języka XAML w <xref:System.Windows.Markup.XmlnsDefinitionAttribute> zestawie `http://schemas.microsoft.com/winfx/2006/xaml`i masz dla . W takim przypadku zazwyczaj należy podwyższyć prefiks `x`.

> [!NOTE]
> Usługi NET XAML definiują również atrybut <xref:System.Windows.Markup.RootNamespaceAttribute>związany z XAML . Ten atrybut jest atrybutem na poziomie zestawu dla obsługi systemu projektu i nie jest istotne dla typów niestandardowych XAML.

## <a name="see-also"></a>Zobacz też

- <xref:System.Attribute>
- [Definiowanie typów niestandardowych do użytku z usługami .NET XAML](define-custom-types.md)
