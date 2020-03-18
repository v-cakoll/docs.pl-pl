---
title: Konstrukcje backreference w wyrażeniach regularnych .NET
description: Dowiedz się, jak zidentyfikować powtarzające się elementy tekstowe przy użyciu konstrukcji backreference w wyrażeniu regularnym.
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
ms.openlocfilehash: 905578d763ebe5d5b8eb96a9056fbe11fbfab137
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711535"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Konstrukcje dopasowań w wyrażeniach regularnych

Odwołania wsteczne zapewniają wygodny sposób identyfikowania powtarzającego się znaku lub podciągu w ciągu. Na przykład jeśli ciąg wejściowy zawiera wiele wystąpień dowolnego podciągu, można dopasować pierwsze wystąpienie do grupy przechwytywania, a następnie użyć odwołania wstecznego, aby dopasować kolejne wystąpienia podciągu.

> [!NOTE]
> Oddzielna składnia jest używana do odwoływania się do nazwanych i numerowanych grup przechwytywania w ciągach zastępczych. Aby uzyskać więcej informacji, zobacz [Podstawienia](substitutions-in-regular-expressions.md).

Program .NET definiuje oddzielne elementy języka w celu odwoływania się do ponumerowanych i nazwanych grup przechwytywania. Aby uzyskać więcej informacji na temat przechwytywania grup, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Numerowane odwołania wsteczne

Numerowane odwołanie wsteczne używa następującej składni:

