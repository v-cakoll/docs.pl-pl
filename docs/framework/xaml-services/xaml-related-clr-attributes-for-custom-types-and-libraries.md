---
title: Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a264ec3fa1232a058a3bfbabbe8b84712cf87322
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956411"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
W tym temacie opisano atrybuty środowiska uruchomieniowego języka wspólnego (CLR), które są zdefiniowane przez .NET Framework usług XAML. Opisano w nim również inne atrybuty CLR, które są zdefiniowane w .NET Framework, które mają scenariusz związany z XAML dla aplikacji do zestawów lub typów. Przypisywanie zestawów, typów lub elementów członkowskich przy użyciu tych atrybutów CLR zapewnia informacje o systemie typów XAML powiązane z typami. Informacje są udostępniane każdemu konsumentowi języka XAML korzystającemu z usług .NET Framework XAML do przetwarzania strumienia węzłów XAML bezpośrednio lub za pośrednictwem dedykowanych czytników XAML i autorów XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atrybuty CLR związane z XAML dla typów niestandardowych i niestandardowych elementów członkowskich  
 Użycie atrybutów CLR polega na tym, że używasz ogólnego środowiska CLR do definiowania typów, w przeciwnym razie takie atrybuty nie są dostępne. Jeśli używasz środowiska CLR do tworzenia kopii zapasowej typu, domyślny kontekst schematu XAML używany przez moduły zapisujące XAML usług XAML .NET Framework może odczytywać przypisanie CLR przez odbicie względem zestawów zapasowych.  
  
 W poniższych sekcjach opisano atrybuty dotyczące języka XAML, które można zastosować do typów niestandardowych lub niestandardowych elementów członkowskich. Każdy atrybut CLR komunikuje informacje istotne dla systemu typu XAML. W ścieżce ładowania informacje o atrybutach są pomocne w odniesieniu do czytnika XAML w postaci prawidłowego strumienia węzła XAML lub ułatwiające składnik zapisywania XAML generowanie prawidłowego grafu obiektów. W ścieżce zapisywania informacje o atrybutach są pomocne w odwzorze XAML w postaci prawidłowego strumienia węzła XAML, który odtworzy informacje o systemie typu XAML; lub deklaruje wskazówki serializacji lub wymagania dotyczące składnika zapisywania XAML lub innych odbiorców języka XAML.  
  
