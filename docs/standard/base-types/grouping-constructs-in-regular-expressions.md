---
title: "Konstrukcje grupujące w wyrażeniach regularnych"
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
- lookbehinds
- regular expressions, grouping constructs
- lookaheads
- .NET Framework regular expressions, grouping constructs
- constructs, grouping
- grouping constructs
ms.assetid: 0fc18634-f590-4062-8d5c-f0b71abe405b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b9e54d8bbc9ca7cc9172fd83bd15968b3cef8e1
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="grouping-constructs-in-regular-expressions"></a>Konstrukcje grupujące w wyrażeniach regularnych
Konstrukcje grupujące odróżniać użyto wyrażenia regularnego i przechwytywania podciągów ciągu wejściowego. Można użyć konstrukcji grupowania wykonywać następujące czynności:  
  
-   Odpowiada Podwyrażenie, który jest powtarzany w ciągu wejściowym.  
  
-   Zastosowania kwantyfikatora do Podwyrażenie, który ma wiele elementów języka wyrażenia regularnego. Aby uzyskać więcej informacji na temat Kwantyfikatory, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Dołączyć podwyrażenia ciąg, który jest zwracany przez <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> i <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metody.  
  
-   Pobrać poszczególnych użyto z <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości i przetwarzanie ich oddzielnie od dopasowanego tekstu jako całość.  
  
 Poniższej tabeli wymieniono konstrukcji grupowania obsługiwane przez aparat wyrażeń regularnych .NET oraz wskazuje, czy są Przechwytywanie lub z systemem innym niż przechwytywania.  
  
