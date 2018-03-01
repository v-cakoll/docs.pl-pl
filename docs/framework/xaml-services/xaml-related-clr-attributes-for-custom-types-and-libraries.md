---
title: "Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 25aac1d4478279561cbcdda6c1cf912c3c3b2cde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek
W tym temacie opisano typowe atrybutów środowiska uruchomieniowego (języka wspólnego CLR) języka, które są zdefiniowane przez usług .NET Framework XAML. Omówiono także inne atrybuty CLR zdefiniowanych w programie .NET Framework mających scenariusza związane z XAML dla aplikacji do zestawów lub typów. Przypisywanie zestawy, typów albo elementów członkowskich z tymi atrybutami CLR dostarcza dane systemowe typu XAML powiązane z typami. Informacje są dostępne wszelkie odbiorcy XAML, który korzysta z usług .NET Framework XAML do przetwarzania strumień węzłów XAML bezpośrednio lub za pośrednictwem dedykowanej czytników XAML i zapisywania XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atrybuty CLR związane z XAML dla niestandardowych typów i członków niestandardowych  
 Przy użyciu atrybutów CLR zakłada, że używasz ogólną CLR do definiowania typów sieci, w przeciwnym razie takie atrybuty nie są dostępne. Jeśli używasz środowiska CLR do definiowania typu kopii domyślny kontekst schematu XAML używane przez autorów .NET Framework XAML Services XAML mogą odczytywać autorstwa CLR przez odbicie przed zestawy kopii.  
  
 W poniższych sekcjach opisano związane z XAML atrybuty stosowane do niestandardowych typów lub niestandardowych elementów członkowskich. Każdy atrybut CLR komunikuje się informacje, które są istotne dla systemu typu XAML. W ścieżce obciążenia oparte na atrybutach informacje pomagają albo czytnika XAML tworzą nieprawidłowy strumień węzłów XAML lub pomaga twórcę XAML tworzy prawidłowy obiekt Wykres. W polu Zapisz ścieżkę, informacje oparte na atrybutach albo pomaga czytnika XAML tworzą nieprawidłowy strumień węzłów XAML, który reconstitutes informacje o systemie typu XAML; lub deklaruje wskazówki serializacji lub wymagania dotyczące zapisywania pliku XAML lub innym klientom XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Dotyczy:** klasę, właściwości lub `get` elementów członkowskich akcesora, które obsługują właściwości możliwe do dołączenia.  
  
 **Argumenty:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute>Wskazuje, że właściwość lub wszystkie właściwości, które przyjmują oparte na atrybutach typu powinny być rozumiane w obszarze koncepcji — właściwość otoczenia w języku XAML. Pojęcie otoczenia odnosi się ustalenie, jak procesory XAML właścicieli typu elementów członkowskich. Właściwością otoczenia jest właściwością, gdy wartość jest powinny być dostępne w kontekście analizatora, podczas tworzenia wykresu obiektu, ale w przypadku wyszukiwania typowych elementu członkowskiego typu została zawieszona natychmiastowego węzłów XAML ustawić tworzona.  
  
 Pojęcie otoczenia można zastosować do możliwe do dołączenia elementy członkowskie, które nie są reprezentowane jako właściwości pod względem sposobu definiuje autorstwa CLR <xref:System.AttributeTargets>. Użycie metody autorstwa powinny być stosowane tylko w odniesieniu `get` akcesor obsługujące użycia możliwe do dołączenia dla języka XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** ciąg określający nazwę właściwości, pasujący do argumentu jednego konstruktora.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Określa można zainicjować za pomocą składni z systemem innym niż domyślny konstruktor obiektu i że określona nazwa właściwości dostarcza informacji konstrukcji. Te informacje są głównie do serializacji w języku XAML. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>Atrybut ContentPropertyAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** ciąg określający nazwę elementu członkowskiego typu atrybutami.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>Wskazuje, że właściwość o nazwie przez argument powinien służyć jako właściwość content XAML dla tego typu. Dziedziczy definicji właściwości zawartości XAML na wszystkich typach pochodnych, które są można przypisać do typu definiującego. Definicja na określony typ pochodny można zastąpić, stosując <xref:System.Windows.Markup.ContentPropertyAttribute> na określonym typu pochodnego.  
  
 Dla właściwości, która służy jako właściwość zawartości XAML element właściwości znakowanie dla właściwości można pominąć użycie XAML. Zwykle możesz określić właściwości zawartości XAML, które wspierają prostsze znaczników XAML dla modeli zawartości i zawierania. Ponieważ tylko jeden element członkowski może zostać wyznaczony jako właściwość zawartości XAML, masz czasami decyzji projektowych dokonanie wskazujące, którzy kontenera kilka właściwości typu powinien zostać wyznaczony jako wartość właściwości zawartości XAML. Inne właściwości kontenera musi być używany z jawną właściwość elementów.  
  
 Strumień węzłów XAML, właściwości zawartości XAML nadal do tworzenia `StartMember` i `EndMember` węzłów, przy użyciu nazwy właściwości <xref:System.Xaml.XamlMember>. Aby określić, czy element członkowski jest właściwością zawartości XAML, należy sprawdzić <xref:System.Xaml.XamlType> wartość z `StartObject` Umieść i uzyskiwanie wartości <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Dotyczy:** klasy, w szczególności typy kolekcji.  
  
 **Argumenty:** A <xref:System.Type> , który określa typ do użycia jako typ zawartości otoki obcego zawartości.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Określa jeden lub więcej typów w typie skojarzonej kolekcji, która będzie służyć do zakodowania zawartości obcego. Zawartość obcego odwołuje się do przypadków, gdy ograniczenia system typu na typ właściwości zawartości nie należy przechwytywać wszystkich możliwych przypadkach zawartości obsługujących spowoduje użycie języka XAML dla jego typu. Na przykład XAML obsługę zawartości określonego typu może obsługiwać ciągów w ogólnej metodzie jednoznacznie <xref:System.Collections.ObjectModel.Collection%601>. Otoki zawartości są przydatne w przypadku migrowania istniejących konwencje znaczników do koncepcji można przypisać wartości do kolekcji, takie jak migracja związanych z tekstem modeli zawartości określonych w języku XAML.  
  
 Aby określić więcej niż jeden typ otoki zawartości, zastosuj atrybut wiele razy.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Dotyczy:** właściwości  
  
 **Argumenty:** ciąg określający nazwę elementu Członkowskiego innego typu atrybutami.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>Wskazuje, że właściwość oparte na atrybutach zależy od wartości innej właściwości. Stosowanie tego atrybutu do definicji właściwości zapewnia najpierw przetworzony zależne właściwości na piśmie obiektu języka XAML. Sposoby użycia <xref:System.Windows.Markup.DependsOnAttribute> Określ wyjątkowych przypadkach właściwości na typy, których określonej kolejności analizowania musi występować do utworzenia prawidłowego obiektu.  
  
 Można zastosować wiele <xref:System.Windows.Markup.DependsOnAttribute> przypadków definicji właściwości.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Dotyczy:** klasy, która ma być <xref:System.Windows.Markup.MarkupExtension> typu pochodnego.  
  
 **Argumenty:** A <xref:System.Type> określająca najbardziej precyzyjne oczekiwać jako `ProvideValue` wynik oparte na atrybutach <xref:System.Windows.Markup.MarkupExtension>.  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** obsługuje dwa rodzaje autorstwa:  
  
