---
title: Niestandardowe ciągi formatujące liczby
ms.date: 06/25/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- format strings
- custom numeric format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- formatting numbers [.NET Framework]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
ms.openlocfilehash: 5961cce4601a89b34708b7090207edfed63b5b08
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242988"
---
# <a name="custom-numeric-format-strings"></a>Niestandardowe ciągi formatujące liczby

Można utworzyć ciąg niestandardowego formatu liczb, który składa się z jednego lub większej liczby niestandardowych specyfikatorów liczbowych, aby zdefiniować sposób formatowania danych liczbowych. Niestandardowy ciąg formatu liczbowego to dowolny ciąg formatu, który nie jest [standardowym ciągiem formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Niestandardowe ciągi formatu numerycznego są obsługiwane `ToString` przez niektóre przeciążenia metody wszystkich typów numerycznych. Na przykład można podać ciąg formatu <xref:System.Int32.ToString%28System.String%29> liczbowego do i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> metod <xref:System.Int32> typu. Niestandardowe ciągi formatu numerycznego są również obsługiwane przez [funkcję formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) `Write` `WriteLine` <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> <xref:System.Console> .NET, która jest używana przez niektóre i metody klas i <xref:System.IO.StreamWriter> klas, metody i metody. Funkcja [interpolacji ciągów](../../csharp/language-reference/tokens/interpolated.md) obsługuje również niestandardowe ciągi formatu numerycznego.

> [!TIP]
> Można pobrać **narzędzie formatowania**, aplikację .NET Core Windows Forms, która umożliwia stosowanie ciągów formatu do wartości liczbowych lub wartości daty i godziny oraz wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [języka C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) i [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

<a name="table"></a>W poniższej tabeli opisano niestandardowe specyfikatory formatu liczbowego i są wyświetlane przykładowe dane wyjściowe wytwarzane przez każdy specyfikator formatu. Zobacz sekcję [Uwagi,](#NotesCustomFormatting) aby uzyskać dodatkowe informacje na temat używania niestandardowych ciągów formatu numerycznego, a także sekcję [Przykład,](#example) aby uzyskać wyczerpującą ilustrację ich użycia.

|Specyfikator formatu|Nazwa|Opis|Przykłady|
|----------------------|----------|-----------------|--------------|
|„0”|Symbol zastępczy zero|Zamienia zero na odpowiednią cyfrę, jeżeli jest ona obecna. W przeciwnym wypadku zero występuje w ciągu wynikowym.<br /><br /> Więcej informacji: [Specyfikator niestandardowy "0"](#Specifier0).|1234.5678 ("00000") -> 01235<br /><br /> 0,45678 ("0,00", en-US) -> 0,46<br /><br /> 0,45678 ("0,00", fr-FR) -> 0,46|
|"#"|Symbol zastępczy cyfry|Zamienia symbol „#” na odpowiednią cyfrę, jeżeli jest ona obecna. W przeciwnym wypadku żadna cyfra nie występuje w ciągu wynikowym.<br /><br /> Należy zauważyć, że żadna cyfra nie pojawia się w ciągu wynikowym, jeśli odpowiednia cyfra w ciągu wejściowym jest nieistotna 0. Na przykład 0003 ("####") -> 3.<br /><br /> Więcej informacji: [Specyfikator niestandardowy "#"](#SpecifierD).|1234.5678 ("#####") -> 1235<br /><br /> 0.45678 ("#.##", en-US) -> .46<br /><br /> 0.45678 ("#.##", fr-FR) -> ,46|
|"."|Punkt dziesiętny|Określa lokalizację separatora dziesiętnego w ciągu wynikowym.<br /><br /> Więcej informacji: ["." Niestandardowy specyfikator](#SpecifierPt).|0,45678 ("0,00", en-US) -> 0,46<br /><br /> 0,45678 ("0,00", fr-FR) -> 0,46|
|","|Separator grup i skalowania liczby|Jest używany zarówno jako separator grup, jak i specyfikator skalowania liczby. Jako separator grup wstawia zlokalizowany znak separatora grup między grupami. Jako specyfikator skalowania liczb dzieli liczbę przez 1000 dla każdej liczby z określonym przecinkiem.<br /><br /> Więcej informacji: ["," Custom Specifier](#SpecifierTh).|Specyfikator separatora grup:<br /><br /> 2147483647 ("##,#", en-US) -> 2 147 483 647<br /><br /> 2147483647 ("##,#", es-ES) -> 2.147.483.647<br /><br /> Specyfikator skalowania:<br /><br /> 2147483647 ("#,#,,", en-US) -> 2147<br /><br /> 2147483647 ("#,#,,", es-ES) -> 2.147|
|"%"|Symbol zastępczy procentu|Mnoży liczbę przez 100 i wstawia zlokalizowany symbol procentu do ciągu wynikowego.<br /><br /> Więcej informacji: [Specyfikator niestandardowy "%"](#SpecifierPct).|0,3697 ("%#0.00", en-US) -> %36.97<br /><br /> 0,3697 ("%#0,00", el-GR) -> %36,97<br /><br /> 0,3697 ("##.0 %", en-US) -> 37,0 %<br /><br /> 0,3697 ("##.0 %", el-GR) -> 37,0 %|
|"‰"|Symbol zastępczy promil|Mnoży liczbę przez 1000 i wstawia zlokalizowany symbol promila do ciągu wynikowego.<br /><br /> Więcej informacji: [Specyfikator niestandardowy "‰"](#SpecifierPerMille).|0.03697 ("#0.00‰", en-US) -> 36.97‰<br /><br /> 0.03697 ("#0.00‰", ru-RU) -> 36,97‰|
|„E0”<br /><br /> „E+0”<br /><br /> „E-0”<br /><br /> „e0”<br /><br /> „e+0”<br /><br /> „e-0”|Notacja wykładnicza|Jeżeli występuje po nim przynajmniej jedno 0 (zero), formatuje wynik za pomocą notacji wykładniczej. Wielkość litery „E” lub „e” wskazuje wielkość symbolu wykładnika w ciągu wynikowym. Liczba zer po znaku „E” lub „e” określa minimalną liczbę cyfr wykładnika. Znak plus (+) wskazuje, że znak zawsze poprzedza wykładnik potęgi. Znak minus (-) wskazuje, że znak poprzedza tylko ujemny wykładnik potęgi.<br /><br /> Więcej informacji: [Niestandardowe specyfikatory "E" i "e"](#SpecifierExponent).|987654 ("#0.0e0") -> 98.8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|
|"\\"|Znak ucieczki|Powoduje, że następny znak należy interpretować jako literał, a nie jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: [Znak ucieczki "\\"](#SpecifierEscape).|987654 ("\\###00\\#") -> #987654 #|
|'*ciąg*'<br /><br /> "*string*"|Ogranicznik ciągu literału|Wskazuje, że znaki w cudzysłowie powinny zostać skopiowane do ciągu wynikowego bez zmian.<br/><br/>Więcej informacji: [Literały znaków](#character-literals).|68 ("# 'degrees'") -> 68 stopni<br /><br /> 68 ("#' stopnie") -> 68 stopni|
|;|Separator sekcji|Definiuje sekcje z oddzielnymi ciągami formatu dla liczb dodatnich, ujemnych i dla zera.<br /><br /> Więcej informacji: [";" Separator sekcji](#SectionSeparator).|12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#);-\0-") -> -0-<br /><br /> -12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0.0<br /><br /> -12.345 ("#0.0#;(#0.0#)") -> (12.35)|
|Inne|Wszystkie inne znaki|Znak jest kopiowany do ciągu wynikowego bez zmian.<br/><br/>Więcej informacji: [Literały znaków](#character-literals).|68 ("# °") -> 68 °|

W poniższych sekcjach znajdują się szczegółowe informacje o poszczególnych niestandardowych specyfikatorach formatu liczb.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)]

<a name="Specifier0"></a>

## <a name="the-0-custom-specifier"></a>Specyfikator niestandardowy "0"

Niestandardowy specyfikator formatu „0” pełni rolę symbolu zastępczego zera. Jeżeli formatowana wartość zawiera cyfrę w miejscu, w którym w ciągu formatu występuje zero, ta cyfra jest kopiowana do ciągu wynikowego. W innym przypadku w ciągu wynikowym występuje zero. Położenie zera znajdującego się najdalej po lewej stronie od punktu dziesiętnego i położenie zera znajdującego się najdalej po prawej stronie od punktu dziesiętnego określa zakres cyfr, które są zawsze obecne w ciągu wynikowym.

Specyfikator „00” powoduje, że wartość zostaje zaokrąglona do najbliższej cyfry poprzedzającej miejsce dziesiętne, gdzie używane jest zawsze zaokrąglanie od zera. Na przykład wynikiem formatowania liczby 34,5 z pomocą specyfikatora „00” byłaby wartość 35.

W poniższym przykładzie pokazano kilka wartości formatowanych za pomocą ciągów formatu niestandardowego, które zawierają symbole zastępcze zera.

[!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
[!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
[!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]

[Powrót do stołu](#table)

<a name="SpecifierD"></a>

## <a name="the--custom-specifier"></a>Specyfikator niestandardowy "#"

Niestandardowy specyfikator formatu „#” służy jako symbol zastępczy cyfry. Jeżeli formatowana wartość zawiera cyfrę w miejscu, w którym w ciągu formatu znajduje się symbol „#”, ta cyfra jest kopiowana do ciągu wynikowego. W przeciwnym wypadku nic nie jest umieszczane w tym miejscu w ciągu wynikowym.

Należy zauważyć, że ten specyfikator nigdy nie wyświetla zera niebędącego cyfrą znaczącą, nawet jeśli zero jest jedyną cyfrą w ciągu. Zero zostanie wyświetlone tylko wtedy, gdy jest cyfrą znaczącą w wyświetlanej liczbie.

Ciąg formatu „##” powoduje, że wartość zostaje zaokrąglona do najbliższej cyfry poprzedzającej miejsce dziesiętne, gdzie używane jest zawsze zaokrąglanie od zera. Na przykład wynikiem formatowania liczby 34,5 za pomocą specyfikatora „##” byłaby wartość 35.

W poniższym przykładzie pokazano kilka wartości formatowanych za pomocą ciągów formatu niestandardowego, które zawierają symbole zastępcze cyfr.

[!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
[!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
[!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]

Aby zwrócić ciąg wynikowy, w którym cyfry nieobecne lub zera wiodące są zastępowane spaniami, użyj [operacji formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) i określ szerokość pola, jak pokazano w poniższym przykładzie.

[!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
[!code-csharp[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
[!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]

[Powrót do stołu](#table)

<a name="SpecifierPt"></a>

## <a name="the--custom-specifier"></a>Specyfikator niestandardowy "."

Niestandardowy specyfikator formatu „.” wstawia zlokalizowany separator dziesiętny do ciągu wynikowego. Pierwszy kropka w ciągu formatu określa lokalizację separatora dziesiętnego w sformatowanej wartości. Wszelkie dodatkowe kropki są ignorowane.

Znak, który jest używany jako separator dziesiętny w ciągu wynik nie zawsze jest kropka; jest określana <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> przez właściwość obiektu, <xref:System.Globalization.NumberFormatInfo> który steruje formatowaniem.

W poniższym przykładzie użyto specyfikatora formatu „.” aby zdefiniować lokalizację punktu dziesiętnego w kilku ciągach wynikowych.

[!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
[!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
[!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]

[Powrót do stołu](#table)

<a name="SpecifierTh"></a>

## <a name="the--custom-specifier"></a>"", specyfikator niestandardowy

Znak „,” jest używany zarówno jako separator grup, jak i specyfikator skalowania liczb.

- Separator grup: jeśli jeden lub więcej przecinków jest określonych między dwoma symbolami zastępczymi cyfr (0 lub #), które formatują całkowite cyfry danej liczby, znak separatora grupy jest wstawiany między poszczególne grupy liczby w całkowitej części wyniku.

  Właściwości <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu określają znak używany jako separator grupy numerów i rozmiar każdej grupy numeracji. Na przykład jeśli ciąg „#,#” i niezmienna kultura są użyte do formatowania liczby 1000, wynikiem będzie „1 000”.

- Specyfikator skalowania liczb: jeśli jeden lub większa liczba przecinków jest określonych natychmiast z lewej strony jawnego lub niejawnego punktu dziesiętnego, formatowana liczba jest dzielona przez 1000 dla każdego przecinka. Na przykład jeśli ciąg „0,,” jest używany do formatowania liczby 100 milionów, wynikiem jest „100”.

Specyfikatorów skalowania liczb i separatorów grup można użyć w tym samym ciągu formatu. Na przykład jeśli ciąg „#,0,,” i niezmienna kultura są używane do formatowania liczby jeden miliard, wynikiem jest „1 000”.

W poniższym przykładzie pokazano użycie przecinka jako separatora grup.

[!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
[!code-csharp[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
[!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]

W poniższym przykładzie pokazano użycie przecinka jako specyfikatora skalowania liczb.

[!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
[!code-csharp[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
[!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]

[Powrót do stołu](#table)

<a name="SpecifierPct"></a>

## <a name="the--custom-specifier"></a>Specyfikator niestandardowy "%"

Znak procentu (%) w ciągu formatu powoduje pomnożenie liczby przez 100 przed formatowaniem. Zlokalizowany symbol procentu jest wstawiany do liczby, w lokalizacji, na której znak % znajduje się w ciągu formatu. Używany znak procentu jest <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> definiowany <xref:System.Globalization.NumberFormatInfo> przez właściwość bieżącego obiektu.

W poniższym przykładzie zdefiniowano kilka ciągów formatu niestandardowego, które zawierają niestandardowy specyfikator „%”.

[!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
[!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
[!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]

[Powrót do stołu](#table)

<a name="SpecifierPerMille"></a>

## <a name="the--custom-specifier"></a>Specyfikator niestandardowy "‰"

Znak promila (‰ lub \u2030) w ciągu formatu powoduje pomnożenie liczby przez 1000 przed formatowaniem. Odpowiedni symbol promila jest wstawiony w zwracanym ciągu w lokalizacji, w której symbol ‰ pojawia się w ciągu formatu. Używany znak na milisel <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> jest zdefiniowany przez właściwość obiektu, który zawiera informacje o formatowaniu specyficzne dla kultury.

W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który zawiera niestandardowy specyfikator „‰”.

[!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
[!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
[!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]

[Powrót do stołu](#table)

<a name="SpecifierExponent"></a>

## <a name="the-e-and-e-custom-specifiers"></a>Specyfikatory niestandardowe "E" i "e"

Jeśli którykolwiek z ciągów „E”, „E+”, „E-”, „e”, „e+” lub „e-” jest obecny w ciągu formatu i natychmiast po nim następuje co najmniej jedno zero, liczba jest formatowana przy użyciu notacji wykładniczej z symbolem „E” lub „e” wstawionym między liczbą a wykładnikiem potęgi. Liczba zer po wskaźniku notacji wykładniczej określa minimalną liczbę cyfr wykładnika potęgi. Formaty „E+” i „e+” wskazują, że znak plus lub znak minus powinien zawsze poprzedzać wykładnik potęgi. Formaty „E”, „E-”, „e” i „e-” wskazują, że znak powinien poprzedzać tylko ujemne wykładniki potęgi.

W poniższym przykładzie sformatowano kilka wartości liczbowych przy użyciu specyfikatorów notacji wykładniczej.

[!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
[!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
[!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]

[Powrót do stołu](#table)

<a name="SpecifierEscape"></a>

## <a name="the--escape-character"></a>Znak\\ucieczki " " "

Symbole „#”, „0”, „.”, „,”, „%” i „‰” w ciągu formatu są interpretowane jako specyfikatory formatu, a nie jako znaki literału. W zależności od ich pozycji w ciągu formatu niestandardowego, wielkie i małe litery „E” oraz symbole + i - także mogą być interpretowane jako specyfikatory formatu.

Aby zapobiec interpretacji znaku jako specyfikatora formatu, można poprzedzić go ukośnikiem odwrotnym, który jest znakiem ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.

Aby uwzględnić ukośnik odwrotny w ciągu wynikowym,`\\`należy uciec od niego innym ukośnikiem odwrotnym ( ).

> [!NOTE]
> Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.

W poniższym przykładzie użyto znaku ucieczki, aby zapobiec interpretacji znaków "#", "0" i "\\jako znaków ucieczki lub specyfikatorów formatu. W przykładach w języku C# są używane dodatkowe ukośniki odwrotne w celu zagwarantowania, że ukośnik odwrotny będzie interpretowany jako znak literału.

[!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
[!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
[!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]

[Powrót do stołu](#table)

<a name="SectionSeparator"></a>

## <a name="the--section-separator"></a>Separator sekcji ";"

Średnik (;) jest warunkowym specyfikatorem formatu, który stosuje do liczby różne formatowania, w zależności od tego, czy wartość jest dodatnia, ujemna, czy równa zero. Aby utworzyć takie zachowanie, ciąg formatu niestandardowego może zawierać maksymalnie trzy sekcje rozdzielone średnikami. Te sekcje opisano w poniższej tabeli.

|Liczba sekcji|Opis|
|------------------------|-----------------|
|Jedna sekcja|Ciąg formatu jest stosowany do wszystkich wartości.|
|Dwie sekcje|Pierwsza sekcja jest stosowana do wartości dodatnich i zer, a druga sekcja do wartości ujemnych.<br /><br /> Jeżeli formatowana liczba jest ujemna, ale staje się zerem po zaokrągleniu zgodnym z formatem w drugiej sekcji, wynikowa wartość zero jest formatowana zgodnie z pierwszą sekcją.|
|Trzy sekcje|Pierwsza sekcja jest stosowana do wartości dodatnich, druga sekcja jest stosowana do wartości ujemnych, a trzecia sekcja jest stosowana do zer.<br /><br /> Druga sekcja może być pozostawiona pusta (nic nie znajduje się między średnikami); w takim przypadku pierwsza sekcja jest stosowana do wszystkich wartości niezerowych.<br /><br /> Jeżeli formatowana liczba jest niezerowa, ale staje się zerem po zaokrągleniu zgodnym z formatem w pierwszej lub drugiej sekcji, wynikowa wartość zero jest formatowana zgodnie z trzecią sekcją.|

Separatory sekcji ignorują wszelkie istniejące wcześniej formatowanie skojarzone z liczbą podczas formatowania wartości końcowej. Na przykład wartości ujemne są zawsze wyświetlane bez znaku minus, gdy używane są separatory sekcji. Jeśli końcowa sformatowana wartość ma mieć znak minus, należy jawnie dołączyć znak minus jako część niestandardowego specyfikatora formatu.

W poniższym przykładzie użyto specyfikatora formatu „;”, aby inaczej formatować liczby dodatnie, ujemne i zera.

[!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
[!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
[!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]

[Powrót do stołu](#table)

## <a name="character-literals"></a>Literały znaków

Specyfikatory formatów, które pojawiają się w niestandardowym ciągu formatu liczbowego, są zawsze interpretowane jako znaki formatowania i nigdy jako znaki dosłowne. Obejmuje to następujące znaki:

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- [E lub e](#SpecifierExponent), w zależności od jego położenia w ciągu formatu.

Wszystkie inne znaki są zawsze interpretowane jako literały znaków i, w operacji formatowania, są uwzględniane w ciągu wynik bez zmian.  W operacji analizowania muszą dokładnie odpowiadać znakom w ciągu wejściowym; w porównaniu jest rozróżniana wielkość liter.

Poniższy przykład ilustruje jedno typowe użycie jednostek znaków literału (w tym przypadku tysięcy):

[!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
[!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]

Istnieją dwa sposoby, aby wskazać, że znaki mają być interpretowane jako znaki literałowe, a nie jako znaki formatowania, dzięki czemu mogą być zawarte w ciągu wynik lub pomyślnie analizowane w ciągu wejściowym:

- Poprzez ucieczkę znaku formatowania. Aby uzyskać więcej informacji, zobacz [znak ucieczki "\\.](#SpecifierEscape)

- Załączając cały ciąg literału w apostrofach cudzysłowu.

W poniższym przykładzie użyto obu podejść do uwzględnienia znaków zastrzeżonych w niestandardowym ciągu formatu liczbowego.

[!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
[!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]

<a name="NotesCustomFormatting"></a>

## <a name="notes"></a>Uwagi

### <a name="floating-point-infinities-and-nan"></a>Bezokojowe bezokołowe i NaN

Niezależnie od ciągu formatu, jeśli <xref:System.Single> wartość <xref:System.Double> typu zmiennoprzecinkowego lub zmiennoprzecinkowego jest dodatnia nieskończoność, ujemna nieskończoność lub nie liczba (NaN), sformatowany ciąg jest wartością <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>odpowiedniego <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, lub <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> właściwością określoną przez aktualnie stosowany <xref:System.Globalization.NumberFormatInfo> obiekt.

### <a name="control-panel-settings"></a>Ustawienia Panelu sterowania

Ustawienia w elemencie **Opcje regionalne i językowe** w Panelu sterowania mają wpływ na ciąg wynikowy wytwarzany przez operację formatowania. Te ustawienia są używane <xref:System.Globalization.NumberFormatInfo> do inicjowania obiektu skojarzonego z bieżącą kulturą wątku, a bieżąca kultura wątku zawiera wartości używane do regulowania formatowania. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> konstruktora do tworzenia <xref:System.Globalization.CultureInfo> wystąpienia nowego obiektu, który reprezentuje tę samą kulturę co bieżąca kultura systemowa, wszystkie dostosowania <xref:System.Globalization.CultureInfo> ustanowione przez element Opcje regionalne i **językowe** w Panelu sterowania zostaną zastosowane do nowego obiektu. Konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> służy do <xref:System.Globalization.CultureInfo> tworzenia obiektu, który nie odzwierciedla dostosowania systemu.

### <a name="rounding-and-fixed-point-format-strings"></a>Ciągi zaokrąglania i formatu stałego

Dla ciągów formatu stałoprzecinkowego (czyli ciągów formatu, które nie zawierają znaków formatu notacji wykładniczej) liczby są zaokrąglane do tylu miejsc dziesiętnych, ile jest symboli zastępczych cyfr po prawej stronie punktu dziesiętnego. Jeśli ciąg formatu nie zawiera punktu dziesiętnego, liczba jest zaokrąglana do najbliższej liczby całkowitej. Jeśli liczba ma więcej cyfr niż jest symboli zastępczych cyfr po lewej stronie punktu dziesiętnego, to dodatkowe cyfry są kopiowane do ciągu wynikowego bezpośrednio przed pierwszym symbolem zastępczym cyfry.

[Powrót do stołu](#table)

<a name="example"></a>

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano dwa ciągi niestandardowego formatu liczb. W obu przypadkach symbol zastępczy cyfry (`#`) wyświetla dane liczbowe, a wszystkie inne znaki są kopiowane do ciągu wynikowego.

[!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
[!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
[!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]

[Powrót do stołu](#table)

## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Standardowe ciągi formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Instrukcje: Uzupełnianie liczby zerami wiodącymi](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Przykład: narzędzie do formatowania .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Przykład: narzędzie do formatowania .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
