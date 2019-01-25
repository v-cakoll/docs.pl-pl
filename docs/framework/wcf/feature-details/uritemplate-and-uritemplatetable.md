---
title: Klasy UriTemplate i UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 3fd60325d2264a2ddeaabef7b0998844ca8c8cd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722611"
---
# <a name="uritemplate-and-uritemplatetable"></a>Klasy UriTemplate i UriTemplateTable
Deweloperzy sieci Web muszą mieć możliwość opisują kształt i układ identyfikatory URI, które ich usługom, odpowiadanie na. Windows Communication Foundation (WCF) dodano dwa nowe klasy oferuje deweloperom kontrolę nad ich identyfikatorów URI. <xref:System.UriTemplate> i <xref:System.UriTemplateTable> stanowią podstawę aparatu wysyłania na podstawie identyfikatora URI programu WCF. Te klasy można również na mechanizmie własnych, dzięki czemu deweloperzy mogą korzystać ze szablonów i identyfikatora URI mapowania bez implementacji usługi WCF.  
  
## <a name="templates"></a>Szablony  
 Szablon jest sposób opisania zestawu względne identyfikatory URI. Zestaw szablonów identyfikatora URI w poniższej tabeli przedstawiono, jak mogą być zdefiniowane system, który pobiera różne rodzaje informacji o pogodzie.  
  
|Dane|Szablon|  
|----------|--------------|  
|Krajowe prognozy|pogoda/national|  
|Stan prognozy|pogoda / {state}|  
|Miasto prognozy|pogoda / {state} / {Miasto}|  
|Działanie prognozy|pogoda / {state} / {Miasto} / {działania}|  
  
 W tej tabeli opisano zestaw strukturalnie podobne identyfikatorów URI. Każdego wpisu jest szablon identyfikatora URI. Segmenty w nawiasach klamrowych opisano zmienne. Segmenty w nawiasy klamrowe nie opisano ciągami tekstowymi. Klasy szablonu WCF umożliwiają deweloperom używają przychodzącego identyfikatora URI, na przykład, "/ pogody/wa/seattle/cykliczny" i dopasować go do szablonu, który opisuje, "/weather/ {stan} / {Miasto} / {działania}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> jest to klasa, która hermetyzuje szablon identyfikatora URI. Konstruktor przyjmuje jako parametr ciągu, który definiuje szablon. Ten ciąg zawiera szablon w formacie opisanym w następnej sekcji. <xref:System.UriTemplate> Klasa dostarcza metody, które pozwalają dopasować identyfikatora URI przychodzącego do szablonu, wygenerować identyfikator URI na podstawie szablonu, pobieranie kolekcji nazwy zmiennych, używany w szablonie, określić, czy dwa szablony są równoważne i zwraca szablonu ciąg.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> pobiera adres podstawowy i Kandydat, identyfikator URI i próbuje dopasować identyfikatora URI do szablonu. Jeśli dopasowanie się powiedzie, <xref:System.UriTemplateMatch> wystąpienie jest zwracane. <xref:System.UriTemplateMatch> Obiekt zawiera podstawowy identyfikator URI Release candidate identyfikatora URI kolekcji nazwa/wartość parametrów zapytania, Tablica segmentów ścieżki względnej, kolekcji nazw i wartości zmiennych, które zostały dopasowane <xref:System.UriTemplate> wystąpienie używane do wykonania dopasowania , ciąg, który zawiera Niedopasowany jakiejkolwiek jego części Release candidate identyfikatora URI (stosowane, gdy szablon ma symbol wieloznaczny), a obiekt, który jest skojarzony z szablonem.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Klasy ignoruje schemat i numer portu podczas dopasowywania Release candidate identyfikatora URI do szablonu.  
  
 Istnieją dwie metody, które umożliwiają Generowanie identyfikatora URI z szablonem, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> pobiera adres podstawowy i kolekcji nazwa/wartość parametrów. Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązana. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> pobiera pary nazwa/wartość i zastępuje je od lewej do prawej.  
  
 <xref:System.UriTemplate.ToString> Zwraca ciąg szablonu.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Właściwość zawiera kolekcję nazw zmiennych, używane w ramach segmenty ścieżki w parametrach szablonu.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> Trwa <xref:System.UriTemplate> jako parametr i zwraca wartość logiczną, która określa, czy dwa szablony są równoważne. Aby uzyskać więcej informacji zobacz sekcję szablonu równoważności w dalszej części tego tematu.  
  
 <xref:System.UriTemplate> jest przeznaczona do pracy z dowolnego schematu identyfikatora URI, który jest zgodny z gramatyki identyfikator URI protokołu HTTP. Poniżej przedstawiono przykłady obsługiwane schematy identyfikatorów URI.  
  
