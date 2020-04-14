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
ms.openlocfilehash: 725884d8ab6d6d9009ad1cdd7bc185889cd5e485
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243066"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka

.NET Framework jest niezależny od języka. Oznacza to, że jako deweloper można rozwijać w jednym z wielu języków, które są przeznaczone dla .NET Framework, takich jak C#, C++/CLI, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL i Windows PowerShell. Można uzyskać dostęp do typów i członków bibliotek klas opracowanych dla programu .NET Framework bez konieczności znać język, w którym zostały pierwotnie napisane i bez konieczności przestrzegania konwencji języka oryginalnego. Jeśli jesteś deweloperem składników, składnik jest dostępny dla dowolnej aplikacji .NET Framework niezależnie od jego języka.

> [!NOTE]
> W tej pierwszej części tego artykułu omówiono tworzenie składników niezależnych od języka — czyli składników, które mogą być używane przez aplikacje napisane w dowolnym języku. Można również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego napisanego w wielu językach; zobacz [Interoperacyjność międzyjęzdań](#CrossLang) w drugiej części tego artykułu.

Aby w pełni współdziałać z innymi obiektami napisanymi w dowolnym języku, obiekty muszą uwidaczniać wywołującym tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest zdefiniowany przez specyfikację języka wspólnego (CLS), która jest zestawem reguł, które mają zastosowanie do wygenerowanych zestawów. Wspólna specyfikacja języka jest zdefiniowana w partycji I, klauzule 7 do 11 [ecma-335 Standard: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny ze specyfikacją języka wspólnego, jest gwarantowane, aby być zgodne ze specyfikacją CLS i można uzyskać dostęp z kodu w zestawach napisanych w dowolnym języku programowania, który obsługuje CLS. Można określić, czy składnik jest zgodny ze specyfikacją języka <xref:System.CLSCompliantAttribute> wspólnego w czasie kompilacji, stosując atrybut do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute).

W tym artykule:

- [Reguły zgodności z CLS](#Rules)

  - [Typy i podpisy elementów członkowskich](#Types)

  - [Konwencje nazewnictwa](#naming)

  - [Konwersja typu](#conversion)

  - [Tablice](#arrays)

  - [Interfejsy](#Interfaces)

  - [Wyliczenia](#enums)

  - [Typ członków w ogóle](#members)

  - [Dostępność dla członków](#MemberAccess)

  - [Typy ogólne i elementy członkowskie](#Generics)

  - [Konstruktorów](#ctors)

  - [Właściwości](#properties)

  - [Zdarzenia](#events)

  - [Overloads](#overloads)

  - [Wyjątki](#exceptions)

  - [Atrybuty](#attributes)

- [Atrybut CLSCompliantAttribute](#CLSAttribute)

- [Współdziałanie między językami](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>Reguły zgodności z CLS

W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS. Aby uzyskać pełną listę reguł, zobacz Partycja I, klauzula 11 [normy ECMA-335 Standard: Wspólna infrastruktura językowa](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Specyfikacja języka wspólnego omówiono każdą regułę zgodności z programem CLS, ponieważ ma ona zastosowanie do konsumentów (deweloperzy, którzy programowo uzyskują dostęp do składnika zgodnego ze specyfikacją CLS), struktur (deweloperzy, którzy używają kompilatora języka do tworzenia bibliotek zgodnych ze specyfikacją CLS) i extenderów (deweloperzy, którzy tworzą narzędzie, takie jak kompilator języka lub analizator kodu, który tworzy składniki zgodne ze specyfikacją CLS). W tym artykule koncentruje się na reguły, które mają zastosowanie do struktur. Należy jednak zauważyć, że niektóre reguły, które mają zastosowanie do extenderów mogą również dotyczyć zestawów, które są tworzone przy użyciu Reflection.Emit.

Aby zaprojektować składnik, który jest niezależny od języka, należy tylko zastosować reguły zgodności z CLS do interfejsu publicznego składnika. Twoja prywatna implementacja nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności z CLS mają zastosowanie tylko do interfejsu publicznego składnika, a nie do jego implementacji prywatnej.

Na przykład niepodpisane liczby całkowite <xref:System.Byte> inne niż nie są zgodne ze specyfikacją CLS. Ponieważ `Person` klasa w poniższym przykładzie `Age` udostępnia <xref:System.UInt16>właściwość typu, poniższy kod wyświetla ostrzeżenie kompilatora.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Można wprowadzić `Person` zgodność klasy CLS, zmieniając `Age` typ <xref:System.UInt16> właściwości <xref:System.Int16>z , który jest zgodny ze specyfikacją CLS, 16-bitową podpisaną 10 000 całkowitej liczby. Nie trzeba zmieniać typu pola prywatnego. `personAge`

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Interfejs publiczny biblioteki składa się z następujących elementów:

- Definicje klas publicznych.

- Definicje publicznych członków klas publicznych i definicje członków dostępnych dla klas pochodnych (czyli chronionych członków).

- Parametry i zwraca typy publicznych metod klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.

Reguły zgodności z CLS są wymienione w poniższej tabeli. Tekst przepisów pochodzi dosłownie z [ecma-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), który jest copyright 2012 przez Ecma International. Bardziej szczegółowe informacje na temat tych reguł znajdują się w poniższych sekcjach.

|Kategoria|Zobacz|Reguła|Numer reguły|
|--------------|---------|----------|-----------------|
|Ułatwienia dostępu|[Dostępność dla członków](#MemberAccess)|Dostępność nie może być zmieniana podczas zastępowania metod dziedziczonych, z wyjątkiem sytuacji, gdy zastępuje się metodą dziedziczoną z innego zestawu z ułatwieniami dostępu. `family-or-assembly` W takim przypadku zastąpienie ma dostępność. `family`|10|
|Ułatwienia dostępu|[Dostępność dla członków](#MemberAccess)|Widoczność i dostępność typów i elementów członkowskich jest taka, aby typy podpisu każdego członka były widoczne i dostępne za każdym razem, gdy sam członek jest widoczny i dostępny. Na przykład metoda publiczna, która jest widoczna poza jego zestawu nie ma argumentu, którego typ jest widoczny tylko w zestawie. Widoczność i dostępność typów tworzących skomlenie typu ogólnego używanego w podpisie dowolnego elementu członkowskiego muszą być widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny. Na przykład smowany typ ogólny obecny w podpisie elementu członkowskiego, który jest widoczny poza jego zestawem, nie może mieć ogólnego argumentu, którego typ jest widoczny tylko w zestawie.|12|
|Tablice|[Tablice](#arrays)|Tablice muszą posiadać elementy z typem zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy muszą mieć dolne granice zerowe. Tylko fakt, że element jest tablicą i typ elementu tablicy muszą być wymagane do rozróżnienia przeciążeń. Gdy przeciążenie opiera się na dwóch lub więcej typów tablicy typy elementów mają być nazwane typy.|16|
|Atrybuty|[Atrybuty](#attributes)|Atrybuty mają <xref:System.Attribute?displayProperty=nameWithType>być typu lub typu dziedziczącego po nim.|41|
|Atrybuty|[Atrybuty](#attributes)|CLS zezwala tylko na podzbiór kodowania atrybutów niestandardowych. Jedynymi typami, które pojawiają się w tych kodowaniach, <xref:System.Int16?displayProperty=nameWithType>są <xref:System.Int32?displayProperty=nameWithType> <xref:System.Int64?displayProperty=nameWithType>(patrz partycja IV): <xref:System.Type?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType> <xref:System.Boolean?displayProperty=nameWithType>, , <xref:System.Byte?displayProperty=nameWithType>, , , , <xref:System.Single?displayProperty=nameWithType>, , , <xref:System.Double?displayProperty=nameWithType>i każdy typ wyliczenia oparty na podstawowym typie całkowitym zgodnym ze specyfikacją CLS.|34|
|Atrybuty|[Atrybuty](#attributes)|CLS nie zezwala na publicznie widoczne wymagane`modreq`modyfikatory ( , zobacz Partycja`modopt`II), ale zezwala na opcjonalne modyfikatory ( , zobacz Partycja II) nie rozumie.|35|
|Konstruktorów|[Konstruktorów](#ctors)|Konstruktor obiektów wywołać niektóre konstruktora wystąpienia jego klasy podstawowej, zanim wystąpi dostęp do danych dziedziczonego wystąpienia. (Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).|21|
|Konstruktorów|[Konstruktorów](#ctors)|Konstruktor obiektów nie może być wywoływany, z wyjątkiem części tworzenia obiektu, a obiekt nie może być inicjowany dwukrotnie.|22|
|Wyliczenia|[Wyliczenia](#enums)|Podstawowym typem wyliczenia jest wbudowany typ liczby całkowitej CLS, nazwa pola jest "value__", a `RTSpecialName`pole to oznacza.|7|
|Wyliczenia|[Wyliczenia](#enums)|Istnieją dwa różne rodzaje wyliczenia, wskazywane <xref:System.FlagsAttribute?displayProperty=nameWithType> przez obecność lub brak atrybutu niestandardowego (zobacz partition IV Library). Jeden reprezentuje nazwane wartości całkowite; inne reprezentuje nazwane flagi bitowe, które mogą być łączone do generowania wartości bez nazwy. Wartość an `enum` nie jest ograniczona do określonych wartości.|8|
|Wyliczenia|[Wyliczenia](#enums)|Dosłowne pola statyczne wyliczenia mają typ samego wyliczenia.|9|
|Zdarzenia|[Zdarzenia](#events)|Metody, które implementują zdarzenie `SpecialName` są oznaczone w metadanych.|29|
|Zdarzenia|[Zdarzenia](#events)|Dostępność wydarzenia i jego akcesorów jest identyczna.|30|
|Zdarzenia|[Zdarzenia](#events)|Zarówno `add` `remove` metody, jak i metody zdarzenia są obecne lub nieobecne.|31|
|Zdarzenia|[Zdarzenia](#events)|Metody `add` `remove` i metody dla zdarzenia przyjmują jeden parametr, którego typ określa typ zdarzenia <xref:System.Delegate?displayProperty=nameWithType>i który pochodzi od .|32|
|Zdarzenia|[Zdarzenia](#events)|Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut, `SpecialName` o którym mowa w regule 29 CLS, jest ignorowany w odpowiednich porównaniach nazw i jest zgodny z regułami identyfikatorów.|33|
|Wyjątki|[Wyjątki](#exceptions)|Obiekty, które są generowane <xref:System.Exception?displayProperty=nameWithType> są typu lub typu dziedziczącego z niego. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.|40|
|Ogólne|[Zgodność z CLS: zasady](#Rules)|Reguły CLS mają zastosowanie tylko do tych części typu, które są dostępne lub widoczne poza definiującym zestawem.|1|
|Ogólne|[Zgodność z CLS: zasady](#Rules)|Elementy niezgodne z CLS nie są oznaczone jako zgodne ze specyfikacją CLS.|2|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typy zagnieżdżone muszą mieć co najmniej tyle parametrów ogólnych, co typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają według pozycji parametrom ogólnym w jego typie otaczającym.|42|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Nazwa typu ogólnego koduje liczbę parametrów typu zadeklarowanych na typie niezagnieżdżonego lub nowo wprowadzonych do typu, jeśli zagnieżdżone, zgodnie z regułami określonymi powyżej.|43|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typ ogólny należy ponownie zadeklarować wystarczające ograniczenia, aby zagwarantować, że wszelkie ograniczenia na typ podstawowy lub interfejsy będą spełnione przez ograniczenia typu ogólnego.|4444|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typy używane jako ograniczenia parametrów ogólnych same w sobie są zgodne ze specyfikacją CLS.|45|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Widoczność i dostępność elementów członkowskich (w tym typów zagnieżdżonych) w s wystąpieniu typu ogólnego uważa się za ograniczone do określonego wystąpienia, a nie deklaracji typu ogólnego jako całości. Przy założeniu, że zasady widoczności i dostępności cls reguły 12 nadal mają zastosowanie.|46|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej musi istnieć domyślna implementacja betonu (nieabstrakcjonowa).|47|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji metod niezgodnych z CLS w celu ich wdrożenia.|18|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól.|19|
|Elementy członkowskie|[Typ członków w ogóle](#members)|Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS.|36|
|Elementy członkowskie|--|Wartość dosłownego statycznego jest określona za pomocą metadanych inicjowania pola. Literał zgodny ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pól, która jest dokładnie tego `enum`samego typu co literał (lub typu źródłowego, jeśli literał jest ).|13|
|Elementy członkowskie|[Typ członków w ogóle](#members)|Ograniczenie vararg nie jest częścią CLS, a jedyną konwencją wywołującą obsługiwaną przez CLS jest standardowa konwencja wywoływania zarządzanego.|15|
|Konwencje nazewnictwa|[Konwencje nazewnictwa](#naming)|Zespoły są zgodne z załącznikiem 7 do raportu technicznego 15 standardu Unicode3.0 regulującego zestaw znaków, <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>które mogą rozpoczynać się i być włączone do identyfikatorów, dostępnych online pod adresem . Identyfikatory są w formacie kanonicznym zdefiniowanym przez formularz C normalizacji Unicode. Do celów CLS dwa identyfikatory są takie same, jeśli ich mapowania małych liter (określone przez Unicode locale-insensitive, jeden do jednego małe mapowania) są takie same. Oznacza to, że aby dwa identyfikatory, które mają być uznane za różne w cls, różnią się one nie tylko ich przypadkiem. Jednak w celu zastąpienia dziedziczonej definicji interfejsu wiersza polecenia wymaga dokładnego kodowania oryginalnej deklaracji.|4|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS muszą być odrębne niezależnie od rodzaju, z wyjątkiem przypadków, gdy nazwy są identyczne i rozpoznawane przez przeciążenie. Oznacza to, że podczas gdy CTSallows pojedynczy typ, aby użyć tej samej nazwy dla metody i pola, CLS nie.|5|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Pola i typy zagnieżdżone muszą być różne tylko przez porównanie identyfikatorów, nawet jeśli CTS umożliwia rozróżnianie odrębnych podpisów. Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikatorów) różnią się o więcej niż tylko typu zwracania, z wyjątkiem określonych w CLS reguły 39.|6|
|Przeciążenie|[Overloads](#overloads)|Tylko właściwości i metody mogą być przeciążone.|37|
|Przeciążenie|[Overloads](#overloads)|Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów `op_Implicit` `op_Explicit`ich parametrów, z wyjątkiem operatorów konwersji o nazwie i , które mogą być również przeciążone na podstawie ich typu zwracanego.|38|
|Przeciążenie|--|Jeśli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę i dla określonego zestawu wystąpienia typu mają te same typy parametrów i zwracanych, wszystkie te metody są semantycznie równoważne w tych wystąpieniach typu.|48|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|<xref:System.Object?displayProperty=nameWithType>jest zgodny ze specyfikacją CLS. Każda inna klasa zgodna ze specyfikacją CLS dziedziczy po klasie zgodnej ze specyfikacją CLS.|23|
|Właściwości|[Właściwości](#properties)|The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.|24|
|Właściwości|[Właściwości](#properties)|Akcesory właściwości muszą być statyczne, wszystkie są wirtualne lub wszystkie będą instancja.|26|
|Właściwości|[Właściwości](#properties)|Typ właściwości jest typem zwracanym gettera i typem ostatniego argumentu ustawiacza. Typy parametrów właściwości są typami parametrów do getter i typy wszystkich, ale końcowy parametr ustawiacza. Wszystkie te typy muszą być zgodne ze specyfikacją CLS i nie są objęte wskaźnikami zarządzanymi (tj. nie są przekazywane przez odniesienie).|27|
|Właściwości|[Właściwości](#properties)|Właściwości muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut, `SpecialName` o którym mowa w regule 24 CLS, jest ignorowany w odpowiednich porównaniach nazw i jest zgodny z regułami identyfikatorów. Właściwość musi mieć metodę metody metody ustalania, metodę ustawiacza lub obie te właściwości.|28|
|Konwersja typu|[Konwersja typu](#conversion)|Jeżeli `op_Implicit` którykolwiek `op_Explicit` lub zostanie dostarczony, należy zapewnić alternatywny sposób zapewnienia przymusu.|39|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|Typy wartości pudełkowych nie są zgodne ze specyfikacją CLS.|3|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|Wszystkie typy pojawiające się w podpisie muszą być zgodne ze specyfikacją CLS. Wszystkie typy tworzące skomlenie typu ogólnego, które zostały skomponowane, muszą być zgodne ze specyfikacją CLS.|11|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|Wpisane odwołania nie są zgodne ze specyfikacją CLS.|14|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|Niezarządzane typy wskaźników nie są zgodne ze specyfikacją CLS.|17|
|Types|[Typ i typ podpisów elementów członkowskich](#Types)|Klasy, typy wartości i interfejsy zgodne ze specyfikacją CLS nie wymagają implementacji elementów członkowskich niezgodnych ze specyfikacją CLS.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich

Typ <xref:System.Object?displayProperty=nameWithType> jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typu .NET Framework. Dziedziczenie w .NET Framework jest albo niejawne (na <xref:System.String> przykład <xref:System.Object> klasa niejawnie dziedziczy <xref:System.Globalization.CultureNotFoundException> z klasy) lub <xref:System.ArgumentException> jawne (na przykład <xref:System.SystemException> klasa jawnie dziedziczy z <xref:System.Exception> klasy, która jawnie dziedziczy z klasy, która jawnie dziedziczy z klasy). Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy musi być również zgodny ze specyfikacją CLS.

Poniższy przykład przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje klasę podstawową, `Counter` która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika. Ponieważ klasa zapewnia funkcjonalność licznika przez zawijanie niepodpisanej liczby całkowitej, klasa jest oznaczona jako niezgodna z CLS. W rezultacie klasa pochodna `NonZeroCounter`, również nie jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Wszystkie typy, które pojawiają się w podpisach elementów członkowskich, w tym typ zwracany metody lub typ właściwości, muszą być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:

- Wszystkie typy, które tworzą skonkreponowany typ ogólny musi być zgodny ze specyfikacją CLS.

- Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.

[System typy typowej](../../docs/standard/base-types/common-type-system.md) platformy .NET Framework zawiera szereg wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie zakodowane w metadanych zestawu. Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

|Typ zgodny ze specyfikacją CLS|Opis|
|-------------------------|-----------------|
|<xref:System.Byte>|8-bitowa niepodpisana czkawce całkowitej|
|<xref:System.Int16>|16-bitowa podpisana integer|
|<xref:System.Int32>|32-bitowa podpisana integer|
|<xref:System.Int64>|64-bitowa podpisana integer|
|<xref:System.Single>|Jednoprecyzyjne wartości zmiennoprzecinkowej|
|<xref:System.Double>|Podwójna precyzja wartości zmiennoprzecinkowej|
|<xref:System.Boolean>|`true`lub `false` typ wartości|
|<xref:System.Char>|Zakodowana jednostka kodowa UTF-16|
|<xref:System.Decimal>|Liczba dziesiętna nieprzecinkowa|
|<xref:System.IntPtr>|Wskaźnik lub uchwyt o rozmiarze zdefiniowanym przez platformę|
|<xref:System.String>|Kolekcja obiektów zero, jeden <xref:System.Char> lub więcej obiektów|

Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.

|Typ niezgodny|Opis|Alternatywa zgodna ze specyfikacją CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8-bitowy podpisany typ danych całkowitej|<xref:System.Int16>|
|<xref:System.TypedReference>|Wskaźnik do obiektu i jego typu środowiska wykonawczego|Brak|
|<xref:System.UInt16>|16-bitowa niepodpisana czkawce całkowitej|<xref:System.Int32>|
|<xref:System.UInt32>|32-bitowa niepodpisana gnilizna|<xref:System.Int64>|
|<xref:System.UInt64>|64-bitowa niepodpisana całkowitej liczby|<xref:System.Int64>(może się <xref:System.Numerics.BigInteger>przelewać), lub<xref:System.Double>|
|<xref:System.UIntPtr>|Niepodpisany wskaźnik lub uchwyt|<xref:System.IntPtr>|

Biblioteka klas .NET Framework lub inna biblioteka klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

- Typy wartości pudełkowych. Poniższy przykład języka C# tworzy klasę, `int*` która `Value`ma właściwość publiczną typu o nazwie . Ponieważ `int*` jest typem wartości w pudełku, kompilator oznacza go jako niezgodny ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Wpisane odwołania, które są konstrukcjami specjalnymi, które zawierają odwołanie do obiektu i odwołanie do typu. Wpisane odwołania są reprezentowane w .NET <xref:System.TypedReference> Framework przez klasę.

Jeśli typ nie jest zgodny ze specyfikacją <xref:System.CLSCompliantAttribute> CLS, `isCompliant` należy `false` zastosować atrybut o wartości do niego. Aby uzyskać więcej informacji, zobacz [CLSCompliantAttribute](#CLSAttribute) sekcji atrybutu.

Poniższy przykład ilustruje problem zgodności cls w podpisie metody i w wystąpieniu typu ogólnego. Definiuje `InvoiceItem` klasę z właściwością typu <xref:System.UInt32>, właściwością `Nullable(Of UInt32)`typu i konstruktorem <xref:System.UInt32> `Nullable(Of UInt32)`z parametrami typu i . Otrzymasz cztery ostrzeżenia kompilatora podczas próby skompilowania w tym przykładzie.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Aby wyeliminować ostrzeżenia kompilatora, zastąp typy niezgodne ze specyfikacją CLS w interfejsie `InvoiceItem` publicznym zgodnymi typami:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Oprócz określonych typów wymienionych, niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Należą do nich niezarządzane typy wskaźników i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczby całkowitych.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Dla klas abstrakcyjnych zgodnych ze specyfikacją `abstract` CLS (czyli klas oznaczonych jako w języku C# lub jak `MustInherit` w języku Visual Basic), wszyscy członkowie klasy muszą być również zgodne ze specyfikacją CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ niektóre języki programowania są niewrażliwe na wielkości, identyfikatory (takie jak nazwy obszarów nazw, typów i elementów członkowskich) muszą się różnić o więcej niż przypadek. Dwa identyfikatory są uważane za równoważne, jeśli ich małe przywzorowania są takie same. Poniższy przykład języka C# definiuje `Person` `person`dwie klasy publiczne i . Ponieważ różnią się one tylko w zależności od przypadku, kompilator języka C# oznacza je jako niezgodne ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Identyfikatory języka programowania, takie jak nazwy obszarów nazw, typów i elementów członkowskich, muszą być zgodne ze [standardem Unicode 3.0, raportem technicznym 15, załącznikiem 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

- Pierwszym znakiem identyfikatora może być dowolna wielka litera Unicode, mała litera, litera tytułu, litera modyfikatora, inna litera lub cyfra litery. Aby uzyskać informacje na temat kategorii <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> znaków Unicode, zobacz wyliczenie.

- Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszego znaku, a także mogą zawierać znaki bez odstępów, odstępy łączące znaczniki, liczby dziesiętne, znaki interpunkcyjne łącznika i kody formatowania.

Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na formularz C normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanych przez UTF-16. Sekwencje znaków, które produkują te same jednostki kodu w formularzu C normalizacji Unicode nie są zgodne ze specyfikacją CLS. Poniższy przykład definiuje właściwość o nazwie `Å`, która składa się ze znaku ANGSTROM SIGN `Å`(U + 212B) i drugą właściwość o nazwie , która składa się ze znaku ŁACIŃSKIEJ WIELKIEJ LITERY A Z PIERŚCIENIEM POWYŻEJ (U + 00C5). Kompilatory języka C# i Visual Basic oflagowalniczy kod źródłowy jako niezgodne ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Nazwy elementów członkowskich w określonym zakresie (takie jak przestrzenie nazw w zestawie, typy w obszarze nazw lub elementy członkowskie w obrębie typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane przez przeciążenie. To wymaganie jest bardziej rygorystyczne niż w systemie typu wspólnego, który umożliwia wielu elementów członkowskich w zakresie mają identyczne nazwy, tak długo, jak są one różne rodzaje elementów członkowskich (na przykład jeden jest metodą, a jeden jest polem). W szczególności dla elementów członkowskich typu:

- Pola i typy zagnieżdżone są rozróżniane tylko przez nazwę.

- Metody, właściwości i zdarzenia, które mają taką samą nazwę musi różnić się o więcej niż tylko zwracany typ.

Poniższy przykład ilustruje wymóg, że nazwy elementów członkowskich muszą być unikatowe w ich zakresie. Definiuje klasę o `Converter` nazwie, która `Conversion`zawiera cztery elementy o nazwie . Trzy są metody, a jeden jest właściwością. Metoda, która <xref:System.Int64> zawiera parametr jest unikatowo nazwany, <xref:System.Int32> ale dwie metody z parametrem nie są, ponieważ zwracana wartość nie jest uważany za część podpisu członka. Właściwość `Conversion` również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążone metody.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Poszczególne języki zawierają unikatowe słowa kluczowe, więc języki, które są kierowane na środowisko uruchomieniowe języka wspólnego musi również zapewnić pewien mechanizm odwoływania się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic. Jednak poniższy przykład języka Visual Basic jest w `case` stanie `case` odróżnić klasę o nazwie od słowa kluczowego przy użyciu nawiasów klamrowych otwierania i zamykania. W przeciwnym razie w przykładzie zostanie wyświetlony komunikat o błędzie "Słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można go skompilować.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Poniższy przykład języka C# jest `case` w stanie `@` utworzyć wystąpienie klasy przy użyciu symbolu, aby odróżnić identyfikator od słowa kluczowego języka. Bez niego kompilator języka C# wyświetli dwa komunikaty o błędach, "Typ oczekiwany" i "Nieprawidłowe wyrażenie terminu 'case'".

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Konwersja typu

Specyfikacja języka wspólnego definiuje dwa operatory konwersji:

- `op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub precyzji. Na przykład <xref:System.Decimal> struktura zawiera przeciążony `op_Implicit` operator do konwersji <xref:System.Char> wartości <xref:System.Decimal> typów i wartości całkowitych na wartości.

- `op_Explicit`, który jest używany do zawężenia konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzji. Na przykład <xref:System.Decimal> struktura zawiera przeciążony `op_Explicit` operator <xref:System.Double> do <xref:System.Single> <xref:System.Decimal> konwersji i <xref:System.Decimal> wartości do <xref:System.Double>i <xref:System.Single>do <xref:System.Char>konwersji wartości do wartości całkowitych, , i .

Jednak nie wszystkie języki obsługują przeciążenie operatora lub definicję operatorów niestandardowych. Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonywania konwersji. Zalecamy podanie `From`metod `To` *Xxx* i *Xxx.*

Poniższy przykład definiuje konwersje niejawne i jawne zgodne ze specyfikacją CLS. Tworzy `UDouble` klasę, która reprezentuje podpisaną podwójną precyzję, liczba zmiennoprzecinowa. Przewiduje niejawne `UDouble` konwersje <xref:System.Double> z do i `UDouble` <xref:System.Single>dla <xref:System.Double> `UDouble`konwersji <xref:System.Single> `UDouble`jawnych z do , do , do i do . `ToDouble` Definiuje również metodę jako alternatywę dla niejawnego `ToSingle` `FromDouble`operatora `FromSingle` konwersji i , i metody jako alternatywy dla operatorów konwersji jawne.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Tablice

Tablice zgodne ze specyfikacją CLS są zgodne z następującymi regułami:

- Wszystkie wymiary tablicy musi mieć dolną granicę zero. Poniższy przykład tworzy tablicę niezgodną z CLS z dolną granicą jednego. Należy zauważyć, że pomimo <xref:System.CLSCompliantAttribute> obecności atrybutu kompilator nie wykrywa, `Numbers.GetTenPrimes` że tablica zwrócona przez metodę nie jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS. Poniższy przykład definiuje dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS. Pierwszy zwraca tablicę <xref:System.UInt32> wartości. Drugi zwraca <xref:System.Object> tablicę, <xref:System.Int32> <xref:System.UInt32> która zawiera i wartości. Chociaż kompilator identyfikuje pierwszą tablicę jako <xref:System.UInt32> niezgodną ze względu na jej typ, nie rozpoznaje, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Przeciążenie rozpoznawania metod, które mają parametry tablicy opiera się na fakcie, że są one tablice i ich typ elementu. Z tego powodu następująca definicja `GetSquares` przeciążona metoda jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Interfejsy

Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji). Interfejs zgodny ze specyfikacją CLS nie może mieć żadnej z następujących czynności:

- Metody statyczne lub pola statyczne. Kompilatory języka C# i Visual Basic generują błędy kompilatora, jeśli zdefiniujesz statyczny element członkowski w interfejsie.

- Pola. Kompilatory języka C# i Visual Basic generują błędy kompilatora, jeśli zdefiniowano pole w interfejsie.

- Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu `INumber.GetUnsigned`zawiera metodę , która jest oznaczona jako niezgodna ze specyfikacją CLS. W tym przykładzie generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Z powodu tej reguły typy zgodne ze specyfikacją CLS nie są wymagane do implementowania elementów członkowskich niezgodnych ze specyfikacją CLS. Jeśli struktura zgodna ze specyfikacją CLS udostępnia klasę, która implementuje interfejs niezgodny z CLS, powinna również zapewnić konkretne implementacje wszystkich elementów członkowskich niezgodnych ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na dostarczanie oddzielnych implementacji elementów członkowskich, które mają taką samą nazwę i podpis w wielu interfejsach.  Zarówno C# i Visual Basic obsługuje [jawne implementacje interfejsu,](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) aby zapewnić różne implementacje o identycznych nazwach metod. Visual Basic obsługuje `Implements` również słowa kluczowego, który umożliwia jawnie wyznaczyć, który interfejs i element członkowski implementuje określonego elementu członkowskiego. Poniższy przykład ilustruje ten `Temperature` scenariusz, definiując klasę, która implementuje `ICelsius` i `IFahrenheit` interfejsy jako jawne implementacje interfejsu.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Wyliczenia

Wyliczenia zgodne ze specyfikacją CLS muszą być zgodne z tymi regułami:

- Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna ze<xref:System.Byte> <xref:System.Int16>specyfikacją CLS ( , , , <xref:System.Int32>, lub <xref:System.Int64>). Na przykład poniższy kod próbuje zdefiniować wyliczenie, którego podstawowym typem jest <xref:System.UInt32> i generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Typ wyliczenia musi mieć jedno `Value__` pole instancji o <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> nazwie, które jest oznaczone atrybutem. Dzięki temu można odwoływać się do wartości pola niejawnie.

- Wyliczenie zawiera dosłowne pola statyczne, których typy odpowiadają typowi samego wyliczenia. Na przykład, jeśli `State` zdefiniowano wyliczenie `State.On` `State.Off`z `State.On` `State.Off` wartościami i , i są `State`zarówno dosłowne pola statyczne, których typ jest .

- Istnieją dwa rodzaje wyliczenia:

  - Wyliczenie, które reprezentuje zestaw wzajemnie wykluczające się, nazwane wartości całkowite. Ten typ wyliczenia jest wskazywany <xref:System.FlagsAttribute?displayProperty=nameWithType> przez brak atrybutu niestandardowego.

  - Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć w celu wygenerowania wartości bez nazwy. Ten typ wyliczenia jest wskazywany <xref:System.FlagsAttribute?displayProperty=nameWithType> przez obecność atrybutu niestandardowego.

  Aby uzyskać więcej informacji, <xref:System.Enum> zobacz dokumentację struktury.

- Wartość wyliczenia nie jest ograniczona do zakresu jego określonych wartości. Innymi słowy zakres wartości w wyliczeniu jest zakres jego wartości podstawowej. Za pomocą <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody można określić, czy określona wartość jest członkiem wyliczenia.

<a name="members"></a>

### <a name="type-members-in-general"></a>Typ członków w ogóle

Specyfikacja języka wspólnego wymaga, aby wszystkie pola i metody były dostępne jako członkowie określonej klasy. W związku z tym globalne pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane oprócz typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz dołączyć pole globalne lub metodę w kodzie źródłowym, kompilatory języka C# i Visual Basic wygenerują błąd kompilatora.

Specyfikacja języka wspólnego obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje konwencji i metod wywoływania niezarządzanego z `varargs` listami argumentów zmiennych oznaczonych słowem kluczowym. W przypadku list argumentów zmiennych zgodnych ze <xref:System.ParamArrayAttribute> standardową konwencją wywoływania zarządzanego `params` należy użyć atrybutu `ParamArray` lub implementacji poszczególnych języków, takich jak słowo kluczowe w języku C# i słowo kluczowe w języku Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Dostępność dla członków

Zastępowanie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego. Na przykład metoda publiczna w klasie podstawowej nie może zostać zastąpiona przez metodę prywatną w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (w języku `Protected Friend` C#) lub (w języku Visual Basic) element członkowski w jednym zestawie, który jest zastępowane przez typ w innym zestawie. W takim przypadku dostępność zastąpienia jest `Protected`.

Poniższy przykład ilustruje błąd, <xref:System.CLSCompliantAttribute> który jest generowany, gdy `true`atrybut jest ustawiony na , i `Human`, który jest klasą pochodną `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznych na prywatnych. Przykład kompiluje pomyślnie, jeśli jego dostępność zostanie zmieniona na public.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Typy w podpisie członka musi być dostępny, gdy ten element członkowski jest dostępny. Oznacza to na przykład, że publiczny element członkowski nie może zawierać parametru, którego typ jest prywatny, chroniony lub wewnętrzny. Poniższy przykład ilustruje błąd kompilatora, który powoduje, gdy konstruktor `StringWrapper` klasy udostępnia wewnętrzną `StringOperationType` wartość wyliczenia, która określa, jak wartość ciągu powinny być opakowane.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Typy ogólne i elementy członkowskie

Typy zagnieżdżone zawsze mają co najmniej tyle parametrów ogólnych, co ich typ otaczający. Odpowiadają one pozycjonowaniu parametrom ogólnym w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrami typu ogólnego typu zawierającego a jego typami zagnieżdżenia może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie `Outer<T>` typ ogólny zawiera `Inner1A` dwie `Inner1B<U>`klasy zagnieżdżone i . Wywołania `ToString` metody, które każda klasa <xref:System.Object.ToString%2A?displayProperty=nameWithType>dziedziczy z , pokaż, że każda klasa zagnieżdżona zawiera parametry typu jej zawierającej klasy.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Nazwy typów ogólnych są kodowane w *nazwie\`* formularza n , \` gdzie *nazwa* jest nazwą typu, jest literałem znakowym, a *n* jest liczbą parametrów zadeklarowanych dla typu lub, w przypadku zagnieżdżonych typów ogólnych, liczbą nowo wprowadzonych parametrów typu. To kodowanie nazw typów ogólnych jest przede wszystkim interesujące dla deweloperów, którzy używają odbicia, aby uzyskać dostęp do typów ogólnych skargi CLS w bibliotece.

Jeśli ograniczenia są stosowane do typu ogólnego, wszystkie typy używane jako ograniczenia muszą być również zgodne ze specyfikacją CLS. Poniższy przykład definiuje klasę `BaseClass` o nazwie, która nie jest `BaseCollection` zgodna ze specyfikacją `BaseClass`CLS, oraz klasę ogólną o nazwie, której parametr typu musi pochodzić od . Ale `BaseClass` ponieważ nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Jeśli typ ogólny pochodzi od typu podstawowego rodzajowego, musi ponownie zadeklarować wszelkie ograniczenia, dzięki czemu może zagwarantować, że ograniczenia na typ podstawowy są również spełnione. Poniższy przykład `Number<T>` definiuje, który może reprezentować dowolny typ liczbowy. Definiuje również `FloatingPoint<T>` klasę, która reprezentuje wartość zmiennoprzecinkową. Jednak kod źródłowy nie można skompilować, ponieważ `Number<T>` nie stosuje ograniczenia na (że T musi być typem wartości) do `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Przykład kompiluje pomyślnie, jeśli ograniczenie `FloatingPoint<T>` jest dodawany do klasy.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Specyfikacja języka wspólnego nakłada konserwatywny model wystąpienia dla zagnieżdżonych typów i chronionych elementów członkowskich. Otwarte typy ogólne nie mogą udostępniać pól ani elementów członkowskich z podpisami zawierającymi określone wystąpienie zagnieżdżonego, chronionego typu ogólnego. Typy niegeneralne, które rozszerzają określone wystąpienie ogólnej klasy podstawowej lub interfejsu, nie mogą udostępniać pól ani elementów członkowskich z podpisami zawierającymi inne wystąpienie zagnieżdżonego, chronionego typu ogólnego.

Poniższy przykład definiuje typ `C1<T>` ogólny `C1(Of T)` (lub w języku Visual Basic) i klasę chroniona `C1<T>.N` (lub `C1(Of T).N` w języku Visual Basic). `C1<T>`ma dwie `M1` metody, i `M2`. Jednak `M1` nie jest zgodny ze `C1<int>.N` specyfikacją CLS, `C1(Of Integer).N`ponieważ próbuje\<zwrócić (lub) `C1(Of T)`obiekt z C1 T> (lub ). Druga klasa, `C2`, pochodzi `C1<long>` od `C1(Of Long)`(lub ). Posiada dwie `M3` metody, `M4`i . `M3`nie jest zgodny ze specyfikacją CLS, `C1(Of Integer).N`ponieważ próbuje zwrócić `C1<long>` `C1<int>.N` (lub) obiekt z podklasy . Należy zauważyć, że kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie visual basic wyświetla błąd `M4`podczas próby skompilowania .

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Konstruktorów

Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z tymi regułami:

- Konstruktor klasy pochodnej musi wywołać konstruktora wystąpienia swojej klasy podstawowej, zanim uzyska dostęp do danych dziedziczonego wystąpienia. To wymaganie wynika z faktu, że konstruktory klasy podstawowej nie są dziedziczone przez ich klas pochodnych. Ta reguła nie ma zastosowania do struktur, które nie obsługują dziedziczenia bezpośredniego.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności z CLS, jak pokazano w poniższym przykładzie. Tworzy `Doctor` klasę, która jest pochodną `Person` klasy, `Doctor` ale klasa `Person` nie można wywołać konstruktora klasy, aby zainicjować pola dziedziczone wystąpienie.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nie można wywołać konstruktora obiektów, z wyjątkiem utworzenia obiektu. Ponadto obiektu nie można zainicjować dwukrotnie. Na przykład oznacza <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> to, że i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> deserializacji metody, takie jak nie można wywołać konstruktorów.

<a name="properties"></a>

### <a name="properties"></a>Właściwości

Właściwości w typach zgodnych ze specyfikacją CLS muszą być zgodne z tymi regułami:

- Właściwość musi mieć ustawiacz, getter lub obu. W zestawie są one implementowane jako metody specjalne, co oznacza, że będą `get_`wyświetlane jako oddzielne metody (metoda gettera `SpecialName` nosi nazwę *propertyname,* a setter jest `set_` *nazwami propertyname)* oznaczonych jako metadane zestawu. Kompilatory języka C# i Visual Basic automatycznie wymuszają tę regułę bez konieczności stosowania atrybutu. <xref:System.CLSCompliantAttribute>

- Typ właściwości jest typem zwracanym właściwości getter i ostatnim argumentem ustawiacza. Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisane do właściwości przez odwołanie (oznacza to, że nie mogą być wskaźnikami zarządzanymi).

- Jeśli właściwość ma zarówno metody ustawiacza, jak i ustawiacza, muszą one być zarówno wirtualne, zarówno statyczne, jak i obu wystąpień. Kompilatory języka C# i Visual Basic automatycznie wymuszają tę regułę za pomocą składni definicji właściwości.

<a name="events"></a>

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przez jego nazwę i jego typ. Typ zdarzenia jest pełnomocnikiem, który jest używany do wskazania zdarzenia. Na przykład <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie jest <xref:System.ResolveEventHandler>typu . Oprócz samego zdarzenia trzy metody o nazwach opartych na nazwie zdarzenia zapewniają `SpecialName` implementację zdarzenia i są oznaczone jako metadane zestawu:

- Metoda dodawania programu obsługi `add_`zdarzeń o nazwie *EventName*. Na przykład metoda subskrypcji zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> dla `add_AssemblyResolve`zdarzenia nosi nazwę .

- Metoda usuwania programu obsługi zdarzeń `remove_`o nazwie *EventName*. Na przykład metoda usuwania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia `remove_AssemblyResolve`nosi nazwę .

- Metoda wskazująca, że zdarzenie miało `raise_`miejsce, o nazwie *EventName*.

> [!NOTE]
> Większość reguł specyfikacji języka wspólnego dotyczące zdarzeń są implementowane przez kompilatory języka i są przejrzyste dla deweloperów składników.

Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć taką samą dostępność. Wszystkie muszą być również statyczne, wystąpienie lub wirtualne. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody dodawania i usuwania muszą być obecne lub oba muszą być nieobecne.

Poniższy przykład definiuje klasę zgodną `Temperature` z CLS `TemperatureChanged` o nazwie, która wywołuje zdarzenie, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. Klasa `Temperature` jawnie definiuje `raise_TemperatureChanged` metodę, dzięki czemu można selektywnie wykonywać programy obsługi zdarzeń.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Overloads

Specyfikacja wspólnego języka nakłada następujące wymagania na przeciążonych elementów członkowskich:

- Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu dowolnego parametru. Wywołanie konwencji, typu zwracania, modyfikatorów niestandardowych stosowanych do metody lub jej parametru i czy parametry są przekazywane przez wartość lub odwołanie nie są brane pod uwagę podczas rozróżniania przeciążeń. Na przykład zobacz kod wymagania, że nazwy muszą być unikatowe w zakresie w sekcji [Konwencje nazewnictwa.](#naming)

- Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

- Metody ogólne mogą być przeciążone na podstawie liczby ich parametrów ogólnych.

> [!NOTE]
> I `op_Explicit` `op_Implicit` operatory są wyjątki od reguły, że zwracana wartość nie jest uważany za część podpisu metody dla rozpoznawania przeciążenia. Te dwa operatory mogą być przeciążone na podstawie ich parametrów i ich wartości zwracanej.

<a name="exceptions"></a>

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątków muszą <xref:System.Exception?displayProperty=nameWithType> pochodzić od lub <xref:System.Exception?displayProperty=nameWithType>z innego typu pochodnego . Poniższy przykład ilustruje błąd kompilatora, `ErrorClass` który powoduje, gdy klasa niestandardowa o nazwie jest używana do obsługi wyjątków.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Aby rozwiązać ten `ErrorClass` błąd, klasa <xref:System.Exception?displayProperty=nameWithType>musi dziedziczyć z . Ponadto `Message` właściwość musi zostać zastąpiona. Poniższy przykład poprawia te błędy, `ErrorClass` aby zdefiniować klasę, która jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Atrybuty

In.NET framework zestawy, atrybuty niestandardowe zapewniają rozszerzalny mechanizm przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programowania, takich jak zestawy, typy, elementy członkowskie i parametry metody. Atrybuty niestandardowe <xref:System.Attribute?displayProperty=nameWithType> muszą pochodzić od <xref:System.Attribute?displayProperty=nameWithType>typu pochodnego lub od niego.

Poniższy przykład narusza tę regułę. Definiuje `NumericAttribute` klasę, która nie pochodzi <xref:System.Attribute?displayProperty=nameWithType>od . Należy zauważyć, że wynik błędu kompilatora tylko wtedy, gdy atrybut niezgodny ze specyfikacją CLS jest stosowany, a nie po zdefiniowaniu klasy.

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

- Dowolny typ wyliczenia, <xref:System.Byte>którego <xref:System.Int16> <xref:System.Int32>podstawowym <xref:System.Int64>typem jest , , lub .

Poniższy przykład definiuje `DescriptionAttribute` klasę, która <xref:System.Attribute>wywodzi się z . Konstruktor klasy ma parametr `Descriptor`typu, więc klasa nie jest zgodna ze specyfikacją CLS. Należy zauważyć, że kompilator języka C# emituje ostrzeżenie, ale kompiluje pomyślnie, podczas gdy kompilator języka Visual Basic nie emituje ani ostrzeżenie, ani błąd.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliantAttribute

Atrybut <xref:System.CLSCompliantAttribute> jest używany do wskazania, czy element programu jest zgodny ze specyfikacją języka wspólnego. Konstruktor <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29> zawiera pojedynczy wymagany `isCompliant`parametr, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie. Kompilator nie emituje ostrzeżeń dla typów lub elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.

Deweloperzy składników <xref:System.CLSCompliantAttribute> mogą używać tego atrybutu na dwa sposoby:

- Aby zdefiniować części interfejsu publicznego udostępniane przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS. Gdy atrybut jest używany do oznaczania poszczególnych elementów programu jako zgodnych ze specyfikacją CLS, jego użycie gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi, które są przeznaczone dla programu .NET Framework.

- Aby upewnić się, że interfejs publiczny biblioteki składników udostępnia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zazwyczaj wydają ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach kompilatory języka wymuszają <xref:System.CLSCompliantAttribute> reguły zgodne ze specyfikacją CLS, niezależnie od tego, czy atrybut jest używany. Na przykład definiowanie statycznego elementu członkowskiego w interfejsie narusza regułę CLS. W związku z tym `static` jeśli zdefiniujesz `Shared` (w języku C#) lub (w języku Visual Basic) element członkowski w interfejsie, kompilatory języka C# i Visual Basic wyświetlić komunikat o błędzie i nie można skompilować aplikacji.

Atrybut <xref:System.CLSCompliantAttribute> jest oznaczony atrybutem <xref:System.AttributeUsageAttribute> o wartości . <xref:System.AttributeTargets.All?displayProperty=nameWithType> Ta wartość umożliwia zastosowanie <xref:System.CLSCompliantAttribute> atrybutu do dowolnego elementu programu, w tym zestawów, modułów, typów (klas, struktur, wyliczeń, interfejsów i delegatów), elementów członkowskich typu (konstruktorów, metod, właściwości, pól i zdarzeń), parametrów, parametrów ogólnych i wartości zwracanych. Jednak w praktyce należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i nadal generują ostrzeżenia kompilatora za każdym razem, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.

Wartość atrybutu <xref:System.CLSCompliantAttribute> jest dziedziczona przez zawarte elementy programu. Na przykład jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.

Można jawnie zastąpić dziedziczoną zgodność, stosując <xref:System.CLSCompliantAttribute> atrybut do elementu programu zawartego. Na przykład można użyć <xref:System.CLSCompliantAttribute> atrybutu `isCompliant` z `false` wartością do zdefiniowania niezgodnego typu w zwymiernym `isCompliant` zestawie `true` i można użyć atrybutu z wartością do zdefiniowania zgodnego typu w zestawie niezgodnym. Można również zdefiniować niezgodne elementy członkowskie w typie zgodnym. Jednak typ niezgodny nie może mieć zgodnych elementów członkowskich, `isCompliant` więc `true` nie można użyć atrybutu z wartością do zastąpienia dziedziczenia z typu niezgodnego.

Podczas tworzenia składników, należy zawsze <xref:System.CLSCompliantAttribute> używać atrybutu, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj, <xref:System.CLSCompliantAttribute> aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.

2. Oznacz wszystkie publicznie widoczne typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Oznacz wszystkie publicznie narażone elementy członkowskie w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Podaj alternatywę ze zgodnością ze specyfikacją CLS dla elementów członkowskich niezgodnych ze specyfikacją CLS.

Jeśli pomyślnie oznaczyłeś wszystkie niezgodne typy i elementy członkowskie, kompilator nie powinien emitować żadnych ostrzeżeń o niezgodności. Należy jednak wskazać, które elementy członkowskie nie są zgodne ze specyfikacją CLS i wyświetlić w dokumentacji produktu ich alternatywy zgodne ze specyfikacją CLS.

W poniższym przykładzie użyto atrybutu <xref:System.CLSCompliantAttribute> do zdefiniowania zestawu `CharacterUtilities`zgodnego ze specyfikacją CLS i typu , który ma dwa elementy członkowskie niezgodne ze specyfikacją CLS. Ponieważ oba elementy członkowskie `CLSCompliant(false)` są oznaczone atrybutem, kompilator nie generuje żadnych ostrzeżeń. Klasa zawiera również alternatywę ze specyfikacją CLS dla obu metod. Zwykle po prostu dodać dwa przeciążenia do `ToUTF16` metody, aby zapewnić alternatywy zgodne ze specyfikacją CLS. Jednak ponieważ metody nie mogą być przeciążone na podstawie wartości zwracanej, nazwy metod zgodnych z CLS różnią się od nazw metod niezgodnych.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Jeśli tworzysz aplikację, a nie bibliotekę (oznacza to, że nie są udostępnianie typów lub członków, które mogą być używane przez innych deweloperów aplikacji), zgodność CLS elementów programu, które zużywa aplikacji są interesujące tylko wtedy, gdy język nie obsługuje ich. W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność językowa ma wiele możliwych znaczeń. Jedno znaczenie, które zostało omówione w artykule [Niezależność języka i składniki niezależne od języka,](../../docs/standard/language-independence-and-language-independent-components.md)polega na bezproblemowym spożywaniu typów napisanych w jednym języku z aplikacji napisanej w innym języku. Drugie znaczenie, które jest głównym tematem tego artykułu, polega na połączeniu kodu napisanego w wielu językach w jeden zestaw .NET Framework.

Poniższy przykład ilustruje interoperacyjność międzyjęzykową, tworząc bibliotekę klas `NumericLib` o `StringLib`nazwie Utilities.dll, która zawiera dwie klasy i . Klasa `NumericLib` jest napisana w języku `StringLib` C#, a klasa jest napisana w języku Visual Basic. Oto kod źródłowy stringutil.vb, który zawiera jeden `ToTitleCase`element `StringLib` członkowski, w swojej klasie.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Oto kod źródłowy dla NumberUtil.cs, który definiuje `NumericLib` klasę, która ma `IsEven` `NearZero`dwa elementy członkowskie i .

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Aby spakować dwie klasy w jednym zestawie, należy skompilować je w moduły. Aby skompilować plik kodu źródłowego języka Visual Basic do modułu, użyj tego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora języka Visual Basic, zobacz [Tworzenie z wiersza polecenia](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Aby skompilować plik kodu źródłowego języka C# do modułu, użyj tego polecenia:

```console
csc /t:module NumberUtil.cs
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora języka C#, zobacz [Tworzenie wiersza polecenia z csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Następnie użyj [opcji konsolidatora,](/cpp/build/reference/linker-options) aby skompilować dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład następnie `NumericLib.NearZero` `StringLib.ToTitleCase` wywołuje i metody. Należy zauważyć, że kod języka Visual Basic i kod C# są w stanie uzyskać dostęp do metod w obu klasach.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Aby skompilować kod języka Visual Basic, użyj tego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować z C#, zmień nazwę kompilatora z **vbc** na **csc**i zmień rozszerzenie pliku z .vb na .cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Zobacz też

- <xref:System.CLSCompliantAttribute>
