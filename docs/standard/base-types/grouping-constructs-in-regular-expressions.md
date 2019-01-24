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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aa7c35ebc06fb67d9cf6216233d2bed65ae76ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645902"
---
# <a name="grouping-constructs-in-regular-expressions"></a>Konstrukcje grupujące w wyrażeniach regularnych
Konstrukcje grupujące odróżnić podwyrażenia wyrażeń regularnych i przechwytywane podciągi ciągu wejściowego. Można użyć konstrukcji grupowania, wykonaj następujące czynności:  
  
-   Dopasowuje Wyrażenie cząstkowe powtarzające się w ciągu wejściowym.  
  
-   Zastosować kwantyfikator do podwyrażenia, który ma wiele elementów języka wyrażeń regularnych. Aby uzyskać więcej informacji na temat Kwantyfikatory zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Dołączyć ciąg, który jest zwracany przez wyrażenie cząstkowe <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody.  
  
-   Pobierz poszczególne podwyrażenia z <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości i przetwarzać je oddzielnie od dopasowany tekst jako całości.  
  
 W poniższej tabeli wymieniono konstrukcje grupujące obsługiwane przez aparat wyrażeń regularnych platformy .NET i wskazuje, czy są one przechwytywania lub nieprzechwytujące.  
  
|Konstrukcja grupująca|Przechwytywania lub niezapamiętywane|  
|------------------------|-------------------------------|  
|[Matched subexpressions](#matched_subexpression)|Przechwytywanie|  
|[O nazwie dopasowane podwyrażenia](#named_matched_subexpression)|Przechwytywanie|  
|[Równoważenie definicji grup](#balancing_group_definition)|Przechwytywanie|  
|[Grupy niezapamiętywane](#noncapturing_group)|Niezapamiętywane|  
|[Wyświetlone są opcje grupy](#group_options)|Niezapamiętywane|  
|[Potwierdzenia pozytywna asercja wyprzedzająca o zerowej szerokości](#zerowidth_positive_lookahead_assertion)|Niezapamiętywane|  
|[Potwierdzenia negatywna asercja wyprzedzająca o zerowej szerokości](#zerowidth_negative_lookahead_assertion)|Niezapamiętywane|  
|[Potwierdzenia dodatnie asercje wsteczne o zerowej szerokości](#zerowidth_positive_lookbehind_assertion)|Niezapamiętywane|  
|[Potwierdzenia negatywna asercja wsteczna o zerowej szerokości](#zerowidth_negative_lookbehind_assertion)|Niezapamiętywane|  
|[Podwyrażenia bez nawrotów](#nonbacktracking_subexpression)|Niezapamiętywane|  
  
 Aby uzyskać informacje na temat grup i model obiektów wyrażeń regularnych, zobacz [konstrukty grupujące i obiekty wyrażeń regularnych](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Dopasowane podwyrażenie  
 Następujące konstrukcja grupująca przechwytuje dopasowane Podwyrażenie:  
  
 `(` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest wzorzec dowolnym prawidłowym wyrażeniem regularnym. Rejestruje, że Użyj nawiasów są numerowane automatycznie od lewej do prawej, na podstawie kolejności nawiasów otwierających w wyrażeniu regularnym, zaczynając od jednego. Przechwytywanie, który wynosi zero numerowane jest tekst pasuje wzorzec całego wyrażenia regularnego.  
  
> [!NOTE]
>  Domyślnie `(` *Podwyrażenie* `)` element języka przechwytuje dopasowane Podwyrażenie. Ale w tym przypadku <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowania do wzorca wyrażenia regularnego zawiera <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagi, lub jeśli `n` opcja jest stosowana do tego podwyrażenia (zobacz [grupie Opcje](#group_options) w dalszej części tego tematu), dopasowane Podwyrażenie nie są przechwytywane.  
  
 Aby uzyskać dostęp przechwyconych grupach na cztery sposoby:  
  
-   Za pomocą dopasowywania wstecznego skonstruować w wyrażeniu regularnym. Dopasowane Podwyrażenie o której mowa w tym samym wyrażeniu regularnym przy użyciu składni `\` *numer*, gdzie *numer* jest numerem porządkowym przechwyconego podwyrażenia.  
  
-   Za pomocą nazwane dopasowanie wsteczne skonstruować w wyrażeniu regularnym. Dopasowane Podwyrażenie o której mowa w tym samym wyrażeniu regularnym przy użyciu składni `\k<` *nazwa*`>`, gdzie *nazwa* to nazwa grupy przechwytywania, lub `\k<` *numer*`>`, gdzie *numer* jest numerem porządkowym grupy przechwytywania. Grupa przechwytywania ma domyślną nazwę, która jest taka sama na odpowiadającą mu liczbę porządkową. Aby uzyskać więcej informacji, zobacz [o nazwie dopasowane podwyrażenia](#named_matched_subexpression) w dalszej części tego tematu.  
  
-   Za pomocą `$` *numer* sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *numer* jest numerem porządkowym przechwyconego podwyrażenia.  
  
-   Programowo, za pomocą <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. Element członkowski w pozycji zero w kolekcji reprezentuje dopasowanie całego wyrażenia regularnego. Każdy członek kolejnych reprezentuje dopasowane Podwyrażenie. Aby uzyskać więcej informacji, zobacz [Grouping Constructs i obiekty wyrażeń regularnych](#Objects) sekcji.  
  
 W poniższym przykładzie pokazano wyrażenie regularne, który identyfikuje zduplikowane wyrazy w tekście. Wzorzec wyrażenia regularnego dwie grupy przechwytywania reprezentują dwa wystąpienia zduplikowane programu word. Drugie wystąpienie ciągu są przechwytywane do zgłaszania jego pozycję początkową w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego jest następująca:  
  
```  
(\w+)\s(\1)\W  
```  
  
 W poniższej tabeli przedstawiono, jak wzorzec wyrażenia regularnego jest interpretowany.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\1)`|Pasuje do ciągu w pierwszej przechwyconej grupy. Jest to druga grupa przechwytywania. Przykład przypisuje go do przechwyconej grupy tak, że pozycja początkowa zduplikowane wyrazu mogą być pobierane z `Match.Index` właściwości.|  
|`\W`|Dopasowuje znak niebędące znakami słowa, w tym białych znaków i znaków interpunkcyjnych. Zapobiega to dopasowania wyrazu, który rozpoczyna się od słowa z pierwszej przechwyconej grupy wzorzec wyrażenia regularnego.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>O nazwie dopasowane podwyrażenia  
 Następujące konstrukcja grupująca przechwytuje dopasowane Podwyrażenie i pozwala uzyskiwać dostęp do według nazwy lub numeru:  
  
```  
(?<name>subexpression)  
```  
  
 lub:  
  
```  
(?'name'subexpression)  
```  
  
 gdzie *nazwa* jest nazwą prawidłowej grupy i *Podwyrażenie* jest wzorzec dowolnym prawidłowym wyrażeniem regularnym. *Nazwa* nie może zawierać żadnych znaków interpunkcyjnych i nie może zaczynać się liczbą.  
  
> [!NOTE]
>  Jeśli <xref:System.Text.RegularExpressions.RegexOptions> parametr metody dopasowania do wzorca wyrażenia regularnego zawiera <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagi, lub jeśli `n` opcja jest stosowana do tego podwyrażenia (zobacz [grupie Opcje](#group_options) w dalszej części tego tematu), tylko Aby Przechwyć Podwyrażenie należy jawnie nazwę grupy przechwytywania.  
  
 Nazwane przechwyconych grupach można uzyskać dostęp, w następujący sposób:  
  
-   Za pomocą nazwane dopasowanie wsteczne skonstruować w wyrażeniu regularnym. Dopasowane Podwyrażenie o której mowa w tym samym wyrażeniu regularnym przy użyciu składni `\k<` *nazwa*`>`, gdzie *nazwa* nazywa się przechwyconego podwyrażenia.  
  
-   Za pomocą dopasowywania wstecznego skonstruować w wyrażeniu regularnym. Dopasowane Podwyrażenie o której mowa w tym samym wyrażeniu regularnym przy użyciu składni `\` *numer*, gdzie *numer* jest numerem porządkowym przechwyconego podwyrażenia. O nazwie dopasowane podwyrażenia są numerowane kolejno od lewej do prawej po dopasowane podwyrażenia.  
  
-   Przy użyciu `${` *nazwa* `}` sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *nazwa* nazywa się przechwyconego podwyrażenia.  
  
-   Za pomocą `$` *numer* sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *numer* jest numerem porządkowym przechwyconego podwyrażenia.  
  
-   Programowo, za pomocą <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. Element członkowski w pozycji zero w kolekcji reprezentuje dopasowanie całego wyrażenia regularnego. Każdy członek kolejnych reprezentuje dopasowane Podwyrażenie. Nazwane przechwyconej grupy są przechowywane w kolekcji po numerowane przechwyconych grupach.  
  
-   Programowo, podając nazwę Podwyrażenie do <xref:System.Text.RegularExpressions.GroupCollection> indeksatora obiektu (w języku C#) lub jego <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwości (Visual Basic).  
  
 Wzorzec wyrażenia regularnego proste ilustruje sposób ponumerowane (bez nazwy) i nazwanych grup mogą być przywoływane programowo lub za pomocą składni języka wyrażeń regularnych. Wyrażenie regularne `((?<One>abc)\d+)?(?<Two>xyz)(.*)` generuje następujące przechwytywania grupy według numeru i według nazwy. Pierwsza grupa (liczba 0) przechwytywania zawsze odwołuje się do całego wzorca.  
  
|Wartość liczbowa|Nazwa|Wzorzec|  
|------------|----------|-------------|  
|0|0 (nazwa domyślna)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (domyślna nazwa)|`((?<One>abc)\d+)`|  
|2|2 (nazwa domyślna)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|Dwa|`(?<Two>xyz)`|  
  
 W poniższym przykładzie pokazano wyrażenie regularne, który identyfikuje zduplikowanych słów i word, który poprzedza każdy wyraz zduplikowane. Wzorzec wyrażenia regularnego definiuje dwa podwyrażenia o nazwie: `duplicateWord`, która reprezentuje zduplikowany word; i `nextWord`, która reprezentuje wyrazu, który następuje po zduplikowane programu word.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego jest następująca:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 W poniższej tabeli przedstawiono, jak wyrażenia regularnego jest interpretowany.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy przechwytywania `duplicateWord`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\k<duplicateWord>`|Pasuje do ciągu z przechwyconej grupy, który nosi nazwę `duplicateWord`.|  
|`\W`|Dopasowuje znak niebędące znakami słowa, w tym białych znaków i znaków interpunkcyjnych. Zapobiega to dopasowania wyrazu, który rozpoczyna się od słowa z pierwszej przechwyconej grupy wzorzec wyrażenia regularnego.|  
|`(?<nextWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy przechwytywania `nextWord`.|  
  
 Należy pamiętać, że nazwa grupy można powtarzać w wyrażeniu regularnym. Na przykład, istnieje możliwość przez więcej niż jednej grupy, można go nazwać `digit`, tak jak pokazano w poniższym przykładzie. W przypadku takich samych nazwach wartość <xref:System.Text.RegularExpressions.Group> obiekt jest określany przez ostatnie pomyślne przechwytywania w ciągu wejściowym. Ponadto <xref:System.Text.RegularExpressions.CaptureCollection> jest wypełniana przy użyciu informacji o każdym przechwytywania tak, jak możesz ją, jeśli nie została zduplikowana nazwa grupy.  
  
 W poniższym przykładzie, wyrażenie regularne `\D+(?<digit>\d+)\D+(?<digit>\d+)?` obejmuje dwa wystąpienia grupę o nazwie `digit`. Pierwszy `digit` nazwanymi przechwytywaniami grupy co najmniej jeden znak cyfry. Drugi `digit` nazwanej grupy przechwytywania zera lub jednego wystąpienia co najmniej jeden znak cyfry. Jako dane wyjściowe w przykładzie pokazano, jeśli drugi przechwytywania pomyślnie grupy jest zgodna z tekstem, wartość ten tekst Określa wartość <xref:System.Text.RegularExpressions.Group> obiektu. Jeśli jest to druga grupa przechwytywania nie nie pasuje ciąg wejściowy wartość ostatniego pomyślnego dopasowania definiuje wartość <xref:System.Text.RegularExpressions.Group> obiektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 W poniższej tabeli przedstawiono, jak wyrażenia regularnego jest interpretowany.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\D+`|Dopasowuje jeden lub więcej znaków niż cyfra niebędąca cyfrą dziesiętną.|  
|`(?<digit>\d+)`|Dopasowuje co najmniej jeden znak cyfry dziesiętnej. Dopasowanie, aby przypisać `digit` o nazwie grupy.|  
|`\D+`|Dopasowuje jeden lub więcej znaków niż cyfra niebędąca cyfrą dziesiętną.|  
|`(?<digit>\d+)?`|Dopasowanie zera lub jednego wystąpienia co najmniej jeden znak cyfry dziesiętnej. Dopasowanie, aby przypisać `digit` o nazwie grupy.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Równoważenie definicji grup  
 Definicję grupy równoważącej usuwa definicję wcześniej zdefiniowanej grupy i magazyny w bieżącej grupie, interwał pomiędzy wcześniej zdefiniowaną grupę i bieżącej grupy. Ta konstrukcja grupująca ma następujący format:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 lub:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 gdzie *Nazwa1* jest bieżącą grupę (opcjonalnie) *Nazwa2* jest wcześniej zdefiniowanej grupy i *Podwyrażenie* jest wzorzec dowolnym prawidłowym wyrażeniem regularnym. Równoważenie definicji grup usuwa definicję *Nazwa2* i przechowuje odstęp między *Nazwa2* i *Nazwa1* w *Nazwa1*. Jeśli nie *Nazwa2* grupy jest zdefiniowany, provided dopasowanie. Ponieważ usuwanie ostatnia definicja *Nazwa2* poprzednią definicję, co spowoduje wyświetlenie *Nazwa2*, ta konstrukcja umożliwia używanie stosu przechwyconych obrazów dla grupy *Nazwa2* jako Licznik rejestrowanie informacji o zagnieżdżonej konstrukcji, takich jak nawiasy lub otwierające i zamykające nawiasy kwadratowe.  
  
 Równoważenie definicji grup używa *Nazwa2* jako stosu. Znak początku każdej zagnieżdżonej konstrukcji znajduje się w grupie, a w jego <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji. Po dopasowaniu znak zamykającego odpowiadającymi mu dostawcami otwierania znaków zostanie usunięty z grupy, a <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekcji zmniejszyła się o jeden. Po otwierającym i znaki zamknięcia wszystkich zagnieżdżonych konstrukcji dopasowane, *Nazwa1* jest pusty.  
  
> [!NOTE]
>  Po użytkownik modyfikuje wyrażenia regularnego w poniższym przykładzie do użycia odpowiednie otwieranie i zamykanie znak zagnieżdżonej konstrukcji, służy do obsługi najbardziej zagnieżdżonej konstrukcji, takich jak wyrażenia matematyczne lub linii kodu programu, które zawierają wiele zagnieżdżonych wywołań metody.  
  
 W poniższym przykładzie użyto definicję grupy równoważącej, aby dopasować lewy i prawy nawias nawiasów kwadratowych (<>) w ciągu wejściowym. W przykładzie zdefiniowano dwie grupy nazwane `Open` i `Close`, które są używane jak stos do śledzenia pary pasujące nawiasy. Każdy przechwyconych lewy nawias kątowy są przesyłane do przechwytywania zbiór `Open` grupy i wszystkich przechwyconych prawy nawias kątowy są przesyłane do przechwytywania zbiór `Close` grupy. Równoważenie definicji grup gwarantuje, że jest pasujący nawias klamrowy pod kątem dla każdego lewego nawiasu ostrego. Jeśli nie, jest ostatnim podciąg wzorca, `(?(Open)(?!))`, jest oceniane tylko wtedy, gdy `Open` grupy nie jest pusty (a w związku z tym, jeśli wszystkie zagnieżdżone konstrukcje nie zostały zamknięte). Jeśli nie zostało ocenione końcowego podciąg wzorca, dopasowanie zakończy się niepowodzeniem, ponieważ `(?!)` podciąg wzorca jest asercja negatywna asercja wyprzedzająca o zerowej szerokości, która zawsze kończy się niepowodzeniem.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego jest:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Wyrażenia regularnego jest interpretowany w następujący sposób:  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij na początku ciągu.|  
|`[^<>]*`|Dopasowuje zero lub więcej znaków, które nie są po lewej stronie lub pod kątem nawiasy kwadratowe.|  
|`(?'Open'<)`|Zgodne z lewego nawiasu ostrego i przypisz je do grupy o nazwie `Open`.|  
|`[^<>]*`|Dopasowuje zero lub więcej znaków, które nie są po lewej stronie lub pod kątem nawiasy kwadratowe.|  
|`((?'Open'<)[^<>]*) +`|Dopasowuje jeden lub więcej wystąpień lewego nawiasu ostrego następuje zero lub więcej znaków, które nie są po lewej stronie lub pod kątem nawiasy kwadratowe. Jest to druga grupa przechwytywania.|  
|`(?'Close-Open'>)`|Prawy nawias kątowy odpowiada, należy przypisać podciąg między `Open` grupy i bieżącą grupą do `Close` grupy i usuń definicję `Open` grupy.|  
|`[^<>]*`|Dopasowuje zero lub więcej wystąpień dowolnego znaku, który nie jest lewe ani prawy nawias kątowy.|  
|`((?'Close-Open'>)[^<>]*)+`|Dopasowuje jeden lub więcej wystąpień prawy nawias kątowy, następuje zero lub więcej wystąpień dowolnego znaku jest prawy nawias kątowy ani po lewej stronie. Podczas dopasowywania prawego nawiasu ostrego, przypisz podciąg między `Open` grupy i bieżącą grupą do `Close` grupy i usuń definicję `Open` grupy. Jest to trzecia grupa przechwytywania.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Dopasowuje zero lub więcej wystąpień następującego wzorca: jeden lub więcej wystąpień lewego nawiasu ostrego następuje zero lub więcej znaków nawiasu ostrego następuje jeden lub więcej wystąpień prawy nawias kątowy, następuje zero lub więcej wystąpień inne niż nawiasy. Podczas dopasowywania prawego nawiasu ostrego, usuń definicję `Open` grupy, a następnie przypisz podciąg między `Open` grupy i bieżącą grupą do `Close` grupy. Jest to pierwsza grupa przechwytywania.|  
|`(?(Open)(?!))`|Jeśli `Open` grupa istnieje, Porzuć dopasowania, jeśli pusty ciąg, który można dopasować, ale nie Przejdź położenie aparat wyrażeń regularnych w ciągu. Jest to asercja negatywna asercja wyprzedzająca o zerowej szerokości. Ponieważ pusty ciąg jest zawsze niejawnie obecne w ciągu wejściowym, tym dopasowanie nie zawsze powiedzie się. Błąd dopasowania to wskazuje, że nawiasy nie są równoważone.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Końcowe Podwyrażenie `(?(Open)(?!))`, wskazuje, czy zagnieżdżania tworzy się w ciągu wejściowym są prawidłowo równoważone, (na przykład, czy każdy lewego nawiasu ostrego dorównuje prawy nawias kątowy). Używa ona dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach; Aby uzyskać więcej informacji, zobacz [konstrukcje](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Jeśli `Open` grupy jest zdefiniowany, aparat wyrażeń regularnych próbuje dopasować Podwyrażenie `(?!)` w ciągu wejściowym. `Open` Grupy powinna być zdefiniowana tylko wtedy, gdy niezrównoważone konstrukcje zagnieżdżenia. W związku z tym wzorzec, które mają zostać dopasowane w ciągu wejściowym powinna wynosić 1, który zawsze powoduje, że dopasowanie nie powiedzie się. W tym przypadku `(?!)` jest asercja negatywna asercja wyprzedzająca o zerowej szerokości która zawsze kończy się niepowodzeniem, ponieważ ciąg pusty występuje zawsze niejawnie w następnej pozycji w ciągu wejściowym.  
  
 W przykładzie, aparat wyrażeń regularnych ocenia ciągu wejściowego "\<abc >< mno\<xyz >>" jak pokazano w poniższej tabeli.  
  
|Krok|Wzorzec|Wynik|  
|----------|-------------|------------|  
|1|`^`|Rozpoczyna dopasowanie na początku ciągu wejściowego|  
|2|`[^<>]*`|Wyszukuje nawiasu ostrego znaków przed lewego nawiasu ostrego; znajdzie żadnych dopasowań.|  
|3|`(((?'Open'<)`|Pasuje do lewego nawiasu ostrego w "\<abc >" i przypisuje go do `Open` grupy.|  
|4|`[^<>]*`|Pasuje do "abc".|  
|5|`)+`|"< abc" jest wartością drugiego przechwyconą grupę.<br /><br /> Następny znak w ciągu wejściowym nie jest lewy nawias kątowy, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|6|`((?'Close-Open'>)`|Pasuje do prawego nawiasu ostrego w "\<abc >", "abc", czyli podciąg przypisuje między `Open` grupy i kąt prosty dopasowywanie do `Close` grupę, a następnie usuwa bieżącą wartość ("<") z `Open` grupy, zostawiać je puste.|  
|7|`[^<>]*`|Wyszukuje nawiasu ostrego znaków od prawego nawiasu ostrego; Umożliwia znalezienie żadnych dopasowań.|  
|8|`)+`|Wartość trzeciego przechwyconej grupy ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawy nawias kątowy, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|9|`)*`|Wartość pierwszej przechwyconej grupy "\<abc >".<br /><br /> Następny znak w ciągu wejściowym jest lewy nawias kątowy, dlatego aparat wyrażeń regularnych w pętli do `(((?'Open'<)` podciąg wzorca.|  
|10|`(((?'Open'<)`|Pasuje do lewego nawiasu ostrego w "\<mno >" i przypisuje go do `Open` grupy. Jego <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> teraz kolekcja zawiera pojedynczą wartość "<".|  
|11|`[^<>]*`|Dopasowuje "mno".|  
|12|`)+`|"< mno" jest wartością drugiego przechwyconą grupę.<br /><br /> Następny znak w ciągu wejściowym jest lewy nawias kątowy, dlatego aparat wyrażeń regularnych w pętli do `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|13|`(((?'Open'<)`|Pasuje do lewego nawiasu ostrego w "\<xyz >" i przypisuje go do `Open` grupy. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Zbiór `Open` grupy obejmuje teraz dwa przechwytywania: lewy nawias kątowy z "\<mno >" i lewego nawiasu ostrego z "\<xyz >".|  
|14|`[^<>]*`|Dopasowania "ciągu xyz".|  
|15|`)+`|"< xyz" jest wartością drugiego przechwyconą grupę.<br /><br /> Następny znak w ciągu wejściowym nie jest lewy nawias kątowy, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|16|`((?'Close-Open'>)`|Pasuje do prawego nawiasu ostrego w "\<xyz >". ciągu "xyz", przypisuje podciąg między `Open` grupy i kąt prosty dopasowywanie do `Close` grupę, a następnie usuwa bieżącą wartość `Open` grupy. Wartość poprzedniego przechwytywania (lewego nawiasu ostrego w "\<mno >") staje się bieżącą wartość `Open` grupy. <xref:System.Text.RegularExpressions.Group.Captures%2A> Zbiór `Open` grupa zawiera teraz pojedynczy przechwytywania, lewy nawias kątowy z "\<xyz >".|  
|17|`[^<>]*`|Wyszukuje nawiasu ostrego znaków. Umożliwia znalezienie żadnych dopasowań.|  
|18|`)+`|Wartość trzeciego przechwyconej grupy ">".<br /><br /> Następny znak w ciągu wejściowym jest prawy nawias kątowy, dlatego aparat wyrażeń regularnych w pętli do `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|19|`((?'Close-Open'>)`|Pasuje do końcowego prawego nawiasu ostrego w "xyz >>", przypisuje "mno\<xyz >" (podciąg między `Open` grupy i prawego nawiasu ostrego) do `Close` grupę, a następnie usuwa bieżącą wartość `Open` grupy. `Open` Grupy jest obecnie pusta.|  
|20|`[^<>]*`|Wyszukuje nawiasu ostrego znaków. Umożliwia znalezienie żadnych dopasowań.|  
|21|`)+`|Wartość trzeciego przechwyconej grupy ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawy nawias kątowy, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|22|`)*`|Wartość pierwszej przechwyconej grupy "< mno\<xyz >>".<br /><br /> Następny znak w ciągu wejściowym nie jest lewy nawias kątowy, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(((?'Open'<)` podciąg wzorca.|  
|23|`(?(Open)(?!))`|`Open` Grupy nie jest zdefiniowana, więc dopasowanie nie zostanie podjęta.|  
|24|`$`|Pasuje do końca ciągu wejściowego.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Grupy niezapamiętywane  
 Następujące konstrukcji grupowania nie przechwytuje podciągu, który pasuje podwyrażenia:  
  
```  
(?:subexpression)  
```  
  
 gdzie *Podwyrażenie* jest wzorzec dowolnym prawidłowym wyrażeniem regularnym. Konstrukcja nieprzechwytywaną grupę zwykle jest używana, gdy do grupy jest stosowany kwantyfikator, ale podciągów przechwycone przez grupę są nie interesujące.  
  
> [!NOTE]
>  Wyrażenie regularne zawiera konstrukcje grupujące zagnieżdżonych, konstrukcja zewnętrzne nieprzechwytywaną grupę nie ma zastosowania do konstrukcji wewnętrzny grupach zagnieżdżonych.  
  
 W poniższym przykładzie pokazano wyrażenie regularne, które obejmuje grupy niezapamiętywane. Należy pamiętać o tym, czy dane wyjściowe nie zawiera żadnych przechwyconych grupach.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Wyrażenie regularne `(?:\b(?:\w+)\W*)+\.` odpowiada zdania, który jest kończony kropką. Ponieważ wyrażenie regularne skupia się na zdania, a nie na poszczególnych wyrazów, konstrukcje grupujące są używane wyłącznie jako Kwantyfikatory. Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?:\w+)`|Dopasowuje co najmniej jeden znak słowa. Nie należy przypisywać dopasowany tekst do przechwyconej grupy.|  
|`\W*`|Dopasowuje zero lub więcej znaki niebędące znakami słowa.|  
|`(?:\b(?:\w+)\W*)+`|Dopasowuje wzorzec jednego lub więcej znaków słowa, uruchamiania na granicy wyrazu, po której następuje zero lub więcej znaki niebędące znakami słowa, jeden lub więcej razy. Nie należy przypisywać dopasowany tekst do przechwyconej grupy.|  
|`\.`|Dopasowanie kropki.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Opcje grupy  
 Następujące konstrukcja grupująca stosuje lub wyłącza określone opcje w podwyrażeniu:  
  
 `(?imnsx-imnsx:` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest wzorzec dowolnym prawidłowym wyrażeniem regularnym. Na przykład `(?i-s:)` włącza ignorowanie wielkości liter i wyłączenie trybu jednowierszowego. Aby uzyskać więcej informacji dotyczących opcji wbudowanej, można określić, zobacz [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Można określić opcje, które mają zastosowanie do całego wyrażenia regularnego zamiast podwyrażenia przy użyciu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub metody statycznej. Można również określić opcje określane w tekście, które są stosowane po określonego punktu w wyrażeniu regularnym przy użyciu `(?imnsx-imnsx)` konstrukcją języka pierwszej klasy.  
  
 Konstrukcja opcje grupy nie jest grupa przechwytywania. Oznacza to mimo że jakiejkolwiek jego części ciągu, która jest przechwytywana przez *Podwyrażenie* wchodzi w dopasowanie, są nie zawarte w przechwyconej grupy ani używanych do wypełniania <xref:System.Text.RegularExpressions.GroupCollection> obiektu.  
  
 Na przykład, wyrażenie regularne `\b(?ix: d \w+)\s` w poniższym przykładzie używa opcji wbudowanej w konstrukcję grupującą aby umożliwić dopasowanie bez uwzględniania wielkości liter i Ignorowanie wzorca odstępu przy określaniu wszystkie wyrazy rozpoczynające się od litera "d". Wyrażenie regularne jest zdefiniowane, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?ix: d \w+)`|Za pomocą dopasowanie bez uwzględniania wielkości liter i ignorowanie biały znak w tym wzorcu, dopasowuje "d", po której następuje jeden lub więcej znaków słowa.|  
|`\s`|Dopasowuje znak odstępu.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Dodatnie asercje z patrzeniem w przód o zerowej szerokości  
 Następujące konstrukcja grupująca definiuje asercja pozytywna asercja wyprzedzająca o zerowej szerokości:  
  
 `(?=` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* się wszelkie wzorzec wyrażenia regularnego. Dopasowanie zakończy się powodzeniem, ciąg wejściowy musi być zgodna ze wzorcem wyrażenia regularnego w *Podwyrażenie*, mimo że dopasowany podciąg nie jest uwzględniony w wyniku dopasowania. Asercja pozytywna asercja wyprzedzająca o zerowej szerokości nie używa wycofywania.  
  
 Zazwyczaj asercja pozytywna asercja wyprzedzająca o zerowej szerokości znajduje się na końcu wzorca wyrażenia regularnego. Definiuje podciąg, muszą znajdować się na końcu ciągu do aby wystąpiło dopasowanie, ale które nie powinny znajdować się dopasowania. Jest to również przydatne w celu zapobiegania nadmiernego wycofywania. Asercja pozytywna asercja wyprzedzająca o zerowej szerokości można użyć, aby upewnić się, że określonego przechwyconej grupy rozpoczyna się od tekst, który pasuje do podzbioru wzorca określonego przechwyconej grupy. Na przykład jeśli grupa przechwytywania pasuje do słowa następujących po sobie znaków, umożliwia to asercja pozytywna asercja wyprzedzająca o zerowej szerokości wymagają pierwszym znakiem alfabetycznym, wielką literę.  
  
 Następujące przykładowe zastosowania asercja pozytywna asercja wyprzedzająca o zerowej szerokości, aby dopasować wyrazu, który poprzedza zlecenie "is" w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Wyrażenie regularne `\b\w+(?=\sis\b)` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(?=\sis\b)`|Określ, czy znaków słowa, których następuje znak odstępu lub ciąg "is", której kończy się na granicy wyrazu. Jeśli tak, dopasowanie zakończy się pomyślnie.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Ujemne asercje z patrzeniem w przód o zerowej szerokości  
 Następujące konstrukcja grupująca definiuje asercja negatywna asercja wyprzedzająca o zerowej szerokości:  
  
 `(?!` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* się wszelkie wzorzec wyrażenia regularnego. Dopasowanie zakończy się powodzeniem, ciąg wejściowy nie może odpowiadać wzorzec wyrażenia regularnego w *Podwyrażenie*, mimo że dopasowany ciąg nie jest uwzględniony w wyniku dopasowania.  
  
 Asercja negatywna asercja wyprzedzająca o zerowej szerokości, jest zazwyczaj używany na początku lub na końcu wyrażenia regularnego. Na początku wyrażenia regularnego, ją zdefiniować określony wzorzec, które nie powinny być dopasowane, gdy na początku wyrażenia regularnego definiuje podobne, ale bardziej ogólnych wzorzec do dopasowania. W tym przypadku jest często używane do ograniczania wycofywania. Na końcu wyrażenia regularnego ją zdefiniować Podwyrażenie, który nie może wystąpić na końcu dopasowania.  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, który używa asercja wyprzedzająca o zerowej szerokości na początku wyrażenia regularnego do dopasowania słów, które nie zaczynają się od "Uruchom".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Wyrażenie regularne `\b(?!un)\w+\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?!un)`|Określanie, czy następne dwa znaki są "Uruchom". Jeśli nie są one dopasowanie jest możliwe.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, który używa asercja wyprzedzająca o zerowej szerokości na końcu wyrażenia regularnego do dopasowania słów, których nie kończy się znakiem interpunkcyjnym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Wyrażenie regularne `\b\w+\b(?!\p{P})` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
|`\p{P})`|Jeśli następny znak nie jest symbolem interpunkcji (np. kropki lub przecinka), dopasowanie się powiedzie.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Dodatnie asercje wsteczne o zerowej szerokości  
 Następujące konstrukcja grupująca definiuje potwierdzenia dodatnie asercje wsteczne o zerowej szerokości:  
  
 `(?<=` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* się wszelkie wzorzec wyrażenia regularnego. Aby dopasowanie zakończyło się zakończyć się pomyślnie *Podwyrażenie* musi przypadać w ciągu wejściowym na lewo od aktualnej pozycji, mimo że `subexpression` nie jest uwzględniony w wyniku dopasowania. Asercja pozytywna asercja wsteczna o zerowej szerokości nie używa wycofywania.  
  
 Potwierdzenia dodatnie asercje wsteczne o zerowej szerokości są zwykle używane na początku wyrażenia regularne. Wzorzec, który określają jest warunkiem wstępnym pod kątem dopasowania, chociaż nie jest częścią wyników dopasowania.  
  
 Na przykład w poniższym przykładzie dopasowywane dwie ostatnie cyfry roku wieku dwudziestego pierwszego (czyli wymaga że cyfr "20" poprzedzać dopasowany ciąg).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Definicję wzorca wyrażenia regularnego `(?<=\b20)\d{2}\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\d{2}`|Dopasowuje dwie cyfry dziesiętne.|  
|`(?<=\b20)`|Kontynuuje dopasowywanie, jeśli dwie cyfry dziesiętne są poprzedzone cyfr dziesiętnych "20" na granicy wyrazu.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Potwierdzenia dodatnie asercje wsteczne o zerowej szerokości są również używane do ograniczania wycofywania, gdy ostatni znak lub znaki w przechwyconej grupy muszą być podzbiorem znaków, które pasuje do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytywania wszystkich znaków słowa kolejnych, umożliwia asercja pozytywna asercja wsteczna o zerowej szerokości wymagać, aby ostatni znak alfabetyczny.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Ujemne asercje wsteczne o zerowej szerokości  
 Następujące konstrukcja grupująca definiuje asercja negatywna asercja wsteczna o zerowej szerokości:  
  
 `(?<!` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* się wszelkie wzorzec wyrażenia regularnego. Aby dopasowanie zakończyło się zakończyć się pomyślnie *Podwyrażenie* nie może wystąpić w ciągu wejściowym na lewo od bieżącej pozycji. Jednak podciąg, która pasuje do `subexpression` nie jest uwzględniony w wyniku dopasowania.  
  
 Negatywna asercja wsteczna o zerowej szerokości potwierdzenia są zwykle używane na początku wyrażenia regularne. Wzorzec, który określają wykluczającą dopasowania w ciągu, który następuje. Służą one również ograniczyć wycofywania, gdy ostatni znak lub znaki w przechwyconej grupy nie może być jeden lub więcej znaków, które pasują do wzorca wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytywania wszystkich znaków słowa kolejnych, umożliwia to asercja pozytywna asercja wsteczna o zerowej szerokości wymagają ostatni znak nie znaku podkreślenia (_).  
  
 W poniższym przykładzie dopasowywane Data dla każdego dnia, tygodnia, który nie jest weekendy (który jest sobota ani niedziela).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Definicję wzorca wyrażenia regularnego `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` jest interpretowane tak jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa, następuje znak odstępu.|  
|`\d{1,2},`|Dopasowuje co najmniej dwie cyfry dziesiętne, następuje znak odstępu i przecinek.|  
|`\d{4}\b`|Odpowiada czterem cyfrom po przecinku, a kończy dopasowanie na granicy wyrazu.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Jeśli dopasowanie jest poprzedzony przez coś innego niż ciągi, "Sobota" lub "Niedziela", po której następuje spacja, dopasowanie zakończy się.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Podwyrażenia bez nawrotów  
 Następujące konstrukcja grupująca reprezentuje Podwyrażenie (znany także jako Podwyrażenie "zachłanne"):  
  
 `(?>` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* się wszelkie wzorzec wyrażenia regularnego.  
  
 Normalnie Jeśli wyrażenie regularne zawiera opcjonalne lub alternatywne dopasowania wzorca i dopasowanie nie powiedzie się, aparat wyrażeń regularnych można rozgałęziać w wielu kierunkach do dopasowania ciągu wejściowego z wzorcem. Jeśli nie zostanie znalezione dopasowanie, podczas pierwszej gałęzi, aparat wyrażeń regularnych można utworzyć kopię zapasową lub śledzenie wsteczne w punkcie, gdzie zajęło to pierwsze dopasowanie i spróbuj dopasowanie za pomocą drugiego oddziału. Ten proces może być kontynuowany, dopóki nie wykonano wszystkich gałęzi.  
  
 `(?>` *Podwyrażenie* `)` języka konstruowania wyłącza wycofywania. Aparat wyrażeń regularnych będzie odpowiadał tak dużą liczbę znaków w ciągu wejściowym, ponieważ jest to możliwe. Żadne dodatkowe dopasowanie jest możliwe, będzie śledzenie wsteczne nie próby dopasowania do wzorca alternatywne. (Czyli Podwyrażenie dopasowuje wyłącznie ciągi, które zostałyby dopasowane przez samo to Podwyrażenie; nie będzie podejmował próby dopasowania ciągu na podstawie Podwyrażenie i wszelkie podwyrażenia, które występują po nim).  
  
 Ta opcja jest zalecana, jeśli wiesz, że używanie wycofywania nie powiedzie się. Aparat wyrażeń regularnych uniemożliwia wykonywanie niepotrzebne wyszukiwania poprawia wydajność.  
  
 W poniższym przykładzie pokazano, jak Podwyrażenie bez wycofywania modyfikuje wyników dopasowania do wzorca. Wycofywania wyrażenie regularne dopasowuje pomyślnie szereg powtarzające się znaki następuje jedno wystąpienie takiego samego znaku na granicy wyrazu, ale bez wyrażenia regularnego nie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Podwyrażenia bez wycofywania wyrażenia regularnego `(?>(\w)\1+).\b` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasowuje znak słowa i przypisz je do pierwszej grupy przechwytywania.|  
|`\1+`|Odpowiada wartości pierwszego przechwyconego podciągu jedną lub więcej razy.|  
|`.`|Dopasowuje dowolny znak.|  
|`\b`|Zakończ dopasowanie na granicy wyrazu.|  
|`(?>(\w)\1+)`|Pasuje jedno lub więcej wystąpień znaku słowa zduplikowane, ale nie wykonuj nawrotu do dopasowania ostatni znak na granicy wyrazu.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Konstrukty grupujące i obiekty wyrażeń regularnych  
 Podciągi, które są dopasowane przez grupę przechwytywania wyrażenia regularnego są reprezentowane przez <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> obiektów, które mogą być pobierane z <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.GroupCollection> Obiektu jest wypełniana w następujący sposób:  
  
-   Pierwszy <xref:System.Text.RegularExpressions.Group> obiektu w kolekcji (object o indeksie zero) reprezentuje całego dopasowania.  
  
-   Zestaw następnego <xref:System.Text.RegularExpressions.Group> obiekty reprezentują nienazwane grupy przechwytywania (numerowana). Pojawiają się w kolejności, w której są zdefiniowane w wyrażeniu regularnym, od lewej do prawej. Indeks wartości tych grup w zakresie od 1 do liczby nienazwane przechwytywania grup w kolekcji. (Indeks określonej grupy jest równoważne z jej numerowane odwołanie wsteczne. Aby uzyskać więcej informacji dotyczących dopasowywania wstecznego, zobacz [konstrukcje dopasowywania wstecznego](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
-   Ostatni zestaw <xref:System.Text.RegularExpressions.Group> obiekty reprezentują nazwanych grup przechwytywania. Pojawiają się w kolejności, w której są zdefiniowane w wyrażeniu regularnym, od lewej do prawej. Wartość indeksu pierwszego nazwanej grupy przechwytywania jest większa o jeden od indeksu ostatniej nienazwanej grupy przechwytywania. W przypadku nie nienazwane przechwytywania grup w wyrażeniu regularnym, wartość indeksu pierwszego nazwanej grupy przechwytywania jest jeden.  
  
 W przypadku zastosowania kwantyfikator do grupy przechwytywania, odpowiedni <xref:System.Text.RegularExpressions.Group> obiektu <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, i <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> właściwości odzwierciedlają ostatni podciąg, która jest przechwytywana przez grupę przechwytywania. Możesz pobrać kompletny zestaw podciągi, które są przechwytywane według grup, które mają Kwantyfikatory z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości.  
  
 Poniższy przykład wyjaśnia stosunek między <xref:System.Text.RegularExpressions.Group> i <xref:System.Text.RegularExpressions.Capture> obiektów.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\w+)\W+)+` wyodrębnia poszczególnych wyrazów z ciągu. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Te znaki tworzą razem wyrazu. Jest to druga grupa przechwytywania.|  
|`\W+`|Dopasowuje znaki niebędące znakami słowa jeden lub więcej.|  
|`(\w+)\W+)+`|Dopasowuje wzorzec jednego lub więcej znaków słowa, następuje jedna lub więcej niebędące znakami słowa jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
 Pierwsza grupa przechwytywania pasuje do każdego wyrazu w zdaniu. Druga grupa przechwytywania pasuje do każdego wyrazu oraz znaków interpunkcyjnych i odstęp wyrazie. <xref:System.Text.RegularExpressions.Group> Obiektu, którego indeks to 2 zawiera informacje dotyczące tekst uwzględniony przez to druga grupa przechwytywania. Kompletny zestaw słów przechwycone przez grupę przechwytywania są dostępne z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
