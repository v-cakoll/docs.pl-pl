---
title: Konstrukcje warunkowe w wyrażeniach regularnych programu .NET
description: Dowiedz się, w jaki sposób używać konstrukcji warunkowych do dopasowywania w wyrażeniach regularnych.
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
ms.openlocfilehash: 8db9ef72415f148aca2c975fc4e8b70421e3adc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711561"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukcje alternacyjne w wyrażeniach regularnych

Konstrukcje warunkowe modyfikują wyrażenie regularne, aby umożliwić Dopasowanie warunkowe/lub lub. Platforma .NET obsługuje trzy konstrukcje warunkowe:

- [Dopasowanie wzorca z&#124;](#Either_Or)
- [Warunkowe dopasowanie do (? ( wyrażenie) tak&#124;nie)](#Conditional_Expr)
- [Dopasowanie warunkowe oparte na prawidłowej przechwyconej grupie](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>Dopasowanie wzorca z&#124;

Można użyć znaku kreski pionowej (`|`), aby dopasować każdą z serii wzorców, gdzie znak `|` oddziela każdy wzorzec.

Podobnie jak w przypadku klasy znaków pozytywnych, znak `|` może być używany w celu dopasowania do jednej z wielu pojedynczych znaków. Poniższy przykład używa zarówno klasy znaku dodatniego, jak i/lub dopasowania wzorca ze znakiem `|`, aby zlokalizować wystąpienia wyrazów "szary" lub "szary" w ciągu. W tym przypadku znak `|` generuje wyrażenie regularne, które jest bardziej pełne.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

Wyrażenie regularne używające znaku `|`, `\bgr(a|e)y\b`, jest interpretowane jak pokazano w poniższej tabeli:

|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`gr`|Dopasowuje znaki "gr".|  
|<code>(a&#124;e)</code>|Dopasowuje znak „a” lub „e”.|  
|`y\b`|Dopasowuje znak "y" na granicy słowa.|  

Znaku `|` można również użyć do wykonania elementu/lub dopasowania z wieloma znakami lub podwyrażeniami, które mogą zawierać dowolną kombinację literałów znakowych i elementy języka wyrażeń regularnych. (Klasa znaku nie zapewnia tej funkcji). Poniższy przykład używa znaku `|`, aby wyodrębnić numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych, który jest 9-cyfrowym numerem w formacie *ddd*-*DD*-*dddd*lub numerem identyfikacyjnym pracodawcy USA (EIN), który jest 9-cyfrowym numerem w formacie *DD*-*ddddddd*.

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane jak pokazano w poniższej tabeli:
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Dopasowuje jedną z następujących wartości: dwie cyfry dziesiętne, po których następuje łącznik, a po nich siedem cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\d`|Kończy dopasowanie na granicy wyrazu.|  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Warunkowe dopasowanie z wyrażeniem

Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy może on pasować do wzorca początkowego. Jego składnia to:  

*wyrażenie* `(?(` `)` *tak* `|` *nie* `)`

*wyrażenie* WHERE jest wzorcem początkowym, *tak* aby pasowało do wzorca, jeśli *wyrażenie* jest dopasowane, a *nie* jest opcjonalnym wzorcem do dopasowania, jeśli *wyrażenie* nie jest zgodne. Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie o zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie postępuje w strumieniu wejściowym po obliczeniu *wyrażenia*. W związku z tym konstrukcja ta jest równoważna następującym:

*wyrażenie* `(?(?=` `)` *tak* `|` *nie* `)`

gdzie `(?=`*expression*`)` jest konstrukcja potwierdzenia o zerowej szerokości. (Aby uzyskać więcej informacji, zobacz [grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md)). Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako zakotwiczenie (potwierdzenie o zerowej szerokości), *wyrażenie* musi być potwierdzeniem o zerowej szerokości (Aby uzyskać więcej informacji, zobacz [kotwice](anchors-in-regular-expressions.md)) lub Podwyrażenie, które jest również zawarte w wartości *tak*. W przeciwnym razie nie można dopasować wzorca *tak* .  
  
> [!NOTE]
> Jeśli *wyrażenie* jest nazwaną lub numerowaną grupą przechwytywania, konstrukcja alternatywna jest interpretowana jako test przechwytywania. Aby uzyskać więcej informacji, zobacz następną sekcję, [Dopasowanie warunkowe na podstawie prawidłowej grupy przechwytywania](#Conditional_Group). Innymi słowy aparat wyrażeń regularnych nie próbuje dopasować przechwyconego podciągu, ale zamiast tego testuje obecność lub brak grupy.  
  
Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji " [dopasowanie &#124; do wzorca" i](#Either_Or) . Używa dopasowania warunkowego, aby określić, czy pierwsze trzy znaki po granicy słowa są dwiema cyframi, po których następuje łącznik. Jeśli są, próbuje dopasować numer identyfikacyjny (EIN) (USA). Jeśli nie, próbuje dopasować numer PESEL (USA).

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

`\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli:

|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?(\d{2}-)`|Ustal, czy następne trzy znaki składają się z dwóch cyfr, po których następuje łącznik.|  
|`\d{2}-\d{7}`|Jeśli poprzedni wzorzec jest zgodny, dopasowuje dwie cyfry, po których następuje łącznik, po którym następuje siedem cyfr.|  
|`\d{3}-\d{2}-\d{4}`|Jeśli poprzedni wzorzec nie jest zgodny, Dopasuj trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Dopasowanie warunkowe oparte na prawidłowej przechwyconej grupie

Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy jest on zgodny z określoną grupą przechwytywania. Jego składnia to:

*nazwa* `(?(` `)` *tak* `|` *nie* `)`

lub

*numer* `(?(` `)` *tak* `|` *nie* `)`

gdzie *name* to nazwa i *numer* jest liczbą grupy przechwytywania, *tak* jest wyrażenie do dopasowania, jeśli *Nazwa* lub *Liczba* ma dopasowanie, a wartość *nie* jest wyrażeniem opcjonalnym do dopasowania, jeśli nie.

Jeśli *Nazwa* nie odpowiada nazwie grupy przechwytywania używanej we wzorcu wyrażenia regularnego, konstrukcja alternatywna jest interpretowana jako test wyrażenia, jak wyjaśniono w poprzedniej sekcji. Zazwyczaj oznacza to, że *wyrażenie* oblicza `false`. Jeśli *Liczba* nie odpowiada numerowanej grupie przechwytywania używanej we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych zgłasza <xref:System.ArgumentException>.

Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji " [dopasowanie &#124; do wzorca" i](#Either_Or) . Używa grupy przechwytywania o nazwie `n2`, która składa się z dwóch cyfr, po których następuje łącznik. Konstrukcja alternatywna testuje, czy ta grupa przechwytywania została dopasowana w ciągu wejściowym. Jeśli ma, konstrukcja alternatywna próbuje dopasować do ostatnich siedmiu cyfr dziewięciu-cyfrowego numeru identyfikacyjnego (EIN). Jeśli nie, próbuje dopasować dziewięć-cyfrowy numer PESEL (USA).

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

`\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli:

|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?<n2>\d{2}-)?`|Dopasowanie do zera lub jednego wystąpienia dwóch cyfr, po których następuje łącznik. Nadaj nazwę tej grupie przechwytywania `n2`.|  
|`(?(n2)`|Sprawdź, czy `n2` został dopasowany w ciągu wejściowym.|  
|`\d{7}`|Jeśli `n2` zostało dopasowane, Dopasuj siedem cyfr dziesiętnych.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Jeśli `n2` nie zostały dopasowane, Dopasuj trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  

W poniższym przykładzie przedstawiono odmianę tego przykładu, która używa numerowanej grupy zamiast nazwanej grupy. Jego wzorzec wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
