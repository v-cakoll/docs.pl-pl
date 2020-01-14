---
title: Znak ucieczki w wyrażeniach regularnych programu .NET
description: Informacje o znakach specjalnych i znakach ucieczki w wyrażeniach regularnych programu .NET.
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711431"
---
# <a name="character-escapes-in-regular-expressions"></a>Znaki specjalne w wyrażeniach regularnych
Ukośnik odwrotny (\\) w wyrażeniu regularnym wskazuje jedną z następujących wartości:  
  
- Znak, który następuje po nim jest znakiem specjalnym, jak pokazano w tabeli w poniższej sekcji. Na przykład `\b` jest zakotwiczeniem wskazującym, że dopasowanie wyrażenia regularnego powinno rozpoczynać się od granicy słowa, `\t` reprezentuje kartę, a `\x020` reprezentuje spację.  
  
- Znak, który w przeciwnym razie mógłby być interpretowany jako nieucieczka konstrukcja języka, należy interpretować dosłownie. Na przykład nawiasy klamrowe (`{`) rozpoczynają definicję kwantyfikatora, ale ukośnik odwrotny, po którym następuje nawias klamrowy (`\{`), wskazuje, że aparat wyrażeń regularnych powinien być zgodny z nawiasem klamrowym. Podobnie pojedynczy ukośnik odwrotny oznacza początek konstrukcji języka o zmienionym znaczeniu, ale dwa ukośniki odwrotne (`\\`) wskazują, że aparat wyrażeń regularnych powinien być zgodny z ukośnikiem odwrotnym.  
  
> [!NOTE]
> Znaki ucieczki są rozpoznawane w wzorcach wyrażeń regularnych, ale nie w wzorcach zastępczych.  
  
## <a name="character-escapes-in-net"></a>Znak ucieczki w programie .NET  
 W poniższej tabeli wymieniono znaki ucieczki obsługiwane przez wyrażenia regularne w programie .NET.  
  
|Znak lub sekwencja|Opis|  
|---------------------------|-----------------|  
|Wszystkie znaki z wyjątkiem następujących:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |Znaki inne niż wymienione w kolumnie **znak lub sekwencja** nie mają specjalnego znaczenia w wyrażeniach regularnych; są one zgodne.<br /><br /> Znaki zawarte w **znakach lub kolumnie sekwencji** są specjalnymi elementami języka wyrażeń regularnych. Aby można było dopasować je w wyrażeniu regularnym, muszą one być zmienione lub dołączone do [grupy znaków pozytywnych](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Na przykład wyrażenie regularne `\$\d+` lub `[$]\d+` pasuje do "$1200".|  
|`\a`|Dopasowuje znak dzwonka (alarm), `\u0007`.|  
|`\b`|W `[`*character_group*`]` Klasa znaku dopasowuje spację, `\u0008`.  (Zobacz [klasy znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)). Poza klasą znaku `\b` jest kotwicą pasującą do granicy słowa. (Zobacz [kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md)).|  
|`\t`|Dopasowuje kartę `\u0009`.|  
|`\r`|Dopasowuje znak powrotu karetki, `\u000D`. Należy pamiętać, że `\r` nie jest odpowiednikiem znaku nowego wiersza, `\n`.|  
|`\v`|Dopasowuje zakładkę pionową `\u000B`.|  
|`\f`|Dopasowuje kanał informacyjny formularza, `\u000C`.|  
|`\n`|Dopasowuje nowy wiersz, `\u000A`.|  
|`\e`|Dopasowuje znak ucieczki `\u001B`.|  
|`\` *nnn*|Dopasowuje znak ASCII, gdzie *nnn* składa się z dwóch lub trzech cyfr reprezentujących kod znaku ósemkowego. Na przykład `\040` reprezentuje znak spacji. Ta konstrukcja jest interpretowana jako odwołanie wsteczne, jeśli ma tylko jedną cyfrę (na przykład `\2`) lub jeśli odpowiada liczbie grupy przechwytywania. (Zobacz [konstrukcje odwołań wstecznych](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md)).|  
|`\x` *nn*|Dopasowuje znak ASCII, gdzie *NN* jest dwucyfrowym kodem znaku szesnastkowego.|  
|`\c` *X*|Dopasowuje znak kontrolny ASCII, gdzie X jest literą znaku kontrolnego. Na przykład `\cC` jest CTRL-C.|  
|`\u` *nnnn*|Dopasowuje jednostkę kodu UTF-16, której wartość to *nnnn* szesnastkowa. **Uwaga:**  Język Perl 5 znaku ucieczki, który jest używany do określenia Unicode, nie jest obsługiwany przez platformę .NET. Znak w języku Perl 5 ma postać `\x{` *####* `…}`, gdzie *####* `…` to seria cyfr szesnastkowych. Zamiast tego należy użyć `\u`*nnnn*.|  
|`\`|Gdy następuje znak, który nie jest rozpoznawany jako znak ucieczki, dopasowuje ten znak. Na przykład `\*` dopasowuje znak gwiazdki (*) i jest taka sama jak `\x2A`.|  
  
## <a name="an-example"></a>Przykład  
 Poniższy przykład ilustruje użycie znaku ucieczki w wyrażeniu regularnym. Analizuje ciąg, który zawiera nazwy największych miast i ich populacje w 2009. Nazwy poszczególnych miast są oddzielone od populacji przez kartę (`\t`) lub pionowy pasek (&#124; lub `\u007c`). Poszczególne miasta i ich populacje są oddzielone od siebie przez powrotu karetki i wysuwu wiersza.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 Wyrażenie regularne `\G(.+)[\t|\u007c](.+)\r?\n` jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\G`|Rozpocznij dopasowanie, gdzie zostało zakończone ostatnie dopasowanie.|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
|`[\t\u007c]`|Dopasowuje kartę (`\t`) lub pionowy pasek (&#124;).|  
|`(.+)`|Dopasowuje dowolny znak jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
|`\r?\n`|Dopasowanie do zera lub jednego wystąpienia znaku powrotu karetki, po którym następuje nowy wiersz.|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
