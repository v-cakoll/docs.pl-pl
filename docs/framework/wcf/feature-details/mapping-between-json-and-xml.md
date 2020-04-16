---
title: Mapowanie między formatami JSON i XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 55812ad15d1f38bb0c295e6895dfff329035206d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464065"
---
# <a name="mapping-between-json-and-xml"></a>Mapowanie między formatami JSON i XML
Czytniki i moduły <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> zapisu opracowane przez udostępnić interfejs API XML za pomocą zawartości JavaScript Object Notation (JSON). JSON koduje dane przy użyciu podzbioru literałów obiektu JavaScript. Czytniki i autorzy produkowane przez tę fabrykę są również używane, gdy zawartość JSON jest <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> wysyłana lub odbierana przez aplikacje Windows Communication Foundation (WCF) za pomocą lub <xref:System.ServiceModel.WebHttpBinding>.

Po zainicjowaniu z zawartością JSON czytnik JSON zachowuje się w taki sam sposób, jak tekstowy czytnik XML w wystąpieniu pliku XML. Moduł zapisujący JSON, gdy podano sekwencję wywołań, które na tekstowym czytniku XML tworzy pewne wystąpienie XML, zapisuje zawartość JSON. Mapowanie między tym wystąpieniem XML i zawartość JSON jest opisany w tym temacie do użycia w zaawansowanych scenariuszach.

Wewnętrznie JSON jest reprezentowany jako zestaw informacyjny XML podczas przetwarzania przez WCF. Zwykle nie trzeba zajmować się tą reprezentacją wewnętrzną, ponieważ mapowanie jest tylko logiczne: JSON zwykle nie jest fizycznie konwertowany na XML w pamięci lub konwertowany na JSON z XML. Mapowanie oznacza, że interfejsy API XML są używane do uzyskiwania dostępu do zawartości JSON.

Gdy WCF używa JSON, zwykły scenariusz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jest, że jest <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> automatycznie podłączony przez <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie lub zachowanie, gdy jest to właściwe. Rozumie <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> mapowanie między JSON i XML infoset i działa tak, jakby ma do czynienia z JSON bezpośrednio. (Możliwe jest użycie <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dowolnego czytnika lub modułu zapisującego XML, ze zrozumieniem, że kod XML jest zgodny z następującym mapowaniem).

W zaawansowanych scenariuszach może okazać się konieczne bezpośrednie uzyskiwany dostęp do następującego mapowania. Te scenariusze występują, gdy chcesz serializować i deserialize JSON <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>w sposób niestandardowy, bez polegania na , lub w kontaktach z typem <xref:System.ServiceModel.Channels.Message> bezpośrednio dla wiadomości zawierających JSON. Mapowanie JSON-XML jest również używane do rejestrowania wiadomości. Podczas korzystania z funkcji rejestrowania wiadomości w WCF, komunikaty JSON jest rejestrowany jako XML zgodnie z mapowaniem opisanym w następnej sekcji.

Aby wyjaśnić pojęcie mapowania, poniższy przykład jest dokument JSON.

```json
{"product":"pencil","price":12}
```

Aby odczytać ten dokument JSON przy użyciu jednego z czytników <xref:System.Xml.XmlDictionaryReader> wcześniej wymienionych, należy użyć tej samej sekwencji wywołań, jak można odczytać następujący dokument XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ponadto jeśli komunikat JSON w przykładzie zostanie odebrany przez WCF i rejestrowane, zobaczysz fragment XML w poprzednim dzienniku.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapowanie między JSON a zestawem informacyjnym XML

Formalnie mapowanie znajduje się między JSON, jak opisano w [RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) (z wyjątkiem pewnych ograniczeń i niektórych innych ograniczeń dodanych) i zestawu informacji XML (a nie tekstowego XML), jak opisano w [zestawie informacji XML](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/). Definicje *elementów informacyjnych* i pól w nawiasach kwadratowych można znaleźć w tym temacie.

Pusty dokument JSON jest mapowyny na pusty dokument XML, a pusty dokument XML jest mapowyny na pusty dokument JSON. Na mapowaniu XML na JSON poprzedzające białe i końcowe odstępy po dokumencie nie są dozwolone.

Mapowanie jest definiowane między elementem informacji o dokumencie (DII) lub elementem informacji o elemencie elementu (EII) i JSON. EII lub DII [document element] właściwości, jest określany jako główny element JSON. Należy zauważyć, że fragmenty dokumentu (XML z wieloma elementami głównymi) nie są obsługiwane w tym mapowaniu.

Przykład: Następujący dokument:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

I następujący element:

```xml
<root type="number">42</root>
```

Oba mają mapowanie do JSON. Element <`root`> jest głównym elementem JSON w obu przypadkach.

Ponadto w przypadku DII należy wziąć pod uwagę:

- Niektóre elementy na liście [dzieci] nie mogą być obecne. Nie należy polegać na tym fakcie podczas odczytywania XML mapowane z JSON.

- Lista [dzieci] nie zawiera żadnych elementów informacji o komentarzach.

- Lista [dzieci] nie zawiera żadnych elementów informacji DTD.

- Lista [dzieci] nie zawiera żadnych informacji osobistych `<?xml…>` (PI) (deklaracja nie jest uważana za element informacji PI)

- Zestaw [notacji] jest pusty.

- [Nieparparowane jednostki] zestaw jest pusty.

Przykład: Poniższy dokument nie ma mapowania do JSON, ponieważ [dzieci] zawiera pi i komentarz.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII dla głównego elementu JSON ma następujące cechy:

- [nazwa lokalna] ma wartość "root".

- [nazwa obszaru nazw] nie ma żadnej wartości.

- [prefiks] nie ma żadnej wartości.

- [dzieci] mogą zawierać EII (które reprezentują elementy wewnętrzne, jak opisano dalej) lub CII (elementy informacji o znakach, jak opisano dalej) lub żaden z nich, ale nie oba.

- [atrybuty] mogą zawierać następujące opcjonalne elementy informacji o atrybutach (AII)

- Atrybut typu JSON ("typ"),zgodnie z opisem dalej. Ten atrybut jest używany do zachowania typu JSON (ciąg, liczba, wartość logiczna, obiekt, tablica lub null) w mapowanym pliku XML.

- Atrybut Data Contract Name\_\_(" typ") opisany dalej. Ten atrybut może być obecny tylko wtedy, gdy atrybut typu JSON jest również obecny, a jego [znormalizowana wartość] jest "object". Ten atrybut jest używany `DataContractJsonSerializer` przez do zachowania informacji o typie kontraktu danych — na przykład w przypadkach polimorficznych, w których typ pochodny jest serializowany i gdzie oczekuje się typu podstawowego. Jeśli nie pracujesz `DataContractJsonSerializer`z , w większości przypadków, ten atrybut jest ignorowany.

- [przestrzenie nazw w zakresie] zawiera powiązanie "xml" zgodnie `http://www.w3.org/XML/1998/namespace` z wymaganiami specyfikacji zestawu informacji.

- [children], [atrybuty] i [w zakresie obszarów nazw] nie może mieć żadnych elementów innych niż określone wcześniej i [atrybuty obszaru nazw] nie może mieć żadnych elementów członkowskich, ale nie opierają się na tych faktów podczas odczytywania XML mapowane z JSON.

Przykład: Poniższy dokument nie ma mapowania do JSON, ponieważ [atrybuty obszaru nazw] nie jest pusty.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

AII dla atrybutu typu JSON ma następujące właściwości:

- [nazwa obszaru nazw] nie ma żadnej wartości.
- [prefiks] nie ma żadnej wartości.
- [nazwa lokalna] jest "type".
- [wartość znormalizowane] jest jedną z możliwych wartości typu opisanych w poniższej sekcji.
- [specified] `true`jest .
- [typ atrybutu] nie ma wartości.
- [odwołania] nie ma żadnej wartości.

AII dla atrybutu Nazwa kontraktu danych ma następujące cechy:

- [nazwa obszaru nazw] nie ma żadnej wartości.
- [prefiks] nie ma żadnej wartości.
- [nazwa lokalna]\_\_to " type" (dwa podkreślenia, a następnie "typ").
- [normalizowana wartość] jest dowolnym prawidłowym ciągiem Unicode — mapowanie tego ciągu do JSON jest opisane w poniższej sekcji.
- [specified] `true`jest .
- [typ atrybutu] nie ma wartości.
- [odwołania] nie ma żadnej wartości.

Elementy wewnętrzne zawarte w głównym elemencie JSON lub innych elementach wewnętrznych mają następujące właściwości:

- [nazwa lokalna] może mieć dowolną wartość, jak opisano dalej.
- [namespace name], [prefiks], [elementy podrzędne], [atrybuty], [atrybuty] i [obszary nazw w zakresie] podlegają tym samym regułom co główny element JSON.

Zarówno w głównym elementem JSON i wewnętrznych elementów, Atrybut typu JSON definiuje mapowanie do JSON i możliwe [dzieci] i ich interpretacji. W [znormalizowanej wartości] atrybutu jest rozróżniana wielkość liter i musi być mała litera i nie może zawierać odstępu.

