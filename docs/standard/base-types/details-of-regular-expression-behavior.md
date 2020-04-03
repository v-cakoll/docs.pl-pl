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
ms.openlocfilehash: 0273d16028315452e35f83086dbc134d6fcb66c6
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635987"
---
# <a name="details-of-regular-expression-behavior"></a>Szczegóły zachowania wyrażenia regularnego

Aparat wyrażeń regularnych .NET Framework jest backtracking matcher wyrażenia regularnego, który zawiera tradycyjne nondeterministic Skończony Automaton (NFA) aparat, takich jak używane przez Perl, Python, Emacs i Tcl. To odróżnia go od szybszych, ale bardziej ograniczonych, czystych ekspresji regularnej Deterministic Finite Automaton (DFA) silników, takich jak te znalezione w awk, egrep lub lex. To również odróżnia go od standardowych, ale wolniej, POSIX NFA. W poniższej sekcji opisano trzy typy aparatów wyrażeń regularnych i wyjaśniono, dlaczego wyrażenia regularne w .NET Framework są implementowane przy użyciu tradycyjnego aparatu NFA.

## <a name="benefits-of-the-nfa-engine"></a>Zalety silnika NFA

 Gdy aparaty DFA wykonać dopasowanie wzorca, ich kolejność przetwarzania jest napędzany przez ciąg wejściowy. Aparat rozpoczyna się na początku ciągu wejściowego i przechodzi sekwencyjnie, aby określić, czy następny znak pasuje do wzorca wyrażenia regularnego. Mogą one zagwarantować, aby dopasować najdłuższy ciąg możliwe. Ponieważ nigdy nie testują tego samego znaku dwa razy, aparaty DFA nie obsługują wycofywania. Jednak ponieważ aparat DFA zawiera tylko stan skończony, nie może dopasować wzorzec z backreferences i ponieważ nie konstruuje jawne rozszerzenie, nie może przechwytywać podwyrażenia.

 W przeciwieństwie do aparatów DFA, gdy tradycyjne aparaty NFA wykonać dopasowanie wzorców, ich kolejność przetwarzania jest napędzany przez wzorzec wyrażenia regularnego. Podczas przetwarzania określonego elementu języka, aparat używa chciwy dopasowania; oznacza to, że pasuje do tyle ciągu wejściowego, jak to możliwe. Ale również zapisuje swój stan po pomyślnym dopasowaniu podwyrażenia. Jeśli dopasowanie ostatecznie zakończy się niepowodzeniem, aparat może powrócić do zapisanego stanu, dzięki czemu może wypróbować dodatkowe dopasowania. Ten proces porzucania pomyślnego dopasowania wyrażenia podrzędnego, tak aby późniejsze elementy języka w wyrażeniu regularnym również były zgodne, jest znane jako *wycofywanie.* Aparaty NFA używają wycofywania do testowania wszystkich możliwych rozszerzeń wyrażenia regularnego w określonej kolejności i akceptowania pierwszego dopasowania. Ponieważ tradycyjny aparat NFA konstruuje określone rozszerzenie wyrażenia regularnego dla pomyślnego dopasowania, może przechwytywać dopasowania wyrażenia podrzędnego i pasujące wnioski wsteczne. Jednak ponieważ tradycyjne backtracks NFA, może odwiedzić ten sam stan wiele razy, jeśli dotrze do stanu na różnych ścieżkach. W rezultacie może działać wykładniczo powoli w najgorszym przypadku. Ponieważ tradycyjny aparat NFA akceptuje pierwsze dopasowanie, które znajdzie, może również pozostawić inne (prawdopodobnie dłuższe) dopasowania nieodkryte.

 Silniki POSIX NFA są jak tradycyjne silniki NFA, z tą różnicą, że nadal się cofają, dopóki nie zagwarantują, że znalazły jak najdłuższy możliwy mecz. W rezultacie silnik POSIX NFA jest wolniejszy niż tradycyjny silnik NFA, a gdy używasz silnika POSIX NFA, nie możesz faworyzować krótszego dopasowania na dłuższy, zmieniając kolejność wyszukiwania wycofywania.

 Tradycyjne silniki NFA są preferowane przez programistów, ponieważ oferują większą kontrolę nad dopasowywaniem ciągów niż silniki DFA lub POSIX NFA. Chociaż w najgorszym przypadku mogą działać wolno, można kierować je do znalezienia dopasowań w czasie liniowym lub wielomianowym za pomocą wzorców, które zmniejszają niejednoznaczności i ograniczają wycofywanie. Innymi słowy, chociaż silniki NFA handlu wydajnością mocy i elastyczności, w większości przypadków oferują one dobre do akceptowalnej wydajności, jeśli wyrażenie regularne jest dobrze napisane i unika przypadków, w których wycofywanie obniża wydajność wykładniczo.

