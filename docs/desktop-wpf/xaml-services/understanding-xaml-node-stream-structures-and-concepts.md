---
title: Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: b3de3dca029c5e676fc7cdebc7735cfdade0228a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071620"
---
# <a name="xaml-node-stream-structures-and-concepts"></a>Struktury i koncepcje strumienia węzłów XAML

Czytniki XAML i moduły zapisu XAML zaimplementowane w usługach .NET XAML są oparte na koncepcji projektowej strumienia węzła XAML. Strumień węzłów XAML jest konceptualizacji zestawu węzłów XAML. W tej konceptualizacji procesor XAML przechodzi przez strukturę relacji węzłów w XAML po jednym na raz. W dowolnym momencie tylko jeden bieżący rekord lub bieżąca pozycja istnieje w otwartym strumieniu węzła XAML, a wiele aspektów interfejsu API raportuje tylko informacje dostępne z tej pozycji. Bieżący węzeł w strumieniu węzła XAML można opisać jako obiekt, element członkowski lub wartość. Traktując XAML jako strumień węzła XAML, czytniki XAML mogą komunikować się ze modułami zapisującymi XAML i umożliwiać programowi wyświetlanie, interakcję z nim lub zmienianie zawartości strumienia węzła XAML podczas ścieżki ładowania lub operacji zapisywania ścieżki obejmującej XAML. Projekt interfejsu API czytnika i modułu zapisującego XAML oraz koncepcja strumienia węzła XAML są podobne do poprzednich <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> powiązanych projektów i koncepcji czytnika i modułu zapisującego, takich jak model obiektu dokumentu XML (DOM) oraz klasy i. W tym temacie omówiono pojęcia strumienia węzłów XAML i opisano, jak można pisać procedury, które współdziałają z reprezentacjami XAML na poziomie węzła XAML.

## <a name="loading-xaml-into-a-xaml-reader"></a>Ładowanie xaml do czytnika XAML

Klasa <xref:System.Xaml.XamlReader> podstawowa nie deklaruje określonej techniki ładowania początkowego XAML do czytnika XAML. Zamiast tego klasa pochodna deklaruje i implementuje technikę ładowania, w tym ogólne cechy i ograniczenia jego źródła wejściowego dla XAML. Na przykład <xref:System.Xaml.XamlObjectReader> odczytuje wykres obiektu, zaczynając od źródła wejściowego pojedynczego obiektu, który reprezentuje katalog główny lub bazowy. Następnie <xref:System.Xaml.XamlObjectReader> tworzy strumień węzła XAML z wykresu obiektu.

Najbardziej widoczna podklasa .NET XAML Services jest . <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlXmlReader> <xref:System.Xaml.XamlXmlReader>ładuje początkowy kod XAML, ładując plik tekstowy bezpośrednio za pośrednictwem strumienia lub ścieżki pliku, lub pośrednio za pośrednictwem powiązanej klasy czytnika, takiej jak <xref:System.IO.TextReader>. Można <xref:System.Xaml.XamlReader> uznać, że zawiera całość źródła danych wejściowych XAML po załadowaniu. Jednak <xref:System.Xaml.XamlReader> podstawowy interfejs API jest zaprojektowany tak, że czytnik wchodzi w interakcję z jednym węzłem XAML. Po pierwszym załadowaniu pierwszy pojedynczy węzeł, który napotkasz, jest katalogiem głównym XAML i jego obiektem początkowym.

### <a name="the-xaml-node-stream-concept"></a>Koncepcja strumienia węzłów XAML

Jeśli jesteś bardziej zaznajomiony z DOM, metafory drzewa lub zapytania oparte podejście do uzyskiwania dostępu do technologii opartych na XML, pomocny sposób koncepcji strumienia węzła XAML jest w następujący sposób. Wyobraź sobie, że załadowany kod XAML jest dom lub drzewa, gdzie każdy możliwy węzeł jest rozwijany do końca, a następnie prezentowane liniowo. W miarę przechodzenia przez węzły, może być przechodzenie "w" lub "out" poziomów, które byłyby istotne dla DOM, ale strumień węzła XAML nie jawnie śledzić, ponieważ te pojęcia poziomu nie są istotne dla strumienia węzła. Strumień węzła ma "bieżącą" pozycję, ale jeśli nie zostały zapisane inne części strumienia samodzielnie jako odwołania, każdy aspekt strumienia węzła innych niż bieżąca pozycja węzła jest poza widoku.