|[wartość znormalizowane] AII atrybutu typu JSON|Dozwolone [dzieci] odpowiedniego EII|Mapowanie do JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string`(lub brak typu JSON AII)<br /><br /> A `string` i brak typu JSON AII są `string` takie same sprawia, że domyślnie.<br /><br /> Tak, `<root> string1</root>` mapy do `string` JSON "string1".|0 lub więcej cii|A JSON `string` (JSON RFC, sekcja 2.5). Każdy `char` z nich jest znakiem odpowiadającym [kod znaku] z CII. Jeśli nie ma cii, mapuje do `string`pustego JSON .<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> Fragment JSON to "42".<br /><br /> W przypadku mapowania XML na JSON znaki, które muszą zostać zmienione, są mapowane na znaki zmienione, wszystkie inne są mapowane na znaki, które nie są zmienione. Znak "/" jest wyjątkowy – jest zmieniany, mimo że nie musi\\być (wypisany jako " /").<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment JSON jest \\"da\\/ta\\"".<br /><br /> W mapowaniu JSON na XML wszystkie znaki i znaki, które nie są zmienione, są poprawnie mapowane na odpowiedni [kod znaku].<br /><br /> Przykład: Fragment JSON "\u0041BC", mapuje następujący element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Ciąg może być otoczony białymi znakami ('ws' w sekcji 2 JSON RFC), który nie jest mapowany na XML.<br /><br /> Przykład: Fragment JSON "ABC" (istnieją spacje przed pierwszym podwójnym cudzysłowem), mapuje do następującego elementu XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Wszystkie białe odstępy w XML mapują na biały znak w języku JSON.<br /><br /> Przykład: Następujący element XML mapuje do fragmentu JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Fragment JSON to " A BC ".|
|`number`|1 lub więcej cii|A JSON `number` (JSON RFC, sekcja 2.4), ewentualnie otoczony białym spacją. Każdy znak w kombinacji liczba/biały znak jest znakiem odpowiadającym [kodowi znaku] z CII.<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Fragment JSON jest 42<br /><br /> (Biały znak jest zachowany).|
|`boolean`|4 lub 5 CII (co `true` `false`odpowiada lub), ewentualnie otoczone dodatkowymi CII w odstępach.|Sekwencja CII odpowiadająca ciągowi "true" jest mapowana `true`na literał, a sekwencja CII odpowiadająca ciągowi "false" jest mapowana na literał `false`. Otaczająca biała przestrzeń jest zachowywana.<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment JSON `false`jest .|
|`null`|Żaden nie jest dozwolony.|Dosłowne `null`. W mapowaniu JSON na `null` XML może być otoczony białymi znakami ("ws" w sekcji 2), które nie są mapowane na kod XML.<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON.<br /><br /> `<root type="null"/>`<br /><br /> lub<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON w obu `Null`przypadkach jest .|
|`object`|0 lub więcej EII.|A `begin-object` (lewa klamra kręcona) jak w sekcji 2.2 JSON RFC, po której następuje rekord elementu członkowskiego dla każdego EII, zgodnie z opisem dalej. Jeśli istnieje więcej niż jeden EII, istnieją separatory wartości (przecinki) między rekordami elementów członkowskich. Wszystko to następuje obiekt końcowy (prawy nawias klamrowy).<br /><br /> Przykład: Następujący element mapuje do fragmentu JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Fragment JSON `{"type1":"aaa","type2":"bbb"}`jest .<br /><br /> Jeśli atrybut typ kontraktu danych jest obecny w mapowaniu XML do JSON, na początku zostanie wstawiony dodatkowy rekord elementu członkowskiego. Jego nazwa jest [nazwa lokalna] atrybutu typu\_\_kontraktu danych (typ"), a jego wartość jest [znormalizowana wartość atrybutu]. Z drugiej strony w mapowaniu JSON na XML, jeśli nazwa pierwszego rekordu członkowskiego jest [nazwa lokalna]\_\_atrybutu typ kontraktu danych (czyli " typ"), odpowiedni atrybut typu kontraktu danych jest obecny w mapowanym pliku XML, ale odpowiedni EII nie jest obecny. Należy zauważyć, że ten rekord elementu członkowskiego musi wystąpić najpierw w obiekcie JSON dla tego specjalnego mapowania do zastosowania. Stanowi to odstępstwo od zwykłego przetwarzania JSON, gdzie kolejność rekordów członkowskich nie jest znacząca.<br /><br /> Przykład:<br /><br /> Poniższy fragment JSON jest mapowana na kod XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Kod XML jest następującym kodem.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Należy zauważyć, że \_ \_typ AII jest \_ \_obecny, ale nie ma typu EII.<br /><br /> Jednak jeśli kolejność w JSON jest odwrócona, jak pokazano w poniższym przykładzie.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Wyświetlany jest odpowiedni kod XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Oznacza to, \_że _type przestaje mieć szczególne znaczenie i mapy do EII jak zwykle, a nie AII.<br /><br /> Ucieczka/unescaping reguły dla AII [znormalizowanej wartości] po mapowaniu do wartości JSON są takie same jak dla ciągów JSON, określone w wierszu "string" tej tabeli.<br /><br /> Przykład:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> do poprzedniego przykładu można zamapować na następujący JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> W przypadku mapowania XML na JSON pierwsza nazwa lokalna EII nie może być "typem".\_\_<br /><br /> Biały znak`ws`( ) nigdy nie jest generowany na XML do mapowania JSON dla obiektów i jest ignorowany na JSON do mapowania XML.<br /><br /> Przykład: Następujący fragment JSON mapuje do elementu XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> Element XML jest wyświetlany w poniższym kodzie.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|tablica|0 lub więcej EII|Tablica początkowa (lewy nawias kwadratowy), jak w sekcji 2.3 JSON RFC, po której następuje rekord tablicy dla każdego EII, zgodnie z opisem dalej. Jeśli istnieje więcej niż jeden EII, istnieją separatory wartości (przecinki) między rekordami tablicy. Wszystko to następuje tablicy końcowej.<br /><br /> Przykład: Następujący element XML mapuje do fragmentu JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Fragment JSON jest`["aaa","bbb"]`<br /><br /> Biały znak`ws`( ) nigdy nie jest generowany na XML do mapowania JSON dla tablic i jest ignorowany w JSON do mapowania XML.<br /><br /> Przykład: Fragment JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> Element XML, do który jest mapowana.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Rekordy członkowskie działają w następujący sposób:

- Element wewnętrzny [nazwa lokalna] `string` mapuje `member` do części zgodnie z definicją w sekcji 2.2 JSON RFC.

Przykład: Następujący element mapuje do fragmentu JSON.

```xml
<root type="object">
    <myLocalName type="string">aaa</myLocalName>
