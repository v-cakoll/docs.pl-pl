---
title: Opcje wyrażeń regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c229b0fc463863b7113c7ba73890b84e86553b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579655"
---
# <a name="regular-expression-options"></a>Opcje wyrażeń regularnych
<a name="Top"></a> Domyślnie porównanie ciągu wejściowego z dowolnego literał znaków wzorzec wyrażenia regularnego jest rozróżniana wielkość liter, biały znak w wzorzec wyrażenia regularnego jest interpretowana jako literał znaków odstępu i grup przechwytywania w wyrażeniu regularnym są także niejawnie jako jawnie nazwane. Te i kilka innych aspektów domyślnego zachowania wyrażeń regularnych można zmieniać, określając opcje wyrażeń regularnych. Te opcje, które są wymienione w poniższej tabeli, może być wbudowany dołączone jako część wzorzec wyrażenia regularnego lub mogą być dostarczane do <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub statyczna wzorca zgodną metodę jako <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wartości wyliczenia.  
  
|Element członkowski RegexOptions|Znak w tekście|Efekt|  
|-------------------------|----------------------|------------|  
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Niedostępne|Zachowanie domyślne. Aby uzyskać więcej informacji, zobacz [domyślne opcje](#Default).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Używa dopasowywania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz [dopasowania Case-Insensitive](#Case).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Użyj trybu wielowierszowego, gdzie `^` i `$` odpowiada początek i koniec każdego wiersza (zamiast początek i koniec ciągu wejściowego). Aby uzyskać więcej informacji, zobacz [trybu wielowierszowego](#Multiline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Użyj trybu jeden wiersz, jeśli kropki (.) odpowiada każdego znaku (zamiast każdego znaku z wyjątkiem `\n`). Aby uzyskać więcej informacji, zobacz [tryb Singleline](#Singleline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nie przechwytuje nienazwanych grup. Jedyne prawidłowe przechwytywane są jawnie o nazwie lub numerowane grup formularza `(?<` *nazwa* `>` *Podwyrażenie*`)`. Aby uzyskać więcej informacji, zobacz [tylko jawne przechwytuje](#Explicit).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Niedostępne|Kompiluj wyrażenia regularnego do zestawu. Aby uzyskać więcej informacji, zobacz [skompilować wyrażeń regularnych](#Compiled).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Wyklucz niezmienionym znaczeniu biały znak z wzorcem i Włącz komentarze po znaku numeru (`#`). Aby uzyskać więcej informacji, zobacz [Ignoruj biały znak](#Whitespace).|  
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Niedostępne|Umożliwia zmianę kierunku wyszukiwania. Wyszukiwanie Przenosi od prawej do lewej strony zamiast od lewej do prawej. Aby uzyskać więcej informacji, zobacz [tryb od prawej do lewej](#RightToLeft).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Niedostępne|Włącz zgodne ECMAScript zachowanie dla wyrażenia. Aby uzyskać więcej informacji, zobacz [zachowanie dopasowania ECMAScript](#ECMAScript).|  
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Niedostępne|Ignoruj kultury różnice w języku. Aby uzyskać więcej informacji, zobacz [porównanie przy użyciu Niezmienna kultura](#Invariant).|  
  
## <a name="specifying-the-options"></a>Określenie opcji  
 Opcje wyrażeń regularnych można określić w jednym z trzech sposobów:  
  
-   W `options` parametr <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub statyczna (`Shared` w języku Visual Basic) dopasowywanie do wzorca metody, takich jak <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametr jest bitowe połączenie lub <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wyliczyć wartości.  
  
     Jeśli opcje są dostarczane do <xref:System.Text.RegularExpressions.Regex> wystąpienia przy użyciu `options` parametru konstruktora klasy, dostępne są następujące opcje są przypisane do <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwości. Jednak <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwości nie są widoczne opcje wbudowany w samej wzorzec wyrażenia regularnego.  
  
     Poniższy przykład stanowi ilustrację. Używa `options` parametr <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody Włącz dopasowywanie bez uwzględniania wielkości liter i Ignoruj wzorzec biały znak podczas identyfikowania wyrazy, które zaczynają się od litery "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
     [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]  
  
-   Stosując opcje wbudowany w wzorzec wyrażenia regularnego przy użyciu składni `(?imnsx-imnsx)`. Opcja ma zastosowanie do wzorca od punktu zdefiniowania opcji, albo na końcu wzorca lub do punktu, jaką opcję jest niezdefiniowana przez inną opcją wbudowanego. Należy pamiętać, że <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwość <xref:System.Text.RegularExpressions.Regex> wystąpienia nie odzwierciedla tych opcji w tekście. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tematu.  
  
     Poniższy przykład stanowi ilustrację. Używa wbudowanego opcji Włącz dopasowywanie bez uwzględniania wielkości liter i Ignoruj wzorzec biały znak podczas identyfikowania wyrazy, które zaczynają się od litery "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
     [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]  
  
-   Stosując opcje wbudowanego w konkretnym grupowania skonstruować we wzorcu wyrażenia regularnego przy użyciu składni `(?imnsx-imnsx:` *Podwyrażenie*`)`. Nie znaku przed zestaw opcji włącza zestaw; znak minus przed zestaw opcji wyłącza zestawu. (`?` jest stałą część składni konstrukcji języka, który jest wymagany, czy opcje są włączone lub wyłączone.) Opcja ma zastosowanie tylko do tej grupy. Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
     Poniższy przykład stanowi ilustrację. Używa wbudowanego opcje w konstrukcji grupowania Włącz dopasowywanie bez uwzględniania wielkości liter i Ignoruj wzorzec biały znak podczas identyfikowania wyrazy, które zaczynają się od litery "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
     [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
 Jeśli opcje są określony w tekście, znak minus (`-`) przed opcji lub zestaw opcji powoduje wyłączenie tych opcji. Na przykład utworzyć wbudowanej `(?ix-ms)` włącza <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcje i wyłącza <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcje. Wszystkie opcje wyrażeń regularnych są domyślnie wyłączone.  
  
> [!NOTE]
>  Jeśli określone opcje wyrażeń regularnych w `options` określić parametr konflikt wywołanie konstruktora lub metody przy użyciu opcji wbudowanego wzorzec wyrażenia regularnego, opcje w tekście są wykorzystywane.  
  
 Można ustawić następujące pięć opcje wyrażeń regularnych zarówno parametr opcje i wbudowany:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>  
  
 Następujące pięć opcje wyrażeń regularnych można ustawić za pomocą `options` parametru, ale nie można ustawić wbudowany:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>  
  
## <a name="determining-the-options"></a>Określanie opcji  
 Można określić, które opcje zostały dostarczone do <xref:System.Text.RegularExpressions.Regex> obiektu, gdy utworzono wystąpienie pobierając wartość tylko do odczytu <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości. Ta właściwość jest szczególnie przydatne podczas określania opcje, które są zdefiniowane wyrażenie regularne skompilowanych utworzone przez <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.  
  
 Aby przetestować obecność każda opcja, z wyjątkiem <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, w trakcie operacji i wartością <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości i <xref:System.Text.RegularExpressions.RegexOptions> wartość, w której jesteś zainteresowany. Następnie sprawdzić, czy wynik jest równe, który <xref:System.Text.RegularExpressions.RegexOptions> wartość. Następujące testy przykład czy <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> została ustawiona opcja.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
 [!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]  
  
 Aby przetestować <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, określić, czy wartość <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości jest równa <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
 [!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]  
  
 W poniższych sekcjach wymieniono opcje obsługiwane przez wyrażenie regularne programu .NET.  
  
<a name="Default"></a>   
## <a name="default-options"></a>Domyślne opcje  
 <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Opcja wskazuje, że nie określono żadnych opcji i aparat wyrażeń regularnych używa jego zachowanie domyślne. Obejmuje to następujące elementy:  
  
-   Wzorzec jest interpretowany jako canonical zamiast ECMAScript wyrażenia regularnego.  
  
-   Wzorzec wyrażenia regularnego jest takie samo w ciągu wejściowym od lewej do prawej.  
  
-   Porównania jest rozróżniana wielkość liter.  
  
-   `^` i `$` elementy języka zgodny początek i koniec ciągu wejściowego.  
  
-   `.` Każdego znaku z wyjątkiem pasującego elementu języka `\n`.  
  
-   Żadnego odstępu w wzorzec wyrażenia regularnego jest interpretowany jako literału spacją.  
  
-   Konwencje bieżącej kultury są używane podczas porównywania wzorca do ciągu wejściowego.  
  
-   Niejawne, jak również jawne są przechwytywania grupy wzorzec wyrażenia regularnego.  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Opcja nie ma żadnych wbudowanego równoważne. Opcje wyrażeń regularnych są stosowane wbudowanego, domyślne zachowanie został przywrócony na podstawie opcji przez opcję wyłączając jedną z opcji. Na przykład `(?i)` włącza porównania bez uwzględniania wielkości liter, a `(?-i)` przywraca domyślne porównania z uwzględnieniem wielkości liter.  
  
 Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> opcji reprezentuje domyślne zachowanie aparat wyrażeń regularnych, został on rzadko jawnie określony w wywołaniu metody. Konstruktora lub metody statycznej dopasowywanie do wzorca bez `options` parametru jest wywoływana zamiast tego.  
  
 [Powrót do początku](#Top)  
  
<a name="Case"></a>   
## <a name="case-insensitive-matching"></a>Dopasowywanie bez uwzględniania wielkości liter  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Opcji lub `i` opcji wbudowanego udostępnia dopasowania bez uwzględniania wielkości liter. Domyślnie są używane konwencje wielkość liter w bieżącej kultury.  
  
 W poniższym przykładzie zdefiniowano wzorzec wyrażenia regularnego, `\bthe\w*\b`, który dopasowuje wszystkie wyrazy rozpoczynające się od ciągu "". Ponieważ pierwszy wywołanie <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda używa domyślnym porównaniem z uwzględnieniem wielkości liter, dane wyjściowe wskazuje, że ciąg "" rozpoczyna się zdanie nie jest zgodny. Jest on zgodny podczas <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda jest wywoływana z opcjami ustawioną <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
 [!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]  
  
 Poniższy przykład modyfikuje wzorzec wyrażenia regularnego z poprzedniego przykładu, aby użyć opcji wbudowanego zamiast `options` parametr, aby zapewnić porównania bez uwzględniania wielkości liter. Pierwszy wzorzec definiuje opcję bez uwzględniania wielkości liter w konstrukcji grupowania, która ma zastosowanie tylko do litery "t" w ciągu "". Ponieważ konstrukcja opcja występuje na początku wzorca, drugi wzorzec dotyczy opcji bez uwzględniania wielkości liter całego wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
 [!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]  
  
 [Powrót do początku](#Top)  
  
<a name="Multiline"></a>   
## <a name="multiline-mode"></a>Wielowierszowy tryb  
 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Opcji lub `m` opcji wbudowanego umożliwia aparat wyrażeń regularnych do obsługi wejściowy ciąg składający się z wielu wierszy. Zmienia interpretacji `^` i `$` elementy języka aby były one zgodne z początku i końca wiersza, zamiast początek i koniec ciągu wejściowego.  
  
 Domyślnie `$` pasuje do końca ciągu wejściowego. Jeśli określisz <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji odpowiada znaku nowego wiersza (`\n`) lub na końcu ciągu wejściowego. Nie, jednak odpowiada kombinacji znaków CR/LF. Aby pomyślnie dopasować je, użyj Podwyrażenie `\r?$` zamiast tylko `$`.  
  
 W poniższym przykładzie wyodrębnia bowlers nazwy i wyniki i dodaje je do <xref:System.Collections.Generic.SortedList%602> kolekcji, która sortowane w kolejności malejącej. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Metoda jest wywoływana dwukrotnie. W pierwszym wywołaniu metody wyrażenie regularne jest `^(\w+)\s(\d+)$` i opcje nie są ustawione. Jako dane wyjściowe zawierają, ponieważ aparat wyrażeń regularnych nie pasuje do wprowadzania wzorzec wraz z początku i na końcu ciągu wejściowego, nieodnalezienia żadnych dopasowań. W drugim wywołania metody, wyrażenie regularne jest zmieniana na `^(\w+)\s(\d+)\r?$` i opcje są ustawione na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Jak pokazano na dane wyjściowe, nazwy i wyniki są dopasowane, a wyniki są wyświetlane w kolejności malejącej.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
 [!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]  
  
 Wzorzec wyrażenia regularnego `^(\w+)\s(\d+)\r*$` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij na początku wiersza.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to druga grupa przechwytywania.|  
|`\r?`|Zgodne zero lub jeden znak powrotu karetki.|  
|`$`|Końcowy na końcu linii.|  
  
 Poniższy przykład jest odpowiednikiem poprzedniego, z wyjątkiem tego, że używa opcji wbudowanego `(?m)` można ustawić zaznaczono opcję.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]  
  
 [Powrót do początku](#Top)  
  
<a name="Singleline"></a>   
## <a name="single-line-mode"></a>Jednowierszowy tryb  
 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Opcji lub `s` opcja wbudowany, powoduje, że aparat wyrażeń regularnych traktować ciąg wejściowy tak, jakby składa się z jednym wierszu. Jest to zmiana zachowania okresu (`.`) element języka, którego nie pasuje do każdego znaku, zamiast dopasowywania każdego znaku z wyjątkiem znaku nowego wiersza `\n` lub \u000A.  
  
 Poniższy przykład przedstawia sposób zachowania `.` element języka zostanie zmieniona, gdy używasz <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcji. Wyrażenie regularne `^.+` rozpoczyna się od początku ciągu i każdy znak jest zgodna. Domyślnie dopasowania kończy się na końcu pierwszego wiersza; znak powrotu karetki, jest zgodna ze wzorcem wyrażenia regularnego `\r` lub \u000D, ale nie odpowiada `\n`. Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcji interpretuje cały ciąg wejściowy jako pojedynczy wiersz, jest on zgodny każdego znaku w ciągu wejściowym w tym `\n`.  
  
 [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
 [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
 Poniższy przykład jest odpowiednikiem poprzedniego, z wyjątkiem tego, że używa opcji wbudowanego `(?s)` Aby włączyć tryb pojedynczej linii.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]  
  
 [Powrót do początku](#Top)  
  
<a name="Explicit"></a>   
## <a name="explicit-captures-only"></a>Jawne przechwytuje tylko  
 Domyślnie przechwytywania grupy są definiowane za pomocą nawiasów w wzorzec wyrażenia regularnego. Grupy nazwane przypisano nazwę lub numer przez `(?<` *nazwa*`>`*Podwyrażenie* `)` opcji języka, są dostępne dla indeksu nazwy grup. W <xref:System.Text.RegularExpressions.GroupCollection> obiekt bez nazwy grup poprzedzać nazwane grup.  
  
 Konstrukcji grupowania są często używane tylko w celu zastosowania Kwantyfikatory do wielu elementów języka, a przechwycony podciągów są nie zainteresowań. Na przykład jeśli następującym wyrażeniem regularnym:  
  
```  
\b\(?((\w+),?\s?)+[\.!?]\)?  
```  
  
 jest przeznaczony tylko do wyodrębniania zdania zawierające kończyć okres, wykrzyknik lub znak zapytania z dokumentu, wynikowy zdanie (reprezentowany przez <xref:System.Text.RegularExpressions.Match> obiektu) ma znaczenie. Poszczególnych wyrazów w kolekcji nie są.  
  
 Przechwytywanie grup, które nie są następnie używane może być kosztowne, ponieważ aparat wyrażeń regularnych musi wypełnić zarówno <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji obiektów. Alternatywnie, można użyć zarówno <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji lub `n` wbudowanego opcję, aby określić jawnie o nazwie lub numerowane grup, które są oznaczane jedyne prawidłowe przechwytywania `(?<` *nazwa* `>` *Podwyrażenie* `)` utworzenia.  
  
 W poniższym przykładzie przedstawiono informacje o dopasowań zwracana przez `\b\(?((\w+),?\s?)+[\.!?]\)?` wzorzec wyrażenia regularnego, kiedy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda jest wywoływana z włączonymi i wyłączonymi <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji. Jako dane wyjściowe z pierwszego metody należy wywołać pokazuje, aparat wyrażeń regularnych pełni wypełnia <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji obiektów z informacjami o przechwyconych podciągów. Ponieważ druga metoda jest wywoływana z `options` ustawioną <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nie nie przechwytywanie informacji dotyczących grup.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
 [!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]  
  
 Wzorzec wyrażenia regularnego`\b\(?((?>\w+),?\s?)+[\.!?]\)?` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Zaczyna granic programu word.|  
|`\(?`|Zgodne zero lub jeden wystąpień nawias otwierający ("(").|  
|`(?>\w+),?`|Zgodne z co najmniej jeden znak słowa następuje zero lub jeden przecinkami. Nie cofnąć podczas dopasowywania znaków słów.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`((\w+),?\s?)+`|Zgodne kombinację co najmniej jeden znak słowa, zero lub jeden przecinkami i zero lub jeden białe znaki jeden lub więcej razy.|  
|`[\.!?]\)?`|Pasuje do żadnego z trzech interpunkcyjnych, następuje zero lub jeden nawiasów zamykających (")").|  
  
 Można również użyć `(?n)` elementu aby pominąć Przechwytywanie automatycznego. Poniższy przykład modyfikuje poprzedniej wzorzec wyrażenia regularnego, aby użyć `(?n)` elementu zamiast <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
 [!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]  
  
 Ponadto można użyć elementu grupy wbudowane `(?n:)` do pomijania automatyczne przechwytywania na podstawie przez grupy. Poniższy przykład modyfikuje wcześniejszego wzorca do pomijania nienazwane przechwytywania w grupie zewnętrzne `((?>\w+),?\s?)`. Należy pamiętać, że to pomija nienazwane przechwytuje w grupy wewnętrznej.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
 [!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]  
  
 [Powrót do początku](#Top)  
  
<a name="Compiled"></a>   
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie są interpretowane wyrażeń regularnych programu .NET. Gdy <xref:System.Text.RegularExpressions.Regex> obiekt jest wystąpień lub statyczna <xref:System.Text.RegularExpressions.Regex> metoda jest wywoływana, wzorzec wyrażenia regularnego jest analizowana w zestawie używa niestandardowych i interpreter używa tych używa do uruchomienia z wyrażeniem regularnym. Obejmuje to zależnościami: koszt inicjowanie aparatu wyrażenie regularne jest zminimalizowany kosztem wydajności w czasie wykonywania.  
  
 Można użyć skompilowany zamiast wyrażeń regularnych interpretowany za pomocą <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji. W tym przypadku jeśli wzorzec jest przekazywany z aparatem wyrażeń regularnych, jest analizowana na zestaw kodów operacji i następnie przekonwertowane na język pośredni firmy Microsoft (MSIL), które mogą zostać przekazane bezpośrednio do środowiska CLR. Skompilowane wyrażenia regularnego zmaksymalizować wydajność środowiska wykonawczego kosztem czas inicjowania.  
  
> [!NOTE]
>  Wyrażenie regularne może zostać skompilowany tylko podając <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> do wartości `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznej metody dopasowywanie do wzorca. Nie jest dostępny jako opcja wbudowanego.  
  
 Można użyć skompilowanych wyrażeń regularnych w wywołaniach obu statyczna i wyrażenia regularne wystąpienia. W wyrażeniach regularnych statycznych <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji jest przekazywana do `options` parametru metody dopasowywanie do wzorca wyrażenia regularnego. W wyrażeniach regularnych wystąpienia, są przekazywane do `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy. W obu przypadkach go powoduje zwiększoną wydajność.  
  
 Jednak ta poprawa wydajności występuje tylko w następujących warunkach:  
  
-   A <xref:System.Text.RegularExpressions.Regex> obiekt reprezentujący określonego wyrażenia regularnego jest używany w wielu wywołań do metod dopasowywanie do wzorca wyrażenia regularnego.  
  
-   <xref:System.Text.RegularExpressions.Regex> Obiektu nie może znaleźć poza zakresem, dlatego mogą być ponownie używane.  
  
-   Statyczne wyrażenia regularnego jest używany w wielu wywołań do metod dopasowywanie do wzorca wyrażenia regularnego. (Wzrost wydajności jest możliwa, ponieważ wyrażeń regularnych, używanym w wywołaniach metody statycznej są buforowane przez aparat wyrażeń regularnych).  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Opcji jest niezwiązanych ze sobą <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodę, która tworzy zestaw specjalny, który zawiera wstępnie zdefiniowane skompilowane wyrażenia regularnego.  
  
 [Powrót do początku](#Top)  
  
<a name="Whitespace"></a>   
## <a name="ignore-white-space"></a>Ignoruj biały znak  
 Domyślnie jest znacząca; biały znak w wzorzec wyrażenia regularnego wymusi aparat wyrażenia regularnego do dopasowania biały znak w ciągu wejściowym. W związku z tym wyrażenie regularne "`\b\w+\s`"i"`\b\w+` " są w przybliżeniu wyrażeń regularnych. Ponadto w przypadku znak numeru (#) we wzorcu wyrażenia regularnego, jest interpretowany jako literał znaków do dopasowania.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Opcji lub `x` opcji wbudowanego zmieni to domyślne zachowanie w następujący sposób:  
  
-   Niezmienionym znaczeniu biały znak w wzorzec wyrażenia regularnego jest ignorowana. Jako część wyrażenia regularnego, należy użyć znaków ucieczki białe znaki (na przykład jako `\s` lub "`\` ").  
  
-   Znak numeru (#) jest interpretowany jako początek wiersza, a nie jako literał znaków. Cały tekst w wzorzec wyrażenia regularnego z #-znak na końcu ciągu jest interpretowany jako komentarz.  
  
 Jednak w następujących przypadkach białe znaki w wyrażeniu regularnym nie są ignorowane, nawet jeśli używasz <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcji:  
  
-   Biały znak w klasie znaku zawsze jest interpretowany jako literału. Na przykład wzorzec wyrażenia regularnego `[ .,;:]` dopasowuje wszystkie pojedynczy znak odstępu, okres, przecinek, średnik lub dwukropek.  
  
-   Biały znak nie jest dozwolona w nawiasach kwadratowych kwantyfikatora, takich jak `{` *n*`}`, `{` *n*`,}`, i `{` *n* `,` *m*`}`. Na przykład wzorzec wyrażenia regularnego `\d{1. 3}` nie odpowiada dowolnej sekwencji cyfr od jednej do trzech cyfr, ponieważ zawiera biały znak.  
  
-   Biały znak nie jest dozwolone w ramach sekwencji znaków, który wprowadzono w elemencie języka. Na przykład:  
  
    -   Language element `(?:` *Podwyrażenie* `)` reprezentuje grupę nieprzechwyconej i `(?:` część elementu nie osadzonych spacji. Wzorzec `(? :` *Podwyrażenie* `)` zgłasza <xref:System.ArgumentException> na czas wykonywania, ponieważ aparat wyrażeń regularnych nie można przeanalizować wzoru i `( ?:` *Podwyrażenie*  `)` nie powiedzie się dopasować *Podwyrażenie*.  
  
    -   Language element `\p{` *nazwa*`}`, która reprezentuje kategorię Unicode, lub o nazwie blok, nie może zawierać spacji osadzonych w `\p{` część elementu. Jeśli dołączysz biały znak, element zgłasza <xref:System.ArgumentException> w czasie wykonywania.  
  
 Włączenie tej opcji upraszcza wyrażeń regularnych, które są często jest trudne do analizowania i zrozumieć. Poprawia czytelność, a umożliwia dokumentu wyrażenia regularnego.  
  
 W poniższym przykładzie zdefiniowano następujące wzorzec wyrażenia regularnego:  
  
 `\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`  
  
 Ten wzorzec jest podobny do wzorcowi określonemu w [tylko jawne przechwytuje](#Explicit) sekcji z tą różnicą, że używa <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcji ignorowania wzorzec biały znak.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
 [!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]  
  
 W poniższym przykładzie użyto opcji wbudowanego `(?x)` Ignorowanie wzorca biały znak.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
 [!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]  
  
 [Powrót do początku](#Top)  
  
<a name="RightToLeft"></a>   
## <a name="right-to-left-mode"></a>Tryb od prawej do lewej  
 Domyślnie aparat wyrażeń regularnych wyszukiwania od lewej do prawej. Można odwrócić kierunek wyszukiwania przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> opcji. Wyszukiwanie automatycznie rozpoczyna się od ostatniej pozycji znaku w ciągu. Dla metody dopasowywanie do wzorca, które obejmują początkowy pozycji parametrów, takich jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, pozycja początkowa jest indeksem pozycji znaku po prawej stronie, przy którym ma się rozpocząć wyszukiwanie.  
  
> [!NOTE]
>  Wzorzec od prawej do lewej tryb jest dostępny tylko podając <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> do wartości `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub metody statycznej dopasowywanie do wzorca. Nie jest dostępny jako opcja wbudowanego.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Opcja zmian z kierunkiem wyszukiwania; nie ma możliwości interpretowania wzorzec wyrażenia regularnego od prawej do lewej. Na przykład, wyrażenie regularne `\bb\w+\s` odpowiada wyrazy, które zaczynają się od litery "b" i następuje biały znak. W poniższym przykładzie ciąg wejściowy składa się z trzech słów, które obejmują co najmniej jeden znak "b". Pierwsze słowo rozpoczyna się od "b", drugi elementach end, których "b", a trzeci obejmuje dwa znaki "b" w trakcie słowo. Dane wyjściowe w przykładzie pokazano, tylko pierwsze słowo jest zgodny ze wzorcem wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
 [!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]  
  
 Należy również zauważyć, że potwierdzenie wyprzedzenia ( `(?=` *Podwyrażenie* `)` element języka) i wybieganie wstecz asercja ( `(?<=` *Podwyrażenie* `)`element języka) nie należy zmieniać kierunku. Szukaj potwierdzenia wyprzedzenia prawo; Szukaj potwierdzenia wybieganie wstecz do lewej strony. Na przykład, wyrażenie regularne `(?<=\d{1,2}\s)\w+,?\s\d{4}` używa wybieganie wstecz asercja do testowania z datą poprzedzającą nazwy miesięcy. Następnie wyrażenie regularne dopasowuje miesiąca i roku. Aby uzyskać informacje na assertsions wyprzedzenia i wybieganie wstecz, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 [!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
 [!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<=\d{1,2}\s)`|Na początku dopasowania musi być poprzedzona jednego lub dwóch miejsc dziesiętnych, następuje spacja.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`,?`|Zgodne zero lub jeden przecinków.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\d{4}`|Zgodne czterech cyfr dziesiętnych.|  
  
 [Powrót do początku](#Top)  
  
<a name="ECMAScript"></a>   
## <a name="ecmascript-matching-behavior"></a>Zachowanie dopasowania ECMAScript  
 Domyślnie aparat wyrażeń regularnych używa canonical zachowanie podczas dopasowywania wzorzec wyrażenia regularnego do wprowadzania tekstu. Jednak możesz wydać aparat wyrażeń regularnych do używania języka ECMAScript dopasowania zachowanie, określając <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> opcji.  
  
> [!NOTE]
>  Zachowanie zgodne ECMAScript jest dostępna tylko poprzez dostarczanie <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> do wartości `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub metody statycznej dopasowywanie do wzorca. Nie jest dostępny jako opcja wbudowanego.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Opcji można połączyć tylko z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcje. Użyj innych opcji w wyrażeniu regularnym powoduje <xref:System.ArgumentOutOfRangeException>.  
  
 Zachowanie języka ECMAScript i wyrażeń regularnych canonical różni się w trzech obszarach: klasa składni, odwołaniem do samego siebie Przechwytywanie grup i ósemkowe i dopasuje interpretacji znaków.  
  
-   Składnia klasy znaku. Ponieważ canonical wyrażeń regularnych obsługują standardu Unicode, podczas gdy nie jest używany język ECMAScript, klasy znaków w języku ECMAScript ma więcej ograniczeń składnię, a niektóre elementy języka klasy znak ma inne znaczenie. Na przykład ECMAScript nie obsługuje elementów języka, takich jak elementy kategorii lub blok Unicode `\p` i `\P`. Podobnie `\w` element, który pasuje do znaku słowa, jest odpowiednikiem `[a-zA-Z_0-9]` znak klasy, korzystając z języka ECMAScript i `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` używając zachowanie kanonicznej. Aby uzyskać więcej informacji, zobacz [klas znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
     Poniższy przykład przedstawia różnicę między kanonicznej i ECMAScript dopasowywania do wzorca. Definiuje wyrażenie regularne `\b(\w+\s*)+`, słowa, po których białe znaki, które odpowiadają. Dane wejściowe obejmuje dwa ciągi, który używa zestaw znaków łacińskich i drugiej, który korzysta z zestawu cyrylicy. Jak przedstawiono na dane wyjściowe, wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, która używa języka ECMAScript dopasowania nie powiedzie się do dopasowania słów cyrylicy, natomiast używającej canonical dopasowania wywołania metody odpowiada te słowa.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
     [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]  
  
-   Grupuje własnym odwołujące się do przechwytywania. Klasa przechwytywania wyrażenia regularnego z dopasowań dla samej siebie muszą zostać zaktualizowane każdej iteracji przechwytywania. Jak pokazano na poniższym przykładzie, ta funkcja umożliwia wyrażenie regularne `((a+)(\1) ?)+` do dopasowania ciągu wejściowego "aa aaaa aaaaaa", gdy przy użyciu języka ECMAScript, a nie przez dopasowanie kanonicznej.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
     [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]  
  
     Wyrażenie regularne jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |(a+)|Dopasowuje litery "" jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
    |(\1)|Zgodny podciąg przechwycone przez pierwszą grupą przechwytywania. Jest to trzecia grupa przechwytywania.|  
    |?|Zgodne zero lub jeden znaków spacji.|  
    |((a+)(\1) ?)+|Dopasowanie wzorzec co najmniej jeden "" znak następuje ciąg, który odpowiada pierwszej grupy przechwytywania następuje zero lub jeden miejsca znaków jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
-   Rozwiązania niejednoznaczności między specjalne ósemkowe i odwołania wstecznego. W poniższej tabeli przedstawiono różnice w ósemkowe i dopasuje interpretacji przez kanonicznej i wyrażeń regularnych języka ECMAScript.  
  
    |Wyrażenie regularne|Canonical zachowanie|Zachowanie języka ECMAScript|  
    |------------------------|------------------------|-------------------------|  
    |`\0` następuje ósemkowe cyfry 0 do 2|Interpretuj jako ósemkowe. Na przykład `\044` zawsze jest interpretowana jako wartość ósemkową i oznacza "$".|Takie samo zachowanie.|  
    |`\` następuje cyfrę z zakresu od 1 do 9, i nie dodatkowe cyfr dziesiętnych|Interpretuj jako dopasowań. Na przykład `\9` zawsze oznacza dopasuje 9, nawet jeśli dziewiąty Przechwytywanie grupa nie istnieje. Jeśli przechwytywanie grupa nie istnieje, zgłasza analizatora składni wyrażeń regularnych <xref:System.ArgumentException>.|Jeśli przechwytywanie pojedynczą cyfrą dziesiętną grupa istnieje, dopasuje tego cyfry. W przeciwnym razie interpretowania wartości jako literału.|  
    |`\` następuje cyfrę z zakresu od 1 do 9, a następnie dodatkowych cyfr dziesiętnych|Interpretuj cyfr jako wartości dziesiętnej. Jeśli istnieje tej grupy przechwytywania, zinterpretować wyrażenia jako dopasowań.<br /><br /> W przeciwnym razie zinterpretować wiodące cyfry ósemkowe maksymalnie ósemkowe 377; oznacza to należy wziąć pod uwagę tylko niski 8 bitów wartość. Interpretowanie pozostałych znaków jako literały. Na przykład w wyrażeniu `\3000`, jeśli istnieje grupa 300 przechwytywania, zinterpretować jako dopasuje 300; Jeśli przechwytywanie grupy 300 nie istnieje, zinterpretować jako ósemkowe 300 następuje 0.|Interpretuj jako dopasowań, konwertując dowolną liczbę cyfr, jak to możliwe wartości dziesiętnej, który może odwoływać się do przechwytywania. Jeśli można przekonwertować nie cyfr, zinterpretować jako ósemkowe przy użyciu wiodące cyfry ósemkowe maksymalnie ósemkowe 377; Interpretowanie pozostałych znaków jako literały.|  
  
 [Powrót do początku](#Top)  
  
<a name="Invariant"></a>   
## <a name="comparison-using-the-invariant-culture"></a>Porównanie przy użyciu Niezmienna kultura  
 Domyślnie gdy aparat wyrażeń regularnych wykonuje porównania bez uwzględniania wielkości liter, używa konwencji wielkość liter w bieżącej kultury ustalenie równoważne wielkich i małych liter.  
  
 Jednak to zachowanie jest niepożądane dla niektórych typów porównań, zwłaszcza w przypadku porównanie danych wejściowych użytkownika do nazw zasobów systemowych, takich jak hasła, plików lub adresów URL. Poniższy przykład przedstawia przykład scenariusza. Kod jest przeznaczone do blokowania dostępu do dowolnego zasobu, którego adres URL jest poprzedzone znakiem **FILE://**. Wyrażenie regularne prób bez uwzględniania wielkości liter dopasowanie z ciągiem przy użyciu wyrażenia regularnego `$FILE://`. Jednak gdy bieżącego ustawienia kulturowego systemu jest tr-TR (Turecki Turcja), "I" nie jest odpowiednikiem wielkie "litery i". W wyniku wywołania <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metoda zwraca `false`, i jest dozwolony dostęp do pliku.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
 [!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących porównania ciągu, który jest rozróżniana wielkość liter, które korzystają z kulturą niezmienną, zobacz [najlepsze rozwiązania dotyczące ciągów za pomocą](../../../docs/standard/base-types/best-practices-strings.md).  
  
 Zamiast porównania bez uwzględniania wielkości liter bieżącej kultury, określ <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> opcję Ignoruj kultury różnice w języku i użyj Konwencji Niezmienna kultura.  
  
> [!NOTE]
>  Porównanie przy użyciu Niezmienna kultura jest dostępna tylko poprzez dostarczanie <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> do wartości `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub metody statycznej dopasowywanie do wzorca. Nie jest dostępny jako opcja wbudowanego.  
  
 Poniższy przykład jest taki sam jak poprzedni przykład, z wyjątkiem statycznych <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda jest wywoływana z opcjami, które obejmują <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Nawet w przypadku bieżącej kultury jest ustawiony na turecki (Turcja), jest w stanie pomyślnie dopasować "FILE" i "file" i zablokowanie dostępu do zasobu pliku aparat wyrażeń regularnych.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
 [!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
