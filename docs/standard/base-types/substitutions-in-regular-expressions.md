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
ms.openlocfilehash: 6e5773c220dccd4d139b4f85e19b55048a64e7ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288007"
---
# <a name="substitutions-in-regular-expressions"></a>Podstawienia w wyrażeniach regularnych
Podstawienia są elementami języka, które są rozpoznawane tylko w obrębie wzorców zamiennych. Używają one wzorca wyrażenia regularnego w celu zdefiniowania całości lub części teksu, który ma zastąpić dopasowany tekst w ciągu wejściowym. Wzorzec zamieniania może składać się z co najmniej jednego podstawienia oraz znaków literału. Wzorce zastępujące są dostarczane do przeciążenia <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody, która ma `replacement` parametr i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę. Metody zastępują pasujący wzorzec wzorcem zdefiniowanym przez `replacement` parametr.  
  
 Program .NET Framework definiuje elementy podstawień wymienione w poniższej tabeli.  
  
|Podstawienie|Opis|  
|------------------|-----------------|  
|$ *Liczba*|Zawiera ostatni podciąg dopasowany przez grupę przechwytywania, która jest identyfikowana przez *liczbę*, gdzie *Number* jest wartością dziesiętną w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie numerowanej grupy](#substituting-a-numbered-group).|  
|$ { *name* }|Zawiera ostatni podciąg dopasowany przez nazwaną grupę, która jest oznaczona `(?<` *nazwą* `> )` w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie nazwanej grupy](#substituting-a-named-group).|  
|$$|Zawiera pojedynczy literał „$” w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie symbolu "$"](#substituting-a--character).|  
|$&|Zawiera kopię całego dopasowania w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Podstawianie całego dopasowania](#substituting-the-entire-match).|  
|$\`|Zawiera cały tekst ciągu wejściowego przed dopasowaniem w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie tekstu przed dopasowaniem](#substituting-the-text-before-the-match).|  
|$'|Zawiera cały tekst ciągu wejściowego po dopasowaniu w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie tekstu po dopasowaniu](#substituting-the-text-after-the-match).|  
|$+|Zawiera ostatnią grupę przechwyconą w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [podstawianie ostatniej przechwyconej grupy](#substituting-the-last-captured-group).|  
|$\_|Zawiera cały ciąg wejściowy w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Podstawianie całego ciągu wejściowego](#substituting-the-entire-input-string).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Elementy podstawienia i wzorce zamieniania  
 Podstawienia to jedyne konstrukcje specjalne rozpoznawane we wzorcu zamieniania. Żadne inne elementy języka wyrażeń regularnych, w tym znaki ucieczki i kropka ( `.` ), które pasują do żadnego znaku, są obsługiwane. Podobnie elementy języka podstawień są rozpoznawane tylko we wzorcach zamieniania, i nigdy nie są prawidłowe we wzorcach wyrażeń regularnych.  
  
 Jedynym znakiem, który może występować we wzorcu wyrażenia regularnego lub podstawienia, jest `$` znak, chociaż ma inne znaczenie w każdym kontekście. We wzorcu wyrażenia regularnego `$` jest kotwicą, która pasuje do końca ciągu. W wzorcu zastępczym `$` wskazuje początek podstawienia.  
  
> [!NOTE]
> Aby w wyrażeniu regularnym uzyskać funkcjonalność podobną do wzorca zamieniania, należy użyć dopasowywania wstecznego. Aby uzyskać więcej informacji na temat odwołań wstecznych, zobacz [konstrukcje odwołań wstecznych](backreference-constructs-in-regular-expressions.md).  

## <a name="substituting-a-numbered-group"></a>Podstawianie numerowanej grupy  
 `$`Element języka *liczb* zawiera ostatni podciąg dopasowany przez grupę przechwytywania *liczb* w ciągu zamiennym, gdzie *Number* to indeks grupy przechwytywania. Na przykład wzorzec zastępczy `$1` wskazuje, że dopasowany podciąg ma zostać zastąpiony przez pierwszą przechwyconą grupę. Aby uzyskać więcej informacji na temat numerowanych grup przechwytywania, zobacz [Grouping konstrukcjes](grouping-constructs-in-regular-expressions.md).  
  
 Wszystkie poniższe cyfry `$` są interpretowane jako należące do grupy *Numbers* . Jeśli nie jest to zgodne z zamiarami użytkownika, można podstawić grupę nazwaną. Można na przykład użyć ciągu zamiennego zamiast, `${1}1` `$11` Aby zdefiniować ciąg zamienny jako wartość pierwszej przechwyconej grupy wraz z liczbą "1". Aby uzyskać więcej informacji, zobacz [podstawianie nazwanej grupy](#substituting-a-named-group).  
  
 Grupy przechwytywania, które nie są jawnie przypisane nazw przy użyciu `(?<` składni *nazwy* , `>)` są numerowane od lewej do prawej, począwszy od jednej. Nazwane grupy także są numerowane od lewej do prawej, począwszy od numeru większego o 1 od indeksu ostatniej nienazwanej grupy. Na przykład w wyrażeniu regularnym `(\w)(?<digit>\d)` indeks `digit` nazwanej grupy wynosi 2.  
  
 Jeśli parametr *Number* nie określa prawidłowej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, `$` *Liczba* jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania każdego dopasowania.  
  
 W poniższym przykładzie zastosowano `$` podstawianie *liczb* w celu rozdzielenia symbolu waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Wzorzec wyrażenia regularnego `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(\s?\d+[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to pierwsza grupa przechwytywania. Ze względu na to, że wzorzec zamiany jest `$1` , wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody zastępuje cały dopasowany podciąg tej przechwyconej grupy.|  

## <a name="substituting-a-named-group"></a>Podstawianie nazwanej grupy  
 `${` *name* `}` Element Language Name zastępuje ostatni podciąg dopasowany przez grupę przechwytywania *nazw* , gdzie *name* to nazwa grupy przechwytywania zdefiniowanej przez `(?<` *name* `>)` element języka nazwy. Aby uzyskać więcej informacji na temat nazwanych grup przechwytywania, zobacz [Grouping konstrukcjes](grouping-constructs-in-regular-expressions.md).  
  
 Jeśli *Nazwa* nie określa prawidłowej nazwanej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, ale zawiera cyfry, `${` *Nazwa* `}` jest interpretowana jako Grupa numerowana.  
  
 Jeśli *name* nie określa prawidłowej nazwanej grupy przechwytywania ani prawidłowej numerowanej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, `${` *Nazwa* `}` jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania każdego dopasowania.  
  
 W poniższym przykładzie zastosowano `${` *name* `}` podstawianie nazw w celu rozdzielenia symbolu waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(?<amount>\s?\d[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. To jest grupa przechwytywania o nazwie `amount` . Ze względu na to, że wzorzec zamiany jest `${amount}` , wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody zastępuje cały dopasowany podciąg tej przechwyconej grupy.|  

## <a name="substituting-a--character"></a>Podstawianie znaku „$”  
 `$$`Podstawienie wstawia literał "$" w zastąpionym ciągu.  
  
 Poniższy przykład używa obiektu, <xref:System.Globalization.NumberFormatInfo> Aby określić symbol waluty bieżącej kultury i jego położenie w ciągu waluty. Następnie jest dynamicznie tworzony wzorzec wyrażenia regularnego i wzorzec zamieniania. Jeśli przykład jest uruchamiany na komputerze, którego bieżącą kulturą jest EN-US, generuje wzorzec wyrażenia regularnego `\b(\d+)(\.(\d+))?` i wzorzec zastępczy `$$ $1$2` . Wzorzec zamieniania zamienia dopasowany tekst na symbol waluty i spację, po której następują pierwsza i druga przechwycona grupa.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Wzorzec wyrażenia regularnego `\b(\d+)(\.(\d+))?` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczęcie dopasowywania na początku granicy wyrazu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to pierwsza grupa przechwytywania.|  
|`\.`|Dopasowanie kropki (separator dziesiętny).|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to trzecia grupa przechwytywania.|  
|`(\.(\d+))?`|Dopasowanie zera lub jednego wystąpienia kropki, po którym następuje co najmniej jedna cyfra dziesiętna. Jest to druga grupa przechwytywania.|  

## <a name="substituting-the-entire-match"></a>Podstawianie całego dopasowania  
 `$&`Podstawienie obejmuje całe dopasowanie w ciągu zamiennym. Często jest używane do dodawania podciągu na początku lub końcu dopasowanego ciągu. Na przykład `($&)` wzorzec zastępczy dodaje nawiasy na początku i końcu każdego dopasowania. Jeśli nie ma dopasowania, `$&` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie użyto `$&` podstawienia do dodania cudzysłowu na początku i końcu tytułów ksiąg przechowywanych w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Wzorzec wyrażenia regularnego `^(\w+\s?)+$` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczęcie dopasowywania na początku ciągu wejściowego.|  
|`(\w+\s?)+`|Dopasowanie wzorca jednego lub większej liczby znaków słowa, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 `"$&"`Wzorzec zamieniania dodaje znak cudzysłowu na początku i końcu każdego dopasowania.  

## <a name="substituting-the-text-before-the-match"></a>Podstawianie tekstu przed dopasowaniem  
 ``$` ``Podstawienie zastępuje dopasowany ciąg do całego ciągu wejściowego przed dopasowaniem. Oznacza to, że duplikuje ciąg wejściowy przed dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się po dopasowanym tekście zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli w ciągu wejściowym będzie znajdować się wiele dopasowań, tekst zamienny będzie pochodził z oryginalnego ciągu wejściowego, a nie z ciągu, w którym tekst został zamieniony na poprzednie dopasowania. \(Przykład zawiera ilustrację. \) Jeśli nie ma dopasowania, ``$` `` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie zastosowano wzorzec wyrażenia regularnego w `\d+` celu dopasowania sekwencji jednej lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępujący ``$` `` zastępuje te cyfry tekstem poprzedzającym dopasowanie.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli pokazano, w jaki sposób ``$` `` podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Położenie|Ciąg przed dopasowaniem|Ciąg wynikowy|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|AA**AA**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**EE5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|

## <a name="substituting-the-text-after-the-match"></a>Podstawianie tekstu po dopasowaniu  
 `$'`Podstawienie zastępuje dopasowany ciąg do całego ciągu wejściowego po dopasowaniu. Oznacza to, że duplikuje ciąg wejściowy za dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się przed dopasowanym tekstem zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli nie ma dopasowania, `$'` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie zastosowano wzorzec wyrażenia regularnego w `\d+` celu dopasowania sekwencji jednej lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg zastępujący `$'` zastępuje te cyfry tekstem, który następuje po dopasowaniu.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 W tym przykładzie ciąg wejściowy `"aa1bb2cc3dd4ee5"` zawiera pięć dopasowań. W poniższej tabeli pokazano, w jaki sposób `$'` podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Położenie|Ciąg po dopasowaniu|Ciąg wynikowy|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**EE5**EE5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  

## <a name="substituting-the-last-captured-group"></a>Podstawianie ostatniej przechwyconej grupy  
 `$+`Podstawienie zastępuje dopasowany ciąg ostatnią przechwyconą grupą. Jeśli nie ma żadnych przechwyconych grup lub jeśli wartość ostatniej przechwyconej grupy to <xref:System.String.Empty?displayProperty=nameWithType> , `$+` podstawianie nie ma żadnego wpływu.  
  
 Poniższy przykład identyfikuje duplikaty wyrazów w ciągu i używa `$+` podstawienia, aby zastąpić je pojedynczym wystąpieniem wyrazu. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>Opcja służy do upewnienia się, że wyrazy, które różnią się w przypadku, ale inaczej, są traktowane jako duplikaty.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\s\1\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasowanie pierwszej przechwyconej grupy.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  

## <a name="substituting-the-entire-input-string"></a>Podstawianie całego ciągu wejściowego  
 `$_`Podstawienie zastępuje dopasowany ciąg ciągiem zawierającym cały ciąg wejściowy. Oznacza to, że usuwa dopasowany tekst i zastępuje go całym ciągiem, w tym dopasowanym tekstem.  
  
 W poniższym przykładzie jest dopasowywana co najmniej jedna cyfra dziesiętna w ciągu wejściowym. Używa `$_` podstawienia, aby zamienić je na cały ciąg wejściowy.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 W tym przykładzie ciąg wejściowy `"ABC123DEF456"` zawiera dwa dopasowania. W poniższej tabeli pokazano, w jaki sposób `$_` podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Położenie|Dopasowanie|Ciąg wynikowy|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|**ABC123DEF456**ABC DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
