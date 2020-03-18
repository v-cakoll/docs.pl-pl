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
ms.openlocfilehash: a53d7517485d2a0b02b6f11928f478a7da3f9503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972112"
---
# <a name="regular-expression-options"></a>Opcje wyrażeń regularnych

Domyślnie porównanie ciągu wejściowego z dowolnymi literałami we wzorcu wyrażenia regularnego jest uwzględniane wielkości liter, odstęp w wzorcu wyrażenia regularnego jest interpretowany jako literał znaków odstępu, a grupy przechwytywania w wyrażeniu regularnym są nazwane niejawnie, jak również jawnie. Można zmodyfikować te i kilka innych aspektów domyślnego zachowania wyrażenia regularnego, określając opcje wyrażenia regularnego. Te opcje, które są wymienione w poniższej tabeli, mogą być zawarte w wierszu jako część <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> wzorca wyrażenia regularnego lub <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> mogą być dostarczane do konstruktora klasy lub statycznej metody dopasowywania wzorców jako wartość wyliczenia.

|Członek RegexOptions|Znak wbudowany|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Niedostępne|Użyj zachowania domyślnego. Aby uzyskać więcej informacji, zobacz [Opcje domyślne](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Używa dopasowywania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz [Dopasowanie niewrażliwe na wielkość liter](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Użyj trybu wielowierszowego, gdzie `^` i `$` dopasować początek i koniec każdego wiersza (zamiast początku i końca ciągu wejściowego). Aby uzyskać więcej informacji, zobacz [Tryb wielowierszowy](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Użyj trybu jednowierszowego, w którym kropka (.) pasuje `\n`do każdego znaku (zamiast każdego znaku z wyjątkiem). Aby uzyskać więcej informacji, zobacz [Tryb jednowierszowy](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nie przechwytuje nienazwanych grup. Tylko prawidłowe przechwytywania są jawnie nazwane lub numerowane grupy `(?<` *wyrażenia* `>` *podrzędnego*`)`nazwy formularza . Aby uzyskać więcej informacji, zobacz [Jawne przechwytywanie tylko](#explicit-captures-only).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Niedostępne|Skompiluj wyrażenie regularne do zestawu. Aby uzyskać więcej informacji, zobacz [Kompilowane wyrażenia regularne](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Wyklucz nieunieulatyce biały znak ze`#`szyku i włącz komentarze po znaku liczbowym ( ). Aby uzyskać więcej informacji, zobacz [Ignorowanie odstępu](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Niedostępne|Zmień kierunek wyszukiwania. Wyszukiwanie przesuwa się od prawej do lewej, a nie od lewej do prawej. Aby uzyskać więcej informacji, zobacz [Tryb od prawej do lewej](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Niedostępne|Włącz zachowanie zgodne ze standardem ECMAScript dla wyrażenia. Aby uzyskać więcej informacji, zobacz [ZACHOWANIE DOPasowywania ECMAScript](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Niedostępne|Ignoruj różnice kulturowe w języku. Aby uzyskać więcej informacji, zobacz [Porównanie przy użyciu kultury niezmiennej](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Określanie opcji

Opcje wyrażeń regularnych można określić na jeden z trzech sposobów:

- W `options` parametrze <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy`Shared` lub statycznej (w języku <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>Visual Basic) metody dopasowywania wzorców, takich jak lub . Parametr `options` jest bitową lub <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> kombinacją wyliczonych wartości.

  Gdy opcje są dostarczane <xref:System.Text.RegularExpressions.Regex> do wystąpienia `options` przy użyciu parametru konstruktora klasy, opcje są przypisane do <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwości. Jednak <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwość nie odzwierciedla opcji wbudowanych w sam wzorzec wyrażenia regularnego.

  Poniższy przykład stanowi ilustrację. Używa `options` parametru <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, aby włączyć dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania wyrazów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Stosując opcje w wierszu wyrażenia regularnego we `(?imnsx-imnsx)`wzorcu wyrażenia regularnego ze składnią . Opcja ma zastosowanie do szyku od punktu, w którym opcja jest zdefiniowana do końca szyku lub do punktu, w którym opcja jest niezdefiniowana przez inną opcję liniową. Należy zauważyć, <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> że <xref:System.Text.RegularExpressions.Regex> właściwość wystąpienia nie odzwierciedla tych opcji wbudowanych. Aby uzyskać więcej informacji, zobacz [Różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tematu.

  Poniższy przykład stanowi ilustrację. Używa opcji wbudowanych, aby umożliwić dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania wyrazów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Stosując opcje w wierszu w określonej konstrukcji grupowania we `(?imnsx-imnsx:`wzorcu wyrażenia regularnego z *podwyrażeniem*`)`składni . Brak znaku przed zestawem opcji włącza zestaw; znak minus przed zestawem opcji wyłącza wyruszył. (`?` jest stałą częścią składni konstrukcji języka, która jest wymagana, czy opcje są włączone lub wyłączone).) Opcja dotyczy tylko tej grupy. Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  Poniższy przykład stanowi ilustrację. Używa opcji wbudowanych w konstrukcji grupowania, aby umożliwić dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca podczas identyfikowania wyrazów, które zaczynają się od litery "d".

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Jeśli opcje są określone w linii,`-`znak minus ( ) przed opcją lub zestawem opcji wyłącza te opcje. Na przykład konstrukcja `(?ix-ms)` inline włącza <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcje i wyłącza <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcje i wyłącza opcje. Wszystkie opcje wyrażenia regularnego są domyślnie wyłączone.

> [!NOTE]
> Jeśli opcje wyrażenia regularnego określone `options` w parametrze konstruktora lub wywołania metody są w konflikcie z opcjami określonymi w wierszu we wzorcu wyrażenia regularnego, używane są opcje wbudowanych.

Następujące pięć opcji wyrażenia regularnego można ustawić zarówno z parametrem opcji, jak i wbudowanym:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Za pomocą parametru `options` można ustawić pięć następujących opcji wyrażenia regularnego, ale nie można ich ustawić w linii:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Określanie opcji

Można określić, które opcje <xref:System.Text.RegularExpressions.Regex> zostały dostarczone do obiektu, gdy został uprzedzony, pobierając wartość właściwości tylko do <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> odczytu. Ta właściwość jest szczególnie przydatna do określania opcji, które są <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> zdefiniowane dla skompilowanego wyrażenia regularnego utworzonego przez metodę.

Aby przetestować obecność dowolnej <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>opcji z wyjątkiem, wykonaj operację AND z wartością <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości i wartością, <xref:System.Text.RegularExpressions.RegexOptions> którą jesteś zainteresowany. Następnie sprawdź, czy wynik <xref:System.Text.RegularExpressions.RegexOptions> jest równy tej wartości. Poniższy przykład sprawdza, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> czy opcja została ustawiona.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Aby sprawdzić <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, należy określić, <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> czy wartość <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>właściwości jest równa , jak pokazano w poniższym przykładzie.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

W poniższych sekcjach wymieniono opcje obsługiwane przez wyrażenie regularne w .NET.

## <a name="default-options"></a>Opcje domyślne

Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> wskazuje, że nie określono żadnych opcji, a aparat wyrażeń regularnych używa jego domyślnezachowanie. Uwzględnione są następujące elementy:

- Wzorzec jest interpretowany jako wyrażenie kanoniczne, a nie regularne ECMAScript.

- Wzorzec wyrażenia regularnego jest dopasowywany w ciągu wejściowym od lewej do prawej.

- W porównaniach jest z uwzględnieniem wielkości liter.

- Elementy `^` `$` i języka odpowiadają początku i na końcu ciągu wejściowego.

- Element `.` języka pasuje do `\n`każdego znaku z wyjątkiem .

- Wszelkie odstępy w wzorcu wyrażenia regularnego są interpretowane jako znak spacji literału.

- Konwencje bieżącej kultury są używane podczas porównywania wzorca do ciągu wejściowego.

- Przechwytywanie grup we wzorcu wyrażenia regularnego są niejawne, a także jawne.

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> nie ma odpowiednika w wierszu. Gdy opcje wyrażenia regularnego są stosowane w linii, domyślne zachowanie jest przywracane na zasadzie option-by-option, przez wyłączenie określonej opcji. Na przykład `(?i)` włącza porównanie bez uwzględniania `(?-i)` wielkości liter i przywraca domyślne porównanie uwzględniania wielkości liter.

Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> opcja reprezentuje domyślne zachowanie aparatu wyrażeń regularnych, rzadko jest jawnie określone w wywołaniu metody. Zamiast tego wywoływana jest metoda `options` dopasowywania wzorców statycznych lub statycznych bez parametru.

## <a name="case-insensitive-matching"></a>Dopasowanie bez uwzględniania wielkości liter

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> lub opcja `i` inline zapewnia dopasowanie bez uwzględniania wielkości liter. Domyślnie używane są konwencje wielkości liter bieżącej kultury.

W poniższym przykładzie zdefiniowano `\bthe\w*\b`wzorzec wyrażenia regularnego, który pasuje do wszystkich wyrazów rozpoczynających się od "the". Ponieważ pierwsze wywołanie <xref:System.Text.RegularExpressions.Regex.Match%2A> metody używa domyślnego porównania z uwzględnieniem wielkości liter, dane wyjściowe wskazują, że ciąg "The", który rozpoczyna zdanie nie jest dopasowywany. Jest on aplikować, <xref:System.Text.RegularExpressions.Regex.Match%2A> gdy metoda <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>jest wywoływana z opcjami ustawionymi na .

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

W poniższym przykładzie modyfikuje wzorzec wyrażenia regularnego z `options` poprzedniego przykładu, aby użyć opcji wbudowanych zamiast parametru, aby zapewnić porównanie bez uwzględniania wielkości liter. Pierwszy wzorzec definiuje opcję bez uwzględniania wielkości liter w konstrukcji grupowania, która ma zastosowanie tylko do litery "t" w ciągu "the". Ponieważ konstrukcja opcji występuje na początku wzorca, drugi wzorzec stosuje opcję bez uwzględniania wielkości liter do całego wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Tryb wielowierszowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> lub opcja `m` inline umożliwia aparatowi wyrażeń regularnych obsługę ciągu wejściowego składającego się z wielu wierszy. Zmienia interpretację `^` elementów `$` języka i tak, aby były one zgodne z początku i końca wiersza, zamiast początku i końca ciągu wejściowego.

Domyślnie `$` pasuje tylko do końca ciągu wejściowego. Jeśli określisz <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcję, pasuje ona`\n`do znaku nowego wiersza ( ) lub końca ciągu wejściowego. Nie jest ona jednak zgodna z kombinacją znaków powrotu/wysuwu wiersza karetki. Aby pomyślnie je dopasować, użyj `\r?$` wyrażenia `$`podrzędnego zamiast tylko .

Poniższy przykład wyodrębnia nazwy meloniki i wyniki <xref:System.Collections.Generic.SortedList%602> i dodaje je do kolekcji, która sortuje je w porządku malejącym. Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A> jest wywoływana dwa razy. W pierwszym wywołaniu metody wyrażenie `^(\w+)\s(\d+)$` regularne jest i nie są ustawiane żadne opcje. Jak pokazuje dane wyjściowe, ponieważ aparat wyrażeń regularnych nie może dopasować wzorca wejściowego wraz z początku i końca ciągu wejściowego, nie znaleziono dopasowań. W drugim wywołaniu metody wyrażenie regularne `^(\w+)\s(\d+)\r?$` zostanie zmienione na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>i opcje są ustawione na . Jak pokazuje dane wyjściowe, nazwy i wyniki są pomyślnie dopasowane, a wyniki są wyświetlane w kolejności malejącej.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Wzorzec `^(\w+)\s(\d+)\r*$` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`^`|Rozpocznij od początku linii.|
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|
|`\s`|Dopasowuje znak odstępu.|
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to druga grupa przechwytywania.|
|`\r?`|Dopasuj znak zerowy lub jeden znak powrotu karetki.|
|`$`|Koniec na końcu wiersza.|

Poniższy przykład jest odpowiednikiem poprzedniego, z tą różnicą, że używa opcji `(?m)` wbudowanych, aby ustawić opcję multiline.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Tryb jednoliniowy

Opcja <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> lub opcja `s` inline powoduje, że aparat wyrażeń regularnych traktuje ciąg wejściowy tak, jakby składa się z pojedynczego wiersza. Czyni to poprzez zmianę zachowania elementu`.`języka period ( ) tak, aby pasował do każdego znaku, zamiast dopasowywania każdego znaku z wyjątkiem znaku `\n` nowego wiersza lub \u000A.

W poniższym przykładzie przedstawiono, `.` jak zmienia się zachowanie <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> elementu języka podczas korzystania z opcji. Wyrażenie `^.+` regularne rozpoczyna się na początku ciągu i dopasowuje każdy znak. Domyślnie dopasowanie kończy się na końcu pierwszego wiersza; wzorzec wyrażenia regularnego pasuje `\r` do znaku powrotu karetki lub `\n`\u000D, ale nie jest zgodny . Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcja interpretuje cały ciąg wejściowy jako pojedynczy wiersz, pasuje do `\n`każdego znaku w ciągu wejściowym, w tym .

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Poniższy przykład jest odpowiednikiem poprzedniego, z tą różnicą, że używa opcji `(?s)` wbudowanych, aby włączyć tryb jednowierszowy.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Jawne przechwytywanie tylko

Domyślnie grupy przechwytywania są definiowane przez użycie nawiasów we wzorcu wyrażenia regularnego. Nazwane grupy są przypisywane nazwę `(?<`lub numer przez opcję języka*podwyrażenia* `)` *nazwy,*`>`podczas gdy grupy bez nazwy są dostępne za pomocą indeksu. W <xref:System.Text.RegularExpressions.GroupCollection> obiekcie nienazwane grupy poprzedzają nazwane grupy.

Grupowanie konstrukcji są często używane tylko do stosowania kwantyfikatorów do wielu elementów języka, a przechwycone podciągi nie są interesujące. Na przykład jeśli następujące wyrażenie regularne:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

ma na celu jedynie wyodrębnienie zdań, które kończą się kropką, wykrzyknikiem lub znakiem <xref:System.Text.RegularExpressions.Match> zapytania z dokumentu, tylko wynikowe zdanie (reprezentowane przez obiekt) jest przedmiotem zainteresowania. Poszczególne słowa w kolekcji nie są.

Przechwytywanie grup, które nie są następnie używane może być <xref:System.Text.RegularExpressions.GroupCollection> kosztowne, ponieważ aparat wyrażeń regularnych musi wypełnić zarówno i <xref:System.Text.RegularExpressions.CaptureCollection> obiektów kolekcji. Alternatywnie można użyć <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji lub opcji `n` wbudowanych, aby określić, że tylko prawidłowe przechwytywania są jawnie nazwane `(?<`lub ponumerowane grupy, które są oznaczone przez konstrukcję *wyrażenia podrzędnego* `)` *nazwy.* `>`

W poniższym przykładzie są wyświetlane informacje `\b\(?((\w+),?\s?)+[\.!?]\)?` o dopasowaniach <xref:System.Text.RegularExpressions.Regex.Match%2A> zwracanych przez wzorzec wyrażenia regularnego, gdy metoda jest wywoływana z opcją i bez niej. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> Jak pokazuje dane wyjściowe z pierwszego wywołania metody, <xref:System.Text.RegularExpressions.GroupCollection> aparat <xref:System.Text.RegularExpressions.CaptureCollection> wyrażeń regularnych w pełni wypełnia i kolekcji obiektów z informacjami o przechwyconych podciągów. Ponieważ druga metoda jest `options` wywoływana z ustawą , <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>nie przechwytuje informacji o grupach.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Wzorzec`\b\(?((?>\w+),?\s?)+[\.!?]\)?` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Rozpocznij od granicy słowa.|
|`\(?`|Dopasuj zero lub jedno wystąpienie nawiasu otwierającego ("(").|
|`(?>\w+),?`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje zero lub jeden przecinek. Nie cofaj się podczas dopasowywania znaków wyrazów.|
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|
|`((\w+),?\s?)+`|Dopasuj kombinację jednego lub więcej znaków wyrazu, zero lub jednego przecinka i zero lub jeden znak biały jeden lub więcej razy.|
|`[\.!?]\)?`|Dopasuj dowolny z trzech symboli interpunkcyjnych, po których następuje zero lub jeden nawias zamykający (")").|

Można również użyć `(?n)` elementu wbudowanych, aby pominąć automatyczne przechwytywanie. Poniższy przykład modyfikuje poprzedni wzorzec `(?n)` wyrażenia regularnego, <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> aby użyć elementu wbudowanyzamiast opcji.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Na koniec można użyć elementu `(?n:)` grupy wbudowanych, aby pominąć automatyczne przechwytywanie na zasadzie gruppo grupie. Poniższy przykład modyfikuje poprzedni wzorzec, aby pominąć `((?>\w+),?\s?)`nienazwane przechwytywanie w grupie zewnętrznej . Należy zauważyć, że spowoduje to wygaszanie nienazwanych przechwytów również w grupie wewnętrznej.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne

Domyślnie wyrażenia regularne w .NET są interpretowane. Gdy <xref:System.Text.RegularExpressions.Regex> obiekt jest tworzony lub wywoływana jest metoda statyczna, <xref:System.Text.RegularExpressions.Regex> wzorzec wyrażenia regularnego jest analizowany w zestawie niestandardowych kodów opcodes, a interpreter używa tych kodów opdo uruchomienia wyrażenia regularnego. Wiąże się to z kompromisem: koszt zainicjowania aparatu wyrażeń regularnych jest zminimalizowany kosztem wydajności w czasie wykonywania.

Można użyć skompilowany zamiast interpretowane wyrażenia <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> regularne przy użyciu opcji. W takim przypadku, gdy wzorzec jest przekazywany do aparatu wyrażeń regularnych, jest analizowany w zestaw opcodes, a następnie konwertowane na język pośredni firmy Microsoft (MSIL), które mogą być przekazywane bezpośrednio do wspólnego języka wykonywania. Skompilowane wyrażenia regularne maksymalizują wydajność w czasie wykonywania kosztem czasu inicjowania.

> [!NOTE]
> Wyrażenie regularne można skompilować tylko <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> przez podanie `options` wartości <xref:System.Text.RegularExpressions.Regex> do parametru konstruktora klasy lub metody dopasowywania wzorców statycznych. Opcja nie jest dostępna jako opcja inline.

Skompilowanych wyrażeń regularnych można używać w wywołaniach zarówno dla wyrażeń regularnych statycznych, jak i wystąpień. W statycznych wyrażeniach regularnych <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcja `options` jest przekazywana do parametru metody dopasowywania wzorców wyrażenia regularnego. W przypadku wyrażeń regularnych `options` jest przekazywana do parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy. W obu przypadkach powoduje zwiększoną wydajność.

Jednak ta poprawa wydajności występuje tylko w następujących warunkach:

- Obiekt, <xref:System.Text.RegularExpressions.Regex> który reprezentuje określone wyrażenie regularne jest używany w wielu wywołań do metod dopasowywania wzorca wyrażenia regularnego.

- Obiekt <xref:System.Text.RegularExpressions.Regex> nie może wykraczać poza zakres, więc może być ponownie użyty.

- Statyczne wyrażenie regularne jest używane w wielu wywołaniach metod dopasowywania wzorców wyrażeń regularnych. (Poprawa wydajności jest możliwe, ponieważ wyrażenia regularne używane w wywołaniach metod statycznych są buforowane przez aparat wyrażeń regularnych.)

> [!NOTE]
> Opcja <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> nie jest związana <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> z metodą, która tworzy zestaw specjalnego przeznaczenia, który zawiera wstępnie zdefiniowane skompilowane wyrażenia regularne.

## <a name="ignore-white-space"></a>Ignoruj biały znak

Domyślnie biały znak we wzorcu wyrażenia regularnego jest znaczący; wymusza aparat wyrażeń regularnych, aby dopasować znak odstępu w ciągu wejściowym. Z tego powodu wyrażenie`\b\w+\s`regularne "`\b\w+` " i " " są mniej więcej równoważnymi wyrażeniami regularnymi. Ponadto po napotkaniu znaku numeru (#) we wzorcu wyrażenia regularnego jest on interpretowany jako znak literałdosłowny do dopasowania.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> lub opcja `x` w wierszu zmienia to domyślne zachowanie w następujący sposób:

- Nieuniknięte białe miejsce we wzorcu wyrażenia regularnego jest ignorowane. Aby być częścią wzorca wyrażenia regularnego, należy uniknąć znaków odstępu `\s` (na przykład jako "`\`

- Znak numeru (#) jest interpretowany jako początek komentarza, a nie jako znak dosłowny. Cały tekst we wzorcu wyrażenia regularnego od znaku # do końca ciągu jest interpretowany jako komentarz.

Jednak w następujących przypadkach znaki odstępu w wyrażeniu regularnym nie są <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> ignorowane, nawet jeśli używasz tej opcji:

- Biały znak w klasie znaków jest zawsze interpretowany dosłownie. Na przykład wzorzec `[ .,;:]` wyrażenia regularnego pasuje do dowolnego pojedynczego znaku odstępu, kropki, przecinka, średnika lub dwukropka.

- Biały znak nie jest dozwolony w kwantyfikatorze w nawiasach, takim `{`jak *n*`}`, `{` *n*`,}`i `{` *n*`,`*m*`}`. Na przykład wzorzec `\d{1, 3}` wyrażenia regularnego nie pasuje do żadnych sekwencji cyfr od jednej do trzech cyfr, ponieważ zawiera znak odstępu.

- Biały znak nie jest dozwolone w sekwencji znaków, który wprowadza element języka. Przykład:

  - `(?:` *Podwyrażenie* `)` elementu języka reprezentuje grupę nieprzechwytywającą, a `(?:` część elementu nie może mieć osadzonych spacjów. Wyrażenie `(? :` *podrzędne* `)` wzorca zgłasza w czasie <xref:System.ArgumentException> wykonywania, ponieważ aparat wyrażeń `( ?:`regularnych nie może przeanalizować wzorca, a *wyrażenie podrzędne* `)` wzorca nie pasuje do *wyrażenia podrzędnego*.

  - `\p{` *name*Nazwa`}`elementu języka , który reprezentuje kategorię Unicode lub nazwany blok, `\p{` nie może zawierać osadzonych spacji w części elementu. Jeśli dołączysz biały znak, element <xref:System.ArgumentException> zgłasza w czasie wykonywania.

Włączenie tej opcji pomaga uprościć wyrażenia regularne, które często są trudne do przeanalizowania i zrozumienia. Poprawia czytelność i umożliwia udokumentowanie wyrażenia regularnego.

W poniższym przykładzie zdefiniowano następujący wzorzec wyrażenia regularnego:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Ten wzorzec jest podobny do wzorca zdefiniowanego w sekcji <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> [Jawne przechwytywanie tylko,](#explicit-captures-only) z tą różnicą, że używa opcji ignorowania odstępu odstępu.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

W poniższym przykładzie użyto opcji `(?x)` wbudowanych do zignorowania odstępu wycinku.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Tryb od prawej do lewej

Domyślnie aparat wyrażeń regularnych wyszukuje od lewej do prawej. Kierunek wyszukiwania można odwrócić za <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> pomocą tej opcji. Wyszukiwanie rozpoczyna się automatycznie w ostatniej pozycji znaku ciągu. W przypadku metod dopasowywania wzorców, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>które zawierają parametr pozycji początkowej, takich jak , pozycja początkowa jest indeksem po prawej stronie pozycji znaku, w którym ma się rozpocząć wyszukiwanie.

> [!NOTE]
> Tryb wzorca od prawej do lewej jest <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> dostępny `options` tylko przez <xref:System.Text.RegularExpressions.Regex> podanie wartości do parametru konstruktora klasy lub statycznej metody dopasowywania wzorców. Opcja nie jest dostępna jako opcja inline.

Opcja <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> zmienia tylko kierunek wyszukiwania; nie interpretuje wzorca wyrażenia regularnego od prawej do lewej. Na przykład wyrażenie `\bb\w+\s` regularne pasuje do wyrazów, które zaczynają się od litery "b", a następnie znak odstępu. W poniższym przykładzie ciąg wejściowy składa się z trzech słów, które zawierają jeden lub więcej znaków "b". Pierwsze słowo zaczyna się od "b", drugie kończy się literą "b", a trzecie zawiera dwa znaki "b" w środku słowa. Jak pokazuje dane wyjściowe z przykładu, tylko pierwsze słowo pasuje do wzorca wyrażenia regularnego.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Należy również zauważyć, że `(?=`potwierdzenie wyszukiwania (element języka *podwyrażenia)* `)` i lookbehind potwierdzenia (element `(?<=`języka *podwyrażenia)* `)` nie zmieniają kierunku. Twierdzenia o patrzeniu w przyszłość patrzą w prawo; za glinami patrzą w lewo. Na przykład wyrażenie `(?<=\d{1,2}\s)\w+,?\s\d{4}` regularne używa potwierdzenia lookbehind do testowania daty poprzedzającej nazwę miesiąca. Wyrażenie regularne odpowiada następnie miesiącowi i rokowi. Aby uzyskać informacje na temat wyszukiwania i wyszukiwania za potwierdzeń, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

|Wzorce|Opis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Początek dopasowania musi być poprzedzony jedną lub dwiema cyframi dziesiętnym, po których następuje spacja.|
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|
|`,?`|Dopasuj zero lub jeden przecinek.|
|`\s`|Dopasowuje znak odstępu.|
|`\d{4}`|Dopasuj cztery cyfry dziesiętne.|

## <a name="ecmascript-matching-behavior"></a>Zachowanie dopasowywania ECMAScript

Domyślnie aparat wyrażeń regularnych używa zachowania kanonicznego podczas dopasowywania wzorca wyrażenia regularnego do tekstu wejściowego. Można jednak poinstruować aparat wyrażeń regularnych, aby używał <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> zachowania dopasowywania ECMAScript, określając tę opcję.

> [!NOTE]
> Zachowanie zgodne ze standardem ECMAScript <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> jest dostępne `options` tylko <xref:System.Text.RegularExpressions.Regex> przez podanie wartości do parametru konstruktora klasy lub statycznej metody dopasowywania wzorców. Opcja nie jest dostępna jako opcja inline.

Opcję <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> można łączyć tylko z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcjami i opcjami. Użycie dowolnej innej opcji w wyrażeniu regularnym skutkuje <xref:System.ArgumentOutOfRangeException>

Zachowanie ECMAScript i kanonicznych wyrażeń regularnych różni się w trzech obszarach: składnia klasy znaków, samoodwoływanie do przechwytywania grup i ósemkowe i wsteczne interpretacji.

- Składnia klasy znaków. Ponieważ kanoniczne wyrażenia regularne obsługują Unicode, podczas gdy ECMAScript nie, klasy znaków w ECMAScript mają bardziej ograniczoną składnię, a niektóre elementy języka klasy znaków mają inne znaczenie. Na przykład ECMAScript nie obsługuje elementów języka, takich jak `\p` kategoria `\P`Unicode lub elementy blokowe i . Podobnie `\w` element, który pasuje do znaku słowa, `[a-zA-Z_0-9]` jest odpowiednikiem klasy znaków `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` podczas korzystania z ECMAScript i podczas korzystania z zachowania kanonicznego. Aby uzyskać więcej informacji, zobacz [Klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Poniższy przykład ilustruje różnicę między dopasowywaniem wzorców kanonicznych i ECMAScript. Definiuje wyrażenie regularne, `\b(\w+\s*)+`które pasuje do wyrazów, po których następują znaki odstępu. Dane wejściowe składa się z dwóch ciągów, jeden, który używa łacińskiego zestawu znaków, a drugi, który używa zestawu znaków cyrylicy. Jak pokazuje dane wyjściowe, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> wywołanie metody, która używa dopasowania ECMAScript nie pasuje do słów cyrylicy, podczas gdy wywołanie metody, która używa dopasowania kanonicznego, pasuje do tych słów.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Samoodwołujące się do przechwytywania grup. Klasa przechwytywania wyrażenia regularnego z odwołaniem wstecznym do siebie musi być aktualizowana przy każdej iteracji przechwytywania. Jak pokazano w poniższym przykładzie, `((a+)(\1) ?)+` ta funkcja umożliwia wyrażenie regularne, aby dopasować ciąg wejściowy " aa aaaa aaaaaa " podczas korzystania z ECMAScript, ale nie podczas korzystania z dopasowania kanonicznego.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Wyrażenie regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.

  |Wzorce|Opis|
  |-------------|-----------------|
  |(a+)|Dopasuj literę "a" jeden lub więcej razy. Jest to druga grupa przechwytywania.|
  |(\1)|Dopasuj podciąg przechwycony przez pierwszą grupę przechwytywania. Jest to trzecia grupa przechwytywania.|
  |?|Dopasuj zero lub jeden znak spacji.|
  |((a+)(\1) ?) +|Dopasuj wzorzec jednego lub więcej znaków "a", po którym następuje ciąg znaków, który pasuje do pierwszej grupy przechwytywania, po której następuje zero lub jeden znak spacji jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|

- Rozwiązanie niejasności między ósemkowych ucieczki i backreferences. W poniższej tabeli podsumowano różnice w interpretacji ósemkowej i wstecznej za pomocą wyrażeń regularnych kanonicznych i ECMAScript.

  |Wyrażenie regularne|Zachowanie kanoniczne|Zachowanie ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0`następnie od 0 do 2 cyfr ósemkowych|Interpretuj jako ósemk. Na przykład `\044` jest zawsze interpretowany jako wartość ósemkowa i oznacza "$".|To samo zachowanie.|
  |`\`następnie cyfra od 1 do 9, po której następuje brak dodatkowych cyfr dziesiętnych,|Interpretować jako odwołanie wsteczne. Na przykład `\9` zawsze oznacza backreference 9, nawet jeśli dziewiąta grupa przechwytywania nie istnieje. Jeśli grupa przechwytywania nie istnieje, analizator wyrażeń regularnych zgłasza plik <xref:System.ArgumentException>.|Jeśli istnieje pojedyncza grupa przechwytywania cyfr dziesiętnych, odwołanie wsteczne do tej cyfry. W przeciwnym razie zinterpretuj wartość jako literał.|
  |`\`następnie cyfra od 1 do 9, a następnie dodatkowe cyfry dziesiętne|Interpretować cyfry jako wartość dziesiętną. Jeśli ta grupa przechwytywania istnieje, zinterpretować wyrażenie jako odwołanie wsteczne.<br /><br /> W przeciwnym razie zinterpretuj wiodące cyfry ósemkowe do ósemkowego 377; oznacza to, że należy wziąć pod uwagę tylko niskie 8 bitów wartości. Zinterpretuj pozostałe cyfry jako literały. Na przykład w `\3000`wyrażeniu , jeśli istnieje przechwytywanie grupy 300, interpretować jako odwołanie wsteczne 300; jeśli przechwytywanie grupy 300 nie istnieje, interpretować jako ósemki 300 następuje 0.|Interpretować jako odwołanie wsteczne, konwertując jak najwięcej cyfr, jak to możliwe do wartości dziesiętnej, która może odwoływać się do przechwytywania. Jeśli nie można przekonwertować żadnych cyfr, zinterpretuj jako ósemkową, używając cyfr liczb ósemkowych do ósemkowych 377; interpretować pozostałe cyfry jako literały.|

## <a name="comparison-using-the-invariant-culture"></a>Porównanie za pomocą kultury niezmiennej

Domyślnie, gdy aparat wyrażeń regularnych wykonuje porównania bez uwzględniania wielkości liter, używa konwencji wielkości liter bieżącej kultury do określenia równoważnych wielkich i małych znaków.

Jednak to zachowanie jest niepożądane w przypadku niektórych typów porównań, szczególnie podczas porównywania danych wejściowych użytkownika z nazwami zasobów systemowych, takich jak hasła, pliki lub adresy URL. Poniższy przykład ilustruje, takich jak scenariusz. Kod ma na celu zablokowanie dostępu do dowolnego zasobu, którego adres URL jest poprzedzony **FILE://**. Wyrażenie regularne próbuje dopasować wielkość liter do ciągu przy `$FILE://`użyciu wyrażenia regularnego . Jednakże, gdy obecna kultura systemu jest tr-TR (turecko-turcja), "I" nie jest wielki odpowiednik "i". W rezultacie wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody `false`powraca, a dostęp do pliku jest dozwolony.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Aby uzyskać więcej informacji na temat porównywań ciągów, które są rozróżniane i które używają kultury niezmiennej, zobacz [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md).

Zamiast używać bez uwzględniania wielkości liter porównania bieżącej kultury, można określić <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> opcję ignorowania różnic kulturowych w języku i używać konwencji kultury niezmiennej.

> [!NOTE]
> Porównanie przy użyciu kultury niezmiennejest dostępna <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> tylko `options` przez podanie <xref:System.Text.RegularExpressions.Regex> wartości do parametru konstruktora klasy lub statycznej metody dopasowywania wzorców. Opcja nie jest dostępna jako opcja inline.

Poniższy przykład jest identyczny z poprzednim przykładem, z tą różnicą, że metoda statyczna <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> jest wywoływana z opcjami, które zawierają <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Nawet wtedy, gdy bieżąca kultura jest ustawiona na turecki (Turcja), aparat wyrażeń regularnych jest w stanie pomyślnie dopasować "PLIK" i "plik" i zablokować dostęp do zasobu pliku.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
