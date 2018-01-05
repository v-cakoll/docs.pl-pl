---
title: "Mapowanie między formatami JSON i XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 770be9ea5327b32286de64207a3cf07bca7449c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-between-json-and-xml"></a>Mapowanie między formatami JSON i XML
Czytniki i zapisywania utworzonego przez <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> dostarczać interfejs API XML nad zawartością JavaScript Object Notation (JSON). JSON koduje dane przy użyciu podzbiór literałów obiektu języka JavaScript. Czytniki i zapisywania utworzonego przez tej fabryki są również używane podczas zawartość JSON są wysyłane lub odbierane przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji przy użyciu <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> lub <xref:System.ServiceModel.WebHttpBinding>.  
  
 Po zainicjowaniu z zawartością JSON, czytnika JSON działa w taki sam sposób, który obsługuje tekstową modułu odczytującego XML za pośrednictwem wystąpienia XML. Składnik zapisywania JSON, gdy sekwencję wywołań, która na tekstową modułu odczytującego XML tworzy określone wystąpienie XML, zapisuje zawartość JSON. Mapowanie między to wystąpienie XML i zawartość JSON jest opisana w tym temacie do użycia w zaawansowanych scenariuszach.  
  
 Wewnętrznie JSON jest reprezentowany jako XML typu infoset sprawdzonych podczas przetwarzania przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Zwykle nie trzeba dotyczą tej reprezentacji wewnętrznej jako mapowanie jest tylko logiczne: JSON jest zwykle nie fizycznie przekonwertowany do formatu XML w pamięci lub konwersji do formatu JSON z pliku XML. Mapowanie oznacza, że XML interfejsów API umożliwiają dostęp do zawartości JSON.  
  
 Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa formatu JSON, zwykle scenariuszu jest to, że <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> automatycznie jest podłączony przez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> zachowanie, lub <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie, gdy jest to konieczne. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Rozumie mapowanie między formatami JSON i XML typu infoset sprawdzonych i działa tak, jakby jego bezpośrednio zajmuje się JSON. (Można użyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> z modułu odczytującego XML lub składnik zapisywania, pamiętając, że plik XML odpowiada następującego mapowania.)  
  
 W zaawansowanych scenariuszach może on stać się niezbędne do uzyskania bezpośredniego dostępu do następującego mapowania. Te scenariusze wystąpić, gdy chcesz serializacji i deserializacji JSON w niestandardowy sposób, bez polegania na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, lub podczas pracy nad <xref:System.ServiceModel.Channels.Message> typu bezpośrednio dla wiadomości zawierające JSON. Mapowanie JSON XML służy także do rejestrowania komunikatów. Podczas używania funkcji rejestrowania komunikatów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], komunikaty JSON jest rejestrowany jako XML zgodnie z mapowania opisany w następnej sekcji.  
  
 Poniższy przykład jest wyjaśnienie pojęcia mapowania, dokumentu JSON.  
  
