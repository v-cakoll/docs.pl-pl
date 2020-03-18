---
title: Inne konstrukcje w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
ms.openlocfilehash: a43ce44e11a9231dee2961ee02bac745d9ca71cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141603"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Inne konstrukcje w wyrażeniach regularnych
Wyrażenia regularne w .NET zawierają trzy różne konstrukcje języka. Jeden pozwala włączyć lub wyłączyć określone opcje dopasowania w środku wzorca wyrażenia regularnego. Pozostałe dwa umożliwiają dołączanie komentarzy do wyrażenia regularnego.  
  
## <a name="inline-options"></a>Opcje w wierszu  
 Można ustawić lub wyłączyć określone opcje dopasowywania wzorców dla części wyrażenia regularnego za pomocą składni  
  
`(?imnsx-imnsx)`  
  
 Po znaku zapytania należy wyświetlić listę opcji, które chcesz włączyć, oraz opcji, które chcesz wyłączyć po znaku minus. W tabeli poniżej opisano wszystkie opcje. Aby uzyskać więcej informacji na temat każdej opcji, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`i`|Dopasowanie bez uwzględniania wielkości liter.|  
|`m`|Tryb wielowierszowy.|  
|`n`|Jawne przechwytuje tylko. (Nawiasy nie działają jako grupy przechwytywania).|  
|`s`|Tryb jednoliniowy.|  
|`x`|Ignoruj nieuniknięte białe osła i zezwalaj na komentarze w trybie x.|  
  
 Wszelkie zmiany w opcjach wyrażenia `(?imnsx-imnsx)` regularnego zdefiniowane przez konstrukcję pozostają w mocy do końca otaczającej grupy.  
  
> [!NOTE]
> Konstrukcja `(?imnsx-imnsx:`grupowania *podwyrężeń* `)` zapewnia identyczne funkcje wyrażenia podrzędnego. Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 W poniższym `i`przykładzie `n`użyto , i `x` opcje, aby włączyć niewrażliwość wielkości liter i jawne przechwytywanie i ignorować biały znak w wzorcu wyrażenia regularnego w środku wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 W przykładzie zdefiniowano dwa wyrażenia regularne. Pierwszy , `\b(D\w+)\s(d\w+)\b`pasuje do dwóch kolejnych słów, które zaczynają się wielkimi literami "D" i małe litery "d". Drugie wyrażenie regularne `\b(D\w+)(?ixn) \s (d\w+) \b`, używa opcji wbudowanych do modyfikowania tego wzorca, zgodnie z opisem w poniższej tabeli. Porównanie wyników potwierdza efekt `(?ixn)` konstrukcji.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(D\w+)`|Dopasuj literę "D", po której następuje jeden lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`(?ixn)`|Od tego momentu należy porównywać wielkość liter bez uwzględniania wielkości liter, umożliwiatylko jawne przechwytywanie i ignorowanie odstępu w wzorcu wyrażenia regularnego.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(d\w+)`|Dopasuj wielkie lub małe litery "d", po którym następuje jeden lub więcej znaków wyrazu. Ta grupa nie jest `n` przechwytywana, ponieważ włączono opcję (jawnego przechwytywania)..|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
## <a name="inline-comment"></a>Komentarz wbudowany  
 Konstrukcja `(?#` *komentarza* `)` umożliwia dołączenie komentarza w wierszu do wyrażenia regularnego. Aparat wyrażeń regularnych nie używa żadnej części komentarza w dopasowaniu wzorca, chociaż <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> komentarz znajduje się w ciągu, który jest zwracany przez metodę. Komentarz kończy się przy pierwszym nawiasie zamykającym.  
  
 Poniższy przykład powtarza pierwszy wzorzec wyrażenia regularnego z przykładu w poprzedniej sekcji. Dodaje dwa komentarze w wierszu do wyrażenia regularnego, aby wskazać, czy porównanie jest rozróżniana. Wzorzec `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`wyrażenia regularnego , jest zdefiniowany w następujący sposób.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?# case-sensitive comparison)`|Komentarz. Nie ma to wpływu na zachowanie dopasowywania wzorców.|  
|`(D\w+)`|Dopasuj literę "D", po której następuje jeden lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(?ixn)`|Od tego momentu należy porównywać wielkość liter bez uwzględniania wielkości liter, umożliwiatylko jawne przechwytywanie i ignorowanie odstępu w wzorcu wyrażenia regularnego.|  
|`(?#case-insensitive comparison)`|Komentarz. Nie ma to wpływu na zachowanie dopasowywania wzorców.|  
|`(d\w+)`|Dopasuj wielkie lub małe litery "d", po którym następuje jeden lub więcej znaków wyrazu. Jest to druga grupa przechwytywania.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentarz na koniec linii  
 Znak liczby`#`( )oznacza komentarz w trybie x, który rozpoczyna się od znaku #unescaped na końcu wzorca wyrażenia regularnego i trwa do końca wiersza. Aby użyć tej konstrukcji, należy `x` włączyć opcję (za pośrednictwem <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcji `option` wbudowanych) lub podać <xref:System.Text.RegularExpressions.Regex> wartość do <xref:System.Text.RegularExpressions.Regex> parametru podczas tworzenia wystąpienia obiektu lub wywoływania metody statycznej.  
  
 Poniższy przykład ilustruje konstrukcję komentarza końca wiersza. Określa, czy ciąg jest ciągiem formatu złożonego, który zawiera co najmniej jeden element formatu. W poniższej tabeli opisano konstrukcje we wzorcu wyrażenia regularnego:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\{`|Dopasuj klamrę otwierającą.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,-*\d+)*`|Dopasuj zero lub jedno wystąpienie przecinka, po którym następuje opcjonalny znak minus, po którym następuje jedna lub więcej cyfr dziesiętnych.|  
|`(\:\w{1,4}?)*`|Dopasuj zero lub jedno wystąpienie dwukropka, po którym następuje od jednego do czterech, ale jak najmniej znaków odstępu.|  
|`\}`|Dopasuj nawias zamykający.|  
|`(?x)`|Włącz opcję wybielania wzorca ignorowania, aby komentarz na końcu wiersza był rozpoznawany.|  
|`# Looks for a composite format item.`|Komentarz na koniec linii.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Należy zauważyć, że zamiast `(?x)` dostarczania konstrukcji w wyrażeniu regularnym, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> komentarz może również <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> zostały rozpoznane przez wywołanie metody i przekazywanie jej wartość wyliczenia.  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
