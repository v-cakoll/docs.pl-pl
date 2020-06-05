---
title: Standardowe ciągi formatujące liczby
description: W tym artykule dowiesz się, jak używać standardowych ciągów formatu liczbowego do formatowania wspólnych typów liczbowych w reprezentacjach tekstowych w programie .NET.
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
ms.openlocfilehash: 605438a5f0e4b5bd9ade96c9db0416ee8611f311
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447124"
---
# <a name="standard-numeric-format-strings"></a>Standardowe ciągi formatujące liczby

Ciągi standardowych formatów liczb służą do formatowania popularnych typów liczbowych. Standardowy ciąg formatu liczbowego przyjmuje formę `Axx` , gdzie:

- `A`jest pojedynczym znakiem alfabetycznym o nazwie *specyfikator formatu*. Dowolny ciąg formatu liczb, który zawiera więcej niż jeden znak alfabetyczny, w tym znak odstępu, jest interpretowany jako ciąg niestandardowego formatu liczb. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatujące](custom-numeric-format-strings.md).

- `xx`jest opcjonalną liczbą całkowitą o nazwie *specyfikator dokładności*. Specyfikator dokładności ma zakres od 0 do 99 i wpływa na liczbę cyfr w wyniku. Należy zauważyć, że specyfikator dokładności określa liczbę cyfr w ciągu reprezentującym liczbę. Nie zaokrągla samej liczby. Aby wykonać operację zaokrąglania, należy użyć <xref:System.Math.Ceiling%2A?displayProperty=nameWithType> metody, <xref:System.Math.Floor%2A?displayProperty=nameWithType> , lub <xref:System.Math.Round%2A?displayProperty=nameWithType> .

  Gdy *specyfikator dokładności* kontroluje liczbę ułamków w ciągu wynikowym, ciąg wynikowy odzwierciedla liczbę, która jest zaokrąglana do wyniku, który zostanie zaprezentowany najbliżej nieskończonie precyzyjnego wyniku. Jeśli istnieją dwa równie zbliżone wyniki:
  - **Na .NET Framework i .NET Core do programu .net core 2,0**środowisko uruchomieniowe wybiera wynik z bardziej mniejszą cyfrą (czyli przy użyciu <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType> ).
  - **W przypadku platformy .NET Core 2,1 i nowszych**środowisko uruchomieniowe wybiera wynik z parzystą cyfrą, która jest równa co najmniej znaczącej liczbie (czyli przy użyciu <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType> ).

  > [!NOTE]
  > Specyfikator dokładności określa liczbę cyfr w ciągu wynikowym. Aby zapełnić ciąg wynikowy początkowymi lub końcowymi spacjami, użyj funkcji [formatowania złożonego](composite-formatting.md) i zdefiniuj *składnik wyrównania* w elemencie formatu.

Ciągi standardowego formatu liczbowego są obsługiwane przez:

- Niektóre przeciążenia `ToString` metody dla wszystkich typów liczbowych. Na przykład można podać ciąg formatu liczbowego dla <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metod i.

- [Funkcja formatowania złożonego](composite-formatting.md)platformy .NET, która jest używana przez niektóre `Write` i `WriteLine` metody <xref:System.Console> klasy i <xref:System.IO.StreamWriter> , metody i <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metody. Funkcja formatu złożonego umożliwia dołączenie ciągu reprezentującego wiele elementów danych w jednym ciągu, aby określić szerokość pola i wyrównać liczby w polu. Aby uzyskać więcej informacji, zobacz [formatowanie złożone](composite-formatting.md).

- [Ciągi interpolowane](../../csharp/language-reference/tokens/interpolated.md) w języku C# i Visual Basic, które zapewniają uproszczoną składnię w porównaniu z ciągami formatu złożonego.

