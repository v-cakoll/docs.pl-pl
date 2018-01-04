---
title: "Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5bce62b03b97f182d314a379c9532fc05148050
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML
Czytniki XAML i zapisywania XAML zgodnie z implementacją w .NET Framework XAML Services są oparte na koncepcję projektu strumienia węzłów XAML. Strumień węzłów XAML jest conceptualization zestawu węzłów XAML. W tym conceptualization procesora XAML przedstawiono struktury relacje węzła w języku XAML, co w czasie. W dowolnym momencie istnieje tylko jeden rekord bieżący lub bieżącą pozycję w otwartych strumień węzłów XAML, a wiele aspektów interfejsu API zgłaszać tylko te informacje dostępne w tym miejscu. Bieżący węzeł w strumień węzłów XAML można przedstawić jako obiekt, element członkowski lub wartość. Traktując XAML jako strumień węzłów XAML, czytników XAML można komunikować się z autorów XAML i włączyć program do wyświetlania, interakcji z i zmienić zawartość strumienia węzłów XAML podczas ładowania ścieżki lub Zapisz operacji ścieżki, która obejmuje XAML. Projekt interfejsu API składników zapisywania i odczytywania XAML i koncepcji strumienia węzłów XAML są takie jak podobne do poprzedniego czytnika pokrewne i zapisywania projektów i pojęcia [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] i <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy. W tym temacie omówiono pojęcia strumienia węzłów XAML i zawiera opis sposobu pisania procedury wchodzące w interakcje z reprezentacji XAML na poziomie węzła XAML.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>Ładowania kodu XAML do czytnika XAML  
 Podstawowym <xref:System.Xaml.XamlReader> klasy nie deklaruje określonego technika ładowania początkowego XAML do czytnika XAML. Zamiast tego klasy pochodnej deklaruje i implementuje technika ładowania, łącznie z właściwości ogólne i ograniczenia jego źródło danych wejściowych dla języka XAML. Na przykład <xref:System.Xaml.XamlObjectReader> odczytuje wykres obiektu, począwszy od źródło pojedynczy obiekt, który reprezentuje katalog główny lub bazy danych wejściowych. <xref:System.Xaml.XamlObjectReader> Następnie tworzy strumień węzłów XAML z wykresu obiektu.  
  
 Najbardziej widocznym usług .NET Framework XAML — definicja <xref:System.Xaml.XamlReader> jest podklasą <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader>ładuje XAML początkowej, albo przez załadowanie pliku tekstowego bezpośrednio za pomocą ścieżki strumienia lub pliku lub pośrednio za pośrednictwem klasy pokrewne czytnika takich jak <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> Mogą być uważane za zawierające całości źródło danych wejściowych XAML po załadowaniu. Jednak <xref:System.Xaml.XamlReader> podstawowy interfejs API zaprojektowano tak, aby czytnik prowadzi interakcję z jednego węzła XAML. Po raz pierwszy załadowano pierwszy jednego węzła, które wystąpią jest elementem głównym pliku XAML, a jego początkowy obiekt.  
  
