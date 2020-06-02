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
ms.openlocfilehash: 8ca888074aa757a1bfba786a7bec5928b75b1da2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290412"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Inne konstrukcje w wyrażeniach regularnych
Wyrażenia regularne w programie .NET zawierają trzy różne konstrukcje językowe. Jeden umożliwia włączenie lub wyłączenie określonych opcji dopasowania w środku wzorca wyrażenia regularnego. Pozostałe dwa umożliwiają uwzględnienie komentarzy w wyrażeniu regularnym.  
  
## <a name="inline-options"></a>Opcje wbudowane  
 Można ustawić lub wyłączyć konkretne opcje dopasowania do wzorca dla części wyrażenia regularnego przy użyciu składni  
  
`(?imnsx-imnsx)`  
  
 Należy wyświetlić listę opcji, które mają być włączone po znaku zapytania, oraz opcje, które mają zostać wyłączone po znaku minus. W tabeli poniżej opisano wszystkie opcje. Aby uzyskać więcej informacji na temat każdej z tych opcji, zobacz [Opcje wyrażenia regularnego](regular-expression-options.md).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`i`|Dopasowywanie bez uwzględniania wielkości liter.|  
|`m`|Tryb wielowierszowy.|  
|`n`|Tylko jawne przechwycenia. (Nawiasy nie działają jako grupy przechwytywania).|  
|`s`|Tryb jednowierszowy.|  
|`x`|Ignoruj nieucieczki biały znak i Zezwalaj na komentarze w trybie x.|  
  
 Wszelkie zmiany opcji wyrażenia regularnego zdefiniowane przez `(?imnsx-imnsx)` konstrukcję pozostają w efekcie do końca otaczającej grupy.  
  
> [!NOTE]
> Konstrukcja `(?imnsx-imnsx:` *podwyrażenia* `)` grupującego zawiera identyczne funkcje dla podwyrażenia. Aby uzyskać więcej informacji, zobacz [grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).  
  
 W poniższym przykładzie są stosowane `i` `n` Opcje, i, które umożliwiają włączenie wyznaczania `x` wielkości liter i jawnych przechwycenia oraz ignorowanie białych znaków we wzorcu wyrażenia regularnego w środku wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 W przykładzie zdefiniowano dwa wyrażenia regularne. Pierwsze, `\b(D\w+)\s(d\w+)\b` , dopasowuje dwa kolejne słowa zaczynające się wielką literą "d" i małą literą "d". Drugie wyrażenie regularne, `\b(D\w+)(?ixn) \s (d\w+) \b` , używa wbudowanych opcji, aby zmodyfikować ten wzorzec, zgodnie z opisem w poniższej tabeli. Porównanie wyników potwierdza efekt `(?ixn)` konstrukcji.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(D\w+)`|Dopasowuje wielką literę "D", po której następuje jeden lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`(?ixn)`|Od tego momentu w programie należy wprowadzać bez uwzględniania wielkości liter, wprowadzać tylko jawne przechwycenia i ignorować biały znak we wzorcu wyrażenia regularnego.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(d\w+)`|Dopasowuje wielkie lub małe litery "d", po którym następuje co najmniej jeden znak wyrazu. Ta grupa nie została przechwycona, ponieważ `n` włączono opcję (jawne przechwytywanie).|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
## <a name="inline-comment"></a>Komentarz w tekście  
 Konstrukcja `(?#` *komentarza* `)` umożliwia dołączenie komentarza wbudowanego w wyrażeniu regularnym. Aparat wyrażeń regularnych nie używa żadnej części komentarza w dopasowaniu do wzorca, chociaż komentarz jest zawarty w ciągu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metodę. Komentarz kończy się przy pierwszym nawiasie zamykającym.  
  
 Poniższy przykład powtarza pierwszy wzorzec wyrażenia regularnego z przykładu w poprzedniej sekcji. Dodaje dwa wbudowane Komentarze do wyrażenia regularnego, aby wskazać, czy w porównaniu jest rozróżniana wielkość liter. Wzorzec wyrażenia regularnego `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b` jest zdefiniowany w następujący sposób.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?# case-sensitive comparison)`|Komentarz. Nie ma to wpływu na zachowanie dopasowania do wzorca.|  
|`(D\w+)`|Dopasowuje wielką literę "D", po której następuje jeden lub więcej znaków wyrazu. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(?ixn)`|Od tego momentu w programie należy wprowadzać bez uwzględniania wielkości liter, wprowadzać tylko jawne przechwycenia i ignorować biały znak we wzorcu wyrażenia regularnego.|  
|`(?#case-insensitive comparison)`|Komentarz. Nie ma to wpływu na zachowanie dopasowania do wzorca.|  
|`(d\w+)`|Dopasowuje wielkie lub małe litery "d", po którym następuje co najmniej jeden znak wyrazu. Jest to druga grupa przechwytywania.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentarz końca wiersza  
 Znak numeru ( `#` ) oznacza komentarz w trybie x, który zaczyna się od znaku nieoznaczonego znakiem # na końcu wzorca wyrażenia regularnego i kontynuuje do końca wiersza. Aby użyć tej konstrukcji, należy włączyć `x` opcję (za pomocą opcji wbudowanych) lub podać <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> wartość do `option` parametru podczas tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu lub wywoływania metody statycznej <xref:System.Text.RegularExpressions.Regex> .  
  
 Poniższy przykład ilustruje zakończenie konstruowania komentarza do końca wiersza. Określa, czy ciąg jest ciągiem formatu złożonego, który zawiera co najmniej jeden element formatu. W poniższej tabeli opisano konstrukcje we wzorcu wyrażenia regularnego:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\{`|Dopasowuje nawias otwierający.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,-*\d+)*`|Dopasowanie do zera lub jednego wystąpienia przecinka, po którym następuje opcjonalny znak minus, po którym następuje co najmniej jedna cyfra dziesiętna.|  
|`(\:\w{1,4}?)*`|Dopasowanie do zera lub jednego wystąpienia dwukropka, po którym następuje jeden do czterech, ale jak najmniejszej liczby znaków odstępu.|  
|`\}`|Dopasowuje zamykający nawias klamrowy.|  
|`(?x)`|Włącz opcję ignorowanie białych znaków wzorca, aby można było rozpoznać komentarz końca wiersza.|  
|`# Looks for a composite format item.`|Komentarz końca wiersza.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Należy pamiętać, że zamiast dostarczać `(?x)` konstrukcję w wyrażeniu regularnym, komentarz mógł również zostać rozpoznany przez wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody i przekazanie jej <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> wartości wyliczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
