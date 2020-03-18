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
ms.openlocfilehash: 504e315dda4e76f56a88d97149b1515b6743668b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124354"
---
# <a name="details-of-regular-expression-behavior"></a>Szczegóły zachowania wyrażeń regularnych

Aparat wyrażeń regularnych .NET Framework jest wstecznym dopasowanie wyrażenia regularnego, który zawiera tradycyjne nondeterministic Finite Automaton (NFA) aparat, takich jak używane przez Perl, Python, Emacs i Tcl. To odróżnia go od szybszych, ale bardziej ograniczone, czystego wyrażenia regularnego Deterministic Finite Automaton (DFA) silników, takich jak te znalezione w awk, egrep, lub lex. To również odróżnia go od standaryzowanych, ale wolniej, POSIX NFAs. W poniższej sekcji opisano trzy typy aparatów wyrażeń regularnych i wyjaśniono, dlaczego wyrażenia regularne w platformie .NET Framework są implementowane przy użyciu tradycyjnego aparatu NFA.

## <a name="benefits-of-the-nfa-engine"></a>Zalety silnika NFA

 Gdy aparaty DFA wykonać dopasowanie wzorca, ich kolejność przetwarzania jest napędzany przez ciąg wejściowy. Aparat rozpoczyna się na początku ciągu wejściowego i przebiega sekwencyjnie, aby ustalić, czy następny znak pasuje do wzorca wyrażenia regularnego. Mogą zagwarantować, aby dopasować najdłuższy ciąg możliwe. Ponieważ nigdy nie testują tego samego znaku dwa razy, aparaty DFA nie obsługują wycofywania. Jednak ponieważ aparat DFA zawiera tylko stan skończony, nie może dopasować wzorca z odwołaniami wstecznymi, a ponieważ nie tworzy jawnego rozszerzenia, nie może przechwytywać wyrażeń podrzędnych.

 W przeciwieństwie do aparatów DFA, gdy tradycyjne aparaty NFA wykonują dopasowywanie wzorców, ich kolejność przetwarzania jest sterowane przez wzorzec wyrażenia regularnego. Podczas przetwarzania określonego elementu języka aparat używa chciwego dopasowania; oznacza to, że pasuje jak najwięcej ciągu wejściowego, jak to możliwe. Ale również zapisuje jego stan po pomyślnym dopasowaniu wyrażenia podrzędnego. Jeśli dopasowanie ostatecznie nie powiedzie się, aparat może powrócić do stanu zapisanego, dzięki czemu można spróbować dodatkowych dopasowań. Ten proces porzucania pomyślnego dopasowania wyrażenia podrzędnego, tak aby późniejsze elementy języka w wyrażeniu regularnym można również dopasować jest znany jako *wycofywania*. Aparaty NFA używają wycofywania do testowania wszystkich możliwych rozszerzeń wyrażenia regularnego w określonej kolejności i akceptowania pierwszego dopasowania. Ponieważ tradycyjny aparat NFA konstruuje określone rozszerzenie wyrażenia regularnego dla pomyślnego dopasowania, może przechwytywać dopasowania wyrażeń podrzędnych i pasujące odwołania wsteczne. Jednak ponieważ tradycyjne backtracks NFA, może odwiedzić ten sam stan wiele razy, jeśli dociera do stanu na różnych ścieżkach. W rezultacie można uruchomić wykładniczo powoli w najgorszym przypadku. Ponieważ tradycyjny aparat NFA akceptuje pierwsze dopasowanie, które znajdzie, może również pozostawić inne (być może dłuższe) dopasowania nieodkryte.

 Silniki POSIX NFA są jak tradycyjne silniki NFA, z tą różnicą, że nadal cofają się, dopóki nie zagwarantują, że znaleźli najdłuższy możliwy mecz. W rezultacie silnik POSIX NFA jest wolniejszy niż tradycyjny aparat NFA, a podczas korzystania z silnika POSIX NFA nie można preferować krótszego dopasowania przez dłuższy, zmieniając kolejność wyszukiwania wstecznego.

 Tradycyjne silniki NFA są preferowane przez programistów, ponieważ oferują większą kontrolę nad dopasowywaniem ciągów niż silniki DFA lub POSIX NFA. Chociaż w najgorszym przypadku mogą działać powoli, można sterować nimi, aby znaleźć dopasowania w czasie liniowym lub wielomianowym za pomocą wzorców, które zmniejszają niejasności i ograniczają wycofywanie. Innymi słowy, chociaż silniki NFA handlu wydajności dla mocy i elastyczności, w większości przypadków oferują one dobre do akceptowalnej wydajności, jeśli wyrażenie regularne jest dobrze napisane i pozwala uniknąć przypadków, w których wycofywanie obniża wydajność wykładniczo.

