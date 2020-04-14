---
title: Standardowe ciągi formatujące liczby
ms.date: 06/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
ms.openlocfilehash: 9b0c784a1c7b6b428636a1a4c99ec8e2bb76a9e0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242715"
---
# <a name="standard-numeric-format-strings"></a>Standardowe ciągi formatujące liczby

Ciągi standardowych formatów liczb służą do formatowania popularnych typów liczbowych. Standardowy ciąg formatu numerycznego przyjmuje formę, `Axx`gdzie:

- `A`jest pojedynczym znakiem alfabetycznym zwanym *specyfikatorem formatu*. Dowolny ciąg formatu liczb, który zawiera więcej niż jeden znak alfabetyczny, w tym znak odstępu, jest interpretowany jako ciąg niestandardowego formatu liczb. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md).

- `xx`jest opcjonalną całkowitej liczby zwanej *specyfikatorem precyzji*. Specyfikator dokładności ma zakres od 0 do 99 i wpływa na liczbę cyfr w wyniku. Należy zauważyć, że specyfikator precyzji steruje liczbą cyfr w reprezentacji ciągu liczby. Nie zaokrągla samej liczby. Aby wykonać operację zaokrąglania, należy użyć metody <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>lub <xref:System.Math.Round%2A?displayProperty=nameWithType> .

  Gdy *specyfikator precyzji* kontroluje liczbę cyfr ułamkowych w ciągu wynik, ciąg wynik odzwierciedla liczbę, która jest zaokrąglana do wynik reprezentacyjny najbliżej nieskończenie precyzyjny wynik. Jeśli istnieją dwa równie zbliżone do reprezentawalnych wyników:
  - **W programie .NET Framework i .NET Core do platformy .NET Core 2.0**środowisko wykonawcze wybiera <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>wynik z większą najmniej znaczącą cyfrą (czyli używającą ).
  - **W programie .NET Core 2.1 i nowszych**środowisko wykonawcze wybiera wynik <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>z nawet najmniej znaczącą cyfrą (czyli używającą ).

  > [!NOTE]
  > Specyfikator precyzji określa liczbę cyfr w ciągu wynikowym. Aby zasypać ciąg wynikowy spacjami wiodącymi lub końcowymi, użyj operacji [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) i zdefiniuj *komponent wyrównania* w elemencie formatu.

Standardowe ciągi formatu numerycznego są obsługiwane przez:

- Niektóre przeciążenia `ToString` metody wszystkich typów numerycznych. Na przykład można podać ciąg formatu <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> numerycznego do i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metod.

- [Funkcja formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).NET , `Write` która `WriteLine` jest <xref:System.Console> używana <xref:System.IO.StreamWriter> przez <xref:System.String.Format%2A?displayProperty=nameWithType> niektóre i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metody i klasy, metodę i metodę. Funkcja formatu złożonego umożliwia uwzględnienie reprezentacji ciągów wielu elementów danych w jednym ciągu, określenie szerokości pola i wyrównanie liczb w polu. Aby uzyskać więcej informacji, zobacz [Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).

- [Interpolowane ciągi](../../csharp/language-reference/tokens/interpolated.md) w języku C# i Visual Basic, które zapewniają uproszczoną składnię w porównaniu do ciągów formatu złożonego.

