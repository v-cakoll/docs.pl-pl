---
title: Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 13cc4d85a1a4b5c9b1ff61afbf7980a54e3d22d0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416281"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
W tym temacie opisano wspólne atrybuty środowiska uruchomieniowego (języka wspólnego CLR) języka, które są definiowane przez .NET Framework XAML Services. Omówiono także inne atrybuty CLR zdefiniowane w programie .NET Framework, które mają scenariusz związane z XAML dla aplikacji do zespołów lub typów. Przypisywanie zestawy, typy lub elementy członkowskie z tych atrybutów CLR udostępnia informacje o systemie typu XAML powiązane z typami. Dane mają charakter-klient XAML, który używa usług programu .NET Framework XAML dla przetwarzania strumienia węzłów XAML bezpośrednio lub za pośrednictwem dedykowanej czytniki XAML i moduły zapisujące XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atrybuty CLR związane z XAML dla niestandardowych typów i członków niestandardowe  
 Przy użyciu atrybutów CLR pociąga za sobą, że używasz ogólnego środowiska CLR do definiowania typów, w przeciwnym razie takie atrybuty nie są dostępne. Jeśli używasz środowiska CLR do definiowania typu kopii domyślny kontekst schematu XAML, używane przez autorów XAML Services programu .NET Framework XAML może odczytywać CLR: uznanie autorstwa przez odbicie względem kopii zestawów.  
  
 W poniższych sekcjach opisano atrybuty związane z XAML, które można stosować do typów niestandardowych lub niestandardowych elementów członkowskich. Każdy atrybut CLR komunikuje się informacje, które są istotne dla systemu typu XAML. W polu Ścieżka obciążenia opartego na atrybutach informacji albo pomaga czytnika XAML tworzą nieprawidłowy strumień węzłów XAML lub pomaga utworzyć wykres prawidłowy obiekt Edytor XAML. W polu Zapisz ścieżkę, opartego na atrybutach informacji albo pomaga czytnika XAML tworzą nieprawidłowy strumień węzłów XAML, który reconstitutes informacje o systemie typu XAML; lub deklaruje wskazówki serializacji lub wymagania dotyczące zapisywania XAML lub innych klientów XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Dotyczy:** klasy, właściwości lub `get` elementy członkowskie metody dostępu, które obsługują można dołączyć właściwości.  
  
 **Argumenty:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute> Wskazuje, że właściwość lub wszystkich właściwości, które przyjmują opartego na atrybutach typu, powinien być interpretowany w ramach pojęcie zmieniono właściwość w XAML. Koncepcja otoczenia odnosi się do jak procesory XAML można ustalić typu właściciele elementów członkowskich. Zmieniono właściwość jest właściwością, w którym oczekiwaną wartością jest udostępnienie w kontekście analizator składni podczas tworzenia wykresu obiektu, ale w przypadku typowej składowej typu wyszukiwania jest zawieszone na natychmiastowe XAML zestawu węzłów tworzonych.  
  
 Otoczenia pojęcia mogą być stosowane do można dołączyć elementy członkowskie, które nie są reprezentowane jako właściwości pod względem jak uznanie autorstwa CLR definiuje <xref:System.AttributeTargets>. Użycie: uznanie autorstwa metody powinny być stosowane tylko w przypadku właściwości `get` metodę dostępu, która obsługuje obciążenie można dołączyć do XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** ciąg określający nazwę właściwości, odpowiadający argument jednego konstruktora.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> Określa, czy obiekt mogą być inicjowane przy użyciu składni innego niż domyślny konstruktor i czy właściwość o określonej nazwie dostarcza informacje do budowy. Te informacje są przeznaczone głównie dla serializacji XAML. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** ciąg, który określa nazwę elementu członkowskiego typu opartego na atrybutach.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> Wskazuje, że właściwość o nazwie określonej przez argument powinien służyć jako właściwość zawartości XAML dla tego typu. Definicja właściwości zawartości XAML dziedziczy dla wszystkich typów pochodnych, które są możliwe do przypisania do definiowania typu. Możesz zastąpić definicję dla określonego typu pochodnego, stosując <xref:System.Windows.Markup.ContentPropertyAttribute> określonego typu pochodnego.  
  
 Dla właściwości, która służy jako właściwość zawartości XAML można pominąć elementu właściwości znakowanie właściwości użycia XAML. Zazwyczaj należy wyznaczyć właściwości zawartości XAML, zapewniających sprawne znaczników XAML dla modeli zawartości i zawierania. Ponieważ tylko jeden element członkowski może zostać wyznaczony jako właściwość zawartości XAML, masz czasami uzasadnienie wyboru tych elementów się wskazujące, którzy kontenera kilka właściwości typu powinny być wyznaczone jako właściwość zawartości XAML. Inne właściwości kontenera musi być używana z jawną właściwość elementów.  
  
 Strumień węzłów XAML, właściwości zawartości XAML nadal do tworzenia `StartMember` i `EndMember` węzłów, przy użyciu nazwy właściwości dla <xref:System.Xaml.XamlMember>. Aby określić, czy członek jest właściwość zawartości XAML, sprawdź <xref:System.Xaml.XamlType> wartość z `StartObject` Umieść i uzyskiwanie wartości <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Dotyczy:** klasy, w szczególności typy kolekcji.  
  
 **Argumenty:** A <xref:System.Type> , który określa typ do użycia jako typ zawartości otoki obcego zawartości.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> Określa co najmniej jednego typu na typ skojarzonej kolekcji, który będzie służyć do zawijania obcy zawartości. Zawartość obcy odwołuje się do przypadków, gdy ograniczenia systemu typu na typ właściwości zawartości nie należy przechwytywać wszystkie możliwe przypadków zawartości, które będą obsługują użycia XAML dla typu, będącego właścicielem. Na przykład XAML Obsługa zawartości określonego typu może obsługiwać ciągi w silnie typizowany ogólny <xref:System.Collections.ObjectModel.Collection%601>. Otoki zawartości są przydatne w przypadku migrowania istniejących konwencje znaczników do koncepcji firmy XAML można przypisać wartości do kolekcji, takie jak migracja związane z tekstem modele zawartości.  
  
 Aby określić więcej niż jeden typ zawartości otoki, zastosuj atrybut wiele razy.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Dotyczy:** właściwości  
  
 **Argumenty:** ciąg określający nazwę innego członka typu opartego na atrybutach.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> Wskazuje, że właściwość opartego na atrybutach zależy od wartości innej właściwości. Zastosowanie tego atrybutu do definicji właściwości gwarantuje, że właściwości zależne są przetwarzane jako pierwsze w formie pisemnej obiektu XAML. Sposoby użycia <xref:System.Windows.Markup.DependsOnAttribute> Określ wyjątkowych przypadkach właściwości na typy, których określonej kolejności analizy musi występować dla utworzenia prawidłowego obiektu.  
  
 Można zastosować wiele <xref:System.Windows.Markup.DependsOnAttribute> przypadków definicji właściwości.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Dotyczy:** klasy, która powinna być <xref:System.Windows.Markup.MarkupExtension> typu pochodnego.  
  
 **Argumenty:** A <xref:System.Type> określa najbardziej dokładne typ oczekiwany jako `ProvideValue` wynik opartego na atrybutach <xref:System.Windows.Markup.MarkupExtension>.  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** obsługuje dwa rodzaje autorstwa:  
  
