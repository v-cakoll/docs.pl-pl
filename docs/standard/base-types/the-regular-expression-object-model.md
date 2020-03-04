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
ms.openlocfilehash: 8956be3cf8f96a8dd255f378d4927404c172c908
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160004"
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
 Aparat wyrażeń regularnych w programie .NET jest reprezentowany przez klasę <xref:System.Text.RegularExpressions.Regex>. Aparat wyrażeń regularnych jest odpowiedzialny za analizowanie i kompilowanie wyrażenia regularnego oraz wykonywanie operacji, które pasują do wzorca wyrażenia regularnego z ciągiem wejściowym. Aparat jest centralnym składnikiem w modelu obiektów wyrażeń regularnych programu .NET.  
  
 Aparat wyrażeń regularnych można używać na dwa sposoby:  
  
- Wywołując metody statyczne klasy <xref:System.Text.RegularExpressions.Regex>. Parametry metody obejmują ciąg wejściowy i wzorzec wyrażenia regularnego. Aparat wyrażeń regularnych buforuje wyrażenia regularne, które są używane w wywołaniach metody statycznej, więc powtórzone wywołania statycznych metod wyrażeń regularnych, które używają tego samego wyrażenia regularnego, zapewniają stosunkowo dobrą wydajność.  
  
- Utworzenie wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex>, przez przekazanie wyrażenia regularnego do konstruktora klasy. W takim przypadku obiekt <xref:System.Text.RegularExpressions.Regex> jest niezmienny (tylko do odczytu) i reprezentuje aparat wyrażeń regularnych, który jest ściśle sprzężony z pojedynczym wyrażeniem regularnym. Ponieważ wyrażenia regularne używane przez wystąpienia <xref:System.Text.RegularExpressions.Regex> nie są buforowane, nie należy wielokrotnie utworzyć wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> z tym samym wyrażeniem regularnym.  
  
 Można wywołać metody klasy <xref:System.Text.RegularExpressions.Regex>, aby wykonać następujące operacje:  
  
- Określ, czy ciąg pasuje do wzorca wyrażenia regularnego.  
  
- Wyodrębnij jedno dopasowanie lub pierwsze dopasowanie.  
  
- Wyodrębnij wszystkie dopasowania.  
  
- Zastąp pasujący podciąg.  
  
- Dzieli pojedynczy ciąg na tablicę ciągów.  
  
 Te operacje są opisane w poniższych sekcjach.  
  
### <a name="matching-a-regular-expression-pattern"></a>Dopasowanie wzorca wyrażenia regularnego  
 Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> zwraca `true`, jeśli ciąg pasuje do wzorca lub `false`, jeśli nie. Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> jest często używana do walidacji danych wejściowych ciągu. Na przykład poniższy kod zapewnia, że ciąg jest zgodny z prawidłowym numerem ubezpieczenia społecznego w Stany Zjednoczone.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 `^\d{3}-\d{2}-\d{4}$` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
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
 Metoda <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.RegularExpressions.Match>, który zawiera informacje na temat pierwszego podciągu, który pasuje do wzorca wyrażenia regularnego. Jeśli właściwość `Match.Success` zwraca `true`, co oznacza, że znaleziono dopasowanie, można pobrać informacje dotyczące kolejnych dopasowań, wywołując metodę <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>. Te wywołania metod mogą być kontynuowane do momentu, gdy `Match.Success` właściwość zwróci `false`. Na przykład poniższy kod używa metody <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>, aby znaleźć pierwsze wystąpienie zduplikowanego wyrazu w ciągu. Następnie wywołuje metodę <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>, aby znaleźć wszelkie dodatkowe wystąpienia. Przykład sprawdza Właściwość `Match.Success` po każdym wywołaniu metody, aby określić, czy bieżące dopasowanie zakończyło się powodzeniem i czy wywołanie metody <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> powinno następować po.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 `\b(\w+)\W+(\1)\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij dopasowanie na granicy słowa.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\W+`|Dopasowuje jeden lub więcej znaków niebędących wyrazami.|  
