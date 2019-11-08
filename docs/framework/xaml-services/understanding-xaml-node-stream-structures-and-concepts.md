---
title: Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 2c8093c3ef497bd836427f71098e62626f228e24
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733391"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML

Czytelnicy XAML i autorzy języka XAML zaimplementowani w .NET Framework usługach XAML opierają się na koncepcji projektowej strumienia węzłów XAML. Strumień węzłów XAML to conceptualization zestawu węzłów XAML. W tym conceptualization procesor XAML przeprowadzi przez strukturę relacji między węzłami w kodzie XAML po jednym naraz. W dowolnym momencie tylko jeden bieżący rekord lub bieżąca pozycja istnieje w otwartym strumieniu węzła XAML i wiele aspektów interfejsu API raportuje tylko te informacje, które są dostępne w tej pozycji. Bieżący węzeł w strumieniu węzła XAML można opisać jako obiekt, element członkowski lub wartość. Traktując kod XAML jako strumień węzłów XAML, czytelnicy XAML mogą komunikować się z modułami zapisujących XAML i umożliwiają programowi wyświetlanie, współdziałanie z lub zmienianie zawartości strumienia węzłów XAML podczas ścieżki ładowania lub operacji zapisywania ścieżki, która obejmuje kod XAML. Model interfejsu API czytnika i składnika zapisywania języka XAML oraz koncepcja strumienia węzłów XAML są podobne do wcześniejszych powiązanych wzorów i koncepcji modułu odczytującego, takich jak Document Object Model XML (DOM) i <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. W tym temacie omówiono koncepcje strumienia węzłów XAML i opisano, jak można pisać procedury, które współdziałają z reprezentacjami XAML na poziomie węzła XAML.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Ładowanie języka XAML do czytnika XAML

Klasa bazowa <xref:System.Xaml.XamlReader> nie deklaruje konkretnej techniki ładowania początkowego kodu XAML do czytnika XAML. Zamiast tego Klasa pochodna deklaruje i implementuje technikę ładowania, łącznie z ogólnymi właściwościami i ograniczeniami źródła danych wejściowych języka XAML. Na przykład <xref:System.Xaml.XamlObjectReader> odczytuje Graf obiektu, rozpoczynając od źródła danych wejściowych pojedynczego obiektu, który reprezentuje element główny lub podstawowy. <xref:System.Xaml.XamlObjectReader> następnie generuje strumień węzłów XAML z grafu obiektów.

Najwygodniejsze .NET Framework usługi XAML zdefiniowane <xref:System.Xaml.XamlReader> podklasą jest <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> ładuje początkowy kod XAML, ładując plik tekstowy bezpośrednio za pomocą strumienia lub ścieżki pliku, lub pośrednio za pomocą powiązanej klasy czytnika, takiej jak <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> może być uważany za zawierający całość źródła danych wejściowych XAML po jego załadowaniu. Jednak podstawowy interfejs API <xref:System.Xaml.XamlReader> jest zaprojektowana tak, aby czytelnik pracowali z pojedynczym węzłem XAML. Po pierwszym załadowaniu pierwszy pojedynczy węzeł jest katalogiem głównym XAML i jego obiektem początkowym.

### <a name="the-xaml-node-stream-concept"></a>Koncepcja strumienia węzłów XAML

Jeśli zazwyczaj znasz metody DOM, Tree metaphor lub oparte na zapytaniach na potrzeby uzyskiwania dostępu do technologii opartych na języku XML, przydatny sposób konceptualizacji strumienia węzłów XAML jest następujący. Załóżmy, że załadowany kod XAML jest modelem DOM lub drzewem, gdzie każdy możliwy węzeł jest rozwinięty, a następnie prezentowany liniowo. Po przejściu między węzłami można przejść do obszaru "in" lub "out", które byłyby odpowiednie dla modelu DOM, ale strumień węzłów XAML nie jest jawnie śledzony, ponieważ te koncepcje poziomu nie mają zastosowania do strumienia węzła. Strumień węzła ma wartość "Current", ale chyba że przechowujesz inne części strumienia samodzielnie jako odwołania, każdy aspekt strumienia węzła poza bieżącą pozycją węzła jest poza widokiem.

