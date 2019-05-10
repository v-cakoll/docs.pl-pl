---
title: Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: a04cc8c9dd3e36e4866e773861fddce3c10d0e20
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755159"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML

XAML czytników i składników zapisywania XAML, zaimplementowanego w .NET Framework XAML Services są oparte na projekt koncepcji strumienia węzłów XAML. Strumień węzłów XAML jest conceptualization zestaw węzłów XAML. W tym conceptualization procesora XAML przeprowadzi struktury relacje węzłem w XAML, jeden na raz. W dowolnym momencie tylko jeden rekord bieżący lub bieżącą pozycję w otwarty strumień węzłów XAML i występuje wiele aspektów interfejsu API zgłaszać tylko informacji dostępnych w tej pozycji. Bieżącego węzła w strumień węzłów XAML można opisać jako obiekt, elementu członkowskiego lub wartość. Traktując XAML jako strumień węzłów XAML, czytniki XAML można komunikować się ze składnikami zapisywania XAML i włączyć program, który będzie wyświetlać, wchodzić w interakcje z lub zmienić zawartość strumienia węzłów XAML podczas ścieżki ładowania lub zapisywania operacji ścieżki, która obejmuje XAML. Projekt interfejsu API czytników i składników zapisywania XAML i koncepcji strumienia węzłów XAML przypominają poprzedniego czytnika powiązane i projekty składnika zapisywania i pojęcia, takie jak [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] i <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy. Ten temat zawiera omówienie koncepcji strumienia węzłów XAML, a w tym artykule opisano, jak można napisać procedury, które współdziałają z reprezentacji XAML na poziomie węzłów XAML.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Ładowanie XAML do czytnika XAML

Podstawa <xref:System.Xaml.XamlReader> klasy nie deklaruje technika określonego czytnika XAML podczas ładowania początkowego XAML. Zamiast tego klasę pochodną deklaruje i implementuje technika ładowania, w tym właściwości ogólnych i ograniczeń jego źródło danych wejściowych dla XAML. Na przykład <xref:System.Xaml.XamlObjectReader> odczytuje wykresu obiektu, począwszy od źródła danych wejściowych jednego obiektu, który reprezentuje katalog główny lub podstawowy. <xref:System.Xaml.XamlObjectReader> Następnie tworzy strumień węzłów XAML, z wykresu obiektu.

Najbardziej znaczącym zdefiniowanych przez .NET Framework XAML Services <xref:System.Xaml.XamlReader> jest podklasą <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> ładuje początkowej XAML, albo ładując plik tekstowy bezpośrednio za pomocą ścieżki pliku lub strumienia lub pośrednio za pośrednictwem klasy pokrewne czytnika takich jak <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> Mogą być uważane za zawierające całego źródła danych wejściowych XAML po załadowaniu. Jednak <xref:System.Xaml.XamlReader> podstawowego interfejsu API jest zaprojektowana tak, że czytnik prowadzi interakcję z jednego węzła XAML. Po raz pierwszy załadowano pierwszy jeden węzeł, występujących jest katalogiem głównym XAML i jego obiekt rozpoczęcia.

### <a name="the-xaml-node-stream-concept"></a>Koncepcja Stream węzłów XAML

Jeśli znasz zazwyczaj bardziej modelu DOM, drzewa metaphor lub oparte na zapytaniach podejście do uzyskiwania dostępu do technologii opartych na języku XML, pomocny sposób wyobrażenie strumień węzłów XAML jest następujący. Wyobraź sobie, że załadować XAML jest modelu DOM lub drzewa, w którym rozwinięte aż każdego możliwego węzła, a następnie prezentowany liniowo. Jak możesz przechodzić przez węzły, użytkownik może być przechodzenie "in" lub "out" poziomów, które są istotne dla modelu DOM, ale strumień węzłów XAML nie jawnie śledzić ponieważ te pojęcia poziomu nie mają znaczenia dla strumień węzłów. Strumień węzłów ma pozycji "bieżący", ale jeśli nie zostały zapisane innych części strumienia samodzielnie jako odniesienia, każdy aspekt strumień węzłów innych niż bieżąca pozycja węzła z widoku.