> [!NOTE]
> Aby uzyskać informacje na temat kary za wykonanie spowodowane przez nadmierne wycofywanie i sposobów tworzenia wyrażenia regularnego, aby obejść je, zobacz [Wycofywanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).

## <a name="net-framework-engine-capabilities"></a>Możliwości aparatu .NET Framework

 Aby skorzystać z zalet tradycyjnego aparatu NFA, aparat wyrażeń regularnych .NET Framework zawiera kompletny zestaw konstrukcji umożliwiających programistom kierowanie aparatem wycofywania. Konstrukcje te mogą być używane do szybszego znajdowania dopasowań lub faworyzowania określonych rozszerzeń nad innymi.

 Inne funkcje aparatu wyrażeń regularnych .NET Framework są następujące:

- Kwantyfikatory `??` `*?`leniwe: , , `+?` `{` *n*`,`*m*`}?`. Te konstrukcje informują wyszukiwarkę wycofywania, aby najpierw przeszukać minimalną liczbę powtórzeń. Natomiast zwykłe chciwe kwantyfikatory próbują najpierw dopasować maksymalną liczbę powtórzeń. Poniższy przykład ilustruje różnicę między tymi dwoma. Wyrażenie regularne pasuje do zdania, które kończy się liczbą, a grupa przechwytywania jest przeznaczona do wyodrębnienia tego numeru. Wyrażenie `.+(\d+)\.` regularne zawiera kwantyfikator `.+`chciwy , co powoduje, że aparat wyrażeń regularnych do przechwytywania tylko ostatnią cyfrę liczby. Natomiast wyrażenie `.+?(\d+)\.` regularne zawiera kwantyfikator `.+?`leniwy , co powoduje, że aparat wyrażeń regularnych do przechwytywania całej liczby.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Chciwi i leniwy wersje tego wyrażenia regularnego są zdefiniowane w sposób pokazany w poniższej tabeli:

    |Wzorce|Opis|
    |-------------|-----------------|
    |`.+`(chciwy kwantyfikator)|Dopasuj co najmniej jedno wystąpienie dowolnego znaku. Powoduje to, że aparat wyrażeń regularnych, aby dopasować cały ciąg, a następnie do backtrack zgodnie z potrzebami, aby dopasować pozostałą część wzorca.|
    |`.+?`(kwantyfikator leniwy)|Dopasuj co najmniej jedno wystąpienie dowolnej postaci, ale dopasuj jak najmniej.|
    |`(\d+)`|Dopasuj co najmniej jeden znak liczbowy i przypisz go do pierwszej grupy przechwytywania.|
    |`\.`|Dopasuj kropkę.|

     Aby uzyskać więcej informacji na temat kwantyfikatorów leniwych, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).

