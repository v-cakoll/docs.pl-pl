---
title: Model obiektów wyrażeń regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, backreferences
- Regex class
- Match class
- pattern-matching with regular expressions, backreferences
- .NET Framework regular expressions, classes
- CaptureCollection class
- Group class
- characters [.NET Framework], backreferences
- substrings
- .NET Framework regular expressions, backreferences
- searching with regular expressions, classes
- backreferences
- Capture class
- repeating groups of characters
- MatchCollection class
- parsing text with regular expressions, backreferences
- regular expressions [.NET Framework]
- characters [.NET Framework], regular expressions
- classes [.NET Framework], regular expression
- regular expressions [.NET Framework], classes
- characters [.NET Framework], metacharacters
- metacharacters, regular expression classes
- metacharacters, backreferences
- parsing text with regular expressions, classes
- regular expressions [.NET Framework], backreferences
- strings [.NET Framework], regular expressions
- pattern-matching with regular expressions, classes
- GroupCollection class
ms.assetid: 49a21470-64ca-4b5a-a889-8e24e3c0af7e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 856b7c8a842b173fbf3e31323ce7224fc05a4f12
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192850"
---
# <a name="the-regular-expression-object-model"></a>Model obiektów wyrażeń regularnych
<a name="introduction"></a> W tym temacie opisano model obiektów używanych w pracy z wyrażeń regularnych programu .NET. Ten temat zawiera następujące sekcje:  
  