Koncepcja strumienia węzła XAML ma znaczącą zaletę, że jeśli przejdziesz przez cały strumień węzła, masz pewność, że przetworzyłeś całą reprezentację XAML; nie musisz się martwić, że kwerenda, operacja DOM lub inne nieliniowe podejście do przetwarzania informacji nie odebrano części pełnej reprezentacji XAML. Z tego powodu reprezentacja strumienia węzła XAML jest idealna zarówno do łączenia czytników XAML i modułów zapisu XAML, jak i do zapewnienia systemu, w którym można wstawić własny proces, który działa między fazami odczytu i zapisu operacji przetwarzania XAML. W wielu przypadkach kolejność węzłów w strumieniu węzła XAML jest celowo optymalizowane lub uporządkowane przez czytniki XAML w porównaniu z kolejnością, która może pojawić się na wykresie tekstu źródłowego, binarnego lub obiektu. To zachowanie jest przeznaczone do wymuszania architektury przetwarzania XAML, zgodnie z którą moduły zapisające XAML nigdy nie znajdują się w sytuacji, w której muszą wrócić "wstecz" w strumieniu węzła. W idealnym przypadku wszystkie operacje zapisu XAML powinny być w stanie działać na podstawie kontekstu schematu oraz bieżącej pozycji strumienia węzła.

## <a name="a-basic-reading-node-loop"></a>Podstawowa pętla węzła odczytu

Podstawowa pętla węzła odczytu do badania strumienia węzła XAML składa się z następujących pojęć. Na potrzeby pętli węzłów, jak omówiono w tym temacie, załóżmy, że czytasz tekstowy, czytelny dla człowieka plik XAML przy użyciu <xref:System.Xaml.XamlXmlReader>. Łącza w tej sekcji odnoszą się do interfejsu API <xref:System.Xaml.XamlXmlReader>pętli węzłów XAML zaimplementowanych przez program .

- Upewnij się, że nie znajdujesz się na końcu <xref:System.Xaml.XamlXmlReader.IsEof%2A>strumienia węzła XAML (sprawdź lub użyj zwracanej <xref:System.Xaml.XamlXmlReader.Read%2A> wartości). Jeśli jesteś na końcu strumienia, nie ma bieżącego węzła i należy zakończyć.

- Sprawdź, jaki typ węzła strumień węzła XAML jest obecnie udostępniany przez wywołanie <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Jeśli masz skojarzony moduł zapisujący obiekt XAML, który <xref:System.Xaml.XamlWriter.WriteNode%2A> jest połączony bezpośrednio, zazwyczaj wywołane w tym momencie.

- Na podstawie <xref:System.Xaml.XamlNodeType> których jest zgłaszane jako bieżący węzeł lub bieżący rekord, wywołać jedną z następujących czynności, aby uzyskać informacje o zawartości węzła:

  - W <xref:System.Xaml.XamlXmlReader.NodeType%2A> przypadku <xref:System.Xaml.XamlNodeType.StartMember> <xref:System.Xaml.XamlNodeType.EndMember>połączenia <xref:System.Xaml.XamlXmlReader.Member%2A> telefonicznego <xref:System.Xaml.XamlMember> lub telefonicznego w celu uzyskania informacji o człowianym. Element członkowski <xref:System.Xaml.XamlDirective>może być elementem członkowskim , a zatem niekoniecznie musi być konwencjonalnym elementem członkowskim zdefiniowanym przez typ poprzedniego obiektu. Na przykład `x:Name` stosowane do obiektu pojawia się jako <xref:System.Xaml.XamlMember.IsDirective%2A> element członkowski <xref:System.Xaml.XamlMember.Name%2A> XAML, gdzie jest true i element członkowski jest `Name`, z innymi właściwościami wskazującymi, że ta dyrektywa znajduje się w języku XAML przestrzeni nazw XAML języka.

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> lub <xref:System.Xaml.XamlNodeType.StartObject> <xref:System.Xaml.XamlNodeType.EndObject>, <xref:System.Xaml.XamlXmlReader.Type%2A> wywołać, aby uzyskać <xref:System.Xaml.XamlType> informacje o obiekcie.

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> a <xref:System.Xaml.XamlNodeType.Value>, <xref:System.Xaml.XamlXmlReader.Value%2A>zadzwoń . Węzeł jest wartością tylko wtedy, gdy jest najprostszym wyrażeniem wartości dla elementu członkowskiego lub tekstem inicjowania obiektu (jednak należy pamiętać o zachowaniu konwersji typu, jak zostało to udokumentowane w nadchodzącej sekcji tego tematu).

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>wywołać, <xref:System.Xaml.XamlXmlReader.Namespace%2A> aby uzyskać informacje o obszarze nazw dla węzła obszaru nazw.

