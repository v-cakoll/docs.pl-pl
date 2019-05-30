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
ms.openlocfilehash: 5c06a20e3d6cf3030da1cc63435423e087408aa6
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301501"
---
# <a name="substitutions-in-regular-expressions"></a>Podstawienia w wyrażeniach regularnych
<a name="Top"></a> Podstawienia są elementami języka, które są rozpoznawane tylko we wzorcach zamieniania. Używają one wzorca wyrażenia regularnego w celu zdefiniowania całości lub części teksu, który ma zastąpić dopasowany tekst w ciągu wejściowym. Wzorzec zamieniania może składać się z co najmniej jednego podstawienia oraz znaków literału. Wzorce zamieniania są dostarczane do przeciążeń <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, która ma `replacement` parametru i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody. Te metody zamieniają dopasowany wzorzec z wzorcem, który jest definiowany przez `replacement` parametru.  
  
 Program .NET Framework definiuje elementy podstawień wymienione w poniższej tabeli.  
  
|Podstawienie|Opis|  
|------------------|-----------------|  
|$ *Numer*|Zawiera ostatni podciąg dopasowany przez grupę przechwytywania, która jest identyfikowana przez *numer*, gdzie *numer* jest wartość dziesiętna w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie numerowanej grupy](#Numbered).|  
|${ *nazwa* }|Zawiera ostatni podciąg dopasowany przez nazwaną grupę, który jest wyznaczone przez `(?<` *nazwa* `> )` w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie nazwanej grupy](#Named).|  
|$$|Zawiera pojedynczy literał „$” w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie symbolu "$"](#DollarSign).|  
|$&|Zawiera kopię całego dopasowania w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie całego dopasowania](#EntireMatch).|  
|$\`|Zawiera cały tekst ciągu wejściowego przed dopasowaniem w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie tekstu przed dopasowaniem](#BeforeMatch).|  
|$'|Zawiera cały tekst ciągu wejściowego po dopasowaniu w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie tekstu po dopasowaniu](#AfterMatch).|  
|$+|Zawiera ostatnią grupę przechwyconą w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie ostatniej przechwyconej grupy](#LastGroup).|  
|$_|Zawiera cały ciąg wejściowy w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie całego ciągu wejściowego](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Elementy podstawienia i wzorce zamieniania  
 Podstawienia to jedyne konstrukcje specjalne rozpoznawane we wzorcu zamieniania. Żadne inne elementy języka wyrażeń regularnych, w tym znak ucieczki i kropka (`.`), który dopasowuje dowolny znak, są obsługiwane. Podobnie elementy języka podstawień są rozpoznawane tylko we wzorcach zamieniania, i nigdy nie są prawidłowe we wzorcach wyrażeń regularnych.  
  
 Jedynym znakiem, który może znajdować się we wzorcu wyrażenia regularnego, jak i w podstawieniu jest `$` znaków, ale ma on inne znaczenie w każdym kontekście. We wzorcu wyrażenia regularnego `$` jest kotwicą dopasowującą koniec ciągu. We wzorcu zamieniania znak `$` wskazuje początek podstawienia.  
  
> [!NOTE]
>  Aby w wyrażeniu regularnym uzyskać funkcjonalność podobną do wzorca zamieniania, należy użyć dopasowywania wstecznego. Aby uzyskać więcej informacji dotyczących dopasowywania wstecznego, zobacz [konstrukcje dopasowywania wstecznego](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Podstawianie numerowanej grupy  
 `$` *Numer* element języka zawiera ostatni podciąg dopasowany przez *numer* przechwytywania grupy w ciągu zamiennym, gdzie *numer* jest Indeks grupy przechwytywania. Na przykład wzorzec zamieniania `$1` wskazuje, że dopasowany podciąg ma zostać zamieniony na pierwszą przechwyconą grupę. Aby uzyskać więcej informacji dotyczących numerowanych grup przechwytywania, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Wszystkie cyfry po znaku `$` są interpretowane jako należące do *numer* grupy. Jeśli nie jest to zgodne z zamiarami użytkownika, można podstawić grupę nazwaną. Na przykład, można użyć ciągu zamiennym `${1}1` zamiast `$11` Aby zdefiniować ciąg zamienny jako wartość pierwszej przechwyconej grupy wraz z liczbą "1". Aby uzyskać więcej informacji, zobacz [podstawianie nazwanej grupy](#Named).  
  
 Grupy przechwytywania, którym nie przypisano jawnie nazw, używając `(?<` *nazwa* `>)` składni są numerowane od lewej do prawej, począwszy jeden. Nazwane grupy także są numerowane od lewej do prawej, począwszy od numeru większego o 1 od indeksu ostatniej nienazwanej grupy. Na przykład w wyrażeniu regularnym `(\w)(?<digit>\d)`, indeks `digit` nazwaną grupę wynosi 2.  
  
 Jeśli *numer* nie określa prawidłowej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego `$` *numer* jest interpretowany jako sekwencja znaków literału, który służy do zastępowania każdego dopasowania.  
  
 W poniższym przykładzie użyto `$` *numer* podstawienia do oddzielenia symbolu waluty od wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(\s?\d+[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to pierwsza grupa przechwytywania. Ponieważ jest wzorzec zamieniania `$1`, wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zastępuje całego dopasowanego podciągu na tę przechwyconą grupę.|  
  
 [Powrót do początku](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Podstawianie nazwanej grupy  
 `${` *Nazwa* `}` element języka podstawia ostatni podciąg dopasowany przez *nazwa* grupa przechwytywania — gdzie *nazwa* nazywa się zdefiniowany przez grupę przechwytywania `(?<` *nazwa* `>)` element języka. Aby uzyskać więcej informacji dotyczących nazwanych grup przechwytywania, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Jeśli *nazwa* nie określa prawidłowej nazwanej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, ale zawiera cyfry, `${` *nazwa* `}` jest interpretowany jako numerowana grupa.  
  
 Jeśli *nazwa* określa prawidłowej nazwanej grupy przechwytywania, ani prawidłowej numerowanej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego `${` *nazwa* `}` jest interpretowany jako Sekwencja znaków literału, który służy do zastępowania każdego dopasowania.  
  
 W poniższym przykładzie użyto `${` *nazwa* `}` podstawienia do oddzielenia symbolu waluty od wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(?<amount>\s?\d[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to grupa przechwytywania o nazwie `amount`. Ponieważ jest wzorzec zamieniania `${amount}`, wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zastępuje całego dopasowanego podciągu na tę przechwyconą grupę.|  
  
 [Powrót do początku](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Podstawianie znaku „$”  
 `$$` Podstawienia Wstawia znak literału "$" w zamienianym ciągu.  
  
 W poniższym przykładzie użyto <xref:System.Globalization.NumberFormatInfo> obiektu, aby ustalić symbol waluty bieżącej kultury i jego położenie w ciągu waluty. Następnie jest dynamicznie tworzony wzorzec wyrażenia regularnego i wzorzec zamieniania. Jeśli ten przykład zostanie uruchomiony na komputerze, którego bieżącą kulturą jest en US, generuje wzorzec wyrażenia regularnego `\b(\d+)(\.(\d+))?` oraz wzorzec zamieniania `$$ $1$2`. Wzorzec zamieniania zamienia dopasowany tekst na symbol waluty i spację, po której następują pierwsza i druga przechwycona grupa.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\d+)(\.(\d+))?` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczęcie dopasowywania na początku granicy wyrazu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to pierwsza grupa przechwytywania.|  
|`\.`|Dopasowanie kropki (separator dziesiętny).|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to trzecia grupa przechwytywania.|  
|`(\.(\d+))?`|Dopasowanie zera lub jednego wystąpienia kropki, po którym następuje co najmniej jedna cyfra dziesiętna. Jest to druga grupa przechwytywania.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Podstawianie całego dopasowania  
 `$&` Podstawienia zawiera całe dopasowanie w ciągu zamiennym. Często jest używane do dodawania podciągu na początku lub końcu dopasowanego ciągu. Na przykład `($&)` wzorzec zamieniania dodaje nawiasy na początku i końcu każdego dopasowania. Jeśli nie zostanie odnaleziony odpowiednik `$&` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto `$&` podstawienia w celu dodania znaków cudzysłowu na początku i na końcu tytułów książek przechowywanych w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego `^(\w+\s?)+$` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczęcie dopasowywania na początku ciągu wejściowego.|  
|`(\w+\s?)+`|Dopasowanie wzorca jednego lub większej liczby znaków słowa, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 `"$&"` Wzorzec zamieniania dodaje literalny znak cudzysłowu na początku i końcu każdego dopasowania.  
  
 [Powrót do początku](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Podstawianie tekstu przed dopasowaniem  
 ``$` `` Podstawienia zamienia dopasowany ciąg na cały ciąg wejściowy przed dopasowaniem. Oznacza to, że duplikuje ciąg wejściowy przed dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się po dopasowanym tekście zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli w ciągu wejściowym będzie znajdować się wiele dopasowań, tekst zamienny będzie pochodził z oryginalnego ciągu wejściowego, a nie z ciągu, w którym tekst został zamieniony na poprzednie dopasowania. \(Przykład stanowi ilustrację.\) Jeśli nie zostanie odnaleziony odpowiednik ``$` `` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorca wyrażenia regularnego `\d+` dostosowując sekwencji jednego lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępujący ``$` `` zamienia te cyfry na tekst, który poprzedza dopasowanie.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli przedstawiono sposób, w jaki ``$` `` podstawienia powoduje, że aparat wyrażeń regularnych do zastępowania każdego dopasowania w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg przed dopasowaniem|Ciąg wynikowy|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Powrót do początku](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Podstawianie tekstu po dopasowaniu  
 `$'` Podstawienia zamienia dopasowany ciąg na cały ciąg wejściowy po dopasowaniu. Oznacza to, że duplikuje ciąg wejściowy za dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się przed dopasowanym tekstem zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli nie zostanie odnaleziony odpowiednik `$'` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorca wyrażenia regularnego `\d+` dostosowując sekwencji jednego lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępujący `$'` zamienia te cyfry na tekst, który następuje po dopasowaniu.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli przedstawiono sposób, w jaki `$'` podstawienia powoduje, że aparat wyrażeń regularnych do zastępowania każdego dopasowania w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg po dopasowaniu|Ciąg wynikowy|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Powrót do początku](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Podstawianie ostatniej przechwyconej grupy  
 `$+` Podstawienia zamienia dopasowany ciąg na ostatnią przechwyconą grupę. W przypadku braku przechwyconych grup lub jeśli ma wartość ostatnią przechwyconą grupę <xref:System.String.Empty?displayProperty=nameWithType>, `$+` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie identyfikowane zduplikowane wyrazy w ciągu i używa `$+` podstawienia w celu zamieniania ich na pojedyncze wystąpienie wyrazu. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Opcja służy do zapewnienia, że wyrazy, które różnią się w przypadku, ale które w przeciwnym razie są identyczne są traktowane jako duplikaty.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\w+)\s\1\b` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
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
 `$_` Podstawienia zamienia dopasowany ciąg na cały ciąg wejściowy. Oznacza to, że usuwa dopasowany tekst i zastępuje go całym ciągiem, w tym dopasowanym tekstem.  
  
 W poniższym przykładzie jest dopasowywana co najmniej jedna cyfra dziesiętna w ciągu wejściowym. Używa ona `$_` podstawienia w celu zamieniania ich na cały ciąg wejściowy.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 W tym przykładzie ciąg wejściowy `"ABC123DEF456"` zawiera dwa dopasowania. W poniższej tabeli przedstawiono sposób, w jaki `$_` podstawienia powoduje, że aparat wyrażeń regularnych do zastępowania każdego dopasowania w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Dopasowanie|Ciąg wynikowy|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
