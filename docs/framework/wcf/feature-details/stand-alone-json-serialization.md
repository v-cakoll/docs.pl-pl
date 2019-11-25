---
title: Autonomiczna Serializacja kodu JSON przy użyciu Klasa DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 412da71617a8627c47e877a75770271d9a3cf180
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976073"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Autonomiczna Serializacja kodu JSON przy użyciu Klasa DataContractJsonSerializer

> [!NOTE]
> Ten artykuł dotyczy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. W przypadku większości scenariuszy, które obejmują Serializowanie i deserializacja kodu JSON, zalecamy korzystanie z narzędzi w [przestrzeni nazw System. Text. JSON](../../../standard/serialization/system-text-json-overview.md). 

JSON (JavaScript Object Notation) to format danych przeznaczony specjalnie do użycia przez kod JavaScript uruchomiony na stronach sieci Web w przeglądarce. Jest to domyślny format danych używany przez usługi ASP.NET AJAX utworzone w Windows Communication Foundation (WCF).

Ten format może być również używany podczas tworzenia usług AJAX bez integrowania z ASP.NET — w tym przypadku XML jest wartością domyślną, ale można wybrać kod JSON.

Na koniec, jeśli wymagana jest obsługa JSON, ale nie jest tworzona usługa AJAX, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> umożliwia bezpośrednie serializacji obiektów .NET do danych JSON i deserializacja takich danych w wystąpieniach typów .NET. Aby dowiedzieć się, jak to zrobić, zobacz [How to: serializacji i deserializacji danych JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Podczas pracy z notacją JSON obsługiwane są te same typy .NET, z kilkoma wyjątkami, które są obsługiwane przez <xref:System.Runtime.Serialization.DataContractSerializer>. Aby zapoznać się z listą obsługiwanych typów, zobacz [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Obejmuje to większość typów pierwotnych, większość tablic i typów kolekcji, a także typy złożone wykorzystujące <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapowanie typów .NET na typy JSON

W poniższej tabeli przedstawiono zgodność między typami .NET a typami JSON/JavaScript, które są mapowane przy użyciu procedur serializacji i deserializacji.

|Typy .NET|JSON/JavaScript|Uwagi|
|----------------|----------------------|-----------|
|Wszystkie typy liczbowe, na przykład <xref:System.Int32>, <xref:System.Decimal> lub <xref:System.Double>|Wartość liczbowa|Wartości specjalne, takie jak `Double.NaN`, `Double.PositiveInfinity` i `Double.NegativeInfinity` nie są obsługiwane i powodują nieprawidłowe dane JSON.|
|<xref:System.Enum>|Wartość liczbowa|Zobacz sekcję "wyliczenia i kod JSON" w dalszej części tego tematu.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Format tych typów w formacie JSON jest taki sam jak w przypadku kodu XML (zasadniczo przedziału czasu dla formatu Duration ISO 8601, identyfikator GUID w formacie "12345678-ABCD-ABCD-ABCD-1234567890AB" i identyfikator URI w postaci ciągu naturalnego, jak "http://www.example.com"). Aby uzyskać szczegółowe informacje, zobacz temat [Informacje o schemacie kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|Format jest "Name: Namespace" (wszystkie przed pierwszym dwukropkiem jest nazwą). Brak nazwy lub przestrzeni nazw. Jeśli nie ma przestrzeni nazw, można również pominąć ten dwukropek.|
|<xref:System.Array> typu <xref:System.Byte>|Tablica liczb|Każda liczba reprezentuje wartość jednego bajtu.|
|<xref:System.DateTime>|DateTime lub String|Zobacz daty/godziny i kod JSON w dalszej części tego tematu.|
|<xref:System.DateTimeOffset>|Typ złożony|Zobacz daty/godziny i kod JSON w dalszej części tego tematu.|
|Typy XML i ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>., Tablice <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Zobacz sekcję Typy XML i kod JSON w tym temacie.|
|<xref:System.DBNull>|Pusty typ złożony|--|
|Kolekcje, słowniki i tablice|Macierzy|Zapoznaj się z sekcją kolekcje, słowniki i tablice w tym temacie.|
|Typy złożone (z zastosowanymi <xref:System.Runtime.Serialization.DataContractAttribute> lub <xref:System.SerializableAttribute>)|Typ złożony|Elementy członkowskie danych stają się elementami członkowskimi typu złożonego JavaScript.|
|Typy złożone implementujące interfejs <xref:System.Runtime.Serialization.ISerializable>)|Typ złożony|Analogicznie jak inne typy złożone, ale niektóre typy <xref:System.Runtime.Serialization.ISerializable> nie są obsługiwane — zobacz część obsługa ISerializable w sekcji Informacje zaawansowane w tym temacie.|
|wartość `Null` dla dowolnego typu|Null|Typy dopuszczające wartości null są również obsługiwane i mapowane na dane JSON w taki sam sposób jak typy niedopuszczające wartości null.|

### <a name="enumerations-and-json"></a>Wyliczenia i JSON

Wartości elementu członkowskiego wyliczenia są traktowane jako liczby w formacie JSON, które różnią się od sposobu, w jaki są traktowane jako nazwy elementów członkowskich. Aby uzyskać więcej informacji na temat traktowania kontraktu danych, zobacz [typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Na przykład jeśli masz `public enum Color {red, green, blue, yellow, pink}`, serializacja `yellow` produkuje liczbę 3, a nie ciąg "żółty".

- Wszystkie składowe `enum` można serializować. Atrybuty <xref:System.Runtime.Serialization.EnumMemberAttribute> i <xref:System.NonSerializedAttribute> są ignorowane, jeśli są używane.

- Istnieje możliwość deserializacji nieistniejącej wartości `enum` — na przykład wartość 87 można deserializować do poprzedniego wyliczenia koloru, nawet jeśli nie zdefiniowano odpowiedniej nazwy koloru.

- Flagi `enum` nie są specjalne i są traktowane jak wszystkie inne `enum`.

### <a name="datestimes-and-json"></a>Daty/godziny i kod JSON

Format JSON nie obsługuje bezpośrednio dat i godzin. Są one jednak bardzo często używane i ASP.NET AJAX zapewnia specjalną pomoc techniczną dla tych typów. W przypadku korzystania z serwerów proxy ASP.NET AJAX, typ <xref:System.DateTime> w programie .NET w pełni odpowiada typowi `DateTime` w języku JavaScript.

- Gdy nie korzystasz z ASP.NET, typ <xref:System.DateTime> jest reprezentowany w formacie JSON jako ciąg z formatem specjalnym, który opisano w sekcji Informacje zaawansowane w tym temacie.

- <xref:System.DateTimeOffset> jest reprezentowana w formacie JSON jako typ złożony: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. Członek `offsetMinutes` jest przesunięty czas lokalny od czasu uniwersalnego Greenwich (GMT), również określany jako uniwersalny czas koordynowany (UTC), skojarzony z lokalizacją interesującego zdarzenia. Element członkowski `dateTime` reprezentuje wystąpienie w czasie, gdy wystąpiło zainteresowanie zdarzeniami (ponownie, `DateTime` w języku JavaScript, gdy ASP.NET AJAX jest używany i ciąg, gdy nie jest). Podczas serializacji element członkowski `dateTime` jest zawsze serializowany w GMT. Dlatego w przypadku opisywania 3:00 czasu Nowego Jorku `dateTime` ma składnik czasu 8:00 AM i `offsetMinutes` są 300 (minus 300 min lub 5 godzin od GMT).

  > [!NOTE]
  > obiekty <xref:System.DateTime> i <xref:System.DateTimeOffset>, podczas serializacji do formatu JSON, zachowują się tylko z dokładnością do milisekund. Wartości podmilisekundy (mikro/nanosekunds) są tracone podczas serializacji.

### <a name="xml-types-and-json"></a>Typy XML i JSON

Typy XML stają się ciągami JSON.

- Na przykład jeśli element członkowski danych "q" typu XElement zawiera \<ABC/>, kod JSON to {"q": "\<ABC/>"}.

- Istnieją pewne specjalne reguły określające sposób zawijania kodu XML — Aby uzyskać więcej informacji, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

- Jeśli używasz ASP.NET AJAX i nie chcesz używać ciągów w języku JavaScript, ale zamiast tego chcesz użyć modelu XML DOM, ustaw właściwość <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> na XML w <xref:System.ServiceModel.Web.WebGetAttribute> lub właściwość <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> na XML na <xref:System.ServiceModel.Web.WebInvokeAttribute>.

### <a name="collections-dictionaries-and-arrays"></a>Kolekcje, słowniki i tablice

Wszystkie kolekcje, słowniki i tablice są reprezentowane w formacie JSON jako tablice.

- Wszelkie dostosowania, które używają <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, zostaną zignorowane w reprezentacji JSON.

- Słowniki nie są sposobem pracy bezpośrednio z formatem JSON. \<słownika, > obiektów nie mogą być obsługiwane w taki sam sposób jak w przypadku programu WCF zgodnie z oczekiwaniami z użyciem innych technologii JSON. Na przykład, jeśli "ABC" jest mapowany na "XYZ" i "def" jest mapowany do 42 w słowniku, reprezentacja JSON nie jest {"ABC": "XYZ", "def": 42}, ale jest [{"Key": "ABC", "value": "XYZ"}, {"Key": "def", "value": 42}].

- Jeśli chcesz, aby bezpośrednio korzystać z kodu JSON (dostęp do kluczy i wartości, bez wstępnego definiowania niesztywnego kontraktu), masz kilka opcji:

  - Rozważ użycie przykładowej [serializacji JSON (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) .

  - Rozważ użycie konstruktorów <xref:System.Runtime.Serialization.ISerializable> i deserializacji — te dwa mechanizmy umożliwiają dostęp do par klucz/wartość JSON na potrzeby serializacji i deserializacji, ale nie działają w scenariuszach częściowej relacji zaufania.

  - Należy rozważyć pracę z [mapowaniem między JSON i XML,](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) a nie przy użyciu serializatora.

  - *Polimorfizm* w kontekście serializacji odwołuje się do możliwości serializacji typu pochodnego, w którym oczekiwany jest jego typ podstawowy. Istnieją specjalne reguły specyficzne dla JSON, które umożliwiają selektywne Używanie kolekcji, na przykład przypisanie kolekcji do <xref:System.Object>. Ten problem jest bardziej szczegółowo omówiony w sekcji Informacje zaawansowane w dalszej części tego tematu.

## <a name="additional-details"></a>Dodatkowe szczegóły

### <a name="order-of-data-members"></a>Kolejność elementów członkowskich danych

Kolejność elementów członkowskich danych nie jest ważna podczas korzystania z formatu JSON. W przypadku ustawienia <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> dane JSON nadal mogą być deserializowane w dowolnej kolejności.

### <a name="json-types"></a>Typy JSON

Typ JSON nie musi być zgodny z poprzednią tabelą podczas deserializacji. Na przykład, `Int` zwykle jest mapowany na numer JSON, ale można go również pomyślnie zdeserializować z ciągu JSON, o ile ten ciąg zawiera prawidłową liczbę. Oznacza to, że oba {"q": 42} i {"q": "42"} są prawidłowe, jeśli istnieje element członkowski danych `Int` o nazwie "q".

### <a name="polymorphism"></a>Polimorfizm

Serializacja polimorficzna składa się z możliwości serializacji typu pochodnego, w którym oczekiwany jest jego typ podstawowy. Jest to obsługiwane w przypadku serializacji JSON przez WCF, która jest porównywalna z sposobem obsługi serializacji XML. Na przykład można serializować `MyDerivedType`, gdzie `MyBaseType` jest oczekiwany, lub serializować `Int` gdzie `Object` jest oczekiwany.

Informacje o typie mogą zostać utracone podczas deserializacji typu pochodnego, jeśli jest oczekiwany typ podstawowy, chyba że jest deserializowany typ złożony. Na przykład jeśli <xref:System.Uri> jest serializowana, gdzie oczekiwana jest <xref:System.Object>, wynikiem jest ciąg JSON. Jeśli ten ciąg jest następnie deserializowany z powrotem do <xref:System.Object>, zwracany jest <xref:System.String> .NET. Deserializator nie wie, że ciąg był początkowo typu <xref:System.Uri>. Ogólnie rzecz biorąc, gdy oczekiwane <xref:System.Object>, wszystkie ciągi JSON są deserializowane jako ciągi .NET, a wszystkie tablice JSON używane do serializacji kolekcji, słowników i tablic platformy .NET są deserializowane jako .NET <xref:System.Array> typu <xref:System.Object>, niezależnie od tego, jaki był oryginalny pierwotny typ. Wartość logiczna JSON jest mapowana na <xref:System.Boolean>.NET. Jeśli jednak oczekujesz <xref:System.Object>, numery JSON są deserializowane jako .NET <xref:System.Int32>, <xref:System.Decimal> lub <xref:System.Double>, gdzie najbardziej odpowiedni typ jest wybierany automatycznie.

Podczas deserializacji do typu interfejsu, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializacji, tak jakby zadeklarowany typ to obiekt.

Podczas pracy z własnym typem podstawowym i pochodnym użycie <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> lub równoważnego mechanizmu jest zwykle wymagane. Na przykład jeśli masz operację, która ma `Animal` zwracaną wartość i faktycznie zwraca wystąpienie `Cat` (pochodzące z `Animal`), należy zastosować <xref:System.Runtime.Serialization.KnownTypeAttribute>do typu `Animal` lub <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operacji i określić typ `Cat` w tych atrybutach. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Aby uzyskać szczegółowe informacje o sposobie działania serializacji polimorficznej i omówieniu niektórych ograniczeń, które muszą być przestrzegane podczas korzystania z niej, zobacz sekcję Informacje zaawansowane w dalszej części tego tematu.

### <a name="versioning"></a>Przechowywanie wersji

Funkcje obsługi wersji kontraktu danych, w tym interfejs <xref:System.Runtime.Serialization.IExtensibleDataObject>, są w pełni obsługiwane w formacie JSON. Ponadto w większości przypadków można zdeserializować typu w jednym formacie (na przykład XML), a następnie serializować go do innego formatu (na przykład JSON) i nadal zachować dane w <xref:System.Runtime.Serialization.IExtensibleDataObject>. Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Pamiętaj, że format JSON jest nieuporządkowany, więc wszelkie informacje o porządku zostaną utracone. Ponadto kod JSON nie obsługuje wielu par klucz/wartość o tej samej nazwie klucza. Na koniec wszystkie operacje na <xref:System.Runtime.Serialization.IExtensibleDataObject> są z natury polimorficzne — jest to typ pochodny przypisany do <xref:System.Object>, typ podstawowy dla wszystkich typów.

## <a name="json-in-urls"></a>KOD JSON w adresach URL

W przypadku korzystania z punktów końcowych ASP.NET AJAX z czasownikiem HTTP GET (przy użyciu atrybutu <xref:System.ServiceModel.Web.WebGetAttribute>) parametry przychodzące są wyświetlane w adresie URL żądania, a nie w treści komunikatu. KOD JSON jest obsługiwany nawet w adresie URL żądania, więc jeśli masz operację, która przyjmuje `Int` o nazwie "number" i `Person` typie złożonym o nazwie "p", adres URL może być podobny do następującego adresu URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Jeśli używasz kontrolki Menedżera skryptów AJAX ASP.NET i serwera proxy do wywoływania usługi, ten adres URL jest generowany automatycznie przez serwer proxy i nie jest widoczny. Nie można używać kodu JSON w adresach URL w punktach końcowych non-ASP.NET AJAX.

## <a name="advanced-information"></a>Informacje zaawansowane

### <a name="iserializable-support"></a>Obsługa ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Obsługiwane i nieobsługiwane typy ISerializable

Ogólnie rzecz biorąc, typy implementujące interfejs <xref:System.Runtime.Serialization.ISerializable> są w pełni obsługiwane podczas serializowania/deserializacji JSON. Jednak niektóre z tych typów (w tym niektóre typy .NET Framework) są implementowane w taki sposób, że aspekty serializacji specyficzne dla JSON powodują, że nie będą poprawnie deserializacji:

- W przypadku <xref:System.Runtime.Serialization.ISerializable>typ poszczególnych elementów członkowskich danych nigdy nie jest znany z góry. Prowadzi to do sytuacji polimorficznej podobnej do deserializacji typów do obiektu. Jak wspomniano wcześniej, może to prowadzić do utraty informacji o typie w formacie JSON. Na przykład typ, który serializować `enum` w swojej implementacji <xref:System.Runtime.Serialization.ISerializable> i próbuje deserializować bezpośrednio do `enum` (bez odpowiednich rzutów) nie powiedzie się, ponieważ `enum` jest serializowana przy użyciu liczb w notacji JSON i liczby JSON deserializacji do wbudowanych typów liczbowych .NET (Int32, decimal lub Double). W związku z tym fakt, że liczba używana jako wartość `enum` zostanie utracona.

- Typ <xref:System.Runtime.Serialization.ISerializable>, który zależy od określonej kolejności deserializacji w konstruktorze deserializacji może również niepowodzeniem deserializować niektórych danych JSON, ponieważ większość serializatorów JSON nie gwarantuje żadnej konkretnej kolejności.

#### <a name="factory-types"></a>Typy fabryk

Chociaż interfejs <xref:System.Runtime.Serialization.IObjectReference> jest obsługiwany w notacji JSON w ogólności, wszystkie typy, które wymagają funkcji "typ fabryki" (zwracając wystąpienie innego typu z <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> niż typ implementujący interfejs) nie są obsługiwane.

### <a name="datetime-wire-format"></a>Format przewodu DateTime

wartości <xref:System.DateTime> są wyświetlane jako ciągi JSON w postaci "/Date (700000 + 0500)/", gdzie pierwsza liczba (700000 w podanym przykładzie) to liczba milisekund w strefie czasowej GMT, regularna (oszczędność nieletnia) od północy, 1 stycznia 1970. Liczba może być ujemna, aby reprezentować wcześniejszy czas. Część, która składa się z "+ 0500" w przykładzie, jest opcjonalna i wskazuje, że czas ma typ <xref:System.DateTimeKind.Local>, czyli należy go przekonwertować na lokalną strefę czasową podczas deserializacji. Jeśli jest nieobecny, czas jest deserializowany jako <xref:System.DateTimeKind.Utc>. Rzeczywista liczba ("0500" w tym przykładzie) i jej znak (+ lub-) są ignorowane.

Podczas serializacji <xref:System.DateTime>czasy <xref:System.DateTimeKind.Local> i <xref:System.DateTimeKind.Unspecified> są zapisywane z przesunięciem, a <xref:System.DateTimeKind.Utc> jest zapisywana bez.

Kod JavaScript klienta ASP.NET AJAX automatycznie konwertuje takie ciągi na wystąpienia `DateTime` JavaScript. Jeśli istnieją inne ciągi o podobnym formularzu, który nie jest typu <xref:System.DateTime> w programie .NET, są one również konwertowane.

Konwersja odbywa się tylko wtedy, gdy znaki "/" są wyprowadzane (to oznacza, że kod JSON wygląda jak "\\/Date (700000 + 0500)\\/"), a dla tego powodu koder JSON usługi WCF (włączony przez <xref:System.ServiceModel.WebHttpBinding>) zawsze wyprowadza znak "/".

### <a name="xml-in-json-strings"></a>XML w ciągach JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> jest serializowany bez zawijania. Na przykład element członkowski danych "x" typu <xref:System.Xml.XmlElement>, który zawiera \<ABC/>, jest reprezentowany w następujący sposób:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Tablice elementów XmlNode

obiekty <xref:System.Array> typu <xref:System.Xml.XmlNode> są opakowane w element o nazwie ArrayOfXmlNode w przestrzeni nazw standardowego kontraktu danych dla tego typu. Jeśli "x" jest tablicą zawierającą węzeł atrybutu "N" w przestrzeni nazw "NS", która zawiera "wartość" i pusty węzeł elementu "M", reprezentacja jest następująca.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atrybuty w pustej przestrzeni nazw na początku tablic XmlNode (przed innymi elementami) nie są obsługiwane.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable, w tym XElement i DataSet

typy <xref:System.Runtime.Serialization.ISerializable> są podzielona na "typy zawartości", "typy zestawów danych" i "typy elementów". Aby zapoznać się z definicjami tych typów, zobacz [Typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Typy "Content" i "DataSet" są serializowane podobne do <xref:System.Array> obiektów <xref:System.Xml.XmlNode> omówionych w poprzedniej sekcji. Są one opakowane w element, którego nazwa i przestrzeń nazw odpowiadają nazwie kontraktu danych i przestrzeni nazw danego typu.

Typy "element", takie jak <xref:System.Xml.Linq.XElement> są serializowane w postaci, podobne do <xref:System.Xml.XmlElement> wcześniej omówione w tym temacie.

### <a name="polymorphism"></a>Polimorfizm

#### <a name="preserving-type-information"></a>Zachowanie informacji o typie

Jak wspomniano wcześniej, polimorfizm jest obsługiwany w formacie JSON z pewnymi ograniczeniami. Język JavaScript jest nieprawidłowym typem języka i tożsamość typu nie jest zazwyczaj problemem. Jednak w przypadku korzystania z formatu JSON do komunikacji między systemem o jednoznacznie określonym typie (.NET) i niejednoznacznie określonym systemem (JavaScript) warto zachować tożsamość typu. Na przykład typy z nazwami kontraktu danych "Square" i "Circle" pochodzą od typu z nazwą kontraktu danych "Shape". Jeśli "okrąg" jest wysyłany z platformy .NET do języka JavaScript i później jest zwracany do metody .NET, która oczekuje "Shape", jest przydatne dla strony .NET, aby wiedzieć, że dany obiekt był pierwotnie "okrąg" — w przeciwnym razie wszelkie informacje specyficzne dla typu pochodnego (na przykład , element członkowski danych "RADIUS" na "Circle") może zostać utracony.

Aby zachować tożsamość typu, podczas serializowania typów złożonych do notacji JSON można dodać "wskazówkę typu", a Deserializator rozpoznaje wskazówkę i odpowiednio działa. "Wskazówka dotycząca typu" to para klucza/wartości JSON z nazwą klucza "\_\_typ" (dwa podkreślenia, po których następuje słowo "Type"). Wartość jest ciągiem JSON o postaci "DataContractName: DataContractNamespace" (wszystkie elementy do pierwszego dwukropka to nazwa). Przy użyciu wcześniejszego przykładu "okrąg" można serializować w następujący sposób.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Wskazówki dotyczące typu są bardzo podobne do atrybutu `xsi:type` zdefiniowanego w standardzie wystąpienia schematu XML i używane podczas serializowania/deserializacji XML.

Elementy członkowskie danych o nazwie "\_\_Type" są zabronione z powodu potencjalnego konfliktu ze wskazówką typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmniejszanie rozmiaru wskazówek typu

Aby zmniejszyć rozmiar komunikatów JSON, domyślny prefiks przestrzeni nazw kontraktu danych (`http://schemas.datacontract.org/2004/07/`) jest zastępowany znakiem "#". (Aby zmienić odwracalnie, zostanie użyta reguła ucieczki: Jeśli przestrzeń nazw zaczyna się od znaków "#" lub "\\", są one dołączane za pomocą dodatkowego znaku "\\"). W takim przypadku, jeśli "Circle" jest typem w przestrzeni nazw .NET "MojaApl. Shapes", jego domyślna przestrzeń nazw kontraktu danych to `http://schemas.datacontract.org/2004/07/MyApp`. Kształty i reprezentacja JSON są następujące.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Obie wartości są obcinane (#MyApp. Shapes) i pełne (nazwy http://schemas.datacontract.org/2004/07/MyApp.Shapes) są zrozumiałe dla deserializacji.

#### <a name="type-hint-position-in-json-objects"></a>Położenie wskazówki typu w obiektach JSON

Należy zauważyć, że Wskazówka typu musi występować najpierw w reprezentacji JSON. Jest to jedyny przypadek, w którym kolejność par klucz/wartość jest ważna w przetwarzaniu JSON. Na przykład następujące polecenie nie jest prawidłowym sposobem określenia wskazówki typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Zarówno <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używany przez funkcje WCF i ASP.NET strony klienckiej AJAX zawsze emitują wskazówkę typu.

#### <a name="type-hints-apply-only-to-complex-types"></a>Wskazówki dotyczące typów dotyczą tylko typów złożonych

Nie istnieje sposób emisji wskazówki typu dla typów niezłożonych. Na przykład jeśli operacja ma <xref:System.Object> zwracanego typu, ale zwraca okrąg, reprezentacja JSON może być jak pokazana wcześniej, a informacje o typie są zachowywane. Jeśli jednak zostanie zwrócony identyfikator URI, reprezentacja JSON jest ciągiem i faktem, że ciąg używany do reprezentowania identyfikatora URI zostanie utracony. Dotyczy to nie tylko typów pierwotnych, ale również do kolekcji i tablic.

#### <a name="when-are-type-hints-emitted"></a>Kiedy są emitowane wskazówki typu

Wskazówki dotyczące typów mogą znacząco zwiększyć rozmiar wiadomości (jednym ze sposobów na ograniczenie tego problemu jest użycie krótszych przestrzeni nazw kontraktu danych, jeśli jest to możliwe). W związku z tym następujące reguły określają, czy wskazówki dotyczące typu są emitowane:

- Gdy jest używany ASP.NET AJAX, wskazówki typu są zawsze emitowane w miarę możliwości, nawet jeśli nie istnieje przypisanie podstawowe/pochodne — na przykład nawet wtedy, gdy okrąg jest przypisany do okręgu. (Jest to wymagane, aby w pełni włączyć proces wywoływania z słabego typu środowiska JSON w środowisku .NET o jednoznacznie określonym typie, bez zaskakujące utraty informacji).

- Gdy korzystasz z usług AJAX z integracją ASP.NET, wskazówki dotyczące typu są emitowane tylko wtedy, gdy istnieje przypisanie podstawowe/pochodne — to jest generowane, gdy okrąg jest przypisywany do kształtu lub <xref:System.Object>, ale nie w przypadku przypisywania do okręgu. Zapewnia to minimalne informacje wymagane do poprawnego zaimplementowania klienta języka JavaScript, a tym samym zwiększenie wydajności, ale nie chroni przed utratą informacji typu w niewłaściwie zaprojektowanych klientach. Należy unikać przypisywania podstawowego/pochodnego całkowicie na serwerze, jeśli chcesz uniknąć tego problemu na kliencie.

- W przypadku korzystania z typu <xref:System.Runtime.Serialization.DataContractSerializer>, parametr konstruktora `alwaysEmitTypeInformation` umożliwia wybranie między poprzednimi trybami, z wartością domyślną "`false`" (tylko w razie potrzeby emitują wskazówki dotyczące typów).

#### <a name="duplicate-data-member-names"></a>Zduplikowane nazwy składowych danych

Informacje o typie pochodnym znajdują się w tym samym obiekcie JSON wraz z podstawowymi informacjami o typie i mogą występować w dowolnej kolejności. Na przykład `Shape` mogą być reprezentowane w następujący sposób.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Okrąg może być reprezentowany w następujący sposób.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Jeśli typ `Shape` podstawowy zawiera również element członkowski danych o nazwie "`radius`", prowadzi to do kolizji obu serializacji (ponieważ obiekty JSON nie mogą mieć powtarzających się nazw kluczy) i deserializacji (ponieważ nie jest jasne, czy "RADIUS" odwołuje się do `Shape.radius` czy `Circle.radius`). W związku z tym, Chociaż pojęcie "Ukrywanie właściwości" (składowe danych o tej samej nazwie w klasach opartych i pochodnych) nie jest ogólnie zalecane w klasach kontraktów danych, jest w rzeczywistości zabronione w przypadku JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm i typy IXmlSerializable

typy <xref:System.Xml.Serialization.IXmlSerializable> mogą być przypisywane do siebie, tak jak zwykle, o ile wymagania znanych typów są spełnione, zgodnie z typowymi regułami kontraktu danych. Jednak Serializacja typu <xref:System.Xml.Serialization.IXmlSerializable> zamiast <xref:System.Object> powoduje utratę informacji o typie, ponieważ wynik jest ciągiem JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm i niektóre typy interfejsów

Nie można serializować typu kolekcji lub typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>, gdzie nie jest typem kolekcji nie<xref:System.Xml.Serialization.IXmlSerializable> (z wyjątkiem <xref:System.Object>). Na przykład niestandardowy interfejs o nazwie `IMyInterface` i `MyType`, który implementuje obydwie <xref:System.Collections.Generic.IEnumerable%601> typu `int` i `IMyInterface`. Zwracanie `MyType` z operacji, której typem zwracanym jest `IMyInterface`, jest zabronione. Jest to spowodowane tym, że `MyType` musi być serializowana jako tablica JSON i wymaga wskazówki dotyczącej typu oraz jak określono przed dołączeniem wskazówki typu z tablicami tylko z typami złożonymi.

#### <a name="known-types-and-configuration"></a>Znane typy i konfiguracja

Wszystkie znane mechanizmy typu używane przez <xref:System.Runtime.Serialization.DataContractSerializer> są również obsługiwane w taki sam sposób przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Oba serializatory odczytują ten sam element konfiguracji, [\<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) w [\<system. runtime. Serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), aby odnaleźć znane typy dodane za pomocą pliku konfiguracji.

#### <a name="collections-assigned-to-object"></a>Kolekcje przypisane do obiektu

Kolekcje przypisane do obiektu są serializowane, tak jakby były kolekcjami implementującymi <xref:System.Collections.Generic.IEnumerable%601>: tablicę JSON z każdym wpisem, który ma wskazówkę typu, jeśli jest typem złożonym. Na przykład <xref:System.Collections.Generic.List%601> typu `Shape` przypisane do <xref:System.Object> wygląda następująco.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

W przypadku deserializacji z powrotem do <xref:System.Object>:

- `Shape` musi znajdować się na liście znanych typów. Posiadanie <xref:System.Collections.Generic.List%601> typu `Shape` w znanych typach nie ma żadnego wpływu. Należy pamiętać, że w tym przypadku nie trzeba dodawać `Shape` do znanych typów podczas serializacji — jest to wykonywane automatycznie.

- Kolekcja jest deserializowana jako <xref:System.Array> typu <xref:System.Object>, który zawiera wystąpienia `Shape`.

#### <a name="derived-collections-assigned-to-base-collections"></a>Kolekcje pochodne przypisane do kolekcji podstawowych

Gdy kolekcja pochodna jest przypisana do kolekcji podstawowej, kolekcja jest zwykle serializowana tak, jakby była kolekcją typu podstawowego. Jeśli jednak typ elementu kolekcji pochodnej nie może zostać przypisany do typu elementu kolekcji podstawowej, zostanie zgłoszony wyjątek.

#### <a name="type-hints-and-dictionaries"></a>Wskazówki i słowniki typów

Po przypisaniu słownika do <xref:System.Object>każdy wpis klucza i wartości w słowniku jest traktowany jak jeśli został przypisany do <xref:System.Object> i pobiera wskazówkę typu.

Podczas serializowania typów słowników, w ustawieniach `alwaysEmitTypeInformation` nie ma wpływ na obiekt JSON, który zawiera elementy członkowskie "Key" i "value".

### <a name="valid-json-key-names"></a>Prawidłowe nazwy kluczy JSON

Serializator XML dekoduje nazwy kluczy, które nie są prawidłowymi nazwami XML. Na przykład element członkowski danych o nazwie "123" będzie miał zakodowaną nazwę, taką jak "\_x0031\_\_x0032\_\_x0033\_", ponieważ "123" jest nieprawidłową nazwą elementu XML (rozpoczyna się od cyfry). Podobna sytuacja może wystąpić w przypadku niektórych międzynarodowych zestawów znaków, które nie są prawidłowe w nazwach XML. Aby uzyskać wyjaśnienie tego wpływu XML na przetwarzanie JSON, zobacz [Mapowanie między danymi JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
