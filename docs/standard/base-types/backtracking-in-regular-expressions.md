---
title: Wycofywanie w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak kontrolować wycofywanie we wzorcu wyrażenia regularnego.
ms.date: 11/12/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, backtracking
- alternative matching patterns
- optional matching patterns
- searching with regular expressions, backtracking
- pattern-matching with regular expressions, backtracking
- backtracking
- regular expressions [.NET Framework], backtracking
- strings [.NET Framework], regular expressions
- parsing text with regular expressions, backtracking
ms.assetid: 34df1152-0b22-4a1c-a76c-3c28c47b70d8
ms.custom: seodec18
ms.openlocfilehash: 6504430f94f800bb9f41761ad64c65fefecb68d6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968258"
---
# <a name="backtracking-in-regular-expressions"></a>Śledzenie wsteczne w wyrażeniach regularnych
Wycofywanie występuje, gdy wzorzec wyrażenia regularnego zawiera opcjonalne [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) lub [konstrukcje warunkowe](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md), a aparat wyrażeń regularnych powraca do poprzedniego zapisanego stanu, aby kontynuować wyszukiwanie zgodności. Wycofywanie stanowi podstawę dużych możliwości wyrażeń regularnych, ponieważ dzięki niemu wyrażenia oferują duże możliwości i są elastyczne, a także umożliwiają dopasowywanie bardzo złożonych wzorców. Jednocześnie te możliwości są obciążone kosztami. Wycofywanie często jest najważniejszym czynnikiem wpływającym na wydajność aparatu wyrażeń regularnych. Na szczęście deweloper ma kontrolę nad zachowaniem aparatu wyrażeń regularnych i sposobem użycia wycofywania. W tym temacie opisano zasadę działania wycofywania i możliwości sterowania nim.  
  
> [!NOTE]
> Ogólnie rzecz biorąc, Niedeterministyczny usługi Automation (NFA), taki jak aparat wyrażeń regularnych programu .NET, jest odpowiedzialny za efektywne, szybkie wyrażenia regularne na deweloperach.  

## <a name="linear-comparison-without-backtracking"></a>Porównanie liniowe bez wycofywania  
 Jeśli wzorzec wyrażenia regularnego nie ma opcjonalnych kwantyfikatorów ani konstrukcji zmiany, aparat wyrażeń regularnych wykonuje go liniowo. Oznacza to, że gdy aparat wyrażeń regularnych znajdzie pierwszy element języka ze wzorca w tekście w ciągu wejściowym, próbuje dopasować następny element języka ze wzorca do następnego znaku lub grupy znaków w ciągu wejściowym. Ten proces jest kontynuowany do czasu, aż dopasowywanie zakończy się pomyślnie lub niepomyślnie. W każdym przypadku aparat wyrażeń regularnych przesuwa się w danej chwili o jeden znak do przodu w ciągu wejściowym.  
  
 Poniższy przykład stanowi ilustrację. Wyrażenie regularne `e{2}\w\b` wyszukuje dwa wystąpienia litery "e", po której następuje dowolny znak słowa, po którym następuje granica wyrazu.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 Chociaż to wyrażenie regularne zawiera `{2}`kwantyfikatora, jest ona oceniana w sposób liniowy. Aparat wyrażeń regularnych nie nawrotu, ponieważ `{2}` nie jest opcjonalnym kwantyfikatorem; określa dokładną liczbę, a nie zmienną liczbę przypadków, w których poprzednie Podwyrażenie musi być zgodne. W wyniku tego aparat wyrażeń regularnych próbuje dopasować wzorzec wyrażenia regularnego do ciągu wejściowego, tak jak pokazano w poniższej tabeli.  
  