|Konstrukcja grupująca|Przechwytywanie lub nieprzechwyconej|  
|------------------------|-------------------------------|  
|[Użyto pasujących](#matched_subexpression)|Przechwytywanie|  
|[Użyto pasujących nazwanego](#named_matched_subexpression)|Przechwytywanie|  
|[Równoważenie definicje grup](#balancing_group_definition)|Przechwytywanie|  
|[Grup nieprzechwyconych](#noncapturing_group)|Nieprzechwyconej|  
|[Opcje grupy](#group_options)|Nieprzechwyconej|  
|[Potwierdzenia wyprzedzenia dodatnią zerowej szerokości](#zerowidth_positive_lookahead_assertion)|Nieprzechwyconej|  
|[Potwierdzenia wyprzedzenia ujemna zerowej szerokości](#zerowidth_negative_lookahead_assertion)|Nieprzechwyconej|  
|[Asercje o zerowej szerokości dodatnie wybieganie wstecz](#zerowidth_positive_lookbehind_assertion)|Nieprzechwyconej|  
|[Asercje o zerowej szerokości ujemne wybieganie wstecz](#zerowidth_negative_lookbehind_assertion)|Nieprzechwyconej|  
|[Użyto nonbacktracking](#nonbacktracking_subexpression)|Nieprzechwyconej|  
  
 Aby uzyskać informacje dotyczące grup i model obiektów wyrażeń regularnych, zobacz [grupowanie konstrukcje i obiektów wyrażeń regularnych](#Objects).  
  
<a name="matched_subexpression"></a>   
## <a name="matched-subexpressions"></a>Dopasowane podwyrażenie  
 Poniższa konstrukcja grupowania przechwytuje Podwyrażenie dopasowane:  
  
 `(` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest wzorzec wszystkie prawidłowe wyrażenie regularne. Przechwytuje, że Użyj nawiasów są numerowane automatycznie od lewej do prawej na podstawie kolejności otwierającymi nawiasami w wyrażeniu regularnym, począwszy od jednej. Przechwytywanie, numerowana zero jest uwzględniony przez wzorzec wyrażenia regularnego cały tekst.  
  
> [!NOTE]
>  Domyślnie `(` *Podwyrażenie* `)` element języka przechwytuje Podwyrażenie dopasowany. Ale jeśli <xref:System.Text.RegularExpressions.RegexOptions> zawiera parametr metody dopasowania wzorca wyrażeń regularnych <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagi, lub jeśli `n` jest stosowana do tego wyrażenia podrzędnego (zobacz [grupy opcje](#group_options) dalszej części tego tematu), nie przechwytuje Podwyrażenie dopasowany.  
  
 Aby dostęp do przechwyconych grup na cztery sposoby:  
  
-   Za pomocą dopasuje skonstruować w wyrażeniu regularnym. Dopasowany Podwyrażenie odwołuje się w tym samym wyrażeniu regularnym przy użyciu składni `\` *numer*, gdzie *numer* jest numerem porządkowym przechwycone Podwyrażenie.  
  
-   Przy użyciu nazwanego dopasuje skonstruować w wyrażeniu regularnym. Dopasowany Podwyrażenie odwołuje się w tym samym wyrażeniu regularnym przy użyciu składni `\k<` *nazwa*`>`, gdzie *nazwa* jest nazwą grupy przechwytywania lub `\k<` *numer*`>`, gdzie *numer* jest numerem porządkowym przechwytywania grupy. Przechwytywanie grupa ma domyślną nazwę, która jest taka sama jak jego numer porządkowy. Aby uzyskać więcej informacji, zobacz [nazwanego dopasowane użyto](#named_matched_subexpression) dalszej części tego tematu.  
  
-   Za pomocą `$` *numer* sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *numer* jest numerem porządkowym przechwycone Podwyrażenie.  
  
-   Programowo, za pomocą <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. Członek na pozycji zero w kolekcji reprezentuje dopasowania całego wyrażenia regularnego. Każdy członek kolejnych reprezentuje dopasowane wyrażenia podrzędnego. Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania i obiektów wyrażeń regularnych](#Objects) sekcji.  
  
 Poniższy przykład przedstawia wyrażenie regularne określające zduplikowanych wyrazów w tekście. Wzorzec wyrażenia regularnego dwóch grup przechwytywania reprezentuje dwa wystąpienia zduplikowanych programu word. Drugie wystąpienie są przechwytywane do zgłaszania jego położenie początkowe w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping1.cs#1)]
 [!code-vb[RegularExpressions.Language.Grouping#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
```  
(\w+)\s(\1)\W  
```  
  
 W poniższej tabeli przedstawiono, jak jest interpretowana wzorzec wyrażenia regularnego.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Jest to pierwsza grupa przechwytywania.|  
|`\s`|Dopasowuje znak odstępu.|  
|`(\1)`|Zgodny z ciągiem w pierwszym przechwyconej grupy. Jest to druga grupa przechwytywania. Przykład przypisuje go do przechwyconej grupy tak, aby pozycja początkowa zduplikowane Word mogą być pobierane z `Match.Index` właściwości.|  
|`\W`|Dopasowuje znak-word, w tym biały znak i znaków interpunkcyjnych. Zapobiega to dopasowania wyrazu, który rozpoczyna się od słowa z pierwszego przechwyconej grupy wzorzec wyrażenia regularnego.|  
  
<a name="named_matched_subexpression"></a>   
## <a name="named-matched-subexpressions"></a>O nazwie dopasowane podwyrażenia  
 Poniższa konstrukcja grupowania przechwytuje Podwyrażenie dopasowane i pozwala uzyskiwać dostęp do według nazwy lub numeru:  
  
```  
(?<name>subexpression)  
```  
  
 lub:  
  
```  
(?'name'subexpression)  
```  
  
 gdzie *nazwa* jest nazwą prawidłową grupę i *Podwyrażenie* jest wzorzec wszystkie prawidłowe wyrażenie regularne. *Nazwa* nie może zawierać żadnych znaków interpunkcyjnych i nie może rozpoczynać się cyfrą.  
  
> [!NOTE]
>  Jeśli <xref:System.Text.RegularExpressions.RegexOptions> zawiera parametr metody dopasowania wzorca wyrażeń regularnych <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> flagi, lub jeśli `n` jest stosowana do tego wyrażenia podrzędnego (zobacz [grupy opcje](#group_options) dalszej części tego tematu), tylko sposobem przechwytuje Podwyrażenie jest jawnie nazwy grup przechwytywania.  
  
 Aby dostęp do przechwyconej grupy nazwane w następujący sposób:  
  
-   Przy użyciu nazwanego dopasuje skonstruować w wyrażeniu regularnym. Dopasowany Podwyrażenie odwołuje się w tym samym wyrażeniu regularnym przy użyciu składni `\k<` *nazwa*`>`, gdzie *nazwa* jest nazwą przechwycone Podwyrażenie.  
  
-   Za pomocą dopasuje skonstruować w wyrażeniu regularnym. Dopasowany Podwyrażenie odwołuje się w tym samym wyrażeniu regularnym przy użyciu składni `\` *numer*, gdzie *numer* jest numerem porządkowym przechwycone Podwyrażenie. Nazwane użyto pasujących są numerowane kolejno od lewej do prawej po użyto dopasowany.  
  
-   Za pomocą `${` *nazwa* `}` sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *nazwa* jest nazwą przechwycone Podwyrażenie.  
  
-   Za pomocą `$` *numer* sekwencji zastąpienia w <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> wywołania metody, gdzie *numer* jest numerem porządkowym przechwycone Podwyrażenie.  
  
-   Programowo, za pomocą <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. Członek na pozycji zero w kolekcji reprezentuje dopasowania całego wyrażenia regularnego. Każdy członek kolejnych reprezentuje dopasowane wyrażenia podrzędnego. Nazwanych grup przechwyconych są przechowywane w kolekcji po numerem grupy przechwycony.  
  
-   Programowo, podając nazwę Podwyrażenie <xref:System.Text.RegularExpressions.GroupCollection> indeksatora obiektu (w języku C#) lub jego <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> właściwości (w języku Visual Basic).  
  
 Proste wyrażenia regularnego ilustruje sposób numerowane (bez nazwy) i nazwanych grup można odwoływać się programowo lub przy użyciu składni wyrażeń regularnych języka. Wyrażenie regularne `((?<One>abc)\d+)?(?<Two>xyz)(.*)` daje następujące przechwytywania grupy według numeru i według nazwy. Pierwszy Przechwytywanie grupy (liczba 0) zawsze odwołuje się do całego wzorca.  
  
|Wartość liczbowa|Nazwa|Wzorzec|  
|------------|----------|-------------|  
|0|0 (nazwa domyślna)|`((?<One>abc)\d+)?(?<Two>xyz)(.*)`|  
|1|1 (domyślna nazwa)|`((?<One>abc)\d+)`|  
|2|2 (nazwa domyślna)|`(.*)`|  
|3|Jeden|`(?<One>abc)`|  
|4|dwa|`(?<Two>xyz)`|  
  
 Poniższy przykład przedstawia identyfikujący zduplikowanych słów i słowem poniższą każdego wyrazu zduplikowanych wyrażenia regularnego. Wzorzec wyrażenia regularnego definiuje dwie użyto nazwanego: `duplicateWord`, reprezentuje zduplikowany word; i `nextWord`, reprezentuje word, znajdujący się zduplikowane programu word.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping2.cs#2)]
 [!code-vb[RegularExpressions.Language.Grouping#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping2.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest następujący:  
  
```  
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)  
```  
  
 W poniższej tabeli przedstawiono, jak jest interpretowana wyrażenia regularnego.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(?<duplicateWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy przechwytywania `duplicateWord`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\k<duplicateWord>`|Zgodny z ciągiem z przechwyconej grupy o nazwie `duplicateWord`.|  
|`\W`|Dopasowuje znak-word, w tym biały znak i znaków interpunkcyjnych. Zapobiega to dopasowania wyrazu, który rozpoczyna się od słowa z pierwszego przechwyconej grupy wzorzec wyrażenia regularnego.|  
|`(?<nextWord>\w+)`|Dopasowuje co najmniej jeden znak słowa. Określ nazwę tej grupy przechwytywania `nextWord`.|  
  
 Należy pamiętać, że nazwa grupy można powtarzać w wyrażeniu regularnym. Na przykład istnieje możliwość więcej niż jednej grupy do nosić `digit`, jak pokazano w poniższym przykładzie. W przypadku takich samych nazwach, wartość <xref:System.Text.RegularExpressions.Group> obiektu jest określane przez ostatniego pomyślnego przechwytywania w ciągu wejściowym. Ponadto <xref:System.Text.RegularExpressions.CaptureCollection> jest wypełniane przy użyciu informacji o każdym przechwytywania, tak samo, jak możesz ją, jeśli nazwa grupy nie zostało zduplikowane.  
  
 W poniższym przykładzie, wyrażenie regularne `\D+(?<digit>\d+)\D+(?<digit>\d+)?` obejmuje dwa wystąpienia grupę o nazwie `digit`. Pierwszy `digit` o nazwie grupy przechwytywania co najmniej jeden znak cyfr. Drugi `digit` nazwaną grupę przechwytuje wystąpienie zero lub jeden lub więcej kolejnych cyfr znaków. Jako dane wyjściowe w przykładzie, jeśli drugi Przechwytywanie grupy pomyślnie pasuje do tekstu, wartość lub tekst Określa wartość <xref:System.Text.RegularExpressions.Group> obiektu. Jeśli nie drugiej grupy przechwytywania nie odpowiada ciąg wejściowy wartość ostatniego pomyślnego dopasowania definiuje wartość <xref:System.Text.RegularExpressions.Group> obiektu.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#12](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/duplicate1.cs#12)]
 [!code-vb[RegularExpressions.Language.Grouping#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/duplicate1.vb#12)]  
  
 W poniższej tabeli przedstawiono, jak jest interpretowana wyrażenia regularnego.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\D+`|Odpowiada co najmniej jeden znak podawać cyfr.|  
|`(?<digit>\d+)`|Zgodne z co najmniej jeden znak cyfrę. Dopasowanie, aby przypisać `digit` o nazwie grupy.|  
|\D+|Odpowiada co najmniej jeden znak podawać cyfr.|  
|`(?<digit>\d+)?`|Wystąpienie dopasowania zero lub jeden co najmniej jeden znak cyfrę. Dopasowanie, aby przypisać `digit` o nazwie grupy.|  
  
<a name="balancing_group_definition"></a>   
## <a name="balancing-group-definitions"></a>Równoważenie definicji grup  
 Równoważenia definicja grupy usuwa definicję uprzednio zdefiniowanej grupy i magazynów w bieżącej grupie, interwał między wcześniej zdefiniowanych grup oraz bieżący. Ta konstrukcja grupowania ma następujący format:  
  
```  
(?<name1-name2>subexpression)  
```  
  
 lub:  
  
```  
(?'name1-name2' subexpression)  
```  
  
 gdzie *Nazwa1* jest bieżącej grupy (opcjonalnie), *Nazwa2* jest grupą uprzednio zdefiniowany i *Podwyrażenie* jest wzorzec wszystkie prawidłowe wyrażenie regularne. Definicja grupy równoważenia usuwa definicję *Nazwa2* i zapisze wartość interwału między *Nazwa2* i *Nazwa1* w *Nazwa1*. Jeśli nie *Nazwa2* grupy jest określona, zapoznawanie dopasowania. Ponieważ usunięcie ostatniego definicji *Nazwa2* ujawnia poprzednią definicję *Nazwa2*, ta konstrukcja pozwala używać stosu przechwyconych obrazów grupy *Nazwa2* jako Licznik rejestrowanie informacji o zagnieżdżonej konstrukcji, takich jak nawiasy lub otwierające i zamykające nawiasy kwadratowe.  
  
 Używa równoważenia definicja grupy *Nazwa2* jako stosu. Pierwszy znak każdej zagnieżdżonej konstrukcji znajduje się w grupie, a w jego <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji. Po dopasowaniu znak zamykającego odpowiadającego znaku otwierania zostanie usunięty z grupy, a <xref:System.Text.RegularExpressions.Group.Captures%2A> kolekcji zostaje zmniejszona o jeden. Po dopasowaniu otwarcia i zamknięcia znaków konstrukcji wszystkich zagnieżdżonych, *Nazwa1* jest pusta.  
  
> [!NOTE]
>  Po zakończeniu modyfikowania wyrażenie regularne w poniższym przykładzie do użycia odpowiedniego otwierania i zamykającego znaku zagnieżdżonej konstrukcji, służy ona do obsługi najbardziej zagnieżdżonej konstrukcji, takich jak wyrażeń matematycznych lub wierszy kodu programu, które obejmują wiele wywołań metody zagnieżdżonych.  
  
 W poniższym przykładzie użyto równoważenia definicja grupy, aby dopasować lewy i prawy nawias nawiasy (<>) w ciągu wejściowym. W przykładzie zdefiniowano dwie grupy nazwane `Open` i `Close`, używane do śledzenia pasujących par nawiasy jak stosu. Każdy przechwyconych lewego nawiasu ostrego zostanie przypisany do kolekcji przechwytywania `Open` grupy i wszystkich przechwyconych prawego nawiasu ostrego zostanie przypisany do kolekcji przechwytywania `Close` grupy. Definicja grupy równoważenia gwarantuje, że jest pasujących nawiasów pod kątem dla każdego lewego nawiasu ostrego. Jeśli nie, jest ostatnim podciąg wzorca, `(?(Open)(?!))`, jest oceniane tylko wtedy, gdy `Open` grupy nie jest pusty (i, w związku z tym, jeśli nie wszystkie konstrukcje zagnieżdżonych zostało zamknięte). Jeśli oceny końcowego podciąg wzorca dopasowania nie powiedzie się, ponieważ `(?!)` podciąg wzorca jest potwierdzenie wyprzedzenia ujemna zerowej szerokości, która zawsze kończy się niepowodzeniem.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/grouping3.cs#3)]
 [!code-vb[RegularExpressions.Language.Grouping#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/grouping3.vb#3)]  
  
 Wzorzec wyrażenia regularnego jest:  
  
```  
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$  
```  
  
 Wyrażenie regularne jest interpretowana w następujący sposób:  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij na początku ciąg.|  
|`[^<>]*`|Zgodne zero lub więcej znaków, które nie są w nawiasach lewej lub pod kątem.|  
|`(?'Open'<)`|Zgodne lewego nawiasu ostrego i przypisz je do grupy o nazwie `Open`.|  
|`[^<>]*`|Zgodne zero lub więcej znaków, które nie są w nawiasach lewej lub pod kątem.|  
|`((?'Open'<)[^<>]*) +`|Odpowiada jednej lub więcej wystąpień lewego nawiasu ostrego następuje zero lub więcej znaków, które nie są w nawiasach lewej lub pod kątem. Jest to druga grupa przechwytywania.|  
|`(?'Close-Open'>)`|Zgodne prawego nawiasu ostrego, przypisz podciąg między `Open` grupy i bieżącą grupę do `Close` , a następnie usunąć definicji `Open` grupy.|  
|`[^<>]*`|Zgodne zero lub więcej wystąpień dowolny znak, który nie jest lewe ani prawego nawiasu ostrego.|  
|`((?'Close-Open'>)[^<>]*)+`|Jeden lub więcej wystąpień prawego nawiasu ostrego są zgodne, następuje zero lub więcej wystąpień dowolnego znaku, który nie jest lewe ani prawego nawiasu ostrego. Podczas dopasowywania prawego nawiasu ostrego, przypisz podciąg między `Open` grupy i bieżącą grupę do `Close` , a następnie usunąć definicji `Open` grupy. Jest to trzecia grupa przechwytywania.|  
|`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*`|Zgodne zero lub więcej wystąpień następującego wzorca: jeden lub więcej wystąpień lewego nawiasu ostrego następuje zero lub więcej znaków nawiasu ostrego następuje jeden lub więcej wystąpień prawego nawiasu ostrego, a następnie zero lub więcej wystąpień z systemem innym niż — nawiasy. Podczas dopasowywania prawego nawiasu ostrego, usuń definicję `Open` , a następnie przypisać podciąg między `Open` grupy i bieżącą grupę do `Close` grupy. Jest to pierwsza grupa przechwytywania.|  
|`(?(Open)(?!))`|Jeśli `Open` grupa istnieje, Porzuć dopasowania, jeśli ciąg pusty można dopasować, ale nie przekazują pozycja aparat wyrażeń regularnych w ciągu. Jest to potwierdzenie zerowej szerokości ujemna wyprzedzenia. Ponieważ ciąg pusty jest zawsze niejawnie występuje w ciągu wejściowym, tego dopasowania nie zawsze powiedzie się. Błąd tego dopasowania wskazuje, że nawiasy są niezrównoważone.|  
|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
 Końcowe Podwyrażenie `(?(Open)(?!))`, wskazuje, czy zagnieżdżanie konstruuje w ciągu wejściowym prawidłowo równoważy (na przykład, czy każdy lewego nawiasu ostrego są dopasowane wg prawego nawiasu ostrego). Używa warunkowego dopasowania oparte na prawidłową grupę przechwyconych; Aby uzyskać więcej informacji, zobacz [konstrukcje Alternacyjne](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md). Jeśli `Open` grupy jest określona, aparat wyrażeń regularnych próbuje dopasować Podwyrażenie `(?!)` w ciągu wejściowym. `Open` Grupy powinien być zdefiniowany tylko wtedy, gdy niezrównoważonej konstrukcje zagnieżdżenia. W związku z tym wzorzec do dopasowania w ciągu wejściowym należy zawsze powoduje dopasowanie niepowodzenia. W takim przypadku `(?!)` jest potwierdzenie wyprzedzenia ujemna zerowej szerokości która zawsze kończy się niepowodzeniem, ponieważ ciąg pusty jest zawsze niejawnie obecne w następnej pozycji w ciągu wejściowym.  
  
 W tym przykładzie aparat wyrażeń regularnych ocenia ciąg wejściowy "\<abc >< mno\<xyz >>" jak pokazano w poniższej tabeli.  
  
|Krok|Wzorzec|Wynik|  
|----------|-------------|------------|  
|1|`^`|Rozpoczyna się na początku ciąg wejściowy dopasowania|  
|2|`[^<>]*`|Wyszukuje znaki nawiasu ostrego przed lewego nawiasu ostrego; znajdzie żadnych wyników.|  
|3|`(((?'Open'<)`|Dopasowuje lewego nawiasu ostrego w "\<abc >", a następnie przypisuje go do `Open` grupy.|  
|4|`[^<>]*`|Dopasowuje "abc".|  
|5|`)+`|"< abc" to wartość drugiego przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest lewego nawiasu ostrego, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|6|`((?'Close-Open'>)`|Odpowiada prawego nawiasu ostrego w "\<abc >", "abc", czyli podciąg przypisuje między `Open` grupy i pod kątem nawiasów do `Close` , a następnie usuwa bieżącą wartość ("<") z `Open` grupy, zostawiać je puste.|  
|7|`[^<>]*`|Wyszukuje znaki nawiasu ostrego po prawego nawiasu ostrego; Umożliwia znalezienie żadnych wyników.|  
|8|`)+`|Wartość trzeciego przechwycone grupy jest ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawego nawiasu ostrego, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|9|`)*`|Wartość pierwszego przechwyconej grupy jest "\<abc >".<br /><br /> Następny znak w ciągu wejściowym jest lewego nawiasu ostrego, więc aparat wyrażeń regularnych pętli do `(((?'Open'<)` podciąg wzorca.|  
|10|`(((?'Open'<)`|Dopasowuje lewego nawiasu ostrego w "\<mno >", a następnie przypisuje go do `Open` grupy. Jego <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> teraz kolekcja zawiera pojedynczą wartość, "<".|  
|11|`[^<>]*`|Dopasowuje "mno".|  
|12|`)+`|"< mno" to wartość drugiego przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym jest lewego nawiasu ostrego, więc aparat wyrażeń regularnych pętli do `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|13|`(((?'Open'<)`|Dopasowuje lewego nawiasu ostrego w "\<xyz >", a następnie przypisuje go do `Open` grupy. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Kolekcja `Open` grupy zawiera teraz dwa przechwytywania: lewego nawiasu ostrego z "\<mno >" i lewego nawiasu ostrego z "\<xyz >".|  
|14|`[^<>]*`|Dopasowuje "xyz".|  
|15|`)+`|"< xyz" to wartość drugiego przechwyconej grupy.<br /><br /> Następny znak w ciągu wejściowym nie jest lewego nawiasu ostrego, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(?'Open'<)[^<>]*)` podciąg wzorca.|  
|16|`((?'Close-Open'>)`|Dopasowuje prawego nawiasu ostrego w "\<xyz >". "xyz" przypisuje podciąg między `Open` grupy i pod kątem nawiasów do `Close` , a następnie usuwa bieżącą wartość `Open` grupy. Wartość poprzedniej przechwytywania (lewego nawiasu ostrego w "\<mno >") staje się bieżącą wartość `Open` grupy. <xref:System.Text.RegularExpressions.Group.Captures%2A> Kolekcja `Open` grupy zawiera teraz jeden przechwytywania, lewego nawiasu ostrego z "\<xyz >".|  
|17|`[^<>]*`|Wyszukuje znaki nawiasu ostrego; Umożliwia znalezienie żadnych wyników.|  
|18|`)+`|Wartość trzeciego przechwycone grupy jest ">".<br /><br /> Następny znak w ciągu wejściowym jest prawego nawiasu ostrego, więc aparat wyrażeń regularnych pętli do `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|19|`((?'Close-Open'>)`|Dopasowuje końcowego prawego nawiasu ostrego w "xyz >>", przypisuje "mno\<xyz >" (podciąg między `Open` grupy i prawego nawiasu ostrego) do `Close` , a następnie usuwa bieżącą wartość `Open` grupy. `Open` Grupa jest obecnie pusta.|  
|20|`[^<>]*`|Wyszukuje znaki nawiasu ostrego; Umożliwia znalezienie żadnych wyników.|  
|21|`)+`|Wartość trzeciego przechwycone grupy jest ">".<br /><br /> Następny znak w ciągu wejściowym nie jest prawego nawiasu ostrego, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `((?'Close-Open'>)[^<>]*)` podciąg wzorca.|  
|22|`)*`|Wartość pierwszego przechwyconej grupy jest "< mno\<xyz >>".<br /><br /> Następny znak w ciągu wejściowym nie jest lewego nawiasu ostrego, więc aparat wyrażeń regularnych nie sprzężenia zwrotnego `(((?'Open'<)` podciąg wzorca.|  
|23|`(?(Open)(?!))`|`Open` Grupy nie jest zdefiniowany, więc nie zostanie podjęta.|  
|24|`$`|Dopasowuje koniec ciągu wejściowego.|  
  
<a name="noncapturing_group"></a>   
## <a name="noncapturing-groups"></a>Grupy niezapamiętywane  
 Poniższa konstrukcja grupowania nie przechwycić podciągu, który jest uwzględniony przez podwyrażenia:  
  
```  
(?:subexpression)  
```  
  
 gdzie *Podwyrażenie* jest wzorzec wszystkie prawidłowe wyrażenie regularne. Konstrukcja grupy nieprzechwyconej jest zwykle używany podczas kwantyfikator jest stosowane do grupy, ale podciągów przechwycone przez grupę są nie zainteresowań.  
  
> [!NOTE]
>  Jeśli wyrażenie regularne zawiera zagnieżdżone grupowanie konstrukcje, grupa zewnętrzna nieprzechwyconej konstrukcja nie dotyczą konstrukcje wewnętrzny grup zagnieżdżonych.  
  
 Poniższy przykład przedstawia wyrażenie regularne, która obejmuje grup nieprzechwyconych. Należy pamiętać, że dane wyjściowe nie zawiera żadnych przechwytywane grup.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/noncapture1.cs#5)]
 [!code-vb[RegularExpressions.Language.Grouping#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/noncapture1.vb#5)]  
  
 Wyrażenie regularne `(?:\b(?:\w+)\W*)+\.` odpowiada zdania, zostanie zakończony kropką. Ponieważ wyrażenia regularnego koncentruje się na zdania, a nie na poszczególnych wyrazów, konstrukcji grupowania służą wyłącznie jako Kwantyfikatory. Wzorzec wyrażenia regularnego jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?:\w+)`|Dopasowuje co najmniej jeden znak słowa. Nie należy przypisywać dopasowany tekst do przechwyconej grupy.|  
|`\W*`|Zgodne zero lub więcej znaków niż word.|  
|`(?:\b(?:\w+)\W*)+`|Zgodne wzorca co najmniej jeden znak word, zaczynając od granicy word, następuje zero lub więcej znaków niż word, jeden lub więcej razy. Nie należy przypisywać dopasowany tekst do przechwyconej grupy.|  
|`\.`|Odpowiada danym okresie.|  
  
<a name="group_options"></a>   
## <a name="group-options"></a>Opcje grupy  
 Poniższa konstrukcja grupowania stosuje lub wyłącza określonych opcji w podwyrażenia:  
  
 `(?imnsx-imnsx:` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest wzorzec wszystkie prawidłowe wyrażenie regularne. Na przykład `(?i-s:)` włącza liter i wyłącza tryb pojedynczej linii. Aby uzyskać więcej informacji na temat opcji wbudowany, można określić, zobacz [opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
> [!NOTE]
>  Możesz określić opcje, które mają zastosowanie do całego wyrażenia regularnego zamiast podwyrażenia przy użyciu <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktora klasy lub metody statycznej. Można również określić opcje wbudowany, które są stosowane po stanie z określonego momentu w wyrażeniu regularnym przy użyciu `(?imnsx-imnsx)` konstrukcji języka.  
  
 Konstrukcja opcje grupy nie jest grupą przechwytywania. Oznacza to mimo że jakiejkolwiek jego części ciągu przechwycony przez *Podwyrażenie* jest uwzględniona w dopasowania, jest nie zawarte w przechwyconej grupy ani służące do wypełniania <xref:System.Text.RegularExpressions.GroupCollection> obiektu.  
  
 Na przykład, wyrażenie regularne `\b(?ix: d \w+)\s` w poniższym przykładzie używa opcji wbudowany w konstrukcji grupowania Włącz dopasowywanie bez uwzględniania wielkości liter i Ignoruj odstępy wzorzec do identyfikowania wszystkie słowa, które zaczynają się od litery "d". Wyrażenie regularne jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?ix: d \w+)`|Za pomocą dopasowywania i zignorowano biały znak w tym wzorcu bez uwzględniania wielkości liter, zgodne "d", po której następuje co najmniej jeden znak programu word.|  
|`\s`|Dopasowuje znak odstępu.|  
  
 [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
<a name="zerowidth_positive_lookahead_assertion"></a>   
## <a name="zero-width-positive-lookahead-assertions"></a>Dodatnie asercje z patrzeniem w przód o zerowej szerokości  
 Poniższa konstrukcja grupowanie definiuje potwierdzenia wyprzedzenia dodatnią zerowej szerokości:  
  
 `(?=` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest żadnych wzorzec wyrażenia regularnego. Pod kątem dopasowania do pomyślnego ciąg wejściowy musi być zgodna ze wzorcem wyrażenia regularnego w *Podwyrażenie*, mimo że podciąg nie znajduje się w wyniku dopasowania. Potwierdzenie wyprzedzenia dodatnią zerowej szerokości nie śledzenie wsteczne.  
  
 Zazwyczaj potwierdzenia wyprzedzenia dodatnią zerowej szerokości znajduje się na końcu wzorzec wyrażenia regularnego. Definiuje podciąg, który musi zostać znaleziony na końcu ciągu do dopasowania występuje, ale które nie powinny znajdować się w dopasowania. Jest również przydatne w przypadku uniemożliwia nadmiernym wykorzystaniem algorytmu wycofywania. Potwierdzenie wyprzedzenia dodatnią zerowej szerokości umożliwia upewnij się, że określonej grupy przechwyconych rozpoczyna się od tekst, który pasuje podzbiór wzorzec zdefiniowane dla tej grupy przechwycony. Na przykład jeśli przechwytywania grupy odpowiada word kolejnych znaków, umożliwia potwierdzenie wyprzedzenia dodatnią zerowej szerokości wymagają pierwszego znaku wielkie litery.  
  
 Następujące przykładowe zastosowania potwierdzenia wyprzedzenia dodatnią zerowej szerokości, aby dopasować słowo, które zlecenie jest wcześniejsza "is" w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#6](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookahead1.cs#6)]
 [!code-vb[RegularExpressions.Language.Grouping#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookahead1.vb#6)]  
  
 Wyrażenie regularne `\b\w+(?=\sis\b)` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`(?=\sis\b)`|Określ, czy znaki word następuje biały znak i ciąg "jest", której kończy się na granicy programu word. Jeśli tak, dopasowanie jest pomyślne.|  
  
<a name="zerowidth_negative_lookahead_assertion"></a>   
## <a name="zero-width-negative-lookahead-assertions"></a>Ujemne asercje z patrzeniem w przód o zerowej szerokości  
 Poniższa konstrukcja grupowanie definiuje potwierdzenia zerowej szerokości wyprzedzenia ujemna:  
  
 `(?!` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest żadnych wzorzec wyrażenia regularnego. Do dopasowania do pomyślnego ciąg wejściowy nie może być zgodna ze wzorcem wyrażenia regularnego w *Podwyrażenie*, mimo że dopasowany ciąg nie jest objęta wynik dopasowania.  
  
 Potwierdzenie zerowej szerokości ujemna wyprzedzenia jest zwykle używana na początku lub na końcu wyrażenia regularnego. Na początku wyrażenia regularnego, zdefiniować określony wzorzec, który nie powinny być zgodne, gdy na początku wyrażenia regularnego definiuje podobne, lecz więcej ogólnych wzorzec do dopasowania. W takim przypadku jest często używany do ograniczania śledzenie wsteczne. Na koniec wyrażenia regularnego zdefiniować Podwyrażenie, który nie może występować na końcu dopasowania.  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, który używa potwierdzenia wyprzedzenia zerowej szerokości na początku wyrażenia regularnego do dopasowania słowa, które nie rozpoczynają się "un".  
  
 [!code-csharp[RegularExpressions.Language.Grouping#7](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead1.cs#7)]
 [!code-vb[RegularExpressions.Language.Grouping#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead1.vb#7)]  
  
 Wyrażenie regularne `\b(?!un)\w+\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(?!un)`|Określanie, czy obok dwa znaki są "un". Jeśli nie, możliwe jest dopasowanie.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 W poniższym przykładzie zdefiniowano wyrażenie regularne, który używa potwierdzenia wyprzedzenia zerowej szerokości na końcu wyrażenia regularnego do dopasowania słowa, które nie kończą się znak interpunkcyjny.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#8](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookahead2.cs#8)]
 [!code-vb[RegularExpressions.Language.Grouping#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookahead2.vb#8)]  
  
 Wyrażenie regularne `\b\w+\b(?!\p{P})` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Dopasowuje co najmniej jeden znak słowa.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
|`\p{P})`|Następny znak nie jest symbol znaki interpunkcyjne (takie jak okres lub przecinkami), dopasowania zakończy się pomyślnie.|  
  
<a name="zerowidth_positive_lookbehind_assertion"></a>   
## <a name="zero-width-positive-lookbehind-assertions"></a>Dodatnie asercje wsteczne o zerowej szerokości  
 Poniższa konstrukcja grupowanie definiuje potwierdzenia dodatnie wybieganie wstecz zerowej szerokości:  
  
 `(?<=` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest żadnych wzorzec wyrażenia regularnego. Dopasowanie do pomyślnej *Podwyrażenie* musi przypadać w ciągu wejściowego na lewo od bieżącego położenia, mimo że `subexpression` nie znajduje się w wyniku dopasowania. Potwierdzenie zerowej szerokości dodatnie wybieganie wstecz nie śledzenie wsteczne.  
  
 Asercje o zerowej szerokości dodatnie wybieganie wstecz są zazwyczaj używane na początku wyrażenia regularne. Wzorzec, które definiują jest warunkiem wstępnym dopasowania, chociaż nie jest częścią wynik dopasowania.  
  
 Na przykład poniższy przykład dopasowuje dwa ostatnie cyfry roku dwudziestego pierwszego wieku (to znaczy wymaga że cyfry "20" poprzedzają dopasowany ciąg).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#9](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/lookbehind1.cs#9)]
 [!code-vb[RegularExpressions.Language.Grouping#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/lookbehind1.vb#9)]  
  
 Wzorzec wyrażenia regularnego `(?<=\b20)\d{2}\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\d{2}`|Zgodne dwóch cyfr dziesiętnych.|  
|`{?<=\b20)`|Nadal dopasowania, jeśli dwa cyfr dziesiętnych są poprzedzone cyfr dziesiętnych "20" na granicy programu word.|  
|`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
 Asercje o zerowej szerokości dodatnie wybieganie wstecz są również używane do ograniczania śledzenie wsteczne podczas ostatni znak lub znaki w przechwyconej grupy muszą być podzbiorem znaków, który jest zgodny z wzorcem wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie znaki kolejnych word, umożliwia potwierdzenie dodatnie wybieganie wstecz zerowej szerokości wymagają alfabetycznej ostatnim znakiem.  
  
<a name="zerowidth_negative_lookbehind_assertion"></a>   
## <a name="zero-width-negative-lookbehind-assertions"></a>Ujemne asercje wsteczne o zerowej szerokości  
 Poniższa konstrukcja grupowanie definiuje potwierdzenia ujemne wybieganie wstecz zerowej szerokości:  
  
 `(?<!` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest żadnych wzorzec wyrażenia regularnego. Dopasowanie do pomyślnej *Podwyrażenie* nie musi przypadać w ciągu wejściowego na lewo od bieżącego położenia. Jednak podciąg, które nie odpowiadają `subexpression` nie znajduje się w wyniku dopasowania.  
  
 Asercje o zerowej szerokości ujemne wybieganie wstecz są zazwyczaj używane na początku wyrażenia regularne. Wzorzec, które definiują wyklucza dopasowania w ciągu, który jest zgodny. Są one również używane do ograniczenia śledzenie wsteczne podczas ostatni znak lub znaki w przechwyconej grupy nie może być jeden lub więcej znaków, które jest zgodny z wzorcem wyrażenia regularnego tej grupy. Na przykład jeśli grupa przechwytuje wszystkie znaki kolejnych word, umożliwia potwierdzenie zerowej szerokości dodatnie wybieganie wstecz wymagana ostatni znak podkreślenia (_) nie jest.  
  
 Poniższy przykład pasuje do daty dla dowolnego dzień tygodnia, który nie jest weekendy (oznacza to, że jest sobota ani niedziela).  
  
 [!code-csharp[RegularExpressions.Language.Grouping#10](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/negativelookbehind1.cs#10)]
 [!code-vb[RegularExpressions.Language.Grouping#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/negativelookbehind1.vb#10)]  
  
 Wzorzec wyrażenia regularnego `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` jest interpretowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`\w+`|Zgodne z co najmniej jeden znak word następuje biały znak.|  
|`\d{1,2},`|Odpowiada jednej lub dwóch cyfr dziesiętnych, następuje biały znak i przecinkami.|  
|`\d{4}\b`|Zgodne cztery cyfry dziesiętne i kończyć dopasowania na granicy programu word.|  
|<code>(?<!(Saturday&#124;Sunday) )</code>|Jeśli dopasowanie jest poprzedzony przez inną niż ciągi, "Sobota" i "Niedziela", po którym następuje spacja, dopasowanie jest pomyślne.|  
  
<a name="nonbacktracking_subexpression"></a>   
## <a name="nonbacktracking-subexpressions"></a>Podwyrażenia bez nawrotów  
 Poniższa konstrukcja grupowania reprezentuje nonbacktracking Podwyrażenie (znanej także jako Podwyrażenie "zachłannego"):  
  
 `(?>` *Podwyrażenie* `)`  
  
 gdzie *Podwyrażenie* jest żadnych wzorzec wyrażenia regularnego.  
  
 Zwykle Jeśli wyrażenie regularne zawiera opcjonalny lub alternatywne dopasowania wzorca i dopasowania nie powiedzie się, aparat wyrażeń regularnych można gałęzi w wielu kierunkach do dopasowania ciągu wejściowego z wzorcem. Jeśli nie znaleziono dopasowania, podczas pierwszej gałęzi, aparat wyrażeń regularnych można utworzyć kopię zapasową lub cofnąć do punktu, w którym zajęło pierwszego dopasowania i spróbuj dopasowania za pomocą drugiego gałęzi. Ten proces można kontynuować do momentu wykonano wszystkie gałęzie.  
  
 `(?>` *Podwyrażenie* `)` języka skonstruować wyłącza śledzenie wsteczne. Aparat wyrażeń regularnych będzie pasował do dowolnej liczby znaków w ciągu wejściowym może. Możliwe jest dalsze dopasowania, będzie śledzenie wsteczne nie ma podjąć próbę dopasowania wzorca alternatywny. (Oznacza to, że Podwyrażenie jest zgodna tylko te ciągi, zgodnych przez samego Podwyrażenie; nie próbuje dopasowanie ciągu na podstawie Podwyrażenie i wszelkie użyto, których przestrzeganie).  
  
 Ta opcja jest zalecana, jeśli wiadomo, że śledzenie wsteczne nie powiedzie się. Aparat wyrażeń regularnych uniemożliwia wykonywanie niepotrzebnych wyszukiwania poprawia wydajność.  
  
 Poniższy przykład przedstawia, jak nonbacktracking Podwyrażenie modyfikuje wyniki dopasowania wzorca. Backtracking wyrażenie regularne dopasowuje pomyślnie szereg powtarzające się znaki następuje jedno wystąpienie tego samego znaku w granicach word, ale nonbacktracking wyrażenia regularnego nie.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#11](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/nonbacktracking1.cs#11)]
 [!code-vb[RegularExpressions.Language.Grouping#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/nonbacktracking1.vb#11)]  
  
 Wyrażenie regularne nonbacktracking `(?>(\w)\1+).\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(\w)`|Dopasowuje znak pojedynczego wyrazu i przypisz je do pierwszej grupy przechwytywania.|  
|`\1+`|Pasuje do wartości pierwszego podciągu przechwyconych jeden lub więcej razy.|  
|`.`|Dopasowuje dowolny znak.|  
|`\b`|W celu dopasowania na granicy programu word.|  
|`(?>(\w)\1+)`|Zgodne jedno lub więcej wystąpień znaku słowa zduplikowane, ale nie śledzenie wsteczne odpowiadające ostatni znak w granicach programu word.|  
  
<a name="Objects"></a>   
## <a name="grouping-constructs-and-regular-expression-objects"></a>Konstrukty grupujące i obiekty wyrażeń regularnych  
 Podciągi dopasowanych przez wyrażenie regularne Przechwytywanie grupy są reprezentowane przez <xref:System.Text.RegularExpressions.Group?displayProperty=nameWithType> obiektów, które mogą być pobierane z <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. <xref:System.Text.RegularExpressions.GroupCollection> Obiektu jest wypełniana w następujący sposób:  
  
-   Pierwszy <xref:System.Text.RegularExpressions.Group> obiektu w kolekcji (obiekt w indeksie zero) reprezentuje cały dopasowania.  
  
-   Zestaw następnej <xref:System.Text.RegularExpressions.Group> reprezentować bez nazwy grup przechwytywania (numerowana). Pojawią się one w kolejności, w którym są definiowane w wyrażeniu regularnym od lewej do prawej. Indeks wartości tych grup w zakresie od 1 do liczby nienazwane przechwytywania grup w kolekcji. (Indeks określonej grupy jest odpowiednikiem jego numerowane dopasowań. Aby uzyskać więcej informacji na temat odwołania wstecznego zobacz [konstrukcje dopasowań](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)  
  
-   Ostatni zestaw <xref:System.Text.RegularExpressions.Group> reprezentować nazwanych grup przechwytywania. Pojawią się one w kolejności, w którym są definiowane w wyrażeniu regularnym od lewej do prawej. Wartość indeksu pierwszego o nazwie grupy przechwytywania jest jeden większa niż indeks ostatniej grupie przechwytywania bez nazwy. Jeśli nie ma nie nienazwane Przechwytywanie grup wyrażenie regularne, wartość indeksu pierwszego o nazwie przechwytywania grupy jest jednym.  
  
 W przypadku zastosowania do przechwytywania grupy, odpowiednie kwantyfikator <xref:System.Text.RegularExpressions.Group> obiektu <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>, <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType>, i <xref:System.Text.RegularExpressions.Capture.Length%2A?displayProperty=nameWithType> właściwości odzwierciedlenia ostatnich podciąg przechwycony przez grupę przechwytywania. Możesz pobrać kompletny zestaw podciągów przechwytywanych przez grupy, które mają Kwantyfikatory z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu, który jest zwracany przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości.  
  
 Poniższy przykład wyjaśnia relacji między <xref:System.Text.RegularExpressions.Group> i <xref:System.Text.RegularExpressions.Capture> obiektów.  
  
 [!code-csharp[RegularExpressions.Language.Grouping#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.grouping/cs/objectmodel1.cs#4)]
 [!code-vb[RegularExpressions.Language.Grouping#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.grouping/vb/objectmodel1.vb#4)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+)\W+)+` wyodrębnia poszczególnych wyrazów z ciągu. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
|`(\w+)`|Dopasowuje co najmniej jeden znak słowa. Te znaki tworzą razem wyrazu. Jest to druga grupa przechwytywania.|  
|`\W+`|Zgodne z co najmniej jeden znak-word.|  
|`(\w+)\W+)+`|Pasuje do wzorca co najmniej jeden znak słowa jednego lub więcej z systemem innym niż word znaków jeden lub więcej razy. Jest to pierwsza grupa przechwytywania.|  
  
 Pierwsza grupa przechwytywania odpowiada każdego wyrazu zdania. Drugiej grupy przechwytywania odpowiada każdego wyrazu oraz znaki interpunkcyjne i białe, który wyrazie. <xref:System.Text.RegularExpressions.Group> Obiektu, którego indeks jest 2 zawiera informacje o tekst uwzględniony przez drugiej grupy przechwytywania. Pełny zestaw wyrazów przechwycone przez Przechwytywanie grupy są dostępne z <xref:System.Text.RegularExpressions.CaptureCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
