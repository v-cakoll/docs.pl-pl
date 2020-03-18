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
ms.openlocfilehash: 3562bd113ae4c9a3f721d8858a5d3625ef548d3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160082"
---
# <a name="substitutions-in-regular-expressions"></a>Podstawienia w wyrażeniach regularnych
Podstawienia są elementy języka, które są rozpoznawane tylko w ramach wzorców zastępczych. Używają one wzorca wyrażenia regularnego w celu zdefiniowania całości lub części teksu, który ma zastąpić dopasowany tekst w ciągu wejściowym. Wzorzec zamieniania może składać się z co najmniej jednego podstawienia oraz znaków literału. Wzorce wymiany są dostarczane <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> do przeciążenia metody, które mają `replacement` parametr i metody. <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metody zastępują dopasowany szyk wzorkiem zdefiniowanym `replacement` przez parametr.  
  
 Program .NET Framework definiuje elementy podstawień wymienione w poniższej tabeli.  
  
|Podstawienie|Opis|  
|------------------|-----------------|  
|$ *Numer*|Zawiera ostatni podciąg dopasowany przez grupę przechwytywania, która jest identyfikowana przez *liczbę*, gdzie *liczba* jest wartością dziesiętną, w ciągu zastępczym. Aby uzyskać więcej informacji, zobacz [Zastępowanie grupy numerowanych](#substituting-a-numbered-group).|  
|${ *nazwa* }|Zawiera ostatni podciąg dopasowany przez nazwaną `(?<`grupę, która jest wyznaczona przez *nazwę* `> )` w ciągu zastępczym. Aby uzyskać więcej informacji, zobacz [Zastępowanie nazwanej grupy](#substituting-a-named-group).|  
|$$|Zawiera pojedynczy literał „$” w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie symbolu "$".](#substituting-a--character)|  
|$&|Zawiera kopię całego dopasowania w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie całego dopasowania](#substituting-the-entire-match).|  
|$\`|Zawiera cały tekst ciągu wejściowego przed dopasowaniem w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie tekstu przed dopasowaniem](#substituting-the-text-before-the-match).|  
|$'|Zawiera cały tekst ciągu wejściowego po dopasowaniu w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie tekstu po meczu](#substituting-the-text-after-the-match).|  
|$+|Zawiera ostatnią grupę przechwyconą w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie grupy ostatnio przechwyconej](#substituting-the-last-captured-group).|  
|$\_|Zawiera cały ciąg wejściowy w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Zastępowanie całego ciągu wejściowego](#substituting-the-entire-input-string).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Elementy podstawienia i wzorce zamieniania  
 Podstawienia to jedyne konstrukcje specjalne rozpoznawane we wzorcu zamieniania. Żaden z innych elementów języka wyrażenia regularnego, w`.`tym unika znaków i kropka ( ), który pasuje do dowolnego znaku, są obsługiwane. Podobnie elementy języka podstawień są rozpoznawane tylko we wzorcach zamieniania, i nigdy nie są prawidłowe we wzorcach wyrażeń regularnych.  
  
 Jedynym znakiem, który może pojawić się we wzorcu wyrażenia regularnego `$` lub w podstawieniu, jest znak, chociaż ma inne znaczenie w każdym kontekście. We wzorcu wyrażenia `$` regularnego jest kotwica, która pasuje do końca ciągu. We wzorcu `$` zamiennym wskazuje początek podstawienia.  
  
> [!NOTE]
> Aby w wyrażeniu regularnym uzyskać funkcjonalność podobną do wzorca zamieniania, należy użyć dopasowywania wstecznego. Aby uzyskać więcej informacji na temat odwołań wstecznych, zobacz [Backreference Konstrukcje](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).  

## <a name="substituting-a-numbered-group"></a>Podstawianie numerowanej grupy  
 Element `$`języka *liczbowego* zawiera ostatni podciąg dopasowany przez grupę przechwytywania *numerów* w ciągu zastępczym, gdzie *liczba* jest indeksem grupy przechwytywania. Na przykład wzorzec `$1` zastępczy wskazuje, że dopasowany podciąg ma zostać zastąpiony przez pierwszą przechwyconą grupę. Aby uzyskać więcej informacji na temat numerowanych grup przechwytywania, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Wszystkie następujące `$` cyfry są interpretowane jako należące do grupy *numerów.* Jeśli nie jest to zgodne z zamiarami użytkownika, można podstawić grupę nazwaną. Na przykład można użyć ciągu `${1}1` zastępczego `$11` zamiast zdefiniować ciąg zastępczy jako wartość pierwszej przechwyconej grupy wraz z liczbą "1". Aby uzyskać więcej informacji, zobacz [Zastępowanie nazwanej grupy](#substituting-a-named-group).  
  
 Przechwytywanie grup, które nie `(?<`są jawnie przypisane nazwy przy użyciu składni *nazwy* `>)` są numerowane od lewej do prawej, począwszy od jednego. Nazwane grupy także są numerowane od lewej do prawej, począwszy od numeru większego o 1 od indeksu ostatniej nienazwanej grupy. Na przykład w wyrażeniu `(\w)(?<digit>\d)`regularnym `digit` indeks nazwanego grupy wynosi 2.  
  
 Jeśli *liczba* nie określa prawidłowej grupy przechwytywania zdefiniowanej `$`we wzorcu wyrażenia regularnego, *liczba* jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania każdego dopasowania.  
  
 W poniższym `$`przykładzie użyto podstawienia *liczb,* aby usunąć symbol waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Wzorzec `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(\s?\d+[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to pierwsza grupa przechwytywania. Ponieważ wzorzec zastępczy `$1`jest <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> , wywołanie metody zastępuje cały dopasowany podciąg z tej grupy przechwyconych.|  

## <a name="substituting-a-named-group"></a>Podstawianie nazwanej grupy  
 Element `${`języka *nazwy* `}` zastępuje ostatni podciąg dopasowany przez grupę przechwytywania *nazw,* gdzie *nazwa* jest nazwą `(?<`grupy przechwytywania zdefiniowanej przez element języka *nazwy.* `>)` Aby uzyskać więcej informacji na temat nazwanych grup przechwytywania, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 Jeśli *nazwa* nie określa prawidłowej nazwanej grupy przechwytywania zdefiniowanej we wzorcu `${`wyrażenia regularnego, ale składającej się z cyfr, *nazwa* `}` jest interpretowana jako grupa numerowana.  
  
 Jeśli *nazwa* nie określa ani prawidłowej nazwie grupy przechwytywania, ani prawidłowej numerowanej `${`grupy przechwytywania zdefiniowanej we wzorcu wyrażenia regularnego, *nazwa* `}` jest interpretowana jako sekwencja znaków literału, która jest używana do zastępowania każdego dopasowania.  
  
 W poniższym `${`przykładzie użyto podstawienia *nazwy,* `}` aby usunąć symbol waluty z wartości dziesiętnej. Usuwane są symbole waluty znajdujące się na początku lub końcu wartości pieniężnej i rozpoznawane są dwa najpopularniejsze separatory dziesiętne („.” i „,”).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Wzorzec `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\p{Sc}*`|Dopasowanie do zera lub większej liczby znaków symbolu waluty.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`[.,]?`|Dopasowanie do zera lub jednej kropki lub przecinka.|  
|`\d*`|Dopasowanie do zera lub większej liczby cyfr dziesiętnych.|  
|`(?<amount>\s?\d[.,]?\d*)`|Dopasowanie do odstępu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następuje zero lub jedna kropka albo przecinek, po którym następuje zero lub większa liczba cyfr dziesiętnych. Jest to grupa przechwytywania `amount`o nazwie . Ponieważ wzorzec zastępczy `${amount}`jest <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> , wywołanie metody zastępuje cały dopasowany podciąg z tej grupy przechwyconych.|  

## <a name="substituting-a--character"></a>Podstawianie znaku „$”  
 Podstawianie `$$` wstawia literał "$" w zastąpionym ciągu.  
  
 W poniższym <xref:System.Globalization.NumberFormatInfo> przykładzie użyto obiektu do określenia symbolu waluty bieżącej kultury i jej umieszczenia w ciągu waluty. Następnie jest dynamicznie tworzony wzorzec wyrażenia regularnego i wzorzec zamieniania. Jeśli przykład jest uruchamiany na komputerze, którego bieżąca kultura jest `\b(\d+)(\.(\d+))?` en-US, `$$ $1$2`generuje wzorzec wyrażenia regularnego i wzorzec zastępczy . Wzorzec zamieniania zamienia dopasowany tekst na symbol waluty i spację, po której następują pierwsza i druga przechwycona grupa.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Wzorzec `\b(\d+)(\.(\d+))?` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczęcie dopasowywania na początku granicy wyrazu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to pierwsza grupa przechwytywania.|  
|`\.`|Dopasowanie kropki (separator dziesiętny).|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to trzecia grupa przechwytywania.|  
|`(\.(\d+))?`|Dopasowanie zera lub jednego wystąpienia kropki, po którym następuje co najmniej jedna cyfra dziesiętna. Jest to druga grupa przechwytywania.|  

## <a name="substituting-the-entire-match"></a>Podstawianie całego dopasowania  
 Podstawienie `$&` zawiera całe dopasowanie w ciągu zastępczym. Często jest używane do dodawania podciągu na początku lub końcu dopasowanego ciągu. Na przykład `($&)` wzorzec zastępczy dodaje nawiasy do początku i końca każdego dopasowania. Jeśli nie ma dopasowania, `$&` podstawienia nie ma wpływu.  
  
 W poniższym `$&` przykładzie użyto podstawienia, aby dodać cudzysłowy na początku i na końcu tytułów książek przechowywanych w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Wzorzec `^(\w+\s?)+$` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczęcie dopasowywania na początku ciągu wejściowego.|  
|`(\w+\s?)+`|Dopasowanie wzorca jednego lub większej liczby znaków słowa, po których co najmniej raz następuje zero lub jeden znak odstępu.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Wzorzec `"$&"` zastępczy dodaje dosłowny cudzysłów na początku i na końcu każdego dopasowania.  

## <a name="substituting-the-text-before-the-match"></a>Podstawianie tekstu przed dopasowaniem  
 Podstawienie ``$` `` zastępuje dopasowany ciąg całym ciągiem wejściowym przed dopasowaniem. Oznacza to, że duplikuje ciąg wejściowy przed dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się po dopasowanym tekście zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli w ciągu wejściowym będzie znajdować się wiele dopasowań, tekst zamienny będzie pochodził z oryginalnego ciągu wejściowego, a nie z ciągu, w którym tekst został zamieniony na poprzednie dopasowania. \(Przykład zawiera ilustrację. \) Jeśli nie ma dopasowania, ``$` `` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorca `\d+` wyrażenia regularnego, aby dopasować sekwencję co najmniej jednej cyfry dziesiętnej w ciągu wejściowym. Ciąg ``$` `` zastępczy zastępuje te cyfry tekstem poprzedzającym dopasowanie.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 W tym przykładzie ciąg `"aa1bb2cc3dd4ee5"` wejściowy zawiera pięć dopasowań. W poniższej tabeli ``$` `` przedstawiono, w jaki sposób podstawienie powoduje, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg przed dopasowaniem|Ciąg wynikowy|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|

## <a name="substituting-the-text-after-the-match"></a>Podstawianie tekstu po dopasowaniu  
 Podstawienie `$'` zastępuje dopasowany ciąg całym ciągiem wejściowym po dopasowaniu. Oznacza to, że duplikuje ciąg wejściowy za dopasowaniem, a jednocześnie usuwa dopasowany tekst. Ciąg znajdujący się przed dopasowanym tekstem zostanie umieszczony w ciągu wynikowym bez zmian. Jeśli nie ma dopasowania, `$'` podstawienia nie ma wpływu.  
  
 W poniższym przykładzie użyto wzorca `\d+` wyrażenia regularnego, aby dopasować sekwencję co najmniej jednej cyfry dziesiętnej w ciągu wejściowym. Ciąg `$'` zastępczy zastępuje te cyfry tekstem następującym po dopasowaniu.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 W tym przykładzie ciąg `"aa1bb2cc3dd4ee5"` wejściowy zawiera pięć dopasowań. W poniższej tabeli `$'` przedstawiono, w jaki sposób podstawienie powoduje, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Ciąg po dopasowaniu|Ciąg wynikowy|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  

## <a name="substituting-the-last-captured-group"></a>Podstawianie ostatniej przechwyconej grupy  
 Podstawienie `$+` zastępuje dopasowany ciąg z ostatnią przechwyconą grupą. Jeśli nie ma przechwyconych grup lub <xref:System.String.Empty?displayProperty=nameWithType>jeśli `$+` wartość ostatniej przechwyconej grupy jest , podstawienie nie ma wpływu.  
  
 W poniższym przykładzie identyfikuje zduplikowane wyrazy w ciągu i używa `$+` podstawienia, aby zastąpić je jednym wystąpieniem wyrazu. Opcja <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> jest używana w celu zapewnienia, że wyrazy, które różnią się w przypadku, ale które w przeciwnym razie są identyczne, są uważane za duplikaty.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Wzorzec `\b(\w+)\s\1\b` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasowanie pierwszej przechwyconej grupy.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  

## <a name="substituting-the-entire-input-string"></a>Podstawianie całego ciągu wejściowego  
 Podstawienie `$_` zastępuje dopasowany ciąg całym ciągiem wejściowym. Oznacza to, że usuwa dopasowany tekst i zastępuje go całym ciągiem, w tym dopasowanym tekstem.  
  
 W poniższym przykładzie jest dopasowywana co najmniej jedna cyfra dziesiętna w ciągu wejściowym. Używa podstawienia, `$_` aby zastąpić je całym ciągiem wejściowym.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 W tym przykładzie ciąg `"ABC123DEF456"` wejściowy zawiera dwa dopasowania. W poniższej tabeli `$_` przedstawiono, w jaki sposób podstawienie powoduje, że aparat wyrażeń regularnych zastępuje każde dopasowanie w ciągu wejściowym. Wstawiony tekst wyróżniono pogrubieniem w kolumnie wyników.  
  
|Dopasowanie|Pozycja|Dopasowanie|Ciąg wynikowy|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