|Operacja|Pozycja we wzorcu|Pozycja w ciągu|Wynik|  
|---------------|-------------------------|------------------------|------------|  
|1|e|„needing a reed” (indeks 0)|Brak dopasowania.|  
|2|e|„eeding a reed” (indeks 1)|Możliwe dopasowanie.|  
|3|{2} e|„eding a reed” (indeks 2)|Możliwe dopasowanie.|  
|4|\w|„ding a reed” (indeks 3)|Możliwe dopasowanie.|  
|5|\b|„ing a reed” (indeks 4)|Możliwe dopasowanie nie powiodło się.|  
|6|e|„eding a reed” (indeks 2)|Możliwe dopasowanie.|  
|7|{2} e|„ding a reed” (indeks 3)|Możliwe dopasowanie nie powiodło się.|  
|8|e|„ding a reed” (indeks 3)|Dopasowanie nie powiodło się.|  
|9|e|„ing a reed” (indeks 4)|Brak dopasowania.|  
|10|e|„ng a reed” (indeks 5)|Brak dopasowania.|  
|11|e|„g a reed” (indeks 6)|Brak dopasowania.|  
|12|e|"a Reed" (indeks 7)|Brak dopasowania.|  
|13|e|"a Reed" (indeks 8)|Brak dopasowania.|  
|14,5|e|"Reed" (indeks 9)|Brak dopasowania.|  
|15000|e|"Reed" (indeks 10)|Brak dopasowania.|  
|16|e|„eed” (indeks 11)|Możliwe dopasowanie.|  
|7|{2} e|„ed” (indeks 12)|Możliwe dopasowanie.|  
|postanowienia|\w|„d” (indeks 13)|Możliwe dopasowanie.|  
|19|\b|„” (indeks 14)|Dopasowanie.|  
  
 Jeśli wzorzec wyrażenia regularnego nie zawiera opcjonalnych kwantyfikatorów ani konstrukcji zmiany, maksymalna liczba porównań niezbędna do wykonania dopasowania wzorca wyrażenia regularnego do ciągu wejściowego jest w przybliżeniu równa liczbie znaków w ciągu wejściowym. W tym przypadku aparat wyrażeń regularnych wykonuje 19 porównań w celu zidentyfikowania możliwych dopasowań w 13-znakowy ciągu.  Innymi słowy, aparat wyrażeń regularnych działa prawie liniowo, jeśli nie zawiera opcjonalnych kwantyfikatorów ani konstrukcji zmiany.   

## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>Wycofywanie z użyciem opcjonalnych kwantyfikatorów lub konstrukcji zmiany  
 Gdy wyrażenie regularne zawiera opcjonalne kwantyfikatory lub konstrukcje zmiany, obliczenia wykonywane na ciągu wejściowym nie są już liniowe. Dopasowywanie wzorca za pomocą aparatu NFA jest oparte na elementach języka w wyrażeniu regularnym, a nie na znakach, które mają zostać dopasowane w ciągu wejściowym. Dlatego aparat wyrażeń regularnych próbuje w pełni dopasować opcjonalne lub alternatywne podwyrażenia. Kiedy aparat wyrażeń regularnych przechodzi do następnego elementu języka w podwyrażeniu i wykonanie dopasowania nie jest możliwe, może porzucić część pomyślnie wykonanego dopasowania i powrócić do wcześniejszego zapisanego stanu dopasowywania wyrażenia regularnego jako całości w ciągu wejściowym. Ten proces wracania do poprzednio zapisanego stanu w celu znalezienia dopasowania jest nazywany wycofywaniem.  
  
 Rozważmy na przykład wzorzec wyrażenia regularnego `.*(es)`, który dopasowuje znaki "es" i wszystkie znaki poprzedzające ją. W poniższym przykładzie pokazano, że jeśli ciągiem wejściowym jest ciąg „Essential services are provided by regular expressions.”, wzorzec dopasowuje cały ciąg aż do znaków „es” w wyrazie „expressions” włącznie.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 W tym celu aparat wyrażeń regularnych używa wycofywania, tak jak opisano poniżej:  
  
- Dopasowuje `.*` (które dopasowuje zero, jeden lub więcej wystąpień dowolnego znaku) za pomocą całego ciągu wejściowego.  
  
- Podejmuje próbę dopasowania znaku „e” we wzorcu wyrażenia regularnego. Jednak ciąg wejściowy nie zawiera już znaków, z którymi można by wykonać porównanie.  
  
- Aparat wycofuje się więc do ostatniego pomyślnego dopasowania (Essential services are provided by regular expressions) i podejmuje próbę dopasowania litery „e” do kropki na końcu zdania. Nie można utworzyć takiego dopasowania.  
  
- Aparat kontynuuje wycofywanie do poprzedniego pomyślnego dopasowania po jednym znaku, aż wykryje, że pasującym podciągiem jest „Essential services are provided by regular expr”. Następnie porównuje znak „e” we wzorcu z drugą literą „e” w wyrazie „expressions” i znajduje dopasowanie.  
  
