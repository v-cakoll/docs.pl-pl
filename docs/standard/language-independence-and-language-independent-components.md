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
ms.openlocfilehash: 689ca9f7278dcf91b12bc62b5255a968388bb9f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400534"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka

Program .NET Framework jest niezależny od języka. Oznacza to, że jako deweloper można rozwijać w jednym z wielu języków, które są przeznaczone dla .NET Framework, takich jak C#, C++/CLI, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL i Windows PowerShell. Można uzyskać dostęp do typów i elementów członkowskich bibliotek klas opracowanych dla .NET Framework bez konieczności znać język, w którym zostały pierwotnie napisane i bez konieczności przestrzegania żadnych konwencji języka oryginalnego. Jeśli jesteś deweloperem składników, składnik aplikuje dowolną aplikacją .NET Framework niezależnie od jego języka.

> [!NOTE]
> W pierwszej części tego artykułu omówiono tworzenie składników niezależnych od języka — czyli składników, które mogą być używane przez aplikacje napisane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego napisanego w wielu językach; zobacz [Interoperacyjność między językami](#CrossLang) w drugiej części tego artykułu.

Aby w pełni wchodzić w interakcje z innymi obiektami napisanymi w dowolnym języku, obiekty muszą uwidaczniać do wywoływania tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest zdefiniowany przez specyfikację języka wspólnego (CLS), który jest zestawem reguł, które mają zastosowanie do wygenerowanych zestawów. Specyfikacja języka wspólnego jest zdefiniowana w partycji I, klauzule 7 do 11 [standardu ECMA-335: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny ze specyfikacją języka wspólnego, jest gwarantowana, aby być zgodne z CLS i można uzyskać dostęp z kodu w zestawach napisanych w dowolnym języku programowania, który obsługuje CLS. Można określić, czy składnik jest zgodny ze specyfikacją języka <xref:System.CLSCompliantAttribute> wspólnego w czasie kompilacji, stosując atrybut do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [CLSCompliantAttribute atrybut .](#CLSAttribute)

W tym artykule:

- [Reguły zgodności z CLS](#Rules)

  - [Typy i podpisy elementów członkowskich typu](#Types)

  - [Konwencje nazewnictwa](#naming)

  - [Konwersja typu](#conversion)

  - [Tablice](#arrays)

  - [Interfejsy](#Interfaces)

  - [Wyliczenia](#enums)

  - [Wpisywanie elementów członkowskich w ogóle](#members)

  - [Dostępność elementów członkowskich](#MemberAccess)

  - [Typy ogólne i elementy członkowskie](#Generics)

  - [Konstruktory](#ctors)

  - [Właściwości](#properties)

  - [Zdarzenia](#events)

  - [Overloads](#overloads)

  - [Wyjątki](#exceptions)

  - [Atrybuty](#attributes)

- [Atrybut CLSCompliantAttribute](#CLSAttribute)

- [Współdziałanie między językami](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>Reguły zgodności z CLS

W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS. Aby uzyskać pełną listę reguł, zobacz partycja I, klauzula 11 [standardu ECMA-335: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specyfikacja języka wspólnego omawia każdą regułę zgodności z usługą CLS, ponieważ ma ona zastosowanie do konsumentów (deweloperzy, którzy programowo uzyskują dostęp do składnika, który jest zgodny ze specyfikacją CLS), struktur (deweloperzy, którzy używają kompilatora języka do tworzenia Biblioteki zgodne ze specyfikacją CLS) i extendery (deweloperzy, którzy tworzą narzędzie, takie jak kompilator języka lub analizator kodu, który tworzy składniki zgodne ze specyfikacją CLS). W tym artykule skupiono się na zasadach, które mają zastosowanie do struktur. Należy jednak zauważyć, że niektóre reguły, które mają zastosowanie do extenders mogą również mieć zastosowanie do zestawów, które są tworzone przy użyciu Reflection.Emit.

Aby zaprojektować składnik niezależny od języka, należy zastosować tylko reguły zgodności z cls do interfejsu publicznego składnika. Implementacja prywatna nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności z cls mają zastosowanie tylko do interfejsu publicznego składnika, a nie do jego prywatnej implementacji.

Na przykład niepodpisane liczby całkowite <xref:System.Byte> inne niż nie są zgodne ze specyfikacją CLS. Ponieważ `Person` klasa w poniższym przykładzie `Age` udostępnia <xref:System.UInt16>właściwość typu, poniższy kod wyświetla ostrzeżenie kompilatora.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Można `Person` sprawić, że klasa CLS jest `Age` zgodna ze standardem <xref:System.UInt16> <xref:System.Int16>CLS, zmieniając typ właściwości na , która jest zgodną ze specyfikacją CLS, 16-bitową liczbą całkowitą z podpisem. Nie trzeba zmieniać typu pola `personAge` prywatnego.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Interfejs publiczny biblioteki składa się z następujących elementów:

- Definicje klas publicznych.

- Definicje publicznych członków klas publicznych i definicje elementów członkowskich dostępne dla klas pochodnych (czyli członków chronionych).

- Parametry i zwracatypy metod publicznych klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.

Reguły zgodności z cls są wymienione w poniższej tabeli. Tekst zasad jest dosłownie zaczerpnięty ze [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 by Ecma International. Bardziej szczegółowe informacje na temat tych reguł można znaleźć w poniższych sekcjach.

|Kategoria|Zobacz|Reguła|Numer reguły|
|--------------|---------|----------|-----------------|
|Ułatwienia dostępu|[Dostępność elementów członkowskich](#MemberAccess)|Ułatwienia dostępu nie mogą być zmieniane podczas zastępowania metod dziedziczonych, `family-or-assembly`z wyjątkiem sytuacji, gdy zastępowanie metody dziedziczonej z innego zestawu z ułatwieniami dostępu . W takim przypadku zastąpienie ma `family`dostępność .|10|
|Ułatwienia dostępu|[Dostępność elementów członkowskich](#MemberAccess)|Widoczność i dostępność typów i elementów członkowskich musi być taka, aby typy w podpisie każdego członka były widoczne i dostępne w każdym przypadku, gdy sam członek jest widoczny i dostępny. Na przykład metoda publiczna, która jest widoczna poza jego zestaw nie ma argumentu, którego typ jest widoczny tylko w zestawie. Widoczność i dostępność typów tworzących wystąpienie typu ogólnego używanego w podpisie każdego członka muszą być widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny. Na przykład uprzedzony typ ogólny obecny w podpisie elementu członkowskiego, który jest widoczny poza jego zestawem, nie może mieć ogólnego argumentu, którego typ jest widoczny tylko w zestawie.|12|
|Tablice|[Tablice](#arrays)|Tablice mają elementy o typie zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy mają dolne granice zera. Tylko fakt, że element jest tablicą i typ elementu tablicy jest wymagane do rozróżnienia przeciążeń. Gdy przeciążenie jest oparte na dwóch lub więcej typów tablicy typy elementów mają być nazwane typy.|16|
|Atrybuty|[Atrybuty](#attributes)|Atrybuty są typu <xref:System.Attribute?displayProperty=nameWithType>lub typu dziedziczenia z niego.|41|
|Atrybuty|[Atrybuty](#attributes)|CLS zezwala tylko podzbiór kodowania atrybutów niestandardowych. Jedynymi typami, które pojawiają się w tych <xref:System.Type?displayProperty=nameWithType>kodowaniach, są (patrz Partycja IV): <xref:System.String?displayProperty=nameWithType>, , <xref:System.Char?displayProperty=nameWithType> <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, i <xref:System.Double?displayProperty=nameWithType>każdy typ wyliczenia oparty na podstawowym typie całkowitym zgodnym ze specyfikacją CLS.|34|
|Atrybuty|[Atrybuty](#attributes)|CLS nie zezwala na publicznie widoczne wymagane`modreq`modyfikatory ( , patrz partycja`modopt`II), ale zezwala na opcjonalne modyfikatory ( , patrz Partycja II) nie rozumie.|35|
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektu wywołaniektóre konstruktora wystąpienia jego klasy podstawowej, zanim nastąpi dostęp do danych wystąpienia dziedziczonego. (Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).|21|
|Konstruktorów|[Konstruktory](#ctors)|Konstruktora obiektu nie może być wywoływana z wyjątkiem jako część tworzenia obiektu, a obiekt nie może być inicjowany dwukrotnie.|22|
|Wyliczenia|[Wyliczenia](#enums)|Podstawowym typem wyliczenia jest wbudowany typ całkowity CLS, nazwa pola jest "value__", a pole to `RTSpecialName`jest oznaczone.|7|
|Wyliczenia|[Wyliczenia](#enums)|Istnieją dwa różne rodzaje wyliczenia, wskazane przez <xref:System.FlagsAttribute?displayProperty=nameWithType> obecność lub brak (zobacz Biblioteka partycji IV) atrybut niestandardowy. Jeden reprezentuje nazwane wartości całkowite; drugi reprezentuje nazwane flagi bitowe, które można połączyć w celu wygenerowania wartości bez nazwy. Wartość nie `enum` jest ograniczona do określonych wartości.|8|
|Wyliczenia|[Wyliczenia](#enums)|Literały pola statyczne wyliczenia mają typ samego wyliczenia.|9|
|Zdarzenia|[Zdarzenia](#events)|Metody implementowania zdarzenia są oznaczone `SpecialName` w metadanych.|29|
|Zdarzenia|[Zdarzenia](#events)|Dostępność zdarzenia i jego dostępu jest identyczna.|30|
|Zdarzenia|[Zdarzenia](#events)|Metody `add` `remove` i metody zdarzenia są obecne lub nieobecne.|31|
|Zdarzenia|[Zdarzenia](#events)|Metody zdarzenia i metody biorą po jednym parametrze, którego typ określa typ zdarzenia <xref:System.Delegate?displayProperty=nameWithType>i który jest pochodną . `add` `remove`|32|
|Zdarzenia|[Zdarzenia](#events)|Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut, `SpecialName` o którym mowa w zasadzie CLS 29, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do zasad identyfikatora.|33|
|Wyjątki|[Wyjątki](#exceptions)|Obiekty, które są generowane, są typu <xref:System.Exception?displayProperty=nameWithType> lub typu dziedziczenia z niego. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.|40|
|Ogólne|[Zgodność z CLS: zasady](#Rules)|Reguły CLS mają zastosowanie tylko do tych części typu, które są dostępne lub widoczne poza zestawem definiującym.|1|
|Ogólne|[Zgodność z CLS: zasady](#Rules)|Członkowie typów niezgodnych ze specyfikacją CLS nie mogą być oznaczani zgodnie z CLS.|2|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typy zagnieżdżone mają co najmniej tyle parametrów ogólnych, co typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają położeniu parametrom ogólnym w jego typie otaczającym.|42|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Nazwa typu ogólnego koduje liczbę parametrów typu zadeklarowanych na typ ie niezagnieżdżonym lub nowo wprowadzonych do typu, jeśli są zagnieżdżone, zgodnie z regułami określonymi powyżej.|43|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typ rodzajowy deklaruje wystarczające ograniczenia, aby zagwarantować, że wszelkie ograniczenia dotyczące typu podstawowego lub interfejsów byłyby spełnione przez ograniczenia typu ogólnego.|4444|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typy stosowane jako ograniczenia parametrów ogólnych same w sobie muszą być zgodne ze specyfikacją CLS.|45|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Widoczność i dostępność elementów członkowskich (w tym typów zagnieżdżonych) w uprzednio typogólny uważa się za zakres do konkretnej wystąpienia, a nie ogólnej deklaracji typu jako całości. Zakładając, że to, zasady widoczności i dostępności reguły CLS 12 nadal mają zastosowanie.|46|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej musi istnieć domyślna konkretna (nieabstrakcyjna) implementacja.|47|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie wymagają definiowania metod niezgodnych ze specyfikacją CLS w celu ich wdrożenia.|18|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól.|19|
|Elementy członkowskie|[Wpisywanie elementów członkowskich w ogóle](#members)|Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS.|36|
|Elementy członkowskie|--|Wartość literału statycznego jest określona za pomocą metadanych inicjowania pola. Literału zgodnego ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pola, która jest dokładnie tego `enum`samego typu co literał (lub typu źródłowego, jeśli ten literał jest ).|13|
|Elementy członkowskie|[Wpisywanie elementów członkowskich w ogóle](#members)|Ograniczenie vararg nie jest częścią CLS, a jedyną konwencją wywołującą obsługiwaną przez cls jest standardowa konwencja wywoływania zarządzanego.|15|
|Konwencje nazewnictwa|[Konwencje nazewnictwa](#naming)|Zespoły następują po załączniku 7 sprawozdania technicznego 15 standardu Unicode3.0, regulującego zestaw znaków dopuszczonych do uruchamiania i umieszczania ich w identyfikatorach dostępnych online pod adresem <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Identyfikatory są w formacie kanonicznym zdefiniowanym przez unicode normalization form C. Dla celów CLS dwa identyfikatory są takie same, jeśli ich małe mapowania (określone przez mapowania niewrażliwe na ustawienia regionalne Unicode, jeden do jednego małe litery) są takie same. Oznacza to, że aby w ramach CLS dwa identyfikatory były uważane za różne, różnią się one w większym niż tylko ich przypadku. Jednak w celu zastąpienia dziedziczonej definicji interfejsu i rdzenia cli wymaga precyzyjnego kodowania oryginalnej deklaracji.|4|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS powinny być odrębne niezależnie od rodzaju, z wyjątkiem przypadków, gdy nazwy są identyczne i rozwiązane poprzez przeciążenie. Oznacza to, że podczas CTSallows jednego typu, aby użyć tej samej nazwy dla metody i pola, CLS nie.|5|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Pola i typy zagnieżdżone różnią się tylko od porównania identyfikatorów, nawet jeśli CTS umożliwia odróżnienie odrębnych podpisów. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikatorów) różnią się o więcej niż tylko typ zwracany, z wyjątkiem przypadków określonych w zasadzie 39 CLS.|6|
|Przeciążenie|[Overloads](#overloads)|Tylko właściwości i metody mogą być przeciążone.|37|
|Przeciążenie|[Overloads](#overloads)|Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów `op_Implicit` ich `op_Explicit`parametrów, z wyjątkiem operatorów konwersji o nazwie i , które mogą być również przeciążone na podstawie ich typu zwracanego.|38|
|Przeciążenie|--|Jeżeli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę, a dla określonego zestawu wystąpień typu mają one ten sam parametr i typy zwracane, wszystkie te metody muszą być semantycznie równoważne w tych wystąpieniach typu.|48|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|<xref:System.Object?displayProperty=nameWithType>jest zgodny ze specyfikacją CLS. Każda inna klasa zgodna ze specyfikacją CLS dziedziczy z klasy zgodnej ze specyfikacją CLS.|23|
|Właściwości|[Właściwości](#properties)|The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.|24|
|Właściwości|[Właściwości](#properties)|Akcesory właściwości muszą być statyczne, wszystkie są wirtualne lub wszystkie są wystąpieniem.|26|
|Właściwości|[Właściwości](#properties)|Typ właściwości jest zwracany typu getter i typ ostatniego argumentu ustawiającego. Typy parametrów właściwości są typy parametrów do getter i typy wszystkich, ale parametr końcowy ustawiania. Wszystkie te rodzaje muszą być zgodne ze specyfikacją CLS i nie mogą być zarządzane wskaźnikami (tj. nie są przekazywane przez odniesienie).|27|
|Właściwości|[Właściwości](#properties)|Właściwości muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut, `SpecialName` o którym mowa w zasadzie CLS 24, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do zasad identyfikatora. Właściwość ma metodę metody getter, metodę ustawiania lub obie te metody.|28|
|Konwersja typu|[Konwersja typu](#conversion)|Jeżeli `op_Implicit` jest `op_Explicit` to jeden lub jest zapewniony, zapewnia się alternatywne środki przymusu.|39|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|Typy wartości pudełkowych nie są zgodne ze specyfikacją CLS.|3|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|Wszystkie typy pojawiające się w podpisie muszą być zgodne ze specyfikacją CLS. Wszystkie typy tworzące wystąpienie typu ogólnego muszą być zgodne ze specyfikacją CLS.|11|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|Wpisane odwołania nie są zgodne ze specyfikacją CLS.|14|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS.|17|
|Typy|[Podpisy elementów członkowskich typu i typu](#Types)|Klasy, typy wartości i interfejsy zgodne ze specyfikacją CLS nie wymagają implementacji elementów członkowskich niezgodnych ze specyfikacją CLS.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu

Typ <xref:System.Object?displayProperty=nameWithType> jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typu .NET Framework. Dziedziczenie w .NET Framework jest niejawne <xref:System.String> (na przykład <xref:System.Object> klasa niejawnie dziedziczy z klasy) <xref:System.ArgumentException> lub jawne (na przykład <xref:System.SystemException> <xref:System.Globalization.CultureNotFoundException> klasa jawnie dziedziczy <xref:System.Exception> z klasy, która jawnie dziedziczy z klasy, która jawnie dziedziczy z klasy). Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy musi być również zgodny ze specyfikacją CLS.

W poniższym przykładzie przedstawiono typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje klasę podstawową, `Counter` która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika. Ponieważ klasa zapewnia funkcjonalność licznika przez zawijanie niepodpisanej liczby całkowitej, klasa jest oznaczona jako niezgodna ze specyfikacją CLS. W rezultacie klasa pochodna `NonZeroCounter`, również nie jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Wszystkie typy, które pojawiają się w podpisach elementów członkowskich, w tym typ zwracany metody lub typ właściwości, muszą być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:

- Wszystkie typy, które tworzą wystąpienie typu ogólnego musi być zgodny ze specyfikacją CLS.

- Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.

System wspólnego [typu](../../docs/standard/base-types/common-type-system.md) .NET Framework zawiera szereg wbudowanych typów, które są obsługiwane bezpośrednio przez wspólny program uruchamiający język i są specjalnie zakodowane w metadanych zestawu. Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

|Typ zgodny ze specyfikacją CLS|Opis|
|-------------------------|-----------------|
|<xref:System.Byte>|8-bitowa liczba całkowita bez znaku|
|<xref:System.Int16>|16-bitowa liczba całkowita podpisana|
|<xref:System.Int32>|32-bitowa liczba całkowita podpisana|
|<xref:System.Int64>|64-bitowa liczba całkowita podpisana|
|<xref:System.Single>|Pojedyncza precyzja wartość zmiennoprzecinkową|
|<xref:System.Double>|Podwójna precyzja wartości zmiennoprzecinkowej|
|<xref:System.Boolean>|`true`lub `false` typ wartości|
|<xref:System.Char>|Jednostka kodu kodowego zakodowanego uTF-16|
|<xref:System.Decimal>|Liczba dziesiętna niezmienno-zmienna|
|<xref:System.IntPtr>|Wskaźnik lub uchwyt rozmiaru zdefiniowanego przez platformę|
|<xref:System.String>|Kolekcja obiektów zero, jeden <xref:System.Char> lub więcej|

Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.

|Typ niezgodny|Opis|Alternatywa zgodna ze specyfikacją CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8-bitowy podpisany typ danych całkowitych|<xref:System.Int16>|
|<xref:System.TypedReference>|Wskaźnik do obiektu i jego typu wykonywania|Brak|
|<xref:System.UInt16>|16-bitowa liczba całkowita bez znaku|<xref:System.Int32>|
|<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku|<xref:System.Int64>|
|<xref:System.UInt64>|64-bitowa liczba całkowita bez znaku|<xref:System.Int64>(może się <xref:System.Numerics.BigInteger>przelać), lub<xref:System.Double>|
|<xref:System.UIntPtr>|Niepodpisany wskaźnik lub uchwyt|<xref:System.IntPtr>|

Biblioteka klas .NET Framework lub inne biblioteki klas mogą zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

- Typy wartości w pudełku. Poniższy przykład języka C# tworzy klasę, która `int*` `Value`ma właściwość publiczną o nazwie . Ponieważ `int*` jest to typ wartości zapakowane, kompilator flagi go jako niezgodne ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Wpisane odwołania, które są specjalne konstrukcje, które zawierają odwołanie do obiektu i odwołanie do typu. Wpisane odwołania są reprezentowane w .NET Framework przez <xref:System.TypedReference> klasę.

Jeśli typ nie jest zgodny ze specyfikacją <xref:System.CLSCompliantAttribute> CLS, `false` należy zastosować atrybut z wartością `isCompliant` do niego. Aby uzyskać więcej informacji, zobacz sekcję [atrybutu CLSCompliantAttribute.](#CLSAttribute)

Poniższy przykład ilustruje problem zgodności cls w podpisie metody i w funkcji wystąpienia typu ogólnego. Definiuje `InvoiceItem` klasę z właściwością <xref:System.UInt32>typu, właściwością `Nullable(Of UInt32)`typu i konstruktorem <xref:System.UInt32> z `Nullable(Of UInt32)`parametrami typu i . Otrzymasz cztery ostrzeżenia kompilatora podczas próby skompilowania tego przykładu.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Aby wyeliminować ostrzeżenia kompilatora, zastąp typy `InvoiceItem` niezgodne ze specyfikacją CLS w interfejsie publicznym zgodnymi typami:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Oprócz określonych typów wymienionych, niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Należą do nich typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczb całkowitych.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Dla klas abstrakcyjnych zgodnych ze specyfikacją `abstract` CLS (czyli klas oznaczonych jako c# lub w `MustInherit` języku Visual Basic) wszystkie elementy członkowskie klasy muszą być również zgodne ze specyfikacją CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ niektóre języki programowania są bez uwzględniania wielkości liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i elementy członkowskie) muszą się różnić o więcej niż wielkość liter. Dwa identyfikatory są uważane za równoważne, jeśli ich małe mapowania są takie same. Poniższy przykład języka C# definiuje `Person` dwie `person`klasy publiczne i . Ponieważ różnią się one tylko przez przypadek, kompilator C# flagi je jako niezgodne ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Identyfikatory języka programowania, takie jak nazwy przestrzeni nazw, typów i elementów członkowskich, muszą być zgodne ze [standardem Unicode 3.0, sprawozdaniem technicznym 15, załącznikiem 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

- Pierwszym znakiem identyfikatora może być dowolna litera jednoliterowa Unicode, mała litera, litera tytułu, litera modyfikatora, inna litera lub litera. Aby uzyskać informacje na temat <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> kategorii znaków Unicode, zobacz wyliczenie.

- Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszy znak, a także mogą zawierać znaki bez odstępów, odstępy łączące znaczniki, liczby dziesiętne, znaki interpunkcyjne łączników i kody formatowania.

Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na formularz Normalizacji Unicode C, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanego w utf-16. Sekwencje znaków, które produkują te same jednostki kodu w unicode normalizacji formularza C nie są zgodne ze specyfikacją CLS. Poniższy przykład definiuje właściwość `Å`o nazwie , która składa się ze znaku ZNAK ANGSTROM SIGN `Å`(U +212B) i drugą właściwość o nazwie , która składa się ze znaku LATIN LITERA A Z PIERŚCIENIEM POWYŻEJ (U +00C5). Kompilatory Języka C# i Visual Basic oflagują kod źródłowy jako niezgodny ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Nazwy elementów członkowskich w określonym zakresie (takie jak obszary nazw w zestawie, typy w obszarze nazw lub elementy członkowskie w obrębie typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane przez przeciążenie. To wymaganie jest bardziej rygorystyczne niż w systemie typu wspólnego, co pozwala wielu elementów członkowskich w zakresie mają identyczne nazwy, o ile są one różne rodzaje elementów członkowskich (na przykład jeden jest metodą, a jeden jest pole). W szczególności dla członków typu:

- Pola i typy zagnieżdżone różnią się samą nazwą.

- Metody, właściwości i zdarzenia, które mają taką samą nazwę musi się różnić o więcej niż tylko zwracać typ.

W poniższym przykładzie przedstawiono wymóg, że nazwy elementów członkowskich muszą być unikatowe w ich zakresie. Definiuje klasę o `Converter` nazwie, która `Conversion`zawiera cztery elementy członkowskie o nazwie . Trzy są metody, a jeden jest właściwością. Metoda, która <xref:System.Int64> zawiera parametr jest jednoznacznie nazwany, ale <xref:System.Int32> dwie metody z parametrem nie są, ponieważ wartość zwracana nie jest uważany za część podpisu członka. Właściwość `Conversion` również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążone metody.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Poszczególne języki zawierają unikatowe słowa kluczowe, więc języki, które są kierowane do wspólnego języka runtime musi również zapewnić pewien mechanizm odwoływania się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak w poniższym przykładzie języka Visual Basic jest w stanie `case` rozróżnić klasę o nazwie od słowa kluczowego `case` przy użyciu otwierania i zamykania nawiasów klamrowych. W przeciwnym razie w przykładzie może wywołać komunikat o błędzie "Słowo kluczowe nie jest prawidłowy jako identyfikator" i nie można skompilować.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Poniższy przykład języka C# jest w `case` stanie utworzyć `@` wystąpienia klasy przy użyciu symbolu do odróżniania identyfikatora od słowa kluczowego języka. Bez niego kompilator Języka C# wyświetlałby dwa komunikaty o błędach: "Typ oczekiwany" i "Nieprawidłowe wyrażenie termin "case".

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Konwersja typu

Specyfikacja języka wspólnego definiuje dwa operatory konwersji:

- `op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub precyzji. Na przykład <xref:System.Decimal> struktura zawiera przeciążony `op_Implicit` operator do konwersji <xref:System.Char> wartości <xref:System.Decimal> typów i wartości całkowitych do wartości.

- `op_Explicit`, który jest używany do zawężania konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzji. Na przykład <xref:System.Decimal> `op_Explicit` struktura zawiera przeciążony operator <xref:System.Double> <xref:System.Single> do <xref:System.Decimal> konwersji i <xref:System.Decimal> wartości do <xref:System.Double>i <xref:System.Single>do <xref:System.Char>konwersji wartości do wartości całkowitych, , , i .

Jednak nie wszystkie języki obsługują przeciążenie operatora lub definicji operatorów niestandardowych. Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonania konwersji. Zalecamy `From`podanie metod *Xxx* i `To` *Xxx.*

W poniższym przykładzie zdefiniowano konwersje niejawne zgodne ze specyfikacją CLS. Tworzy `UDouble` klasę, która reprezentuje podpisaną podwójną precyzję, numer zmiennoprzecinkowy. Przewiduje ona konwersje `UDouble` <xref:System.Double> niejawne z `UDouble` do <xref:System.Single> <xref:System.Double> i `UDouble`dla <xref:System.Single> `UDouble`jawnych konwersji z do , do , i do . `ToDouble` Definiuje również metodę jako alternatywę dla niejawnego `ToSingle` `FromDouble`operatora `FromSingle` konwersji i , i metody jako alternatywy dla jawnych operatorów konwersji.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Tablice

Tablice zgodne ze specyfikacją CLS są zgodne z następującymi regułami:

- Wszystkie wymiary tablicy muszą mieć dolną obwiednię zerową. Poniższy przykład tworzy tablicę niezgodną ze specyfikacją CLS z dolną obwiednią. Należy zauważyć, że pomimo <xref:System.CLSCompliantAttribute> obecności atrybutu kompilator nie wykrywa, `Numbers.GetTenPrimes` że tablica zwracana przez metodę nie jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS. Pierwszy zwraca tablicę <xref:System.UInt32> wartości. Drugi zwraca <xref:System.Object> tablicy, <xref:System.Int32> <xref:System.UInt32> która zawiera i wartości. Mimo że kompilator identyfikuje pierwszą tablicę jako niezgodną ze względu na jej <xref:System.UInt32> typ, nie rozpoznaje, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Rozpoznawanie przeciążenia dla metod, które mają parametry tablicy opiera się na fakcie, że są one tablice i na ich typ elementu. Z tego powodu następująca definicja `GetSquares` metody przeciążonej jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Interfejsy

Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji). Interfejs zgodny ze specyfikacją CLS nie może mieć żadnej z następujących czynności:

- Metody statyczne lub pola statyczne. Kompilatory Języka C# i Visual Basic generują błędy kompilatora, jeśli zdefiniujesz statyczny element członkowski w interfejsie.

- Pola. Kompilatory Języka C# i Visual Basic generują błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.

- Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu `INumber.GetUnsigned`zawiera metodę, która jest oznaczona jako niezgodna ze specyfikacją CLS. W tym przykładzie generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Z powodu tej reguły typy zgodne ze specyfikacją CLS nie są wymagane do implementowania elementów członkowskich niezgodnych ze specyfikacją CLS. Jeśli struktura zgodna ze specyfikacją CLS udostępnia klasę, która implementuje interfejs zgodny ze specyfikacją CLS, powinna również zapewnić konkretne implementacje wszystkich elementów członkowskich niezgodnych ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na dostarczanie oddzielnych implementacji elementów członkowskich, które mają taką samą nazwę i podpis w wielu interfejsach.  Zarówno C# i Visual Basic obsługują [implementacje interfejsu jawnego,](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) aby zapewnić różne implementacje metod o identycznej nazwie. Visual Basic obsługuje `Implements` również słowo kluczowe, które umożliwia jawnie określić, który interfejs i element członkowski implementuje określonego elementu członkowskiego. W poniższym przykładzie przedstawiono ten `Temperature` scenariusz, definiując klasę, która implementuje `ICelsius` i `IFahrenheit` interfejsy jako implementacje interfejsu jawnego.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Wyliczenia

Wyliczenia zgodne ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna<xref:System.Byte> <xref:System.Int16>ze <xref:System.Int32>specyfikacją CLS ( , , lub <xref:System.Int64>). Na przykład poniższy kod próbuje zdefiniować wyliczenie, <xref:System.UInt32> którego typem źródłowym jest i generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Typ wyliczenia musi mieć pole `Value__` pojedynczego wystąpienia <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> o nazwie oznaczone atrybutem. Dzięki temu można odwoływać się do wartości pola niejawnie.

- Wyliczenie zawiera literały pola statyczne, których typy są zgodne z typem samego wyliczenia. Na przykład, jeśli `State` zdefiniujesz wyliczenie `State.On` z wartościami `State.Off`i , `State.On` i `State.Off` są zarówno literały pola statyczne, których typem jest `State`.

- Istnieją dwa rodzaje wyliczeń:

  - Wyliczenie, które reprezentuje zestaw wzajemnie się wykluczają, nazwane wartości całkowite. Ten typ wyliczenia jest wskazywany przez brak atrybutu niestandardowego. <xref:System.FlagsAttribute?displayProperty=nameWithType>

  - Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć, aby wygenerować wartość bez nazwy. Ten typ wyliczenia jest wskazywany przez obecność atrybutu niestandardowego. <xref:System.FlagsAttribute?displayProperty=nameWithType>

  Aby uzyskać więcej informacji, <xref:System.Enum> zobacz dokumentację struktury.

- Wartość wyliczenia nie jest ograniczona do zakresu jego określonych wartości. Innymi słowy zakres wartości w wyliczeniu jest zakres jego wartości bazowej. Metoda służy <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> do określenia, czy określona wartość jest członkiem wyliczenia.

<a name="members"></a>

### <a name="type-members-in-general"></a>Wpisywanie elementów członkowskich w ogóle

Specyfikacja języka wspólnego wymaga dostępu do wszystkich pól i metod jako członków określonej klasy. W związku z tym globalne pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane z wyjątkiem typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz uwzględnić globalne pole lub metodę w kodzie źródłowym, kompilatory Języka C# i Visual Basic generują błąd kompilatora.

Specyfikacja języka wspólnego obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje niezarządzanych konwencji i metod wywoływania z listami argumentów zmiennych oznaczonych `varargs` słowem kluczowym. Dla zmiennej listy argumentów, które są zgodne <xref:System.ParamArrayAttribute> ze standardową konwencją wywołania `params` zarządzanego, należy `ParamArray` użyć atrybutu lub implementacji poszczególnych języków, takich jak słowo kluczowe w języku C# i słowo kluczowe w języku Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Dostępność elementów członkowskich

Zastąpienie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego. Na przykład metoda publiczna w klasie podstawowej nie może zostać zastąpiona metodą prywatną w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku `Protected Friend` C#) lub (w języku Visual Basic) element członkowski w jednym zestawie, który jest zastępowany przez typ w innym zestawie. W takim przypadku dostępność zastąpienia wynosi `Protected`.

Poniższy przykład ilustruje błąd, który <xref:System.CLSCompliantAttribute> jest generowany, gdy `true`atrybut jest ustawiony na , i `Human`, który jest klasą wyprowadzoną z `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznych na prywatne. Przykład kompiluje się pomyślnie, jeśli jego dostępność zostanie zmieniona na publiczne.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Typy w podpisie elementu członkowskiego muszą być dostępne, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że element członkowski nie może zawierać parametru, którego typ jest prywatny, chroniony lub wewnętrzny. W poniższym przykładzie przedstawiono błąd kompilatora, który powoduje, że konstruktor `StringWrapper` klasy udostępnia wewnętrzną `StringOperationType` wartość wyliczenia, która określa, jak wartość ciągu powinna być opakowana.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Typy ogólne i elementy członkowskie

Typy zagnieżdżone zawsze mają co najmniej tyle parametrów ogólnych, co ich typ otaczający. Odpowiadają one według pozycji parametrów ogólnych w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrami typu ogólnego typu zawierającego i jego zagnieżdżonymi typami może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ `Outer<T>` ogólny zawiera dwie `Inner1A` `Inner1B<U>`klasy zagnieżdżone i . Wywołania `ToString` metody, z której dziedziczy każda <xref:System.Object.ToString%2A?displayProperty=nameWithType>klasa, pokazują, że każda klasa zagnieżdżona zawiera parametry typu jej klasy zawierającej.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Nazwy typów ogólnych są kodowane w *nazwie\`* formularza n \` , gdzie *nazwa* jest nazwą typu, jest literałznaku, a *n* jest liczbą parametrów zadeklarowanych dla typu lub, dla zagnieżdżonych typów ogólnych, liczbą nowo wprowadzonych parametrów typu. To kodowanie nazw typów ogólnych jest szczególnie interesujące dla deweloperów, którzy używają odbicia, aby uzyskać dostęp do typów ogólnych skarg CLS w bibliotece.

Jeśli ograniczenia są stosowane do typu ogólnego, wszystkie typy używane jako ograniczenia muszą być również zgodne ze specyfikacją CLS. Poniższy przykład definiuje klasę `BaseClass` o nazwie, która nie jest zgodna ze specyfikacją CLS i klasę ogólną o nazwie, `BaseCollection` której parametr typu musi pochodzić od `BaseClass`. Ale `BaseClass` ponieważ nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Jeśli typ ogólny pochodzi z ogólnego typu podstawowego, musi ponownie zadeklarować wszelkie ograniczenia, aby zagwarantować, że ograniczenia typu podstawowego są również spełnione. Poniższy przykład definiuje, `Number<T>` który może reprezentować dowolny typ liczbowy. Definiuje również `FloatingPoint<T>` klasę, która reprezentuje wartość zmiennoprzecinkową. Jednak kod źródłowy nie może skompilować, ponieważ nie `Number<T>` stosuje ograniczenia na (że `FloatingPoint<T>`T musi być typem wartości) do .

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Przykład kompiluje pomyślnie, jeśli ograniczenie jest `FloatingPoint<T>` dodawany do klasy.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Specyfikacja języka wspólnego nakłada konserwatywny model wystąpienia dla typów zagnieżdżonych i chronionych elementów członkowskich. Otwórz typy ogólne nie można uwidaczniać pól lub elementów członkowskich z podpisami, które zawierają określone wystąpienia zagnieżdżonego, chronionego typu ogólnego. Typy nierodzajowe, które rozszerzają określony wystąpienia ogólnej klasy podstawowej lub interfejsu nie można uwidaczniać pól lub elementów członkowskich z podpisów, które zawierają różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.

W poniższym przykładzie zdefiniowano `C1<T>` `C1(Of T)` typ ogólny (lub w `C1<T>.N` języku `C1(Of T).N` Visual Basic) i klasę chronioną (lub w języku Visual Basic). `C1<T>`ma dwie metody `M1` `M2`i . Jednak `M1` nie jest zgodny ze `C1<int>.N` specyfikacją CLS, `C1(Of Integer).N`ponieważ próbuje\<zwrócić (lub `C1(Of T)`) obiekt z C1 T> (lub ). Druga klasa, `C2`pochodzi od `C1<long>` (lub `C1(Of Long)`). Ma dwie metody `M3` i `M4`. `M3`nie jest zgodny ze specyfikacją `C1<int>.N` CLS, `C1(Of Integer).N`ponieważ próbuje zwrócić `C1<long>`(lub ) obiekt z podklasy . Należy zauważyć, że kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie visual basic wyświetla błąd podczas `M4`próby skompilowania .

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Konstruktorów

Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Konstruktor klasy pochodnej musi wywołać konstruktora wystąpienia jego klasy podstawowej, zanim uzyskuje dostęp do danych wystąpienia dziedziczonego. Wymaganie to wynika z faktu, że konstruktory klasy podstawowej nie są dziedziczone przez ich klas pochodnych. Ta reguła nie ma zastosowania do struktur, które nie obsługują dziedziczenia bezpośredniego.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności z cls, jak pokazano w poniższym przykładzie. Tworzy `Doctor` klasę, która jest pochodną `Person` klasy, `Doctor` ale klasa `Person` nie może wywołać konstruktora klasy, aby zainicjować pola wystąpienia dziedziczone.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nie można wywołać konstruktora obiektu, z wyjątkiem utworzenia obiektu. Ponadto obiekt nie może zostać zainicjowany dwukrotnie. Na przykład oznacza <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> to, że i metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> deserializacji, takie jak nie może wywoływać konstruktorów.

<a name="properties"></a>

### <a name="properties"></a>Właściwości

Właściwości w typach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Właściwość musi mieć ustawiacz, getter lub obu. W zestawie są one implementowane jako metody specjalne, co oznacza, że będą one `get_`wyświetlane jako oddzielne metody `set_`(getter nosi nazwę *właściwości,* a setter jest *propertyname)* oznaczone jako `SpecialName` w metadanych zestawu. Kompilatory Języka C# i Visual Basic wymuszają <xref:System.CLSCompliantAttribute> tę regułę automatycznie bez konieczności stosowania atrybutu.

- Typ właściwości jest zwracany typ getter właściwości i ostatni argument setter. Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisane do właściwości przez odwołanie (oznacza to, że nie mogą być zarządzane wskaźniki).

- Jeśli właściwość ma zarówno metody święceń, jak i metody ustawiania, muszą być zarówno wirtualne, statyczne lub oba wystąpienia. Kompilatory Języka C# i Visual Basic automatycznie wymuszają tę regułę za pomocą składni definicji właściwości.

<a name="events"></a>

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przez jego nazwę i typ. Typ zdarzenia jest pełnomocnikiem, który jest używany do wskazania zdarzenia. Na przykład <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie jest <xref:System.ResolveEventHandler>typu . Oprócz samego zdarzenia trzy metody z nazwami opartymi na nazwie zdarzenia zapewniają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:

- Metoda dodawania programu obsługi `add_`zdarzeń o nazwie *EventName*. Na przykład metoda subskrypcji zdarzeń <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> dla `add_AssemblyResolve`zdarzenia nosi nazwę .

- Metoda usuwania programu obsługi zdarzeń `remove_`o nazwie *EventName*. Na przykład metoda usuwania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia nosi `remove_AssemblyResolve`nazwę .

- Metoda wskazująca, że zdarzenie wystąpiło, `raise_`o nazwie *EventName*.

> [!NOTE]
> Większość reguł specyfikacji języka wspólnego dotyczące zdarzeń są implementowane przez kompilatory języka i są przezroczyste dla deweloperów składników.

Metody dodawania, usuwania i podnoszenia zdarzenia muszą mieć taką samą dostępność. Muszą być również statyczne, wystąpienia lub wirtualne. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody dodawania i usuwania muszą być obecne lub oba muszą być nieobecne.

W poniższym przykładzie zdefiniowano klasę `Temperature` zgodną `TemperatureChanged` ze specyfikacją CLS o nazwie, która wywołuje zdarzenie, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. Klasa `Temperature` jawnie definiuje `raise_TemperatureChanged` metodę, dzięki czemu można selektywnie wykonywać programy obsługi zdarzeń.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Overloads

Specyfikacja języka wspólnego nakłada następujące wymagania na przeciążone elementy członkowskie:

- Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu dowolnego parametru. Konwencja wywołująca, typ zwracany, modyfikatory niestandardowe stosowane do metody lub jej parametru i czy parametry są przekazywane przez wartość lub przez odwołanie nie są brane pod uwagę podczas rozróżniania między przeciążenia. Na przykład zobacz kod wymagania, że nazwy muszą być unikatowe w zakresie w [konwencji nazewnictwa](#naming) sekcji.

- Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

- Metody ogólne mogą być przeciążone na podstawie liczby ich parametrów ogólnych.

> [!NOTE]
> I `op_Explicit` `op_Implicit` operatory są wyjątki od reguły, że wartość zwracana nie jest uważana za część podpisu metody dla rozpoznawania przeciążenia. Te dwa operatory mogą być przeciążone na podstawie zarówno ich parametrów, jak i ich wartości zwracanej.

<a name="exceptions"></a>

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątku muszą <xref:System.Exception?displayProperty=nameWithType> pochodzić od lub <xref:System.Exception?displayProperty=nameWithType>z innego typu pochodzącego z . W poniższym przykładzie przedstawiono błąd kompilatora, który powoduje, że klasa niestandardowa o nazwie `ErrorClass` jest używany do obsługi wyjątków.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Aby poprawić ten `ErrorClass` błąd, klasa <xref:System.Exception?displayProperty=nameWithType>musi dziedziczyć z . Ponadto `Message` właściwość musi zostać zastąpiona. W poniższym przykładzie poprawiono `ErrorClass` te błędy, aby zdefiniować klasę, która jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Atrybuty

In.NET zestawów Framework, atrybuty niestandardowe zapewniają rozszerzalny mechanizm przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programowania, takich jak zestawy, typy, elementy członkowskie i parametry metody. Atrybuty niestandardowe muszą <xref:System.Attribute?displayProperty=nameWithType> pochodzić od lub <xref:System.Attribute?displayProperty=nameWithType>z typu pochodzącego z .

Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasę, która nie pochodzi <xref:System.Attribute?displayProperty=nameWithType>od . Należy zauważyć, że błąd kompilatora powoduje tylko wtedy, gdy atrybut niezgodny ze specyfikacją CLS jest stosowany, a nie po zdefiniowaniu klasy.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

Konstruktor lub właściwości atrybutu zgodnego ze specyfikacją CLS mogą uwidaczniać tylko następujące typy:

- <xref:System.Boolean>

- <xref:System.Byte>

- <xref:System.Char>

- <xref:System.Double>

- <xref:System.Int16>

- <xref:System.Int32>

- <xref:System.Int64>

- <xref:System.Single>

- <xref:System.String>

- <xref:System.Type>

- Każdy typ wyliczenia, <xref:System.Byte>którego <xref:System.Int16> <xref:System.Int32>typem <xref:System.Int64>bazowym jest , , lub .

Poniższy przykład definiuje `DescriptionAttribute` klasę, która <xref:System.Attribute>pochodzi od . Konstruktor klasy ma `Descriptor`parametr typu, więc klasa nie jest zgodna ze specyfikacją CLS. Należy zauważyć, że kompilator Języka C# emituje ostrzeżenie, ale kompilacji pomyślnie, podczas gdy kompilator języka Visual Basic nie emituje ani ostrzeżenie, ani błąd.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliantAttribute

Atrybut <xref:System.CLSCompliantAttribute> służy do wskazania, czy element programu jest zgodny ze specyfikacją języka wspólnego. Konstruktor <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> zawiera pojedynczy wymagany `isCompliant`parametr, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie emituje ostrzeżenia dla typów lub elementów członkowskich, które są jawnie uznane za niezgodne.

Deweloperzy składników <xref:System.CLSCompliantAttribute> mogą używać tego atrybutu na dwa sposoby:

- Aby zdefiniować części interfejsu publicznego udostępniane przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. Gdy atrybut jest używany do oznaczania określonych elementów programu jako zgodny chezb, jego użycie gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi, które są przeznaczone dla .NET Framework.

- Aby upewnić się, że interfejs publiczny biblioteki składników udostępnia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zazwyczaj wystawiają ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach kompilatory języka wymuszają reguły <xref:System.CLSCompliantAttribute> zgodne ze specyfikacją CLS, niezależnie od tego, czy atrybut jest używany. Na przykład definiowanie statycznego elementu członkowskiego w interfejsie narusza regułę CLS. W związku z tym `static` jeśli zdefiniujesz `Shared` (w języku C#) lub (w języku Visual Basic) element członkowski w interfejsie, kompilatory Języka C# i Visual Basic wyświetlają komunikat o błędzie i nie mogą skompilować aplikacji.

Atrybut <xref:System.CLSCompliantAttribute> jest oznaczony <xref:System.AttributeUsageAttribute> atrybutem o wartości <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Ta wartość umożliwia zastosowanie <xref:System.CLSCompliantAttribute> atrybutu do dowolnego elementu programu, w tym zestawów, modułów, typów (klas, struktur, wyliczeń, interfejsów i delegatów), elementów członkowskich typu (konstruktorów, metod, właściwości, pól i zdarzeń), parametrów, parametrów ogólnych i wartości zwracanych. Jednak w praktyce należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i nadal generują ostrzeżenia kompilatora, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.

Wartość atrybutu <xref:System.CLSCompliantAttribute> jest dziedziczona przez zawarte elementy programu. Na przykład jeśli złożenie jest oznaczone jako zgodne ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego typy zagnieżdżone i elementy członkowskie są również zgodne ze specyfikacją CLS.

Dziedziczoną zgodność można jawnie <xref:System.CLSCompliantAttribute> zastąpić, stosując atrybut do elementu programu zawartego. Na przykład można użyć <xref:System.CLSCompliantAttribute> atrybutu `isCompliant` z `false` wartością do zdefiniowania niezgodnego typu w zgodnym `isCompliant` zestawie `true` i można użyć atrybutu z wartością do zdefiniowania zgodnego typu w niezgodnym zestawie. Można również zdefiniować niezgodne elementy członkowskie w typie zgodnym. Jednak niezgodny typ nie może mieć zgodnych elementów członkowskich, `isCompliant` więc `true` nie można użyć atrybutu z wartością zastąpienia dziedziczenia z typu niezgodnego.

Podczas opracowywania składników, należy zawsze <xref:System.CLSCompliantAttribute> używać atrybutu, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj <xref:System.CLSCompliantAttribute> oznaczenia złożenia jako zgodnego ze specyfikacją CLS.

2. Oznacz wszystkie publicznie uwidocznione typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Oznacz wszystkie publicznie uwycone elementy członkowskie w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Podaj alternatywę zgodną ze specyfikacją CLS dla elementów członkowskich niezgodnych ze specyfikacją CLS.

Jeśli pomyślnie oznaczyłeś wszystkie niezgodne typy i elementy członkowskie, kompilator nie powinien emitować żadnych ostrzeżeń o niezgodnościach. Należy jednak wskazać, którzy członkowie nie są zgodni ze specyfikacją CLS i wymienić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.

W poniższym <xref:System.CLSCompliantAttribute> przykładzie użyto atrybutu do zdefiniowania zestawu zgodnego ze specyfikacją CLS i typu, `CharacterUtilities`który ma dwa elementy członkowskie niezgodne ze specyfikacją CLS. Ponieważ oba elementy członkowskie `CLSCompliant(false)` są oznaczone atrybutem, kompilator nie generuje żadnych ostrzeżeń. Klasa zapewnia również alternatywę zgodną ze specyfikacją CLS dla obu metod. Zwykle dodalibyśmy dwa przeciążenia do `ToUTF16` metody, aby zapewnić alternatywy zgodne ze specyfikacją CLS. Ponieważ jednak metody nie mogą być przeciążone na podstawie wartości zwracanej, nazwy metod zgodnych ze specyfikacją CLS różnią się od nazw metod niezgodnych.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Jeśli tworzysz aplikację, a nie bibliotekę (to znaczy, jeśli nie ujawniasz typów lub elementów członkowskich, które mogą być używane przez innych deweloperów aplikacji), zgodność cls elementów programu, które zużywa aplikacja są interesujące tylko wtedy, gdy język ich nie obsługuje . W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność językowa ma wiele możliwych znaczeń. Jedno znaczenie, które zostało omówione w artykule [Niezależność języka i składniki niezależne od języka,](../../docs/standard/language-independence-and-language-independent-components.md)polega na bezproblemowym konsumpcyjnym typach napisanych w jednym języku z aplikacji napisanej w innym języku. Drugie znaczenie, które jest przedmiotem tego artykułu, polega na łączeniu kodu napisanego w wielu językach w jeden zestaw .NET Framework.

W poniższym przykładzie przedstawiono współdziałanie międzyjęzykowe, tworząc bibliotekę klas o `NumericLib` `StringLib`nazwie Utilities.dll, która zawiera dwie klasy i . Klasa `NumericLib` jest napisana w języku C#, a klasa jest napisana `StringLib` w języku Visual Basic. Oto kod źródłowy stringutil.vb, który zawiera `ToTitleCase`jeden `StringLib` element członkowski, w swojej klasie.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Oto kod źródłowy dla NumberUtil.cs, `NumericLib` który definiuje klasę, `NearZero`która ma dwa elementy członkowskie i `IsEven` .

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Aby spakować dwie klasy w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego języka Visual Basic do modułu, użyj następującego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora języka Visual Basic, zobacz [Tworzenie z wiersza polecenia](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Aby skompilować plik kodu źródłowego Języka C# do modułu, użyj następującego polecenia:

```console
csc /t:module NumberUtil.cs
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora C#, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Następnie użyj [opcji konsolidatora,](/cpp/build/reference/linker-options) aby skompilować dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład następnie `NumericLib.NearZero` wywołuje `StringLib.ToTitleCase` i metody. Należy zauważyć, że zarówno kod języka Visual Basic, jak i kod Języka C# mają dostęp do metod w obu klasach.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Aby skompilować kod języka Visual Basic, użyj następującego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować z C#, zmień nazwę kompilatora z **vbc** na **csc**i zmień rozszerzenie pliku z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Zobacz też

- <xref:System.CLSCompliantAttribute>
