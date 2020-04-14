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
ms.openlocfilehash: bf352d6494a823d4f7b24eb2876d9bffa5877b2b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242780"
---
# <a name="regular-expression-options"></a>Opcje wyrażeń regularnych

Domyślnie porównanie ciągu wejściowego z dowolnymi znakami dosłownymi we wzorcu wyrażenia regularnego jest rozróżniane wielkość liter, biały znak we wzorcu wyrażenia regularnego jest interpretowany jako dosłowne znaki odstępu, a przechwytywanie grup w wyrażeniu regularnym nosi nazwę niejawnie, a także jawnie. Można zmodyfikować te i kilka innych aspektów domyślnego zachowania wyrażenia regularnego, określając opcje wyrażenia regularnego. Te opcje, które są wymienione w poniższej tabeli, mogą być zawarte w linii jako <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> część wzorca wyrażenia regularnego lub <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> mogą być dostarczane do konstruktora klasy lub statycznego wzorca dopasowania metody jako wartość wyliczenia.

|Członek reexoptions|Znak wbudowany|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Niedostępne|Użyj zachowania domyślnego. Aby uzyskać więcej informacji, zobacz [Opcje domyślne](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Używa dopasowywania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz [Dopasowanie bez uwzględniania wielkości liter](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Użyj trybu wielowierszowego, gdzie `^` i `$` dopasować początek i koniec każdego wiersza (zamiast początku i końca ciągu wejściowego). Aby uzyskać więcej informacji, zobacz [Tryb wielowierszowy](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Użyj trybu jednowierszowego, w którym kropka (.) pasuje `\n`do każdego znaku (zamiast każdego znaku z wyjątkiem ). Aby uzyskać więcej informacji, zobacz [Tryb jednowierszowy](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nie przechwytuje nienazwanych grup. Jedynymi prawidłowymi ujęciami są jawnie nazwane `(?<`lub ponumerowane grupy *podwyrażenia*`)` *nazwy* `>` formularza . Aby uzyskać więcej informacji, zobacz [Tylko jawne przechwytywanie](#explicit-captures-only).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Niedostępne|Skompilować wyrażenie regularne do zestawu. Aby uzyskać więcej informacji, zobacz [Skompilowane wyrażenia regularne](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Wyklucz nieskażone białe znaki ze wzoru i włącz`#`komentarze po znaku liczbowym ( ). Aby uzyskać więcej informacji, zobacz [Ignorowanie odstępu](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Niedostępne|Zmień kierunek wyszukiwania. Wyszukiwanie przesuwa się od prawej do lewej, a nie od lewej do prawej. Aby uzyskać więcej informacji, zobacz [Tryb od prawej do lewej](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Niedostępne|Włącz zachowanie zgodne z ecmascript dla wyrażenia. Aby uzyskać więcej informacji, zobacz [ECMAScript Matching Behavior](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Niedostępne|Ignoruj różnice kulturowe w języku. Aby uzyskać więcej informacji, zobacz [Porównanie przy użyciu kultury niezmiennej](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Określanie opcji

Opcje wyrażeń regularnych można określić na jeden z trzech sposobów:

- W `options` parametrze <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy`Shared` lub statycznej (w języku Visual <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>Basic) metody dopasowywania wzorca, takiej jak lub . Parametr `options` jest bitową kombinacją <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> or wyliczonych wartości.

  Gdy opcje są <xref:System.Text.RegularExpressions.Regex> dostarczane do `options` wystąpienia przy użyciu parametru konstruktora <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> klasy, opcje są przypisane do właściwości. Jednak <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwość nie odzwierciedla opcji wbudowanych w wzorcu wyrażenia regularnego.

  Poniższy przykład stanowi ilustrację. Używa parametru `options` <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, aby włączyć dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania słów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Stosując opcje wbudowane we wzorcu wyrażenia regularnego `(?imnsx-imnsx)`ze składnią . Opcja ma zastosowanie do wzorca od punktu, w którym opcja jest zdefiniowana na końcu szyku lub do punktu, w którym opcja jest niezdefiniowana przez inną opcję wbudowaną. Należy zauważyć, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> że <xref:System.Text.RegularExpressions.Regex> właściwość wystąpienia nie odzwierciedla tych opcji wbudowanych. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tematu.

  Poniższy przykład stanowi ilustrację. Używa opcji wbudowanych, aby włączyć dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania słów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Stosując opcje wbudowane w konstrukcji grupy w wzorcu wyrażenia regularnego `(?imnsx-imnsx:`z *podciągliwość*`)`składni . Brak znaku przed zestawem opcji włącza się zestaw; znak minus, zanim zestaw opcji wyłączy ustawienie. (`?` jest stałą częścią składni konstrukcji języka, która jest wymagana, niezależnie od tego, czy opcje są włączone, czy wyłączone.) Opcja ta dotyczy tylko tej grupy. Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  Poniższy przykład stanowi ilustrację. Używa opcji wbudowanych w konstrukcji grupowania, aby włączyć dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania wyrazów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Jeśli opcje są określone w linii, znak minus (`-`) przed opcją lub zestawem opcji wyłącza te opcje. Na przykład wbudowana `(?ix-ms)` konstrukcja włącza <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> i opcje i <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> wyłącza i opcje. Wszystkie opcje wyrażenia regularnego są domyślnie wyłączone.

> [!NOTE]
> Jeśli opcje wyrażenia regularnego `options` określone w parametrze konstruktora lub wywołania metody są w konflikcie z opcjami określonymi w ywór w wzorcu wyrażenia regularnego, używane są opcje wbudowane.

Następujące pięć opcji wyrażenia regularnego można ustawić zarówno za pomocą parametru opcji, jak i wbudowanego:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Następujące pięć opcji wyrażenia regularnego można `options` ustawić przy użyciu parametru, ale nie można ustawić w linii:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Określanie opcji

Można określić, które opcje <xref:System.Text.RegularExpressions.Regex> zostały dostarczone do obiektu, gdy został skreślony <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> przez pobranie wartości właściwości tylko do odczytu. Ta właściwość jest szczególnie przydatna do określania opcji, które są <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> zdefiniowane dla skompilowanego wyrażenia regularnego utworzonego przez metodę.

Aby przetestować obecność dowolnej <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>opcji z wyjątkiem , wykonać <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> operację AND <xref:System.Text.RegularExpressions.RegexOptions> z wartością właściwości i wartością, w której jesteś zainteresowany. Następnie sprawdź, czy wynik <xref:System.Text.RegularExpressions.RegexOptions> jest równy tej wartości. Poniższy przykład sprawdza, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> czy opcja została ustawiona.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Aby przetestować dla <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, określić, <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>czy wartość właściwości jest równa , jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

W poniższych sekcjach przedstawiono opcje obsługiwane przez wyrażenie regularne w .NET.

## <a name="default-options"></a>Opcje domyślne

Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> wskazuje, że nie określono żadnych opcji, a aparat wyrażeń regularnych używa jego domyślnego zachowania. Uwzględnione są następujące elementy:

- Wzorzec jest interpretowany jako wyrażenie regularne kanoniczne, a nie ecmascript.

- Wzorzec wyrażenia regularnego jest dopasowywane w ciągu wejściowym od lewej do prawej.

- W porównaniach rozróżniana jest wielkość liter.

- Elementy `^` `$` i język są zgodne z początkiem i końcem ciągu wejściowego.

- Element `.` języka pasuje do `\n`każdego znaku z wyjątkiem .

- Każdy biały znak we wzorcu wyrażenia regularnego jest interpretowany jako znak spacji literału.

- Konwencje bieżącej kultury są używane podczas porównywania wzorca z ciągiem wejściowym.

- Przechwytywanie grup we wzorcu wyrażeń regularnych są niejawne, a także jawne.

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> nie ma odpowiednika wbudowanego. Gdy opcje wyrażenia regularnego są stosowane w linii, domyślne zachowanie jest przywracane na zasadzie opcji według opcji, wyłączając określoną opcję. Na przykład `(?i)` włącza porównanie bez uwzględniania wielkości `(?-i)` liter i przywraca domyślne porównanie z uwzględnieniem wielkości liter.

Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> opcja reprezentuje domyślne zachowanie aparatu wyrażeń regularnych, rzadko jest jawnie określony w wywołaniu metody. Zamiast tego wywoływana jest metoda dopasowywania konstruktora lub statycznego `options` wzorca bez parametru.

## <a name="case-insensitive-matching"></a>Dopasowanie bez uwzględniania wielkości liter

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> lub opcja `i` wbudowana zapewnia dopasowanie bez uwzględniania wielkości liter. Domyślnie używane są konwencje wielkości liter bieżącej kultury.

Poniższy przykład definiuje wzorzec `\bthe\w*\b`wyrażenia regularnego, który pasuje do wszystkich wyrazów, począwszy od "the". Ponieważ pierwsze wywołanie <xref:System.Text.RegularExpressions.Regex.Match%2A> metody używa domyślnego porównania z uwzględnieniem wielkości liter, dane wyjściowe wskazują, że ciąg "The", który rozpoczyna zdanie, nie jest dopasowany. Jest onpasytowany, gdy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>jest wywoływana z opcjami ustawionymi na .

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Poniższy przykład modyfikuje wzorzec wyrażenia regularnego z poprzedniego przykładu, aby użyć opcji wbudowanych zamiast parametru, `options` aby zapewnić porównanie bez uwzględniania wielkości liter. Pierwszy wzorzec definiuje opcję bez uwzględniania wielkości liter w konstrukcji grupowania, która ma zastosowanie tylko do litery "t" w ciągu "the". Ponieważ konstruowanie opcji występuje na początku wzorca, drugi wzorzec stosuje opcję bez uwzględniania wielkości liter do całego wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Tryb wielowierszowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> lub opcja `m` wbudowana umożliwia aparatowi wyrażeń regularnych obsługę ciągu wejściowego, który składa się z wielu wierszy. Zmienia interpretację `^` elementów `$` języka i tak, aby były zgodne z początkiem i końcem wiersza, zamiast początku i końca ciągu wejściowego.

Domyślnie `$` dopasowuje tylko koniec ciągu wejściowego. Jeśli <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> określisz tę opcję, jest ona zgodna`\n`ze znakiem nowego linii ( ) lub na końcu ciągu wejściowego. Nie jest to jednak zgodne z kombinacją znaków powrotu karetki/wiersza. Aby pomyślnie je dopasować, użyj `\r?$` podwyrażenia zamiast tylko `$`.

Poniższy przykład wyodrębnia nazwy meloniki i wyniki <xref:System.Collections.Generic.SortedList%602> i dodaje je do kolekcji, która sortuje je w porządku malejącym. Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A> jest wywoływana dwa razy. W pierwszym wywołaniu metody wyrażenie `^(\w+)\s(\d+)$` regularne jest i nie są ustawione żadne opcje. Jak pokazuje dane wyjściowe, ponieważ aparat wyrażeń regularnych nie może dopasować wzorzec danych wejściowych wraz z początku i końca ciągu wejściowego, nie znaleziono żadnych dopasowań. W drugim wywołaniu metody wyrażenie regularne `^(\w+)\s(\d+)\r?$` jest zmieniane <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>na i opcje są ustawione na . Jak pokazano dane wyjściowe, nazwy i wyniki są pomyślnie dopasowane, a wyniki są wyświetlane w kolejności malejącej.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Wzorzec `^(\w+)\s(\d+)\r*$` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`^`|Rozpocznij od początku wiersza.|
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|
|`\s`|Dopasowuje znak odstępu.|
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to druga grupa przechwytywania.|
|`\r?`|Dopasuj zero lub jeden znak powrotu karetki.|
|`$`|Koniec na końcu wiersza.|

Poniższy przykład jest odpowiednikiem poprzedniego, z tą różnicą, że używa opcji `(?m)` wbudowanej do ustawiania opcji wielowierszowej.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Tryb jednowierszowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> lub opcja `s` wbudowana powoduje, że aparat wyrażeń regularnych traktuje ciąg wejściowy tak, jakby składa się z pojedynczego wiersza. Odbywa się to poprzez zmianę zachowania`.`elementu języka kropka ( ) tak, aby pasował do każdego `\n` znaku, zamiast dopasowywania każdego znaku z wyjątkiem znaku nowego linii lub \u000A.

Poniższy przykład ilustruje, `.` jak zmienia się zachowanie <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> elementu języka podczas korzystania z opcji. Wyrażenie regularne `^.+` rozpoczyna się na początku ciągu i pasuje do każdego znaku. Domyślnie dopasowanie kończy się na końcu pierwszego wiersza; wzorzec wyrażenia regularnego pasuje `\r` do znaku powrotu karetki lub \u000D, ale nie jest zgodny `\n`. Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcja interpretuje cały ciąg wejściowy jako pojedynczy wiersz, pasuje do `\n`każdego znaku w ciągu wejściowym, w tym .

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Poniższy przykład jest odpowiednikiem poprzedniego, z tą różnicą, że używa opcji `(?s)` wbudowanej, aby włączyć tryb jednowierszowy.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Tylko jawne przechwytywanie

Domyślnie grupy przechwytywania są definiowane przez użycie nawiasów we wzorcu wyrażenia regularnego. Nazwane grupy są przypisywane nazwę `(?<`lub numer przez *nazwę*`>`*subexpression* `)` opcji języka, podczas gdy nienazwane grupy są dostępne przez indeks. W <xref:System.Text.RegularExpressions.GroupCollection> obiekcie grupy bez nazwy poprzedzają nazwane grupy.

Konstrukcje grupowania są często używane tylko do stosowania kwantyfikatorów do wielu elementów języka, a przechwycone podciągi nie są interesujące. Na przykład, jeśli następujące wyrażenie regularne:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

jest przeznaczony tylko do wyodrębniania zdań, które kończą się kropką, wykrzyknikiem lub znakiem <xref:System.Text.RegularExpressions.Match> zapytania z dokumentu, interesujące jest tylko zdanie wynikowe (reprezentowane przez obiekt). Poszczególne słowa w kolekcji nie są.

Przechwytywanie grup, które nie są następnie używane może być kosztowne, <xref:System.Text.RegularExpressions.GroupCollection> ponieważ <xref:System.Text.RegularExpressions.CaptureCollection> aparat wyrażeń regularnych musi wypełniać obiekty i kolekcji. Alternatywnie można użyć <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji lub opcji `n` wbudowanej, aby określić, że tylko prawidłowe przechwytuje są jawnie nazwane lub ponumerowane grupy, które są wyznaczone `(?<`przez konstrukcję *subexpression* `)` *nazwy.* `>`

Poniższy przykład wyświetla informacje o `\b\(?((\w+),?\s?)+[\.!?]\)?` dopasowania zwracanych <xref:System.Text.RegularExpressions.Regex.Match%2A> przez wzorzec wyrażenia <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> regularnego, gdy metoda jest wywoływana z i bez opcji. Jak pokazano dane wyjściowe z pierwszego wywołania metody, <xref:System.Text.RegularExpressions.GroupCollection> aparat <xref:System.Text.RegularExpressions.CaptureCollection> wyrażeń regularnych w pełni wypełnia obiekty i kolekcji informacjami o przechwyconych podciągach. Ponieważ druga metoda jest `options` wywoływana z set to <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nie przechwytuje informacji o grupach.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Wzorzec`\b\(?((?>\w+),?\s?)+[\.!?]\)?` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Zacznij od granicy słowa.|
|`\(?`|Dopasuj zero lub jedno wystąpienie nawiasu otwierającego ("(").|
|`(?>\w+),?`|Dopasuj jeden lub więcej znaków wyrazowych, po których następuje zero lub jeden przecinek. Nie cofaj się podczas dopasowywania znaków wyrazowych.|
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|
|`((\w+),?\s?)+`|Dopasuj kombinację jednego lub więcej znaków wyrazowych, zero lub jeden przecinek i zero lub jeden znak odstępu jeden lub więcej razy.|
|`[\.!?]\)?`|Dopasuj dowolny z trzech symboli interpunkcyjnych, po których następuje zero lub jeden nawias zamykający (")").|

Można również użyć `(?n)` elementu wbudowanego, aby pominąć automatyczne przechwytywanie. Poniższy przykład modyfikuje poprzedni wzorzec wyrażenia regularnego, aby użyć elementu `(?n)` wbudowanego zamiast <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Na koniec można użyć elementu `(?n:)` grupy wbudowanej, aby pominąć automatyczne przechwytywanie na podstawie grupy po grupie. Poniższy przykład modyfikuje poprzedni wzorzec, aby pominąć nienazwane przechwytuje w grupie zewnętrznej, `((?>\w+),?\s?)`. Należy zauważyć, że pomija to nienazwane przechwytuje w grupie wewnętrznej, jak również.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne

Domyślnie interpretowane są wyrażenia regularne w domenie .NET. Gdy <xref:System.Text.RegularExpressions.Regex> obiekt jest wystąpienia lub metoda <xref:System.Text.RegularExpressions.Regex> statyczna jest wywoływana, wzorzec wyrażenia regularnego jest analizowany w zestawie niestandardowych kodów operacyjnych, a interpreter używa tych kodów opcode do uruchomienia wyrażenia regularnego. Wiąże się to z kompromisem: koszt inicjowania aparatu wyrażeń regularnych jest zminimalizowany kosztem wydajności w czasie wykonywania.

Za pomocą <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> tej opcji można użyć skompilowanych zamiast interpretowanych wyrażeń regularnych. W takim przypadku, gdy wzorzec jest przekazywany do aparatu wyrażeń regularnych, jest analizowany w zestawie kodów operacyjnych, a następnie konwertowany na język pośredni firmy Microsoft (MSIL), który może być przekazywany bezpośrednio do środowiska wykonawczego języka wspólnego. Skompilowane wyrażenia regularne maksymalizują wydajność w czasie wykonywania kosztem czasu inicjowania.

> [!NOTE]
> Wyrażenie regularne można skompilować tylko <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> przez `options` podanie wartości <xref:System.Text.RegularExpressions.Regex> do parametru konstruktora klasy lub metody dopasowywania wzorców statycznych. Nie jest dostępna jako opcja wbudowana.

Można użyć skompilowanych wyrażeń regularnych w wywołaniach zarówno statycznych, jak i wystąpień regularnych. W statycznych wyrażeniach <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> regularnych opcja jest `options` przekazywana do parametru metody dopasowywania wzorca wyrażenia regularnego. W przypadku wyrażeń regularnych jest `options` przekazywana do parametru konstruktora <xref:System.Text.RegularExpressions.Regex> klasy. W obu przypadkach powoduje zwiększoną wydajność.

Jednak ta poprawa wydajności występuje tylko w następujących warunkach:

- Obiekt, <xref:System.Text.RegularExpressions.Regex> który reprezentuje określone wyrażenie regularne jest używany w wielu wywołań metod dopasowywania wzorców wyrażeń regularnych.

- Obiekt <xref:System.Text.RegularExpressions.Regex> nie może wyjść poza zakres, więc może być ponownie ponownie.

- Statyczne wyrażenie regularne jest używane w wielu wywołaniach metod dopasowywania wzorców wyrażeń regularnych. (Poprawa wydajności jest możliwe, ponieważ wyrażenia regularne używane w wywołaniach metody statycznej są buforowane przez aparat wyrażeń regularnych.)

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> nie jest <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> związana z metodą, która tworzy zestaw specjalnego przeznaczenia, który zawiera wstępnie zdefiniowane skompilowane wyrażenia regularne.

## <a name="ignore-white-space"></a>Ignoruj biały spację

Domyślnie biały znak we wzorcu wyrażenia regularnego jest znaczący; wymusza aparat wyrażeń regularnych, aby dopasować znak odstępu w ciągu wejściowym. Z tego powodu wyrażenie`\b\w+\s`regularne "`\b\w+` " i " " są mniej więcej równoważnymi wyrażeniami regularnymi. Ponadto po napotkaniu znaku liczbowego (#) we wzorcu wyrażenia regularnego jest on interpretowany jako znak literał, który ma być dopasowany.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> lub opcja `x` wbudowana zmienia to domyślne zachowanie w następujący sposób:

- Niesłańcuchowany biały znak we wzorcu wyrażenia regularnego jest ignorowany. Aby być częścią wzorca wyrażenia regularnego, znaki odstępu muszą `\s` być`\` zmienione (na przykład jako lub " ").

- Znak numeru (#) jest interpretowany jako początek komentarza, a nie jako znak literał. Cały tekst we wzorcu wyrażenia regularnego od znaku # do końca ciągu jest interpretowany jako komentarz.

Jednak w następujących przypadkach znaki odstępu w wyrażeniu regularnym nie są <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> ignorowane, nawet jeśli używasz tej opcji:

- Biały znak w klasie znaków jest zawsze interpretowany dosłownie. Na przykład wzorzec `[ .,;:]` wyrażenia regularnego pasuje do dowolnego pojedynczego znaku odstępu, kropki, przecinka, średnika lub dwukropka.

- Biały znak nie jest dozwolony w nawiasie `{`kwantyfikatora, takiego jak *n*`}`, `{` *n*`,}`i `{` *n*`,`*m*`}`. Na przykład wzorzec `\d{1, 3}` wyrażenia regularnego nie pasuje do wszystkich sekwencji cyfr od jednej do trzech cyfr, ponieważ zawiera znak odstępu.

- Biały znak nie jest dozwolone w sekwencji znaków, która wprowadza element języka. Przykład:

  - `(?:` *Podwyrażenie* `)` elementu języka reprezentuje grupę niebędącą `(?:` częścią elementu, a część elementu nie może mieć osadzonych spacji. `(? :` *Podwyrażenie* `)` wzorca zgłasza <xref:System.ArgumentException> w czasie wykonywania, ponieważ aparat wyrażeń regularnych nie `( ?:`może analizować wzorca, a *wyrażenie podrzędne* `)` wzorca nie odpowiada *podwyrażeniem podrzędnym.*

  - `\p{` *name*Nazwa`}`elementu języka , która reprezentuje kategorię Unicode lub nazwany blok, `\p{` nie może zawierać osadzonych spacji w części elementu. Jeśli zostanie dodasz biały znak, element <xref:System.ArgumentException> zgłasza w czasie wykonywania.

Włączenie tej opcji pomaga uprościć wyrażenia regularne, które są często trudne do przeanalizowania i zrozumienia. Poprawia czytelność i umożliwia dokumentowanie wyrażenia regularnego.

Poniższy przykład definiuje następujący wzorzec wyrażenia regularnego:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Ten wzorzec jest podobny do wzorca zdefiniowanego w [jawnych przechwytuje tylko](#explicit-captures-only) sekcji, z tą różnicą, <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> że używa opcji do ignorowania wzorca biały znak.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

W poniższym przykładzie użyto opcji `(?x)` wbudowanej do ignorowania odstępu szyku.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Tryb od prawej do lewej

Domyślnie aparat wyrażeń regularnych wyszukuje od lewej do prawej. Kierunek wyszukiwania można odwrócić <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> za pomocą tej opcji. Wyszukiwanie rozpoczyna się automatycznie od ostatniej pozycji znaku ciągu. Dla metod dopasowywania wzorców, które <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>zawierają parametr pozycji początkowej, takich jak pozycja początkowa jest indeks po prawej stronie znaku, w którym ma się rozpocząć wyszukiwanie.

> [!NOTE]
> Tryb wzorca od prawej do lewej jest <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> dostępny `options` tylko przez <xref:System.Text.RegularExpressions.Regex> podanie wartości do parametru konstruktora klasy lub metody dopasowywania wzorca statycznego. Nie jest dostępna jako opcja wbudowana.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> zmienia tylko kierunek wyszukiwania; nie interpretuje wzorca wyrażenia regularnego od prawej do lewej. Na przykład wyrażenie `\bb\w+\s` regularne dopasowuje wyrazy, które zaczynają się od litery "b", a po nim następuje znak odstępu. W poniższym przykładzie ciąg wejściowy składa się z trzech wyrazów, które zawierają jeden lub więcej znaków "b". Pierwsze słowo zaczyna się od "b", drugie kończy się na "b", a trzecie zawiera dwa znaki "b" w środku wyrazu. Jak pokazano dane wyjściowe z przykładu, tylko pierwsze słowo pasuje do wzorca wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Należy również zauważyć, że asercja wyprzedzająca `(?=`(element`)` języka `(?<=` *podwyrażenia)* i twierdzenie patrząc za (element`)` języka *podwyrażenia)* nie zmieniają kierunku. Twierdzenia wyprzedzające patrzą w prawo; spojrzenia na poprzestały w lewo. Na przykład wyrażenie `(?<=\d{1,2}\s)\w+,?\s\d{4}` regularne używa potwierdzenia lookbehind do testowania daty poprzedzającej nazwę miesiąca. Wyrażenie regularne następnie pasuje do miesiąca i roku. Aby uzyskać informacje na temat twierdzeń wyprzedzających i obradych, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Początek dopasowania musi być poprzedzony jedną lub dwiema cyframi dziesiętnymi, po których następuje spacja.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|`,?`|Dopasuj zero lub jeden przecinek.|
|`\s`|Dopasowuje znak odstępu.|
|`\d{4}`|Dopasuj cztery cyfry dziesiętne.|

## <a name="ecmascript-matching-behavior"></a>Zachowanie dopasowywania ECMAScript

Domyślnie aparat wyrażeń regularnych używa zachowania kanonicznego podczas dopasowywania wzorca wyrażenia regularnego do tekstu wejściowego. Można jednak poinstruować aparat wyrażeń regularnych, aby używał <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> zachowania dopasowywania ECMAScript, określając tę opcję.

> [!NOTE]
> Zachowanie zgodne ze standardem ECMAScript <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> jest dostępne `options` tylko <xref:System.Text.RegularExpressions.Regex> przez podanie wartości parametru konstruktora klasy lub metody dopasowywania wzorców statycznych. Nie jest dostępna jako opcja wbudowana.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> może być łączona <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> tylko z opcjami i opcjami. Użycie dowolnej innej opcji w wyrażeniu regularnym powoduje <xref:System.ArgumentOutOfRangeException>

Zachowanie ECMAScript i kanonicznych wyrażeń regularnych różni się w trzech obszarach: składnia klasy znaków, samonawodujące się grupy przechwytywania oraz interpretacja ósemkowe i wsteczne.

- Składnia klasy znaków. Ponieważ kanoniczne wyrażenia regularne obsługują Unicode, podczas gdy ECMAScript nie, klasy znaków w ecmascript mają bardziej ograniczoną składnię, a niektóre elementy języka klasy znaków mają inne znaczenie. Na przykład ecmascript nie obsługuje elementów języka, takich jak `\p` `\P`kategoria Unicode lub elementy bloku i . Podobnie `\w` element, który pasuje do znaku wyrazu, `[a-zA-Z_0-9]` jest odpowiednikiem klasy `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` znaków podczas korzystania z ECMAScript i podczas korzystania z zachowania kanonicznego. Aby uzyskać więcej informacji, zobacz [Klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Poniższy przykład ilustruje różnicę między dopasowaniem wzorców kanonicznych i ECMAScript. Definiuje wyrażenie regularne, `\b(\w+\s*)+`które dopasowuje wyrazy, po których następują znaki odstępu. Dane wejściowe składają się z dwóch ciągów, jeden, który używa zestawu znaków łacińskich, a drugi, który używa zestawu znaków cyrylicy. Jak pokazano na wyjściu, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> wywołanie metody, która używa dopasowania ECMAScript nie odpowiada cyrylicy, podczas gdy wywołanie metody, która używa dopasowania kanonicznego, jest zgodne z tymi słowami.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Samonawiązujące się grupy przechwytywania. Klasa przechwytywania wyrażeń regularnych z wstecznązwycesością do siebie musi być aktualizowana przy każdej iteracji przechwytywania. Jak pokazano w poniższym przykładzie, `((a+)(\1) ?)+` ta funkcja umożliwia wyrażenie regularne dopasowanie ciągu wejściowego " aaaaa aaaaaa " podczas korzystania z ECMAScript, ale nie podczas korzystania z dopasowywania kanonicznego.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Wyrażenie regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.

  |Wzorce|Opis|
  |-------------|-----------------|
  |1lit.|Dopasuj literę "a" jeden lub więcej razy. Jest to druga grupa przechwytywania.|
  |(\1)|Dopasuj podciąg przechwycony przez pierwszą grupę przechwytywania. Jest to trzecia grupa przechwytywania.|
  |?|Dopasuj zero lub jeden znak spacji.|
  |((a+)(\1) ?) +|Dopasuj wzorzec jednego lub więcej znaków "a", po którym następuje ciąg, który pasuje do pierwszej grupy przechwytywania, po której następuje zero lub jeden znak spacji jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|

- Rozwiązywanie niejasności między ósemkowymi ucieczkami a wnioskami wsteczowymi. W poniższej tabeli podsumowano różnice w interpretacji ósemkowej i wstecznej za pomocą wyrażeń regularnych kanonicznych i ECMAScript.

  |Wyrażenie regularne|Zachowanie kanoniczne|Zachowanie ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0`następnie od 0 do 2 cyfr ósemkowych|Interpretuj jako ósemki. Na przykład `\044` jest zawsze interpretowane jako wartość ósemki i oznacza "$".|To samo zachowanie.|
  |`\`po którym następuje cyfra od 1 do 9, po której następuje brak dodatkowych cyfr dziesiętnych,|Interpretować jako wniosek wsteczny. Na przykład `\9` zawsze oznacza backreference 9, nawet jeśli dziewiąta grupa przechwytywania nie istnieje. Jeśli grupa przechwytywania nie istnieje, analizator wyrażenia regularnego <xref:System.ArgumentException>zgłasza plik .|Jeśli istnieje grupa przechwytywania pojedynczej cyfry dziesiętnej, odniesienie wsteczne do tej cyfry. W przeciwnym razie należy interpretować wartość jako literał.|
  |`\`po którym następuje cyfra od 1 do 9, a następnie dodatkowe cyfry dziesiętne|Interpretuj cyfry jako wartość dziesiętną. Jeśli ta grupa przechwytywania istnieje, należy interpretować wyrażenie jako wniosek wsteczny.<br /><br /> W przeciwnym razie należy interpretować wiodące cyfry ósemki do ósemki 377; oznacza to, że należy wziąć pod uwagę tylko niskie 8 bitów wartości. Zinterpretuj pozostałe cyfry jako literały. Na przykład w `\3000`wyrażeniu , jeśli istnieje przechwytywanie grupy 300, interpretuj jako przyw. jeśli przechwytywanie grupy 300 nie istnieje, interpretować jako ósemki 300 następuje 0.|Interpretować jako backreference konwertując jak najwięcej cyfr, jak to możliwe do wartości dziesiętnej, która może odnosić się do przechwytywania. Jeśli nie można przekonwertować żadnych cyfr, należy interpretować jako ósemę przy użyciu cyfr ósemkowych wiodących do ósemki 377; interpretować pozostałe cyfry jako literały.|

## <a name="comparison-using-the-invariant-culture"></a>Porównanie przy użyciu kultury niezmiennej

Domyślnie, gdy aparat wyrażeń regularnych wykonuje porównania bez uwzględniania wielkości liter, używa konwencji wielkości liter bieżącej kultury do określenia równoważnych wielkich i małych liter.

Jednak to zachowanie jest niepożądane w przypadku niektórych typów porównań, szczególnie podczas porównywania danych wejściowych użytkownika z nazwami zasobów systemowych, takich jak hasła, pliki lub adresy URL. Poniższy przykład ilustruje takie jak scenariusz. Kod ma na celu zablokowanie dostępu do dowolnego zasobu, którego adres URL jest poprzedzony **FILE://**. Wyrażenie regularne próbuje dopasowania bez uwzględniania wielkości liter z ciągiem `$FILE://`przy użyciu wyrażenia regularnego . Jednakże, gdy obecna kultura systemu jest tr-TR (turecko-turecki), "I" nie jest wielką literą odpowiednik "i". W rezultacie wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody zwraca `false`, a dostęp do pliku jest dozwolony.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat porównań ciągów, które są rozróżniane z literą i które używają kultury niezmiennej, zobacz [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)znaków .

Zamiast używać porównania bez uwzględniania wielkości liter bieżącej kultury, można <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> określić opcję ignorowania różnic kulturowych w języku i używać konwencji kultury niezmiennej.

> [!NOTE]
> Porównanie przy użyciu kultury niezmiennej jest dostępna <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> tylko przez `options` podanie <xref:System.Text.RegularExpressions.Regex> wartości do parametru konstruktora klasy lub statycznej metody dopasowywania wzorców. Nie jest dostępna jako opcja wbudowana.

Poniższy przykład jest identyczny z poprzednim przykładem, z tą różnicą, że metoda statyczna <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> jest wywoływana z opcjami, które zawierają <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Nawet wtedy, gdy bieżąca kultura jest ustawiona na turecki (Turcja), aparat wyrażeń regularnych jest w stanie pomyślnie dopasować "PLIK" i "plik" i zablokować dostęp do zasobu pliku.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