- Wywołanie, <xref:System.Xaml.XamlXmlReader.Read%2A> aby przejść czytnik XAML do następnego węzła w strumieniu węzła XAML i powtórzyć kroki ponownie.

Strumień węzła XAML dostarczany przez czytniki XAML usług .NET XAML zawsze zapewnia pełny, głęboki przechodzenie wszystkich możliwych węzłów. Typowe techniki kontroli przepływu dla pętli węzła XAML `while (reader.Read())`obejmują definiowanie <xref:System.Xaml.XamlXmlReader.NodeType%2A> obiektu w obrębie i włączanie w każdym punkcie węzła w pętli węzła.

Jeśli strumień węzła znajduje się na końcu pliku, bieżący węzeł ma wartość null.

Najprostsza pętla, która używa czytnika i modułu zapisującego przypomina poniższy przykład.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Ten podstawowy przykład pętli węzła XAML ścieżki obciążenia w sposób przejrzysty łączy czytnik XAML i <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>moduł zapisujący XAML, nie robiąc nic innego niż w przypadku użycia . Ale ta podstawowa struktura jest następnie rozszerzana, aby zastosować do scenariusza czytania lub pisania. Niektóre możliwe scenariusze są następujące:

- Włącz <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Wykonaj różne akcje w zależności od tego, który typ węzła jest odczytywany.

- Nie dzwonić <xref:System.Xaml.XamlWriter.WriteNode%2A> we wszystkich przypadkach. Tylko <xref:System.Xaml.XamlWriter.WriteNode%2A> w <xref:System.Xaml.XamlXmlReader.NodeType%2A> niektórych przypadkach.

- W ramach logiki dla określonego typu węzła przeanalizuj specyfikę tego węzła i działaj na nich. Na przykład można zapisywać tylko obiekty pochodzące z określonego obszaru nazw XAML, a następnie upuszczać lub odraczać wszystkie obiekty, które nie pochodzą z tego obszaru nazw XAML. Można też upuścić lub w inny sposób ponownie przetworzyć wszelkie dyrektywy XAML, które system XAML nie obsługuje w ramach przetwarzania elementu członkowskiego.

- Zdefiniuj niestandardowe, <xref:System.Xaml.XamlObjectWriter> które zastępuje `Write*` metody, ewentualnie wykonywanie mapowania typów, który pomija kontekst schematu XAML.

- Konstruuj <xref:System.Xaml.XamlXmlReader> do użycia kontekstu schematu XAML nondefault, tak aby dostosowane różnice w zachowaniu XAML są używane zarówno przez czytelnika, jak i moduł zapisujący.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Uzyskiwanie dostępu do xaml poza koncepcją pętli węzła

Istnieją potencjalnie inne sposoby pracy z reprezentacją XAML inne niż jako pętla węzła XAML. Na przykład może istnieć czytnik XAML, który może odczytywać indeksowany węzeł `x:Name`lub `x:Uid`w szczególności uzyskuje dostęp do węzłów bezpośrednio przez , przez , lub za pośrednictwem innych identyfikatorów. Usługi .NET XAML nie zapewniają pełną implementację, ale zapewnia sugerowany wzorzec za pośrednictwem usług i typów pomocy technicznej. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IXamlIndexingReader> i <xref:System.Xaml.XamlNodeList>.

## <a name="working-with-the-current-node"></a>Praca z bieżącym węzłem

Większość scenariuszy, które używają pętli węzła XAML nie tylko odczytywać węzły. Większość scenariuszy przetwarza bieżące węzły i przekazuje każdy <xref:System.Xaml.XamlWriter>węzeł po jednym naraz do implementacji programu .

W typowym scenariuszu <xref:System.Xaml.XamlXmlReader> ścieżki obciążenia tworzy strumień węzła XAML; węzły XAML są przetwarzane zgodnie z logiką i kontekstem schematu XAML; a węzły są przekazywane <xref:System.Xaml.XamlObjectWriter>do pliku . Następnie należy zintegrować wykres wynikowy obiektu do aplikacji lub struktury.

W typowym scenariuszu <xref:System.Xaml.XamlObjectReader> zapisz ścieżki odczytuje wykres obiektu, przetwarzane są poszczególne <xref:System.Xaml.XamlXmlWriter> węzły XAML, a wynik wyprowadza serializowany wynik jako plik tekstowy XAML. Kluczem jest to, że zarówno ścieżki, jak i scenariusze obejmują pracę z dokładnie jednym węzłem XAML naraz, a węzły XAML są dostępne do leczenia w znormalizowany sposób zdefiniowany przez system typu XAML i the.NET interfejsów API usług XAML.

