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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160004"
---
# <a name="the-regular-expression-object-model"></a>Model obiektów wyrażeń regularnych
<a name="introduction"></a>W tym temacie opisano model obiektu używany do pracy z wyrażeniami regularnymi .NET. Ten temat zawiera następujące sekcje:  
  
- [Aparat wyrażeń regularnych](#Engine)  
  
- [MatchCollection i dopasowywanie obiektów](#Match_and_MCollection)  
  
- [Kolekcja grupowa](#GroupCollection)  
  
- [Przechwycona grupa](#the_captured_group)  
  
- [Kolekcja przechwytywania](#CaptureCollection)  
  
- [Indywidualne przechwytywanie](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Aparat wyrażeń regularnych  
 Aparat wyrażeń regularnych w .NET jest reprezentowany przez <xref:System.Text.RegularExpressions.Regex> klasę. Aparat wyrażeń regularnych jest odpowiedzialny za analizowanie i kompilowanie wyrażenia regularnego oraz wykonywanie operacji, które pasują do wzorca wyrażenia regularnego z ciągiem wejściowym. Aparat jest centralnym składnikiem modelu obiektu wyrażenia regularnego .NET.  
  
 Aparatwyrawa regularnego można używać na dwa sposoby:  
  
- Wywołując metody statyczne <xref:System.Text.RegularExpressions.Regex> klasy. Parametry metody obejmują ciąg wejściowy i wzorzec wyrażenia regularnego. Aparat wyrażeń regularnych buforuje wyrażenia regularne, które są używane w wywołaniach metod statycznych, więc powtarzające się wywołania statycznych metod wyrażenia regularnego, które używają tego samego wyrażenia regularnego oferują stosunkowo dobrą wydajność.  
  
- Przez tworzenie wystąpienia <xref:System.Text.RegularExpressions.Regex> obiektu, przekazując wyrażenie regularne do konstruktora klasy. W takim przypadku <xref:System.Text.RegularExpressions.Regex> obiekt jest niezmienny (tylko do odczytu) i reprezentuje aparat wyrażeń regularnych, który jest ściśle sprzężona z jednym wyrażeniem regularnym. Ponieważ wyrażenia regularne <xref:System.Text.RegularExpressions.Regex> używane przez wystąpienia nie są buforowane, nie <xref:System.Text.RegularExpressions.Regex> należy utworzyć wystąpienia obiektu wiele razy z tym samym wyrażeniem regularnym.  
  
 Można wywołać metody klasy, <xref:System.Text.RegularExpressions.Regex> aby wykonać następujące operacje:  
  
- Określ, czy ciąg pasuje do wzorca wyrażenia regularnego.  
  
- Wyodrębnij pojedynczy mecz lub pierwsze dopasowanie.  
  
- Wyodrębnij wszystkie dopasowania.  
  
- Zamień dopasowany podciąg.  
  
- Podziel pojedynczy ciąg na tablicę ciągów.  
  
 Te operacje są opisane w poniższych sekcjach.  
  
### <a name="matching-a-regular-expression-pattern"></a>Dopasowywanie wzorca wyrażenia regularnego  
 Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> zwraca, `true` jeśli ciąg pasuje `false` do wzorca lub jeśli nie. Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> jest często używana do sprawdzania poprawności wprowadzania ciągu. Na przykład poniższy kod zapewnia, że ciąg pasuje do prawidłowego numeru ubezpieczenia społecznego w Stanach Zjednoczonych.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Wzorzec `^\d{3}-\d{2}-\d{4}$` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Dopasuj początek ciągu wejściowego.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`-`|Dopasuj łącznik.|  
|`\d{2}`|Dopasuj dwie cyfry dziesiętne.|  
|`-`|Dopasuj łącznik.|  
|`\d{4}`|Dopasuj cztery cyfry dziesiętne.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Wyodrębnianie pojedynczego dopasowania lub pierwszego dopasowania  
 Metoda <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje o pierwszym podciągu, który pasuje do wzorca wyrażenia regularnego. Jeśli `Match.Success` właściwość `true`zwraca , wskazując, że dopasowanie zostało znalezione, można pobrać <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> informacje o kolejnych dopasowań, wywołując metodę. Te wywołania metody `Match.Success` można `false`kontynuować, dopóki właściwość nie powróci . Na przykład poniższy kod <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> używa metody, aby znaleźć pierwsze wystąpienie zduplikowanego wyrazu w ciągu. Następnie wywołuje <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę, aby znaleźć wszelkie dodatkowe wystąpienia. W przykładzie sprawdza `Match.Success` właściwość po każdym wywołaniu metody, aby ustalić, czy <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> bieżące dopasowanie zakończyło się pomyślnie i czy należy wykonać wywołanie metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Wzorzec `\b(\w+)\W+(\1)\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpocznij dopasowanie na granicy słowa.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\W+`|Dopasuj jeden lub więcej znaków innych niż word.|  
|`(\1)`|Dopasuj pierwszy przechwycony ciąg. Jest to druga grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
### <a name="extracting-all-matches"></a>Wyodrębnianie wszystkich dopasowań  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera informacje o wszystkich dopasowań, które aparat wyrażeń regularnych znaleźć w ciągu wejściowym. Na przykład poprzedni przykład może zostać przepisany, aby <xref:System.Text.RegularExpressions.Regex.Match%2A> <xref:System.Text.RegularExpressions.Match.NextMatch%2A> wywołać <xref:System.Text.RegularExpressions.Regex.Matches%2A> metodę zamiast i metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Zastępowanie dopasowanego podciągu  
 Metoda <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> zastępuje każdy podciąg, który pasuje do wzorca wyrażenia regularnego z określonym ciągiem lub wzorcem wyrażenia regularnego i zwraca cały ciąg wejściowy z zamiennikami. Na przykład poniższy kod dodaje symbol waluty usa przed liczbą dziesiętną w ciągu.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Wzorzec `\b\d+\.\d{2}\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\.`|Dopasuj kropkę.|  
|`\d{2}`|Dopasuj dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec `$$$&` zastępczy jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Ciąg zastępczy|  
|-------------|------------------------|  
|`$$`|Znak dolara ($).|  
|`$&`|Cały dopasowany podciąg.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dzielenie pojedynczego ciągu na tablicę ciągów  
 Metoda <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> dzieli ciąg wejściowy w pozycjach zdefiniowanych przez dopasowanie wyrażenia regularnego. Na przykład poniższy kod umieszcza elementy na liście numerowanej w tablicy ciągów.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Wzorzec `\b\d{1,2}\.\s` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d{1,2}`|Dopasuj jedną lub dwie cyfry dziesiętne.|  
|`\.`|Dopasuj kropkę.|  
|`\s`|Dopasowuje znak odstępu.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection i dopasowywanie obiektów  
 Metody Regex zwracają dwa obiekty, które są częścią <xref:System.Text.RegularExpressions.MatchCollection> modelu obiektu <xref:System.Text.RegularExpressions.Match> wyrażenia regularnego: obiekt i obiekt.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Kolekcja Match  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, <xref:System.Text.RegularExpressions.Match> który zawiera obiekty, które reprezentują wszystkie dopasowania, które znaleziono aparat wyrażeń regularnych, w kolejności, w jakiej występują w ciągu wejściowym. Jeśli nie ma żadnych dopasowań, metoda zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt bez elementów członkowskich. Właściwość <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> umożliwia dostęp do poszczególnych elementów członkowskich kolekcji przez indeks, od <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> zera do jednego mniej niż wartość właściwości. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>jest indeksatorem kolekcji (w języku C#) i właściwością domyślną (w języku Visual Basic).  
  
 Domyślnie wywołanie <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody używa oceny z opóźnieniem do wypełniania <xref:System.Text.RegularExpressions.MatchCollection> obiektu. Dostęp do właściwości, które wymagają w pełni <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> wypełnione <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> kolekcji, takich jak i właściwości, może obejmować kary wydajności. W związku z tym zaleca się dostęp <xref:System.Collections.IEnumerator> do kolekcji przy użyciu <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> obiektu, który jest zwracany przez metodę. Poszczególne języki zapewniają konstrukcje, takie jak `For Each` w języku Visual Basic i `foreach` C#, które zawijają <xref:System.Collections.IEnumerator> interfejs kolekcji.  
  
 W poniższym <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> przykładzie użyto <xref:System.Text.RegularExpressions.MatchCollection> metody do wypełniania obiektu ze wszystkimi dopasowaniami znalezionymi w ciągu wejściowym. W przykładzie wylicza kolekcji, kopiuje dopasowań do tablicy ciągów i rejestruje pozycje znaków w tablicy całkowitej.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Mecz  
 Klasa <xref:System.Text.RegularExpressions.Match> reprezentuje wynik dopasowania pojedynczego wyrażenia regularnego. Dostęp do <xref:System.Text.RegularExpressions.Match> obiektów można uzyskać na dwa sposoby:  
  
- Pobierając je z <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> zwracany przez metodę. Aby pobrać <xref:System.Text.RegularExpressions.Match> poszczególne obiekty, iterate `foreach` kolekcji przy użyciu `For Each`(w języku C#) lub ... `Next` (w języku Visual Basic) <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> konstruować lub <xref:System.Text.RegularExpressions.Match> użyć właściwości, aby pobrać określony obiekt przez indeks lub według nazwy. Można również pobrać <xref:System.Text.RegularExpressions.Match> poszczególnych obiektów z kolekcji przez iteracji kolekcji według indeksu, od zera do jednego mniej niż liczba obiektów w kolekcji. Jednak ta metoda nie korzysta z oceny z opóźnieniem, ponieważ uzyskuje dostęp do <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład pobiera <xref:System.Text.RegularExpressions.Match> poszczególnych <xref:System.Text.RegularExpressions.MatchCollection> obiektów z obiektu przez iteracji kolekcji przy użyciu `foreach` lub `For Each`... `Next` konstrukcji. Wyrażenie regularne po prostu pasuje do ciągu "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Wywołując <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metodę, która zwraca <xref:System.Text.RegularExpressions.Match> obiekt, który reprezentuje pierwsze dopasowanie w ciągu lub część ciągu. Można określić, czy dopasowanie zostało znalezione przez pobranie wartości `Match.Success` właściwości. Aby <xref:System.Text.RegularExpressions.Match> pobrać obiekty, które reprezentują <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> kolejne dopasowania, `Success` wywołać metodę <xref:System.Text.RegularExpressions.Match> wielokrotnie, `false`dopóki właściwość zwróconego obiektu jest .  
  
     W poniższym <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> przykładzie <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> użyto i metody, aby dopasować ciąg "abc" w ciągu wejściowym.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dwie właściwości obiektów <xref:System.Text.RegularExpressions.Match> kolekcji zwracanej przez klasę:  
  
- Właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, który zawiera informacje o podciągi, które pasują do grup przechwytywania we wzorcu wyrażenia regularnego.  
  
- Właściwość `Match.Captures` zwraca <xref:System.Text.RegularExpressions.CaptureCollection> obiekt, który jest ograniczone użycie. Kolekcja nie jest wypełniana <xref:System.Text.RegularExpressions.Match> dla `Success` obiektu, którego właściwość jest `false`. W przeciwnym razie <xref:System.Text.RegularExpressions.Capture> zawiera pojedynczy obiekt, który <xref:System.Text.RegularExpressions.Match> ma te same informacje co obiekt.  
  
 Aby uzyskać więcej informacji na temat tych obiektów, zobacz [Group Collection](#GroupCollection) i [Kolekcji przechwytywania](#CaptureCollection) sekcje w dalszej części tego tematu.  
  
 Dwie dodatkowe właściwości <xref:System.Text.RegularExpressions.Match> klasy zawierają informacje o meczu. Właściwość `Match.Value` zwraca podciąg w ciągu wejściowym, który pasuje do wzorca wyrażenia regularnego. Właściwość `Match.Index` zwraca pozycję początkową od zera dopasowanego ciągu w ciągu wejściowym.  
  
 Klasa <xref:System.Text.RegularExpressions.Match> ma również dwie metody dopasowywania wzorców:  
  
- Metoda <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> znajduje dopasowanie po meczu reprezentowane przez <xref:System.Text.RegularExpressions.Match> bieżący obiekt <xref:System.Text.RegularExpressions.Match> i zwraca obiekt, który reprezentuje, że dopasowanie.  
  
- Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wykonuje określoną operację zastępowania na dopasowanym ciągu i zwraca wynik.  
  
 W poniższym <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> przykładzie użyto metody do przyłączania symbolu $ i spacji przed każdą liczbą zawierającą dwie cyfry ułamkowe.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Wzorzec `\b\d+(,\d{3})*\.\d{2}\b` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`(,\d{3})*`|Dopasuj zero lub więcej wystąpień przecinka, po którym następują trzy cyfry dziesiętne.|  
|`\.`|Dopasuj znak przecinka dziesiętnego.|  
|`\d{2}`|Dopasuj dwie cyfry dziesiętne.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Wzorzec `$$ $&` zastępczy wskazuje, że dopasowany podciąg powinien zostać `$$` zastąpiony symbolem znaku dolara ($) (wzorzec), spacjai i wartością dopasowania `$&` (wzorzec).  
  
 [Powrót do początku](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Kolekcja grupowa  
 Właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> zwraca <xref:System.Text.RegularExpressions.GroupCollection> obiekt, <xref:System.Text.RegularExpressions.Group> który zawiera obiekty, które reprezentują przechwycone grupy w jednym dopasowaniu. Pierwszy <xref:System.Text.RegularExpressions.Group> obiekt w kolekcji (w indeksie 0) reprezentuje całe dopasowanie. Każdy obiekt, który następuje reprezentuje wyniki pojedynczej grupy przechwytywania.  
  
 Można pobrać <xref:System.Text.RegularExpressions.Group> poszczególnych obiektów w <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> kolekcji przy użyciu właściwości. Można pobrać nienazwane grupy według ich pozycji ordinal w kolekcji i pobrać nazwane grupy według nazwy lub pozycji liczba mięsionka. Nienazwane przechwytywania są wyświetlane jako pierwsze w kolekcji i są indeksowane od lewej do prawej w kolejności, w jakiej pojawiają się we wzorcu wyrażenia regularnego. Nazwane przechwytywania są indeksowane po nienazwanych przechwytywaniach, od lewej do prawej w kolejności, w jakiej pojawiają się we wzorcu wyrażenia regularnego. Aby określić, jakie grupy numerowane są dostępne w kolekcji zwróconej dla określonej <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metody dopasowywania wyrażeń regularnych, można wywołać metodę wystąpienia. Aby określić, jakie nazwane grupy są dostępne w <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> kolekcji, można wywołać metodę wystąpienia. Obie metody są szczególnie przydatne w procedurach ogólnego przeznaczenia, które analizują dopasowania znalezione przez dowolne wyrażenie regularne.  
  
 Właściwość <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> jest indeksatorem kolekcji w języku C# i właściwości domyślnej obiektu kolekcji w języku Visual Basic. Oznacza to, <xref:System.Text.RegularExpressions.Group> że poszczególne obiekty mogą być dostępne za pomocą indeksu (lub według nazwy, w przypadku nazwanych grup) w następujący sposób:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które używa konstrukcji grupowania do przechwytywania miesiąca, dnia i roku daty.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Wzorzec `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{1,2})`|Dopasuj jedną lub dwie cyfry dziesiętne. Jest to druga grupa przechwytywania.|  
|`,`|Dopasuj przecinek.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\d{4})`|Dopasuj cztery cyfry dziesiętne. Jest to trzecia grupa przechwytywania.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
 [Powrót do początku](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Przechwycona grupa  
 Klasa <xref:System.Text.RegularExpressions.Group> reprezentuje wynik z pojedynczej grupy przechwytywania. Obiekty grupy reprezentujące grupy przechwytywania zdefiniowane w wyrażeniu <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> regularnym <xref:System.Text.RegularExpressions.GroupCollection> są zwracane <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> przez właściwość obiektu zwróconego przez właściwość. Właściwość <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> jest indeksator (w języku C#) i właściwość <xref:System.Text.RegularExpressions.Group> domyślna (w języku Visual Basic) klasy. Można również pobrać poszczególnych elementów członkowskich przez `foreach` `For Each` iteracji kolekcji przy użyciu lub konstrukcji. Na przykład zobacz poprzednią sekcję.  
  
 W poniższym przykładzie użyto zagnieżdżonych konstrukcji grupowania do przechwytywania podciągów w grupy. Wzorzec `(a(b))c` wyrażenia regularnego pasuje do ciągu "abc". Przypisuje podciąg "ab" do pierwszej grupy przechwytywania, a podciąg "b" do drugiej grupy przechwytywania.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 W poniższym przykładzie użyto nazwanych konstrukcji grupowania do przechwytywania podciągów z ciągu zawierającego dane w formacie "DATANAME:VALUE", który wyrażenie regularne dzieli na dwukropek (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Wzorzec `^(?<name>\w+):(?<value>\w+)` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego.|  
|`(?<name>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania `name`jest .|  
|`:`|Dopasuj dwukropek.|  
|`(?<value>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwa tej grupy przechwytywania `value`jest .|  
  
 Właściwości <xref:System.Text.RegularExpressions.Group> klasy zawierają informacje o przechwyconej grupie: Właściwość `Group.Value` `Group.Index` zawiera przechwycony podciąg, właściwość `Group.Length` wskazuje pozycję początkową przechwyconej grupy w tekście wejściowym, właściwość zawiera długość przechwyconego tekstu, a `Group.Success` właściwość wskazuje, czy podciąg pasuje do wzorca zdefiniowanego przez grupę przechwytywania.  
  
 Zastosowanie kwantyfikatorów do grupy (aby uzyskać więcej informacji, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) modyfikuje relację jednego przechwytywania na grupę przechwytywania na dwa sposoby:  
  
- Jeśli `*` lub `*?` kwantyfikator (który określa zero lub więcej dopasowań) jest stosowany do grupy, grupa przechwytywania może nie mieć dopasowania w ciągu wejściowym. Jeśli nie ma przechwyconego <xref:System.Text.RegularExpressions.Group> tekstu, właściwości obiektu są ustawione w sposób pokazany w poniższej tabeli.  
  
    |Właściwość grupy|Wartość|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Poniższy przykład stanowi ilustrację. W wzorcu `aaa(bbb)*ccc`wyrażenia regularnego pierwsza grupa przechwytywania (podciąg "bbb") może być dopasowana zero lub więcej razy. Ponieważ ciąg wejściowy "aaaccc" pasuje do wzorca, grupa przechwytywania nie ma dopasowania.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Kwantyfikatory mogą odpowiadać wielu wystąpień wzorca, który jest zdefiniowany przez grupę przechwytywania. W takim przypadku `Value` `Length` i właściwości <xref:System.Text.RegularExpressions.Group> obiektu zawierają tylko informacje o ostatnim przechwyconym podciągu. Na przykład następujące wyrażenie regularne pasuje do pojedynczego zdania, które kończy się kropką. Używa dwóch konstrukcji grupowania: Pierwszy przechwytuje poszczególne słowa wraz ze znakiem odstępu; drugi przechwytuje pojedyncze słowa. Jak pokazuje dane wyjściowe z przykładu, mimo że wyrażenie regularne zakończy się przechwytywaniem całego zdania, druga grupa przechwytywania przechwytuje tylko ostatnie słowo.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Powrót do początku](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Kolekcja przechwytywania  
 Obiekt <xref:System.Text.RegularExpressions.Group> zawiera tylko informacje o ostatnim przechwyceniu. Jednak cały zestaw przechwytuje wykonane przez grupę przechwytywania jest <xref:System.Text.RegularExpressions.CaptureCollection> nadal dostępna z obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwość. Każdy element członkowski <xref:System.Text.RegularExpressions.Capture> kolekcji jest obiektem, który reprezentuje przechwytywania wykonane przez tę grupę przechwytywania, w kolejności, w jakiej zostały przechwycone (i, w związku z tym, w kolejności, w jakiej ciągi przechwyconych zostały dopasowane od lewej do prawej w ciągu wejściowym). Poszczególne <xref:System.Text.RegularExpressions.Capture> obiekty można pobrać z kolekcji na dwa sposoby:  
  
- Przez iteracji za pomocą kolekcji `foreach` przy użyciu konstrukcji, `For Each` takich jak (w języku C#) lub (w języku Visual Basic).  
  
- Za pomocą <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> właściwości, aby pobrać określony obiekt przez indeks. Właściwość <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> jest <xref:System.Text.RegularExpressions.CaptureCollection> właściwością domyślną obiektu (w języku Visual Basic) lub indeksatorem (w języku C#).  
  
 Jeśli kwantyfikator nie jest stosowany do <xref:System.Text.RegularExpressions.CaptureCollection> grupy przechwytywania, obiekt zawiera pojedynczy <xref:System.Text.RegularExpressions.Capture> obiekt, który jest mało <xref:System.Text.RegularExpressions.Group> interesujące, ponieważ zawiera informacje o tym samym dopasowania jako jego obiektu. Jeśli kwantyfikator zostanie zastosowany do <xref:System.Text.RegularExpressions.CaptureCollection> grupy przechwytywania, obiekt zawiera wszystkie przechwytywania wykonane przez grupę przechwytywania, a ostatni <xref:System.Text.RegularExpressions.Group> element członkowski kolekcji reprezentuje ten sam przechwytywania jako obiekt.  
  
 Na przykład jeśli używasz wzorca `((a(b))c)+` wyrażenia regularnego (gdzie + kwantyfikator określa jeden lub więcej dopasowań) do przechwytywania dopasowań z ciągu "abcabcabc", <xref:System.Text.RegularExpressions.CaptureCollection> obiekt dla każdego <xref:System.Text.RegularExpressions.Group> obiektu zawiera trzy elementy członkowskie.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 W poniższym przykładzie `(Abc)+` użyto wyrażenia regularnego, aby znaleźć jeden lub więcej kolejnych przebiegów ciągu "Abc" w ciągu "XYZAbcAbcAbcXYZAbcAb". W przykładzie przedstawiono użycie <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości do zwrócenia wielu grup przechwyconych podciągów.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Powrót do początku](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Indywidualne przechwytywanie  
 Klasa <xref:System.Text.RegularExpressions.Capture> zawiera wyniki z pojedynczego przechwytywania wyrażenia podrzędnego. Właściwość <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> zawiera dopasowany tekst, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> a właściwość wskazuje pozycję o zerowej podstawie w ciągu wejściowym, od którego zaczyna się dopasowany podciąg.  
  
 W poniższym przykładzie przeanalizowano ciąg wejściowy dla temperatury wybranych miast. Przecinek (",") służy do oddzielania miasta od jego temperatury, a średnik (";") służy do oddzielania danych każdego miasta. Cały ciąg wejściowy reprezentuje pojedyncze dopasowanie. W wzorcu `((\w+(\s\w+)*),(\d+);)+`wyrażenia regularnego , który jest używany do analizowania ciągu, nazwa miasta jest przypisana do drugiej grupy przechwytywania, a temperatura jest przypisana do czwartej grupy przechwytywania.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Wyrażenie regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(\s\w+)*`|Dopasuj zero lub więcej wystąpień znaku odstępu, po którym następuje jeden lub więcej znaków wyrazu. Ten wzorzec pasuje do nazw miast wielowyrazowych. Jest to trzecia grupa przechwytywania.|  
|`(\w+(\s\w+)*)`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje zero lub więcej wystąpień znaku odstępu i jeden lub więcej znaków wyrazu. Jest to druga grupa przechwytywania.|  
|`,`|Dopasuj przecinek.|  
|`(\d+)`|Dopasuj jedną lub więcej cyfr. Jest to czwarta grupa przechwytywania.|  
|`;`|Dopasuj średnik.|  
|`((\w+(\s\w+)*),(\d+);)+`|Dopasuj wzorzec wyrazu, po którym następują dodatkowe wyrazy, po których następuje przecinek, jedna lub więcej cyfr i średnik jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Text.RegularExpressions>
- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
