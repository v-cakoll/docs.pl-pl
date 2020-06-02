---
title: Konstrukcje odwołań wstecznych w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak identyfikować powtarzające się elementy tekstowe przy użyciu konstrukcji odwołań wstecznych w wyrażeniu regularnym.
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
ms.openlocfilehash: 87c3dbde2eb2b5a19b91f34bb2b088af5c0d1827
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290607"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukcje dopasowań w wyrażeniach regularnych

Odwołania wsteczne zapewniają wygodny sposób identyfikowania Powtórzonego znaku lub podciągu w ciągu. Na przykład, jeśli ciąg wejściowy zawiera wiele wystąpień dowolnego podciągu, można dopasować pierwsze wystąpienie z grupą przechwytywania, a następnie użyć odwołania wstecznego, aby dopasować kolejne wystąpienia podciągu.

> [!NOTE]
> Oddzielna składnia jest używana do odwoływania się do nazwanych i numerowanych grup przechwytywania w ciągach zamiennych. Aby uzyskać więcej informacji, zobacz [podstawianie](substitutions-in-regular-expressions.md).

Platforma .NET definiuje oddzielne elementy języka, aby można było odwoływać się do numerowanych i nazwanych grup przechwytywania. Aby uzyskać więcej informacji na temat przechwytywania grup, zobacz [Grouping konstrukcjes](grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Numerowane odwołania

Numerowane odwołanie używa następującej składni:

`\`*Liczba*

gdzie *Number* jest pozycją porządkową grupy przechwytywania w wyrażeniu regularnym. Na przykład `\4` dopasowuje zawartość czwartej grupy przechwytywania. Jeśli *Liczba* nie jest zdefiniowana we wzorcu wyrażenia regularnego, wystąpi błąd analizy, a aparat wyrażeń regularnych zgłasza <xref:System.ArgumentException> . Na przykład wyrażenie regularne `\b(\w+)\s\1` jest prawidłowe, ponieważ `(\w+)` jest pierwszą i jedyną grupą przechwytywania w wyrażeniu. Z drugiej strony `\b(\w+)\s\2` jest nieprawidłowa i zgłasza wyjątek argumentu, ponieważ nie ma numerowanej grupy przechwytywania `\2` . Ponadto, jeśli *Liczba* identyfikuje grupę przechwytywania w określonej pozycji porządkowej, ale do grupy przechwytywania jest przypisana nazwa różna od jej pozycji porządkowej, Analizator wyrażeń regularnych również wygeneruje <xref:System.ArgumentException> .

Zwróć uwagę na niejednoznaczność między ósemkowymi kodami ucieczki (takimi jak `\16` ) i `\` *numerami* odwołań wstecznych, które używają tej samej notacji. Ta niejednoznaczność jest rozpoznawana w następujący sposób:

- Wyrażenia `\1` przez `\9` są zawsze interpretowane jako odwołania wsteczne, a nie jako kody ósemkowe.

- Jeśli Pierwsza cyfra wyrażenia wielocyfrowego wynosi 8 lub 9 (na przykład `\80` lub `\91` ), wyrażenie jako literał.

- Wyrażenia z `\10` i są uznawane za odwołania wsteczne, jeśli istnieje odwołanie wsteczne odpowiadające temu numerowi; w przeciwnym razie są interpretowane jako kody ósemkowe.

- Jeśli wyrażenie regularne zawiera odwołanie wsteczne do niezdefiniowanego numeru grupy, wystąpi błąd analizy, a aparat wyrażeń regularnych zgłasza <xref:System.ArgumentException> .

Jeśli niejednoznaczność to problem, można użyć `\k<` *name* `>` notacji nazwy, która jest niejednoznaczna i nie można jej pomylić z kodami znaków ósemkowych. Podobnie kody szesnastkowe, takie jak `\xdd` są niejednoznaczne i nie można ich mylić z odwołaniami wstecznymi.

Poniższy przykład umożliwia znalezienie podwójnych znaków wyrazu w ciągu. Definiuje wyrażenie regularne, `(\w)\1` które składa się z następujących elementów.

|Element|Opis|
|-------------|-----------------|
|`(\w)`|Dopasowuje znak słowa i przypisuje go do pierwszej grupy przechwytywania.|
|`\1`|Dopasowuje następny znak, który jest taki sam jak wartość pierwszej grupy przechwytywania.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Nazwane odwołania wsteczne

Nazwane odwołanie wsteczne jest zdefiniowane przy użyciu następującej składni:

`\k<`*Nazwa*`>`

lub:

`\k'`*Nazwa*`'`

gdzie *name* to nazwa grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego. Jeśli *Nazwa* nie jest zdefiniowana we wzorcu wyrażenia regularnego, wystąpi błąd analizy, a aparat wyrażeń regularnych zgłasza <xref:System.ArgumentException> .

Poniższy przykład umożliwia znalezienie podwójnych znaków wyrazu w ciągu. Definiuje wyrażenie regularne, `(?<char>\w)\k<char>` które składa się z następujących elementów.

|Element|Opis|
|-------------|-----------------|
|`(?<char>\w)`|Dopasowuje znak słowa i przypisuje go do grupy przechwytywania o nazwie `char` .|
|`\k<char>`|Dopasowuje następny znak, który jest taki sam jak wartość `char` grupy przechwytywania.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Nazwane odwołania wsteczne

W nazwie odwołanie wsteczne z `\k` , *Nazwa* może być również ciągiem reprezentującym liczbę. Na przykład poniższy przykład używa wyrażenia regularnego, `(?<2>\w)\k<2>` Aby znaleźć podwójne znaki wyrazu w ciągu. W tym przypadku przykład definiuje grupę przechwytywania, która jest jawnie o nazwie "2", a odwołanie wsteczne jest zgodne o nazwie "2".

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Jeśli *Nazwa* jest reprezentacją liczby, a żadna grupa przechwytywania nie ma tej nazwy, `\k<` *Nazwa* `>` jest taka sama jak numer odwołania wstecznego `\` *number*, gdzie *Number* jest pozycją porządkową przechwytywania. W poniższym przykładzie istnieje Pojedyncza grupa przechwytywania o nazwie `char` . Konstrukcja odwołania wstecznego odwołuje się do niego jako `\k<1>` . Jak wynika z przykładu, wywołanie do <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> powiedzie się, ponieważ jest to `char` Pierwsza grupa przechwytywania.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Jeśli jednak *Nazwa* jest reprezentacją liczby, a grupa przechwytywania w tym położeniu została jawnie przypisana nazwą liczbową, Analizator wyrażenia regularnego nie może zidentyfikować grupy przechwytywania według jej pozycji porządkowej. Zamiast tego zgłasza <xref:System.ArgumentException> . Jedyną grupą przechwytywania w poniższym przykładzie jest nazwa "2". Ponieważ `\k` konstrukcja jest używana do definiowania odwołania wstecznego o nazwie "1", Analizator wyrażenia regularnego nie może zidentyfikować pierwszej grupy przechwytywania i zgłasza wyjątek.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Dopasowanie wsteczne

Odwołanie wsteczne odwołuje się do ostatniej definicji grupy (od razu do lewej, gdy dopasowuje od lewej do prawej). Gdy grupa wykonuje wiele przechwycenia, odwołanie wsteczne odwołuje się do ostatniego przechwycenia.

Poniższy przykład zawiera wzorzec wyrażenia regularnego, `(?<1>a)(?<1>\1b)*` który ponownie definiuje nazwaną grupę \ 1. W poniższej tabeli opisano każdy wzorzec w wyrażeniu regularnym.

|Wzorce|Opis|
|-------------|-----------------|
|`(?<1>a)`|Dopasowuje znak "a" i przypisuje wynik do grupy przechwytywania o nazwie `1` .|
|`(?<1>\1b)*`|Dopasowuje zero lub więcej wystąpień grupy o nazwie `1` "b" i przypisuje wynik do grupy przechwytywania o nazwie `1` .|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

W porównaniu do wyrażenia regularnego z ciągiem wejściowym ("aababb") aparat wyrażeń regularnych wykonuje następujące operacje:

1. Rozpoczyna się na początku ciągu i pomyślnie dopasowuje znak "a" przy użyciu wyrażenia `(?<1>a)` . Wartość `1` grupy jest teraz "a".

2. Przechodzi do drugiego znaku i pomyślnie pasuje do ciągu "AB" przy użyciu wyrażenia `\1b` lub "AB". Następnie przypisuje wynik "AB" do `\1` .

3. Przechodzi do czwartego znaku. Wyrażenie `(?<1>\1b)*` ma być dopasowane do zera lub więcej razy, więc pomyślnie pasuje do ciągu "ABB" z wyrażeniem `\1b` . Przypisuje wynik "ABB", z powrotem do `\1` .

W tym przykładzie jest to kwantyfikator cykliczny `*` — jest oceniany wielokrotnie do momentu, gdy aparat wyrażeń regularnych nie będzie pasował do zdefiniowanego wzorca. Kwantyfikatory w pętli nie usuwają definicji grup.

Jeśli grupa nie przechwytuje żadnych podciągów, odwołanie wsteczne do tej grupy jest niezdefiniowane i nigdy nie jest zgodne. Jest to zilustrowane przez wzorzec wyrażenia regularnego `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` , który jest zdefiniowany w następujący sposób:

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Rozpocznij dopasowanie na granicy słowa.|
|`(\p{Lu}{2})`|Dopasowuje dwie wielkie litery. Jest to pierwsza grupa przechwytywania.|
|`(\d{2})?`|Dopasowanie do zera lub jednego wystąpienia dwóch cyfr dziesiętnych. Jest to druga grupa przechwytywania.|
|`(\p{Lu}{2})`|Dopasowuje dwie wielkie litery. Jest to trzecia grupa przechwytywania.|
|`\b`|Zakończ dopasowanie na granicy słowa.|

Ciąg wejściowy może być zgodny z tym wyrażeniem regularnym, nawet jeśli nie ma dwóch cyfr dziesiętnych, które są zdefiniowane przez drugą grupę przechwytywania. Poniższy przykład pokazuje, że mimo że dopasowanie się powiedzie, zostanie znaleziona pusta grupa przechwytywania między dwiema pomyślnymi grupami przechwytywania.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