`\` *numer*

gdzie *liczba* jest pozycją liczbową grupy przechwytywania w wyrażeniu regularnym. Na przykład `\4` pasuje do zawartości czwartej grupy przechwytywania. Jeśli *liczba* nie jest zdefiniowana we wzorcu wyrażenia regularnego, występuje błąd analizy, a aparat wyrażeń regularnych zgłasza plik <xref:System.ArgumentException>. Na przykład wyrażenie `\b(\w+)\s\1` regularne jest `(\w+)` prawidłowy, ponieważ jest pierwszym i tylko przechwytywania grupy w wyrażeniu. Z drugiej strony `\b(\w+)\s\2` jest nieprawidłowy i zgłasza wyjątek argumentu, ponieważ nie `\2`ma żadnej grupy przechwytywania ponumerowane . Ponadto jeśli *liczba* identyfikuje grupę przechwytywania w określonej pozycji ordinal, ale tej grupie przechwytywania przypisano nazwę liczbową inną niż jej pozycja liczba, <xref:System.ArgumentException>analizator wyrażeń regularnych również zgłasza .

Należy zwrócić uwagę na niejednoznaczność między `\16`liczbami óskowymi (np. ) i `\`odwołania wsteczne *liczb,* które używają tej samej notacji. Ta niejednoznaczność jest rozwiązana w następujący sposób:

- Wyrażenia `\1` za `\9` pośrednictwem są zawsze interpretowane jako odwołania wsteczne, a nie jako kody ósemkowe.

- Jeśli pierwsza cyfra wyrażenia wielocyfrowego to 8 `\80` lub `\91`9 (np. lub ), wyrażenie interpretowane jako literał.

- Wyrażenia z `\10` i większe są uważane za odwołania wsteczne, jeśli istnieje odwołanie wsteczne odpowiadające tej liczbie; w przeciwnym razie są one interpretowane jako kody ósemkowe.

- Jeśli wyrażenie regularne zawiera odwołanie wsteczne do niezdefiniowanego numeru grupy, występuje błąd analizy, <xref:System.ArgumentException>a aparat wyrażeń regularnych zgłasza plik .

Jeśli niejednoznaczność jest problemem, można `\k<`użyć notacji *nazwy,* `>` która jest jednoznaczna i nie można pomylić z kodami znaków ósemkowych. Podobnie kody szesnastkowe, takie jak `\xdd` są jednoznaczne i nie można ich mylić z odwołaniami wstecznymi.

W poniższym przykładzie wyszukuje znaki wyrazów podwojonych w ciągu. Definiuje wyrażenie regularne, `(\w)\1`które składa się z następujących elementów.

|Element|Opis|
|-------------|-----------------|
|`(\w)`|Dopasuj znak wyrazu i przypisz go do pierwszej grupy przechwytywania.|
|`\1`|Dopasuj następny znak, który jest taki sam jak wartość pierwszej grupy przechwytywania.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Nazwane odwołania wsteczne

Nazwane odwołanie wsteczne jest definiowane przy użyciu następującej składni:

`\k<`*nazwa*`>`

lub:

`\k'`*nazwa*`'`

gdzie *nazwa* jest nazwą grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego. Jeśli *nazwa* nie jest zdefiniowana we wzorcu wyrażenia regularnego, występuje błąd analizy, a aparat wyrażeń regularnych zgłasza plik <xref:System.ArgumentException>.

W poniższym przykładzie wyszukuje znaki wyrazów podwojonych w ciągu. Definiuje wyrażenie regularne, `(?<char>\w)\k<char>`które składa się z następujących elementów.

|Element|Opis|
|-------------|-----------------|
|`(?<char>\w)`|Dopasuj znak wyrazu i przypisz go do grupy przechwytywania o nazwie `char`.|
|`\k<char>`|Dopasuj następny znak, który jest `char` taki sam jak wartość grupy przechwytywania.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Nazwane numeryczne odwołania wsteczne

W nazwie backreference `\k`z , *nazwa* może być również reprezentacja ciągu liczby. Na przykład w poniższym przykładzie `(?<2>\w)\k<2>` użyto wyrażenia regularnego, aby znaleźć podwojone znaki wyrazu w ciągu. W takim przypadku przykład definiuje grupę przechwytywania, która jest jawnie o nazwie "2", a odwołanie wsteczne jest odpowiednio o nazwie "2".

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Jeśli *nazwa* jest reprezentacją ciągu liczby, a żadna grupa `\k<`przechwytywania nie ma tej nazwy, *nazwa* `>` jest taka sama jak `\` *numer*odniesienia wstecznego , gdzie *liczba* jest pozycją liczbową przechwytywania. W poniższym przykładzie istnieje jedna grupa `char`przechwytywania o nazwie . Konstrukcja backreference odnosi się `\k<1>`do niego jako . Jak pokazuje dane wyjściowe z przykładu, wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> sukcesu, ponieważ `char` jest pierwszą grupą przechwytywania.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Jeśli jednak *nazwa* jest reprezentacją ciągu liczby, a grupie przechwytywania w tej pozycji wyraźnie przypisano nazwę liczbową, analizator wyrażeń regularnych nie może zidentyfikować grupy przechwytywania według jej pozycji ordinal. Zamiast tego rzuca <xref:System.ArgumentException>. Jedyna grupa przechwytywania w poniższym przykładzie nosi nazwę "2". Ponieważ `\k` konstrukcja jest używana do definiowania odwołania wstecznego o nazwie "1", analizator wyrażeń regularnych nie może zidentyfikować pierwszej grupy przechwytywania i zgłasza wyjątek.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Co backreferences pasuje

Odwołanie wsteczne odnosi się do najnowszej definicji grupy (definicja najbardziej natychmiast po lewej stronie, podczas dopasowywania od lewej do prawej). Gdy grupa wykonuje wiele przechwytów, odwołanie wsteczne odnosi się do ostatniego przechwytywania.

Poniższy przykład zawiera wzorzec wyrażenia regularnego, `(?<1>a)(?<1>\1b)*`który ponownie definiuje \1 nazwaną grupę. W poniższej tabeli opisano każdy wzorzec w wyrażeniu regularnym.

|Wzorce|Opis|
|-------------|-----------------|
|`(?<1>a)`|Dopasuj znak "a" i przypisz `1`wynik do grupy przechwytywania o nazwie .|
|`(?<1>\1b)*`|Dopasuj zero lub więcej `1` wystąpień grupy o nazwie wraz z "b" `1`i przypisz wynik do grupy przechwytywania o nazwie .|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

Porównując wyrażenie regularne z ciągiem wejściowym ("aababb"), aparat wyrażeń regularnych wykonuje następujące operacje:

1. Rozpoczyna się na początku ciągu i pomyślnie dopasowuje "a" z wyrażeniem `(?<1>a)`. Wartość `1` grupy jest teraz "a".

2. Przechodzi do drugiego znaku i pomyślnie dopasowuje ciąg "ab" z wyrażeniem `\1b`lub "ab". Następnie przypisuje wynik "ab" do `\1`.

3. Przechodzi do czwartego znaku. Wyrażenie `(?<1>\1b)*` ma być dopasowane zero lub więcej razy, więc pomyślnie pasuje do `\1b`ciągu "abb" z wyrażeniem . Przypisuje wynik "abb", z powrotem `\1`do .

W tym `*` przykładzie jest kwantyfikatorem pętli - jest obliczany wielokrotnie, dopóki aparat wyrażeń regularnych nie będzie w stanie dopasować zdefiniowanego wzorca. Kwantyfikatory pętli nie wyczyszczają definicji grup.

Jeśli grupa nie przechwyciła żadnych podciągów, odwołanie wsteczne do tej grupy jest niezdefiniowane i nigdy nie jest zgodne. Ilustruje to wzorzec `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`wyrażenia regularnego, który jest zdefiniowany w następujący sposób:

|Wzorce|Opis|
|-------------|-----------------|
|`\b`|Rozpocznij dopasowanie na granicy słowa.|
|`(\p{Lu}{2})`|Dopasuj dwie wielkie litery. Jest to pierwsza grupa przechwytywania.|
|`(\d{2})?`|Dopasuj zero lub jedno wystąpienie dwóch cyfr dziesiętnych. Jest to druga grupa przechwytywania.|
|`(\p{Lu}{2})`|Dopasuj dwie wielkie litery. Jest to trzecia grupa przechwytywania.|
|`\b`|Zakończ dopasowanie na granicy słowa.|

Ciąg wejściowy może być zgodny z tym wyrażeniem regularnym, nawet jeśli nie występują dwie cyfry dziesiętne zdefiniowane przez drugą grupę przechwytywania. W poniższym przykładzie pokazano, że mimo pomyślnego dopasowania, puste grupy przechwytywania znajduje się między dwiema udanymi grupami przechwytywania.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