Koncepcja strumienia węzłów XAML ma istotną korzyść, która w przypadku przechodzenia przez cały strumień węzła ma pewność, że przetworzono całą reprezentację XAML; nie trzeba martwić się, że zapytanie, operacja modelu DOM lub inne nieliniowe podejście do przetwarzania informacji nie pozostałej części kompletnej reprezentacji XAML. Z tego powodu Reprezentacja strumienia węzłów XAML jest idealnym rozwiązaniem do łączenia czytników XAML i autorów XAML oraz do zapewnienia systemu, w którym można wstawić własny proces, który działa między fazami odczytu i zapisu operacji przetwarzania XAML. W wielu przypadkach kolejność węzłów w strumieniu węzła XAML jest świadomie zoptymalizowana lub zmieniana według czytelników, a w zależności od tego, w jaki sposób kolejność może być wyświetlana w postaci tekstu źródłowego, binarnego lub grafu obiektów. To zachowanie służy do wymuszania architektury przetwarzania XAML, w której moduły zapisujące XAML nigdy nie znajdują się w pozycji, w której muszą przejść "Wstecz" w strumieniu węzła. W idealnym przypadku wszystkie operacje zapisu XAML powinny być w stanie działać na podstawie kontekstu schematu oraz bieżącego położenia strumienia węzła.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Podstawowa pętla do odczytu węzła

Podstawowa pętla do odczytu między węzłami do badania strumienia węzłów XAML składa się z następujących pojęć. Na potrzeby pętli węzłów zgodnie z opisem w tym temacie założono, że odczytywany jest tekstowy plik XAML, który można odczytać przez człowieka przy użyciu <xref:System.Xaml.XamlXmlReader>. Linki w tej sekcji odnoszą się do określonego interfejsu API pętli węzła XAML zaimplementowanego przez <xref:System.Xaml.XamlXmlReader>.

- Upewnij się, że nie znajdujesz się na końcu strumienia węzła XAML (Sprawdź <xref:System.Xaml.XamlXmlReader.IsEof%2A>lub użyj <xref:System.Xaml.XamlXmlReader.Read%2A> wartości zwracanej). Jeśli znajdujesz się na końcu strumienia, nie ma bieżącego węzła i nie należy go zamykać.

- Sprawdź, jakiego typu węzeł strumień węzłów XAML jest obecnie ujawniany przez wywołanie <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Jeśli masz skojarzony moduł zapisujący obiektów XAML, który jest połączony bezpośrednio, na tym etapie zwykle jest wywoływana <xref:System.Xaml.XamlWriter.WriteNode%2A>.

- Na podstawie tego, który <xref:System.Xaml.XamlNodeType> jest raportowany jako bieżący węzeł lub bieżący rekord, wywołaj jedną z następujących czynności, aby uzyskać informacje o zawartości węzła:

  - W przypadku <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartMember> lub <xref:System.Xaml.XamlNodeType.EndMember>Wywołaj <xref:System.Xaml.XamlXmlReader.Member%2A>, aby uzyskać <xref:System.Xaml.XamlMember> informacje o członku. Należy zauważyć, że element członkowski może być <xref:System.Xaml.XamlDirective>i w ten sposób może niekoniecznie być konwencjonalnym zdefiniowanym typem elementu członkowskiego poprzedniego obiektu. Na przykład `x:Name` zastosowana do obiektu jest wyświetlana jako element członkowski języka XAML, gdzie <xref:System.Xaml.XamlMember.IsDirective%2A> ma wartość true, a <xref:System.Xaml.XamlMember.Name%2A> elementu członkowskiego jest `Name`, z innymi właściwościami wskazującymi, że ta dyrektywa znajduje się w przestrzeni nazw XAML języka XAML.

  - W przypadku <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartObject> lub <xref:System.Xaml.XamlNodeType.EndObject>Wywołaj <xref:System.Xaml.XamlXmlReader.Type%2A>, aby uzyskać <xref:System.Xaml.XamlType> informacje o obiekcie.

  - Aby uzyskać <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.Value>, wywołaj <xref:System.Xaml.XamlXmlReader.Value%2A>. Węzeł jest wartością tylko wtedy, gdy jest to najprostsze wyrażenie wartości elementu członkowskiego lub tekst inicjujący dla obiektu (jednak należy pamiętać o zachowaniu konwersji typu zgodnie z opisem w dalszej części tego tematu).

  - Aby uzyskać <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, wywołaj <xref:System.Xaml.XamlXmlReader.Namespace%2A> w celu uzyskania informacji o przestrzeni nazw dla węzła przestrzeni nazw.

