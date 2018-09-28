---
title: Konstrukcje alternacyjne w wyrażeniach regularnych
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b653972fad71ce3a89c35598513b94f71fb4bf0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425995"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukcje alternacyjne w wyrażeniach regularnych
<a name="top"></a> Konstrukcje zmiany modyfikują wyrażenie regularne, aby włączyć opcję / lub lub dopasowanie warunkowe. .NET obsługuje trzy konstrukcje zmiany:  
  
-   [Dopasowywanie wzorca z&#124;](#Either_Or)  
  
-   [Dopasowanie warunkowe z (? () wyrażenie) tak&#124;nie)](#Conditional_Expr)  
  
-   [Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Dopasowywanie wzorca z&#124;  
 Można użyć pionowy pasek (`|`) znaku, aby dopasować dowolny z szeregu wzorców, gdzie `|` rozdziela każdy wzorzec.  
  
 Klasy znaków pozytywnych, takich jak `|` znak może być użyty do dopasowania dowolną liczbę pojedynczych znaków. W poniższym przykładzie użyto klasy znaków pozytywnych i albo / lub za pomocą dopasowywania do wzorca `|` znaku, aby zlokalizować wystąpienia słowa "szarym" lub "szare" w ciągu. W tym przypadku `|` znaków generuje wyrażeń regularnych, które jest pełniejszy.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Wyrażenie regularne, które używa `|` znak `\bgr(a|e)y\b`, jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`gr`|Dopasowuje znaki "gr".|  
|<code>(a&#124;e)</code>|Dopasowuje znak „a” lub „e”.|  
|`y\b`|Dopasowuje "y" na granicy wyrazu.|  
  
 `|` Znaku można również przeprowadzić albo / lub zgodne z wielu znaków lub podwyrażenia, które mogą obejmować dowolną kombinację literały znakowe i elementy języka wyrażeń regularnych. (Klasy znaku nie zapewnia tej funkcji). W poniższym przykładzie użyto `|` znaków do wyodrębnienia albo USA Numer ubezpieczenia społecznego (SSN), czyli 9 cyfr w formacie *ddd*-*dd*-*dddd*, lub Pracodawca Identyfikacja numeru (NIP), czyli 9 cyfr w formacie *dd*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Odpowiada jednej z następujących pozycji: dwie cyfry dziesiętne, następuje łącznik następuje siedmiu cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\d`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Dopasowanie warunkowe z wyrażeniem  
 Ten element języka podejmuje próbę dopasowania, jednym z dwóch wzorców w zależności od tego, czy może dopasować wzorca początkowej. Jego składnia jest następująca:  
  
 `(?(` *wyrażenie* `)` *tak* `|` *nie* `)`  
  
 gdzie *wyrażenie* jest początkowa wzorzec do dopasowania, *tak* jest wzorzec do dopasowania, jeśli *wyrażenie* jest dopasowywany i *nie* jest opcjonalna wzorzec do dopasowania, jeśli *wyrażenie* nie został dopasowany. Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie awansować w strumień wejściowy po ocenia *wyrażenie*. Dlatego ta konstrukcja jest odpowiednikiem następujących czynności:  
  
 `(?(?=` *wyrażenie* `)` *tak* `|` *nie* `)`  
  
 gdzie `(?=` *wyrażenie* `)` to konstrukcja asercja o zerowej szerokości. (Aby uzyskać więcej informacji, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako elementu zakotwiczenia (asercja o zerowej szerokości), *wyrażenie* musi być asercja o zerowej szerokości (Aby uzyskać więcej informacji, zobacz [ Kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) lub Podwyrażenie, które również znajdują się w *tak*. W przeciwnym razie *tak* nie można dopasować wzorzec.  
  
> [!NOTE]
>  Jeśli *wyrażenie*jest nazwana lub numerowana grupa przechwytywania, konstrukcje jest interpretowana jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [warunkowego dopasowania na podstawie prawidłowej grupy przechwytywania](#Conditional_Group). Innymi słowy aparat wyrażeń regularnych nie jest podejmowana próba Dopasuj podciąg przechwycony, ale zamiast tego sprawdza obecność lub Brak grupy.  
  
 Poniższy przykład jest odmianą przykładu, który pojawia się w [albo / lub za pomocą dopasowywania do wzorca &#124; ](#Either_Or) sekcji. Aby ustalić, czy pierwsze trzy znaki po granicy słowa dwie cyfry, następuje łącznik używa dopasowanie warunkowe. Jeśli są one podejmuje próbę dopasowania Federalny Numer identyfikacji podatkowej (NIP). W przeciwnym razie podejmuje próbę dopasowania Federalny Numer ubezpieczenia społecznego (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?(\d{2}-)`|Ustal, czy kolejne trzy znaki składają się z dwóch cyfr następuje łącznik.|  
|`\d{2}-\d{7}`|Jeśli poprzedni wzorzec jest zgodny, dopasowuje dwie cyfry, następuje łącznik następuje siedmiu cyfr.|  
|`\d{3}-\d{2}-\d{4}`|Jeśli poprzedni wzorzec nie jest zgodny, zgodne trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach  
 Ten element języka podejmuje próbę dopasowania, jednym z dwóch wzorców w zależności od tego, czy dopasowywane określonej grupy przechwytywania. Jego składnia jest następująca:  
  
 `(?(` *Nazwa* `)` *tak* `|` *nie* `)`  
  
 lub  
  
 `(?(` *Liczba* `)` *tak* `|` *nie* `)`  
  
 gdzie *nazwa* nazywa się i *numer* jest numerem grupy przechwytywania, *tak* jest wyrażeniem które pasują, jeśli *nazwa* lub *numer* jest zgodny, oraz *nie* jest opcjonalne wyrażenie dopasowania, jeśli nie ma.  
  
 Jeśli *nazwa* nie odpowiada na nazwę grupy przechwytywania, który jest używany we wzorcu wyrażenia regularnego, konstrukcje jest interpretowana jako test wyrażenia, zgodnie z opisem w poprzedniej sekcji. Zazwyczaj oznacza to, że *wyrażenie* daje w wyniku `false`. Jeśli *numer* nie odpowiada numerowaną grupę przechwytywania, który jest używany we wzorcu wyrażenia regularnego zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 Poniższy przykład jest odmianą przykładu, który pojawia się w [albo / lub za pomocą dopasowywania do wzorca &#124; ](#Either_Or) sekcji. Używa ona grupa przechwytywania o nazwie `n2` składający się z dwóch cyfr następuje łącznik. Konstrukcja testów czy ta grupa przechwytywania został dopasowany do ciągu wejściowego. Jeśli tak, konstrukcja warunkowa próbuje dopasować ostatnich siedmiu cyfr US dziewięciu cyfr Numer identyfikacji podatkowej (NIP). Jeśli nie ma on podejmuje próbę dopasowania USA dziewięciu cyfr Numer ubezpieczenia społecznego (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Definicję wzorca wyrażenia regularnego `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?<n2>\d{2}-)?`|Dopasowanie zera lub jednego wystąpienia dwie cyfry, następuje łącznik. Określ nazwę tej grupy przechwytywania `n2`.|  
|`(?(n2)`|Test czy `n2` zostały dopasowane do ciągu wejściowego.|  
|`)\d{7}`|Jeśli `n2` został dopasowany, pasuje do siedmiu cyfr dziesiętnych.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Jeśli `n2` nie zostały dopasowane do elementu, dopasowania trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 Zmiany w tym przykładzie, która używa numerowanej grupy zamiast nazwaną grupę przedstawiono w poniższym przykładzie. Jej wzorca wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
