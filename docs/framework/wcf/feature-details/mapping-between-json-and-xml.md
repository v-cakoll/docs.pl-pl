---
title: Mapowanie między formatami JSON i XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 075f85887f99708dd1f3479bf0b036203886af71
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156679"
---
# <a name="mapping-between-json-and-xml"></a>Mapowanie między formatami JSON i XML
Czytniki i moduły zapisujące są produkowane przez <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> dostarczać interfejs API XML nad zawartością JavaScript Object Notation (JSON). JSON koduje dane za pomocą podzestawu literałów obiektu języka JavaScript. Czytniki i moduły zapisujące, generowane przez tę fabrykę są również używane podczas zawartość JSON jest wysyłane lub odbierane przez Windows Communication Foundation (WCF) aplikacji przy użyciu <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> lub <xref:System.ServiceModel.WebHttpBinding>.

Po zainicjowaniu z zawartością JSON, Czytelnik JSON zachowuje się w taki sam sposób, jak tekstową odczytującego XML obsługuje za pośrednictwem wystąpienia XML. Moduł zapisujący JSON, gdy podano sekwencję wywołań tworzącego na tekstowy odczytującego XML określone wystąpienie kodu XML, zapisuje zawartość JSON. Mapowanie między to wystąpienie XML i zawartość JSON jest opisane w tym temacie do użycia w zaawansowanych scenariuszach.

Wewnętrznie JSON jest reprezentowany jako zestaw informacji XML podczas przetwarzania przez architekturę WCF. Zwykle nie trzeba dotyczą tego wewnętrznej reprezentacji mapowanie jest tylko jeden logiczne: JSON jest zwykle nie fizycznie przekonwertować na format XML w pamięci lub konwersji do formatu JSON z pliku XML. Mapowanie oznacza, że interfejsów API XML są używane do uzyskiwania dostępu do zawartości w formacie JSON.

Gdy WCF używa formatu JSON, zwykle scenariusza jest to, że <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jest automatycznie zasilane z sieci przez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> zachowanie, lub <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie, gdy jest to konieczne. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Rozumie mapowanie między formatami JSON i zestaw informacji XML i działa tak, jakby on bezpośrednio zajmuje się JSON. (Można użyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> z dowolnym odczytującego XML lub moduł zapisujący przy założeniu, że kod XML jest zgodny ze następującego mapowania.)

W zaawansowanych scenariuszach może być konieczne uzyskiwania bezpośredniego dostępu do następującego mapowania. Tych scenariuszy wystąpić, gdy użytkownik chce serializacji i deserializacji JSON w niestandardowy sposób, bez konieczności polegania na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, lub podczas pracy z <xref:System.ServiceModel.Channels.Message> typu bezpośrednio dla wiadomości zawierające JSON. Mapowanie JSON XML służy do rejestrowania komunikatów. Korzystając z funkcji rejestrowania wiadomości w usłudze WCF, komunikatów JSON jest rejestrowane jako XML zgodnie z mapowania opisane w następnej sekcji.

Wyjaśnienie pojęcia mapowania, poniższy przykład jest dokumentu JSON.

```json
{"product":"pencil","price":12}
```

