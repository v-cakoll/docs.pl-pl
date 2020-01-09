---
title: Zachowanie wyrażenia regularnego
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
ms.openlocfilehash: af812e1e42d57c349e94b5992b768636857d2a0c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348281"
---
# <a name="details-of-regular-expression-behavior"></a>Szczegóły zachowania wyrażeń regularnych

Aparat wyrażeń regularnych .NET Framework to wsteczny odpowiednik wyrażenia regularnego, który zawiera tradycyjny, Niedeterministyczny aparat usługi Automation (NFA), taki jak używany przez język Perl, Python, Emacs: i TCL. Odróżnia to od szybszego, ale bardziej ograniczone, czyste wyrażenie regularne deterministycznie skończone usługi Automation (DFA), takie jak te, które znajdują się w AWK, egrep lub Lex. Odróżnia to również od standaryzacji, ale wolniejsze, NFAs POSIX. W poniższej sekcji opisano trzy typy aparatów wyrażeń regularnych i wyjaśniono, dlaczego wyrażenia regularne w .NET Framework są implementowane przy użyciu tradycyjnego aparatu NFA.

## <a name="benefits-of-the-nfa-engine"></a>Zalety aparatu NFA

 Gdy aparaty DFA wykonują dopasowanie do wzorca, ich kolejność przetwarzania jest określana przez ciąg wejściowy. Aparat rozpoczyna się na początku ciągu wejściowego i przechodzi sekwencyjnie, aby określić, czy następny znak jest zgodny ze wzorcem wyrażenia regularnego. Mogą one zagwarantować, że najdłuższy ciąg będzie możliwy. Ponieważ nigdy nie testują tego samego znaku dwa razy, aparaty DFA nie obsługują wycofywania. Jednak ponieważ aparat DFA zawiera tylko skończoną wartość, nie może pasować do wzorca z odwołaniami wstecznymi i ponieważ nie konstruuje jawnego rozszerzania, nie może przechwycić podwyrażeń.

 W przeciwieństwie do aparatów DFA, gdy tradycyjne aparaty NFA wykonują dopasowywanie do wzorców, ich kolejność przetwarzania jest oparta na wzorcu wyrażenia regularnego. Ponieważ przetwarza określony element języka, aparat używa dopasowywania zachłanne; oznacza to, że jest ona zgodna ze zbyt dużą ilością ciągu wejściowego, jak to możliwe. Ale również zapisuje swój stan po pomyślnym dopasowaniu podwyrażenia. Jeśli dopasowanie zakończyło się niepowodzeniem, aparat może powrócić do zapisanego stanu, aby umożliwić wypróbowanie dodatkowych dopasowań. Ten proces porzucania dopasowania podwyrażenia powiodło się, aby późniejsze elementy języka w wyrażeniu regularnym mogły być również zgodne *z wycofywaniem.* Silniki NFA używają wycofywania do testowania wszystkich możliwych rozszerzeń wyrażenia regularnego w określonej kolejności i akceptują pierwsze dopasowanie. Ze względu na to, że tradycyjny aparat NFA konstruuje określone rozszerzenie wyrażenia regularnego dla sukcesu, może przechwycić dopasowania podwyrażenia i pasujące odwołania wsteczne. Jednak ze względu na to, że tradycyjne NFA, mogą odwiedzać ten sam stan wielokrotnie, jeśli dociera do stanu dla różnych ścieżek. W związku z tym może działać wykładniczo powoli w najgorszym przypadku. Ze względu na to, że tradycyjny aparat NFA akceptuje pierwsze znalezione dopasowanie, może również pozostawić inne (prawdopodobnie dłużej) dopasowania niewykrywalne.

 Aparaty NFA POSIX są podobne do tradycyjnych aparatów NFA, z tą różnicą, że nadal są nawrotu, dopóki nie będą mogły zagwarantować, że wystąpiły najdłuższe dopasowanie. W efekcie aparat NFA systemu POSIX jest wolniejszy niż tradycyjny aparat NFA i w przypadku korzystania z aparatu NFA POSIX nie można preferować krótszego dopasowania przez zmianę kolejności wyszukiwania wycofywania.

 Tradycyjne aparaty NFA są preferowane przez programistów, ponieważ oferują większą kontrolę nad dopasowaniem ciągu niż aparaty DFA lub POSIX NFA. Mimo że w najgorszym przypadku mogą one działać wolno, można przełączać je, aby znaleźć dopasowania w liniowym lub wieloznacznym czasie, używając wzorców, które zmniejszają niejasności i ograniczają wycofywanie. Innymi słowy, chociaż silniki NFAją wydajność wymiany dla mocy i elastyczności, w większości przypadków zapewnia ona akceptowalną wydajność, jeśli wyrażenie regularne jest dobrze zapisywane i unika przypadków, w których wycofywanie obniża wydajność.