- Porównuje znak „s” we wzorcu z literą „s” występującą po dopasowanym znaku „e” (pierwsza litera „s” w wyrazie „expressions”). Dopasowanie jest wykonywane pomyślnie.  
  
 Gdy jest używane wycofywanie, wykonanie dopasowania wzorca wyrażenia regularnego do ciągu wejściowego składającego się z 55 znaków wymaga wykonania 67 operacji porównania. Ogólnie, jeśli wzorzec wyrażenia regularnego zawiera jedną konstrukcję zmiany lub jeden opcjonalny kwantyfikator, liczba operacji porównania wymaganych do wykonania dopasowania wzorca jest ponad dwa razy większa niż liczba znaków w ciągu wejściowym.   

## <a name="backtracking-with-nested-optional-quantifiers"></a>Wycofywanie z użyciem zagnieżdżonych opcjonalnych kwantyfikatorów  
 Liczba operacji porównania wymaganych do wykonania dopasowania wzorca wyrażenia regularnego rośnie wykładniczo, gdy wzorzec zawiera dużą liczbę konstrukcji zmiany, jeśli zawiera zagnieżdżone konstrukcje zmiany lub, co występuje najczęściej, zawiera zagnieżdżone kwantyfikatory opcjonalne. Na przykład wzorzec wyrażenia regularnego `^(a+)+$` został zaprojektowany tak, aby pasował do kompletnego ciągu, który zawiera jeden lub więcej znaków "a". W przykładzie podano dwa ciągi wejściowe o identycznej długości, ale tylko pierwszy ciąg pasuje do wzorca. Klasa <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> służy do określenia, jak długo trwa operacja dopasowania.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 Jak wynika z danych wyjściowych z przykładu, aparat wyrażeń regularnych potrzebuje prawie dwa razy więcej czasu na ustalenie, że ciąg wejściowy nie pasuje do wzorca, niż na zidentyfikowanie pasującego ciągu. Jest to spowodowane tym, że niepowodzenie tworzenia dopasowania zawsze jest scenariuszem najgorszego przypadku. Aparat wyrażeń regularnych musi użyć wyrażenia regularnego, aby sprawdzić wszystkie możliwe ścieżki w danych, zanim będzie mógł uznać, że nie można wykonać dopasowania, a zagnieżdżone nawiasy powodują powstanie wielu dodatkowych ścieżek w danych. Aparat wyrażeń regularnych dochodzi do wniosku, że drugi ciąg nie pasuje do wzorca, wykonując następujące czynności:  
  
- Sprawdza, czy znajdował się na początku ciągu, a następnie dopasowuje pięć pierwszych znaków w ciągu z wzorcem `a+`. Następnie ustala, że w ciągu nie znajdują się dodatkowe grupy liter „a”. Na końcu sprawdza, czy znajduje się na końcu ciągu. W ciągu pozostał jeden dodatkowy znak, więc wykonywanie dopasowania kończy się niepowodzeniem. To nieudane dopasowanie wymaga wykonania 9 porównań. Aparat wyrażeń regularnych zapisuje też informacje o stanie swoich dopasowań znaku „a” (dopasowanie 1), znaków „aa” (dopasowanie 2), znaków „aaa” (dopasowanie 3) i znaków „aaaa” (dopasowanie 4).  
  
- Aparat powraca do uprzednio zapisanego dopasowania 4. Ustala, że istnieje jeden dodatkowy znak „a”, który można przypisać do dodatkowej przechwyconej grupy. Na końcu sprawdza, czy znajduje się na końcu ciągu. W ciągu pozostał jeden dodatkowy znak, więc wykonywanie dopasowania kończy się niepowodzeniem. To dopasowanie nie powiodło się wymaga 4 porównań. Do tego momentu zostało wykonanych 13 porównań.  
  
