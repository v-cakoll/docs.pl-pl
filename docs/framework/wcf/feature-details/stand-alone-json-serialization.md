---
title: Autonomiczna Serializacja kodu JSON przy użyciu Klasa DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 5561cddb22a02fdae9f792b1d1ec71d01c4fc916
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600909"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Autonomiczna Serializacja kodu JSON przy użyciu Klasa DataContractJsonSerializer

> [!NOTE]
> Ten artykuł ma informacje o programie <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . W przypadku większości scenariuszy obejmujących serializację i deserializacja kodu JSON zalecamy używanie interfejsów API w [przestrzeni nazw System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) to format danych przeznaczony specjalnie do użycia przez kod JavaScript uruchomiony na stronach sieci Web w przeglądarce. Jest to domyślny format danych używany przez usługi ASP.NET AJAX utworzone w Windows Communication Foundation (WCF).

Ten format może być również używany podczas tworzenia usług AJAX bez integrowania z ASP.NET — w tym przypadku XML jest wartością domyślną, ale można wybrać kod JSON.

Na koniec Jeśli wymagana jest obsługa JSON, ale nie jest tworzona usługa AJAX, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> można bezpośrednio serializować obiekty .NET do danych JSON i deserializować takie dane do wystąpień typów .NET. Aby dowiedzieć się, jak to zrobić, zobacz [How to: serializacji i deserializacji danych JSON](how-to-serialize-and-deserialize-json-data.md).

Podczas pracy z notacją JSON obsługiwane są te same typy .NET, z kilkoma wyjątkami, które są obsługiwane przez program <xref:System.Runtime.Serialization.DataContractSerializer> . Aby zapoznać się z listą obsługiwanych typów, zobacz [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md). Obejmuje to większość typów pierwotnych, większość tablic i typów kolekcji, a także typy złożone używające <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> .

## <a name="mapping-net-types-to-json-types"></a>Mapowanie typów .NET na typy JSON

W poniższej tabeli przedstawiono zgodność między typami .NET a typami JSON/JavaScript, które są mapowane przy użyciu procedur serializacji i deserializacji.