> [!NOTE]
> Aby uzyskać informacje na temat kary za wydajność spowodowane nadmiernym wycofywaniem i sposobami tworzenia wyrażenia regularnego w celu obejść je, zobacz [Wycofywanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).

## <a name="net-framework-engine-capabilities"></a>Możliwości aparatu .NET Framework

 Aby skorzystać z zalet tradycyjnego aparatu NFA, aparat wyrażeń regularnych programu .NET Framework zawiera kompletny zestaw konstrukcji, aby umożliwić programistom kierowanie aparatem wycofywania. Konstrukcje te mogą służyć do szybszego znajdowania dopasowań lub faworyzowania określonych rozszerzeń nad innymi.

 Inne funkcje aparatu wyrażeń regularnych programu .NET Framework są następujące:

- Lazy kwantyfikatory: `??`, `*?`, `+?` `{` *n*`,`*m*`}?`. Konstrukcje te informują silnik wycofywania, aby najpierw przeszukał minimalną liczbę powtórzeń. Natomiast zwykłe chciwe kwantyfikatory starają się najpierw dopasować maksymalną liczbę powtórzeń. Poniższy przykład ilustruje różnicę między tymi dwoma. Wyrażenie regularne pasuje do zdania, które kończy się liczbą, a grupa przechwytywania jest przeznaczona do wyodrębniania tej liczby. Wyrażenie regularne `.+(\d+)\.` zawiera kwantyfikator `.+`chciwy , co powoduje, że aparat wyrażeń regularnych do przechwytywania tylko ostatnią cyfrę liczby. Natomiast wyrażenie `.+?(\d+)\.` regularne zawiera kwantyfikator `.+?`leniwy , co powoduje, że aparat wyrażeń regularnych do przechwytywania całej liczby.

     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]

     Chciwi i leniwe wersje tego wyrażenia regularnego są zdefiniowane w sposób pokazany w poniższej tabeli:

    |Wzorce|Opis|
    |-------------|-----------------|
    |`.+`(chciwy kwantyfikator)|Dopasuj co najmniej jedno wystąpienie dowolnego znaku. Powoduje to, że aparat wyrażeń regularnych, aby dopasować cały ciąg, a następnie do wycofywania w razie potrzeby, aby dopasować pozostałą część wzorca.|
    |`.+?`(leniwy kwantyfikator)|Dopasuj co najmniej jedno wystąpienie dowolnego znaku, ale dopasuj jak najmniej.|
    |`(\d+)`|Dopasuj co najmniej jeden znak liczbowy i przypisz go do pierwszej grupy przechwytywania.|
    |`\.`|Dopasuj okres.|

     Aby uzyskać więcej informacji na temat leniwych kwantyfikatorów, zobacz [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).

