---
title: Konstrukcje naprzemienne w wyrażeniach regularnych .NET
description: Dowiedz się, jak używać konstrukcji naprzemiennych do uzgadniania warunkowego w wyrażeniach regularnych.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159692"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukcje alternacyjne w wyrażeniach regularnych

Konstrukcje alternation modyfikują wyrażenie regularne, aby włączyć dopasowywanie warunkowe lub dopasowanie warunkowe. .NET obsługuje trzy konstrukcje naprzemienne:

- [Dopasowanie wzorców do &#124;](#Either_Or)
- [Warunkowe dopasowanie z (?( wyrażenie)tak&#124;nie)](#Conditional_Expr)
- [Uzgadnianie warunkowe na podstawie prawidłowej przechwyconej grupy](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>Dopasowanie wzorca do &#124;

Można użyć pionowego`|`paska ( ) znaku, aby dopasować dowolny z serii wzorów, gdzie `|` znak oddziela każdy wzór.

Podobnie jak dodatnia `|` klasa znaków, znak może być używany do dopasowania jednego z wielu pojedynczych znaków. W poniższym przykładzie użyto zarówno dodatniej klasy `|` znaków, jak i dopasowania albo/lub wzorca do znaku, aby zlokalizować wystąpienia słów "szary" lub "szary" w ciągu. W takim przypadku `|` znak tworzy wyrażenie regularne, które jest bardziej pełne.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

Wyrażenie regularne, które `|` używa `\bgr(a|e)y\b`znaku, jest interpretowane w sposób pokazany w poniższej tabeli:

|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`gr`|Dopasuj znaki "gr".|  
|<code>(a&#124;e)</code>|Dopasowuje znak „a” lub „e”.|  
|`y\b`|Dopasuj "y" na granicy słowa.|  

Znak `|` może być również używany do wykonywania jednego/lub dopasowania do wielu znaków lub podwyrażeń, które mogą zawierać dowolną kombinację literałów znaków i elementów języka wyrażenia regularnego. (Klasa znaków nie udostępnia tej funkcji). Poniższy przykład używa `|` tego znaku do wyodrębnienia numeru ubezpieczenia społecznego (SSN), który jest 9-cyfrowym numerem o formacie- *ddd*-*ddddd*-*dddd*lub numerem identyfikacyjnym amerykańskiego pracodawcy (EIN), który jest 9-cyfrowym numerem o formacie*dddddddd.* *dd*

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

Wyrażenie `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` regularne jest interpretowane w sposób pokazany w poniższej tabeli:
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Dopasuj jedną z następujących czynności: dwie cyfry dziesiętne, po których następuje łącznik, po którym następuje siedem cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\d`|Kończy dopasowanie na granicy wyrazu.|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a>Warunkowe uzgadnianie z wyrażeniem

Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy można dopasować wzorzec początkowy. Jego składnia jest:  

`(?(`*wyrażenie* `)` *tak* `|` *nie*`)`

gdzie *wyrażenie* jest początkowy wzorzec do dopasowania, *tak* jest wzorzec, aby dopasować, jeśli *wyrażenie* jest dopasowane, a *nie* jest opcjonalny wzorzec, aby dopasować, jeśli *wyrażenie* nie jest dopasowane. Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie o zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie zaliczki w strumieniu wejściowym po ocenia *wyrażenie*. W związku z tym ta konstrukcja jest odpowiednikiem następujących:

`(?(?=`*wyrażenie* `)` *tak* `|` *nie*`)`

gdzie `(?=` *wyrażenie* `)` jest konstrukcją potwierdzenia o zerowej szerokości. (Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako kotwicę (twierdzenie o zerowej szerokości), *wyrażenie* musi być potwierdzeniem o zerowej szerokości (aby uzyskać więcej informacji, zobacz [Kotwice)](anchors-in-regular-expressions.md)lub wyrażeniem podrzędnym, które jest również zawarte w *yes*. W przeciwnym razie nie można dopasować wzorca *tak.*  
  
> [!NOTE]
> Jeśli *wyrażenie* jest nazwaną lub numerowane grupy przechwytywania, konstrukcja naprzemienna jest interpretowany jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [Dopasowanie warunkowe na podstawie prawidłowej grupy przechwytywania](#Conditional_Group). Innymi słowy aparat wyrażeń regularnych nie próbuje dopasować przechwyconego podciągu, ale zamiast tego testuje obecność lub brak grupy.  
  
Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji [Dopasowywanie wzorców lub do &#124;.](#Either_Or) Używa dopasowania warunkowego, aby ustalić, czy pierwsze trzy znaki po granicy wyrazu są dwie mastce, po którym następuje łącznik. Jeśli tak, próbuje dopasować numer identyfikacyjny amerykańskiego pracodawcy (EIN). Jeśli nie, próbuje dopasować numer ubezpieczenia społecznego USA (SSN).

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

Wzorzec `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli:

|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?(\d{2}-)`|Określ, czy następne trzy znaki składają się z dwóch cyfr, po których następuje łącznik.|  
|`\d{2}-\d{7}`|Jeśli poprzedni wzorzec jest zgodny, dopasuj dwie cyfry, po których następuje łącznik, po którym następują siedem cyfr.|  
|`\d{3}-\d{2}-\d{4}`|Jeśli poprzedni wzorzec nie jest zgodny, dopasuj trzy cyfry dziesiętne: łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Uzgadnianie warunkowe na podstawie prawidłowej przechwyconej grupy

Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy dopasował określoną grupę przechwytywania. Jego składnia jest:

`(?(`*nazwa* `)` *tak nie* `|` *no*`)`

lub

`(?(`*liczba* `)` *tak nie* `|` *no*`)`

gdzie *nazwa* jest nazwą, a *liczba* jest numerem grupy przechwytywania, *tak* jest wyrażeniem pasującym, jeśli *nazwa* lub *liczba* ma dopasowanie, a *nie* jest opcjonalnym wyrażeniem, które jest zgodne, jeśli nie.

Jeśli *nazwa* nie odpowiada nazwie grupy przechwytywania, która jest używana w wzorcu wyrażenia regularnego, konstrukcja naprzemienna jest interpretowana jako test wyrażenia, jak wyjaśniono w poprzedniej sekcji. Zazwyczaj oznacza to, *expression* że wyrażenie `false`oblicza . Jeśli *liczba* nie odpowiada numerowanej grupie przechwytywania, która jest używana we wzorcu <xref:System.ArgumentException>wyrażenia regularnego, aparat wyrażeń regularnych zgłasza plik .

Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji [Dopasowywanie wzorców lub do &#124;.](#Either_Or) Używa grupy przechwytywania o `n2` nazwie, która składa się z dwóch cyfr, po których następuje łącznik. Konstrukcja naprzemienna sprawdza, czy ta grupa przechwytywania została dopasowana w ciągu wejściowym. Jeśli tak, konstrukcja naprzemienna próbuje dopasować ostatnie siedem cyfr dziewięciocyfrowego numeru identyfikacyjnego pracodawcy (EIN). Jeśli tak nie jest, próbuje dopasować dziewięciocyfrowy numer ubezpieczenia społecznego (SSN).

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

Wzorzec `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli:

|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?<n2>\d{2}-)?`|Dopasuj zero lub jedno wystąpienie dwóch cyfr, po którym następuje łącznik. Nazwij tę `n2`grupę przechwytywania .|  
|`(?(n2)`|Sprawdź, `n2` czy został dopasowany w ciągu wejściowym.|  
|`\d{7}`|Jeśli `n2` został dopasowany, dopasuj siedem cyfr dziesiętnych.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Jeśli `n2` nie został dopasowany, dopasuj trzy cyfry dziesiętne: łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  

Odmiana tego przykładu, która używa ponumerowanej grupy zamiast nazwanej grupy jest pokazana w poniższym przykładzie. Jego wzorzec wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
