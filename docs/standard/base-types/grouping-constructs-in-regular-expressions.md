---
title: Konstrukcje grupujące w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET Framework regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
ms.openlocfilehash: 5b2ea110837d9d5b905f97ab706af52a594f1c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159224"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Konstrukcje grupujące w wyrażeniach regularnych
Grupowanie konstrukcji nakreślić podwyrażenia wyrażenia regularnego i przechwycić podciągi ciągu wejściowego. Można użyć konstrukcji grupowania, aby wykonać następujące czynności:  
  
- Dopasuj wyrażenie podrzędne, które jest powtarzane w ciągu wejściowym.  
  
- Zastosuj kwantyfikator do wyrażenia podrzędnego, który ma wiele elementów języka wyrażenia regularnego. Aby uzyskać więcej informacji na temat kwantyfikatorów, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Dołącz wyrażenie podrzędne w ciągu, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> który <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> jest zwracany przez i metody.  
  
- Pobierz poszczególne wyrażenia <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> podrzędne z właściwości i przetwórz je oddzielnie od dopasowanego tekstu jako całości.  
  
 W poniższej tabeli wymieniono konstrukcje grupowania obsługiwane przez aparat wyrażeń regularnych .NET i wskazuje, czy są przechwytywane lub nie przechwytywanie.  
  