- Wywołaj <xref:System.Xaml.XamlXmlReader.Read%2A>, aby uzyskać więcej czytnika XAML do następnego węzła w strumieniu węzła XAML, a następnie powtórz te kroki ponownie.

Strumień węzłów XAML dostarczany przez czytniki XAML usług XAML .NET Framework zawsze zapewnia pełne, głębokie przechodzenie wszystkich możliwych węzłów. Typowe techniki kontroli przepływu dla pętli węzła XAML obejmują Definiowanie treści w `while (reader.Read())`i przełączanie <xref:System.Xaml.XamlXmlReader.NodeType%2A> w każdym punkcie węzła w pętli węzła.

Jeśli strumień węzłów znajduje się na końcu pliku, bieżący węzeł ma wartość null.

Najprostsza pętla korzystająca z czytnika i składnika zapisywania jest podobna do poniższego przykładu.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Ten podstawowy przykład pętli węzła XAML ścieżki ładowania w sposób przezroczysty łączy czytniki XAML i składnik zapisywania XAML, co nie działa tak, jakby były używane <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Jednak ta podstawowa struktura jest następnie rozwinięta w celu zastosowania do scenariusza odczytu lub zapisu. Poniżej przedstawiono niektóre możliwe scenariusze:

- Przełącz na <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Wykonaj różne akcje w zależności od tego, który typ węzła jest odczytywany.

- Nie wywołuj <xref:System.Xaml.XamlWriter.WriteNode%2A> we wszystkich przypadkach. Wywołaj tylko <xref:System.Xaml.XamlWriter.WriteNode%2A> w niektórych <xref:System.Xaml.XamlXmlReader.NodeType%2A> przypadkach.

- W ramach logiki dla określonego typu węzła analizowanie określonych elementów tego węzła i wykonywanie na nich działań. Można na przykład napisać tylko te obiekty, które pochodzą z określonej przestrzeni nazw XAML, a następnie porzucić lub odłożyć wszystkie obiekty, które nie pochodzą z tej przestrzeni nazw XAML. Można też porzucić lub w inny sposób ponownie przetworzyć wszystkie dyrektywy XAML, które nie są obsługiwane przez system XAML w ramach przetwarzania elementu członkowskiego.

- Zdefiniuj niestandardową <xref:System.Xaml.XamlObjectWriter>, która zastąpi metody `Write*`, prawdopodobnie wykonując mapowanie typu, które pomija kontekst schematu XAML.

- Utwórz <xref:System.Xaml.XamlXmlReader>, aby użyć niedomyślnego kontekstu schematu XAML, tak aby dostosowane różnice w zachowaniu XAML były używane zarówno przez czytnik, jak i moduł zapisujący.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Uzyskiwanie dostępu do języka XAML poza koncepcją pętli węzłów

Istnieją inne sposoby pracy z reprezentacją XAML inną niż pętla węzła XAML. Na przykład może istnieć czytnik XAML, który może odczytać indeksowany węzeł lub w szczególności uzyskuje dostęp do węzłów bezpośrednio przez `x:Name`, przez `x:Uid`, lub za pomocą innych identyfikatorów. Usługi .NET Framework XAML nie zapewniają pełnej implementacji, ale udostępniają sugerowany wzorzec za pomocą usług i typów pomocy technicznej. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IXamlIndexingReader> i <xref:System.Xaml.XamlNodeList>.

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Praca z bieżącym węzłem

Większość scenariuszy korzystających z pętli węzłów XAML nie tylko odczytuje węzły. Większość scenariuszy przetwarza bieżące węzły i przekazuj każdy węzeł pojedynczo do implementacji <xref:System.Xaml.XamlWriter>.

W scenariuszu typowej ścieżki ładowania <xref:System.Xaml.XamlXmlReader> tworzy strumień węzłów XAML; węzły XAML są przetwarzane zgodnie z kontekstem schematu logiki i języka XAML; i węzły są przesyłane do <xref:System.Xaml.XamlObjectWriter>. Następnie można zintegrować otrzymany Graf obiektów z aplikacją lub strukturą.