Koncepcji strumienia węzłów XAML ma tę zaletę istotne, że jeśli przejdziesz przez strumień całej węzłów zapewni przetworzyły całą reprezentację XAML; nie trzeba martwić się, że zapytanie, operacja modelu DOM lub innych nieliniowych podejście do przetwarzania informacji brak część pełną reprezentację XAML. Z tego powodu reprezentacji strumienia węzłów XAML doskonale zarówno do łączenia z XAML czytników i składników zapisywania XAML i zapewniające systemu gdzie można wstawiać swoim własnym procesie, która działa między etapami odczytu i zapisu operacji przetwarzania XAML. W wielu przypadkach kolejność węzłów na strumień węzłów XAML jest celowo zoptymalizowane pod kątem lub zmieniana przez czytniki zawartości XAML, a jak kolejność może pojawić się w tekście źródłowym, binary lub wykres obiektu. To zachowanie jest przeznaczona do wymuszania architektury przetwarzania XAML, zgodnie z którą XAML moduły zapisujące są nigdy nie w sytuacji, w której mają Wróć "" w usłudze stream węzła. W idealnym przypadku XAML wszystkie operacje zapisu powinny być możliwość działania oparte na kontekście schematu oraz bieżącą pozycję w strumieniu węzła.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Pętla węzła podstawowych odczytu

Podstawowy odczytywania węzła pętli badanie strumień węzłów XAML składa się z następujące pojęcia. Na potrzeby węzła pętli zgodnie z opisem w tym temacie przyjęto założenie, odczytujesz XAML oparte na tekście, czytelny dla człowieka plików przy użyciu <xref:System.Xaml.XamlXmlReader>. Łącza w tej sekcji dotyczą konkretnego pętli węzłów XAML implementowane przez interfejs API <xref:System.Xaml.XamlXmlReader>.

- Upewnij się, że firma nie jest na końcu strumienia węzłów XAML (Sprawdź <xref:System.Xaml.XamlXmlReader.IsEof%2A>, lub użyj <xref:System.Xaml.XamlXmlReader.Read%2A> zwracają wartość). Jeśli na końcu strumienia, jest nie bieżącego węzła i powinno powodować wyjście.

- Sprawdź, jakiego typu węzła strumień węzłów XAML aktualnie ujawnia przez wywołanie metody <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- W przypadku skojarzone Edytor obiektu XAML, który jest podłączony bezpośrednio ogólnie wywołujesz <xref:System.Xaml.XamlWriter.WriteNode%2A> w tym momencie.

- Na podstawie którego <xref:System.Xaml.XamlNodeType> zostanie zgłoszony jako bieżącego węzła lub bieżącego rekordu wywołać jedną z następujących czynności, aby uzyskać informacje na temat zawartość węzła:

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartMember> lub <xref:System.Xaml.XamlNodeType.EndMember>, wywołaj <xref:System.Xaml.XamlXmlReader.Member%2A> uzyskać <xref:System.Xaml.XamlMember> informacji na temat członka. Należy zauważyć, że składowa może być <xref:System.Xaml.XamlDirective>, a zatem niekoniecznie jest konwencjonalne członkowski zdefiniowany typ poprzedniego obiektu. Na przykład `x:Name` zastosowane do obiektu, który pojawia się jako członek XAML gdzie <xref:System.Xaml.XamlMember.IsDirective%2A> ma wartość true i <xref:System.Xaml.XamlMember.Name%2A> elementu członkowskiego jest `Name`, z innymi właściwościami, co oznacza, że ta dyrektywa w przestrzeni nazw XAML języka XAML.

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartObject> lub <xref:System.Xaml.XamlNodeType.EndObject>, wywołaj <xref:System.Xaml.XamlXmlReader.Type%2A> uzyskać <xref:System.Xaml.XamlType> informacje dotyczące obiektu.

  - Aby uzyskać <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.Value>, wywołaj <xref:System.Xaml.XamlXmlReader.Value%2A>. Węzeł to wartość tylko wtedy, gdy jest Najprostszym wyrażeniem wartość dla elementu członkowskiego lub tekst inicjowania obiektu (jednak należy pamiętać o zachowanie konwersji typu zgodnie z opisem w następnej sekcji tego tematu).

  - Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, wywołaj <xref:System.Xaml.XamlXmlReader.Namespace%2A> można uzyskać informacji dotyczących przestrzeni nazw węzła obszaru nazw.

- Wywołaj <xref:System.Xaml.XamlXmlReader.Read%2A> Przejdź czytnika XAML do następnego węzła w strumień węzłów XAML i powtórz kroki ponownie.

