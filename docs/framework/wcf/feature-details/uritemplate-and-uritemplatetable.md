---
title: Klasy UriTemplate i UriTemplateTable
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b0fedb812cee5cfa1e4c2ff921a78beb2a6c1beb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="uritemplate-and-uritemplatetable"></a>Klasy UriTemplate i UriTemplateTable
Deweloperzy sieci Web wymagają możliwości opis kształtu i układu identyfikatory URI, które odpowiadają swoich usług. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dodano dwa nowe klasy umożliwiają deweloperom kontrolę nad ich identyfikatorów URI. <xref:System.UriTemplate> i <xref:System.UriTemplateTable> stanowią podstawę aparat wysyłki na podstawie identyfikatora URI w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Te klasy można również na ich własnych, dzięki czemu deweloperzy mógł korzystać z szablonów i mechanizmu mapowanie identyfikatora URI bez stosowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
## <a name="templates"></a>Szablony  
 Szablon jest umożliwia opisywanie zestaw względne identyfikatory URI. Zestaw szablonów identyfikatora URI w poniższej tabeli pokazano, jak można zdefiniować systemu, które pobierają różne rodzaje informacji o pogodzie.  
  
|Dane|Szablon|  
|----------|--------------|  
|Prognozy National|pogody/national|  
|Prognozy stanu|pogody / {stanu}|  
|Prognozy miasta|pogody / {stanu} / {Miasto}|  
|Prognozy działania|pogody / {stanu} / {Miasto} / {działania}|  
  
 Poniższa tabela zawiera opis zestawu strukturę podobną identyfikatorów URI. Każdy wpis jest szablon identyfikatora URI. Segmenty w nawiasach klamrowych opisano zmienne. Segmenty nie w nawiasach klamrowych opisano ciągi literału. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Szablonu klasy umożliwiają dewelopera zająć przychodzący identyfikator URI, na przykład "/ pogody/wa/seattle/cyklicznie", i porównuje ją do szablonu, który opisuje, "/weather/ {stanu} / {Miasto} / {działania}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> jest klasa, która hermetyzuje szablon identyfikatora URI. Konstruktor ma parametr typu string, który definiuje szablonu. Ten ciąg zawiera szablon w formacie opisany w następnej sekcji. <xref:System.UriTemplate> Klasa udostępnia metody, które należy spełnić odpowiada przychodzący identyfikator URI do szablonu, wygenerować identyfikator URI na podstawie szablonu, pobierania kolekcję nazwy zmiennych używane w szablonie, określić, czy dwa szablony są równoważne i zwracać szablon ciąg.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> pobiera adres podstawowy i kandydatem identyfikatora URI i próbuje dopasować identyfikatora URI do szablonu. Gdy dopasowanie jest pomyślne, <xref:System.UriTemplateMatch> zwrócone wystąpienie. <xref:System.UriTemplateMatch> Podstawowy identyfikator URI candidate identyfikatora URI kolekcji nazw i wartości parametrów zapytania, Tablica segmentów ścieżki względnej, kolekcji nazw i wartości zmiennych, które zostały spełnione, zawiera obiekt <xref:System.UriTemplate> wystąpienie używane w celu wykonania dopasowania , ciąg, który zawiera niedopasowane części candidate identyfikatora URI (stosowane, gdy szablon ma symboli wieloznacznych), a obiekt, który jest skojarzony z szablonem.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Klasy ignoruje schemat i numer portu podczas dopasowywania identyfikatora URI kandydatem do szablonu.  
  
 Istnieją dwie metody, dzięki którym można wygenerować identyfikatora URI na podstawie szablonu, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> pobiera adres podstawowy i kolekcję nazw i wartości parametrów. Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązana. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> pobiera pary nazwa/wartość i zastępuje je od lewej do prawej.  
  
 <xref:System.UriTemplate.ToString> Zwraca ciąg szablonu.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Właściwość zawiera kolekcję nazw zmiennych w segmentach ścieżki w ciągu szablonu.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> Trwa <xref:System.UriTemplate> jako parametr i zwraca wartość logiczną, która określa, czy dwa szablony są równoważne. Aby uzyskać więcej informacji zobacz sekcję równoważność szablonu w dalszej części tego tematu.  
  
 <xref:System.UriTemplate> jest przeznaczona do pracy z dowolnego schemat URI, który odpowiada gramatyki identyfikator URI protokołu HTTP. Poniżej przedstawiono przykłady obsługiwane schematy identyfikatorów URI.  
  
-   http://  
  
-   https://  
  
-   net.tcp://  
  
