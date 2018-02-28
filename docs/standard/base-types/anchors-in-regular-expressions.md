---
title: "Zakotwiczenia w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e328c294a9b4ca3047c4ad1750ddedf64bac2218
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="anchors-in-regular-expressions"></a>Zakotwiczenia w wyrażeniach regularnych
<a name="top"></a> Kotwice lub niepodzielne asercje o zerowej szerokości, należy określić pozycji w ciągu, w którym musi wystąpić dopasowania. Gdy używasz zakotwiczenia w wyrażeniu wyszukiwania aparat wyrażeń regularnych nie przechodzić przez ciąg lub zużywać znaków. Wyszukuje dopasowania w określonej pozycji. Na przykład `^` Określa, że dopasowania musi zaczynać się na początku wiersza lub ciąg. W związku z tym wyrażenia regularnego `^http:` zgodny "http:" tylko wtedy, gdy wystąpi go na początku wiersza. W poniższej tabeli wymieniono kotwice obsługiwane przez wyrażeń regularnych programu .NET.  
  
|Kotwica|Opis|  
|------------|-----------------|  
|`^`|Dopasowania musi występować na początku ciąg lub wiersza. Aby uzyskać więcej informacji, zobacz [Start ciąg lub wiersza](#Start).|  
|`$`|Dopasowania musi występować na końcu ciągu lub wiersza lub przed `\n` na końcu ciągu lub wiersza. Aby uzyskać więcej informacji, zobacz [End of String lub wiersza](#End).|  
|`\A`|Dopasowania musi występować na początku tylko ciągi (bez obsługi wielowierszowe). Aby uzyskać więcej informacji, zobacz [Start z ciągu tylko](#StartOnly).|  
|`\Z`|Dopasowania musi występować na końcu ciągu lub przed `\n` na końcu ciągu. Aby uzyskać więcej informacji, zobacz [End of String lub przed zakończeniem nowego wiersza](#EndOrNOnly).|  
|`\z`|Dopasowania musi występować na końcu tylko ciągi. Aby uzyskać więcej informacji, zobacz [zakończenia z ciągu tylko](#EndOnly).|  
|`\G`|Dopasowania musi rozpoczynać się w miejscu, gdzie zakończył poprzedniego dopasowania. Aby uzyskać więcej informacji, zobacz [ciągłe dopasowań](#Contiguous).|  
|`\b`|Dopasowania musi przypadać w granicach programu word. Aby uzyskać więcej informacji, zobacz [granicy słowa](#WordBoundary).|  
|`\B`|Dopasowanie nie musi przypadać w granicach programu word. Aby uzyskać więcej informacji, zobacz [granic Non-Word](#NonwordBoundary).|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>Początek ciągu lub wiersz: ^  
 `^` Zakotwiczenia określa, że następującego wzorca musi się rozpoczynać od pierwszego pozycja znaku w ciągu. Jeśli używasz `^` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji (zobacz [opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)), dopasowania musi występować na początku każdego wiersza.  
  
 W poniższym przykładzie użyto `^` zakotwiczenia w wyrażeniu regularnym, który wyodrębnia informacje o lat, podczas których istniał niektóre zespoły professional baseball. Przykład wywołuje dwa przeciążenia <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody:  
  
-   Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> przeciążenia znajduje pierwszy podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego.  
  
-   Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> przeciążenia z `options` ustawiona <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> znajduje wszystkie pięć podciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowania na początku ciąg wejściowy (lub na początek wiersza, jeśli metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcja).|  
|`((\w+(\s?)){2,}`|Odpowiada jeden lub więcej znaków programu word, a następnie zero lub jedną spację dokładnie dwa razy. Jest to pierwsza grupa przechwytywania. To wyrażenie również definiuje grupę przechwytywania drugi i trzeci: drugi składa się przechwyconych Word, a trzeci składa się z przechwyconych spacji.|  
|`,\s`|Odpowiada to przecinek biały znak.|  
|`(\w+\s\w+)`|Zgodne z co najmniej jeden znak słowa spację, następuje co najmniej jeden znak programu word. Jest to czwarty grupa przechwytywania.|  
|`,`|Zgodne przecinkami.|  
|`\s\d{4}`|Zgodne miejsca, a następnie czterech cyfr dziesiętnych.|  
|<code>(-(\d{4}&#124;present))?</code>|Zgodne wystąpienie zero lub jeden łącznik następuje cztery cyfry dziesiętne lub ciąg "istnieje". Jest to szóstego grupa przechwytywania. Obejmuje on też siódmego Przechwytywanie grupy.|  
|`,?`|Wystąpienie dopasowania zero lub jeden przecinkami.|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|Zgodne z co najmniej jedno wystąpienie następujących: spację, czterech cyfr dziesiętnych, zero lub jeden wystąpienia łącznika następuje cztery cyfry dziesiętne lub ciąg "Brak" oraz zero lub jeden przecinkami. Jest to piąty grupa przechwytywania.|  
  
 [Powrót do początku](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>Koniec ciągu lub linii: $  
 `$` Zakotwiczenia określa, że wzorzec poprzedniego muszą występować na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego.  
  
 Jeśli używasz `$` z <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji dopasowania może również wystąpić na końcu linii. Należy pamiętać, że `$` odpowiada `\n` , ale nie pasuje `\r\n` (kombinacja karetki powrotu i znaki nowego wiersza lub CR/LF). Aby dopasować kombinacji znaków CR/LF, obejmują `\r?$` w wzorzec wyrażenia regularnego.  
  
 W poniższym przykładzie dodano `$` kotwicy na wzorzec wyrażenia regularnego używane w przykładzie [Start ciąg lub wiersza](#Start) sekcji. W przypadku użycia z oryginalnego ciąg wejściowy zawiera pięć wierszy tekstu, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda jest nie można odnaleźć dopasowania, ponieważ końcu pierwszego wiersza nie jest zgodny z `$` wzorca. Gdy oryginalny ciąg wejściowy jest podzielony na tablicę ciągów, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda zakończy się powodzeniem we wszystkich pięciu wierszach dopasowania. Gdy <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda jest wywoływana z `options` parametru <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>, ponieważ element powrotu karetki (\u+000D) bez uwzględnienia wzorzec wyrażenia regularnego nieodnalezienia żadnych dopasowań. Jednak jeśli wzorzec wyrażenia regularnego jest modyfikowany przez zastąpienie `$` z `\r?$`, wywoływania <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody z `options` ustawiona <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> ponownie znalezieniu pięć pasujących.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [Powrót do początku](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>Tylko początek ciągu: \A  
 `\A` Zakotwiczenia określa, że dopasowania musi występować na początku ciąg wejściowy. Jest on identyczny `^` kontrolne, z wyjątkiem `\A` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym może wyłącznie odpowiadać początek w pierwszym wierszu wielowierszowy ciąg wejściowy.  
  
 Poniższy przykład jest podobne do dla `^` i `$` zakotwiczenia. Używa `\A` zakotwiczenia w wyrażeniu regularnym, który wyodrębnia informacje o lat, podczas których istniał niektóre zespoły professional baseball. Ciąg wejściowy zawiera pięć wiersze. Wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda znajdzie pierwszego podciągu w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego. Jak w przykładzie <xref:System.Text.RegularExpressions.RegexOptions.Multiline> opcja nie ma znaczenia.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>Koniec ciągu lub przed zakończeniem nowego wiersza: \Z  
 `\Z` Zakotwiczenia określa, że dopasowania musi występować na końcu ciągu wejściowego lub przed `\n` na końcu ciągu wejściowego. Jest on identyczny `$` kontrolne, z wyjątkiem `\Z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W związku z tym w wielowierszowy ciąg tylko dopasowania końcu ostatniego wiersza lub ostatni wiersz przed `\n`.  
  
 Należy pamiętać, że `\Z` odpowiada `\n` , ale nie pasuje `\r\n` (kombinacji znaków CR/LF). Aby dopasować CR/LF, obejmują `\r?\Z` w wzorzec wyrażenia regularnego.  
  
 W poniższym przykładzie użyto `\Z` zakotwiczenia w wyrażeniu regularnym, która jest podobna do przykładu w [Start ciąg lub wiersza](#Start) sekcji, która wyodrębnia informacje o lat, podczas których niektóre baseball professional zespoły istniała. Podwyrażenie `\r?\Z` w wyrażeniu regularnym `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` końca ciągu i ciąg, który kończy się wyrazem `\n` lub `\r\n`. W związku z tym każdy element tablicy jest zgodna ze wzorcem wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [Powrót do początku](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>Tylko koniec ciągu: \z  
 `\z` Zakotwiczenia określa, że dopasowania musi występować na końcu ciągu wejściowego. Podobnie jak `$` element języka, `\z` ignoruje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji. W odróżnieniu od `\Z` element języka, `\z` niezgodny `\n` znak na końcu ciągu. W związku z tym może wyłącznie odpowiadać ostatni wiersz ciągu wejściowego.  
  
 W poniższym przykładzie użyto `\z` zakotwiczenia w wyrażeniu regularnym, który jest taki sam jak przykładowy w poprzedniej sekcji, która wyodrębnia informacje o lat, podczas których istniał niektóre zespoły professional baseball. Przykład próbuje dopasować, każdy z pięciu elementów w tablicy ciągów z wzorcem wyrażenia regularnego `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`. Zwraca dwa końce ciągi karetki i znaki wysuwu wiersza, zakończy się wiersz znaków i zwracać dwa kończyć ani karetki ani znak wysuwu wiersza. Jak pokazano na dane wyjściowe, zwróć tylko ciągi bez karetki lub wysuw znak dopasowania wzorca.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [Powrót do początku](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>Ciągłe dopasowanie: \G  
 `\G` Zakotwiczenia określa, że dopasowania musi występować w momencie, gdy upłynął poprzedniego dopasowania. Jeśli używasz tego zakotwiczenia z <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody gwarantuje, że wszystkie dopasowania są ciągłe.  
  
 W poniższym przykładzie użyto wyrażenia regularnego do wyodrębniania nazw gryzonia Określa ciąg rozdzielany przecinkami.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 Wyrażenie regularne `\G(\w+\s?\w*),?` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij, gdzie zakończenia ostatniego dopasowania.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\s?`|Dopasowanie zero lub jeden miejsca.|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`(\w+\s?\w*)`|Zgodne z co najmniej jeden znak słowa następuje zero lub jeden miejsca, następuje zero lub więcej znaków programu word. Jest to pierwsza grupa przechwytywania.|  
|`,?`|Wystąpienie dopasowania zero lub jeden znak literału przecinkami.|  
  
 [Powrót do początku](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>Wyszukiwanie granicy wyrazów: \b  
 `\b` Zakotwiczenia określa, że dopasowania musi występować w granicach od litery ( `\w` element języka) i znak-word ( `\W` element języka). Znaki Word zawierają znaki alfanumeryczne oraz znaki podkreślenia; znak-word jest dowolny znak, który nie jest alfanumeryczne lub podkreślenie. (Aby uzyskać więcej informacji, zobacz [klas znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Dopasowanie może również wystąpić na granicy słowa na początku lub końca ciągu.  
  
 `\b` Zakotwiczenia jest często używany do upewnij się, że podwyrażenia odpowiada całe wyrazy, a nie tylko początek lub koniec słowa. Wyrażenie regularne `\bare\w*\b` w poniższym przykładzie przedstawiono użycie tego. Jest on zgodny słowa rozpoczyna się od "czy" podciąg. Dane wyjściowe w przykładzie przedstawiono również który `\b` odpowiada początku i na końcu ciągu wejściowego.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`are`|Dopasowanie podciągu "czy".|  
|`\w*`|Dopasowuje zero lub więcej znaków słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>Brak wyszukiwania granicy wyrazów: \B  
 `\B` Zakotwiczenia określa ogranicznik słowa nie mogą występować dopasowania. Jest przeciwieństwem `\b` zakotwiczenia.  
  
 W poniższym przykładzie użyto `\B` zakotwiczenia, aby zlokalizować wystąpienia podciągu "ustawienia kol" w edytorze. Wzorzec wyrażenia regularnego `\Bqu\w+` pasuje do podciągu, który rozpoczyna się od "Ustawienia kol" nie rozpoczyna wyraz i który będzie kontynuowane do końca słowa.  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\B`|Rozpoczyna się dopasowania na granicy programu word.|  
|`qu`|Zgodne podciągu "ustawienia kol".|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md)
