---
title: Kwantyfikatory w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
ms.openlocfilehash: dbfe4422b89b6223988ec9c6034d4b91b6ec8b5d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276151"
---
# <a name="quantifiers-in-regular-expressions"></a>Kwantyfikatory w wyrażeniach regularnych
Kwantyfikatory określają, ile wystąpień znaku, grupy lub klasy znaków musi być obecne w danych wejściowych, aby można było znaleźć dopasowanie.  W poniższej tabeli wymieniono Kwantyfikatory obsługiwane przez platformę .NET.  
  
|Kwantyfikator zachłanne|Kwantyfikator z opóźnieniem|Opis|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Dopasowanie zero lub więcej razy.|  
|`+`|`+?`|Dopasowuje jeden lub więcej razy.|  
|`?`|`??`|Dopasowuje zero lub jeden raz.|  
|`{`*n*`}`|`{`*n*`}?`|Dopasowuje dokładnie *n* razy.|  
|`{`*n*`,}`|`{`*n*`,}?`|Dopasowanie co najmniej *n* razy.|  
|`{`*n* `,` *m*`}`|`{`*n* `,` *m*`}?`|Dopasowuje od *n* do *m* razy.|  
  
 Ilości `n` i `m` są stałymi całkowitymi. Zwykle Kwantyfikatory są zachłanne; powodują, że aparat wyrażeń regularnych dopasowuje jako wiele wystąpień określonych wzorców, jak to możliwe. Dołączanie `?` znaku do kwantyfikatora powoduje jego odłączenie. powoduje to, że aparat wyrażeń regularnych dopasowuje jak najmniejszej liczby wystąpień. Aby uzyskać pełny opis różnicy między zachłanne i kwantyfikatorami z opóźnieniem, zobacz sekcję [zachłanne i Kwantyfikatory z opóźnieniem](#Greedy) w dalszej części tego tematu.  
  
> [!IMPORTANT]
> Zagnieżdżanie kwantyfikatorów (na przykład jako wzorca wyrażenia regularnego `(a*)*` ) może zwiększyć liczbę porównań, które musi wykonać aparat wyrażeń regularnych, jako funkcję wykładniczą liczby znaków w ciągu wejściowym. Aby uzyskać więcej informacji na temat tego zachowania i jego obejść [, zobacz](backtracking-in-regular-expressions.md)wycofywanie.  
  
## <a name="regular-expression-quantifiers"></a>Kwantyfikatory wyrażeń regularnych  
 W poniższych sekcjach wymieniono Kwantyfikatory obsługiwane przez wyrażenia regularne programu .NET.  
  
> [!NOTE]
> Jeśli znaki *, +,?, {i} są napotkane we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych interpretuje je jako Kwantyfikatory lub część konstrukcji kwantyfikatora, chyba że znajdują się w [klasie znaków](character-classes-in-regular-expressions.md). Aby interpretować te jako znaki literału poza klasą znaków, należy je zmienić, poprzedzając je ukośnikiem odwrotnym. Na przykład ciąg `\*` we wzorcu wyrażenia regularnego jest interpretowany jako literał gwiazdki (" \* ").  
  
### <a name="match-zero-or-more-times-"></a>Dopasowanie zero lub więcej razy: *  
 `*`Kwantyfikator dopasowuje poprzedni element zero lub więcej razy. Jest to odpowiednik `{0,}` kwantyfikatora. `*`jest kwantyfikatorem zachłanne, którego odpowiednikiem opóźnionym jest `*?` .  
  
 Poniższy przykład ilustruje to wyrażenie regularne. Dziewięć cyfr w ciągu wejściowym, pięć pasuje do wzorca i cztery (,, `95` `929` `9219` i `9919` ) nie.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`91*`|Dopasowuje "9", po którym następuje zero lub więcej znaków "1".|  
|`9*`|Dopasowuje zero lub więcej znaków "9".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-one-or-more-times-"></a>Dopasowuje jeden lub więcej razy: +  
 `+`Kwantyfikator dopasowuje poprzedni element jeden lub więcej razy. Jest równoważne `{1,}` . `+`jest kwantyfikatorem zachłanne, którego odpowiednikiem opóźnionym jest `+?` .  
  
 Na przykład wyrażenie regularne `\ban+\w*?\b` próbuje dopasować całe wyrazy, które zaczynają się od litery, `a` po którym następuje co najmniej jedno wystąpienie litery `n` . Poniższy przykład ilustruje to wyrażenie regularne. Wyrażenie regularne pasuje do wyrazów `an` , `annual` , `announcement` , i `antique` i prawidłowo nie można dopasować `autumn` i `all` .  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an+`|Dopasowuje "a", po którym następuje co najmniej jeden znak "n".|  
|`\w*?`|Dopasowuje znak słowa zero lub więcej razy, ale tyle razy, ile to możliwe.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-zero-or-one-time-"></a>Dopasowanie zero lub jeden raz:?  
 `?`Kwantyfikator dopasowuje poprzedni element zero lub jeden raz. Jest równoważne `{0,1}` . `?`jest kwantyfikatorem zachłanne, którego odpowiednikiem opóźnionym jest `??` .  
  
 Na przykład wyrażenie regularne `\ban?\b` próbuje dopasować całe wyrazy rozpoczynające się od litery, `a` po której następuje zero lub jedno wystąpienie litery `n` . Innymi słowy, próbuje dopasować słowa `a` i `an` . Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`an?`|Dopasowuje "a", po którym następuje zero lub jeden znak "n".|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-exactly-n-times-n"></a>Dopasuj dokładnie n razy: {n}  
 Kwantyfikator `{` *n* `}` dopasowuje poprzedni element dokładnie *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `}` jest kwantyfikatorem zachłanne, którego odpowiednik opóźniony to `{` *n* `}?` .  
  
 Na przykład wyrażenie regularne `\b\d+\,\d{3}\b` próbuje dopasować granicę wyrazu, po którym następuje co najmniej jedna cyfra dziesiętna, po której następują trzy cyfry dziesiętne, a po niej granicę wyrazu. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d+`|Dopasowanie do co najmniej jednej cyfry dziesiętnej.|  
