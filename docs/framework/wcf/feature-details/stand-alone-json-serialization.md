---
title: Autonomiczna serializacja kodu JSON
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 63f40333b53bce33e4c3aafb784e038f52bc8630
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663756"
---
# <a name="stand-alone-json-serialization"></a>Autonomiczna serializacja kodu JSON

JSON (JavaScript Object Notation) jest formatem danych przeznaczone do użycia przez kod JavaScript na stronach sieci Web uruchomionych w przeglądarce. Jest to domyślny format danych używany przez usługi ASP.NET AJAX, utworzone w Windows Communication Foundation (WCF).

Ten format można również podczas tworzenie usług AJAX bez integracji z usługą ASP.NET — w tym przypadku XML jest ustawieniem domyślnym, ale można wybrać JSON.

Na koniec, jeśli wymagana jest obsługa JSON, ale są nietworzenie usługa AJAX <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> umożliwia bezpośrednio serializować obiekty platformy .NET na dane JSON i deserializować tych danych do wystąpienia typów .NET. Aby uzyskać opis jak to zrobić, zobacz [jak: Serializowanie i Deserializowanie danych JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Podczas pracy z formatu JSON, te same typy .NET są obsługiwane, z pewnymi wyjątkami, ponieważ są obsługiwane przez <xref:System.Runtime.Serialization.DataContractSerializer>. Aby uzyskać listę typów obsługiwanych zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Obejmuje to najbardziej pierwotnych typów, większość tablicy i typy kolekcji, jak również tak złożonego typy używające <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapowania typów .NET do formatu JSON typów

W poniższej tabeli przedstawiono związek między typami .NET i typy JSON/JavaScript, gdy mapowany przez procedury serializacji i deserializacji.

|Typy .NET|JSON/JavaScript|Uwagi|
|----------------|----------------------|-----------|
|Wszystkie typy liczbowe, na przykład <xref:System.Int32>, <xref:System.Decimal> lub <xref:System.Double>|Wartość liczbowa|Specjalne wartości, takich jak `Double.NaN`, `Double.PositiveInfinity` i `Double.NegativeInfinity` nie są obsługiwane i spowodować obiekt JSON jest nieprawidłowy.|
|<xref:System.Enum>|Wartość liczbowa|Zobacz "Wyliczeń i JSON" w dalszej części tego tematu.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Format tych typów w formacie JSON jest taki sam jak XML (zasadniczo przedział czasu w formacie ISO 8601 czas, identyfikator GUID w formacie "12345678-ABCD-ABCD-ABCD-1234567890AB" i identyfikatora URI w postaci ciągu fizyczne, takie jak "http://www.example.com"). Aby uzyskać dokładne informacje, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|Format jest "Nazwa: namespace" (wszystko przed pierwszym dwukropkiem nazywa się). Nazwa lub obszar nazw może być brak. Przypadku żadnej przestrzeni nazw można również pominąć dwukropkiem.|
|<xref:System.Array> tego typu <xref:System.Byte>|Tablica liczb|Każdy numer reprezentuje wartość jednego bajtu.|
|<xref:System.DateTime>|Data i godzina lub ciągu|Zobacz daty / godziny i JSON w dalszej części tego tematu.|
|<xref:System.DateTimeOffset>|Typ złożony|Zobacz daty / godziny i JSON w dalszej części tego tematu.|
|Typy XML i ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Tablice <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Zobacz sekcję typy XML i JSON w tym temacie.|
|<xref:System.DBNull>|Pusty typ złożony|--|
|Kolekcje, słowniki i tablic|Array|Zobacz sekcję kolekcje, słowniki i tablic w tym temacie.|
|Typy złożone (przy użyciu <xref:System.Runtime.Serialization.DataContractAttribute> lub <xref:System.SerializableAttribute> zastosowane)|Typ złożony|Elementy członkowskie danych stają się elementy członkowskie typu złożonego kodu JavaScript.|
|Typy złożone Implementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu)|Typ złożony|Taki sam jak inne typy złożone, ale niektóre <xref:System.Runtime.Serialization.ISerializable> typy nie są obsługiwane — zobacz temat pomocy technicznej ISerializable część sekcji Zaawansowane informacje o tym temacie.|
|`Null` wartość dla dowolnego typu|Null|Typy dopuszczające wartości zerowe są również obsługiwane i mapowanie do formatu JSON w taki sam sposób, jak typy niedopuszczające.|

