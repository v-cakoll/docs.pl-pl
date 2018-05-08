---
title: Niezależność od języka i elementy niezależne od języka
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf18fb7238eb35b5ceb1624c14b83486485ddc1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka
.NET Framework jest niezależny od języka. Oznacza to, że deweloper, można tworzyć w jednym z wielu języków, które odnoszą się do programu .NET Framework, takich jak C#, C + +/ CLI, Eiffel F #, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL i środowiska Windows PowerShell. Dostępne typy i składniki bibliotek klas utworzonych dla programu .NET Framework, bez konieczności znajomości języka, w której zostały pierwotnie zapisany i bez konieczności postępuj zgodnie z oryginalnego języka Konwencji. Jeśli jesteś deweloperem składnika składnika jest dostępna przez dowolną aplikację .NET Framework, niezależnie od języka.  
  
> [!NOTE]
>  To pierwsza część w tym artykule omówiono tworzenie niezależny od języka składników — czyli składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikacji z kodu źródłowego w wielu językach; zobacz [współdziałanie między językami](#CrossLang) w drugiej części tego artykułu.  
  
 Pełni interakcję z innymi obiektami w dowolnym języku, obiektów musi ujawniać dotyczące obiektów wywołujących te funkcje, które są wspólne dla wszystkich języków. Ten zestaw typowych funkcji jest zdefiniowany przez wspólnej specyfikacji języka (CLS), który jest zestaw reguł stosowanych do zestawów wygenerowanych. Specyfikacja języka wspólnego jest zdefiniowany w partycji I klauzule 7 do 11 [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Jeśli składnik spełnia specyfikacja języka wspólnego, może być zgodne ze specyfikacją CLS i są dostępne z kodu w zestawach napisane w języku programowania, który obsługuje ze specyfikacją CLS. Można określić, czy składnik jest zgodny ze specyfikacja języka wspólnego w czasie kompilacji, stosując <xref:System.CLSCompliantAttribute> atrybutu do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute).  
  
 W tym artykule:  
  
-   [Zasady zgodności ze specyfikacją CLS](#Rules)  
  
    -   [Typy i podpisy elementów członkowskich typu](#Types)  
  
    -   [Konwencje nazewnictwa](#naming)  
  
    -   [Konwersja typów](#conversion)  
  
    -   [Tablice](#arrays)  
  
    -   [Interfejsy](#Interfaces)  
  
    -   [Wyliczenia](#enums)  
  
    -   [Ogólnie rzecz biorąc wpisz elementy członkowskie](#members)  
  
    -   [Dostępność elementu członkowskiego](#MemberAccess)  
  
    -   [Typy ogólne i elementów członkowskich](#Generics)  
  
    -   [Konstruktory](#ctors)  
  
    -   [Właściwości](#properties)  
  
    -   [Zdarzenia](#events)  
  
    -   [Overloads](#overloads)  
  
    -   [Wyjątki](#exceptions)  
  
    -   [Atrybuty](#attributes)  
  
-   [Atrybut CLSCompliant](#CLSAttribute)  
  
-   [Współdziałanie między językami](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>Zasady zgodności ze specyfikacją CLS  
 W tej sekcji omówiono reguł do tworzenia składnika zgodne ze specyfikacją CLS. Pełną listę zasad, zobacz partycji I 11 klauzuli [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
> [!NOTE]
>  Specyfikacja języka wspólnego omówiono każdej reguły zgodności ze specyfikacją CLS, zastosowanie w przypadku użytkowników (deweloperów, którzy są uzyskiwania dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperów, którzy korzystają z kompilatora języka Aby utworzyć CLS-compliant biblioteki) i rozszerzeń (deweloperów, którzy tworzą narzędzia, takiego jak kompilatora języka lub analizator kodu tworzącego składniki zgodne ze specyfikacją CLS). Ten artykuł dotyczy reguł odnoszących się do struktur. Należy pamiętać, że niektóre reguły, które dotyczą Extender mogą również dotyczyć zestawy, które są tworzone przy użyciu Reflection.Emit.  
  
 Projektowanie składnik, który jest niezależny od języka, wystarczy dotyczą zasady zgodności ze specyfikacją CLS interfejs publiczny danego składnika. Prywatnej implementacji nie ma być zgodny ze specyfikacją.  
  
> [!IMPORTANT]
>  Zasady zgodności ze specyfikacją CLS dotyczą tylko interfejs publiczny składnika, nie można jej prywatna implementacja.  
  
 Na przykład innych niż podpisane liczby całkowite <xref:System.Byte> nie są zgodne ze specyfikacją CLS. Ponieważ `Person` udostępnia klasy w poniższym przykładzie `Age` właściwość typu <xref:System.UInt16>, poniższy kod wyświetla ostrzeżenie kompilatora.  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 Możesz wprowadzić `Person` klasy zgodne ze specyfikacją CLS, zmieniając typ `Age` właściwość z <xref:System.UInt16> do <xref:System.Int16>, który jest zgodny ze specyfikacją CLS, 16-bitową liczbę całkowitą ze znakiem. Nie trzeba zmienić typ prywatna `personAge` pola.  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 Interfejs publiczny biblioteki składa się z następujących czynności:  
  
-   Definicje klas publicznych.  
  
-   Definicje publiczne elementy członkowskie publicznych klas i definicje członków dostępne dla klas pochodnych (elementy chronione).  
  
-   Parametry i zwracane typy metod publicznych klas publicznych i parametrów i zwracanych typów metod dostępne dla klas pochodnych.  
  
 W poniższej tabeli wymieniono zasady zgodności ze specyfikacją CLS. Tekst reguły jest zajęta dosłownego wyrażenia z [ECMA-335 standardowe: wspólną infrastrukturę języka](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 międzynarodowej Ecma. W poniższych sekcjach znajduje się bardziej szczegółowe informacje o tych reguł.  
  
|Kategoria|Zobacz|Reguła|Numer reguły|  
|--------------|---------|----------|-----------------|  
|Ułatwienia dostępu|[Dostępność elementu członkowskiego](#MemberAccess)|Ułatwienia dostępu nie zmienia się w przypadku zastępowanie dziedziczonych metod, z wyjątkiem podczas przesłaniania metody dziedziczone z innego zestawu z ułatwieniami dostępu `family-or-assembly`. W takim przypadku zastąpienie ma ułatwień dostępu `family`.|10|  
|Ułatwienia dostępu|[Dostępność elementu członkowskiego](#MemberAccess)|Widoczność i dostępności typów i członków się typy w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny. Na przykład metodę publiczną, która jest widoczny spoza jej zestawu nie ma argument o typie jest widoczna tylko w zestawie. Widoczność i dostępności typów tworzenia wystąpień typu ogólnego używane w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny. Na przykład wystąpień typu ogólnego w podpisie elementu członkowskiego, który jest widoczny spoza jej zestawu nie posiada argumentów ogólnych, którego typ jest widoczna tylko w zestawie.|12|  
|Tablice|[Tablice](#arrays)|Tablice mają elementy o typie zgodnym ze specyfikacją CLS, oraz wszystkie wymiary tablicy posiada dolne granice tablicy o wartości zero. Fakt, że element jest tablicą i typ elementu tablicy wymaga aby odróżnić przeciążenia. Gdy przeładowanie opiera się na dwóch lub więcej tablicy typów typów elementów są nazw typów.|16|  
|Atrybuty|[Atrybuty](#attributes)|Atrybuty powinny być typu <xref:System.Attribute?displayProperty=nameWithType>, lub dziedziczenie z tego typu.|41|  
|Atrybuty|[Atrybuty](#attributes)|Ze specyfikacją CLS umożliwia tylko podzbiór kodowania atrybutów niestandardowych. Są tylko typy, które pojawia się w tych kodowania (patrz partycji IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , i dowolnego typu wyliczenie oparte na zgodne ze specyfikacją CLS typu podstawowego liczby całkowitej.|34|  
|Atrybuty|[Atrybuty](#attributes)|Ze specyfikacją CLS nie zezwala na Modyfikatory wymagane widocznego publicznie (`modreq`, zobacz II partycji), ale zezwala na Modyfikatory opcjonalne (`modopt`, zobacz II partycji) nie rozpoznaje.|35|  
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektu są wywołać niektórych konstruktora wystąpienia klasy podstawowej przed wystąpieniem dostęp do danych odziedziczone wystąpienie. (To nie dotyczą typów wartości, które nie muszą mieć konstruktorów.)|21|  
|Konstruktorów|[Konstruktory](#ctors)|Nie jest wymagany Konstruktor obiektów z wyjątkiem w ramach tworzenia obiektu, a jest nie można zainicjować obiektu dwa razy.|22|  
|Wyliczenia|[Wyliczenia](#enums)|Podstawowy typ wyliczeniowy powinien być typem wbudowanym liczby całkowitej ze specyfikacją CLS, nazwy pola są "value__" i to pole jest oznaczone jako `RTSpecialName`.|7|  
|Wyliczenia|[Wyliczenia](#enums)|Istnieją dwa różne rodzaje wyliczenia wskazywanym przez obecności lub braku <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu niestandardowego (zobacz Biblioteka IV partycji). Reprezentuje jedną o nazwie liczby całkowite; inne reprezentuje nazwę flagi bitów, które można łączyć do generowania wartości bez nazwy. Wartość `enum` nie jest ograniczony do określonej wartości.|8|  
|Wyliczenia|[Wyliczenia](#enums)|Literał pola statyczne typu wyliczeniowego ma typ wyliczenia samej siebie.|9|  
|Zdarzenia|[Zdarzenia](#events)|Metody, które implementują zdarzenia są oznaczane `SpecialName` w themetadata.|29|  
|Zdarzenia|[Zdarzenia](#events)|Dostępność zdarzenia i jego metody dostępu muszą być identyczne.|30|  
|Zdarzenia|[Zdarzenia](#events)|`add` i `remove` metody dla zdarzenia są oba albo być obecny lub nieobecny.|31|  
|Zdarzenia|[Zdarzenia](#events)|`add` i `remove` metody zdarzenia przyjmują jeden parametr o typie definiuje typ zdarzenia i która pochodzi z <xref:System.Delegate?displayProperty=nameWithType>.|32|  
|Zdarzenia|[Zdarzenia](#events)|Zdarzenia będzie stosować się do określonego wzorca nazewnictwa. `SpecialName` Atrybut określone w regule ze specyfikacją CLS 29 nie będą uwzględniane w porównania odpowiednią nazwę i będzie stosować się do identyfikatora reguły.|33|  
|Wyjątki|[Wyjątki](#exceptions)|Obiekty, które są generowane jest typu <xref:System.Exception?displayProperty=nameWithType> lub dziedziczenie z tego typu. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.|40|  
|Ogólne|[Zgodności ze specyfikacją CLS: zasady](#Rules)|Reguły ze specyfikacją CLS mają zastosowanie tylko do tych elementów typu, które są dostępne lub widoczne outsideof zestawu definiującego.|1|  
|Ogólne|[Zgodności ze specyfikacją CLS: zasady](#Rules)|Elementy członkowskie typów zgodnych ze specyfikacją CLS nie jest oznaczony zgodne ze specyfikacją CLS.|2|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Typy zagnieżdżone mają co najmniej tyle parametry ogólne, jak typ otaczający. Parametry ogólne w typu zagnieżdżonego odpowiada za pomocą pozycji do parametrów ogólnych w jego typie otaczającym.|42|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Nazwa typu ogólnego jest zakodowania liczba parametrów typu dla typu niezagnieżdżonego lub nowo wprowadzonych do typu, jeśli zagnieżdżony, zgodnie z regułami zdefiniowanych powyżej.|43|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Typ ogólny jest ponownie zadeklarować ograniczenia wystarczające, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsy będzie spełniony przez ograniczeń typu ogólnego.|4444|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Typy używane jako ograniczenia dotyczące parametrów ogólnych są się zgodne ze specyfikacją CLS.|45|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Widoczność i dostępności elementów członkowskich (w tym typy zagnieżdżone) w ogólnym typem skonkretyzowanym uznaje się ograniczyć zakres konkretnego wystąpienia zamiast deklaracji typu ogólnego jako całość. Zakładając, że to, widoczność i dostępności reguły ze specyfikacją CLS 12 nadal zastosowanie zasady.|46|  
|Typy ogólne|[Typy ogólne i elementów członkowskich](#Generics)|Dla każdej metodzie abstrakcyjnej ani wirtualnej ogólny jest domyślną konkretną implementację (nieabstrakcyjnej).|47|  
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji compliantmethods niezgodny ze specyfikacją CLS w celu ich wdrożenia.|18|  
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie określają metody statyczne nie są one Definiowanie pól.|19|  
|Elementy członkowskie|[Ogólnie rzecz biorąc wpisz elementy członkowskie](#members)|Globalne pola statyczne i metod nie są zgodne ze specyfikacją CLS.|36|  
|Elementy członkowskie|--|Przy użyciu metadanych inicjowania pola określona jest wartość literału statycznego. Literał zgodne ze specyfikacją CLS muszą mieć określoną wartość w polu inicjowania metadanych, które jest taki sam typ, jak literał (lub podstawowego typu, jeśli ten literał `enum`).|13|  
|Elementy członkowskie|[Ogólnie rzecz biorąc wpisz elementy członkowskie](#members)|Ograniczenie vararg nie jest częścią ze specyfikacją CLS, a tylko Konwencja wywoływania obsługiwane przez ze specyfikacją CLS jest standardowego zarządzanych konwencję wywołania.|15|  
|Konwencje nazewnictwa|[Konwencje nazewnictwa](#naming)|Zestawy zachowuje załącznika 7 z techniczne raportu 15 Unicode Standard3.0 regulujące zestaw znaków mogą uruchomić i uwzględniane w identyfikatorach, dostępne onlineat http://www.unicode.org/unicode/reports/tr15/tr15-18.html. Identyfikatory powinien być w formacie thecanonical zdefiniowane przez Unicode normalizacji formularza C. Do celów ze specyfikacją CLS, identifiersare dwa takie same, jeśli ich mapowania małe litery (określone mapowania toonelowercase jednego z ustawień regionalnych niewrażliwe, Unicode) są takie same. Oznacza to, że dla dwóch identyfikatorów wziąć pod uwagę differentunder ze specyfikacją CLS są różnią się tylko w ich przypadku. Jednak aby można było zastąpić aninherited definicji interfejsu wiersza polecenia wymaga dokładne kodowanie oryginalnej deklaracji.|4|  
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Nazwy wszystkich wprowadzonych w zakresie zgodne ze specyfikacją CLS są różne ofkind niezależne, z wyjątkiem przypadków, w których nazwy są identyczne i rozwiązane za pomocą przeciążenia. Oznacza to, że podczas CTSallows jednego typu, aby użyć takiej samej nazwy metody i pole ze specyfikacją CLS nie.|5|  
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Pola i typy zagnieżdżone powinna różnić się przez porównanie identyfikator samodzielnie, eventhough CTS pozwala odrębnych podpisów rozróżnienie. Metody, właściwości i eventsthat mają takie same nazwy (porównanie identyfikator) może różnić się nie tylko typem zwracanym, z wyjątkiem zgodnie ze specyfikacją CLS 39 reguły.|6|  
|Przeciążenie|[Overloads](#overloads)|Tylko właściwości i metody może być przeciążony.|37|  
|Przeciążenie|[Overloads](#overloads)|Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów ich parametrów, z wyjątkiem operatory konwersji o nazwie `op_Implicit` i `op_Explicit`, które również można przeciążać na podstawie ich zwracanego typu.|38|  
|Przeciążenie|--|Jeśli co najmniej dwie metody zgodne ze specyfikacją CLS zadeklarowana w typie ma tego samego nameand, do określonych wystąpień typu mają ten sam parametr i typy zwracane, thenall tych metod jest semantycznie równoważne w tych wystąpień typu.|48|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|<xref:System.Object?displayProperty=nameWithType> jest zgodny ze specyfikacją CLS. Inne klasy zgodne ze specyfikacją CLS są dziedziczy z klasy, zgodne ze specyfikacją CLS.|23|  
|Właściwości|[Właściwości](#properties)|Metody, które implementują metody pobierającej i ustawiającej shallbe właściwości oznaczone `SpecialName` w metadanych.|24|  
|Właściwości|[Właściwości](#properties)|Metody dostępu właściwości zostaje być wszystkie statyczne, wszystkie wirtualne lub wszystkie można instancji.|26|  
|Właściwości|[Właściwości](#properties)|Typ właściwości jest zwracany typ metody pobierającej i typ ostatni argument metody ustawiającej. Typy parametrów właściwości są typy parametrów metody pobierającej i wszystkie typy, ale ostatni parametr metody ustawiającej. Wszystkie te typy są zgodne ze specyfikacją CLS, a nie są zarządzane wskaźników (tj. nie mogą być przekazywane przez odwołanie).|27|  
|Właściwości|[Właściwości](#properties)|Właściwości będzie stosować się do określonego wzorca nazewnictwa. `SpecialName` Atrybut określone w regule ze specyfikacją CLS 24 nie będą uwzględniane w porównania odpowiednią nazwę i będzie stosować się do identyfikatora reguły. Właściwość ma metodę metody pobierającej i/lub metody ustawiającej.|28|  
|Konwersja typów|[Konwersja typów](#conversion)|Jeśli dowolny `op_Implicit` lub `op_Explicit` została podana, należy zapewnić alternatywne metody udostępniania wymuszenia.|39|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Spakowane typy wartości nie są zgodne ze specyfikacją CLS.|3|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Wszystkie typy w podpis jest zgodne ze specyfikacją CLS. Wszystkie typy tworzenia wystąpień typu ogólnego jest zgodne ze specyfikacją CLS.|11|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Odwołania do typu nie są zgodne ze specyfikacją CLS.|14|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS.|17|  
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają wykonania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS.|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu  
 <xref:System.Object?displayProperty=nameWithType> Typ jest zgodny ze specyfikacją CLS i jest podstawowym typem wszystkie typy obiektów w systemie typów .NET Framework. Dziedziczenia w programie .NET Framework jest albo niejawne (na przykład <xref:System.String> klasy niejawnie dziedziczy <xref:System.Object> klasy) bezpośredniego lub pośredniego (na przykład <xref:System.Globalization.CultureNotFoundException> jawnie dziedziczy klasa <xref:System.ArgumentException> klasy, która jawnie dziedziczy <xref:System.SystemException> klasy, która dziedziczy po jawnie <xref:System.Exception> klasy). Typ pochodny być zgodne ze specyfikacją CLS jego typ podstawowy również musi być zgodne ze specyfikacją CLS.  
  
 W poniższym przykładzie przedstawiono typem pochodnym, którego typ podstawowy nie jest zgodne ze specyfikacją CLS. Definiuje podstawowej `Counter` klasy, która używa jako licznik całkowitą bez znaku 32-bitowych. Ponieważ ta klasa dostarcza funkcje licznika zawijania całkowitą bez znaku, klasa jest oznaczona jako niezgodne-ze specyfikacją CLS. W rezultacie Klasa pochodna `NonZeroCounter`, również jest niezgodny ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 Wszystkie typy, które pojawiają się w podpisach elementu członkowskiego, w tym zwracany typ metody lub typ właściwości musi być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:  
  
-   Wszystkie typy, które tworzą ogólnego typu musi być zgodne ze specyfikacją CLS.  
  
-   Wszystkie typy używane jako ograniczenia dotyczące parametrów ogólnych musi być zgodne ze specyfikacją CLS.  
  
 .NET Framework [wspólny system typów](../../docs/standard/base-types/common-type-system.md) zawiera kilka wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i specjalnie są zakodowane w metadanych zestawu. Te typy wewnętrzne typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.  
  
|Typie zgodnym ze specyfikacją CLS|Opis|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8-bitową liczbę całkowitą bez znaku|  
|<xref:System.Int16>|16-bitową liczbę całkowitą ze znakiem|  
|<xref:System.Int32>|32-bitowej liczby całkowitej ze znakiem|  
|<xref:System.Int64>|64-bitowej liczby całkowitej ze znakiem|  
|<xref:System.Single>|Wartość zmiennoprzecinkową o pojedynczej dokładności|  
|<xref:System.Double>|Wartość zmiennoprzecinkową podwójnej precyzji|  
|<xref:System.Boolean>|`true` lub `false` typu wartości|  
|<xref:System.Char>|Jednostka zakodowanego kodu UTF-16|  
|<xref:System.Decimal>|Liczba dziesiętna non--zmiennoprzecinkowych|  
|<xref:System.IntPtr>|Wskaźnika lub dojścia o rozmiarze określone platformy|  
|<xref:System.String>|Kolekcja zero, co najmniej jeden <xref:System.Char> obiektów|  
  
 Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.  
  
|Niezgodny typ|Opis|Alternatywnym, zgodnym ze specyfikacją CLS|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|Typ danych 8-bitową liczbę całkowitą ze znakiem|<xref:System.Int16>|  
|<xref:System.TypedReference>|Wskaźnik do obiektu i jego typ środowiska uruchomieniowego|Brak|  
|<xref:System.UInt16>|16-bitową liczbę całkowitą bez znaku|<xref:System.Int32>|  
|<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku|<xref:System.Int64>|  
|<xref:System.UInt64>|64-bitowej liczby całkowitej bez znaku|<xref:System.Int64> (może przepełnienie), <xref:System.Numerics.BigInteger>, lub <xref:System.Double>|  
|<xref:System.UIntPtr>|Niepodpisane wskaźnika lub dojścia|<xref:System.IntPtr>|  
  
 Biblioteka klas programu .NET Framework lub inne biblioteki klas może zawierać innych typów, które nie są zgodne z CLS; na przykład:  
  
-   Spakowanymi typami wartości. W poniższym przykładzie C# tworzy klasę, która ma właściwości publicznej typu `int*` o nazwie `Value`. Ponieważ `int*` jest opakowanym typem wartościowym, kompilator flagi go jako niezgodne-ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
-   Odwołania typu, które są specjalne konstrukcje, które zawierają odwołania do obiektu i odwołania do typu. Odwołania do typu są wyświetlane w programie .NET Framework według <xref:System.TypedReference> klasy.  
  
 Jeśli typ nie jest zgodne ze specyfikacją CLS, należy zastosować <xref:System.CLSCompliantAttribute> atrybutem `isCompliant` wartość `false` do niego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute) sekcji.  
  
 Poniższy przykład przedstawia problem zgodności ze specyfikacją CLS w podpisie metody i podczas tworzenia wystąpienia typu ogólnego. Definiuje `InvoiceItem` z właściwością typu <xref:System.UInt32>, właściwość typu `Nullable(Of UInt32)`ani konstruktora z parametrami typu <xref:System.UInt32> i `Nullable(Of UInt32)`. Otrzymasz cztery ostrzeżeń kompilatora podczas kompilowania w tym przykładzie.  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 Aby wyeliminować ostrzeżeń kompilatora, Zastąp ze specyfikacją CLS-niezgodnych typów w `InvoiceItem` interfejs publiczny z typów zgodnych:  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 Oprócz folderów dla określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Obejmują one typy niezarządzanych wskaźników i typów wskaźnika funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej w celu utworzenia tablicy liczb całkowitych.  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 Klasy abstrakcyjne dla zgodne ze specyfikacją CLS (czyli oznaczenie klasy `abstract` w języku C# lub jako `MustInherit` w języku Visual Basic), wszystkie elementy członkowskie klasy również musi być zgodne ze specyfikacją CLS.  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>Konwencje nazewnictwa  
 Ponieważ niektóre języki programowania jest rozróżniana wielkość liter, identyfikatory (takich jak nazwy przestrzeni nazw, typy i składniki) musi się różnić tylko wielkością liter. Dwa identyfikatory są traktowane jako równoważne, jeśli ich małe mapowania są takie same. W poniższym przykładzie C# definiuje dwie klasy publicznej, `Person` i `person`. Ponieważ różnią się tylko wielkością liter, kompilator języka C# flagi je jako nie zgodne z CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 Programowanie identyfikatorów języka, takich jak nazwy przestrzeni nazw, typów i członków, musi być zgodna z [Unicode Standard 3.0, techniczne 15 raportu, załącznik 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:  
  
-   Pierwszy znak identyfikatora mogą być dowolnej Unicode wielkie litery, małe litery, tytuł wielkość list, litera modyfikatora, innego litery lub list numer. Aby uzyskać informacje na kategorie znaków Unicode, zobacz <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> wyliczenia.  
  
-   Kolejne znaki mogą pochodzić z jednej z kategorii jako pierwszy znak i mogą również obejmować znaczniki bez spacji, odstępy łączenie znaki, liczby dziesiętne, łączące znaki interpunkcyjne i kody formatowania.  
  
 Przed porównywania identyfikatorów, należy odfiltrować kody formatowania i dokonać konwersji identyfikatory C formularza normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu algorytmem UTF-16. Sekwencje znaków, które powodują powstanie tej samej jednostki kodu w języku C formularza normalizacji Unicode nie są zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano właściwość o nazwie `Å`, który składa się z znaku ANGSTROM znak (U + 212B) i drugi właściwość o nazwie `Å`, który składa się z znak LATIN litera A z PIERŚCIEŃ powyżej (U + 00 C 5). C# i Visual Basic kompilatory Flaga kodu źródłowego jako niezgodne-ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 Nazwy elementów członkowskich z określonego zakresu (na przykład przestrzeni nazw w zestawie, typy w przestrzeni nazw lub elementy członkowskie w określonym typie) musi być unikatowa, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia. To wymaganie jest bardziej rygorystyczne niż wspólny system typów, dzięki czemu wiele elementów członkowskich w zakresie mają identyczne nazwy tak długo, jak są one różne rodzaje elementów członkowskich (na przykład, jeden to metoda i jedna jest polem). W szczególności dla elementów członkowskich typu:  
  
-   Pola i typy zagnieżdżone są rozróżnianych na podstawie samej nazwy.  
  
-   Metody, właściwości i zdarzenia, które mają taką samą nazwę musi się różnić się bardziej niż tylko typem zwracanym.  
  
 Poniższy przykład przedstawia wymaganie, że nazwy składników muszą być unikatowe w ich zakresie. Definiuje klasę o nazwie `Converter` który obejmuje cztery elementy członkowskie o nazwie `Conversion`. Są trzy metody, a jeden z nich jest właściwością. Metoda, która obejmuje <xref:System.Int64> parametru jest unikatowo o nazwie, ale te dwie metody z <xref:System.Int32> parametru są, ponieważ wartość zwrotna nie jest uznawany za część podpisu elementu członkowskiego. `Conversion` Właściwość również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążonej metody.  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 Poszczególne języki unikatowych słów kluczowych, więc języków przeznaczonych środowisko uruchomieniowe języka wspólnego należy również podać mechanizmu dla odwołania do identyfikatorów (na przykład wpisz nazwy), które pokrywają się z słów kluczowych. Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak w poniższym przykładzie w języku Visual Basic jest w stanie odróżnić klasę o nazwie `case` z `case` — słowo kluczowe przy użyciu otwierające i zamykające nawiasy klamrowe. W przeciwnym razie przykładzie tworzy komunikat o błędzie, "— słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można skompilować.  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 W poniższym przykładzie C# jest w stanie utworzyć wystąpienia `case` przy użyciu `@` symbol do odróżniania identyfikator ze słowem kluczowym języka. Bez tego kompilatora C# będzie wyświetlane dwa komunikaty o błędach, "Oczekiwano typu" i "nieprawidłowe wyrażenie termin"case"."  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>Konwersja typów  
 Specyfikacja języka wspólnego definiuje dwa operatory konwersji:  
  
-   `op_Implicit`, używany dla rozszerzanie konwersji, które nie powodują utratę danych lub dokładności. Na przykład <xref:System.Decimal> struktura zawiera przeciążone `op_Implicit` operator do konwersji wartości typów całkowitych i <xref:System.Char> wartości do <xref:System.Decimal> wartości.  
  
-   `op_Explicit`, używany dla zawężanie konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub dokładności. Na przykład <xref:System.Decimal> struktura zawiera przeciążone `op_Explicit` operatora, aby przekonwertować <xref:System.Double> i <xref:System.Single> wartości do <xref:System.Decimal> i konwertowania <xref:System.Decimal> wartości całkowitych wartości <xref:System.Double>, <xref:System.Single>, i <xref:System.Char>.  
  
 Jednak nie obsługuje wszystkich języków przeładowania operatora lub definicję operatorów niestandardowych. Jeśli wybierzesz do wdrożenia tych operatorów konwersji, musisz także podać innym sposobem wykonania konwersji. Firma Microsoft zaleca, aby podać `From` *Xxx* i `To` *Xxx* metody.  
  
 W poniższym przykładzie zdefiniowano zgodne ze specyfikacją CLS Konwersje jawne i niejawne. Tworzy `UDouble` klasa, która reprezentuje numer podpisem podwójnej precyzji, zmiennoprzecinkowych. Zapewnia niejawną konwersję z `UDouble` do <xref:System.Double> i jawne konwersje z `UDouble` do <xref:System.Single>, <xref:System.Double> do `UDouble`, i <xref:System.Single> do `UDouble`. Definiuje również `ToDouble` metody zamiast operatora niejawnej konwersji i `ToSingle`, `FromDouble`, i `FromSingle` metod jako alternatywy dla operatory jawnej konwersji.  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>Tablice  
 Tablice zgodne ze specyfikacją CLS spełniać następujące reguły:  
  
-   Wszystkie wymiary tablicy muszą mieć dolna granica zero. Poniższy przykład tworzy specyfikacją CLS tablicy z dolną granicą jednego. Należy zauważyć, że mimo występowania <xref:System.CLSCompliantAttribute> atrybutu, kompilator nie wykrywa czy tablica zwrócona przez `Numbers.GetTenPrimes` metody nie jest zgodne ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
-   Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody zwracające tablice niezgodnym-ze specyfikacją CLS. Pierwszy zwraca tablicę <xref:System.UInt32> wartości. Zwraca drugie <xref:System.Object> tablicy, która obejmuje <xref:System.Int32> i <xref:System.UInt32> wartości. Mimo że kompilator identyfikuje pierwszy tablicy jako niezgodne z powodu jego <xref:System.UInt32> typu, nie rozpoznaje, że druga tablica zawiera elementy niezgodnym-ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
-   Rozpoznanie przeciążenia dla metod, które mają tablicy parametrów jest opiera się na fakt, że są one tablicami i na ich typ elementu. Z tego powodu definicji następujące przeciążone `GetSquares` metody jest zgodne ze specyfikacją CLS.  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Interfejsy  
 Interfejsy zgodne ze specyfikacją CLS można określić właściwości, zdarzeń i metody wirtualne (metody z żadnej implementacji). Interfejsie zgodnym ze specyfikacją CLS nie może mieć jedną z następujących czynności:  
  
-   Metody statycznej lub pola statyczne. C# i Visual Basic kompilatory generować błędy kompilatora, w przypadku definiowania statycznego elementu członkowskiego w interfejsie.  
  
-   Pola. C# i Visual Basic kompilatory generować błędy kompilatora, w przypadku definiowania pola w interfejsie.  
  
-   Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następujący definicji interfejsu zawiera metodę, `INumber.GetUnsigned`, która jest oznaczona jako specyfikacją CLS. W tym przykładzie generuje ostrzeżenie kompilatora.  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     Z powodu działania tej reguły typów zgodnych ze specyfikacją CLS nie są wymagane do zaimplementowania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS. Jeśli zgodne ze specyfikacją CLS framework ujawnia klasy, która implementuje interfejsie zgodnym ze specyfikacją CLS, on również zawierał konkretnych implementacje wszystkich członków z systemem innym niż — zgodne z CLS.  
  
 Kompilatory języka zgodne ze specyfikacją CLS, należy także zezwolić klasę, aby zapewnić oddzielne implementacje elementów członkowskich, które mają taką samą nazwę i sygnaturę w wielu interfejsach.  Obsługa zarówno C# i Visual Basic [jawne implementacje interfejsu](~/docs/csharp/programming-guide/interfaces/explicit-interface-implementation.md) zapewnienie różnych implementacji metody o identycznej nazwie. Obsługuje również Visual Basic `Implements` implementuje — słowo kluczowe, dzięki czemu można jawnie określić które interfejsu i element członkowski określonego elementu członkowskiego. Poniższy przykład przedstawia tego scenariusza, definiując `Temperature` klasa implementująca `ICelsius` i `IFahrenheit` interfejsy jako jawne implementacje interfejsu.  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>Wyliczenia  
 Wyliczenia zgodne ze specyfikacją CLS, należy wykonać następujące czynności:  
  
-   Podstawowy typ wyliczenia musi być całkowitą wewnętrzne zgodne ze specyfikacją CLS (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, lub <xref:System.Int64>). Na przykład następujący kod próbuje zdefiniowanie wyliczenia o typie podstawowym <xref:System.UInt32> i generuje ostrzeżenie kompilatora.  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
-   Typ wyliczenia musi mieć pojedynczego wystąpienia pola o nazwie `Value__` który jest oznaczony atrybutem <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> atrybutu. Dzięki temu można jawnie odwoływać wartość pola.  
  
-   Wyliczenie zawiera literału pól statycznych, których typ zgodny z typem wyliczenia samej siebie. Na przykład w przypadku definiowania `State` wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` to statycznego pola literału typu `State`.  
  
-   Istnieją dwa rodzaje wyliczenia:  
  
    -   Reprezentuje zestaw wykluczają się wzajemnie, wyliczenie o nazwie wartości będące liczbami całkowitymi. Ten typ wyliczenia jest określane przez braku <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu niestandardowego.  
  
    -   Wyliczenie reprezentuje zestaw flagi bitów, które można łączyć do generowania wartości bez nazwy. Ten typ wyliczenia jest określane przez obecności <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu niestandardowego.  
  
     Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.Enum> struktury.  
  
-   Wartość wyliczenia nie jest ograniczona do jego określonej wartości z zakresu. Innymi słowy zakres wartości podstawowej jest zakres wartości wyliczenia. Można użyć <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metodę, aby ustalić, czy określona wartość elementu członkowskiego wyliczenia.  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>Ogólnie rzecz biorąc wpisz elementy członkowskie  
 Specyfikacja języka wspólnego wymaga wszystkich pól i metod można uzyskać dostępu do jako członków konkretnej klasy. W związku z tym globalnych pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane oprócz typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz obejmują pole lub metoda globalna w kodzie źródłowym Kompilatory języka C# i Visual Basic wygenerowanie błędu kompilatora.  
  
 Specyfikacja języka wspólnego obsługuje tylko standardowe zarządzanych konwencję wywołania. Nie obsługuje niezarządzane konwencji wywoływania i metody z listami zmiennych argumentów oznaczony atrybutem `varargs` — słowo kluczowe. Listy zmiennych argumentów, które są zgodne z standardowej konwencji wywoływania zarządzanych, można użyć <xref:System.ParamArrayAttribute> lub atrybutu implementacji poszczególnych języków, takich jak `params` — słowo kluczowe języka C# i `ParamArray` słów kluczowych w języku Visual Basic.  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>Dostępność elementu członkowskiego  
 Zastępowanie dziedziczonego elementu członkowskiego nie można zmienić dostępności tego członka. Na przykład publiczną metodę w klasie podstawowej nie mogą zostać zastąpione przez prywatnej metody w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku C#) lub `Protected Friend` (w języku Visual Basic) elementu członkowskiego w jednym zestawie, który jest zastępowany przez typ w innym zestawie. W takim przypadku jest dostępność zastąpienie `Protected`.  
  
 Poniższy przykład pokazuje błąd, który jest generowany, gdy <xref:System.CLSCompliantAttribute> atrybut ma ustawioną `true`, i `Person`, które jest klasą pochodną `Animal`, próbuje zmienić dostępności `Species` właściwości z publiczny prywatnej. Przykład pomyślnie kompiluje zmiana jego dostępność publiczną.  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 Typy w podpisie elementu członkowskiego musi być dostępny zawsze, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że publicznego elementu członkowskiego nie może zawierać parametru, którego typ jest prywatny, chronionych lub wewnętrzny. Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas `StringWrapper` konstruktora klasy uwidacznia wewnętrzny `StringOperationType` wartość wyliczenia, która określa, jak powinien być zawijany wartość ciągu.  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>Typy ogólne i elementów członkowskich  
 Zagnieżdżone typy zawsze mieć co najmniej tyle parametrów ogólnych jak ich typ otaczający. Te odpowiada za pomocą pozycji do parametrów ogólnych w typ otaczający. Typ ogólny mogą również obejmować nowe parametry ogólne.  
  
 Relacja między typ zawierający parametry typu ogólnego i jego zagnieżdżone typy mogą być ukryte przez składnię poszczególnych języków. W poniższym przykładzie typu ogólnego `Outer<T>` zawiera dwie klasy zagnieżdżonej `Inner1A` i `Inner1B<U>`. Wywołania `ToString` metodę, która dziedziczy po każdej klasy <xref:System.Object.ToString%2A?displayProperty=nameWithType>, Pokaż, że każda klasa zagnieżdżona zawiera parametry typu zawierająca go klasa.  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 Nazwy typu ogólnego są zakodowane w postaci *nazwa\`n*, gdzie *nazwa* jest nazwą typu \` jest znakiem literału, i *n* jest liczbą parametrami zadeklarowanymi jako w typie lub, w przypadku zagnieżdżonych typów ogólnych liczbę nowo wprowadzonych parametrów typu. To kodowanie nazwy typu ogólnego jest głównie deweloperom, którzy zgodne ze specyfikacją CLS typy ogólne w bibliotece dostęp do za pomocą odbicia.  
  
 Jeśli ograniczenia są stosowane do ogólnego typu żadnych typów, używany jako ograniczenia również musi być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` czyli nie zgodne ze specyfikacją CLS i rodzajowy klasę o nazwie `BaseCollection` których parametru typu muszą pochodzić od `BaseClass`. Jednak ponieważ `BaseClass` nie jest zgodny z CLS, kompilator emituje ostrzeżenie.  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 Jeśli typem ogólnym pochodzi od typu podstawowego ogólny, go ponownie zadeklarować żadnych ograniczeń, dzięki czemu można zagwarantować, że spełnione są również ograniczenia dotyczące typu podstawowego. W poniższym przykładzie zdefiniowano `Number<T>` reprezentujące dowolnego typu liczbowego. Definiuje również `FloatingPoint<T>` klasa, która reprezentuje zmiennoprzecinkową wartości. Jednak kod źródłowy nie powiedzie się do kompilacji, ponieważ nie ma zastosowania ograniczenie na `Number<T>` (czy T musi być typem wartości) do `FloatingPoint<T>`.  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 Przykład kompiluje pomyślnie dodany do ograniczenia `FloatingPoint<T>` klasy.  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Specyfikacja języka wspólnego nakłada model wystąpienia zachowawcze zagnieżdżone typy i chronione elementy członkowskie. Otwórz typy ogólne nie może ujawnić pól lub elementy członkowskie o podpisy zawierające konkretnego wystąpienia typu ogólnego zagnieżdżone, chronionych. Inne niż ogólne typy, które rozszerzają konkretnego wystąpienia metody rodzajowe klasy podstawowej lub interfejsu nie może ujawnić pól lub elementy członkowskie o podpisy zawierające inną podczas tworzenia wystąpienia typu ogólnego zagnieżdżone, chronionych.  
  
 W poniższym przykładzie zdefiniowano typu ogólnego, `C1<T>` (lub `C1(Of T)` w języku Visual Basic) i Klasa chroniona, `C1<T>.N` (lub `C1(Of T).N` w języku Visual Basic). `C1<T>` ma dwie metody `M1` i `M2`. Jednak `M1` nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` (lub `C1(Of Integer).N`) obiektu C1\<T > (lub `C1(Of T)`). W drugiej klasy `C2`, jest określana na podstawie `C1<long>` (lub `C1(Of Long)`). Składa się z dwóch metod `M3` i `M4`. `M3` nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` (lub `C1(Of Integer).N`) obiektu z podklasą `C1<long>`. Należy pamiętać, że Kompilatory języka można jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic jest wyświetlany błąd przy próbie skompilować `M4`.  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>Konstruktorów  
 Konstruktory zgodne ze specyfikacją CLS klas i struktur muszą wykonać następujące czynności:  
  
-   Konstruktora klasy pochodnej musi wywołać konstruktora wystąpień klasy podstawowej, zanim uzyskuje dostęp do danych wystąpienia dziedziczone. To wymaganie dotyczy faktu, że konstruktorów klasy podstawowej nie są dziedziczone przez ich klas pochodnych. Ta zasada dotyczy struktur, które nie obsługują bezpośredniego dziedziczenia.  
  
     Zazwyczaj kompilatory wymuszania tej reguły, niezależnie od zgodności ze specyfikacją CLS, jak przedstawiono na poniższym przykładzie. Tworzy `Doctor` klasy, która jest pochodną `Person` klasy, ale `Doctor` klasa nie może wywołać `Person` konstruktora klasy w celu zainicjowania pól wystąpień dziedziczone.  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
-   Nie można wywołać konstruktora obiektów z wyjątkiem tworzenia obiektu. Ponadto nie można zainicjować obiektu dwa razy. Oznacza to, że na przykład <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> i metody deserializacji, takich jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> nie mogą wywoływać konstruktorów.  
  
<a name="properties"></a>   
### <a name="properties"></a>Właściwości  
 Właściwości typów zgodnych ze specyfikacją CLS, należy wykonać następujące czynności:  
  
-   Właściwość musi mieć metody ustawiającej i/lub metody pobierającej. W zestawie te są zaimplementowane jako specjalnych metod, co oznacza, że będą wyświetlane jako osobne metody (nosi nazwę metody pobierającej `get_` *propertyname* i metodę ustawiającą `set_` *propertyname*) oznaczone jako `SpecialName` w metadanych zestawu. Kompilatory języka C# i Visual Basic wymusić tę regułę automatycznie bez konieczności zastosowania <xref:System.CLSCompliantAttribute> atrybutu.  
  
-   Typ właściwości jest zwracany typ metody pobierającej właściwości i ostatni argument metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS, oraz argumentów nie można przypisać do właściwości przez odwołanie (oznacza to, nie może być wskaźniki zarządzanych).  
  
-   Jeśli właściwość ma metodę pobierającą i metody ustawiającej, oba muszą być wirtualny, statycznym lub oba wystąpienia. C# i Visual Basic kompilatorów automatycznie wymuszać tej reguły za pomocą składni definicji ich właściwości.  
  
<a name="events"></a>   
### <a name="events"></a>Zdarzenia  
 Zdarzenie jest definiowane przez jego nazwa i jej typie. Typ zdarzenia jest delegata, który służy do wskazywania zdarzenia. Na przykład <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie jest typu <xref:System.ResolveEventHandler>. Oprócz samym zdarzeniu trzy metody z nazw na podstawie nazwy zdarzenia implementacji zdarzeń i są oznaczone jako `SpecialName` w metadanych zestawu:  
  
-   Dodawanie obsługi zdarzeń, o nazwie metodę `add_` *EventName*. Na przykład metoda subskrypcji zdarzeń dla <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> nosi nazwę zdarzenia `add_AssemblyResolve`.  
  
-   Metoda usuwania program obsługi zdarzeń o nazwie `remove_` *EventName*. Na przykład metoda usuwania dla <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> nosi nazwę zdarzenia `remove_AssemblyResolve`.  
  
-   Metoda wskazującą, w której wystąpiło zdarzenie, o nazwie `raise_` *EventName*.  
  
> [!NOTE]
>  Większość specyfikacja języka wspólnego zasady dotyczące zdarzenia są implementowane przez Kompilatory języka i są niewidoczne dla deweloperów składnika.  
  
 Metody dodawania, usuwania i wywoływanie zdarzeń musi mieć tą samą dostępnością. One również wszystkie muszą być statyczne, wystąpienie, lub wirtualnych. Metody do dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Dodawanie i usuwanie metody muszą być obecne jednocześnie lub nieobecne.  
  
 W poniższym przykładzie zdefiniowano klasę zgodne ze specyfikacją CLS o nazwie `Temperature` który zgłasza `TemperatureChanged` zdarzeń, jeśli zmiana temperatury między dwa odczyty jest równa lub przekracza wartość progową. `Temperature` Klasa jawnie definiuje `raise_TemperatureChanged` metodę, tak aby selektywnie można wykonać procedury obsługi zdarzeń.  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Overloads  
 Specyfikacja języka wspólnego nakłada się na przeciążone elementy członkowskie następujące wymagania:  
  
-   Elementy członkowskie można przeciążać, na podstawie liczby parametrów i typ żadnego parametru. Wywoływanie Konwencji, zwracany typ niestandardowy Modyfikatory stosowane do metody lub jej parametr i określa, czy parametry są przekazywane przez wartości lub według odwołania nie są uznawane za podczas rozróżnianie między przeciążenia. Na przykład, zobacz kod z wymaganiem, aby nazwy musi być unikatowa w zakresie w [konwencje nazewnictwa](#naming) sekcji.  
  
-   Tylko właściwości i metody może być przeciążony. Pola i zdarzenia nie może być przeciążony.  
  
-   Metody ogólne można przeciążać, na podstawie liczby ich parametry ogólne.  
  
> [!NOTE]
>  `op_Explicit` i `op_Implicit` operatory są wyjątki od reguły, które zwracają wartość nie jest uznawany za część sygnatury metody Rozpoznanie przeciążenia. Te dwa operatory można przeciążać, na podstawie zarówno ich parametrów i ich wartości zwracanej.  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>Wyjątki  
 Obiekty wyjątków muszą pochodzić od <xref:System.Exception?displayProperty=nameWithType> lub inny typ pochodny typu <xref:System.Exception?displayProperty=nameWithType>. Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas niestandardowej klasy o nazwie `ErrorClass` służy do obsługi wyjątków.  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 Aby rozwiązać ten problem, `ErrorClass` musi dziedziczyć po klasie <xref:System.Exception?displayProperty=nameWithType>. Ponadto `Message` właściwość musi zostać zastąpiona. Poniższy przykład poprawia te błędy, aby zdefiniować `ErrorClass` klasy, która jest zgodna ze specyfikacją CLS.  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>Atrybuty  
 Zestawy struktury In.NET, atrybuty niestandardowe udostępnić extensible mechanizm do przechowywania niestandardowych atrybutów i pobierania metadanych dotyczących programowania obiekty, takie jak zestawy, typy elementów członkowskich i parametrów metody. Atrybuty niestandardowe musi pochodzić od <xref:System.Attribute?displayProperty=nameWithType> lub typ pochodny typu <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasy, która nie pochodzi od <xref:System.Attribute?displayProperty=nameWithType>. Należy pamiętać, że wystąpi błąd kompilatora wyniki, tylko gdy specyfikacją CLS atrybut jest stosowany, nie, jeśli klasa jest zdefiniowana.  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 Konstruktor lub właściwości atrybutu zgodne ze specyfikacją CLS mogą uwidaczniać tylko następujących typów:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Byte>  
  
-   <xref:System.Char>  
  
-   <xref:System.Double>  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int64>  
  
-   <xref:System.Single>  
  
-   <xref:System.String>  
  
-   <xref:System.Type>  
  
-   Dowolnego typu wyliczenia o typie podstawowym <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, lub <xref:System.Int64>.  
  
 W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasą pochodzącą z <xref:System.Attribute>. Konstruktor klasy ma parametr typu `Descriptor`, więc klasa nie jest zgodne ze specyfikacją CLS. Zauważ, że kompilator języka C# emituje ostrzeżenie, który kompiluje się pomyślnie, dlatego kompilator Visual Basic emituje ostrzeżenie ani wystąpił błąd.  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliant  
 <xref:System.CLSCompliantAttribute> Atrybut używany do określenia, czy program element spełnia specyfikacja języka wspólnego. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Konstruktor zawiera jeden wymagany parametr `isCompliant`, który wskazuje, czy program element jest zgodne ze specyfikacją CLS.  
  
 W czasie kompilacji kompilatorowi wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie Emituj ostrzeżenia dla typów albo elementów członkowskich, które są jawnie uznane za niezgodne.  
  
 Składnik deweloperzy mogą używać <xref:System.CLSCompliantAttribute> atrybutu na dwa sposoby:  
  
-   Aby zdefiniować części interfejs publiczny udostępnianych przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. W przypadku atrybutu można oznaczyć jako zgodnego ze specyfikacją CLS elementy określonego programu użytkowania gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi przeznaczonych dla platformy .NET Framework.  
  
-   Aby upewnić się, że biblioteka składnik publiczny interfejs przedstawia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory będzie zazwyczaj ostrzeżenie.  
  
> [!WARNING]
>  W niektórych przypadkach Kompilatory języka wymuszania reguł zgodne ze specyfikacją CLS, niezależnie od tego, czy <xref:System.CLSCompliantAttribute> atrybut jest używany. Na przykład definiowania statycznego elementu członkowskiego w interfejsie narusza regułę ze specyfikacją CLS. W tym zakresie, w przypadku definiowania `static` (w języku C#) lub `Shared` (w języku Visual Basic) elementu członkowskiego w interfejsie, zarówno Kompilatory języka C# i Visual Basic wyświetlony komunikat o błędzie i nie można skompilować aplikację.  
  
 <xref:System.CLSCompliantAttribute> Atrybut jest oznaczony atrybutem <xref:System.AttributeUsageAttribute> atrybut, który ma wartość <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Ta wartość umożliwia stosowanie <xref:System.CLSCompliantAttribute> atrybut do dowolnych programów, zestawy, moduły, w tym typów (klasy, struktury, wyliczenia, interfejsów i delegatów), typy elementów członkowskich (konstruktorów, metod, właściwości, pól i zdarzenia), Parametry, parametry ogólne i wartości zwracanych. Jednak w praktyce, powinien zastosować atrybut tylko do zestawów, typy i elementy członkowskie typu. W przeciwnym razie kompilatory Ignoruj ten atrybut i nadal generować ostrzeżenia kompilatora zawsze, gdy wystąpi parametrem niezgodnych parametru ogólnego lub zwróć wartość interfejs publiczny biblioteki.  
  
 Wartość <xref:System.CLSCompliantAttribute> atrybutu jest dziedziczona przez program zawartych w niej elementów. Na przykład jeśli zestaw jest oznaczony jako zgodnego ze specyfikacją CLS, jego typów także są zgodne ze specyfikacją CLS. Typ jest oznaczony jako zgodnego ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie nie są zgodne ze specyfikacją CLS.  
  
 Można jawnie przesłonić odziedziczonego zgodności, stosując <xref:System.CLSCompliantAttribute> atrybutu element zawartych w niej program. Na przykład można użyć <xref:System.CLSCompliantAttribute> atrybutem `isCompliant` wartość `false` można użyć do definiowania niezgodnych typów w zestawie zgodne, a atrybut o `isCompliant` wartość `true` do definiowania zgodny z typem w niezgodny z zestawu. Można również zdefiniować niezgodnych elementów członkowskich w typie zgodnym. Jednak niezgodnych typów nie może mieć elementy członkowskie zgodne, więc nie można użyć atrybutu o `isCompliant` wartość `true` do przesłonięcia dziedziczenia z typem niezgodnych.  
  
 Gdy tworzysz składników, zawsze należy używać <xref:System.CLSCompliantAttribute> atrybutu, aby wskazać, czy używanemu zestawowi, jego typów i jej elementów członkowskich są zgodne ze specyfikacją CLS.  
  
 Aby utworzyć zgodny z CLS składniki:  
  
1.  Użyj <xref:System.CLSCompliantAttribute> aby oznaczyć możesz zestawu jako zgodnego ze specyfikacją CLS.  
  
2.  Oznacz publicznie ujawnionych typów w zestawie, które nie są zgodne z CLS jako niezgodne.  
  
3.  Oznacz żadnych publicznie ujawnionych elementów członkowskich w typach zgodne ze specyfikacją CLS jako niezgodne.  
  
4.  Podaj alternatywnym, zgodnym ze specyfikacją CLS elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS.  
  
 Jeśli pomyślnie zostały oznaczone jako niezgodne typy i elementy członkowskie, kompilujący powinien nie Emituj wszelkie ostrzeżenia o braku zgodności. Jednak należy wskazać elementów członkowskich, które nie są zgodne ze specyfikacją CLS i wyświetlać ich zgodne ze specyfikacją CLS alternatyw w dokumentacji produktu.  
  
 W poniższym przykładzie użyto <xref:System.CLSCompliantAttribute> atrybut do definiowania zgodne ze specyfikacją CLS zestawu i typu `CharacterUtilities`, która ma dwa elementy członkowskie z systemem innym niż — zgodne z CLS. Ponieważ oba elementy są oznaczane `CLSCompliant(false)` atrybutu, kompilator generuje żadnych ostrzeżeń. Ta klasa dostarcza również alternatywnym, zgodnym ze specyfikacją CLS dla obu metod. Zwykle po prostu dodamy dwa przeciążenia do `ToUTF16` metodę w celu zapewnienia alternatywnych zgodne ze specyfikacją CLS. Jednak ponieważ metody nie może zostać przeciążony oparte na wartości zwracanej, nazwy metody zgodne ze specyfikacją CLS różnią się od nazwy metod niezgodnych.  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 Jeśli opracowujesz aplikację, a nie w bibliotece (Jeśli nie są udostępnianie typów albo elementów członkowskich, które mogą być używane przez innych aplikacji), zgodności ze specyfikacją CLS elementów programu, które korzysta z aplikacji mogą być przydatne tylko wtedy, gdy język nie obsługuje ich . W takim przypadku kompilujący języka zostanie wygenerowany błąd podczas próby użycia elementu niezgodnym-ze specyfikacją CLS.  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>Współdziałanie między językami  
 Niezależność od języka ma liczbę możliwych znaczenie. Jeden znaczenie, który został omówiony w artykule [niezależność od języka i elementy niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md), obejmuje bezproblemowo używające typów napisane w języku jednej z aplikacji w innym języku. Drugi znaczenie, które ma fokus w tym artykule, polega na połączeniu kod napisany w wielu językach w ramach jednego zestawu .NET Framework.  
  
 Poniższy przykład przedstawia współdziałanie między językami przez tworzenia biblioteki klas o nazwie Utilities.dll, który zawiera dwie klasy `NumericLib` i `StringLib`. `NumericLib` Klasy jest napisany w języku C# i `StringLib` klasy jest napisany w języku Visual Basic. Oto kod źródłowy StringUtil.vb, łącznie z pojedynczego elementu członkowskiego, `ToTitleCase`w jego `StringLib` klasy.  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 Oto kod źródłowy NumberUtil.cs, który definiuje `NumericLib` klasy, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 Aby pakiet dwóch klas w jednym zestawie, należy skompilować je w modułach. Aby skompilować pliku kodu źródłowego języka Visual Basic w module, użyj tego polecenia:  
  
```  
vbc /t:module StringUtil.vb   
```  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora Visual Basic, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
 Aby skompilować pliku kodu źródłowego C# w module, użyj tego polecenia:  
  
```  
csc /t:module NumberUtil.cs  
```  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora C#, zobacz [budynku wiersza polecenia z csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
 Następnie należy użyć [Link-narzędzie (Link.exe)](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129) do skompilowania w zespół dwa moduły:  
  
```  
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll   
```  
  
 Poniższy przykład wywołuje `NumericLib.NearZero` i `StringLib.ToTitleCase` metody. Należy zauważyć, że zarówno kod Visual Basic, jak i kodu C# możliwość dostępu metody w obu klasach.  
  
 [!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
 [!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]  
  
 Aby skompilować kod Visual Basic, użyj tego polecenia:  
  
```  
vbc example.vb /r:UtilityLib.dll  
```  
  
 Aby skompilować w języku C#, Zmień nazwę kompilatora z **vbc** do **csc**i zmień rozszerzenie pliku z .vb CS:  
  
```  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.CLSCompliantAttribute>