### <a name="the-xaml-node-stream-concept"></a>Pojęcie strumienia węzłów XAML  
 Jeśli znasz zazwyczaj bardziej modelu DOM, metaphor drzewa lub oparte na zapytaniach podejście do uzyskiwania dostępu do technologii opartych na języku XML, pomocny sposób conceptualize strumień węzłów XAML ma następującą składnię. Załóżmy, że załadować XAML jest modelu DOM lub drzewa, w którym rozwinięty aż co węzłów, a następnie udostępniana liniowo. Jak możesz przechodzić przez węzły, możesz może być przechodzenie "in" lub "out" poziomów, które są istotne dla modelu DOM, ale strumień węzłów XAML nie jawnie śledzić ponieważ tych pojęć poziomu nie są odpowiednie do strumienia węzłów. Strumień węzłów ma pozycji "bieżący", ale chyba, że są przechowywane inne części strumienia samodzielnie jako odniesienie, każdego aspektu strumieniu węzłów, innej niż bieżąca pozycja węzła niewidocznymi.  
  
 Pojęcie strumienia węzłów XAML ma tę zaletę zauważalne, że przejście do strumienia całego węzła zapewni przetworzyły całej reprezentacji XAML; nie trzeba się martwić się, że zapytanie, operacja modelu DOM lub innych rożne podejście do przetwarzania informacji brakuje część pełną reprezentacja XAML. Z tego powodu reprezentacja strumienia węzłów XAML jest idealny zarówno w przypadku łączenia czytników XAML i zapisywania XAML i udostępnia system gdzie wstawić własnego procesu działającego między etapami odczytu i zapisu operacji przetwarzania XAML. W wielu przypadkach kolejność węzłów w strumieniu węzłów XAML jest celowo zoptymalizowanych pod kątem lub zmienić kolejności przez czytelników XAML i jak kolejność może pojawiać się tekst źródłowy, binary lub wykres obiektu. To zachowanie jest przeznaczony do wymuszania Architektura przetwarzania XAML, zgodnie z którymi autorów XAML znajdują się nigdy w pozycji, które mają Wróć "" w strumieniu węzłów. W idealnym przypadku XAML wszystkie operacje zapisu powinny być możliwość działania oparte na kontekst schematu oraz bieżącą pozycję w strumieniu węzłów.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Pętla węzła podstawowego odczytu  
 Podstawowy odczytywania węzła pętli badania strumień węzłów XAML składa się z następujące pojęcia. Dla celów węzła pętle zgodnie z opisem w tym temacie założono, czytają XAML tekstu, czytelny dla człowieka plików przy użyciu <xref:System.Xaml.XamlXmlReader>. Łącza w tej sekcji odnoszą się do określonego węzła XAML pętli API zaimplementowano przez <xref:System.Xaml.XamlXmlReader>.  
  
-   Upewnij się, że firma nie jest końcem strumienia węzłów XAML (Sprawdź <xref:System.Xaml.XamlXmlReader.IsEof%2A>, lub użyj <xref:System.Xaml.XamlXmlReader.Read%2A> wartość zwracana). Jeśli na końcu strumienia, nie nie bieżącego węzła a powinny być kończone.  
  
-   Sprawdź, jakiego typu węzła strumień węzłów XAML obecnie udostępnia przez wywołanie metody <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Jeśli masz skojarzone Edytor obiektu XAML, który jest podłączony bezpośrednio, zazwyczaj wywołania <xref:System.Xaml.XamlWriter.WriteNode%2A> w tym momencie.  
  
-   Na podstawie którego <xref:System.Xaml.XamlNodeType> jest zgłaszana jako bieżący węzeł lub bieżącego rekordu, wywołaj jedną z następujących czynności, aby uzyskać informacje o zawartości węzła:  
  
    -   Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartMember> lub <xref:System.Xaml.XamlNodeType.EndMember>, wywołaj <xref:System.Xaml.XamlXmlReader.Member%2A> uzyskanie <xref:System.Xaml.XamlMember> informacje o składniku. Należy pamiętać, że element członkowski może być <xref:System.Xaml.XamlDirective>, i w związku z tym może nie musi należeć do konwencjonalnych zdefiniowany typ poprzedniego obiektu. Na przykład `x:Name` dotyczą obiekt pojawia się jako członek XAML gdzie <xref:System.Xaml.XamlMember.IsDirective%2A> ma wartość true i <xref:System.Xaml.XamlMember.Name%2A> elementu członkowskiego jest `Name`, z innymi właściwościami, co oznacza, że ta dyrektywa w przestrzeni nazw XAML języka XAML.  
  
    -   Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartObject> lub <xref:System.Xaml.XamlNodeType.EndObject>, wywołaj <xref:System.Xaml.XamlXmlReader.Type%2A> uzyskanie <xref:System.Xaml.XamlType> informacji o obiekcie.  
  
    -   Aby uzyskać <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.Value>, wywołaj <xref:System.Xaml.XamlXmlReader.Value%2A>. Węzeł jest wartością tylko wtedy, gdy jest najprostsza wyrażenie wartości dla elementu członkowskiego lub tekst inicjowania dla obiekt (jednak należy pamiętać o zachowanie konwersji typu zgodnie z opisem w następnej sekcji tego tematu).  
  
    -   Dla <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, wywołaj <xref:System.Xaml.XamlXmlReader.Namespace%2A> można uzyskać informacji dotyczących przestrzeni nazw dla węzła przestrzeni nazw.  
  
