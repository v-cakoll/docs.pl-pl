---
title: Konstrukcje dopasowań w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7953e34f76e23e3f9f4913726adc4b2176b172c9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884305"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukcje dopasowań w wyrażeniach regularnych
Dopasowywania wstecznego zapewniają wygodny sposób identyfikowania powtarzających się znaków lub podciągu wewnątrz ciągu. Na przykład jeśli ciąg wejściowy zawiera wiele wystąpień dowolnego podciąg, można dopasować pierwsze wystąpienie z grupy przechwytywania, a następnie należy użyć dopasowywania wstecznego do dopasowania pozostałe wystąpienia podciągu.  
  
> [!NOTE]
>  Oddzielne składnia jest używana do odwoływania się do nazwanych i numerowanej grupy w ciągach zastąpienie przechwytywania. Aby uzyskać więcej informacji, zobacz [podstawienia](substitutions-in-regular-expressions.md).  
  
 .NET definiuje elementy języka oddzielnych do odwoływania się do numerowane i nazwanych grup przechwytywania. Aby uzyskać więcej informacji na temat grupy przechwytywania, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="numbered-backreferences"></a>Numerowany dopasowywania wstecznego  
 Numerowany dopasowywania wstecznego używa następującej składni:  
  
 `\` *Numer*  
  
 gdzie *numer* jest numerem porządkowym grupy przechwytywania w wyrażeniu regularnym. Na przykład `\4` pasuje do zawartości czwarty grupa przechwytywania. Jeśli *numer* jest niezdefiniowana we wzorcu wyrażenia regularnego, występuje błąd analizy, i zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>. Na przykład, wyrażenie regularne `\b(\w+)\s\1` jest prawidłowy, ponieważ `(\w+)` jest pierwszą i jedyną grupa przechwytywania w wyrażeniu. Z drugiej strony `\b(\w+)\s\2` jest nieprawidłowy i zgłasza wyjątek argumentu, ponieważ nie istnieje żadna grupa przechwytywania numerowane `\2`. Ponadto jeśli *numer* identyfikuje grupy przechwytywania w określonym położeniu porządkowe, ale ta grupa przechwytywania przypisano liczbową nazwa różni się od jego porządkowym, analizator składni wyrażeń regularnych generuje również <xref:System.ArgumentException>. 
  
 Należy pamiętać, niejednoznaczności między kody unikowe ósemkowe (takie jak `\16`) i `\` *numer* dopasowywania wstecznego, użyj takiej samej notacji. Tę niejednoznaczność zostanie rozwiązany w następujący sposób:  
  
-   Wyrażenia `\1` za pośrednictwem `\9` są zawsze interpretowane jako odwołania wsteczne, a nie jako ósemkowe kodów.  
  
-   Jeżeli pierwsza cyfra multidigit wyrażenie jest 8 i 9 (takie jak `\80` lub `\91`), wyrażeń, jak interpretować jako literał.  
  
-   Wyrażenia z `\10` i większa jest uznawana za odwołaniem wstecznym, jeśli istnieje odwołanie wsteczne odpowiadającej pozycji oznacza numer; w przeciwnym razie, są interpretowane jako ósemkowe kodów.  
  
-   Jeśli wyrażenie regularne zawiera odwołanie wsteczne numer nedefinovanou, wystąpi błąd podczas analizowania, i zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 W przypadku niejednoznaczności problemu, można użyć `\k<` *nazwa* `>` notacji, która jest jednoznaczny i nie należy mylić z kody znaków ósemkowych. Podobnie, szesnastkowe kody takich jak `\xdd` jednoznaczne i nie należy mylić z odwołań wstecznych.  
  
 Poniższy przykład umożliwia znalezienie word podwojone znaki w ciągu. Definiuje wyrażenie regularne `(\w)\1`, który składa się z następujących elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasuj znak wyrazu i przypisać je do pierwszej grupy przechwytywania.|  
|`\1`|Dopasowuje znak dalej, która jest taka sama jak wartość pierwszą grupę przechwytywania.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>Nazwane dopasowywania wstecznego  
 Nazwane dopasowanie wsteczne to zdefiniowane przy użyciu następującej składni:  
  
 `\k<` *Nazwa* `>`  
  
 lub:  
  
 `\k'` *Nazwa* `'`  
  
 gdzie *nazwa* to nazwa grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego. Jeśli *nazwa* jest niezdefiniowana we wzorcu wyrażenia regularnego, występuje błąd analizy, i zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 Poniższy przykład umożliwia znalezienie word podwojone znaki w ciągu. Definiuje wyrażenie regularne `(?<char>\w)\k<char>`, który składa się z następujących elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`(?<char>\w)`|Dopasuj znak wyrazu i przypisz je do grupy przechwytywania o nazwie `char`.|  
|`\k<char>`|Następny znak, który jest taka sama jak wartość dopasowania `char` grupa przechwytywania.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  

## <a name="named-numeric-backreferences"></a>O nazwie liczbowych dopasowywania wstecznego

W nazwane dopasowanie wsteczne z `\k`, *nazwa* może być również ciąg reprezentujący liczbę. Na przykład w poniższym przykładzie użyto wyrażenia regularnego `(?<2>\w)\k<2>` można znaleźć słowo podwojone znaki w ciągu. W takim przypadku w przykładzie zdefiniowano grupę przechwytywania, jawnie o nazwie "2", a odwołanie wsteczne odpowiednio o nazwie "2". 
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  

Jeśli *nazwa* to ciąg reprezentujący liczbę, a nie grupy przechwytywania tej samej nazwie, `\k<` *nazwa* `>` jest taka sama jak odwołanie wsteczne `\`  *Liczba*, gdzie *numer* jest numerem porządkowym przechwytywania. W poniższym przykładzie jest pojedynczy grupa przechwytywania o nazwie `char`. Konstrukcja dopasowywania wstecznego odwołuje się do niego jako `\k<1>`. Jak wynika z w przykładzie pokazano wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> powiedzie się, ponieważ `char` jest pierwszą grupę przechwytywania.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]  

Jednak jeśli *nazwa* jest ciąg reprezentujący liczbę, a grupy przechwytywania w, że pozycja jawnie przypisano nazwy liczbowej, analizator składni wyrażeń regularnych nie może zidentyfikować grupa przechwytywania przez jego porządkowym . Zamiast tego wyniku weryfikacji zgłasza wyjątek <xref:System.ArgumentException>. Tylko grupy przechwytywania w poniższym przykładzie nosi nazwę "2". Ponieważ `\k` koncept jest wykorzystywany do definiowania odwołanie wsteczne o nazwie "1", analizator składni wyrażeń regularnych nie może zidentyfikować pierwszą grupę przechwytywania i zgłasza wyjątek.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]  

## <a name="what-backreferences-match"></a>Jakie dopasowanie dopasowywania wstecznego  
 Odwołanie wsteczne odnosi się do najnowszych definicji grupy (definicja najbardziej natychmiast po lewej stronie, podczas dopasowywania od lewej do prawej). Gdy ułatwia grupy, który przechwytuje wielu, odwołanie wsteczne odnosi się do przechwytywania najbardziej aktualne.  
  
 Poniższy przykład zawiera wzorzec wyrażenia regularnego `(?<1>a)(?<1>\1b)*`, które ponownie definiuje \1 o nazwie grupy. W poniższej tabeli opisano każdy wzorzec w wyrażeniu regularnym.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<1>a)`|Dopasowuje znak "a" i przypisz wynik do grupy przechwytywania o nazwie `1`.|  