### <a name="frames-and-scope"></a>Ramki i zakres

Pętla węzła XAML przechodzi przez strumień węzła XAML w sposób liniowy. Strumień węzła przechodzi do obiektów, do elementów członkowskich, które zawierają inne obiekty i tak dalej. Często jest przydatne do śledzenia zakresu w strumieniu węzła XAML przez implementowanie koncepcji ramki i stosu. Jest to szczególnie ważne, jeśli aktywnie dostosowujesz strumień węzła, gdy jesteś w nim. Obsługa ramki i stosu, które można zaimplementować jako część logiki pętli węzła może liczyć `StartObject` (lub) `GetObject`i `EndObject` zakresy, jak zejść do struktury węzła XAML, jeśli struktura jest przemyślana z perspektywy DOM.

## <a name="traversing-and-entering-object-nodes"></a>Przechodzenie przez węzły obiektów i wprowadzanie ich

Pierwszy węzeł w strumieniu węzła, gdy jest otwierany przez czytnik XAML, jest węzłem-obiektem startowym obiektu głównego. Z definicji ten obiekt jest zawsze węzeł pojedynczego obiektu i nie ma żadnych rysów. W każdym przykładzie XAML w świecie rzeczywistym obiekt główny jest zdefiniowany jako zawierający jedną lub więcej właściwości, które przechowują więcej obiektów, a te właściwości mają węzły członkowskie. Węzły członkowskie mają następnie jeden lub więcej węzłów obiektu lub może również zakończyć się w węźle wartości zamiast. Obiekt główny zazwyczaj definiuje identyfikatory nazw XAML, które są syntaktycznie przypisywane jako atrybuty w `Namescope` znacznikach tekstowych XAML, ale mapowane na typ węzła w reprezentacji strumienia węzła XAML.

Rozważmy poniższy przykład XAML (jest to dowolny kod XAML, który nie jest wspierany przez istniejące typy w .NET). Załóżmy, że `FavorCollection` w `List<T>` `Favor`tym `Balloon` `NoiseMaker` modelu obiektu, `Favor`jest `Balloon.Color` , i `Color` są przypisane do , właściwość jest wspierany `Color` przez obiekt podobny do sposobu WPF definiuje kolory jako znane nazwy kolorów i obsługuje konwerter typów dla składni atrybutów.

|Znaczniki XAML|Wynikowy strumień węzła XAML|
|-----------------|--------------------------------|
|`<Party`|`Namespace`węzeł dla`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`węzeł dla`Party`|
|`<Party.Favors>`|`StartMember`węzeł dla`Party.Favors`|
||`StartObject`węzeł dla niejawnych`FavorCollection`|
||`StartMember`dla właściwości `FavorCollection` niejawne elementy.|
|`<Balloon`|`StartObject`węzeł dla`Balloon`|
|`Color="Red"`|`StartMember`węzeł dla`Color`<br /><br /> `Value`węzeł dla ciągu wartości atrybutu`"Red"`<br /><br /> `EndMember`For`Color`|
|`HasHelium="True"`|`StartMember`węzeł dla`HasHelium`<br /><br /> `Value`węzeł dla ciągu wartości atrybutu`"True"`<br /><br /> `EndMember`For`HasHelium`|
|`>`|`EndObject`For`Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`węzeł dla`NoiseMaker`<br /><br /> `StartMember`węzeł dla`_Initialization`<br /><br /> `Value`węzeł dla ciągu wartości inicjowania`"Loudest"`<br /><br /> `EndMember`węzeł dla`_Initialization`<br /><br /> `EndObject`For`NoiseMaker`|
||`EndMember`dla właściwości `FavorCollection` niejawne elementy.|
||`EndObject`węzeł dla niejawnych`FavorCollection`|
|`</Party.Favors>`|`EndMember`For`Favors`|
|`</Party>`|`EndObject`For`Party`|

W strumieniu węzła XAML można polegać na następującym zachowaniu:

- Jeśli `Namespace` węzeł istnieje, jest dodawany do strumienia bezpośrednio przed `StartObject` zadeklarowanym `xmlns`obszarem nazw XAML z programem . Spójrz na poprzednią tabelę z XAML i przykładowy strumień węzła ponownie. Zwróć `StartObject` uwagę, `Namespace` jak i węzły wydają się być transponowane w porównaniu do ich pozycji deklaracji w znacznikach tekstu. Jest to reprezentatywne dla zachowania, w którym węzły obszaru nazw zawsze pojawiają się przed węzłem, do którego mają zastosowanie w strumieniu węzła. Celem tego projektu jest to, że informacje o przestrzeni nazw są niezbędne do modułu zapisującego obiekt i muszą być znane, zanim moduł zapisujący obiekt podejmie próbę wykonania mapowania typów lub innego przetworzenia obiektu. Umieszczenie informacji o przestrzeni nazw XAML przed jego zakres aplikacji w strumieniu ułatwia zawsze przetwarzać strumień węzła w jego przedstawionej kolejności.

- Ze względu na powyższe uwagę `Namespace` jest to jeden lub więcej węzłów, które można przeczytać najpierw w większości `StartObject` rzeczywistych przypadków znaczników podczas przechodzenia przez węzły od początku, a nie katalogu głównego.

- Po `StartObject` węźle `StartMember`może `Value`nastąpić `EndObject`, lub natychmiastowy . Nigdy nie następuje `StartObject`od razu inny .

- A `StartMember` może nastąpić `StartObject` `Value`, lub `EndMember`natychmiastowe . Może następować `GetObject`po , dla elementów członkowskich, gdzie wartość ma pochodzić `StartObject` z istniejącej wartości obiektu nadrzędnego, a nie, który będzie utworzyć wystąpienie nowej wartości. Po nim może również `Namespace` znajdować się węzeł, `StartObject`który ma zastosowanie do nadchodzącego . Nigdy nie następuje `StartMember`od razu inny .

- Węzeł `Value` reprezentuje samą wartość; nie ma "EndValue". Po nim może następować tylko plik `EndMember`.

  - Tekst inicjowania XAML obiektu, który może być użyty przez konstrukcję, nie powoduje, że struktura Object-Value. Zamiast tego tworzony jest węzeł dedykowanego elementu członkowskiego dla nazwanego `_Initialization` elementu członkowskiego. i ten węzeł elementu członkowskiego zawiera ciąg wartości inicjowania. Jeśli istnieje, `_Initialization` jest zawsze `StartMember`pierwszym . `_Initialization`mogą być kwalifikowane w niektórych reprezentacji usług XAML z języka XAML namescope języka, aby wyjaśnić, że `_Initialization` nie jest zdefiniowaną właściwością w typach kopii zapasowych.

  - Kombinacja Wartość elementu członkowskiego reprezentuje ustawienie atrybutu wartości. Ostatecznie może istnieć konwerter wartości zaangażowany w przetwarzanie tej wartości, a wartość jest zwykłym ciągiem. Jednak to nie jest oceniane, dopóki moduł zapisujący obiekt XAML przetwarza ten strumień węzła. Moduł zapisujący obiekt XAML posiada niezbędny kontekst schematu XAML, mapowanie systemu typu i inne wsparcie potrzebne do konwersji wartości.

- Węzeł `EndMember` może następować `StartMember` węzeł dla następnego elementu `EndObject` członkowskiego lub węzeł dla właściciela elementu członkowskiego.

- Węzeł `EndObject` może następować `EndMember` po węźle. Może również następować `StartObject` węzeł dla przypadków, gdy obiekty są równorzędne w elementach kolekcji. Lub może być po `Namespace` węźle, który `StartObject`ma zastosowanie do nadchodzącego .

  - W przypadku unikatowego zamknięcia całego strumienia `EndObject` węzła, po katalogu głównym nie następuje nic; czytnik jest teraz koniec pliku i <xref:System.Xaml.XamlReader.Read%2A> `false`zwraca .

## <a name="value-converters-and-the-xaml-node-stream"></a>Konwertery wartości i strumień węzłów XAML

Konwerter wartości jest ogólnym terminem dla rozszerzenia znaczników, konwertera typów (w tym serializatorów wartości) lub innej dedykowanej klasy, która jest raportowana jako konwerter wartości za pośrednictwem systemu typu XAML. W strumieniu węzła XAML użycie konwertera typu i użycie rozszerzenia znaczników mają bardzo różne reprezentacje.

### <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typów w strumieniu węzłów XAML