W typowym scenariuszu zapisywania ścieżki <xref:System.Xaml.XamlObjectReader> odczytuje wykres obiektów, poszczególne węzły XAML są przetwarzane, a <xref:System.Xaml.XamlXmlWriter> wyprowadza Zserializowany wynik jako plik tekstowy XAML. Klucz polega na tym, że zarówno ścieżki, jak i scenariusze obejmują pracę z dokładnie jednym węzłem XAML w danym momencie, a węzły XAML są dostępne do zastosowania w ustandaryzowany sposób, który jest definiowany przez system typów XAML i interfejsów API usług the.NET Framework XAML.

### <a name="frames-and-scope"></a>Ramki i zakres

Pętla węzła XAML przeprowadzi przez strumień węzłów XAML w liniowy sposób. Strumień węzłów przechodzi do obiektów, do elementów członkowskich, które zawierają inne obiekty itd. Często warto śledzić zakres w strumieniu węzła XAML przez implementację koncepcji ramki i stosu. Jest to szczególnie istotne, jeśli aktywnie dostosowujesz strumień węzłów w trakcie jego pracy. Obsługa ramek i stosu zaimplementowana w ramach logiki pętli węzłów może liczyć `StartObject` (lub `GetObject`) i `EndObject` zakresy w miarę jak w strukturze węzłów XAML, jeśli struktura jest traktowana z perspektywy modelu DOM.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Przechodzenie i wprowadzanie węzłów obiektów

Pierwszy węzeł w strumieniu węzła, gdy jest otwarty przez czytnik XAML, jest węzłem startowym obiektu głównego. Według definicji ten obiekt jest zawsze pojedynczym węzłem obiektu i nie ma elementów równorzędnych. W dowolnym rzeczywistym przykładzie XAML, obiekt główny jest zdefiniowany, aby mieć co najmniej jedną właściwość, która zawiera więcej obiektów, i te właściwości mają węzły członkowskie. Węzły elementu członkowskiego mają co najmniej jeden węzeł obiektu lub mogą również kończyć się w węźle wartości. Obiekt główny zwykle definiuje Zakresy nazw WPF języka XAML, które są składniowo przypisywane jako atrybuty w znaczniku tekstowym XAML, ale mapuje do `Namescope` typu węzła w reprezentacji strumienia węzłów XAML.

Rozważmy następujący przykład kodu XAML (jest to dowolny kod XAML, ale nie jest on obsługiwany przez istniejące typy w .NET Framework). Załóżmy, że w tym modelu obiektów `FavorCollection` jest `List<T>` `Favor`, `Balloon` i `NoiseMaker` są przypisywane do `Favor`, właściwość `Balloon.Color` jest obsługiwana przez obiekt `Color`, podobnie jak WPF definiuje kolory jako znane nazwy kolorów. , a `Color` obsługuje konwerter typów dla składni atrybutów.

|Znacznik XAML|Otrzymany strumień węzłów XAML|
|-----------------|--------------------------------|
|`<Party`|`Namespace` węzeł `Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject` węzeł `Party`|
|`<Party.Favors>`|`StartMember` węzeł `Party.Favors`|
||`StartObject` węzła dla niejawnego `FavorCollection`|
||`StartMember` węzła dla właściwości niejawnych elementów `FavorCollection`.|
|`<Balloon`|`StartObject` węzeł `Balloon`|
|`Color="Red"`|`StartMember` węzeł `Color`<br /><br /> `Value` węzła dla ciągu wartości atrybutu `"Red"`<br /><br /> `EndMember` `Color`|
|`HasHelium="True"`|`StartMember` węzeł `HasHelium`<br /><br /> `Value` węzła dla ciągu wartości atrybutu `"True"`<br /><br /> `EndMember` `HasHelium`|
|`>`|`EndObject` `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` węzeł `NoiseMaker`<br /><br /> `StartMember` węzeł `_Initialization`<br /><br /> `Value` węzeł dla ciągu wartości inicjującej `"Loudest"`<br /><br /> `EndMember` węzeł `_Initialization`<br /><br /> `EndObject` `NoiseMaker`|
||`EndMember` węzła dla właściwości niejawnych elementów `FavorCollection`.|
||`EndObject` węzła dla niejawnego `FavorCollection`|
|`</Party.Favors>`|`EndMember` `Favors`|
|`</Party>`|`EndObject` `Party`|

W strumieniu węzła XAML można polegać na następujących zasadach:

- Jeśli węzeł `Namespace` istnieje, jest dodawany do strumienia bezpośrednio przed `StartObject`, który deklaruje przestrzeń nazw XAML z `xmlns`. Zapoznaj się z poprzednią tabelą i ponownie strumieniem węzła XAML i przykładu. Zauważ, jak węzły `StartObject` i `Namespace` są transponowane w porównaniu z ich pozycjami deklaracji w znacznikach tekstowych. Jest to przedstawiciel zachowania, w którym węzły przestrzeni nazw zawsze pojawiają się przed węzłem, do którego stosują się w strumieniu węzła. Celem tego projektu jest to, że informacje o przestrzeni nazw są istotne dla autorów obiektów i muszą być znane przed próbą wykonania mapowania obiektów przez moduł zapisujący, a w przeciwnym razie przetworzyć obiekt. Umieszczenie informacji o przestrzeni nazw XAML przed jej zakresem aplikacji w strumieniu sprawia, że jest to prostsze, aby zawsze przetwarzać strumień węzłów w jego przedstawionej kolejności.

- Ze względu na powyższym zagadnieniem jest jeden lub więcej węzłów `Namespace`, które są najpierw odczytywane w najbardziej rzeczywistych przypadkach znaczników w przypadku przechodzenia między węzłami, a nie `StartObject` korzenia.

- Po węźle `StartObject` może następować `StartMember`, `Value`lub bezpośrednio `EndObject`. Nigdy nie następuje bezpośrednio przez inny `StartObject`.

- Po `StartMember` może następować `StartObject`, `Value`lub bezpośrednio `EndMember`. Może następować `GetObject`, dla elementów członkowskich, w których wartość powinna pochodzić z istniejącej wartości obiektu nadrzędnego, a nie `StartObject`, która spowodowałaby utworzenie wystąpienia nowej wartości. Może również następować `Namespace` węzeł, który ma zastosowanie do nadchodzącego `StartObject`. Nigdy nie następuje bezpośrednio przez inny `StartMember`.

- Węzeł `Value` reprezentuje samą wartość; Brak "wartość końcowa". Może ono następować tylko `EndMember`.

  - Tekst inicjalizacji XAML obiektu, który może być używany przez konstrukcję, nie powoduje, że jest to struktura wartości obiektu. Zamiast tego tworzony jest dedykowany węzeł członkowski dla elementu członkowskiego o nazwie `_Initialization`. i ten węzeł członkowski zawiera ciąg wartości inicjującej. Jeśli istnieje, `_Initialization` jest zawsze pierwszą `StartMember`. `_Initialization` mogą być kwalifikowane w niektórych usługach XAML z namescope XAML języka XAML, aby wyjaśnić, że `_Initialization` nie jest właściwością zdefiniowaną w typach zapasowych.

  - Kombinacja elementu członkowskiego reprezentuje ustawienie atrybutu wartości. W efekcie przetwarzania tej wartości może być używany konwerter wartości, a wartość jest zwykłym ciągiem. Nie jest to jednak oceniane do momentu, gdy moduł zapisujący obiektów XAML przetwarza ten strumień węzła. Moduł zapisujący obiektów XAML posiada wymagany kontekst schematu XAML, mapowanie systemu typów i inne wsparcie wymagane do konwersji wartości.

- Po węźle `EndMember` może następować węzeł `StartMember` dla kolejnego elementu członkowskiego lub przez węzeł `EndObject` dla właściciela elementu członkowskiego.

