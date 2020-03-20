---
title: Samodzielna serializacja JSON przy użyciu funkcji DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 36945f2d42f22ef3aa4f27bcbe403466f124a279
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184420"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Samodzielna serializacja JSON przy użyciu funkcji DataContractJsonSerializer

> [!NOTE]
> Ten artykuł <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>dotyczy tematu . W przypadku większości scenariuszy, które obejmują serializację i deserializację JSON, zalecamy interfejsy API w [obszarze nazw System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) to format danych, który jest specjalnie zaprojektowany do użycia przez kod JavaScript uruchomiony na stronach internetowych wewnątrz przeglądarki. Jest to domyślny format danych używany przez usługi ASP.NET AJAX utworzone w Programie Komunikacji systemu Windows (WCF).

Ten format może być również używany podczas tworzenia usług AJAX bez integracji z ASP.NET — w tym przypadku XML jest domyślny, ale można wybrać JSON.

Na koniec jeśli potrzebujesz obsługi JSON, ale nie są <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tworzenie usługi AJAX, umożliwia bezpośrednio serializacji obiektów .NET do danych JSON i deserializacji takich danych z powrotem do wystąpień typów .NET. Aby uzyskać opis sposobu wykonywania tej pracy, zobacz [Jak: Serialize i Deserialize JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Podczas pracy z JSON obsługiwane są te same typy .NET, z kilkoma <xref:System.Runtime.Serialization.DataContractSerializer>wyjątkami, które są obsługiwane przez program . Aby uzyskać listę obsługiwanych typów, zobacz [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Obejmuje to większość typów pierwotnych, większość typów tablic i kolekcji, a także typy złożone, które używają <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapowanie typów .NET do typów JSON

W poniższej tabeli przedstawiono zgodność między typami .NET i typami JSON/JavaScript podczas mapowania przez procedury serializacji i deserializacji.

|Typy .NET|JSON/JavaScript|Uwagi|
|----------------|----------------------|-----------|
|Wszystkie typy liczbowe, na przykład <xref:System.Int32>, <xref:System.Decimal> lub<xref:System.Double>|Liczba|Wartości specjalne, `Double.NaN` `Double.PositiveInfinity` takie `Double.NegativeInfinity` jak , i nie są obsługiwane i spowodować nieprawidłowe JSON.|
|<xref:System.Enum>|Liczba|Zobacz "Wyliczenia i JSON" w dalszej części tego tematu.|
|<xref:System.Boolean>|Wartość logiczna|--|
|<xref:System.String>, <xref:System.Char>|Ciąg|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Ciąg|Format tych typów w JSON jest taki sam jak w XML (zasadniczo TimeSpan w formacie ISO 8601 Czas trwania, GUID w "12345678-ABCD-ABCD-ABCD-1234567890AB" format i URI w naturalnej formie ciągu jak "http://www.example.com"). Aby uzyskać dokładne informacje, zobacz [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Ciąg|Format to "name:namespace" (wszystko przed pierwszym dwukropkiem to nazwa). Może brakować nazwy lub obszaru nazw. Jeśli nie ma obszaru nazw, dwukropek można również pominąć.|
|<xref:System.Array>typu<xref:System.Byte>|Tablica liczb|Każda liczba reprezentuje wartość jednego bajtu.|
|<xref:System.DateTime>|DateTime lub String|Zobacz daty/godziny i JSON w dalszej części tego tematu.|
|<xref:System.DateTimeOffset>|Typ złożony|Zobacz daty/godziny i JSON w dalszej części tego tematu.|
|Typy XML i<xref:System.Xml.XmlElement>ADO.NET ( ,<br /><br /> <xref:System.Xml.Linq.XElement>. Tablice <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Ciąg|Zobacz sekcję Typy XML i JSON w tym temacie.|
|<xref:System.DBNull>|Pusty typ kompleksu|--|
|Kolekcje, słowniki i tablice|Tablica|Zobacz kolekcje, słowniki i tablice sekcji tego tematu.|
|Typy złożone <xref:System.Runtime.Serialization.DataContractAttribute> (z lub <xref:System.SerializableAttribute> stosowane)|Typ złożony|Elementy członkowskie danych stają się członkami typu złożonego JavaScript.|
|Typy złożone <xref:System.Runtime.Serialization.ISerializable> implementujące interfejs)|Typ złożony|Tak samo jak inne <xref:System.Runtime.Serialization.ISerializable> typy złożone, ale niektóre typy nie są obsługiwane — zobacz część pomocy technicznej iserializable sekcji Informacje zaawansowane w tym temacie.|
|`Null`wartość dla każdego typu|Null|Typy nullable są również obsługiwane i mapować do JSON w taki sam sposób jak typy nienastępne do wartości null.|

### <a name="enumerations-and-json"></a>Wyliczenia i JSON

Wartości członkowskie wyliczenia są traktowane jako liczby w JSON, który różni się od sposobu ich traktowania w kontraktach danych, gdzie są one uwzględniane jako nazwy elementów członkowskich. Aby uzyskać więcej informacji na temat leczenia kontraktów danych, zobacz [Typy wyliczenia w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Na przykład, jeśli `public enum Color {red, green, blue, yellow, pink}`masz `yellow` , serializacji tworzy liczbę 3, a nie ciąg "żółty".

- Wszyscy `enum` członkowie są serializable. Atrybuty <xref:System.Runtime.Serialization.EnumMemberAttribute> <xref:System.NonSerializedAttribute> i są ignorowane, jeśli są używane.

- Istnieje możliwość deserializacji nieistniejącej `enum` wartości — na przykład wartość 87 można zdesywić do poprzedniego wyliczenia color, nawet jeśli nie zdefiniowano odpowiedniej nazwy koloru.

- Flaga `enum` nie jest wyjątkowa i jest `enum`traktowana tak samo jak każda inna .

### <a name="datestimes-and-json"></a>Daty/godziny i JSON

Format JSON nie obsługuje bezpośrednio dat i godzin. Jednak są one bardzo powszechnie używane i ASP.NET AJAX zapewnia specjalną obsługę dla tych typów. Podczas korzystania z serwerów proxy ASP.NET <xref:System.DateTime> AJAX, typ w .NET w pełni odpowiada typowi `DateTime` w języku JavaScript.

- Jeśli nie używa ASP.NET, <xref:System.DateTime> typ jest reprezentowany w JSON jako ciąg o specjalnym formacie, który jest opisany w sekcji Informacje zaawansowane w tym temacie.

- <xref:System.DateTimeOffset>jest reprezentowana w JSON jako typ złożony: {"DateTime":dateTime,"OffsetMinutes":offsetMinutes}. Element `offsetMinutes` członkowski jest przesunięcie czasu lokalnego z Greenwich Mean Time (GMT), również teraz określane jako Skoordynowany czas uniwersalny (UTC), związane z lokalizacją zdarzenia zainteresowania. Element `dateTime` członkowski reprezentuje wystąpienie w czasie, gdy wystąpiło `DateTime` zdarzenie zainteresowania (ponownie staje się w javascript, gdy ASP.NET AJAX jest w użyciu i ciąg, gdy nie jest). Podczas serializacji `dateTime` element członkowski jest zawsze serializowany w programie GMT. Tak więc, jeśli opisujące 3:00 `dateTime` czasu nowojorskiego, ma składnik czasu `offsetMinutes` 8:00 AM i są 300 (minus 300 minut lub 5 godzin od GMT).

  > [!NOTE]
  > <xref:System.DateTime>i <xref:System.DateTimeOffset> obiektów, gdy serializowane do JSON, tylko zachować informacje do dokładności milisekundy. Wartości poniżej milisekundy (mikro/nanosekund) są tracone podczas serializacji.

### <a name="xml-types-and-json"></a>Typy XML i JSON

Typy XML stają się ciągami JSON.

- Na przykład jeśli element członkowski danych "q" \<typu XElement zawiera abc/>, JSON to {"q":"\<abc/>"}.

- Istnieje kilka specjalnych reguł, które określają, jak XML jest zawijany — aby uzyskać więcej informacji, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

- Jeśli używasz ASP.NET AJAX i nie chcesz używać ciągów w javascript, ale chcesz XML <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> DOM zamiast, <xref:System.ServiceModel.Web.WebGetAttribute> ustaw <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwość XML <xref:System.ServiceModel.Web.WebInvokeAttribute>lub właściwość XML na .

### <a name="collections-dictionaries-and-arrays"></a>Kolekcje, słowniki i tablice

Wszystkie kolekcje, słowniki i tablice są reprezentowane w JSON jako tablice.

- Wszelkie dostosowania, które <xref:System.Runtime.Serialization.CollectionDataContractAttribute> używa jest ignorowana w reprezentacji JSON.

- Słowniki nie są sposobem na bezpośrednią pracę z JSON. Ciąg\<słownika, obiekt> nie mogą być obsługiwane w taki sam sposób w WCF, zgodnie z oczekiwaniami od pracy z innymi technologiami JSON. Na przykład, jeśli "abc" jest mapowane na "xyz" i "def" jest mapowany na 42 w słowniku, reprezentacja JSON nie jest {"abc":"xyz","def":42}, ale jest [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}] zamiast.

- Jeśli chcesz pracować bezpośrednio z JSON (dynamicznie uzyskując dostęp do kluczy i wartości, bez wstępnego zdefiniowania sztywnego kontraktu), masz kilka opcji:

  - Należy rozważyć użycie słabo wpisanego modułu [serializacji JSON (AJAX).](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md)

  - Należy rozważyć <xref:System.Runtime.Serialization.ISerializable> użycie konstruktorów interfejsu i deserializacji — te dwa mechanizmy umożliwiają dostęp do par klucz/wartość JSON na serializacji i deserializacji odpowiednio, ale nie działają w scenariuszach częściowego zaufania.

  - Należy rozważyć pracę z [mapowania między JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) zamiast przy użyciu serializatora.

  - *Polimorfizm* w kontekście serializacji odnosi się do możliwości serializacji typu pochodnego, w którym oczekuje się jego typu podstawowego. Istnieją specjalne reguły specyficzne dla JSON podczas korzystania z kolekcji polimorficznie, <xref:System.Object>gdy na przykład przypisywanie kolekcji do pliku . Ten problem jest bardziej szczegółowo omówione w sekcji Informacje zaawansowane w dalszej części tego tematu.

## <a name="additional-details"></a>Dodatkowe szczegóły

### <a name="order-of-data-members"></a>Kolejność członków danych

Kolejność elementów członkowskich danych nie jest ważne podczas korzystania z JSON. W szczególności, <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> nawet jeśli jest ustawiona, dane JSON nadal mogą być deserializowane w dowolnej kolejności.

### <a name="json-types"></a>Typy JSON

Typ JSON nie musi odpowiadać poprzedniej tabeli na deserializacji. Na przykład `Int` zwykle mapuje do numeru JSON, ale można również pomyślnie zdesializowany z ciągu JSON, tak długo, jak ten ciąg zawiera prawidłową liczbę. Oznacza to, że zarówno {"q":42} i {"q":"42"} są prawidłowe, jeśli istnieje element `Int` członkowski danych o nazwie "q".

### <a name="polymorphism"></a>Polimorfizm

Serializacja polimorficzna składa się z możliwości serializacji typu pochodnego, w którym oczekuje się jego typu podstawowego. Jest to obsługiwane dla serializacji JSON przez WCF porównywalne ze sposobem serializacji XML jest obsługiwany. Na przykład `MyDerivedType` można serializować, gdzie `MyBaseType` jest `Int` `Object` oczekiwane lub serializować, gdzie jest oczekiwane.

Informacje o typie mogą zostać utracone podczas deserializacji typu pochodnego, jeśli typ podstawowy jest oczekiwany, chyba że są deserializacji typu złożonego. Na przykład <xref:System.Uri> jeśli jest <xref:System.Object> serializowane, gdzie jest oczekiwane, powoduje ciąg JSON. Jeśli ten ciąg jest następnie <xref:System.Object>deserialized <xref:System.String> z powrotem do , .NET jest zwracany. Deserializer nie wie, że ciąg był <xref:System.Uri>początkowo typu . Ogólnie rzecz biorąc, <xref:System.Object>gdy oczekuje , wszystkie ciągi JSON są deserializowane jako ciągi .NET, a wszystkie tablice JSON używane do <xref:System.Array> serializacji <xref:System.Object>kolekcji.NET, słowniki i tablice są deserializowane jako .NET typu , niezależnie od tego, jaki był rzeczywisty typ oryginalny. Logiczne mapy JSON na <xref:System.Boolean>.NET . Jednak w przypadku <xref:System.Object>oczekiwania liczby JSON są deserializowane <xref:System.Int32>jako <xref:System.Decimal> <xref:System.Double>.NET lub , gdzie najbardziej odpowiedni typ jest automatycznie pobierany.

Podczas deserializacji do typu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> interfejsu, deserializes tak, jakby zadeklarowany typ był obiektem.

Podczas pracy z własną bazą i <xref:System.Runtime.Serialization.KnownTypeAttribute>typami pochodnymi zwykle wymagane jest użycie mechanizmu <xref:System.ServiceModel.ServiceKnownTypeAttribute> lub równoważnego mechanizmu. Na przykład, jeśli masz operację, `Animal` która ma wartość zwracaną `Cat` i faktycznie `Animal`zwraca wystąpienie (pochodne z ), należy zastosować <xref:System.Runtime.Serialization.KnownTypeAttribute>, do `Animal` typu lub <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operacji i określić `Cat` typ w tych atrybutach. Aby uzyskać więcej informacji, zobacz [Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Aby uzyskać szczegółowe informacje na temat działania serializacji polimorficznej i omówienie niektórych ograniczeń, które muszą być przestrzegane podczas korzystania z niej, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

### <a name="versioning"></a>Obsługa wersji

Funkcje przechowywania wersji kontraktu <xref:System.Runtime.Serialization.IExtensibleDataObject> danych, w tym interfejs, są w pełni obsługiwane w JSON. Ponadto w większości przypadków możliwe jest deserializacja typu w jednym formacie (na przykład XML), a następnie serializowanie go w innym <xref:System.Runtime.Serialization.IExtensibleDataObject>formacie (na przykład JSON) i zachowanie danych w pliku . Aby uzyskać więcej informacji, zobacz [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Należy pamiętać, że JSON jest nieuisorowany, więc wszelkie informacje o zamówieniu są tracone. Ponadto JSON nie obsługuje wielu par klucz/wartość o tej samej nazwie klucza. Na koniec wszystkie <xref:System.Runtime.Serialization.IExtensibleDataObject> operacje na są z natury polimorficzne — to <xref:System.Object>jest ich typ pochodny są przypisane do , typ podstawowy dla wszystkich typów.

## <a name="json-in-urls"></a>JSON w adresach URL

W przypadku korzystania z ASP.NET punktów końcowych AJAX z <xref:System.ServiceModel.Web.WebGetAttribute> zleceniem HTTP GET (przy użyciu atrybutu) parametry przychodzące są wyświetlane w adresie URL żądania zamiast treści wiadomości. JSON jest obsługiwany nawet w adresie URL żądania, więc `Int` jeśli masz operację, która ma o nazwie "numer" i `Person` typ złożony o nazwie "p", adres URL może przypominać następujący adres URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Jeśli używasz ASP.NET ajax script manager kontroli i serwera proxy do wywołania usługi, ten adres URL jest automatycznie generowany przez serwer proxy i nie jest widoczny. JSON nie może być używany w adresach URL w punktach końcowych non-ASP.NET AJAX.

## <a name="advanced-information"></a>Informacje zaawansowane

### <a name="iserializable-support"></a>Pomoc techniczna iserializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Obsługiwane i nieobsługiwanych typów ISerializable

Ogólnie rzecz biorąc typy, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejs są w pełni obsługiwane podczas serializacji/deserializacji JSON. Jednak niektóre z tych typów (w tym niektóre typy .NET Framework) są implementowane w taki sposób, że aspekty serializacji specyficzne dla JSON powodują, że nie są poprawnie deserializacji:

- W <xref:System.Runtime.Serialization.ISerializable>programach , typ poszczególnych elementów członkowskich danych nigdy nie jest znany z wyprzedzeniem. Prowadzi to do sytuacji polimorficznej podobnej do deserializacji typów w obiekcie. Jak wspomniano wcześniej, może to prowadzić do utraty informacji o typie w JSON. Na przykład typ, który serializuje `enum` <xref:System.Runtime.Serialization.ISerializable> w jego implementacji i próbuje deserialize z powrotem bezpośrednio do `enum` (bez prawidłowego rzutowania) kończy się niepowodzeniem, `enum` ponieważ jest seryjny przy użyciu liczb w JSON i JSON numery deserialize do wbudowanych typów numerycznych .NET (Int32, Dziesiętne lub Double). Tak więc fakt, że liczba `enum` kiedyś wartość jest tracona.

- Typ, <xref:System.Runtime.Serialization.ISerializable> który zależy od określonej kolejności deserializacji w konstruktorze deserializacji może również nie deserializacji niektórych danych JSON, ponieważ większość serializatorów JSON nie gwarantuje żadnej określonej kolejności.

#### <a name="factory-types"></a>Typy fabryczne

Podczas <xref:System.Runtime.Serialization.IObjectReference> gdy interfejs jest obsługiwany w JSON w ogóle, wszelkie typy, które wymagają funkcji <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> "typ fabryki" (zwracając wystąpienie innego typu niż typ, który implementuje interfejs) nie są obsługiwane.

### <a name="datetime-wire-format"></a>Format przewodowy DateTime

<xref:System.DateTime>wartości są wyświetlane jako ciągi JSON w postaci "/Date(70000+0500)/", gdzie pierwszą liczbą (700000 w podanym przykładzie) jest liczba milisekund w strefie czasowej GMT, czas regularny (niezwiązany z czasem letniskowym) od północy, 1 stycznia 1970. Liczba może być ujemna do reprezentowania wcześniejszych czasów. Część, która składa się z "+0500" w przykładzie jest <xref:System.DateTimeKind.Local> opcjonalna i wskazuje, że czas jest tego rodzaju — oznacza to, że powinien zostać przekonwertowany na lokalną strefę czasową podczas deserializacji. Jeśli jest nieobecny, czas jest <xref:System.DateTimeKind.Utc>deserializowany jako . Rzeczywista liczba ("0500" w tym przykładzie) i jej znak (+ lub -) są ignorowane.

Podczas <xref:System.DateTime>serializacji <xref:System.DateTimeKind.Local> <xref:System.DateTimeKind.Unspecified> i razy są zapisywane <xref:System.DateTimeKind.Utc> z przesunięciem i jest zapisywany bez.

Kod JavaScript klienta ASP.NET AJAX automatycznie konwertuje takie ciągi na wystąpienia JavaScript. `DateTime` Jeśli istnieją inne ciągi, które mają podobny <xref:System.DateTime> formularz, które nie są typu w .NET, są one również konwertowane.

Konwersja ma miejsce tylko wtedy, gdy znaki "/" są przestarzałe (oznacza to, że JSON wygląda tak "\\/Date(700000+0500)\\/"), i z tego powodu koder JSON WCF (włączony przez <xref:System.ServiceModel.WebHttpBinding>) zawsze wymazuje znak "/".

### <a name="xml-in-json-strings"></a>XML w ciągach JSON

#### <a name="xmlelement"></a>Xmlelement

<xref:System.Xml.XmlElement>jest serializowany, jak jest, bez zawijania. Na przykład element członkowski danych <xref:System.Xml.XmlElement> "x" typu zawierającego \<abc/> jest reprezentowany w następujący sposób:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Tablice XmlNode

<xref:System.Array>obiekty typu <xref:System.Xml.XmlNode> są zawijane w element o nazwie ArrayOfXmlNode w standardowej przestrzeni nazw kontraktu danych dla tego typu. Jeśli "x" jest tablicą, która zawiera węzeł atrybutu "N" w obszarze nazw "ns", który zawiera "wartość" i pusty węzeł elementu "M", reprezentacja jest następująca.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atrybuty w pustej przestrzeni nazw na początku tablic XmlNode (przed innymi elementami) nie są obsługiwane.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>IXmlSerializable Typy, w tym XElement i DataSet

<xref:System.Runtime.Serialization.ISerializable>typy dzielą się na "typy zawartości", "Typy zestawów danych" i "typy elementów". Aby zapoznać się z definicjami tych typów, zobacz [XML i ADO.NET Typy w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Typy "Zawartość" i "DataSet" <xref:System.Array> są <xref:System.Xml.XmlNode> serializowane podobnie do obiektów omówionych w poprzedniej sekcji. Są one zawijane w elemencie, którego nazwa i obszar nazw odpowiada nazwie kontraktu danych i przestrzeni nazw danego typu.

Typy "Element", <xref:System.Xml.Linq.XElement> takie jak są serializowane, podobnie jak jest, podobnie jak <xref:System.Xml.XmlElement> wcześniej omówione w tym temacie.

### <a name="polymorphism"></a>Polimorfizm

#### <a name="preserving-type-information"></a>Zachowywanie informacji o typie

Jak wspomniano wcześniej, polimorfizm jest obsługiwany w JSON z pewnymi ograniczeniami. JavaScript jest słabo wpisanym językiem i tożsamość typu zwykle nie jest problemem. Jednak w przypadku korzystania z JSON do komunikowania się między silnie typizowanym systemem (.NET) a słabo typowanym systemem (JavaScript), przydatne jest zachowanie tożsamości typu. Na przykład typy o nazwach kontraktów danych "Kwadrat" i "Circle" pochodzą od typu o nazwie kontraktu danych "Kształt". Jeśli "Circle" jest wysyłany z platformy .NET do języka JavaScript, a później zwracany do metody .NET, która oczekuje "Shape", warto wiedzieć, że dany obiekt pierwotnie był "Circle" - w przeciwnym razie wszelkie informacje specyficzne dla typu pochodnego (na przykład , element członkowski danych "promień" w "Okręgu") może zostać utracony.

Aby zachować tożsamość typu, podczas serializacji typów złożonych do JSON można dodać "wskazówka typu", a deserializator rozpoznaje wskazówkę i działa odpowiednio. "Wskazówka typu" jest parą klucz/wartość JSON\_\_z nazwą klucza " type" (dwa podkreślenia, po których następuje słowo "type"). Wartość jest ciąg JSON formularza "DataContractName:DataContractNamespace" (wszystko do pierwszego dwukropka jest nazwą). Przy użyciu wcześniejszego przykładu "Circle" może być serializowany w następujący sposób.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Wskazówka typu jest bardzo `xsi:type` podobna do atrybutu zdefiniowanego przez standard wystąpienia schematu XML i używana podczas serializacji/deserializacji XML.

Elementy członkowskie\_\_danych o nazwie "typ" są zabronione ze względu na potencjalny konflikt z wskazówki typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmniejszenie rozmiaru wskazówek dotyczących typu

Aby zmniejszyć rozmiar komunikatów JSON, domyślny prefiks obszaru nazw kontraktu danych (`http://schemas.datacontract.org/2004/07/`) jest zastępowany znakiem "#". (Aby to zastąpienie było odwracalne, używana jest reguła ucieczki: jeśli obszar nazw\\zaczyna się od znaków "#"\\lub " , są one dołączane z dodatkowym znakiem ""). W związku z tym jeśli "Circle" jest typem w obszarze nazw .NET "MyApp.Shapes", jego domyślny obszar nazw kontraktu danych jest `http://schemas.datacontract.org/2004/07/MyApp`. Kształty i reprezentacja JSON są następujące.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Zarówno obcięty (#MyApp.Shapes) i pełnehttp://schemas.datacontract.org/2004/07/MyApp.Shapes) (nazwy są rozumiane na deserializacji.

#### <a name="type-hint-position-in-json-objects"></a>Wpisz pozycję wskazówki w obiektach JSON

Należy zauważyć, że wskazówka typu musi pojawić się jako pierwsza w reprezentacji JSON. Jest to jedyny przypadek, w którym kolejność par klucz/wartość jest ważna w przetwarzaniu JSON. Na przykład następujące nie jest prawidłowy sposób, aby określić wskazówkę typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Zarówno <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używane przez WCF i ASP.NET stron klienta AJAX zawsze najpierw emitują wskazówkę typu.

#### <a name="type-hints-apply-only-to-complex-types"></a>Wskazówki dotyczące typu dotyczą tylko typów złożonych

Nie ma sposobu, aby emitować wskazówkę typu dla typów niezpokonanych. Na przykład jeśli operacja <xref:System.Object> ma typ zwracany, ale zwraca Circle, reprezentacja JSON może być taka, jak pokazano wcześniej, a informacje o typie są zachowywane. Jednak jeśli uri jest zwracany, reprezentacja JSON jest ciągiem i fakt, że ciąg używany do reprezentowania Uri zostanie utracony. Dotyczy to nie tylko typów pierwotnych, ale także kolekcji i tablic.

#### <a name="when-are-type-hints-emitted"></a>Kiedy są emitowane wskazówki dotyczące typu

Wskazówki dotyczące typów mogą znacznie zwiększyć rozmiar wiadomości (jednym ze sposobów złagodzenia tego jest użycie krótszych obszarów nazw kontraktu danych, jeśli to możliwe). W związku z tym następujące reguły regulują, czy wskazówki dotyczące typu są emitowane:

- Podczas korzystania z ASP.NET AJAX, wskazówki dotyczące typu są zawsze emitowane, gdy jest to możliwe, nawet jeśli nie ma przypisania podstawowej/pochodnej — na przykład, nawet jeśli Circle jest przypisany do okręgu. (Jest to wymagane, aby w pełni włączyć proces wywoływania ze środowiska JSON słabo typizowane do silnie typizowanego środowiska .NET bez zaskakującej utraty informacji.)

- Podczas korzystania z usług AJAX bez integracji ASP.NET, wskazówki dotyczące typu są emitowane tylko wtedy, gdy istnieje przypisanie <xref:System.Object> podstawowe/pochodne - czyli emitowane, gdy Circle jest przypisany do kształtu lub ale nie po przypisaniu do Circle. Zapewnia to minimalne informacje wymagane do prawidłowego zaimplementowania klienta JavaScript, poprawiając w ten sposób wydajność, ale nie chroni przed utratą informacji o typie u niepoprawnie zaprojektowanych klientów. Unikaj przypisań podstawowych/pochodnych całkowicie na serwerze, jeśli chcesz uniknąć radzenia sobie z tym problemem na kliencie.

- Podczas korzystania <xref:System.Runtime.Serialization.DataContractSerializer> z `alwaysEmitTypeInformation` typu parametr konstruktora umożliwia wybór między dwoma poprzednimi`false`trybami, przy czym domyślnie jest " ( emitują tylko wskazówki dotyczące typu, gdy jest to wymagane).

#### <a name="duplicate-data-member-names"></a>Zduplikowane nazwy elementów członkowskich danych

Informacje o typie pochodnym są obecne w tym samym obiekcie JSON wraz z informacjami o typie podstawowym i mogą wystąpić w dowolnej kolejności. Na przykład `Shape` mogą być reprezentowane w następujący sposób.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Okrąg może być reprezentowany w następujący sposób.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Jeśli typ `Shape` podstawowy zawierał również element`radius`członkowski danych o nazwie " ", prowadzi to do kolizji zarówno serializacji (ponieważ obiekty JSON nie mogą mieć `Shape.radius` `Circle.radius`powtarzających się nazw kluczy), jak i deserializacji (ponieważ nie jest jasne, czy "promień" odnosi się do lub ). W związku z tym podczas gdy pojęcie "ukrywanie właściwości" (elementy członkowskie danych o tej samej nazwie na podstawie i klas pochodnych) zazwyczaj nie jest zalecane w klasach kontraktów danych, jest faktycznie zabronione w przypadku JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm i IXmlSerializable Typy

<xref:System.Xml.Serialization.IXmlSerializable>typy mogą być polimorficznie przypisane do siebie jak zwykle, tak długo, jak znane typy wymagania są spełnione, zgodnie ze zwykłymi regułami umowy danych. Jednak serializacji <xref:System.Xml.Serialization.IXmlSerializable> typu zamiast <xref:System.Object> powoduje utratę informacji o typie, ponieważ wynik jest ciąg JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm i niektóre typy interfejsów

Zabrania się serializacji typu kolekcji lub typu, <xref:System.Xml.Serialization.IXmlSerializable> który implementuje, gdzie <xref:System.Xml.Serialization.IXmlSerializable> oczekuje się <xref:System.Object>typu niezbierania, który nie jest (z wyjątkiem). Na przykład niestandardowy `IMyInterface` interfejs wywoływany i `MyType` typ, który implementuje zarówno typ, <xref:System.Collections.Generic.IEnumerable%601> `int` jak i `IMyInterface`. Zabrania się powrotu `MyType` z operacji, której `IMyInterface`typem zwrotu jest . Jest tak, ponieważ `MyType` musi być serializowany jako tablica JSON i wymaga wskazówki typu, a jak podano, zanim nie można dołączyć wskazówkę typu z tablicami, tylko ze złożonymi typami.

#### <a name="known-types-and-configuration"></a>Znane typy i konfiguracja

Wszystkie mechanizmy znanego typu <xref:System.Runtime.Serialization.DataContractSerializer> używane przez są również obsługiwane <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>w ten sam sposób przez plik . Oba serializatory odczytują ten sam element konfiguracji, [ \<dataContractSerializer>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) w [ \<>system.runtime.serialization ](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), aby odkryć znane typy dodane za pośrednictwem pliku konfiguracyjnego.

#### <a name="collections-assigned-to-object"></a>Kolekcje przypisane do obiektu

Kolekcje przypisane do Object są serializowane tak, <xref:System.Collections.Generic.IEnumerable%601>jakby były kolekcje, które implementują: tablica JSON z każdego wpisu, który ma wskazówkę typu, jeśli jest to typ złożony. Na przykład <xref:System.Collections.Generic.List%601> typ `Shape` przypisany <xref:System.Object> do wygląda następująco.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Po zdemalianiu z powrotem do: <xref:System.Object>

- `Shape`musi znajdować się na liście Znane typy. Posiadanie <xref:System.Collections.Generic.List%601> typu `Shape` w znanych typach nie ma wpływu. Należy zauważyć, że nie `Shape` trzeba dodawać do znanych typów serializacji w tym przypadku — odbywa się to automatycznie.

- Kolekcja jest deserializowane <xref:System.Array> jako <xref:System.Object> typu, `Shape` który zawiera wystąpienia.

#### <a name="derived-collections-assigned-to-base-collections"></a>Kolekcje pochodne przypisane do kolekcji podstawowych

Gdy kolekcja pochodna jest przypisana do kolekcji podstawowej, kolekcja jest zwykle serializowane tak, jakby była kolekcją typu podstawowego. Jednak jeśli typ elementu kolekcji pochodnej nie można przypisać do typu towaru kolekcji podstawowej, wyjątek.

#### <a name="type-hints-and-dictionaries"></a>Wskazówki i słowniki typu

Gdy słownik jest przypisany <xref:System.Object>do , każdy wpis Klucz i wartość w słowniku jest <xref:System.Object> traktowany tak, jakby został przypisany do i pobiera wskazówkę typu.

Podczas serializacji typów słownika, JSON obiekt, który zawiera "Key" i "Value" elementów członkowskich jest nienaruszone przez `alwaysEmitTypeInformation` ustawienie i zawiera tylko wskazówkę typu, gdy poprzednie reguły kolekcji wymagają.

### <a name="valid-json-key-names"></a>Prawidłowe nazwy kluczy JSON

Serializator XML koduje nazwy kluczy, które nie są prawidłowymi nazwami XML. Na przykład element członkowski danych o nazwie "123" miałby zakodowaną nazwę,\_\_taką jak "\_\_\_x0031 x0032 x0033\_", ponieważ "123" jest nieprawidłową nazwą elementu XML (zaczyna się od cyfry). Podobna sytuacja może wystąpić w przypadku niektórych międzynarodowych zestawów znaków nieprawidłowych w nazwach XML. Aby uzyskać wyjaśnienie tego wpływu XML na przetwarzanie JSON, zobacz [Mapowanie między JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Zobacz też

- [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
