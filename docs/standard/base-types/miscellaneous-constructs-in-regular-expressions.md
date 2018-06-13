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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fabf1a133ca3c3b3ba39a4898ce0aceb378f76d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571985"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Inne konstrukcje w wyrażeniach regularnych
Wyrażeń regularnych programu .NET obejmują trzy różne języka konstrukcje. Co pozwala włączyć lub wyłączyć opcjami pasującego środku wzorzec wyrażenia regularnego. Dwóch pozostałych pozwala na uwzględnianie komentarzy w wyrażeniu regularnym.  
  
## <a name="inline-options"></a>Wbudowane opcje  
 Możesz ustawić lub wyłącz określonego wzorca dopasowania opcje część wyrażenia regularnego przy użyciu składni  
  
```  
(?imnsx-imnsx)  
```  
  
 Możesz wyświetlić listę opcje, które chcesz włączyć po znaku zapytania i opcje, które mają zostać wyłączone po znaku minus. W tabeli poniżej opisano wszystkie opcje. Aby uzyskać więcej informacji na temat poszczególnych opcji, zobacz [opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`i`|Dopasowywanie bez uwzględniania wielkości liter.|  
|`m`|Wielowierszowy tryb.|  
|`n`|Jawne przechwytywanie tylko. (Nawiasy mają nie zachowywać się jak przechwytywanie grup.)|  
|`s`|Jednowierszowy tryb.|  
|`x`|Ignoruj niezmienionym znaczeniu biały znak, a następnie poczekanie komentarze w trybie x.|  
  
 Zmiany w opcjach wyrażenia regularnego zdefiniowane przez `(?imnsx-imnsx)` w celu utworzenia pozostaje aż do zakończenia otaczające grupy.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Podwyrażenie* `)` konstrukcji grupowania udostępnia funkcję identyczne dla podwyrażenia. Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 W poniższym przykładzie użyto `i`, `n`, i `x` opcje umożliwiające liter i jawne przechwytywanie i Ignoruj biały znak w wzorzec wyrażenia regularnego w trakcie wykonywania wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 W przykładzie zdefiniowano dwóch wyrażeń regularnych. Pierwsza strona, `\b(D\w+)\s(d\w+)\b`, odpowiada dwa kolejne słowa zaczynające się wielkie litery "D" i "d" jedną małą literę. Drugie wyrażenie regularne, `\b(D\w+)(?ixn) \s (d\w+) \b`, używa wbudowanego opcji do modyfikowania tego wzorca, zgodnie z opisem w poniższej tabeli. Porównanie wyników potwierdza efekt `(?ixn)` utworzenia.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(D\w+)`|Zgodne kapitału "D", po którym następuje co najmniej jeden znak programu word. Jest to pierwsza grupa przechwytywania.|  
|`(?ixn)`|Z tego punktu na marka porównania bez uwzględniania wielkości liter markę tylko jawne przechwytuje i Ignoruj biały znak w wzorzec wyrażenia regularnego.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(d\w+)`|Zgodne wielkie i małe litery "d" następuje co najmniej jeden znak programu word. Ta grupa nie jest przechwycona, ponieważ `n` została włączona opcja (jawne przechwytywanie).|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
## <a name="inline-comment"></a>Komentarz w tekście  
 `(?#` *Komentarz* `)` konstrukcja pozwala umieścić komentarz w tekście w wyrażeniu regularnym. Pomimo że komentarz zawiera ciąg, który jest zwracany przez aparat wyrażeń regularnych nie używa dowolną część komentarz w dopasowywania do wzorca <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metody. Komentarz kończy się przy pierwszym nawiasie zamykającym.  
  
 Poniższy przykład powtarza pierwszy wzorzec wyrażenia regularnego z przykładu w poprzedniej sekcji. Dodaje dwa komentarzy wewnętrznych do wyrażenia regularnego, aby wskazać, czy wynik porównania jest rozróżniana wielkość liter. Wzorzec wyrażenia regularnego `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, jest zdefiniowany w następujący sposób.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?# case-sensitive comparison)`|Komentarz. Nie ma ona wpływu na zachowanie dopasowywanie do wzorca.|  
|`(D\w+)`|Zgodne kapitału "D", po którym następuje co najmniej jeden znak programu word. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(?ixn)`|Z tego punktu na marka porównania bez uwzględniania wielkości liter markę tylko jawne przechwytuje i Ignoruj biały znak w wzorzec wyrażenia regularnego.|  
|`(?#case-insensitive comparison)`|Komentarz. Nie ma ona wpływu na zachowanie dopasowywanie do wzorca.|  
|`(d\w+)`|Zgodne wielkie i małe litery "d" następuje co najmniej jeden znak programu word. Jest to drugi grupa przechwytywania.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentarz do końca wiersza  
 Znak liczby (`#`) oznacza komentarz w trybie x, który rozpoczyna się od znaku # niezmienionym znaczeniu na końcu wzorzec wyrażenia regularnego i jest kontynuowane do końca wiersza. Aby użyć tej konstrukcji, należy albo Włącz `x` opcja (przy użyciu opcji wbudowany) lub podać <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> do wartości `option` parametru podczas tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu lub wywoływania statycznych <xref:System.Text.RegularExpressions.Regex> — metoda.  
  
 Poniższy przykład przedstawia konstrukcja komentarz końca wiersza. Określają one, czy ciąg formatu złożony, który zawiera co najmniej jeden element formatu ciągu. W poniższej tabeli opisano konstrukcje w wzorzec wyrażenia regularnego:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\{`|Zgodny z nawiasem otwierającym.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,-*\d+)*`|Zgodne wystąpienie zero lub jeden przecinkami, i opcjonalnie znak minus następuje co najmniej jeden cyfr dziesiętnych.|  
|`(\:\w{1,4}?)*`|Zgodne wystąpienie zero lub jeden dwukropek, następuje 1 do 4, ale jak najmniejszej liczby znaków, jak to możliwe, biały znak.|  
|`(?#case insensitive comparison)`|Komentarz w tekście. Go nie ma wpływu na zachowanie dopasowywanie do wzorca.|  
|`\}`|Zgodny nawiasem zamykającym.|  
|`(?x)`|Tak, aby komentarz końca wiersza zostanie rozpoznany, należy włączyć opcję białe wzorzec ignorowania.|  
|`# Looks for a composite format item.`|Komentarz do końca wiersza.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Należy zauważyć, że zamiast dostarczanie `(?x)` skonstruować w wyrażeniu regularnym komentarz można również zostały uznane przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> — metoda i przekazanie jej <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> wartość wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