- Po węźle `EndObject` może następować węzeł `EndMember`. Może również następować węzeł `StartObject`, aby przypadki, w których obiekty są równorzędne w elementach kolekcji. Lub może następować `Namespace` węzeł, który ma zastosowanie do nadchodzącego `StartObject`.

  - W przypadku unikatowego przypadku zamykania całego strumienia węzłów `EndObject` elementu głównego nie następuje po nim. czytnik jest teraz końcem pliku, a <xref:System.Xaml.XamlReader.Read%2A> zwraca `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Konwertery wartości i strumień węzłów XAML

Konwerter wartości jest ogólnym terminem dla rozszerzenia znacznika, konwertera typów (w tym serializacji wartości) lub innej dedykowanej klasy, która jest raportowana jako konwerter wartości za pomocą systemu typów XAML. W strumieniu węzła XAML użycie konwertera typów i użycie rozszerzenia znacznika ma bardzo różne reprezentacje.

### <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typów w strumieniu węzła XAML

Ustawiony atrybut, który ostatecznie powoduje użycie konwertera typów, jest raportowany w strumieniu węzła XAML jako wartość elementu członkowskiego. Strumień węzłów XAML nie próbuje utworzyć obiektu wystąpienia konwertera typów i przekazać do niego wartości. Użycie implementacji konwersji konwertera typów wymaga wywołania kontekstu schematu XAML i użycia go do mapowania typów. Nawet określenie, która Klasa konwertera typów powinna być używana do przetwarzania wartości, wymaga pośredniego kontekstu schematu XAML. W przypadku użycia domyślnego kontekstu schematu języka XAML te informacje są dostępne w systemie typów XAML. Jeśli potrzebujesz informacji o klasie konwerterów typów na poziomie strumienia węzła XAML przed połączeniem z modułem zapisu XAML, możesz uzyskać go z <xref:System.Xaml.XamlMember> informacji o zestawie elementów członkowskich. Ale w przeciwnym razie wprowadzanie konwertera typów powinno być zachowywane w strumieniu węzła XAML jako wartość zwykła, dopóki nie zostaną wykonane pozostałe operacje, które wymagają systemu mapowania typów i kontekstu schematu języka XAML, na przykład utworzenie obiektu przez moduł zapisujący obiektów XAML.

Rozważmy na przykład poniższy konspekt definicji klasy i użycie języka XAML:

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

Tekstowa reprezentacja strumienia węzłów XAML dla tego użycia może być wyrażona w następujący sposób:

`StartObject` z <xref:System.Xaml.XamlType> reprezentującymi `GameBoard`

`StartMember` z <xref:System.Xaml.XamlMember> reprezentującymi `BoardSize`

`Value` węzeł, z ciągiem tekstowym "`8x8`"

`EndMember` dopasowuje `BoardSize`

`EndObject` dopasowuje `GameBoard`

Zwróć uwagę, że w tym strumieniu węzła nie ma wystąpienia konwertera typów. Można jednak uzyskać informacje dotyczące konwertera typów, wywołując <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> `BoardSize`. Jeśli masz prawidłowy kontekst schematu XAML, możesz również wywołać metody konwertera, uzyskując wystąpienie z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w strumieniu węzła XAML

Użycie rozszerzenia znacznika jest zgłaszane w strumieniu węzła XAML jako węzeł obiektu w obrębie elementu członkowskiego, gdzie obiekt reprezentuje wystąpienie rozszerzenia znaczników. W rezultacie użycie rozszerzenia znacznika jest bardziej jawne w reprezentacji strumienia węzłów niż użycie konwertera typów i zawiera więcej informacji. informacje <xref:System.Xaml.XamlMember> nie mogły uzyskać informacji o rozszerzeniu znacznika, ponieważ użycie jest w sytuacji i różni się w każdym możliwym przypadku adiustacji; Ta wartość nie jest dedykowana i niejawna dla typu lub elementu członkowskiego, tak jak w przypadku konwerterów typów.

Strumień węzłów jest reprezentacją rozszerzeń znaczników jako węzłów obiektów, nawet jeśli użycie rozszerzenia znacznika zostało wykonane w postaci atrybutu w znaczniku tekstu XAML (co jest często w przypadku). Użycie rozszerzeń znaczników, które używały jawnego formularza elementu obiektu, jest traktowane w taki sam sposób.

W węźle obiektu rozszerzenia znacznika mogą istnieć elementy należące do tego rozszerzenia znacznika. Reprezentacja strumienia węzłów XAML zachowuje użycie tego rozszerzenia znacznika, niezależnie od tego, czy jest to użycie parametru pozycyjnego, czy użycie z jawnymi nazwanymi parametrami.

W przypadku użycia parametru pozycyjnego strumień węzłów XAML zawiera `_PositionalParameters` Właściwość zdefiniowana w języku XAML, która rejestruje użycie. Ta właściwość jest ogólnym <xref:System.Collections.Generic.List%601> z ograniczeniami <xref:System.Object>. Ograniczenie jest obiektem, a nie ciągiem, ponieważ w tym czasie użycie parametru pozycyjnego może zawierać zagnieżdżone użycie rozszerzenia znaczników. Aby uzyskać dostęp do parametrów pozycyjnych z użycia, można przejść przez listę i użyć indeksatorów dla poszczególnych wartości listy.

W przypadku użycia nazwanego parametru każdy nazwany parametr jest reprezentowany jako węzeł elementu członkowskiego tej nazwy w strumieniu węzła. Wartości elementów członkowskich nie muszą być ciągami, ponieważ może istnieć użycie zagnieżdżonego rozszerzenia znaczników.

`ProvideValue` z rozszerzenia znaczników nie jest jeszcze wywoływana. Jest on jednak wywoływany w przypadku podłączenia czytnika XAML i składnika zapisywania XAML, tak że `WriteEndObject` jest wywoływana w węźle rozszerzenia znacznika podczas badania w strumieniu węzła. Z tego powodu zwykle potrzebny jest ten sam kontekst schematu XAML, który będzie używany w celu utworzenia grafu obiektów na ścieżce ładowania. W przeciwnym razie `ProvideValue` z dowolnego rozszerzenia znacznika może zgłosić wyjątki w tym miejscu, ponieważ nie ma oczekiwanych usług dostępnych.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Elementy członkowskie zdefiniowane w języku XAML i XML w strumieniu węzła XAML

Niektóre elementy członkowskie są wprowadzane do strumienia węzłów XAML ze względu na interpretacje i konwencje czytnika XAML, a nie za pomocą jawnego wyszukiwania <xref:System.Xaml.XamlMember> lub konstrukcji. Często te elementy członkowskie są dyrektywami XAML. W niektórych przypadkach jest to czynność odczytywania kodu XAML, który wprowadza dyrektywę do strumienia węzłów XAML. Inaczej mówiąc, pierwotny wejściowy tekst języka XAML nie określa jawnie dyrektywy member, ale czytnik XAML wstawia dyrektywę w celu spełnienia strukturalnej Konwencji XAML i raportów informacji w strumieniu węzła XAML przed utratą tych informacji.

Poniższa lista zawiera informacje o wszystkich przypadkach, w których czytnik XAML powinien wprowadzić dyrektywę elementu członkowskiego języka XAML i jak ten węzeł jest identyfikowany w .NET Framework implementacjach usług XAML.

- **Tekst inicjujący dla węzła obiektu:** Nazwa tego węzła elementu członkowskiego jest `_Initialization`, reprezentuje dyrektywę XAML i jest zdefiniowana w przestrzeni nazw XAML języka XAML. Możesz uzyskać statyczną jednostkę dla tej <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Parametry pozycyjne dla rozszerzenia znacznika:** Nazwa tego węzła elementu członkowskiego jest `_PositionalParameters`i jest zdefiniowana w przestrzeni nazw XAML języka XAML. Zawsze zawiera ogólną listę obiektów, z których każdy jest parametrem pozycyjnym wstępnie oddzielonym przez dzielenie w znaku ograniczającym `,`, jak to podano w wejściowym języku XAML. Można uzyskać statyczną jednostkę dla dyrektywy Position Parameters z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Nieznana zawartość:** Nazwa tego węzła elementu członkowskiego jest `_UnknownContent`. Dokładnie mówiąc, jest to <xref:System.Xaml.XamlDirective>i jest zdefiniowany w przestrzeni nazw XAML języka XAML. Ta dyrektywa jest używana jako wskaźnik kontrolny dla przypadków, gdy element obiektu XAML zawiera zawartość w źródłowym kodzie XAML, ale nie można określić żadnej właściwości zawartości w ramach obecnie dostępnego kontekstu schematu języka XAML. Ten przypadek można wykryć w strumieniu węzła XAML, sprawdzając elementy członkowskie o nazwach `_UnknownContent`. Jeśli nie zostanie podjęta żadna inna akcja w strumieniu węzła XAML ścieżki ładowania, domyślna <xref:System.Xaml.XamlObjectWriter> zgłasza prób `WriteEndObject`, gdy napotka `_UnknownContent` element członkowski dla dowolnego obiektu. Domyślne <xref:System.Xaml.XamlXmlWriter> nie zgłasza i traktuje element członkowski jako niejawny. Możesz uzyskać statyczną jednostkę dla `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Właściwość kolekcji kolekcji:** Chociaż typ CLR tworzenia kopii zapasowej klasy kolekcji, która jest używana na potrzeby języka XAML zazwyczaj ma dedykowaną, nazwaną właściwość, która przechowuje elementy kolekcji, ta właściwość nie jest znana systemowi typu XAML przed rozpoczęciem rozpoznawania typów zapasowych. Zamiast tego strumień węzłów XAML wprowadza `Items` symbol zastępczy jako element członkowski typu XAML kolekcji. W .NET Framework implementacji usług XAML nazwa tej dyrektywy/elementu członkowskiego w strumieniu węzła jest `_Items`. Stałą dla tej dyrektywy można uzyskać z <xref:System.Xaml.XamlLanguage.Items%2A>.

    Należy zauważyć, że strumień węzłów XAML może zawierać Właściwość Items z elementami, które nie są możliwe do przeanalizowania w oparciu o rozpoznawanie typów i kontekst schematu XAML. Na przykład