> [!TIP]
> Możesz pobrać **Narzędzie formatowania**, aplikację .net Core Windows Forms, która umożliwia stosowanie ciągów formatowania do wartości liczbowych lub daty i godziny i wyświetla ciąg wynikowy. Kod źródłowy jest dostępny dla [języków C#](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs) i [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb).

<a name="table"></a>W poniższej tabeli opisano standardowe specyfikatory formatu liczbowego i przedstawiono przykładowe dane wyjściowe generowane przez każdy specyfikator formatu. Zapoznaj się z sekcją [uwagi](#NotesStandardFormatting) , aby uzyskać dodatkowe informacje dotyczące używania ciągów standardowego formatu liczb, oraz sekcję [przykładową](#example) dla obszernej ilustracji dotyczącej ich używania.

|Specyfikator formatu|Nazwa|Opis|Przykłady|
|----------------------|----------|-----------------|--------------|
|„C” lub „c”|Waluta|Wynik: wartość waluty.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Więcej informacji: [specyfikator formatu waluty ("C")](#CFormatString).|123,456 ("C", en-US)-> \\ $123,46<br /><br /> 123,456 ("C", fr-FR)-> 123, 46 €<br /><br /> 123,456 ("C", ja-JP) — > ¥123<br /><br /> -123,456 ("C3", en-US)-> ( \\ $123,456)<br /><br /> -123,456 ("C3", fr-FR)->-€123 456<br /><br /> -123,456 ("C3", ja-JP)->-¥123,456|
|„D” lub „d”|Wartość dziesiętna|Wynik: liczby całkowite z opcjonalnym znakiem minus.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: minimalna liczba cyfr.<br /><br /> Domyślny specyfikator dokładności: minimalna liczba wymaganych cyfr.<br /><br /> Więcej informacji: [specyfikator formatu dziesiętnego ("D")](#DFormatString).|1234 ("D")-> 1234<br /><br /> -1234 ("D6")->-001234|
|„E” lub „e”|Wartość wykładnicza (naukowa)|Wynik: zapis wykładniczy.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: 6.<br /><br /> Więcej informacji: [specyfikator formatu wykładniczego ("E")](#EFormatString).|1052,0329112756 ("E", en-US)-> 1.052033 E + 003<br /><br /> 1052,0329112756 ("e", fr-FR)-> 1, 052033e + 003<br /><br /> -1052,0329112756 ("E2", en-US)->-1,05 e + 003<br /><br /> -1052,0329112756 ("E2", fr-FR)->-1, 05E + 003|
|„F” lub „f”|Wartość stałoprzecinkowa|Wynik: cyfry całkowite i dziesiętne z opcjonalnym znakiem minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Więcej informacji: [specyfikator formatu stałego punktu ("F")](#FFormatString).|1234,567 ("F", en-US) — > 1234,57<br /><br /> 1234,567 ("F", de-DE)-> 1234, 57<br /><br /> 1234 ("F1", en-US)-> 1234,0<br /><br /> 1234 ("F1", de-DE)-> 1234, 0<br /><br /> -1234,56 ("F4", en-US)->-1234,5600<br /><br /> -1234,56 ("F4", de-DE)->-1234, 1234,5600|
|„G” lub „g”|Ogólne|Wynik: bardziej zwartość notacji stałej lub wykładniczej.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr znaczących.<br /><br /> Domyślny specyfikator dokładności: zależy od typu liczbowego.<br /><br /> Więcej informacji: [specyfikator formatu ogólnego ("G")](#GFormatString).|-123,456 ("G", en-US)->-123,456<br /><br /> -123,456 ("G", SV-SE)->-123 456<br /><br /> 123,4546 ("G4", en-US) — > 123,5<br /><br /> 123,4546 ("G4", SV-SE)-> 123, 5<br /><br /> -1.234567890 e-25 ("G", en-US)->-1.23456789 E-25<br /><br /> -1.234567890 e-25 ("G", SV-SE)->-1, 23456789E-25|
|„N” lub „n”|Liczba|Wynik: cyfry całkowite i dziesiętne, separatory grup i separator dziesiętny z opcjonalnym znaku minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Więcej informacji: [specyfikator formatu liczbowego ("N")](#NFormatString).|1234,567 ("N", en-US) — > 1 234,57<br /><br /> 1234,567 ("N", ru-RU) — > 1 234, 57<br /><br /> 1234 ("N1", en-US) — > 1 234,0<br /><br /> 1234 ("N1", ru-RU) — > 1 234, 0<br /><br /> -1234,56 ("N3", en-US)->-1 234,560<br /><br /> -1234,56 ("N3", ru-RU)->-1 234 560|
|„P” lub „p”|Wartość procentowa|Wynik: liczba pomnożona przez 100 i wyświetlana z symbolem procentu.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Więcej informacji: [specyfikator formatu procentowego ("P")](#PFormatString).|1 ("P", en-US)-> 100,00%<br /><br /> 1 ("P", fr-FR)-> 100, 00%<br /><br /> -0,39678 ("P1", en-US)->-39,7%<br /><br /> -0,39678 ("P1", fr-FR)->-39, 7%|
|„R” lub „r”|Wartość dwustronna|Wynik: ciąg, który można dwustronnie konwertować na identyczny numer.<br /><br /> Obsługiwane przez: <xref:System.Single> , <xref:System.Double> , i <xref:System.Numerics.BigInteger> .<br /><br /> Uwaga: zalecane tylko dla tego <xref:System.Numerics.BigInteger> typu. Dla <xref:System.Double> typów Użyj "G17"; dla <xref:System.Single> typów, użyj "G9". <br> Specyfikator dokładności: ignorowany.<br /><br /> Więcej informacji: [specyfikator formatu rundying ("R")](#RFormatString).|123456789,12345678 ("R") — > 123456789,12345678<br /><br /> -1234567890,12345678 ("R")->-1234567890,1234567|
|„X” lub „x”|Wartość szesnastkowa|Wynik: ciąg szesnastkowy.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: liczba cyfr w ciągu wynikowym.<br /><br /> Więcej informacji: [specyfikator formatu szesnastkowego ("X")](#XFormatString).|255 ("X") — > FF<br /><br /> -1 ("x")-> FF<br /><br /> 255 ("X4") — > 00ff<br /><br /> -1 ("X4")-> 00FF|
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator|Wynik: zgłasza <xref:System.FormatException> w czasie wykonywania.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Korzystając ze standardowego, numerycznego ciągu formatującego

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Ciąg standardowego formatu liczb może służyć do definiowania formatowania wartości liczbowej na jeden z dwóch sposobów:

- Można go przesłać do przeciążenia `ToString` metody, która ma `format` parametr. Poniższy przykład formatuje wartość liczbową jako ciąg waluty w bieżącej kulturze (w tym przypadku kultury en-US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Może być dostarczony jako `formatString` argument w elemencie formatu używany z takimi metodami jak <xref:System.String.Format%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> . Aby uzyskać więcej informacji, zobacz [formatowanie złożone](composite-formatting.md). W poniższym przykładzie element formatu jest używany do wstawienia wartości waluty w ciągu.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Opcjonalnie możesz podać `alignment` argument, aby określić szerokość pola liczbowego i czy jego wartość jest wyrównana do prawej lub do lewej. Poniższy przykład umożliwia wyrównanie wartości walutowej w 28-znakowym polu i wyrównanie wartości walutowej do pola 14 znaków.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Może być dostarczony jako `formatString` argument w elemencie wyrażenia interpolowanego ciągu interpolowanego. Aby uzyskać więcej informacji, zobacz temat [Interpolacja ciągów](../../csharp/language-reference/tokens/interpolated.md) w dokumentacji C# lub w temacie [ciągi interpolowane](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) w odwołaniu Visual Basic.

Poniższe sekcje zawierają szczegółowe informacje o poszczególnych ciągach standardowego formatu liczb.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Specyfikator formatu waluty („C”)

Specyfikator formatu C (currency) konwertuje liczbę na ciąg przedstawiający kwotę w walucie. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych w wynikowym ciągu. Jeśli specyfikator dokładności zostanie pominięty, domyślna precyzja jest definiowana przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> Właściwość.

Jeśli wartość do sformatowania ma więcej miejsc dziesiętnych niż określona lub domyślna liczba miejsc dziesiętnych, wartość ułamkowa zostanie zaokrąglona w wynikowym ciągu. Jeśli wartość na prawo od określonej liczby miejsc dziesiętnych wynosi 5 lub więcej, ostatnia cyfra w ciągu wynikowym jest zaokrąglana w kierunku od zera.

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie zwracanego ciągu.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definiuje położenie symbolu waluty dla wartości dodatnich.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definiuje położenie symbolu waluty dla wartości ujemnych i określa, czy znak minus jest reprezentowany przez nawiasy, czy <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Właściwość.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje znak ujemny używany, jeśli <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> wskazuje, że nawiasy nie są używane.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definiuje symbol waluty.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości waluty. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|

Poniższy przykład formatuje <xref:System.Double> wartość przy użyciu specyfikatora formatu waluty:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Wróć do tabeli](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Specyfikator formatu dziesiętnego („D”)

Specyfikator formatu D (decimal) konwertuje liczbę na ciąg cyfr dziesiętnych (0–9), poprzedzony znakiem minus, jeśli liczba jest ujemna. Ten format jest obsługiwany tylko w przypadku typów całkowitych.

Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności. Jeśli nie zostanie określony specyfikator dokładności, wartością domyślną jest wartość minimalna wymagana do przedstawienia wartości całkowitej bez zer wiodących.

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Jak pokazano w poniższej tabeli, jedna właściwość ma wpływ na formatowanie ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|

Poniższy przykład formatuje <xref:System.Int32> wartość przy użyciu specyfikatora formatu dziesiętnego.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Wróć do tabeli](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Specyfikator formatu wykładniczego („E”)

Specyfikator formatu wykładniczego („E”) konwertuje liczbę na ciąg w postaci „-d,ddd...E + ddd” lub „-d,ddd...e+ddd”, gdzie każda litera „d” wskazuje cyfrę (0–9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna. Zawsze dokładnie jedna cyfra poprzedza punkt dziesiętny.

Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator dokładności zostanie pominięty, domyślnie będzie używanych sześć cyfr po punkcie dziesiętnym.

Wielkość liter specyfikatora formatu wskazuje, czy wykładnik potęgi ma być poprzedzany prefiksem „E”, czy „e”. Wykładnik zawsze składa się ze znaku plus lub minus i co najmniej trzech cyfr. W razie potrzeby wykładnik jest dopełniany zerami w celu spełnienia tego minimum.

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie zwracanego ciągu.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna zarówno dla współczynnika, jak i wykładnika.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Określa ciąg oddzielający cyfry całkowite od cyfr dziesiętnych we współczynniku.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

Poniższy przykład formatuje <xref:System.Double> wartość przy użyciu specyfikatora formatu wykładniczego:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Wróć do tabeli](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Specyfikator formatu stałoprzecinkowego („F”)

Specyfikator formatu stałego ("F") konwertuje liczbę na ciąg w postaci "-. DDD..." gdzie każda litera "d" wskazuje cyfrę (0-9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna.

Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. Jeśli specyfikator dokładności zostanie pominięty, bieżąca <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> Właściwość dostarcza precyzji liczbowej.

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę właściwości <xref:System.Globalization.NumberFormatInfo> obiektu, które sterują formatowaniem ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|

Poniższy przykład formatuje <xref:System.Double> i <xref:System.Int32> wartość przy użyciu specyfikatora formatu ustalonego:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Wróć do tabeli](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Specyfikator formatu ogólnego („G”)

Specyfikator formatu ogólnego ("G") konwertuje liczbę na bardziej zwartą notacji stałej lub wykładniczej, w zależności od typu liczby i tego, czy jest obecny Specyfikator dokładności. Specyfikator dokładności określa maksymalną liczbę cyfr znaczących, które mogą być wyświetlane w ciągu wynikowym. Jeżeli specyfikator dokładności zostanie pominięty lub będzie równy zero, typ liczby określa dokładność domyślną, tak jak opisano w poniższej tabeli.

|Typ liczbowy|Dokładność domyślna|
|------------------|-----------------------|
|<xref:System.Byte> lub <xref:System.SByte>|3 cyfry|
|<xref:System.Int16> lub <xref:System.UInt16>|5 cyfr|
|<xref:System.Int32> lub <xref:System.UInt32>|10 cyfr|
|<xref:System.Int64>|19 cyfr|
|<xref:System.UInt64>|20 cyfr|
|<xref:System.Numerics.BigInteger>|Bez ograniczeń (analogicznie jak ["R"](#RFormatString))|
|<xref:System.Single>|7 cyfr|
|<xref:System.Double>|15 cyfr|
|<xref:System.Decimal>|29 cyfr|

Notacja stałoprzecinkowa jest używana, jeśli wykładnik, który byłby wynikiem wyrażenia liczby w notacji wykładniczej, jest większy niż -5 i mniejszy niż specyfikator dokładności. W przeciwnym wypadku jest używana notacja wykładnicza. Wynik zawiera punkt dziesiętny, jeśli jest to wymagane, a zera końcowe po punkcie dziesiętnym są pomijane. Jeśli specyfikator dokładności jest obecny i liczba cyfr znaczących w wyniku przekracza określoną dokładność, nadmiarowe cyfry końcowe są usuwane przez zaokrąglenie.

Jeśli jednak liczba ma wartość <xref:System.Decimal> i specyfikator dokładności zostanie pominięty, notacja stałego punktu jest zawsze używana i końcowe zera są zachowywane.

Jeśli jest używana notacja wykładnicza, wykładnik w wyniku otrzymuje prefiks „E”, jeśli specyfikatorem formatu jest „G”, lub „e”, jeśli specyfikatorem formatu jest „g”. Wykładnik zawiera co najmniej dwie cyfry. Różni się to od formatu notacji wykładniczej tworzonej przez specyfikator formatu wykładniczego, który obejmuje co najmniej trzy cyfry wykładnika.

Należy pamiętać, że w przypadku użycia z <xref:System.Double> wartością specyfikator formatu "G17" gwarantuje, że oryginalna <xref:System.Double> wartość została pomyślnie przebłądzenia. Jest to spowodowane tym, <xref:System.Double> że jest to zgodna z IEEE 754-2008 liczba zmiennoprzecinkowa o podwójnej precyzji `binary64` , która zapewnia maksymalnie 17 znaczących cyfr dokładności. Zaleca się używanie zamiast [specyfikatora formatu "r"](#RFormatString), ponieważ w niektórych przypadkach "r" nie powiodło się pomyślnie rundy wartości zmiennoprzecinkowych podwójnej precyzji. Poniższy przykład ilustruje jeden przypadek.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

W przypadku użycia z <xref:System.Single> wartością specyfikator formatu "G9" gwarantuje, że oryginalna <xref:System.Single> wartość została pomyślnie przerundna. Jest to spowodowane tym, <xref:System.Single> że jest to zgodna z IEEE 754-2008 `binary32` liczba zmiennoprzecinkowa o pojedynczej precyzji, która daje maksymalnie dziewięć znaczących cyfr dokładności. Ze względu na wydajność zaleca się użycie zamiast [specyfikatora formatu "R"](#RFormatString).

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

Poniższy przykład formatuje różne wartości zmiennoprzecinkowe przy użyciu specyfikatora formatu ogólnego:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Wróć do tabeli](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Specyfikator formatu numerycznego („N”)

Specyfikator formatu liczbowego („N”) konwertuje liczbę na ciąg w postaci „-d ddd ddd,ddd…”, gdzie „-” oznacza w razie potrzeby liczbę ujemną, „d” oznacza cyfrę (0–9), „ ” oznacza separator grupy, a „,” oznacza symbol punktu dziesiętnego. Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator dokładności zostanie pominięty, Liczba miejsc dziesiętnych jest definiowana przez bieżącą <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> Właściwość.

Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definiuje format wartości ujemnych i określa, czy znak minus jest reprezentowany przez nawiasy, czy <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Właściwość.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się pomiędzy separatorami grup.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|

Poniższy przykład formatuje różne wartości zmiennoprzecinkowe przy użyciu specyfikatora formatu liczb:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Wróć do tabeli](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Specyfikator formatu procenta („P”)

Specyfikator formatu procentowego („P”) mnoży liczbę przez 100 i konwertuje ją na ciąg, który przedstawia wartość procentową. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. Jeśli specyfikator dokładności zostanie pominięty, zostanie użyta Domyślna precyzja liczbowa podana przez bieżącą <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> Właściwość.

Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie zwracanego ciągu.

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

W poniższym przykładzie wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu wartości procentowej:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Wróć do tabeli](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Specyfikator formatu obustronnej konwersji („R”)

Specyfikator formatu rundy ("R") próbuje upewnić się, że wartość liczbowa, która jest konwertowana na ciąg, zostanie przeanalizowana z powrotem na taką samą wartość liczbową. Ten format jest obsługiwany tylko w przypadku <xref:System.Single> <xref:System.Double> typów, i <xref:System.Numerics.BigInteger> .

<xref:System.Double>W przypadku wartości, specyfikator formatu "R" w niektórych przypadkach nie może pomyślnie wykonać rundy pierwotnej wartości. Dla obu <xref:System.Double> i <xref:System.Single> wartości, oferuje również stosunkowo niską wydajność. Zamiast tego zalecamy użycie specyfikatora formatu ["G17"](#GFormatString) dla <xref:System.Double> wartości i specyfikatora formatu ["G9"](#GFormatString) , aby pomyślnie zaokrąglić <xref:System.Single> wartości.

Gdy <xref:System.Numerics.BigInteger> wartość jest formatowana przy użyciu tego specyfikatora, jego reprezentacja w postaci ciągu zawiera wszystkie znaczące cyfry w <xref:System.Numerics.BigInteger> wartości.

Można dodawać specyfikator dokładności, ale jest on ignorowany. W przypadku korzystania z tego specyfikatora konwersje dwustronne mają pierwszeństwo przed dokładnością.
Informacje o formatowaniu bieżącego obiektu mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> . Poniższa tabela zawiera listę <xref:System.Globalization.NumberFormatInfo> właściwości, które kontrolują formatowanie ciągu wynikowego.

|Właściwość NumberFormatInfo|Opis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|

Poniższy przykład formatuje <xref:System.Numerics.BigInteger> wartość przy użyciu specyfikatora formatu okrężnego.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> W niektórych przypadkach <xref:System.Double> wartości sformatowane przy użyciu standardowego ciągu formatu liczbowego "R" nie przeprowadzono pomyślnie rundy w przypadku skompilowania za `/platform:x64` pomocą `/platform:anycpu` przełącznika lub i uruchomienia w systemach 64-bitowych. Więcej informacji można znaleźć w poniższym akapicie.

Aby obejść problem z <xref:System.Double> wartościami sformatowanymi przy użyciu standardowego ciągu formatu liczbowego "R", który nie został pomyślnie zaokrąglony, w przypadku skompilowania za pomocą `/platform:x64` lub `/platform:anycpu` przełączników i uruchomienia w systemach 64-bitowych. można sformatować <xref:System.Double> wartości przy użyciu standardowego ciągu formatu liczbowego "G17". Poniższy przykład używa ciągu formatu "R" z <xref:System.Double> wartością, która nie jest pomyślna, a także używa ciągu formatu "G17", aby pomyślnie zaokrąglić oryginalną wartość:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Wróć do tabeli](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Specyfikator formatu szesnastkowego („X”)

Specyfikator formatu szesnastkowego („X”) konwertuje liczbę na ciąg cyfr szesnastkowych. Wielkość liter specyfikatora formatu wskazuje, czy w przypadku cyfr szesnastkowych, które są większe niż 9, należy używać wielkich, czy małych liter. Na przykład użycie specyfikatora „X” umożliwia uzyskanie cyfr „ABCDEF”, a specyfikatora „x” — cyfr „abcdef”. Ten format jest obsługiwany tylko w przypadku typów całkowitych.

Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności.

Informacje o formatowaniu bieżącego obiektu nie mają wpływ na ciąg wynikowy <xref:System.Globalization.NumberFormatInfo> .

Poniższy przykład formatuje <xref:System.Int32> wartości ze specyfikatorem formatu szesnastkowego.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Wróć do tabeli](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Uwagi

### <a name="control-panel-settings"></a>Ustawienia panelu sterowania

Ustawienia w elemencie **Opcje regionalne i językowe** w panelu sterowania wpływają na ciąg wynikowy generowany przez operację formatowania. Te ustawienia są używane do inicjowania <xref:System.Globalization.NumberFormatInfo> obiektu skojarzonego z bieżącą kulturą wątku, która zapewnia wartości używane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.

Ponadto, jeśli <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> Konstruktor jest używany do utworzenia wystąpienia nowego <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje tę samą kulturę co bieżąca kultura systemu, wszelkie dostosowania ustanowione przez element **Opcje regionalne i językowe** w panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Można użyć konstruktora, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> Aby utworzyć <xref:System.Globalization.CultureInfo> obiekt, który nie odzwierciedla dostosowań systemu.

### <a name="numberformatinfo-properties"></a>Właściwości klasy NumberFormatInfo

Na formatowanie mają wpływ właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu, który jest dostarczany niejawnie przez bieżącą kulturę wątku lub jawnie przez <xref:System.IFormatProvider> parametr metody, która wywołuje formatowanie. Określ <xref:System.Globalization.NumberFormatInfo> obiekt lub <xref:System.Globalization.CultureInfo> dla tego parametru.

> [!NOTE]
> Aby uzyskać informacje na temat dostosowywania wzorców lub ciągów używanych w formatowaniu wartości liczbowych, zobacz <xref:System.Globalization.NumberFormatInfo> temat Klasa.

### <a name="integral-and-floating-point-numeric-types"></a>Całkowite i zmiennoprzecinkowe rodzaje wartości numerycznych

Niektóre opisy specyfikatorów standardowego formatu liczb odnoszą się do całkowitych lub zmiennoprzecinkowych typów liczbowych. Całkowite typy liczbowe to,,,,,, <xref:System.Byte> <xref:System.SByte> ,, <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> i <xref:System.Numerics.BigInteger> . Zmiennoprzecinkowe typy liczbowe to <xref:System.Decimal> , <xref:System.Single> , i <xref:System.Double> .

### <a name="floating-point-infinities-and-nan"></a>Zmiennoprzecinkowe nieskończoności i NaN

Bez względu na ciąg formatu, jeśli wartość <xref:System.Single> <xref:System.Double> typu lub zmiennoprzecinkowego jest nieskończoności dodatniej, nieskończoności ujemnej lub nie jest liczbą (NaN), sformatowany ciąg jest wartością odpowiedniej <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A> <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A> właściwości, lub właściwość, <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> która jest określona przez aktualnie stosowany <xref:System.Globalization.NumberFormatInfo> obiekt.

## <a name="example"></a>Przykład

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

W poniższym przykładzie całkowita i zmiennoprzecinkowa wartość liczbowa jest formatowana przy użyciu kultury en-US i wszystkich specyfikatorów standardowego formatu liczb. W tym przykładzie używamy dwóch określonych typów liczbowych ( <xref:System.Double> i <xref:System.Int32> ), ale byłyby podobne wyniki dla dowolnego z innych liczbowych typów podstawowych (,,,,,,,,, <xref:System.Byte> <xref:System.SByte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Numerics.BigInteger> <xref:System.Decimal> i <xref:System.Single> ).

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.NumberFormatInfo>
- [Niestandardowe ciągi formatujące liczby](custom-numeric-format-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Instrukcje: Uzupełnianie liczby zerami wiodącymi](how-to-pad-a-number-with-leading-zeros.md)
- [Formatowanie złożone](composite-formatting.md)
- [Przykład: Narzędzie formatowania programu .NET Core WinForms (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Przykład: Narzędzie formatowania programu .NET Core WinForms (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb)