|`\,`|Dopasowuje znak przecinka.|  
|`\d{3}`|Dopasowuje trzy cyfry dziesiętne.|  
|`\b`|Kończy na granicy wyrazu.|  
  
### <a name="match-at-least-n-times-n"></a>Dopasowuje co najmniej n razy: {n,}  
 Kwantyfikator `{` *n* `,}` dopasowuje poprzedni element co najmniej *n* razy, gdzie *n* jest dowolną liczbą całkowitą. `{`*n* `,}` jest kwantyfikatorem zachłanne, którego odpowiednik opóźniony to `{` *n* `,}?` .  
  
 Na przykład wyrażenie regularne `\b\d{2,}\b\D+` próbuje dopasować granicę wyrazu, po którym następuje co najmniej dwie cyfry, po których następuje granica słowa i znak niebędący cyfrą. Poniższy przykład ilustruje to wyrażenie regularne. Wyrażenie regularne nie pasuje do frazy `"7 days"` , ponieważ zawiera tylko jedną cyfrę dziesiętną, ale pomyślnie dopasowuje frazy `"10 weeks and 300 years"` .  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\d{2,}`|Dopasowuje co najmniej dwie cyfry dziesiętne.|  
|`\b`|Dopasowuje granicę wyrazu.|  
|`\D+`|Dopasowuje co najmniej jedną cyfrę niedziesiętną.|  
  
### <a name="match-between-n-and-m-times-nm"></a>Dopasowanie między n i m razy: {n, m}  
 Kwantyfikator `{` *n* `,` *m* `}` dopasowuje poprzedni element co najmniej *n* razy, ale nie więcej niż *m* razy, gdzie *n* i *m* są liczbami całkowitymi. `{`*n* `,` *m* `}` jest kwantyfikatorem zachłanne, którego odpowiednik opóźniony to `{` *n* `,` *m* `}?` .  
  
 W poniższym przykładzie wyrażenie regularne `(00\s){2,4}` próbuje dopasować między dwoma i czterema wystąpieniami dwóch cyfr zerowych, po których występuje spacja. Należy zauważyć, że końcowa część ciągu wejściowego zawiera ten wzorzec pięć razy, a nie maksymalnie cztery. Jednak tylko początkowa część tego podciągu (do spacji i piąta para zer) pasuje do wzorca wyrażenia regularnego.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Dopasowuje zero lub więcej razy (dopasowanie z opóźnieniem): *?  
 `*?`Kwantyfikator dopasowuje poprzedzający element zero lub więcej razy, ale tyle razy, ile to możliwe. Jest odpowiednikiem z opóźnieniem kwantyfikatora zachłanne `*` .  
  
 W poniższym przykładzie wyrażenie regularne `\b\w*?oo\w*?\b` dopasowuje wszystkie wyrazy, które zawierają ciąg `oo` .  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`\w*?`|Dopasowuje zero lub więcej znaków słowa, ale jak najmniejsza liczba znaków.|  
|`oo`|Dopasowuje ciąg "oo".|  
|`\w*?`|Dopasowuje zero lub więcej znaków słowa, ale jak najmniejsza liczba znaków.|  
|`\b`|Koniec na granicy słowa.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Dopasowuje jeden lub więcej razy (dopasowanie z opóźnieniem): +?  
 `+?`Kwantyfikator dopasowuje poprzedni element jeden lub więcej razy, ale jak najszybciej, jak to możliwe. Jest odpowiednikiem z opóźnieniem kwantyfikatora zachłanne `+` .  
  
 Na przykład wyrażenie regularne `\b\w+?\b` dopasowuje co najmniej jeden znak rozdzielony przez granice słowa. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Dopasowuje zero lub jeden raz (dopasowanie z opóźnieniem):?  
 `??`Kwantyfikator dopasowuje poprzedni element zero lub jeden raz, ale tyle razy, ile to możliwe. Jest odpowiednikiem z opóźnieniem kwantyfikatora zachłanne `?` .  
  
 Na przykład wyrażenie regularne `^\s*(System.)??Console.Write(Line)??\(??` próbuje dopasować ciągi "Console. Write" lub "Console. WriteLine". Ciąg może również zawierać "system". przed "konsolą" i może następować nawias otwierający. Ciąg musi znajdować się na początku wiersza, chociaż może być poprzedzony białym znakiem. Poniższy przykład ilustruje to wyrażenie regularne.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`^`|Dopasowuje początek strumienia wejściowego.|  
|`\s*`|Dopasowanie do zera lub większej liczby znaków odstępu.|  
|`(System.)??`|Dopasowanie do zera lub jednego wystąpienia ciągu "System.".|  
|`Console.Write`|Dopasowuje ciąg "Console. Write".|  
|`(Line)??`|Dopasowanie do zera lub jednego wystąpienia ciągu "line".|  
|`\(??`|Dopasowanie do zera lub jednego wystąpienia nawiasu otwierającego.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Dopasuj dokładnie n razy (dopasowanie z opóźnieniem): {n}?  
 Kwantyfikator `{` *n* `}?` dopasowuje poprzedni element dokładnie `n` raz, gdzie *n* jest dowolną liczbą całkowitą. Jest to odpowiednik opóźniony kwantyfikatora zachłanne `{` *n* `}` .  
  
 W poniższym przykładzie wyrażenie regularne `\b(\w{3,}?\.){2}?\w{3,}?\b` służy do identyfikowania adresu witryny sieci Web. Należy pamiętać, że pasuje do "www.microsoft.com" i "msdn.microsoft.com", ale nie pasuje do "Website" lub "mycompany.com".  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`(\w{3,}?\.)`|Dopasowuje co najmniej 3 znaki słowa, ale jak najmniejsza liczba znaków, po których następuje znak kropki lub kropki. Jest to pierwsza grupa przechwytywania.|  
|`(\w{3,}?\.){2}?`|Dopasowuje wzorzec w pierwszej grupie dwa razy, ale tyle razy, ile to możliwe.|  
|`\b`|Zakończ dopasowanie na granicy słowa.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Dopasowuje co najmniej n razy (dopasowanie z opóźnieniem): {n,}?  
 Kwantyfikator `{` *n* `,}?` dopasowuje poprzedni element co najmniej `n` razy, gdzie *n* jest dowolną liczbą całkowitą, ale tyle razy, ile to możliwe. Jest to odpowiednik opóźniony kwantyfikatora zachłanne `{` *n* `,}` .  
  
 Zobacz przykład dla `{` *n* `}?` kwantyfikatora n w poprzedniej sekcji dla ilustracji. Wyrażenie regularne w tym przykładzie używa `{` *n* `,}` kwantyfikatora n, aby dopasować ciąg, który zawiera co najmniej trzy znaki, po których następuje kropka.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Dopasowanie między n i m razy (dopasowanie z opóźnieniem): {n, m}?  
 Kwantyfikator `{` *n* `,` *m* `}?` dopasowuje poprzedni element między `n` i `m` Times, gdzie *n* i *m* są liczbami całkowitymi, ale tyle razy, ile to możliwe. Jest to odpowiednik opóźniony kwantyfikatora zachłanne `{` *n* `,` *m* `}` .  
  
 W poniższym przykładzie wyrażenie regularne `\b[A-Z](\w*?\s*?){1,10}[.!?]` dopasowuje zdania zawierające od jednego do dziesięciu wyrazów. Dopasowuje wszystkie zdania w ciągu wejściowym z wyjątkiem jednego zdania zawierającego 18 wyrazów.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|`[A-Z]`|Dopasowuje wielką literę od A do Z.|  
|`(\w*?\s*?)`|Dopasowuje zero lub więcej znaków wyrazu, po którym następuje co najmniej jeden znak odstępu, ale tyle razy, ile to możliwe. Jest to pierwsza grupa przechwytywania.|  
|`{1,10}`|Dopasowuje poprzedni wzorzec od 1 do 10 razy.|  
|`[.!?]`|Dopasowuje dowolny z tych znaków interpunkcyjnych ".", "!" lub "?".|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a>Zachłanne i Kwantyfikatory z opóźnieniem  
 Liczba kwantyfikatorów ma dwie wersje:  
  
- Wersja zachłanne.  
  
     Kwantyfikator zachłanne próbuje dopasować element tyle razy, ile to możliwe.  
  
- Wersja innego typu niż zachłanne (lub z opóźnieniem).  
  
     Kwantyfikator inny niż zachłanne próbuje dopasować element jak najprawdopodobniej, jak to możliwe. Kwantyfikator zachłanne można przekształcić w kwantyfikator z opóźnieniem, po prostu dodając `?` .  
  
 Rozważ proste wyrażenie regularne, które jest przeznaczone do wyodrębnienia ostatnich czterech cyfr z ciągu cyfr, takich jak numer karty kredytowej. Wersja wyrażenia regularnego, która używa `*` kwantyfikatora zachłanne `\b.*([0-9]{4})\b` . Jeśli jednak ciąg zawiera dwie liczby, to wyrażenie regularne dopasowuje się do ostatnich czterech cyfr w drugiej liczbie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 Wyrażenie regularne nie dopasowuje pierwszej liczby `*` , ponieważ kwantyfikator próbuje dopasować poprzedni element tyle razy, ile jest to możliwe w całym ciągu, i dlatego znalazł jego dopasowanie na końcu ciągu.  
  
 Nie jest to pożądane zachowanie. Zamiast tego można użyć `*?` kwantyfikatora opóźnionego do wyodrębnienia cyfr z obu liczb, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 W większości przypadków wyrażenia regularne z zachłanne i kwantyfikatorów opóźnionych zwracają te same dopasowania. Najczęściej zwracają różne wyniki, gdy są używane z symbolem wieloznacznym ( `.` ), który dopasowuje dowolny znak.  
  
## <a name="quantifiers-and-empty-matches"></a>Kwantyfikatory i puste dopasowania  
 Kwantyfikatory `*` , `+` i `{` *n* `,` *m* `}` i ich odpowiedniki z opóźnieniem nigdy nie powtarzają się po pustym dopasowaniu po znalezieniu minimalnej liczby przechwytywania. Ta reguła uniemożliwia kwantyfikatorom wprowadzanie nieskończonych pętli przy pustym podrażeniu, gdy maksymalna liczba możliwych przechwycenia grupy jest nieskończona lub bliska nieskończoność.  
  
 Na przykład poniższy kod ilustruje wynik wywołania <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody z wzorcem wyrażenia regularnego `(a?)*` , który odpowiada zero lub jeden znak "a" zero lub więcej razy. Należy zauważyć, że pojedyncza grupa przechwytywania przechwytuje każdy "a" <xref:System.String.Empty?displayProperty=nameWithType> , ale nie ma drugiego pustego dopasowania, ponieważ pierwsze puste dopasowanie powoduje, że kwantyfikator przestanie powtarzać się.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Aby zobaczyć praktyczną różnicę między grupą przechwytywania, która definiuje minimalną i maksymalną liczbę przechwytywania, i jedną, która definiuje stałą liczbę przechwytywania, należy wziąć pod uwagę wzorce wyrażeń regularnych `(a\1|(?(1)\1)){0,2}` i `(a\1|(?(1)\1)){2}` . Oba wyrażenia regularne składają się z pojedynczej grupy przechwytywania, która jest zdefiniowana w poniższej tabeli.  
  
|Wzorce|Opis|  
|-------------|-----------------|  
|`(a\1`|Dopasowuje wartość "a" wraz z wartością pierwszej przechwyconej grupy...|  
|<code>&#124;(?(1)</code>|… lub Przetestuj, czy pierwsza przechwycona Grupa została zdefiniowana. (Należy zauważyć, że `(?(1)` konstrukcja nie definiuje grupy przechwytywania).|  
|`\1))`|W przypadku istnienia pierwszej przechwyconej grupy Dopasuj jej wartość. Jeśli grupa nie istnieje, grupa będzie pasować <xref:System.String.Empty?displayProperty=nameWithType> .|  
  
 Pierwsze wyrażenie regularne próbuje dopasować ten wzorzec od zera do dwóch razy; sekunda, dokładnie dwa razy. Ze względu na to, że pierwszy wzorzec osiągnie swoją minimalną liczbę przechwytywania z pierwszym przechwyceniem <xref:System.String.Empty?displayProperty=nameWithType> , nigdy nie powtarza się, aby spróbować dopasować `a\1` ; `{0,2}` kwantyfikator dopuszcza tylko puste dopasowania w ostatniej iteracji. Natomiast drugie wyrażenie regularne dopasowuje się do "a", ponieważ szacuje `a\1` drugi raz; minimalna liczba iteracji, 2, wymusza powtarzanie aparatu po pustym dopasowaniu.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)
- [Nawracanie](backtracking-in-regular-expressions.md)
