---
title: "Konstrukcje dopasowań w wyrażeniach regularnych"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a884e70f542c2ed7ff63e39cb7eadedf0ef7b4d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukcje dopasowań w wyrażeniach regularnych
Odwołania wstecznego zapewnić wygodny sposób identyfikowania powtarzających się znaków lub podciąg ciągu. Na przykład jeśli ciąg wejściowy zawiera wiele wystąpień dowolnego podciąg, można odpowiada pierwszego wystąpienia z grupą przechwytywanie, a następnie użyć dopasuje odpowiadające kolejne wystąpienia podciąg.  
  
> [!NOTE]
>  Oddzielne składni jest użyta w odwołaniu do nazwane i numerem grupy w ciągów zamiennych przechwycone. Aby uzyskać więcej informacji, zobacz [podstawienia](substitutions-in-regular-expressions.md).  
  
 .NET definiuje elementy oddzielne języka Aby odwołać się do grup przechwytywania numerowane i nazwane. Aby uzyskać więcej informacji na temat grup przechwytywania, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Numerowane odwołania wstecznego  
 Numerowane dopasuje używa następującej składni:  
  
 `\`*numer*  
  
 gdzie *numer* jest numerem porządkowym przechwytywania grupy w wyrażeniu regularnym. Na przykład `\4` odpowiada zawartość czwarty grupy przechwytywania. Jeśli *numer* nie jest zdefiniowany w wzorzec wyrażenia regularnego, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>. Na przykład, wyrażenie regularne `\b(\w+)\s\1` jest nieprawidłowe, ponieważ `(\w+)` jest pierwszy i tylko Przechwytywanie grupy w wyrażeniu. Z drugiej strony `\b(\w+)\s\2` jest nieprawidłowy i zgłasza wyjątek argumentu, ponieważ nie istnieje żadna grupa przechwytywania numerowane `\2`.  
  
 Należy zwrócić uwagę niejednoznaczności między kody ósemkowe ESC (takich jak `\16`) i `\` *numer* odwołania wstecznego, które używają tego samego notacji. Tę niejednoznaczność zostanie rozwiązany w następujący sposób:  
  
-   Wyrażenia `\1` za pośrednictwem `\9` zawsze będą interpretowane jako odwołania wstecznego, a nie jako ósemkowe kodów.  
  
-   Jeśli cyfry multidigit wyrażenia jest 8, 9 (takich jak `\80` lub `\91`), wyrażenia, jak jest interpretowana jako literału.  
  
-   Wyrażenia z `\10` i większa są traktowane jako odwołania wstecznego przypadku braku dopasowań, odpowiadającego do to numer, a w przeciwnym, są traktowane jako ósemkowe kodów.  
  
-   Jeśli wyrażenie regularne zawiera dopasuje do niezdefiniowanego numeru grupy, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 Jeśli niejednoznaczności problem, można użyć `\k<` *nazwa* `>` zapisu, który jest jednoznaczne i nie należy mylić jej z kodów ósemkowe znaków. Podobnie, takich jak liczba szesnastkowa kodów `\xdd` są jednoznaczne i nie należy mylić jej z odwołania wstecznego.  
  
 Poniższy przykład umożliwia znalezienie podwójna word znaków w ciągu. Definiuje wyrażenie regularne `(\w)\1`, który składa się z następujących elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasowuje znak słowa i przypisz je do pierwszej grupy przechwytywania.|  
|`\1`|Zgodne następny znak, który jest taka sama jak wartość w pierwszej grupy przechwytywania.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Nazwane odwołania wstecznego  
 Nazwane dopasuje jest definiowana za pomocą następującej składni:  
  
 `\k<`*nazwa*`>`  
  
 lub:  
  
 `\k'`*nazwa*`'`  
  
 gdzie *nazwa* to nazwa grupy przechwytywania zdefiniowanej w wzorzec wyrażenia regularnego. Jeśli *nazwa* nie jest zdefiniowany w wzorzec wyrażenia regularnego, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 Poniższy przykład umożliwia znalezienie podwójna word znaków w ciągu. Definiuje wyrażenie regularne `(?<char>\w)\k<char>`, który składa się z następujących elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`(?<char>\w)`|Dopasowuje znak słowa i przypisz je do przechwytywania grupę o nazwie `char`.|  
|`\k<char>`|Następny znak, który jest taka sama jak wartość odpowiada `char` Przechwytywanie grupy.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 Należy pamiętać, że *nazwa* można także reprezentację liczby. Na przykład w poniższym przykładzie użyto wyrażenia regularnego `(?<2>\w)\k<2>` można znaleźć w ciągu znaków podwójna słów.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a>Jakie dopasowania odwołania wstecznego  
 Dopasuje odwołuje się do najnowszych definicji grupy (definicja najbardziej bezpośrednio po lewej, podczas dopasowywania od lewej do prawej). Gdy ułatwia grupy, który przechwytuje wielu, dopasuje odwołuje się do najnowszych przechwytywania.  
  
 Poniższy przykład zawiera wzorzec wyrażenia regularnego, `(?<1>a)(?<1>\1b)*`, które ponownie definiuje \1 o nazwie grupy. W poniższej tabeli opisano każdy wzorzec wyrażenia regularnego.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<1>a)`|Dopasowanie znaku "a" i przypisz wynik do przechwytywania grupy o nazwie `1`.|  