- Powraca do wcześniej zapisanego dopasowania 3. Ustala, że istnieją dwa dodatkowe znaki „a”, które można przypisać do dodatkowej przechwyconej grupy. Jednak test końca ciągu kończy się niepowodzeniem. Następnie aparat wraca do dopasowania 3 i próbuje dopasować dwa dodatkowe znaki „a” w dwóch dodatkowych przechwyconych grupach. Test końca ciągu nadal kończy się niepowodzeniem. Te nieudane dopasowania wymagały wykonania 12 porównań. Do tej pory zostały wykonane wszystkie 25 porównań.  
  
 Porównywanie ciągu wejściowego z wyrażeniem regularnym w ten sposób będzie kontynuowane, dopóki aparat wyrażeń regularnych nie wypróbuje wszystkich możliwych kombinacji dopasowań, a następnie uzna, że nie istnieje dopasowanie. Ze względu na zagnieżdżone kwantyfikatory to porównanie jest operacją O (2<sup>n</sup>) lub wykładniczą, gdzie *n* to liczba znaków w ciągu wejściowym. Oznacza to, że w najgorszym przypadku ciąg wejściowy o długości 30 znaków będzie wymagał wykonania ok. 1 073 741 824 porównań, a ciąg wejściowy o długości 40 znaków będzie wymagał wykonania ok. 1 099 511 627 776 porównań. Gdy są używane ciągi o takiej lub większej długości, wykonanie metod opartych na wyrażeniach regularnych może trwać niezwykle długo, jeśli w przetwarzanych ciągach nie będą znajdować się dopasowania do wzorca wyrażenia regularnego. 

