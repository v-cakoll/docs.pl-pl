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
ms.openlocfilehash: 5be98a5a213592b169bee430d84c4fc3a1d5fcef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290529"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Konstrukcje grupujące w wyrażeniach regularnych
Konstrukcje grupujące odróżnić podwyrażenia wyrażenia regularnego i przechwytuje podciągi ciągu wejściowego. Można użyć konstrukcji grupowania, aby wykonać następujące czynności:  
  
- Dopasowuje Podwyrażenie powtarzające się w ciągu wejściowym.  
  
- Zastosuj kwantyfikator do podwyrażenia, które ma wiele elementów języka wyrażenia regularnego. Aby uzyskać więcej informacji na temat kwantyfikatorów, zobacz [Kwantyfikatory](quantifiers-in-regular-expressions.md).  
  
- Uwzględnij Podwyrażenie w ciągu, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> .  
  
- Pobierz pojedyncze Podwyrażenie z <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości i przetwórz je niezależnie od dopasowanego tekstu jako całości.  
  
 W poniższej tabeli wymieniono konstrukcje grupujące obsługiwane przez aparat wyrażeń regularnych programu .NET i wskazuje, czy są przechwytywane lub nieprzechwytywane.  
  
|Konstrukcja grupująca|Przechwytywanie lub przechwytywanie|  
|------------------------|-------------------------------|  
|[Dopasowane podwyrażenia](#matched_subexpression)|Przechwytywania|  
|[Nazwane dopasowane wyrażenia cząstkowe](#named_matched_subexpression)|Przechwytywania|  
|[Definicje grup równoważenia](#balancing_group_definition)|Przechwytywania|  
|[Grupy nieprzechwycone](#noncapturing_group)|Nieprzechwyconą|  
|[Opcje grupy](#group_options)|Nieprzechwyconą|  
|[Pozytywne potwierdzenia naprzód o zerowej szerokości](#zerowidth_positive_lookahead_assertion)|Nieprzechwyconą|  
|[Negatywne potwierdzenia naprzód w zerowej szerokości](#zerowidth_negative_lookahead_assertion)|Nieprzechwyconą|  
|[Pozytywne potwierdzenia asercja wsteczna o zerowej szerokości](#zerowidth_positive_lookbehind_assertion)|Nieprzechwyconą|  
|[Negatywne asercja wstecznay o zerowej szerokości](#zerowidth_negative_lookbehind_assertion)|Nieprzechwyconą|  
|[Grupy niepodzielne](#atomic_groups)|Nieprzechwyconą|  
  
 Aby uzyskać informacje na temat grup i modelu obiektów wyrażeń regularnych, zobacz [Grouping konstrukcjes and Regular Expression Objects](#Objects).  
  
<a name="matched_subexpression"></a>
## <a name="matched-subexpressions"></a>Dopasowane podwyrażenie  
 Następująca konstrukcja grupująca przechwytuje Dopasowane Podwyrażenie:  
  
 `(`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym prawidłowym wzorcem wyrażenia regularnego. Przechwytuje, że nawiasy są numerowane automatycznie od lewej do prawej na podstawie kolejności nawiasów otwierających w wyrażeniu regularnym, rozpoczynając od jednego. Przechwytywanie o numerze zero jest tekstem dopasowanym przez cały wzorzec wyrażenia regularnego.  
  
> [!NOTE]
> Domyślnie `(` element języka *subexpression* `)` przechwytuje Dopasowane Podwyrażenie. Ale jeśli <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowania do wzorca wyrażenia regularnego zawiera <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagę lub jeśli `n` opcja jest stosowana do tego podwyrażenia (zobacz [Opcje grupy](#group_options) w dalszej części tego tematu), dopasowane Podwyrażenie nie jest przechwytywane.  
  
 Dostęp do przechwyconych grup można uzyskać na cztery sposoby:  
  
- Za pomocą konstrukcji odwołania wstecznego w wyrażeniu regularnym. Dopasowane Podwyrażenie jest przywoływane w tym samym wyrażeniu regularnym przy użyciu `\` *numeru*składni, gdzie *Number* jest numerem porządkowym przechwyconego podwyrażenia.  
  
- Za pomocą nazwanej konstrukcji odwołania wstecznego w wyrażeniu regularnym. Dopasowane Podwyrażenie jest przywoływane w tym samym wyrażeniu regularnym przy użyciu `\k<` *nazwy*składni `>` , gdzie *name* jest nazwą grupy przechwytywania lub `\k<` *cyfrą* `>` , gdzie *Number* jest numerem porządkowym grupy przechwytywania. Grupa przechwytywania ma nazwę domyślną, która jest identyczna z numerem porządkowym. Aby uzyskać więcej informacji, zobacz [nazwane dopasowane podwyrażenia](#named_matched_subexpression) w dalszej części tego tematu.  
  
- Przy użyciu `$` sekwencji zastępczej *liczb* w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołaniu metody lub, gdzie *Number* jest numerem porządkowym przechwyconego podwyrażenia.  
  
- Programowo, przy użyciu <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość. Element członkowski na pozycji zero w kolekcji reprezentuje całe dopasowanie wyrażenia regularnego. Każdy kolejny element członkowski reprezentuje Dopasowane Podwyrażenie. Aby uzyskać więcej informacji, zobacz sekcję [konstrukcje grupujące i obiekty wyrażeń regularnych](#Objects) .  
  
 Poniższy przykład ilustruje wyrażenie regularne, które identyfikuje duplikaty wyrazów w tekście. Dwie grupy przechwytywania wzorca wyrażenia regularnego reprezentują dwa wystąpienia zduplikowanego wyrazu. Drugie wystąpienie jest przechwytywane, aby zgłosić jego pozycję początkową w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
`(\w+)\s(\1)\W`  
  
 W poniższej tabeli przedstawiono sposób interpretowania wzorca wyrażenia regularnego.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\1)`|Dopasowuje ciąg w pierwszej przechwyconej grupie. Jest to druga grupa przechwytywania. Przykład przypisuje go do przechwyconej grupy, aby można było pobrać początkową pozycję zduplikowanego słowa z `Match.Index` właściwości.|  
|`\W`|Dopasowuje znak niebędący słowem, w tym odstępy i znaki interpunkcyjne. Zapobiega to, aby wzorzec wyrażenia regularnego był zgodny z wyrazem rozpoczynającym się od pierwszej przechwyconej grupy.|  
  
<a name="named_matched_subexpression"></a>
## <a name="named-matched-subexpressions"></a>O nazwie dopasowane podwyrażenia  
 Następująca konstrukcja grupująca przechwytuje Dopasowane Podwyrażenie i umożliwia dostęp do niego według nazwy lub liczby:  
  
`(?<name>subexpression)`  
  
 lub:  
  
`(?'name'subexpression)`  
  
 gdzie *name* jest prawidłową nazwą grupy, a *subexpression* jest dowolnym prawidłowym wzorcem wyrażenia regularnego. *Nazwa* nie może zawierać żadnych znaków interpunkcyjnych i nie może rozpoczynać się od cyfry.  
  
> [!NOTE]
> Jeśli <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowania do wzorca wyrażenia regularnego zawiera <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagę lub jeśli `n` opcja jest stosowana do tego podwyrażenia (zobacz [Opcje grupy](#group_options) w dalszej części tego tematu), jedynym sposobem przechwycenia podwyrażenia jest jawne nazwa przechwytywania grup.  
  
 Można uzyskać dostęp do nazwanych przechwyconych grup w następujący sposób:  
  
- Za pomocą nazwanej konstrukcji odwołania wstecznego w wyrażeniu regularnym. Dopasowane Podwyrażenie jest przywoływane w tym samym wyrażeniu regularnym przy użyciu `\k<` *nazwy*składni `>` , gdzie *name* to nazwa przechwyconego podwyrażenia.  
  
- Za pomocą konstrukcji odwołania wstecznego w wyrażeniu regularnym. Dopasowane Podwyrażenie jest przywoływane w tym samym wyrażeniu regularnym przy użyciu `\` *numeru*składni, gdzie *Number* jest numerem porządkowym przechwyconego podwyrażenia. Nazwane dopasowane podwyrażenia są numerowane kolejno od lewej do prawej po dopasowaniu podwyrażeń.  
  
- Przy użyciu `${` *name* `}` kolejności zamieniania nazw w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołaniu metody lub, gdzie *name* jest nazwą przechwyconego podwyrażenia.  
  
- Przy użyciu `$` sekwencji zastępczej *liczb* w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołaniu metody lub, gdzie *Number* jest numerem porządkowym przechwyconego podwyrażenia.  
  
- Programowo, przy użyciu <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość. Element członkowski na pozycji zero w kolekcji reprezentuje całe dopasowanie wyrażenia regularnego. Każdy kolejny element członkowski reprezentuje Dopasowane Podwyrażenie. Nazwane przechwycone grupy są przechowywane w kolekcji po numerowanych przechwyconych grupach.  
  
- Programowo, dostarczając nazwę podwyrażenia do <xref:System.Text.RegularExpressions.GroupCollection> indeksatora obiektu (w języku C#) lub do jego <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwości (w Visual Basic).  
  
 Prosty wzorzec wyrażenia regularnego ilustruje, jak numerowane (nienazwane) i nazwane grupy mogą być przywoływane programowo lub za pomocą składni języka wyrażenia regularnego. Wyrażenie regularne `((?<One>abc)\d+)?(?<Two>xyz)(.*)` generuje następujące grupy przechwytywania według liczby i według nazwy. Pierwsza grupa przechwytywania (numer 0) zawsze odwołuje się do całego wzorca.  
  
|Liczba|Nazwa|Wzorce|  
|------------|----------|-------------|  
|0|0 (nazwa domyślna)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (nazwa domyślna)|`((?<One>abc)\d+)`|  
|2|2 (nazwa domyślna)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Dwa|`(?<Two>xyz)`|  
  
 Poniższy przykład ilustruje wyrażenie regularne, które identyfikuje zduplikowane wyrazy i słowo, które bezpośrednio następuje po każdym zduplikowanym wyrazie. Wzorzec wyrażenia regularnego definiuje dwa nazwane Podwyrażenie: `duplicateWord` , które reprezentuje duplikat wyrazu, i `nextWord` , który reprezentuje wyraz, który następuje po zduplikowanym wyrazie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
`(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)`  
  
 W poniższej tabeli przedstawiono sposób interpretowania wyrażenia regularnego.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nadaj nazwę tej grupie przechwytywania `duplicateWord` .|  
|`\s`|Dopasowuje znak odstępu.|  
|`\k<duplicateWord>`|Dopasowuje ciąg z przechwyconej grupy o nazwie `duplicateWord` .|  
|`\W`|Dopasowuje znak niebędący słowem, w tym odstępy i znaki interpunkcyjne. Zapobiega to, aby wzorzec wyrażenia regularnego był zgodny z wyrazem rozpoczynającym się od pierwszej przechwyconej grupy.|  
|`(?<nextWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Nadaj nazwę tej grupie przechwytywania `nextWord` .|  
  
 Należy zauważyć, że nazwa grupy może być powtórzona w wyrażeniu regularnym. Na przykład można mieć więcej niż jedną grupę `digit` , jak pokazano w poniższym przykładzie. W przypadku zduplikowanych nazw wartość <xref:System.Text.RegularExpressions.Group> obiektu zależy od ostatniego pomyślnego przechwycenia w ciągu wejściowym. Ponadto <xref:System.Text.RegularExpressions.CaptureCollection> jest wypełniany informacjami o każdym przechwytywaniu, tak jak gdyby nazwa grupy nie była duplikatem.  
  
 W poniższym przykładzie wyrażenie regularne `\D+(?<digit>\d+)\D+(?<digit>\d+)?` zawiera dwa wystąpienia grupy o nazwie `digit` . Pierwsza `digit` nazwana grupa przechwytuje co najmniej jeden znak cyfr. Druga `digit` nazwana grupa przechwytuje zero lub jedno wystąpienie co najmniej jednego znaku cyfry. Jako dane wyjściowe z przykładu pokazują, jeśli druga grupa przechwytywania pomyślnie dopasowuje tekst, wartość tego tekstu definiuje wartość <xref:System.Text.RegularExpressions.Group> obiektu. Jeśli druga grupa przechwytywania nie może być zgodna z ciągiem wejściowym, wartość ostatniego pomyślnego dopasowania definiuje wartość <xref:System.Text.RegularExpressions.Group> obiektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 W poniższej tabeli przedstawiono sposób interpretowania wyrażenia regularnego.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\D+`|Dopasowuje co najmniej jeden znak niebędący cyfrą dziesiętną.|  
|`(?<digit>\d+)`|Dopasowuje jeden lub więcej cyfr dziesiętnych. Przypisz dopasowanie do `digit` nazwanej grupy.|  
|`\D+`|Dopasowuje co najmniej jeden znak niebędący cyfrą dziesiętną.|  
|`(?<digit>\d+)?`|Dopasowanie do zera lub jednego wystąpienia co najmniej jednego znaku cyfry dziesiętnej. Przypisz dopasowanie do `digit` nazwanej grupy.|  
  
<a name="balancing_group_definition"></a>
## <a name="balancing-group-definitions"></a>Równoważenie definicji grup  
 Definicja grupy równoważenia usuwa definicję wcześniej zdefiniowanej grupy i magazynów w bieżącej grupie, interwał między wcześniej zdefiniowaną grupą a bieżącą grupą. Ta konstrukcja grupująca ma następujący format:  
  
`(?<name1-name2>subexpression)`  
  
 lub:  
  
`(?'name1-name2' subexpression)`
  
 gdzie *Name1* jest bieżącą grupą (opcjonalnie), *NAME2* jest wcześniej zdefiniowaną grupą i *podwyrażeniem* jest dowolnym prawidłowym wzorcem wyrażenia regularnego. Definicja grupy równoważenia usuwa definicję *NAME2* i przechowuje interwał między *NAME2* i *Name1* w *Name1*. Jeśli nie zdefiniowano żadnej grupy *NAME2* , dopasowanie wsteczne. Ponieważ usunięcie ostatniej definicji elementu *NAME2* ujawnia poprzednią definicję *NAME2*, konstrukcja ta umożliwia użycie stosu przechwytywania dla grupy *NAME2* jako licznika do śledzenia zagnieżdżonych konstrukcji, takich jak nawiasy lub otwierające i zamykające nawiasy.  
  
 Definicja grupy równoważenia używa *NAME2* jako stosu. Początkowy znak każdej zagnieżdżonej konstrukcji jest umieszczany w grupie i w swojej <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji. Po dopasowaniu znaku zamykającego jego odpowiedni znak otwierający jest usuwany z grupy, a <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekcja zostanie zmniejszona o jeden. Po dopasowaniu i zamykaniu znaków wszystkich zagnieżdżonych konstrukcji *NAME2* jest puste.  
  
> [!NOTE]
> Po zmodyfikowaniu wyrażenia regularnego w poniższym przykładzie, aby użyć odpowiedniego otwierającego i zamykającego znaku zagnieżdżonej konstrukcji, można użyć go do obsługi większości zagnieżdżonych konstrukcji, takich jak wyrażenia matematyczne lub wiersze kodu programu, które zawierają wiele wywołań metod zagnieżdżonych.  
  
 W poniższym przykładzie użyta zostanie definicja grupy równoważenia do dopasowania do lewego i prawego nawiasu ostrego (<>) w ciągu wejściowym. W przykładzie zdefiniowano dwie nazwane grupy `Open` , `Close` które są używane jak stos do śledzenia dopasowania par nawiasów ostrych. Każdy przechwycony lewy nawias kątowy jest wypychany do kolekcji przechwytywania `Open` grupy, a każdy przechwycony prawy nawias kątowy jest wypychany do kolekcji przechwytywania `Close` grupy. Definicja grupy równoważenia gwarantuje, że istnieje pasujący prawy nawias kątowy dla każdego lewego nawiasu kątowego. Jeśli nie istnieje, ostateczny podwzorzec, `(?(Open)(?!))` ,, jest oceniany tylko wtedy, gdy `Open` Grupa nie jest pusta (i dlatego, jeśli wszystkie zagnieżdżone konstrukcje nie zostały zamknięte). Jeśli ostateczny wzorzec jest szacowany, dopasowanie nie powiedzie się, ponieważ `(?!)` podwzorzec jest nieprawidłowym pomyślnym wyprzedzeniem o zerowej szerokości, które zawsze kończy się niepowodzeniem.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Wzorzec wyrażenia regularnego:  
  
`^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$`  
  
 Wyrażenie regularne jest interpretowane w następujący sposób:  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Zacznij od początku ciągu.|  
|`[^<>]*`|Dopasowuje zero lub więcej znaków, które nie są w lewo lub w prawo.|  
|`(?'Open'<)`|Dopasowuje lewy nawias ostry i przypisuje go do grupy o nazwie `Open` .|  
|`[^<>]*`|Dopasowuje zero lub więcej znaków, które nie są w lewo lub w prawo.|  
|`((?'Open'<)[^<>]*)+`|Dopasowuje co najmniej jedno wystąpienie lewego nawiasu kątowego, po którym następuje zero lub więcej znaków, które nie są w lewo lub w prawo. Jest to druga grupa przechwytywania.|  
|`(?'Close-Open'>)`|Dopasowuje prawy nawias kątowy, przypisz podciąg między `Open` grupą i bieżącą grupą do `Close` grupy, a następnie usuń definicję `Open` grupy.|  
|`[^<>]*`|Dopasowuje zero lub więcej wystąpień dowolnego znaku, który nie jest lewym ani prawym nawiasem ostrym.|  
|`((?'Close-Open'>)[^<>]*)+`|Dopasowuje jedno lub więcej wystąpień prawego nawiasu ostrego, po którym następuje zero lub więcej wystąpień dowolnego znaku, który nie jest lewym ani prawym nawiasem ostrym. W przypadku dopasowania do prawego nawiasu ostrego Przypisz podciąg między `Open` grupą i bieżącą grupą do `Close` grupy, a następnie usuń definicję `Open` grupy. Jest to trzecia grupa przechwytywania.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Dopasowanie do zera lub większej liczby wystąpień następującego wzorca: co najmniej jedno wystąpienie lewego nawiasu kątowego, po którym następuje zero lub więcej znaków nieostrych, po którym następuje jedno lub więcej wystąpień prawego nawiasu ostrego, po którym następuje zero lub więcej wystąpień nieostrych nawiasów. W przypadku dopasowania do prawego nawiasu ostrego usuń definicję `Open` grupy i przypisz podciąg między `Open` grupą a bieżącą grupą do `Close` grupy. Jest to pierwsza grupa przechwytywania.|  
|`(?(Open)(?!))`|Jeśli `Open` Grupa istnieje, Porzuć dopasowanie, jeśli ciąg pusty można dopasować, ale nie przesuwaj pozycji aparatu wyrażeń regularnych w ciągu. Jest to nieujemne potwierdzenie o zerowej szerokości. Ponieważ pusty ciąg jest zawsze niejawnie obecny w ciągu wejściowym, to dopasowanie zawsze kończy się niepowodzeniem. Niepowodzenie tego dopasowania wskazuje, że nawiasy kątowe nie są zrównoważone.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Ostateczne Podwyrażenie, `(?(Open)(?!))` , wskazuje, czy konstrukcje zagnieżdżania w ciągu wejściowym są prawidłowo zrównoważone (na przykład czy każdy lewy nawias kątowy jest dopasowywany przez prawy nawias kątowy). Używa dopasowania warunkowego opartego na prawidłowej przechwyconej grupie; Aby uzyskać więcej informacji, zobacz [konstrukcje warunkowe](alternation-constructs-in-regular-expressions.md). Jeśli `Open` Grupa jest zdefiniowana, aparat wyrażeń regularnych próbuje dopasować Podwyrażenie `(?!)` w ciągu wejściowym. `Open`Grupę należy zdefiniować tylko wtedy, gdy konstrukcje zagnieżdżania są niezrównoważone. W związku z tym wzorzec, który ma zostać dopasowany w ciągu wejściowym powinien być taki, który zawsze powoduje niepowodzenie dopasowania. W tym przypadku jest to bezwzględne, `(?!)` negatywne potwierdzenie o zerowej szerokości, które zawsze kończy się niepowodzeniem, ponieważ pusty ciąg jest zawsze niejawnie obecny na następnej pozycji w ciągu wejściowym.  
  
 W przykładzie aparat wyrażeń regularnych szacuje ciąg wejściowy " \<abc><mno \<xyz>>", jak pokazano w poniższej tabeli.  
  
|Krok|Wzorce|Wynik|  
|----------|-------------|------------|  
|1|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego|  
|2|`[^<>]*`|Wyszukuje znaki niebędące nawiasami ostrymi przed lewym nawiasem ostrym; znajduje brak dopasowań.|  
|3|`(((?'Open'<)`|Dopasowuje lewy nawias ostry w " \<abc> " i przypisuje go do `Open` grupy.|  
|4|`[^<>]*`|Pasuje do "ABC".|  
|5|`)+`|"<ABC" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem ostrym, dlatego aparat wyrażeń regularnych nie jest odtwarzany z powrotem do `(?'Open'<)[^<>]*)` wzorca.|  
|6|`((?'Close-Open'>)`|Dopasowuje prawy nawias kątowy w " \<abc> ", przypisuje "ABC", który jest podciągiem między `Open` grupą i prawego nawiasu ostrego, do `Close` grupy i usuwa bieżącą wartość ("<") `Open` grupy, pozostawiając ją pustą.|  
|7|`[^<>]*`|Wyszukuje znaki niebędące nawiasami ostrymi po prawym nawiasie ostrym; nie znaleziono żadnych dopasowań.|  
|8|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawym nawiasem ostrym, więc aparat wyrażeń regularnych nie jest w pętli z powrotem do `((?'Close-Open'>)[^<>]*)` wzorca.|  
|9|`)*`|Wartość pierwszej przechwyconej grupy to " \<abc> ".<br /><br /> Następny znak w ciągu wejściowym jest lewym nawiasem ostrym, dlatego aparat wyrażeń regularnych jest odtwarzany z powrotem do `(((?'Open'<)` wzorca.|  
|10|`(((?'Open'<)`|Dopasowuje lewy nawias kątowy w polu " \<mno" and assigns it to the `Open` group. Its <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Kolekcja ma teraz pojedynczą wartość" < ".|  
|11|`[^<>]*`|Pasuje do "MNO".|  
|12|`)+`|"<MNO" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym jest lewym nawiasem ostrym, dlatego aparat wyrażeń regularnych jest odtwarzany z powrotem do `(?'Open'<)[^<>]*)` wzorca.|  
|13|`(((?'Open'<)`|Dopasowuje lewy nawias ostry w " \<xyz> " i przypisuje go do `Open` grupy. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>Kolekcja `Open` grup zawiera teraz dwa przechwycenia: lewy nawias kątowy od " \<mno", and the left angle bracket from "\<xyz> ".|  
|14|`[^<>]*`|Dopasowuje "XYZ".|  
|15|`)+`|"<XYZ" to wartość drugiej przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem ostrym, dlatego aparat wyrażeń regularnych nie jest odtwarzany z powrotem do `(?'Open'<)[^<>]*)` wzorca.|  
|16|`((?'Close-Open'>)`|Dopasowuje prawy nawias kątowy w " \<xyz> ". "XYZ", przypisuje podciąg między `Open` grupą i prawego nawiasu ostrego do `Close` grupy, a następnie usuwa bieżącą wartość `Open` grupy. Wartość poprzedniego przechwytywania (lewy nawias kątowy w \<mno") becomes the current value of the `Open` group. The <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekcji `Open` grupy zawiera teraz pojedyncze przechwytywanie, lewy nawias ostry od " \<xyz> ".|  
|17|`[^<>]*`|Wyszukuje znaki niebędące nawiasami ostrymi; nie znaleziono żadnych dopasowań.|  
|18|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym jest prawym nawiasem kątowym, więc aparat wyrażeń regularnych jest odtwarzany z powrotem do `((?'Close-Open'>)[^<>]*)` wzorca.|  
|19|`((?'Close-Open'>)`|Dopasowuje do ostatniego zamykającego nawiasu ostrego w "XYZ>>" przypisuje "MNO \<xyz> " (podciąg między `Open` grupą i prawego nawiasu ostrego) do `Close` grupy i usuwa bieżącą wartość `Open` grupy. `Open`Grupa jest teraz pusta.|  
|20|`[^<>]*`|Wyszukuje znaki niebędące nawiasami ostrymi; nie znaleziono żadnych dopasowań.|  
|21|`)+`|Wartość trzeciej przechwyconej grupy to ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawym nawiasem ostrym, więc aparat wyrażeń regularnych nie jest w pętli z powrotem do `((?'Close-Open'>)[^<>]*)` wzorca.|  
|22|`)*`|Wartość pierwszej przechwyconej grupy to "<MNO \<xyz>>".<br /><br /> Następny znak w ciągu wejściowym nie jest nawiasem ostrym, dlatego aparat wyrażeń regularnych nie jest odtwarzany z powrotem do `(((?'Open'<)` wzorca.|  
|23|`(?(Open)(?!))`|`Open`Grupa nie jest zdefiniowana, więc nie podjęto żadnego dopasowania.|  
|24|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
<a name="noncapturing_group"></a>
## <a name="noncapturing-groups"></a>Grupy niezapamiętywane  
 Następująca konstrukcja grupująca nie przechwytuje podciągu, który jest dopasowany przez Podwyrażenie:  
  
`(?:subexpression)`
  
 gdzie *subexpression* jest dowolnym prawidłowym wzorcem wyrażenia regularnego. Konstrukcja grupy nieprzechwyconej jest zwykle używana w przypadku zastosowania kwantyfikatora do grupy, ale podciągi przechwycone przez grupę nie są przedmiotem zainteresowania.  
  
> [!NOTE]
> Jeśli wyrażenie regularne zawiera zagnieżdżone konstrukcje grupowania, zewnętrzna konstrukcja grupy nieprzechwytującej nie ma zastosowania do wewnętrznych zagnieżdżonych konstrukcji grupowych.  
  
 Poniższy przykład ilustruje wyrażenie regularne, które zawiera grupy nieprzechwytywania. Należy zauważyć, że dane wyjściowe nie obejmują żadnych przechwyconych grup.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Wyrażenie regularne `(?:\b(?:\w+)\W*)+\.` dopasowuje zdanie, które zostało zakończone przez okres. Ponieważ wyrażenie regularne koncentruje się na zdaniach, a nie na pojedynczych słowach, konstrukcje grupujące są używane wyłącznie jako Kwantyfikatory. Wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?:\w+)`|Dopasowuje co najmniej jeden znak słowa. Nie przypisuj dopasowanego tekstu do przechwyconej grupy.|  
|`\W*`|Dopasowuje zero lub więcej znaków niebędących wyrazami.|  
|`(?:\b(?:\w+)\W*)+`|Dopasowuje wzorzec jednego lub więcej znaków słowa, zaczynając od granicy słowa, po którym następuje zero lub więcej znaków niebędących wyrazami (jeden lub więcej razy). Nie przypisuj dopasowanego tekstu do przechwyconej grupy.|  
|`\.`|Dopasowuje okres.|  
  
<a name="group_options"></a>
## <a name="group-options"></a>Opcje grupy  
 Następująca konstrukcja grupująca stosuje lub wyłącza określone opcje w ramach podwyrażenia:  
  
 `(?imnsx-imnsx:`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym prawidłowym wzorcem wyrażenia regularnego. Na przykład `(?i-s:)` włącza opcję nierozróżniania wielkości liter i wyłącza tryb jednowierszowy. Aby uzyskać więcej informacji na temat opcji wbudowanych, które można określić, zobacz [Opcje wyrażenia regularnego](regular-expression-options.md).  
  
> [!NOTE]
> Można określić opcje, które mają zastosowanie do całego wyrażenia regularnego, a nie podwyrażenia przy użyciu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub metody statycznej. Można również określić opcje wbudowane, które są stosowane po określonym punkcie w wyrażeniu regularnym, za pomocą `(?imnsx-imnsx)` konstrukcji języka.  
  
 Konstrukcja opcji grupy nie jest grupą przechwytywania. Oznacza to, że mimo że jakakolwiek część ciągu, który jest przechwytywany przez *Podwyrażenie* jest uwzględniona w dopasowaniu, nie jest uwzględniona w przechwyconej grupie ani użyta do wypełnienia <xref:System.Text.RegularExpressions.GroupCollection> obiektu.  
  
 Na przykład w wyrażeniu regularnym `\b(?ix: d \w+)\s` w poniższym przykładzie są używane opcje wbudowane w konstrukcji grupującej, aby umożliwić dopasowanie bez uwzględniania wielkości liter i ignorowanie odstępu wzorca w przypadku identyfikowania wszystkich słów zaczynających się od litery "d". Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?ix: d \w+)`|Przy użyciu dopasowania bez uwzględniania wielkości liter i ignorowania białego znaku w tym wzorcu dopasowuje znak "d", po którym następuje jeden lub więcej znaków wyrazu.|  
|`\s`|Dopasowuje znak odstępu.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>
## <a name="zero-width-positive-lookahead-assertions"></a>Dodatnie asercje z patrzeniem w przód o zerowej szerokości  
 Następująca konstrukcja grupująca definiuje pozytywne potwierdzenie o zerowej szerokości:  
  
 `(?=`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, ciąg wejściowy musi być zgodny ze wzorcem wyrażenia regularnego w *podrażeniu*, chociaż dopasowany podciąg nie jest uwzględniony w wyniku dopasowania. Potwierdzenie o zerowej szerokości nie nawrotu.  
  
 Zazwyczaj na końcu wzorca wyrażenia regularnego zostanie znalezione pozytywne potwierdzenie o zerowej szerokości. Definiuje podciąg, który musi zostać znaleziony na końcu ciągu, aby nastąpiło dopasowanie, ale nie powinien być uwzględniony w dopasowaniu. Jest on również przydatny do zapobiegania nadmiernemu wycofywaniu. Możesz użyć pozytywnego potwierdzenia naprzódgo o zerowej szerokości, aby upewnić się, że określona przechwycona Grupa rozpoczyna się od tekstu, który jest zgodny z podzbiorem wzorca zdefiniowanego dla tej przechwyconej grupy. Na przykład, jeśli grupa przechwytywania dopasowuje kolejne znaki wyrazu, można użyć pozytywnej wartości zerowej z wyprzedzeniem, aby wymagać, aby pierwszy znak był wielką literą.  
  
 W poniższym przykładzie zastosowano dodatnie potwierdzenie o zerowej szerokości, aby dopasować wyraz poprzedzający zlecenie "is" w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Wyrażenie regularne `\b\w+(?=\sis\b)` jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(?=\sis\b)`|Ustal, czy znaki słowa są poprzedzone znakiem odstępu, a ciąg "is", który jest kończący się na granicy słowa. Jeśli tak, dopasowanie zostanie wykonane pomyślnie.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>
## <a name="zero-width-negative-lookahead-assertions"></a>Ujemne asercje z patrzeniem w przód o zerowej szerokości  
 Następująca konstrukcja grupująca definiuje negatywną Poprzednia wartość zerowej szerokości:  
  
 `(?!`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, ciąg wejściowy nie może być zgodny ze wzorcem wyrażenia regularnego w *podrażeniu*, chociaż dopasowany ciąg nie jest uwzględniony w wyniku dopasowania.  
  
 Potwierdzenie negatywnej zerowej szerokości jest zwykle używane na początku lub na końcu wyrażenia regularnego. Na początku wyrażenia regularnego można zdefiniować konkretny wzorzec, który nie powinien być dopasowany, gdy początek wyrażenia regularnego definiuje podobny, ale bardziej ogólny wzorzec do dopasowania. W takim przypadku jest często używany do ograniczania wycofywania. Na końcu wyrażenia regularnego można zdefiniować Podwyrażenie, które nie może wystąpić na końcu dopasowania.  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które używa potwierdzenia przeszukiwania zerowej szerokości na początku wyrażenia regularnego w celu dopasowania wyrazów, które nie zaczynają się od "un".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Wyrażenie regularne `\b(?!un)\w+\b` jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?!un)`|Ustal, czy dwa następne znaki są "un". Jeśli tak nie jest, możliwe jest dopasowanie.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, które używa potwierdzenia przeszukiwania zerowej szerokości na końcu wyrażenia regularnego, aby dopasować wyrazy, które nie kończą się znakiem interpunkcji.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Wyrażenie regularne `\b\w+\b(?!\p{P})` jest interpretowane jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
|`\p{P})`|Jeśli następny znak nie jest symbolem interpunkcji (na przykład kropką lub przecinkiem), dopasowanie powiedzie się.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>
## <a name="zero-width-positive-lookbehind-assertions"></a>Dodatnie asercje wsteczne o zerowej szerokości  
 Następująca konstrukcja grupująca definiuje asercja wsteczna pozytywnej o zerowej szerokości:  
  
 `(?<=`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie powiodło się, *Podwyrażenie* musi wystąpić w ciągu wejściowym z lewej strony bieżącego położenia, chociaż `subexpression` nie jest uwzględnione w wyniku dopasowania. Pozytywna asercja wstecznaa o zerowej szerokości nie nawrotu.  
  
 Pozytywne potwierdzenia asercja wsteczna o zerowej szerokości są zwykle używane na początku wyrażeń regularnych. Wzorzec, który definiuje, jest warunkiem wstępnym dla dopasowania, chociaż nie jest częścią wyniku dopasowania.  
  
 Na przykład poniższy przykład dopasowuje ostatnie dwie cyfry roku dla dwudziestego pierwszego stulecia (czyli wymaga, aby cyfry "20" poprzedzać pasujący ciąg).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Wzorzec wyrażenia regularnego `(?<=\b20)\d{2}\b` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`(?<=\b20)`|Kontynuuj dopasowanie, jeśli dwie cyfry dziesiętne poprzedzają cyfry dziesiętne "20" na granicy wyrazu.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Pozytywne potwierdzenia asercja wsteczna o zerowej szerokości są również używane do ograniczania wycofywania, gdy ostatni znak lub znaki w przechwyconej grupie muszą być podzbiorem znaków, które pasują do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie kolejne znaki wyrazu, można użyć pozytywnej asercja wsteczna o zerowej szerokości, aby wymagać, aby ostatni znak był alfabetyczny.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>
## <a name="zero-width-negative-lookbehind-assertions"></a>Ujemne asercje wsteczne o zerowej szerokości  
 Następująca konstrukcja grupująca definiuje negatywną asercja wstecznaą o zerowej szerokości:  
  
 `(?<!`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym wzorcem wyrażenia regularnego. Aby dopasowanie zakończyło się pomyślnie, *Podwyrażenie* nie może wystąpić w ciągu wejściowym z lewej strony bieżącego położenia. Jednak dowolny podciąg, który nie jest zgodny, `subexpression` nie jest uwzględniony w wyniku dopasowania.  
  
 Ujemne asercja wstecznay o zerowej szerokości są zwykle używane na początku wyrażeń regularnych. Zdefiniowany przez siebie wzorzec wyklucza dopasowanie w ciągu poniżej. Są one również używane do ograniczania wycofywania, gdy ostatni znak lub znaki w przechwyconej grupie nie mogą być jednym lub więcej znaków, które pasują do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie kolejne znaki wyrazu, można użyć pozytywnej asercja wsteczna o zerowej szerokości, aby wymagać, aby ostatni znak nie był podkreśleniem ( \_ ).  
  
 Poniższy przykład dopasowuje datę dla każdego dnia tygodnia, który nie jest weekendem (czyli nie jest to sobota ani Niedziela).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Wzorzec wyrażenia regularnego `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` jest interpretowany jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje jeden lub więcej znaków wyrazu, po którym następuje znak odstępu.|  
|`\d{1,2},`|Dopasowuje jedną lub dwie cyfry dziesiętne, po których następuje znak odstępu i przecinek.|  
|`\d{4}\b`|Dopasowuje cztery cyfry dziesiętne i kończy dopasowanie na granicy wyrazu.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Jeśli dopasowanie jest poprzedzone znakiem innym niż ciągi "Sobota" lub "Niedziela", po którym następuje spacja, dopasowanie zostanie wykonane pomyślnie.|  
  
<a name="atomic_groups"></a>
## <a name="atomic-groups"></a>Grupy niepodzielne  
 Następująca konstrukcja grupująca reprezentuje niepodzielną grupę (znaną w innych aparatach wyrażeń regularnych jako Podwyrażenie Podwyrażenie, dwuwyrażenie cząstkowe lub Podwyrażenie tylko raz):
  
 `(?>`*Podwyrażenie*`)`  
  
 gdzie *subexpression* jest dowolnym wzorcem wyrażenia regularnego.  
  
 Zwykle Jeśli wyrażenie regularne zawiera opcjonalny lub alternatywny wzorzec dopasowywania, a dopasowanie nie powiedzie się, aparat wyrażeń regularnych może rozgałęziać się w wielu kierunkach, aby dopasować ciąg wejściowy do wzorca. Jeśli dopasowanie nie zostanie znalezione podczas pierwszego rozgałęzienia, aparat wyrażeń regularnych może utworzyć kopię zapasową lub nawrotu do punktu, w którym zajęło pierwsze dopasowanie, i spróbować dopasować przy użyciu drugiego rozgałęzienia. Ten proces może być kontynuowany, dopóki nie zostaną wypróbowane wszystkie gałęzie.  
  
 `(?>`Konstrukcja języka *subexpression* `)` powoduje wyłączenie wycofywania. Aparat wyrażeń regularnych będzie pasował do tylu znaków w ciągu wejściowym, jak to możliwe. Gdy nie jest możliwe dalsze dopasowanie, nie będzie nawrotu prób alternatywnej dopasowania wzorca. (Oznacza to, że Podwyrażenie dopasowuje tylko ciągi, które byłyby dopasowane tylko przez Podwyrażenie; nie próbuje dopasować ciągu w oparciu o Podwyrażenie i wszystkie Podwyrażenie, które je obserwują).  
  
 Ta opcja jest zalecana, Jeśli wiesz, że wycofywanie nie powiedzie się. Uniemożliwianie aparatowi wyrażeń regularnych wykonywanie niepotrzebnych operacji wyszukiwania poprawia wydajność.  
  
 Poniższy przykład ilustruje, jak niepodzielna Grupa modyfikuje wyniki dopasowania do wzorca. Wyrażenie regularne śledzenia wstecznego pomyślnie dopasowuje serię powtarzających się znaków, a po nim wystąpienie tego samego znaku na granicy wyrazu, ale wyrażenie regularne Podwyrażenie nie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Wyrażenie regularne Podwyrażenie `(?>(\w)\1+).\b` jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasowuje pojedynczy znak słowa i przypisuje go do pierwszej grupy przechwytywania.|  
|`\1+`|Dopasowuje wartość pierwszego przechwyconego podciągu jeden lub więcej razy.|  
|`.`|Dopasowuje dowolny znak.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
|`(?>(\w)\1+)`|Dopasowuje jedno lub więcej wystąpień zduplikowanego znaku słowa, ale nie nawrotu się w celu dopasowania do ostatniego znaku na granicy słowa.|  
  
<a name="Objects"></a>
## <a name="grouping-constructs-and-regular-expression-objects"></a>Konstrukty grupujące i obiekty wyrażeń regularnych  
 Podciągi dopasowane przez grupę przechwyconą wyrażenia regularnego są reprezentowane przez <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> obiekty, które można pobrać z obiektu, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> który jest zwracany przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość. <xref:System.Text.RegularExpressions.GroupCollection>Obiekt jest wypełniany w następujący sposób:  
  
- Pierwszy <xref:System.Text.RegularExpressions.Group> obiekt w kolekcji (obiekt pod indeksem zero) reprezentuje całe dopasowanie.  
  
- Następny zestaw <xref:System.Text.RegularExpressions.Group> obiektów reprezentuje grupy przechwytywania bez nazwy. Są one wyświetlane w kolejności, w jakiej są zdefiniowane w wyrażeniu regularnym od lewej do prawej. Wartości indeksu tych grup należą do zakresu od 1 do liczby nienazwanych grup przechwytywania w kolekcji. (Indeks określonej grupy jest równoznaczny z numerowanym odwołaniem wstecznym. Aby uzyskać więcej informacji na temat odwołań wstecznych, zobacz [konstrukcje odwołań wstecznych](backreference-constructs-in-regular-expressions.md).)  
  
- Końcowy zestaw <xref:System.Text.RegularExpressions.Group> obiektów reprezentuje nazwane grupy przechwytywania. Są one wyświetlane w kolejności, w jakiej są zdefiniowane w wyrażeniu regularnym od lewej do prawej. Wartość indeksu pierwszej nazwanej grupy przechwytywania jest większa niż indeks ostatniej nienazwanej grupy przechwytywania. Jeśli w wyrażeniu regularnym nie ma grup przechwytywania bez nazwy, wartość indeksu pierwszej nazwanej grupy przechwytywania to jeden.  
  
 W przypadku zastosowania kwantyfikatora do grupy przechwytywania odpowiednie <xref:System.Text.RegularExpressions.Group> obiekty <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> , <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> Właściwości odzwierciedlają ostatni podciąg, który jest przechwytywany przez grupę przechwytywania. Można pobrać kompletny zestaw podciągów, które są przechwytywane przez grupy, które mają Kwantyfikatory z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Właściwość.  
  
 W poniższym przykładzie wyjaśniono relację między <xref:System.Text.RegularExpressions.Group> obiektami i <xref:System.Text.RegularExpressions.Capture> .  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Wzorzec wyrażenia regularnego `(\b(\w+)\W+)+` wyodrębnia poszczególne wyrazy z ciągu. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Razem te znaki tworzą słowo. Jest to druga grupa przechwytywania.|  
|`\W+`|Dopasowuje jeden lub więcej znaków niebędących wyrazami.|  
|`(\b(\w+)\W+)`|Dopasowuje wzorzec jednego lub więcej znaków słowa, po których następuje jeden lub więcej znaków niebędących wyrazami. Jest to pierwsza grupa przechwytywania.|  
  
 Druga grupa przechwytywania dopasowuje każdy wyraz zdania. Pierwsza grupa przechwytywania dopasowuje każdy wyraz wraz z interpunkcją i białym znakiem, który obserwuje wyraz. <xref:System.Text.RegularExpressions.Group>Obiekt, którego indeks jest 2, zawiera informacje dotyczące tekstu dopasowanego przez drugą grupę przechwytywania. Pełny zestaw wyrazów przechwytywanych przez grupę przechwytywania jest dostępny z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Właściwość.  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
- [Nawracanie](backtracking-in-regular-expressions.md)
