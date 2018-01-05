---
title: Autonomiczna serializacja kodu JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8583ac00f1216e68f95c3d41d8c896b555d0aa8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stand-alone-json-serialization"></a>Autonomiczna serializacja kodu JSON
JSON (JavaScript Object Notation) to format danych przeznaczone do użycia przez kod JavaScript uruchomionych na stronach sieci Web w przeglądarce. Jest to domyślny format danych używany przez usługi ASP.NET AJAX utworzone w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Ten format można również tworzenie usług AJAX bez integracji z platformy ASP.NET — w takim przypadku XML jest domyślnie, ale można wybrać JSON.  
  
 Na koniec, jeśli jest wymagana obsługa JSON, ale nie są tworzone usługa AJAX <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> umożliwia bezpośrednio serializować obiekty .NET na dane JSON i deserializować tych danych do wystąpienia typów .NET. Opis jak to zrobić, zobacz [porady: serializacji i deserializacji danych JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Podczas pracy z formatu JSON, ten sam typ .NET są obsługiwane, z kilkoma wyjątkami, jak są obsługiwane przez <xref:System.Runtime.Serialization.DataContractSerializer>. Aby uzyskać listę obsługiwanych typów, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Obejmuje to najbardziej pierwotne typy, większość tablicy i typy kolekcji, również w złożonych typów używające <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>Mapowania typów .NET do typów JSON  
 W poniższej tabeli przedstawiono związek między typy .NET i JSON/JavaScript po zmapowaniu przez procedury serializacji i deserializacji.  
  
|Typy .NET|JSON/JavaScript|Uwagi|  
|----------------|----------------------|-----------|  
|Wszystkie typy liczbowe, na przykład <xref:System.Int32>, <xref:System.Decimal> lub<xref:System.Double>|Wartość liczbowa|Specjalne wartości, takich jak `Double.NaN`, `Double.PositiveInfinity` i `Double.NegativeInfinity` nie są obsługiwane i powoduje nieprawidłowe JSON.|  
|<xref:System.Enum>|Wartość liczbowa|Zobacz "Wyliczenia i JSON" w dalszej części tego tematu.|  
|<xref:System.Boolean>|Boolean|--|  
|<xref:System.String>, <xref:System.Char>|String|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Format tych typów w formacie JSON jest taki sam jak XML (zasadniczo TimeSpan w formacie ISO 8601 Duration, identyfikator GUID w formacie "12345678-ABCD-ABCD-ABCD-1234567890AB" oraz identyfikatora URI w postaci ciągu fizyczne, takie jak "http://www.example.com"). Aby uzyskać dokładne informacje, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|String|Ma format "Nazwa: przestrzeń nazw" (wszystko przed dwukropkiem pierwszy to nazwa). Nazwa lub obszar nazw może brakować. Brak obszaru nazw również można pominąć dwukropkiem.|  
|<xref:System.Array>typu<xref:System.Byte>|Tablica liczb|Każdy numer reprezentuje wartość jednego bajtu.|  
|<xref:System.DateTime>|Data/Godzina lub ciąg|Zobacz daty / godziny i JSON w dalszej części tego tematu.|  
|<xref:System.DateTimeOffset>|Typ złożony|Zobacz daty / godziny i JSON w dalszej części tego tematu.|  
|Typy XML i ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>., Tablice <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Zobacz sekcję typów XML i JSON w tym temacie.|  
|<xref:System.DBNull>|Pusty typu złożonego|--|  
|Kolekcje, słowniki i tablice|Tablica|Zobacz sekcję kolekcje, słowniki i tablic w tym temacie.|  
|Typy złożone (z <xref:System.Runtime.Serialization.DataContractAttribute> lub <xref:System.SerializableAttribute> zastosowane)|Typ złożony|Elementy członkowskie danych stają się elementami typu złożonego kodu JavaScript.|  
|Typy złożone implementacja <xref:System.Runtime.Serialization.ISerializable> interfejsu)|Typ złożony|Taki sam jak inne typy złożone, ale niektóre <xref:System.Runtime.Serialization.ISerializable> typy nie są obsługiwane — zobacz część ISerializable pomocy technicznej w sekcji Zaawansowane informacje w tym temacie.|  
|`Null`wartość dla każdego typu|Null|Typy dopuszczające wartości null są również obsługiwane i mapowanie do formatu JSON w taki sam sposób jak typów wartości null.|  
  