-   Ciąg określający nazwę właściwości w typie oparte na atrybutach.  
  
-   Ciąg określający nazwę właściwości oraz a <xref:System.Type> dla typu, który definiuje właściwość o nazwie. Ten formularz służy do określania dołączalny element członkowski jako właściwość namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Określa właściwość, która zawiera wartość namescope XAML dla klasy oparte na atrybutach. Oczekuje, że właściwość namescope XAML odwołuje się do obiektu, który implementuje <xref:System.Windows.Markup.INameScope> i przechowuje rzeczywiste namescope XAML, jego magazynu i jego zachowania.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** ciąg określający nazwę właściwości Nazwa środowiska wykonawczego oparte na atrybutach typu.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>Raporty właściwości oparte na atrybutach typu, który jest mapowany na XAML [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md). Wartość właściwości musi być typu <xref:System.String> i musi być do odczytu/zapisu.  
  
 Definicja dziedziczy na wszystkich typach pochodnych, które są można przypisać do typu definiującego. Definicja na określony typ pochodny można zastąpić, stosując <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> na określonym typu pochodnego.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Dotyczy:** typów  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>jest stosowany do określonych typów, które mogą być wyświetlane jako elementy podrzędne w zawartości znaczących spacji (zawartość posiadanych przez kolekcję, która ma <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>dotyczy głównie Zapisz ścieżkę, ale jest dostępna w systemie typów języka XAML w ścieżce obciążenia, sprawdzając <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Dokumentacji:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Dotyczy:** klasę, właściwości, metody (tylko XAML prawidłowe metody wielkość liter jest `get` dostępu, który obsługuje dołączalny element członkowski).  
  
 **Argumenty:** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>w języku XAML kontekstu odwołuje się do niestandardowego <xref:System.ComponentModel.TypeConverter>. To <xref:System.ComponentModel.TypeConverter> zapewnia zachowanie konwersji typu niestandardowych typów lub elementy członkowskie tego typu.  
  
 Należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do typu, odwołanie do implementacji konwertera typu. Można zdefiniować klasy, struktury lub interfejsy typy konwerterów dla XAML. Nie trzeba podać konwersja typu dla wyliczenia, konwersja włączono natywnie.  
  
 Sieci typu konwertera powinno być możliwe do przekonwertowania z ciągiem, który jest używany dla atrybutów lub inicjowania tekstu w znaczniku, do danego przeznaczenia typu. Aby uzyskać więcej informacji, zobacz [TypeConverters i języka XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Zamiast zastosowanie do wszystkich wartości typu, zachowanie konwerter typu dla XAML może być ustalona na określoną właściwość. W takim przypadku należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do definicji property (zewnętrznej definicji, nie konkretnym `get` i `set` definicje).  
  
 Zachowanie konwerter typu dla XAML użycia niestandardowego dołączalny element członkowski można przypisać stosując <xref:System.ComponentModel.TypeConverterAttribute> do `get` dostępu metody, obsługujący użycie języka XAML.  
  
 Podobnie jak <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> były dostępne w programie .NET Framework, przed istnienie XAML i modelu konwertera typu obsłużone innych celów. Aby można było odwołać i użyj <xref:System.ComponentModel.TypeConverterAttribute>, muszą w pełni Kwalifikuj lub podaj `using` instrukcji dla <xref:System.ComponentModel>. W projekcie, musi również obejmować zestawu systemowego.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** ciąg, który odwołuje się do odpowiednich właściwości według nazwy.  
  
 Wskazuje, że aliasy właściwość CLR klasy [x: Uid — dyrektywa](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** wartość logiczną. Jeśli używana do jego przeznaczenie, to należy zawsze należy określać jako `true`.  
  
 Wskazuje, czy ten typ jest wbudowana góra dół podczas tworzenia wykresu obiektu języka XAML. Jest to zaawansowane pojęcia, które jest prawdopodobnie zbliżona do definicji modelu programowania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Dotyczy:** klasę, właściwości, metody (tylko XAML prawidłowe metody wielkość liter jest `get` dostępu, który obsługuje dołączalny element członkowski).  
  
 **Argumenty:** A <xref:System.Type> , który określa klasę pomocy technicznej wartość serializator używany podczas serializowania wszystkie właściwości typu atrybutami lub konkretnym przypisanych właściwości.  
  
 <xref:System.Windows.Markup.ValueSerializer>Określa klasę serializacji wartości, która wymaga więcej stanu i kontekst niż <xref:System.ComponentModel.TypeConverter> jest. <xref:System.Windows.Markup.ValueSerializer>może być skojarzony z dołączalny element członkowski, stosując <xref:System.Windows.Markup.ValueSerializerAttribute> atrybutu statycznych `get` metodę dostępu dla dołączalny element członkowski. Wartość serializacji mają też zastosowanie do wyliczenia, interfejsów i struktury, ale nie dla obiektów delegowanych.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Dotyczy:** klasy, w szczególności typy kolekcji, które powinny udostępniać zawartość mieszaną, gdzie biały znak wokół elementów obiektu może być istotne dla reprezentacja interfejsu użytkownika.  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>Wskazuje, czy typ kolekcji powinna zostać przetworzona jako znaczące światła procesora XAML, które wpływa konstrukcji strumień węzłów XAML wartość węzły w kolekcji. Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Dotyczy:** klasę, właściwości.  
  
 **Argumenty:** autorstwa obsługuje dwa typy jako ciągi formularzy lub typy jako <xref:System.Type>. Zobacz <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Wskazuje, że klasa lub właściwość ma użycie odłożonego ładowania dla XAML (np. zachowanie szablonu) i zgłasza klasę, która umożliwia zachowanie odkładanie i jej typ docelowy/zawartości.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** nazwy wywołania zwrotnego.  
  
 Wskazuje, że można użyć rozszerzenia znaczników Podaj wartość dla co najmniej jednego z jego właściwości klasy i odwołuje się do obsługi, która Edytor XAML powinny wywoływać przed wykonaniem operacji set rozszerzenia znacznika, w dowolnej właściwości klasy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** nazwy wywołania zwrotnego.  
  
 Wskazuje, że można użyć konwertera typów podać wartość dla co najmniej jednego z jego właściwości klasy i odwołuje się do obsługi, która Edytor XAML powinny wywoływać przed wykonaniem typu konwertera operację na dowolną właściwość klasy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Dotyczy:** — klasa  
  
 **Argumenty:** ciąg określający nazwę właściwości do aliasu `xml:lang` oparte na atrybutach typu.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>Raporty właściwość typu oparte na atrybutach, który jest mapowany na XML `lang` dyrektywy. Właściwość nie jest zawsze typu <xref:System.String>, ale musi istnieć możliwość przypisania z ciągu (można to osiągnąć, kojarząc konwertera typów, z typem właściwości lub z konkretną właściwością). Wartość właściwości musi być odczytu/zapisu.  
  
 Scenariusz mapowania `xml:lang` jest tak, aby modelu obiektów czasu wykonywania miał dostęp do informacji o kodzie XML określono język bez przetwarzania w szczególności z XMLDOM.  
  
 Definicja dziedziczy na wszystkich typach pochodnych, które są można przypisać do typu definiującego. Definicja na określony typ pochodny można zastąpić, stosując <xref:System.Windows.Markup.XmlLangPropertyAttribute> na określonym pochodnych typu, ale jest rzadko scenariusza.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atrybuty CLR związane z XAML na poziomie zestawu  
 W poniższych sekcjach opisano atrybuty związane z XAML, które nie są stosowane do typów lub definicji elementu członkowskiego, ale zamiast tego są stosowane do zestawów. Te atrybuty są przydatne do ogólnym celem Definiowanie biblioteki, która zawiera niestandardowe typy do użycia w języku XAML. Niektóre atrybuty nie zawsze wpływ strumień węzłów XAML bezpośrednio, ale są przekazywane w strumieniu węzłów dla innych klientów do użycia. Konsumenci informacje obejmują środowisk projektowania lub serializacji procesy, które wymagają informacji dotyczących przestrzeni nazw XAML i skojarzone z nimi informacje prefiks. XAML kontekst schematu (w tym domyślnego usług .NET Framework XAML) również używa tych informacji.  
  
### <a name="xmlnscompatiblewithattribute"></a>Atrybut XmlnsCompatibleWithAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumenty:**  
  
-   Ciąg określający identyfikator przestrzeni nazw XAML do uwzględnienia.  
  
-   Ciąg określający identyfikator przestrzeni nazw XAML, który można uwzględnienia przestrzeni nazw XAML z poprzednich argumentu.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Określa, że przestrzeń nazw XAML może włączony przez inną przestrzeń nazw XAML. Zwykle wskazuje subsuming przestrzeni nazw XAML w uprzednio zdefiniowanej <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta technika może być używany do przechowywania wersji słownika XAML w bibliotece, a także aby był zgodny z wcześniej zdefiniowanego znaczników względem starszych wersji słownika.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumenty:**  
  
-   Ciąg określający identyfikator przestrzeni nazw XAML, aby zdefiniować.  
  
-   Ciąg, który określa przestrzeń nazw CLR. Przestrzeń nazw środowiska CLR powinna definiować typy publiczne, w tym zestawem, i co najmniej jeden z typów przestrzeń nazw CLR powinien być przeznaczone do użycia XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Określa mapowanie na podstawie na zestawie między przestrzeni nazw XAML i przestrzeń nazw środowiska CLR, która jest następnie używany do rozpoznawania typu przez moduł zapisujący obiektu języka XAML i kontekst schematu XAML.  
  
 Więcej niż jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> może odnosić się do zestawu. Może to zrobić dla dowolne z następujących powodów:  
  
-   Projekt biblioteki zawiera wiele nazw CLR dla organizacji logicznego dostępu do interfejsu API środowiska wykonawczego; ma jednak wszystkie typy w tych obszarach nazw może być XAML — używany przez odwołanie do tego samego obszaru nazw XAML. W takim przypadku należy zastosować kilka <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atrybuty korzystającej z tego samego <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartość, ale o innej <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> wartości. Jest to szczególnie przydatne, jeśli definiujesz mapowania do przestrzeni nazw XAML, która sieci framework lub aplikację jako domyślna przestrzeń nazw XAML w typowych użycia.  
  
-   Projekt biblioteki zawiera wiele nazw CLR i chcesz oddzielenie użycia typów w tych obszarach nazw CLR zamierzonego przestrzeni nazw XAML.  
  
-   Definiuje przestrzeń nazw CLR w zestawie, i ma być dostępna przez więcej niż jedną przestrzeń nazw XAML. W tym scenariuszu występuje, gdy wiele vocabularies z tej samej bazy kodu są obsługiwane.  
  
-   Jeden lub kilka przestrzeni nazw CLR definiowania obsługę języka XAML. W tym przypadku <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> wartość powinna być `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Dokumentacji:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumenty:**  
  
-   Ciąg określający identyfikator przestrzeni nazw XAML.  
  
-   Ciąg określający zalecaną prefiks.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Określa zalecaną prefiksu dla przestrzeni nazw XAML. Prefiks jest przydatne podczas zapisywania elementów i atrybutów w pliku XAML, który jest serializowany przez usług .NET Framework XAML <xref:System.Xaml.XamlXmlWriter>, lub gdy biblioteki wykonawcze języka XAML wchodzi w interakcję w środowisku projektowania, który ma XAML funkcje edytowania.  
  
 Więcej niż jeden <xref:System.Windows.Markup.XmlnsPrefixAttribute> może odnosić się do zestawu. Może to zrobić dla dowolne z następujących powodów:  
  
-   Używanemu zestawowi definiuje typy dla więcej niż jedną przestrzeń nazw XAML. W takim przypadku należy zdefiniować prefiksu różnych wartości dla każdej przestrzeni nazw XAML.  
  
-   Wiele vocabularies są obsługiwane i używać różnych prefiksów dla każdego słownictwa i przestrzeni nazw XAML.  
  
-   Definiowanie obsługi języka XAML w zestawie i mieć <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dla `http://schemas.microsoft.com/winfx/2006/xaml`. W takim przypadku można zwykle wspierała prefiks `x`.  
  
> [!NOTE]
>  Usługi XAML .NET framework również definiuje atrybut związane z XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Ten atrybut jest atrybut poziomu zestawu obsługi systemu projektu i nie jest istotne dla niestandardowych typów XAML.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute>  
 [Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
