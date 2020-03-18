---
title: Kotwice w wyrażeniach regularnych .NET
description: Dowiedz się, jak używać zakotwiczeń we wzorcach wyrażeń regularnych.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET Framework regular expressions, anchors
- .NET Framework regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
ms.openlocfilehash: c4853a6854f5da1a3217c976a03ddbde3b528560
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159666"
---
# <a name="anchors-in-regular-expressions"></a>Zakotwiczenia w wyrażeniach regularnych
Kotwice lub niepodzielne potwierdzenia o zerowej szerokości określ pozycję w ciągu, w którym musi wystąpić dopasowanie. Jeśli używasz zakotwiczenia w wyrażeniu wyszukiwania, aparat wyrażeń regularnych nie przechodzi przez ciąg znaków lub zużywają znaki; szuka dopasowania tylko w określonej pozycji. Na przykład `^` określa, że dopasowanie musi rozpocząć się na początku wiersza lub ciągu. W związku z `^http:` tym wyrażenie regularne pasuje do "http:" tylko wtedy, gdy występuje na początku wiersza. W poniższej tabeli wymieniono kotwice obsługiwane przez wyrażenia regularne w platformie .NET.  
  
|Kotwica|Opis|  
|------------|-----------------|  
|`^`|Domyślnie dopasowanie musi wystąpić na początku ciągu; w trybie wielowierszowym, musi występować na początku linii. Aby uzyskać więcej informacji, zobacz [Początek ciągu lub wiersza](#start-of-string-or-line-).|  
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu `\n` lub wcześniej na końcu ciągu; w trybie wielowierszowym musi występować na końcu `\n` linii lub wcześniej na końcu linii. Aby uzyskać więcej informacji, zobacz [Koniec ciągu lub wiersz](#end-of-string-or-line-).|  
|`\A`|Dopasowanie musi wystąpić tylko na początku ciągu (brak obsługi wielowierszowej). Aby uzyskać więcej informacji, zobacz [Początek tylko ciąg](#start-of-string-only-a).|  
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub `\n` wcześniej na końcu ciągu. Aby uzyskać więcej informacji, zobacz [Koniec ciągu lub Przed zakończeniem Newline](#end-of-string-or-before-ending-newline-z).|  
|`\z`|Dopasowanie musi wystąpić tylko na końcu ciągu. Aby uzyskać więcej informacji, zobacz [Tylko koniec ciągu](#end-of-string-only-z).|  
|`\G`|Mecz musi rozpocząć się od miejsca, w którym zakończył się poprzedni mecz. Aby uzyskać więcej informacji, zobacz [Mecze ciągłe](#contiguous-matches-g).|  
|`\b`|Dopasowanie musi wystąpić na granicy słowa. Aby uzyskać więcej informacji, zobacz [Granica programu Word](#word-boundary-b).|  
|`\B`|Dopasowanie nie może wystąpić na granicy słowa. Aby uzyskać więcej informacji, zobacz [Granica nieprogramu Word](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Początek ciągu lub wiersz: ^  
 Domyślnie kotwica `^` określa, że następujący wzorzec musi rozpoczynać się od pierwszej pozycji znaku ciągu. Jeśli używasz `^` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcją (zobacz [Opcje wyrażenia regularnego),](../../../docs/standard/base-types/regular-expression-options.md)dopasowanie musi nastąpić na początku każdego wiersza.  
  
 W poniższym `^` przykładzie użyto kotwicy w wyrażeniu regularnym, które wyodrębnia informacje o latach, w których niektóre profesjonalne drużyny baseballowe istniały. Przykład wywołuje dwa przeciążenia <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> przeciążenia znajduje tylko pierwszy podciąg w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego.  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> przeciążenia z `options` parametrem <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ustawionym na znalezienie wszystkich pięciu podciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Wzorzec `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu wejściowego (lub na początku wiersza, jeśli metoda jest wywoływana z opcją). <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>|  
|`((\w+(\s?)){2,}`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje zero lub jedno miejsce co najmniej dwa razy. Jest to pierwsza grupa przechwytywania. To wyrażenie definiuje również drugą i trzecią grupę przechwytywania: Drugi składa się z przechwyconego wyrazu, a trzeci składa się z przechwyconego odstępu.|  
|`,\s`|Dopasuj przecinek, po którym następuje znak odstępu.|  
|`(\w+\s\w+)`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje spacja, po której następuje jeden lub więcej znaków wyrazu. Jest to czwarta grupa przechwytywania.|  
|`,`|Dopasuj przecinek.|  
|`\s\d{4}`|Dopasuj spację, po której następują cztery cyfry dziesiętne.|  
|<code>(-(\d{4}&#124;present))?</code>|Dopasuj zero lub jedno wystąpienie łącznika, po którym następują cztery cyfry dziesiętne lub ciąg "obecny". Jest to szósta grupa przechwytywania. Obejmuje również siódmą grupę przechwytywania.|  
|`,?`|Dopasuj zero lub jedno wystąpienie przecinka.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Dopasuj jedno lub więcej wystąpień następujących elementów: spacje, cztery cyfry dziesiętne, zero lub jedno wystąpienie łącznika, po którym następują cztery cyfry dziesiętne lub ciąg "obecny" i zero lub jeden przecinek. Jest to piąta grupa przechwytywania.|

## <a name="end-of-string-or-line-"></a>Koniec ciągu lub linii: $  
 Kotwica `$` określa, że poprzedni wzorzec musi występować na `\n` końcu ciągu wejściowego lub wcześniej na końcu ciągu wejściowego.  
  
 Jeśli używasz `$` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcją, dopasowanie może również wystąpić na końcu wiersza. Należy `$` zauważyć, że pasuje, `\n` ale nie pasuje `\r\n` (kombinacja powrotu karetki i znaków newline lub CR/LF). Aby dopasować kombinację znaków CR/LF, dołącz `\r?$` do wzorca wyrażenia regularnego.  
  
 W poniższym `$` przykładzie dodano zakotwiczenie do wzorca wyrażenia regularnego użytego w przykładzie w sekcji [Początek ciągu lub wiersza.](#start-of-string-or-line-) W przypadku użycia z oryginalnym ciągiem wejściowym, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> który zawiera pięć wierszy tekstu, metoda nie może `$` znaleźć dopasowania, ponieważ koniec pierwszego wiersza nie pasuje do wzorca. Gdy oryginalny ciąg wejściowy jest dzielony <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> na tablicę ciągu, metoda powiedzie się w dopasowaniu każdego z pięciu wierszy. Gdy <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda jest wywoływana z parametrem ustawionym `options` na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nie znaleziono żadnych dopasowań, ponieważ wzorzec wyrażenia regularnego nie uwzględnia elementu zwracanego karetki (\u+000D). Jednak gdy wzorzec wyrażenia regularnego `$` `\r?$`jest modyfikowany przez zastąpienie , wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody z parametrem ustawionym `options` ponownie <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znajdzie pięć dopasowań.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Tylko początek ciągu: \A  
 Kotwica `\A` określa, że dopasowanie musi wystąpić na początku ciągu wejściowego. Jest identyczny `^` z zakotwiczeniem, z tą różnicą, `\A` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> że ignoruje tę opcję. W związku z tym może dopasować tylko początek pierwszego wiersza w wielowierszowym ciągu wejściowym.  
  
 Poniższy przykład jest podobny do przykładów dla `^` i `$` kotwic. Wykorzystuje kotwicę `\A` w wyrażeniu regularnym, które wyodrębnia informacje o latach, w których istniały niektóre profesjonalne drużyny baseballowe. Ciąg wejściowy zawiera pięć wierszy. Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody znajduje tylko pierwszy podciąg w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego. Jak pokazano w <xref:System.Text.RegularExpressions.RegexOptions.Multiline> przykładzie, opcja nie ma wpływu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Koniec ciągu lub przed zakończeniem nowego wiersza: \Z  
 Kotwica `\Z` określa, że dopasowanie musi wystąpić na końcu ciągu `\n` wejściowego lub wcześniej na końcu ciągu wejściowego. Jest identyczny `$` z zakotwiczeniem, z tą różnicą, `\Z` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> że ignoruje tę opcję. W związku z tym w ciągu wielowierszowym może odpowiadać tylko końcu `\n`ostatniego wiersza lub ostatniego wiersza przed .  
  
 Należy `\Z` pamiętać, że pasuje, `\n` ale nie pasuje `\r\n` (kombinacja znaków CR/LF). Aby dopasować CR/LF, uwzględnij `\r?\Z` wzorzec wyrażenia regularnego.  
  
 W poniższym `\Z` przykładzie użyto zakotwiczenia w wyrażeniu regularnym, które jest podobne do przykładu w sekcji [Start of String lub Line,](#start-of-string-or-line-) która wyodrębnia informacje o latach istnienia niektórych profesjonalnych drużyn baseballowych. Wyrażenie `\r?\Z` podrzędne w `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` wyrażeniu regularnym odpowiada końcu ciągu, `\n` a `\r\n`także pasuje do ciągu, który kończy się lub . W rezultacie każdy element w tablicy pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Tylko koniec ciągu: \z  
 Kotwica `\z` określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego. Podobnie `$` jak element `\z` języka, <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ignoruje opcję. W `\Z` przeciwieństwie do `\z` elementu języka `\n` nie pasuje do znaku na końcu ciągu. W związku z tym można dopasować tylko ostatni wiersz ciągu wejściowego.  
  
 W poniższym `\z` przykładzie użyto zakotwiczenia w wyrażeniu regularnym, które w przeciwnym razie jest identyczne z przykładem w poprzedniej sekcji, która wyodrębnia informacje o latach, w których istniały niektóre profesjonalne drużyny baseballowe. Przykład próbuje dopasować każdy z pięciu elementów w tablicy `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`ciągu do wzorca wyrażenia regularnego . Dwa ciągi kończą się znakiem powrotu karetki i wysuwu wiersza, jeden kończy się znakiem wysuwu wiersza, a dwa kończą się ani zwrotem karetki, ani znakiem wysuwu wiersza. Jak pokazuje dane wyjściowe, tylko ciągi bez powrotu karetki lub znak wysuwu wiersza odpowiadają wzorcowi.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Ciągłe dopasowanie: \G  
 Zakotwiczenie `\G` określa, że dopasowanie musi wystąpić w punkcie, w którym zakończył się poprzedni mecz. Korzystając z tej kotwicy z <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody, zapewnia, że wszystkie dopasowania są ciągłe.  
  
 W poniższym przykładzie użyto wyrażenia regularnego do wyodrębnienia nazw gatunków gryzoni z ciągu rozdzielanego przecinkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Wyrażenie `\G(\w+\s?\w*),?` regularne jest interpretowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij od miejsca, w którym zakończył się ostatni mecz.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\s?`|Dopasuj zero lub jedno miejsce.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`(\w+\s?\w*)`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje zero lub jedno miejsce, po którym następuje zero lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`,?`|Dopasuj zero lub jedno wystąpienie znaku przecinka literału.|

## <a name="word-boundary-b"></a>Wyszukiwanie granicy wyrazów: \b  
 Zakotwiczenie `\b` określa, że dopasowanie musi występować na `\w` granicy między znakiem wyrazu (elementem języka) a znakiem nie-word (elementem `\W` języka). Znaki wyrazów składają się ze znaków alfanumerycznych i podkreśleń; znak niebędący wyrazem to dowolny znak, który nie jest alfanumeryczny ani podkreślony. (Aby uzyskać więcej informacji, zobacz [Klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Dopasowanie może również wystąpić na granicy słowa na początku lub na końcu ciągu.  
  
 Zakotwiczenie `\b` jest często używane w celu zapewnienia, że wyrażenie podrzędne pasuje do całego wyrazu, a nie tylko początku lub końca wyrazu. Wyrażenie `\bare\w*\b` regularne w poniższym przykładzie ilustruje to użycie. Pasuje do dowolnego wyrazu, który zaczyna się od podciągu "są". Dane wyjściowe z przykładu `\b` również ilustruje, że pasuje zarówno początku i na końcu ciągu wejściowego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`are`|Dopasuj podciąg "są".|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  

## <a name="non-word-boundary-b"></a>Brak wyszukiwania granicy wyrazów: \B  
 Zakotwiczenie `\B` określa, że dopasowanie nie może występować na granicy słowa. Jest przeciwieństwem kotwicy. `\b`  
  
 W poniższym `\B` przykładzie użyto zakotwiczenia do zlokalizowania wystąpień podciągu "qu" w słowie. Wzorzec `\Bqu\w+` wyrażenia regularnego pasuje do podciągu, który zaczyna się od "qu", który nie uruchamia wyrazu i który jest kontynuowany do końca wyrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\B`|Nie rozpoczynaj dopasowania na granicy słowa.|  
|`qu`|Dopasuj podciąg "qu".|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
