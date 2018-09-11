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
ms.openlocfilehash: 8956726915ebe1c0b1c7654e62e2e28620274b4a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276123"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Inne konstrukcje w wyrażeniach regularnych
Wyrażenia regularne w .NET obejmują trzy konstrukcji językowych różne. Jeden pozwala włączyć lub wyłączyć określonego opcje dopasowania w środku wzorca wyrażenia regularnego. Dwóch pozostałych pozwala na uwzględnianie komentarzy w wyrażeniu regularnym.  
  
## <a name="inline-options"></a>Opcje określane w tekście  
 Można ustawić lub wyłączyć określony wzorzec dopasowywania opcje dla części wyrażenia regularnego przy użyciu składni  
  
```  
(?imnsx-imnsx)  
```  
  
 Możesz wyświetlić listę opcje, które chcesz włączyć po znaku zapytania, a także opcje, które chcesz wyłączyć po znaku minus. W tabeli poniżej opisano wszystkie opcje. Aby uzyskać więcej informacji na temat poszczególnych opcji, zobacz [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Opcja|Opis|  
|------------|-----------------|  
|`i`|Dopasowywanie bez uwzględniania wielkości liter.|  
|`m`|Tryb wielowierszowy.|  
|`n`|Tylko jawne przechwytywania. (Nawias mają nie zachowywać się jak grupy przechwytywania.)|  
|`s`|Trybu jednowierszowego.|  
|`x`|Ignoruj niekodowany biały znak i umożliwiają komentarz trybu x.|  
  
 Wszelkie zmiany w opcje wyrażeń regularnych zdefiniowane przez `(?imnsx-imnsx)` konstruowania pozostają w mocy aż do zakończenia otaczającego grupy.  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Podwyrażenie* `)` konstrukcja grupująca zapewnia identyczne funkcje podwyrażenia. Aby uzyskać więcej informacji, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 W poniższym przykładzie użyto `i`, `n`, i `x` opcje umożliwiające ignorowanie wielkości liter i jawne przechwytywania i ignoruje biały znak we wzorcu wyrażenia regularnego w trakcie wykonywania wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 W przykładzie zdefiniowano dwóch wyrażeń regularnych. Pierwsza strona, `\b(D\w+)\s(d\w+)\b`, dopasowuje dwa kolejne wyrazy rozpoczynające się od wielkiej "D" i "d" małymi literami. Drugie wyrażenie regularne `\b(D\w+)(?ixn) \s (d\w+) \b`, używa opcji wbudowanej do modyfikowania tego wzorca, zgodnie z opisem w poniższej tabeli. Porównanie wyników potwierdza efekt `(?ixn)` konstruowania.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(D\w+)`|Dopasowuje wielkiej litery "D", po którym następuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`(?ixn)`|Od tej pory na marki porównania bez uwzględniania wielkości liter upewnij tylko jawne przechwytuje i Ignoruj biały znak we wzorcu wyrażenia regularnego.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(d\w+)`|Dopasowuje wielkimi lub małymi literami "d" następuje jeden lub więcej znaków słowa. Ta grupa nie jest przechwytywany, ponieważ `n` została włączona opcja (jawne przechwytywania)...|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
## <a name="inline-comment"></a>Komentarz w tekście  
 `(?#` *Komentarz* `)` konstrukcja pozwala dołączyć komentarz w tekście w wyrażeń regularnych. Aparat wyrażeń regularnych nie korzysta z dowolnej części komentarz w dopasowywania do wzorca, chociaż komentarz znajduje się w ciągu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> metody. Komentarz kończy się przy pierwszym nawiasie zamykającym.  
  
 Poniższy przykład jest powtarzany wzorca pierwszego wyrażenia regularnego z przykładu w poprzedniej sekcji. Dodaje dwa komentarze w tekście do wyrażenia regularnego, aby wskazać, czy wynikiem porównania jest uwzględniana wielkość liter. Wzorzec wyrażenia regularnego `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, jest zdefiniowana w następujący sposób.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?# case-sensitive comparison)`|Komentarz. Nie ma wpływu na zachowanie dopasowania do wzorca.|  
|`(D\w+)`|Dopasowuje wielkiej litery "D", po którym następuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(?ixn)`|Od tej pory na marki porównania bez uwzględniania wielkości liter upewnij tylko jawne przechwytuje i Ignoruj biały znak we wzorcu wyrażenia regularnego.|  
|`(?#case-insensitive comparison)`|Komentarz. Nie ma wpływu na zachowanie dopasowania do wzorca.|  
|`(d\w+)`|Dopasowuje wielkimi lub małymi literami "d" następuje jeden lub więcej znaków słowa. Jest to druga grupa przechwytywania.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Komentarz do końca wiersza  
 Znak numeru (`#`) oznacza komentarz trybu x, która rozpoczyna się od znaku # o niezmienionym znaczeniu na końcu wzorca wyrażenia regularnego i jest kontynuowany aż do końca wiersza. Aby użyć tej konstrukcji, musisz albo Włącz `x` opcji (za pomocą opcji wbudowanych) lub podać <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> wartość `option` parametru podczas tworzenia wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu lub wywoływania statycznej <xref:System.Text.RegularExpressions.Regex> metody.  
  
 W poniższym przykładzie pokazano konstrukcję końca wiersza komentarza. Określa, czy ciąg jest ciąg formatu złożonego, który zawiera co najmniej jeden element formatu. W poniższej tabeli opisano konstrukcje we wzorcu wyrażenia regularnego:  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\{`|Zgodny z nawiasem otwierającym.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,-*\d+)*`|Dopasowuje wystąpienia zero lub jeden przecinek, następuje opcjonalny znak minusa, następuje jeden lub więcej cyfr dziesiętnych.|  
|`(\:\w{1,4}?)*`|Dopasowuje zero lub jeden wystąpienie dwukropek i 1 do 4, ale tak małą możliwie białych znaków.|  
|`\}`|Dopasowuje zamykającego nawiasu klamrowego.|  
|`(?x)`|Włącz opcję Ignoruj wzorca odstępu komentarz końca wiersza zostanie rozpoznana.|  
|`# Looks for a composite format item.`|Komentarz do końca wiersza.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Należy zauważyć, że zamiast podawać `(?x)` konstruowania w wyrażeniu regularnym komentarz może również zostały uznane przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody i przekazanie do niej <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> wartość wyliczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