-   Ciąg, który określa nazwę właściwości typu opartego na atrybutach.  
  
-   Ciąg, który określa nazwę właściwości i a <xref:System.Type> dla typu, który definiuje właściwość o nazwie. Ta forma jest do określania elementu członkowskiego można dołączyć jako właściwość namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> Określa właściwość, która zawiera wartość namescope XAML dla klasy opartego na atrybutach. Właściwość namescope XAML powinien odwoływać się do obiektu, który implementuje <xref:System.Windows.Markup.INameScope> i przechowuje rzeczywiste namescope XAML, jego magazynu i jego zachowanie.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** ciąg określający nazwę właściwości czasu wykonywania, nazwa typu opartego na atrybutach.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> Raporty właściwość typu opartego na atrybutach, który jest mapowany do XAML [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md). Właściwość musi być typu <xref:System.String> i musi być odczytu/zapisu.  
  
 Definicja dziedziczy dla wszystkich typów pochodnych, które są możliwe do przypisania do definiowania typu. Możesz zastąpić definicję dla określonego typu pochodnego, stosując <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> określonego typu pochodnego.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Dotyczy:** typów  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> jest stosowany do określonych typów, które mogą być wyświetlane jako elementy podrzędne w zawartości znaczące odstępu (zawartość w posiadaniu kolekcja, która ma <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> dotyczy głównie Zapisz ścieżkę, ale jest dostępna w systemie typu XAML w ścieżce obciążenia, sprawdzając <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Dokumentacja:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Dotyczy:** klas, właściwości, metody (tylko XAML prawidłową wielkość metoda `get` metodę dostępu, która obsługuje można dołączyć elementu członkowskiego).  
  
 **Argumenty:** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> w XAML kontekstu odwołuje się do niestandardowego <xref:System.ComponentModel.TypeConverter>. To <xref:System.ComponentModel.TypeConverter> zapewnia zachowanie konwersji typu niestandardowe typy lub elementy członkowskie tego typu.  
  
 Należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> atrybutu do danego typu odwołuje się do implementacji konwertera typu. Typy konwerterów dla XAML można zdefiniować klasy, struktury lub interfejsów. Nie trzeba podać konwersja typu dla wyliczenia, jest natywnie włączona konwersja.  
  
 Usługi konwertera typów powinno być możliwe do przekonwertowania w ciąg, który jest używany dla atrybutów lub inicjowania tekstu w znacznikach, do danego typu miejsca docelowego. Aby uzyskać więcej informacji, zobacz [TypeConverters i XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Zamiast stosowania się do wszystkich wartości na typ, zachowanie konwerter typu dla XAML może zostać nawiązana na określoną właściwość. W takim przypadku należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do definicji właściwości (definicja zewnętrzne, nie konkretne `get` i `set` definicji).  
  
 Można przypisać zachowanie konwertera typu użycia XAML niestandardowe można dołączyć elementu członkowskiego, stosując <xref:System.ComponentModel.TypeConverterAttribute> do `get` metodę dostępu metody, która obsługuje użycia XAML.  
  
 Podobnie jak <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> istniał w .NET Framework przed istnienie XAML, model konwertera typu od i do innych celów. Aby można było odwołać się i używać <xref:System.ComponentModel.TypeConverterAttribute>, należy całkowicie go lub podaj `using` poufności informacji dotyczące <xref:System.ComponentModel>. W projekcie, należy również uwzględnić zestawu systemowego.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** ciąg, który odwołuje się do odpowiednich właściwości według nazwy.  
  
 Wskazuje właściwość CLR klasy tego aliasy [x: Uid — dyrektywa](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** wartość logiczną. Jeśli używany dla atrybutu zamierzony cel, to zawsze powinien być określony jako `true`.  
  
 Wskazuje, czy ten typ jest wbudowana góra dół podczas tworzenia wykresu obiektu XAML. Jest to zaawansowanych koncepcji, który jest prawdopodobnie ściśle powiązane z definicji modelu programowania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Dotyczy:** klas, właściwości, metody (tylko XAML prawidłową wielkość metoda `get` metodę dostępu, która obsługuje można dołączyć elementu członkowskiego).  
  
 **Argumenty:** A <xref:System.Type> , który określa klasę wartość serializatora obsługi używany podczas serializowania wszystkich właściwości typu opartego na atrybutach lub konkretne opartego na atrybutach właściwości.  
  
 <xref:System.Windows.Markup.ValueSerializer> Określa klasę serializacji wartość, która wymaga więcej stanu i kontekście niż <xref:System.ComponentModel.TypeConverter> jest. <xref:System.Windows.Markup.ValueSerializer> może być skojarzony z możliwością dołączenia składową, stosując <xref:System.Windows.Markup.ValueSerializerAttribute> atrybutu statycznej `get` metody dostępu można dołączyć elementu członkowskiego. Serializacja wartości mają również zastosowanie do wyliczenia, interfejsy i struktur, ale nie dla obiektów delegowanych.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Dotyczy:** klasy, w szczególności typy kolekcji, które mają hostować zawartość mieszana, gdzie biały znak wokół elementów obiektu może być istotne dla reprezentacji interfejsu użytkownika.  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> Wskazuje typ kolekcji mają być przetwarzane jako znaczące biały procesora XAML, ma wpływ na konstrukcji węzłów wartość strumień węzłów XAML w kolekcji. Aby uzyskać więcej informacji, zobacz [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Dotyczy:** klasy i właściwości.  
  
 **Argumenty:** autorstwa obsługuje dwa typy jako ciągi formularzy lub typów jako <xref:System.Type>. Zobacz <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Wskazuje, że klasa lub właściwość ma użycia odroczonego ładowania XAML (np. zachowanie szablonu) i zgłasza klasę, która umożliwia zachowanie odkładanie i jego typu docelowego/zawartości.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** nazwy wywołania zwrotnego.  
  
 Wskazuje, że klasa umożliwia rozszerzenie znaczników podać wartość dla co najmniej jednej z jej właściwości i odwołuje się do programu obsługi, który Edytor XAML należy wywołać przed wykonaniem operacji zestawu rozszerzenia znaczników dowolne właściwości klasy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** nazwy wywołania zwrotnego.  
  
 Wskazuje, że klasy można użyć konwertera typów, aby podać wartość dla co najmniej jednej z jej właściwości i odwołuje się do programu obsługi, który Edytor XAML należy wywołać przed wykonaniem operacji zestawu konwertera typu dowolne właściwości klasy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Dotyczy:** klasy  
  
 **Argumenty:** ciąg określający nazwę właściwości do aliasu `xml:lang` opartego na atrybutach typu.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> Raporty właściwość typu atrybutami, który jest mapowany do pliku XML `lang` dyrektywy. Właściwość nie jest zawsze typu <xref:System.String>, ale musi być możliwy do przypisania z ciągu (można to osiągnąć przez skojarzenie konwertera typów z typem właściwości lub określone właściwości). Właściwość musi być odczytu/zapisu.  
  
 Scenariusz dla mapowania `xml:lang` jest model obiektowy środowiska uruchomieniowego ma dostęp do informacji język określony XML bez specjalnie przetwarzania za pomocą XMLDOM.  
  
 Definicja dziedziczy dla wszystkich typów pochodnych, które są możliwe do przypisania do definiowania typu. Możesz zastąpić definicję dla określonego typu pochodnego, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> na konkretnym pochodne typu, ale jest rzadko scenariusza.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atrybuty CLR związane z XAML na poziomie zestawu  
 W poniższych sekcjach opisano atrybuty związane z XAML, które nie są stosowane do typów lub definicje elementów członkowskich, ale zamiast tego są stosowane do zestawów. Te atrybuty są odpowiednie do ogólnego celu definiowania bibliotekę, która zawiera niestandardowe typy do użycia w XAML. Niektóre atrybuty nie zawsze wpływ strumień węzłów XAML bezpośrednio, ale są przekazywane w strumieniu węzła dla innych klientów do użycia. Konsumenci informacje obejmują środowiska projektowe lub procesy serializacji, które muszą informacji dotyczących przestrzeni nazw XAML i skojarzone z nimi informacje prefiks. XAML kontekst schematu (w tym domyślny usług programu .NET Framework XAML) również używa tych informacji.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumenty:**  
  
-   Ciąg, który określa identyfikator przestrzeni nazw XAML do uwzględnienia.  
  
-   Ciąg, który określa identyfikator przestrzeni nazw XAML, który można uwzględnienia przestrzeń nazw XAML z poprzednim argumentu.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> Określa, że przestrzeń nazw XAML może włączony przez innej przestrzeni nazw XAML. Zazwyczaj jest oznaczany subsuming przestrzeń nazw XAML w uprzednio zdefiniowanej <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta technika może być używane do obsługi wersji XAML słownictwa używanego w bibliotece i aby był zgodny z wcześniej zdefiniowanego znaczników względem wcześniej słownictwa numerów wersji.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumenty:**  
  
-   Ciąg, który określa identyfikator przestrzeni nazw XAML, aby zdefiniować.  
  
-   Ciąg, który nazwy przestrzeni nazw CLR. Przestrzeń nazw środowiska CLR, należy zdefiniować typy publiczne w swoim zestawie, i co najmniej jeden z typów przestrzeni nazw CLR powinien być przeznaczone do użycia XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Określa mapowanie na zasadzie na zestawie między przestrzeni nazw XAML i przestrzeń nazw środowiska CLR, która jest następnie używany do rozpoznawania typu przez moduł zapisujący obiektu XAML i kontekst schematu XAML.  
  
 Więcej niż jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> może odnosić się do zestawu. Może to zostać zrobione w jakiejkolwiek kombinacji następujących przyczyn:  
  
-   Projekt Biblioteka zawiera wiele przestrzeni nazw CLR dla logicznej organizacji dostęp do interfejsu API środowiska wykonawczego; Jednakże chcesz, aby wszystkie typy w tych obszarach nazw jako XAML można używać, odwołując się do tej samej przestrzeni nazw XAML. W takim przypadku należy zastosować kilka <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atrybuty, korzystając z tych samych <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartość, ale o innej <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> wartości. Jest to szczególnie przydatne w przypadku definiowania mapowań dla przestrzeni nazw XAML, który zamierza być domyślna przestrzeń nazw XAML wspólnej wykorzystania sieci framework lub aplikację.  
  
-   Projekt Biblioteka zawiera wiele przestrzeni nazw CLR i chcesz, aby oddzielenie użycia typów w tych przestrzeni nazw CLR zamierzonego przestrzeń nazw XAML.  
  
-   Definiowanie przestrzeni nazw CLR w zestawie i chcesz, aby być dostępne przez więcej niż jednej przestrzeni nazw XAML. W tym scenariuszu występuje, gdy znajdują się pomocne vocabularies wiele z tą samą bazą kodu.  
  
-   Obsługa języka XAML definiuje się w przestrzeni nazw CLR. W tym przypadku <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> . wartość powinna być `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Dokumentacja:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumenty:**  
  
-   Ciąg, który określa identyfikator przestrzeni nazw XAML.  
  
-   Ciąg, który określa zalecaną prefiks.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Określa prefiks zalecane dla przestrzeni nazw XAML. Prefiks jest przydatne podczas pisania elementów i atrybutów w pliku XAML, który jest serializowany przez usług .NET Framework XAML <xref:System.Xaml.XamlXmlWriter>, lub gdy biblioteki wykonawcze XAML korzysta z środowisko projektowania, który ma XAML funkcje edycji.  
  
 Więcej niż jeden <xref:System.Windows.Markup.XmlnsPrefixAttribute> może odnosić się do zestawu. Może to zostać zrobione w jakiejkolwiek kombinacji następujących przyczyn:  
  
-   Zestaw definiuje typy dla więcej niż jednej przestrzeni nazw XAML. W takim przypadku należy zdefiniować prefiksu różne wartości dla każdej przestrzeni nazw XAML.  
  
-   Wiele vocabularies znajdują się pomocne i używać różnych prefiksów dla każdego słownictwa i przestrzeń nazw XAML.  
  
-   Możesz zdefiniować obsługę języka XAML w zestawie, a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dla `http://schemas.microsoft.com/winfx/2006/xaml`. W tym przypadku zwykle powinny podwyższania poziomu prefiks `x`.  
  
> [!NOTE]
>  .NET framework XAML Services definiuje również atrybut związane z XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Ten atrybut jest atrybut poziomu zestawu Obsługa systemów projektów i nie jest to istotne dla niestandardowych typów XAML.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute>  
 [Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