Aby odczytać dokument JSON przy użyciu jednej z czytników wcześniej wspomniano, należy użyć taką samą sekwencję <xref:System.Xml.XmlDictionaryReader> wywołuje się, jak w przypadku przeczytaj następujący dokument XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ponadto jeśli komunikat JSON w przykładzie jest odbierany przez architekturę WCF i rejestrowany, zobacz fragment XML w poprzednim dziennika.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapowanie między formatami JSON i zestaw informacji XML
Formalnie, mapowanie jest między JSON, zgodnie z opisem w [RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) (z wyjątkiem z pewnymi ograniczeniami swobodna i niektóre inne ograniczenia, które dodano) oraz XML zestaw informacji (i nie tekstowych XML) jako opisanych w [informacji XML Ustaw](https://go.microsoft.com/fwlink/?LinkId=98809) . Zobacz ten temat, aby uzyskać definicje *elementy informacji* i pól w [kwadratowych].

Pusty dokument JSON mapowany na pusty dokument XML, a pusty dokument XML jest mapowany na pusty dokument JSON. W pliku XML do mapowania JSON poprzedzających biały znak i końcowe biały znak po dokumentu nie są dozwolone.

Mapowanie jest zdefiniowane między albo element informacji dokumentu (DII) lub Element informacji elementu (EII) i JSON. EII lub właściwości [element dokumentu] DII, nazywa się głównym elementem JSON. Należy pamiętać, że fragmenty dokumentu (XML z wieloma elementami katalogu głównego) nie są obsługiwane w to mapowanie.

Przykład: Następujący dokument:

```xml
<?xml version="1.0"?>
<root type="number">42</root>`
```

I następującego elementu:

```xml
<root type="number">42</root>
```

Zarówno ma mapowania do formatu JSON. <`root`> Element jest elementem głównym JSON w obu przypadkach.

Ponadto w przypadku DII, należy rozważyć:

- Niektóre elementy na liście [dzieci] nie może być obecny. Nie należy polegać na ten fakt, odczytując XML mapowania z formatu JSON.

- Listy [dzieci] zawiera Brak komentarza elementy informacji.

- Listy [dzieci] przechowuje informacje elementów DTD.

- Listy [dzieci] nie zawiera żadnych elementów informacji osobistych (PI) ( `<?xml…>` deklaracja nie jest uważany za element informacji PI)

- Zestaw [notacji] jest pusty.

- Zestaw [nieanalizowanych jednostek] jest pusty.

Przykład: Ten dokument ma nie mapowania na format JSON ponieważ przechowuje [dzieci] PI i komentarz.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII dla elementu JSON głównego ma następującą charakterystykę:

- [Nazwa lokalnego] ma wartość "root".

- [nazwa przestrzeni nazw] nie ma wartości.

- [prefix] nie ma wartości.

- [dzieci] może zawierać EIIs, (które reprezentują elementy wewnętrzne, zgodnie z opisem w dalszej) lub CIIs (znak informacji elementów zgodnie z opisem w dalszej) lub żadna z tych, ale nie oba.

- [atrybuty] może zawierać następujące elementy informacji opcjonalnego atrybutu (AIIs)

- Atrybut typu JSON ("type") zgodnie z opisem w dalszej. Ten atrybut służy do zachowania typu JSON (ciąg, liczba, wartość logiczna, obiektu, tablicy lub wartość null) zamapowanego pliku XML.

- Atrybut Name kontraktu danych ("\_\_typu") zgodnie z opisem w dalszej. Ten atrybut jest tylko mogą być obecne [znormalizowaną wartość] to "obiekt", jeśli jest również obecny atrybut typu JSON. Ten atrybut jest używany przez `DataContractJsonSerializer` zachować kontraktu danych informacji o typie — na przykład w przypadku polimorficznych gdzie typem pochodnym jest serializowana, a oczekiwano typu podstawowego. Jeśli nie pracujesz z `DataContractJsonSerializer`, w większości przypadków, ten atrybut jest ignorowany.

- [w zakresie namespaces] zawiera powiązania "xml" do `http://www.w3.org/XML/1998/namespace` nieużywanie przez specyfikację zestaw informacji.

- [dzieci], [atrybuty] i [w zakresie namespaces] nie może mieć żadnych elementów innych niż określony wcześniej i [atrybuty z przestrzeni nazw] musi mieć żadnych elementów członkowskich, ale nie należy polegać na następujące fakty, podczas odczytywania pliku XML mapowane z formatu JSON.

Przykład: Ten dokument ma nie mapowania na format JSON ponieważ [atrybuty z przestrzeni nazw] nie jest pusty.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

Wszystko dla atrybutu typu JSON ma następującą charakterystykę:

- [nazwa przestrzeni nazw] nie ma wartości.
- [prefix] nie ma wartości.
- [Nazwa lokalnego] jest "type".
- [wartość znormalizowana] to jedna z wartości możliwych typów, opisanych w poniższej sekcji.
- [] jest `true`.
- [atrybutu type] nie ma wartości.
- [odwołania] nie ma wartości.

Wszystko dla atrybutu Name kontraktu danych ma następującą charakterystykę:

- [nazwa przestrzeni nazw] nie ma wartości.
- [prefix] nie ma wartości.
- [Nazwa lokalna] "\_\_typu" (dwóch znaków podkreślenia i następnie "type").
- [wartość znormalizowana] to dowolny prawidłowy ciąg Unicode — mapowanie tego ciągu do ciągu JSON jest opisane w poniższej sekcji.
- [] jest `true`.
- [atrybutu type] nie ma wartości.
- [odwołania] nie ma wartości.

Wewnętrzny zawartym w elemencie głównym elementem JSON lub inne elementy wewnętrzny mają następującą charakterystykę:

- zgodnie z opisem w dalszej, [Nazwa lokalnego] może mieć dowolną wartość.
- [nazwa przestrzeni nazw], [prefix], [dzieci], [atrybuty], [przestrzeń nazw atrybutów], i podlegają one te same reguły jako elementu JSON głównego [w zakresie namespaces].

W głównym elementem JSON i elementy wewnętrzne atrybut typu JSON definiuje mapowanie na format JSON i możliwe [dzieci] i ich interpretację. [Wartość znormalizowana] atrybutu jest uwzględniana wielkość liter i musi zawierać tylko litery i nie może zawierać białego.

|[znormalizowane wartości] dla atrybutu typu JSON wszystko|Dozwolone [] elementów podrzędnych odpowiedniego EII|Mapowanie do formatu JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (lub Brak typu JSON wszystko)<br /><br /> A `string` i braku typu JSON wszystko to sprawia, że ten sam `string` domyślnie.<br /><br /> Dlatego `<root> string1</root>` mapuje dane JSON `string` "ciąg1".|0 lub więcej CIIs|JSON `string` (RFC JSON sekcję 2.5). Każdy `char` jest znak, który odnosi się do [kod znaku] z CII. W przypadku CIIs nie jest on mapowany pusty kod JSON `string`.<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> Fragment kodu JSON to "42".<br /><br /> W pliku XML do JSON mapowania znaków, które muszą być poprzedzone znakiem zmiany znaczenia mapy na znaki ucieczki przestają być, mapowania wszystkie inne znaki, które nie miały zmienione znaczenie. Znak "/" jest szczególna — została zmieniona, mimo że nie musi on być (pisemne się jako "\\/").<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment kodu JSON to " \\" da\\/ta\\"".<br /><br /> W formacie JSON do pliku XML wszelkie znaki ucieczki przestają być i znaków, które nie są poprzedzone znakiem zmiany znaczenia mapy poprawnie do odpowiedniego [kod znaku].<br /><br /> Przykład: Fragment kodu JSON "\u0041BC" mapuje do następujących elementów XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Ciąg może być otoczona biały ("ws" w sekcji 2 JSON RFC), które nie są mapowane do pliku XML.<br /><br /> Przykład: Za pomocą pliku JSON fragmentu "ABC", (ma spacji przed pierwszym podwójnego cudzysłowu), mapuje do następujących elementów XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dowolny biały obszar w pliku XML jest mapowany na biały znak w formacie JSON.<br /><br /> Przykład: Następujący element XML mapuje fragment kodu JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Fragment kodu JSON to "BC".|
|`number`|co najmniej 1 CIIs|JSON `number` (RFC JSON, sekcji 2.4), prawdopodobnie otoczony biały znak. Każdy znak w połączeniu numer/biały znak jest znakiem, który odnosi się do [kod znaku] z CII.<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Fragment kodu JSON jest 42<br /><br /> (Biały znak jest zachowane).|
|`boolean`|CIIs 4 lub 5 (co odpowiada `true` lub `false`), prawdopodobnie otoczone dodatkowe CIIs odstępu.|Sekwencję CII, która odnosi się do ciągu "true" jest mapowana na literału `true`, i sekwencji CII, który odpowiada ciągowi "false" jest mapowany do literału `false`. Otaczającego biały znak są zachowywane.<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment kodu JSON jest `false`.|
|`null`|Zezwalaj na Brak.|Literał `null`. Na ciąg JSON do mapowania XML `null` otoczony biały ("ws" w sekcji 2), które nie są mapowane do pliku XML.<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON.<br /><br /> `<root type="null"/>`<br /><br /> lub<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment kodu JSON w obu przypadkach jest `Null`.|
|`object`|0 lub więcej EIIs.|Element `begin-object` (od lewej nawias klamrowy) tak jak w sekcji 2.2 JSON RFC, a następnie rekord elementu członkowskiego dla każdego EII zgodnie z opisem w dalszej. W przypadku więcej niż jeden EII między rekordów elementów członkowskich są wartości separatorów (przecinkami). To wszystko następuje koniec — obiekt (prawy nawias klamrowy).<br /><br /> Przykład: Następujący element mapuje fragment kodu JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Fragment kodu JSON jest `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Jeśli atrybut typu kontraktu danych ma na języku XML do mapowania JSON, dodatkowy rekord elementu członkowskiego jest wstawiany na początku. Jego nazwa jest [Nazwa lokalnego] atrybutu typu kontraktu danych ("\_\_typu"), a jego wartość to atrybut [Znormalizowana wartość]. Z drugiej strony, w formacie JSON do pliku XML, jeśli nazwa pierwszego elementu członkowskiego rekordu jest [Nazwa lokalnego] atrybutu typu kontraktu danych (czyli "\_\_typu"), odpowiedniego atrybutu typu kontraktu danych znajduje się w mapowanych XML, ale nie ma odpowiedniego EII. Należy pamiętać, że ten rekord elementu członkowskiego musi wystąpić najpierw w obiekcie JSON dla tego mapowania specjalne do zastosowania. To oznacza odejście od zwykle przetwarzania JSON, w którym kolejność rekordów elementów członkowskich nie jest znaczący.<br /><br /> Przykład:<br /><br /> Poniższy fragment kodu JSON mapowany do pliku XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Kod XML ma następujący kod.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Należy zauważyć, że \_ \_typu wszystko jest obecny, ale ma nie \_ \_wpisz EII.<br /><br /> Jednak jeśli kolejność, w formacie JSON zostanie odwrócony jako pokazano w poniższym przykładzie.<br /><br /> {"name": "John","\_\_typu": "Person"}<br /><br /> Odpowiedni kod XML jest wyświetlany.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Oznacza to, że \__typ przestaje w zwykły sposób, mają specjalne znaczenie i mapuje do EII nie wszystko.<br /><br /> Anulowanie unescaping zasady wszystko [Znormalizowana wartość] mapowane na wartości JSON są takie same jak dla ciągów JSON, określone w wierszu "string" w tej tabeli.<br /><br /> Przykład:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> do poprzedniego przykładu można zamapować następujące dane JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> W pliku XML do mapowania JSON, nie może być pierwszym EII firmy [Nazwa lokalnego] "\_\_typu".<br /><br /> Biały znak (`ws`) nigdy nie jest generowany na języku XML do mapowania JSON dla obiektów i jest ignorowany w formacie JSON do pliku XML.<br /><br /> Przykład: Poniższy fragment kodu JSON mapowany na XML element.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> XML element przedstawiono w poniższym kodzie.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|tablica|0 lub więcej EIIs|Begin — tablica (lewy nawias kwadratowy) tak jak w sekcji 2.3 JSON RFC, następuje rekord tablicy do każdego EII zgodnie z opisem w dalszej. Jeśli istnieje więcej niż jeden EII, istnieją wartości separatorów (przecinkami) między rekordami tablicy. Następuje to tablica zakończenia.<br /><br /> Przykład: Następujący element XML mapuje fragment kodu JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Fragment kodu JSON to ["aaa", "bbb"]<br /><br /> Biały znak (`ws`) nigdy nie jest generowany na języku XML do mapowania JSON dla tablic i jest ignorowany w formacie JSON do pliku XML.<br /><br /> Przykład: Fragment kodu JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> Element XML, który jest on mapowany.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Rekordy elementów roboczych w następujący sposób:

- Mapuje element wewnętrzny firmy [Nazwa lokalnego] `string` wchodzi w skład `member` zgodnie z definicją w sekcji 2.2 JSON RFC.

Przykład: Następujący element mapuje fragment kodu JSON.

`<root type="object"/>`

`<myLocalName type="string">aaa</myLocalName>`

`</root >`

Poniższy fragment kodu JSON jest wyświetlana.

`{"myLocalName":"aaa"}`

- Na XML do mapowania JSON będą miały zmienione znaczenie znaków, które muszą być wyjściowym w formacie JSON, a pozostałe są nie zawiera wyjścia. Znak "/", mimo że nie jest znakiem, który musi być poprzedzone znakiem zmiany znaczenia, jest poprzedzone znakiem zmiany znaczenia mimo wszystko (nie musi być poprzedzone znakiem zmiany znaczenia w formacie JSON do pliku XML). Jest to wymagane do obsługi formatu ASP.NET AJAX `DateTime` dane w formacie JSON.

- W formacie JSON do pliku XML, wszystkie znaki (w tym znaki ucieczki nie, jeśli to konieczne) są pobierane do formularza `string` daje [Nazwa lokalnej].

- Elementy wewnętrzne [dzieci] mapy do wartości w sekcji 2.2, zgodnie z opisem w `JSON Type Attribute` podobnie jak w przypadku dla `Root JSON Element`. Wiele poziomów zagnieżdżenia EIIs (w tym zagnieżdżenia w macierzy) są dozwolone.

Przykład: Następujący element mapuje fragment kodu JSON.

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

Poniższy fragment kodu JSON to, co to jest on mapowany.

`{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`

> [!NOTE]
> W poprzednim mapowanie jest bez kroku kodowania XML. W związku z tym usługi WCF obsługuje tylko dokumenty JSON, w którym wszystkie znaki nazwy kluczy są prawidłowych znaków w nazwach elementów XML. Na przykład dokument JSON {"<": ""} nie jest obsługiwana, ponieważ < nie jest prawidłową nazwą elementu XML.

Sytuacja odwrotna (znaki dozwolone w XML, ale nie w formacie JSON) nie powoduje żadnych problemów, ponieważ mapowanie poprzedniego zawiera kroki anulowania zapewnianego element unescaping JSON.

Rekordy tablicy pracować w następujący sposób:

- Wewnętrzny elementu [Nazwa lokalnego] jest "elementu".

- Wewnętrzny elementu [dzieci] mapy do wartości w sekcji 2.3, zgodnie z atrybutu typu JSON to dla elementu głównego w formacie JSON. Wiele poziomów zagnieżdżenia EIIs (w tym zagnieżdżenia w obiektach) są dozwolone.

Przykład: Następujący element mapuje fragment kodu JSON.

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

`["myValue1",2,[true,null]]`

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Autonomiczna serializacja kodu JSON](stand-alone-json-serialization.md)