- Pozytywne spojrzenie `(?=`w przyszłość: *podwyrażenie*`)`. Ta funkcja umożliwia aparatowi wycofywania powrót do tego samego miejsca w tekście po dopasowaniu wyrażenia podrzędnego. Jest to przydatne do wyszukiwania w całym tekście, weryfikując wiele wzorców, które zaczynają się od tej samej pozycji. Umożliwia również aparatowi sprawdzenie, czy podciąg istnieje na końcu dopasowania bez uwzględniania podciągu w dopasowanym tekście. W poniższym przykładzie użyto pozytywnego punktu wyjrzenia w przyszłość, aby wyodrębnić wyrazy w zdaniu, po których nie następują symbole interpunkcyjne.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     Wyrażenie `\b[A-Z]+\b(?=\P{P})` regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`[A-Z]+`|Dopasuj dowolny znak alfabetyczny jeden lub więcej razy. Ponieważ <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda jest wywoływana z opcją, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> porównanie jest bez uwzględniania wielkości liter.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|
    |`(?=\P{P})`|Spójrz w przyszłość, aby ustalić, czy następny znak jest symbolem interpunkcyjnym. Jeśli tak nie jest, dopasowanie zakończy się powodzeniem.|

     Aby uzyskać więcej informacji na temat pozytywnych potwierdzeń wyszukiwania, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Negatywne spojrzenie `(?!`w przyszłość: *podwyrażenie*`)`. Ta funkcja dodaje możliwość dopasowania wyrażenia tylko wtedy, gdy wyrażenie podrzędne nie pasuje. Jest to szczególnie skuteczne w przypadku przycinania wyszukiwania, ponieważ często jest to prostsze, aby zapewnić wyrażenie dla sprawy, która powinna zostać wyeliminowana niż wyrażenie w przypadkach, które muszą zostać uwzględnione. Na przykład trudno jest napisać wyrażenie dla słów, które nie zaczynają się od "non". W poniższym przykładzie użyto negatywnego wyglądu, aby je wykluczyć.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     Wzorzec `\b(?!non)\w+\b` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`(?!non)`|Spójrz w przyszłość, aby upewnić się, że bieżący ciąg nie zaczyna się od "non". Jeśli tak, dopasowanie nie powiedzie się.|
    |`(\w+)`|Dopasowuje co najmniej jeden znak słowa.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|

     Aby uzyskać więcej informacji na temat negatywnych potwierdzeń wyszukiwania, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- `(?(`Ocena warunkowa: `(?(` *wyrażenie*`)`*tak*`|`*nie* `)` i *nazwa*`)`*tak*`|`*nie*`)`, gdzie *wyrażenie* jest wyrażeniem podrzędnym do dopasowania, *nazwa* jest nazwą grupy przechwytywania, *tak* jest ciągiem do dopasowania, jeśli *wyrażenie* jest dopasowane lub *nazwa* jest prawidłową, niepustą przechwyconą grupą, a *nie* jest to wyrażenie podrzędne, które ma być zgodne, jeśli wyrażenie jest zgodne, jeśli *wyrażenie *nie jest dopasowana lub *nazwa* nie jest prawidłową, niepustą przechwyconą grupą. Ta funkcja umożliwia wyszukiwarce wyszukiwanie przy użyciu więcej niż jednego wzorca alternatywnego, w zależności od wyniku poprzedniego dopasowania wyrażenia podrzędnego lub wyniku potwierdzenia o zerowej szerokości. Dzięki temu bardziej zaawansowana forma backreference, która pozwala, na przykład, dopasowanie wyrażenia podrzędnego na podstawie tego, czy poprzednie wyrażenie podrzędne zostało dopasowane. Wyrażenie regularne w poniższym przykładzie pasuje do akapitów, które są przeznaczone zarówno do użytku publicznego, jak i wewnętrznego. Akapity przeznaczone tylko do użytku `<PRIVATE>` wewnętrznego zaczynają się od znacznika. Wzorzec `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` wyrażenia regularnego używa oceny warunkowej do przypisywania zawartości akapitów przeznaczonych do publicznego i do użytku wewnętrznego do oddzielania grup przechwytywania. Następnie te akapity mogą być traktowane inaczej.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij mecz na początku linii.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Dopasuj zero lub `<PRIVATE>` jedno wystąpienie ciągu, po którym następuje znak odstępu. Przypisz dopasowanie do grupy `Pvt`przechwytywania o nazwie .|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Jeśli `Pvt` istnieje grupa przechwytywania, dopasuj jedno lub więcej wystąpień jednego lub więcej znaków wyrazu, po których następuje separator zero lub jeden znak interpunkcyjny, po którym następuje znak odstępu. Przypisz podciąg do pierwszej grupy przechwytywania.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|Jeśli `Pvt` grupa przechwytywania nie istnieje, dopasuj jedno lub więcej wystąpień jednego lub więcej znaków wyrazu, po których następuje separator zero lub jeden znak interpunkcyjny, po którym następuje znak odstępu. Przypisz podciąg do trzeciej grupy przechwytywania.|
    |`\r?$`|Dopasuj koniec wiersza lub koniec ciągu.|

     Aby uzyskać więcej informacji na temat oceny warunkowej, zobacz [Konstrukcje zmienne](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).