|Konstrukcja grupująca|Przechwytywanie lub nieprzechwytywanie|  
|------------------------|-------------------------------|  
|[Dopasowane wyrażenia podrzędne](#matched_subexpression)|Przechwytywanie|  
|[Nazwane dopasowane wyrażenia podrzędne](#named_matched_subexpression)|Przechwytywanie|  
|[Definicje grup bilansowania](#balancing_group_definition)|Przechwytywanie|  
|[Grupy nieprzechwytujące](#noncapturing_group)|Nieprzechwytywanie|  
|[Opcje grupy](#group_options)|Nieprzechwytywanie|  
|[Dodatnie potwierdzenia wyjmowania o zerowej szerokości](#zerowidth_positive_lookahead_assertion)|Nieprzechwytywanie|  
|[Negatywne potwierdzenia wyglądu o zerowej szerokości](#zerowidth_negative_lookahead_assertion)|Nieprzechwytywanie|  
|[Potwierdzenia dodatnie o zerowej szerokości](#zerowidth_positive_lookbehind_assertion)|Nieprzechwytywanie|  
|[Negatywne twierdzenia o zerowej szerokości](#zerowidth_negative_lookbehind_assertion)|Nieprzechwytywanie|  
|[Grupy atomowe](#atomic_groups)|Nieprzechwytywanie|  
  
 Aby uzyskać informacje na temat grup i modelu obiektów wyrażenia regularnego, zobacz [Grupowanie konstrukcji i obiektów wyrażenia regularnego](#Objects).  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Dopasowane podwyrażenie  
 Następująca konstrukcja grupowania przechwytuje dopasowane wyrażenie podrzędne:  
  
 `(`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest prawidłowym wzorcem wyrażenia regularnego. Przechwytywanie, które używają nawiasów są numerowane automatycznie od lewej do prawej na podstawie kolejności nawiasów otwarcia w wyrażeniu regularnym, począwszy od jednego. Przechwytywanie, które jest ponumerowane zero jest tekstem dopasowanym do całego wzorca wyrażenia regularnego.  
  
> [!NOTE]
> Domyślnie `(`element języka *wyrażenia podrzędnego* `)` przechwytuje dopasowane wyrażenie podrzędne. Jeśli jednak <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowywania <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> wzorców wyrażenia `n` regularnego zawiera flagę lub jeśli opcja jest stosowana do tego wyrażenia podrzędnego (zobacz [Opcje grupy](#group_options) w dalszej części tego tematu), dopasowane wyrażenie podrzędne nie jest przechwytywane.  
  
 Dostęp do przechwyconych grup można uzyskać na cztery sposoby:  
  
- Za pomocą backreference konstrukcji w wyrażeniu regularnym. Dopasowane wyrażenie podrzędne odwołuje się w tym samym `\`wyrażeniu regularnym przy użyciu *liczby*składni , gdzie *liczba* jest liczbą porządkną przechwyconego wyrażenia podrzędnego.  
  
- Za pomocą konstrukcji o nazwie backreference w wyrażeniu regularnym. Dopasowane podwyrażenie odwołuje się w tym samym wyrażeniu regularnym przy użyciu `\k<` *nazwy*`>`składni `\k<`, gdzie *nazwa* jest nazwą grupy przechwytywania lub *liczbą*`>`, gdzie *liczba* jest liczbą porządkową grupy przechwytywania. Grupa przechwytywania ma domyślną nazwę, która jest identyczna z jej liczbą liczbą liczbową. Aby uzyskać więcej informacji, zobacz [Nazwane dopasowane wyrażenia podrzędne](#named_matched_subexpression) w dalszej części tego tematu.  
  
- Za pomocą `$`sekwencji zastępowania <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> *numerów* w wywołaniu lub metody, gdzie *numer* jest liczbą porządkową przechwyconego wyrażenia podrzędnego.  
  
- Programowo przy użyciu <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> przez właściwość. Element członkowski w pozycji zero w kolekcji reprezentuje całą dopasowanie wyrażenia regularnego. Każdy kolejny element członkowski reprezentuje dopasowane wyrażenie podrzędne. Aby uzyskać więcej informacji, zobacz [Grouping Konstrukcje i obiekty wyrażenia regularnego](#Objects) sekcji.  
  
 W poniższym przykładzie przedstawiono wyrażenie regularne, które identyfikuje zduplikowane wyrazy w tekście. Dwie grupy przechwytywania wyrażenia regularnego reprezentują dwa wystąpienia zduplikowanego wyrazu. Drugie wystąpienie jest przechwytywane w celu raportowania jego pozycji wyjściowej w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
`(\w+)\s(\1)\W`  
  
 W poniższej tabeli pokazano, jak interpretowany jest wzorzec wyrażenia regularnego.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\1)`|Dopasuj ciąg w pierwszej przechwyconej grupie. Jest to druga grupa przechwytywania. Przykład przypisuje go do przechwyconej grupy, dzięki czemu pozycja `Match.Index` początkowa zduplikowanego wyrazu może zostać pobrana z właściwości.|  
|`\W`|Dopasuj znak niebędący wyrazem, w tym biały znak i znaki interpunkcyjne. Zapobiega to dopasowywaniu wzorca wyrażenia regularnego od wyrazu, który zaczyna się od słowa z pierwszej przechwyconej grupy.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>O nazwie dopasowane podwyrażenia  
 Następująca konstrukcja grupowania przechwytuje dopasowane podwyrażenie i umożliwia dostęp do niego według nazwy lub liczby:  
  
`(?<name>subexpression)`  
  
 lub:  
  
`(?'name'subexpression)`  
  
 gdzie *nazwa* jest prawidłową nazwą grupy, a *wyrażenie podrzędne* jest prawidłowym wzorcem wyrażenia regularnego. *nazwa* nie może zawierać żadnych znaków interpunkcyjnych i nie może zaczynać się od liczby.  
  
> [!NOTE]
> Jeśli <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowywania wzorców wyrażenia regularnego zawiera <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagę lub jeśli `n` opcja jest stosowana do tego wyrażenia podrzędnego (zobacz Opcje [grupy](#group_options) w dalszej części tego tematu), jedynym sposobem przechwycenia wyrażenia podrzędnego jest jawna nazwanie grup przechwytywania.  
  
 Dostęp do nazwanych przechwyconych grup można uzyskać w następujący sposób:  
  
- Za pomocą konstrukcji o nazwie backreference w wyrażeniu regularnym. Dopasowane wyrażenie podrzędne odwołuje się do tego samego `\k<`wyrażenia regularnego przy użyciu *nazwy*`>`składni , gdzie *nazwa* jest nazwą przechwyconego wyrażenia podrzędnego.  
  
- Za pomocą backreference konstrukcji w wyrażeniu regularnym. Dopasowane wyrażenie podrzędne odwołuje się w tym samym `\`wyrażeniu regularnym przy użyciu *liczby*składni , gdzie *liczba* jest liczbą porządkną przechwyconego wyrażenia podrzędnego. Nazwane dopasowane wyrażenia podrzędne są numerowane kolejno od lewej do prawej po dopasowanych wyrażeniach podrzędnych.  
  
- Za pomocą `${`sekwencji zastępowania <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> *nazw* `}` w wywołaniu lub metody, gdzie *nazwa* jest nazwą przechwyconego wyrażenia podrzędnego.  
  
- Za pomocą `$`sekwencji zastępowania <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> *numerów* w wywołaniu lub metody, gdzie *numer* jest liczbą porządkową przechwyconego wyrażenia podrzędnego.  
  
- Programowo przy użyciu <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> przez właściwość. Element członkowski w pozycji zero w kolekcji reprezentuje całą dopasowanie wyrażenia regularnego. Każdy kolejny element członkowski reprezentuje dopasowane wyrażenie podrzędne. Nazwane przechwycone grupy są przechowywane w kolekcji po numerowanych przechwyconych grupach.  
  
- Programowo, podając nazwę podwyrażenia indeksatorowi obiektu (w języku <xref:System.Text.RegularExpressions.GroupCollection> C#) lub jego <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwości (w języku Visual Basic).  
  
 Prosty wzorzec wyrażenia regularnego ilustruje, jak można odwoływać się do ponumerowanych (nienazwanych) i nazwanych grup programowo lub przy użyciu składni języka wyrażenia regularnego. Wyrażenie `((?<One>abc)\d+)?(?<Two>xyz)(.*)` regularne tworzy następujące grupy przechwytywania według liczby i nazwy. Pierwsza grupa przechwytywania (liczba 0) zawsze odnosi się do całego wzorca.  
  
|Liczba|Nazwa|Wzorce|  
|------------|----------|-------------|  
|0|0 (nazwa domyślna)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (nazwa domyślna)|`((?<One>abc)\d+)`|  
|2|2 (nazwa domyślna)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Dwa|`(?<Two>xyz)`|  
  
 W poniższym przykładzie przedstawiono wyrażenie regularne, które identyfikuje zduplikowane wyrazy i słowo, które natychmiast następuje po każdym zduplikowanym słowie. Wzorzec wyrażenia regularnego definiuje dwa `duplicateWord`nazwane wyrażenia podrzędne: , który reprezentuje zduplikowane słowo; i `nextWord`, który reprezentuje słowo, które następuje po zduplikowanym słowie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 W poniższej tabeli pokazano, jak interpretowane jest wyrażenie regularne.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwij tę `duplicateWord`grupę przechwytywania .|  
|`\s`|Dopasowuje znak odstępu.|  
|`\k<duplicateWord>`|Dopasuj ciąg z przechwyconej grupy o nazwie `duplicateWord`.|  
|`\W`|Dopasuj znak niebędący wyrazem, w tym biały znak i znaki interpunkcyjne. Zapobiega to dopasowywaniu wzorca wyrażenia regularnego od wyrazu, który zaczyna się od słowa z pierwszej przechwyconej grupy.|  
|`(?<nextWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nazwij tę `nextWord`grupę przechwytywania .|  
  
 Należy zauważyć, że nazwę grupy można powtórzyć w wyrażeniu regularnym. Na przykład jest możliwe dla więcej niż `digit`jednej grupy, aby być nazwane , jak pokazano w poniższym przykładzie. W przypadku zduplikowanych nazw <xref:System.Text.RegularExpressions.Group> wartość obiektu jest określana przez ostatnie udane przechwycenie w ciągu wejściowym. Ponadto <xref:System.Text.RegularExpressions.CaptureCollection> jest wypełniona informacjami o każdym przechwyceniu, tak jak byłoby, gdyby nazwa grupy nie została zduplikowana.  
  
 W poniższym przykładzie wyrażenie `\D+(?<digit>\d+)\D+(?<digit>\d+)?` regularne zawiera dwa wystąpienia `digit`grupy o nazwie . Pierwsza `digit` nazwana grupa przechwytuje jeden lub więcej znaków cyfr. Druga `digit` nazwana grupa przechwytuje zero lub jedno wystąpienie jednego lub więcej znaków cyfr. Jak pokazuje dane wyjściowe z przykładu, jeśli druga grupa przechwytywania pomyślnie pasuje do tekstu, <xref:System.Text.RegularExpressions.Group> wartość tego tekstu definiuje wartość obiektu. Jeśli druga grupa przechwytywania nie może być zgodna z ciągiem wejściowym, wartość <xref:System.Text.RegularExpressions.Group> ostatniego pomyślnego dopasowania definiuje wartość obiektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 W poniższej tabeli pokazano, jak interpretowane jest wyrażenie regularne.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\D+`|Dopasuj co najmniej jeden znak cyfry niedziesiętne.|  
|`(?<digit>\d+)`|Dopasuj co najmniej jeden znak cyfry dziesiętne. Przypisz dopasowanie `digit` do nazwanej grupy.|  
|`\D+`|Dopasuj co najmniej jeden znak cyfry niedziesiętne.|  
|`(?<digit>\d+)?`|Dopasuj zero lub jedno wystąpienie jednego lub więcej znaków cyfr dziesiętnych. Przypisz dopasowanie `digit` do nazwanej grupy.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Równoważenie definicji grup  
 Definicja grupy bilansującej usuwa definicję wcześniej zdefiniowanej grupy i przechowuje w bieżącej grupie interwał między wcześniej zdefiniowaną grupą a bieżącą grupą. Ta konstrukcja grupowania ma następujący format:  
  
`(?<name1-name2>subexpression)`  
  
 lub:  
  
`(?'name1-name2' subexpression)`
  
 gdzie *name1* jest bieżącą grupą (opcjonalnie), *name2* jest wcześniej zdefiniowaną grupą, a *wyrażenie podrzędne* jest prawidłowym wzorcem wyrażenia regularnego. Definicja grupy bilansującej usuwa definicję *nazwy2* i przechowuje interwał między *name2* i *name1* w *nazwie1*. Jeśli nie zdefiniowano grupy *name2,* backtracks meczu. Ponieważ usunięcie ostatniej definicji *name2* ujawnia poprzednią definicję *name2*, ta konstrukcja umożliwia użycie stosu przechwytów dla *nazwy grupy2* jako licznika do śledzenia zagnieżdżonych konstrukcji, takich jak nawiasy lub nawiasy otwierające i zamykające.  
  
 Definicja grupy równoważenia używa *name2* jako stosu. Początkowy znak każdej zagnieżdżonej konstrukcji <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> jest umieszczany w grupie i w jej kolekcji. Po dopasowaniu znaku zamykającego jego odpowiedni znak otwarcia <xref:System.Text.RegularExpressions.Group.Captures%2A> jest usuwany z grupy, a kolekcja jest zmniejszana o jeden. Po dopasowaniu znaków otwarcia i zamknięcia wszystkich zagnieżdżonych konstrukcji *nazwa2* jest pusta.  
  
> [!NOTE]
> Po zmodyfikowaniu wyrażenia regularnego w poniższym przykładzie, aby użyć odpowiedniego znaku otwarcia i zamknięcia konstrukcji zagnieżdżonej, można go używać do obsługi większości zagnieżdżonych konstrukcji, takich jak wyrażenia matematyczne lub wiersze kodu programu, które zawierają wiele wywołań metody zagnieżdżonej.  
  
 W poniższym przykładzie użyto definicji grupy równoważenia, aby dopasować nawiasy kąta lewego i prawego (<>) w ciągu wejściowym. W przykładzie zdefiniowano `Open` dwie `Close`nazwane grupy i , które są używane jak stos do śledzenia pasujących par nawiasów kątowych. Każdy przechwycony lewy nawias `Open` kątowy jest wypychany do kolekcji przechwytywania `Close` grupy, a każdy przechwycony nawias kąta prawego jest wypychany do kolekcji przechwytywania grupy. Definicja grupy wyważania zapewnia, że dla każdego lewego nawiasu kątowego znajduje się pasujący nawias kątowy. Jeśli nie ma, końcowy podwzorzec , jest obliczana tylko wtedy, `(?(Open)(?!))`gdy `Open` grupa nie jest pusta (i dlatego, jeśli wszystkie zagnieżdżone konstrukcje nie zostały zamknięte). Jeśli ostateczny podwzorzec jest obliczany, `(?!)` dopasowanie nie powiedzie się, ponieważ podwzorzec jest zero szerokości ujemne wyczekiwanie potwierdzenia, że zawsze nie powiedzie się.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Wzorzec wyrażenia regularnego jest następujące:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Wyrażenie regularne jest interpretowane w następujący sposób:  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij od początku ciągu.|  
|`[^<>]*`|Dopasuj zero lub więcej znaków, które nie są nawiasami kąta lewego lub prawego.|  
|`(?'Open'<)`|Dopasuj lewy nawias kątowy i `Open`przypisz go do grupy o nazwie .|  
|`[^<>]*`|Dopasuj zero lub więcej znaków, które nie są nawiasami kąta lewego lub prawego.|  
|`((?'Open'<)[^<>]*)+`|Dopasuj co najmniej jedno wystąpienie nawiasu kątowego po lewej stronie, po którym następuje zero lub więcej znaków, które nie są nawiasami kąta lewego lub prawego. Jest to druga grupa przechwytywania.|  
|`(?'Close-Open'>)`|Dopasuj nawias kątowy, przypisz podciąg między `Open` `Close` grupą a bieżącą `Open` grupą do grupy i usuń definicję grupy.|  
|`[^<>]*`|Dopasuj zero lub więcej wystąpień dowolnego znaku, który nie jest ani lewym, ani prawym kątem.|  
|`((?'Close-Open'>)[^<>]*)+`|Dopasuj co najmniej jedno wystąpienie nawiasu kątowego, po którym następuje zero lub więcej wystąpień dowolnego znaku, który nie jest ani lewym, ani prawym kątem. Podczas dopasowywania nawiasu kąta prostokątnego należy przypisać podciąg między grupą `Open` a bieżącą grupą `Close` do grupy i usunąć definicję `Open` grupy. Jest to trzecia grupa przechwytywania.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Dopasuj zero lub więcej wystąpień następującego wzorca: jedno lub więcej wystąpień nawiasu kątowego po lewej stronie, po których następuje zero lub więcej znaków nawiasu niekątnego, po których następuje jedno lub więcej wystąpień wnawiasu kątowego, po którym następuje zero lub więcej wystąpień wsporniki niekącowe. Podczas dopasowywania nawiasu kąta `Open` prostokątnego usuń definicję grupy `Open` i przypisz `Close` podciąg między grupą a bieżącą grupą do grupy. Jest to pierwsza grupa przechwytywania.|  
|`(?(Open)(?!))`|Jeśli `Open` grupa istnieje, porzuć dopasowanie, jeśli można dopasować pusty ciąg, ale nie rozwijaj pozycji aparatu wyrażeń regularnych w ciągu. Jest to potwierdzenie ujemne o zerowej szerokości. Ponieważ pusty ciąg jest zawsze niejawnie obecny w ciągu wejściowym, to dopasowanie zawsze kończy się niepowodzeniem. Niepowodzenie tego dopasowania wskazuje, że nawiasy kątowe nie są zrównoważone.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Ostateczne wyrażenie podrzędne wskazuje, `(?(Open)(?!))`czy konstrukcje zagnieżdżania w ciągu wejściowym są prawidłowo zrównoważone (na przykład, czy każdy lewy nawias kątowy jest dopasowywany przez nawias kątowy). Używa uzgadniania warunkowego na podstawie prawidłowej przechwyconej grupy; Aby uzyskać więcej informacji, zobacz [Konstrukcje alternacji](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Jeśli `Open` grupa jest zdefiniowana, aparat wyrażeń `(?!)` regularnych próbuje dopasować wyrażenie podrzędne w ciągu wejściowym. Grupa `Open` powinna być zdefiniowana tylko wtedy, gdy konstrukcje zagnieżdżania są niezrównoważone. W związku z tym wzorzec, który ma być dopasowany w ciągu wejściowym powinien być taki, który zawsze powoduje, że dopasowanie nie powiedzie się. W takim `(?!)` przypadku jest zero szerokości ujemnego wyglądu twierdzenie, które zawsze kończy się niepowodzeniem, ponieważ pusty ciąg jest zawsze niejawnie obecny w następnej pozycji w ciągu wejściowym.  
  
 W tym przykładzie aparat wyrażeń regularnych\<oblicza ciąg\<wejściowy " abc><mno xyz>>", jak pokazano w poniższej tabeli.  
  
|Krok|Wzorce|Wynik|  
|----------|-------------|------------|  
|1|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego|  
|2|`[^<>]*`|Wyszukuje znaki nawiasu niekątnego przed lewym nawiasem kątowym;nie znajduje żadnych dopasowań.|  
|3|`(((?'Open'<)`|Pasuje do lewego\<nawiasu kątowego w "abc>" i przypisuje go do `Open` grupy.|  
|4|`[^<>]*`|Pasuje do "abc".|  
|5|`)+`|"<abc" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem kąta lewego, `(?'Open'<)[^<>]*)` więc aparat wyrażeń regularnych nie pętli z powrotem do wzorca.|  
|6|`((?'Close-Open'>)`|Dopasowuje nawias kąta prawego w\<"abc>", przypisuje `Open` "abc", który jest podciągiem między grupą a prawym nawiasem kątowym, do `Close` grupy i usuwa bieżącą wartość ("<") `Open` grupy, pozostawiając ją pustą.|  
|7|`[^<>]*`|Wyszna znaków nawiasu niekątnego po nawiasie kąta prostokątnego; nie znajdzie żadnych dopasowań.|  
|8|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem kąta prostokątnego, `((?'Close-Open'>)[^<>]*)` więc aparat wyrażeń regularnych nie pętli z powrotem do podwzorca.|  
|9|`)*`|Wartość pierwszej przechwyconej grupy to "\<abc>".<br /><br /> Następny znak w ciągu wejściowym jest nawiasem kąta po lewej `(((?'Open'<)` stronie, więc aparat wyrażeń regularnych pętli z powrotem do wzorca.|  
|10|`(((?'Open'<)`|Pasuje do lewego\<nawiasu kątowego w "mno" i przypisuje go do `Open` grupy. Jego <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcja ma teraz jedną wartość, "<".|  
|11|`[^<>]*`|Mecze "mno".|  
|12|`)+`|"<mno" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym jest nawiasem kąta po lewej `(?'Open'<)[^<>]*)` stronie, więc aparat wyrażeń regularnych pętli z powrotem do wzorca.|  
|13|`(((?'Open'<)`|Pasuje do lewego\<nawiasu kątowego w " xyz>" i przypisuje go do `Open` grupy. Kolekcja <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> `Open` grupy zawiera teraz dwa ujęcia: lewy wspornik kątowy z "\<\<mno", a lewy wspornik kątowy z " xyz>".|  
|14|`[^<>]*`|Pasuje do "xyz".|  
|15|`)+`|"<xyz" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem kąta lewego, `(?'Open'<)[^<>]*)` więc aparat wyrażeń regularnych nie pętli z powrotem do wzorca.|  
|16|`((?'Close-Open'>)`|Pasuje do nawiasu\<kątowego w " xyz>". "xyz", przypisuje podciąg między `Open` grupą a prawym `Close` nawiasem kątowym do grupy `Open` i usuwa bieżącą wartość grupy. Wartość poprzedniego przechwytywania (lewy nawias kątowy\<w " mno") staje `Open` się bieżącą wartością grupy. Kolekcja <xref:System.Text.RegularExpressions.Group.Captures%2A> `Open` grupy zawiera teraz pojedynczy uchwyt kątowy, lewy\<wspornik kątowy z " xyz>".|  
|17|`[^<>]*`|Wyszna znaków nawiasu niekątnego; nie znajdzie żadnych dopasowań.|  
|18|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym jest nawiasem kątowym, więc aparat `((?'Close-Open'>)[^<>]*)` wyrażeń regularnych pętli z powrotem do wzorca.|  
|19|`((?'Close-Open'>)`|Dopasowuje ostatni nawias kątowy w "xyz\<>>", przypisuje grupie "mno `Open` xyz>" (podciąg między grupą a nawiasem kąta prostokątnego) `Close` i usuwa bieżącą `Open` wartość grupy. Grupa `Open` jest teraz pusta.|  
|20|`[^<>]*`|Wyszna znaków nawiasu niekątnego; nie znajdzie żadnych dopasowań.|  
|21|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem kąta prostokątnego, `((?'Close-Open'>)[^<>]*)` więc aparat wyrażeń regularnych nie pętli z powrotem do podwzorca.|  
|22|`)*`|Wartość pierwszej przechwyconej\<grupy to "<mno xyz>>".<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem kąta lewego, `(((?'Open'<)` więc aparat wyrażeń regularnych nie pętli z powrotem do wzorca.|  
|23|`(?(Open)(?!))`|Grupa `Open` nie jest zdefiniowana, więc nie jest podejmowana żadna relacja.|  
|24|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Grupy niezapamiętywane  
 Następująca konstrukcja grupowania nie przechwytuje podciągu, który jest dopasowywany przez wyrażenie podrzędne:  
  
`(?:subexpression)`
  
 gdzie *wyrażenie podrzędne* jest prawidłowym wzorcem wyrażenia regularnego. Konstrukcja grupy nieprzechwytującej jest zwykle używana, gdy kwantyfikator jest stosowany do grupy, ale podciągi przechwycone przez grupę nie są interesujące.  
  
> [!NOTE]
> Jeśli wyrażenie regularne zawiera zagnieżdżone konstrukcje grupowania, zewnętrzna konstrukcja grupy nieprzechwytującej nie ma zastosowania do konstrukcji grupy zagnieżdżonej wewnętrznie.  
  
 W poniższym przykładzie przedstawiono wyrażenie regularne, które zawiera grupy nieprzechwytujące. Należy zauważyć, że dane wyjściowe nie zawiera żadnych przechwyconych grup.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Wyrażenie `(?:\b(?:\w+)\W*)+\.` regularne jest zgodne z zdaniem zakończonym kropką. Ponieważ wyrażenie regularne koncentruje się na zdaniach, a nie na poszczególnych wyrazach, konstrukcje grupowania są używane wyłącznie jako kwantyfikatory. Wzorzec wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?:\w+)`|Dopasowuje co najmniej jeden znak słowa. Nie należy przypisywać dopasowanego tekstu do przechwyconej grupy.|  
|`\W*`|Dopasuj zero lub więcej znaków innych niż word.|  
|`(?:\b(?:\w+)\W*)+`|Dopasuj wzorzec jednego lub więcej znaków wyrazu rozpoczynających się od granicy wyrazu, po których następuje zero lub więcej znaków innych niż słowa, jeden lub więcej razy. Nie należy przypisywać dopasowanego tekstu do przechwyconej grupy.|  
|`\.`|Dopasuj kropkę.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Opcje grupy  
 Następująca konstrukcja grupowania stosuje lub wyłącza określone opcje w wyrażeniu podrzędnym:  
  
 `(?imnsx-imnsx:`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest prawidłowym wzorcem wyrażenia regularnego. Na przykład `(?i-s:)` włącza niewrażliwość wielkości liter i wyłącza tryb jednowierszowy. Aby uzyskać więcej informacji na temat opcji wbudowanych, które można określić, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
> Można określić opcje, które mają zastosowanie do całego wyrażenia <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> regularnego, a nie wyrażenia podrzędnego przy użyciu konstruktora klasy lub metody statycznej. Można również określić opcje w wierszu, które mają zastosowanie `(?imnsx-imnsx)` po określonym punkcie w wyrażeniu regularnym przy użyciu konstrukcji języka.  
  
 Konstrukcja opcji grupy nie jest grupą przechwytywania. Oznacza to, że chociaż dowolna część ciągu przechwycona przez *wyrażenie podrzędne* jest uwzględniona w dopasowaniu, nie jest uwzględniona w przechwyconej grupie ani nie jest używana do wypełniania <xref:System.Text.RegularExpressions.GroupCollection> obiektu.  
  
 Na przykład wyrażenie `\b(?ix: d \w+)\s` regularne w poniższym przykładzie używa opcji wbudowanych w konstrukcji grupowania, aby umożliwić dopasowanie bez uwzględniania wielkości liter i ignorować biały znak wzorca w identyfikowaniu wszystkich wyrazów, które zaczynają się od litery "d". Wyrażenie regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?ix: d \w+)`|Używając dopasowywania bez uwzględniania wielkości liter i ignorując biały znak w tym wzorcu, dopasuj literę "d", po której następuje jeden lub więcej znaków wyrazu.|  
|`\s`|Dopasowuje znak odstępu.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Dodatnie asercje z patrzeniem w przód o zerowej szerokości  
 Następująca konstrukcja grupowania definiuje potwierdzenie dodatniego oczekiwania o zerowej szerokości:  
  
 `(?=`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, ciąg wejściowy musi być zgodny z wzorcem wyrażenia regularnego w *wyrażeniu podrzędnym,* chociaż dopasowany podciąg nie jest uwzględniony w wyniku dopasowania. Zero szerokości dodatnie lookahead potwierdzenia nie backtrack.  
  
 Zazwyczaj potwierdzenie dodatnie o zerowej szerokości znajduje się na końcu wzorca wyrażenia regularnego. Definiuje podciąg, który musi znajdować się na końcu ciągu, aby dopasowanie wystąpiło, ale nie powinno być uwzględnione w dopasowaniu. Jest to również przydatne do zapobiegania nadmiernego wycofywania. Można użyć potwierdzenia z wyprzedzeniem dodatnim o zerowej szerokości, aby upewnić się, że określona przechwycona grupa zaczyna się od tekstu, który pasuje do podzbioru wzorca zdefiniowanego dla tej przechwyconej grupy. Na przykład jeśli grupa przechwytywania pasuje do kolejnych znaków wyrazu, można użyć potwierdzenia z wynikiem dodatnim o zerowej szerokości, aby wymagać, aby pierwszy znak był alfabetycznym wielkimznakiem.  
  
 W poniższym przykładzie użyto potwierdzenia dodatniego punktu wyczekiwania o zerowej szerokości, aby dopasować słowo, które poprzedza czasownik "is" w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Wyrażenie `\b\w+(?=\sis\b)` regularne jest interpretowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(?=\sis\b)`|Określ, czy po znakach wyrazu następuje znak odstępu, a ciąg "is", który kończy się na granicy wyrazu. Jeśli tak, dopasowanie zakończy się pomyślnie.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Ujemne asercje z patrzeniem w przód o zerowej szerokości  
 Następująca konstrukcja grupowania definiuje potwierdzenie ujemnego wyglądu o zerowej szerokości:  
  
 `(?!`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, ciąg wejściowy nie może być zgodny z wzorcem wyrażenia regularnego w *wyrażeniu podrzędnym,* chociaż dopasowany ciąg nie jest uwzględniony w wyniku dopasowania.  
  
 Zero szerokości ujemne wygląd potwierdzenia jest zwykle używany na początku lub na końcu wyrażenia regularnego. Na początku wyrażenia regularnego można zdefiniować określony wzorzec, który nie powinien być dopasowywany, gdy początek wyrażenia regularnego definiuje podobny, ale bardziej ogólny wzorzec do dopasowania. W takim przypadku jest często używany do ograniczenia wycofywania. Na końcu wyrażenia regularnego można zdefiniować wyrażenie podrzędne, które nie może wystąpić na końcu dopasowania.  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które używa potwierdzenia wyszukiwania o zerowej szerokości na początku wyrażenia regularnego, aby dopasować wyrazy, które nie zaczynają się od "un".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Wyrażenie `\b(?!un)\w+\b` regularne jest interpretowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?!un)`|Określ, czy następne dwa znaki są "un". Jeśli tak nie jest, dopasowanie jest możliwe.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które używa potwierdzenia wyszukiwania o zerowej szerokości na końcu wyrażenia regularnego, aby dopasować wyrazy, które nie kończą się znakiem interpunkcyjnym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Wyrażenie `\b\w+\b(?!\p{P})` regularne jest interpretowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
|`\p{P})`|Jeśli następny znak nie jest symbolem interpunkcyjnym (na przykład kropką lub przecinkiem), dopasowanie zakończy się pomyślnie.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Dodatnie asercje wsteczne o zerowej szerokości  
 Następująca konstrukcja grupowania definiuje potwierdzenie wyszukiwania dodatniego o zerowej szerokości:  
  
 `(?<=`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, *wyrażenie podrzędne* musi występować w `subexpression` ciągu wejściowym po lewej stronie bieżącej pozycji, chociaż nie jest uwzględniony w wyniku dopasowania. Zero-width dodatnie lookbehind potwierdzenia nie backtrack.  
  
 Zero-width dodatnie lookbehind potwierdzeń są zwykle używane na początku wyrażeń regularnych. Wzorzec, który definiują jest warunkiem wstępnym dla dopasowania, chociaż nie jest częścią wyniku meczu.  
  
 Na przykład poniższy przykład pasuje do dwóch ostatnich cyfr roku dla dwudziestego pierwszego wieku (oznacza to, że wymaga, aby cyfry "20" poprzedzały dopasowany ciąg).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Wzorzec `(?<=\b20)\d{2}\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\d{2}`|Dopasuj dwie cyfry dziesiętne.|  
|`(?<=\b20)`|Kontynuuj dopasowanie, jeśli dwie cyfry dziesiętne są poprzedzone cyframi dziesiętnymi "20" na granicy wyrazu.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Potwierdzenia dodatnie o zerowej szerokości są również używane do ograniczania wycofywania, gdy ostatni znak lub znaki w przechwyconej grupie muszą być podzbiorem znaków, które pasują do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie kolejne znaki wyrazu, można użyć potwierdzenia widoku dodatniego o zerowej szerokości, aby wymagać, aby ostatni znak był alfabetyczny.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Ujemne asercje wsteczne o zerowej szerokości  
 Następująca konstrukcja grupowania definiuje potwierdzenie ujemnego lookbehind o zerowej szerokości:  
  
 `(?<!`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, *wyrażenie podrzędne* nie może występować w ciągu wejściowym po lewej stronie bieżącej pozycji. Jednak każdy podciąg, który `subexpression` nie jest zgodny, nie jest uwzględniony w wyniku dopasowania.  
  
 Zero szerokości negatywnych lookbehind potwierdzeń są zwykle używane na początku wyrażeń regularnych. Wzorzec, który definiują wyklucza dopasowanie w ciągu, który następuje. Są one również używane do ograniczania wycofywania, gdy ostatni znak lub znaki w przechwyconej grupie nie mogą być co najmniej jedną z znaków, które pasują do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie kolejne znaki wyrazu, można użyć potwierdzenia widoku dodatniego o zerowej szerokości, aby wymagać, aby ostatni znak nie był znakiem podkreślenia (\_).  
  
 Poniższy przykład pasuje do daty dla każdego dnia tygodnia, który nie jest weekendem (to nie jest ani sobota, ani niedziela).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Wzorzec `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasuj jeden lub więcej znaków wyrazu, po których następuje znak odstępu.|  
|`\d{1,2},`|Dopasuj jedną lub dwie cyfry dziesiętne, po których następuje znak odstępu i przecinek.|  
|`\d{4}\b`|Dopasuj cztery cyfry dziesiętne i zakończ dopasowanie na granicy wyrazu.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Jeśli mecz jest poprzedzony czymś innym niż ciągi "sobota" lub "niedziela", po którym następuje spacja, dopasowanie zakończy się pomyślnie.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Grupy atomowe  
 Następująca konstrukcja grupowania reprezentuje grupę atomową (znaną w niektórych innych aparatach wyrażeń regularnych jako podwyrażenie niezwrotne, podwyrażenie atomowe lub podwyrażenie tylko raz):
  
 `(?>`*wyrażenie podrzędne*`)`  
  
 gdzie *wyrażenie podrzędne* jest dowolnym wzorcem wyrażenia regularnego.  
  
 Zwykle, jeśli wyrażenie regularne zawiera opcjonalny lub alternatywny wzorc dopasowania i dopasowania nie powiedzie się, aparat wyrażeń regularnych można rozgałęzić w wielu kierunkach, aby dopasować ciąg wejściowy do wzorca. Jeśli dopasowanie nie zostanie znaleziony, gdy trwa pierwszej gałęzi, aparat wyrażeń regularnych można z powrotem lub backtrack do punktu, w którym miało pierwsze dopasowanie i spróbuj dopasować przy użyciu drugiej gałęzi. Ten proces może być kontynuowany, dopóki wszystkie gałęzie nie zostaną wypróbowane.  
  
 Konstrukcja `(?>`języka *podwyrażenia* `)` wyłącza wycofywanie. Aparat wyrażeń regularnych będzie pasować do tylu znaków w ciągu wejściowym, jak to możliwe. Gdy nie ma możliwości dalszego dopasowania, nie cofa się, aby próbować alternatywnych dopasowań wzorca. (Oznacza to, że wyrażenie podrzędne pasuje tylko do ciągów, które byłyby dopasowane przez wyrażenie podrzędne samodzielnie; nie próbuje dopasować ciąg oparty na wyrażeniu podrzędnym i wszelkich wyrażeniach podrzędnych, które następują po nim.)  
  
 Ta opcja jest zalecana, jeśli wiesz, że wycofywanie nie powiedzie się. Uniemożliwienie aparatowi wyrażeń regularnych wykonywania niepotrzebnego wyszukiwania zwiększa wydajność.  
  
 W poniższym przykładzie przedstawiono sposób, w jaki grupa atomowa modyfikuje wyniki dopasowania wzorca. Wycofywanie wyrażenia regularnego pomyślnie pasuje do serii powtarzających się znaków, po których następuje jeszcze jedno wystąpienie tego samego znaku na granicy słowa, ale niecofanie wyrażenia regularnego nie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Wyrażenie `(?>(\w)\1+).\b` regularne nonbacktracking jest zdefiniowane w sposób pokazany w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasuj pojedynczy znak wyrazu i przypisz go do pierwszej grupy przechwytywania.|  
|`\1+`|Dopasuj wartość pierwszego przechwyconego podciągu jeden lub więcej razy.|  
|`.`|Dopasuj dowolny znak.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
|`(?>(\w)\1+)`|Dopasuj jedno lub więcej wystąpień zduplikowanego znaku wyrazu, ale nie cofaj się, aby dopasować ostatni znak na granicy słowa.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Konstrukty grupujące i obiekty wyrażeń regularnych  
 Podciągi, które są dopasowane przez grupę przechwytywania <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> wyrażenia regularnego są reprezentowane przez <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> obiekty, które mogą <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> być pobierane z obiektu, który jest zwracany przez właściwość. Obiekt <xref:System.Text.RegularExpressions.GroupCollection> jest wypełniany w następujący sposób:  
  
- Pierwszy <xref:System.Text.RegularExpressions.Group> obiekt w kolekcji (obiekt na indeksie zero) reprezentuje całe dopasowanie.  
  
- Następny zestaw <xref:System.Text.RegularExpressions.Group> obiektów reprezentuje nienazwane (numerowane) grupy przechwytywania. Pojawiają się one w kolejności, w jakiej są zdefiniowane w wyrażeniu regularnym, od lewej do prawej. Wartości indeksu tych grup wahają się od 1 do liczby nienazwanych grup przechwytywania w kolekcji. (Indeks określonej grupy jest odpowiednikiem jego numerowane odwołanie wsteczne. Aby uzyskać więcej informacji na temat odwołań wstecznych, zobacz [Backreference Konstrukcje](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
- Ostateczny zestaw <xref:System.Text.RegularExpressions.Group> obiektów reprezentuje nazwane grupy przechwytywania. Pojawiają się one w kolejności, w jakiej są zdefiniowane w wyrażeniu regularnym, od lewej do prawej. Wartość indeksu pierwszej nazwanej grupy przechwytywania jest większa niż indeks ostatniej nienazwanej grupy przechwytywania. Jeśli w wyrażeniu regularnym nie ma żadnych nienazwanych grup przechwytywania, wartość indeksu pierwszej nazwanej grupy przechwytywania jest jedną z nich.  
  
 Jeśli kwantyfikator zostanie zastosowany do <xref:System.Text.RegularExpressions.Group> grupy <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>przechwytywania, odpowiedni obiekt , <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>i <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> właściwości odzwierciedlają ostatni podciąg, który jest przechwytywany przez grupę przechwytywania. Można pobrać kompletny zestaw podciągów, które są przechwytywane przez <xref:System.Text.RegularExpressions.CaptureCollection> grupy, które mają <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kwantyfikatory z obiektu, który jest zwracany przez właściwość.  
  
 Poniższy przykład wyjaśnia relację <xref:System.Text.RegularExpressions.Group> między <xref:System.Text.RegularExpressions.Capture> obiektami i.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Wzorzec `(\b(\w+)\W+)+` wyrażenia regularnego wyodrębnia poszczególne wyrazy z ciągu. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Razem te znaki tworzą słowo. Jest to druga grupa przechwytywania.|  
|`\W+`|Dopasuj jeden lub więcej znaków innych niż word.|  
|`(\b(\w+)\W+)`|Dopasuj wzorzec jednego lub więcej znaków wyrazu, po którym następuje jeden lub więcej znaków innych niż word jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
 Druga grupa przechwytywania pasuje do każdego słowa zdania. Pierwsza grupa przechwytywania pasuje do każdego wyrazu wraz z znakiem interpunkcyjnym i białym znakiem, które następują po słowie. Obiekt, <xref:System.Text.RegularExpressions.Group> którego indeks ma 2 zawiera informacje o tekście dopasowanym przez drugą grupę przechwytywania. Kompletny zestaw słów przechwyconych przez <xref:System.Text.RegularExpressions.CaptureCollection> grupę przechwytywania są <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> dostępne z obiektu zwróconego przez właściwość.  
  
## <a name="see-also"></a>Zobacz też

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Nawracanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