Zestaw atrybutów, który ostatecznie powoduje użycie konwertera typu jest zgłaszany w strumieniu węzła XAML jako wartość elementu członkowskiego. Strumień węzła XAML nie próbuje utworzyć obiektu wystąpienia konwertera typu i przekazać wartość do niego. Przy użyciu implementacji konwersji konwertera typów wymaga wywoływania kontekstu schematu XAML i używania go do mapowania typu. Nawet określenie, który typ klasy konwertera powinny być używane do przetwarzania wartości wymaga kontekstu schematu XAML pośrednio. W przypadku korzystania z domyślnego kontekstu schematu XAML te informacje są dostępne w systemie typu XAML. Jeśli potrzebujesz informacji o klasie konwertera typu na poziomie strumienia węzła XAML przed <xref:System.Xaml.XamlMember> nawiązaniem połączenia z modułem zapisu XAML, możesz uzyskać je na podstawie informacji o ustawionym członu. Jednak w przeciwnym razie dane wejściowe konwertera typu powinny być zachowywane w strumieniu węzła XAML jako wartość zwykła, dopóki nie zostaną wykonane pozostałe operacje wymagające systemu mapowania typów i kontekstu schematu XAML, na przykład tworzenie obiektu przez moduł zapisujący obiekt XAML.

Rozważmy na przykład następujący konspekt definicji klasy i użycie XAML dla niego:

```csharp
public class BoardSizeConverter : TypeConverter {
  //converts from string to an int[2] by splitting on an "x" char
}
public class GameBoard {
  [TypeConverter(typeof(BoardSizeConverter))]
  public int[] BoardSize; //2x2 array, initialization not shown
}
```

```xaml
<GameBoard BoardSize="8x8"/>
```

Tekstowa reprezentacja strumienia węzła XAML dla tego użycia może być wyrażona w następujący sposób:

`StartObject`z <xref:System.Xaml.XamlType> reprezentowaniem`GameBoard`

`StartMember`z <xref:System.Xaml.XamlMember> reprezentowaniem`BoardSize`

`Value`węzeł, z ciągiem tekstowym "`8x8`"

`EndMember`Pasuje`BoardSize`

`EndObject`Pasuje`GameBoard`

Należy zauważyć, że nie ma wystąpienia konwertera typu w tym strumieniu węzła. Ale można uzyskać informacje konwerter typu, dzwoniąc <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> for `BoardSize`. Jeśli masz prawidłowy kontekst schematu XAML, możesz również wywołać metody konwertera, uzyskując wystąpienie z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>programu .

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w strumieniu węzłów XAML

Użycie rozszerzenia znaczników jest zgłaszane w strumieniu węzła XAML jako węzeł obiektu w obrębie elementu członkowskiego, gdzie obiekt reprezentuje wystąpienie rozszerzenia znaczników. W związku z tym użycie rozszerzenia znaczników jest przedstawiony bardziej jawnie w reprezentacji strumienia węzła niż użycie konwertera typu jest i przenosi więcej informacji. <xref:System.Xaml.XamlMember>informacje nie mogły powiedzieć ci nic o rozszerzeniu znaczników, ponieważ użycie ma miejsce sytuacyjne i różni się w każdym możliwym przypadku znaczników; nie jest dedykowany i niejawny dla każdego typu lub elementu członkowskiego, jak w przypadku konwerterów typów.

Reprezentacja strumienia węzłów rozszerzeń znaczników jako węzłów obiektów ma miejsce, nawet jeśli użycie rozszerzenia znaczników zostało dokonane w formularzu atrybutu w znacznikach tekstowych XAML (co często ma miejsce). Rozszerzenia znaczników, które używały jawnego formularza elementu obiektu, są traktowane w ten sam sposób.

W węźle obiektu rozszerzenia znaczników mogą istnieć elementy członkowskie tego rozszerzenia znaczników. Reprezentacja strumienia węzła XAML zachowuje użycie tego rozszerzenia znaczników, niezależnie od tego, czy jest to użycie parametru pozycyjnego, czy użycie z jawnymi nazwanymi parametrami.

W przypadku użycia parametru pozycyjnego strumień węzła XAML `_PositionalParameters` zawiera właściwość zdefiniowaną przez język XAML, która rejestruje użycie. Ta właściwość <xref:System.Collections.Generic.List%601> jest <xref:System.Object> rodzajowy z ograniczeniem. Ograniczenie jest obiektem, a nie ciągiem, ponieważ niewykluczone użycie parametru pozycyjnego może zawierać zagnieżdżone użycie rozszerzenia znaczników w nim. Aby uzyskać dostęp do parametrów pozycyjnych z użycia, można iterować za pośrednictwem listy i używać indeksatorów dla poszczególnych wartości listy.