-   Wywołanie <xref:System.Xaml.XamlXmlReader.Read%2A> przejść do następnego węzła w strumieniu węzłów XAML czytnika XAML i powtórz kroki ponownie.  
  
 Strumień węzłów XAML, które są udostępniane przez .NET Framework XAML Services XAML czytniki zawsze zapewnia pełne, głębokie przejście przez wszystkie węzły możliwych. Sterowanie przepływem typowe techniki pętli węzła XAML obejmują definiowanie treści w `while (reader.Read())`i włączenie <xref:System.Xaml.XamlXmlReader.NodeType%2A> w każdym węźle punktu w pętli węzła.  
  
 Jeśli na końcu pliku strumieniu węzłów, bieżący węzeł ma wartość null.  
  
 Najprostsza pętli, które używa składników zapisywania i odczytywania podobnego do następującego.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Ten prosty przykład pętli węzła XAML ścieżki obciążenia niewidocznie łączy XAML zapisywania i odczytywania XAML, czynności nic innego niż w przypadku korzystania <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Jednak to podstawowa struktura jest rozszerzana do zastosowania do odczytu lub zapisu scenariusza. Niektóre możliwe scenariusze są następujące:  
  
-   Przełącz <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Wykonaj różne akcje, w zależności od tego, który węzeł odczyt typu.  
  
-   Nie wywołuj <xref:System.Xaml.XamlWriter.WriteNode%2A> we wszystkich przypadkach. Wywoływać tylko <xref:System.Xaml.XamlWriter.WriteNode%2A> w niektórych <xref:System.Xaml.XamlXmlReader.NodeType%2A> przypadkach.  
  
-   W ramach logikę typu określonego węzła analizować szczegółowe informacje na temat tego węzła i działają na nich. Na przykład można zapisać tylko te obiekty, które pochodzą z określonego obszaru nazw XAML, a następnie upuść lub odroczenie żadne obiekty nie z tej przestrzeni nazw XAML. Lub może porzucić lub w przeciwnym razie ponownie przetworzyć wszystkie dyrektyw XAML, które nie obsługuje systemu XAML w ramach przetwarzania elementów członkowskich.  
  
-   Definiowanie niestandardowego <xref:System.Xaml.XamlObjectWriter> który zastępuje `Write*` metod, prawdopodobnie wykonywania mapowanie typu, które pomija kontekst schematu XAML.  
  
