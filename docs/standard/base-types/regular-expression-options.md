---
title: Opcje wyrażeń regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
ms.openlocfilehash: 4cc62696cb6589151e3abc59bbea64b693e8b3a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121730"
---
# <a name="regular-expression-options"></a>Opcje wyrażeń regularnych

<a name="Top"></a>Domyślnie porównanie ciągu wejściowego z dowolnymi znakami literału we wzorcu wyrażenia regularnego uwzględnia wielkość liter, biały znak w wzorcu wyrażenia regularnego jest interpretowany jako literał znaków białych i przechwytuje grupy w wyrażeniu regularnym są nazywane niejawnie, a także jawnie. Można modyfikować te i kilka innych aspektów domyślnego zachowania wyrażeń regularnych, określając opcje wyrażenia regularnego. Te opcje, które są wymienione w poniższej tabeli, mogą być ujęte wewnętrznie jako część wzorca wyrażenia regularnego lub mogą być dostarczone do konstruktora klasy <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> lub statycznej metody dopasowania do wzorca jako <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wartość wyliczenia.

|RegexOptions element członkowski|Znak wbudowany|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Niedostępne|Użyj zachowania domyślnego. Aby uzyskać więcej informacji, zobacz [Opcje domyślne](#Default).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Używa dopasowywania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz [Dopasowanie bez uwzględniania wielkości](#Case)liter.|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Użyj trybu wielowierszowego, gdzie `^` i `$` pasują do początku i końca każdego wiersza (zamiast początku i końca ciągu wejściowego). Aby uzyskać więcej informacji, zobacz [tryb wielowierszowy](#Multiline).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Użyj trybu jednowierszowego, gdzie kropka (.) dopasowuje każdy znak (zamiast każdego znaku z wyjątkiem `\n`). Aby uzyskać więcej informacji, zobacz [trybie Singleline Mode](#Singleline).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nie przechwytuje nienazwanych grup. Jedyne prawidłowe przechwycenia to jawnie nazwane lub numerowane grupy formularza `(?<`*nazwa*`>` *podwyrażeniem*`)`. Aby uzyskać więcej informacji, zobacz [tylko jawne przechwycenia](#Explicit).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Niedostępne|Kompiluj wyrażenie regularne do zestawu. Aby uzyskać więcej informacji, zobacz [skompilowane wyrażenia regularne](#Compiled).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Wyklucz niezmieniony znak ze wzorca i Włącz Komentarze po znaku numeru (`#`). Aby uzyskać więcej informacji, zobacz [Ignorowanie białych znaków](#Whitespace).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Niedostępne|Zmień kierunek wyszukiwania. Wyszukiwanie przechodzi od prawej do lewej zamiast od lewej do prawej. Aby uzyskać więcej informacji, zobacz [tryb od prawej do lewej](#RightToLeft).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Niedostępne|Włącz zachowanie zgodne ze standardem ECMAScript dla wyrażenia. Aby uzyskać więcej informacji, zobacz [zachowanie dopasowania języka ECMAScript](#ECMAScript).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Niedostępne|Ignoruj różnice kulturowe w języku. Aby uzyskać więcej informacji, zobacz [porównanie przy użyciu niezmiennej kultury](#Invariant).|

## <a name="specifying-the-options"></a>Określanie opcji

Możesz określić opcje dla wyrażeń regularnych na jeden z trzech sposobów:

- W parametrze `options` konstruktora klasy <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> lub statycznej (`Shared` w Visual Basic) metody dopasowania do wzorca, takiej jak <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` parametr jest bitową lub kombinacją <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wartości wyliczeniowych.

  Gdy opcje są dostarczane do wystąpienia <xref:System.Text.RegularExpressions.Regex> przy użyciu parametru `options` konstruktora klasy, opcje są przypisywane do właściwości <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>. Jednak Właściwość <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> nie odzwierciedla opcji wbudowanych we wzorcu wyrażenia regularnego.

  Poniższy przykład stanowi ilustrację. Używa `options` parametru metody <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>, aby włączyć Dopasowywanie bez uwzględniania wielkości liter i ignorować biały znak w przypadku identyfikowania słów zaczynających się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Stosując opcje wbudowane we wzorcu wyrażenia regularnego z składnią `(?imnsx-imnsx)`. Opcja ma zastosowanie do wzorca od punktu, w którym opcja jest zdefiniowana do końca wzorca lub do punktu, w którym opcja jest niezdefiniowana przez inną opcję wbudowaną. Należy zauważyć, że właściwość <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wystąpienia <xref:System.Text.RegularExpressions.Regex> nie odzwierciedla tych wbudowanych opcji. Aby uzyskać więcej informacji, zobacz temat [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) .

  Poniższy przykład stanowi ilustrację. Używa opcji wbudowanych, aby włączyć Dopasowywanie bez uwzględniania wielkości liter i ignorować biały znak w przypadku identyfikowania wyrazów zaczynających się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Stosując opcje wbudowane w określonej konstrukcji grupowania we wzorcu wyrażenia regularnego z składnią `(?imnsx-imnsx:`*podwyrażeniem*`)`. Nie pisz przed zestawem opcji ustawia włączony; znak minus przed zestawem opcji powoduje wyłączenie zestawu. (`?` jest stałą częścią składni konstrukcji języka, która jest wymagana, czy opcje są włączone, czy wyłączone). Ta opcja ma zastosowanie tylko do tej grupy. Aby uzyskać więcej informacji, zobacz [grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  Poniższy przykład stanowi ilustrację. Używa wbudowanych opcji w konstrukcji grupującej, aby umożliwić Dopasowywanie bez uwzględniania wielkości liter i ignorować biały znak w przypadku identyfikowania wyrazów rozpoczynających się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Jeśli opcje są określone w tekście, znak minusa (`-`) przed opcją lub zestaw opcji wyłącza te opcje. Na przykład, konstrukcja wbudowana `(?ix-ms)` włącza opcje <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> i wyłącza opcje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. Wszystkie opcje wyrażenia regularnego są domyślnie wyłączone.

> [!NOTE]
> Jeśli opcje wyrażenia regularnego określone w parametrze `options` konstruktora lub wywołania metody powodują konflikt z opcjami określonymi wewnętrznie we wzorcu wyrażenia regularnego, są używane wbudowane opcje.

Następujące pięć opcji wyrażenia regularnego można ustawić przy użyciu parametru options i inline:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Następujące pięć opcji wyrażenia regularnego można ustawić przy użyciu parametru `options`, ale nie można ustawić go w tekście:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Określanie opcji

Można określić, które opcje zostały dostarczone do obiektu <xref:System.Text.RegularExpressions.Regex> podczas tworzenia wystąpienia, pobierając wartość właściwości <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> tylko do odczytu. Ta właściwość jest szczególnie przydatna do określania opcji, które są zdefiniowane dla skompilowanego wyrażenia regularnego utworzonego przez metodę <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>.

Aby przetestować obecność dowolnej opcji z wyjątkiem <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, wykonaj operację i z wartością właściwości <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> i wartość <xref:System.Text.RegularExpressions.RegexOptions>, w której interesują Cię zainteresowania. Następnie należy sprawdzić, czy wynik jest równy tej wartości <xref:System.Text.RegularExpressions.RegexOptions>. Poniższy przykład sprawdza, czy opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> została ustawiona.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Aby przetestować <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, ustal, czy wartość właściwości <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> jest równa <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

W poniższych sekcjach wymieniono opcje obsługiwane przez wyrażenie regularne w programie .NET.

<a name="Default"></a>

## <a name="default-options"></a>Opcje domyślne

Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> wskazuje, że nie określono żadnych opcji, a aparat wyrażeń regularnych używa swojego zachowania domyślnego. Uwzględnione są następujące elementy:

- Wzorzec jest interpretowany jako kanoniczny, a nie wyrażenie regularne języka ECMAScript.

- Wzorzec wyrażenia regularnego jest dopasowywany w ciągu wejściowym od lewej do prawej.

- W porównaniach rozróżniana jest wielkość liter.

- Elementy języka `^` i `$` pasują do początku i końca ciągu wejściowego.

- Element języka `.` pasuje do każdego znaku z wyjątkiem `\n`.

- Wszystkie białe znaki we wzorcu wyrażenia regularnego są interpretowane jako znak spacji literału.

- Konwencje bieżącej kultury są używane podczas porównywania wzorców z ciągiem wejściowym.

- Grupy przechwytywania we wzorcu wyrażenia regularnego są niejawne i jawne.

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> nie ma odpowiedników wbudowanych. Gdy opcje wyrażenia regularnego są stosowane w tekście, zachowanie domyślne jest przywracane w zależności od opcji, poprzez wyłączenie określonej opcji. Na przykład `(?i)` włącza porównanie bez uwzględniania wielkości liter, a `(?-i)` przywraca domyślne porównanie z uwzględnieniem wielkości liter.

Ponieważ opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> reprezentuje domyślne zachowanie aparatu wyrażeń regularnych, jest rzadko jawnie określona w wywołaniu metody. Zamiast tego wywołano Konstruktor lub statyczną metodę dopasowania do wzorca bez parametru `options`.

[Powrót do początku](#Top)

<a name="Case"></a>

## <a name="case-insensitive-matching"></a>Dopasowywanie bez uwzględniania wielkości liter

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>, lub opcja wbudowana `i`, zapewnia Dopasowywanie bez uwzględniania wielkości liter. Domyślnie używane są konwencje wielkości liter bieżącej kultury.

W poniższym przykładzie zdefiniowano wzorzec wyrażenia regularnego, `\bthe\w*\b`, który dopasowuje wszystkie wyrazy rozpoczynające się od "a". Ponieważ pierwsze wywołanie metody <xref:System.Text.RegularExpressions.Regex.Match%2A> używa domyślnego porównania uwzględniającego wielkość liter, dane wyjściowe wskazują, że ciąg "" ", który rozpoczyna zdanie, nie jest dopasowany. Jest dopasowywany, gdy metoda <xref:System.Text.RegularExpressions.Regex.Match%2A> jest wywoływana z opcjami ustawionymi na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Poniższy przykład modyfikuje wzorzec wyrażenia regularnego z poprzedniego przykładu, aby użyć opcji wbudowanych zamiast parametru `options`, aby zapewnić porównanie bez uwzględniania wielkości liter. Pierwszy wzorzec definiuje opcję nieuwzględniającą wielkości liter w konstrukcji grupującej, która ma zastosowanie tylko do litery "t" w ciągu "The". Ponieważ konstrukcja opcji występuje na początku wzorca, drugi wzorzec stosuje opcję bez uwzględniania wielkości liter do całego wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

[Powrót do początku](#Top)

<a name="Multiline"></a>

## <a name="multiline-mode"></a>Tryb wielowierszowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> lub opcja wbudowana `m` umożliwia aparatowi wyrażeń regularnych obsługę ciągu wejściowego, który składa się z wielu wierszy. Zmienia interpretację `^` i `$` elementów języka, tak aby pasowały do początku i końca wiersza, zamiast początku i końca ciągu wejściowego.

Domyślnie `$` dopasowuje tylko koniec ciągu wejściowego. Jeśli określisz opcję <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, dopasowuje ona znak nowego wiersza (`\n`) lub koniec ciągu wejściowego. Nie jest jednak zgodna z kombinacją znaku powrotu karetki/wysuwu wiersza. Aby pomyślnie dopasować je, użyj podwyrażenia `\r?$` zamiast tylko `$`.

W poniższym przykładzie są wyodrębniane i dające się i są dodawane do kolekcji <xref:System.Collections.Generic.SortedList%602>, która sortuje je w kolejności malejącej. Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A> jest wywoływana dwukrotnie. W pierwszym wywołaniu metody wyrażenie regularne jest `^(\w+)\s(\d+)$` i żadne opcje nie są ustawione. Jak pokazuje dane wyjściowe, ponieważ aparat wyrażeń regularnych nie może dopasować wzorca wejściowego do początku i końca ciągu wejściowego, nie znaleziono żadnych dopasowań. W drugim wywołaniu metody wyrażenie regularne jest zmieniane na `^(\w+)\s(\d+)\r?$`, a opcje są ustawione na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Jak pokazuje dane wyjściowe, nazwy i oceny zostaną pomyślnie dopasowane, a wyniki są wyświetlane w kolejności malejącej.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

`^(\w+)\s(\d+)\r*$` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.

|Wzorzec|Opis|
|-------------|-----------------|
|`^`|Zacznij od początku wiersza.|
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|
|`\s`|Dopasowuje znak odstępu.|
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to druga grupa przechwytywania.|
|`\r?`|Dopasowanie do zera lub jednego znaku powrotu karetki.|
|`$`|Koniec na końcu wiersza.|

Poniższy przykład jest równoważny poprzedniemu, z tą różnicą, że używa opcji wbudowanej `(?m)`, aby ustawić opcję wiele wierszy.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

[Powrót do początku](#Top)

<a name="Singleline"></a>

## <a name="single-line-mode"></a>Tryb jednowierszowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> lub opcja wbudowana `s` powoduje, że aparat wyrażeń regularnych traktuje ciąg wejściowy tak, jakby zawiera pojedynczy wiersz. Robi to poprzez zmianę zachowania elementu języka (`.`), tak aby pasował do każdego znaku, zamiast dopasowywania każdego znaku z wyjątkiem znaku nowego wiersza `\n` lub \u000A.

Poniższy przykład ilustruje, jak zachowanie `.` elementu języka w przypadku użycia opcji <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. Wyrażenie regularne `^.+` rozpoczyna się na początku ciągu i dopasowuje każdy znak. Domyślnie dopasowanie kończy się na końcu pierwszego wiersza; wzorzec wyrażenia regularnego dopasowuje znak powrotu karetki, `\r` lub \u000D, ale nie jest zgodny z `\n`. Ponieważ opcja <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> interpretuje cały ciąg wejściowy jako pojedynczy wiersz, dopasowuje każdy znak w ciągu wejściowym, w tym `\n`.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Poniższy przykład jest równoważny poprzedniemu, z tą różnicą, że używa opcji wbudowanej `(?s)` do włączenia trybu jednowierszowego.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

[Powrót do początku](#Top)

<a name="Explicit"></a>

## <a name="explicit-captures-only"></a>Tylko jawne przechwycenia

Domyślnie grupy przechwytywania są definiowane przy użyciu nawiasów we wzorcu wyrażenia regularnego. Do nazwanych grup są przypisywane nazwy lub liczby przez `(?<``>`*podwyrażeniem*`)`, podczas gdy *grupy bez nazwy* są dostępne dla indeksu. W obiekcie <xref:System.Text.RegularExpressions.GroupCollection> nienazwane grupy poprzedzają nazwane grupy.

Konstrukcje grupujące są często używane tylko do zastosowania kwantyfikatorów do wielu elementów języka, a przechwycone podciągi nie są istotne. Na przykład, jeśli następujące wyrażenie regularne:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

jest przeznaczony tylko do wyodrębniania zdań kończących się kropką, wykrzyknikiem lub znakiem zapytania z dokumentu, tylko zdanie wyniku (które jest reprezentowane przez obiekt <xref:System.Text.RegularExpressions.Match>) jest przedmiotem zainteresowania. Poszczególne wyrazy w kolekcji nie są.

Grupy przechwytywania, które nie są następnie używane, mogą być kosztowne, ponieważ aparat wyrażeń regularnych musi wypełnić zarówno <xref:System.Text.RegularExpressions.GroupCollection> jak i <xref:System.Text.RegularExpressions.CaptureCollection> obiekty kolekcji. Alternatywnie możesz użyć opcji <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> lub opcji wbudowanej `n`, aby określić, że jedyne prawidłowe przechwycenia są jawnymi nazwami lub numerowanymi grupami, które są oznaczone *nazwą* `(?<``>` *podwyrażeniem* @no__t_6 Konstruuj.

Poniższy przykład wyświetla informacje o dopasowaniach zwracanych przez `\b\(?((\w+),?\s?)+[\.!?]\)?` wzorca wyrażenia regularnego, gdy metoda <xref:System.Text.RegularExpressions.Regex.Match%2A> jest wywoływana z i bez opcji <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>. Ponieważ dane wyjściowe z pierwszego wywołania metody są wyświetlane, aparat wyrażeń regularnych wypełnia <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> obiekty kolekcji z informacjami o przechwyconych podciągach. Ponieważ druga metoda jest wywoływana z `options` ustawioną na <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nie przechwytują informacji o grupach.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

`\b\(?((?>\w+),?\s?)+[\.!?]\)?` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.

|Wzorzec|Opis|
|-------------|-----------------|
|`\b`|Zacznij od granicy słowa.|
|`\(?`|Dopasowanie do zera lub jednego wystąpienia nawiasu otwierającego ("(").|
|`(?>\w+),?`|Dopasowuje co najmniej jeden znak słowa, po którym następuje zero lub jeden przecinek. Nie nawrotu podczas dopasowywania znaków słowa.|
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|
|`((\w+),?\s?)+`|Dopasowuje kombinację jednego lub więcej znaków wyrazu, zera lub jednego przecinka oraz zero lub jeden znak odstępu jeden lub więcej razy.|
|`[\.!?]\)?`|Dopasowuje dowolny z trzech symboli interpunkcyjnych, po których następuje zero lub jedno nawias zamykający (")").|

Można również użyć `(?n)` wbudowanego elementu, aby pominąć Automatyczne przechwytywanie. Poniższy przykład modyfikuje poprzedni wzorzec wyrażenia regularnego, aby użyć `(?n)` wbudowanego elementu zamiast opcji <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Na koniec można użyć wbudowanego elementu grupy `(?n:)`, aby pominąć Automatyczne przechwytywanie dla poszczególnych grup. Poniższy przykład modyfikuje poprzedni wzorzec, aby pominąć nienazwane przechwycenia w grupie zewnętrznej, `((?>\w+),?\s?)`. Należy zauważyć, że spowoduje to pominięcie nienazwanych przechwyconych w grupie wewnętrznej.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

[Powrót do początku](#Top)

<a name="Compiled"></a>

## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne

Domyślnie wyrażenia regularne w programie .NET są interpretowane. Po utworzeniu wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> lub wywołaniu metody statycznej <xref:System.Text.RegularExpressions.Regex>, wzorzec wyrażenia regularnego jest analizowany w zestawie niestandardowych kodów operacji, a interpreter używa tych kodów opcode do uruchomienia wyrażenia regularnego. Obejmuje to kompromis: koszt inicjowania aparatu wyrażeń regularnych jest zminimalizowany na koszt wydajności w czasie wykonywania.

Można używać skompilowanych wyrażeń regularnych zamiast interpretowanych za pomocą opcji <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>. W tym przypadku, gdy wzorzec jest przenoszona do aparatu wyrażeń regularnych, jest analizowany w zestaw kodów operacji, a następnie konwertowany do języka pośredniego firmy Microsoft (MSIL), który można przesłać bezpośrednio do środowiska uruchomieniowego języka wspólnego. Skompilowane wyrażenia regularne maksymalizują wydajność w czasie wykonywania kosztem czasu inicjacji.

> [!NOTE]
> Wyrażenie regularne może być kompilowane tylko poprzez dostarczenie wartości <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> do `options` parametr konstruktora klasy <xref:System.Text.RegularExpressions.Regex> lub statycznej metody dopasowania do wzorca. Nie jest ona dostępna jako opcja wbudowana.

Skompilowane wyrażenia regularne można używać w wywołaniach zarówno w wyrażeniach statycznych, jak i wystąpieniach regularnych. W statycznych wyrażeniach regularnych opcja <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> jest przenoszona do parametru `options` metody dopasowania do wzorca wyrażenia regularnego. W wyrażeniach regularnych wystąpienia jest ona przenoszona do `options` parametru konstruktora klasy <xref:System.Text.RegularExpressions.Regex>. W obu przypadkach powstaje zwiększona wydajność.

Jednak ten wzrost wydajności występuje tylko w następujących warunkach:

- Obiekt <xref:System.Text.RegularExpressions.Regex>, który reprezentuje określone wyrażenie regularne jest używany w wielu wywołaniach metod dopasowania do wzorca wyrażenia regularnego.

- Obiekt <xref:System.Text.RegularExpressions.Regex> nie może wykraczać poza zakres, więc można go ponownie użyć.

- Statyczne wyrażenie regularne jest używane w wielu wywołaniach metod dopasowania do wzorca wyrażenia regularnego. (Zwiększenie wydajności jest możliwe, ponieważ wyrażenia regularne używane w wywołaniach metod statycznych są buforowane przez aparat wyrażeń regularnych).

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> nie jest związana z metodą <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, która tworzy zestaw specjalnego przeznaczenia zawierający wstępnie skompilowane wyrażenia regularne.

[Powrót do początku](#Top)

<a name="Whitespace"></a>

## <a name="ignore-white-space"></a>Ignoruj odstępy

Domyślnie biały znak we wzorcu wyrażenia regularnego jest znaczący; wymusza, aby aparat wyrażeń regularnych pasował do znaku odstępu w ciągu wejściowym. W związku z tym wyrażenie regularne "`\b\w+\s`" i "`\b\w+`" są w przybliżeniu odpowiednikiem wyrażeń regularnych. Ponadto, gdy w wzorcu wyrażenia regularnego jest wykryty znak numeru (#), jest interpretowany jako znak literału, który ma zostać dopasowany.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> lub opcja wbudowana `x` zmienia to zachowanie domyślne w następujący sposób:

- Niezmieniony biały znak we wzorcu wyrażenia regularnego jest ignorowany. Aby była częścią wzorca wyrażenia regularnego, znaki białych znaków muszą być wyprowadzane (na przykład jako `\s` lub "`\`").

- Znak numeru (#) jest interpretowany jako początek komentarza, a nie jako znak literału. Cały tekst we wzorcu wyrażenia regularnego ze znaku # na końcu ciągu jest interpretowany jako komentarz.

Jednak w następujących przypadkach znaki odstępu w wyrażeniu regularnym nie są ignorowane, nawet jeśli używana jest opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>:

- Biały znak w klasie znaków jest zawsze interpretowany dosłownie. Na przykład wzorzec wyrażenia regularnego `[ .,;:]` dopasowuje dowolny pojedynczy znak odstępu, kropkę, przecinek, średnik lub dwukropek.

- Biały znak nie jest dozwolony w nawiasie klamrowym, na przykład `{`*n*`}`, `{`*n*`,}`i `{`*n*`,`*m*`}`. Na przykład wzorzec wyrażenia regularnego `\d{1, 3}` nie jest zgodny z żadną sekwencją cyfr z jednej do trzech cyfr, ponieważ zawiera znak odstępu.

- Biały znak jest niedozwolony w sekwencji znaków, która wprowadza element języka. Na przykład:

  - Element języka `(?:`*podwyrażeniem*`)` reprezentuje grupę nieprzechwytującą, a część `(?:` elementu nie może mieć osadzonych spacji. `(? :`*wyrażenia* podrzędnego wzorca`)` zgłasza <xref:System.ArgumentException> w czasie wykonywania, ponieważ aparat wyrażeń regularnych nie może przeanalizować wzorca, a wzorzec `( ?:`*Podwyrażenie*`)` nie pasuje do *wyrażenia*podrzędnego.

  - Element języka `\p{`*name*`}`, który reprezentuje kategorię Unicode lub nazwany blok, nie może zawierać osadzonych miejsc w `\p{` części elementu. Jeśli zostanie uwzględniony biały znak, element zgłasza <xref:System.ArgumentException> w czasie wykonywania.

Włączenie tej opcji pomaga uprościć wyrażenia regularne, które często trudno jest analizować i zrozumieć. Zwiększa czytelność i umożliwia dokumentowanie wyrażenia regularnego.

W poniższym przykładzie zdefiniowano następujący wzorzec wyrażenia regularnego:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Ten wzorzec jest podobny do wzorca zdefiniowanego w sekcji [tylko przechwycenia jawne](#Explicit) , z tą różnicą, że używa opcji <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>, aby zignorować biały znak w deseniu.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Poniższy przykład używa opcji inline `(?x)`, aby zignorować biały znak w deseniu.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

[Powrót do początku](#Top)

<a name="RightToLeft"></a>

## <a name="right-to-left-mode"></a>Tryb od prawej do lewej

Domyślnie aparat wyrażeń regularnych przeszukuje od lewej do prawej. Kierunek wyszukiwania można odwrócić przy użyciu opcji <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>. Wyszukiwanie rozpocznie się automatycznie od ostatniej pozycji znaku ciągu. Dla metod dopasowania do wzorca, które zawierają parametr pozycji początkowej, takich jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, pozycja początkowa jest indeksem pozycji znaku po prawej stronie, w którym rozpocznie się wyszukiwanie.

> [!NOTE]
> Tryb wzorca od prawej do lewej jest dostępny tylko poprzez dostarczenie wartości <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> do `options` parametr konstruktora klasy <xref:System.Text.RegularExpressions.Regex> lub statycznej metody dopasowania do wzorca. Nie jest ona dostępna jako opcja wbudowana.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> zmienia tylko kierunek wyszukiwania; wzorzec wyrażenia regularnego nie jest interpretowany od prawej do lewej. Na przykład wyrażenie regularne `\bb\w+\s` dopasowuje słowa zaczynające się od litery "b", po którym następuje znak odstępu. W poniższym przykładzie ciąg wejściowy składa się z trzech słów, które zawierają jeden lub więcej znaków "b". Pierwsze słowo rozpoczyna się od litery "b", drugi kończą się znakiem "b", a trzeci zawiera dwa znaki "b" w środku słowa. Jak pokazano na przykładzie, tylko pierwszy wyraz pasuje do wzorca wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Należy również zauważyć, że potwierdzenie naprzód (`(?=`*Podwyrażenie*`)` element języka) i potwierdzenie asercja wsteczna (`(?<=`*Podwyrażenie*`)`) nie zmieniają kierunku. Potwierdzenia naprzód są przeszukiwane w prawo; potwierdzenia asercja wsteczna wyglądają po lewej stronie. Na przykład wyrażenie regularne `(?<=\d{1,2}\s)\w+,?\s\d{4}` używa potwierdzenia asercja wsteczna, aby przetestować datę poprzedzającą nazwę miesiąca. Następnie wyrażenie regularne dopasowuje miesiąc i rok. Aby uzyskać informacje na temat potwierdzeń i asercja wsteczna, zobacz [Grouping konstrukcjes](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.

|Wzorzec|Opis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Początek dopasowania musi być poprzedzony jedną lub dwiema cyframi dziesiętnymi, po których występuje spacja.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|`,?`|Dopasowanie do zera lub jednego przecinka.|
|`\s`|Dopasowuje znak odstępu.|
|`\d{4}`|Dopasowuje cztery cyfry dziesiętne.|

[Powrót do początku](#Top)

<a name="ECMAScript"></a>

## <a name="ecmascript-matching-behavior"></a>Zachowanie dopasowania ECMAScript

Domyślnie aparat wyrażeń regularnych używa zachowania kanonicznego, gdy dopasowuje wzorzec wyrażenia regularnego do tekstu wejściowego. Można jednak nakazać aparatowi wyrażeń regularnych używanie zachowań dopasowania ECMAScript, określając opcję <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>.

> [!NOTE]
> Zachowanie zgodne ze standardem ECMAScript jest dostępne tylko poprzez dostarczenie wartości <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> do `options` parametr konstruktora klasy <xref:System.Text.RegularExpressions.Regex> lub statycznej metody dopasowania do wzorca. Nie jest ona dostępna jako opcja wbudowana.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> może być łączona tylko z opcjami <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Użycie jakichkolwiek innych opcji w wyrażeniu regularnym powoduje <xref:System.ArgumentOutOfRangeException>.

Zachowanie ECMAScript i kanoniczne wyrażenia regularne różnią się w trzech obszarach: Składnia klasy znaków, grupy przechwytywania do odwołujących się do siebie oraz interpretacja ósemkowa i wsteczna.

- Składnia klasy znaków. Ze względu na to, że kanoniczne wyrażenia regularne obsługują standard Unicode, natomiast klasy znaków w ECMAScript mają bardziej ograniczoną składnię, a niektóre elementy języka klasy znaku mają inne znaczenie. Na przykład ECMAScript nie obsługuje elementów języka, takich jak kategoria Unicode lub elementy bloku `\p` i `\P`. Podobnie, element `\w`, który pasuje do znaku słowa, jest odpowiednikiem klasy znaku `[a-zA-Z_0-9]` podczas korzystania z języka ECMAScript i `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` podczas korzystania z zachowań kanonicznych. Aby uzyskać więcej informacji, zobacz [klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Poniższy przykład ilustruje różnicę między kanonicznym i ECMAScript dopasowania do wzorca. Definiuje wyrażenie regularne, `\b(\w+\s*)+`, które pasuje do wyrazów, po których następuje znak spacji. Dane wejściowe składają się z dwóch ciągów, jeden, który używa zestawu znaków łacińskich, a drugi, który używa zestawu znaków cyrylicy. Ponieważ dane wyjściowe są wyświetlane, wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>, która używa dopasowania ECMAScript, nie jest zgodne z wyrazami cyrylicy, podczas gdy wywołanie metody używające dopasowywania kanonicznego jest zgodne z tymi wyrazami.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Odwołujące się do siebie grupy przechwytywania. Klasa przechwytywania wyrażenia regularnego z odwołaniem wstecznym musi zostać zaktualizowana przy użyciu każdej iteracji przechwytywania. Jak pokazano na poniższym przykładzie, ta funkcja włącza wyrażenie regularne `((a+)(\1) ?)+`, aby dopasować ciąg wejściowy "AA AAAA aaaaaa" podczas korzystania z języka ECMAScript, ale nie w przypadku używania dopasowania kanonicznego.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.

  |Wzorzec|Opis|
  |-------------|-----------------|
  |(a +)|Dopasowuje znak "a" jeden lub więcej razy. Jest to druga grupa przechwytywania.|
  |(\ 1)|Dopasowuje podciąg przechwytywany przez pierwszą grupę przechwytywania. Jest to trzecia grupa przechwytywania.|
  |?|Dopasowuje zero lub jeden znak spacji.|
  |((a +) (\ 1)?) +|Dopasowuje wzorzec składający się z co najmniej jednego znaku "a", po którym następuje ciąg, który pasuje do pierwszej grupy przechwytywania, po którym następuje zero lub jeden znak spacji. Jest to pierwsza grupa przechwytywania.|

- Rozpoznawanie niejasności między ósemkowymi znakami ucieczki i odwołaniami wstecznymi. Poniższa tabela podsumowuje różnice w liczbie ósemkowej i interpretacji odwołania wstecznego przez kanoniczne i ECMAScript wyrażenia regularne.

  |Wyrażenie regularne|Zachowanie kanoniczne|Zachowanie języka ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0` następują cyfry ósemkowe od 0 do 2|Interpretuj jako ósemkowy. Na przykład `\044` jest zawsze interpretowana jako wartość ósemkowa i oznacza "$".|Takie samo zachowanie.|
  |`\` następuje cyfra od 1 do 9, a następnie nie ma dodatkowych cyfr dziesiętnych,|Interpretuj jako odwołanie wsteczne. Na przykład `\9` zawsze oznacza odwołanie wsteczne 9, nawet jeśli dziewiąta grupa przechwytywania nie istnieje. Jeśli grupa przechwytywania nie istnieje, Analizator wyrażeń regularnych zgłosi <xref:System.ArgumentException>.|Jeśli istnieje pojedyncza cyfra dziesiętna grupa przechwytywania, odwołuje się do tej cyfry. W przeciwnym razie interpretuje wartość jako literał.|
  |`\` następuje cyfra od 1 do 9, a następnie dodatkowe cyfry dziesiętne|Interpretuj cyfry jako wartość dziesiętną. Jeśli ta grupa przechwytywania istnieje, interpretuj wyrażenie jako odwołanie wsteczne.<br /><br /> W przeciwnym razie Interpretuj wiodące cyfry ósemkowe do ósemkowego 377; oznacza to, że należy wziąć pod uwagę tylko 8 bitów wartości. Interpretuj pozostałe cyfry jako literały. Na przykład w wyrażeniu `\3000`, jeśli grupa przechwytywania 300 istnieje, interpretuj jako odwołanie wsteczne 300; Jeśli grupa przechwytywania 300 nie istnieje, interpretuj jako ósemkową 300, a następnie 0.|Interpretuj jako odwołanie wsteczne, konwertując dowolną liczbę cyfr na wartość dziesiętną, która może odwoływać się do przechwytywania. Jeśli nie można przekonwertować cyfr, interpretuj jako ósemkowy przy użyciu wiodących cyfr ósemkowych do ósemkowego 377; Interpretuj pozostałe cyfry jako literały.|

[Powrót do początku](#Top)

<a name="Invariant"></a>

## <a name="comparison-using-the-invariant-culture"></a>Porównanie przy użyciu niezmiennej kultury

Domyślnie, gdy aparat wyrażeń regularnych wykonuje porównania bez uwzględniania wielkości liter, używa konwencji osłony dla bieżącej kultury, aby określić równoważne wielkie i małe litery.

Jednak takie zachowanie jest niepożądane w przypadku niektórych typów porównań, szczególnie w przypadku porównywania danych wejściowych użytkownika z nazwami zasobów systemowych, takich jak hasła, pliki lub adresy URL. Poniższy przykład ilustruje przykład scenariusza. Kod jest przeznaczony do blokowania dostępu do dowolnego zasobu, którego adres URL jest poprzedzony **File://** . Wyrażenie regularne próbuje dopasować wielkość liter do ciągu przy użyciu wyrażenia regularnego `$FILE://`. Jednakże gdy bieżącą kulturą systemu jest TR-TR (turecki-Turcja), "I" nie jest odpowiednikiem litery "i". W związku z tym wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> zwraca `false`i dostęp do pliku jest dozwolony.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat porównań ciągów, w których jest rozróżniana wielkość liter i które używają niezmiennej kultury, zobacz [najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md).

Zamiast korzystać z porównania w obecnej kulturze bez uwzględniania wielkości liter, można określić opcję <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>, aby zignorować różnice kulturowe w języku i używać konwencji niezmiennej kultury.

> [!NOTE]
> Porównanie przy użyciu niezmiennej kultury jest dostępne tylko poprzez dostarczenie wartości <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> do `options` parametr konstruktora klasy <xref:System.Text.RegularExpressions.Regex> lub statycznej metody dopasowania do wzorca. Nie jest ona dostępna jako opcja wbudowana.

Poniższy przykład jest identyczny z poprzednim przykładem, z tą różnicą, że metoda statyczna <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> jest wywoływana z opcjami, które zawierają <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Nawet jeśli bieżąca kultura jest ustawiona na turecki (Turcja), aparat wyrażeń regularnych może pomyślnie dopasować "plik" i "plik" i zablokować dostęp do zasobu pliku.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