Dla użycia nazwanego parametru każdy nazwany parametr jest reprezentowany jako węzeł członkowski o tej nazwie w strumieniu węzła. Wartości członkowskie nie są koniecznie ciągi, ponieważ może istnieć użycie rozszerzenia znaczników zagnieżdżonych.

`ProvideValue`z rozszerzenia znaczników nie jest jeszcze wywoływana. Jednak jest wywoływana, jeśli połączysz czytnik XAML i `WriteEndObject` moduł zapisujący XAML, tak aby jest wywoływany w węźle rozszerzenia znaczników podczas badania go w strumieniu węzła. Z tego powodu zazwyczaj potrzebujesz tego samego kontekstu schematu XAML dostępne, jak byłoby używane w celu utworzenia wykresu obiektu na ścieżce ładowania. W `ProvideValue` przeciwnym razie z dowolnego rozszerzenia znaczników można zgłaszać wyjątki w tym miejscu, ponieważ nie ma oczekiwanych usług dostępnych.

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Elementy członkowskie xaml i xml zdefiniowane w strumieniu węzłów XAML

Niektóre elementy członkowskie są wprowadzane do strumienia węzła XAML z powodu interpretacji i <xref:System.Xaml.XamlMember> konwencji czytnika XAML, a nie za pośrednictwem jawnego wyszukiwania lub konstrukcji. Często te elementy członkowskie są dyrektywy XAML. W niektórych przypadkach jest to czynność odczytu XAML, który wprowadza dyrektywę do strumienia węzła XAML. Innymi słowy oryginalny wpisowy tekst XAML nie jawnie określić dyrektywy elementu członkowskiego, ale czytnik XAML wstawia dyrektywy w celu spełnienia strukturalnych konwencji XAML i raport informacji w strumieniu węzła XAML przed utratą tych informacji.

Na poniższej liście zwraca uwagę na wszystkie przypadki, w których oczekuje się, że czytnik XAML wprowadzi węzeł elementu członkowskiego XAML dyrektywy i jak ten węzeł elementu członkowskiego jest identyfikowany w implementacjach usług .NET XAML Services.

- **Tekst inicjowania węzła obiektu:** Nazwa tego węzła `_Initialization`członkowskiego jest , reprezentuje dyrektywę XAML i jest zdefiniowana w przestrzeni nazw XAML języka XAML języka. Można uzyskać jednostkę statyczną <xref:System.Xaml.XamlLanguage.Initialization%2A>dla niego z .

- **Parametry pozycyjne dla rozszerzenia znaczników:** Nazwa tego węzła `_PositionalParameters`członkowskiego jest i jest zdefiniowana w przestrzeni nazw XAML języka XAML języka. Zawsze zawiera ogólną listę obiektów, z których każdy jest parametrem pozycyjnym wstępnie oddzielone przez podział na znak `,` ogranicznika, jak podano w wejściowym XAML. Można uzyskać jednostkę statyczną dla dyrektywy <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>parametrów pozycyjnych z .

- **Nieznana zawartość:** Nazwa tego węzła `_UnknownContent`członkowskiego to . Ściśle rzecz biorąc, <xref:System.Xaml.XamlDirective>jest to , i jest zdefiniowany w języku XAML przestrzeni nazw XAML. Ta dyrektywa jest używana jako wartownika w przypadkach, gdy element obiektu XAML zawiera zawartość w źródłowym XAML, ale nie można określić właściwości zawartości w aktualnie dostępnym kontekście schematu XAML. Ten przypadek można wykryć w strumieniu węzła `_UnknownContent`XAML, sprawdzając, czy nie ma członków o nazwie . Jeśli żadna inna akcja nie zostanie podjęta w <xref:System.Xaml.XamlObjectWriter> strumieniu węzła `WriteEndObject` XAML `_UnknownContent` ścieżki obciążenia, domyślna próba jest podejmowana, gdy napotka element członkowski na dowolnym obiekcie. Domyślny <xref:System.Xaml.XamlXmlWriter> nie zgłasza i traktuje element członkowski jako niejawny. Można uzyskać jednostkę statyczną dla `_UnknownContent` z . <xref:System.Xaml.XamlLanguage.UnknownContent%2A>

