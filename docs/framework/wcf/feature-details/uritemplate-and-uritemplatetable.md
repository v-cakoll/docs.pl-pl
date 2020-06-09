---
title: Klasy UriTemplate i UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 106ba21b58dabab96afbc8fb6db5cb305386f2fe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595079"
---
# <a name="uritemplate-and-uritemplatetable"></a>Klasy UriTemplate i UriTemplateTable
Deweloperzy sieci Web wymagają możliwości opisania kształtu i układu identyfikatorów URI, na które odpowiada ich usługi. Windows Communication Foundation (WCF) dodał dwie nowe klasy, aby umożliwić deweloperom kontrolę nad ich identyfikatorami URI. <xref:System.UriTemplate>i <xref:System.UriTemplateTable> stanowi podstawę aparatu wysyłania opartego na identyfikatorze URI w programie WCF. Te klasy mogą być również używane samodzielnie, co pozwala deweloperom korzystać z szablonów i mechanizmu mapowania identyfikatorów URI bez implementowania usługi WCF.  
  
## <a name="templates"></a>Szablony  
 Szablon jest sposobem opisu zestawu względnych identyfikatorów URI. Zestaw szablonów identyfikatorów URI w poniższej tabeli pokazuje, jak można zdefiniować system, który pobiera różne typy informacji o pogodzie.  
  
|Dane|Szablon|  
|----------|--------------|  
|Prognoza krajowa|Pogoda/narodowe|  
|Prognoza stanu|Pogoda/{State}|  
|Prognoza miejscowości|Pogoda/{State}/{City}|  
|Prognoza działań|Pogoda/{State}/{City}/{Activity}|  
  
 W tej tabeli opisano zestaw podobnych identyfikatorów URI. Każdy wpis jest szablonem identyfikatora URI. Segmenty w nawiasach klamrowych opisują zmienne. Segmenty nie w nawiasach klamrowych opisują ciągi literału. Klasy szablonów WCF umożliwiają deweloperowi przejęcie przychodzącego identyfikatora URI, na przykład "/Weather/wa/Seattle/Cycling" i dopasowanie go do szablonu opisującego go, "/Weather/{State}/{City}/{Activity}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate>jest klasą, która hermetyzuje szablon identyfikatora URI. Konstruktor przyjmuje parametr ciągu, który definiuje szablon. Ten ciąg zawiera szablon w formacie opisanym w następnej sekcji. <xref:System.UriTemplate>Klasa zawiera metody, które umożliwiają dopasowanie przychodzącego identyfikatora URI do szablonu, generowanie identyfikatora URI na podstawie szablonu, pobieranie kolekcji nazw zmiennych używanych w szablonie, określanie, czy dwa szablony są równoważne i zwracają ciąg szablonu.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>Pobiera adres podstawowy i identyfikator URI kandydata, a następnie próbuje dopasować identyfikator URI do szablonu. Jeśli dopasowanie zakończyło się pomyślnie, <xref:System.UriTemplateMatch> zostanie zwrócone wystąpienie. <xref:System.UriTemplateMatch>Obiekt zawiera podstawowy identyfikator URI, identyfikator URI kandydata, Kolekcja nazw/wartości parametrów zapytania, Tablica segmentów ścieżki względnej, Kolekcja nazw/wartości zmiennych, które zostały dopasowane, <xref:System.UriTemplate> wystąpienie użyte do przeprowadzenia dopasowania, ciąg, który zawiera niedopasowaną część identyfikatora URI kandydata (używany, gdy szablon ma symbol wieloznaczny), oraz obiekt, który jest skojarzony z szablonem.  
  
> [!NOTE]
> <xref:System.UriTemplate>Klasa ignoruje schemat i numer portu podczas dopasowywania do szablonu identyfikatora URI kandydata.  
  
 Istnieją dwie metody, które umożliwiają generowanie identyfikatora URI na podstawie szablonu <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> . <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>przyjmuje adres podstawowy i kolekcję nazw/wartości parametrów. Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązany. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>przyjmuje pary nazwa/wartość i zastępuje je lewej strony.  
  
 <xref:System.UriTemplate.ToString>Zwraca ciąg szablonu.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A>Właściwość zawiera kolekcję nazw zmiennych używanych w segmentach ścieżki w ciągu szablonu.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>przyjmuje <xref:System.UriTemplate> jako parametr i zwraca wartość logiczną określającą, czy dwa szablony są równoważne. Aby uzyskać więcej informacji, zobacz sekcję równoważność szablonu w dalszej części tego tematu.  
  
 <xref:System.UriTemplate>Program jest przeznaczony do pracy z dowolnym schematem identyfikatorów URI, który jest zgodny z gramatyką URI protokołu HTTP. Poniżej przedstawiono przykłady obsługiwanych schematów URI.  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 Schematy, takie jak file://i urn://, nie są zgodne z gramatyką URI HTTP i powodują nieprzewidywalne wyniki w przypadku używania z szablonami identyfikatorów URI.  
  