- Pozytywne wysuw: `(?=` *subexpression*`)`. Ta funkcja umożliwia aparat wycofywania, aby powrócić do tego samego miejsca w tekście po dopasowaniu subexpression. Jest to przydatne do wyszukiwania w całym tekście, weryfikując wiele wzorców, które zaczynają się od tej samej pozycji. Umożliwia również aparatowi sprawdzenie, czy podciąg istnieje na końcu dopasowania bez uwzględniania podciągu w dopasowanym tekście. W poniższym przykładzie użyto dodatniego wysuwu, aby wyodrębnić wyrazy w zdaniu, po którym nie następują symbole interpunkcyjne.

     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]

     Wyrażenie regularne `\b[A-Z]+\b(?=\P{P})` jest zdefiniowane w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`[A-Z]+`|Dopasuj dowolny znak alfabetyczny jeden lub więcej razy. Ponieważ <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> opcją, porównanie jest bez uwzględniania wielkości liter.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|
    |`(?=\P{P})`|Spójrz w przyszłość, aby ustalić, czy następny znak jest symbolem interpunkcyjnym. Jeśli tak nie jest, mecz zakończy się pomyślnie.|

     Aby uzyskać więcej informacji na temat pozytywnych potwierdzeń wyczekiwania, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Negatywne wysuw: `(?!` *subexpression*`)`. Ta funkcja dodaje możliwość dopasowania wyrażenia tylko wtedy, gdy wyrażenie podrzędne nie powiedzie się. Jest to zaawansowane do przycinania wyszukiwania, ponieważ często jest prostsze, aby zapewnić wyrażenie dla sprawy, które powinny zostać wyeliminowane niż wyrażenie dla przypadków, które muszą być uwzględnione. Na przykład trudno jest napisać wyrażenie dla słów, które nie zaczynają się od "non". W poniższym przykładzie użyto negatywnego wysuwu, aby je wykluczyć.

     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]

     Wzorzec `\b(?!non)\w+\b` wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|
    |`(?!non)`|Spójrz w przyszłość, aby upewnić się, że bieżący ciąg nie zaczyna się od "non". Jeśli tak, dopasowanie zakończy się niepowodzeniem.|
    |`(\w+)`|Dopasowuje co najmniej jeden znak słowa.|
    |`\b`|Kończy dopasowanie na granicy wyrazu.|

     Aby uzyskać więcej informacji na temat negatywnych potwierdzeń wyprzedzających, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Ocena warunkowa: `(?(` *wyrażenie*`)` `(?(`*tak*`|`*nie* `)` i *nazwa*`)`*tak*`|`*nie*`)`, gdzie *wyrażenie* jest wyrażeniem podrzędnym, aby dopasować, *nazwa* jest nazwą grupy przechwytywania, *tak* jest ciągiem do dopasowania, jeśli *wyrażenie* jest dopasowane lub *nazwa* jest prawidłową, niepustą grupą przechwyconą, a *nie* jest wyrażeniem podrzędnym, aby dopasować, jeśli *wyrażenie* nie jest dopasowane lub *nazwa* nie jest prawidłową, niepustą przechwyconą grupą. Ta funkcja umożliwia aparatowi wyszukiwanie przy użyciu więcej niż jednego alternatywnego wzorca, w zależności od wyniku poprzedniego dopasowania podwyrażenia lub wyniku potwierdzenia o zerowej szerokości. Pozwala to na bardziej zaawansowana forma wstecznego odniesienia, która pozwala na przykład na dopasowanie podwyrażenia na podstawie tego, czy poprzednie podwyrażenie zostało dopasowane. Wyrażenie regularne w poniższym przykładzie pasuje do akapitów, które są przeznaczone zarówno do użytku publicznego, jak i wewnętrznego. Akapity przeznaczone tylko do `<PRIVATE>` użytku wewnętrznego zaczynają się od znacznika. Wzorzec `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` wyrażenia regularnego używa oceny warunkowej do przypisywania zawartości akapitów przeznaczonych do użytku publicznego i do użytku wewnętrznego w celu oddzielenia grup przechwytywania. Akapity te mogą być następnie traktowane inaczej.

     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]

     Wzorzec wyrażenia regularnego jest zdefiniowany w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij mecz na początku wiersza.|
    |`(?<Pvt>\<PRIVATE\>\s)?`|Dopasuj zero lub `<PRIVATE>` jedno wystąpienie ciągu, po którym następuje znak odstępu. Przypisz dopasowanie do grupy `Pvt`przechwytywania o nazwie .|
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Jeśli `Pvt` grupa przechwytywania istnieje, dopasuj jedno lub więcej wystąpień jednego lub więcej znaków wyrazu, po których następuje zero lub jeden separator interpunkcyjny, po którym następuje znak odstępu. Przypisz podciąg do pierwszej grupy przechwytywania.|
    |<code>&#124;((\w+\p{P}?\s)+))</code>|Jeśli `Pvt` grupa przechwytywania nie istnieje, dopasuj jedno lub więcej wystąpień jednego lub więcej znaków wyrazu, po których następuje zero lub jeden separator interpunkcyjny, po którym następuje znak odstępu. Przypisz podciąg do trzeciej grupy przechwytywania.|
    |`\r?$`|Dopasuj koniec wiersza lub koniec ciągu.|

     Aby uzyskać więcej informacji na temat oceny warunkowej, zobacz [Konstrukcje alternacji](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).