- **Właściwość kolekcji:** Mimo że zapasowy typ CLR klasy kolekcji, który jest używany dla XAML zwykle ma dedykowaną właściwość o nazwie, która przechowuje elementy kolekcji, ta właściwość nie jest znana systemowi typu XAML przed rozdzielczością typu kopii zapasowej. Zamiast tego strumień węzła XAML `Items` wprowadza symbol zastępczy jako element członkowski typu XAML kolekcji. W implementacji usług .NET XAML nazwa tej dyrektywy lub `_Items`elementu członkowskiego w strumieniu węzła jest . Stała dla tej dyrektywy może <xref:System.Xaml.XamlLanguage.Items%2A>być uzyskana z .

    Należy zauważyć, że strumień węzła XAML może zawierać Items właściwości z elementów, które okazują się nie być parsable na podstawie rozdzielczości typu kopii zapasowej i kontekstu schematu XAML. Na przykład:

- **Elementy członkowskie zdefiniowane w języku XML:** Zdefiniowane `xml:base`przez XML elementy `xml:lang` członkowskie `xml:space` są zgłaszane jako `base` `lang`dyrektywy `space` XAML o nazwie , a także w implementacjach usług .NET XAML Services. Obszar nazw dla nich jest obszar `http://www.w3.org/XML/1998/namespace`nazw XML . Stałe dla każdego z nich <xref:System.Xaml.XamlLanguage>można uzyskać od .

## <a name="node-order"></a>Kolejność węzłów

W niektórych <xref:System.Xaml.XamlXmlReader> przypadkach zmienia kolejność węzłów XAML w strumieniu węzłów XAML w porównaniu z kolejnością, w jaką węzły są wyświetlane, jeśli są wyświetlane w znacznikach lub są przetwarzane jako XML. Odbywa się to w celu zamówienia węzłów, takie, że można <xref:System.Xaml.XamlObjectWriter> przetwarzać strumień węzła w sposób tylko do przodu.  W usługach XAML .NET czytnik XAML zmienia kolejność węzłów, zamiast pozostawiać to zadanie modułowi zapisującego XAML jako optymalizację wydajności dla konsumentów modułu zapisującego obiekt XAML strumienia węzła.

Niektóre dyrektywy są przeznaczone specjalnie do zapewnienia więcej informacji do tworzenia obiektu z elementu obiektu. Dyrektywy te są `Initialization` `PositionalParameters`następujące: `FactoryMethod` `Arguments`, , `TypeArguments`, . Czytniki XAML usług .NET XAML próbują umieścić te dyrektywy jako pierwsze elementy `StartObject`członkowskie w strumieniu węzłów po obiekcie , z przyczyn, które są wyjaśnione w następnej sekcji.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Zachowanie XamlObjectWriter i kolejność węzłów

`StartObject`do <xref:System.Xaml.XamlObjectWriter> a nie musi być sygnał do modułu zapisującego obiekt XAML do natychmiastowego konstruowania wystąpienia obiektu. XAML zawiera kilka funkcji języka, które umożliwiają zainicjowanie obiektu z dodatkowymi danymi wejściowymi i nie polegać wyłącznie na wywoływaniu konstruktora bez parametrów do tworzenia obiektu początkowego, a dopiero potem ustawienie właściwości. Funkcje te <xref:System.Windows.Markup.XamlDeferLoadAttribute>obejmują: ; tekst inicjowania; [x:TypArguments](xtypearguments-directive.md); parametry pozycyjne rozszerzenia znaczników; metody fabryczne i skojarzone [x:Arguments](xarguments-directive.md) nodes (XAML 2009). Każdy z tych przypadków opóźnia rzeczywistą budowę obiektu, a ponieważ strumień węzła jest ponownie zamówiony, moduł zapisujący obiekt XAML może polegać na zachowaniu faktycznego konstruowania wystąpienia za każdym razem, gdy napotka się element członkowski start, który nie jest specjalnie dyrektywą budowlaną dla tego typu obiektu.

### <a name="getobject"></a>GetObject

`GetObject`reprezentuje węzeł XAML, gdzie zamiast konstruowania nowego obiektu, moduł zapisujący obiekt XAML powinien zamiast tego uzyskać wartość właściwości zawierającej obiekt. Typowy przypadek, `GetObject` w którym węzeł występuje w strumieniu węzła XAML jest dla obiektu kolekcji lub obiektu słownika, gdy zawierająca właściwość jest celowo tylko do odczytu w modelu obiektu typu zapasowego. W tym scenariuszu kolekcji lub słownika często jest tworzony i inicjowany (zwykle puste) przez logikę inicjowania typu posiadania.

## <a name="see-also"></a>Zobacz też

- <xref:System.Xaml.XamlObjectReader>
- [Usługi XAML](index.md)
- [Przestrzeń nazw XAML](namespaces.md)
