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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 5f722977928604e5876e52a7329eef5c933bf2a7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046469"
---
# <a name="anchors-in-regular-expressions"></a>Zakotwiczenia w wyrażeniach regularnych
<a name="top"></a>Kotwice lub niepodzielne potwierdzenia zerowej szerokości, określ pozycję w ciągu, w którym musi wystąpić dopasowanie. Gdy używasz kotwicy w wyrażeniu wyszukiwania, aparat wyrażeń regularnych nie przeprowadzi przechodzenia przez ciąg lub zużywa znaki; szuka dopasowania tylko w określonej pozycji. Na przykład `^` określa, że dopasowanie musi rozpoczynać się na początku wiersza lub ciągu. W związku z tym wyrażenie `^http:` regularne dopasowuje wartość "http:" tylko wtedy, gdy występuje na początku wiersza. W poniższej tabeli wymieniono kotwice obsługiwane przez wyrażenia regularne w programie .NET.  
  
|Kotwica|Opis|  
|------------|-----------------|  
|`^`|Domyślnie dopasowanie musi wystąpić na początku ciągu znaków. w trybie wielowierszowym musi wystąpić na początku wiersza. Aby uzyskać więcej informacji, zobacz [początek ciągu lub wiersza](#Start).|  
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu lub przed `\n` końcem ciągu; w trybie wielowierszowym, musi wystąpić na końcu wiersza lub przed `\n` końcem wiersza. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub wiersza](#End).|  
|`\A`|Dopasowanie musi wystąpić na początku ciągu znaków (bez obsługi wielu wierszy). Aby uzyskać więcej informacji, zobacz [początek ciągu](#StartOnly).|  
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub przed `\n` końcem ciągu. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub przed końcowym znakiem nowego wiersza](#EndOrNOnly).|  
|`\z`|Dopasowanie musi wystąpić na końcu ciągu. Aby uzyskać więcej informacji, zobacz [koniec ciągu](#EndOnly).|  
|`\G`|Dopasowanie musi rozpoczynać się w miejscu, w którym zakończono poprzednie dopasowanie. Aby uzyskać więcej informacji, zobacz [przyległe dopasowania](#Contiguous).|  
|`\b`|Dopasowanie musi wystąpić na granicy słowa. Aby uzyskać więcej informacji, [](#WordBoundary)Zobacz granica wyrazu.|  
|`\B`|Dopasowanie nie może wystąpić na granicy słowa. Aby uzyskać więcej informacji, [](#NonwordBoundary)Zobacz granica niebędąca słowem.|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Początek ciągu lub wiersz: ^  
 Domyślnie `^` kotwica określa, że następujący wzorzec musi rozpoczynać się od pierwszego położenia znaku w ciągu. Jeśli używasz `^` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> z opcją (zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md)), dopasowanie musi wystąpić na początku każdego wiersza.  
  
 Poniższy przykład używa `^` kotwicy w wyrażeniu regularnym, która wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Przykład wywołuje dwa przeciążenia <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> przeciążenia znajduje tylko pierwszy podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego.  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> przeciążenia `options` z parametrem ustawionym na Znajdź wszystkie pięć podciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Wzorzec `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu wejściowego (lub początku wiersza, jeśli metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcją).|  
|`((\w+(\s?)){2,}`|Dopasowuje jeden lub więcej znaków słowa, po których następuje zero lub jedno miejsce co najmniej dwa razy. Jest to pierwsza grupa przechwytywania. To wyrażenie definiuje również drugą i trzecią grupę przechwytywania: Druga składa się z przechwyconego wyrazu, a trzecia składa się z przechwyconych białych znaków.|  
|`,\s`|Dopasowuje przecinek, po którym następuje znak odstępu.|  
|`(\w+\s\w+)`|Dopasowuje co najmniej jeden znak słowa, po którym następuje spacja, po którym następuje jeden lub więcej znaków wyrazu. Jest to czwarta grupa przechwytywania.|  
|`,`|Dopasowuje przecinek.|  
|`\s\d{4}`|Dopasowuje miejsce, po którym następuje cztery cyfry dziesiętne.|  
|<code>(-(\d{4}&#124;present))?</code>|Dopasowanie do zera lub jednego wystąpienia łącznika, po którym następuje cztery cyfry dziesiętne lub ciąg "obecny". To jest szósta grupa przechwytywania. Obejmuje również siódmą grupę przechwytywania.|  
|`,?`|Dopasowanie do zera lub jednego wystąpienia przecinka.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Dopasowuje jedno lub więcej wystąpień następujących elementów: spacja, cztery cyfry dziesiętne, zero lub jedno wystąpienie łącznika, po którym następuje cztery cyfry dziesiętne lub ciąg "obecny" oraz zero lub jeden przecinek. To jest piąta grupa przechwytywania.|  
  
 [Powrót do początku](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Koniec ciągu lub linii: $  
 Zakotwiczenie określa, że poprzedzający wzorzec musi wystąpić na końcu ciągu wejściowego lub przed `\n` końcem ciągu wejściowego. `$`  
  
 Jeśli używasz `$` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> z opcją, dopasowanie może również wystąpić na końcu wiersza. Należy zauważyć `$` , `\n` że pasują do `\r\n` siebie, ale nie pasują do siebie (kombinacji znaku powrotu karetki i znaków nowego wiersza lub CR/LF). Aby dopasować kombinację znaków CR/LF, Dołącz `\r?$` do wzorca wyrażenia regularnego.  
  
 Poniższy przykład dodaje `$` kotwicę do wzorca wyrażenia regularnego użytego w przykładzie w sekcji [początku ciągu lub wiersza](#Start) . Gdy jest używany z oryginalnym ciągiem wejściowym, który zawiera pięć wierszy tekstu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> Metoda nie może znaleźć dopasowania, ponieważ koniec pierwszego wiersza nie jest zgodny ze `$` wzorcem. Gdy pierwotny ciąg wejściowy jest podzielony na tablicę ciągów, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda pomyślnie pasuje do każdego z pięciu wierszy. Gdy metoda jest wywoływana `options` z parametrem ustawionym na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nie znaleziono dopasowań, ponieważ wzorzec wyrażenia regularnego nie jest kontem dla elementu powrotu karetki (\u + 000D). <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> Jeśli jednak wzorzec wyrażenia regularnego jest modyfikowany przez zastąpienie `$` przy `\r?$`użyciu, `options` wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody z parametrem ustawionym <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> na ponownie powoduje znalezienie pięciu dopasowań.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Tylko początek ciągu: \A  
 `\A` Zakotwiczenie określa, że dopasowanie musi wystąpić na początku ciągu wejściowego. Jest ona identyczna `^` z zakotwiczeniem, z tą <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> różnicą, że `\A` ignoruje opcję. W związku z tym można dopasować tylko początek pierwszego wiersza w wielowierszowym ciągu wejściowym.  
  
 Poniższy przykład jest podobny do przykładów dla `^` kotwic i. `$` Używa `\A` kotwicy w wyrażeniu regularnym, która wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Ciąg wejściowy zawiera pięć wierszy. Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody znajduje tylko pierwszy podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego. Jak pokazano w przykładzie, <xref:System.Text.RegularExpressions.RegexOptions.Multiline> opcja nie ma żadnego wpływu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Koniec ciągu lub przed zakończeniem nowego wiersza: \Z  
 Zakotwiczenie określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego lub przed `\n` końcem ciągu wejściowego. `\Z` Jest ona identyczna `$` z zakotwiczeniem, z tą <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> różnicą, że `\Z` ignoruje opcję. W związku z tym w ciągu wielowierszowym można dopasować tylko koniec ostatniego wiersza lub ostatni wiersz przed `\n`.  
  
 Należy zauważyć `\Z` , `\n` że pasują do `\r\n` siebie, ale nie są zgodne (kombinacja znaków CR/LF). Aby dopasować znaki CR/LF, `\r?\Z` Dołącz do wzorca wyrażenia regularnego.  
  
 Poniższy przykład używa `\Z` kotwicy w wyrażeniu regularnym podobnym do przykładu w sekcji [początku ciągu lub wiersza](#Start) , który wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Podwyrażenie `\r?\Z` w wyrażeniu `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` regularnym dopasowuje koniec ciągu, a także dopasowuje ciąg kończący się znakiem `\n` or `\r\n`. W związku z tym każdy element w tablicy jest zgodny ze wzorcem wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Tylko koniec ciągu: \z  
 `\z` Zakotwiczenie określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego. Podobnie jak element <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> `\z` `$` języka, ignoruje opcję. W przeciwieństwie `\Z` do `\z` elementu języka nie pasuje do `\n` znaku na końcu ciągu. W związku z tym może pasować tylko do ostatniego wiersza ciągu wejściowego.  
  
 Poniższy przykład używa `\z` kotwicy w wyrażeniu regularnym, która jest inna niż w przypadku przykładu w poprzedniej sekcji, która wyodrębnia informacje o latach, w których istniały niektóre profesjonalne zespoły siatkówki. Przykład próbuje dopasować każdy z pięciu elementów w tablicy ciągów z wzorcem `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`wyrażenia regularnego. Dwa z ciągów kończą się znakiem powrotu karetki i znakami wysuwu wiersza, jednym końcem znaku wysuwu wiersza i dwoma końcami bez znaku powrotu karetki ani znakiem wysuwu wiersza. Ponieważ dane wyjściowe są wyświetlane, tylko ciągi bez znaku powrotu karetki lub wysuwu wiersza pasują do wzorca.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Powrót do początku](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Ciągłe dopasowanie: \G  
 `\G` Zakotwiczenie określa, że dopasowanie musi wystąpić w punkcie, w którym zakończono poprzednie dopasowanie. Gdy używasz tej kotwicy przy użyciu <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody lub <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> , gwarantuje to, że wszystkie dopasowania są ciągłe.  
  
 Poniższy przykład używa wyrażenia regularnego do wyodrębniania nazw gatunków gryzoni z ciągu rozdzielanego przecinkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Wyrażenie `\G(\w+\s?\w*),?` regularne jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Zacznij od zakończenia ostatniego dopasowania.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\s?`|Dopasowanie do zera lub jednego miejsca.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`(\w+\s?\w*)`|Dopasowuje co najmniej jeden znak słowa, po którym następuje zero lub jeden znak, po którym następuje zero lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`,?`|Dopasowanie do zera lub jednego wystąpienia znaku przecinka literału.|  
  
 [Powrót do początku](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Wyszukiwanie granicy wyrazów: \b  
 Zakotwiczenie określa, że dopasowanie musi wystąpić na granicy między znakiem słowa `\w` (elementem języka) i znakiem niezawierającym wyrazu ( `\W` element języka). `\b` Znaki słowa składają się z znaków alfanumerycznych i podkreśleń; znak inny niż słowo jest dowolnym znakiem, który nie jest alfanumeryczny ani podkreśleniem. (Aby uzyskać więcej informacji, zobacz [klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)). Dopasowanie może również wystąpić na granicy wyrazu na początku lub na końcu ciągu.  
  
 `\b` Zakotwiczenie jest często używane, aby upewnić się, że Podwyrażenie pasuje do całego wyrazu, a nie tylko początku lub końca wyrazu. W poniższym przykładzie `\bare\w*\b` wyrażenie regularne ilustruje to użycie. Dopasowuje wszystkie słowa zaczynające się od podciągu "są". Wynik z przykładu ilustruje także, że `\b` dopasowuje zarówno początek, jak i koniec ciągu wejściowego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`are`|Dopasowuje podciąg "są".|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Brak wyszukiwania granicy wyrazów: \B  
 `\B` Kotwica określa, że dopasowanie nie może wystąpić na granicy słowa. Jest przeciwieństwem `\b` zakotwiczenia.  
  
 Poniższy przykład używa `\B` kotwicy do lokalizowania wystąpień podciągu "Qu" w słowie. Wzorzec `\Bqu\w+` wyrażenia regularnego pasuje do podciągu rozpoczynającego się od znaku "Qu", który nie rozpoczyna się od słowa i który jest nadal kończący się na końcu wyrazu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\B`|Nie rozpoczynaj dopasowania na granicy wyrazu.|  
|`qu`|Dopasowuje podciąg "Qu".|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
