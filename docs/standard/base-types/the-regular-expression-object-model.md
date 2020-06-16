---
title: Model obiektów wyrażeń regularnych
description: Przejrzyj model obiektów wyrażeń regularnych w programie .NET. Pracuj z aparatem wyrażeń regularnych, & obiektów & kolekcje związane z dopasowywaniem, grupowaniem i & przechwytywaniem.
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
ms.openlocfilehash: 43672b85ecb64a15179881ec23c7fadd13d64868
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768056"
---
# <a name="the-regular-expression-object-model"></a>Model obiektów wyrażeń regularnych
<a name="introduction"></a>W tym temacie opisano model obiektów używany w pracy z wyrażeniami regularnymi programu .NET. Ten temat zawiera następujące sekcje:  
  
- [Aparat wyrażeń regularnych](#Engine)  
  
- [MatchCollection i Match Objects](#Match_and_MCollection)  
  
- [Kolekcja grup](#GroupCollection)  
  
- [Przechwycona Grupa](#the_captured_group)  
  
- [Kolekcja przechwytywania](#CaptureCollection)  
  
- [Pojedyncze przechwycenie](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Aparat wyrażeń regularnych  
 Aparat wyrażeń regularnych w programie .NET jest reprezentowany przez <xref:System.Text.RegularExpressions.Regex> klasę. Aparat wyrażeń regularnych jest odpowiedzialny za analizowanie i kompilowanie wyrażenia regularnego oraz wykonywanie operacji, które pasują do wzorca wyrażenia regularnego z ciągiem wejściowym. Aparat jest centralnym składnikiem w modelu obiektów wyrażeń regularnych programu .NET.  
  
 Aparat wyrażeń regularnych można używać na dwa sposoby:  
  
- Wywoływanie metod statycznych <xref:System.Text.RegularExpressions.Regex> klasy. Parametry metody obejmują ciąg wejściowy i wzorzec wyrażenia regularnego. Aparat wyrażeń regularnych buforuje wyrażenia regularne, które są używane w wywołaniach metody statycznej, więc powtórzone wywołania statycznych metod wyrażeń regularnych, które używają tego samego wyrażenia regularnego, zapewniają stosunkowo dobrą wydajność.  
  
- Utworzenie wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu przez przekazanie wyrażenia regularnego do konstruktora klasy. W tym przypadku <xref:System.Text.RegularExpressions.Regex> obiekt jest niezmienny (tylko do odczytu) i reprezentuje aparat wyrażeń regularnych, który jest ściśle sprzężony z pojedynczym wyrażeniem regularnym. Ponieważ wyrażenia regularne używane przez <xref:System.Text.RegularExpressions.Regex> wystąpienia nie są buforowane, nie należy wielokrotnie tworzyć wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu za pomocą tego samego wyrażenia regularnego.  
  
 Można wywołać metody <xref:System.Text.RegularExpressions.Regex> klasy, aby wykonać następujące operacje:  
  
- Określ, czy ciąg pasuje do wzorca wyrażenia regularnego.  
  
- Wyodrębnij jedno dopasowanie lub pierwsze dopasowanie.  
  
- Wyodrębnij wszystkie dopasowania.  
  
- Zastąp pasujący podciąg.  
  
- Dzieli pojedynczy ciąg na tablicę ciągów.  
  
 Te operacje są opisane w poniższych sekcjach.  
  
### <a name="matching-a-regular-expression-pattern"></a>Dopasowanie wzorca wyrażenia regularnego  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>Metoda zwraca `true` , czy ciąg pasuje do wzorca, czy nie `false` . <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>Metoda jest często używana do walidacji danych wejściowych ciągu. Na przykład poniższy kod zapewnia, że ciąg jest zgodny z prawidłowym numerem ubezpieczenia społecznego w Stany Zjednoczone.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Wzorzec wyrażenia regularnego `^\d{3}-\d{2}-\d{4}$` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Dopasowuje początek ciągu wejściowego.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`-`|Dopasowuje łącznik.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`-`|Dopasowuje łącznik.|  
|`\d{4}`|Dopasowuje cztery cyfry dziesiętne.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Wyodrębnianie pojedynczego dopasowania lub pierwszego dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>Metoda zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje na temat pierwszego podciągu, który pasuje do wzorca wyrażenia regularnego. Jeśli `Match.Success` Właściwość zwraca `true` , wskazując, że znaleziono dopasowanie, można pobrać informacje o kolejnych dopasowaniach, wywołując <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę. Te wywołania metod mogą być kontynuowane do momentu, gdy `Match.Success` właściwość zwróci wartość `false` . Na przykład poniższy kod używa <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody, aby znaleźć pierwsze wystąpienie zduplikowanego wyrazu w ciągu. Następnie wywołuje <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę w celu znalezienia wszelkich dodatkowych wystąpień. Przykład sprawdza `Match.Success` Właściwość po wywołaniu każdej metody, aby określić, czy bieżące dopasowanie zakończyło się powodzeniem i czy wywołanie <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody powinno następować po.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\W+(\1)\b` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij dopasowanie na granicy słowa.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\W+`|Dopasowuje jeden lub więcej znaków niebędących wyrazami.|  
|`(\1)`|Dopasowuje pierwszy przechwycony ciąg. Jest to druga grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
### <a name="extracting-all-matches"></a>Wyodrębnianie wszystkich dopasowań  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera informacje o wszystkich dopasowaniach, które aparat wyrażeń regularnych znalazł w ciągu wejściowym. Na przykład poprzedni przykład może zostać ponownie zapisany w celu wywołania <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody zamiast <xref:System.Text.RegularExpressions.Regex.Match%2A> <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metod i.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Zastępowanie dopasowanego podciągu  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>Metoda zastępuje każdy podciąg, który jest zgodny ze wzorcem wyrażenia regularnego z określonym ciągiem lub wzorcem wyrażenia regularnego, i zwraca cały ciąg wejściowy z zamiennikami. Na przykład poniższy kod dodaje symbol waluty USA przed liczbą dziesiętną w ciągu.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Wzorzec wyrażenia regularnego `\b\d+\.\d{2}\b` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\.`|Dopasowuje okres.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zamieniania `$$$&` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Ciąg zamienny|  
|-------------|------------------------|  
|`$$`|Znak dolara ($).|  
|`$&`|Cały dopasowany podciąg.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dzielenie pojedynczego ciągu na tablicę ciągów  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>Metoda dzieli ciąg wejściowy w pozycjach zdefiniowanych przez wyrażenie regularne dopasowywania. Na przykład poniższy kod umieszcza elementy w numerowanej liście do tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Wzorzec wyrażenia regularnego `\b\d{1,2}\.\s` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d{1,2}`|Dopasowuje jedną lub dwie cyfry dziesiętne.|  
|`\.`|Dopasowuje okres.|  
|`\s`|Dopasowuje znak odstępu.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection i Match Objects  
 Metody wyrażeń regularnych zwracają dwa obiekty, które są częścią modelu obiektów wyrażeń regularnych: <xref:System.Text.RegularExpressions.MatchCollection> obiekt i <xref:System.Text.RegularExpressions.Match> obiekt.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Kolekcja dopasowania  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Match> obiekty, które reprezentują wszystkie dopasowania wykryte przez aparat wyrażeń regularnych w kolejności, w jakiej występują w ciągu wejściowym. Jeśli nie ma żadnych dopasowań, metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt bez elementów członkowskich. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType>Właściwość umożliwia dostęp do poszczególnych elementów członkowskich kolekcji przez indeks, od zera do jednego mniejszego od wartości <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>jest indeksatorem kolekcji (w języku C#) i właściwością domyślną (w Visual Basic).  
  
 Domyślnie wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody używa oceny z opóźnieniem do wypełnienia <xref:System.Text.RegularExpressions.MatchCollection> obiektu. Dostęp do właściwości, które wymagają w pełni wypełnionej kolekcji, takiej <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> jak <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwości i, mogą spowodować spadek wydajności. W związku z tym zalecamy dostęp do kolekcji przy użyciu <xref:System.Collections.IEnumerator> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metodę. Poszczególne języki udostępniają konstrukcje, takie jak `For Each` w Visual Basic i `foreach` w języku C#, które zawijają <xref:System.Collections.IEnumerator> interfejs kolekcji.  
  
 W poniższym przykładzie zastosowano <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Text.RegularExpressions.MatchCollection> obiekt wszystkimi dopasowań znalezionych w ciągu wejściowym. Przykład wylicza kolekcję, kopiuje dopasowania do tablicy ciągów i rejestruje pozycje znaku w tablicy liczb całkowitych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Dopasowanie  
 <xref:System.Text.RegularExpressions.Match>Klasa reprezentuje wynik pojedynczego wyrażenia regularnego dopasowywania. Dostęp do obiektów można uzyskać <xref:System.Text.RegularExpressions.Match> na dwa sposoby:  
  
- Pobierając je z <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metodę. Aby pobrać pojedyncze <xref:System.Text.RegularExpressions.Match> obiekty, należy wykonać iterację kolekcji przy użyciu funkcji `foreach` (w języku C#) lub `For Each` ... `Next` (w Visual Basic) lub użyć <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> właściwości w celu pobrania określonego <xref:System.Text.RegularExpressions.Match> obiektu według indeksu lub według nazwy. Możesz również pobrać pojedyncze <xref:System.Text.RegularExpressions.Match> obiekty z kolekcji, przenosząc kolekcje według indeksu, od zera do jednego mniejszego niż liczba obiektów w kolekcji. Jednakże ta metoda nie wykorzystuje oceny z opóźnieniem, ponieważ uzyskuje dostęp do <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład pobiera pojedyncze <xref:System.Text.RegularExpressions.Match> obiekty z <xref:System.Text.RegularExpressions.MatchCollection> obiektu przez iterację kolekcji przy użyciu `foreach` `For Each` konstrukcji lub... `Next` . Wyrażenie regularne jest po prostu zgodne z ciągiem "ABC" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Wywołanie <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody, która zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje pierwsze dopasowanie w ciągu lub części ciągu. Można określić, czy dopasowanie zostało znalezione przez pobranie wartości `Match.Success` właściwości. Aby pobrać <xref:System.Text.RegularExpressions.Match> obiekty, które reprezentują kolejne dopasowania, wywołaj <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę wielokrotnie, dopóki `Success` Właściwość zwracanego <xref:System.Text.RegularExpressions.Match> obiektu nie jest `false` .  
  
     W poniższym przykładzie zastosowano <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody i, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Aby dopasować ciąg "ABC" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dwie właściwości <xref:System.Text.RegularExpressions.Match> klasy zwracanych obiektów kolekcji:  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera informacje o podciągach, które pasują do grup przechwytywania we wzorcu wyrażenia regularnego.  
  
- `Match.Captures`Właściwość zwraca <xref:System.Text.RegularExpressions.CaptureCollection> obiekt mający ograniczone użycie. Kolekcja nie jest wypełniona dla <xref:System.Text.RegularExpressions.Match> obiektu, którego `Success` Właściwość ma wartość `false` . W przeciwnym razie zawiera pojedynczy <xref:System.Text.RegularExpressions.Capture> obiekt, który ma te same informacje co <xref:System.Text.RegularExpressions.Match> obiekt.  
  
 Aby uzyskać więcej informacji na temat tych obiektów, zobacz sekcję [Kolekcja grup](#GroupCollection) i [Kolekcja przechwytywania](#CaptureCollection) w dalszej części tego tematu.  
  
 Dwie dodatkowe właściwości <xref:System.Text.RegularExpressions.Match> klasy zawierają informacje o dopasowaniu. `Match.Value`Właściwość zwraca podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego. `Match.Index`Właściwość zwraca pozycję początkową z uwzględnieniem zera w ciągu wejściowym.  
  
 <xref:System.Text.RegularExpressions.Match>Klasa ma również dwie metody dopasowania do wzorca:  
  
- <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>Metoda znajduje dopasowanie po dopasowaniu przedstawionym przez bieżący <xref:System.Text.RegularExpressions.Match> obiekt i zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje ten odpowiednik.  
  
- <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda wykonuje określoną operację zamiany dla dopasowanego ciągu i zwraca wynik.  
  
 W poniższym przykładzie zastosowano <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodę, aby połączyć symbol $ i spację przed każdą liczbą, która zawiera dwie cyfry ułamkowe.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Wzorzec wyrażenia regularnego `\b\d+(,\d{3})*\.\d{2}\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,\d{3})*`|Dopasowuje zero lub więcej wystąpień przecinka, po których następują trzy cyfry dziesiętne.|  
|`\.`|Dopasowuje znak dziesiętny.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zamieniania `$$ $&` wskazuje, że dopasowany podciąg powinien zostać zastąpiony symbolem znaku dolara ($) ( `$$` wzorzec), spacją i wartością dopasowania ( `$&` wzorzec).  
  
 [Powrót do początku](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Kolekcja grup  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera <xref:System.Text.RegularExpressions.Group> obiekty reprezentujące przechwycone grupy w jednym dopasowaniu. Pierwszy <xref:System.Text.RegularExpressions.Group> obiekt w kolekcji (pod indeksem 0) reprezentuje cały odpowiednik. Każdy obiekt, który następuje, reprezentuje wyniki pojedynczej grupy przechwytywania.  
  
 Poszczególne <xref:System.Text.RegularExpressions.Group> obiekty w kolekcji można pobrać przy użyciu <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> właściwości. Grupy nienazwanych można pobrać według ich pozycji porządkowej w kolekcji i pobrać nazwane grupy według nazwy lub pozycji porządkowej. Przechwycenia nienazwane są wyświetlane jako pierwsze w kolekcji i są indeksowane od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Nazwane przechwycenia są indeksowane po nienazwanym przechwytywaniu, od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Aby określić, które grupy numerowane są dostępne w kolekcji zwróconej dla konkretnej metody zgodnej z wyrażeniem regularnym, można wywołać <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metodę wystąpienia. Aby określić, które nazwane grupy są dostępne w kolekcji, można wywołać <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metodę wystąpienia. Obie metody są szczególnie przydatne w procedurach ogólnego przeznaczenia, które analizują dopasowania znalezione przez dowolne wyrażenie regularne.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType>Właściwość jest indeksator kolekcji w języku C# i właściwość Default obiektu Collection w Visual Basic. Oznacza to, że <xref:System.Text.RegularExpressions.Group> można uzyskać dostęp do poszczególnych obiektów według indeksu (lub według nazwy, w przypadku nazwanych grup) w następujący sposób:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które korzysta z konstrukcji grupujących, aby przechwycić miesiąc, dzień i rok daty.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{1,2})`|Dopasowuje jedną lub dwie cyfry dziesiętne. Jest to druga grupa przechwytywania.|  
|`,`|Dopasowuje przecinek.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{4})`|Dopasowuje cztery cyfry dziesiętne. Jest to trzecia grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
 [Powrót do początku](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Przechwycona Grupa  
 <xref:System.Text.RegularExpressions.Group>Klasa reprezentuje wynik z pojedynczej grupy przechwytywania. Obiekty grupy reprezentujące grupy przechwytywania zdefiniowane w wyrażeniu regularnym są zwracane przez <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Właściwość <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A>Właściwość jest indeksatorem (w języku C#) i właściwością domyślną (w Visual Basic) <xref:System.Text.RegularExpressions.Group> klasy. Możesz również pobrać poszczególnych członków, iterjąc kolekcję przy użyciu `foreach` konstrukcji lub `For Each` . Aby zapoznać się z przykładem, zobacz poprzednią sekcję.  
  
 Poniższy przykład używa zagnieżdżonych konstrukcji grupowania do przechwytywania podciągów do grup. Wzorzec wyrażenia regularnego `(a(b))c` pasuje do ciągu "ABC". Przypisuje podciąg "AB" pierwszej grupie przechwytywania, a podciąg "b" drugiej grupie przechwytywania.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 W poniższym przykładzie używane są nazwane konstrukcje grupowania do przechwytywania podciągów z ciągu, który zawiera dane w formacie "DATAname: VALUE", które wyrażenie regularne dzieli na dwukropek (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Wzorzec wyrażenia regularnego `^(?<name>\w+):(?<value>\w+)` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`(?<name>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania to `name` .|  
|`:`|Dopasowuje dwukropek.|  
|`(?<value>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania to `value` .|  
  
 Właściwości <xref:System.Text.RegularExpressions.Group> klasy zawierają informacje o przechwyconej grupie: `Group.Value` Właściwość zawiera przechwycony podciąg, `Group.Index` Właściwość wskazuje pozycję początkową przechwyconej grupy w tekście wejściowym, `Group.Length` Właściwość zawiera długość przechwyconego tekstu, a `Group.Success` Właściwość wskazuje, czy podciąg pasuje do wzorca zdefiniowanego przez grupę przechwytywania.  
  
 Stosowanie kwantyfikatorów do grupy (Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](quantifiers-in-regular-expressions.md)) modyfikują relację jednego przechwytywania na grupę przechwytywania na dwa sposoby:  
  
- Jeśli `*` `*?` do grupy jest stosowany kwantyfikator lub (który określa zero lub więcej dopasowań), grupa przechwytywania może nie mieć dopasowania w ciągu wejściowym. Gdy nie ma przechwyconego tekstu, właściwości <xref:System.Text.RegularExpressions.Group> obiektu są ustawiane, jak pokazano w poniższej tabeli.  
  
    |Group — Właściwość|Wartość|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Poniższy przykład stanowi ilustrację. We wzorcu wyrażenia regularnego `aaa(bbb)*ccc` Pierwsza grupa przechwytywania (podciąg "BBB") może być dopasowana zero lub więcej razy. Ponieważ ciąg wejściowy "aaaccc" pasuje do wzorca, grupa przechwytywania nie ma dopasowania.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Kwantyfikatory mogą odpowiadać wielu wystąpieniu wzorca, który jest zdefiniowany przez grupę przechwytywania. W takim przypadku `Value` `Length` właściwości i <xref:System.Text.RegularExpressions.Group> obiektu zawierają informacje tylko na temat ostatniego przechwyconego podciągu. Na przykład następujące wyrażenie regularne dopasowuje pojedyncze zdanie kończące się kropką. Używa dwóch konstrukcji grupowania: pierwszy przechwytuje poszczególne słowa wraz ze znakiem odstępu; drugi przechwytuje pojedyncze słowa. Jak widać dane wyjściowe z przykładu, chociaż wyrażenie regularne pomyślnie przechwytuje całe zdanie, druga grupa przechwytywania przechwytuje tylko ostatni wyraz.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Powrót do początku](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Kolekcja przechwytywania  
 <xref:System.Text.RegularExpressions.Group>Obiekt zawiera informacje dotyczące ostatniego przechwytywania. Jednak cały zestaw przechwytywania wykonany przez grupę przechwytywania nadal jest dostępny z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Właściwość. Każdy element członkowski kolekcji jest <xref:System.Text.RegularExpressions.Capture> obiektem, który reprezentuje przechwytywanie wykonane przez tę grupę przechwytywania w kolejności, w której zostały przechwycone (i w związku z tym w kolejności, w której przechwycone ciągi zostały dopasowane od lewej do prawej w ciągu wejściowym). Poszczególne obiekty można pobrać <xref:System.Text.RegularExpressions.Capture> z kolekcji na jeden z dwóch sposobów:  
  
- Przez iterację kolekcji przy użyciu konstrukcji takiej jak `foreach` (w języku C#) lub `For Each` (w Visual Basic).  
  
- Za pomocą <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> właściwości do pobierania określonego obiektu według indeksu. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A>Właściwość jest <xref:System.Text.RegularExpressions.CaptureCollection> właściwością domyślną obiektu (w Visual Basic) lub indeksatorem (w języku C#).  
  
 Jeśli kwantyfikator nie zostanie zastosowany do grupy przechwytywania, <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera pojedynczy <xref:System.Text.RegularExpressions.Capture> obiekt, który ma niewielki odsetek, ponieważ zawiera informacje na temat tego samego dopasowania jak jego <xref:System.Text.RegularExpressions.Group> obiekt. Jeśli kwantyfikator zostanie zastosowany do grupy przechwytywania, <xref:System.Text.RegularExpressions.CaptureCollection> obiekt zawiera wszystkie przechwycenia wykonane przez grupę przechwytywania, a ostatni element członkowski kolekcji reprezentuje takie samo przechwycenie jak <xref:System.Text.RegularExpressions.Group> obiekt.  
  
 Na przykład jeśli używasz wzorca wyrażenia regularnego `((a(b))c)+` (gdzie + kwantyfikator określa jeden lub więcej dopasowań) do przechwytywania dopasowań z ciągu "abcabcabc", <xref:System.Text.RegularExpressions.CaptureCollection> obiekt dla każdego <xref:System.Text.RegularExpressions.Group> obiektu zawiera trzech członków.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 W poniższym przykładzie używa się wyrażenia regularnego `(Abc)+` w celu znalezienia jednego lub kilku kolejnych uruchomień ciągu "ABC" w ciągu "XYZAbcAbcAbcXYZAbcAb". Przykład ilustruje użycie <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości, aby zwrócić wiele grup przechwyconych podciągów.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Powrót do początku](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Pojedyncze przechwycenie  
 <xref:System.Text.RegularExpressions.Capture>Klasa zawiera wyniki przechwycenia pojedynczego podwyrażenia. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>Właściwość zawiera dopasowany tekst, a <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> Właściwość wskazuje pozycję od zera w ciągu wejściowym, w którym rozpoczyna się dopasowany podciąg.  
  
 Poniższy przykład analizuje ciąg wejściowy dla temperatury wybranych miast. Przecinek (",") jest używany do oddzielenia miejscowości i jej temperatury, a średnik (";") jest używany do oddzielania danych poszczególnych miast. Cały ciąg wejściowy reprezentuje pojedyncze dopasowanie. We wzorcu wyrażenia regularnego `((\w+(\s\w+)*),(\d+);)+` , który jest używany do analizowania ciągu, nazwa miasta jest przypisywana do drugiej grupy przechwytywania, a temperatura jest przypisana do czwartej grupy przechwytywania.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(\s\w+)*`|Dopasowuje zero lub więcej wystąpień znaku odstępu, po którym następuje jeden lub więcej znaków wyrazu. Ten wzorzec pasuje do nazw miast wielowyrazowych. Jest to trzecia grupa przechwytywania.|  
|`(\w+(\s\w+)*)`|Dopasowuje co najmniej jeden znak słowa, po którym następuje zero lub więcej wystąpień znaku odstępu i jednego lub więcej znaków wyrazu. Jest to druga grupa przechwytywania.|  
|`,`|Dopasowuje przecinek.|  
|`(\d+)`|Dopasowuje co najmniej jedną cyfrę. Jest to czwarta grupa przechwytywania.|  
|`;`|Dopasowuje średnika.|  
|`((\w+(\s\w+)*),(\d+);)+`|Dopasowuje wzorzec wyrazu, po którym następuje wszelkie dodatkowe słowa, po których następuje przecinek, jedna lub więcej cyfr i średnik, jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Text.RegularExpressions>
- [Wyrażenia regularne .NET](regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