- **Elementy członkowskie zdefiniowane w kodzie XML:** Elementy członkowskie zdefiniowane przez XML `xml:base`, `xml:lang` i `xml:space` są raportowane jako dyrektywy XAML o nazwach `base`, `lang`i `space` w implementacjach usług XAML .NET Framework. Przestrzeń nazw dla tych przestrzeni nazw XML `http://www.w3.org/XML/1998/namespace`. Stałe dla każdej z nich można uzyskać z <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Kolejność węzłów

W niektórych przypadkach <xref:System.Xaml.XamlXmlReader> zmienić kolejność węzłów XAML w strumieniu węzła XAML, a w zależności od kolejności wyświetlania węzłów, jeśli są one wyświetlane w znaczniku lub w przypadku przetworzenia jako XML. Jest to wykonywane w celu uporządkowania węzłów w taki sposób, że <xref:System.Xaml.XamlObjectWriter> może przetwarzać strumień węzłów w sposób tylko do przodu.  W .NET Framework usługach XAML czytnik XAML zmienia kolejność węzłów zamiast opuszczania tego zadania do składnika zapisywania XAML, jako Optymalizacja wydajności dla odbiorców składnika zapisywania obiektów XAML w strumieniu węzła.

Niektóre dyrektywy mają na celu dostarczenie większej ilości informacji na potrzeby tworzenia obiektów z elementu obiektu. Dyrektywy te są następujące: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Czytelnicy XAML usług .NET Framework XAML próbują umieścić te dyrektywy jako pierwsze elementy członkowskie w strumieniu węzła po `StartObject`obiektu, z powodów opisanych w następnej sekcji.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Zachowanie XamlObjectWriter i kolejność węzłów