### <a name="template-string-syntax"></a>Składnia ciągu szablonu  
 Szablon składa się z trzech części: ścieżki, opcjonalnego zapytania i opcjonalnego fragmentu. Aby zapoznać się z przykładem, zobacz następujący szablon:  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 Ścieżka składa się z "/Weather/{State}/{City}", zapytanie składa się z "? Prognoza = {Length}, a fragment składa się z" #frag1 ".  
  
 Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki. Wyrażenia zapytania i fragmentu można pominąć całkowicie. Ścieżka składa się z serii segmentów rozdzielonych znakiem "/", każdy segment może mieć wartość literału, nazwę zmiennej (zapisaną w {nawiasy klamrowe}) lub symbol wieloznaczny (zapisany jako " \* "). W poprzednim szablonie "segment \weather\ jest wartością literału, podczas gdy" {State} "i" {City} "są zmiennymi. Zmienne przyjmują swoją nazwę z zawartości swoich nawiasów klamrowych i później mogą zostać zastąpione konkretną wartością w celu utworzenia *zamkniętego identyfikatora URI*. Symbol wieloznaczny jest opcjonalny, ale może występować tylko na końcu identyfikatora URI, gdzie logicznie pasuje do "reszty ścieżki".  
  
 Wyrażenie zapytania, jeśli istnieje, określa serię nieuporządkowanych par nazwa/wartość, które są ograniczone przez "&". Elementy wyrażenia zapytania mogą być parami literałów (x = 2) lub parę zmiennej (x = {var}). Tylko prawa strona zapytania może mieć wyrażenie zmiennej. ({niektóre} = {wartość someValue} są niedozwolone. Wartości niesparowane (? x) są niedozwolone. Nie ma różnicy między pustym wyrażeniem zapytania i wyrażeniem zapytania składającym się z tylko jednego elementu "?" (oba oznaczają "dowolne zapytanie").  
  
 Wyrażenie fragmentu może składać się z wartości literału, ale nie są dozwolone żadne zmienne.  
  
 Wszystkie nazwy zmiennych szablonu w ciągu szablonu muszą być unikatowe. Nazwy zmiennych szablonów nie uwzględniają wielkości liter.  
  
 Przykłady prawidłowych ciągów szablonu:  
  
- ""  
  
- "/shoe"  
  
- "/Shoe/ \* "  
  
- "{szczęka}/Boat"  
  
- "{szczęka}/{Boat}/Bed/{Quilt}"  
  
- "obuwie/{łodzi}"  
  
- "szczęka/{łodzi}/ \* "  
  
- "obuwie/łódź? x = 2"  
  
- "obuwie/{łodzi}? x = {łóżka}"  
  
- "obuwie/{łodzi}? x = {łóżka} &y = pasmo"  
  
- "? x = {szczęka}"  
  
- "obuwie? x = 3&y = {var}  
  
 Przykłady nieprawidłowych ciągów szablonu:  
  
- "{szczęka}/{SHOE}/x = 2" — zduplikowane nazwy zmiennych.  
  
- "{szczęka}/Boat/? łóżka = {szczęka}" — zduplikowane nazwy zmiennych.  
  
- "? x = 2&x = 3" — pary nazwa/wartość w ciągu zapytania muszą być unikatowe, nawet jeśli są literałami.  
  
- "? x = 2&" — ciąg zapytania jest źle sformułowany.  
  
- "? 2&x = {szczęka}" — ciąg zapytania musi być par nazwa/wartość.  
  
- "? y = 2&&X = 3" — ciąg zapytania musi być parami wartości nazwy, nazwy nie mogą rozpoczynać się od "&".  
  
### <a name="compound-path-segments"></a>Segmenty ścieżki złożonej  
 Segmenty ścieżki złożonej umożliwiają pojedynczemu segmentowi ścieżki URI zawiera wiele zmiennych, a także zmienne połączone z literałami. Poniżej przedstawiono przykłady prawidłowych segmentów ścieżki złożonej.  
  
- /filename. {EXT}/  
  
- /{filename}.jpg/  
  
- /{filename}. {EXT}/  
  
- z. {b} someLiteral {c} ({d})/  
  
 Poniżej przedstawiono przykłady nieprawidłowych segmentów ścieżek.  
  
- {}Zmienne muszą mieć nazwę.  
  
- /{Shoe}{Boat} — zmienne muszą być rozdzielone literałem.  
  
### <a name="matching-and-compound-path-segments"></a>Dopasowywanie i złożone segmenty ścieżki  
 Segmenty ścieżki złożonej umożliwiają zdefiniowanie elementu UriTemplate, który ma wiele zmiennych w obrębie jednego segmentu ścieżki. Na przykład, w następującym ciągu szablonu: "Addresss/{State}. {Miasto} "dwie zmienne (województwo i miejscowość) są zdefiniowane w obrębie tego samego segmentu. Ten szablon będzie pasował do adresu URL, takiego jak, `http://example.com/Washington.Redmond` ale również będzie pasował do adresu URL, takiego jak `http://example.com/Washington.Redmond.Microsoft` . W tym ostatnim przypadku zmienna stanu będzie zawierać wartość "Waszyngton", a zmienna miasto będzie zawierać "Redmond. Microsoft". W takim przypadku dowolny tekst (z wyjątkiem "/") będzie pasował do zmiennej {City}. Jeśli chcesz, aby szablon, który nie był zgodny z tekstem "Extra", umieść zmienną w osobnym segmencie szablonu, na przykład: "Addresss/{State}/{City}.  
  
### <a name="named-wildcard-segments"></a>Nazwane segmenty wieloznaczne  
 Nazwany segment symboli wieloznacznych jest dowolnym segmentem zmiennej PATH, którego nazwa zmiennej zaczyna się od symbolu wieloznacznego " \* ". Następujący ciąg szablonu zawiera nazwany segment wieloznaczny o nazwie "obuwie".  
  
`"literal/{*shoe}"`  
  
 Wieloznaczne segmenty muszą być zgodne z następującymi regułami:  
  
- Dla każdego ciągu szablonu może istnieć co najwyżej jeden nazwany segment wieloznaczny.  
  
- Nazwany segment symboli wieloznacznych musi znajdować się w segmencie znajdującym się w prawym największej ścieżce.  
  
- Nazwany segment wieloznaczny nie może współistnieć z anonimowym segmentem wieloznacznym w tym samym ciągu szablonu.  
  
- Nazwa pojedynczego segmentu wieloznacznego musi być unikatowa.  
  
- Nazwane segmenty wieloznaczne nie mogą mieć wartości domyślnych.  
  
- Nazwane segmenty wieloznaczne nie mogą kończyć się znakiem "/".  
  
### <a name="default-variable-values"></a>Domyślne wartości zmiennych  
 Domyślne wartości zmiennych umożliwiają określanie wartości domyślnych dla zmiennych w ramach szablonu. Zmienne domyślne można określić za pomocą nawiasów klamrowych, które deklarują zmienną lub jako kolekcję przekazaną do konstruktora UriTemplate. Poniższy szablon przedstawia dwa sposoby określania <xref:System.UriTemplate> zmiennych z wartościami domyślnymi.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Ten szablon deklaruje zmienną o nazwie `a` z wartością domyślną `1` i zmienną o nazwie `b` z wartością domyślną `5` .  
  
> [!NOTE]
> Tylko zmienne segmentu ścieżki mogą mieć wartości domyślne. Zmienne ciągu zapytania, zmienne segmentu złożonego i nazwane zmienne symboli wieloznacznych nie mogą mieć wartości domyślnych.  
  
 Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas dopasowywania identyfikatora URI kandydata.  
  
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
> Identyfikator URI, taki jak nie jest `http://localhost:8000///` zgodny z szablonem wymienionym w powyższym kodzie, jednak identyfikator URI, taki jak `http://localhost:8000/` .  
  
 Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas tworzenia identyfikatora URI przy użyciu szablonu.  
  
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
  
Gdy zmienna otrzymuje wartość domyślną, istnieją `null` pewne dodatkowe ograniczenia. Zmienna może mieć wartość domyślną, `null` Jeśli zmienna jest zawarta w prawym najbardziej segmencie ciągu szablonu lub jeśli wszystkie segmenty z prawej strony segmentu mają wartości domyślne `null` . Poniżej podano prawidłowe ciągi szablonów z wartościami domyślnymi `null` :  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Poniżej znajdują się nieprawidłowe ciągi szablonów z wartościami domyślnymi `null` :  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Wartości domyślne i dopasowanie  
 W przypadku dopasowania identyfikatora URI kandydata z szablonem, który ma wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli wartości nie są określone w identyfikatorze URI kandydata.  
  
### <a name="template-equivalence"></a>Równoważność szablonu  
 Dwa szablony są uważane za *strukturalnie równoważne* , gdy wszystkie literały szablonów pasują do siebie i mają zmienne w tych samych segmentach. Na przykład następujące szablony są strukturalnie równoważne:  
  
- /a/{var1}/b b/{var2}? x = 1&y = 2  
  
- a/{x}/b% 20b/{var1}? y = 2&x = 1  
  
- a/{y}/B% 20B/{z}/? y = 2&x = 1  
  
 Kilka kwestii, które należy zauważyć:  
  
- Jeśli szablon zawiera wiodące ukośniki, tylko pierwszy z nich jest ignorowany.  
  
- Podczas porównywania ciągów szablonów dla równoważności strukturalnej, wielkość liter jest ignorowana w przypadku nazw zmiennych i segmentów ścieżki, w których ciągi zapytań są rozróżniane wielkości liter.  
  
- Ciągi zapytań są nieuporządkowane.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable>Klasa reprezentuje tabelę asocjacyjną <xref:System.UriTemplate> obiektów powiązaną z obiektem wyboru dewelopera. A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> . Zawartość elementu <xref:System.UriTemplateTable> można zmienić do momentu <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> wywołania. Walidacja jest wykonywana, gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana. Typ wykonywanej walidacji zależy od wartości `allowMultiple` parametru do <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana `false` , <xref:System.UriTemplateTable> sprawdza, czy nie ma żadnych szablonów w tabeli. W przypadku znalezienia wszelkich odpowiedników strukturalnych szablony zgłasza wyjątek. Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> , gdy chcesz zapewnić, że tylko jeden szablon pasuje do przychodzącego identyfikatora URI.  
  
 Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest nazywana przekazywaniem `true` , <xref:System.UriTemplateTable> umożliwia korzystanie z wielu szablonów równoważnych, które mają być zawarte w <xref:System.UriTemplateTable> .  
  
 Jeśli zestaw <xref:System.UriTemplate> obiektów dodanych do <xref:System.UriTemplateTable> zawiera ciągi zapytania, nie mogą być niejednoznaczne. Identyczne ciągi zapytań są dozwolone.  
  
> [!NOTE]
> Chociaż <xref:System.UriTemplateTable> zezwala na adresy podstawowe wykorzystujące schematy inne niż http, schemat i numer portu są ignorowane podczas dopasowywania identyfikatorów URI kandydujących do szablonów.  
  
### <a name="query-string-ambiguity"></a>Niejednoznaczność ciągu zapytania  
 Szablony, które współdzielą równoważną ścieżkę, zawierają niejednoznaczne ciągi zapytań, jeśli istnieje identyfikator URI, który odpowiada więcej niż jednemu szablonowi.  
  
 Następujące zestawy ciągów zapytań są niejednoznaczne w samym sobie:  
  
- ? x = 1  
  
- ? x = 2  
  
- ? x = 3  
  
- ? x = 1&y = {var}  
  
- ? x = 2&z = {var}  
  
- ? x = 3  
  
- ? x = 1  
  
- ?  
  
- ? x = {var}  
  
- ?  
  
- ? m = Pobierz&c = RSS  
  
- ? m = Put&c = RSS  
  
- ? m = Pobierz&c = Atom  
  
- ? m = Put&c = Atom  
  
 Następujące zestawy szablonów ciągu zapytania są niejednoznaczne w obrębie siebie:  
  
- ? x = 1  
  
- ? x = {var}  
  
 "x = 1" — dopasowuje oba szablony.  
  
- ? x = 1  
  
- ? y = 2  
  
 "x = 1&y = 2" pasuje do obu szablonów. Wynika to z faktu, że ciąg zapytania może zawierać więcej zmiennych ciągu zapytania, a następnie szablon, który jest zgodny.  
  
- ? x = 1  
  
- ? x = 1&y = {var}  
  
 "x = 1&y = 3" dopasowuje oba szablony.  
  
- ? x = 3&y = 4  
  
- ? x = 3&z = 5  
  
> [!NOTE]
> Znaki i i. są uważane za różne znaki, gdy są wyświetlane jako część ścieżki URI lub <xref:System.UriTemplate> literału segmentu ścieżki (ale znaki a i a są uważane za takie same). Znaki i, są uznawane za te same znaki, gdy pojawiają się jako część <xref:System.UriTemplate> {VariableName} lub ciągu zapytania (a i a są również uznawane za te same znaki).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](wcf-web-http-programming-model-overview.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-object-model.md)
- [UriTemplate](../samples/uritemplate-sample.md)
- [Tabela UriTemplate](../samples/uritemplate-table-sample.md)
- [Dyspozytor tabeli UriTemplate](../samples/uritemplate-table-dispatcher-sample.md)