### <a name="enumerations-and-json"></a>Wyliczenia i JSON  
 Wartości elementu członkowskiego wyliczenia są traktowane jako liczby w formacie JSON, który jest inny niż jak są traktowane w kontraktach danych, w którym zostaną one dołączone jako nazwy elementów członkowskich. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]traktowanie, kontraktu danych zobacz [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Na przykład, jeśli masz `public enum Color {red, green, blue, yellow, pink}`, serializacji `yellow` tworzy liczbę 3, a nie ciąg "żółty".  
  
-   Wszystkie `enum` należą do serializacji. <xref:System.Runtime.Serialization.EnumMemberAttribute> i <xref:System.NonSerializedAttribute> atrybuty są ignorowane w przypadku użycia.  
  
-   Istnieje możliwość deserializacji nieistniejącą `enum` wartość — na przykład wartość 87 może być zdeserializowany do poprzedniego wyliczenia kolor nawet, jeśli nie wystąpi żadne odpowiadającą jej nazwą kolor zdefiniowany.  
  
-   Flagi `enum` nie specjalne i jest traktowane jako taki sam jak wszystkie inne `enum`.  
  
### <a name="datestimes-and-json"></a>Daty/godziny i JSON  
 JSON format nie obsługuje bezpośrednio daty i godziny. Jednak bardzo często są one używane i ASP.NET AJAX zapewnia specjalną obsługę tych typów. Korzystając z serwerów proxy ASP.NET AJAX, <xref:System.DateTime> typu w środowisku .NET pełni odpowiada `DateTime` typu w języku JavaScript.  
  
-   Gdy nie za pomocą programu ASP.NET, <xref:System.DateTime> typu jest reprezentowana w formacie JSON jako ciąg w formacie specjalne opisaną w sekcji Zaawansowane informacje w tym temacie.  
  
-   <xref:System.DateTimeOffset>jest wyświetlana w formacie JSON jako typ złożony: {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes` Element członkowski jest przesunięcie czasu lokalnego z czas uniwersalny Greenwich (GMT), teraz również określany jako uniwersalny czas koordynowany (UTC), związane z lokalizacją zdarzenia zainteresowań. `dateTime` Elementu członkowskiego reprezentuje wystąpienie w godzina wystąpienia zdarzenia zainteresowań (ponownie, staje się `DateTime` w języku JavaScript, jeśli ASP.NET AJAX w użycie i ciąg, gdy nie jest on). W serializacji `dateTime` Członek serializowany jest zawsze GMT. Jeśli opisujące 3:00 czasu Nowym Jorku, więc `dateTime` ma składnik godziny z 8:00 AM a `offsetMinutes` to 300 (minus 300 minut lub 5 godzin od GMT).  
  
    > [!NOTE]
    >  <xref:System.DateTime>i <xref:System.DateTimeOffset> obiektów serializować do notacji JSON, tylko zachować informacje dokładnością do milisekund. Wartości podrzędne milisekund (micro/nanosekundach) zostaną utracone podczas serializacji.  
  
### <a name="xml-types-and-json"></a>Typy XML i JSON  
 Typy XML stają się ciągi formatu JSON.  
  
-   Na przykład, jeśli element członkowski danych "q" z typu klasy XElement zawiera \<abc / >, jest w formacie JSON {"q": "\<abc / >"}.  
  
-   Istnieje kilka specjalnych zasad, które Określ sposób opakowana XML — Aby uzyskać więcej informacji, zobacz sekcję zaawansowane informacje w dalszej części tego tematu.  
  
-   Jeśli używasz środowiska ASP.NET AJAX i nie chcesz użyć ciągów w języku JavaScript, ale zamiast tego chcesz XML modelu DOM, ustaw <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> właściwości do pliku XML na <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości do pliku XML na <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Kolekcje, słowniki i tablice  
 Wszystkie kolekcje, słowniki i tablice są reprezentowane jako tablice w formacie JSON.  
  
-   Wszystkie dostosowania, który używa <xref:System.Runtime.Serialization.CollectionDataContractAttribute> jest ignorowana w reprezentacja JSON.  
  
-   Słowniki nie są sposób pracy bezpośrednio z formatu JSON. Słownik\<string, object > może nie być obsługiwana w taki sam sposób w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zgodnie z oczekiwaniami na współpracę z innymi technologiami JSON. Na przykład, jeśli "abc" jest zamapowany na "xyz" i "def" jest zamapowany na 42 w słowniku, reprezentacja JSON nie jest {"abc": "xyz", "def": 42}, ale jest [{"Klucz": "abc", "Wartość": "xyz"}, {"Klucz": "def", "Value": 42}] zamiast tego.  
  
-   Jeśli chcesz pracować bezpośrednio z JSON (Uzyskiwanie dostępu do kluczy i wartości dynamicznie, bez wstępnie definiujący kontrakt sztywne), masz kilka opcji:  
  
    -   Należy rozważyć użycie [słabą kontrolą serializacji JSON (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) próbki.  
  
    -   Należy rozważyć użycie <xref:System.Runtime.Serialization.ISerializable> konstruktorów interfejsu i deserializacji — umożliwiają dostęp do pary klucz wartość JSON na serializacji i deserializacji odpowiednio te dwa mechanizmy, ale nie działają w scenariuszach częściowo zaufanych.  
  
    -   Należy wziąć pod uwagę pracy z [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) zamiast przy użyciu serializatora.  
  
    -   *Polimorfizm* w kontekście serializacji odnosi się do możliwości serializacji typu pochodnego, których można oczekiwać jego typ podstawowy. Istnieją reguły specjalne specyficzne dla formatu JSON, podczas korzystania z kolekcji polymorphically, przypisując, na przykład, aby <xref:System.Object>. Ten problem jest bardziej dokładnie opisane w sekcji Zaawansowane informacje w dalszej części tego tematu.  
  
## <a name="additional-details"></a>Dodatkowe szczegóły  
  
### <a name="order-of-data-members"></a>Kolejność elementów członkowskich danych  
 Kolejność elementów członkowskich danych nie jest ważna, korzystając z formatu JSON. W szczególności, nawet jeśli <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ustawiono JSON danych może nadal być zdeserializowany, w dowolnej kolejności.  
  
### <a name="json-types"></a>Typy JSON  
 Typ JSON nie musi odpowiadać powyższej tabeli przy deserializacji. Na przykład `Int` zwykle mapy numer JSON, ale można też pomyślnie zdeserializowany z ciągu JSON pod warunkiem, że ciąg zawiera prawidłową liczbę. Oznacza to, że oba {"q": 42} i {"q": "42"} są prawidłowe w przypadku braku `Int` członka danych o nazwie "q".  
  
### <a name="polymorphism"></a>Polimorfizm  
 Serializacja polimorficznych składa się z możliwość serializować typ pochodny, których można oczekiwać jego typ podstawowy. Ta funkcja jest obsługiwana dla serializacji JSON przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializacja XML można porównywać pod względem sposobu jest obsługiwana. Na przykład można serializować `MyDerivedType` gdzie `MyBaseType` jest zgodne z oczekiwaniami albo serializować `Int` gdzie `Object` jest oczekiwany.  
  
 Informacje o typie mogą zostać utracone podczas deserializacji typem pochodnym, jeśli oczekiwany jest typ podstawowy, chyba że są deserializacji typu złożonego. Na przykład jeśli <xref:System.Uri> jest serializowany gdzie <xref:System.Object> oczekuje powoduje ciągu JSON. Jeśli ten ciąg jest następnie deserializowany do <xref:System.Object>, .NET <xref:System.String> jest zwracany. Deserializator nie wie, ciąg został początkowo typu <xref:System.Uri>. Ogólnie rzecz biorąc gdy oczekiwano <xref:System.Object>, wszystkie ciągi JSON są zdeserializować jako ciągi .NET i wszystkie tablice notacji JSON używany do serializacji kolekcji .NET, słowniki, i tablice są rozszeregować jako .NET <xref:System.Array> typu <xref:System.Object>, niezależnie od tego, co rzeczywisty typ oryginalny został. Wartość logiczna JSON mapuje .NET <xref:System.Boolean>. Jednak gdy oczekiwano <xref:System.Object>, numery JSON są rozszeregować jako albo .NET <xref:System.Int32>, <xref:System.Decimal> lub <xref:System.Double>, gdzie automatycznego pobrania najbardziej odpowiedniego typu.  
  
 Podczas deserializacji do typu interfejsu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializuje tak, jakby obiekt był deklarowanego typu.  
  
 Podczas pracy z własnych typów podstawowych i pochodnych, za pomocą <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> lub równoważnego mechanizmu jest zwykle wymagane. Na przykład, jeśli masz operację, która ma `Animal` zwracać wartości i faktycznie zwraca moduł wystąpienia `Cat` (pochodną `Animal`), albo stosuje <xref:System.Runtime.Serialization.KnownTypeAttribute>, do `Animal` typu lub <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operację i określ `Cat` typu w tych atrybutów. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Szczegółowe informacje, jak polimorficznych prac serializacji i omówienie niektóre ograniczenia, które należy przestrzegać podczas korzystania z niego zobacz sekcję zaawansowane informacje w dalszej części tego tematu.  
  
### <a name="versioning"></a>Przechowywanie wersji  
 Funkcji przechowywania wersji, w tym kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, są w pełni obsługiwane w formacie JSON. Ponadto, w większości przypadków użytkownik może deserializować typu w jednym formacie (na przykład XML) i serializować go w innym formacie (na przykład JSON) i nadal zachowania danych w <xref:System.Runtime.Serialization.IExtensibleDataObject>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Należy pamiętać, że JSON jest nieuporządkowaną, więc wszystkie informacje o kolejności zostaną utracone. Ponadto JSON nie obsługuje wielu pary klucz wartość o takiej samej nazwie klucza. Ponadto wszystkie operacje na <xref:System.Runtime.Serialization.IExtensibleDataObject> są z założenia polimorficznych - będący ich typ pochodny są przypisane do <xref:System.Object>, typ podstawowy dla wszystkich typów.  
  
## <a name="json-in-urls"></a>JSON w adresach URL  
 Podczas korzystania z punktów końcowych ASP.NET AJAX z zlecenie HTTP GET (przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute> atrybut), parametry przychodzące są wyświetlane w adresie URL żądania, zamiast treść komunikatu. JSON jest obsługiwany, nawet w adresie URL żądania, tak więc jeśli masz operację, która przyjmuje `Int` o nazwie "numer" i `Person` typu złożonego o nazwie "p", adres URL może przypominać następujący adres URL.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Jeśli używasz kontrolki Menedżera skryptów AJAX ASP.NET i serwera proxy do wywołania tej usługi, ten adres URL jest generowana automatycznie przez serwer proxy i nie jest widoczne. JSON nie można używać w adresach URL dla punktów końcowych - ASP.NET AJAX.  
  
## <a name="advanced-information"></a>Zaawansowane informacje  
  
### <a name="iserializable-support"></a>Obsługa iSerializable  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Obsługiwane i nieobsługiwane typy ISerializable  
 Ogólnie rzecz biorąc, typy, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejsu są w pełni obsługiwane podczas serializacji/deserializacji JSON. Jednak niektóre z tych typów (w tym niektórych typów .NET Framework) są wykonywane w taki sposób, aspekty serializacji JSON specyficzne spowodować ich zdeserializować nie prawidłowo:  
  
-   Z <xref:System.Runtime.Serialization.ISerializable>, typ danych poszczególnych członków nigdy nie jest znany wcześniej. Prowadzi to do sytuacji polimorficznych podobne do deserializacji do obiektu typu. Jak wspomniano wcześniej, może to doprowadzić do utraty informacji o typie w formacie JSON. Na przykład typ, który serializuje `enum` w jego <xref:System.Runtime.Serialization.ISerializable> implementacji i podejmuje próbę deserializacji z powrotem bezpośrednio do `enum` (bez prawidłowego rzutowania) nie powiedzie się, ponieważ `enum` jest serializowany w postaci liczb w formacie JSON i JSON deserializuje liczb na wbudowane typy liczbowe .NET (Int32, Decimal lub o podwójnej precyzji). Dlatego fakt użytą jako numer `enum` wartości zostaną utracone.  
  
-   <xref:System.Runtime.Serialization.ISerializable> Typu, który jest zależny od określonej kolejności deserializacji w Konstruktorze jego deserializacji może również się nie powieść deserializacji niektóre dane JSON, ponieważ większość serializatorów JSON nie gwarantuje dowolnej kolejności.  
  
#### <a name="factory-types"></a>Typy fabryki  
 Gdy <xref:System.Runtime.Serialization.IObjectReference> interfejs jest obsługiwany w formacie JSON na ogół żadnych typów, które wymagają funkcji "Typ fabryki" (zwracanie wystąpienia innego typu niż <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> niż typ, który implementuje interfejs) nie są obsługiwane.  
  
### <a name="datetime-wire-format"></a>Format daty/godziny podczas transmisji  
 <xref:System.DateTime>wartości są wyświetlane jako ciągi JSON w formie "/ Date(700000+0500) /", gdzie numer pierwszej (700000 w przykładzie przedstawionym) to wyrażony w milisekundach czas w strefie czasowej GMT regularne (z systemem innym niż-letniego) czas od północy, 1 stycznia 1970. Liczba może być ujemna do reprezentowania wcześniejszych razy. Element, który składa się z "+0500" w tym przykładzie jest opcjonalna i wskazuje, że czas jest o <xref:System.DateTimeKind.Local> rodzaj — to znaczy powinny być konwertowane na lokalnej strefie czasowej przy deserializacji. Jeśli nie ma czasu jest rozszeregować jako <xref:System.DateTimeKind.Utc>. Rzeczywista liczba ("0500" w tym przykładzie) i znaku (+ lub -) są ignorowane.  
  
 Podczas serializowania <xref:System.DateTime>, <xref:System.DateTimeKind.Local> i <xref:System.DateTimeKind.Unspecified> czasy są zapisywane z przesunięciem i <xref:System.DateTimeKind.Utc> napisano bez.  
  
 Kod JavaScript klienta ASP.NET AJAX powoduje automatyczną konwersję takich ciągów na język JavaScript `DateTime` wystąpień. Jeśli istnieją inne ciągów, które mają podobne formularza, które nie są typu <xref:System.DateTime> w środowisku .NET, zostaną one przetworzone również.  
  
 Konwersja tylko ma miejsce, jeśli będą miały zmienione znaczenie znaków "/" (czyli JSON wygląda następująco: "\\/Date(700000+0500)\\/") i z tego powodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]przez koder JSON (włączane przez <xref:System.ServiceModel.WebHttpBinding>) zawsze specjalne "/" znak.  
  
### <a name="xml-in-json-strings"></a>XML w ciągach formatu JSON  
  
#### <a name="xmlelement"></a>Element XmlElement  
 <xref:System.Xml.XmlElement>jest serializowany, ponieważ jest z bez zawijania. Na przykład elementu członkowskiego danych "x" typu <xref:System.Xml.XmlElement> zawierający \<abc / > jest reprezentowany w następujący sposób.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>Tablic elementów XmlNode  
 <xref:System.Array>obiekty typu <xref:System.Xml.XmlNode> są ujęte w element o nazwie ArrayOfXmlNode w przestrzeni nazw kontraktu danych standardowych dla typu. Jeśli tablica zawierająca węzła atrybutu "N" w przestrzeni nazw "ns", który zawiera "value" i węzeł pustego elementu "M", "x" reprezentacja ma następującą składnię.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 Atrybuty w pustej przestrzeni nazw na początku XmlNode tablic (przed innymi elementami) nie są obsługiwane.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy interfejsu IXmlSerializable, w tym klasy XElement i zestawu danych  
 <xref:System.Runtime.Serialization.ISerializable>typy podzielić na "typy zawartości", "Typów zestawu danych" i "typów elementów". Dla definicji tego typu, zobacz [typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "Zawartość" i "Zestawu danych" typy są serializowane podobny do <xref:System.Array> obiektów <xref:System.Xml.XmlNode> opisanych w poprzedniej sekcji. Są one ujęte w element o nazwie i przestrzeni nazw odpowiada nazwie kontraktu danych i przestrzeni nazw typu zagrożona.  
  
 "Element" typów, takie jak <xref:System.Xml.Linq.XElement> są serializowane, tak jak, podobnie jak <xref:System.Xml.XmlElement> wcześniej omówione w tym temacie.  
  
### <a name="polymorphism"></a>Polimorfizm  
  
#### <a name="preserving-type-information"></a>Informacje o typie zachowania  
 Jak wspomniano wcześniej, polimorfizm jest obsługiwane w formacie JSON z pewnymi ograniczeniami. JavaScript jest językiem słabą kontrolą i typ tożsamości zwykle nie jest istotna. Korzystając z formatu JSON do komunikacji między systemem jednoznacznie (.NET) i słabą kontrolą systemu (JavaScript), zaleca się zachowanie tożsamości typu. Na przykład typy danych kontraktu nazwy "Kwadrat" i "Koło" pochodzi z typu o nazwie kontraktu danych "Kształtu". Jeśli "Okrąg" są wysyłane z .NET do języka JavaScript, a później są zwracane do metody .NET, która oczekuje "Kształtu", jest przydatne w przypadku po stronie .NET dowiedzieć się, że danego obiektu pierwotnie "Okrąg" — w przeciwnym razie żadnych informacji specyficznych dla typu pochodnego (np. element członkowski danych "radius" na "Okręgu") mogą zostać utracone.  
  
 Aby zachować typu tożsamości, gdy serializacji typy złożone do formatu JSON wskazówkę"typu" można dodać, a Deserializator rozpoznaje wskazówka i działa prawidłowo. Wskazówka"typu" jest parę klucz/wartość JSON z nazwą klucza "__type" (dwa podkreślenia następuje słowo "type"). Wartość jest ciągiem JSON w postaci "DataContractName:DataContractNamespace" (niczego do pierwszego dwukropka to nazwa). Przy użyciu wcześniejszego przykładu, "Okrąg" może być Zserializowany w następujący sposób.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 Wskazówka typu jest bardzo podobny do `xsi:type` atrybutu zdefiniowanym przez standardowe wystąpienie schematu XML, używane podczas serializacji/deserializacji XML.  
  
 Elementy członkowskie danych o nazwie "__type" są zabronione ze względu na potencjalne konflikt ze wskazówką typu.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Zmniejszenie rozmiaru wskazówek typu  
 Aby zmniejszyć rozmiar wiadomości w formacie JSON, prefiks przestrzeni nazw kontraktu danych domyślne (http://schemas.datacontract.org/2004/07/) jest zastępowany znaku "#". (Aby zamiany odwracalny, ucieczki reguła jest używana: Jeśli przestrzeń nazw rozpoczyna się od znaku "#" lub "\\" znaki, są dołączony dodatkowy "\\" znaków). W związku z tym "Okrąg" jest typem w przestrzeni nazw .NET "MyApp.Shapes", jego domyślnej przestrzeni nazw kontraktu danych jest http://schemas.datacontract.org/2004/07/MyApp. Kształty i reprezentacja JSON ma następującą składnię.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Zarówno skróconą (#MyApp.Shapes), jak i nazwy pełny (http://schemas.datacontract.org/2004/07/MyApp.Shapes) jest rozpoznawany przy deserializacji.  
  
#### <a name="type-hint-position-in-json-objects"></a>Typ pozycji wskazówka obiektów JSON  
 Należy pamiętać, że wskazówki dotyczącej typu musi występować jako pierwszy w reprezentacja JSON. Jest to tylko wówczas, gdy kolejność par klucz/wartość jest ważna w formacie JSON przetwarzania. Na przykład następujący ciąg nie jest prawidłową sposobem określania wskazówki dotyczącej typu.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Zarówno <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> używane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i strony klienta ASP.NET AJAX najpierw zawsze Emituj wskazówki dotyczącej typu.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Typ stosuje się tylko do typów złożonych  
 Nie istnieje sposób można wyemitować wskazówkę typu dla typów innych niż złożone. Na przykład, jeśli operacja ma <xref:System.Object> zwracany typ, ale zwraca koło, może być reprezentacja JSON, jak pokazano wcześniej i informacje o typie zostaną zachowane. Jednak jeśli identyfikator Uri jest zwracany, reprezentacja JSON jest ciągiem i fakt, że ciąg używany do reprezentowania identyfikatora Uri jest utracone. Dotyczy to nie tylko typy pierwotne, ale również do kolekcji i tablic.  
  
#### <a name="when-are-type-hints-emitted"></a>Gdy są emitowane wskazówek typu  
 Typ wskazówki może zwiększyć rozmiar komunikatu znacznie (Aby zmniejszyć to Użyj krótszej przestrzeni nazw kontraktu danych, jeśli to możliwe). W związku z tym następujące reguły decydować, czy są emitowane typu wskazówek:  
  
-   Gdy za pomocą kodu ASP.NET AJAX, wskazówki dotyczące typu są zawsze emitowane Jeśli to możliwe, nawet jeśli dostępny jest brak przypisania bazową/dziedziczoną — na przykład, nawet jeśli koło jest przypisany do okręgu. (Jest to wymagane, aby w pełni włączyć proces wywoływania ze środowiska JSON słabą kontrolą do środowiska .NET jednoznacznie zaskakująco bez utraty informacji.)  
  
-   Podczas korzystania z usług AJAX z Brak integracji ASP.NET, po przypisaniu bazową/dziedziczoną - emitowanego gdy kółko jest przypisany do kształtu typu wskazówki tylko są emitowane lub <xref:System.Object> , ale nie po przypisaniu do okręgu. Zawiera minimalne informacje wymagane do poprawnego zaimplementowania klienta JavaScript, co poprawia wydajność, ale nie chroni przed utratą informacji typu w klientach niepoprawnie zaprojektowane. Całkowicie Unikaj bazową/dziedziczoną przypisań na serwerze, jeśli chce się uniknąć dotyczącą tego problemu na kliencie.  
  
-   Korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> typu `alwaysEmitTypeInformation` parametru Konstruktora Umożliwia wybór między poprzednim dwa tryby z są domyślne "`false`" (Emituj tylko typ wskazówek, gdy jest to wymagane).  
  
#### <a name="duplicate-data-member-names"></a>Zduplikowane nazwy elementów członkowskich danych  
 Typ pochodny informacji znajduje się w ten sam obiekt JSON, wraz z informacjami w typie podstawowym, a może wystąpić w dowolnej kolejności. Na przykład `Shape` mogą być reprezentowane w następujący sposób.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Podczas gdy kółko mogą być reprezentowane w następujący sposób.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Jeśli bazie `Shape` typu zawiera również element członkowski danych o nazwie "`radius`", to prowadzi do kolizji na obu serializacji (ponieważ obiektów JSON nie może mieć powtarzające się nazwy kluczy) oraz deserializację (ponieważ nie jest jasne, czy "radius" odwołuje się do `Shape.radius` lub `Circle.radius`). W związku z tym podczas pojęcie "ukrywanie właściwości" (elementy członkowskie danych o takiej samej nazwie, na podstawie i klasy pochodne) jest zwykle nie jest zalecane w klasach kontraktu danych, faktycznie jest zabroniony w przypadku JSON.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm i typów IXmlSerializable  
 <xref:System.Xml.Serialization.IXmlSerializable>typy mogły zostać polymorphically przypisane do siebie nawzajem w zwykły sposób tak długo, jak są spełnione wymagania znane typy, zgodnie z regułami kontraktu danych zwykle. Jednak serializacji <xref:System.Xml.Serialization.IXmlSerializable> wpisz zamiast <xref:System.Object> powoduje utratę danych typu jako wynik jest ciągiem formatu JSON.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm i niektórych typów interfejsów  
 Jest zabronione serializować typ kolekcji lub typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> w przypadku, gdy typ innych niż kolekcji, który nie jest <xref:System.Xml.Serialization.IXmlSerializable> (z wyjątkiem <xref:System.Object>) jest oczekiwany. Na przykład niestandardowy interfejs o nazwie `IMyInterface` i typ `MyType` implementować jednocześnie <xref:System.Collections.Generic.IEnumerable%601> typu `int` i `IMyInterface`. Zwracany jest zabronione `MyType` z operacji, których typem zwracanym jest `IMyInterface`. Jest to spowodowane `MyType` muszą być zserializowane jako tablica JSON i wymaga wskazówkę typu i podaną przed nie może zawierać wskazówkę typu z tablicami tylko z typów złożonych.  
  
#### <a name="known-types-and-configuration"></a>Znane typy i konfiguracji  
 Wszystkie te mechanizmy znany typ używany przez <xref:System.Runtime.Serialization.DataContractSerializer> są również obsługiwane w taki sam sposób przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Serializatorów zarówno do odczytu tego samego elementu konfiguracji [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) w [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), aby odnaleźć dodany ze znanych typów za pomocą pliku konfiguracji.  
  
#### <a name="collections-assigned-to-object"></a>Kolekcji przypisanych do obiektu  
 Kolekcji przypisanych do obiektu są serializowane, tak jakby są kolekcje, które implementują <xref:System.Collections.Generic.IEnumerable%601>: tablica JSON z każdego wpisu, który ma typ wskazówkę, jeśli jest typem złożonym. Na przykład <xref:System.Collections.Generic.List%601> typu `Shape` przypisane do <xref:System.Object> wygląda podobnie do następującego.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Podczas deserializacji do <xref:System.Object>:  
  
-   `Shape`musi należeć do listy znanych typów. O <xref:System.Collections.Generic.List%601> typu `Shape` w znanych typów nie ma wpływu. Należy pamiętać, że nie trzeba dodać `Shape` do znanych typów na serializacji w takim przypadku - odbywa się to automatycznie.  
  
-   Kolekcja jest rozszeregować jako <xref:System.Array> typu <xref:System.Object> zawierający `Shape` wystąpień.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Pochodne kolekcji przypisanych do kolekcji podstawowej  
 Gdy pochodnej kolekcji jest przypisany do kolekcji podstawowej, kolekcji zwykle jest serializowany tak, jakby był kolekcję typu podstawowego. Jednak jeśli typ elementu kolekcji pochodnych nie można przypisać do typu elementu podstawowego kolekcji, jest zwracany wyjątek.  
  
#### <a name="type-hints-and-dictionaries"></a>Wskazówki dotyczące typu i słowników  
 Jeśli słownik jest przypisany do <xref:System.Object>, każdy wpis kluczy i wartości w słowniku jest traktowana tak, jakby został przypisany do <xref:System.Object> i pobiera wskazówkę typu.  
  
 Podczas serializowania typów słownika, obiekt JSON, który zawiera elementy członkowskie "Klucz" a "Wartość" jest poza zasięgiem `alwaysEmitTypeInformation` ustawienie i zawiera tylko wskazówkę typu podczas wymagają powyższych zasad kolekcji.  
  
### <a name="valid-json-key-names"></a>Nazwy kluczy poprawne dane JSON  
 Nazwy kluczy serializator koduje XML, które nie są prawidłowe nazwy XML. Na przykład element członkowski danych o nazwie "123" miałyby zakodowane nazwy takie jak "_x0031\__x0032\__x0033\_" ponieważ "123" jest nieprawidłową nazwą — element XML (rozpoczyna się od cyfry). Podobna sytuacja mogą wynikać z niektóre zestawy znaków międzynarodowych nie jest prawidłowa w nazw XML. Aby uzyskać informacje o tej wpływa XML na przetwarzanie JSON, zobacz [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