|`(\1)`|Dopasowuje pierwszy przechwycony ciąg. Jest to druga grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
### <a name="extracting-all-matches"></a>Wyodrębnianie wszystkich dopasowań  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.RegularExpressions.MatchCollection>, który zawiera informacje o wszystkich dopasowaniach, które aparat wyrażeń regularnych znalazł w ciągu wejściowym. Na przykład poprzedni przykład może zostać ponownie zapisany, aby wywołać metodę <xref:System.Text.RegularExpressions.Regex.Matches%2A> zamiast metod <xref:System.Text.RegularExpressions.Regex.Match%2A> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A>.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Zastępowanie dopasowanego podciągu  
 Metoda <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> zastępuje każdy podciąg, który jest zgodny ze wzorcem wyrażenia regularnego z określonym ciągiem lub wzorcem wyrażenia regularnego, i zwraca cały ciąg wejściowy z zamiennikami. Na przykład poniższy kod dodaje symbol waluty USA przed liczbą dziesiętną w ciągu.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 `\b\d+\.\d{2}\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\.`|Dopasowuje okres.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 `$$$&` Wzorzec zamieniania jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Ciąg zamienny|  
|-------------|------------------------|  
|`$$`|Znak dolara ($).|  
|`$&`|Cały dopasowany podciąg.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dzielenie pojedynczego ciągu na tablicę ciągów  
 Metoda <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> dzieli ciąg wejściowy w pozycjach zdefiniowanych przez dopasowanie wyrażenia regularnego. Na przykład poniższy kod umieszcza elementy w numerowanej liście do tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 `\b\d{1,2}\.\s` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d{1,2}`|Dopasowuje jedną lub dwie cyfry dziesiętne.|  
|`\.`|Dopasowuje okres.|  
|`\s`|Dopasowuje znak odstępu.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection i Match Objects  
 Metody wyrażenia regularnego zwracają dwa obiekty, które są częścią modelu obiektu wyrażenia regularnego: obiekt <xref:System.Text.RegularExpressions.MatchCollection> i <xref:System.Text.RegularExpressions.Match> obiektu.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Kolekcja dopasowania  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.RegularExpressions.MatchCollection>, który zawiera <xref:System.Text.RegularExpressions.Match> obiekty, które reprezentują wszystkie dopasowania wykryte przez aparat wyrażeń regularnych w kolejności, w jakiej występują w ciągu wejściowym. Jeśli nie ma żadnych dopasowań, metoda zwraca obiekt <xref:System.Text.RegularExpressions.MatchCollection> bez elementów członkowskich. Właściwość <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> umożliwia dostęp do poszczególnych elementów członkowskich kolekcji przez indeks, od zera do jednego mniejszego niż wartość właściwości <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType>. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> to indeksator kolekcji (w programie C#) i domyślna właściwość (w Visual Basic).  
  
 Domyślnie wywołanie metody <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> używa oceny z opóźnieniem do wypełnienia obiektu <xref:System.Text.RegularExpressions.MatchCollection>. Dostęp do właściwości, które wymagają w pełni wypełnionej kolekcji, takich jak właściwości <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType>, może spowodować spadek wydajności. W związku z tym zalecamy dostęp do kolekcji przy użyciu obiektu <xref:System.Collections.IEnumerator>, który jest zwracany przez metodę <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType>. Poszczególne języki zawierają konstrukcje, takie jak `For Each` w Visual Basic i `foreach` w C#programie, które zawijają interfejs <xref:System.Collections.IEnumerator> kolekcji.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType>, aby wypełnić obiekt <xref:System.Text.RegularExpressions.MatchCollection> ze wszystkimi dopasowań znalezionych w ciągu wejściowym. Przykład wylicza kolekcję, kopiuje dopasowania do tablicy ciągów i rejestruje pozycje znaku w tablicy liczb całkowitych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Dopasowanie  
 Klasa <xref:System.Text.RegularExpressions.Match> reprezentuje wynik pojedynczego wyrażenia regularnego dopasowania. Dostęp do <xref:System.Text.RegularExpressions.Match> obiektów można uzyskać na dwa sposoby:  
  
- Pobierając je z obiektu <xref:System.Text.RegularExpressions.MatchCollection>, który jest zwracany przez metodę <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. Aby pobrać pojedyncze obiekty <xref:System.Text.RegularExpressions.Match>, należy wykonać iterację kolekcji przy użyciu `foreach` ( C#w) lub `For Each`...`Next` (w Visual Basic) konstrukcji lub użyć właściwości <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> do pobrania określonego obiektu <xref:System.Text.RegularExpressions.Match> przez indeks lub według nazwy. Możesz również pobrać pojedyncze obiekty <xref:System.Text.RegularExpressions.Match> z kolekcji, iterjąc kolekcje według indeksu, od zera do jednego mniej, ile obiektów w kolekcji. Jednak ta metoda nie wykorzystuje oceny z opóźnieniem, ponieważ uzyskuje dostęp do właściwości <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType>.  
  
     Poniższy przykład pobiera indywidualne obiekty <xref:System.Text.RegularExpressions.Match> z obiektu <xref:System.Text.RegularExpressions.MatchCollection> przez iterację kolekcji przy użyciu `foreach` lub `For Each`...`Next` konstrukcja. Wyrażenie regularne jest po prostu zgodne z ciągiem "ABC" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Wywołując metodę <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>, która zwraca obiekt <xref:System.Text.RegularExpressions.Match>, który reprezentuje pierwsze dopasowanie w ciągu lub części ciągu. Można określić, czy dopasowanie zostało znalezione przez pobranie wartości właściwości `Match.Success`. Aby pobrać obiekty <xref:System.Text.RegularExpressions.Match>, które reprezentują kolejne dopasowania, wywołaj metodę <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> wielokrotnie, dopóki nie zostanie `false`Właściwość `Success` zwróconego obiektu <xref:System.Text.RegularExpressions.Match>.  
  
     W poniższym przykładzie zastosowano metody <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>, aby dopasować ciąg "ABC" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dwie właściwości klasy <xref:System.Text.RegularExpressions.Match> zwracają obiekty kolekcji:  
  
- Właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.RegularExpressions.GroupCollection>, który zawiera informacje o podciągach, które pasują do grup przechwytywania we wzorcu wyrażenia regularnego.  
  
- Właściwość `Match.Captures` zwraca obiekt <xref:System.Text.RegularExpressions.CaptureCollection>, który ma ograniczone użycie. Kolekcja nie jest wypełniona dla obiektu <xref:System.Text.RegularExpressions.Match>, którego właściwość `Success` jest `false`. W przeciwnym razie zawiera pojedynczy obiekt <xref:System.Text.RegularExpressions.Capture>, który ma te same informacje co obiekt <xref:System.Text.RegularExpressions.Match>.  
  
 Aby uzyskać więcej informacji na temat tych obiektów, zobacz sekcję [Kolekcja grup](#GroupCollection) i [Kolekcja przechwytywania](#CaptureCollection) w dalszej części tego tematu.  
  
 Dwie dodatkowe właściwości klasy <xref:System.Text.RegularExpressions.Match> zawierają informacje o dopasowaniu. Właściwość `Match.Value` zwraca podciąg w ciągu wejściowym, który jest zgodny ze wzorcem wyrażenia regularnego. Właściwość `Match.Index` zwraca pozycję początkową z uwzględnieniem zera w ciągu wejściowym.  
  
 Klasa <xref:System.Text.RegularExpressions.Match> ma również dwie metody dopasowania do wzorca:  
  
- Metoda <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> znajduje dopasowanie po dopasowaniu przedstawionym przez bieżący obiekt <xref:System.Text.RegularExpressions.Match> i zwraca obiekt <xref:System.Text.RegularExpressions.Match> reprezentujący to dopasowanie.  
  
- Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wykonuje określoną operację zamiany dla dopasowanego ciągu i zwraca wynik.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>, aby poprzedź symbol $ i spację przed każdą liczbą, która zawiera dwie cyfry ułamkowe.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 `\b\d+(,\d{3})*\.\d{2}\b` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,\d{3})*`|Dopasowuje zero lub więcej wystąpień przecinka, po których następują trzy cyfry dziesiętne.|  
|`\.`|Dopasowuje znak dziesiętny.|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec zamieniania `$$ $&` wskazuje, że dopasowany podciąg powinien zostać zastąpiony symbolem znaku dolara ($) (wzorzec `$$`), spacją i wartością dopasowania (wzorzec `$&`).  
  
 [Powrót do początku](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Kolekcja grup  
 Właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Text.RegularExpressions.GroupCollection>, który zawiera <xref:System.Text.RegularExpressions.Group> obiekty reprezentujące przechwycone grupy w jednym dopasowaniu. Pierwszy obiekt <xref:System.Text.RegularExpressions.Group> w kolekcji (pod indeksem 0) reprezentuje cały odpowiednik. Każdy obiekt, który następuje, reprezentuje wyniki pojedynczej grupy przechwytywania.  
  
 Można pobrać pojedyncze obiekty <xref:System.Text.RegularExpressions.Group> w kolekcji przy użyciu właściwości <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType>. Grupy nienazwanych można pobrać według ich pozycji porządkowej w kolekcji i pobrać nazwane grupy według nazwy lub pozycji porządkowej. Przechwycenia nienazwane są wyświetlane jako pierwsze w kolekcji i są indeksowane od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Nazwane przechwycenia są indeksowane po nienazwanym przechwytywaniu, od lewej do prawej w kolejności, w jakiej są wyświetlane we wzorcu wyrażenia regularnego. Aby określić, które grupy numerowane są dostępne w kolekcji zwróconej dla konkretnej metody zgodnej z wyrażeniem regularnym, można wywołać metodę <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> wystąpienia. Aby określić, które nazwane grupy są dostępne w kolekcji, można wywołać metodę <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> wystąpienia. Obie metody są szczególnie przydatne w procedurach ogólnego przeznaczenia, które analizują dopasowania znalezione przez dowolne wyrażenie regularne.  
  
 Właściwość <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> jest indeksator kolekcji w C# i właściwość domyślna obiektu kolekcja w Visual Basic. Oznacza to, że do poszczególnych obiektów <xref:System.Text.RegularExpressions.Group> można uzyskać dostęp za pomocą indeksu (lub według nazwy, w przypadku nazwanych grup) w następujący sposób:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które korzysta z konstrukcji grupujących, aby przechwycić miesiąc, dzień i rok daty.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
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
 Klasa <xref:System.Text.RegularExpressions.Group> reprezentuje wynik z pojedynczej grupy przechwytywania. Obiekty grupy reprezentujące grupy przechwytywania zdefiniowane w wyrażeniu regularnym są zwracane przez właściwość <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> obiektu <xref:System.Text.RegularExpressions.GroupCollection> zwróconego przez właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. Właściwość <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> jest indeksatorem (in C#) i właściwością domyślną (w Visual Basic) klasy <xref:System.Text.RegularExpressions.Group>. Możesz również pobrać poszczególnych członków, wykonując iterację kolekcji przy użyciu konstrukcji `foreach` lub `For Each`. Aby zapoznać się z przykładem, zobacz poprzednią sekcję.  
  
 Poniższy przykład używa zagnieżdżonych konstrukcji grupowania do przechwytywania podciągów do grup. Wzorzec wyrażenia regularnego `(a(b))c` pasuje do ciągu "ABC". Przypisuje podciąg "AB" pierwszej grupie przechwytywania, a podciąg "b" drugiej grupie przechwytywania.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 W poniższym przykładzie używane są nazwane konstrukcje grupowania do przechwytywania podciągów z ciągu, który zawiera dane w formacie "DATAname: VALUE", które wyrażenie regularne dzieli na dwukropek (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 `^(?<name>\w+):(?<value>\w+)` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`(?<name>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `name`.|  
|`:`|Dopasowuje dwukropek.|  
|`(?<value>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania jest `value`.|  
  
 Właściwości klasy <xref:System.Text.RegularExpressions.Group> zawierają informacje o przechwyconej grupie: Właściwość `Group.Value` zawiera przechwycony podciąg, właściwość `Group.Index` wskazuje pozycję początkową przechwyconej grupy w tekście wejściowym, właściwość `Group.Length` zawiera długość przechwyconego tekstu, a właściwość `Group.Success` wskazuje, czy podciąg jest zgodny ze wzorcem zdefiniowanym przez grupę przechwytywania.  
  
 Stosowanie kwantyfikatorów do grupy (Aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) modyfikują relację jednego przechwytywania na grupę przechwytywania na dwa sposoby:  
  
- Jeśli do grupy zastosowano kwantyfikator `*` lub `*?` (które określa zero lub więcej dopasowań), grupa przechwytywania może nie mieć dopasowania w ciągu wejściowym. Gdy nie ma przechwyconego tekstu, właściwości obiektu <xref:System.Text.RegularExpressions.Group> są ustawiane, jak pokazano w poniższej tabeli.  
  
    |Group — Właściwość|Wartość|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Poniższy przykład stanowi ilustrację. We wzorcu wyrażenia regularnego `aaa(bbb)*ccc`pierwszą grupą przechwytywania (podciąg "BBB") można dopasować zero lub więcej razy. Ponieważ ciąg wejściowy "aaaccc" pasuje do wzorca, grupa przechwytywania nie ma dopasowania.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Kwantyfikatory mogą odpowiadać wielu wystąpieniu wzorca, który jest zdefiniowany przez grupę przechwytywania. W takim przypadku właściwości `Value` i `Length` obiektu <xref:System.Text.RegularExpressions.Group> zawierają informacje dotyczące ostatniego przechwyconego podciągu. Na przykład następujące wyrażenie regularne dopasowuje pojedyncze zdanie kończące się kropką. Używa dwóch konstrukcji grupowania: pierwszy przechwytuje poszczególne słowa wraz ze znakiem odstępu; drugi przechwytuje pojedyncze słowa. Jak widać dane wyjściowe z przykładu, chociaż wyrażenie regularne pomyślnie przechwytuje całe zdanie, druga grupa przechwytywania przechwytuje tylko ostatni wyraz.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Powrót do początku](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Kolekcja przechwytywania  
 Obiekt <xref:System.Text.RegularExpressions.Group> zawiera informacje dotyczące ostatniego przechwycenia. Jednak cały zestaw przechwytywania wykonany przez grupę przechwytywania nadal jest dostępny z obiektu <xref:System.Text.RegularExpressions.CaptureCollection>, który jest zwracany przez właściwość <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>. Każdy element członkowski kolekcji jest obiektem <xref:System.Text.RegularExpressions.Capture>, który reprezentuje przechwytywanie wykonane przez tę grupę przechwytywania, w kolejności, w której zostały przechwycone (i w związku z tym w kolejności, w której przechwycone ciągi zostały dopasowane od lewej do prawej w ciągu wejściowym). Poszczególne obiekty <xref:System.Text.RegularExpressions.Capture> można pobrać z kolekcji na jeden z dwóch sposobów:  
  
- Przez iterację kolekcji przy użyciu konstrukcji, takiej jak `foreach` (in C#) lub `For Each` (w Visual Basic).  
  
- Za pomocą właściwości <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> do pobrania określonego obiektu według indeksu. Właściwość <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> jest właściwością domyślną obiektu <xref:System.Text.RegularExpressions.CaptureCollection> (w Visual Basic) lub indeksatorem (w programie C#).  
  
 Jeśli kwantyfikator nie zostanie zastosowany do grupy przechwytywania, obiekt <xref:System.Text.RegularExpressions.CaptureCollection> zawiera pojedynczy obiekt <xref:System.Text.RegularExpressions.Capture>, który jest mało interesujący, ponieważ zawiera informacje na temat tego samego dopasowania jak jego obiekt <xref:System.Text.RegularExpressions.Group>. Jeśli kwantyfikator jest stosowany do grupy przechwytywania, obiekt <xref:System.Text.RegularExpressions.CaptureCollection> zawiera wszystkie przechwycenia wykonane przez grupę przechwytywania, a ostatni element członkowski kolekcji reprezentuje takie samo przechwytywanie, jak obiekt <xref:System.Text.RegularExpressions.Group>.  
  
 Na przykład, jeśli używasz wzorca wyrażenia regularnego `((a(b))c)+` (gdzie + kwantyfikator określa jeden lub więcej dopasowań) do przechwytywania dopasowań z ciągu "abcabcabc", obiekt <xref:System.Text.RegularExpressions.CaptureCollection> dla każdego obiektu <xref:System.Text.RegularExpressions.Group> zawiera trzech członków.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Poniższy przykład używa wyrażenia regularnego `(Abc)+`, aby znaleźć jeden lub kilka kolejnych uruchomień ciągu "ABC" w ciągu "XYZAbcAbcAbcXYZAbcAb". Przykład ilustruje użycie właściwości <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>, aby zwrócić wiele grup przechwyconych podciągów.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Powrót do początku](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Pojedyncze przechwycenie  
 Klasa <xref:System.Text.RegularExpressions.Capture> zawiera wyniki przechwycenia pojedynczego podwyrażenia. Właściwość <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> zawiera dopasowany tekst, a właściwość <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> wskazuje pozycję od zera w ciągu wejściowym, w którym rozpoczyna się dopasowany podciąg.  
  
 Poniższy przykład analizuje ciąg wejściowy dla temperatury wybranych miast. Przecinek (",") jest używany do oddzielenia miejscowości i jej temperatury, a średnik (";") jest używany do oddzielania danych poszczególnych miast. Cały ciąg wejściowy reprezentuje pojedyncze dopasowanie. We wzorcu wyrażenia regularnego `((\w+(\s\w+)*),(\d+);)+`, który jest używany do analizowania ciągu, nazwa miasta jest przypisywana do drugiej grupy przechwytywania, a temperatura jest przypisana do czwartej grupy przechwytywania.  
  
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
- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
