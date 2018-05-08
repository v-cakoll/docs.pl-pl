---
title: Podstawienia w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53fd4ee63d49b3943fa0b1164591aaddaa764abc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="substitutions-in-regular-expressions"></a>Podstawienia w wyrażeniach regularnych
<a name="Top"></a> Podstawienia są elementy języka, które są rozpoznawane tylko w obrębie wzorce zamiany. Używają one wzorca wyrażenia regularnego w celu zdefiniowania całości lub części teksu, który ma zastąpić dopasowany tekst w ciągu wejściowym. Wzorzec zamieniania może składać się z co najmniej jednego podstawienia oraz znaków literału. Wzorce zamiany są dostarczane do przeciążenia <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, która ma `replacement` parametru i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody. Metody Zastąp wzorzec dopasowany wzorzec, który jest zdefiniowany przez `replacement` parametru.  
  
 Program .NET Framework definiuje elementy podstawień wymienione w poniższej tabeli.  
  
|Podstawienie|Opis|  
|------------------|-----------------|  
|`$` *Numer*|Obejmuje ostatnich podciąg pasujący do grupy przechwytywania, identyfikowany przez *numer*, gdzie *numer* jest wartość dziesiętna, w ciągu zastępowania. Aby uzyskać więcej informacji, zobacz [podstawiając grupy numerowane](#Numbered).|  
|`${` *Nazwa* `}`|Obejmuje ostatnich podciąg pasujący do grupy o nazwie określony przez `(?<` *nazwa* `> )` w ciąg zastępczy. Aby uzyskać więcej informacji, zobacz [podstawiając grupę o nazwie](#Named).|  
|`$$`|Zawiera pojedynczy literał „$” w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawiając Symbol "$"](#DollarSign).|  
|`$&`|Zawiera kopię całego dopasowania w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawiając całego dopasowania](#EntireMatch).|  
|<code>$\`</code>|Zawiera cały tekst ciągu wejściowego przed dopasowaniem w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [zastępując tekst przed dopasowania](#BeforeMatch).|  
|`$'`|Zawiera cały tekst ciągu wejściowego po dopasowaniu w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [zamiast tekstu po dopasowania](#AfterMatch).|  
|`$+`|Zawiera ostatnią grupę przechwyconą w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawiając ostatniej grupie przechwycone](#LastGroup).|  
|`$_`|Zawiera cały ciąg wejściowy w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawiając cały ciąg wejściowy](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Elementy podstawienia i wzorce zamieniania  
 Podstawienia to jedyne konstrukcje specjalne rozpoznawane we wzorcu zamieniania. Brak innych wyrażenia regularnego elementy języka, w tym znaków specjalne i okres (`.`), który dopasowuje dowolny znak, są obsługiwane. Podobnie elementy języka podstawień są rozpoznawane tylko we wzorcach zamieniania, i nigdy nie są prawidłowe we wzorcach wyrażeń regularnych.  
  
 Tylko znak, który może wystąpić w wyrażeniu regularnym lub w podstawieniu jest `$` znaków, ale ma inne znaczenie w każdy kontekst. We wzorcu wyrażenia regularnego `$` jest zakotwiczenie pasuje do końca ciągu. We wzorcu zastępczy `$` wskazuje początek podstawienia.  
  
> [!NOTE]
>  Aby w wyrażeniu regularnym uzyskać funkcjonalność podobną do wzorca zamieniania, należy użyć dopasowywania wstecznego. Aby uzyskać więcej informacji na temat odwołania wstecznego zobacz [konstrukcje dopasowań](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Podstawianie numerowanej grupy  
 `$` *Numer* element języka obejmuje ostatnich podciąg pasujący do *numer* Przechwytywanie grupy w ciągu zastępowania, gdzie *numer* jest Indeks przechwytywania grupy. Na przykład wzorzec zastępczy `$1` oznacza mają zostać zastąpione przez pierwszy przechwyconej grupy podciąg. Aby uzyskać więcej informacji na temat numerowane grup przechwytywania, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Wszystkie cyfry, które należy wykonać `$` będą interpretowane jako należące do *numer* grupy. Jeśli nie jest to zgodne z zamiarami użytkownika, można podstawić grupę nazwaną. Na przykład można użyć ciąg zastępczy `${1}1` zamiast `$11` do definiowania ciąg zastępczy jako wartości pierwszej grupy przechwyconych wraz z liczbą "1". Aby uzyskać więcej informacji, zobacz [podstawiając grupę o nazwie](#Named).  
  
 Przechwytywanie grup, które nie są jawnie przypisanej nazwy przy użyciu `(?<` *nazwa* `>)` składni są ponumerowane od lewej do prawej, począwszy od jednej. Nazwane grupy także są numerowane od lewej do prawej, począwszy od numeru większego o 1 od indeksu ostatniej nienazwanej grupy. Na przykład w wyrażeniu regularnym `(\w)(?<digit>\d)`, indeks `digit` nazwaną grupę wynosi 2.  
  
 Jeśli *numer* nie określa prawidłową grupę przechwytywania zdefiniowane w wzorzec wyrażenia regularnego `$` *numer* jest interpretowana jako sekwencję znak, który jest używany do zastępowania każdym dopasowaniu.  
  
 W poniższym przykładzie użyto `$` *numer* podstawienia usunąć symbol waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Wzorzec wyrażenia regularnego `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(\s?\d+[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to pierwsza grupa przechwytywania. Ponieważ wzorzec zastępczy jest `$1`, wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zastępuje całą podciąg z tą grupą przechwycony.|  
  
 [Powrót do początku](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Podstawianie nazwanej grupy  
 `${` *Nazwa* `}` element języka zastępuje ostatniego podciąg pasujący do *nazwa* Przechwytywanie grupy, których *nazwa* jest nazwą Przechwytywanie grupy zdefiniowane przez `(?<` *nazwa* `>)` element języka. Aby uzyskać więcej informacji o nazwanych grup przechwytywania, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Jeśli *nazwa* , ale nie określa prawidłowej o nazwie przechwytywania grupy zdefiniowanej w wzorzec wyrażenia regularnego składa się z cyfr, `${` *nazwa* `}` jest interpretowana jako numerem grupy.  
  
 Jeśli *nazwa* określa prawidłową grupę o nazwie przechwytywania ani prawidłowy numerem grupy przechwytywania zdefiniowanej w wzorzec wyrażenia regularnego `${` *nazwa* `}` jest interpretowana jako Sekwencja znak, który jest używany do zastępowania każdym dopasowaniu.  
  
 W poniższym przykładzie użyto `${` *nazwa* `}` podstawienia usunąć symbol waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(?<amount>\s?\d[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to grupa przechwytywania o nazwie `amount`. Ponieważ wzorzec zastępczy jest `${amount}`, wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zastępuje całą podciąg z tą grupą przechwycony.|  
  
 [Powrót do początku](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Podstawianie znaku „$”  
 `$$` Podstawienia wstawia zastąpionego ciąg literału znaku "$".  
  
 W poniższym przykładzie użyto <xref:System.Globalization.NumberFormatInfo> obiektem, aby określić symbol waluty bieżącej kultury i umieszczania jej w ciągu waluty. Następnie jest dynamicznie tworzony wzorzec wyrażenia regularnego i wzorzec zamieniania. Jeśli na przykład jest uruchamiana na komputerze, na których bieżącej kultury jest en US, generuje wzorzec wyrażenia regularnego `\b(\d+)(\.(\d+))?` i wzorzec zastępczy `$$ $1$2`. Wzorzec zamieniania zamienia dopasowany tekst na symbol waluty i spację, po której następują pierwsza i druga przechwycona grupa.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Wzorzec wyrażenia regularnego `\b(\d+)(\.(\d+))?` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczęcie dopasowywania na początku granicy wyrazu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to pierwsza grupa przechwytywania.|  
|`\.`|Dopasowanie kropki (separator dziesiętny).|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to trzecia grupa przechwytywania.|  
|`(\.(\d+))?`|Dopasowanie zera lub jednego wystąpienia kropki, po którym następuje co najmniej jedna cyfra dziesiętna. Jest to druga grupa przechwytywania.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Podstawianie całego dopasowania  
 `$&` Podstawienia obejmuje całego dopasowania w ciągu zastępowania. Często jest używane do dodawania podciągu na początku lub końcu dopasowanego ciągu. Na przykład `($&)` wzorzec zastępczy dodaje nawiasów na początku i na końcu każdej dopasowania. Jeśli nie zostanie odnaleziony odpowiednik `$&` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto `$&` podstawienia, aby dodać cudzysłów na początku i na końcu tytułów książek przechowywane w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Wzorzec wyrażenia regularnego `^(\w+\s?)+$` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczęcie dopasowywania na początku ciągu wejściowego.|  
|`(\w+\s?)+`|Dopasowanie wzorca jednego lub większej liczby znaków słowa, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 `"$&"` Wzorzec zastępczy dodaje literału znaku cudzysłowu na początku i na końcu każdej dopasowania.  
  
 [Powrót do początku](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Podstawianie tekstu przed dopasowaniem  
 <code>$\`</code> Podstawienia są zastępowane dopasowany ciąg cały ciąg wejściowy przed dopasowania. Oznacza to, że duplikuje ciąg wejściowy przed dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się po dopasowanym tekście zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli w ciągu wejściowym będzie znajdować się wiele dopasowań, tekst zamienny będzie pochodził z oryginalnego ciągu wejściowego, a nie z ciągu, w którym tekst został zamieniony na poprzednie dopasowania. \(W przykładzie przedstawiono ilustracji.\) Jeśli nie zostanie odnaleziony odpowiednik <code>$\`</code> podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorzec wyrażenia regularnego `\d+` odpowiadające sekwencję jeden lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępczy <code>$`</code> zastępuje te znaki tekstu poprzedzającego dopasowania.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli przedstawiono sposób <code>$`</code> podstawienia powoduje, że aparat wyrażeń regularnych zastąpić każdym dopasowaniu w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg przed dopasowaniem|Ciąg wynikowy|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|AA**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Powrót do początku](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Podstawianie tekstu po dopasowaniu  
 `$'` Podstawienia są zastępowane dopasowany ciąg cały ciąg wejściowy po dopasowania. Oznacza to, że duplikuje ciąg wejściowy za dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się przed dopasowanym tekstem zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli nie zostanie odnaleziony odpowiednik `$'` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorzec wyrażenia regularnego `\d+` odpowiadające sekwencję jeden lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępczy `$'` zastępuje te znaki tekst następujący dopasowania.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli przedstawiono sposób `$'` podstawienia powoduje, że aparat wyrażeń regularnych zastąpić każdym dopasowaniu w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg po dopasowaniu|Ciąg wynikowy|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|AA**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Powrót do początku](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Podstawianie ostatniej przechwyconej grupy  
 `$+` Podstawienia są zastępowane dopasowany ciąg ostatniego przechwyconej grupy. Jeśli nie ma żadnych grup przechwyconych lub wartość ostatniego przechwyconej grupy jest <xref:System.String.Empty?displayProperty=nameWithType>, `$+` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie identyfikuje zduplikowane słowa w ciągu i używa `$+` podstawienia je zastąpić pojedyncze wystąpienie wyrazu. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Jest używana opcja, aby upewnić się, że słowa, które różnią się wielkością liter, ale w przeciwnym razie są identyczne są traktowane jako duplikaty.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\s\1\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasowanie pierwszej przechwyconej grupy.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#Top)  
  
<a name="EntireString"></a>   
## <a name="substituting-the-entire-input-string"></a>Podstawianie całego ciągu wejściowego  
 `$_` Podstawienia są zastępowane dopasowany ciąg cały ciąg wejściowy. Oznacza to, że usuwa dopasowany tekst i zastępuje go całym ciągiem, w tym dopasowanym tekstem.  
  
 W poniższym przykładzie jest dopasowywana co najmniej jedna cyfra dziesiętna w ciągu wejściowym. Używa `$_` podstawienia je zastąpić cały ciąg wejściowy.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 W tym przykładzie ciąg wejściowy `"ABC123DEF456"` zawiera dwa dopasowań. W poniższej tabeli przedstawiono sposób `$_` podstawienia powoduje, że aparat wyrażeń regularnych zastąpić każdym dopasowaniu w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Dopasowanie|Ciąg wynikowy|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
