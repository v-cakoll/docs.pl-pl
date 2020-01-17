---
title: Mapowanie między formatami JSON i XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 0dbe37a07024ae70e574b92582715d2d2ef52e5c
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212089"
---
# <a name="mapping-between-json-and-xml"></a>Mapowanie między formatami JSON i XML
Czytelnicy i autorzy wytwarzani przez <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> udostępniają zawartość XML API over JavaScript Object Notation (JSON). KOD JSON koduje dane przy użyciu podzestawu literałów obiektów JavaScript. Czytelnicy i autorzy wytwarzani przez tę fabrykę są również używani, gdy zawartość JSON jest wysyłana lub odbierana przez aplikacje Windows Communication Foundation (WCF) przy użyciu <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> lub <xref:System.ServiceModel.WebHttpBinding>.

Po zainicjowaniu z zawartością JSON, czytnik JSON zachowuje się tak samo, jak czytnik tekstowy XML w przypadku wystąpienia XML. Składnik zapisywania JSON, gdy dana sekwencja wywołań, które w czytniku tekstowym XML tworzy pewne wystąpienie XML, zapisuje zawartość JSON. Mapowanie między tym wystąpieniem XML a zawartością JSON zostało opisane w tym temacie do użycia w zaawansowanych scenariuszach.

Wewnętrznie, JSON jest reprezentowane jako sprawdzonych XML podczas przetwarzania przez WCF. Zwykle nie trzeba się omawiać w tej wewnętrznej reprezentacji, ponieważ mapowanie jest tylko logicznym: JSON zwykle nie jest fizycznie konwertowane na XML w pamięci lub konwertowane na notację JSON z pliku XML. Mapowanie oznacza, że interfejsy API XML są używane w celu uzyskania dostępu do zawartości JSON.

Gdy WCF korzysta z JSON, typowym scenariuszem jest to, że <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jest automatycznie podłączany przez zachowanie <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> lub przez zachowanie <xref:System.ServiceModel.Description.WebHttpBehavior>, gdy jest to konieczne. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> rozumie mapowanie między formatem JSON i sprawdzonych XML i działa tak, jakby dotyczyć bezpośrednio kodu JSON. (Możliwe jest użycie <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> z dowolnym czytelnikem lub modułem zapisu XML, co oznacza, że kod XML jest zgodny z poniższym mapowaniem).

W zaawansowanych scenariuszach może być konieczne uzyskanie bezpośredniego dostępu do poniższego mapowania. Te scenariusze występują, gdy chcesz serializować i deserializować kod JSON w sposób niestandardowy, bez polegania na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>lub w przypadku <xref:System.ServiceModel.Channels.Message> typu bezpośrednio dla komunikatów zawierających kod JSON. Mapowanie JSON-XML jest również używane do rejestrowania komunikatów. W przypadku korzystania z funkcji rejestrowania komunikatów w programie WCF komunikaty JSON są rejestrowane jako XML zgodnie z mapowaniem opisanym w następnej sekcji.

Aby wyjaśnić koncepcję mapowania, Poniższy przykład jest dokumentem JSON.

```json
{"product":"pencil","price":12}
```

Aby odczytać ten dokument JSON przy użyciu jednego z wymienionych wcześniej czytników, Użyj tej samej sekwencji <xref:System.Xml.XmlDictionaryReader> wywołań, co pozwoli odczytać następujący dokument XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ponadto, jeśli komunikat JSON w przykładzie jest odbierany przez WCF i rejestrowany, w poprzednim dzienniku zobaczysz fragment kodu XML.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapowanie między elementami JSON i sprawdzonych XML

Od tego momentu mapowanie ma postać między kodem JSON opisanym w [dokumencie RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) (z wyjątkiem pewnych ograniczeń, które są ograniczone i niektóre inne ograniczenia) oraz XML sprawdzonych (i nie tekst XML) zgodnie z opisem w [zestawie informacji XML](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/). Zapoznaj się z tym tematem definicje elementów i pól *informacji* w [nawiasy kwadratowe].

Pusty dokument JSON jest mapowany do pustego dokumentu XML, a pusty dokument XML jest mapowany do pustego dokumentu JSON. W przypadku mapowania XML do formatu JSON poprzedzający biały znak i końcowe białe znaki po dokumencie są niedozwolone.

Mapowanie jest zdefiniowane między elementem informacji o dokumencie (DII) lub elementem informacji o elemencie (EII) i JSON. EII lub właściwość DII [Document element] jest określana mianem głównego elementu JSON. Należy zauważyć, że fragmenty dokumentu (XML z wieloma elementami głównymi) nie są obsługiwane w ramach tego mapowania.

Przykład: następujący dokument:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

I następujący element:

```xml
<root type="number">42</root>
```

Oba mają mapowanie na format JSON. Element <`root`> jest głównym elementem JSON w obu przypadkach.