`StartObject` do <xref:System.Xaml.XamlObjectWriter> nie musi być sygnałem do modułu zapisywania obiektów XAML, aby natychmiast skonstruować wystąpienie obiektu. Język XAML zawiera kilka funkcji języka, które umożliwiają inicjowanie obiektu z dodatkowymi danymi wejściowymi i nie polegają wyłącznie na wywołaniu konstruktora bez parametrów, aby utworzyć obiekt początkowy, a dopiero potem ustawić właściwości. Do tych funkcji należą: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; tekst inicjujący; [x:TypeArguments —](x-typearguments-directive.md); parametry pozycyjne rozszerzenia znaczników; Metody fabryki i skojarzone węzły [x:arguments —](x-arguments-directive.md) (XAML 2009). Każdy z tych przypadków opóźnia rzeczywistą konstrukcję obiektu i ze względu na to, że strumień węzłów jest zmieniany, moduł zapisujący obiektów XAML może polegać na zachowaniu rzeczywistego konstruowania wystąpienia, gdy napotkany jest początkowy element członkowski, który nie jest konkretnie konstrukcja Dyrektywa dla tego typu obiektu.

### <a name="getobject"></a>GetObject —

`GetObject` reprezentuje węzeł XAML, gdzie zamiast konstruowania nowego obiektu moduł zapisujący obiektów XAML powinien zamiast niego pobrać wartość właściwości zawierającego obiekt. Typowy przypadek, w którym `GetObject` węzeł jest napotkany w strumieniu węzła XAML jest dla obiektu kolekcji lub obiektu słownika, gdy Właściwość zawierająca jest świadomie tylko do odczytu w modelu obiektów typu zapasowego. W tym scenariuszu kolekcja lub słownik często są tworzone i inicjowane (zwykle puste) przez logikę inicjującą typu będącego właścicielem.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xaml.XamlObjectReader>
- [Usługi XAML](index.md)
- [Przestrzeń nazw XAML](xaml-namespaces-for-net-framework-xaml-services.md)
