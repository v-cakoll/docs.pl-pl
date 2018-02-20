---
title: "Model obiektów wyrażeń regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8917ce764d615282f95aad2eee494fcc0ba7a847
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="the-regular-expression-object-model"></a>Model obiektów wyrażeń regularnych
<a name="introduction"></a> W tym temacie opisano model obiektów używane w pracy w wyrażeniach regularnych programu .NET. Ten temat zawiera następujące sekcje:  
  
-   [Aparat wyrażeń regularnych](#Engine)  
  
-   [Matchcollection — i obiektów dopasowania](#Match_and_MCollection)  
  
-   [Kolekcja grup](#GroupCollection)  
  
-   [Przechwyconej grupy](#the_captured_group)  
  
-   [Kolekcja przechwytywania](#CaptureCollection)  
  
-   [Poszczególne przechwytywania](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Aparat wyrażeń regularnych  
 Aparat wyrażeń regularnych programu .NET jest reprezentowana przez <xref:System.Text.RegularExpressions.Regex> klasy. Aparat wyrażeń regularnych jest odpowiedzialny za analizowanie i kompilowanie wyrażenia regularnego i do wykonywania operacji, które jest zgodny z wzorcem wyrażenia regularnego z ciągu wejściowego. Aparat jest składnikiem centralnej w modelu obiektów wyrażeń regularnych programu .NET.  
  
 Aparat wyrażeń regularnych można użyć w jeden z dwóch sposobów:  
  
-   Przez wywołanie metody statycznej <xref:System.Text.RegularExpressions.Regex> klasy. Parametry metody zawierają ciąg wejściowy i wzorzec wyrażenia regularnego. Aparat wyrażeń regularnych buforuje wyrażeń regularnych, używanych w wywołaniach metody statycznej, powtarzane wywołania metody statycznej wyrażenia regularnego, które używają tego samego wyrażenia regularnego oferują stosunkowo dobrą wydajność.  
  
-   Przy uruchamianiu <xref:System.Text.RegularExpressions.Regex> obiektu, przekazując wyrażenia regularnego do konstruktora klasy. W takim przypadku <xref:System.Text.RegularExpressions.Regex> obiektu nie można modyfikować (tylko do odczytu) i reprezentuje aparat wyrażeń regularnych, który jest ściśle powiązana z pojedynczego wyrażenia regularnego. Ponieważ użyć wyrażeń regularnych przez <xref:System.Text.RegularExpressions.Regex> wystąpień nie są buforowane, nie należy utworzyć wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu wiele razy przy użyciu tego samego wyrażenia regularnego.  
  
 Można wywołać metody <xref:System.Text.RegularExpressions.Regex> klasy do wykonania następujących czynności:  
  
-   Określ, czy ciąg ze wzorcem wyrażenia regularnego.  
  
-   Wyodrębnij jedną pasującą lub pierwszego dopasowania.  
  
-   Wyodrębnij wszystkie dopasowania.  
  
-   Zastępuje podciąg.  
  
-   Podziel pojedynczy ciąg na tablicę ciągów.  
  
 W poniższych sekcjach opisano te operacje.  
  
### <a name="matching-a-regular-expression-pattern"></a>Dopasowanie wzorca wyrażeń regularnych  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Metoda zwraca `true` Jeśli ciąg zgodny z wzorcem lub `false` jeśli jej nie ma. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Metody często używany do weryfikowania ciąg na wejściu. Na przykład poniższy kod zapewnia zgodność ciąg prawidłowy numer ubezpieczenia społecznego w USA.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^\d{3}-\d{2}-\d{4}$` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Odpowiada na początku ciąg wejściowy.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`-`|Zgodne łącznika.|  
|`\d{2}`|Zgodne dwóch cyfr dziesiętnych.|  
|`-`|Zgodne łącznika.|  
|`\d{4}`|Zgodne czterech cyfr dziesiętnych.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Wyodrębnianie jedną pasującą lub pierwszego dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.Match> obiektu, który zawiera informacje dotyczące pierwszego podciągu zgodnego ze wzorcem wyrażenia regularnego. Jeśli `Match.Success` zwraca `true`, wskazujący, że Znaleziono dopasowanie, można pobrać informacji o kolejnych dopasowań przez wywołanie metody <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody. Te wywołania metody można kontynuować do momentu `Match.Success` zwraca właściwość `false`. Na przykład poniższy kod używa <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody do znalezienia pierwszego wystąpienia zduplikowanych słowa w ciągu. Następnie wywołuje <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody do znalezienia wszelkie dodatkowe wystąpienia. Przykład sprawdza `Match.Success` właściwości po każdej wywołania metody, aby określić, czy bieżące dopasowanie zakończyło się pomyślnie i czy wywołanie <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody należy wykonać.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\W+(\1)\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij dopasowania na granicy programu word.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\W+`|Zgodne z co najmniej jeden znak-word.|  
|`(\1)`|Odpowiada pierwszy ciąg przechwycony. Jest to druga grupa przechwytywania.|  
|`\b`|W celu dopasowania na granicy programu word.|  
  
### <a name="extracting-all-matches"></a>Wyodrębnianie wszystkie dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który zawiera informacje o wszystkich dopasowań, które aparat wyrażeń regularnych odnalezione w ciągu wejściowym. Na przykład poprzedniego przykładu można ulegną wywołać <xref:System.Text.RegularExpressions.Regex.Matches%2A> zamiast metody <xref:System.Text.RegularExpressions.Regex.Match%2A> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Zastępuje podciąg  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Metoda zastępuje każdego podciągu, który jest zgodny ze wzorcem wyrażenia regularnego z określony ciąg lub wzorzec wyrażenia regularnego i zwraca cały ciąg wejściowy z zamiany. Na przykład następujący kod dodaje symbol waluty USA przed liczbą dziesiętną w ciągu.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Wzorzec wyrażenia regularnego `\b\d+\.\d{2}\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\.`|Odpowiada danym okresie.|  
|`\d{2}`|Zgodne dwóch cyfr dziesiętnych.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zastępczy `$$$&` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Ciąg zastępczy|  
|-------------|------------------------|  
|`$$`|Znak dolara ($).|  
|`$&`|Cały podciąg.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dzielenie na pojedynczy ciąg na tablicę ciągów  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Metody dzieli ciąg wejściowy w pozycji zdefiniowane przez dopasowanie wyrażenia regularnego. Na przykład następujący kod umieszcza elementy w Lista numerowana w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Wzorzec wyrażenia regularnego `\b\d{1,2}\.\s` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d{1,2}`|Odpowiada jednej lub dwóch miejsc dziesiętnych.|  
|`\.`|Odpowiada danym okresie.|  
|`\s`|Dopasowuje znak odstępu.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>Matchcollection — i obiektów dopasowania  
 Metody regex zwracać dwa obiekty, które są częścią model obiektów wyrażeń regularnych: <xref:System.Text.RegularExpressions.MatchCollection> obiektu, a <xref:System.Text.RegularExpressions.Match> obiektu.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Kolekcja dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Match> obiektów, które reprezentują dopasowań, które można odnaleźć aparat wyrażeń regularnych w kolejności ich występowania w ciągu wejściowym. Jeśli nie mają odpowiedników, metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiektu bez członków. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Właściwości umożliwia dostęp do poszczególnych członków kolekcji przez indeks, zero do jeden mniejsza niż wartość <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> to kolekcji indeksatora (w języku C#) i właściwości domyślnej (w języku Visual Basic).  
  
 Domyślnie wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda używa obliczanie leniwe do wypełnienia <xref:System.Text.RegularExpressions.MatchCollection> obiektu. Dostęp do właściwości, które wymagają całkowicie wypełnione kolekcji, takie jak <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwości, może pociągać za sobą zmniejszenie wydajności. W związku z tym zaleca się uzyskać dostępu do kolekcji przy użyciu <xref:System.Collections.IEnumerator> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metody. Poszczególne języki Podaj konstrukcje, taki jak `For``Each` w języku Visual Basic i `foreach` w języku C#, który zawijać kolekcji <xref:System.Collections.IEnumerator> interfejsu.  
  
 W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Text.RegularExpressions.MatchCollection> obiektu ze wszystkich dopasowań w parametrach wejściowych. Przykład wylicza kolekcji, kopiuje dopasowania do tablicy ciągów i rejestruje pozycji znaku w tablicy liczby całkowitej.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Dopasowania  
 <xref:System.Text.RegularExpressions.Match> Klasa przedstawia wynik dopasowania pojedynczego wyrażenia regularnego. Dostęp można uzyskać <xref:System.Text.RegularExpressions.Match> obiektów na dwa sposoby:  
  
-   Pobierając je z <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody. Aby pobrać poszczególnych <xref:System.Text.RegularExpressions.Match> obiektów, iteracji kolekcji za pomocą `foreach` (w języku C#) lub `For Each`... `Next` (w języku Visual Basic) konstrukcja lub użyj <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwości do pobrania określonego <xref:System.Text.RegularExpressions.Match> obiektu przez indeks lub według nazwy. Można również pobrać poszczególnych <xref:System.Text.RegularExpressions.Match> obiektów z kolekcji przez iteracja kolekcji przez indeks, z zero do jeden mniej który liczbę obiektów w kolekcji. Jednak ta metoda nie korzystać z opóźnieniem oceny, ponieważ uzyskuje dostęp do <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład pobiera poszczególnych <xref:System.Text.RegularExpressions.Match> obiektów z <xref:System.Text.RegularExpressions.MatchCollection> obiektu Iterowanie za pomocą kolekcji `foreach` lub `For Each`... `Next` utworzenia. Wyrażenie regularne po prostu pasującej do ciągu "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Wywołując <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody, która zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje pierwszego dopasowania w ciągu lub część ciągu. Można określić, czy zostały znalezione dopasowanie pobierając zaletą `Match.Success` właściwości. Można pobrać <xref:System.Text.RegularExpressions.Match> obiektów, które reprezentują kolejne są zgodne, wywołanie <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> — metoda wielokrotnie, dopóki `Success` właściwości zwracana <xref:System.Text.RegularExpressions.Match> obiekt jest `false`.  
  
     W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody do dopasowania ciągu "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dwie właściwości <xref:System.Text.RegularExpressions.Match> zwracany kolekcji obiektów klasy:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera informacje o podciągów zgodnych Przechwytywanie grupy w wzorzec wyrażenia regularnego.  
  
-   `Match.Captures` Zwraca <xref:System.Text.RegularExpressions.CaptureCollection> obiekt, który jest ograniczone użycie. Kolekcja jest pusta dla <xref:System.Text.RegularExpressions.Match> którego `Success` jest właściwość `false`. W przeciwnym razie wartość zawiera jedną <xref:System.Text.RegularExpressions.Capture> obiektu, który ma te same informacje co <xref:System.Text.RegularExpressions.Match> obiektu.  
  
 Aby uzyskać więcej informacji na temat tych obiektów, zobacz [Collection grupy](#GroupCollection) i [Collection przechwytywania](#CaptureCollection) sekcje w dalszej części tego tematu.  
  
 Dwa dodatkowe właściwości <xref:System.Text.RegularExpressions.Match> klasy zawierają informacje o zgodności. `Match.Value` Właściwość zwraca podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego. `Match.Index` Właściwość zwraca liczony od zera pozycja początkowa dopasowane ciągu w ciągu wejściowym.  
  
 <xref:System.Text.RegularExpressions.Match> Klasa ma również dwie metody dopasowywanie do wzorca:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Metoda znajdzie dopasowania po dopasowania reprezentowany przez bieżący <xref:System.Text.RegularExpressions.Match> obiektu i zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje zgodne.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda wykonuje operację zamiany określonego dopasowany ciąg i zwraca wynik.  
  
 W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę dołączy $ symbol i odstęp przed każdym liczba, która zawiera dwa cyfr ułamkowych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Wzorzec wyrażenia regularnego `\b\d+(,\d{3})*\.\d{2}\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,\d{3})*`|Zgodne zero lub więcej wystąpień to przecinek trzech cyfr dziesiętnych.|  
|`\.`|Dopasowanie znaku dziesiętnego.|  
|`\d{2}`|Zgodne dwóch cyfr dziesiętnych.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zastępczy `$$ $&` wskazuje, że podciąg powinna zostać zastąpiona symbol dolara ($) ( `$$` wzorzec), spacji i wartość dopasowania ( `$&` wzorzec).  
  
 [Powrót do początku](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Kolekcja grup  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Group> obiekty reprezentujące grup przechwyconych w jednym dopasowania. Pierwszy <xref:System.Text.RegularExpressions.Group> obiektu w kolekcji (pod indeksem 0) reprezentuje cały dopasowania. Każdy obiekt, który następuje reprezentuje wyniki pojedynczej grupy przechwytywania.  
  
 Możesz pobrać poszczególnych <xref:System.Text.RegularExpressions.Group> obiektów z kolekcji przy użyciu <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> właściwości. Można pobrać bez nazwy grupy według ich pozycji porządkowej w kolekcji i pobrać nazwanych grup według nazwy lub porządkowym. Nienazwane przechwytywania występować jako pierwszy w kolekcji i są indeksowane od lewej do prawej w kolejności, w jakiej występują w wzorzec wyrażenia regularnego. Nazwane przechwytywane są indeksowane po nienazwane przechwytywanie, od lewej do prawej w kolejności, w jakiej występują w wzorzec wyrażenia regularnego. Aby ustalić, jakie grupy numerowanych są dostępne w kolekcji zwrócony dla określonego wyrażenia regularnego dopasowanie — metoda, należy wywołać wystąpienie <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metody. Aby ustalić, jakie grupy o nazwie są dostępne w kolekcji, należy wywołać wystąpienie <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metody. Obie metody są szczególnie przydatne w procedur ogólnego przeznaczenia, które analizowanie dopasowań przez dowolne wyrażenie regularne.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Właściwość jest indeksatora kolekcji w języku C# i obiektu kolekcji domyślnej właściwości w języku Visual Basic. Oznacza to, że osoba <xref:System.Text.RegularExpressions.Group> obiektów można uzyskać dostęp przez indeks (lub według nazwy, w przypadku nazwanych grup) w następujący sposób:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, używaną do przechwytywania dzień, miesiąc i rok z daty w konstrukcji grupowania.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{1,2})`|Odpowiada jednej lub dwóch miejsc dziesiętnych. Jest to druga grupa przechwytywania.|  
|`,`|Zgodne przecinkami.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{4})`|Zgodne czterech cyfr dziesiętnych. Jest to trzecia grupa przechwytywania.|  
|`\b`|W celu dopasowania na granicy programu word.|  
  
 [Powrót do początku](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Przechwyconej grupy  
 <xref:System.Text.RegularExpressions.Group> Klasa reprezentuje wynik z pojedynczej grupy przechwytywania. Obiekty grupy, które reprezentują przechwytywania grup zdefiniowanych w wyrażeniu regularnym są zwracane przez <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwość <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Jest właściwość, indeksator (w języku C#) i domyślną właściwość (w języku Visual Basic) <xref:System.Text.RegularExpressions.Group> klasy. Można również pobrać poszczególne elementy Iterowanie za pomocą kolekcji `foreach` lub `For``Each` utworzenia. Na przykład zobacz poprzedniej sekcji.  
  
 W poniższym przykładzie użyto konstrukcji zagnieżdżone grupowanie do przechwytywania podciągów w grupach. Wzorzec wyrażenia regularnego `(a(b))c` pasującej do ciągu "abc". Przypisuje podciągu "ab" pierwszej grupy przechwytywania i podciąg "b" do drugiej grupy przechwytywania.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 W poniższym przykładzie użyto konstrukcji grupowania nazwanego przechwytywania podciągów z ciąg, który zawiera dane w formacie "DATANAME:VALUE", który przeszedł wyrażenia regularnego dwukropka (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Wzorzec wyrażenia regularnego `^(?<name>\w+):(?<value>\w+)` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`(?<name>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `name`.|  
|`:`|Zgodny z dwukropkiem.|  
|`(?<value>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `value`.|  
  
 Właściwości <xref:System.Text.RegularExpressions.Group> klasy zawierają informacje o grupie przechwycony: `Group.Value` właściwość zawiera podciąg przechwyconych `Group.Index` właściwość wskazuje pozycję początkową przechwyconej grupy w tekstu wejściowego `Group.Length` właściwość zawiera długość tekstu przechwycony i `Group.Success` właściwość wskazuje, czy podciągu dopasować wzorzec zdefiniowanym przez grupę przechwytywania.  
  
 Stosowanie Kwantyfikatory do grupy (Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) modyfikuje relacji jeden przechwytywania na przechwytywanie grupy na dwa sposoby:  
  
-   Jeśli `*` lub `*?` kwantyfikator (który określa zero lub więcej dopasowań) jest stosowane do grupy, grupa przechwytywania może nie mają odpowiednika w ciągu wejściowym. Jeśli nie ma żadnego tekstu przechwyconych właściwości <xref:System.Text.RegularExpressions.Group> obiektu są ustawione, jak pokazano w poniższej tabeli.  
  
    |Właściwości grupy|Wartość|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Poniższy przykład stanowi ilustrację. We wzorcu wyrażenia regularnego `aaa(bbb)*ccc`, pierwsza grupa przechwytywania (podciągu "bbb") można dopasować zero lub więcej razy. Ponieważ ciąg wejściowy "aaaccc" zgodny z wzorcem, przechwytywania grupa nie ma dopasowania.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Kwantyfikatory może dopasować wiele wystąpień wzorca, który jest zdefiniowany przez grupę przechwytywania. W takim przypadku `Value` i `Length` właściwości <xref:System.Text.RegularExpressions.Group> obiekt zawiera tylko informacje dotyczące ostatnich podciąg przechwycony. Na przykład poniższe wyrażenie regularne dopasowuje pojedynczego zdanie, które kończą się kropką. Używa dwóch konstrukcji grupowania: pierwszy przechwytuje poszczególnych wyrazów wraz z biały znak; drugi przechwytuje poszczególnych wyrazów. Jak dane wyjściowe w przykładzie pokazano, mimo że wyrażenie regularne pomyślnie Przechwytywanie całe zdanie, drugiej grupy przechwytywania przechwytuje ostatniego wyrazu.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Powrót do początku](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Kolekcja przechwytywania  
 <xref:System.Text.RegularExpressions.Group> Obiekt zawiera tylko informacje dotyczące ostatnich przechwytywania. Jednak jest nadal dostępne z całego zestawu przechwytywane przez grupę przechwyconą <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości. Każdy element członkowski kolekcji <xref:System.Text.RegularExpressions.Capture> obiekt, który reprezentuje przechwytywania wprowadzone przez tę grupę przechwytywania, w kolejności ich przechwytywania (i w związku z tym w kolejności, w którym przechwyconych ciągi były zgodne od lewej do prawej w ciągu wejściowym). Możesz pobrać poszczególnych <xref:System.Text.RegularExpressions.Capture> obiektów z kolekcji w jeden z dwóch sposobów:  
  
-   Przez iteracji w kolekcji, takie jak przy użyciu konstrukcję `foreach` (w języku C#) lub `For``Each` (w języku Visual Basic).  
  
-   Za pomocą <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> właściwości do pobrania określonego obiektu przez indeks. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Jest właściwość <xref:System.Text.RegularExpressions.CaptureCollection> obiektu domyślnej właściwości (w języku Visual Basic) lub indeksator (w języku C#).  
  
 Jeśli kwantyfikator nie została zastosowana do grupy przechwytywania <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera jeden <xref:System.Text.RegularExpressions.Capture> obiekt, który jest zebranych, ponieważ zawiera informacje o tym samym dopasowania jako jego <xref:System.Text.RegularExpressions.Group> obiektu. Jeśli kwantyfikator jest stosowane do grupy przechwytywania, <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera wszystkie przechwytywane przez grupę przechwytywania i tego samego przechwytywania jako reprezentuje ostatni element członkowski kolekcji <xref:System.Text.RegularExpressions.Group> obiektu.  
  
 Na przykład, jeśli używasz wzorzec wyrażenia regularnego `((a(b))c)+` (gdzie + kwantyfikatora określa jeden lub więcej dopasowań) do przechwytywania jest zgodna z ciągu "abcabcabc" <xref:System.Text.RegularExpressions.CaptureCollection> obiekt dla każdego <xref:System.Text.RegularExpressions.Group> obiektu zawiera trzy elementy członkowskie.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 W poniższym przykładzie użyto wyrażenia regularnego `(Abc)+` można znaleźć co najmniej jeden przebieg kolejnych ciągu "Abc" w ciągu "XYZAbcAbcAbcXYZAbcAb". Przykład przedstawia użycie <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości, aby powrócić do wielu grup przechwycone podciągów.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Powrót do początku](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Poszczególne przechwytywania  
 <xref:System.Text.RegularExpressions.Capture> Klasa zawiera wyników przechwytywania pojedynczego wyrażenia podrzędnego. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Właściwość zawiera dopasowany tekst i <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> właściwość wskazuje liczona od zera pozycja w ciągu wejściowym, od której rozpoczyna się podciąg.  
  
 Poniższy przykład analizuje wejściowy ciąg dla temperatury wybranych miast. Przecinka (",") jest używany do rozdzielania miejscowości i jego temperatury i średnikiem (";") jest używany do rozdzielania każdemu miastu danych. Cały ciąg wejściowy reprezentuje pojedynczy dopasowania. We wzorcu wyrażenia regularnego `((\w+(\s\w+)*),(\d+);)+`, które są wykorzystywane do analizy ciągu nazwę miejscowości jest przypisany do drugiej grupy przechwytywania i temperatura jest przypisany do czwartej grupy przechwytywania.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Wyrażenie regularne jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(\s\w+)*`|Zgodne zero lub więcej wystąpień biały znak, następuje co najmniej jeden znak słowa. Ten wzorzec jest zgodny nazwy word wiele miast. Jest to trzecia grupa przechwytywania.|  
|`(\w+(\s\w+)*)`|Zgodne z co najmniej jeden znak word następuje biały znak zero lub więcej wystąpień i co najmniej jeden znak programu word. Jest to druga grupa przechwytywania.|  
|`,`|Zgodne przecinkami.|  
|`(\d+)`|Zgodne z co najmniej jedną cyfrę. Jest to czwarty grupa przechwytywania.|  
|`;`|Zgodne średnikiem.|  
|`((\w+(\s\w+)*),(\d+);)+`|Jest zgodna z wzorcem wyraz następuje wszelkie dodatkowe słowa następuje przecinek, co najmniej jedną cyfrę i średnika, jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.RegularExpressions>  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