## <a name="controlling-backtracking"></a>Sterowanie wycofywaniem  
 Wycofywanie umożliwia tworzenie zaawansowanych, elastycznych wyrażeń regularnych. Jednak, tak jak pokazano w poprzedniej sekcji, ich zalety może przesłonić nieakceptowalnie niska wydajność. Aby zapobiec nadmiernemu śledzeniu, należy zdefiniować interwał limitu czasu podczas tworzenia wystąpienia obiektu <xref:System.Text.RegularExpressions.Regex> lub wywołania statycznej metody dopasowania wyrażenia regularnego. Ta czynność została omówiona w następnej sekcji. Ponadto platforma .NET obsługuje trzy elementy języka wyrażeń regularnych, które ograniczają lub pomijają funkcję wycofywania oraz obsługują złożone wyrażenia regularne z małą ilością lub brakiem wydajności: [Podwyrażenie subexpressions](#nonbacktracking-subexpression), [asercja wsteczna potwierdzenia](#lookbehind-assertions)i [potwierdzenia naprzód](#lookahead-assertions). Aby uzyskać więcej informacji na temat każdego elementu języka, zobacz [Grouping konstrukcjes](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  

### <a name="defining-a-time-out-interval"></a>Definiowanie interwału limitu czasu  
 Począwszy od .NET Framework 4,5, można ustawić wartość limitu czasu reprezentującą najdłuższy interwał, przez który aparat wyrażeń regularnych będzie wyszukiwać pojedyncze dopasowanie, zanim porzuca próbę i zgłosi wyjątek <xref:System.Text.RegularExpressions.RegexMatchTimeoutException>. Należy określić interwał limitu czasu, dostarczając wartość <xref:System.TimeSpan> do konstruktora <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> dla wyrażeń regularnych wystąpienia. Ponadto każda statyczna metoda dopasowywania do wzorca ma Przeciążenie z parametrem <xref:System.TimeSpan>, który pozwala określić wartość limitu czasu. Domyślnie interwał limitu czasu jest ustawiony na <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType> i aparat wyrażeń regularnych nie przekroczy limitu czasu.  
  
> [!IMPORTANT]
> Zalecane jest, aby zawsze ustawić interwał limitu czasu, jeśli w wyrażeniu regularnym jest stosowane wycofywanie.  
  
 Wyjątek <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> wskazuje, że aparat wyrażeń regularnych nie mógł znaleźć dopasowania w określonym interwale limitu czasu, ale nie wskazuje dlaczego wyjątek został zgłoszony. Przyczyną może być nadmierne wycofywanie, ale możliwe jest też, że ustawiono zbyt krótki interwał limitu czasu w stosunku do obciążenia systemu w chwili zgłoszenia wyjątku. Podczas obsługi tego wyjątku można określić, że nie mają być wykonywane kolejne porównania z ciągiem wejściowym, albo zwiększyć interwał limitu czasu i ponowić próbę wykonania operacji dopasowywania.  
  
 Na przykład poniższy kod wywołuje konstruktora <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, aby utworzyć wystąpienie obiektu <xref:System.Text.RegularExpressions.Regex> z wartością limitu czasu jedną sekundą. Wzorzec wyrażenia regularnego `(a+)+$`, który dopasowuje co najmniej jedną sekwencję składającą się z co najmniej jednego znaku "a" na końcu wiersza, podlega nadmiernemu śledzeniu. Jeśli zostanie zgłoszony <xref:System.Text.RegularExpressions.RegexMatchTimeoutException>, w przykładzie zostanie zwiększona wartość limitu czasu do maksymalnie trzech sekund. Po upływie tego czasu nie będą już podejmowane próby dopasowania wzorca.  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  

### <a name="nonbacktracking-subexpression"></a>Podwyrażenie bez wycofywania  
 Podwyrażenie `(?>``)` element języka pomija wycofywanie w wyrażeniu podwyrażenia. Jest to użyteczne w rozwiązywaniu problemów z wydajnością związanych z nieudanymi dopasowaniami.  
  
 W poniższym przykładzie pokazano, w jaki sposób pomijanie wycofywania zwiększa wydajność w sytuacji, gdy są używane kwantyfikatory zagnieżdżone. Mierzony jest czas potrzebny aparatowi wyrażeń regularnych na ustalenie, że ciąg wejściowy nie pasuje do dwóch wyrażeń regularnych. W pierwszym wyrażeniu regularnym jest używane wycofywanie w celu podjęcia próby dopasowania ciągu zawierającego co najmniej jedno wystąpienie co najmniej jednej cyfry szesnastkowej, po której następuje dwukropek, po którym następuje co najmniej jedna cyfra szesnastkowa, po której następują dwa dwukropki. Drugie wyrażenie regularne jest takie samo jak pierwsze, aby wyłączono w nim wycofywanie. Jak widać w wynikach przykładu, wyłączenie wycofywania przynosi znaczącą poprawę wydajności.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  

### <a name="lookbehind-assertions"></a>Asercje wsteczne  
 Platforma .NET zawiera dwa elementy języka, `(?<=`*Podwyrażenie*`)` i `(?<!`*podwyrażenia*`)`, które pasują do poprzedniego znaku lub znaków w ciągu wejściowym. Oba elementy języka są potwierdzeniami o zerowej szerokości; oznacza to, że określają, czy znak lub znaki bezpośrednio poprzedzające bieżący znak mogą być dopasowane przez *Podwyrażenie*, bez przeciągania lub wycofywania.  
  
 `(?<=` *podwyrażeniem* `)` jest pozytywnym potwierdzeniem asercja wsteczna; oznacza to, że znak lub znaki przed bieżącą pozycją muszą pasować do *podwyrażenia*. `(?<!`*podwyrażeniem*`)` jest ujemną asercja wstecznaą; oznacza to, że znak lub znaki przed bieżącą pozycją nie mogą pasować do *podwyrażenia*. Pozytywne i negatywne potwierdzenia asercja wsteczna są najbardziej przydatne, gdy *Podwyrażenie* jest podzbiorem poprzedniego podwyrażenia.  
  
 W poniższym przykładzie są używane dwa równoważne wzorce wyrażeń regularnych, które weryfikują nazwę użytkownika w adresie e-mail. Pierwszy wzorzec działa z niską wydajnością z powodu nadmiernego wycofywania. Drugi wzorzec modyfikuje pierwsze wyrażenie regularne, zastępując zagnieżdżony kwantyfikator pozytywną asercją wsteczną. Dane wyjściowe z przykładu wyświetlają czas wykonywania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 Pierwszy wzorzec wyrażenia regularnego, `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`, jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowywanie na początku ciągu.|  
|`[0-9A-Z]`|Dopasowuje znak alfanumeryczny. W tym porównaniu wielkość liter nie jest rozróżniana, ponieważ metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.|  
|`[-.\w]*`|Dopasowuje zero, jedno lub większą liczbę wystąpień łącznika, kropki lub znaku słowa.|  
|`[0-9A-Z]`|Dopasowuje znak alfanumeryczny.|  
|`([-.\w]*[0-9A-Z])*`|Dopasowuje zero lub większą liczbę wystąpień kombinacji składających się z zera lub większej liczby łączników, kropek lub znaków słowa, po których występuje znak alfanumeryczny. Jest to pierwsza grupa przechwytywania.|  
|`@`|Dopasowuje znak ("\@").|  
  
 Wzorzec drugiego wyrażenia regularnego, `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`, używa pozytywnego potwierdzenia asercja wsteczna. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowywanie na początku ciągu.|  
|`[0-9A-Z]`|Dopasowuje znak alfanumeryczny. W tym porównaniu wielkość liter nie jest rozróżniana, ponieważ metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.|  
|`[-.\w]*`|Dopasowuje zero lub większą liczbę wystąpień łącznika, kropki lub znaku słowa.|  
|`(?<=[0-9A-Z])`|Sprawdza ostatni dopasowany znak i kontynuuje dopasowywanie, jeśli jest to znak alfanumeryczny. Należy zauważyć, że znaki alfanumeryczne stanowią podzestaw zestawu składającego się z kropek, łączników i wszystkich znaków słowa.|  
|`@`|Dopasowuje znak ("\@").|  

### <a name="lookahead-assertions"></a>Asercje wyprzedzające  
 Platforma .NET zawiera dwa elementy języka, `(?=`*Podwyrażenie*`)` i `(?!`*podwyrażenia*`)`, które pasują do następnego znaku lub znaków w ciągu wejściowym. Oba elementy języka są potwierdzeniami o zerowej szerokości; oznacza to, że określają, czy znak lub znaki znajdujące się bezpośrednio po bieżącym znaku mogą być dopasowane przez *Podwyrażenie*, bez przeciągania lub wycofywania.  
  
 `(?=` *podwyrażeniem* `)` jest pozytywnym potwierdzeniem naprzód; oznacza to, że znak lub znaki po bieżącej pozycji muszą pasować do *podwyrażenia*. `(?!`*podwyrażeniem*`)` jest negatywnym potwierdzeniem naprzód; oznacza to, że znak lub znaki po bieżącej pozycji nie mogą pasować do *podwyrażenia*. Pozytywne i negatywne potwierdzenia naprzód są najbardziej przydatne, gdy *Podwyrażenie* jest podzbiorem następnego podwyrażenia.  
  
 W poniższym przykładzie są używane dwa równoważne wzorce wyrażenia regularnego sprawdzające w pełni kwalifikowaną nazwę typu. Pierwszy wzorzec działa z niską wydajnością z powodu nadmiernego wycofywania. Drugi wzorzec modyfikuje pierwsze wyrażenie regularne, zastępując zagnieżdżony kwantyfikator pozytywną asercją wyprzedzającą. Dane wyjściowe z przykładu wyświetlają czas wykonywania metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 Pierwszy wzorzec wyrażenia regularnego, `^(([A-Z]\w*)+\.)*[A-Z]\w*$`, jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowywanie na początku ciągu.|  
|`([A-Z]\w*)+\.`|Dopasowuje znak alfanumeryczny (A–Z), po którym co najmniej raz występuje zero lub większa liczba znaków słowa, po których następuje kropka. W tym porównaniu wielkość liter nie jest rozróżniana, ponieważ metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.|  
|`(([A-Z]\w*)+\.)*`|Dopasowuje poprzedni wzorzec zero lub większą liczbę razy.|  
|`[A-Z]\w*`|Dopasowuje znak alfabetyczny, po którym występuje zero lub większa liczba znaków słowa.|  
|`$`|Dopasowywanie kończy się na końcu ciągu wejściowego.|  
  
 Wzorzec drugiego wyrażenia regularnego, `^((?=[A-Z])\w+\.)*[A-Z]\w*$`, używa pozytywnego potwierdzenia naprzód. Definicję tego wyrażenia pokazano w poniższej tabeli.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowywanie na początku ciągu.|  
|`(?=[A-Z])`|Sprawdza pierwszy następny znak i kontynuuje dopasowywanie, jeśli jest to znak alfabetyczny (A–Z). W tym porównaniu wielkość liter nie jest rozróżniana, ponieważ metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.|  
|`\w+\.`|Dopasowuje co najmniej jeden znak słowa, po którym następuje kropka.|  
|`((?=[A-Z])\w+\.)*`|Dopasowuje wzorzec składający się z co najmniej jednego znaku słowa, po którym zero lub większą liczbę razy występuje kropka. Początkowy znak słowa musi być znakiem alfabetycznym.|  
|`[A-Z]\w*`|Dopasowuje znak alfabetyczny, po którym występuje zero lub większa liczba znaków słowa.|  
|`$`|Dopasowywanie kończy się na końcu ciągu wejściowego.|  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)
- [Konstrukcje warunkowe](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)
- [Konstrukcje grupujące](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)
