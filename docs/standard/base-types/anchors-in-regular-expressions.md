---
title: Kotwice w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak używać kotwic we wzorcach wyrażeń regularnych.
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
ms.openlocfilehash: f0e42c0032dc6f9dac0895a29db9de79547c0a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698892"
---
# <a name="anchors-in-regular-expressions"></a>Zakotwiczenia w wyrażeniach regularnych
<a name="top"></a> Kotwice lub atomic asercjami o zerowej szerokości, należy określić pozycja w ciągu, w którym dopasowanie musi wystąpić. Korzystając z elementu zakotwiczenia w wyrażeniu wyszukiwania, aparat wyrażeń regularnych nie przechodzi ciągu lub używa znaków; Wyszukuje dopasowania w określonej pozycji. Na przykład `^` Określa, że dopasowanie musi rozpoczynać się na początku wiersza lub ciągu. W związku z tym, wyrażenie regularne `^http:` pasuje do "http:" tylko wtedy, gdy wystąpi go na początku wiersza. W poniższej tabeli wymieniono kotwic obsługiwane przez wyrażenia regularne w .NET.  
  
|Kotwica|Opis|  
|------------|-----------------|  
|`^`|Domyślnie dopasowanie musi wystąpić na początku ciągu; w tryb wielowierszowy musi wystąpić na początku wiersza. Aby uzyskać więcej informacji, zobacz [Start ciągu lub linii](#Start).|  
|`$`|Domyślnie dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu; w tryb wielowierszowy musi wystąpić na końcu linii lub przed `\n` na końcu wiersza. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub linii](#End).|  
|`\A`|Dopasowanie musi wystąpić na początku tylko ciągi (bez obsługi wielowierszowy). Aby uzyskać więcej informacji, zobacz [Start z ciągu tylko](#StartOnly).|  
|`\Z`|Dopasowanie musi wystąpić na końcu ciągu lub przed `\n` na końcu ciągu. Aby uzyskać więcej informacji, zobacz [koniec ciągu lub przed Kończenie znakami nowego wiersza](#EndOrNOnly).|  
|`\z`|Dopasowanie musi wystąpić na końcu tylko ciągi. Aby uzyskać więcej informacji, zobacz [zakończenia z ciągu tylko](#EndOnly).|  
|`\G`|Dopasowanie musi rozpoczynać się w miejscu, gdzie kończy się poprzednie dopasowanie. Aby uzyskać więcej informacji, zobacz [ciągłe](#Contiguous).|  
|`\b`|Dopasowanie musi wystąpić na granicy wyrazu. Aby uzyskać więcej informacji, zobacz [granicy słowa](#WordBoundary).|  
|`\B`|Dopasowanie nie musi wystąpić na granicy wyrazu. Aby uzyskać więcej informacji, zobacz [granicy słowa inne niż](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Początek ciągu lub wiersz: ^  
 Domyślnie `^` zakotwiczenia określa, że następujący wzorzec musi rozpoczynać się od pierwszego pozycji znaku w ciągu. Jeśli używasz `^` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji (zobacz [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md)), dopasowanie musi wystąpić na początku każdego wiersza.  
  
 W poniższym przykładzie użyto `^` zakotwiczenia w wyrażeniach regularnych, która wyodrębnia informacje o lat, podczas których niektóre zespoły profesjonalnych mecz istniał. Przykład wywołuje dwa przeciążenia metody <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> przeciążenie umożliwia znalezienie pierwszego podciągu w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego.  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> przeciążenia z `options` parametr <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znajdzie wszystkie pięć podciągi.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Dopasowanie musi przypadać na początku ciągu wejściowego (lub na początku wiersza, jeśli metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji).|  
|`((\w+(\s?)){2,}`|Dopasowuje co najmniej jeden znak słowa, a następnie przez zero lub jedną spację dokładnie dwa razy. Jest to pierwsza grupa przechwytywania. To wyrażenie definiuje również druga i trzecia grupa przechwytywania: Drugi składa się z przechwyconych programu word, a trzeci składa się z przechwyconych miejsca do magazynowania.|  
|`,\s`|Dopasowuje przecinek następuje znak odstępu.|  
|`(\w+\s\w+)`|Dopasowuje co najmniej jeden znak słowa, spację, następuje jeden lub więcej znaków słowa. Jest to czwarty grupa przechwytywania.|  
|`,`|Odpowiada wartości przecinkami.|  
|`\s\d{4}`|Dopasowanie do miejsca, następuje czterem cyfrom po przecinku.|  
|<code>(-(\d{4}&#124;present))?</code>|Dopasowuje zero lub jeden wystąpienie łącznika następują cztery cyfry dziesiętne lub ciąg "obecne". To jest szóstego grupa przechwytywania. Zawiera on również siódmego grupa przechwytywania.|  
|`,?`|Wystąpienie Dopasuj zero lub jeden przecinek.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Zgodne z co najmniej jedno z następujących czynności: spację, czterem cyfrom po przecinku, zera lub jednego wystąpienia z łącznikiem następuje czterem cyfrom po przecinku lub ciąg "obecny" oraz zero lub jeden przecinek. Jest to piąty grupa przechwytywania.|  
  
 [Powrót do początku](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Koniec ciągu lub linii: $  
 `$` Zakotwiczenia określa, że poprzedni wzorzec musi wystąpić na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego.  
  
 Jeśli używasz `$` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcję dopasowanie może również wystąpić na końcu wiersza. Należy pamiętać, że `$` odpowiada `\n` , ale nie pasuje `\r\n` (kombinację karetki return i znaki nowego wiersza lub CR/LF). Aby dopasować kombinacji znaków CR/LF, obejmują `\r?$` we wzorcu wyrażenia regularnego.  
  
 W poniższym przykładzie dodano `$` kotwicy na wzorcu wyrażenia regularnego użytego w przykładzie w [Start ciągu lub linii](#Start) sekcji. Gdy jest używane z oryginalnego ciągu wejściowego, który zawiera pięć wierszy tekstu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> — metoda nie może odnaleźć dopasowania, ponieważ nie są zgodne w końcu pierwszego wiersza `$` wzorca. Gdy oryginalny ciąg wejściowy jest podzielony na tablicę ciągów, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda zakończy się pomyślnie w dopasowywania wszystkich pięciu wierszach. Gdy <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda jest wywoływana z `options` parametr <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, nie znaleziono żadnych dopasowań, ponieważ wzorzec wyrażenia regularnego nie uwzględniać return elementu powrotu karetki (\u+000D). Jednak, gdy wzorzec wyrażenia regularnego jest modyfikowany przez zastąpienie `$` z `\r?$`, wywoływania <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody z `options` parametr <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ponownie znajduje się pięć dopasowań.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Tylko początek ciągu: \A  
 `\A` Zakotwiczenia określa, że dopasowanie musi wystąpić na początku ciągu wejściowego. Jest on identyczny `^` zakotwiczyć, chyba że `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym może wyłącznie odpowiadać początek pierwszy wiersz w wielowierszowy ciąg wejściowy.  
  
 Poniższy przykład jest podobny do przykładów dla `^` i `$` zakotwiczenia. Używa ona `\A` zakotwiczenia w wyrażeniach regularnych, która wyodrębnia informacje o lat, podczas których niektóre zespoły profesjonalnych mecz istniał. Ciąg wejściowy zawiera pięć wierszy. Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda znajdzie pierwszego podciągu w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego. Jak pokazano w przykładzie <xref:System.Text.RegularExpressions.RegexOptions.Multiline> opcja nie ma wpływu.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Koniec ciągu lub przed zakończeniem nowego wiersza: \Z  
 `\Z` Zakotwiczenia określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego. Jest on identyczny `$` zakotwiczyć, chyba że `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym, w wielowierszowy ciąg je mogą tylko odnosić się do końca ostatni wiersz lub ostatni wiersz przed `\n`.  
  
 Należy pamiętać, że `\Z` odpowiada `\n` , ale nie pasuje `\r\n` (kombinacji znaków CR/LF). Aby dopasować CR/LF, obejmują `\r?\Z` we wzorcu wyrażenia regularnego.  
  
 W poniższym przykładzie użyto `\Z` zakotwiczenia w wyrażeniach regularnych, która jest podobna do przykładu w [Start ciągu lub linii](#Start) sekcji, która wyodrębnia informacje o lat, podczas której niektóre mecz professional zespoły istniał. Podwyrażenie `\r?\Z` w wyrażeniu regularnym `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` pasuje do końca ciągu, a także pasuje do ciągu, która kończy się `\n` lub `\r\n`. W rezultacie każdy element w tablicy pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Tylko koniec ciągu: \z  
 `\z` Zakotwiczenia określa, że dopasowanie musi wystąpić na końcu ciągu wejściowego. Podobnie jak `$` element języka `\z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W odróżnieniu od `\Z` element języka `\z` nie odpowiada `\n` znak na końcu ciągu. W związku z tym może wyłącznie odpowiadać ostatni wiersz w ciągu wejściowym.  
  
 W poniższym przykładzie użyto `\z` zakotwiczenia w wyrażeniach regularnych, które w przeciwnym razie jest taka sama jak w przykładzie w poprzedniej sekcji, która wyodrębnia informacje o lat, podczas których niektóre zespoły profesjonalnych mecz istniał. Przykład podejmuje próbę dopasowania wszystkich pięć kolejnych elementów w tablicy ciągów z wzorcem wyrażenia regularnego `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Zwraca dwa ciągi kończyć powrotu karetki i znaki wysuwu wiersza, zakończy się znak nowego wiersza i zwraca karetki ani kończyć się w dwóch ani znak wysuwu wiersza. Dane wyjściowe pokazują, zwracać tylko ciągi bez znaków powrotu karetki lub wysuwu wiersza dopasowania znaku wzorca.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Powrót do początku](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Ciągłe dopasowanie: \G  
 `\G` Zakotwiczenia określa, że dopasowanie musi wystąpić w punkcie, w którym kończy się poprzednie dopasowanie. Kiedy używać tego zakotwiczenia z <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody go gwarantuje, że wszystkie dopasowania będą ciągłe.  
  
 W poniższym przykładzie użyto wyrażenia regularnego można wyodrębnić nazwy gryzonia gatunków z ciągów rozdzielanych przecinkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Wyrażenie regularne `\G(\w+\s?\w*),?` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij, gdzie zakończenia ostatniego dopasowania.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\s?`|Dopasowanie do zera lub jednego miejsca.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`(\w+\s?\w*)`|Dopasowuje co najmniej jeden znak słowa, następuje zero lub jeden miejsce, w którym następuje zero lub więcej znaków słowa. Jest to pierwsza grupa przechwytywania.|  
|`,?`|Wystąpienie Dopasuj zero lub jeden znak przecinka literału.|  
  
 [Powrót do początku](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Wyszukiwanie granicy wyrazów: \b  
 `\b` Zakotwiczenia określa, że dopasowanie musi wystąpić na granicy między znakiem słowa ( `\w` element języka) i znaki niebędące znakami słowa ( `\W` element języka). Znak słowa zawierać znaki alfanumeryczne i znaki podkreślenia; znaki niebędące znakami słowa jest dowolny znak, który nie jest alfanumerycznym lub znakiem podkreślenia. (Aby uzyskać więcej informacji, zobacz [klas znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Dopasowanie może również wystąpić na granicy słowa na początku lub na końcu ciągu.  
  
 `\b` Zakotwiczenia jest często używany do upewnij się, że wyrażenie cząstkowe odpowiada całe wyrazy, a nie tylko początek lub koniec wyrazu. Wyrażenie regularne `\bare\w*\b` w poniższym przykładzie przedstawiono użycie tych. Dopasowuje dowolny wyraz rozpoczynający się od podciągu "czy". Dane wyjściowe z przykładu, ilustruje `\b` pasuje do początku i na końcu ciągu wejściowego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`are`|Dopasuj podciąg "czy".|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Brak wyszukiwania granicy wyrazów: \B  
 `\B` Zakotwiczenia określa, że dopasowanie nie musi wystąpić na granicy wyrazu. Jest to odwrotność `\b` zakotwiczenia.  
  
 W poniższym przykładzie użyto `\B` kontrolne, aby zlokalizować wystąpienia podciągu "kwerendy" w wyrazie. Definicję wzorca wyrażenia regularnego `\Bqu\w+` pasuje do podciągu, który rozpoczyna się od "kwerendy", nie uruchamia program word i która kontynuuje do końca słowa.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\B`|Nie rozpoczyna dopasowanie na granicy wyrazu.|  
|`qu`|Dopasuj podciąg "kwerendy".|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