Strumień węzłów XAML, które są dostarczane przez czytniki zawartości XAML Services programu .NET Framework XAML zawsze zapewnia pełne, szczegółowe przechodzenia przez wszystkie węzły możliwych. Techniki typowe sterowanie przepływem dla pętli węzłów XAML to m.in. definiowania jednostka w obrębie `while (reader.Read())`i przełączania na <xref:System.Xaml.XamlXmlReader.NodeType%2A> w każdym węźle punktu w pętli węzła.

Jeśli strumień węzłów znajduje się na końcu pliku, bieżącego węzła ma wartość null.

Najprostsza pętli, która używa czytników i składników zapisywania przypomina poniższy przykład.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Ten prosty przykład pętli węzłów XAML ścieżki obciążenia przezroczyste łączy, XAML, zapisywania i odczytywania XAML, czynności inny niż w przypadku korzystania <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Ale to podstawowa struktura jest rozszerzany do zastosowania do odczytu lub zapisu scenariusza. Oto kilka możliwych scenariuszy:

- Przełącz <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Wykonaj różne akcje, w zależności od tego, który węzeł typu jest odczytu.

- Nie wywołuj <xref:System.Xaml.XamlWriter.WriteNode%2A> we wszystkich przypadkach. Wywoływać tylko <xref:System.Xaml.XamlWriter.WriteNode%2A> w niektórych <xref:System.Xaml.XamlXmlReader.NodeType%2A> przypadków.

- W ramach logiki dla typu określonego węzła analizować szczegółowe informacje na temat tego węzła i wykonywania względem nich działań. Na przykład można napisać tylko obiekty, które pochodzą z określonej przestrzeni nazw XAML i następnie upuść lub Odrocz wszystkie obiekty spoza tej przestrzeni nazw XAML. Lub można porzucić lub w przeciwnym razie ponownie przetworzyć żadnych dyrektyw XAML, które nie obsługuje systemu XAML w ramach przetwarzania elementów członkowskich.

- Definiowanie niestandardowego <xref:System.Xaml.XamlObjectWriter> , zastępuje `Write*` metod, prawdopodobnie wykonanie mapowania typów, które pomija kontekst schematu XAML.

- Konstruowania <xref:System.Xaml.XamlXmlReader> używać inny niż domyślny kontekst schematu XAML, aby dostosowane różnice w zachowaniu XAML są używane zarówno przez czytników i składników zapisywania.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Uzyskiwanie dostępu do XAML poza węzeł koncepcji pętli

Istnieją inne sposoby pracy z reprezentacji XAML w innym niż jako pętli węzłów XAML. Na przykład może istnieć czytnika XAML, który może odczytywać indeksowanych węzła lub w szczególności uzyskuje dostęp do węzłów bezpośrednio przez `x:Name`, `x:Uid`, lub za pośrednictwem innych identyfikatorów. .NET framework XAML Services nie zapewnia pełnej implementacji, ale zapewnia sugerowany wzorzec za pośrednictwem typów usług i pomocy technicznej. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IXamlIndexingReader> i <xref:System.Xaml.XamlNodeList>.