|`(?<1>\1b)*`|Wystąpienie dopasowania 0 lub 1 grupę o nazwie `1` wraz z "b" i przypisz wynik do przechwytywania grupy o nazwie `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 W porównaniu z wyrażeniem regularnym z ciągu wejściowego ("aababb"), aparat wyrażeń regularnych wykonuje następujące operacje:  
  
1.  Rozpoczyna się od początku ciągu i pomyślnie zgodny "a" na wyrażenie `(?<1>a)`. Wartość `1` grupy jest teraz "".  
  
2.  Przechodzi do drugiego znaku i pomyślnie pasującej do ciągu "ab" za pomocą wyrażenia `\1b`, lub "ab". Następnie przypisuje wynik "ab", aby `\1`.  
  
3.  Zmienia jego czwarty znak. Wyrażenie `(?<1>\1b)` jest być dopasowane zero lub więcej razy, aby go pomyślnie pasującej do ciągu "abb" za pomocą wyrażenia `\1b`. Przypisuje wynik "abb", przywracając `\1`.  
  
 W tym przykładzie `*` jest pętli kwantyfikatora — ocena wielokrotnie aż aparat wyrażeń regularnych nie jest zgodna z wzorcem definiuje. Kwantyfikatory pętli nie usuwaj definicje grup.  
  
 Jeśli grupa nie ma przechwycone żadnych podciągów, dopasowań dla tej grupy nie jest zdefiniowana i nigdy nie jest zgodna. Jest to zilustrowane wzorzec wyrażenia regularnego `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, która jest zdefiniowana w następujący sposób:  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij dopasowania na granicy programu word.|  
|`(\p{Lu}{2})`|Zgodne dwie wielkie litery. Jest to pierwsza grupa przechwytywania.|  
|`(\d{2})?`|Zgodne wystąpienie zero lub jeden z dwóch cyfr dziesiętnych. Jest to druga grupa przechwytywania.|  
|`(\p{Lu}{2})`|Zgodne dwie wielkie litery. Jest to trzecia grupa przechwytywania.|  
|`\b`|W celu dopasowania na granicy programu word.|  
  
 Ciąg wejściowy można dopasować tego wyrażenia regularnego, nawet jeśli nie występują dwa cyfr dziesiętnych, które są definiowane przez drugiej grupy przechwytywania. W poniższym przykładzie pokazano, czy mimo że dopasowanie jest pomyślne, pustej grupy przechwytywania znajduje się między dwie grupy przechwytywania powiodło się.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