```json  
{"product":"pencil","price":12}  
```  
  
 Aby przeczytać ten dokument JSON przy użyciu jednej z czytników wcześniej wspomniano, użyj tej samej sekwencji <xref:System.Xml.XmlDictionaryReader> wywołuje się, jak w przypadku następujących dokumentu XML.  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 Ponadto, jeśli komunikat JSON w przykładzie jest odbierany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i rejestrowania, można zobaczyć fragmentem kodu XML w poprzednim dzienniku.  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapowanie między formatami JSON i XML typu infoset sprawdzonych  
 Formalnie, jest mapowanie między JSON zgodnie z opisem w [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (z wyjątkiem z pewnymi ograniczeniami swobodna i niektórych innych ograniczeń dodany) oraz XML typu infoset (i nie tekstowy XML) jako opisane w [informacje XML Ustaw](http://go.microsoft.com/fwlink/?LinkId=98809) . Ten temat dla definicji *elementów informacji* i pól w [kwadratowych].  
  
 Pusty dokument JSON mapuje pusty dokument XML, a pusty dokument XML mapowana na pusty dokument JSON. W pliku XML do mapowania JSON poprzedzających spacji i końcowe po dokumentu nie są dozwolone.  
  
 Mapowanie zdefiniowano między albo element informacji dokumentu (DII) lub elementu informacji elementu (EII) i JSON. EII lub właściwości [element dokumentu] DII, jest określana jako elementu JSON głównego. Uwaga fragmenty dokumentu (XML o wiele elementów głównych) nie są obsługiwane w tym mapowania.  
  
 Przykład: Następującym dokumencie:  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 I następującego elementu:  
  
 `<root type="number">42</root>`  
  
 Mają mapowania do formatu JSON. <`root`> Element jest elementem głównym JSON w obu przypadkach.  
  
 Ponadto w przypadku DII, należy rozważyć:  
  
-   Niektóre elementy na liście [dzieci] nie może być obecny. Nie należy polegać na tym, podczas odczytu XML mapowania z formatu JSON.  
  
-   Listy [dzieci] przechowuje ma komentarza elementów informacji.  
  
-   Listy [dzieci] przechowuje informacje elementów DTD.  
  
-   Listy [dzieci] przechowuje nie elementów informacji osobistych (PI) ( \<? xml... > Deklaracja nie jest uważana za elementu informacji PI)  
  
-   Zestaw [notacji] jest pusty.  
  
-   Zestaw [nieprzeanalizowanej jednostki] jest pusty.  
  
 Przykład: Następujący dokument nie ma żadnych mapowania do formatu JSON ponieważ blokad [dzieci] PI i komentarza.  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 EII dla elementu głównego JSON ma następującą charakterystykę:  
  
-   [Nazwa lokalna] ma wartość "root".  
  
-   [nazwa przestrzeni nazw] nie ma wartości.  
  
-   [prefix] nie ma wartości.  
  
-   [elementy podrzędne] mogą zawierać EIIs (które reprezentują elementy wewnętrzne, zgodnie z opisem w dalszej) lub CIIs (znak informacji elementów zgodnie z opisem w dalszej) lub żadna z tych, ale nie oba.  
  
-   [atrybuty] może zawierać następujące elementy informacji opcjonalny atrybut (AIIs)  
  
-   Atrybut typu JSON ("type") zgodnie z opisem dalej. Ten atrybut służy do zachowania typu JSON (ciąg, liczbę, wartość logiczna, obiektu, tablicy lub wartość null) w mapowanej XML.  
  
-   Dane kontraktu atrybut Name ("__type") zgodnie z opisem dalej. Ten atrybut jest tylko mogą być obecne, jeśli atrybut typu JSON jest również obecne i jego [wartość znormalizowaną] "object". Ten atrybut jest używany przez `DataContractJsonSerializer` zachować kontraktu danych informacji o typie — na przykład w przypadku polimorficznym gdzie typem pochodnym jest serializowany i gdzie oczekiwany jest typ podstawowy. Jeśli nie pracujesz z `DataContractJsonSerializer`, w większości przypadków ten atrybut jest ignorowany.  
  
-   [w zakresie przestrzeni nazw] zawiera powiązanie "xml" do "http://www.w3.org/XML/1998/namespace" upoważnieni przez specyfikację typu infoset.  
  
-   [elementy podrzędne], [atrybuty] i [w zakresie przestrzeni nazw] nie może mieć żadnych elementów innych niż określone wcześniej oraz [przestrzeń nazw atrybutów] musi mieć żadnych elementów członkowskich, ale nie należy polegać na następujące fakty podczas odczytywania pliku XML zamapowana z formatu JSON.  
  
 Przykład: Następujący dokument nie ma żadnych mapowania do formatu JSON ponieważ [przestrzeń nazw atrybutów] nie jest pusty.  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 AII dla atrybutu typu JSON ma następującą charakterystykę:  
  
-   [nazwa przestrzeni nazw] nie ma wartości.  
  
-   [prefix] nie ma wartości.  
  
-   [Nazwa lokalna] jest "type".  
  
-   [wartość znormalizowaną] to jedna z wartości typu możliwe opisane w poniższej sekcji.  
  
-   [] jest `true`.  
  
-   [typ atrybutu] nie ma wartości.  
  
-   [odwołań] nie ma wartości.  
  
 AII atrybutu nazwy kontraktu danych ma następującą charakterystykę:  
  
-   [nazwa przestrzeni nazw] nie ma wartości.  
  
-   [prefix] nie ma wartości.  
  
-   [Nazwa lokalna] jest "__type" (dwa znaki podkreślenia, a następnie "typ").  
  
-   [wartość znormalizowaną] jest dowolny prawidłowy ciąg Unicode — mapowania tego ciągu do formatu JSON jest opisany w następnej sekcji.  
  
-   [] jest `true`.  
  
-   [typ atrybutu] nie ma wartości.  
  
-   [odwołań] nie ma wartości.  
  
 Elementy wewnętrzne zawarty w elemencie głównym JSON lub inne elementy wewnętrzne mają następującą charakterystykę:  
  
-   [Nazwa lokalna] może mieć dowolną wartość zgodnie z opisem w dalszej  
  
-   [nazwa przestrzeni nazw], [prefix], [dzieci], [atrybuty], [atrybuty przestrzeni nazw] i [w zakresie przestrzeni nazw] obowiązują te same zasady stosowania jako elementu JSON głównego.  
  
 W elemencie głównym JSON i elementy wewnętrzne atrybut typu JSON Określa mapowania do formatu JSON i możliwych [dzieci] i ich interpretacji. [Wartość znormalizowaną] atrybutu jest rozróżniana wielkość liter i muszą być małymi literami i nie może zawierać spacji.  
  
|[wartość znormalizowany] z `JSON Type Attribute`w AII|Dozwolone [] elementów podrzędnych odpowiedniego EII|Mapowanie do ciągu JSON|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string`(lub Brak typu JSON AII)<br /><br /> A `string` i braku typu JSON AII są tego samego ułatwia `string` domyślny.<br /><br /> Tak `<root> string1</root>` mapuje JSON `string` "ciąg1".|0 lub więcej CIIs|JSON `string` (RFC JSON sekcji 2.5). Każdy `char` jest znak odpowiadający [kod znaku] z CII. Jeśli nie ma żadnych CIIs, mapuje on pusty JSON `string`.<br /><br /> Przykład: Następujący element mapy do fragmentu JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON fragment jest "42".<br /><br /> W pliku XML do mapowania JSON znaków, które muszą być zmienione znaczenie mapy zmienionym znaków, mapowania wszystkie inne znaki, które nie są anulowane. Znak "/" to specjalne — zostanie zmienione jego znaczenie, nawet jeśli nie ma być (napisane się jako "\\/").<br /><br /> Przykład: Następujący element mapy do fragmentu JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment JSON " \\" da\\/ta\\"".<br /><br /> W formacie JSON do pliku XML wszelkie znaki zmienionym i znaki, które nie są wyjściowym mapy poprawnie do odpowiedniego [kod znaku].<br /><br /> Przykład: Fragmentu JSON "\u0041BC" mapuje do następujących elementów XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Ciąg może być ujęte w spacji ("ws" w sekcji 2 JSON RFC) nie pobrać zamapowane do pliku XML.<br /><br /> Przykład: JSON fragmentu "ABC", (występują spacje przed pierwszym podwójnego cudzysłowu), mapy do następujących elementów XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Mapuje żadnych spacji w kodzie XML odstępu w formacie JSON.<br /><br /> Przykład: Następujący element XML mapuje do fragmentu JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON fragment jest "BC".|  
|`number`|CIIs 1 lub więcej|JSON `number` (RFC JSON, sekcji 2.4), prawdopodobnie otoczona odstępu. Każdy znak w połączeniu numer/spacji jest znak odpowiadający [kod znaku] z CII.<br /><br /> Przykład: Następujący element mapy do fragmentu JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON fragment jest 42<br /><br /> (Spacji jest zachowane).|  
|`boolean`|CIIs 4 i 5 (które odpowiada `true` lub `false`), prawdopodobnie otoczone dodatkowe odstępem CIIs.|Sekwencję CII, która odnosi się do ciągu "true" jest zamapowany na literał `true`, oraz sekwencję CII, która odnosi się do ciągu "false" jest zamapowany na literał `false`. Zachowana jest otaczającego odstępu.<br /><br /> Przykład: Następujący element mapy do fragmentu JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment JSON `false`.|  
|`null`|Zezwalaj na Brak.|Literał `null`. W formacie JSON do pliku XML `null` otoczona spacji ("ws" w sekcji 2) nie pobrać zamapowane do pliku XML.<br /><br /> Przykład: Następujący element mapy do fragmentu JSON.<br /><br /> `<root type="null"/>`<br /><br /> lub<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON w obu przypadkach `Null`.|  
|`object`|0 lub więcej EIIs.|A `begin-object` (po lewej nawias klamrowy) w sekcji 2.2 JSON RFC, następuje rekord elementu członkowskiego dla każdego EII zgodnie z opisem w dalszej. Jeśli istnieje więcej niż jeden EII między rekordy elementów są wartości separatorów (przecinkami). Następuje to końcowy — obiekt (prawy nawias klamrowy).<br /><br /> Przykład: Następujący element mapuje fragmentu JSON.<br /><br /> \<Typ główny = "object" ><br /><br /> \<Typ type1 = "string" > aaa\</type1 ><br /><br /> \<Typ type2 = "string" > bbb\</type2 ><br /><br /> \</ root ><br /><br /> Fragment JSON {"type1": "aaa", "type2": "bbb"}.<br /><br /> Jeśli atrybut typu kontraktu danych znajduje się na XML do mapowania JSON, dodatkowy rekord elementu członkowskiego są wstawiane na początku. Jego nazwa jest [Nazwa lokalnego] atrybut typu kontraktu danych ("__type"), a jego wartość wynosi [wartość znormalizowaną] atrybutu. Z drugiej strony, w formacie JSON do pliku XML, jeśli nazwa pierwszego elementu członkowskiego rekordu [Nazwa lokalnego] atrybut typu kontraktu danych (czyli "\__wprowadź"), odpowiedniego atrybutu typu kontraktu danych jest obecny w mapowanej XML, ale nie jest odpowiedni EII obecny. Należy pamiętać, że ten rekord elementu członkowskiego musi występować jako pierwsza w obiekcie JSON to specjalne mapowanie do zastosowania. To oznacza odejście od zwykle przetwarzania JSON, w którym kolejność rekordów element członkowski nie jest znacząca.<br /><br /> Przykład:<br /><br /> Poniższy fragment JSON mapy do pliku XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Plik XML jest następujący kod.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Zwróć uwagę, że \__wprowadź AII jest obecny, ale nie \__wprowadź EII.<br /><br /> Jednak jeśli kolejności w formacie JSON jest wycofywany jako pokazano w poniższym przykładzie.<br /><br /> {"name": "Jan","\__wprowadź": "Osoby"}<br /><br /> Przedstawiono odpowiedniego pliku XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Oznacza to, że \__wprowadź przestaje mają specjalne znaczenie i map do EII w zwykły sposób, nie AII.<br /><br /> Anulowanie unescaping zasady AII [Znormalizowana wartość] Jeśli są mapowane na wartość JSON są takie same, jak w przypadku ciągi formatu JSON, określona w wierszu "string" w tej tabeli.<br /><br /> Przykład:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> z poprzednim przykładem mogą być mapowane do następującego formatu JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Na XML do mapowania JSON nie może być pierwszym EII firmy [Nazwa lokalna] "\__wprowadź".<br /><br /> Odstęp (`ws`) nie jest generowany na XML do mapowania JSON dla obiektów i jest ignorowany w formacie JSON do pliku XML.<br /><br /> Przykład: Poniższy fragment JSON mapuje do elementu XML.<br /><br /> {"DW": "aaa", "ddd": "bbb"}<br /><br /> XML element przedstawiono w poniższym kodzie.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
promień "|0 lub więcej EIIs|Begin — tablicą (otwierający nawias kwadratowy) w sekcji 2.3 JSON RFC następuje rekordu tablicy dla każdego EII zgodnie z opisem w dalszej. Jeśli istnieje więcej niż jeden EII między rekordów tablicy są wartości separatorów (przecinkami). Następuje to koniec tablicy.<br /><br /> Przykład: Następujący element XML mapuje do fragmentu JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON fragment jest ["aaa", "bbb"]<br /><br /> Odstęp (`ws`) nigdy nie został wygenerowany na XML do mapowania JSON dla tablic i jest ignorowany w formacie JSON do pliku XML.<br /><br /> Przykład: AJSON fragmentu.<br /><br /> ["aaa", "bbb"]<br /><br /> Element XML mapowania.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 Rekordy elementów roboczych w następujący sposób:  
  
-   Mapuje wewnętrzny elementu [Nazwa lokalna] `string` częścią `member` zgodnie z definicją w sekcji 2.2 JSON RFC.  
  
 Przykład: Następujący element mapy do fragmentu JSON.  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 Zostanie wyświetlony następujący fragment JSON.  
  
 `{"myLocalName":"aaa"}`  
  
-   W pliku XML do mapowania JSON znaki, które należy użyć znaków ucieczki w formacie JSON będą miały zmienione znaczenie, a innych nie są anulowane. Znak "/", mimo że nie jest to znak, który musi zostać zmieniona, zostanie zmienione znaczenie mimo wszystko (nie ma można użyć znaków ucieczki w formacie JSON do pliku XML). Jest to wymagane do obsługi formatu kodu ASP.NET AJAX `DateTime` dane w formacie JSON.  
  
-   W formacie JSON do pliku XML, wszystkie znaki (w tym znaków nie zmienionym znaczeniu, w razie potrzeby) zostają przeniesieni do formularza `string` daje [Nazwa lokalnego].  
  
-   Elementy wewnętrzne [dzieci] mapy do wartości w sekcji 2.2, zgodnie z `JSON Type Attribute` podobnie jak w przypadku `Root JSON Element`. Wiele poziomów zagnieżdżenia EIIs (w tym zagnieżdżenia w tablicach) są dozwolone.  
  
 Przykład: Następujący element mapy do fragmentu JSON.  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 Poniższy fragment JSON jest, co wskazuje na.  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  Brak nie krok kodowania XML w poprzednim mapowania. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko dokumenty JSON, gdzie wszystkie znaki w nazwach kluczy są prawidłowe znaki w nazwach elementów XML. Na przykład dokument JSON {"<": ""} nie jest obsługiwana, ponieważ < nie jest prawidłową nazwą elementu XML.  
  
 Sytuacja odwrotna (znaki nieprawidłowe w XML, ale nie w formacie JSON) nie powoduje żadnych problemów, ponieważ poprzednie mapowanie zawiera kroki anulowanie unescaping JSON.  
  
 Rejestruje tablicy działają w następujący sposób:  
  
-   Wewnętrzny elementu [Nazwa lokalna] jest "element".  
  
-   Wewnętrzny elementu [dzieci] mapy do wartości w sekcji 2.3, zgodnie z atrybut typu JSON, ponieważ jest elementem głównym JSON. Wiele poziomów zagnieżdżenia EIIs (w tym zagnieżdżenia w obiektach) są dozwolone.  
  
 Przykład: Następujący element mapy do fragmentu JSON.  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 Poniżej przedstawiono JSON fragment.  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
