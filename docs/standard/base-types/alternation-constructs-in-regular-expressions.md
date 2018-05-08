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
ms.openlocfilehash: 956d16b47fb31549de8f25c513d73c43ab41c267
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="alternation-constructs-in-regular-expressions"></a>Konstrukcje alternacyjne w wyrażeniach regularnych
<a name="top"></a> Konstrukcje alternacyjne zmodyfikować wyrażenie regularne, aby włączyć opcję / lub lub pasujące warunkowego. .NET obsługuje trzy konstrukcje alternacyjne:  
  
-   [Dopasowywanie do wzorca z&#124;](#Either_Or)  
  
-   [Warunkowe dopasowywanie (? () wyrażenie) tak&#124;nie)](#Conditional_Expr)  
  
-   [Dopasowywanie warunkowego oparte na prawidłową grupę przechwycony](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Dopasowywanie do wzorca z&#124;  
 Można użyć pionowy pasek (`|`) znaków do dopasowania któregokolwiek z serii wzorców, gdzie `|` rozdziela każdego wzorca.  
  
 Klasa dodatnią znaków, takich jak `|` znak może być użyty do dopasowania dowolną liczbę pojedynczy znaki. W poniższym przykładzie użyto zarówno klasy znaku dodatnią i albo / lub dopasowywanie do wzorca za `|` znak, aby zlokalizować wystąpienia wyrazy "szarym" lub "szare" w ciągu. W takim przypadku `|` znak tworzy wyrażenie regularne jest na pełniejsze.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Wyrażenie regularne, która używa `|` znak, `\bgr(a|e)y\b`, jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`gr`|Pasować do znaków "gr".|  
|<code>(a&#124;e)</code>|Dopasowuje znak „a” lub „e”.|  
|`y\b`|Odpowiada na granicy słowa "y".|  
  
 `|` Znak można również wykonać jedno / lub pasuje do wielu znaków lub zakresie, które może zawierać dowolną kombinację znaków literały i elementy języka wyrażenia regularnego. (Klasy znaku nie zapewnia tę funkcję). W poniższym przykładzie użyto `|` znak wyodrębnić albo stany USA Numer ubezpieczenia społecznego (SSN), który jest 9 cyfr w formacie *ddd*-*dd*-*dddd*, lub stany USA Pracodawcy Identyfikacja numeru (NIP), czyli 9 cyfr w formacie *dd*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Pasuje do żadnej z następujących czynności: dwie cyfry dziesiętne następuje myślnik następuje siedmiu cyfr dziesiętnych; lub trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.|  
|`\d`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>Dopasowanie warunkowe z wyrażeniem  
 Ten element języka próbuje pasuje do jednej z dwóch wzorców w zależności od tego, czy dopasowania wzorca początkowej. Składnia to:  
  
 `(?(` *wyrażenie* `)` *tak* `|` *nie* `)`  
  
 gdzie *wyrażenie* jest początkowej wzorzec do dopasowania, *tak* jest wzorzec do dopasowania, jeśli *wyrażenie* dopasowaniu, i *nie* jest opcjonalny wzorzec do dopasowania, jeśli *wyrażenie* nie jest zgodny. Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie wcześniejszego w strumieniu wejściowym po oblicza *wyrażenia*. W związku z tym ta konstrukcja jest odpowiednikiem następujące czynności:  
  
 `(?(?=` *wyrażenie* `)` *tak* `|` *nie* `)`  
  
 gdzie `(?=` *wyrażenie* `)` jest konstrukcję potwierdzenia zerowej szerokości. (Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako swojej kotwicy (Potwierdzenie zerowej szerokości), *wyrażenie* musi być potwierdzenia zerowej szerokości (Aby uzyskać więcej informacji, zobacz [ Kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) lub Podwyrażenie, które również znajdują się w *tak*. W przeciwnym razie *tak* nie można dopasować wzorzec.  
  
> [!NOTE]
>  Jeśli *wyrażenie*jest nazwane lub numerem grupy przechwytywania, konstrukcja alternacyjne jest interpretowany jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [warunkowego dopasowania na podstawie prawidłową grupę przechwytywania](#Conditional_Group). Innymi słowy aparat wyrażeń regularnych nie próbował dopasować podciąg przechwycony, ale zamiast tego testów dla obecności lub braku grupy.  
  
 Poniższy przykład jest odmianą przykładu, która jest wyświetlana w [albo / lub dopasowanie wzorca z &#124; ](#Either_Or) sekcji. Aby ustalić, czy pierwsze trzy znaki po granic word dwie cyfry następuje łącznik używa warunkowego dopasowania. Jeśli są one go próbuje dopasować stany USA Numer identyfikacyjny pracodawcy (NIP). Jeśli nie, jego próbuje dopasować stany USA Numer ubezpieczenia społecznego (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Wzorzec wyrażenia regularnego `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?(\d{2}-)`|Ustal, czy trzech kolejnych znaków składają się z dwóch cyfr zostały wykonane przez łącznik.|  
|`\d{2}-\d{7}`|Jeśli poprzednie wzorzec jest zgodny, odpowiadać dwie cyfry następuje myślnik następuje siedem cyfr.|  
|`\d{3}-\d{2}-\d{4}`|Niezgodna wcześniejszego wzorca odpowiada trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 [Powrót do początku](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach  
 Ten element języka próbuje pasuje do jednej z dwóch wzorców w zależności od tego, czy dopasowywane określonej grupy przechwytywania. Składnia to:  
  
 `(?(` *Nazwa* `)` *tak* `|` *nie* `)`  
  
 lub  
  
 `(?(` *numer* `)` *tak* `|` *nie* `)`  
  
 gdzie *nazwa* jest nazwą i *numer* jest numer grupy przechwytywania, *tak* jest wyrażeniem do dopasowania, jeśli *nazwa* lub *numer* jest zgodny i *nie* wyrażenie opcjonalne do dopasowania, jeśli nie jest.  
  
 Jeśli *nazwa* nie odpowiada na nazwę grupy przechwytywania, który jest używany w wzorzec wyrażenia regularnego, konstrukcja alternacyjne jest interpretowana jako testu wyrażenie zgodnie z objaśnieniem w poprzedniej sekcji. Zazwyczaj oznacza to, że *wyrażenie* daje w wyniku `false`. Jeśli *numer* jest niezgodne z numerem grupy przechwytywania, używanym w wzorzec wyrażenia regularnego zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.  
  
 Poniższy przykład jest odmianą przykładu, która jest wyświetlana w [albo / lub dopasowanie wzorca z &#124; ](#Either_Or) sekcji. Używa przechwytywania grupę o nazwie `n2` składający się z dwóch cyfr zostały wykonane przez łącznik. Wyrażenia warunkowe utworzenia testów, czy ta grupa przechwytywania ma dopasowane w ciągu wejściowym. Jeśli ma ona alternacyjne skonstruować próbuje dopasować ostatnich siedmiu cyfr US dziewięciu cyfr Numer identyfikacyjny pracodawcy (NIP). Jeśli go nie ma, próbuje odpowiada USA dziewięciu cyfr Numer ubezpieczenia społecznego (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Wzorzec wyrażenia regularnego `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(?<n2>\d{2}-)?`|Wystąpienie dopasowania zero lub jeden dwie cyfry oraz łącznik. Określ nazwę tej grupy przechwytywania `n2`.|  
|`(?(n2)`|Test czy `n2` został uzyskany w ciągu wejściowym.|  
|`)\d{7}`|Jeśli `n2` został zgodne, zgodne siedmiu cyfr dziesiętnych.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Jeśli `n2` nie było zgodne, zgodne trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 W poniższym przykładzie przedstawiono zmiany w tym przykładzie, który korzysta z numerem grupy zamiast nazwaną grupę. Jest jego wzorzec wyrażenia regularnego `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
