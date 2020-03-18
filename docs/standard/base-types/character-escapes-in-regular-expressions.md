---
title: Unika znaków w wyrażeniach regularnych .NET
description: Dowiedz się więcej o znakach specjalnych i unikanych znakach w wyrażeniach regularnych .NET.
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
ms.openlocfilehash: 82e60b3cb5eb777d48219209550367642f78d8c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711431"
---
# <a name="character-escapes-in-regular-expressions"></a>Znaki specjalne w wyrażeniach regularnych
Ukośnik\\odwrotny ( ) w wyrażeniu regularnym wskazuje jedną z następujących czynności:  
  
- Poniższa po nim postać jest znakiem specjalnym, jak pokazano w tabeli w poniższej sekcji. Na przykład `\b` jest kotwicą, która wskazuje, że dopasowanie wyrażenia `\t` regularnego powinno rozpocząć `\x020` się na granicy wyrazu, reprezentuje kartę i reprezentuje spację.  
  
- Znak, który w przeciwnym razie byłby interpretowany jako konstrukcja języka nieuciekł należy interpretować dosłownie. Na przykład nawias`{`klamrowy ( ) rozpoczyna definicję kwantyfikatora, ale ukośnik odwrotny, po którym następuje klamra (`\{`) wskazuje, że aparat wyrażeń regularnych powinien odpowiadać nawiasowi klamry. Podobnie pojedynczy ukośnik odwrotny oznacza początek konstrukcji języka, który uciekł, ale dwa ukośniki wsteczne (`\\`) wskazują, że aparat wyrażeń regularnych powinien odpowiadać ukośnikowi odwrotnemu.  
  
> [!NOTE]
> Ucieczki znaków są rozpoznawane we wzorcach wyrażeń regularnych, ale nie we wzorcach zastępczych.  
  
## <a name="character-escapes-in-net"></a>Postać ucieka w .NET  
 W poniższej tabeli wymieniono znaki, które są obsługiwane przez wyrażenia regularne w .NET.  
  
|Znak lub sekwencja|Opis|  
|---------------------------|-----------------|  
|Wszystkie znaki z wyjątkiem następujących elementów:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Znaki inne niż wymienione w kolumnie **Znak lub sekwencja** nie mają specjalnego znaczenia w wyrażeniach regularnych; pasują do siebie.<br /><br /> Znaki zawarte w **kolumnie Znak lub sekwencja** są specjalnymi elementami języka wyrażenia regularnego. Aby dopasować je w wyrażeniu regularnym, muszą zostać uniknięte lub uwzględnione w [grupie znaków dodatnich.](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) Na przykład wyrażenie `\$\d+` regularne `[$]\d+` lub pasuje do "$1200".|  
|`\a`|Dopasowuje znak dzwonka `\u0007`(alarmu), .|  
|`\b`|W klasie znaków *character_group* `]` pasuje do `\u0008`backspace, . `[`  (Zobacz [klasy znaków.)](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) Poza klasą `\b` znaków jest kotwicą, która pasuje do granicy słowa. (Zobacz [Kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Dopasowuje `\u0009`kartę .|  
|`\r`|Pasuje do powrotu karetki, `\u000D`. Należy `\r` zauważyć, że nie jest `\n`odpowiednikiem znaku nowego wiersza, .|  
|`\v`|Pasuje do pionowej karty . `\u000B`.|  
|`\f`|Dopasowuje kanał `\u000C`informacyjny formularza, .|  
|`\n`|Pasuje do nowej `\u000A`linii, .|  
|`\e`|Pasuje do `\u001B`ucieczki, .|  
|`\`*nnn (nnn)*|Dopasowuje znak ASCII, gdzie *nnn* składa się z dwóch lub trzech cyfr reprezentujących kod znaku ósemkowego. Na przykład `\040` reprezentuje znak spacji. Ta konstrukcja jest interpretowana jako odwołanie wsteczne, `\2`jeśli ma tylko jedną cyfrę (na przykład) lub jeśli odpowiada liczbie grupy przechwytywania. (Zobacz [Backreference Konstrukcje](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x`*nn*|Dopasowuje znak ASCII, gdzie *nn* jest dwucyfrowym kodem szesnastkowym.|  
|`\c` *X*|Dopasowuje znak kontrolny ASCII, gdzie X jest literą znaku kontrolnego. Na przykład `\cC` jest CTRL-C.|  
|`\u`*nnnn (nnnn)*|Dopasowuje jednostkę kodu UTF-16, której wartość jest *nnnn* szesnastkowa. **Uwaga:**  Ucieczka znaków Perla 5, która jest używana do określania Unicode, nie jest obsługiwana przez .NET. Ucieczka znaków Perla 5 `\x{` *####* `…}`ma *####* `…` formę , gdzie jest seria cyfr szesnastkowych. Zamiast tego `\u`należy użyć *nnnn*.|  
|`\`|Po nadaniu znaku, który nie jest rozpoznawany jako znak uciekł, dopasowuje ten znak. Na przykład `\*` pasuje do gwiazdki (*) i `\x2A`jest taka sama jak .|  
  
## <a name="an-example"></a>Przykład  
 Poniższy przykład ilustruje użycie znaków ucieka w wyrażeniu regularnym. Analizuje ciąg, który zawiera nazwy największych miast na świecie i ich populacji w 2009 roku. Każda nazwa miasta jest oddzielona`\t`od jego populacji kartą `\u007c`( ) lub pionowym paskiem (&#124; lub ). Poszczególne miasta i ich populacje są oddzielone od siebie transportem powrotnym i kanałem liniowym.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Wyrażenie `\G(.+)[\t|\u007c](.+)\r?\n` regularne jest interpretowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij mecz, w którym zakończył się ostatni mecz.|  
|`(.+)`|Dopasuj dowolną postać jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
|`[\t\u007c]`|Dopasuj`\t`kartę ( ) lub pionowy pasek (&#124;).|  
|`(.+)`|Dopasuj dowolną postać jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
|`\r?\n`|Dopasuj zero lub jedno wystąpienie powrotu karetki, po którym następuje nowy wiersz.|  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