Ponadto w przypadku DII należy wziąć pod uwagę następujące kwestie:

- Niektóre elementy na liście [Children] nie mogą być obecne. Nie należy polegać na tym fakcie podczas odczytywania kodu XML zamapowanego z formatu JSON.

- Lista [Children] nie zawiera żadnych elementów informacji o komentarzach.

- Lista [Children] nie zawiera żadnych elementów informacji DTD.

- Lista [Children] nie zawiera żadnych elementów informacji osobistych (PI) (Deklaracja `<?xml…>` nie jest uważana za element informacji o liczbie PI)

- Zestaw [Notations] jest pusty.

- Zestaw [nieanalizowane jednostki] jest pusty.

Przykład: następujący dokument nie ma mapowania na kod JSON, ponieważ element [Children] zawiera znak PI i komentarz.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII dla głównego elementu JSON ma następującą charakterystykę:

- [nazwa lokalna] ma wartość "root".

- [nazwa przestrzeni nazw] nie ma wartości.

- [prefix] nie ma wartości.

- [elementy podrzędne] mogą zawierać EIIs (reprezentujący elementy wewnętrzne zgodnie z opisem) lub CIIs (elementy informacji o znakach, jak opisano w dalszej części) lub żadne z nich, ale nie oba.

- [atrybuty] mogą zawierać następujące opcjonalne elementy informacji o atrybucie (AIIs)

- Atrybut typu JSON ("Type"), zgodnie z opisem w dalszej postaci. Ten atrybut służy do zachowania typu JSON (ciąg, liczba, wartość logiczna, obiekt, tablica lub wartość null) w mapowanym kodzie XML.

- Atrybut nazwy kontraktu danych ("\_\_typ"), zgodnie z opisem w dalszej postaci. Ten atrybut jest dostępny tylko wtedy, gdy atrybut typu JSON jest również obecny i jego [znormalizowana wartość] to "Object". Ten atrybut jest używany przez `DataContractJsonSerializer` do zachowania informacji o typie kontraktu danych — na przykład w przypadkach polimorficznych, w których typ pochodny jest serializowany i gdy oczekiwany jest typ podstawowy. Jeśli nie pracujesz z `DataContractJsonSerializer`, w większości przypadków ten atrybut jest ignorowany.

- [przestrzenie nazw w zakresie] zawierają powiązanie "XML" do `http://www.w3.org/XML/1998/namespace` zgodnie z zaleceniami specyfikacji sprawdzonych.

- [elementy podrzędne], [atrybuty] i [przestrzenie nazw w zakresie] nie mogą zawierać elementów innych niż określone wcześniej, a [atrybuty przestrzeni nazw] nie mogą mieć żadnych elementów członkowskich, ale nie należy polegać na tych faktach podczas odczytywania danych XML mapowanych z formatu JSON.

Przykład: następujący dokument nie ma mapowania na kod JSON, ponieważ atrybuty [Namespace] nie są puste.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

WSZYSTKO dla atrybutu typu JSON ma następującą charakterystykę:

- [nazwa przestrzeni nazw] nie ma wartości.
- [prefix] nie ma wartości.
- [nazwa lokalna] to "typ".
- [znormalizowana wartość] to jedno z możliwych wartości typu opisanych w poniższej sekcji.
- [określony] jest `true`.
- [typ atrybutu] nie ma wartości.
- [References] nie ma wartości.

WSZYSTKO dla atrybutu nazwy kontraktu danych ma następującą charakterystykę:

- [nazwa przestrzeni nazw] nie ma wartości.
- [prefix] nie ma wartości.
- [nazwa lokalna] to "\_\_typ" (dwie podkreślenia, a następnie "Type").
- [znormalizowana wartość] jest dowolnym prawidłowym ciągiem Unicode — mapowanie tego ciągu na format JSON jest opisane w poniższej sekcji.
- [określony] jest `true`.
- [typ atrybutu] nie ma wartości.
- [References] nie ma wartości.

Elementy wewnętrzne zawarte w głównym elemencie JSON lub inne elementy wewnętrzne mają następującą charakterystykę:

- [nazwa lokalna] może mieć dowolną wartość, zgodnie z opisem.
- [nazwa przestrzeni nazw], [prefiks], [elementy podrzędne], [atrybuty], [atrybuty przestrzeni nazw] i [przestrzenie nazw w zakresie] są objęte tymi samymi regułami, co główny element JSON.

Zarówno w głównym elemencie JSON, jak i elementach wewnętrznych, atrybut typu JSON definiuje mapowanie do formatu JSON oraz możliwe [elementy podrzędne] i ich interpretację. Atrybut [znormalizowana wartość] ma wielkość liter i musi być pisany małymi literami i nie może zawierać białych znaków.