-   Utworzyć <xref:System.Xaml.XamlXmlReader> do użycia inny niż domyślny kontekst schematu XAML, aby dostosowane różnice w zachowaniu XAML są używane zarówno przez składnik zapisywania i odczytywania.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Uzyskiwanie dostępu do XAML poza węzeł koncepcji pętli  
 Istnieją inne sposoby pracy z reprezentacji XAML innych niż jako pętli węzła XAML. Na przykład mogą istnieć czytnika XAML, który może odczytywać indeksowanego węzła lub w szczególności uzyskuje dostęp do węzłów bezpośrednio przez `x:Name`, przez `x:Uid`, lub za pośrednictwem innych identyfikatorów. Usługi XAML .NET framework nie zapewnia pełnej implementacji, ale zapewnia sugerowane wzorzec za pośrednictwem typów usług i pomocy technicznej. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IXamlIndexingReader> i <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  Firma Microsoft tworzy również wydania poza pasmem, znane jako Microsoft XAML Toolkit. Ta wersja poza pasmem jest nadal w jego etapów wersji wstępnej. Jeśli jest gotowa do pracy ze składnikami wersji wstępnej, XAML zestawu narzędzi firmy Microsoft zapewnia jednak niektóre ciekawe zasoby dla języka XAML narzędzi i analizy statycznej XAML. XAML zestawu narzędzi firmy Microsoft obejmuje interfejs API modelu DOM języka XAML, obsługują analizy programu FxCop i kontekst schematu XAML dla programu Silverlight. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi firmy Microsoft XAML](http://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Praca z bieżącego węzła  
 Większość scenariuszy, które korzystają z pętli węzła XAML nie tylko odczytać węzłów. Większości scenariuszy przetwarzania bieżącego węzłów i przekaż każdego węzła, co w czasie do wykonania <xref:System.Xaml.XamlWriter>.  
  
 W tym scenariuszu ścieżki typowego obciążenia <xref:System.Xaml.XamlXmlReader> tworzy strumień węzłów XAML; węzłów XAML są przetwarzane zgodnie z sieci logiczne i kontekst schematu XAML i węzły są przekazywane do <xref:System.Xaml.XamlObjectWriter>. Następnie można zintegrować wynikowy wykres obiektu do aplikacji lub framework.  
  
 W typowym Zapisz scenariusz ścieżki <xref:System.Xaml.XamlObjectReader> odczytuje wykres obiektu, poszczególne węzły XAML są przetwarzane i <xref:System.Xaml.XamlXmlWriter> generuje serializacji wynik w postaci pliku tekstowego XAML. Klucz jest, że zarówno ścieżki, jak i scenariusze obejmują pracy z dokładnie jednego węzła XAML w czasie i węzłów XAML są dostępne do przetwarzania w sposób Zestandaryzowany zdefiniowanego przez system typów języka XAML i środowiska.NET Framework XAML Services API.  
  
### <a name="frames-and-scope"></a>Ramek i zakresu  
 Pętla węzła XAML przeprowadzi Cię przez strumień węzłów XAML w sposób liniowej. Strumień węzłów jest przesyłany do obiektów, do elementów członkowskich, które zawierają inne obiekty i tak dalej. Często jest przydatne do śledzenia zakresie w strumieniu węzłów XAML zaimplementowanie koncepcji ramki i stosu. Jest to szczególnie istotne, jeśli są aktywnie dostosowywania strumieniu węzłów, gdy są w nim. Ramki i stosu obsługuje, można zaimplementować jako część logiki pętli węzeł może liczba `StartObject` (lub `GetObject`) i `EndObject` zakresów jako malejąca w strukturze węzła XAML, jeśli struktura jest traktować z punktu widzenia DOM.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Przeglądanie i wprowadzając węzłów obiektowych  
 Pierwszy węzeł w strumieniu węzła, gdy jest otwarty przez czytnik XAML jest węzeł początkowy obiekt obiektu głównego. Zgodnie z definicją tego obiektu jest zawsze pojedynczy obiekt węzła i ma nie elementów równorzędnych. W przykładzie XAML żadnych rzeczywistych zdefiniowano główny obiekt ma co najmniej jednej właściwości zawierających więcej obiektów, a te właściwości mają węzły elementu członkowskiego. Węzły element członkowski ma co najmniej jeden węzeł obiektu lub może być zamknięcie w węźle wartości zamiast tego. Obiekt główny zwykle definiuje namescopes XAML, składniowo są przypisane jako atrybuty tekstu w kodzie XAML, ale mapowania `Namescope` typ węzła w reprezentacji strumienia węzłów XAML.  
  
 Należy wziąć pod uwagę w poniższym przykładzie XAML (jest to dowolnego języka XAML, nie jest obsługiwana przez istniejące typy w programie .NET Framework). Przyjęto założenie, że w tym modelu obiektu `FavorCollection` jest `List<T>` z `Favor`, `Balloon` i `NoiseMaker` są można przypisać do `Favor`, `Balloon.Color` właściwość nie jest obsługiwana przez `Color` obiektu podobny do sposobu definiuje WPF kolory jako nazwy kolorów znane, i `Color` obsługuje konwertera typów programu Składnia atrybutu.  
  
|Kod znaczników XAML|Wynikowa strumień węzłów XAML|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace`węzeł`Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject`węzeł`Party`|  
|`<Party.Favors>`|`StartMember`węzeł`Party.Favors`|  
||`StartObject`węzeł niejawne`FavorCollection`|  
||`StartMember`węzeł niejawne `FavorCollection` elementów właściwości.|  
|`<Balloon`|`StartObject`węzeł`Balloon`|  
|`Color="Red"`|`StartMember`węzeł`Color`<br /><br /> `Value`węzeł ciągu wartości atrybutu`"Red"`<br /><br /> `EndMember`dla`Color`|  
|`HasHelium="True"`|`StartMember`węzeł`HasHelium`<br /><br /> `Value`węzeł ciągu wartości atrybutu`"True"`<br /><br /> `EndMember`dla`HasHelium`|  
|`>`|`EndObject`dla`Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`węzeł`NoiseMaker`<br /><br /> `StartMember`węzeł`_Initialization`<br /><br /> `Value`węzeł wartość ciągu inicjowania`"Loudest"`<br /><br /> `EndMember`węzeł`_Initialization`<br /><br /> `EndObject`dla`NoiseMaker`|  
||`EndMember`węzeł niejawne `FavorCollection` elementów właściwości.|  
||`EndObject`węzeł niejawne`FavorCollection`|  
|`</Party.Favors>`|`EndMember`dla`Favors`|  
|`</Party>`|`EndObject`dla`Party`|  
  
 W strumieniu węzłów XAML może polegać na następujące zachowanie:  
  
-   Jeśli `Namespace` węzeł istnieje, jest ona dodawana do strumienia bezpośrednio przed `StartObject` który zadeklarowana w przestrzeni nazw XAML z `xmlns`. Szukaj w poprzedniej tabeli z strumień węzłów XAML i przykładowe ponownie. Powiadomienie jak `StartObject` i `Namespace` węzły wydają się być niepotrzebnemu i ich położenia deklaracji w znacznikach tekstu. To jest reprezentatywna zachowania, gdzie węzły nazw zawsze były wyświetlane przed węzeł dotyczą one w strumieniu węzłów. Celem tego projektu jest czy informacji dotyczących przestrzeni nazw jest niezbędne do zapisywania obiektów i musi być znane, aby obiekt składnika zapisywania próby wykonania typu mapowania lub w inny sposób przetwarzania obiektu. Wprowadzenie do informacji dotyczących przestrzeni nazw XAML przed jego zakres aplikacji w strumieniu uproszczono zawsze przetworzyć strumieniu węzłów w jego przedstawioną kolejności.  
  
-   Z powodu powyżej brany pod uwagę jest co najmniej jeden `Namespace` węzłów, które można odczytać najpierw w większości przypadków rzeczywistych znaczników podczas przechodzących przez węzły od początku, nie `StartObject` głównego.  
  
-   A `StartObject` następuje węzła `StartMember`, `Value`, lub natychmiastowe `EndObject`. To nigdy a bezpośrednio przez inną `StartObject`.  
  
-   A `StartMember` może następować `StartObject`, `Value`, lub natychmiastowe `EndMember`. Może występować przez `GetObject`, dla członków, gdzie wartość powinien pochodzić z istniejącej wartości w obiekcie nadrzędnym zamiast `StartObject` który spowoduje utworzenie wystąpienia nową wartość. Może również wystąpić przez `Namespace` węzła, który ma zastosowanie do przyszłych `StartObject`. To nigdy a bezpośrednio przez inną `StartMember`.  
  
-   A `Value` reprezentuje węzeł samą wartość; nie istnieje żadne "wartość końcowa panelu". Może być stosowana tylko przez `EndMember`.  
  
    -   W strukturze wartość obiektu nie powoduje tekstu XAML inicjowania obiektu, ponieważ może być używany przez konstrukcji. Zamiast tego węzła dedykowanych elementu członkowskiego dla elementu członkowskiego o nazwie `_Initialization` jest tworzony. i ten węzeł elementu członkowskiego zawiera wartość ciągu inicjowania. Jeśli istnieje, `_Initialization` jest zawsze pierwszy `StartMember`. `_Initialization`może być kwalifikowany w niektórych reprezentacje usług XAML z namescope XAML języka XAML, wyjaśnienia, że `_Initialization` nie jest właściwością zdefiniowanych w tworzeniu kopii typów.  
  
    -   Kombinacja wartości elementu członkowskiego reprezentuje ustawienia wartości atrybutów. Po pewnym czasie prawdopodobnie konwerter wartości objętego przetwarzania tej wartości, a wartość to zwykły ciąg. Jednakże, który nie jest oceniany, aż do zapisywania obiektów XAML przetwarza strumień węzła. Moduł zapisywania obiektów XAML posiada niezbędne kontekst schematu XAML, mapowanie typu systemu i innych obsługi potrzebne do konwersji wartości.  
  
-   `EndMember` Następuje węzła `StartMember` węzła dla kolejnych elementów członkowskich lub przez `EndObject` węzła właściciela elementu członkowskiego.  
  
-   `EndObject` Następuje węzła `EndMember` węzła. Może również wystąpić przez `StartObject` węzła w przypadkach, w których obiekty są równorzędne w kolekcji elementów. Lub może występować przez `Namespace` węzła, który ma zastosowanie do przyszłych `StartObject`.  
  
    -   W przypadku unikatowy zamknięcie strumienia całego węzła `EndObject` z katalogu głównego nie następuje niczego; czytnik jest teraz końca pliku i <xref:System.Xaml.XamlReader.Read%2A> zwraca `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Konwertery wartości i strumień węzłów XAML  
 Konwerter wartości to ogólny termin dla rozszerzenia znacznika, konwertera typów (w tym serializatorów wartość) lub innej dedykowanych klasy, która jest raportowana jako konwertera wartości przez system typów języka XAML. W strumieniu węzłów XAML użycie konwertera typu i użycie rozszerzenia znaczników mają bardzo różne reprezentacje.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typu w strumieniu węzłów XAML  
 Atrybut ustawiony, że ostatecznie powoduje użycie konwertera typu jest zgłaszany w strumieniu węzłów XAML jako wartość elementu członkowskiego. Strumień węzłów XAML nie próbuje utworzyć wystąpienie obiektu konwertera typu i wartość należy przekazać do niego. Przy użyciu konwertera typów implementacji konwersja wymaga wywoływania kontekst schematu XAML i używa go dla mapowania typu. Nawet określanie, która klasa konwertera typu powinny być używane do przetwarzania wartość wymaga pośrednio kontekst schematu XAML. Gdy używany jest domyślny kontekst schematu XAML, te informacje są dostępne w systemie typów języka XAML. Jeśli potrzebujesz informacji o klasie konwertera typu na poziomie strumienia węzła XAML przed połączenia do modułu zapisującego XAML, możesz uzyskać je od <xref:System.Xaml.XamlMember> informacji jest zestaw elementów członkowskich. Ale w przeciwnym razie dane wejściowe konwertera typu powinna zostać zachowana w strumieniu węzłów XAML jako wartość zwykły aż do końca operacji, które wymagają systemu mapowania typów i kontekst schematu XAML są wykonywane, na przykład tworzenie obiektu przez XAML obiekt składnika zapisywania.  
  
 Na przykład należy wziąć pod uwagę następujące konspekt definicji klasy i użycie języka XAML go:  
  
```  
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
  
 Tekstowa reprezentacja strumień węzłów XAML dla tego użycia mogą być wyrażone w następujący sposób:  
  
 `StartObject`z <xref:System.Xaml.XamlType> reprezentujący`GameBoard`  
  
 `StartMember`z <xref:System.Xaml.XamlMember> reprezentujący`BoardSize`  
  
 `Value`węzeł, z ciągu tekstowego "`8x8`"  
  
 `EndMember`dopasowań`BoardSize`  
  
 `EndObject`dopasowań`GameBoard`  
  
 Zwróć uwagę, nie jest żadne wystąpienie konwertera typu strumienia tego węzła. Ale można uzyskać informacji o typie konwertera wywołując <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> dla `BoardSize`. Jeśli masz prawidłowy kontekst schematu XAML, można także wywoływać metody konwertera uzyskując wystąpienia z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w strumieniu węzłów XAML  
 Użycie rozszerzenia znaczników jest zgłaszane w strumieniu węzłów XAML jako obiekt węzła w ramach elementu członkowskiego, w którym obiekt reprezentuje wystąpienie rozszerzenia znaczników. W związku z tym użycie rozszerzenia znaczników jest podana więcej jawnie w reprezentacji strumienia węzłów niż użycie konwertera typu jest i zawiera więcej informacji. <xref:System.Xaml.XamlMember>informacji może nie mieć polecił niczego o rozszerzeniu znaczników ponieważ użycia jest oparty na analizie sytuacji i zmienia się w każdym przypadku możliwe znaczników; nie jest dedykowany i niejawne według typu lub elementu członkowskiego jak w przypadku konwertery typu.  
  
 Reprezentacja strumienia węzeł rozszerzenia znaczników jako węzły obiektu jest to możliwe nawet wtedy, gdy użycie rozszerzenia znaczników została wprowadzona w formie atrybutu tekstowego w kodzie XAML (która jest często wielkość liter). Użycia rozszerzenia znaczników, używane w postaci elementu jawne obiektu są traktowane tak samo.  
  
 W węźle obiektu rozszerzenia znaczników mogą być członkami tego rozszerzenia znacznika. Reprezentacja strumienia węzłów XAML zachowuje użycia tego rozszerzenia znacznika, czy to być użycia parametrów pozycyjnych lub użycia z jawne parametry nazwane.  
  
 W przypadku użycia parametrów pozycyjnych, strumień węzłów XAML zawiera właściwości zdefiniowane w języku XAML `_PositionalParameters` zawierające rekordy użycia. Ta właściwość jest rodzajowy <xref:System.Collections.Generic.List%601> z <xref:System.Object> ograniczenia. Ograniczenie jest obiektu i nie ciągu, ponieważ powrotne użycia parametrów pozycyjnych mogą zawierać użycia rozszerzenia znaczników zagnieżdżonych w niej. Dostęp do parametrów pozycyjnych z użycia, można wykonać iterację listy i użyj indeksatorów dla poszczególnych wartości.  
  
 Nazwany parametr użytkowania każdy nazwany parametr jest reprezentowany jako węzeł elementu członkowskiego o tej nazwie w strumieniu węzłów. Wartości elementów członkowskich niekoniecznie ciągów, ponieważ może być użycie rozszerzenia znaczników zagnieżdżonych.  
  
 `ProvideValue`z poziomu znacznika rozszerzenia nie jest jeszcze wywołana. Jednak jest wywoływana, jeśli Podłącz czytnik XAML i składnika zapisywania języka XAML, aby `WriteEndObject` jest wywoływana w węźle rozszerzenia znaczników, gdy należy zbadać w strumieniu węzłów. Z tego powodu konieczne są zwykle tym samym kontekście schematu XAML dostępne, ponieważ mają być używane w celu utworzenia wykresu obiektu na ścieżce obciążenia. W przeciwnym razie `ProvideValue` z żadnych znaczników rozszerzenia można zgłaszają wyjątki, w tym miejscu, ponieważ nie ma oczekiwanego dostępność usług.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML i XML język elementów członkowskich zdefiniowanych w strumieniu węzłów XAML  
 Niektóre elementy członkowskie są wprowadzane do strumień węzłów XAML z powodu interpretacje i konwencje czytnik XAML, zamiast za pośrednictwem jawnego <xref:System.Xaml.XamlMember> wyszukiwania lub konstrukcji. Te elementy członkowskie są często dyrektywy XAML. W niektórych przypadkach jest czynnością odczytywania XAML, przedstawiający dyrektywy do strumienia węzłów XAML. Innymi słowy, oryginalny tekst XAML wejściowy został explictly nie określać dyrektywę elementu członkowskiego, ale czytnik XAML wstawia dyrektywy w celu spełnienia strukturalnych XAML Konwencji i przekazuje informacje w strumieniu węzłów XAML, aby te informacje zostaną utracone.  
  
 Poniższe uwagi listy wszystkich przypadkach, których można oczekiwać czytnik XAML wprowadzenie dyrektywy węzeł elementu członkowskiego XAML i jak ten węzeł elementu członkowskiego jest identyfikowane we wdrożeniach usług .NET Framework XAML.  
  
-   **Tekst inicjowania dla obiekt węzła:** jest nazwa węzła tego elementu członkowskiego `_Initialization`reprezentuje dyrektywy XAML i jest on zdefiniowany w przestrzeni nazw XAML języka XAML. Statyczne jednostki można uzyskać z poziomu <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Parametry pozycyjne dla rozszerzenia znacznika:** nazwa tego węzła elementu członkowskiego jest `_PositionalParameters`, i jest on zdefiniowany w przestrzeni nazw XAML języka XAML. Zawsze zawiera ogólne listę obiektów, z których każdy jest parametrów pozycyjnych wstępnie oddzielone dzielenie na `,` znak ogranicznika zgodnie z podanym w danych wejściowych XAML. Możesz też uzyskać statycznych jednostki dyrektywy parametrów pozycyjnych z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Nieznany zawartości:** jest nazwa węzła tego elementu członkowskiego `_UnknownContent`. Mówiąc ściślej, jest <xref:System.Xaml.XamlDirective>, i jest on zdefiniowany w przestrzeni nazw XAML języka XAML. Ta dyrektywa jest używana jako wskaźnikowych w przypadkach, gdy XAML object element zawiera zawartość w źródle XAML, ale można ustalić ma właściwości zawartości w obszarze obecnie kontekst schematu XAML. Ten przypadek może wykryć w strumień węzłów XAML, sprawdzając dla elementów członkowskich o nazwie `_UnknownContent`. Jeśli nie podjęto żadnych innych akcji w obciążenia ścieżki strumień węzłów XAML, wartość domyślna <xref:System.Xaml.XamlObjectWriter> zgłoszenie próba `WriteEndObject` po napotkaniu `_UnknownContent` Członkowskie dowolnego obiektu. Wartość domyślna <xref:System.Xaml.XamlXmlWriter> nie zgłasza i traktuje jako niejawne elementu członkowskiego. Możesz uzyskać statycznych jednostki dla `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Właściwości kolekcji kolekcji:**chociaż zapasowy typ CLR kolekcji klasy, która jest zwykle używany dla XAML zawiera dedykowany nazwane właściwości, która przechowuje elementy kolekcji, tej właściwości jest nieznany system typów języka XAML, przed wykonaniem kopii typu rozdzielczość. Zamiast tego strumień węzłów XAML wprowadzono `Items` symbol zastępczy jest członkiem kolekcji typu XAML. W implementacji usług .NET Framework XAML nazwę tej dyrektywy / element członkowski w strumieniu węzłów jest `_Items`. Stała dla tej dyrektywy można uzyskać z <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     Należy pamiętać, że strumień węzłów XAML może zawierać właściwości elementów z elementów, które stają się nie być parseable na podstawie rozpoznawania typu zapasowy i kontekst schematu XAML. Na przykład  
  
-   **Elementy członkowskie zdefiniowane XML:** zdefiniowane XML `xml:base`, `xml:lang` i `xml:space` elementy członkowskie są raportowane klientowi jako XAML dyrektywy o nazwie `base`, `lang`, i `space` w usług .NET Framework XAML implementacje. Przestrzeń nazw dla tych jest przestrzeń nazw XML `http://www.w3.org/XML/1998/namespace`. Stałe dla każdego z nich można uzyskać z <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Kolejność węzłów  
 W niektórych przypadkach <xref:System.Xaml.XamlXmlReader> zmienia kolejność węzłów XAML w strumieniu węzłów XAML, a kolejność węzły wyświetlane w znaczniku lub przetwarzane w formacie XML. Jest to realizowane aby uporządkowane węzły tak, aby <xref:System.Xaml.XamlObjectWriter> może przetwarzać strumieniu węzłów w sposób tylko do przodu.  W programie .NET Framework XAML Services czytnika XAML zmienia kolejność węzłów zamiast pozostawiając to zadanie optymalizacji wydajności dla XAML obiektu składnika zapisywania konsumentów strumienia węzła twórcę XAML.  
  
 Niektórych dyrektyw są przeznaczone specjalnie, o podanie dodatkowych informacji w celu utworzenia obiektu z elementu object. Te dyrektywy: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Czytniki .NET Framework XAML Services XAML próbować umieścić te dyrektywy jako pierwszy elementów członkowskich w strumieniu węzłów następującego obiektu `StartObject`, przyczyn, które opisano szczegółowo w następnej sekcji.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>Zachowanie XamlObjectWriter i kolejność węzłów  
 `StartObject`Aby <xref:System.Xaml.XamlObjectWriter> niekoniecznie sygnał do zapisywania obiektów XAML od razu utworzyć wystąpienie obiektu. XAML zawiera kilka funkcji języka, które umożliwiają można zainicjować obiektu przy użyciu dodatkowych danych wejściowych, a nie polegać wyłącznie na wywołania konstruktora domyślnego do tworzenia obiektu początkowej i następnie ustawienie właściwości. Te funkcje obejmują: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; inicjowania tekstu. [x: typearguments —](../../../docs/framework/xaml-services/x-typearguments-directive.md); pozycyjnych Parametry rozszerzenia znacznika; metodami factory i skojarzone [x: Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) węzłów (XAML 2009). Każdy z tych przypadkach opóźnienie konstruowania rzeczywistego obiektu, a ponieważ ponownie sortowane strumień węzłów XAML zapisywania obiektu może polegać na zachowanie faktycznie konstruowanie wystąpienie napotkaniu członka start, które nie jest specjalnie konstrukcji dyrektywa dla tego typu obiektu.  
  
### <a name="getobject"></a>GetObject  
 `GetObject`reprezentuje węzeł XAML, gdzie zamiast tworzenia nowego obiektu, Edytor obiektu XAML powinien zamiast tego Pobierz wartość obiektu zawierającego. Typowy przypadek gdzie `GetObject` napotkano węzła do węzła XAML strumień jest dla obiektu kolekcji lub słownika, gdy zawierająca go właściwość jest celowo tylko do odczytu w modelu obiektu zapasowego typu. W tym scenariuszu kolekcji lub słownika często jest tworzony i inicjowany (zazwyczaj puste) przez logikę inicjowania typu będący właścicielem.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xaml.XamlObjectReader>  
 [Usługi XAML](../../../docs/framework/xaml-services/index.md)  
 [Przestrzeń nazw XAML](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