> [!TIP]
> Firma Microsoft tworzy również wersji poza pasmem, znane jako XAML zestawu narzędzi usług Microsoft. W tej wersji out-of-band nadal trwa jego etapów wersji wstępnej. Jednak jeśli jesteś gotowy do pracy ze składnikami wersji wstępnej, XAML zestawu narzędzi usług Microsoft zapewnia kilka interesujących zasobów XAML narzędzia i analizę statyczną XAML. XAML zestawu narzędzi usług Microsoft obejmuje interfejs API modelu DOM XAML, Obsługa analizy programu FxCop i kontekst schematu XAML dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi usług Microsoft XAML](https://code.msdn.microsoft.com/XAML).

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Praca z bieżącego węzła

Większość scenariuszy korzystających z pętli węzłów XAML nie tylko odczytać węzłów. Większość scenariuszy przetwarzania bieżące węzły i przekazać każdy węzeł, jeden w danym momencie implementacji <xref:System.Xaml.XamlWriter>.

W tym scenariuszu ścieżki typowego obciążenia <xref:System.Xaml.XamlXmlReader> tworzy strumień węzłów XAML; węzłów XAML są przetwarzane zgodnie z usługi Logic Apps i kontekst schematu XAML i węzły są przekazywane do <xref:System.Xaml.XamlObjectWriter>. Następnie możesz zintegrować wynikowy wykres obiektu, do aplikacji lub framework.

W typowej Zapisz ścieżkę scenariuszu <xref:System.Xaml.XamlObjectReader> odczytuje wykresu obiektu, poszczególnych węzłów XAML są przetwarzane i <xref:System.Xaml.XamlXmlWriter> wyświetla wynik Zserializowany jako plik tekstowy XAML. Klucz jest, że zarówno w ścieżkach, jak i w scenariuszach operuje dokładnie jeden węzeł XAML w danym momencie i węzłów XAML są dostępne do traktowania w sposób Zestandaryzowany, który jest definiowany przez system typów XAML i środowiska.NET Framework XAML usług API.

### <a name="frames-and-scope"></a>Ramki i zakresu

Pętla węzłów XAML przeprowadzi strumień węzłów XAML w sposób liniowy. Strumień węzłów przechodzi do obiektów, do elementów członkowskich, które zawierają inne obiekty i tak dalej. Często jest to przydatne do śledzenia zakresu, w ramach strumienia węzłów XAML implementując koncepcja ramki i stosu. Jest to szczególnie istotne, jeśli są aktywnie Dostosowywanie strumień węzłów, są w nim. Ramki i stosu obsługi, można zaimplementować jako część logiki pętli węzła może liczyć `StartObject` (lub `GetObject`) i `EndObject` zakresów jako malejąca w strukturze węzłów XAML, jeśli struktura jest traktowane z punktu widzenia DOM w LICZBIE.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Przechodzenie przez i wprowadzając węzłów obiektowych

Pierwszego węzła w strumieniu węzła, gdy zostanie otwarta przez czytnik XAML jest węzeł obiektu rozpoczęcia obiektu głównego. Zgodnie z definicją ten obiekt jest zawsze pojedynczy obiekt węzła i zawiera nie elementów równorzędnych. W przykładzie XAML żadnych rzeczywistych głównego obiektu jest zdefiniowana ma jedną lub więcej właściwości, które zawierają więcej obiektów, a te właściwości mają węzłach Członkowskich. Węzłach Członkowskich mają co najmniej jeden węzeł obiektu lub też może przerwać w węźle wartości na zamiast tego. Obiekt główny zwykle definiuje zakresy nazw XAML, który składniowo przypisanych jako atrybutów w znaczniku XAML tekstu, ale zamapować na `Namescope` typ węzła w reprezentacji strumienia węzłów XAML.

Rozważmy następujący przykład XAML (jest to dowolnego XAML, nie są obsługiwane przez istniejące typy w programie .NET Framework). Przyjęto założenie, że w tym modelu obiektu `FavorCollection` jest `List<T>` z `Favor`, `Balloon` i `NoiseMaker` są można przypisać do `Favor`, `Balloon.Color` właściwość jest wspierana przez `Color` obiektu, podobnie jak definiuje się WPF kolory jako nazw kolorów znane, i `Color` obsługuje konwertera typów dla składni atrybutów.

|Kod znaczników w XAML|Wynikowy strumień węzłów XAML|
|-----------------|--------------------------------|
|`<Party`|`Namespace` węzeł `Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject` węzeł `Party`|
|`<Party.Favors>`|`StartMember` węzeł `Party.Favors`|
||`StartObject` węzeł niejawne `FavorCollection`|
||`StartMember` węzeł niejawne `FavorCollection` elementów właściwości.|
|`<Balloon`|`StartObject` węzeł `Balloon`|
|`Color="Red"`|`StartMember` węzeł `Color`<br /><br /> `Value` węzeł ciągu wartości atrybutu `"Red"`<br /><br /> `EndMember` Aby uzyskać `Color`|
|`HasHelium="True"`|`StartMember` węzeł `HasHelium`<br /><br /> `Value` węzeł ciągu wartości atrybutu `"True"`<br /><br /> `EndMember` Aby uzyskać `HasHelium`|
|`>`|`EndObject` Aby uzyskać `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` węzeł `NoiseMaker`<br /><br /> `StartMember` węzeł `_Initialization`<br /><br /> `Value` węzeł wartość ciągu inicjującego `"Loudest"`<br /><br /> `EndMember` węzeł `_Initialization`<br /><br /> `EndObject` Aby uzyskać `NoiseMaker`|
||`EndMember` węzeł niejawne `FavorCollection` elementów właściwości.|
||`EndObject` węzeł niejawne `FavorCollection`|
|`</Party.Favors>`|`EndMember` Aby uzyskać `Favors`|
|`</Party>`|`EndObject` Aby uzyskać `Party`|

W strumień węzłów XAML możesz polegać na następujące zachowanie:

- Jeśli `Namespace` węzeł istnieje, jest ona dodawana do strumienia bezpośrednio przed `StartObject` zadeklarowany, przestrzeń nazw XAML z `xmlns`. Spójrz na poprzedniej tabeli za pomocą strumienia węzłów XAML i przykład ponownie. Zwróć uwagę sposób, w jaki `StartObject` i `Namespace` węzły wydają się być przekształcony w zależności od ich pozycji deklaracji w znacznikach tekstu. To jest reprezentatywna zachowania, gdzie węzły przestrzeni nazw zawsze są wyświetlane przed węzłem odnoszą się do w strumieniu węzła. Celem ten projekt jest, że informacje o przestrzeni nazw jest niezbędny do składników zapisywania obiektu i musi być znane, zanim obiekt składnika zapisywania próby wykonania typu mapowanie lub w inny sposób przetwarzania obiektu. Wprowadzenie do informacji dotyczących przestrzeni nazw XAML przed jego zakres aplikacji w strumieniu upraszcza zawsze przetwarzać strumień węzłów w ich kolejność prezentowanych.

- Ze względu na powyższe rozpatrywaniu ma jeden lub więcej `Namespace` węzły, które można odczytać najpierw w większości przypadków znacznikach rzeczywistych podczas przechodzenia między węzłami od samego początku nie `StartObject` katalogu głównego.

- A `StartObject` węzła może następować `StartMember`, `Value`, natychmiastowych `EndObject`. Nigdy nie następuje natychmiast innego `StartObject`.

- A `StartMember` może następować `StartObject`, `Value`, natychmiastowych `EndMember`. Może występować przez `GetObject`, dla elementów członkowskich, gdzie wartość powinien pochodzić z istniejącej wartości obiektu nadrzędnego, zamiast `StartObject` , jakbyś tworzył nową wartość. Może również występować przez `Namespace` węzła, który ma zastosowanie do przyszłych `StartObject`. Nigdy nie następuje natychmiast innego `StartMember`.

- A `Value` węzeł reprezentuje sama wartość; nie ma żadnych "wartość końcowa panelu". Może być stosowana tylko przez `EndMember`.

  - XAML tekst inicjowanie obiektu może być używany przez konstrukcja nie powoduje w strukturze wartość obiektu. Zamiast tego węzła dedykowanych składowej dla elementu członkowskiego o nazwie `_Initialization` zostanie utworzony. a ten węzeł elementu członkowskiego zawiera wartość ciągu inicjującego. Jeśli istnieje, `_Initialization` zawsze jest to pierwszy `StartMember`. `_Initialization` może być kwalifikowana w niektórych reprezentacje usług XAML z namescope XAML języka XAML, które informuje, że `_Initialization` nie jest zdefiniowany właściwością przy tworzeniu kopii typów.

  - Kombinacja wartość elementu członkowskiego reprezentuje ustawienia wartości atrybutów. Po pewnym czasie prawdopodobnie istnieje konwerter wartości związane z przetwarzaniem tę wartość, a wartość to zwykły ciąg znaków. Jednakże, nie jest oceniany, dopóki zapisywania obiektu XAML przetwarza strumień tego węzła. Moduł zapisywania obiektów XAML ma niezbędne kontekst schematu XAML, mapowania systemu typów i innych pomocy technicznej potrzebnych do konwersji wartości.

- `EndMember` Węzła może następować `StartMember` węzła dla kolejnych elementów członkowskich lub przez `EndObject` węzła właściciela elementu członkowskiego.

- `EndObject` Węzła może następować `EndMember` węzła. Może również występować przez `StartObject` węzła w przypadkach, w których obiekty są elementami równorzędnymi, w kolekcji elementów. Lub może być stosowana przez `Namespace` węzła, który ma zastosowanie do przyszłych `StartObject`.

  - Przypadku unikatowy zamykać strumień cały węzeł `EndObject` z katalogu głównego nie następuje niczego; czytnik jest teraz końca pliku i <xref:System.Xaml.XamlReader.Read%2A> zwraca `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Konwertery wartości i Stream węzłów XAML

Konwerter wartości jest ogólnym terminem dla rozszerzenia znaczników, konwertera typów (w tym serializatory wartość) lub inny dedykowany klasy, która jest zgłaszana jako konwertera wartości w systemie typu XAML. W strumieniu węzłów XAML użycia konwertera typu i użycie rozszerzenia znaczników mają bardzo różne reprezentacje.

### <a name="type-converters-in-the-xaml-node-stream"></a>Typy konwerterów w Stream węzłów XAML

Atrybut ustawiony na tym, że ostatecznie wyniki użycia konwertera typu jest zgłaszana w strumień węzłów XAML jako wartość elementu członkowskiego. Strumień węzłów XAML nie próbuje utworzyć obiekt typu konwertera wystąpienia i przekaż wartość do niego. Przy użyciu konwertera typów konwersji implementacji wymaga wywołania kontekst schematu XAML i używać go do mapowania typów. Nawet określanie, której typ klasy konwertera powinien być używany do przetwarzania wartość pośredni wymaga kontekst schematu XAML. Gdy używany jest domyślny kontekst schematu XAML, te informacje są dostępne w systemie typu XAML. Jeśli potrzebujesz informacji o klasie konwertera typu na poziomie strumienia węzłów XAML przed połączenie Edytor XAML, możesz uzyskać je od <xref:System.Xaml.XamlMember> informacji jest zestaw elementów członkowskich. Ale w przeciwnym razie dane wejściowe konwertera typu powinny zostać zachowane w strumień węzłów XAML jako zwykły wartość aż do końca operacji wymagających system mapowanie typu i kontekst schematu XAML są wykonywane, na przykład tworzenia obiektu przez XAML obiekt składnika zapisywania.

Na przykład należy wziąć pod uwagę następujące konspektu definicji klasy i użycie XAML dla niego:

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

Tekstowa reprezentacja strumień węzłów XAML dla tego użycia może być wyrażona jako następujące:

`StartObject` za pomocą <xref:System.Xaml.XamlType> reprezentujący `GameBoard`

`StartMember` za pomocą <xref:System.Xaml.XamlMember> reprezentujący `BoardSize`

`Value` węzeł, z ciągu tekstowego "`8x8`"

`EndMember` Dopasowania `BoardSize`

`EndObject` Dopasowania `GameBoard`

Zauważ, że istnieje żadne wystąpienie konwertera typu w strumieniu tego węzła. Ale możesz uzyskać informacje o typie konwerter przez wywołanie metody <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> dla `BoardSize`. Jeśli masz prawidłowy kontekst schematu XAML, można także wywoływać metody konwerter, uzyskując wystąpienie z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w XAML Stream węzła

Użycie rozszerzenia znaczników jest zgłaszany w strumień węzłów XAML jako węzeł obiektu elementu członkowskiego, w którym obiekt reprezentuje wystąpienie rozszerzenia znaczników. Związku z tym to użycia rozszerzenia znaczników jest przedstawiony bardziej jawny sposób w reprezentacji strumienia węzłów niż użycia konwertera typu to a niesie ze sobą więcej informacji. <xref:System.Xaml.XamlMember> informacji może nie mieć informację, możesz niczego o rozszerzenie znaczników ponieważ użycie jest sytuacyjnej i różni się w każdym przypadku znaczników możliwe; nie jest dedykowany i niejawne dla typu lub elementu członkowskiego jak w przypadku konwerterów typów.

Reprezentacja strumienia węzła Rozszerzenia znaczników jako węzły obiektów jest przypadek, nawet wtedy, gdy użycie rozszerzenia znaczników została wprowadzona w formie atrybutu w znaczniku tekst XAML (co ma często miejsce). Użycia rozszerzenia znaczników, używane w formularzu elementów obiektu jawne, są traktowane tak samo.

W węźle obiektu rozszerzenia znaczników może być członkami tego rozszerzenia znaczników. Reprezentacja strumienia węzłów XAML zachowuje użycie tego rozszerzenia znaczników, czy użycie parametr pozycyjne czy użycia za pomocą jawnego nazwanych parametrów.

Użycie parametr pozycyjne strumień węzłów XAML zawiera właściwość zdefiniowanym przez język XAML `_PositionalParameters` zawierające rekordy użycia. Ta właściwość jest ogólny <xref:System.Collections.Generic.List%601> z <xref:System.Object> ograniczenia. Ograniczenie jest obiekt i nie ciągu, ponieważ wielkiego użycia parametr pozycyjne może zawierać użycia rozszerzenia znaczników zagnieżdżony w nim. Dostęp do parametry pozycyjne z użycia, możesz iteracji przez listę i użyj indeksatorów dla poszczególnych wartości.

Użycie nazwany parametr każdy nazwany parametr jest reprezentowany jako węzeł element członkowski o takiej nazwie w strumieniu węzła. Wartości elementów członkowskich niekoniecznie ciągów, ponieważ może to być to użycia rozszerzenia znaczników zagnieżdżonych.

`ProvideValue` z kodu znaczników rozszerzenie nie jest jeszcze wywoływany. Jednak jest wywoływana, jeśli łączysz się XAML odczytywania i zapisywania XAML, aby `WriteEndObject` jest wywoływana w węźle rozszerzenia znaczników podczas badania w usłudze stream węzła. Z tego powodu konieczne są zazwyczaj ten sam kontekst schematu XAML dostępne zostałyby użyte w celu utworzenia wykresu obiektu na ścieżce obciążenia. W przeciwnym razie `ProvideValue` z marżę rozszerzenia mogą zgłosić wyjątek, ponieważ nie ma oczekiwanego dostępne usługi.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML i XML zdefiniowanym przez język elementów członkowskich w Stream węzłów XAML

Niektóre elementy członkowskie są wprowadzane do strumienia węzłów XAML z powodu interpretacje i konwencje czytnik XAML zamiast za pomocą jawnego <xref:System.Xaml.XamlMember> wyszukiwania lub konstrukcji. Często te elementy członkowskie są dyrektywami XAML. W niektórych przypadkach jest act, odczytywania, XAML, która wprowadza dyrektywy do strumienia węzłów XAML. Innymi słowy oryginalnym wprowadź tekst XAML nie określone jawnie member, dyrektywa, ale czytnik XAML wstawia dyrektywy, aby spełnić wymagania strukturalne XAML Konwencji i przekazuje informacje w strumień węzłów XAML, zanim te informacje zostaną utracone.

Poniższe listy informacje o wszystkich przypadkach, gdzie czytnik XAML jest oczekiwana wprowadzenie dyrektywy węzeł składowej XAML i sposób identyfikacji tego węzła elementu członkowskiego we wdrożeniach usług programu .NET Framework XAML.

- **Tekst inicjowania węzeł obiektu:** Nazwa tego węzła elementu członkowskiego jest `_Initialization`reprezentuje dyrektywa XAML i jest on zdefiniowany w przestrzeni nazw XAML dla języka XAML. Możesz też uzyskać statyczne jednostki z <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Parametry pozycyjne rozszerzenia znaczników:** Nazwa tego węzła elementu członkowskiego jest `_PositionalParameters`, i jest on zdefiniowany w przestrzeni nazw XAML dla języka XAML. Zawsze zawiera listy ogólnej obiektów, z których każdy jest parametr pozycyjne wstępnie rozdzielone dzielenie na `,` znak ogranicznika, ponieważ podana w danych wejściowych XAML. Możesz też uzyskać statyczne jednostki dyrektywy parametry pozycyjne z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Nieznany zawartość:** Nazwa tego węzła elementu członkowskiego jest `_UnknownContent`. Ściśle rzecz ujmując, jest <xref:System.Xaml.XamlDirective>, i jest on zdefiniowany w przestrzeni nazw XAML dla języka XAML. Ta dyrektywa służy jako wskaźnikowych w przypadkach, gdy XAML object element zawiera zawartość w źródle, XAML, ale żadnej zawartości właściwości można określić w ramach aktualnie dostępne kontekst schematu XAML. Można wykryć tego przypadku w strumień węzłów XAML przez sprawdzenie, czy elementy członkowskie o nazwie `_UnknownContent`. Jeśli żadna inna akcja nie zostaną podjęte w postaci strumienia węzłów XAML ścieżki obciążenia o domyślnie <xref:System.Xaml.XamlObjectWriter> zgłoszenie próba `WriteEndObject` po napotkaniu `_UnknownContent` Członkowskie dowolnego obiektu. Wartość domyślna <xref:System.Xaml.XamlXmlWriter> nie generuje i traktuje elementu członkowskiego jako niejawne. Możesz uzyskać statyczne jednostki dla `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Właściwość kolekcji kolekcji:** Mimo że zapasowy typ CLR klasy kolekcji, która jest zwykle używany dla XAML ma dedykowany nazwane właściwości, który zawiera elementy kolekcji, tej właściwości jest nieznany w systemie typu XAML przed wykonaniem kopii rozpoznawanie typu. Zamiast tego strumienia węzłów XAML wprowadzono `Items` symbol zastępczy jest członkiem kolekcji typu XAML. W implementacji .NET Framework XAML Services nazwę tej dyrektywy / element członkowski w strumieniu węzła jest `_Items`. Stała tym dyrektywy można uzyskać z <xref:System.Xaml.XamlLanguage.Items%2A>.

    Należy pamiętać, że strumień węzłów XAML może zawierać elementy slajdu elementy, które okazały się nie można przeanalizować na podstawie zapasowego typu rozwiązania i kontekst schematu XAML. Na przykład

- **Elementy członkowskie zdefiniowane XML:** Definicja XML `xml:base`, `xml:lang` i `xml:space` elementy członkowskie są zgłaszane jako XAML dyrektywy o nazwie `base`, `lang`, i `space` we wdrożeniach usług programu .NET Framework XAML. Przestrzeń nazw dla tych jest przestrzeń nazw XML `http://www.w3.org/XML/1998/namespace`. Stałe dla każdego z nich można uzyskać z <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Kolejność węzłów

W niektórych przypadkach <xref:System.Xaml.XamlXmlReader> zmienia kolejność węzłów XAML w strumień węzłów XAML, a kolejność węzłów wyświetlane w znaczniku, lub jeśli przetwarzane jako XML. W ten sposób można kolejność węzłów tak, aby <xref:System.Xaml.XamlObjectWriter> może przetwarzać strumień węzłów w sposób tylko do przodu.  W programie .NET Framework XAML Services czytnika XAML zmienia kolejność węzłów, a nie pozostawiając tego zadania w składniku zapisywania XAML, jak zoptymalizować wydajność XAML obiekt składnika zapisywania konsumentów strumień węzłów.

Niektóre dyrektywy są przeznaczone specjalnie w celu zapewnienia dodatkowe informacje dotyczące tworzenia obiektu z elementu obiektu. Te dyrektywy są: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Czytelnicy XAML Services programu .NET Framework XAML próbować umieścić te dyrektywy jako pierwsze elementy członkowskie w strumieniu węzła następującego obiektu `StartObject`, przyczyn, które są opisane w następnej sekcji.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Zachowanie XamlObjectWriter i kolejność węzłów

`StartObject` Aby <xref:System.Xaml.XamlObjectWriter> niekoniecznie jest sygnał do modułu zapisywania obiektu XAML bezpośrednio utworzyć wystąpienie obiektu. XAML udostępnia kilka funkcji języka, które umożliwiają programowi na można zainicjować obiektu przy użyciu dodatkowych danych wejściowych i nie zależą od całkowicie wywoływania konstruktora domyślnego, aby wygenerować początkowego obiektu, a dopiero potem Ustawianie właściwości. Te funkcje obejmują: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; inicjowania tekstu. [x: typearguments —](x-typearguments-directive.md); pozycyjnych parametrów rozszerzenia znaczników; metodach fabryki i skojarzone [x: Arguments](x-arguments-directive.md) węzłów (XAML 2009). Każda z tych przypadków opóźnienie konstruowania rzeczywistego obiektu, a ponieważ strumień węzłów kolejność została zmieniona, modułu zapisywania obiektu XAML może polegać na zachowanie faktycznie konstruowanie wystąpienie, zawsze wtedy, gdy członek start zostanie osiągnięty, który nie jest specjalnie konstrukcji dyrektywa dla tego typu obiektu.

### <a name="getobject"></a>GetObject

`GetObject` reprezentuje węzeł XAML, gdzie zamiast tworzenia nowego obiektu, Edytor XAML obiekt powinien zamiast tego uzyskać wartość zawierającą je właściwość obiektu. Typowy przypadek gdzie `GetObject` napotkaniu węzeł w węźle XAML strumień jest dla obiektu kolekcji lub obiekt słownika podczas zawierającą je właściwość jest celowo tylko do odczytu w zapasowy typ obiektu modelu. W tym scenariuszu, kolekcji lub słownika często jest tworzony i inicjowany (zazwyczaj jest to puste) elementowi logiki inicjowania typu, będącego właścicielem.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xaml.XamlObjectReader>
- [Usługi XAML](index.md)
- [Przestrzeń nazw XAML](xaml-namespaces-for-net-framework-xaml-services.md)
