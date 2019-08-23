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
ms.openlocfilehash: 4b079809fa76097cd575d96c70d17d1c6c85e3a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968529"
---
# <a name="substitutions-in-regular-expressions"></a>Podstawienia w wyrażeniach regularnych
<a name="Top"></a>Podstawienia są elementami języka, które są rozpoznawane tylko w obrębie wzorców zamiennych. Używają one wzorca wyrażenia regularnego w celu zdefiniowania całości lub części teksu, który ma zastąpić dopasowany tekst w ciągu wejściowym. Wzorzec zamieniania może składać się z co najmniej jednego podstawienia oraz znaków literału. Wzorce zastępujące są dostarczane do przeciążenia <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody, która `replacement` ma parametr i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę. Metody zastępują pasujący wzorzec wzorcem zdefiniowanym przez `replacement` parametr.  
  
 Program .NET Framework definiuje elementy podstawień wymienione w poniższej tabeli.  
  
|Podstawienie|Opis|  
|------------------|-----------------|  
|$ *Liczba*|Zawiera ostatni podciąg dopasowany przez grupę przechwytywania, która jest identyfikowana przez *liczbę*, gdzie *Number* jest wartością dziesiętną w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [numerowanej grupy](#Numbered).|  
|$ { *name* }|Zawiera ostatni podciąg dopasowany przez nazwaną grupę, która jest oznaczona `(?<` *nazwą* `> )` w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [nazwanej grupy](#Named).|  
|$$|Zawiera pojedynczy literał „$” w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [symbolu "$"](#DollarSign).|  
|$&|Zawiera kopię całego dopasowania w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [całego dopasowania](#EntireMatch).|  
|$\`|Zawiera cały tekst ciągu wejściowego przed dopasowaniem w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [tekstu przed dopasowaniem](#BeforeMatch).|  
|$'|Zawiera cały tekst ciągu wejściowego po dopasowaniu w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [tekstu po dopasowaniu](#AfterMatch).|  
|$+|Zawiera ostatnią grupę przechwyconą w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [ostatniej przechwyconej grupy](#LastGroup).|  
|$_|Zawiera cały ciąg wejściowy w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz podstawianie [całego ciągu wejściowego](#EntireString).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Elementy podstawienia i wzorce zamieniania  
 Podstawienia to jedyne konstrukcje specjalne rozpoznawane we wzorcu zamieniania. Żadne inne elementy języka wyrażeń regularnych, w tym znaki ucieczki i kropka (`.`), które pasują do żadnego znaku, są obsługiwane. Podobnie elementy języka podstawień są rozpoznawane tylko we wzorcach zamieniania, i nigdy nie są prawidłowe we wzorcach wyrażeń regularnych.  
  
 Jedynym znakiem, który może występować we wzorcu wyrażenia regularnego lub podstawienia, jest `$` znak, chociaż ma inne znaczenie w każdym kontekście. We wzorcu `$` wyrażenia regularnego jest kotwicą, która pasuje do końca ciągu. W wzorcu `$` zastępczym wskazuje początek podstawienia.  
  
> [!NOTE]
> Aby w wyrażeniu regularnym uzyskać funkcjonalność podobną do wzorca zamieniania, należy użyć dopasowywania wstecznego. Aby uzyskać więcej informacji na temat odwołań wstecznych, zobacz [konstrukcje odwołań wstecznych](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>Podstawianie numerowanej grupy  
 Element języka liczb zawiera ostatni podciąg dopasowany przez grupę przechwytywania *liczb* w ciągu zamiennym, gdzie *Number* to indeks grupy przechwytywania. `$` Na przykład wzorzec `$1` zastępczy wskazuje, że dopasowany podciąg ma zostać zastąpiony przez pierwszą przechwyconą grupę. Aby uzyskać więcej informacji na temat numerowanych grup [](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)przechwytywania, zobacz Grouping konstrukcjes.  
  
 Wszystkie poniższe `$` cyfry są interpretowane jako należące do grupy *Numbers* . Jeśli nie jest to zgodne z zamiarami użytkownika, można podstawić grupę nazwaną. Można na przykład użyć ciągu `${1}1` zamiennego `$11` zamiast, aby zdefiniować ciąg zamienny jako wartość pierwszej przechwyconej grupy wraz z liczbą "1". Aby uzyskać więcej informacji, zobacz podstawianie [nazwanej grupy](#Named).  
  
 Grupy przechwytywania, które nie są jawnie przypisane nazw przy `(?<`użyciu składni *nazwy* `>)` , są numerowane od lewej do prawej, począwszy od jednej. Nazwane grupy także są numerowane od lewej do prawej, począwszy od numeru większego o 1 od indeksu ostatniej nienazwanej grupy. Na przykład w wyrażeniu `(\w)(?<digit>\d)`regularnym indeks `digit` nazwanej grupy wynosi 2.  
  
 Jeśli parametr *Number* nie określa prawidłowej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, `$` *Liczba* jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania każdego dopasowania.  
  
 W poniższym przykładzie zastosowano `$`podstawianie *liczb* w celu rozdzielenia symbolu waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Wzorzec `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(\s?\d+[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to pierwsza grupa przechwytywania. Ze względu na to `$1`, że wzorzec zamiany <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> jest, wywołanie metody zastępuje cały dopasowany podciąg tej przechwyconej grupy.|  
  
 [Powrót do początku](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>Podstawianie nazwanej grupy  
 `(?<` Element Languagename`}` zastępuje ostatni podciąg dopasowany przez nazwę grupy przechwytywania, gdzie Name to nazwa grupy przechwytywania zdefiniowanej przez nazwę `${``>)`element języka. Aby uzyskać więcej informacji na temat nazwanych grup [](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)przechwytywania, zobacz Grouping konstrukcjes.  
  
 Jeśli *Nazwa* nie określa prawidłowej nazwanej grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, ale `${`zawiera cyfry, *Nazwa* `}` jest interpretowana jako Grupa numerowana.  
  
 Jeśli *Nazwa* nie określa prawidłowej nazwanej grupy przechwytywania ani prawidłowej numerowanej grupy przechwytywania zdefiniowanej we wzorcu `${`wyrażenia regularnego, *Nazwa* `}` jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania Każdy odpowiednik.  
  
 W poniższym przykładzie zastosowano `${`podstawianie *nazw* `}` w celu rozdzielenia symbolu waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Wzorzec `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(?<amount>\s?\d[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. To jest grupa przechwytywania o nazwie `amount`. Ze względu na to `${amount}`, że wzorzec zamiany <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> jest, wywołanie metody zastępuje cały dopasowany podciąg tej przechwyconej grupy.|  
  
 [Powrót do początku](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>Podstawianie znaku „$”  
 `$$` Podstawienie wstawia literał "$" w zastąpionym ciągu.  
  
 Poniższy przykład używa <xref:System.Globalization.NumberFormatInfo> obiektu, aby określić symbol waluty bieżącej kultury i jego położenie w ciągu waluty. Następnie jest dynamicznie tworzony wzorzec wyrażenia regularnego i wzorzec zamieniania. Jeśli przykład jest uruchamiany na komputerze, którego bieżącą kulturą jest en-us, generuje wzorzec `\b(\d+)(\.(\d+))?` wyrażenia regularnego i wzorzec `$$ $1$2`zastępczy. Wzorzec zamieniania zamienia dopasowany tekst na symbol waluty i spację, po której następują pierwsza i druga przechwycona grupa.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Wzorzec `\b(\d+)(\.(\d+))?` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczęcie dopasowywania na początku granicy wyrazu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to pierwsza grupa przechwytywania.|  
|`\.`|Dopasowanie kropki (separator dziesiętny).|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to trzecia grupa przechwytywania.|  
|`(\.(\d+))?`|Dopasowanie zera lub jednego wystąpienia kropki, po którym następuje co najmniej jedna cyfra dziesiętna. Jest to druga grupa przechwytywania.|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>Podstawianie całego dopasowania  
 `$&` Podstawienie obejmuje całe dopasowanie w ciągu zamiennym. Często jest używane do dodawania podciągu na początku lub końcu dopasowanego ciągu. Na przykład `($&)` wzorzec zastępczy dodaje nawiasy na początku i końcu każdego dopasowania. Jeśli nie ma dopasowania, `$&` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie użyto `$&` podstawienia do dodania cudzysłowu na początku i końcu tytułów ksiąg przechowywanych w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Wzorzec `^(\w+\s?)+$` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczęcie dopasowywania na początku ciągu wejściowego.|  
|`(\w+\s?)+`|Dopasowanie wzorca jednego lub większej liczby znaków słowa, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Wzorzec `"$&"` zamieniania dodaje znak cudzysłowu na początku i końcu każdego dopasowania.  
  
 [Powrót do początku](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>Podstawianie tekstu przed dopasowaniem  
 ``$` `` Podstawienie zastępuje dopasowany ciąg do całego ciągu wejściowego przed dopasowaniem. Oznacza to, że duplikuje ciąg wejściowy przed dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się po dopasowanym tekście zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli w ciągu wejściowym będzie znajdować się wiele dopasowań, tekst zamienny będzie pochodził z oryginalnego ciągu wejściowego, a nie z ciągu, w którym tekst został zamieniony na poprzednie dopasowania. \(Przykład zawiera ilustrację.\) Jeśli nie ma dopasowania, ``$` `` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie zastosowano wzorzec `\d+` wyrażenia regularnego w celu dopasowania sekwencji jednej lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg ``$` `` zastępujący zastępuje te cyfry tekstem poprzedzającym dopasowanie.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 W tym przykładzie ciąg `"aa1bb2cc3dd4ee5"` wejściowy zawiera pięć dopasowań. W poniższej tabeli pokazano, w ``$` `` jaki sposób podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg przed dopasowaniem|Ciąg wynikowy|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|AA**AA**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [Powrót do początku](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>Podstawianie tekstu po dopasowaniu  
 `$'` Podstawienie zastępuje dopasowany ciąg do całego ciągu wejściowego po dopasowaniu. Oznacza to, że duplikuje ciąg wejściowy za dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się przed dopasowanym tekstem zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli nie ma dopasowania, `$'` podstawienie nie ma żadnego wpływu.  
  
 W poniższym przykładzie zastosowano wzorzec `\d+` wyrażenia regularnego w celu dopasowania sekwencji jednej lub więcej cyfr dziesiętnych w ciągu wejściowym. Ciąg `$'` zastępujący zastępuje te cyfry tekstem, który następuje po dopasowaniu.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 W tym przykładzie ciąg `"aa1bb2cc3dd4ee5"` wejściowy zawiera pięć dopasowań. W poniższej tabeli pokazano, w `$'` jaki sposób podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg po dopasowaniu|Ciąg wynikowy|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [Powrót do początku](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>Podstawianie ostatniej przechwyconej grupy  
 `$+` Podstawienie zastępuje dopasowany ciąg ostatnią przechwyconą grupą. Jeśli nie ma żadnych przechwyconych grup lub jeśli wartość ostatniej przechwyconej grupy <xref:System.String.Empty?displayProperty=nameWithType>to `$+` , podstawianie nie ma żadnego wpływu.  
  
 Poniższy przykład identyfikuje duplikaty wyrazów w ciągu i używa podstawienia, `$+` aby zastąpić je pojedynczym wystąpieniem wyrazu. <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> Opcja służy do upewnienia się, że wyrazy, które różnią się w przypadku, ale inaczej, są traktowane jako duplikaty.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Wzorzec `\b(\w+)\s\1\b` wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
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
 `$_` Podstawienie zastępuje dopasowany ciąg ciągiem zawierającym cały ciąg wejściowy. Oznacza to, że usuwa dopasowany tekst i zastępuje go całym ciągiem, w tym dopasowanym tekstem.  
  
 W poniższym przykładzie jest dopasowywana co najmniej jedna cyfra dziesiętna w ciągu wejściowym. Używa podstawienia `$_` , aby zamienić je na cały ciąg wejściowy.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 W tym przykładzie ciąg `"ABC123DEF456"` wejściowy zawiera dwa dopasowania. W poniższej tabeli pokazano, w `$_` jaki sposób podstawienie sprawia, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Dopasowanie|Ciąg wynikowy|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