- Definicje grup bilansujących: `(?<` *name1*`-`*name2* `>` *podwyrażenie*`)`. Ta funkcja umożliwia aparatowi wyrażeń regularnych śledzenie zagnieżdżonych konstrukcji, takich jak nawiasy lub nawiasy otwierające i zamykające. Na przykład zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Grupy atomowe: `(?>` *wyrażenie podrzędne*`)`. Ta funkcja umożliwia aparatowi wycofywania zagwarantowanie, że wyrażenie podrzędne pasuje tylko do pierwszego dopasowania znalezionego dla tego wyrażenia podrzędnego, tak jakby wyrażenie było uruchomione niezależnie od jego wyrażenia zawierającego. Jeśli ta konstrukcja nie zostanie użyje, wycofywanie wyszukiwań z większego wyrażenia może zmienić zachowanie wyrażenia podrzędnego. Na przykład wyrażenie `(a+)\w` regularne pasuje do jednego lub więcej znaków "a" wraz ze znakiem słownym, który następuje po sekwencji znaków "a" i przypisuje sekwencję znaków "a" do pierwszej grupy przechwytywania. Jednak jeśli końcowy znak ciągu wejściowego jest również "a", `\w` jest dopasowywany przez element języka i nie jest uwzględniony w grupie przechwyconych.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     Wyrażenie `((?>a+))\w` regularne zapobiega takiemu zachowaniu. Ponieważ wszystkie kolejne znaki "a" są dopasowywane bez wycofywania, pierwsza grupa przechwytywania zawiera wszystkie kolejne znaki "a". Jeśli po znakach "a" nie następuje co najmniej jeden znak inny niż "a", dopasowanie kończy się niepowodzeniem.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Aby uzyskać więcej informacji na temat grup atomowych, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Dopasowanie od prawej do lewej, które jest <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> określone przez <xref:System.Text.RegularExpressions.Regex> dostarczenie opcji do konstruktora klasy lub metody dopasowywania wystąpienia statycznego. Ta funkcja jest przydatna podczas wyszukiwania od prawej do lewej, a nie od lewej do prawej, lub w przypadkach, gdy bardziej efektywne jest rozpoczęcie dopasowania w prawej części wzorca zamiast w lewo. Jak pokazano w poniższym przykładzie, przy użyciu dopasowania od prawej do lewej można zmienić zachowanie chciwych kwantyfikatorów. Przykład prowadzi dwa wyszukiwania dla zdania, które kończy się liczbą. Wyszukiwanie od lewej do prawej, które używa kwantyfikatora `+` chciwego, pasuje do jednej z sześciu cyfr w zdaniu, podczas gdy wyszukiwanie od prawej do lewej odpowiada wszystkim sześciu cyfrom. Aby uzyskać opis wzorca wyrażenia regularnego, zobacz przykład, który ilustruje kwantyfikatory leniwy wcześniej w tej sekcji.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Aby uzyskać więcej informacji na temat dopasowywania od prawej do lewej, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).

- Pozytywne i negatywne `(?<=`spojrzenie za: *podwyrażenie* `)` `(?<!`dla pozytywnego lookbehind i *podwyrażenie* `)` dla negatywnego lookbehind. Ta funkcja jest podobna do przyszłości, która została omówiona wcześniej w tym temacie. Ponieważ aparat wyrażeń regularnych umożliwia pełne dopasowanie od prawej do lewej, wyrażenia regularne umożliwiają nieograniczone lookbehinds. Dodatnie i negatywne lookbehind można również użyć, aby uniknąć zagnieżdżania kwantyfikatorów, gdy zagnieżdżone podwyrażenie jest nadzbiorem wyrażenia zewnętrznego. Wyrażenia regularne z takimi kwantyfikatorami zagnieżdżonymi często oferują słabą wydajność. Na przykład w poniższym przykładzie sprawdza, czy ciąg zaczyna się i kończy znakiem alfanumerycznym i że każdy inny znak w ciągu jest jednym z większych podzbioru. Stanowi część wyrażenia regularnego używanego do sprawdzania poprawności adresów e-mail; Aby uzyskać więcej informacji, zobacz [Jak: Sprawdź, czy ciągi są w prawidłowym formacie wiadomości e-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     Wyrażenie ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` regularne jest zdefiniowane w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij dopasowanie na początku ciągu.|
    |`[A-Z0-9]`|Dopasuj dowolny znak numeryczny lub alfanumeryczny. (W porównaniu jest bez uwzględniania wielkości liter).|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Dopasuj zero lub więcej wystąpień dowolnego znaku wyrazu lub dowolnego z następujących znaków: \*-, !, #, $, %, &, ', ., ,,+, /, =, ?, ^, &#96;, {, }, &#124; lub ~.|
    |`(?<=[A-Z0-9])`|Spójrz z tyłu na poprzedni znak, który musi być numeryczny lub alfanumeryczny. (W porównaniu jest bez uwzględniania wielkości liter).|
    |`$`|Zakończ dopasowanie na końcu ciągu.|

     Aby uzyskać więcej informacji na temat pozytywnych i negatywnych lookbehind, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="related-articles"></a>Pokrewne artykuły:

|Tytuł|Opis|
|-----------|-----------------|
|[Nawracanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Zawiera informacje o tym, jak wyrażenie regularne wycofywania gałęzi, aby znaleźć alternatywne dopasowania.|
|[Kompilacja i ponowne używanie](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Zawiera informacje dotyczące kompilowania i ponownego używania wyrażeń regularnych w celu zwiększenia wydajności.|
|[Bezpieczeństwo wątków](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Zawiera informacje o bezpieczeństwie wątków wyrażenia regularnego i wyjaśnia, kiedy należy synchronizować dostęp do obiektów wyrażeń regularnych.|
|[.NET Framework — Wyrażenia regularne](../../../docs/standard/base-types/regular-expressions.md)|Zawiera omówienie aspektu języka programowania wyrażeń regularnych.|
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu ilustrujące sposób używania klas wyrażeń regularnych.|
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują użycie wyrażeń regularnych w typowych aplikacjach.|
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje o zestawie znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|

## <a name="reference"></a>Dokumentacja

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
