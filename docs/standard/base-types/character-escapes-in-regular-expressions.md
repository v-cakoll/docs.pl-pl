---
title: Znaki specjalne w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebdcda655a186d54065e98f8b9c5c7ae2fda4955
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569911"
---
# <a name="character-escapes-in-regular-expressions"></a>Znaki specjalne w wyrażeniach regularnych
Kreska ułamkowa odwrócona (\\) w wyrażeniu regularnym wskazuje jedną z następujących czynności:  
  
-   Znak, który następuje jest znak specjalny, jak pokazano w tabeli w następnej sekcji. Na przykład `\b` jest zakotwiczenie wskazuje, czy dopasowanie wyrażenia regularnego powinny one zacząć na granicy word `\t` reprezentuje kartę, i `\x020` reprezentuje spacją.  
  
-   Znak, które w przeciwnym razie będzie interpretowana jako konstrukcji języka niezmienionym znaczeniu, które powinny być rozumiane jako literału. Na przykład nawiasu klamrowego (`{`) rozpoczyna się definicji kwantyfikator, ale ukośnik odwrotny, a następnie nawiasu klamrowego (`\{`) wskazuje, że nawiasem powinna być zgodna z aparatem wyrażeń regularnych. Podobnie, pojedynczy ukośnik odwrotny oznacza początek konstrukcji języka zmieniony, ale dwa razy (`\\`) wskazuje, że aparat wyrażeń regularnych powinna być zgodna ukośniku odwrotnym.  
  
> [!NOTE]
>  Znaki specjalne są rozpoznawane w wzorców wyrażeń regularnych, ale nie w wzorce zamiany.  
  
## <a name="character-escapes-in-net"></a>Znaki specjalne w .NET  
 Poniższa lista zawiera znaki specjalne obsługiwane przez wyrażeń regularnych programu .NET.  
  
|Znak lub sekwencji|Opis|  
|---------------------------|-----------------|  
|Wszystkie znaki oprócz następujących:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \|Znaki inne niż wymienione w **znaków ani sekwencji** kolumna ma specjalnego znaczenia w wyrażeniach regularnych; pasują do siebie.<br /><br /> Znaki znajdujące się w **znaków ani sekwencji** kolumny są elementy języka specjalne wyrażenia regularnego. Aby uwzględnić je w wyrażeniu regularnym, muszą być zmienione znaczenie lub zawarte w [grupy dodatnią znak](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Na przykład, wyrażenie regularne `\$\d+` lub `[$]\d+` "$1200" jest zgodna.|  
|`\a`|Reprezentuje znak dzwonka (alarm) `\u0007`.|  
|`\b`|W `[` *character_group* `]` znak klasy, dopasowań a backspace `\u0008`.  (Zobacz [klasy znaku](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Poza klasą znak `\b` jest zakotwiczenie pasuje do ograniczenia wyrazu. (Zobacz [kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Dopasowuje kartę `\u0009`.|  
|`\r`|Powrót karetki odpowiada `\u000D`. Należy pamiętać, że `\r` nie jest odpowiednikiem znaku nowego wiersza `\n`.|  
|`\v`|Dopasowuje tabulator pionowy, `\u000B`.|  
|`\f`|Dopasowuje wysuw, `\u000C`.|  
|`\n`|Nowy wiersz, jest zgodna `\u000A`.|  
|`\e`|Dopasowuje ucieczki `\u001B`.|  
|`\` *nnn*|Pasuje do znaku ASCII, gdzie *nnn* składa się z dwóch lub trzech cyfr reprezentujących ósemkowe znakowy kod. Na przykład `\040` reprezentuje znak odstępu. Ta konstrukcja jest interpretowana jako dopasowań, jeśli ma ona tylko jedną cyfrę (na przykład `\2`) lub jeśli odpowiadający mu numer przechwytywania grupy. (Zobacz [Konstrukty](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Pasuje do znaku ASCII, gdzie *nn* kodu dwucyfrowe znaków szesnastkowych.|  
|`\c` *X*|Dopasowuje znak kontrolny ASCII, gdzie X jest literą znaku kontrolnego. Na przykład `\cC` jest CTRL-C.|  
|`\u` *nnnn*|Dopasowuje jednostki kodu UTF-16, którego wartość jest *nnnn* szesnastkową. **Uwaga:** ucieczki znak Perl 5, który służy do określania Unicode nie jest obsługiwany przez platformę .NET. Ucieczki znaku Perl 5 ma postać `\x{` *####* `…}`, gdzie *####* `…` jest seria cyfr szesnastkowych. Zamiast tego należy użyć `\u` *nnnn*.|  
|`\`|Gdy następuje znak, który nie został rozpoznany jako oczekiwanego znaku, pasuje do tego znaku. Na przykład `\*` odpowiada znak gwiazdki (*) i jest taki sam jak `\x2A`.|  
  
## <a name="an-example"></a>Przykład  
 Poniższy przykład przedstawia użycie znaki specjalne w wyrażeniu regularnym. Analizuje ciąg, który zawiera nazwy miast największa na świecie i ich populacji w 2009 roku. Każda nazwa miejscowości jest oddzielona od jego wypełniania przez kartę (`\t`) lub pionowej kreski (&#124; lub `\u007c`). W poszczególnych miastach i ich populacji są oddzielone od siebie powrotu karetki i wysuwu wiersza.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Wyrażenie regularne `\G(.+)[\t|\u007c](.+)\r?\n` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij dopasowania, gdzie zakończenia ostatniego dopasowania.|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
|`[\t\u007c]`|Zgodne karty (`\t`) lub pionowej kreski (&#124;).|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
|`\r?\n`|Zgodne wystąpienie zero lub jeden znak powrotu karetki znak nowego wiersza.|  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