|Typy .NET|JSON/JavaScript|Uwagi|
|----------------|----------------------|-----------|
|Wszystkie typy liczbowe, na przykład <xref:System.Int32> <xref:System.Decimal> lub<xref:System.Double>|Liczba|Wartości specjalne, takie `Double.NaN` jak `Double.PositiveInfinity` i, `Double.NegativeInfinity` nie są obsługiwane i powodują nieprawidłowe dane JSON.|
|<xref:System.Enum>|Liczba|Zobacz sekcję "wyliczenia i kod JSON" w dalszej części tego tematu.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Format tych typów w formacie JSON jest taki sam jak w kodzie XML (zasadniczo wartość TimeSpan w formacie czasu trwania ISO 8601, identyfikator GUID w formacie "12345678-ABCD-ABCD-ABCD-1234567890AB" i identyfikator URI w postaci ciągu naturalnego, jak " http://www.example.com "). Aby uzyskać szczegółowe informacje, zobacz temat [Informacje o schemacie kontraktu danych](data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|Format jest "Name: Namespace" (wszystkie przed pierwszym dwukropkiem jest nazwą). Brak nazwy lub przestrzeni nazw. Jeśli nie ma przestrzeni nazw, można również pominąć ten dwukropek.|
|<xref:System.Array>typu<xref:System.Byte>|Tablica liczb|Każda liczba reprezentuje wartość jednego bajtu.|
|<xref:System.DateTime>|DateTime lub String|Zobacz daty/godziny i kod JSON w dalszej części tego tematu.|
|<xref:System.DateTimeOffset>|Typ złożony|Zobacz daty/godziny i kod JSON w dalszej części tego tematu.|
|Typy XML i ADO.NET ( <xref:System.Xml.XmlElement> ,<br /><br /> <xref:System.Xml.Linq.XElement>. Tablice <xref:System.Xml.XmlNode> ,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Zobacz sekcję Typy XML i kod JSON w tym temacie.|
|<xref:System.DBNull>|Pusty typ złożony|--|
|Kolekcje, słowniki i tablice|Tablica|Zapoznaj się z sekcją kolekcje, słowniki i tablice w tym temacie.|
|Typy złożone (z <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.SerializableAttribute> zastosowaniem lub)|Typ złożony|Elementy członkowskie danych stają się elementami członkowskimi typu złożonego JavaScript.|
|Typy złożone implementujące <xref:System.Runtime.Serialization.ISerializable> interfejs)|Typ złożony|Analogicznie jak w przypadku innych typów złożonych, ale niektóre <xref:System.Runtime.Serialization.ISerializable> typy nie są obsługiwane — zobacz część obsługa ISerializable w sekcji Informacje zaawansowane w tym temacie.|
|`Null`wartość dowolnego typu|Null|Typy wartości null są również obsługiwane i mapowane na notację JSON w taki sam sposób, jak typy wartości niedopuszczające wartości null.|

### <a name="enumerations-and-json"></a>Wyliczenia i JSON

Wartości elementu członkowskiego wyliczenia są traktowane jako liczby w formacie JSON, które różnią się od sposobu, w jaki są traktowane jako nazwy elementów członkowskich. Aby uzyskać więcej informacji na temat traktowania kontraktu danych, zobacz [typy wyliczeniowe w kontraktach danych](enumeration-types-in-data-contracts.md).

- Na przykład jeśli masz `public enum Color {red, green, blue, yellow, pink}` , serializacja `yellow` generuje liczbę 3, a nie ciąg "żółty".

- Wszystkie `enum` elementy członkowskie są serializowane. <xref:System.Runtime.Serialization.EnumMemberAttribute>I <xref:System.NonSerializedAttribute> atrybuty są ignorowane, jeśli są używane.

- Istnieje możliwość deserializacji nieistniejącej `enum` wartości — na przykład wartość 87 można deserializować do poprzedniego wyliczenia koloru, nawet jeśli nie zdefiniowano odpowiedniej nazwy koloru.

- Flagi `enum` nie są specjalne i są traktowane jako inne `enum` .

### <a name="datestimes-and-json"></a>Daty/godziny i kod JSON

Format JSON nie obsługuje bezpośrednio dat i godzin. Są one jednak bardzo często używane i ASP.NET AJAX zapewnia specjalną pomoc techniczną dla tych typów. W przypadku korzystania z serwerów proxy ASP.NET AJAX, <xref:System.DateTime> Typ w programie .NET w pełni odpowiada `DateTime` typowi w języku JavaScript.

- Gdy nie korzystasz z ASP.NET, <xref:System.DateTime> Typ jest reprezentowany w formacie JSON jako ciąg z formatem specjalnym, który opisano w sekcji Informacje zaawansowane w tym temacie.

- <xref:System.DateTimeOffset>jest reprezentowany w formacie JSON jako typ złożony: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes`Element członkowski jest przesunięty do czasu lokalnego od czasu uniwersalnego Greenwich (GMT), nazywany także uniwersalnym czasem koordynowanym (UTC), skojarzony z lokalizacją interesującego zdarzenia. `dateTime`Element członkowski reprezentuje wystąpienie w czasie, kiedy wystąpił przedmiot zainteresowania (ponownie, `DateTime` w języku JavaScript, gdy ASP.NET AJAX jest używany i ciąg, gdy nie jest). W przypadku serializacji `dateTime` element członkowski jest zawsze serializowany w GMT. Tak więc, w przypadku opisu 3:00 czasu ostatniego, `dateTime` ma składnik czasu 8:00 am i `offsetMinutes` są 300 (minus 300 min lub 5 godzin od GMT).

  > [!NOTE]
  > <xref:System.DateTime>i <xref:System.DateTimeOffset> obiekty, podczas serializacji do formatu JSON, zachowują tylko informacje o dokładności milisekund. Wartości podmilisekundy (mikro/nanosekunds) są tracone podczas serializacji.

### <a name="xml-types-and-json"></a>Typy XML i JSON

Typy XML stają się ciągami JSON.

- Na przykład jeśli element członkowski danych "q" typu XElement zawiera \<abc/> , kod JSON to {"q": " \<abc/> "}.

- Istnieją pewne specjalne reguły określające sposób zawijania kodu XML — Aby uzyskać więcej informacji, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

- Jeśli używasz ASP.NET AJAX i nie chcesz używać ciągów w języku JavaScript, ale zamiast tego chcesz użyć modelu XML DOM, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> Właściwość na XML <xref:System.ServiceModel.Web.WebGetAttribute> lub właściwość na <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> XML w obiekcie <xref:System.ServiceModel.Web.WebInvokeAttribute> .

### <a name="collections-dictionaries-and-arrays"></a>Kolekcje, słowniki i tablice

Wszystkie kolekcje, słowniki i tablice są reprezentowane w formacie JSON jako tablice.

- Każde dostosowanie, które używa elementu, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> jest ignorowane w reprezentacji JSON.

- Słowniki nie są sposobem pracy bezpośrednio z formatem JSON. Słownik \<string,object> może nie być obsługiwany w ten sam sposób w programie WCF zgodnie z oczekiwaniami w przypadku pracy z innymi technologiami JSON. Na przykład, jeśli "ABC" jest mapowany na "XYZ" i "def" jest mapowany do 42 w słowniku, reprezentacja JSON nie jest {"ABC": "XYZ", "def": 42}, ale jest [{"Key": "ABC", "value": "XYZ"}, {"Key": "def", "value": 42}].

- Jeśli chcesz, aby bezpośrednio korzystać z kodu JSON (dostęp do kluczy i wartości, bez wstępnego definiowania niesztywnego kontraktu), masz kilka opcji:

  - Rozważ użycie przykładowej [serializacji JSON (AJAX)](../samples/weakly-typed-json-serialization-sample.md) .

  - Rozważ użycie <xref:System.Runtime.Serialization.ISerializable> konstruktorów interfejsu i deserializacji — te dwa mechanizmy umożliwiają dostęp do par klucz/wartość JSON na potrzeby serializacji i deserializacji, ale nie działają w scenariuszach częściowej relacji zaufania.

  - Należy rozważyć pracę z [mapowaniem między JSON i XML,](mapping-between-json-and-xml.md) a nie przy użyciu serializatora.

  - *Polimorfizm* w kontekście serializacji odwołuje się do możliwości serializacji typu pochodnego, w którym oczekiwany jest jego typ podstawowy. Istnieją specjalne reguły specyficzne dla JSON, które umożliwiają selektywne Używanie kolekcji, gdy na przykład przypiszesz kolekcję do <xref:System.Object> . Ten problem jest bardziej szczegółowo omówiony w sekcji Informacje zaawansowane w dalszej części tego tematu.

## <a name="additional-details"></a>Dodatkowe szczegóły

### <a name="order-of-data-members"></a>Kolejność elementów członkowskich danych

Kolejność elementów członkowskich danych nie jest ważna podczas korzystania z formatu JSON. W odróżnieniu od tego, nawet jeśli <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> jest ustawiona, dane JSON nadal można deserializować w dowolnej kolejności.

### <a name="json-types"></a>Typy JSON

Typ JSON nie musi być zgodny z poprzednią tabelą podczas deserializacji. Na przykład zwykle jest `Int` mapowany na numer JSON, ale można go również pomyślnie zdeserializować z ciągu JSON, o ile ten ciąg zawiera prawidłową liczbę. Oznacza to, że oba {"q": 42} i {"q": "42"} są prawidłowe, jeśli istnieje `Int` element członkowski danych o nazwie "q".

### <a name="polymorphism"></a>Polimorfizm

Serializacja polimorficzna składa się z możliwości serializacji typu pochodnego, w którym oczekiwany jest jego typ podstawowy. Jest to obsługiwane w przypadku serializacji JSON przez WCF, która jest porównywalna z sposobem obsługi serializacji XML. Można na przykład serializować `MyDerivedType` miejsce, gdzie `MyBaseType` jest oczekiwany, lub serializować, `Int` gdzie `Object` jest oczekiwany.

Informacje o typie mogą zostać utracone podczas deserializacji typu pochodnego, jeśli jest oczekiwany typ podstawowy, chyba że jest deserializowany typ złożony. Na przykład jeśli <xref:System.Uri> jest serializowany, gdzie jest <xref:System.Object> oczekiwany, jego wynikiem jest ciąg JSON. Jeśli ten ciąg jest następnie deserializowany z powrotem do <xref:System.Object> , <xref:System.String> zwracany jest program .NET. Deserializator nie wie, że ciąg był początkowo typu <xref:System.Uri> . Ogólnie rzecz biorąc, w oczekiwany <xref:System.Object> sposób wszystkie ciągi JSON są deserializowane jako ciągi .NET, a wszystkie tablice JSON używane do serializacji kolekcji, słowników i tablic programu .NET są deserializowane jako .NET <xref:System.Array> typu <xref:System.Object> , niezależnie od tego, jaki jest rzeczywisty oryginalny typ. Wartość logiczna JSON jest mapowana na platformę .NET <xref:System.Boolean> . Jednak w przypadku, gdy oczekiwane jest <xref:System.Object> , numery JSON są deserializowane jako .NET <xref:System.Int32> <xref:System.Decimal> lub <xref:System.Double> , w przypadku których typ najbardziej odpowiedni jest automatycznie wybierany.

Podczas deserializacji do typu interfejsu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializacji jako obiekt zadeklarowany typ.

Podczas pracy z własnymi typami podstawowymi i pochodnymi <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.ServiceModel.ServiceKnownTypeAttribute> zwykle wymagane jest zastosowanie lub równoważnego mechanizmu. Na przykład jeśli masz operację, która ma `Animal` wartość zwracaną, a faktycznie zwróci wystąpienie `Cat` (pochodzące od `Animal` ), należy zastosować <xref:System.Runtime.Serialization.KnownTypeAttribute> , do `Animal` typu lub <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operacji i określić `Cat` Typ w tych atrybutach. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](data-contract-known-types.md).

Aby uzyskać szczegółowe informacje o sposobie działania serializacji polimorficznej i omówieniu niektórych ograniczeń, które muszą być przestrzegane podczas korzystania z niej, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

### <a name="versioning"></a>Przechowywanie wersji

Funkcje obsługi wersji kontraktu danych, w tym <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs, są w pełni obsługiwane w formacie JSON. Ponadto w większości przypadków można zdeserializować typu w jednym formacie (na przykład XML), a następnie serializować go do innego formatu (na przykład JSON) i nadal zachować dane w <xref:System.Runtime.Serialization.IExtensibleDataObject> . Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](forward-compatible-data-contracts.md). Pamiętaj, że format JSON jest nieuporządkowany, więc wszelkie informacje o porządku zostaną utracone. Ponadto kod JSON nie obsługuje wielu par klucz/wartość o tej samej nazwie klucza. Na koniec wszystkie operacje <xref:System.Runtime.Serialization.IExtensibleDataObject> są z natury polimorficzne — jest to typ pochodny przypisany do <xref:System.Object> , typ podstawowy dla wszystkich typów.

## <a name="json-in-urls"></a>KOD JSON w adresach URL

W przypadku korzystania z punktów końcowych ASP.NET AJAX z czasownikiem HTTP GET (przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu) parametry przychodzące są wyświetlane w adresie URL żądania, a nie w treści komunikatu. KOD JSON jest obsługiwany nawet w adresie URL żądania, więc jeśli masz operację, która przyjmuje `Int` nazwę "number" i `Person` typ złożony o nazwie "p", adres URL może być podobny do następującego adresu URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Jeśli używasz kontrolki Menedżera skryptów AJAX ASP.NET i serwera proxy do wywoływania usługi, ten adres URL jest generowany automatycznie przez serwer proxy i nie jest widoczny. Nie można używać kodu JSON w adresach URL w punktach końcowych non-ASP.NET AJAX.

## <a name="advanced-information"></a>Informacje zaawansowane

### <a name="iserializable-support"></a>Obsługa ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Obsługiwane i nieobsługiwane typy ISerializable

Ogólnie rzecz biorąc, typy implementujące <xref:System.Runtime.Serialization.ISerializable> interfejs są w pełni obsługiwane podczas serializacji/deserializacji JSON. Jednak niektóre z tych typów (w tym niektóre typy .NET Framework) są implementowane w taki sposób, że aspekty serializacji specyficzne dla JSON powodują, że nie będą poprawnie deserializacji:

- W przypadku <xref:System.Runtime.Serialization.ISerializable> , typ poszczególnych elementów członkowskich danych nigdy nie jest znany z góry. Prowadzi to do sytuacji polimorficznej podobnej do deserializacji typów do obiektu. Jak wspomniano wcześniej, może to prowadzić do utraty informacji o typie w formacie JSON. Na przykład typ, który `enum` wykonuje serializacji w jego <xref:System.Runtime.Serialization.ISerializable> implementacji i próbuje zdeserializować bezpośrednio do obiektu `enum` (bez odpowiednich rzutowania) kończy się niepowodzeniem, ponieważ `enum` jest serializowany przy użyciu liczb w notacji JSON i liczbie JSON deserializacji do wbudowanych typów liczbowych .NET (Int32, decimal lub Double). Dlatego, że liczba użyta jako `enum` wartość zostanie utracona.

- <xref:System.Runtime.Serialization.ISerializable>Typ, który zależy od określonej kolejności deserializacji w konstruktorze deserializacji, może również niepowodzeniem deserializować niektórych danych JSON, ponieważ większość serializatorów JSON nie gwarantuje żadnej konkretnej kolejności.

#### <a name="factory-types"></a>Typy fabryk

Mimo że <xref:System.Runtime.Serialization.IObjectReference> interfejs jest obsługiwany w formacie JSON w ogólności, wszystkie typy, które wymagają funkcji "typ fabryki" (zwracając wystąpienie innego typu <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> niż typ implementujący interfejs) nie są obsługiwane.

### <a name="datetime-wire-format"></a>Format przewodu DateTime

<xref:System.DateTime>wartości są wyświetlane jako ciągi JSON w postaci "/Date (700000 + 0500)/", gdzie pierwsza liczba (700000 w podanym przykładzie) to liczba milisekund w strefie czasowej GMT, regularna (oszczędność nieletnia) od północy, 1 stycznia 1970. Liczba może być ujemna, aby reprezentować wcześniejszy czas. Część, która składa się z "+ 0500" w przykładzie, jest opcjonalna i wskazuje, że czas jest <xref:System.DateTimeKind.Local> typu, który jest, należy przekonwertować na lokalną strefę czasową podczas deserializacji. Jeśli jest nieobecny, czas jest deserializowany jako <xref:System.DateTimeKind.Utc> . Rzeczywista liczba ("0500" w tym przykładzie) i jej znak (+ lub-) są ignorowane.

Podczas serializacji <xref:System.DateTime> <xref:System.DateTimeKind.Local> i <xref:System.DateTimeKind.Unspecified> godziny są zapisywane z przesunięciem i <xref:System.DateTimeKind.Utc> zapisywane bez.

Kod JavaScript klienta ASP.NET AJAX automatycznie konwertuje takie ciągi na wystąpienia JavaScript `DateTime` . Jeśli istnieją inne ciągi o podobnym formularzu, który nie jest typem w programie <xref:System.DateTime> .NET, są one również konwertowane.

Konwersja odbywa się tylko wtedy, gdy znaki "/" są wyprowadzane (to oznacza, że kod JSON wygląda podobnie jak " \\ /Date (700000 + 0500) \\ /"). z tego powodu koder JSON usługi WCF (włączony przez <xref:System.ServiceModel.WebHttpBinding> ) zawsze wyprowadza znak "/".

### <a name="xml-in-json-strings"></a>XML w ciągach JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement>jest serializowany jako, bez zawijania. Na przykład element członkowski danych "x" typu <xref:System.Xml.XmlElement> , który zawiera, \<abc/> jest reprezentowany w następujący sposób:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Tablice elementów XmlNode

<xref:System.Array>obiekty typu <xref:System.Xml.XmlNode> są opakowane w elemencie o nazwie ArrayOfXmlNode w przestrzeni nazw standardowego kontraktu danych dla tego typu. Jeśli "x" jest tablicą zawierającą węzeł atrybutu "N" w przestrzeni nazw "NS", która zawiera "wartość" i pusty węzeł elementu "M", reprezentacja jest następująca.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atrybuty w pustej przestrzeni nazw na początku tablic XmlNode (przed innymi elementami) nie są obsługiwane.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable, w tym XElement i DataSet

<xref:System.Runtime.Serialization.ISerializable>typy dzielą się na "typy zawartości", "typy zestawów danych" i "typy elementów". Aby zapoznać się z definicjami tych typów, zobacz [Typy XML i ADO.NET w kontraktach danych](xml-and-ado-net-types-in-data-contracts.md).

Typy "Content" i "DataSet" są serializowane podobnie jak <xref:System.Array> obiekty <xref:System.Xml.XmlNode> omówione w poprzedniej sekcji. Są one opakowane w element, którego nazwa i przestrzeń nazw odpowiadają nazwie kontraktu danych i przestrzeni nazw danego typu.

Typy "element", takie jak <xref:System.Xml.Linq.XElement> są serializowane w postaci, podobnie jak <xref:System.Xml.XmlElement> wcześniej omówione w tym temacie.

### <a name="polymorphism"></a>Polimorfizm

#### <a name="preserving-type-information"></a>Zachowanie informacji o typie

Jak wspomniano wcześniej, polimorfizm jest obsługiwany w formacie JSON z pewnymi ograniczeniami. Język JavaScript jest nieprawidłowym typem języka i tożsamość typu nie jest zazwyczaj problemem. Jednak w przypadku korzystania z formatu JSON do komunikacji między systemem o jednoznacznie określonym typie (.NET) a niejednoznacznie określonym systemem (JavaScript) warto zachować tożsamość typu. Na przykład typy z nazwami kontraktu danych "Square" i "Circle" pochodzą od typu z nazwą kontraktu danych "Shape". Jeśli "okrąg" jest wysyłany z platformy .NET do języka JavaScript i później jest zwracany do metody .NET, która oczekuje "Shape", jest to przydatne w przypadku strony .NET, aby wiedzieć, że dany obiekt był pierwotnie "Circle" — w przeciwnym razie wszelkie informacje specyficzne dla typu pochodnego (na przykład "promień" elementu członkowskiego danych "Circle") mogą zostać utracone.

Aby zachować tożsamość typu, podczas serializowania typów złożonych do notacji JSON można dodać "wskazówkę typu", a Deserializator rozpoznaje wskazówkę i odpowiednio działa. "Wskazówka dotycząca typu" to para klucza/wartości JSON z nazwą klucza " \_ \_ Type" (dwa podkreślenia, po których następuje słowo "Type"). Wartość jest ciągiem JSON o postaci "DataContractName: DataContractNamespace" (wszystkie elementy do pierwszego dwukropka to nazwa). Przy użyciu wcześniejszego przykładu "okrąg" można serializować w następujący sposób.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Wskazówki dotyczące typu są bardzo podobne do `xsi:type` atrybutu zdefiniowanego w standardzie wystąpienia schematu XML i używane podczas serializacji/deserializacji XML.

Elementy członkowskie danych o nazwie " \_ \_ Type" są zabronione z powodu potencjalnego konfliktu ze wskazówką typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmniejszanie rozmiaru wskazówek typu

Aby zmniejszyć rozmiar wiadomości JSON, domyślny prefiks przestrzeni nazw kontraktu danych ( `http://schemas.datacontract.org/2004/07/` ) jest zastępowany znakiem "#". (Aby zmienić odwracalnie, używana jest reguła ucieczki: Jeśli przestrzeń nazw zaczyna się od znaków "#" lub " \\ ", są one dołączane z dodatkowym \\ znakiem ""). W takim przypadku, jeśli "Circle" jest typem w przestrzeni nazw .NET "MojaApl. Shapes", jego domyślna przestrzeń nazw kontraktu danych to `http://schemas.datacontract.org/2004/07/MyApp` . Kształty i reprezentacja JSON są następujące.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Obie wartości (#MyApp. Shapes) i pełne ( <http://schemas.datacontract.org/2004/07/MyApp.Shapes> ) są zrozumiałe dla deserializacji.

#### <a name="type-hint-position-in-json-objects"></a>Położenie wskazówki typu w obiektach JSON

Należy zauważyć, że Wskazówka typu musi występować najpierw w reprezentacji JSON. Jest to jedyny przypadek, w którym kolejność par klucz/wartość jest ważna w przetwarzaniu JSON. Na przykład następujące polecenie nie jest prawidłowym sposobem określenia wskazówki typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Obie <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> strony KLIENCKIE WCF i ASP.NET AJAX zawsze emitują wskazówkę typu.

#### <a name="type-hints-apply-only-to-complex-types"></a>Wskazówki dotyczące typów dotyczą tylko typów złożonych

Nie istnieje sposób emisji wskazówki typu dla typów niezłożonych. Na przykład jeśli operacja ma <xref:System.Object> zwracany typ, ale zwraca okrąg, reprezentacja JSON może być jak pokazana wcześniej, a informacje o typie są zachowywane. Jeśli jednak zostanie zwrócony identyfikator URI, reprezentacja JSON jest ciągiem i faktem, że ciąg używany do reprezentowania identyfikatora URI zostanie utracony. Dotyczy to nie tylko typów pierwotnych, ale również do kolekcji i tablic.

#### <a name="when-are-type-hints-emitted"></a>Kiedy są emitowane wskazówki typu

Wskazówki dotyczące typów mogą znacząco zwiększyć rozmiar wiadomości (jednym ze sposobów na ograniczenie tego problemu jest użycie krótszych przestrzeni nazw kontraktu danych, jeśli jest to możliwe). W związku z tym następujące reguły określają, czy wskazówki dotyczące typu są emitowane:

- Gdy jest używany ASP.NET AJAX, wskazówki typu są zawsze emitowane w miarę możliwości, nawet jeśli nie istnieje przypisanie podstawowe/pochodne — na przykład nawet wtedy, gdy okrąg jest przypisany do okręgu. (Jest to wymagane, aby w pełni włączyć proces wywoływania z słabego typu środowiska JSON w środowisku platformy .NET o jednoznacznie określonym typie bez zaskakujące utraty informacji).

- Gdy korzystasz z usług AJAX z integracją ASP.NET, wskazówki dotyczące typów są emitowane tylko wtedy, gdy istnieje przypisanie podstawowe/pochodne — to jest generowane, gdy okrąg jest przypisywany do kształtu lub, <xref:System.Object> ale nie w przypadku przypisywania do okręgu. Zapewnia to minimalne informacje wymagane do poprawnego zaimplementowania klienta języka JavaScript, a tym samym zwiększenie wydajności, ale nie chroni przed utratą informacji typu w niewłaściwie zaprojektowanych klientach. Należy unikać przypisywania podstawowego/pochodnego całkowicie na serwerze, jeśli chcesz uniknąć tego problemu na kliencie.

- Przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> typu, `alwaysEmitTypeInformation` parametr konstruktora umożliwia wybranie między poprzednimi trybami, z wartością domyślną " `false` " (tylko wskazówki dotyczące typu są emitowane w razie potrzeby).

#### <a name="duplicate-data-member-names"></a>Zduplikowane nazwy składowych danych

Informacje o typie pochodnym znajdują się w tym samym obiekcie JSON wraz z podstawowymi informacjami o typie i mogą występować w dowolnej kolejności. Na przykład `Shape` może być reprezentowane w następujący sposób.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Okrąg może być reprezentowany w następujący sposób.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Jeśli typ podstawowy `Shape` zawiera również składową danych o nazwie " `radius` ", prowadzi to do kolizji obu serializacji (ponieważ obiekty JSON nie mogą mieć powtarzających się nazw kluczy) i deserializacji (ponieważ nie jest jasne, czy "RADIUS" odwołuje się do `Shape.radius` lub `Circle.radius` ). W związku z tym, Chociaż pojęcie "Ukrywanie właściwości" (składowe danych o tej samej nazwie w klasach opartych i pochodnych) nie jest ogólnie zalecane w klasach kontraktów danych, jest w rzeczywistości zabronione w przypadku JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm i typy IXmlSerializable

<xref:System.Xml.Serialization.IXmlSerializable>typy mogą być przypisywane do siebie, tak jak zwykle, o ile wymagania znanych typów są spełnione, zgodnie z typowymi regułami kontraktu danych. Jednak Serializacja <xref:System.Xml.Serialization.IXmlSerializable> typu zamiast <xref:System.Object> wyników powoduje utratę informacji o typie, ponieważ wynik jest ciągiem JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm i niektóre typy interfejsów

Nie można serializować typu kolekcji lub typu, który implementuje, <xref:System.Xml.Serialization.IXmlSerializable> gdzie nie jest oczekiwany typ niebędący kolekcją <xref:System.Xml.Serialization.IXmlSerializable> (z wyjątkiem for <xref:System.Object> ). Na przykład niestandardowy interfejs o nazwie `IMyInterface` i typ implementujący `MyType` oba <xref:System.Collections.Generic.IEnumerable%601> typy `int` i `IMyInterface` . Powrót `MyType` z operacji, której typem zwracanym jest zabronione `IMyInterface` . Jest to spowodowane tym, że `MyType` musi być serializowana jako tablica JSON i wymaga wskazówki dotyczącej typu oraz jak określono przed włączeniem wskazówki typu z tablicami tylko z typami złożonymi.

#### <a name="known-types-and-configuration"></a>Znane typy i konfiguracja

Wszystkie znane mechanizmy typu używane przez <xref:System.Runtime.Serialization.DataContractSerializer> są również obsługiwane w taki sam sposób przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . Obie serializatory odczytują ten sam element konfiguracji [\<dataContractSerializer>](../../configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) w programie w [\<system.runtime.serialization>](../../configure-apps/file-schema/wcf/system-runtime-serialization.md) celu odnajdywania znanych typów dodanych za pomocą pliku konfiguracji.

#### <a name="collections-assigned-to-object"></a>Kolekcje przypisane do obiektu

Kolekcje przypisane do obiektu są serializowane, jeśli są kolekcjami, które implementują <xref:System.Collections.Generic.IEnumerable%601> : tablicę JSON z każdym wpisem, który ma wskazówkę typu, jeśli jest to typ złożony. Na przykład, <xref:System.Collections.Generic.List%601> typu `Shape` przypisanego do <xref:System.Object> wygląda jak poniżej.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

W przypadku deserializacji z powrotem do <xref:System.Object> :

- `Shape`musi znajdować się na liście znanych typów. Posiadanie <xref:System.Collections.Generic.List%601> typu `Shape` w znanych typach nie ma żadnego wpływu. Należy pamiętać, że `Shape` w tym przypadku nie trzeba dodawać do znanych typów podczas serializacji — jest to wykonywane automatycznie.

- Kolekcja jest deserializowana jako typ zawierający <xref:System.Array> <xref:System.Object> `Shape` wystąpienia.

#### <a name="derived-collections-assigned-to-base-collections"></a>Kolekcje pochodne przypisane do kolekcji podstawowych

Gdy kolekcja pochodna jest przypisana do kolekcji podstawowej, kolekcja jest zwykle serializowana tak, jakby była kolekcją typu podstawowego. Jeśli jednak typ elementu kolekcji pochodnej nie może zostać przypisany do typu elementu kolekcji podstawowej, zostanie zgłoszony wyjątek.

#### <a name="type-hints-and-dictionaries"></a>Wskazówki i słowniki typów

Po przypisaniu słownika do programu <xref:System.Object> każdy wpis klucza i wartości w słowniku jest traktowany jak jeśli został przypisany do <xref:System.Object> i pobiera wskazówkę typu.

Podczas serializowania typów słowników ustawienie nie ma wpływ na obiekt JSON, który zawiera elementy członkowskie "Key" i "value", `alwaysEmitTypeInformation` i zawiera wskazówkę dotyczącą typu tylko wtedy, gdy wymagają tego zasady.

### <a name="valid-json-key-names"></a>Prawidłowe nazwy kluczy JSON

Serializator XML dekoduje nazwy kluczy, które nie są prawidłowymi nazwami XML. Na przykład element członkowski danych o nazwie "123" będzie miał zakodowaną nazwę, taką jak " \_ x0031 \_ \_ x0032 \_ \_ x0033", \_ ponieważ "123" jest nieprawidłową nazwą elementu XML (zaczyna się od cyfry). Podobna sytuacja może wystąpić w przypadku niektórych międzynarodowych zestawów znaków, które nie są prawidłowe w nazwach XML. Aby uzyskać wyjaśnienie tego wpływu XML na przetwarzanie JSON, zobacz [Mapowanie między danymi JSON i XML](mapping-between-json-and-xml.md).

## <a name="see-also"></a>Zobacz też

- [Obsługa formatu JSON i innych formatów transferowania danych](support-for-json-and-other-data-transfer-formats.md)