|[znormalizowana wartość] wszystko atrybutu typu JSON|Dozwolone elementy [Children] odpowiadającego EII|Mapowanie do formatu JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (lub brak typu JSON wszystko)<br /><br /> `string` i brak typu JSON wszystko są takie same, `string` wartością domyślną.<br /><br /> Dlatego `<root> string1</root>` są mapowane na kod JSON `string` "ciąg1".|0 lub więcej CIIs|`string` JSON (kod JSON RFC, sekcja 2,5). Każdy `char` jest znakiem, który odnosi się do [kod znaku] z CII. Jeśli nie ma żadnych CIIs, mapuje do pustego `string`JSON.<br /><br /> Przykład: następujący element mapuje do fragmentu JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> Fragment JSON to "42".<br /><br /> W przypadku mapowania XML do formatu JSON znaki, które muszą mieć sekwencję ucieczki do znaków ucieczki, wszystkie inne są mapowane na znaki, które nie są wyprowadzane. Znak "/" jest specjalny — oznacza, że jest on zmieniony, mimo że nie musi być (zapisany jako "\\/").<br /><br /> Przykład: Poniższy element mapuje do fragmentu JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment JSON to "\\" da\\/ta\\"".<br /><br /> W mapowaniu JSON na XML, wszelkie znaki ucieczki i znaki, które nie są poprawnie mapowane na mapę, do odpowiadającego [znakowego kodu].<br /><br /> Przykład: fragment JSON "\u0041BC" mapuje do następującego elementu XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Ciąg może być otoczony białym znakiem ("ws" w sekcji 2 dokumentu JSON RFC), który nie jest mapowany do formatu XML.<br /><br /> Przykład: fragment JSON "ABC" (zawiera spacje przed pierwszym cudzysłowem), mapuje do następującego elementu XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dowolny biały znak w programie XML mapuje do białego miejsca w formacie JSON.<br /><br /> Przykład: Poniższy element XML mapuje do fragmentu JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Fragment JSON to "A BC".|
|`number`|1 lub więcej CIIs|`number` JSON (kod JSON RFC, sekcja 2,4), prawdopodobnie ujęty w białe znaki. Każdy znak w kombinacji liczby/odstępu jest znakiem, który odnosi się do [kod znaku] z CII.<br /><br /> Przykład: Poniższy element mapuje do fragmentu JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Fragment JSON to 42<br /><br /> (Biały znak jest zachowywany).|
|`boolean`|4 lub 5 CIIs (który odnosi się do `true` lub `false`), prawdopodobnie otoczony dodatkowymi białymi miejscami CIIs.|Sekwencja CII odpowiadająca ciągowi "true" jest mapowana na literał `true`, a sekwencja CII, która odpowiada ciągowi "false", jest mapowana na `false`literału. Zachowywany jest biały znak.<br /><br /> Przykład: Poniższy element mapuje do fragmentu JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment JSON jest `false`.|
|`null`|Brak dozwolonych.|Literał `null`. W mapowaniu JSON na XML, `null` może być otoczona białym znakiem ("ws" w sekcji 2), który nie jest mapowany do formatu XML.<br /><br /> Przykład: Poniższy element mapuje do fragmentu JSON.<br /><br /> `<root type="null"/>`<br /><br /> lub<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment kodu JSON w obu przypadkach jest `Null`.|
|`object`|0 lub więcej EIIs.|`begin-object` (lewy nawias klamrowy) jak w sekcji 2,2 specyfikacji RFC JSON, a następnie rekord elementu członkowskiego dla każdego EIIu, zgodnie z opisem. Jeśli istnieje więcej niż jeden EII, istnieją separatory wartości (przecinki) między rekordami elementu członkowskiego. Po nim następuje obiekt końcowy (prawy nawias klamrowy).<br /><br /> Przykład: Poniższy element jest mapowany do fragmentu JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Fragment JSON jest `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Jeśli atrybut typu kontraktu danych jest obecny w mapowaniu XML do formatu JSON, na początku zostanie wstawiony dodatkowy rekord elementu członkowskiego. Jego nazwą jest [local name] atrybutu typu kontraktu danych ("\_\_Type"), a jego wartością jest [znormalizowana wartość]. Z kolei w przypadku mapowania JSON na XML, jeśli nazwa pierwszego elementu członkowskiego rekordu to [lokalna nazwa] atrybutu typu kontraktu danych (czyli "\_\_typ"), odpowiedni atrybut typu kontraktu danych jest obecny w mapowanym kodzie XML, ale nie ma odpowiedniego EII. Należy zauważyć, że ten rekord elementu członkowskiego musi wystąpić najpierw w obiekcie JSON dla tego mapowania specjalnego do zastosowania. Reprezentuje to wyjście z normalnego przetwarzania JSON, w którym kolejność rekordów elementów członkowskich nie jest istotna.<br /><br /> Przykład:<br /><br /> Poniższy fragment kodu JSON jest mapowany na format XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Kod XML jest poniższym kodem.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Zauważ, że \_\_typu wszystko jest obecny, ale nie ma \_\_typu EII.<br /><br /> Jeśli jednak porządek w kodzie JSON zostanie odwrócony, jak pokazano w poniższym przykładzie.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Wyświetlany jest odpowiedni kod XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Oznacza to, że \__type przestaje mieć specjalne znaczenie i jest mapowany na EII w zwykły sposób, a nie wszystko.<br /><br /> Reguły ucieczki/anulowania ucieczki dla [znormalizowanej wartości] wszystko są takie same jak w przypadku ciągów JSON określonych w wierszu "String" tej tabeli.<br /><br /> Przykład:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> do poprzedniego przykładu można zamapować do poniższego kodu JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> W przypadku mapowania XML do formatu JSON pierwszy EII [nazwa lokalna] nie może być "\_\_typu".<br /><br /> Białe znaki (`ws`) nigdy nie są generowane w mapowaniu XML na notację JSON dla obiektów i są ignorowane w mapowaniu JSON na XML.<br /><br /> Przykład: Poniższy fragment kodu JSON jest mapowany na element XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> Element XML jest pokazany w poniższym kodzie.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|tablica|0 lub więcej EIIs|Tablica BEGIN-Array (lewy nawias kwadratowy), jak w sekcji 2,3 w formacie JSON, a następnie rekord tablicy dla każdego EIIu, zgodnie z opisem w dalszej części. Jeśli istnieje więcej niż jeden EII, istnieją separatory wartości (przecinki) między rekordami tablicy. Jest to po nim tablica końcowa.<br /><br /> Przykład: Poniższy element XML mapuje do fragmentu JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Fragment JSON jest `["aaa","bbb"]`<br /><br /> Białe znaki (`ws`) nigdy nie są generowane w mapowaniu XML do formatu JSON dla tablic i są ignorowane w mapowaniu JSON na XML.<br /><br /> Przykład: fragment JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> Element XML, który jest mapowany na.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Rekordy elementów członkowskich działają w następujący sposób:

- Element wewnętrzny [local name] mapuje do `string`ej części `member` zgodnie z definicją w sekcji 2,2 specyfikacji RFC JSON.

Przykład: Poniższy element mapuje do fragmentu JSON.

```xml
<root type="object"/>
<myLocalName type="string">aaa</myLocalName>
</root >
```

Zostanie wyświetlony następujący fragment kodu JSON.

```json
{"myLocalName":"aaa"}
```

- W przypadku mapowania XML do formatu JSON znaki, które muszą zostać zmienione w formacie JSON, są wyprowadzane, a inne nie są wyprowadzane. Znak "/", mimo że nie jest znakiem, który musi zostać zmieniony, jest Niemniej niezbędny (w przypadku mapowania JSON to XML). Jest to wymagane do obsługi formatu ASP.NET AJAX dla danych `DateTime` w formacie JSON.

- W przypadku mapowania JSON na XML wszystkie znaki (w tym znaki nieucieczki, w razie potrzeby) są podejmowane w celu utworzenia `string`, który tworzy [local name].

- Elementy wewnętrzne [Children] mapują do wartości w sekcji 2,2, zgodnie z `JSON Type Attribute`, tak jak w przypadku `Root JSON Element`. Dozwolone jest użycie wielu poziomów zagnieżdżenia EIIs (w tym zagnieżdżania w tablicach).

Przykład: Poniższy element mapuje do fragmentu JSON.

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

Poniższy fragment kodu JSON jest mapowany do programu.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> W poprzednim mapowaniu nie ma kroku kodowania XML. W związku z tym WCF obsługuje tylko dokumenty JSON, w których wszystkie znaki w nazwach kluczy są prawidłowymi znakami w nazwach elementów XML. Na przykład dokument JSON {"<": "a"} nie jest obsługiwany, ponieważ < nie jest prawidłową nazwą elementu XML.

Odwrócona sytuacja (znaki prawidłowe w kodzie XML, ale nie w formacie JSON) nie powoduje żadnych problemów, ponieważ poprzednie mapowanie obejmuje ucieczki kodu JSON/etapy anulowania ucieczki.

Rekordy tablic działają w następujący sposób:

- Element wewnętrzny [local name] to "Item".

- Element wewnętrzny [Children] mapuje do wartości w sekcji 2,3, zgodnie z atrybutem typu JSON dla elementu głównego JSON. Dozwolone są wiele poziomów zagnieżdżenia elementu EIIs (w tym zagnieżdżanie w obrębie obiektów).

Przykład: Poniższy element mapuje do fragmentu JSON.

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

Poniżej znajduje się fragment kodu JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Autonomiczna serializacja kodu JSON](stand-alone-json-serialization.md)