- http://  
  
- https://  
  
- net.tcp://  
  
- net.pipe://  
  
- sb://  
  
 Schematy, takich jak file:// i urn: / / nie są zgodne z gramatyki identyfikator URI protokołu HTTP i powodować nieprzewidywalne skutki, gdy jest używana z szablonami identyfikatora URI.  
  
### <a name="template-string-syntax"></a>Składnia ciągu szablonu  
 Szablon ma trzy części: ścieżki, opcjonalne zapytanie i fragment opcjonalne. Aby uzyskać przykład zobacz następujący szablon:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Ścieżka składa się z "/weather/ {stan} / {Miasto}", zapytanie składa się z"? prognozy = {length}, i zawiera fragmentu"#frag1".  
  
 Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki. Wyrażenia zapytań i fragment można pominąć całkowicie. Ścieżka składa się z szeregu segmentów rozdzielonych przez '/', każdy z segmentów może mieć wartości literału, nazwa zmiennej (napisanego w {nawiasów klamrowych}) lub symbol wieloznaczny (zapisane jako\*"). W szablonie poprzedniego "\weather\ segmentu jest literałem wartości podczas"{state}"i"{city}"są zmiennymi. Zmienne pobrać nazwy z zawartości ich nawiasów klamrowych i ich później można zastąpić wartością konkretną wartość, aby utworzyć *zamknięte URI*. Symbol wieloznaczny jest opcjonalne, ale może wystąpić tylko na końcu identyfikatora URI, których logicznie odpowiada "pozostałą część ścieżki".  
  
 Wyrażenie zapytania, jeśli jest obecny, określa szereg nieuporządkowaną nazwę/pary wartości rozdzielane znakami "&". Elementy wyrażenia zapytania może to być literał pary (x = 2) lub pary zmiennej (x = {var}). Tylko po prawej stronie zapytania może mieć zmiennej wyrażenia. ({JakaśNazwa} = {wartość someValue} nie jest dozwolone. Niesparowane wartości (? x) nie są dozwolone. Nie ma żadnej różnicy między wyrażenie pustego zapytania i składający się z tylko jednego wyrażenia zapytania "?" (zarówno oznacza "dowolne zapytanie").  
  
 Wyrażenie fragmentacji może składać się z wartością literału, zmienne nie są dozwolone.  
  
 Wszystkie nazwy zmiennej szablonu w ciągu szablonu muszą być unikatowe. Nazwy zmiennych szablonu jest rozróżniana wielkość liter.  
  
 Przykłady ciągów prawidłowy szablon:  
  
- ""  
  
- "/ uniesienia"  
  
- "/shoe/\*"  
  
- "{buta} / łodzi"  
  
- "{shoe}/{boat}/bed/{quilt}"  
  
- "uniesienia / {łodzi}"  
  
- "uniesienia / {łodzi} /\*"  
  
- "buta/łodzi? x = 2"  
  
- "uniesienia / {łodzi}? x = {bielizny}"  
  
- "uniesienia / {łodzi}? x = {bielizny} & y = poza pasmem"  
  
- "?x={shoe}"  
  
- "buta? x = 3 & y = {var}  
  
 Przykłady ciągów nieprawidłowy szablon:  
  
- "{buta} / {UNIESIENIA} / x = 2" — zduplikowane nazwy zmiennej.  
  
- "{buta} /boat/? bielizny = {buta}" — zduplikowane nazwy zmiennej.  
  
- "? x = 2 & x = 3" — pary nazwa/wartość w ciągu zapytania musi być unikatowa, nawet jeśli są literały.  
  
- "? x = 2 &" — ciąg zapytania jest nieprawidłowo sformułowany.  
  
- "? 2 & x = {buta}" — ciąg zapytania musi być pary nazwa/wartość.  
  
- "? y = 2 & & X = 3" — ciąg zapytania musi być pary nazwa / wartość, nazwy nie może zaczynać 'i'.  
  
### <a name="compound-path-segments"></a>Segmenty ścieżki złożona (c)  
 Segmenty ścieżki złożonej zezwala na pojedynczy segment ścieżki identyfikatora URI zawiera wiele zmiennych, a także zmienne w połączeniu z literałami. Poniżej przedstawiono przykłady segmentów prawidłową ścieżkę złożoną.  
  
- /filename.{ext}/  
  
- /{filename}.jpg/  
  
- /{filename}.{ext}/  
  
- /{a}.{b}someLiteral{c}({d})/  
  
 Poniżej przedstawiono przykłady segmentów nieprawidłową ścieżkę.  
  
- /{} — Zmienne musi mieć nazwę.  
  
- / {uniesienia} {łodzi} — zmienne muszą być rozdzielone literału.  
  
### <a name="matching-and-compound-path-segments"></a>Zgodne i złożone segmenty ścieżki  
 Segmenty ścieżki złożonej umożliwiają definiowanie UriTemplate, który ma wiele zmiennych w segmencie pojedynczą ścieżkę. Na przykład w następujący ciąg szablonu: "Adresów / {state}. {Miasto} "w tym samym segmencie są zdefiniowane dwie zmienne (stanu i miasta). Ten szablon będzie odpowiadać takie jak adres URL `http://example.com/Washington.Redmond` , ale również pokaże adresu URL, takich jak `http://example.com/Washington.Redmond.Microsoft`. W tym ostatnim przypadku zmiennej stanu będzie zawierać "Waszyngton", a zmienna Miasto będzie zawierać "Redmond.Microsoft". W takim przypadku dowolny tekst (z wyjątkiem "/") będzie odpowiadał zmiennej {miasto}. Szablon, który nie będą zgodne z tekstem "dodatkowe", umieść zmienną w segmencie oddzielne szablonu, na przykład: "Adresów / {state} / {miasto}.  
  
### <a name="named-wildcard-segments"></a>Segmenty nazwanych symboli wieloznacznych  
 Segment nazwanych symboli wieloznacznych jest żadnych zmiennych segmentu ścieżki którego nazwa zmiennej zaczyna się od znaku wieloznacznego "\*". Następujący ciąg szablonu zawiera nazwanych symboli wieloznacznych segment o nazwie "buta".  
  
```  
"literal/{*shoe}"  
```  
  
 Segmenty symboli wieloznacznych, należy wykonać następujące reguły:  
  
- Może być co najwyżej jeden segment nazwanych symboli wieloznacznych dla każdego ciągu szablonu.  
  
- Segment o nazwie symbolu wieloznacznego musi znajdować się w segmencie najdalej z prawej strony w ścieżce.  
  
- Segment o nazwie symbolu wieloznacznego nie może współistnieć z segment wieloznaczny anonimowe, w ramach tych samych parametrach szablonu.  
  
- Nazwa segmentu nazwany symbol wieloznaczny musi być unikatowa.  
  
- Segmenty, o nazwie symbolu wieloznacznego nie może mieć wartości domyślne.  
  
- Segmentów nazwanych symboli wieloznacznych nie może kończyć się znakiem "/".  
  
### <a name="default-variable-values"></a>Domyślne wartości zmiennej  
 Domyślne wartości zmiennej umożliwiają określanie wartości domyślnych dla zmiennych w szablonie. Domyślne zmienne można określić za pomocą nawiasów klamrowych, które Zadeklaruj zmienną lub jako kolekcja przekazany do konstruktora UriTemplate. Następujący szablon przedstawia dwa sposoby określania <xref:System.UriTemplate> za pomocą zmiennych z wartościami domyślnymi.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Ten szablon deklaruje zmienną o nazwie `a` z wartością domyślną `1` i zmienną o nazwie `b` z wartością domyślną `5`.  
  
> [!NOTE]
>  Tylko zmienne segmentu ścieżki mogą mają przypisane wartości domyślne. Zmiennych ciągu zapytania, zmienne złożonego segmentu i zmiennych nazwanych symboli wieloznacznych nie mogą mieć wartości domyślne.  
  
 Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas dopasowywania identyfikatora URI Kandydat.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> Identyfikator URI, takich jak `http://localhost:8000///` jest niezgodna z szablonu wymienionych w poprzednim kodzie jednak identyfikatora URI, takich jak `http://localhost:8000/` jest.  
  
 Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas tworzenia identyfikatora URI za pomocą szablonu.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
Gdy zmienna ta otrzymuje wartość domyślną `null` istnieją pewne dodatkowe ograniczenia. Zmienna może mieć wartość domyślną `null` czy zmienna jest zawarty w prawo większość segment ciąg szablonu, czy wszystkie segmenty po prawej stronie segmentu mają przypisane wartości domyślne dla `null`. Poniżej podano prawidłowy szablon ciągi z wartościami domyślnymi `null`:  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Poniżej podano nieprawidłowy szablon ciągi z wartościami domyślnymi `null`:  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Wartości domyślne i dopasowania  
 Podczas dopasowywania Release candidate identyfikatora URI za pomocą szablonu, który zawiera wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli wartości nie są określone w identyfikatorze URI Release candidate.  
  
### <a name="template-equivalence"></a>Template Equivalence  
 Dwa szablony są określane jako *strukturalnie równoważne* kiedy wszystkie szablony literały odpowiadać i mają zmiennych w tej samej segmentów. Na przykład poniższe szablony są strukturalnie równoważne:  
  
- b /b /a/ {var1} / {var2}? x = 1 & y = 2  
  
- a/{x}/b%20b/{var1}?y=2&x=1  
  
- a/{y}/B%20B/{z}/?y=2&x=1  
  
 Kilka istotnych kwestii:  
  
- Jeśli szablon zawiera ukośników wiodących, tylko pierwszy z nich jest ignorowany.  
  
- Podczas porównywania ciągi szablonu dla równoważności strukturalnych, wielkość liter jest ignorowana w nazwach zmiennych i segmenty ścieżki, ciągi zapytań jest uwzględniana wielkość liter.  
  
- Ciągi zapytania są nieuporządkowane.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Klasa reprezentuje asocjacyjnych tabelę <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera jego wybranie. A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. Zawartość <xref:System.UriTemplateTable> można zmienić do czasu <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana. Sprawdzanie poprawności jest wykonywane podczas <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana. Typ weryfikacji, wykonywane są zależne od wartości `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `false`, <xref:System.UriTemplateTable> kontrole, aby upewnić się, Brak szablonów w tabeli. Jeśli zostaną znalezione żadne szablony strukturalnie równoważne, zgłasza wyjątek. Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gdy zachodzi potrzeba zapewnienia tylko jeden szablon pasuje do przychodzącego identyfikatora URI.  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `true`, <xref:System.UriTemplateTable> zezwala na wiele szablonów strukturalnie równoważne, muszą być zawarte w <xref:System.UriTemplateTable>.  
  
 Jeśli zestaw <xref:System.UriTemplate> obiekty dodane do <xref:System.UriTemplateTable> zawierających ciągi zapytań nie może być niejednoznaczna. Ciągi zapytań identyczne są dozwolone.  
  
> [!NOTE]
>  Gdy <xref:System.UriTemplateTable> umożliwia base adresów tego schematów użycia innego niż HTTP, to schemat, a numer portu są ignorowane podczas dopasowywania Release candidate identyfikatorów URI do szablonów.  
  
### <a name="query-string-ambiguity"></a>Niejednoznaczności ciągu zapytania  
 Szablony, które są równoważne ścieżkę udziału zawierają ciągi zapytań niejednoznaczne, jeśli identyfikator URI, który odpowiada więcej niż jeden szablon.  
  
 Następujące zestawy ciągów zapytań są jednoznaczne między sobą:  
  
- ?x=1  
  
- ?x=2  
  
- ?x=3  
  
- ? x = 1 & y = {var}  
  
- ?x=2&z={var}  
  
- ?x=3  
  
- ?x=1  
  
- ?  
  
- ? x={var}  
  
- ?  
  
- ?m=get&c=rss  
  
- ?m=put&c=rss  
  
- ?m=get&c=atom  
  
- ?m=put&c=atom  
  
 Następujące zestawy szablony ciągów zapytania są niejednoznaczne między sobą:  
  
- ?x=1  
  
- ? x = {var}  
  
 "x = 1"-dopasowuje oba szablony.  
  
- ?x=1  
  
- ?y=2  
  
 "x = 1 & y = 2" odpowiada oba szablony. Jest to spowodowane ciągu zapytania może zawierać więcej zmiennych ciągu zapytania, a następnie dopasowuje szablon.  
  
- ?x=1  
  
- ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" odpowiada oba szablony.  
  
- ?x=3&y=4  
  
- ?x=3&z=5  
  
> [!NOTE]
> Α znaków i Α są traktowane jako różne znaki pojawiających się jako część ścieżka identyfikatora URI lub <xref:System.UriTemplate> literał segmentu ścieżki (ale a znaków i A są traktowane jako taki sam). Α znaków i Α są uznawane za te same znaki pojawiających się jako część a <xref:System.UriTemplate> {variableName} lub ciąg zapytania (i a i A są również uważana za te same znaki).  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [Tabela UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dyspozytor tabeli UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
