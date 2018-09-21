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
ms.openlocfilehash: 9b390b1d3d935ad045d59dd6b3d2e42cdbe82dd7
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481874"
---
# <a name="character-escapes-in-regular-expressions"></a>Znaki specjalne w wyrażeniach regularnych
Ukośnik odwrotny (\\) w wyrażeniu regularnym wskazuje jedną z następujących czynności:  
  
-   Znak, który po nim następuje jest znakiem specjalnym, jak pokazano w tabeli w poniższej sekcji. Na przykład `\b` jest kotwicę, która wskazuje, że dopasowanie wyrażenia regularnego ma się zacząć na granicy wyrazu `\t` reprezentuje kartę, a `\x020` reprezentuje spację.  
  
-   Znak, które w przeciwnym razie może być interpretowany jako konstrukcji języka o niezmienionym znaczeniu, które powinny być interpretowany literalnie. Na przykład nawias klamrowy (`{`) rozpoczyna się definicji kwantyfikator, ale ukośnikiem nawiasu klamrowego (`\{`) wskazuje, że aparat wyrażeń regularnych powinny odpowiadać nawiasu klamrowego. Podobnie, pojedynczy ukośnik odwrotny oznacza początek konstrukcji języka o zmienionym znaczeniu, ale dwa ukośniki odwrotne (`\\`) wskazują, że aparat wyrażeń regularnych powinny odpowiadać ukośnik odwrotny.  
  
> [!NOTE]
>  Sekwencje ucieczki znaków są rozpoznawane we wzorcach wyrażeń regularnych, ale nie we wzorcach zamieniania.  
  
## <a name="character-escapes-in-net"></a>Znaki specjalne w .NET  
 W poniższej tabeli wymieniono sekwencje ucieczki znaków obsługiwane przez wyrażenia regularne w .NET.  
  
|Znaku lub sekwencji|Opis|  
|---------------------------|-----------------|  
|Wszystkie znaki z wyjątkiem następujących:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Znaki inne niż te wymienione w **znaku lub sekwencji** kolumny nie mają specjalnego znaczenia w wyrażeniach regularnych; pasują do siebie.<br /><br /> Znaki znajdujące się w **znaku lub sekwencji** kolumny są elementami języka wyrażeń regularnych specjalne. Aby dopasować je w wyrażeniu regularnym, muszą być poprzedzone znakiem zmiany znaczenia lub objęte [grupa znaków pozytywnych](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Na przykład, wyrażenie regularne `\$\d+` lub `[$]\d+` pasuje do "$1200".|  
|`\a`|Dopasowuje znak dzwonek (alarm) `\u0007`.|  
|`\b`|W `[` *character_group* `]` klasy, dopasowań, a backspace, znak `\u0008`.  (Zobacz [klasy znaku](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Poza klasą znak `\b` jest kotwicą dopasowującą granicy wyrazu. (Zobacz [kotwic](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Dopasowuje znak tabulatora `\u0009`.|  
|`\r`|Dopasowuje znak powrotu karetki, `\u000D`. Należy pamiętać, że `\r` nie jest odpowiednikiem znaku nowego wiersza, `\n`.|  
|`\v`|Dopasowuje tabulator pionowy, `\u000B`.|  
|`\f`|Dopasowuje znak wysuwu strony, `\u000C`.|  
|`\n`|Dopasowuje znak nowego wiersza `\u000A`.|  
|`\e`|Dopasowuje znak escape `\u001B`.|  
|`\` *nnn*|Dopasowuje znak ASCII gdzie *nnn* składa się z dwóch lub trzech cyfr, które reprezentują ósemkowy kod znaku. Na przykład `\040` reprezentuje znak spacji. Ta konstrukcja jest interpretowany jako odwołanie wsteczne, jeśli ma on tylko jedna cyfra (na przykład `\2`) lub jeśli odnosi się do liczby grupa przechwytywania. (Zobacz [konstrukcje dopasowywania wstecznego](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Dopasowuje znak ASCII gdzie *nn* jest dwucyfrową szesnastkowego kodu znaku.|  
|`\c` *X*|Dopasowuje znak kontrolny ASCII, gdzie X jest literą znaku kontrolnego. Na przykład `\cC` to CTRL-C.|  
|`\u` *nnnn*|Dopasowuje jednostkę kodu UTF-16, którego wartością jest *nnnn* szesnastkowe. **Uwaga:** znak ucieczki Perl 5, który jest używany do określenia Unicode nie jest obsługiwana przez platformy .NET. Znak ucieczki Perl 5 ma postać `\x{` *####* `…}`, gdzie *####* `…` to seria cyfr szesnastkowych. Zamiast tego należy użyć `\u` *nnnn*.|  
|`\`|Gdy następuje znak, który nie jest rozpoznawany jako znak ucieczki, dopasowuje ten znak. Na przykład `\*` dopasowuje znak gwiazdki (*) i jest taka sama jak `\x2A`.|  
  
## <a name="an-example"></a>Przykład  
 Poniższy przykład ilustruje użycie sekwencje ucieczki znaków w wyrażeniu regularnym. Analizuje ciąg, który zawiera nazwy miast największych na świecie i ich populacji w 2009 roku. Każda nazwa miasta jest oddzielona od jego populację kartę (`\t`) lub pionowy pasek (&#124; lub `\u007c`). W poszczególnych miastach i ich populacji są oddzielone od siebie nawzajem powrotu karetki i wysuwu wiersza.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Wyrażenie regularne `\G(.+)[\t|\u007c](.+)\r?\n` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Rozpoczyna dopasowanie, gdzie zakończenia ostatniego dopasowania.|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
|`[\t\u007c]`|Zgodne karty (`\t`) lub pionowy pasek (&#124;).|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
|`\r?\n`|Dopasowuje zero lub jednego wystąpienia znaku powrotu karetki znak nowego wiersza.|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
