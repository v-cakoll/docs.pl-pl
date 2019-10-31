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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120755"
---
# <a name="language-independence-and-language-independent-components"></a>Niezależność od języka i elementy niezależne od języka

.NET Framework jest niezależne od języka. Oznacza to, że jako deweloper można opracowywać w jednym z wielu języków przeznaczonych dla .NET Framework, takich jak C# C++/CLI, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL i Windows PowerShell. Można uzyskać dostęp do typów i elementów członkowskich bibliotek klas opracowanych dla .NET Framework bez konieczności znajomości języka, w którym zostały pierwotnie napisane, i bez konieczności przestrzegania jakichkolwiek Konwencji języka oryginalnego. Jeśli jesteś deweloperem składnika, dostęp do składnika można uzyskać za pomocą dowolnej aplikacji .NET Framework niezależnie od języka.

> [!NOTE]
> W pierwszej części tego artykułu omówiono Tworzenie składników niezależnych od języka — to znaczy składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku. Możesz również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego zapisaną w wielu językach. Zobacz [współdziałanie między językami](#CrossLang) w drugiej części tego artykułu.

Aby w pełni współistnieć z innymi obiektami zapisanymi w dowolnym języku, obiekty muszą uwidocznić wywołujących tylko te funkcje, które są wspólne dla wszystkich języków. Ten wspólny zestaw funkcji jest definiowany przez Common Language Specification (CLS), który jest zestawem reguł, które są stosowane do wygenerowanych zestawów. Common Language Specification jest zdefiniowany w partycji I, klauzule od 7 do 11 w [standardzie ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Jeśli składnik jest zgodny z Common Language Specification, gwarantowany jest zgodność ze specyfikacją CLS i można uzyskać do niego dostęp z kodu w zestawach pisanych w dowolnym języku programowania, który obsługuje specyfikację CLS. Można określić, czy składnik jest zgodny z Common Language Specification w czasie kompilacji, stosując atrybut <xref:System.CLSCompliantAttribute> do kodu źródłowego. Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#CLSAttribute).

W tym artykule:

- [Reguły zgodności ze specyfikacją CLS](#Rules)

  - [Typy i podpisy elementów członkowskich typu](#Types)

  - [Konwencje nazewnictwa](#naming)

  - [Konwersja typu](#conversion)

  - [Tablice](#arrays)

  - [Interfejsy](#Interfaces)

  - [Wyliczenia](#enums)

  - [Ogólnie wpisz składowe](#members)

  - [Ułatwienia dostępu członków](#MemberAccess)

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

## <a name="cls-compliance-rules"></a>Reguły zgodności ze specyfikacją CLS

W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS. Aby uzyskać pełną listę reguł, zobacz partycja I, klauzula 11 [wzorca ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Common Language Specification omawia każdą zasadę zgodności ze specyfikacją CLS, która ma zastosowanie do konsumentów (deweloperzy, którzy korzystają z programistycznego dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperzy używający kompilatora języka do tworzenia Biblioteki zgodne ze specyfikacją CLS) i rozszerzeń (deweloperzy tworzący narzędzie, takie jak kompilator języka lub parser kodu, który tworzy składniki zgodne ze specyfikacją CLS). Ten artykuł koncentruje się na regułach, które mają zastosowanie do struktur. Należy zauważyć, że niektóre reguły, które mają zastosowanie do rozszerzeń, mogą również być stosowane do zestawów, które są tworzone za pomocą odbicia. Emituj.

Aby zaprojektować składnik niezależny od języka, należy zastosować reguły zgodności ze specyfikacją CLS dla interfejsu publicznego składnika. Twoja prywatna implementacja nie musi być zgodna ze specyfikacją.

> [!IMPORTANT]
> Reguły zgodności ze specyfikacją CLS mają zastosowanie tylko do interfejsu publicznego składnika, a nie do prywatnej implementacji.

Na przykład liczby całkowite bez znaku inne niż <xref:System.Byte> nie są zgodne ze specyfikacją CLS. Ponieważ Klasa `Person` w poniższym przykładzie uwidacznia Właściwość `Age` typu <xref:System.UInt16>, poniższy kod wyświetla ostrzeżenie kompilatora.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Można wprowadzić `Person` klasę CLS, zmieniając typ właściwości `Age` z <xref:System.UInt16> na <xref:System.Int16>, która jest zgodna ze specyfikacją CLS, 16-bitową liczbą całkowitą ze znakiem. Nie musisz zmieniać typu pola `personAge` prywatnego.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Interfejs publiczny biblioteki składa się z następujących elementów:

- Definicje klas publicznych.

- Definicje publicznych członków klas publicznych oraz definicje członków dostępnych dla klas pochodnych (czyli chronionych elementów członkowskich).

- Parametry i zwracane typy metod publicznych klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.

Reguły zgodności ze specyfikacją CLS są wymienione w poniższej tabeli. Tekst reguł jest pobierany Verbatim z [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 przez Ecma International. Bardziej szczegółowe informacje o tych regułach znajdują się w poniższych sekcjach.

|Kategoria|Zobacz|Reguła|Numer reguły|
|--------------|---------|----------|-----------------|
|Ułatwienia dostępu|[Ułatwienia dostępu członków](#MemberAccess)|Dostępność nie jest zmieniana podczas zastępowania metod dziedziczonych, z wyjątkiem tego, że w przypadku przesłania metody dziedziczonej z innego zestawu z `family-or-assembly`ułatwień dostępu. W takim przypadku zastąpienie ma `family`ułatwień dostępu.|10|
|Ułatwienia dostępu|[Ułatwienia dostępu członków](#MemberAccess)|Widoczność i dostępność typów i członków jest taka, że typy w podpisie każdego elementu członkowskiego są widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny. Na przykład metoda publiczna widoczna poza jej zestawem nie ma argumentu, którego typ jest widoczny tylko w obrębie zestawu. Widoczność i dostępność typów tworzących typ ogólny, używany w podpisie dowolnego elementu członkowskiego, są widoczne i dostępne za każdym razem, gdy element członkowski jest widoczny i dostępny. Na przykład typ generyczny skonkretyzowany obecny w sygnaturze elementu członkowskiego, który jest widoczny poza jego zestawem, nie powinien mieć argumentu ogólnego, którego typ jest widoczny tylko w obrębie zestawu.|12|
|Tablice|[Tablice](#arrays)|Tablice powinny mieć elementy z typem zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy mają dolne granice równe zero. Tylko fakt, że element jest tablicą, a typ elementu tablicy musi być wymagany do rozróżnienia między przeciążeniami. W przypadku przeciążania opartego na co najmniej dwóch typach tablic typy elementów muszą być nazwanymi typami.|16|
|Atrybuty|[Atrybuty](#attributes)|Atrybuty są typu <xref:System.Attribute?displayProperty=nameWithType>lub dziedziczą z niego typ.|41|
|Atrybuty|[Atrybuty](#attributes)|CLS zezwala tylko na podzbiór kodowań atrybutów niestandardowych. Jedyne typy, które są wyświetlane w tych kodowaniach, to (zobacz partycja IV): <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType>i dowolny typ wyliczenia na podstawie typu Integer zgodnego ze specyfikacją CLS.|34|
|Atrybuty|[Atrybuty](#attributes)|Specyfikacja CLS nie zezwala na publicznie widoczne wymagane Modyfikatory (`modreq`, zobacz partycja II), ale zezwala na Modyfikatory opcjonalne (`modopt`, zobacz partycja II), które nie są zrozumiałe.|35|
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektu wywołuje niektórych konstruktorów wystąpień swojej klasy podstawowej przed wszelkimi dostępami do dziedziczonych danych wystąpienia. (Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).|43|
|Konstruktorów|[Konstruktory](#ctors)|Konstruktor obiektów nie jest wywoływany, chyba że jest częścią tworzenia obiektu, a obiekt nie zostanie dwukrotnie zainicjowany.|22|
|Wyliczenia|[Wyliczenia](#enums)|Typ podstawowy wyliczenia musi być wbudowanym typem Integer CLS, nazwą pola będzie "value__", a to pole jest oznaczone `RTSpecialName`.|7|
|Wyliczenia|[Wyliczenia](#enums)|Istnieją dwa odrębne rodzaje wyliczeń, wskazywane przez obecność lub brak <xref:System.FlagsAttribute?displayProperty=nameWithType> (Zobacz Biblioteka partycji IV) atrybut niestandardowy. Jeden reprezentuje nazwane wartości całkowite; Druga reprezentuje nazwane flagi bitowe, które można połączyć w celu wygenerowania nienazwanej wartości. Wartość `enum` nie jest ograniczona do określonych wartości.|8|
|Wyliczenia|[Wyliczenia](#enums)|Literałowe pola statyczne typu wyliczeniowego mają typ wyliczenia.|9|
|Zdarzenia|[Zdarzenia](#events)|Metody implementujące zdarzenie należy oznaczyć `SpecialName` w metadanych.|dnia|
|Zdarzenia|[Zdarzenia](#events)|Dostępność zdarzenia i jego metod dostępu powinna być taka sama.|0,30|
|Zdarzenia|[Zdarzenia](#events)|Metody `add` i `remove` dla zdarzenia muszą być obecne lub nieobecne.|niż|
|Zdarzenia|[Zdarzenia](#events)|Metody `add` i `remove` dla zdarzenia muszą przyjmować jeden parametr, którego typ definiuje typ zdarzenia i który powinien pochodzić od <xref:System.Delegate?displayProperty=nameWithType>.|32|
|Zdarzenia|[Zdarzenia](#events)|Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut `SpecialName`, do którego odwołuje się reguła CLS 29, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatorów.|33|
|Wyjątki|[Wyjątki](#exceptions)|Obiekty, które są generowane, są typu <xref:System.Exception?displayProperty=nameWithType> lub dziedziczą z niego typ. Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.|40|
|Ogólne|[Zgodność ze specyfikacją CLS: reguły](#Rules)|Reguły CLS stosują się tylko do tych części typu, które są dostępne lub widoczne poza zestawem definiującym.|1|
|Ogólne|[Zgodność ze specyfikacją CLS: reguły](#Rules)|Elementy członkowskie typów niezgodnych ze specyfikacją CLS nie mogą być oznaczone jako zgodne ze specyfikacją CLS.|2|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Zagnieżdżone typy powinny zawierać co najmniej tyle parametrów ogólnych jak typ otaczający. Parametry ogólne w typie zagnieżdżonym odpowiadają pozycjom parametrów ogólnych w jego typie otaczającym.|42|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Nazwa typu ogólnego zawiera kodowanie liczby parametrów typu zadeklarowanych w typie niezagnieżdżonym lub nowo wprowadzona do typu, jeśli jest zagnieżdżona, zgodnie z regułami określonymi powyżej.|43|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typ ogólny musi redeklarować wystarczające ograniczenia, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsów byłyby spełnione przez ograniczenia typu ogólnego.|4444|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Typy używane jako ograniczenia parametrów ogólnych będą same w sobie zgodne ze specyfikacją CLS.|45|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Widoczność i dostępność elementów członkowskich (w tym zagnieżdżonych typów) w typie ogólnym, który można utworzyć, jest uznawana za zakres do określonego wystąpienia, a nie jako całości deklaracji typu ogólnego. Przy założeniu, że nadal mają zastosowanie reguły widoczności i dostępności reguły CLS 12.|46|
|Typy ogólne|[Typy ogólne i elementy członkowskie](#Generics)|Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej należy mieć domyślną implementację specyficzną (nieabstrakcyjną).|47|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji metod niezgodnych ze specyfikacją CLS w celu ich wdrożenia.|postanowienia|
|Interfejsy|[Interfejsy](#Interfaces)|Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól.|19|
|Elementy członkowskie|[Ogólnie wpisz składowe](#members)|Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS.|36|
|Elementy członkowskie|--|Wartość literału statycznego jest określana za pomocą metadanych inicjacji pola. Literał zgodny ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pola, która jest identyczna z tym samym typem co literał (lub typ podstawowy, jeśli ten literał jest `enum`).|13|
|Elementy członkowskie|[Ogólnie wpisz składowe](#members)|Ograniczenie vararg nie jest częścią specyfikacji CLS, a jedyną konwencją wywoływania obsługiwaną przez specyfikację CLS jest standardowa zarządzana Konwencja wywoływania.|15000|
|Konwencje nazewnictwa|[Konwencje nazewnictwa](#naming)|Zestawy będą zgodne z załącznikiem 7 raportu technicznego 15 standardu Unicode 3.0, który zawiera zestaw znaków dozwolonych do uruchomienia i uwzględnionych w identyfikatorach dostępnych w trybie online w <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Identyfikatory powinny znajdować się w formacie kanonicznym zdefiniowanym przez normalizację Unicode w postaci C. W celach CLS dwa identyfikatory są takie same, jeśli ich mapowania małymi literami (zgodnie z ustawieniami regionalnymi Unicode, które różnią się od liter, jeden do jednego) są takie same. Oznacza to, że w przypadku dwóch identyfikatorów, które mają być uznawane za różne pod względem CLS, różnią się w więcej niż w ich przypadku. Jednak w celu zastąpienia definicji dziedziczonej, interfejs wiersza polecenia wymaga dokładnego kodowania oryginalnej deklaracji.|4|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS powinny być odrębne niezależnie od rodzaju, z wyjątkiem sytuacji, gdy nazwy są identyczne i rozwiązywane przez przeciążanie. Oznacza to, że podczas CTSallows jednego typu do używania tej samej nazwy dla metody i pola, CLS nie.|5|
|Przeciążenie|[Konwencje nazewnictwa](#naming)|Pola i zagnieżdżone typy powinny różnić się odrębnie przez porównanie identyfikatorów, nawet jeśli CTS zezwala na rozróżnianie unikatowych podpisów. Metody, właściwości i zdarzenia, które mają taką samą nazwę (za pomocą porównania identyfikatorów), różnią się więcej niż tylko zwracanym typem, z wyjątkiem określonych w regule CLS 39.|6|
|Przeciążenie|[Overloads](#overloads)|Tylko właściwości i metody mogą być przeciążone.|37|
|Przeciążenie|[Overloads](#overloads)|Właściwości i metody mogą być przeciążone na podstawie liczby i typów ich parametrów, z wyjątkiem operatorów konwersji o nazwie `op_Implicit` i `op_Explicit`, które mogą być również przeciążone na podstawie ich typu zwracanego.|38|
|Przeciążenie|--|Jeśli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę i, dla określonego zestawu wystąpień typu, mają one te same parametry i zwracane typy, wówczas wszystkie te metody są semantycznie równoważne w tych wystąpieniach typu.|48|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|<xref:System.Object?displayProperty=nameWithType> jest zgodna ze specyfikacją CLS. Wszystkie inne klasy zgodne ze specyfikacją CLS są dziedziczone z klasy zgodnej ze specyfikacją CLS.|233|
|Właściwości|[Właściwości](#properties)|Metody, które implementują metody pobierającej i ustawiającej właściwość, są oznaczone `SpecialName` w metadanych.|codzienne|
|Właściwości|[Właściwości](#properties)|Metody dostępu do właściwości muszą być statyczne, wszystkie być wirtualne lub być wystąpieniem.|25|
|Właściwości|[Właściwości](#properties)|Typ właściwości musi być typem zwracanym metody pobierającej i typem ostatniego argumentu metody ustawiającej. Typy parametrów właściwości są typami parametrów do metody pobierającej i typami wszystkich oprócz końcowych parametrów metody ustawiającej. Wszystkie te typy muszą być zgodne ze specyfikacją CLS i nie mogą być wskaźnikami zarządzanymi (tj. nie są przesyłane przez odwołanie).|27|
|Właściwości|[Właściwości](#properties)|Właściwości muszą być zgodne z określonym wzorcem nazewnictwa. Atrybut `SpecialName`, do którego odwołuje się reguła CLS, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatorów. Właściwość ma metodę pobierającą, metodę ustawiającą lub obie te metody.|28|
|Konwersja typu|[Konwersja typu](#conversion)|Jeśli podano `op_Implicit` lub `op_Explicit`, należy podać alternatywny sposób dostarczenia przekształcenia.|39|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Opakowane typy wartości nie są zgodne ze specyfikacją CLS.|3|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Wszystkie typy występujące w podpisie muszą być zgodne ze specyfikacją CLS. Wszystkie typy tworzące typ ogólny, który tworzy wystąpienie, są zgodne ze specyfikacją CLS.|11|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Wpisane odwołania nie są zgodne ze specyfikacją CLS.|14,5|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Niezarządzane typy wskaźnika nie są zgodne ze specyfikacją CLS.|7|
|Types|[Typ i podpisy elementów członkowskich typu](#Types)|Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają implementacji członków niezgodnych ze specyfikacją CLS.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Typy i podpisy elementów członkowskich typu

Typ <xref:System.Object?displayProperty=nameWithType> jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie typu .NET Framework. Dziedziczenie w .NET Framework jest niejawne (na przykład Klasa <xref:System.String> niejawnie dziedziczy z klasy <xref:System.Object>) lub jawna (na przykład Klasa <xref:System.Globalization.CultureNotFoundException> jawnie dziedziczy z klasy <xref:System.ArgumentException>, która jawnie dziedziczy po Klasa <xref:System.SystemException>, która jawnie dziedziczy z klasy <xref:System.Exception>). Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy również musi być zgodny ze specyfikacją CLS.

Poniższy przykład przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS. Definiuje on klasę bazową `Counter`, która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika. Ponieważ Klasa udostępnia funkcje licznika przez Zawijanie liczby całkowitej bez znaku, Klasa jest oznaczona jako niezgodna ze specyfikacją CLS. W związku z tym Klasa pochodna, `NonZeroCounter`, również nie jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Wszystkie typy, które pojawiają się w sygnaturach składowych, łącznie z typem zwracanym metody lub typem właściwości, muszą być zgodne ze specyfikacją CLS. Ponadto dla typów ogólnych:

- Wszystkie typy tworzące typ ogólny wystąpienia muszą być zgodne ze specyfikacją CLS.

- Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.

[Wspólny system typów](../../docs/standard/base-types/common-type-system.md) .NET Framework obejmuje wiele wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie kodowane w metadanych zestawu. Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.

|Typ zgodny ze specyfikacją CLS|Opis|
|-------------------------|-----------------|
|<xref:System.Byte>|8-bitowa liczba całkowita bez znaku|
|<xref:System.Int16>|16-bitowa liczba całkowita ze znakiem|
|<xref:System.Int32>|32-bitowa liczba całkowita ze znakiem|
|<xref:System.Int64>|64-bitowa liczba całkowita ze znakiem|
|<xref:System.Single>|Wartość zmiennoprzecinkowa o pojedynczej precyzji|
|<xref:System.Double>|Wartość zmiennoprzecinkowa o podwójnej precyzji|
|<xref:System.Boolean>|Typ wartości `true` lub `false`|
|<xref:System.Char>|Jednostka kodu zakodowana w formacie UTF-16|
|<xref:System.Decimal>|Liczba dziesiętna liczb zmiennoprzecinkowych|
|<xref:System.IntPtr>|Wskaźnik lub uchwyt rozmiaru zdefiniowanego przez platformę|
|<xref:System.String>|Kolekcja zero, jeden lub więcej obiektów <xref:System.Char>|

Typy wewnętrzne wymienione w poniższej tabeli są niezgodne ze specyfikacją CLS.

|Niezgodny typ|Opis|Alternatywa zgodna ze specyfikacją CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8-bitowy typ danych ze znakiem liczb całkowitych|<xref:System.Int16>|
|<xref:System.TypedReference>|Wskaźnik do obiektu i jego typu środowiska uruchomieniowego|Brak|
|<xref:System.UInt16>|16-bitowa liczba całkowita bez znaku|<xref:System.Int32>|
|<xref:System.UInt32>|32-bitowa liczba całkowita bez znaku|<xref:System.Int64>|
|<xref:System.UInt64>|64-bitowa liczba całkowita bez znaku|<xref:System.Int64> (może przepełnić się), <xref:System.Numerics.BigInteger>lub <xref:System.Double>|
|<xref:System.UIntPtr>|Niepodpisany wskaźnik lub dojście|<xref:System.IntPtr>|

Biblioteka klas .NET Framework lub jakakolwiek inna Biblioteka klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:

- Opakowane typy wartości. Poniższy C# przykład tworzy klasę, która ma właściwość publiczną typu `int*` o nazwie `Value`. Ponieważ `int*` jest opakowanym typem wartościowym, kompilator flaguje go jako niezgodny ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Typy odwołań, które są specjalnymi konstrukcjami, które zawierają odwołanie do obiektu i odwołanie do typu. Wpisane odwołania są reprezentowane w .NET Framework przez klasę <xref:System.TypedReference>.

Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować atrybut <xref:System.CLSCompliantAttribute> z `isCompliant` wartością `false`. Aby uzyskać więcej informacji, zobacz sekcję [atrybut CLSCompliantAttribute](#CLSAttribute) .

Poniższy przykład ilustruje problem zgodności ze specyfikacją CLS w sygnaturze metody i w tworzeniu wystąpienia typu ogólnego. Definiuje klasę `InvoiceItem` z właściwością typu <xref:System.UInt32>, właściwością typu `Nullable(Of UInt32)`i konstruktorem z parametrami typu <xref:System.UInt32> i `Nullable(Of UInt32)`. Podczas próby skompilowania tego przykładu uzyskasz cztery ostrzeżenia kompilatora.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Aby wyeliminować ostrzeżenia kompilatora, Zastąp typy niezgodne ze specyfikacją CLS w `InvoiceItem` publicznym interfejsie z zgodnymi typami:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Oprócz określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS. Są to między innymi typy wskaźników niezarządzanych i typy wskaźników funkcji. Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczb całkowitych.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Dla klas abstrakcyjnych zgodnych ze specyfikacją CLS (czyli klas oznaczonych C# jako `abstract` w lub jako `MustInherit` w Visual Basic) wszystkie elementy członkowskie klasy muszą również być zgodne ze specyfikacją CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Konwencje nazewnictwa

Ponieważ w niektórych językach programowania nie jest rozróżniana wielkość liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i składowe) muszą różnić się więcej niż wielkością liter. Dwa identyfikatory są uważane za równoważne, jeśli ich mapowania małych liter są takie same. W poniższym C# przykładzie zdefiniowano dwie klasy publiczne, `Person` i `person`. Ponieważ różnią się tylko wielkością liter C# , kompilator flaguje je jako niezgodne ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Identyfikatory języków programowania, takie jak nazwy przestrzeni nazw, typy i elementy członkowskie, muszą być zgodne ze [standardem Unicode 3,0, sprawozdanie techniczne 15, załącznik 7](https://www.unicode.org/reports/tr15/tr15-18.html). Oznacza to, że:

- Pierwszy znak identyfikatora może być dowolną wielką literą Unicode, małą literą, literą litery tytułu, literą modyfikującą, inną literą lub cyfrą. Aby uzyskać informacje dotyczące kategorii znaków Unicode, zobacz Wyliczenie <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType>.

- Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszy znak i mogą również zawierać znaczniki niebędące odstępami, odstępy łączące znaczniki, liczby dziesiętne, interpunkcji łącznika i kody formatowania.

Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na postać normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanych w formacie UTF-16. Sekwencje znaków tworzące te same jednostki kodu w formularzu normalizacji Unicode nie są zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano właściwość o nazwie `Å`, która składa się ze znaku ANGSTROM znak (U + 212B), a druga właściwość o nazwie `Å`, która składa się z znaku Wielka litera A z PIERŚCIENIem powyżej (U + 00C5). Zarówno kompilatory C# , jak i Visual Basic będą flagować kod źródłowy jako niezgodny ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Nazwy elementów członkowskich w ramach określonego zakresu (takie jak przestrzenie nazw w obrębie zestawu, typy w przestrzeni nazw lub elementy członkowskie w ramach typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia. To wymaganie jest bardziej rygorystyczne niż w przypadku systemu wspólnego typu, który umożliwia wielu członkom w zakresie posiadanie identycznych nazw, o ile są one różnymi rodzajami elementów członkowskich (na przykład jest to metoda, a jedna to pole). W szczególności dla elementów członkowskich typu:

- Pola i zagnieżdżone typy są rozróżniane wyłącznie nazwami.

- Metody, właściwości i zdarzenia, które mają taką samą nazwę, muszą różnić się więcej niż tylko zwracanym typem.

Poniższy przykład ilustruje wymaganie, aby nazwy elementów członkowskich muszą być unikatowe w ramach zakresu. Definiuje klasę o nazwie `Converter`, która zawiera cztery składowe o nazwie `Conversion`. Trzy to metody, a jedna jest właściwością. Metoda, która zawiera parametr <xref:System.Int64>, ma unikatową nazwę, ale dwie metody z parametrem <xref:System.Int32> nie są, ponieważ wartość zwracana nie jest uważana za część podpisu elementu członkowskiego. Właściwość `Conversion` również narusza to wymaganie, ponieważ właściwości nie mogą mieć takiej samej nazwy jak przeciążone metody.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Poszczególne języki zawierają unikatowe słowa kluczowe, dlatego Języki przeznaczone dla środowiska uruchomieniowego języka wspólnego muszą również zawierać mechanizm odwołujący się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi. Na przykład `case` jest słowem kluczowym w C# obu i Visual Basic. Jednak poniższy Visual Basic przykład jest w stanie odróżnić klasę o nazwie `case` od słowa kluczowego `case` przy użyciu otwierającego i zamykającego nawiasu klamrowego. W przeciwnym razie przykład zostanie wyświetlony komunikat o błędzie "słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można go skompilować.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Poniższy C# przykład jest w stanie utworzyć wystąpienie klasy `case` przy użyciu symbolu `@`, aby odróżnić identyfikator od słowa kluczowego języka. Bez niej, C# kompilator wyświetli dwa komunikaty o błędach, "Oczekiwano typu" i "wyrażenie dotyczące nieprawidłowego terminu". "

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Konwersja typu

Common Language Specification definiuje dwa operatory konwersji:

- `op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub dokładności. Na przykład struktura <xref:System.Decimal> zawiera przeciążony operator `op_Implicit` do konwersji wartości typów całkowitych i wartości <xref:System.Char> na wartości <xref:System.Decimal>.

- `op_Explicit`, który jest używany na potrzeby konwersji zawężających, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzję. Na przykład struktura <xref:System.Decimal> zawiera przeciążony operator `op_Explicit` do konwersji wartości <xref:System.Double> i <xref:System.Single> na <xref:System.Decimal> oraz do konwersji wartości <xref:System.Decimal> na wartości całkowite, <xref:System.Double>, <xref:System.Single>i <xref:System.Char>.

Jednak nie wszystkie języki obsługują przeciążanie operatora lub definicję operatorów niestandardowych. Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonywania konwersji. Zalecamy dostarczenie metod `From`*XXX* i `To`*XXX* .

W poniższym przykładzie zdefiniowano Konwersje jawne zgodne ze specyfikacją CLS. Tworzy klasę `UDouble`, która reprezentuje podpisaną liczbę zmiennoprzecinkową o podwójnej precyzji. Zapewnia to niejawne konwersje z `UDouble` do <xref:System.Double> i dla jawnych konwersji z `UDouble` do <xref:System.Single>, <xref:System.Double> `UDouble`i <xref:System.Single> `UDouble`. Definiuje również metodę `ToDouble` jako alternatywę dla operatora niejawnej konwersji, metody `ToSingle`, `FromDouble`i `FromSingle` jako alternatywy dla operatorów jawnej konwersji.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Tablice

Tablice zgodne ze specyfikacją CLS są zgodne z następującymi regułami:

- Wszystkie wymiary tablicy muszą mieć dolną granicę równą zero. Poniższy przykład tworzy tablicę niezgodną ze specyfikacją CLS z dolną granicą. Należy zauważyć, że pomimo obecności atrybutu <xref:System.CLSCompliantAttribute>, kompilator nie wykrywa, że tablica zwracana przez metodę `Numbers.GetTenPrimes` nie jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Wszystkie elementy tablicy muszą zawierać typy zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS. Pierwszy zwraca tablicę wartości <xref:System.UInt32>. Druga zwraca tablicę <xref:System.Object>, która zawiera wartości <xref:System.Int32> i <xref:System.UInt32>. Chociaż kompilator identyfikuje pierwszą tablicę jako niezgodną ze względu na typ <xref:System.UInt32>, nie rozpozna, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Rozpoznawanie przeciążenia dla metod, które mają parametry tablicowe, jest oparte na faktach, że są tablicami i według ich typu elementu. Z tego powodu następująca definicja przeciążonej metody `GetSquares` jest zgodna ze specyfikacją CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Interfejsy

Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji). Interfejs zgodny ze specyfikacją CLS nie może mieć następujących elementów:

- Metody statyczne lub pola statyczne. Kompilatory C# i Visual Basic generują błędy kompilatora, jeśli zdefiniujesz statyczną składową w interfejsie.

- Pola. Kompilatory C# i Visual Basic generują błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.

- Metody, które nie są zgodne ze specyfikacją CLS. Na przykład następująca definicja interfejsu zawiera metodę `INumber.GetUnsigned`, która jest oznaczona jako niezgodna ze specyfikacją CLS. Ten przykład generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Ze względu na tę regułę typy zgodne ze specyfikacją CLS nie są wymagane do implementacji członków niezgodnych ze specyfikacją CLS. Jeśli struktura zgodna ze specyfikacją CLS uwidacznia klasę, która implementuje interfejs niezgodny ze specyfikacją CLS, powinien również udostępnić konkretne implementacje wszystkich członków niezgodnych ze specyfikacją CLS.

Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na udostępnianie oddzielnych implementacji elementów członkowskich o tej samej nazwie i podpisie w wielu interfejsach.  Zarówno C# , jak i Visual Basic obsługują [jawne implementacje interfejsu](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) , aby zapewnić różne implementacje metod o identycznych nazwach. Visual Basic obsługuje także słowo kluczowe `Implements`, co umożliwia jawne wyznaczanie interfejsów i elementów członkowskich implementujących określony element członkowski. Poniższy przykład ilustruje ten scenariusz, definiując klasę `Temperature` implementującą interfejsy `ICelsius` i `IFahrenheit` jako jawne implementacje interfejsu.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Wyliczenia

Wyliczenia zgodne ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna ze specyfikacją CLS (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>lub <xref:System.Int64>). Na przykład poniższy kod próbuje zdefiniować Wyliczenie, którego typ podstawowy jest <xref:System.UInt32> i generuje ostrzeżenie kompilatora.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Typ wyliczeniowy musi mieć pole pojedynczego wystąpienia o nazwie `Value__`, które jest oznaczone atrybutem <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType>. Dzięki temu można odwołać się do wartości pola niejawnie.

- Wyliczenie zawiera literał pól statycznych, których typy pasują do typu wyliczenia. Na przykład, jeśli zdefiniujesz `State` Wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` są polami literałów statycznych, których typ to `State`.

- Istnieją dwa rodzaje wyliczeń:

  - Wyliczenie, które reprezentuje zestaw wzajemnie wykluczających się wartości o nazwach całkowitych. Ten typ wyliczenia jest wskazywany przez brak atrybutu niestandardowego <xref:System.FlagsAttribute?displayProperty=nameWithType>.

  - Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć w celu wygenerowania nienazwanej wartości. Ten typ wyliczenia jest wskazywany przez obecność <xref:System.FlagsAttribute?displayProperty=nameWithType> niestandardowego atrybutu.

  Aby uzyskać więcej informacji, zapoznaj się z dokumentacją struktury <xref:System.Enum>.

- Wartość wyliczenia nie jest ograniczona do zakresu określonych wartości. Innymi słowy, zakres wartości w wyliczeniu jest zakresem jego wartości źródłowej. Można użyć metody <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>, aby określić, czy określona wartość jest elementem członkowskim wyliczenia.

<a name="members"></a>

### <a name="type-members-in-general"></a>Ogólnie wpisz składowe

Common Language Specification wymaga, aby wszystkie pola i metody były dostępne jako elementy członkowskie konkretnej klasy. W związku z tym globalne pola i metody statyczne (czyli pola statyczne lub metody, które są zdefiniowane niezależnie od typu) nie są zgodne ze specyfikacją CLS. Jeśli spróbujesz dołączyć pole globalne lub metodę w kodzie źródłowym, kompilatory C# i Visual Basic generują błąd kompilatora.

Common Language Specification obsługuje tylko standardową konwencję wywoływania zarządzanego. Nie obsługuje ona niezarządzanych konwencji wywoływania i metod z listami zmiennych argumentów oznaczonych za pomocą słowa kluczowego `varargs`. W przypadku list zmiennych argumentów, które są zgodne ze standardową konwencją wywoływania zarządzanego, Użyj atrybutu <xref:System.ParamArrayAttribute> lub implementacji poszczególnych języków, takich jak słowo kluczowe `params` w C# i słowo kluczowe `ParamArray` w Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Ułatwienia dostępu członków

Zastępowanie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego. Na przykład metoda publiczna w klasie bazowej nie może zostać zastąpiona przez prywatną metodę w klasie pochodnej. Istnieje jeden wyjątek: `protected internal` (in C#) lub `Protected Friend` (w Visual Basic) składowej w jednym zestawie, który jest zastępowany przez typ w innym zestawie. W takim przypadku dostępność przesłonięcia jest `Protected`.

Poniższy przykład ilustruje błąd generowany, gdy atrybut <xref:System.CLSCompliantAttribute> jest ustawiony na `true`, a `Human`, który jest klasą pochodną `Animal`, próbuje zmienić dostępność właściwości `Species` z publicznego na prywatny. Przykład został pomyślnie skompilowany, jeśli jego dostępność została zmieniona na publiczną.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Typy w podpisie składowej muszą być dostępne za każdym razem, gdy ten element członkowski jest dostępny. Na przykład oznacza to, że publiczna składowa nie może zawierać parametru, którego typem jest Private, protected lub internal. Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy Konstruktor klasy `StringWrapper` uwidacznia `StringOperationType` wewnętrzną wartość wyliczenia, która określa, w jaki sposób wartość ciągu powinna być opakowana.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Typy ogólne i elementy członkowskie

Zagnieżdżone typy zawsze mają co najmniej tyle parametrów ogólnych jak ich typ otaczający. Odnoszą się one do parametrów ogólnych w typie otaczającym. Typ ogólny może również zawierać nowe parametry ogólne.

Relacja między parametrami typu ogólnego typu zawierającego i jego zagnieżdżonymi typami może być ukryta przez składnię poszczególnych języków. W poniższym przykładzie typ ogólny `Outer<T>` zawiera dwie klasy zagnieżdżone, `Inner1A` i `Inner1B<U>`. Wywołania metody `ToString`, którą każda klasa dziedziczy z <xref:System.Object.ToString%2A?displayProperty=nameWithType>, pokazują, że każda klasa zagnieżdżona zawiera parametry typu klasy zawierającej.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Nazwy typów ogólnych są zakodowane w *nazwie formularza\`n*, gdzie *name* jest nazwą typu, \` jest literałem znaku, a *n* to liczba parametrów zadeklarowanych w typie, lub dla zagnieżdżonych typów ogólnych, liczba nowo wprowadzonych parametry typu. To kodowanie nazw typów ogólnych jest szczególnie przydatne dla deweloperów korzystających z odbicia w celu uzyskania dostępu do typów ogólnych z aspektami CLS w bibliotece.

Jeśli ograniczenia są stosowane do typu generycznego, wszystkie typy używane jako ograniczenia muszą również być zgodne ze specyfikacją CLS. W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass`, która jest niezgodna ze specyfikacją CLS, i klasy generycznej o nazwie `BaseCollection` której parametr typu musi pochodzić od `BaseClass`. Ale ponieważ `BaseClass` nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Jeśli typ ogólny pochodzi od generycznego typu podstawowego, musi ponownie zadeklarować wszelkie ograniczenia, aby można było zagwarantować, że ograniczenia dotyczące typu podstawowego również są spełnione. W poniższym przykładzie zdefiniowano `Number<T>`, która może reprezentować dowolny typ liczbowy. Definiuje również klasę `FloatingPoint<T>`, która reprezentuje wartość zmiennoprzecinkową. Jednak kod źródłowy nie zostanie skompilowany, ponieważ nie ma zastosowania ograniczenia dotyczącego `Number<T>` (to T musi być typem wartości), aby `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Przykład zostanie skompilowany pomyślnie, jeśli ograniczenie zostanie dodane do klasy `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Common Language Specification nakładają się na model tworzenia wystąpień dla zagnieżdżonych typów i chronionych elementów członkowskich. Otwarte typy ogólne nie mogą ujawniać pól ani członków z podpisami zawierającymi określone wystąpienie zagnieżdżonego, chronionego typu ogólnego. Typy nieogólne, które zwiększają wystąpienie określonego wystąpienia generycznej klasy podstawowej lub interfejsu, nie mogą ujawniać pól ani elementów członkowskich z podpisami zawierającymi różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.

Poniższy przykład definiuje typ ogólny, `C1<T>` (lub `C1(Of T)` w Visual Basic) oraz chronioną klasę `C1<T>.N` (lub `C1(Of T).N` w Visual Basic). `C1<T>` ma dwie metody, `M1` i `M2`. Jednakże `M1` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić obiekt `C1<int>.N` (lub `C1(Of Integer).N`) z C1\<T > (lub `C1(Of T)`). Druga klasa, `C2`, pochodzi od `C1<long>` (lub `C1(Of Long)`). Ma dwie metody, `M3` i `M4`. `M3` jest niezgodna ze specyfikacją CLS, ponieważ próbuje zwrócić obiekt `C1<int>.N` (lub `C1(Of Integer).N`) z podklasy `C1<long>`. Należy zauważyć, że kompilatory języka mogą być jeszcze bardziej restrykcyjne. W tym przykładzie Visual Basic wyświetla błąd podczas próby skompilowania `M4`.

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Konstruktorów

Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Konstruktor klasy pochodnej musi wywoływać konstruktora wystąpienia swojej klasy bazowej przed uzyskaniem dostępu do danych dziedziczonego wystąpienia. To wymaganie wynika z faktu, że konstruktory klasy bazowej nie są dziedziczone przez ich klasy pochodne. Ta zasada nie ma zastosowania do struktur, które nie obsługują bezpośredniego dziedziczenia.

  Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności ze specyfikacją CLS, jak pokazano w poniższym przykładzie. Tworzy klasę `Doctor`, która jest pochodną klasy `Person`, ale Klasa `Doctor` nie może wywołać konstruktora klasy `Person` w celu zainicjowania pól dziedziczonego wystąpienia.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Konstruktor obiektów nie może zostać wywołany z wyjątkiem tworzenia obiektu. Ponadto nie można dwukrotnie zainicjować obiektu. Oznacza to na przykład, że metody <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> i deserializacji, takie jak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>, nie mogą wywoływać konstruktorów.

<a name="properties"></a>

### <a name="properties"></a>Właściwości

Właściwości typów zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:

- Właściwość musi mieć metody ustawiającej, pobierającej lub obu. W zestawie są one implementowane jako metody specjalne, co oznacza, że będą wyświetlane jako oddzielne metody (metoda pobierająca nosi nazwę `get_`*PropertyName* , a Metoda ustawiająca to `set_`*PropertyName*) oznaczona jako `SpecialName` w zestawie metadane. Kompilatory C# i Visual Basic wymuszają tę regułę automatycznie bez konieczności stosowania atrybutu <xref:System.CLSCompliantAttribute>.

- Typ właściwości jest typem zwracanym metody pobierającej właściwości i ostatnim argumentem metody ustawiającej. Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisywane do właściwości przez odwołanie (oznacza to, że nie mogą być wskaźnikami zarządzanymi).

- Jeśli właściwość ma zarówno metodę pobierającą, jak i setter, muszą jednocześnie być wirtualne, zarówno statyczne, jak i oba wystąpienia. Kompilatory C# i Visual Basic automatycznie wymuszają tę regułę za pomocą składni definicji właściwości.

<a name="events"></a>

### <a name="events"></a>Zdarzenia

Zdarzenie jest definiowane przy użyciu jego nazwy i typu. Typ zdarzenia jest delegatem, który jest używany do wskazania zdarzenia. Na przykład zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> jest typu <xref:System.ResolveEventHandler>. Oprócz samego zdarzenia trzy metody z nazwami na podstawie nazwy zdarzenia dostarczają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:

- Metoda dodawania programu obsługi zdarzeń o nazwie `add_`*EventName*. Na przykład Metoda subskrypcji zdarzeń dla zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> ma nazwę `add_AssemblyResolve`.

- Metoda usuwania programu obsługi zdarzeń o nazwie `remove_`*EventName*. Na przykład metoda usuwania dla zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> ma nazwę `remove_AssemblyResolve`.

- Metoda wskazująca, że zdarzenie wystąpiło o nazwie `raise_`*EventName*.

> [!NOTE]
> Większość reguł Common Language Specification dotyczących zdarzeń jest implementowanych przez kompilatory języka i są przezroczyste dla deweloperów składników.

Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć taki sam dostęp. Muszą one również być statyczne, wystąpienia lub wirtualne. Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia. Metody Add i Remove muszą być obecne lub być nieobecne.

W poniższym przykładzie zdefiniowano klasę zgodną ze specyfikacją CLS o nazwie `Temperature`, która wywołuje zdarzenie `TemperatureChanged`, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową. Klasa `Temperature` jawnie definiuje metodę `raise_TemperatureChanged`, aby umożliwić selektywne wykonywanie programów obsługi zdarzeń.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Overloads

Common Language Specification nakładają następujące wymagania dotyczące przeciążonych elementów członkowskich:

- Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu każdego parametru. Konwencja wywoływania, zwracany typ, Modyfikatory niestandardowe stosowane do metody lub jej parametru oraz czy parametry są przesyłane przez wartość lub przez odwołanie nie są brane pod uwagę podczas różnicowania przeciążeń. Aby zapoznać się z przykładem, zobacz kod wymagający, aby nazwy muszą być unikatowe w zakresie w sekcji [konwencji nazewnictwa](#naming) .

- Tylko właściwości i metody mogą być przeciążone. Pola i zdarzenia nie mogą być przeciążone.

- Metody generyczne mogą być przeciążone na podstawie liczby parametrów ogólnych.

> [!NOTE]
> Operatory `op_Explicit` i `op_Implicit` są wyjątkami od reguły, która zwraca wartość nie jest uważana za część sygnatury metody w celu rozpoznania przeciążenia. Te dwa operatory mogą być przeciążone na podstawie zarówno ich parametrów, jak i ich wartości zwracanej.

<a name="exceptions"></a>

### <a name="exceptions"></a>Wyjątki

Obiekty wyjątków muszą pochodzić od <xref:System.Exception?displayProperty=nameWithType> lub z innego typu pochodzącego od <xref:System.Exception?displayProperty=nameWithType>. Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy Klasa niestandardowa o nazwie `ErrorClass` jest używana do obsługi wyjątków.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Aby naprawić ten błąd, Klasa `ErrorClass` musi dziedziczyć po <xref:System.Exception?displayProperty=nameWithType>. Ponadto należy zastąpić Właściwość `Message`. Poniższy przykład koryguje te błędy w celu zdefiniowania klasy `ErrorClass`, która jest zgodna ze specyfikacją CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Atrybuty

Zestawy platformy In.NET Framework, atrybuty niestandardowe oferują rozszerzalny mechanizm do przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry metody. Atrybuty niestandardowe muszą pochodzić od <xref:System.Attribute?displayProperty=nameWithType> lub z typu pochodnego od <xref:System.Attribute?displayProperty=nameWithType>.

Poniższy przykład narusza tę regułę. Definiuje klasę `NumericAttribute`, która nie pochodzi z <xref:System.Attribute?displayProperty=nameWithType>. Należy zauważyć, że błąd kompilatora występuje tylko wtedy, gdy jest stosowany atrybut niezgodny ze specyfikacją CLS, nie gdy Klasa jest zdefiniowana.

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

- Każdy typ wyliczeniowy, którego typ podstawowy to <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>lub <xref:System.Int64>.

W poniższym przykładzie zdefiniowano klasę `DescriptionAttribute`, która pochodzi z <xref:System.Attribute>. Konstruktor klasy ma parametr typu `Descriptor`, więc Klasa nie jest zgodna ze specyfikacją CLS. Należy zauważyć, C# że kompilator emituje ostrzeżenie, ale kompiluje się pomyślnie, natomiast kompilator Visual Basic emituje nie ostrzeżenia ani błąd.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Atrybut CLSCompliantAttribute

Atrybut <xref:System.CLSCompliantAttribute> służy do wskazywania, czy element programu jest zgodny z Common Language Specification. Konstruktor <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> zawiera jeden wymagany parametr `isCompliant`, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.

W czasie kompilacji kompilator wykrywa niezgodne elementy, które są zgodne ze specyfikacją CLS, i emituje ostrzeżenie. Kompilator nie emituje ostrzeżeń dla typów lub elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.

Deweloperzy składników mogą używać atrybutu <xref:System.CLSCompliantAttribute> na dwa sposoby:

- Do definiowania części interfejsu publicznego uwidocznionych przez składnik, który jest zgodny ze specyfikacją CLS, i części, które nie są zgodne ze specyfikacją CLS. Gdy atrybut jest używany do oznaczania określonych elementów programu jako zgodnych ze specyfikacją CLS, jego użycie gwarantuje, że te elementy są dostępne we wszystkich językach i narzędziach przeznaczonych dla .NET Framework.

- Aby zapewnić, że interfejs publiczny biblioteki składników uwidacznia tylko elementy programu, które są zgodne ze specyfikacją CLS. Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zwykle wygenerują ostrzeżenie.

> [!WARNING]
> W niektórych przypadkach kompilatory języka wymuszają reguły zgodne ze specyfikacją CLS niezależnie od tego, czy atrybut <xref:System.CLSCompliantAttribute> jest używany. Na przykład definiowanie statycznego elementu członkowskiego w interfejsie narusza regułę CLS. W związku z tym, jeśli zdefiniujesz `static` (w C#) lub `Shared` (w Visual Basic) w interfejsie, kompilatory C# i Visual Basic wyświetlają komunikat o błędzie i nie kompilują aplikacji.

Atrybut <xref:System.CLSCompliantAttribute> jest oznaczony atrybutem <xref:System.AttributeUsageAttribute> o wartości <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Ta wartość pozwala zastosować atrybut <xref:System.CLSCompliantAttribute> do dowolnego elementu programu, w tym zestawów, modułów, typów (klasy, struktury, wyliczenia, interfejsy i delegatów), składowych typu (konstruktory, metody, właściwości, pola i zdarzenia), parametry, parametry ogólne i wartości zwracane. Jednakże, w przypadku, należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu. W przeciwnym razie kompilatory ignorują atrybut i kontynuuje generowanie ostrzeżeń kompilatora zawsze wtedy, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.

Wartość atrybutu <xref:System.CLSCompliantAttribute> jest dziedziczona przez zawarte elementy programu. Na przykład, jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS. Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.

Dziedziczonej zgodności można jawnie zastąpić, stosując atrybut <xref:System.CLSCompliantAttribute> do zawartego elementu programu. Na przykład można użyć atrybutu <xref:System.CLSCompliantAttribute> z `isCompliant` wartością `false` do zdefiniowania niezgodnego typu w zgodnym zestawie i można użyć atrybutu z wartością `isCompliant` `true` do zdefiniowania zgodnego typu w niezgodnym zestawie. Istnieje również możliwość zdefiniowania niezgodnych elementów członkowskich w typie zgodnym. Niezgodny typ nie może jednak mieć zgodnych elementów członkowskich, dlatego nie można użyć atrybutu z `isCompliant` wartością `true`, aby zastąpić dziedziczenie z niezgodnego typu.

Podczas tworzenia składników należy zawsze używać atrybutu <xref:System.CLSCompliantAttribute>, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.

Aby utworzyć składniki zgodne ze specyfikacją CLS:

1. Użyj <xref:System.CLSCompliantAttribute>, aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.

2. Oznacz wszystkie publicznie uwidocznione typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.

3. Oznacz wszystkie publicznie uwidocznionych członków w typach zgodnych ze specyfikacją CLS jako niezgodne.

4. Podaj alternatywę zgodną ze specyfikacją CLS dla członków niezgodnych ze specyfikacją CLS.

Jeśli wszystkie niezgodne typy i elementy członkowskie zostały oznaczone pomyślnie, kompilator nie powinien emitować ostrzeżeń o braku zgodności. Należy jednak wskazać, które elementy członkowskie nie są zgodne ze specyfikacją CLS, i wyświetlić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.

Poniższy przykład używa atrybutu <xref:System.CLSCompliantAttribute>, aby zdefiniować zestaw zgodny ze specyfikacją CLS i typ `CharacterUtilities`, który ma dwie składowe niezgodne ze specyfikacją CLS. Ponieważ oba elementy członkowskie są oznaczone atrybutem `CLSCompliant(false)`, kompilator nie generuje ostrzeżeń. Klasa zawiera również alternatywę zgodną ze specyfikacją CLS dla obu tych metod. Zwykle dodaliśmy dwa przeciążenia do metody `ToUTF16`, aby zapewnić alternatywy zgodne ze specyfikacją CLS. Jednak ponieważ metody nie mogą być przeciążone w oparciu o wartość zwracaną, nazwy metod zgodnych ze specyfikacją CLS różnią się od nazw metod niezgodnych.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Jeśli tworzysz aplikację, a nie bibliotekę (czyli jeśli nie ujawniasz typów lub elementów członkowskich, które mogą być używane przez innych deweloperów aplikacji), zgodność ze specyfikacją CLS elementów programu, których używa aplikacja, jest interesująca tylko wtedy, gdy język ich nie obsługuje . W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Współdziałanie między językami

Niezależność od języka ma wiele możliwych znaczenia. Jednym z nich, który jest omawiany w [zależności od języka artykułu i składników niezależnych od języka](../../docs/standard/language-independence-and-language-independent-components.md), obejmuje bezproblemowe zużywanie typów pisanych w jednym języku z aplikacji w innym języku. Drugie znaczenie, które jest fokusem tego artykułu, obejmuje łączenie kodu pisanego w wielu językach w jeden zestaw .NET Framework.

Poniższy przykład ilustruje współdziałanie między językami przez utworzenie biblioteki klas o nazwie Utilities. dll zawierającej dwie klasy, `NumericLib` i `StringLib`. Klasa `NumericLib` jest zapisywana C#, a Klasa `StringLib` jest zapisywana w Visual Basic. Oto kod źródłowy dla StringUtil. vb, który zawiera pojedynczy element członkowski, `ToTitleCase`, w swojej klasie `StringLib`.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Oto kod źródłowy dla NumberUtil.cs, który definiuje klasę `NumericLib`, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Aby spakować dwie klasy w jednym zestawie, należy skompilować je do modułów. Aby skompilować plik kodu źródłowego Visual Basic do modułu, użyj tego polecenia:

```console
vbc /t:module StringUtil.vb
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia kompilatora Visual Basic, zobacz [Kompilowanie z poziomu wiersza polecenia](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Aby skompilować plik C# kodu źródłowego do modułu, użyj tego polecenia:

```console
csc /t:module NumberUtil.cs
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia C# kompilatora, zobacz [wiersza polecenia kompilowanego za pomocą pliku CSC. exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Następnie użyj [opcji konsolidatora](/cpp/build/reference/linker-options) , aby skompilować dwa moduły do zestawu:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Poniższy przykład wywołuje metody `NumericLib.NearZero` i `StringLib.ToTitleCase`. Należy zauważyć, że zarówno kod Visual Basic, C# jak i kod mogą uzyskać dostęp do metod w obu klasach.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Aby skompilować kod Visual Basic, użyj tego polecenia:

```console
vbc example.vb /r:UtilityLib.dll
```

Aby skompilować przy C#użyciu, Zmień nazwę kompilatora z **VBC** na **CSC**i Zmień rozszerzenie pliku z. vb na. cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Zobacz także

- <xref:System.CLSCompliantAttribute>