-   NET.pipe://  
  
-   sb://  
  
 Systemy, takie jak file:// i urn: / / nie odpowiadać gramatyce identyfikator URI protokołu HTTP i spowodować nieprzewidywalne skutki, gdy jest używany z szablonów identyfikatora URI.  
  
### <a name="template-string-syntax"></a>Składnia ciągu szablonu  
 Szablon ma trzy części: ścieżki, opcjonalne zapytania i opcjonalne fragmentu. Na przykład zobacz następujący szablon:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Ścieżka składa się z "/weather/ {stanu} / {Miasto}", zapytanie składa się z"? prognozy = {długość}, a fragment składa się z"#frag1".  
  
 Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki. Wyrażenia zapytania i fragment można całkowicie pominąć. Ścieżka składa się z szeregu segmentów rozdzielonych przez '/', każdy z segmentów może mieć wartość literału, nazwa zmiennej (zapisany w {nawiasy klamrowe}) lub symbolem wieloznacznym (zapisane jako\*"). W szablonie poprzedniej "\weather\ segmentu jest literałem wartość podczas"stan {}"i"{Miasto}"są zmienne. Zmienne podjąć odpowiednią nazwę z zawartości ich nawiasy klamrowe, a później mogą być zastępowane z konkretną wartość, aby utworzyć *zamknięte URI*. Symbol wieloznaczny jest opcjonalne, ale może wystąpić tylko na końcu identyfikator URI, których logicznie pasuje "pozostałej części ścieżki".  
  
 Wyrażenia zapytania, jeśli jest dostępna Określa ciąg par nazwa/wartość nieuporządkowaną rozdzielone 'i'. Elementy wyrażenia zapytania mogą być pary literału (x = 2) dysków lub para zmiennej (x = {var}). Tylko po prawej stronie zapytania może mieć zmiennej wyrażenia. ({JakaśNazwa} = {someValue} nie jest dozwolone. Nieparzysty wartości (? x) nie są dozwolone. Nie ma żadnej różnicy między wyrażeniem zapytania pusta w wyrażeniu kwerendy składające się z tylko jedną "?" (zarówno oznacza "wszelkie zapytania").  
  
 Wyrażenie fragmentacji może składać się z wartością literałową, zmienne nie są dozwolone.  
  
 Wszystkie nazwy zmiennych szablonu w ciągu szablonu musi być unikatowa. Nazwy zmiennych szablonu jest rozróżniana wielkość liter.  
  
 Przykłady ciągów prawidłowego szablonu:  
  
-   ""  
  
-   "/ uniesienia"  
  
-   "/ buta / *"  
  
-   "{buta} / łodzi"  
  
-   "{buta} / {łodzi} /bed/ {patchworkowa}"  
  
-   "uniesienia / {łodzi}"  
  
-   "uniesienia / {łodzi} / *"  
  
-   "buta/łodzi? x = 2"  
  
-   "uniesienia / {łodzi}? x = {bielizny}"  
  
-   "uniesienia / {łodzi}? x = {bielizny} & y = poza pasmem"  
  
-   "? x = {buta}"  
  
-   "buta? x = 3 & y = {var}  
  
 Przykłady parametrów szablonu jest nieprawidłowa:  
  
-   "{buta} / {UNIESIENIA} / x = 2" — zduplikowane nazwy zmiennej.  
  
-   "{buta} /boat/? bielizny = {buta}" — zduplikowane nazwy zmiennej.  
  
-   "? x = 2 & x = 3" — pary nazwa/wartość ciągu zapytania musi być unikatowa, nawet jeśli są one literały.  
  
-   "? x = 2 &" — ciąg zapytania jest nieprawidłowo sformułowany.  
  
-   "? 2 & x = {buta}" — ciąg zapytania musi mieć pary nazwa/wartość.  
  
-   "? y = 2 & & X = 3" — ciąg zapytania musi być par wartości nazw, nazwa nie może rozpoczynać się 'i'.  
  
### <a name="compound-path-segments"></a>Segmenty ścieżki złożone  
 Segmenty ścieżki złożonej Zezwalaj pojedynczy segment ścieżki identyfikatora URI zawiera wiele zmiennych, a także zmienne w połączeniu z literały. Poniżej przedstawiono przykłady segmentów prawidłową ścieżkę złożonego.  
  
-   /filename.{ext}/  
  
-   /{filename}.jpg/  
  
-   /{filename}.{ext}/  
  
-   /{a}.{b}someLiteral{c}({d})/  
  
 Poniżej przedstawiono przykłady segmentów nieprawidłową ścieżkę.  
  
-   /{} -Zmienne musi mieć nazwę.  
  
-   / {łodzi} - {uniesienia} zmiennych muszą być oddzielone literału.  
  
### <a name="matching-and-compound-path-segments"></a>Segmenty ścieżki dopasowywania i złożone  
 Segmenty ścieżki złożonej zezwala na określanie obiektu UriTemplate, która ma wiele zmiennych w segmencie pojedynczą ścieżkę. Na przykład w poniższym ciągu szablonu: "adresy / {stanu}. {Miasto} "dwie zmienne (stanu i miasta) są zdefiniowane w ten sam segment. Ten szablon spowoduje dopasowanie takie jak adres URL "http://example.com/Washington.Redmond", ale adres URL, jak również będzie odpowiadała"http://example.com/Washington.Redmond.Microsoft". W drugim przypadku zmiennej stanu będzie zawierać "W stanie Waszyngton" i zmiennej Miasto będzie zawierać "Redmond.Microsoft". W takim przypadku tekstem (z wyjątkiem "/") będzie odpowiadała zmiennej {miasto}. Szablon, który nie będzie odpowiadała "dodatkowy" tekst, umieść zmiennej w segmencie oddzielnego szablonu, na przykład: "adresy / {stanu} / {miasto}.  
  
### <a name="named-wildcard-segments"></a>Segmenty nazwanego symboli wieloznacznych  
 Segment o nazwie symboli wieloznacznych jest żadnych segment zmiennej ścieżki których nazwa zmiennej rozpoczyna się od znaku wieloznacznego "*". Następujący ciąg szablonu zawiera segment wieloznaczny nazwane o nazwie "buta".  
  
```  
"literal/{*shoe}"  
```  
  
 Segmenty symboli wieloznacznych, należy wykonać następujące reguły:  
  
-   Może istnieć co najwyżej jeden segment o nazwie symboli wieloznacznych dla każdego ciąg szablonu.  
  
-   Segment o nazwie symbolu wieloznacznego musi znajdować się na prawej segment w ścieżce.  
  
-   Segment o nazwie wieloznaczny nie może współistnieć z segment wieloznaczny anonimowe ciągu szablonu.  
  
-   Nazwa segment wieloznaczny nazwanego musi być unikatowa.  
  
-   O nazwie symbolu wieloznacznego segmentów nie może mieć wartości domyślne.  
  
-   Segmenty nazwanego symbolu wieloznacznego nie może kończyć się "/".  
  
### <a name="default-variable-values"></a>Domyślne wartości zmiennej  
 Domyślne wartości zmiennej umożliwiają określanie wartości domyślnych do zmiennych w ramach szablonu. Można określić domyślne zmienne w nawiasach klamrowych, które zadeklarować zmienną lub jako kolekcja przekazany do konstruktora obiektu UriTemplate. Następujący szablon przedstawia dwa sposoby określ <xref:System.UriTemplate> ze zmiennymi wartościami domyślnymi.  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Ten szablon deklaruje zmienną o nazwie `a` z wartością domyślną `1` i zmiennej o nazwie `b` z wartością domyślną `5`.  
  
> [!NOTE]
>  Tylko zmienne segmentu ścieżki mogą mają przypisane wartości domyślne. Zmiennych ciągu zapytania, zmienne złożonego segmentu i zmienne nazwanego symbolu wieloznacznego nie mogą mieć wartości domyślne.  
  
 Poniższy kod przedstawia sposób obsługi domyślnych wartości zmiennych podczas dopasowywania identyfikatora URI kandydatem.  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  Identyfikator URI, takich jak http://localhost:8000/// pasuje do szablonu, jednak wymienione w poprzednim kodzie identyfikatora URI, takich jak http://localhost:8000/ jest.  
  
 Poniższy kod przedstawia sposób obsługi domyślnych wartości zmiennych podczas tworzenia identyfikator URI przy użyciu szablonu.  
  
```  
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
  
 Gdy zmienna znajduje się wartość domyślną równą `null` istnieją pewne dodatkowe ograniczenia. Zmienna może mieć wartości domyślnej równej `null` Jeśli zmienna jest zawarty w prawo większości segment ciąg szablonu lub wszystkie segmenty z prawej strony segmentu ma domyślne wartości `null`. Poniżej podano prawidłowy szablon parametry z wartościami domyślnymi `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 Poniżej podano nieprawidłowy szablon parametry z wartościami domyślnymi `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>Wartości domyślne i dopasowywanie  
 Podczas dopasowywania candidate identyfikator URI przy użyciu szablonu, który zawiera wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli nie określono wartości w candidate identyfikatora URI.  
  
### <a name="template-equivalence"></a>Równoważność szablonu  
 Dwa szablony są określane jako *strukturę równoważne* gdy wszystkie te szablony literałów odpowiadać i mają zmiennych w segmentach tego samego. Na przykład następujące szablony są strukturalnie równoważne:  
  
-   b /b /a/ {var1} / {var2}? x = 1 & y = 2  
  
-   a/{x}/b%20b/{var1}?y=2&x=1  
  
-   a/{y}/B%20B/{z}/?y=2&x=1  
  
 Zwróć uwagę kilka istotnych:  
  
-   Jeśli szablon zawiera początkowe ukośniki, tylko pierwszy z nich jest ignorowana.  
  
-   Podczas porównywania ciągów szablonów do pełnienia roli równoważnika strukturalnych, wielkość liter jest ignorowana w nazwach zmiennych i segmentów ścieżki, ciągów zapytania jest uwzględniana wielkość liter.  
  
-   Ciągi zapytań są nieuporządkowane.  
  
## <a name="uritemplatetable"></a>Obiekt UriTemplateTable  
 <xref:System.UriTemplateTable> Klasa reprezentuje asocjacyjnej spis <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera na wybór. A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. Zawartość <xref:System.UriTemplateTable> można go zmienić, dopóki <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana. Sprawdzanie poprawności jest wykonywane podczas <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana. Typ weryfikacji wykonać zależy od wartości `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `false`, <xref:System.UriTemplateTable> kontroli, aby upewnić się, że nie ma szablonów w tabeli. Jeśli znajdzie żadnych szablonów strukturalnie równoważne zgłasza wyjątek. Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gdy chcesz zapewnić tylko jeden szablon URI przychodzącego jest zgodna.  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `true`, <xref:System.UriTemplateTable> umożliwia wielu strukturalnie równoważne szablony mają być zawarte w <xref:System.UriTemplateTable>.  
  
 Jeśli zestaw <xref:System.UriTemplate> obiekty dodane do <xref:System.UriTemplateTable> zawiera ciągi zapytań nie może być niejednoznaczna. Ciągi zapytań identyczne są dozwolone.  
  
> [!NOTE]
>  Gdy <xref:System.UriTemplateTable> umożliwia base adresów tego użycia systemów innych niż HTTP, schemat i numer portu są ignorowane podczas dopasowywania candidate identyfikatorów URI do szablonów.  
  
### <a name="query-string-ambiguity"></a>Niejednoznaczności ciąg zapytania  
 Szablonów mających równoważną ścieżkę zawiera ciągi zapytań niejednoznaczny, jeśli identyfikator URI, który odpowiada więcej niż jeden szablon.  
  
 Następujące zestawy ciągi zapytań są jednoznaczne między sobą:  
  
-   ?x=1  
  
-   ?x=2  
  
-   ?x=3  
  
-   ? x = 1 & y = {var}  
  
-   ?x=2&z={var}  
  
-   ?x=3  
  
-   ?x=1  
  
-   ?  
  
-   ? x = {var}  
  
-   ?  
  
-   ?m=get&c=rss  
  
-   ?m=put&c=rss  
  
-   ?m=get&c=atom  
  
-   ?m=put&c=atom  
  
 Następujące zestawy szablonów ciąg zapytania są niejednoznaczne między sobą:  
  
-   ?x=1  
  
-   ? x = {var}  
  
 "x = 1" — jest zgodny zarówno szablonów.  
  
-   ?x=1  
  
-   ?y=2  
  
 "x = 1 & y = 2" jest zgodny zarówno szablonów. Jest to spowodowane ciąg zapytania mogą zawierać więcej zmiennych ciągu zapytania, a następnie szablon zgodny.  
  
-   ?x=1  
  
-   ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" jest zgodny zarówno szablonów.  
  
-   ?x=3&y=4  
  
-   ?x=3&z=5  
  
> [!NOTE]
>  Α znaków i Α są traktowane jako różne znaki gdy są one wyświetlane jako część ścieżka identyfikatora URI lub <xref:System.UriTemplate> literał segmentu ścieżki (ale a znaków i A są traktowane jako taki sam). Α znaków i Α są traktowane jako znaków gdy są one wyświetlane jako część a <xref:System.UriTemplate> {variableName} lub ciąg kwerendy (i a i A są także traktowane jako znaków).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [Tabela UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Dyspozytor tabeli UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