- Definicje grup równoważących: `(?<` *nazwa1*`-`*name2* `>` *podwyrażenie*`)`. Ta funkcja umożliwia aparatowi wyrażeń regularnych śledzenie zagnieżdżonych konstrukcji, takich jak nawiasy lub nawiasy otwierające i zamykające. Na przykład zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Grupy atomowe: `(?>` *podwyrażenie*`)`. Ta funkcja umożliwia aparat wycofywania, aby zagwarantować, że wyrażenie podrzędne pasuje tylko do pierwszego dopasowania znalezionego dla tego wyrażenia podrzędnego, tak jakby wyrażenie działało niezależnie od jego wyrażenia zawierającego. Jeśli nie używasz tej konstrukcji, wycofywanie wyszukiwań z większego wyrażenia może zmienić zachowanie wyrażenia podrzędnego. Na przykład wyrażenie `(a+)\w` regularne pasuje do jednego lub więcej znaków "a" wraz ze znakiem wyrazu, który następuje po sekwencji znaków "a" i przypisuje sekwencję znaków "a" do pierwszej grupy przechwytywania. Jednak jeśli końcowy znak ciągu wejściowego jest również "a", jest `\w` dopasowywany przez element języka i nie jest uwzględniony w grupie przechwycone.

     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]

     Wyrażenie regularne `((?>a+))\w` zapobiega temu zachowaniu. Ponieważ wszystkie kolejne znaki "a" są dopasowywały się bez wycofywania, pierwsza grupa przechwytywania zawiera wszystkie kolejne znaki "a". Jeśli po znakach "a" nie następuje co najmniej jeden znak inny niż "a", dopasowanie nie powiedzie się.

     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]

     Aby uzyskać więcej informacji na temat grup atomowych, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

- Dopasowywanie od prawej do lewej, <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> które jest <xref:System.Text.RegularExpressions.Regex> określone przez podanie opcji do konstruktora klasy lub metody dopasowywania wystąpienia statycznego. Ta funkcja jest przydatna podczas wyszukiwania od prawej do lewej, a nie od lewej do prawej lub w przypadkach, gdy jest bardziej efektywne, aby rozpocząć dopasowanie w prawej części wzorca, a nie po lewej stronie. Jak pokazano w poniższym przykładzie, za pomocą dopasowywania od prawej do lewej można zmienić zachowanie chciwych kwantyfikatorów. W przykładzie przeprowadza dwa wyszukiwania dla zdania, które kończy się liczbą. Wyszukiwanie od lewej do prawej, które używa chciwego kwantyfikatora, `+` pasuje do jednej z sześciu cyfr w zdaniu, podczas gdy wyszukiwanie od prawej do lewej pasuje do wszystkich sześciu cyfr. Aby zapoznać się z opisem wzorca wyrażenia regularnego, zobacz przykład ilustruje ilośćdychorazowe wcześniej w tej sekcji.

     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]

     Aby uzyskać więcej informacji na temat dopasowywania od prawej do lewej, zobacz [Opcje wyrażenia regularnego](../../../docs/standard/base-types/regular-expression-options.md).