> [!TIP]
> Można pobrać **narzędzie formatowania**, aplikację .NET Core Windows Forms, która umożliwia stosowanie ciągów formatu do wartości liczbowych lub wartości daty i godziny oraz wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [języka C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) i [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

<a name="table"></a>W poniższej tabeli opisano standardowe specyfikatory formatu numerycznego i są wyświetlane dane wyjściowe próbki wytwarzane przez każdy specyfikator formatu. Zobacz sekcję [Uwagi,](#NotesStandardFormatting) aby uzyskać dodatkowe informacje na temat używania standardowych ciągów formatu numerycznego, a także sekcję [Przykład,](#example) aby uzyskać wyczerpującą ilustrację ich użycia.

|Specyfikator formatu|Nazwa|Opis|Przykłady|
|----------------------|----------|-----------------|--------------|
|„C” lub „c”|Waluta|Wynik: wartość waluty.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator precyzji: Zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [Specyfikator formatu waluty ("C").](#CFormatString)|123.456 ("C", en-US) -> \\123,46 USD<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) ->\\( $123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123.456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|„D” lub „d”|Wartość dziesiętna|Wynik: liczby całkowite z opcjonalnym znakiem minus.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: minimalna liczba cyfr.<br /><br /> Domyślny specyfikator dokładności: minimalna liczba wymaganych cyfr.<br /><br /> Więcej informacji: [Specyfikator formatu dziesiętnego("D").](#DFormatString)|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|
|„E” lub „e”|Wartość wykładnicza (naukowa)|Wynik: zapis wykładniczy.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: 6.<br /><br /> Więcej informacji: [Specyfikator formatu wykładniczego ("E").](#EFormatString)|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1.052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|„F” lub „f”|Wartość stałoprzecinkowa|Wynik: cyfry całkowite i dziesiętne z opcjonalnym znakiem minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator precyzji: Zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [Specyfikator formatu fixed-point ("F").](#FFormatString)|1234.567 ("F", en-US) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234,0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234,56 ("F4", en-US) -> -1234.5600<br /><br /> -1234,56 ("F4", de-DE) -> -1234 5600|
|„G” lub „g”|Ogólne|Wynik: Bardziej zwarta notacja stała lub naukowa.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr znaczących.<br /><br /> Domyślny specyfikator dokładności: zależy od typu liczbowego.<br /><br /> Więcej informacji: [Ogólny ("G") Format Specifier](#GFormatString).|-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123.456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|
|„N” lub „n”|Liczba|Wynik: cyfry całkowite i dziesiętne, separatory grup i separator dziesiętny z opcjonalnym znaku minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny specyfikator precyzji: Zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [Specyfikator formatu numerycznego ("N").](#NFormatString)|1234.567 ("N", en-US) -> 1.234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1.234,0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234,56 ("N3", en-US) -> -1 234 560<br /><br /> -1234,56 ("N3", ru-RU) -> -1 234 560|
|„P” lub „p”|Wartość procentowa|Wynik: liczba pomnożona przez 100 i wyświetlana z symbolem procentu.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny specyfikator precyzji: Zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [Specyfikator formatu procent ("P").](#PFormatString)|1 ("P", en-US) -> 100,00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0,39678 ("P1", en-US) -> -39,7 %<br /><br /> -0,39678 ("P1", fr-FR) -> -39,7 %|
|„R” lub „r”|Wartość dwustronna|Wynik: ciąg, który można dwustronnie konwertować na identyczny numer.<br /><br /> Obsługiwane przez: <xref:System.Single> <xref:System.Double>, <xref:System.Numerics.BigInteger>, i .<br /><br /> Uwaga: Zalecane <xref:System.Numerics.BigInteger> tylko dla typu. W <xref:System.Double> przypadku typów należy użyć "G17"; dla <xref:System.Single> typów, należy użyć "G9". <br> Specyfikator dokładności: ignorowany.<br /><br /> Więcej informacji: [Specyfikator formatu w obie strony ("R").](#RFormatString)|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|
|„X” lub „x”|Wartość szesnastkowa|Wynik: ciąg szesnastkowy.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: liczba cyfr w ciągu wynikowym.<br /><br /> Więcej informacji: [HexaDecimal ("X") Format Specifier](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator|Wynik: Rzuca <xref:System.FormatException> w czasie wykonywania.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Korzystając ze standardowego, numerycznego ciągu formatującego

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Ciąg standardowego formatu liczb może służyć do definiowania formatowania wartości liczbowej na jeden z dwóch sposobów:

- Może być przekazany do przeciążenia `ToString` metody, `format` która ma parametr. Poniższy przykład formatuje wartość liczbową jako ciąg waluty w bieżącej kulturze (w tym przypadku kultury en-US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Może być dostarczony `formatString` jako argument w elemencie <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>formatu <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>używanym z takimi metodami, jak , i . Aby uzyskać więcej informacji, zobacz [Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md). W poniższym przykładzie element formatu jest używany do wstawienia wartości waluty w ciągu.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Opcjonalnie można podać `alignment` argument, aby określić szerokość pola liczbowego i czy jego wartość jest wyrównana do prawej czy do lewej. Poniższy przykład wyrównuje wartość waluty w polu 28 znaków i wyrównuje wartość waluty do prawej w polu 14-znakowym.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Może być dostarczony `formatString` jako argument w interpolowanym elemencie wyrażenia interpolowanego ciągu. Aby uzyskać więcej informacji, zobacz temat [interpolacji ciągów](../../csharp/language-reference/tokens/interpolated.md) w odwołaniu do języka C# lub w temacie [Interpolowane ciągi](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) w odwołaniu do języka Visual Basic.

Poniższe sekcje zawierają szczegółowe informacje o poszczególnych ciągach standardowego formatu liczb.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Specyfikator formatu waluty („C”)

Specyfikator formatu C (currency) konwertuje liczbę na ciąg przedstawiający kwotę w walucie. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych w wynikowym ciągu. Jeśli specyfikator precyzji zostanie pominięty, domyślna <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> precyzja jest definiowana przez właściwość.

Jeśli wartość do sformatowania ma więcej miejsc dziesiętnych niż określona lub domyślna liczba miejsc dziesiętnych, wartość ułamkowa zostanie zaokrąglona w wynikowym ciągu. Jeśli wartość na prawo od określonej liczby miejsc dziesiętnych wynosi 5 lub więcej, ostatnia cyfra w ciągu wynikowym jest zaokrąglana w kierunku od zera.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem zwracanego ciągu.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definiuje położenie symbolu waluty dla wartości dodatnich.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definiuje położenie symbolu waluty dla wartości ujemnych i określa, czy znak ujemny jest <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> reprezentowany przez nawiasy lub właściwość.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje znak ujemny <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> używany, jeśli wskazuje, że nawiasy nie są używane.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definiuje symbol waluty.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości waluty. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|

W poniższym przykładzie jest formatowanie wartości za <xref:System.Double> pomocą specyfikatora formatu waluty:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Powrót do stołu](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Specyfikator formatu dziesiętnego („D”)

Specyfikator formatu D (decimal) konwertuje liczbę na ciąg cyfr dziesiętnych (0–9), poprzedzony znakiem minus, jeśli liczba jest ujemna. Ten format jest obsługiwany tylko w przypadku typów całkowitych.

Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności. Jeśli nie zostanie określony specyfikator dokładności, wartością domyślną jest wartość minimalna wymagana do przedstawienia wartości całkowitej bez zer wiodących.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. Jak pokazano w poniższej tabeli, jedna właściwość ma wpływ na formatowanie ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|

Poniższy przykład formatuje <xref:System.Int32> wartość z specyfikatorem formatu dziesiętnego.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Powrót do stołu](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Specyfikator formatu wykładniczego („E”)

Specyfikator formatu wykładniczego („E”) konwertuje liczbę na ciąg w postaci „-d,ddd...E + ddd” lub „-d,ddd...e+ddd”, gdzie każda litera „d” wskazuje cyfrę (0–9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna. Zawsze dokładnie jedna cyfra poprzedza punkt dziesiętny.

Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator dokładności zostanie pominięty, domyślnie będzie używanych sześć cyfr po punkcie dziesiętnym.

Wielkość liter specyfikatora formatu wskazuje, czy wykładnik potęgi ma być poprzedzany prefiksem „E”, czy „e”. Wykładnik zawsze składa się ze znaku plus lub minus i co najmniej trzech cyfr. W razie potrzeby wykładnik jest dopełniany zerami w celu spełnienia tego minimum.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem zwracanego ciągu.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna zarówno dla współczynnika, jak i wykładnika.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Określa ciąg oddzielający cyfry całkowite od cyfr dziesiętnych we współczynniku.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

W poniższym przykładzie jest formatowanie wartości przy <xref:System.Double> obliczeniu formatu wykładniczego:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Powrót do stołu](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Specyfikator formatu stałoprzecinkowego („F”)

Specyfikator formatu o stałym punkcie ("F") konwertuje liczbę na ciąg formularza "-ddd.ddd..." gdzie każde "d" oznacza cyfrę (0-9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna.

Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. Jeśli specyfikator precyzji zostanie pominięty, bieżąca <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> właściwość dostarcza dokładność numeryczną.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej tabeli wymieniono właściwości <xref:System.Globalization.NumberFormatInfo> obiektu sterującego formatowaniem ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|

Poniższy przykład formatuje <xref:System.Double> <xref:System.Int32> wartość i wartość za pomocą specyfikatora formatu stałego punktu:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Powrót do stołu](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Specyfikator formatu ogólnego („G”)

Specyfikator formatu ogólnego ("G") konwertuje liczbę na bardziej zwartą notację stałą lub naukową, w zależności od typu liczby i tego, czy występuje specyfikator precyzji. Specyfikator dokładności określa maksymalną liczbę cyfr znaczących, które mogą być wyświetlane w ciągu wynikowym. Jeżeli specyfikator dokładności zostanie pominięty lub będzie równy zero, typ liczby określa dokładność domyślną, tak jak opisano w poniższej tabeli.

|Typ liczbowy|Dokładność domyślna|
|------------------|-----------------------|
|<xref:System.Byte> lub <xref:System.SByte>|3 cyfry|
|<xref:System.Int16> lub <xref:System.UInt16>|5 cyfr|
|<xref:System.Int32> lub <xref:System.UInt32>|10 cyfr|
|<xref:System.Int64>|19 cyfr|
|<xref:System.UInt64>|20 cyfr|
|<xref:System.Numerics.BigInteger>|Nieograniczony (taki sam jak ["R"](#RFormatString))|
|<xref:System.Single>|7 cyfr|
|<xref:System.Double>|15 cyfr|
|<xref:System.Decimal>|29 cyfr|

Notacja stałoprzecinkowa jest używana, jeśli wykładnik, który byłby wynikiem wyrażenia liczby w notacji wykładniczej, jest większy niż -5 i mniejszy niż specyfikator dokładności. W przeciwnym wypadku jest używana notacja wykładnicza. Wynik zawiera punkt dziesiętny, jeśli jest to wymagane, a zera końcowe po punkcie dziesiętnym są pomijane. Jeśli specyfikator dokładności jest obecny i liczba cyfr znaczących w wyniku przekracza określoną dokładność, nadmiarowe cyfry końcowe są usuwane przez zaokrąglenie.

Jeśli jednak liczba jest <xref:System.Decimal> a i specyfikator precyzji jest pomijany, notacja o stałym punkcie jest zawsze używana, a końcowe zera są zachowywane.

Jeśli jest używana notacja wykładnicza, wykładnik w wyniku otrzymuje prefiks „E”, jeśli specyfikatorem formatu jest „G”, lub „e”, jeśli specyfikatorem formatu jest „g”. Wykładnik zawiera co najmniej dwie cyfry. Różni się to od formatu notacji wykładniczej tworzonej przez specyfikator formatu wykładniczego, który obejmuje co najmniej trzy cyfry wykładnika.

Należy zauważyć, że <xref:System.Double> w przypadku użycia z wartością specyfikator formatu <xref:System.Double> "G17" zapewnia, że oryginalna wartość pomyślnie rund. Dzieje się <xref:System.Double> tak dlatego, że jest to zgodną z wymogami IEEE 754-2008 podwójną precyzją (`binary64`) zmiennoprzecinkiem, która daje do 17 znaczących cyfr precyzji. Zaleca się jego użycie zamiast [specyfikatora formatu "R",](#RFormatString)ponieważ w niektórych przypadkach "R" nie powiedzie się pomyślnie w obie strony wartości zmiennoprzecinkowych podwójnej precyzji. Poniższy przykład ilustruje jeden taki przypadek.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

W przypadku <xref:System.Single> użycia z wartością specyfikator formatu "G9" zapewnia, że oryginalna <xref:System.Single> wartość pomyślnie rund. Dzieje się <xref:System.Single> tak dlatego, że jest to zgodną z wymaganiami IEEE 754-2008 pojedynczą precyzją (`binary32`) zmiennoprzecinku, która daje do dziewięciu znaczących cyfr precyzji. Ze względu na wydajność zalecamy jego użycie zamiast [specyfikatora formatu "R".](#RFormatString)

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

W poniższym przykładzie formatuje różne wartości zmiennoprzecinkowe z ogólnym specyfikatorem formatu:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Powrót do stołu](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Specyfikator formatu numerycznego („N”)

Specyfikator formatu liczbowego („N”) konwertuje liczbę na ciąg w postaci „-d ddd ddd,ddd…”, gdzie „-” oznacza w razie potrzeby liczbę ujemną, „d” oznacza cyfrę (0–9), „ ” oznacza separator grupy, a „,” oznacza symbol punktu dziesiętnego. Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator precyzji zostanie pominięty, liczba miejsc dziesiętnych <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> jest definiowana przez bieżącą właściwość.

Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definiuje format wartości ujemnych i określa, czy znak ujemny jest reprezentowany <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> przez nawiasy lub właściwość.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się pomiędzy separatorami grup.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|

W poniższym przykładzie są formatowane różne wartości zmiennoprzecinkowe ze specyfikatorem formatu liczb:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Powrót do stołu](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Specyfikator formatu procenta („P”)

Specyfikator formatu procentowego („P”) mnoży liczbę przez 100 i konwertuje ją na ciąg, który przedstawia wartość procentową. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. Jeśli specyfikator precyzji zostanie pominięty, używana jest <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> domyślna dokładność numeryczna podana przez bieżącą właściwość.

W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem zwracanego ciągu.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Definiuje położenie symbolu procentu dla wartości dodatnich.|
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Definiuje położenie symbol procentu i symbolu wartości ujemnej dla wartości ujemnych.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Definiuje symbol procentu.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości procentowej. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|

W poniższym przykładzie formatuje wartości zmiennoprzecinkowe z specyfikatorem formatu procentu:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Powrót do stołu](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Specyfikator formatu obustronnej konwersji („R”)

Specyfikator formatu w obie strony ("R") próbuje upewnić się, że wartość liczbowa konwertowana na ciąg jest analizowana z powrotem na tę samą wartość liczbową. Ten format jest obsługiwany <xref:System.Single>tylko <xref:System.Double>dla <xref:System.Numerics.BigInteger> , i typów.

Dla <xref:System.Double> wartości specyfikator formatu "R" w niektórych przypadkach nie uda się w obie strony oryginalnej wartości. Dla <xref:System.Double> obu <xref:System.Single> i wartości, oferuje również stosunkowo niską wydajność. Zamiast tego zaleca się użycie specyfikatora formatu ["G17"](#GFormatString) dla <xref:System.Double> wartości i specyfikatora <xref:System.Single> formatu ["G9",](#GFormatString) aby pomyślnie wartości w obie strony.

Gdy <xref:System.Numerics.BigInteger> wartość jest sformatowana przy użyciu tego specyfikatora, <xref:System.Numerics.BigInteger> jej reprezentacja ciągów zawiera wszystkie cyfry znaczące w wartości.

Można dodawać specyfikator dokładności, ale jest on ignorowany. W przypadku korzystania z tego specyfikatora konwersje dwustronne mają pierwszeństwo przed dokładnością.
Na ciąg wynikowy mają wpływ informacje o <xref:System.Globalization.NumberFormatInfo> formatowaniu bieżącego obiektu. W poniższej <xref:System.Globalization.NumberFormatInfo> tabeli wymieniono właściwości sterujące formatowaniem ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

Poniższy przykład formatuje <xref:System.Numerics.BigInteger> wartość za pomocą specyfikatora formatu w obie strony.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> W niektórych <xref:System.Double> przypadkach wartości sformatowane za pomocą standardowego ciągu formatu numerycznego `/platform:x64` `/platform:anycpu` "R" nie są pomyślnie w obie strony, jeśli są kompilowane przy użyciu przełączników lub i są uruchamiane w systemach 64-bitowych. Zobacz poniższy akapit, aby uzyskać więcej informacji.

Aby obejść problem <xref:System.Double> wartości sformatowanych za pomocą standardowego ciągu formatu numerycznego "R", który nie został pomyślnie zaokrąglony, jeśli został skompilowany przy użyciu przełączników `/platform:x64` lub `/platform:anycpu` i uruchomiony w systemach 64-bitowych., można formatować <xref:System.Double> wartości przy użyciu standardowego ciągu formatu numerycznego "G17". W poniższym przykładzie użyto ciągu <xref:System.Double> formatu "R" z wartością, która nie jest pomyślna w obie strony, a także używa ciągu formatu "G17", aby pomyślnie w obie strony oryginalną wartość:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Powrót do stołu](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Specyfikator formatu szesnastkowego („X”)

Specyfikator formatu szesnastkowego („X”) konwertuje liczbę na ciąg cyfr szesnastkowych. Wielkość liter specyfikatora formatu wskazuje, czy w przypadku cyfr szesnastkowych, które są większe niż 9, należy używać wielkich, czy małych liter. Na przykład użycie specyfikatora „X” umożliwia uzyskanie cyfr „ABCDEF”, a specyfikatora „x” — cyfr „abcdef”. Ten format jest obsługiwany tylko w przypadku typów całkowitych.

Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności.

Na ciąg wynikowy nie mają wpływu informacje <xref:System.Globalization.NumberFormatInfo> o formatowaniu bieżącego obiektu.

Poniższy przykład <xref:System.Int32> formatuje wartości za pomocą specyfikatora formatu szesnastkowego.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Powrót do stołu](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Uwagi

### <a name="control-panel-settings"></a>Ustawienia panelu sterowania

Ustawienia w elemencie **Opcje regionalne i językowe** w Panelu sterowania mają wpływ na ciąg wynikowy wytwarzany przez operację formatowania. Te ustawienia są używane <xref:System.Globalization.NumberFormatInfo> do inicjowania obiektu skojarzonego z bieżącą kulturą wątku, która zawiera wartości używane do regulowania formatowania. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> jeśli konstruktor jest używany do tworzenia <xref:System.Globalization.CultureInfo> wystąpienia nowego obiektu, który reprezentuje tę samą kulturę co bieżąca kultura systemowa, wszystkie dostosowania <xref:System.Globalization.CultureInfo> ustanowione przez element Opcje regionalne i **językowe** w Panelu sterowania zostaną zastosowane do nowego obiektu. Konstruktora <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> służy do <xref:System.Globalization.CultureInfo> tworzenia obiektu, który nie odzwierciedla dostosowania systemu.

### <a name="numberformatinfo-properties"></a>Właściwości klasy NumberFormatInfo

Formatowanie zależy od właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu, który jest niejawnie przez bieżącą kulturę <xref:System.IFormatProvider> wątku lub jawnie przez parametr metody, która wywołuje formatowanie. Określ <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.CultureInfo> lub obiekt dla tego parametru.

> [!NOTE]
> Aby uzyskać informacje na temat dostosowywania wzorców lub ciągów używanych w formatowaniu wartości liczbowych, zobacz temat <xref:System.Globalization.NumberFormatInfo> klasy.

### <a name="integral-and-floating-point-numeric-types"></a>Całkowite i zmiennoprzecinkowe rodzaje wartości numerycznych

Niektóre opisy specyfikatorów standardowego formatu liczb odnoszą się do całkowitych lub zmiennoprzecinkowych typów liczbowych. Integralną typami liczbowymi <xref:System.SByte> <xref:System.Int16>są <xref:System.Int32> <xref:System.Byte>, , <xref:System.UInt64>, <xref:System.Numerics.BigInteger> <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, , i . Typy liczbowe zmiennoprzecinkowe to <xref:System.Decimal>, <xref:System.Single>i <xref:System.Double>.

### <a name="floating-point-infinities-and-nan"></a>Zmiennoprzecinkowe nieskończoności i NaN

Niezależnie od ciągu formatu, jeśli <xref:System.Single> wartość <xref:System.Double> typu zmiennoprzecinkowego lub zmiennoprzecinkowego jest dodatnia nieskończoność, ujemna nieskończoność lub nie liczba (NaN), sformatowany ciąg jest wartością <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>odpowiedniego , <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>lub <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> właściwością określoną przez aktualnie stosowany <xref:System.Globalization.NumberFormatInfo> obiekt.

## <a name="example"></a>Przykład

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

W poniższym przykładzie całkowita i zmiennoprzecinkowa wartość liczbowa jest formatowana przy użyciu kultury en-US i wszystkich specyfikatorów standardowego formatu liczb. W tym przykładzie użyto<xref:System.Double> dwóch <xref:System.Int32>określonych typów liczbowych ( i ), ale<xref:System.Byte>przyniesie <xref:System.SByte> <xref:System.Int16>podobne <xref:System.Int32>wyniki dla każdego z innych typów bazowych liczbowych ( <xref:System.Int64>, , , , <xref:System.UInt16>, , <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, , <xref:System.Decimal>, , i <xref:System.Single>).

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.NumberFormatInfo>
- [Niestandardowe ciągi formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Instrukcje: Uzupełnianie liczby zerami wiodącymi](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Formatowanie kompozytowe](../../../docs/standard/base-types/composite-formatting.md)
- [Przykład: narzędzie do formatowania .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Przykład: narzędzie do formatowania .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