-   [Aparat wyrażeń regularnych](#Engine)  
  
-   [Matchcollection — i dopasuj obiekty](#Match_and_MCollection)  
  
-   [Kolekcja grupy](#GroupCollection)  
  
-   [Przechwyconą grupę](#the_captured_group)  
  
-   [Kolekcja przechwytywania](#CaptureCollection)  
  
-   [Poszczególne przechwytywania](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Aparat wyrażeń regularnych  
 Aparat wyrażeń regularnych w programie .NET jest reprezentowany przez <xref:System.Text.RegularExpressions.Regex> klasy. Aparat wyrażeń regularnych jest odpowiedzialny za analizowaniem i kompilowaniem wyrażenia regularnego i do wykonywania operacji, które pasują do wzorca wyrażenia regularnego, ciąg wejściowy. Aparat jest składnikiem centralny model obiektów wyrażeń regularnych platformy .NET.  
  
 Umożliwia aparatowi wyrażeń regularnych w jeden z dwóch sposobów:  
  
-   Przez wywołanie metody statyczne <xref:System.Text.RegularExpressions.Regex> klasy. Parametry metody obejmują ciąg wejściowy i wzorzec wyrażenia regularnego. Aparat wyrażeń regularnych buforuje wyrażeń regularnych, które są używane w wywołaniach metody statycznej, więc wielokrotnego wywołania metody statyczne wyrażenie regularne, które używają tego samego wyrażenia regularnego oferują stosunkowo dobrej wydajności.  
  
-   Przez utworzenie wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu, przekazując wyrażeń regularnych do konstruktora klasy. W tym przypadku <xref:System.Text.RegularExpressions.Regex> obiektu jest niezmienny (tylko do odczytu) i reprezentuje aparat wyrażeń regularnych, który jest ściśle powiązany z pojedynczego wyrażenia regularnego. Ponieważ wyrażenia regularne, używany przez <xref:System.Text.RegularExpressions.Regex> wystąpienia nie są buforowane, nie należy utworzyć wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektów wiele razy z tym samym wyrażeniem regularnym.  
  
 Można wywołać metody <xref:System.Text.RegularExpressions.Regex> klasy, aby wykonywać następujące operacje:  
  
-   Określ, czy ciąg jest zgodny z wzorcem wyrażenia regularnego.  
  
-   Wyodrębnij pojedynczego dopasowania lub pierwsze dopasowanie.  
  
-   Wyodrębnij wszystkie dopasowania.  
  
-   Zastąp dopasowanego podciągu.  
  
-   Podziel pojedynczy ciąg na tablicę ciągów.  
  
 Te operacje są opisane w poniższych sekcjach.  
  
### <a name="matching-a-regular-expression-pattern"></a>Pasujące do wzorca wyrażenia regularnego  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Metoda zwraca `true` Jeśli ciąg pasuje do wzorca lub `false` Jeśli tak nie jest. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Metoda jest często używana do zweryfikowania ciąg wejściowy. Na przykład poniższy kod zapewnia zgodność ciąg prawidłowy numer ubezpieczenia społecznego w Stanach Zjednoczonych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego `^\d{3}-\d{2}-\d{4}$` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Dopasowuje początek ciągu wejściowego.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`-`|Dopasowuje łącznik.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`-`|Dopasowuje łącznik.|  
|`\d{4}`|Odpowiada czterem cyfrom po przecinku.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Trwa wyodrębnianie pojedynczego dopasowania lub pierwsze dopasowanie  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.Match> obiektu, który zawiera informacje dotyczące pierwszego podciągu, który jest zgodny ze wzorcem wyrażenia regularnego. Jeśli `Match.Success` właściwość zwraca `true`, wskazującą, czy znaleziono dopasowanie, można pobrać informacji o kolejnych dopasowań, wywołując <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody. Wywołania tych metod można kontynuować do momentu `Match.Success` właściwość zwraca `false`. Na przykład, poniższy kod używa <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody do znalezienia pierwszego wystąpienia wyrazu zduplikowane w ciągu. Następnie wywołuje <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody do znalezienia wszelkie dodatkowe wystąpienia. Przykład sprawdza, czy `Match.Success` właściwości po każdego wywołania metody, aby określić, czy bieżące dopasowanie zakończyło się pomyślnie i zezwolić wywołaniu <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody należy wykonać.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\w+)\W+(\1)\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\W+`|Dopasowuje znaki niebędące znakami słowa jeden lub więcej.|  
|`(\1)`|Pasuje do pierwszej przechwyconej ciągu. Jest to druga grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy wyrazu.|  
  
### <a name="extracting-all-matches"></a>Trwa wyodrębnianie wszystkie dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który zawiera informacje o wszystkie dopasowania, które aparat wyrażeń regularnych znalezione w ciągu wejściowym. Na przykład poprzedni przykład można dopasować do wywołania <xref:System.Text.RegularExpressions.Regex.Matches%2A> zamiast metody <xref:System.Text.RegularExpressions.Regex.Match%2A> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Zastępowanie dopasowanego podciągu  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Metoda zastępuje każdy podciągu, który pasuje do wzorca wyrażenia regularnego przy użyciu określonego ciągu lub wzorca wyrażenia regularnego i zwraca cały ciąg wejściowy o zamiany. Na przykład poniższy kod dodaje symbol waluty Stanów Zjednoczonych, zanim liczba dziesiętna w ciągu.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Definicję wzorca wyrażenia regularnego `\b\d+\.\d{2}\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\.`|Dopasowanie kropki.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zamieniania `$$$&` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Ciąg zastępujący|  
|-------------|------------------------|  
|`$$`|Znak dolara ($).|  
|`$&`|Całego dopasowanego podciągu.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dzielenie pojedynczego ciągu na tablicę ciągów  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Metoda dzieli ciąg wejściowy w pozycjach zdefiniowane przez dopasowanie wyrażenia regularnego. Na przykład poniższy kod umieszcza elementy listy numerowanej w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Definicję wzorca wyrażenia regularnego `\b\d{1,2}\.\s` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d{1,2}`|Dopasowuje co najmniej dwie cyfry dziesiętne.|  
|`\.`|Dopasowanie kropki.|  
|`\s`|Dopasowuje znak odstępu.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>Matchcollection — i dopasuj obiekty  
 Wyrażenie regularne metody zwracają dwa obiekty, które są częścią model obiektów wyrażeń regularnych: <xref:System.Text.RegularExpressions.MatchCollection> obiektu, a <xref:System.Text.RegularExpressions.Match> obiektu.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Kolekcja dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Match> obiekty reprezentujące wszystkie dopasowania, które zostały odnalezione aparat wyrażeń regularnych, w kolejności, w jakiej występują one w ciągu wejściowym. Jeśli brak dopasowań, metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiektu bez członków. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Właściwości zapewnia dostęp do poszczególnych elementów członkowskich kolekcji za pomocą indeksu, od zera do mniejszej o jeden od wartości <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> to kolekcji indeksatora (w języku C#) i właściwość domyślną (w języku Visual Basic).  
  
 Domyślnie, wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda użyje obliczanie z opóźnieniem, aby wypełnić <xref:System.Text.RegularExpressions.MatchCollection> obiektu. Dostęp do właściwości, które wymagają całkowicie wypełnione kolekcji, takie jak <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwości, mogą powodować spadek wydajności. W rezultacie firma Microsoft zaleca uzyskać dostęp do kolekcji przy użyciu <xref:System.Collections.IEnumerator> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metody. Poszczególne języki zapewniają konstrukcji, takich jak `For Each` w języku Visual Basic i `foreach` w języku C#, opakowywanie zbioru <xref:System.Collections.IEnumerator> interfejsu.  
  
 W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Text.RegularExpressions.MatchCollection> obiektu z wszystkie dopasowania w ciągu wejściowym. Przykład wylicza kolekcji, kopiuje dopasowania na tablicę ciągów i rejestruje pozycji znaku w tablicę liczb całkowitych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Dopasowanie  
 <xref:System.Text.RegularExpressions.Match> Klasa przedstawia wynik dopasowania pojedynczego wyrażenia regularnego. Możesz uzyskać dostęp <xref:System.Text.RegularExpressions.Match> obiektów na dwa sposoby:  
  
-   Pobierając je z <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody. Aby pobrać poszczególne <xref:System.Text.RegularExpressions.Match> obiektów iteracji kolekcji za pomocą `foreach` (w języku C#) lub `For Each`... `Next` (w języku Visual Basic) konstrukcja lub użyj <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwość służąca do pobierania określonej <xref:System.Text.RegularExpressions.Match> obiektu za pomocą indeksu lub według nazwy. Możesz również pobrać poszczególne <xref:System.Text.RegularExpressions.Match> obiektów z kolekcji, iteracja kolekcji za pomocą indeksu, od zera do jednego mniej, liczbę obiektów w kolekcji. Jednak ta metoda nie korzystać z opóźnieniem, ponieważ uzyskuje dostęp do <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład pobiera poszczególnych <xref:System.Text.RegularExpressions.Match> obiekty <xref:System.Text.RegularExpressions.MatchCollection> obiektu przez Iterowanie za pomocą kolekcji `foreach` lub `For Each`... `Next` konstruowania. Po prostu wyrażenia regularnego pasuje do ciągu "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody, która zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje pierwsze dopasowanie w ciągu lub część ciągu. Można określić, czy zostały znalezione dopasowanie poprzez pobranie wartości `Match.Success` właściwości. Można pobrać <xref:System.Text.RegularExpressions.Match> obiektami, które reprezentują kolejne są zgodne, wywołanie <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda wielokrotnie, dopóki `Success` właściwości zwracanego <xref:System.Text.RegularExpressions.Match> obiekt jest `false`.  
  
     W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody pasuje do ciągu "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dwie właściwości <xref:System.Text.RegularExpressions.Match> zwracanej kolekcji obiektów klasy:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera informacje, które odpowiadają przechwytywania podciągów grup we wzorcu wyrażenia regularnego.  
  
-   `Match.Captures` Właściwość zwraca <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który ma ograniczone użycie. Kolekcja jest pusta dla <xref:System.Text.RegularExpressions.Match> którego `Success` właściwość `false`. W przeciwnym razie zawiera pojedynczy <xref:System.Text.RegularExpressions.Capture> obiekt, który ma te same informacje co <xref:System.Text.RegularExpressions.Match> obiektu.  
  
 Aby uzyskać więcej informacji na temat tych obiektów, zobacz [kolekcji grupy](#GroupCollection) i [kolekcji przechwytywania](#CaptureCollection) sekcje w dalszej części tego tematu.  
  
 Dwa dodatkowe właściwości <xref:System.Text.RegularExpressions.Match> klasy zawierają informacje o zgodności. `Match.Value` Właściwość zwraca podciąg ciągu wejściowego, który pasuje do wzorca wyrażenia regularnego. `Match.Index` Właściwość zwraca liczony od zera pozycja początkowa dopasowanego ciągu do ciągu wejściowego.  
  
 <xref:System.Text.RegularExpressions.Match> Klasa ma również dwie metody dopasowania do wzorca:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Metoda znajdzie dopasowanie, po dopasowaniu reprezentowany przez bieżącą <xref:System.Text.RegularExpressions.Match> obiektu i zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje zgodnych.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda wykonuje określoną zamieniania na dopasowany ciąg i zwraca wynik.  
  
 W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody dołączana $ symbol i spacji przed każdy numer, który zawiera dwie cyfry ułamkowe.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Definicję wzorca wyrażenia regularnego `\b\d+(,\d{3})*\.\d{2}\b` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,\d{3})*`|Dopasowuje zero lub więcej wystąpień przecinek następują trzy cyfry dziesiętne.|  
|`\.`|Dopasowuje znak przecinka dziesiętnego.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zamieniania `$$ $&` wskazuje, że dopasowany podciąg powinna zostać zastąpiona przez symbol znaku dolara ($) ( `$$` wzorca), spację, a wartość dopasowania ( `$&` wzorca).  
  
 [Powrót do początku](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Kolekcja grupy  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Group> obiekty reprezentujące przechwyconych grupach w pojedyncze dopasowanie. Pierwszy <xref:System.Text.RegularExpressions.Group> obiektu w kolekcji (pod indeksem 0) reprezentuje całego dopasowania. Każdy obiekt, który następuje po reprezentuje wyniki pojedynczą grupę przechwytywania.  
  
 Możesz pobrać poszczególne <xref:System.Text.RegularExpressions.Group> obiektów w kolekcji przy użyciu <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> właściwości. Możesz pobrać nienazwanych grup według ich pozycji numer porządkowy w kolekcji i pobrać nazwane grupy według nazwy lub porządkowym. Nienazwane przechwytywania występować jako pierwszy w kolekcji i są indeksowane od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Nazwane przechwytywania są indeksowane po nienazwane przechwytywania, od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Aby ustalić, jakie numerowanej grupy są dostępne w zbiorze zwróconym dla poszczególnych wyrażeń regularnych, metoda wykonująca dopasowanie, należy wywołać wystąpienie <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metody. Aby ustalić, jakie nazwane grupy są dostępne w kolekcji, należy wywołać wystąpienie <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metody. Obie metody są szczególnie przydatne w procedury ogólnego przeznaczenia, które analizują dopasowań znalezionych przez dowolne wyrażenie regularne.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Właściwość jest indeksator kolekcji w języku C# i obiekt kolekcji domyślnej właściwości w języku Visual Basic. Oznacza to, że osoba <xref:System.Text.RegularExpressions.Group> obiekty są dostępne za pomocą indeksu (lub według nazwy, a w przypadku nazwanych grup) w następujący sposób:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, używany przez konstrukcje grupujące do przechwytywania, dzień, miesiąc i rok z daty.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{1,2})`|Dopasowuje co najmniej dwie cyfry dziesiętne. Jest to druga grupa przechwytywania.|  
|`,`|Odpowiada wartości przecinkami.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{4})`|Odpowiada czterem cyfrom po przecinku. Jest to trzecia grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy wyrazu.|  
  
 [Powrót do początku](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Przechwyconą grupę  
 <xref:System.Text.RegularExpressions.Group> Klasa przedstawia wynik z pojedynczą grupę przechwytywania. Obiekty grupy, które reprezentują grupy przechwytywania zdefiniowany w wyrażeniu regularnym są zwracane przez <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwość <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Właściwość jest indeksatora (w języku C#) i domyślną właściwość (w języku Visual Basic) <xref:System.Text.RegularExpressions.Group> klasy. Możesz również pobrać poszczególnych elementów członkowskich według Iterowanie za pomocą kolekcji `foreach` lub `For Each` konstruowania. Aby uzyskać przykład zobacz poprzednią sekcję.  
  
 W poniższym przykładzie użyto konstrukcji zagnieżdżonego grupowania do przechwytywania podciągów w grupach. Definicję wzorca wyrażenia regularnego `(a(b))c` pasuje do ciągu "abc". Przypisuje podciągu "ab" pierwszą grupę przechwytywania i podciąg "b" do drugiej grupy przechwytywania.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 W poniższym przykładzie użyto konstrukcji grupowania nazwanych do przechwytywania podciągów z ciągu, który zawiera dane w formacie "DATANAME:VALUE", który przeszedł wyrażenia regularnego dwukropek (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Definicję wzorca wyrażenia regularnego `^(?<name>\w+):(?<value>\w+)` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`(?<name>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `name`.|  
|`:`|Dopasowuje dwukropka.|  
|`(?<value>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `value`.|  
  
 Właściwości <xref:System.Text.RegularExpressions.Group> klasy zawierają informacje o przechwyconej grupy: `Group.Value` właściwość zawiera podciąg przechwycony `Group.Index` właściwość wskazuje pozycję początkową przechwyconej grupy w tekście wejściowym `Group.Length` właściwość zawiera długość przechwytywany tekst i `Group.Success` właściwość wskazuje, czy podciąg dopasowany wzorzec zdefiniowany przez grupę przechwytywania.  
  
 Stosowanie Kwantyfikatory do grupy (Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) modyfikuje relację jednego przechwytywania na przechwytywanie grupy na dwa sposoby:  
  
-   Jeśli `*` lub `*?` kwantyfikator (który określa zero lub więcej dopasowań) jest stosowany do grupy, grupa przechwytywania nie może mieć dopasowania w ciągu wejściowym. Gdy nie ma żadnego tekstu przechwyconych właściwości <xref:System.Text.RegularExpressions.Group> obiektu są ustawione, jak pokazano w poniższej tabeli.  
  
    |Właściwości grupy|Wartość|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Poniższy przykład stanowi ilustrację. We wzorcu wyrażenia regularnego `aaa(bbb)*ccc`, pierwszą grupę przechwytywania (podciąg "bbb") można dopasować zero lub więcej razy. Ponieważ ciąg wejściowy "aaaccc" pasuje do wzorca, grupa przechwytywania nie ma dopasowania.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Kwantyfikatory może odnosić się wiele wystąpień wzorzec, który jest definiowany przez grupę przechwytywania. W tym przypadku `Value` i `Length` właściwości <xref:System.Text.RegularExpressions.Group> obiekt zawiera informacje tylko o ostatni podciąg przechwycony. Na przykład poniższe wyrażenie regularne dopasowuje jednym zdaniu, która kończy się kropką. Używa dwóch konstrukcje grupujące: pierwszy przechwytuje poszczególne wyrazy wraz z biały znak; drugi przechwytuje poszczególne wyrazy. Dane wyjściowe z przykładu pokazują, mimo że wyrażenie regularne zakończy się pomyślnie w przechwytywaniu całe zdanie, druga grupa przechwytywania przechwytuje tylko ostatni wyraz.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Powrót do początku](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Kolekcja przechwytywania  
 <xref:System.Text.RegularExpressions.Group> Obiektu zawiera informacje dotyczące tylko ostatni przechwytywania. Jednak cały zestaw przechwytywań przez grupę przechwytywania jest nadal dostępne z poziomu <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości. Każdy element członkowski kolekcji jest <xref:System.Text.RegularExpressions.Capture> obiekt, który reprezentuje przechwytywania wprowadzone przez grupę przechwytywania, w kolejności, w którym zostały przechwycone (i w związku z tym, w kolejności, w którym zostały dopasowane przechwyconych ciągi od lewej do prawej w ciągu wejściowym). Możesz pobrać poszczególne <xref:System.Text.RegularExpressions.Capture> obiektów z kolekcji w jeden z dwóch sposobów:  
  
-   Według iteracji w kolekcji przy użyciu konstrukcji, takich jak `foreach` (w języku C#) lub `For Each` (w języku Visual Basic).  
  
-   Za pomocą <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> właściwość służąca do pobierania z określonym obiektem według indeksu. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Właściwość <xref:System.Text.RegularExpressions.CaptureCollection> indeksatora (w języku C#) lub domyślnej właściwości (w języku Visual Basic) obiektu.  
  
 Jeśli do grupy przechwytywania, nie jest stosowany kwantyfikator <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera pojedynczy <xref:System.Text.RegularExpressions.Capture> obiektu, który ma znaczenie nieco, ponieważ zawiera informacje o tym samym dopasowaniem jako jego <xref:System.Text.RegularExpressions.Group> obiektu. Jeśli do grupy przechwytywania, jest stosowany kwantyfikator <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera wszystkie przechwytywań przez grupę przechwytywania, a ostatni element członkowski kolekcji reprezentuje sam przechwytywania jako <xref:System.Text.RegularExpressions.Group> obiektu.  
  
 Na przykład, jeśli używasz wzorzec wyrażenia regularnego `((a(b))c)+` (gdzie + kwantyfikator Określa jedno lub więcej dopasowań) do przechwytywania jest zgodny z ciągiem "abcabcabc" <xref:System.Text.RegularExpressions.CaptureCollection> obiekt dla każdego <xref:System.Text.RegularExpressions.Group> obiekt zawiera trzy elementy członkowskie.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 W poniższym przykładzie użyto wyrażenia regularnego `(Abc)+` można znaleźć co najmniej jeden przebieg kolejnych ciągu "Abc" w ciągu "XYZAbcAbcAbcXYZAbcAb". W przykładzie pokazano użycie <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości, aby zwrócić wiele grup przechwycone podciągi.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Powrót do początku](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Poszczególne przechwytywania  
 <xref:System.Text.RegularExpressions.Capture> Klasa zawiera wyniki przechwycone Podwyrażenie jednego. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Właściwość zawiera dopasowany tekst i <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> właściwość wskazuje liczona od zera pozycja w ciągu wejściowym, od której rozpoczyna się podciągiem.  
  
 Poniższy przykład analizuje ciągu wejściowym, aby temperatura wybranych miastach. Przecinek (",") jest używany do oddzielania miejscowość i jego temperatury i średnikiem (";") jest używany do oddzielania danych każdego miasta. Cały ciąg wejściowy reprezentuje pojedyncze dopasowanie. We wzorcu wyrażenia regularnego `((\w+(\s\w+)*),(\d+);)+`, używany do analizowania, nazwę miasta jest przypisany do drugiej grupy przechwytywania i temperatura jest przypisany do czwartej grupa przechwytywania.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(\s\w+)*`|Dopasowuje zero lub więcej wystąpień znak odstępu, w którym następuje co najmniej jeden znak słowa. Ten wzorzec pasuje do nazwy miast wielu słów. Jest to trzecia grupa przechwytywania.|  
|`(\w+(\s\w+)*)`|Dopasowuje co najmniej jeden znak słowa, następuje zero lub więcej wystąpień znaku odstępu i co najmniej jeden znak słowa. Jest to druga grupa przechwytywania.|  
|`,`|Odpowiada wartości przecinkami.|  
|`(\d+)`|Dopasowuje jeden lub więcej cyfr. Jest to czwarty grupa przechwytywania.|  
|`;`|Dopasowuje średnikiem.|  
|`((\w+(\s\w+)*),(\d+);)+`|Pasuje do wzorca programu word, następuje dodatkowych słów, następuje przecinek, co najmniej jedna cyfra i średnikiem, jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.RegularExpressions>  
- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)  
- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