</root>
```

Wyświetlany jest następujący fragment JSON.

```json
{"myLocalName":"aaa"}
```

- W odwzorowaniu XML do JSON znaki, które muszą zostać zmienione w JSON, są zmienione, a pozostałe nie są wykreślane. Znak "/", mimo że nie jest znakiem, który musi zostać zmieniony, jest jednak zmieniony (nie musi być zmieniany w mapowaniu JSON do XML). Jest to wymagane do obsługi ASP.NET formatu `DateTime` AJAX dla danych w JSON.

- W mapowaniu JSON na XML wszystkie znaki (w tym znaki nieułomne, jeśli to konieczne) są pobierane w celu utworzenia `string` [nazwa lokalna].

- Elementy wewnętrzne [dzieci] mapują wartość w sekcji 2.2, zgodnie z `JSON Type Attribute` tak jak dla `Root JSON Element`. Dozwolone jest wiele poziomów zagnieżdżania EII (w tym zagnieżdżanie w tablicach).

Przykład: Następujący element mapuje do fragmentu JSON.

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

Poniższy fragment JSON jest to, co mapuje do.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> W poprzednim mapowaniu nie ma kroku kodowania XML. W tym WCF obsługuje tylko dokumenty JSON, gdzie wszystkie znaki w nazwach kluczy są prawidłowe znaki w nazwach elementów XML. Na przykład dokument JSON {"<":"a"} nie jest obsługiwany, ponieważ < nie jest prawidłową nazwą elementu XML.

Sytuacja odwrotna (znaki prawidłowe w XML, ale nie w JSON) nie powoduje żadnych problemów, ponieważ poprzednie mapowanie zawiera JSON ucieczki/unescaping kroki.

Rekordy tablicy działają w następujący sposób:

- Element wewnętrzny [nazwa lokalna] jest "element".

- [Elementy podrzędne] elementu wewnętrznego mapują na wartość w sekcji 2.3, zgodnie z atrybutem typu JSON, podobnie jak w przypadku głównego elementu JSON. Dozwolone jest wiele poziomów zagnieżdżania EII (w tym zagnieżdżanie w obiektach).

Przykład: Następujący element mapuje do fragmentu JSON.

```xml
<root type="array">
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root>
```

Poniżej znajduje się fragment JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Autonomiczna serializacja kodu JSON](stand-alone-json-serialization.md)
