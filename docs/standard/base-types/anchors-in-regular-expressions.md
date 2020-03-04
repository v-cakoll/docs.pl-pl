---
title: Kotwice w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak używać kotwic w wzorcach wyrażeń regularnych.
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159666"
---
# <a name="anchors-in-regular-expressions"></a>Zakotwiczenia w wyrażeniach regularnych
Kotwice lub niepodzielne potwierdzenia zerowej szerokości, określ pozycję w ciągu, w którym musi wystąpić dopasowanie. Gdy używasz kotwicy w wyrażeniu wyszukiwania, aparat wyrażeń regularnych nie przeprowadzi przechodzenia przez ciąg lub zużywa znaki; szuka dopasowania tylko w określonej pozycji. Na przykład `^` określa, że dopasowanie musi rozpoczynać się na początku wiersza lub ciągu. Dlatego wyrażenie regularne `^http:` dopasowuje wartość "http:" tylko wtedy, gdy występuje na początku wiersza. W poniższej tabeli wymieniono kotwice obsługiwane przez wyrażenia regularne w programie .NET.  
  
|Kotwica|Opis|  
|------------|-----------------|  
|`^`|Domyślnie dopasowanie musi wystąpić na początku ciągu znaków. w trybie wielowierszowym musi wystąpić na początku wiersza. Aby uzyskać więcej informacji, zobacz [początek ciągu lub wiersza](#start-of-string-or-line-).|  
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu; w trybie wielowierszowym, musi wystąpić na końcu wiersza lub przed `\n` na końcu wiersza. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub wiersza](#end-of-string-or-line-).|  
|`\A`|Dopasowanie musi wystąpić na początku ciągu znaków (bez obsługi wielu wierszy). Aby uzyskać więcej informacji, zobacz [początek ciągu](#start-of-string-only-a).|  
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub przed końcowym znakiem nowego wiersza](#end-of-string-or-before-ending-newline-z).|  
|`\z`|Dopasowanie musi wystąpić na końcu ciągu. Aby uzyskać więcej informacji, zobacz [koniec ciągu](#end-of-string-only-z).|  
|`\G`|Dopasowanie musi rozpoczynać się w miejscu, w którym zakończono poprzednie dopasowanie. Aby uzyskać więcej informacji, zobacz [przyległe dopasowania](#contiguous-matches-g).|  
|`\b`|Dopasowanie musi wystąpić na granicy słowa. Aby uzyskać więcej informacji, zobacz [granica wyrazu](#word-boundary-b).|  
|`\B`|Dopasowanie nie może wystąpić na granicy słowa. Aby uzyskać więcej informacji, zobacz granica niebędąca [słowem](#non-word-boundary-b).|  

## <a name="start-of-string-or-line-"></a>Początek ciągu lub wiersz: ^  
 Domyślnie kotwica `^` określa, że następujący wzorzec musi rozpoczynać się od pierwszego pozycji znaku ciągu. Jeśli używasz `^` z opcją <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> (zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md)), dopasowanie musi wystąpić na początku każdego wiersza.  
  
 Poniższy przykład używa kotwicy `^` w wyrażeniu regularnym, który wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Przykład wywołuje dwa przeciążenia metody <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>:  
  
- Wywołanie przeciążenia <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> umożliwia znalezienie tylko pierwszego podciągu w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego.  
  
- Wywołanie przeciążenia <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> z parametrem `options` ustawionym na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> odnajdzie wszystkie pięć podciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu wejściowego (lub początku wiersza, jeśli metoda jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>).|  
|`((\w+(\s?)){2,}`|Dopasowuje jeden lub więcej znaków słowa, po których następuje zero lub jedno miejsce co najmniej dwa razy. Jest to pierwsza grupa przechwytywania. To wyrażenie definiuje również drugą i trzecią grupę przechwytywania: druga składa się z przechwyconego wyrazu, a trzecia składa się z przechwyconego białego znaku.|  
|`,\s`|Dopasowuje przecinek, po którym następuje znak odstępu.|  
|`(\w+\s\w+)`|Dopasowuje co najmniej jeden znak słowa, po którym następuje spacja, po którym następuje jeden lub więcej znaków wyrazu. Jest to czwarta grupa przechwytywania.|  
|`,`|Dopasowuje przecinek.|  
|`\s\d{4}`|Dopasowuje miejsce, po którym następuje cztery cyfry dziesiętne.|  
|<code>(-(\d{4}&#124;present))?</code>|Dopasowanie do zera lub jednego wystąpienia łącznika, po którym następuje cztery cyfry dziesiętne lub ciąg "obecny". To jest szósta grupa przechwytywania. Obejmuje również siódmą grupę przechwytywania.|  
|`,?`|Dopasowanie do zera lub jednego wystąpienia przecinka.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Dopasowuje jedno lub więcej wystąpień następujących elementów: spacja, cztery cyfry dziesiętne, zero lub jedno wystąpienie łącznika, po którym następuje cztery cyfry dziesiętne lub ciąg "obecny" oraz zero lub jeden przecinek. To jest piąta grupa przechwytywania.|

## <a name="end-of-string-or-line-"></a>Koniec ciągu lub linii: $  
 Zakotwiczenie `$` określa, że poprzedzający wzorzec musi wystąpić na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego.  
  
 Jeśli używasz `$` z opcją <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, dopasowanie może również wystąpić na końcu wiersza. Należy zauważyć, że `$` dopasowuje `\n`, ale nie pasuje do `\r\n` (kombinacji znaku powrotu karetki i znaków nowego wiersza lub CR/LF). Aby dopasować kombinację znaków CR/LF, Uwzględnij `\r?$` we wzorcu wyrażenia regularnego.  
  
 Poniższy przykład dodaje kotwicę `$` do wzorca wyrażenia regularnego użytego w przykładzie w sekcji [początku ciągu lub wiersza](#start-of-string-or-line-) . Gdy jest używany z oryginalnym ciągiem wejściowym, który zawiera pięć wierszy tekstu, Metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> nie może znaleźć dopasowania, ponieważ koniec pierwszego wiersza nie jest zgodny ze wzorcem `$`. Gdy pierwotny ciąg wejściowy jest podzielony na tablicę ciągów, Metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> pomyślnie pasuje do każdego z pięciu wierszy. Gdy metoda <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> jest wywoływana z parametrem `options` ustawionym na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nie znaleziono żadnych dopasowań, ponieważ wzorzec wyrażenia regularnego nie jest kontem dla elementu powrotu karetki (\u + 000D). Jeśli jednak wzorzec wyrażenia regularnego jest modyfikowany przez zastępowanie `$` z `\r?$`, wywołanie metody <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> z parametrem `options` ustawionym na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> spowoduje ponowne znalezienie pięciu dopasowań.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]

## <a name="start-of-string-only-a"></a>Tylko początek ciągu: \A  
 Zakotwiczenie `\A` określa, że dopasowanie musi wystąpić na początku ciągu wejściowego. Jest ona identyczna z zakotwiczeniem `^`, z tą różnicą, że `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym można dopasować tylko początek pierwszego wiersza w wielowierszowym ciągu wejściowym.  
  
 Poniższy przykład jest podobny do przykładów dla zakotwiczenia `^` i `$`. Używa kotwicy `\A` w wyrażeniu regularnym, który wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Ciąg wejściowy zawiera pięć wierszy. Wywołanie metody <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> powoduje znalezienie tylko pierwszego podciągu w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego. Jak pokazano w przykładzie, opcja <xref:System.Text.RegularExpressions.RegexOptions.Multiline> nie ma żadnego wpływu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]

## <a name="end-of-string-or-before-ending-newline-z"></a>Koniec ciągu lub przed zakończeniem nowego wiersza: \Z  
 Zakotwiczenie `\Z` określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego. Jest ona identyczna z zakotwiczeniem `$`, z tą różnicą, że `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym w ciągu wielowierszowym można dopasować tylko koniec ostatniego wiersza lub ostatni wiersz przed `\n`.  
  
 Należy zauważyć, że `\Z` pasuje do `\n`, ale nie pasuje do `\r\n` (kombinacja znaków CR/LF). Aby dopasować znaki CR/LF, Uwzględnij `\r?\Z` we wzorcu wyrażenia regularnego.  
  
 Poniższy przykład używa kotwicy `\Z` w wyrażeniu regularnym podobnym do przykładu w sekcji [początku ciągu lub wiersza](#start-of-string-or-line-) , który wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Podwyrażenie `\r?\Z` w wyrażeniu regularnym `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` dopasowuje koniec ciągu, a także dopasowuje ciąg kończący się na `\n` lub `\r\n`. W związku z tym każdy element w tablicy jest zgodny ze wzorcem wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]

## <a name="end-of-string-only-z"></a>Tylko koniec ciągu: \z  
 Zakotwiczenie `\z` określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego. Podobnie jak `$` element języka `\z` ignoruje opcję <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. W przeciwieństwie do `\Z` elementu języka `\z` nie pasuje do znaku `\n` na końcu ciągu. W związku z tym może pasować tylko do ostatniego wiersza ciągu wejściowego.  
  
 W poniższym przykładzie pokazano kotwicę `\z` w wyrażeniu regularnym, która jest identyczna z przykładem w poprzedniej sekcji, która wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Przykład próbuje dopasować każdy z pięciu elementów w tablicy ciągów z wzorcem wyrażenia regularnego `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Dwa z ciągów kończą się znakiem powrotu karetki i znakami wysuwu wiersza, jednym końcem znaku wysuwu wiersza i dwoma końcami bez znaku powrotu karetki ani znakiem wysuwu wiersza. Ponieważ dane wyjściowe są wyświetlane, tylko ciągi bez znaku powrotu karetki lub wysuwu wiersza pasują do wzorca.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]

## <a name="contiguous-matches-g"></a>Ciągłe dopasowanie: \G  
 Zakotwiczenie `\G` określa, że dopasowanie musi wystąpić w punkcie, w którym zakończono poprzednie dopasowanie. Gdy używasz tej kotwicy z metodą <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>, gwarantuje to, że wszystkie dopasowania są ciągłe.  
  
 Poniższy przykład używa wyrażenia regularnego do wyodrębniania nazw gatunków gryzoni z ciągu rozdzielanego przecinkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Wyrażenie regularne `\G(\w+\s?\w*),?` jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\G`|Zacznij od zakończenia ostatniego dopasowania.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\s?`|Dopasowanie do zera lub jednego miejsca.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`(\w+\s?\w*)`|Dopasowuje co najmniej jeden znak słowa, po którym następuje zero lub jeden znak, po którym następuje zero lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`,?`|Dopasowanie do zera lub jednego wystąpienia znaku przecinka literału.|

## <a name="word-boundary-b"></a>Wyszukiwanie granicy wyrazów: \b  
 Zakotwiczenie `\b` określa, że dopasowanie musi wystąpić na granicy między znakiem słowa (element języka `\w`) i znakiem niezawierającym wyrazu (`\W` elementu języka). Znaki słowa składają się z znaków alfanumerycznych i podkreśleń; znak inny niż słowo jest dowolnym znakiem, który nie jest alfanumeryczny ani podkreśleniem. (Aby uzyskać więcej informacji, zobacz [klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)). Dopasowanie może również wystąpić na granicy wyrazu na początku lub na końcu ciągu.  
  
 Kotwica `\b` jest często używana do upewnienia się, że Podwyrażenie pasuje do całego wyrazu, a nie tylko początku lub końca wyrazu. W poniższym przykładzie wyrażenie regularne `\bare\w*\b` ilustruje to użycie. Dopasowuje wszystkie słowa zaczynające się od podciągu "są". Wynik z przykładu ilustruje również, że `\b` dopasowuje zarówno początek, jak i koniec ciągu wejściowego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`are`|Dopasowuje podciąg "są".|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  

## <a name="non-word-boundary-b"></a>Brak wyszukiwania granicy wyrazów: \B  
 Zakotwiczenie `\B` określa, że dopasowanie nie może wystąpić na granicy słowa. Jest przeciwieństwem zakotwiczenia `\b`.  
  
 Poniższy przykład używa kotwicy `\B`, aby zlokalizować wystąpienia podciągu "Qu" w słowie. Wzorzec wyrażenia regularnego `\Bqu\w+` pasuje do podciągu rozpoczynającego się od "Qu", który nie uruchamia słowa i który jest nadal kończący się na końcu wyrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\B`|Nie rozpoczynaj dopasowania na granicy wyrazu.|  
|`qu`|Dopasowuje podciąg "Qu".|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