|`(?<1>\1b)*`|Wystąpienie dopasowania 0 lub 1 grupę o nazwie `1` wraz z "b" i przypisz wynik do grupa przechwytywania o nazwie `1`.|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 Przy porównywaniu wyrażenia regularnego do ciągu wejściowego ("aababb"), aparat wyrażeń regularnych wykonuje następujące operacje:  
  
1.  Rozpoczyna się od początku ciągu i dopasowuje pomyślnie "" z wyrażeniem `(?<1>a)`. Wartość `1` grupy jest teraz "".  
  
2.  Przechodzi do drugim znakiem i pomyślnie pasuje do ciągu "ab" z wyrażeniem `\1b`, lub "ab". Następnie przypisuje wynik, "ab", aby `\1`.  
  
3.  Przechodzi do czwartej znaków. Wyrażenie `(?<1>\1b)` to być dopasowane zero lub więcej razy, więc go pomyślnie pasuje do ciągu "abb" z wyrażeniem `\1b`. Przypisuje wynik, "abb", wróć do `\1`.  
  
 W tym przykładzie `*` jest pętli kwantyfikator — zostanie ono ocenione wielokrotnie, dopóki aparat wyrażeń regularnych nie pasuje do wzorca, definiuje. Kwantyfikatory pętli nie usuwaj zaznaczenia opcji definicje grup.  
  
 Jeśli grupa nie przechwytywane podciągi wszelkie odwołaniem wstecznym do tej grupy jest nieokreślone i nigdy nie jest zgodny. Jest to zilustrowane przez wzorzec wyrażenia regularnego `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, która została zdefiniowana w następujący sposób:  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\p{Lu}{2})`|Dopasowuje dwie wielkie litery. Jest to pierwsza grupa przechwytywania.|  
|`(\d{2})?`|Dopasowanie zera lub jednego wystąpienia dwóch cyfr dziesiętnych. Jest to druga grupa przechwytywania.|  
|`(\p{Lu}{2})`|Dopasowuje dwie wielkie litery. Jest to trzecia grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy wyrazu.|  
  
 Ciąg wejściowy można dopasować tego wyrażenia regularnego, nawet jeśli nie są dwie cyfry dziesiętne, które są definiowane przez to druga grupa przechwytywania. Poniższy przykład pokazuje, czy mimo, że dopasowanie się powiedzie, pustej grupy przechwytywania znajduje się między dwiema grupami przechwytywania pomyślne.  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