> [!NOTE]
> Aby uzyskać informacje o tym, jak spadek wydajności spowodowany przez nadmierne wycofywanie i sposoby [rozłożenia wyrażenia](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)regularnego do obejść, zobacz wycofywanie.

## <a name="net-framework-engine-capabilities"></a>Możliwości aparatu .NET Framework

 Aby skorzystać z zalet tradycyjnego aparatu NFA, aparat wyrażeń regularnych .NET Framework zawiera kompletny zestaw konstrukcji umożliwiających programistom sterownie aparatem wycofywania. Konstrukcje te mogą służyć do szybszego znajdowania dopasowania lub w celu uzyskania określonych rozszerzeń dla innych.

 Inne funkcje aparatu wyrażeń regularnych .NET Framework są następujące:

- Kwantyfikatory opóźnione: `??`, `*?`, `+?``{`*n*`,`*m*`}?`. Te konstrukcje informują aparat wycofywania, aby najpierw przeszukać minimalną liczbę powtórzeń. W przeciwieństwie do zwykłych kwantyfikatorów zachłanne spróbuj najpierw dopasować maksymalną liczbę powtórzeń. Poniższy przykład ilustruje różnicę między nimi. Wyrażenie regularne dopasowuje zdanie kończące się na liczbie, a grupa przechwytywania jest przeznaczona do wyodrębnienia tej liczby. Wyrażenie regularne `.+(\d+)\.` zawiera `.+`kwantyfikatora zachłanne, co powoduje, że aparat wyrażeń regularnych przechwytuje tylko ostatnią cyfrę liczby. Z kolei wyrażenie regularne `.+?(\d+)\.` zawiera `.+?`kwantyfikatora z opóźnieniem, co powoduje, że aparat wyrażeń regularnych przechwytuje całą liczbę.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Wersje zachłanne i z opóźnieniem tego wyrażenia regularnego są zdefiniowane, jak pokazano w poniższej tabeli:

    |Wzorzec|Opis|
    |-------------|-----------------|
    |`.+` (kwantyfikator zachłanne)|Dopasowuje co najmniej jedno wystąpienie dowolnego znaku. Powoduje to, że aparat wyrażeń regularnych dopasowuje cały ciąg, a następnie do nawrotu w razie potrzeby dopasowania do pozostałej części wzorca.|
    |`.+?` (kwantyfikator opóźniony)|Dopasowuje co najmniej jedno wystąpienie dowolnego znaku, ale dopasowanie jak najmniejszej liczby.|
    |`(\d+)`|Dopasowuje co najmniej jeden znak liczbowy i przypisuje go do pierwszej grupy przechwytywania.|
    |`\.`|Dopasowuje okres.|

     Aby uzyskać więcej informacji na temat kwantyfikatorów z opóźnieniem, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).