### <a name="enumerations-and-json"></a>Wyliczenia i JSON

Wartości elementów członkowskich wyliczenia są traktowane jako liczby w formacie JSON, który jest inny niż jak są traktowane w kontraktach danych, w którym zostaną one dołączone jako nazwy elementów członkowskich. Aby uzyskać więcej informacji na temat przetwarzania kontraktu danych, zobacz [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Na przykład, jeśli masz `public enum Color {red, green, blue, yellow, pink}`, serializacji `yellow` generuje numer 3 i nie ciągu "yellow".

- Wszystkie `enum` elementy członkowskie są możliwe do serializacji. <xref:System.Runtime.Serialization.EnumMemberAttribute> i <xref:System.NonSerializedAttribute> atrybuty są ignorowane, jeśli używany.

- Można wykonać deserializacji nieistniejącej `enum` wartość — na przykład, wartość 87 może być zdeserializowany do poprzedniego wyliczenia Color, nawet jeśli istnieje bez odpowiedniej nazwy zdefiniowane.

- Flagi `enum` nie specjalnych i jest traktowane jako taki sam jak każdy inny `enum`.

### <a name="datestimes-and-json"></a>Daty/godziny i JSON

JSON format nie obsługuje bezpośrednio daty i godziny. Jednak bardzo często są one używane, i ASP.NET AJAX zapewnia obsługę specjalnego rodzaju. Korzystając z serwerów proxy ASP.NET AJAX, <xref:System.DateTime> typ na platformie .NET, ale w pełni odpowiada `DateTime` typ w języku JavaScript.

- Bez korzystania z platformy ASP.NET, <xref:System.DateTime> typ jest reprezentowany w formacie JSON jako ciąg znaków za pomocą specjalnych formatu, który opisano w sekcji Zaawansowane informacje o tym temacie.

- <xref:System.DateTimeOffset> jest reprezentowana w formacie JSON jako typ złożony: {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes` Element członkowski jest przesunięcie czasu lokalnego z czasu uniwersalnego Greenwich (GMT), teraz również określane jako uniwersalny czas koordynowany (UTC), skojarzona z lokalizacją zdarzenia zainteresowania. `dateTime` Elementu członkowskiego reprezentuje wystąpienie w czasie, kiedy wystąpiło zdarzenie zainteresowania (ponownie staje się `DateTime` w języku JavaScript, gdy ASP.NET AJAX jest w użyciu i ciąg, gdy nie jest). Na serializacji `dateTime` element członkowski zawsze jest serializowany w strefie czasowej GMT. Jeśli opisujące 3:00 czasu Nowy Jork, więc `dateTime` składnik czasu w 8:00:00 i `offsetMinutes` to 300 (minus 300 minut lub 5 godzin od GMT).

  > [!NOTE]
  > <xref:System.DateTime> i <xref:System.DateTimeOffset> obiektów, gdy serializować do notacji JSON, tylko zachować informacje dokładności do milisekundy. Liczone w ułamkach milisekund wartości (micro/nanosekundach) zostaną utracone podczas serializacji.

### <a name="xml-types-and-json"></a>Typy XML i JSON

Typy XML stają się ciągów JSON.

- Na przykład, jeśli element członkowski danych "q" z typu klasy XElement zawiera \<abc / >, za pomocą pliku JSON jest {"q": "\<abc / >"}.

- Istnieją pewne specjalne reguły, które Określ, jak opakowane XML — Aby uzyskać więcej informacji, zobacz sekcję zaawansowane informacje w dalszej części tego tematu.

- Jeśli używasz rozszerzeń ASP.NET AJAX i nie chcesz używać parametrów w języku JavaScript, ale zamiast tego chcesz modelu DOM języka XML, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> właściwości XML <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości XML <xref:System.ServiceModel.Web.WebInvokeAttribute>.

### <a name="collections-dictionaries-and-arrays"></a>Kolekcje, słowniki i tablice

Wszystkie kolekcje słowników i tablice są reprezentowane w formacie JSON jako tablice.

- Wszelkie dostosowania, który używa <xref:System.Runtime.Serialization.CollectionDataContractAttribute> jest ignorowana w reprezentacji JSON.

- Słowniki są nowy sposób pracy bezpośrednio z formatu JSON. Słownik\<string, object > mogą nie być obsługiwane w taki sam sposób, w programie WCF zgodnie z oczekiwaniami działanie z innymi technologiami w formacie JSON. Na przykład, jeśli "abc" jest mapowana do ciągu "xyz", "def" jest mapowana do 42 w słowniku reprezentacji JSON nie jest {"abc": "xyz", "def": 42}, ale jest [{"Key": "abc", "Wartość": "xyz"}, {"Key": "def", "Value": 42}] zamiast tego.

- Jeśli chcesz pracować z JSON bezpośrednio (Uzyskiwanie dostępu do kluczy i wartości dynamicznie bez wstępnie definiowanie kontraktu sztywne), masz kilka opcji:

  - Należy rozważyć użycie [ze słabą kontrolą typów serializacji JSON (technologia AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) próbki.

  - Należy rozważyć użycie <xref:System.Runtime.Serialization.ISerializable> interfejsu i deserializacji konstruktory — pozwala na uzyskiwanie dostępu do pary klucz/wartość JSON na serializacji i deserializacji odpowiednio te dwa mechanizmy, ale nie działają w scenariuszach częściowej relacji zaufania.

  - Rozważ współpracę z [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) zamiast serializatora.

  - *Polimorfizm* w kontekście serializacji odnosi się do możliwości, które można serializować typu pochodnego, gdy jego typ podstawowy jest oczekiwany. Istnieją specjalne reguły specyficzne dla formatu JSON przy użyciu kolekcji polymorphically, przypisując, na przykład, kolekcję, aby <xref:System.Object>. Ten problem jest dokładniej omówione w sekcji informacje o zaawansowanych w dalszej części tego tematu.

## <a name="additional-details"></a>Dodatkowe szczegóły

### <a name="order-of-data-members"></a>Kolejność elementów członkowskich danych

Kolejność elementów członkowskich danych nie jest ważna w przypadku korzystania z formatu JSON. Ściślej mówiąc, nawet jeśli <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ustawiono JSON danych nadal może być zdeserializowany w dowolnej kolejności.

### <a name="json-types"></a>Typy JSON

Typu JSON nie musi odpowiadać zgodnie z poprzednią tabelą przy deserializacji. Na przykład `Int` zwykle mapy numer JSON, ale można też pomyślnie po deserializacji z ciągu JSON tak długo, jak ciąg zawiera prawidłowy numer. Oznacza to, że zarówno {"q": 42} i {"q": "42"} są prawidłowe w przypadku `Int` element członkowski danych o nazwie "q".

### <a name="polymorphism"></a>Polimorfizm

Serializacji polimorficznych składa się z możliwością serializacji typu pochodnego, gdy jego typ podstawowy jest oczekiwany. Jest to obsługiwane dla serializacji JSON przez architekturę WCF porównywalne do sposobu serializacji XML jest obsługiwane. Na przykład można serializować `MyDerivedType` gdzie `MyBaseType` oczekuje się, w przeciwnym razie serializacji `Int` gdzie `Object` oczekuje.

Informacje o typie mogą zostać utracone podczas deserializacji typem pochodnym, jeśli oczekiwany jest typ podstawowy, chyba że są deserializacji typie złożonym. Na przykład jeśli <xref:System.Uri> jest serializowana gdzie <xref:System.Object> oczekuje się, czego wynikiem ciągu JSON. Jeśli ten ciąg jest następnie deserializowany do <xref:System.Object>, .NET <xref:System.String> jest zwracana. Deserializator nie zna ten ciąg został początkowo typu <xref:System.Uri>. Ogólnie rzecz biorąc gdy oczekiwano <xref:System.Object>, wszystkie ciągi JSON są deserializacji jako ciągi .NET i wszystkie tablice JSON służący do serializowania słowników, kolekcjach .NET i tablice są deserializacji jako .NET <xref:System.Array> typu <xref:System.Object>, niezależnie od tego, co dotychczas rzeczywiste oryginalnego typu. Wartość logiczna JSON mapowany na .NET <xref:System.Boolean>. Jednak gdy oczekiwano <xref:System.Object>, JSON cyfry są deserializacji jako .NET albo <xref:System.Int32>, <xref:System.Decimal> lub <xref:System.Double>, której najbardziej odpowiednim typem jest pobierany automatycznie.

Podczas deserializacji do typu interfejsu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializuje tak, jakby zadeklarowanym typem zostały obiektu.

Podczas pracy z własnych typów podstawowych i pochodnych, za pomocą <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> lub równoważnego mechanizmu jest zwykle wymagany. Na przykład, jeśli operacja, która ma `Animal` zwracać wartości i faktycznie Zwraca wystąpienie `Cat` (pochodną `Animal`), należy albo zastosować <xref:System.Runtime.Serialization.KnownTypeAttribute>, `Animal` typu lub <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operację i określ `Cat` typu w tych atrybutów. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Szczegółowe informacje, jak polimorficznych działa serializacji i dyskusji niektórych ograniczeń, które należy przestrzegać podczas korzystania z niego zobacz sekcję zaawansowane informacje w dalszej części tego tematu.

### <a name="versioning"></a>Przechowywanie wersji

Przechowywanie wersji funkcji, takich jak kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs, są w pełni obsługiwane w formacie JSON. Ponadto, w większości przypadków użytkownik może zdeserializować typ w jednym formacie (na przykład XML) i serializować go do innego formatu (na przykład JSON), a także zachować dane w <xref:System.Runtime.Serialization.IExtensibleDataObject>. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Należy pamiętać, JSON jest nieuporządkowaną, dzięki czemu utracenie wszelkich informacji o zamówieniu. Ponadto JSON nie obsługuje wiele pary klucz/wartość z taką samą nazwę klucza. Ponadto wszystkie operacje na <xref:System.Runtime.Serialization.IExtensibleDataObject> są założenia polimorficznych —, która jest ich typ pochodny są przypisane do <xref:System.Object>, typ podstawowy dla wszystkich typów.

## <a name="json-in-urls"></a>JSON w adresach URL

Podczas korzystania z punktów końcowych ASP.NET AJAX przy użyciu czasownik HTTP GET (przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute> atrybut), parametry przychodzące są wyświetlane w adresie URL żądania, a nie treści komunikatu. JSON jest obsługiwane, nawet w adresie URL żądania, więc jeśli masz operacją, która przyjmuje `Int` o nazwie "number" i `Person` typu złożonego o nazwie "p", adres URL może przypominać następujący adres URL.

```
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Jeśli używasz kontrolki Menedżera skryptów AJAX programu ASP.NET i serwera proxy do wywołania, ten adres URL jest generowana automatycznie przez serwer proxy i nie jest widoczny. Punkty końcowe — ASP.NET AJAX, JSON nie można używać w adresach URL.

## <a name="advanced-information"></a>Informacje zaawansowane

### <a name="iserializable-support"></a>Obsługa iSerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Obsługiwane i nieobsługiwane typy ISerializable

Ogólnie rzecz biorąc, typami, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejsu są w pełni obsługiwane podczas serializacji/deserializacji JSON. Jednak niektóre z tych typów (w tym niektórych typów programu .NET Framework) są implementowane w taki sposób, aby aspekty serializacji specyficzne dla formatu JSON spowodować ich zdeserializować nie prawidłowo:

- Za pomocą <xref:System.Runtime.Serialization.ISerializable>, typ danych elementów członkowskich nigdy nie jest znana z wyprzedzeniem. Prowadzi to do sytuacji polimorficznych, podobnie jak na obiekt podczas deserializacji typów. Jak wspomniano wcześniej, może to prowadzić do utraty informacji o typie w formacie JSON. Na przykład typ, który serializuje `enum` w jego <xref:System.Runtime.Serialization.ISerializable> implementacji, próba deserializacji z powrotem bezpośrednio do `enum` (bez prawidłowego rzutowania) zakończy się niepowodzeniem, ponieważ `enum` jest serializowana, przy użyciu liczb w formacie JSON i JSON numery deserializuje na wbudowane typy liczbowe .NET (Int32, Decimal lub podwójne). Więc fakt, numer używany `enum` wartości zostaną utracone.

- <xref:System.Runtime.Serialization.ISerializable> Typ, który zależy od określonej kolejności deserializacji w jego konstruktorze deserializacji mogą zakończyć się niepowodzeniem do deserializacji niektóre dane JSON, ponieważ większość serializatory JSON nie gwarantują jakiejkolwiek ustalonej kolejności.

#### <a name="factory-types"></a>Typy fabryki

Gdy <xref:System.Runtime.Serialization.IObjectReference> interfejs jest obsługiwany w formacie JSON, ogólnie rzecz biorąc, wszelkie typy, które wymagają funkcji "fabryki type" (zwrócenia wystąpienia innego typu niż <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> niż typ, który implementuje interfejs) nie są obsługiwane.

### <a name="datetime-wire-format"></a>DateTime Wire Format

<xref:System.DateTime> wartości są wyświetlane jako ciągi JSON w formie "/ Date(700000+0500) /", gdzie jest to pierwszy numer (700000 w przykładzie przedstawionym) liczbę milisekund w strefie czasowej GMT regularne (innych niż-letniego) czas od północy 1 stycznia 1970. Liczba może być ujemna do reprezentowania wcześniej razy. Element, który składa się z "+0500" w przykładzie jest opcjonalny, a także wskazuje, że czas jest <xref:System.DateTimeKind.Local> rodzaj — oznacza to, że powinny być konwertowane na podstawie lokalnej strefy czasowej na deserializacji. Jeśli jest nieobecne, czas jest przeprowadzona jako <xref:System.DateTimeKind.Utc>. Rzeczywista liczba ("0500" w tym przykładzie) i jej znak (+ lub -), są ignorowane.

Podczas serializacji <xref:System.DateTime>, <xref:System.DateTimeKind.Local> i <xref:System.DateTimeKind.Unspecified> godziny są zapisywane z użyciem przesunięcie i <xref:System.DateTimeKind.Utc> są zapisywane bez.

Kod JavaScript klienta ASP.NET AJAX automatycznie konwertuje takie ciągi na język JavaScript `DateTime` wystąpień. W przypadku innych ciągów, które mają podobne formularza, które nie mają wartości typu <xref:System.DateTime> na platformie .NET, są one konwertowane również.

Konwersja tylko ma miejsce, jeśli są poprzedzone znakiem zmiany znaczenia znakami "/" (oznacza to, za pomocą pliku JSON wygląda "\\/Date(700000+0500)\\/") i WCF ta Przyczyna JSON encoder (włączane przez <xref:System.ServiceModel.WebHttpBinding>) zawsze zmienia znaczenie znaku "/".

### <a name="xml-in-json-strings"></a>Kod XML w ciągów JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> jest serializowany z bez zawijania. Na przykład element członkowski danych "x" o typie <xref:System.Xml.XmlElement> zawierający \<abc / > jest reprezentowany w następujący sposób.

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Tablic elementów XmlNode

<xref:System.Array> obiekty typu <xref:System.Xml.XmlNode> zostaną opakowane w elemencie o nazwie ArrayOfXmlNode w przestrzeni nazw kontraktu danych w warstwie standardowa dla typu. Jeśli "x" jest tablicą, która zawiera węzeł atrybutu "N" w przestrzeni nazw "ns", który zawiera "value" i węzeł pustego elementu "M", reprezentacja jest następujący.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atrybuty w pustej przestrzeni nazw na początku XmlNode tablic (przed innymi elementami) nie są obsługiwane.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy interfejsu IXmlSerializable, w tym XElement i zestaw danych

<xref:System.Runtime.Serialization.ISerializable> typy podzielić na "typów zawartości", "Typy zestawu danych" i "typy elementów". Aby uzyskać definicje tych typów, zobacz [typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

"Zawartość" oraz "Zestaw danych" typy są serializowane podobne do <xref:System.Array> obiektów <xref:System.Xml.XmlNode> opisanych w poprzedniej sekcji. Są one opakowane w elemencie o nazwie i przestrzeni nazw odpowiada nazwie kontraktu danych i przestrzeni nazw typu zagrożona.

"Element" typy, takie jak <xref:System.Xml.Linq.XElement> są serializowane, tak jak, podobnie jak <xref:System.Xml.XmlElement> omówionych wcześniej w tym temacie.

### <a name="polymorphism"></a>Polimorfizm

#### <a name="preserving-type-information"></a>Zachowywanie informacji o typie

Jak wspomniano wcześniej, polimorfizm jest obsługiwane w formacie JSON z pewnymi ograniczeniami. JavaScript jest językiem ze słabą kontrolą typów, a typ tożsamości zwykle nie jest problemem. Korzystając z formatu JSON do komunikowania się między systemem silnie typizowane (.NET), a system ze słabą kontrolą typów (JavaScript), zaleca się zachować typ tożsamości. Na przykład typy przy użyciu danych umowy nazwy "Patrol" i "Koło" pochodzić od typu o nazwie kontraktu danych "Kształt". Jeśli "Koło" są wysyłane z .NET do JavaScript i nowszej jest zwracany do metody .NET, który oczekuje, że "Kształt", jest przydatne w przypadku po stronie platformy .NET dowiedzieć się, że danego obiektu była pierwotnie "Koło" — w przeciwnym razie wszelkie informacje specyficzne dla typu pochodnego (na przykład element członkowski danych "radius" na "Koło") mogą zostać utracone.

Aby zachować tożsamości typu serializacji typy złożone do formatu JSON wskazówką"typu" można dodać, gdy Deserializator rozpoznaje wskazówka i działa prawidłowo. Wskazówka"typu" jest para klucza i wartości JSON, nazwą klucza "\_\_typu" (dwóch znaków podkreślenia następuje od słowa "type"). Wartość ciągu JSON w postaci "DataContractName:DataContractNamespace" (niczego maksymalnie pierwszym dwukropkiem ma na imię). Korzystając z poprzedniego przykładu, "Koło" może być serializowany w następujący sposób.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Wskazówka typu jest bardzo podobny do `xsi:type` Atrybut zdefiniowanym przez standard wystąpienia schematu XML, używany podczas serializacji/deserializacji XML.

Elementy członkowskie danych o nazwie "\_\_typu" są zabronione ze względu na potencjalne konflikt ze wskazówką typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmniejszenie rozmiaru wskazówek dotyczących typów

Aby zmniejszyć rozmiar JSON komunikaty, domyślny prefiks przestrzeni nazw kontraktu danych (`http://schemas.datacontract.org/2004/07/`) jest zastępowany znaku "#". (Aby ta zastępowania odwracalny, odwrócony reguła jest używana: Jeśli przestrzeń nazw, który rozpoczyna się od "#" lub "\\" znaków, są one dołączane za pomocą dodatkowych "\\" znaków). W związku z tym, czy "Koło" jest typem w przestrzeni nazw .NET "MyApp.Shapes", jest jego domyślna przestrzeń nazw kontraktu danych `http://schemas.datacontract.org/2004/07/MyApp`. Kształty i reprezentacji JSON wygląda następująco:

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Skrócona (#MyApp.Shapes) i pełną (http://schemas.datacontract.org/2004/07/MyApp.Shapes) nazw jest zrozumiały przy deserializacji.

#### <a name="type-hint-position-in-json-objects"></a>Pozycja wskazówki dotyczącej typu w obiekty JSON

Należy pamiętać, że wskazówki dotyczącej typu musi występować jako pierwszy w reprezentacji JSON. Jest to tylko wówczas, których kolejność pary klucz/wartość jest ważna w przetwarzaniu JSON. Na przykład następujące nie jest prawidłowy sposób określania wskazówki dotyczącej typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Zarówno <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używane przez program WCF i ASP.NET AJAX stron klienta zawsze emitować wskazówki dotyczącej typu najpierw.

#### <a name="type-hints-apply-only-to-complex-types"></a>Wskazówek dotyczących typów mają zastosowanie tylko do typów złożonych

Nie ma możliwości do emitowania wskazówką typu dla typów innych niż złożone. Na przykład, jeśli operacja ma <xref:System.Object> zwracany typ, ale zwraca okrąg, może być reprezentacji JSON, jak pokazano wcześniej i informacje o typie są zachowywane. Jednak jeśli zostanie zwrócony identyfikator Uri, reprezentacja JSON jest ciąg się oraz fakt, że ciąg używany do reprezentowania identyfikatora Uri zostaną utracone. Dotyczy to nie tylko dla typów pierwotnych, ale także do kolekcji i tablic.

#### <a name="when-are-type-hints-emitted"></a>Kiedy są emitowane wskazówek dotyczących typów

Wskazówek dotyczących typów może znacznie zwiększyć rozmiar komunikatu (jednym ze sposobów, aby zmniejszyć to jest Użyj krótszych nazw kontraktu danych, jeśli to możliwe). W związku z tym następujące reguły określają, czy wskazówek dotyczących typów są emitowane:

- Korzystając z technologii ASP.NET AJAX, wskazówek dotyczących typów są zawsze emitowane zawsze, gdy jest to możliwe, nawet jeśli dostępny jest nie przypisania bazową/dziedziczoną — na przykład, nawet jeśli okrąg jest przypisany do okrąg. (Jest to wymagane, aby w pełni włączyć proces wywoływania ze środowiska JSON ze słabą kontrolą typów, w środowisku .NET silnie typizowane bez Zaskakujące utraty informacji.)

- Podczas korzystania z usług AJAX dzięki integracji platformy ASP.NET, nie wskazówek dotyczących typów tylko są emitowane po przypisanie bazową/dziedziczoną — emitowanego po okręgu jest przypisany do kształtu lub <xref:System.Object> , ale nie po przypisaniu do okrąg. To zapewnia minimalne informacje wymagane do poprawnego zaimplementowania klienta JavaScript, co poprawia wydajność, ale nie chroni przed utratą informacji typu w klientach niepoprawnie zaprojektowany. Należy unikać bazową/dziedziczoną przypisania całkowicie na serwerze, aby uniknąć tego problemu na komputerze klienckim.

- Korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> typu `alwaysEmitTypeInformation` parametr konstruktora można wybrać z poprzednich dwóch trybów z jest domyślna "`false`" (Emituj tylko wskazówek dotyczących typów, gdy jest to wymagane).

#### <a name="duplicate-data-member-names"></a>Zduplikowane nazwy elementów członkowskich danych

Typ pochodny informacji znajduje się w ten sam obiekt JSON, wraz z informacjami o typie podstawowym, a może występować w dowolnej kolejności. Na przykład `Shape` mogą być reprezentowane w następujący sposób.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Natomiast okrąg mogą być reprezentowane w następujący sposób.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Jeśli podstawowy `Shape` typu również znajdują się element członkowski danych o nazwie "`radius`", prowadzi to do kolizji na obu serializacji (ponieważ obiekty JSON nie może mieć powtarzające się nazwy kluczy) oraz deserializacji (ponieważ nie jest jasne, czy "radius" odnosi się do `Shape.radius` lub `Circle.radius`). W związku z tym, podczas gdy pojęcie "ukrywanie właściwości" (elementy członkowskie danych o takiej samej nazwie w podstawie i klas pochodnych) zwykle nie jest zalecane w klasach kontraktu danych faktycznie jest niedozwolona w przypadku formatu JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm i typów IXmlSerializable

<xref:System.Xml.Serialization.IXmlSerializable> typy może być polymorphically przypisana do siebie nawzajem w zwykły sposób tak długo, jak są spełnione wymagania znane typy, zgodnie z regułami kontraktu danych zwykle. Jednak serializacji <xref:System.Xml.Serialization.IXmlSerializable> wpisz zamiast <xref:System.Object> powoduje utratę informacji o typie, ponieważ ciąg JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm i niektórych typów interfejsu

Jest zabroniona można serializować typu kolekcji lub typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> w przypadku, gdy typ — do kolekcji, który nie jest <xref:System.Xml.Serialization.IXmlSerializable> (z wyjątkiem <xref:System.Object>) jest oczekiwany. Na przykład niestandardowy interfejs o nazwie `IMyInterface` i typ `MyType` zaimplementować obu <xref:System.Collections.Generic.IEnumerable%601> typu `int` i `IMyInterface`. Jest zabroniona do zwrócenia `MyType` z operacją, którego typem zwracanym jest `IMyInterface`. Jest to spowodowane `MyType` muszą być serializowane jako tablicę JSON i wymaga wskazówką typu, a podana przed nie może zawierać wskazówką typu z tablicami, tylko z typów złożonych.

#### <a name="known-types-and-configuration"></a>Znane typy i Konfiguracja

Wszystkie mechanizmów znany typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> są również obsługiwane w taki sam sposób, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Zarówno serializatory odczytu tego samego elementu konfiguracji [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) w [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), aby odnaleźć znanych typów dodanych za pomocą pliku konfiguracji.

#### <a name="collections-assigned-to-object"></a>Kolekcji przypisanych do obiektu

Przypisane do obiektu kolekcji są serializowane, tak, jakby są kolekcjami, które implementują <xref:System.Collections.Generic.IEnumerable%601>: tablica JSON z każdego wpisu, który ma wskazówką typu, jeśli jest to typ złożony. Na przykład <xref:System.Collections.Generic.List%601> typu `Shape` przypisane do <xref:System.Object> wygląda podobnie do następującego.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Podczas deserializacji do <xref:System.Object>:

- `Shape` musi należeć do listy znanych typów. Posiadanie <xref:System.Collections.Generic.List%601> typu `Shape` w znanych typów nie ma wpływu. Należy zauważyć, że nie trzeba dodawać `Shape` do znanych typów na serializacji w tym przypadku — odbywa się to automatycznie.

- Kolekcja jest przeprowadzona jako <xref:System.Array> typu <xref:System.Object> zawierający `Shape` wystąpień.

#### <a name="derived-collections-assigned-to-base-collections"></a>Pochodne kolekcji przypisane do podstawowej kolekcji

Po przypisaniu pochodnej kolekcji do podstawowej kolekcji, Kolekcja zwykle jest serializowana, tak jakby znajdowała się kolekcja typu podstawowego. Jednak jeśli typ elementu kolekcji pochodnych nie można przypisać do typu elementu podstawowego kolekcji, jest zgłaszany wyjątek.

#### <a name="type-hints-and-dictionaries"></a>Wskazówek dotyczących typów i słowników

Po przypisaniu do słownika <xref:System.Object>, każdego wpisu klucza i wartości w słowniku jest traktowany tak, jakby został przypisany do <xref:System.Object> i pobiera wskazówkę z typu.

Podczas serializacji typów słownika, obiekt JSON, który zawiera elementy członkowskie "Key" i "Wartość" nie jest zależny od `alwaysEmitTypeInformation` ustawienie i zawiera tylko wskazówką typu podczas poprzednich zasad zbierania tego wymagają.

### <a name="valid-json-key-names"></a>Nazwy kluczy z prawidłowym kodem JSON

Serializator koduje XML nazwy kluczy, które nie są prawidłowe nazwy XML. Na przykład element członkowski danych o nazwie "123" miałby zakodowane nazwę taką jak "\_x0031\_\_x0032\_\_x0033\_" ponieważ "123" jest nieprawidłową nazwą — element XML (rozpoczyna się od cyfry). Podobna sytuacja może powstać z niektórych zestawów znaków międzynarodowych nazw XML nie jest prawidłowy. Opis ten efekt XML na przetwarzanie JSON zawiera [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