### <a name="ambientattribute"></a>W otoczeniu  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Dotyczy:** Elementy członkowskie klasy, właściwości `get` lub akcesora, które obsługują właściwości możliwe do dołączenia.  
  
 **Argumentu** Brak  
  
 <xref:System.Windows.Markup.AmbientAttribute>wskazuje, że właściwość lub wszystkie właściwości, które przyjmują typ z atrybutem, powinny być interpretowane w ramach koncepcji właściwości otoczenia w języku XAML. Koncepcja otoczenia odnosi się do tego, jak procesory XAML określają właścicieli typów członków. Właściwość otoczenia jest właściwością, w której oczekiwana wartość jest dostępna w kontekście analizatora podczas tworzenia grafu obiektów, ale w przypadku gdy typowe wyszukiwanie elementu członkowskiego typu jest zawieszone dla tworzonego zestawu węzłów XAML.  
  
 Koncepcję otoczenia można zastosować do dołączalnych elementów członkowskich, które nie są reprezentowane jako właściwości w zależności od tego, jak definiuje <xref:System.AttributeTargets>się przypisanie CLR. Użycie metody do przypisywania metod powinno być stosowane tylko w przypadku `get` metody dostępu, która obsługuje dołączanie użycia dla języka XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Ciąg określający nazwę właściwości, która pasuje do pojedynczego argumentu konstruktora.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Określa, że obiekt może zostać zainicjowany przy użyciu składni konstruktora bez parametrów i że właściwość o określonej nazwie dostarcza informacje o konstrukcji. Te informacje są przeznaczone głównie do serializacji XAML. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>Atrybut ContentPropertyAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Ciąg określający nazwę elementu członkowskiego typu z atrybutami.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>wskazuje, że właściwość o nazwie argumentu powinna być taka sama jak Właściwość zawartości XAML dla tego typu. Definicja właściwości zawartości XAML dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Możesz przesłonić definicję określonego typu pochodnego, stosując <xref:System.Windows.Markup.ContentPropertyAttribute> się do określonego typu pochodnego.  
  
 Dla właściwości, która służy jako właściwość zawartości XAML, można pominąć znakowanie elementu właściwości w użyciu języka XAML. Zwykle wyznacza się właściwości zawartości XAML, które promują udoskonalone znaczniki języka XAML dla zawartości i modeli zawierania. Ponieważ tylko jeden element członkowski można wyznaczyć jako właściwość zawartości XAML, czasami istnieje możliwość wyboru projektu, dla którego kilka właściwości kontenera typu powinna być wyznaczyna jako właściwość zawartości XAML. Inne właściwości kontenera muszą być używane z jawnymi elementami właściwości.  
  
 W strumieniu węzła XAML właściwości zawartości XAML nadal są `StartMember` wytwarzane `EndMember` i węzły przy użyciu nazwy właściwości <xref:System.Xaml.XamlMember>. Aby określić, czy element członkowski jest właściwością zawartość XAML, sprawdź <xref:System.Xaml.XamlType> wartość `StartObject` z pozycji <xref:System.Xaml.XamlType.ContentProperty%2A>i uzyskaj wartość.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Dotyczy:** Klasy, w tym typy kolekcji.  
  
 **Argumentu** A <xref:System.Type> określa typ, który ma być używany jako typ otoki zawartości dla zawartości obcej.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Określa jeden lub więcej typów w skojarzonym typie kolekcji, który będzie używany do zawijania zawartości obcej. Zawartość obca odnosi się do przypadków, w których ograniczenia systemu typu dla typu właściwości zawartości nie przechwytują wszystkich możliwych przypadków zawartości, które są obsługiwane przez użycie języka XAML dla typu będącego właścicielem. Na przykład, obsługa języka XAML dla zawartości określonego typu może obsługiwać ciągi w rodzajowym <xref:System.Collections.ObjectModel.Collection%601>jednoznacznie określonym typie. Otoki zawartości są przydatne do migrowania istniejących konwencji oznakowania do elementów kodu XAML, które można przypisać do kolekcji, takich jak Migrowanie modeli zawartości związanych z tekstem.  
  
 Aby określić więcej niż jeden typ otoki zawartości, zastosuj atrybut wiele razy.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Dotyczy:** Właściwość  
  
 **Argumentu** Ciąg określający nazwę innego elementu członkowskiego typu z atrybutami.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>wskazuje, że właściwość z atrybutami zależy od wartości innej właściwości. Zastosowanie tego atrybutu do definicji właściwości gwarantuje, że właściwości zależne są przetwarzane najpierw w zapisie obiektu XAML. <xref:System.Windows.Markup.DependsOnAttribute> Użycia określają wyjątkowe przypadki właściwości na typach, w których należy wykonać konkretną kolejność analizy, aby można było utworzyć prawidłowe obiekty.  
  
 Do definicji właściwości można <xref:System.Windows.Markup.DependsOnAttribute> zastosować wiele przypadków.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Dotyczy:** Klasa, która powinna być <xref:System.Windows.Markup.MarkupExtension> typem pochodnym.  
  
 **Argumentu** A <xref:System.Type> , który określa najdokładniejszy typ, który powinien `ProvideValue` być oczekiwany jako <xref:System.Windows.Markup.MarkupExtension>wynik atrybutu.  
  
 Aby uzyskać więcej informacji, zobacz [znaczniki rozszerzeń dla języka XAML — Omówienie](markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Obsługuje dwie formy przypisywania:  
  
- Ciąg określający nazwę właściwości w typie z atrybutem.  
  
- Ciąg określający nazwę właściwości, a <xref:System.Type> dla typu, który definiuje nazwaną właściwość. Ten formularz służy do określania dołączalnego elementu członkowskiego jako właściwości namescope języka XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Określa właściwość, która dostarcza wartość namescope języka XAML dla klasy z atrybutami. Właściwość namescope języka XAML powinna odwoływać się do obiektu, który <xref:System.Windows.Markup.INameScope> implementuje i utrzymuje rzeczywiste namescope XAML, jego magazyn i jego zachowanie.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Ciąg określający nazwę właściwości Run-Time w typie z atrybutem.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>raportuje właściwość typu przypisanego do [x:Name](x-name-directive.md)języka XAML. Właściwość musi być typu <xref:System.String> i musi mieć Odczyt/zapis.  
  
 Definicja dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Możesz przesłonić definicję określonego typu pochodnego, stosując <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> się do określonego typu pochodnego.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Dotyczy:** Types  
  
 **Argumentu** Brak.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>stosuje się do określonych typów, które mogą być wyświetlane jako elementy podrzędne w ramach znaczącej ilości wolnego miejsca (zawartości przechowywanej przez <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>kolekcję mającą). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>ma głównie znaczenie dla ścieżki zapisu, ale jest dostępny w systemie typów XAML w ścieżce ładowania, sprawdzając <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Przetwarzanie białych miejsc w języku XAML](whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Dokumentacja referencyjna:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Dotyczy:** Klasa, właściwość, Metoda (jedyny przypadek metody języka XAML to `get` metoda dostępu, która obsługuje dołączalną składową).  
  
 **Argumentu** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>w kontekście XAML odwołuje się do <xref:System.ComponentModel.TypeConverter>niestandardowego. Zapewnia <xref:System.ComponentModel.TypeConverter> to zachowanie konwersji typu dla typów niestandardowych lub elementów członkowskich tego typu.  
  
 Ten <xref:System.ComponentModel.TypeConverterAttribute> atrybut jest stosowany do typu, który odwołuje się do implementacji konwertera typów. Można definiować konwertery typów dla języka XAML w klasach, strukturach lub interfejsach. Nie trzeba dostarczać konwersji typu dla wyliczeń, ponieważ konwersja jest włączona natywnie.  
  
 Konwerter typu powinien być w stanie konwertować z ciągu, który jest używany dla atrybutów lub tekstu inicjującego w znaczniku, do docelowego typu lokalizacji. Aby uzyskać więcej informacji, zobacz [TypeConverters i XAML](../wpf/advanced/typeconverters-and-xaml.md).  
  
 Zamiast stosować do wszystkich wartości typu, zachowanie konwertera typów dla języka XAML można również ustalić dla konkretnej właściwości. W takim przypadku stosuje <xref:System.ComponentModel.TypeConverterAttribute> się do definicji właściwości (definicja zewnętrzna, a nie określone `get` i `set` definicje).  
  
 Zachowanie konwertera typów dla użycia XAML niestandardowego elementu członkowskiego dołączalnego można przypisać, stosując <xref:System.ComponentModel.TypeConverterAttribute> `get` metodę dostępu metody, która obsługuje użycie XAML.  
  
 Podobne do <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> istniały w .NET Framework przed istnieniem języka XAML, a model konwertera typów obsługuje inne cele. Aby można było odwołać się <xref:System.ComponentModel.TypeConverterAttribute>i używać, należy w pełni zakwalifikować się `using` do <xref:System.ComponentModel>niego lub podać instrukcję. Musisz również dołączyć zestaw systemowy do projektu.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Ciąg, który odwołuje się do odpowiedniej właściwości według nazwy.  
  
 Wskazuje Właściwość CLR klasy, która aliasuje [dyrektywę x:UID —](x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Wartość logiczna. Jeśli jest używany dla zamierzonego przeznaczenie atrybutu, powinien on zawsze być `true`określony jako.  
  
 Wskazuje, czy ten typ jest zbudowany na podstawie góry podczas tworzenia grafu obiektów XAML. Jest to zaawansowana koncepcja, która prawdopodobnie jest blisko związana z definicją modelu programowania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Dotyczy:** Klasa, właściwość, Metoda (jedyny przypadek metody języka XAML to `get` metoda dostępu, która obsługuje dołączalną składową).  
  
 **Argumentu** A <xref:System.Type> , który określa klasę obsługi serializatora wartości do użycia podczas serializacji wszystkich właściwości typu z atrybutem lub określonej właściwości atrybutu.  
  
 <xref:System.Windows.Markup.ValueSerializer>Określa klasę serializacji wartości, która wymaga więcej stanu i kontekstu niż element <xref:System.ComponentModel.TypeConverter> . <xref:System.Windows.Markup.ValueSerializer>można skojarzyć z dołączalną składową, stosując <xref:System.Windows.Markup.ValueSerializerAttribute> atrybut metody statycznej `get` akcesora dla dołączalnego elementu członkowskiego. Serializacja wartości jest również stosowana dla wyliczeń, interfejsów i struktur, ale nie dla delegatów.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Dotyczy:** Klasa, w odniesieniu do typów kolekcji, które powinny obsługiwać zawartość mieszaną, gdzie biały znak wokół elementów obiektu może być znaczący dla reprezentacji interfejsu użytkownika.  
  
 **Argumentu** Brak.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>wskazuje, że typ kolekcji ma być przetwarzany jako biały odstęp przez procesor XAML, który ma wpływ na konstrukcję węzłów wartości strumienia węzła XAML w kolekcji. Aby uzyskać więcej informacji, zobacz [Przetwarzanie białych miejsc w języku XAML](whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Dotyczy:** Klasa, właściwość.  
  
 **Argumentu** Obsługuje dwa typy formularzy do przypisania jako ciągi lub typy jako <xref:System.Type>. Zobacz <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Wskazuje, że Klasa lub właściwość ma odroczone użycie obciążenia dla języka XAML (takie jak zachowanie szablonu) i raportuje klasę, która umożliwia odciążanie i typ zawartości.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Nadaje nazwę wywołania zwrotnego.  
  
 Wskazuje, że Klasa może użyć rozszerzenia znaczników, aby podać wartość dla jednej lub większej liczby jej właściwości i odwołuje się do programu obsługi, który powinien wywołać moduł zapisujący XAML przed wykonaniem operacji ustawiania rozszerzenia znacznika dla dowolnej właściwości klasy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Nadaje nazwę wywołania zwrotnego.  
  
 Wskazuje, że Klasa może użyć konwertera typów, aby podać wartość jednej lub więcej jej właściwości i odwołuje się do programu obsługi, który powinien wywołać moduł zapisujący XAML przed wykonaniem operacji zestawu konwertera typów dla dowolnej właściwości klasy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Dotyczy:** Class  
  
 **Argumentu** Ciąg określający nazwę właściwości, która ma być aliasem `xml:lang` w typie z atrybutem.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>raportuje właściwość typu przypisanego do dyrektywy XML `lang` . Właściwość nie musi być typu <xref:System.String>, ale musi być możliwa do przypisania z ciągu (można to osiągnąć przez skojarzenie konwertera typów z typem właściwości lub określoną właściwością). Właściwość musi mieć wartość Read/Write.  
  
 Scenariusz mapowania `xml:lang` polega na tym, że model obiektowy środowiska uruchomieniowego ma dostęp do informacji o języku XML określony bez przetwarzania za pomocą XMLDOM.  
  
 Definicja dziedziczy do wszystkich typów pochodnych, które można przypisać do typu definiującego. Możesz przesłonić definicję określonego typu pochodnego, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> się do określonego typu pochodnego, chociaż jest to typowy scenariusz.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atrybuty CLR związane z XAML na poziomie zestawu  
 W poniższych sekcjach opisano atrybuty dotyczące języka XAML, które nie są stosowane do definicji typów lub elementów członkowskich, ale są stosowane do zestawów. Te atrybuty są istotne dla ogólnego celu zdefiniowania biblioteki zawierającej typy niestandardowe do użycia w języku XAML. Niektóre atrybuty niekoniecznie wpływają bezpośrednio na strumień węzłów XAML, ale są one przesyłane w strumieniu węzła, aby inni klienci mogli używać. Odbiorcy informacji obejmują środowiska projektowe lub procesy serializacji, które wymagają informacji o przestrzeni nazw XAML i skojarzonych informacji o prefiksie. Kontekst schematu XAML (w tym domyślne usługi .NET Framework XAML) również używa tych informacji.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumentu**  
  
- Ciąg określający identyfikator przestrzeni nazw XAML do uwzględnienia.  
  
- Ciąg określający identyfikator przestrzeni nazw XAML, który może uwzględnienia przestrzeń nazw XAML z poprzedniego argumentu.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Określa, że przestrzeń nazw XAML może być subsumed przez inną przestrzeń nazw XAML. Typowo, subsuming przestrzeń nazw XAML jest wskazana w wcześniej zdefiniowanym <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta technika może służyć do obsługi wersji słownika XAML w bibliotece i w celu zapewnienia zgodności z wcześniej zdefiniowanym znacznikiem w porównaniu ze starszymi wersjami słownika.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumentu**  
  
- Ciąg określający identyfikator przestrzeni nazw XAML do zdefiniowania.  
  
- Ciąg określający nazwę przestrzeni nazw CLR. Przestrzeń nazw CLR powinna definiować typy publiczne w zestawie, a co najmniej jeden typ przestrzeni nazw CLR powinien być przeznaczony do użycia XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Określa mapowanie dla poszczególnych zestawów między przestrzenią nazw XAML i przestrzenią nazw CLR, która jest następnie używana do rozpoznawania typów przez moduł zapisujący obiektów XAML lub kontekst schematu XAML.  
  
 Do zestawu można <xref:System.Windows.Markup.XmlnsDefinitionAttribute> zastosować więcej niż jeden element. Można to zrobić z dowolną kombinacją następujących przyczyn:  
  
- Projekt biblioteki zawiera wiele przestrzeni nazw środowiska CLR dla logicznej organizacji dostępu do interfejsu API czasu wykonywania; Jednak wszystkie typy w tych przestrzeniach nazw mają być używane do użycia w języku XAML przez odwołanie do tej samej przestrzeni nazw XAML. W takim przypadku należy zastosować kilka <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atrybutów przy użyciu tej samej <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartości, ale różne <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> wartości. Jest to szczególnie przydatne, jeśli definiujesz mapowania dla przestrzeni nazw XAML, która jest używana przez platformę lub aplikację jako domyślną przestrzeń nazw XAML we wspólnym użyciu.  
  
- Projekt biblioteki zawiera wiele przestrzeni nazw środowiska CLR i ma być rozbudowana przestrzeń nazw języka XAML między użyciem typów w tych przestrzeniach nazw środowiska CLR.  
  
- Zdefiniuj przestrzeń nazw CLR w zestawie i chcesz, aby była ona dostępna za pomocą więcej niż jednej przestrzeni nazw XAML. Ten scenariusz występuje, gdy obsługujesz wiele Słownictw z tą samą bazą kodu.  
  
- Obsługę języka XAML definiuje się w co najmniej jednym obszarze nazw środowiska CLR. Dla tych <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartości powinna być `http://schemas.microsoft.com/winfx/2006/xaml`wartość.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Dokumentacja referencyjna:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumentu**  
  
- Ciąg określający identyfikator przestrzeni nazw XAML.  
  
- Ciąg określający Zalecany prefiks.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Określa Zalecany prefiks do użycia w przestrzeni nazw XAML. Prefiks jest przydatny podczas pisania elementów i atrybutów w pliku XAML, który jest serializowany przez .NET Framework usług <xref:System.Xaml.XamlXmlWriter>XAML, lub gdy biblioteka języka XAML współdziała z środowiskiem projektowym, które ma funkcje edycji XAML.  
  
 Do zestawu można <xref:System.Windows.Markup.XmlnsPrefixAttribute> zastosować więcej niż jeden element. Można to zrobić z dowolną kombinacją następujących przyczyn:  
  
- Zestaw definiuje typy dla więcej niż jednej przestrzeni nazw XAML. W takim przypadku należy zdefiniować różne wartości prefiksu dla każdej przestrzeni nazw XAML.  
  
- Obsługujesz wiele słownictwa i używasz różnych prefiksów dla każdego słownictwa i przestrzeni nazw XAML.  
  
- Obsługę języka XAML definiuje się w zestawie i masz <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dla. `http://schemas.microsoft.com/winfx/2006/xaml` W takim przypadku zazwyczaj należy podwyższyć poziom prefiksu `x`.  
  
> [!NOTE]
> .NET Framework usługi XAML definiują również atrybut <xref:System.Windows.Markup.RootNamespaceAttribute>związany z XAML. Ten atrybut jest atrybutem poziomu zestawu na potrzeby obsługi systemu projektu i nie jest przeznaczony dla typów niestandardowych XAML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Attribute>
- [Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML](defining-custom-types-for-use-with-net-framework-xaml-services.md)