- Pozytywne wyprzedzenie: `(?=`*podwyrażeniem*`)`. Ta funkcja pozwala aparatowi wycofywania na powrót do tego samego miejsca w tekście po dopasowaniu podwyrażenia. Jest to przydatne do wyszukiwania w całym tekście przez zweryfikowanie wielu wzorców, które zaczynają się od tego samego położenia. Umożliwia także aparatowi sprawdzenie, czy podciąg istnieje na końcu dopasowania bez uwzględniania podciągu w dopasowanym tekście. W poniższym przykładzie użyto pozytywnego naprzód w celu wyodrębnienia wyrazów w zdaniu, które nie poprzedzają symboli interpunkcyjnych.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     Wyrażenie regularne `\b[A-Z]+\b(?=\P{P})` jest zdefiniowane, jak pokazano w poniższej tabeli.

    |Wzorzec|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`[A-Z]+`|Dopasowuje dowolny znak alfabetyczny jeden lub więcej razy. Ponieważ metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> jest wywoływana z opcją <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>, porównanie nie uwzględnia wielkości liter.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|
    |`(?=\P{P})`|Zapoznaj się z wyprzedzeniem, aby określić, czy następny znak jest symbolem interpunkcji. Jeśli tak nie jest, dopasowanie powiedzie się.|

     Aby uzyskać więcej informacji na temat pozytywnych potwierdzeń z wyprzedzeniem, zobacz [Grouping konstrukcjes](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Ujemne naprzód: `(?!`*podwyrażeniem*`)`. Ta funkcja dodaje możliwość dopasowania wyrażenia tylko w przypadku niepowodzenia dopasowania podwyrażenia. Jest to szczególnie zaawansowane w przypadku oczyszczania wyszukiwania, ponieważ często jest prostsze, aby podać wyrażenie dla przypadku, które należy wyeliminować niż wyrażenie dla przypadków, które muszą być uwzględnione. Na przykład trudno jest napisać wyrażenie dla słów, które nie zaczynają się od "non". W poniższym przykładzie zastosowano ujemne naprzód, aby je wykluczyć.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     `\b(?!non)\w+\b` wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.

    |Wzorzec|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`(?!non)`|Sprawdź w przód, aby upewnić się, że bieżący ciąg nie zaczyna się od "non". W przeciwnym razie dopasowanie nie powiedzie się.|
    |`(\w+)`|Dopasowuje co najmniej jeden znak słowa.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|

     Aby uzyskać więcej informacji na temat negatywnych potwierdzeń naprzód, zobacz [grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Ocena warunkowa: `(?(`*expression*`)`*tak*`|`*nie*`)` i `(?(`*Nazwa*`)`*tak*`|`*nie*`)`, gdzie *wyrażenie* jest zgodne z wyrażeniem, *Nazwa* jest nazwą grupy przechwytywania, *tak* jest ciąg do dopasowania, jeśli wyrażenie jest dopasowane lub *Nazwa* jest prawidłową, niepustą grupą, a *nie* jest podwyrażeniem, aby *dopasować wyrażenie IF*nie jest dopasowany lub *Nazwa* nie jest prawidłową, niepustą grupą przechwyconą. Ta funkcja umożliwia aparatowi wyszukiwanie przy użyciu więcej niż jednego wzorca alternatywnego, w zależności od wyniku poprzedniego dopasowania podwyrażenia lub wyniku potwierdzeń o zerowej szerokości. Pozwala to na bardziej wydajną postać odwołania, która pozwala na przykład dopasować Podwyrażenie w zależności od tego, czy poprzednie Podwyrażenie zostało dopasowane. Wyrażenie regularne w poniższym przykładzie dopasowuje akapity, które są przeznaczone do użytku publicznego i wewnętrznego. Akapity przeznaczone tylko do użytku wewnętrznego zaczynają się od tagu `<PRIVATE>`. Wzorzec wyrażenia regularnego `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` używa oceny warunkowej do przypisywania zawartości akapitów przeznaczonych do użytku publicznego oraz do wewnętrznego użycia w celu oddzielenia grup przechwytywania. Te akapity mogą być następnie obsługiwane inaczej.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.

    |Wzorzec|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij dopasowanie na początku wiersza.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Dopasowanie do zera lub jednego wystąpienia ciągu `<PRIVATE>` po którym następuje znak odstępu. Przypisz dopasowanie do grupy przechwytywania o nazwie `Pvt`.|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Jeśli istnieje `Pvt` grupy przechwytywania, dopasowuje jedno lub więcej wystąpień jednego lub większej liczby znaków słowa, po których następuje zero lub jeden separator interpunkcji, po którym następuje znak odstępu. Przypisz podciąg do pierwszej grupy przechwytywania.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|Jeśli grupa przechwytywania `Pvt` nie istnieje, dopasowuje jedno lub więcej wystąpień jednego lub większej liczby znaków słowa, po których następuje zero lub jeden separator interpunkcji, po którym następuje znak odstępu. Przypisz podciąg do trzeciej grupy przechwytywania.|
    |`\r?$`|Dopasowuje koniec wiersza lub koniec ciągu.|

     Aby uzyskać więcej informacji na temat oceny warunkowej, zobacz [konstrukcje warunkowe](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).

- Definicje grup równoważenia: `(?<`*name1*`-`*NAME2*`>` *podwyrażenia*`)`. Ta funkcja umożliwia aparatowi wyrażeń regularnych śledzenie zagnieżdżonych konstrukcji, takich jak nawiasy, otwierające i zamykające nawiasy klamrowe. Aby zapoznać się z przykładem, zobacz [grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Podwyrażenia Podwyrażenie (znane również jako zachłanne subexpressions): `(?>`*podwyrażeniem*`)`. Ta funkcja umożliwia aparatowi wycofywania w celu zagwarantowania, że Podwyrażenie dopasowuje tylko pierwsze dopasowanie znalezione dla tego podwyrażenia, tak jakby wyrażenie było uruchomione niezależnie od jego wyrażenia zawierającego. Jeśli ta konstrukcja nie jest używana, wyszukiwanie wsteczne z większego wyrażenia może zmienić zachowanie podwyrażenia. Na przykład wyrażenie regularne `(a+)\w` dopasowuje jeden lub więcej znaków "a", wraz ze znakiem słowa, które następuje po sekwencji znaków "a" i przypisuje sekwencję znaków "a" do pierwszej grupy przechwytywania, jednak jeśli końcowy znak ciągu wejściowego jest również "a", jest dopasowywany przez element języka `\w` i nie jest uwzględniony w przechwyconej grupie.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     Wyrażenie regularne `((?>a+))\w` uniemożliwia takie zachowanie. Ponieważ wszystkie kolejne znaki "a" są dopasowywane bez wycofywania, pierwsza grupa przechwytywania zawiera wszystkie kolejne znaki "a". Jeśli po znaku "a" nie występuje co najmniej jeden znak inny niż "a", dopasowanie nie powiedzie się.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Aby uzyskać więcej informacji o podwyrażeniach Podwyrażenie, zobacz [Grouping konstrukcjes](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Dopasowanie od prawej do lewej, które jest określone przez dostarczenie opcji <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> do konstruktora klasy <xref:System.Text.RegularExpressions.Regex> lub statycznej metody dopasowywania wystąpień. Ta funkcja jest przydatna podczas wyszukiwania od prawej do lewej zamiast od lewej do prawej lub w przypadkach, gdy jest bardziej wydajna, aby zacząć dopasowywanie do prawej części wzorca zamiast z lewej strony. Jak pokazano na poniższym przykładzie, użycie dopasowania od prawej do lewej może zmienić zachowanie kwantyfikatorów zachłanne. Przykład wykonuje dwa wyszukiwania zdania kończącego się na liczbie. Wyszukiwanie od lewej do prawej, które używa kwantyfikatora zachłanne `+` dopasowuje jeden z sześciu cyfr w zdaniu, podczas gdy wyszukiwanie od prawej do lewej jest zgodne ze wszystkimi sześcioma cyframi. Aby uzyskać opis wzorca wyrażenia regularnego, zobacz przykład, który ilustruje liczbę kwantyfikatorów opóźnionych wcześniej w tej sekcji.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Aby uzyskać więcej informacji na temat dopasowywania do prawej strony, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).

- Dodatnie i ujemne asercja wsteczna: `(?<=`*Podwyrażenie*`)` dla dodatnich asercja wsteczna, i `(?<!`*podwyrażeniem*`)` dla negatywnej asercja wsteczna. Ta funkcja jest podobna do wyprzedzenia, która została omówiona wcześniej w tym temacie. Ponieważ aparat wyrażeń regularnych umożliwia pełne dopasowywanie do prawej strony, wyrażenia regularne zezwalają na nieograniczony lookbehinds. Można również użyć asercja wsteczna pozytywnej i ujemnej, aby uniknąć zagnieżdżania kwantyfikatorów, gdy zagnieżdżone Podwyrażenie jest nadzbiorem wyrażenia zewnętrznego. Wyrażenia regularne z takimi kwantyfikatorami zagnieżdżonymi często zapewniają niską wydajność. Na przykład poniższy przykład sprawdza, czy ciąg rozpoczyna się i zamyka znak alfanumeryczny, a każdy inny znak w ciągu jest jednym z większego podzbioru. Stanowi część wyrażenia regularnego służącego do sprawdzania poprawności adresów e-mail. Aby uzyskać więcej informacji, zobacz [How to: Sprawdź, czy ciągi są w prawidłowym formacie poczty E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     Wyrażenie regularne ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` jest zdefiniowane, jak pokazano w poniższej tabeli.

    |Wzorzec|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij dopasowanie na początku ciągu.|
    |`[A-Z0-9]`|Dopasowuje dowolny znak liczbowy lub alfanumeryczny. (W porównaniu z rozróżnianiem wielkości liter).|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Dopasowuje zero lub więcej wystąpień dowolnego znaku słowa lub dowolny z następujących znaków:-,!, #, $,%, &,,,,, \*, +,/, =,?, ^, &#96;, {,}, &#124;lub ~.|
    |`(?<=[A-Z0-9])`|Odszukaj w powyższym znaku, który musi być numeryczny lub alfanumeryczny. (W porównaniu z rozróżnianiem wielkości liter).|
    |`$`|Zakończ dopasowanie na końcu ciągu.|

     Aby uzyskać więcej informacji na temat pozytywnych i negatywnych asercja wsteczna, zobacz [Grouping konstrukcjes](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="related-articles"></a>Pokrewne artykuły:

|Stanowisko|Opis|
|-----------|-----------------|
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Zawiera informacje dotyczące sposobu, w jaki rozgałęzienia wyrażenia regularnego do znajdowania alternatywnych dopasowań.|
|[Kompilacja i ponowne używanie](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Zawiera informacje dotyczące kompilowania i ponownego używania wyrażeń regularnych w celu zwiększenia wydajności.|
|[Bezpieczeństwo wątków](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Zawiera informacje na temat bezpieczeństwa wątku wyrażeń regularnych i wyjaśnia, kiedy należy synchronizować dostęp do obiektów wyrażeń regularnych.|
|[.NET Framework wyrażeń regularnych](../../../docs/standard/base-types/regular-expressions.md)|Zawiera omówienie aspektu języka programowania wyrażeń regularnych.|
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu ilustrujące sposób użycia klas wyrażeń regularnych.|
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują użycie wyrażeń regularnych we wspólnych aplikacjach.|
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje dotyczące zestawu znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|

## <a name="reference"></a>Tematy pomocy

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
