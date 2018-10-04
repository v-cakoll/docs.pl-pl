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
ms.openlocfilehash: dbc5909a3d4ea1ba2747fcc694bf1f34e20e7d2b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582791"
---
# <a name="regular-expression-options"></a>Opcje wyrażeń regularnych
<a name="Top"></a> Domyślnie porównanie ciągu wejściowego z dowolnymi literałami we wzorcu wyrażenia regularnego jest uwzględniana wielkość liter, biały znak we wzorcu wyrażenia regularnego jest interpretowany jako znaki spacji literału, a grupy przechwytywania w wyrażeniu regularnym są nazywane niejawnie jak również jawnie. Można zmodyfikować te i wiele innych aspektów regularnej ekspresji przez specyfikowanie opcji regularnej ekspresji. Te opcje, które są wymienione w poniższej tabeli, mogą być wbudowane jako część wzorca wyrażenia regularnego lub mogą być dostarczane do <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub statycznym wzorca dopasowania metodę jako <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wartość wyliczenia.  
  
|Członek regexoptions|Wbudowany znak|Efekt|  
|-------------------------|----------------------|------------|  
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Niedostępne|Użyj zachowania domyślnego. Aby uzyskać więcej informacji, zobacz [opcje domyślne](#Default).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Używa dopasowywania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz [dopasowanie bez uwzględniania wielkości liter](#Case).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Użyj trybu wielowierszowego, gdzie `^` i `$` pasuje do początku i końcu każdego wiersza (zamiast początku i końca ciągu wejściowego). Aby uzyskać więcej informacji, zobacz [tryb wielowierszowy](#Multiline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Użyj trybu jednowierszowego, gdzie kropki (.) dopasowuje każdy znak (a nie każdemu znakowi, z wyjątkiem `\n`). Aby uzyskać więcej informacji, zobacz [tryb jednowierszowy](#Singleline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nie przechwytuje nienazwanych grup. Jedyne prawidłowe przechwycenia są jawnie nazwane lub ponumerowane grupy z formularza `(?<` *nazwa* `>` *Podwyrażenie*`)`. Aby uzyskać więcej informacji, zobacz [tylko jawne Przechwytywanie](#Explicit).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Niedostępne|Kompiluj wyrażenie regularne do zestawu. Aby uzyskać więcej informacji, zobacz [skompilowane wyrażenia regularne](#Compiled).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Wyklucz niekodowany biały znak od wzorca i włączanie komentarzy po znaku numeru (`#`). Aby uzyskać więcej informacji, zobacz [Ignoruj białe miejsca](#Whitespace).|  
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Niedostępne|Zmień kierunek wyszukiwania. Wyszukiwanie przenosi się od prawej do lewej zamiast od lewej do prawej. Aby uzyskać więcej informacji, zobacz [tryb od prawej do lewej](#RightToLeft).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Niedostępne|Włącz zachowanie zgodne z ECMAScript, wyrażenie. Aby uzyskać więcej informacji, zobacz [zachowanie dopasowywania ECMAScript](#ECMAScript).|  
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Niedostępne|Ignorowanie różnic kulturowych w języku. Aby uzyskać więcej informacji, zobacz [porównanie przy użyciu niezmiennej kultury](#Invariant).|  
  
## <a name="specifying-the-options"></a>Określenie opcji  
 Można określić opcje dla wyrażeń regularnych w jeden z trzech sposobów:  
  
-   W `options` parametru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub statycznym (`Shared` w języku Visual Basic) metoda dopasowania do wzorca, takich jak <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametr jest bitową kombinacją OR <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> wyliczonych wartości.  
  
     Jeśli opcje są dostarczane do <xref:System.Text.RegularExpressions.Regex> wystąpienia przy użyciu `options` parametr konstruktora klasy, dostępne są następujące opcje są przypisane do <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwości. Jednak <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwość nie będzie odzwierciedlał opcje wbudowane we wzorcu wyrażenia regularnego, sam.  
  
     Poniższy przykład stanowi ilustrację. Używa ona `options` parametru <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, aby umożliwić dopasowanie bez uwzględniania wielkości liter i Ignorowanie wzorca odstępu przy identyfikowaniu wyrazy zaczynające się na literę "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
     [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]  
  
-   Stosując opcje wbudowane we wzorcu wyrażenia regularnego przy użyciu składni `(?imnsx-imnsx)`. Opcja dotyczy wzorca od punktu, opcją jest zdefiniowany do końca wzorca lub punktu, w którym opcją jest niezdefiniowana przez inną opcję wbudowaną. Należy pamiętać, że <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> właściwość <xref:System.Text.RegularExpressions.Regex> wystąpienia nie będzie odzwierciedlał te opcje określane w tekście. Aby uzyskać więcej informacji, zobacz [różne konstrukcje](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tematu.  
  
     Poniższy przykład stanowi ilustrację. Używa opcji wbudowanej, aby umożliwić dopasowanie bez uwzględniania wielkości liter i Ignorowanie wzorca odstępu przy identyfikowaniu wyrazy zaczynające się na literę "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
     [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]  
  
-   Stosując opcje wbudowane w określonej metodzie grupowania konstruowania we wzorcu wyrażenia regularnego przy użyciu składni `(?imnsx-imnsx:` *Podwyrażenie*`)`. Żaden znak przed zestawem opcji nie włącza zestawu; znak minus przed zestawem opcji wyłącza zestaw. (`?` jest stałą częścią składni konstrukcji języka, który jest wymagany, czy opcje są włączone lub wyłączone.) Opcja ma zastosowanie tylko do tej grupy. Aby uzyskać więcej informacji, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
     Poniższy przykład stanowi ilustrację. Jej używa opcji wbudowanej w konstrukcję grupującą, aby umożliwić dopasowanie bez uwzględniania wielkości liter i Ignorowanie wzorca odstępu przy identyfikowaniu wyrazy zaczynające się na literę "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
     [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
 Jeśli opcje są określone w jednej linii, znak minus (`-`) przed opcją lub zestawem opcji powoduje wyłączenie tych opcji. Na przykład wbudowana konstrukcja `(?ix-ms)` włącza <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> a wyłącza opcje <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcje. Wszystkie opcje wyrażeń regularnych są domyślnie wyłączone.  
  
> [!NOTE]
>  Jeśli opcje wyrażenia regularnego określone w `options` parametru konflikt wywołania konstruktora lub metody za pomocą opcji określonymi wewnątrz we wzorcu wyrażenia regularnego, opcje wbudowane są używane.  
  
 Pięć następujących opcji wyrażenia regularnego można ustawić zarówno za pomocą parametru options i wbudowane:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>  
  
 Pięć następujących opcji wyrażenia regularnego można ustawić za pomocą `options` parametru, ale nie można ustawić wbudowany:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>  
  
## <a name="determining-the-options"></a>Określanie opcji  
 Można określić, które opcje są dostarczone do <xref:System.Text.RegularExpressions.Regex> obiektu, kiedy utworzono wystąpienie poprzez pobranie wartości tylko do odczytu <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości. Ta właściwość jest szczególnie przydatne w przypadku określenia opcji, które są zdefiniowane dla skompilowanego wyrażenia regularnego utworzonego przez <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.  
  
 Aby przetestować obecność dowolnej opcji z wyjątkiem <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, wykonać operację AND z wartością <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości i <xref:System.Text.RegularExpressions.RegexOptions> wartość, w którym interesuje Cię. Następnie sprawdź, czy wynik jest równy <xref:System.Text.RegularExpressions.RegexOptions> wartość. Poniższy przykład sprawdza czy <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> została ustawiona opcja.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
 [!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]  
  
 Aby sprawdzić <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, określić, czy wartość <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> właściwości jest równa <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, tak jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
 [!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]  
  
 W poniższych sekcjach wymieniono opcje obsługiwane przez wyrażenia regularne w .NET.  
  
<a name="Default"></a>   
## <a name="default-options"></a>Opcje domyślne  
 <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Opcja wskazuje, że nie określono żadnych opcji, a aparat wyrażeń regularnych używa swojego zachowania domyślnego. Uwzględnione są następujące elementy:  
  
-   Wzorzec jest interpretowany jako kanonicznej zamiast wyrażeń regularnych ECMAScript.  
  
-   Definicję wzorca wyrażenia regularnego jest dopasowywany do ciągu wejściowego od lewej do prawej.  
  
-   Porównania uwzględniają wielkość liter.  
  
-   `^` i `$` elementy języka pasuje do początku i końca ciągu wejściowego.  
  
-   `.` Element języka pasuje do każdego znaku z wyjątkiem `\n`.  
  
-   Dowolny odstęp we wzorcu wyrażenia regularnego jest interpretowany jako znak spacji literału.  
  
-   Podczas porównywania wzorca z ciągiem wejściowym, są używane konwencje bieżącej kultury.  
  
-   Grupy przechwytywania we wzorcu wyrażenia regularnego są niejawne, jak również jawne.  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Opcji nie ma odpowiednika wbudowanego. Opcje wyrażeń regularnych stosowane są wbudowane, domyślne zachowanie zostanie przywrócony na podstawie opcji wg opcji przez wyłączenie konkretnej opcji. Na przykład `(?i)` włącza porównania bez uwzględniania wielkości liter, a `(?-i)` przywraca domyślne porównywanie uwzględniające wielkość liter.  
  
 Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> opcji reprezentuje domyślne zachowanie aparatu wyrażenia regularnego, rzadko jawnie określono w wywołaniu metody. Konstruktor lub statycznej metody dopasowania do wzorca bez `options` zamiast tego wywoływany jest parametr.  
  
 [Powrót do początku](#Top)  
  
<a name="Case"></a>   
## <a name="case-insensitive-matching"></a>Dopasowywanie bez uwzględniania wielkości liter  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Opcji lub `i` opcji wbudowanej, oferuje dopasowywanie bez uwzględniania wielkości liter. Domyślnie są używane konwencje obudowy bieżącej kultury.  
  
 W poniższym przykładzie zdefiniowano wzorzec wyrażenia regularnego `\bthe\w*\b`, który dopasowuje wszystkie wyrazy rozpoczynające się od ciągu "". Ponieważ pierwsze wywołanie do <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda używa domyślnego porównania uwzględniającego wielkość liter, dane wyjściowe wskazują, że ciąg "", który rozpoczyna zdanie, nie został dopasowany. Jest dopasowywany gdy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda jest wywoływana z opcji zestawu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
 [!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]  
  
 Poniższy przykład modyfikuje wzorzec wyrażenia regularnego z poprzedniego przykładu, aby używał opcji wbudowanych zamiast `options` parametru do podania porównania bez uwzględniania wielkości liter. Pierwszy wzorzec definiuje opcją nieuwzględniania wielkości liter w konstrukcji grupowania, która dotyczy tylko litery "t" w ciągu "". Ponieważ konstrukcja opcja występuje na początku wzorca, drugi wzorzec dotyczy opcji nieuwzględniającej wielkości liter całego wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
 [!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]  
  
 [Powrót do początku](#Top)  
  
<a name="Multiline"></a>   
## <a name="multiline-mode"></a>Tryb wielowierszowy  
 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Opcji lub `m` opcji wbudowanej, umożliwia aparatowi wyrażeń regularnych obsługę ciągu wejściowego, który składa się z wielu wierszy. Zmienia interpretację `^` i `$` elementów języka, aby odpowiadały na początku i na końcu wiersza, zamiast początku i końca ciągu wejściowego.  
  
 Domyślnie `$` pasuje do końca ciągu wejściowego. Jeśli określisz <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcji dopasowuje znak nowego wiersza (`\n`) lub na końcu ciągu wejściowego. Nie pasuje jednak kombinacji znaków CR/LF. Aby pomyślnie je dopasować, należy użyć wyrażenia cząstkowego `\r?$` zamiast po prostu `$`.  
  
 Poniższy przykład wyodrębnia nazwiska i wyniki kręglarzy i dodaje je do <xref:System.Collections.Generic.SortedList%602> kolekcji, która sortuje je w kolejności malejącej. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Metoda jest wywoływana dwa razy. W pierwszym wywołaniu metody, wyrażenie regularne jest `^(\w+)\s(\d+)$` i opcje nie są ustawione. Dane wyjściowe pokazują, ponieważ aparat wyrażeń regularnych nie może dopasować wzorca danych wejściowych z początkiem i końcem ciągu wejściowego, nie znaleziono żadnych dopasowań. W drugim wywołaniu metody, wyrażenia regularnego jest zmieniana na `^(\w+)\s(\d+)\r?$` i opcje są ustawione na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Dane wyjściowe pokazują, nazwy i wyniki są pomyślnie dopasowywane, a wyniki są wyświetlane w kolejności malejącej.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
 [!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego `^(\w+)\s(\d+)\r*$` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij na początku wiersza.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d+)`|Dopasowanie do co najmniej jednej cyfry dziesiętnej. Jest to druga grupa przechwytywania.|  
|`\r?`|Odpowiada zero lub jeden znaku powrotu karetki.|  
|`$`|Kończy się na końcu wiersza.|  
  
 Poniższy przykład jest równoważny poprzedniemu, z tą różnicą, że używa opcji wbudowanej `(?m)` można ustawić opcję wiele wierszy.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]  
  
 [Powrót do początku](#Top)  
  
<a name="Singleline"></a>   
## <a name="single-line-mode"></a>Tryb jednowierszowy  
 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Opcji lub `s` opcji wbudowanej, powoduje, że aparat wyrażeń regularnych do traktowania ciąg wejściowy tak, jakby składa się z jednego wiersza. Robi to poprzez zmianę zachowania okresu (`.`) elementu języka, tak że pasuje do każdego znaku, a nie pasuje do każdego znaku z wyjątkiem znaku nowego wiersza `\n` lub \u000A.  
  
 Poniższy przykład ilustruje sposób zachowania `.` zmiany elementu języka, korzystając z <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcji. Wyrażenie regularne `^.+` rozpoczyna się od początku ciągu i dopasowuje każdy znak. Domyślnie dopasowanie kończy się na końcu pierwszego wiersza; wzorzec wyrażenia regularnego pasuje do znaku powrotu karetki `\r` lub \u000D, ale nie jest zgodny `\n`. Ponieważ <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> opcji interpretuje cały ciąg wejściowy jako jeden wiersz, więc dopasowuje każdy znak w ciągu wejściowym, łącznie z `\n`.  
  
 [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
 [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
 Poniższy przykład jest równoważny poprzedniemu, z tą różnicą, że używa opcji wbudowanej `(?s)` do włączenia trybu jednowierszowego.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]  
  
 [Powrót do początku](#Top)  
  
<a name="Explicit"></a>   
## <a name="explicit-captures-only"></a>Tylko jawne Przechwytywanie  
 Domyślnie grupy przechwytywania są definiowane przy użyciu nawiasów we wzorcu wyrażenia regularnego. Nazwane grupy przypisano nazwę lub numer przez `(?<` *nazwa*`>`*Podwyrażenie* `)` język opcji, gdzie nienazwane grupy są dostępne za pomocą indeksu. W <xref:System.Text.RegularExpressions.GroupCollection> obiektu grupy bez nazwy poprzedzają nazwane grupy.  
  
 Konstrukcje grupowania są często używane tylko po to, aby zastosować Kwantyfikatory do wielu elementów języka, a przechwycone podciągi są nie interesujące. Na przykład jeśli następujące wyrażenie regularne:  
  
```  
\b\(?((\w+),?\s?)+[\.!?]\)?  
```  
  
 jest przeznaczony tylko do wyodrębnienia zdań, które kończą się kropką, wykrzyknikiem lub znakiem zapytania z dokumentu, tylko wynikowy zdanie (które jest reprezentowane przez <xref:System.Text.RegularExpressions.Match> obiekt) ma znaczenie. Poszczególne wyrazy w kolekcji nie są.  
  
 Grupy przechwytywania, które nie są następnie używane mogą być kosztowne, ponieważ aparat wyrażeń regularnych musi wypełniać <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji obiektów. Alternatywnie, można użyć <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji lub `n` opcji wbudowanej, aby określić jawnie nazwane lub ponumerowane grupy, które są oznaczone przez jedyne prawidłowe przechwycenia `(?<` *nazwa* `>` *Podwyrażenie* `)` konstruowania.  
  
 Poniższy przykład wyświetla informacje o dopasowań zwracana przez `\b\(?((\w+),?\s?)+[\.!?]\)?` wzorca wyrażenia regularnego, gdy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda jest wywoływana z lub bez <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji. Jak wynika z pierwszej metody wywołania, aparat wyrażeń regularnych <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> kolekcji obiektów z informacjami o przechwyconych podciągach. Ponieważ druga metoda jest wywoływana z `options` równa <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nie przechwytuje informacji na temat grup.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
 [!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]  
  
 Definicję wzorca wyrażenia regularnego`\b\(?((?>\w+),?\s?)+[\.!?]\)?` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij na granicy wyrazu.|  
|`\(?`|Dopasowuje zero lub jeden wystąpień nawias otwierający ("(").|  
|`(?>\w+),?`|Dopasowuje znak słowa, następuje zero lub jeden przecinek. Nie wykonuj nawrotu podczas dopasowywania znaków słowa.|  
|`\s?`|Dopasowanie do zera lub jednego znaku odstępu.|  
|`((\w+),?\s?)+`|Dopasowuje kombinacji jednego lub więcej znaków wyrazu, zero lub jeden przecinek i zero lub jeden znak odstępu jeden lub więcej razy.|  
|`[\.!?]\)?`|Pasuje do żadnego trzy symbole znaków interpunkcyjnych, w którym następuje zero lub jeden zamykający nawias (")").|  
  
 Można również użyć `(?n)` wbudowanego elementu do blokowania automatycznego przechwytywania. Poniższy przykład modyfikuje poprzedni wzorzec wyrażenia regularnego, aby użyć `(?n)` wbudowanego elementu zamiast <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> opcji.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
 [!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]  
  
 Na koniec można użyć wbudowanego elementu grupy `(?n:)` do blokowania automatycznego przechwytywania na podstawie przez grupy. Poniższy przykład modyfikuje poprzedni wzorzec do pomijania nienazwane przechwytywania w grupy zewnętrznej `((?>\w+),?\s?)`. Należy zauważyć, że to pomija nienazwane przechwytywania w grupy wewnętrznej.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
 [!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]  
  
 [Powrót do początku](#Top)  
  
<a name="Compiled"></a>   
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie są interpretowane wyrażenia regularne w .NET. Gdy <xref:System.Text.RegularExpressions.Regex> obiektu jest skonkretyzowany lub statyczna <xref:System.Text.RegularExpressions.Regex> metoda jest wywoływana, wzorzec wyrażenia regularnego jest analizowany na zbiór niestandardowych rozkazów i interpretujący używa tych rozkazów do uruchomienia wyrażenia regularnego. Wiąże się to z kompromisem: koszt inicjowania aparatu wyrażeń regularnych jest zminimalizowany kosztem wydajności w czasie wykonywania.  
  
 Można użyć skompilowanych zamiast interpretowanych wyrażeń regularnych, za pomocą <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji. W tym przypadku gdy wzorzec zostanie przekazany do aparatu wyrażeń regularnych, jest analizowany na zbiór rozkazów i następnie konwertowany na język Microsoft intermediate language (MSIL), które mogą być przekazywane bezpośrednio do środowiska uruchomieniowego języka wspólnego. Skompilowane wyrażenia regularne maksymalizują wydajność uruchomieniową kosztem czasu inicjowania.  
  
> [!NOTE]
>  Wyrażenie regularne może być kompilowane tylko poprzez dostarczenie <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> wartość `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznej metody dopasowania do wzorca. Nie jest dostępna jako opcja wbudowana.  
  
 Można użyć skompilowanych wyrażeń regularnych w wywołaniach statycznych i przypadkowych wyrażeń regularnych. W statycznych wyrażeniach regularnych <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji jest przekazywany do `options` parametru metody dopasowania do wzorca wyrażenia regularnego. W wyrażeniach regularnych wystąpień jest przekazywana do `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy. W obu przypadkach go powoduje zwiększoną wydajność.  
  
 Jednakże ta poprawa wydajności występuje tylko w następujących warunkach:  
  
-   A <xref:System.Text.RegularExpressions.Regex> obiekt, który reprezentuje określonego wyrażenia regularnego jest używana w wielu wywołaniach metod dopasowania do wzorca wyrażenia regularnego.  
  
-   <xref:System.Text.RegularExpressions.Regex> Obiektu nie może wykraczać poza zakres, dzięki czemu mogą być ponownie używane.  
  
-   Statyczne wyrażenie regularne jest używane w wielu wywołaniach metod dopasowania do wzorca wyrażenia regularnego. (Wzrost wydajności jest możliwy, ponieważ wyrażenia regularne użyte w wywołaniach metody statycznej są buforowane przez silnik wyrażeń regularnych).  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Opcja nie jest powiązana z <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody, która tworzy zestaw specjalny zawierający wstępnie skompilowane wyrażenia regularne.  
  
 [Powrót do początku](#Top)  
  
<a name="Whitespace"></a>   
## <a name="ignore-white-space"></a>Ignoruj białe miejsca  
 Domyślnie biały znak we wzorcu wyrażenia regularnego ma znaczenie; Wymusza aparat wyrażeń regularnych, aby dopasować znak odstępu, w ciągu wejściowym. W związku z tym, wyrażenie regularne "`\b\w+\s`"i"`\b\w+` " są mniej więcej odpowiednikami wyrażeń regularnych. Ponadto po napotkaniu we wzorcu wyrażenia regularnego znak numeru (#) jest interpretowany jako znak literałowy, do dopasowania.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Opcji lub `x` opcji wbudowanej, zmienia to zachowanie domyślne w następujący sposób:  
  
-   Niekodowany biały znak we wzorcu wyrażenia regularnego jest ignorowany. Jako część wzorca wyrażenia regularnego, musi być zmienione znaczenie znaków spacji (na przykład, jako `\s` lub "`\` ").  
  
-   Znak numeru (#) jest interpretowany jako początek komentarza, a nie jako znak literałowy. Cały tekst we wzorcu wyrażenia regularnego od znaku # do końca ciągu jest interpretowany jako komentarz.  
  
 Jednak w następujących przypadkach białe znaki w wyrażeniu regularnym nie są ignorowane, nawet w przypadku używania <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> opcji:  
  
-   Biały znak w klasie znaku zawsze jest interpretowany dosłownie. Na przykład wzorzec wyrażenia regularnego `[ .,;:]` pasuje do dowolnego pojedynczy znak odstępu, okres, przecinek, średnik lub średnikami.  
  
-   Biały znak nie jest dozwolona w nawiasach kwadratowych kwantyfikator, takich jak `{` *n*`}`, `{` *n*`,}`, i `{` *n* `,` *m*`}`. Na przykład wzorzec wyrażenia regularnego `\d{1, 3}` nie powiedzie się dopasować istnienie sekwencji cyfr od jednej do trzech cyfr, ponieważ zawiera znak odstępu.  
  
-   Biały znak nie jest dozwolone w obrębie sekwencji znaków, która wprowadza element języka. Na przykład:  
  
    -   Element języka `(?:` *Podwyrażenie* `)` reprezentuje grupę nieprzechwytującą i `(?:` część elementu nie można osadzić miejsca do magazynowania. Wzorzec `(? :` *Podwyrażenie* `)` zgłasza <xref:System.ArgumentException> w czasie wykonywania, ponieważ aparat wyrażeń regularnych nie można przeanalizować wzorzec i wzorzec `( ?:` *Podwyrażenie*  `)` nie powiedzie się dopasować *Podwyrażenie*.  
  
    -   Element języka `\p{` *nazwa*`}`, która reprezentuje kategorię Unicode, lub o nazwie bloku, nie może zawierać spacji osadzonych w `\p{` część elementu. Jeśli dołączysz do odstępu, element zgłasza <xref:System.ArgumentException> w czasie wykonywania.  
  
 Włączenie tej opcji pomaga uprościć wyrażenia regularne, które są często trudne do analizowania i zrozumienia. Zwiększa czytelność i umożliwia dokumentowanie wyrażenia regularnego.  
  
 Poniższy przykład definiuje następujący wzorzec wyrażenia regularnego:  
  
 `\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`  
  
 Wzorzec ten jest podobny do wzorca określonego w [tylko jawne Przechwytywanie](#Explicit) sekcji, z tą różnicą, że używa <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> możliwość Ignorowanie wzorca odstępu.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
 [!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]  
  
 Poniższy przykład używa opcji wbudowanej `(?x)` Ignorowanie wzorca odstępu.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
 [!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]  
  
 [Powrót do początku](#Top)  
  
<a name="RightToLeft"></a>   
## <a name="right-to-left-mode"></a>Tryb od prawej do lewej  
 Domyślnie aparat wyrażenia regularnego przeszukuje od lewej do prawej. Można odwrócić kierunek poszukiwania, używając <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> opcji. Wyszukiwanie rozpoczyna się automatycznie od ostatniej pozycji znaku w ciągu. Dla metod dopasowania do wzorca, które obejmują początkowy pozycji parametrów, takich jak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, pozycja początkowa jest indeksem pozycji znaku po prawej stronie, w którym ma się rozpocząć wyszukiwanie.  
  
> [!NOTE]
>  Tryb wzorca od prawej do lewej jest dostępny tylko poprzez dostarczenie <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> wartość `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznej metody dopasowania do wzorca. Nie jest dostępna jako opcja wbudowana.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Opcji zmienia jedynie kierunek wyszukiwania; nie interpretuje wzorca wyrażenia regularnego od prawej do lewej. Na przykład, wyrażenie regularne `\bb\w+\s` dopasowuje słowa, które zaczynają się od litery "b" i których następuje znak odstępu. W poniższym przykładzie ciąg wejściowy składa się z trzech słów, które zawierają jeden lub więcej znaków "b". Pierwszy wyraz rozpoczyna się znakiem "b", drugi kończy się znakiem "b", a trzeci zawiera dwa znaki "b" w środku. Dane wyjściowe z przykładu pokazują, tylko pierwszy wyraz pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
 [!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]  
  
 Należy również zauważyć, że asercja wyprzedzająca o ( `(?=` *Podwyrażenie* `)` element języka) i asercja z patrzeniem ( `(?<=` *Podwyrażenie* `)`element języka) nie zmieniają kierunku. Asercje wyprzedzające "patrzą" po prawej stronie; asercje wsteczne się po lewej stronie. Na przykład, wyrażenie regularne `(?<=\d{1,2}\s)\w+,?\s\d{4}` używa asercja wsteczna o do testowania dla daty, który poprzedza nazwę miesiąca. Następnie wyrażenie regularne dopasowuje miesiąc i rok. Informacje na temat assertsions lookahead i można zobaczyć [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 [!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
 [!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]  
  
 Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<=\d{1,2}\s)`|Początek dopasowania musi być poprzedzony przez jedną lub dwiema cyframi dziesiętnymi, następuje spacja.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`,?`|Dopasowuje zero lub jeden znak przecinka.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\d{4}`|Odpowiada czterem cyfrom po przecinku.|  
  
 [Powrót do początku](#Top)  
  
<a name="ECMAScript"></a>   
## <a name="ecmascript-matching-behavior"></a>Zachowanie dopasowywania ECMAScript  
 Domyślnie aparat wyrażenia regularnego używa zachowania kanonicznego podczas dopasowywania wzorca wyrażenia regularnego do tekstu wejściowego. Jednak można nakazać aparat wyrażeń regularnych, aby użyć ECMAScript pasujące do zachowania, określając <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> opcji.  
  
> [!NOTE]
>  Zachowanie zgodne z ECMAScript jest dostępne tylko poprzez dostarczenie <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> wartość `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznej metody dopasowania do wzorca. Nie jest dostępna jako opcja wbudowana.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Opcja może być łączone tylko z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> opcje. Użyj innej opcji w wyrażeniu regularnym powoduje <xref:System.ArgumentOutOfRangeException>.  
  
 Zachowanie ECMAScript i kanonicznych wyrażeń regularnych różni się w trzech obszarach: składni klasy odwołujących się do grupy przechwytywania i ósemkowych w porównaniu z dopasowywania wstecznego interpretacji znaków.  
  
-   Składnia klasy znaku. Ponieważ kanoniczne wyrażenia regularne obsługują Unicode, natomiast ECMAScript nie, klasy znaku w ECMAScript mają bardziej ograniczoną składnię, a niektóre elementy języka klasy znaku mają inne znaczenie. Na przykład ECMAScript nie obsługuje elementów języka, takich jak elementy kategorii lub blok Unicode `\p` i `\P`. Podobnie `\w` element, który pasuje do znaku słowa, jest odpowiednikiem `[a-zA-Z_0-9]` klasy znaków, korzystając z ECMAScript i `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` korzystając z zachowania kanonicznego. Aby uzyskać więcej informacji, zobacz [klas znaków](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
     Poniższy przykład ilustruje różnicę między kanonicznym i ECMAScript dopasowywania do wzorca. Definiuje wyrażenie regularne `\b(\w+\s*)+`, które odpowiada wyrazom następują znaki odstępu. Dane wejściowe składa się z dwóch ciągów, jeden używa zestawu znaków łacińskich, a druga używa zestawu znaków cyrylicy. Tak jak pokazano w danych wyjściowych, wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, która używa dopasowywania ECMAScript nie powiedzie się do dopasowania słów w cyrylicy, podczas gdy wywołanie metody używające dopasowania kanonicznego.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
     [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]  
  
-   Grupy przechwytywania odwołujące. Klasa przechwytywania wyrażeń regularnych z odwołaniem wstecznym do siebie musi być aktualizowana przy każdej iteracji przechwytywania. Jak pokazano na poniższym przykładzie, ta funkcja umożliwia wyrażenia regularnego `((a+)(\1) ?)+` do pasuje do ciągu wejściowego "aa aaaa aaaaaa", korzystając z ECMAScript, ale nie przy wykorzystaniu dopasowania kanonicznego.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
     [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]  
  
     Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |(a+)|Odpowiada literze "a" jeden lub więcej razy. Jest to druga grupa przechwytywania.|  
    |(\1)|Dopasuj podciąg przechwycony przez pierwszą grupę przechwytywania. Jest to trzecia grupa przechwytywania.|  
    |?|Dopasowuje zero lub jeden znak spacji.|  
    |((a+)(\1) ?)+|Dopasowanie wzorca jednego lub więcej znaki "a następuje ciąg, który pasuje do pierwszej grupy przechwytywania" następuje zero lub jeden obszar znaków, jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
-   Rozdzielczość niejasności między ósemkową zwraca i wprowadza odwołania wsteczne. W poniższej tabeli podsumowano różnice w ósemkowych w porównaniu z dopasowywania wstecznego interpretacji przez canonical i wyrażeń regularnych ECMAScript.  
  
    |Wyrażenie regularne|Zachowanie kanoniczne|Zachowanie ECMAScript|  
    |------------------------|------------------------|-------------------------|  
    |`\0` następują cyfry ósemkowe 0 do 2|Interpretuj jako ósemkowy. Na przykład `\044` jest zawsze interpretowane jako wartość ósemkowa i oznacza "$".|Takie samo zachowanie.|  
    |`\` następuje numer od 1 do 9, bez dodatkowych cyfr dziesiętnych|Interpretuj jako odwołanie wsteczne. Na przykład `\9` zawsze oznacza odwołanie wsteczne nr 9, nawet jeśli dziewiąta grupa przechwytywania nie istnieje. Jeśli grupa przechwytywania nie istnieje, analizator składni wyrażeń regularnych zgłasza <xref:System.ArgumentException>.|Jeśli przechwytywanie pojedynczą cyfrą dziesiętną grupa istnieje, Utwórz wsteczne odwołanie do tej cyfry. W przeciwnym razie interpretuje wartość jako literał.|  
    |`\` następuje numer od 1 do 9, a następnie dodatkowe cyfry dziesiętne|Interpretuj cyfry jako wartość dziesiętną. Jeśli ta grupa przechwytywania istnieje, następuje interpretacja wyrażenia jako odwołanie wsteczne.<br /><br /> W przeciwnym wypadku interpretuje wiodące cyfry ósemkowe do ósemkowej 377; oznacza to należy rozważyć tylko niskie 8 bitów wartości. Interpretuj pozostałe cyfry jako literały. Na przykład w wyrażeniu `\3000`, jeśli istnieje grupa przechwytywania 300, następuje interpretacja jako odwołania wstecznego 300; Jeśli grupa przechwytywania 300 nie istnieje, następuje interpretacja jako ósemkowe 300, następuje 0.|Interpretuj jako odwołanie wsteczne, konwertując dowolną liczbę cyfr jak najbliżej wartość dziesiętnych, która może odwoływać się do przechwytywania. Jeśli mogą być konwertowane nie cyfry, następuje interpretacja jako wartości ósemkowej za pomocą wiodących cyfr ósemkowych aż do ósemkowej 377; interpretuj pozostałe cyfry jako literały.|  
  
 [Powrót do początku](#Top)  
  
<a name="Invariant"></a>   
## <a name="comparison-using-the-invariant-culture"></a>Porównanie przy użyciu niezmiennej kultury  
 Domyślnie gdy aparat wyrażeń regularnych wykonuje porównania bez uwzględniania wielkości liter, używa konwencji obudowy bieżącej kultury, aby określić równoważne znaki wielkich i małych.  
  
 To zachowanie jest jednak niepożądane dla niektórych rodzajów porównań, szczególnie podczas porównywania danych wprowadzonych przez użytkownika z nazwami zasobów systemowych, takich jak hasła, pliki lub adresy URL. Poniższy przykład ilustruje taki scenariusz. Kod jest przeznaczony do blokowania dostępu do dowolnego zasobu, którego adres URL jest poprzedzony elementem **FILE://**. Wyrażenie regularne próbuje dopasowanie bez uwzględniania wielkości liter na ciąg przy użyciu wyrażeń regularnych `$FILE://`. Jednak gdy bieżącą kulturą systemu jest tr-TR (Turecki-Turcja), "I" nie jest odpowiednikiem wielkie litery "i". W wyniku wywołania <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metoda zwraca `false`, i jest dozwolony dostęp do pliku.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
 [!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat porównań ciągów, które jest rozróżniana wielkość liter i które używają niezmiennej kultury zobacz [najlepsze rozwiązania dotyczące Using Strings](../../../docs/standard/base-types/best-practices-strings.md).  
  
 Zamiast korzystać z porównania bez uwzględniania wielkości liter bieżącej kultury, można określić <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> opcję Ignoruj różnice kulturowe w języku i używać konwencji Niezmienna kultura.  
  
> [!NOTE]
>  Porównanie przy użyciu kultura niezmienna jest dostępne tylko poprzez dostarczenie <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> wartość `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznej metody dopasowania do wzorca. Nie jest dostępna jako opcja wbudowana.  
  
 Poniższy przykład jest identyczny z poprzednim przykładem, chyba że statyczne <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda jest wywoływana z opcji obejmujących <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. Nawet wtedy, gdy bieżącą kulturę ustawiono turecki (Turcja), aparat wyrażeń regularnych jest w stanie pomyślnie dopasować elementy "FILE" i "file" i zablokować dostęp do zasobów plików.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
 [!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