- Pozytywny i negatywny wygląd: `(?<=` *podwyrażenie* `)` dla pozytywnego wyglądu i `(?<!` *subexpresion* `)` dla negatywnego wyglądu. Ta funkcja jest podobna do lookahead, która jest omawiana wcześniej w tym temacie. Ponieważ aparat wyrażeń regularnych umożliwia pełne dopasowywanie od prawej do lewej, wyrażenia regularne umożliwiają nieograniczone wyglądy. Pozytywne i negatywne spojrzenie może być również używane w celu uniknięcia zagnieżdżania kwantyfikatorów, gdy zagnieżdżone wyrażenie podrzędne jest nadzbiorem wyrażenia zewnętrznego. Wyrażenia regularne z takimi zagnieżdżonych kwantyfikatorów często oferują niską wydajność. Na przykład poniższy przykład sprawdza, czy ciąg zaczyna się i kończy znak alfanumeryczny i że każdy inny znak w ciągu jest jednym z większego podzbioru. Stanowi część wyrażenia regularnego używanego do sprawdzania poprawności adresów e-mail; Aby uzyskać więcej informacji, zobacz [Jak: Sprawdź, czy ciągi są w prawidłowym formacie wiadomości e-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]

     Wyrażenie regularne ``^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$`` jest zdefiniowane w sposób pokazany w poniższej tabeli.

    |Wzorce|Opis|
    |-------------|-----------------|
    |`^`|Rozpocznij dopasowanie na początku ciągu.|
    |`[A-Z0-9]`|Dopasuj dowolny znak numeryczny lub alfanumeryczny. (Porównanie jest niewrażliwe na argumenty).|
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])\*</code>|Dopasuj zero lub więcej wystąpień dowolnego znaku wyrazu lub dowolnego z następujących znaków: -, !, #, \*$, %, &, ', ., ,,,,/, =, ?, ^, &#96;, {, }, &#124; lub ~.|
    |`(?<=[A-Z0-9])`|Spójrz za poprzedni znak, który musi być numeryczny lub alfanumeryczny. (Porównanie jest niewrażliwe na argumenty).|
    |`$`|Zakończ dopasowanie na końcu ciągu.|

     Aby uzyskać więcej informacji na temat pozytywnych i negatywnych spojrzeń, zobacz [Grupowanie konstrukcji](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="related-articles"></a>Pokrewne artykuły:

|Tytuł|Opis|
|-----------|-----------------|
|[Nawracanie](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Zawiera informacje o tym, jak wyrażeń regularnych wycofywania oddziałów, aby znaleźć alternatywne dopasowania.|
|[Kompilacja i ponowne użycie](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Zawiera informacje dotyczące kompilowania i ponownego żyk wyrażeń regularnych w celu zwiększenia wydajności.|
|[Bezpieczeństwo wątków](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Zawiera informacje o bezpieczeństwie wątku wyrażenia regularnego i wyjaśnia, kiedy należy synchronizować dostęp do obiektów wyrażenia regularnego.|
|[.NET Framework — Wyrażenia regularne](../../../docs/standard/base-types/regular-expressions.md)|Zawiera omówienie aspektu języka programowania wyrażeń regularnych.|
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu ilustrujące sposób używania klas wyrażeń regularnych.|
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje o zestawie znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|

## <a name="reference"></a>Dokumentacja

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
