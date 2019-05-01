---
title: Szczegóły zachowania dotyczącego wyrażeń regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4d8fdc39153f227e8344ea1da52a0dba2688d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955964"
---
# <a name="details-of-regular-expression-behavior"></a>Szczegóły zachowania dotyczącego wyrażeń regularnych
Aparat wyrażeń regularnych systemu .NET Framework jest wycofywania dopasowywania wyrażenia regularnego, uwzględniająca tradycyjnych aparatu niedeterministyczne Niedeterministycznej skończonej (NFA) takim Perl, Python, Emacs i Tcl. To odróżnia go od szybsze, ale aparatów deterministyczne Niedeterministycznej skończonej (DFA) bardziej ograniczone, czysty wyrażeń regularnych, takich jak znajdujący się w awk, egrep lub lex. To również odróżniającym od standardowych, ale wolniej, POSIX NFAs. Poniższej sekcji opisano trzy typy aparatów wyrażeń regularnych i wyjaśnia, dlaczego wyrażeń regularnych w programie .NET Framework są implementowane przy użyciu tradycyjnych aparatu NFA.  
  
## <a name="benefits-of-the-nfa-engine"></a>Korzyści z aparatu NFA  
 Aparaty DFA realizacji dopasowania do wzorca, ich kolejność przetwarzania są sterowane ciągu wejściowego. Aparat rozpoczyna się od początku ciągu wejściowego i będzie kontynuowana po kolei do określenia, czy następny znak pasuje do wzorca wyrażenia regularnego. One może zagwarantować jest zgodny z ciągiem najdłuższy możliwe. Ponieważ nigdy nie sprawdzają one takiego samego znaku dwa razy, aparaty DFA nie obsługują wycofywania. Jednak ponieważ aparat DFA zawiera tylko ograniczone stan, nie może być zgodna wzorcu przy użyciu odwołań wstecznych i, ponieważ nie to utworzyć rozszerzenie jawne, nie można przechwycić w niej podwyrażenia.  
  
 W odróżnieniu od aparatów DFA podczas tradycyjnych aparatów NFA realizacji dopasowania do wzorca, ich kolejność przetwarzania jest wymuszany przez wzorzec wyrażenia regularnego. W czasie przetwarzania elementu danego języka, aparat używa parametru dopasowania zachłannego; oznacza to, że jest on zgodny tyle ciągu wejściowego możliwie najszybsza prawdopodobnie. Ale zapisuje również jego stanu po pomyślnie dopasowywania podwyrażenia. Jeśli dopasowanie ostatecznie zakończy się niepowodzeniem, aparat możesz wrócić do zapisanego stanu, aby podjąć dodatkowe dopasowań. Porzucenie Podwyrażenie pomyślnego dopasowania, aby nowsze elementy języka w wyrażeniu regularnym, można także dopasować ten proces jest znany jako *wycofywania*. Aparaty NFA używane wycofywanie przetestować wszystkie możliwe rozszerzenia wyrażeń regularnych w określonej kolejności i zaakceptować pierwsze dopasowanie. Ponieważ tradycyjnych aparatu NFA tworzy określone rozszerzenie wyrażenie regularne udanych dopasowań, można przechwycić, Podwyrażenie dopasowuje i pasującego odwołania wsteczne. Jednak ponieważ tradycyjnych NFA provided, jego mogą odwiedzić takiego samego stanu wiele razy jeśli dociera stan za pośrednictwem różnych ścieżek. W rezultacie może działać wykładniczo wolno w najgorszym przypadku. Ponieważ tradycyjnych aparatu NFA przyjmuje pierwszy Dopasuj do niego znajduje, zostawiają innych dopasowań (prawdopodobnie dłużej) niewykrytych.  
  
 Aparaty POSIX NFA są podobne do tradycyjnych silników NFA, z tą różnicą, że nadal używa wycofywania, dopóki nie może zagwarantować, że ich Znaleziono dopasowanie najdłuższego możliwe. W rezultacie aparatu POSIX NFA jest mniejsza niż tradycyjne aparatu NFA, a gdy za pomocą aparatu POSIX NFA nie Preferuj dopasowania krótszej na dłużej, zmiana kolejności wyszukiwania wycofywania.  
  
 Tradycyjne aparatów NFA są faworytem przez programistów, ponieważ oferują one większą kontrolę nad dopasowanie niż DFA lub POSIX NFA silników ciągów. Mimo że w najgorszym przypadku, można je uruchomić powoli, można je znajdowanie dopasowań w czasie liniowego lub wielomianowej przy użyciu wzorców, które zmniejszyć niejednoznaczności i ograniczyć wycofywania kierowania. Innymi słowy mimo że aparatów NFA handlu wydajność możliwości i elastyczność w większości przypadków, które oferują one dobrze akceptowalny poziom wydajności, jeśli wyrażenie regularne jest dobrze napisane i pozwala uniknąć sytuacjach, w których wycofywania obniża wydajność wykładniczo.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat spadek wydajności spowodowany przez nadmierne używanie wycofywania i informacje o tym, jak tworzyć wyrażenia regularnego w celu ich obejścia, zobacz [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>Możliwości aparatu programu .NET framework  
 Aby móc korzystać z zalet tradycyjnego aparatu NFA, aparat wyrażeń regularnych systemu .NET Framework zawiera kompletny zestaw konstrukcji, aby umożliwić programistom kieruje aparatem wycofywania. Można te konstrukcje, aby szybciej wykrywać dopasowań lub preferować określonego rozszerzenia przez inne osoby.  
  
 Inne funkcje aparatu wyrażeń regularnych systemu .NET Framework są następujące:  
  
- Kwantyfikatory opóźniające: `??`, `*?`, `+?`, `{` *n*`,`*m*`}?`. Te konstrukcje Poinformuj aparatowi wycofywania, zacznij od wyszukiwania minimalną liczbę powtórzeń. Z kolei zwykłych Kwantyfikatory zachłanne spróbuj Dopasuj najpierw maksymalną liczbę powtórzeń. Poniższy przykład ilustruje różnicę między nimi. Wyrażenie regularne dopasowuje zdanie, które kończy się liczbą, a grupę przechwytywania jest przeznaczona do wyodrębnienia tę liczbę. Wyrażenie regularne `.+(\d+)\.` zawiera kwantyfikator zachłanne `.+`, co powoduje, że aparat wyrażeń regularnych w celu przechwycenia tylko ostatnia cyfra numeru. Z drugiej strony, wyrażenie regularne `.+?(\d+)\.` obejmuje kwantyfikatorem opóźniającym `.+?`, co powoduje, że aparat wyrażeń regularnych przechwytywać cały numer.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Zachłanne podręczne i leniwa wersje tego wyrażenia regularnego są zdefiniowane zgodnie z poniższą tabelą. "  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`.+` (zachłanne kwantyfikator)|Dopasowuje co najmniej jedno wystąpienie dowolnego znaku. Powoduje to, że aparat wyrażeń regularnych dopasować cały ciąg, a następnie aparat jako potrzebne do końca wzorca dopasowania.|  
    |`.+?` (kwantyfikatorem opóźniającym)|Zgodne z co najmniej jedno wystąpienie dowolnego znaku, ale pasuje możliwie.|  
    |`(\d+)`|Dopasuj co najmniej jedną cyfrę i przypisz je do pierwszej grupy przechwytywania.|  
    |`\.`|Dopasowanie kropki.|  
  
     Aby uzyskać więcej informacji na temat Kwantyfikatory opóźniające zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
- Pozytywna asercja wyprzedzająca o: `(?=` *Podwyrażenie*`)`. Ta funkcja umożliwia aparat wycofywania powrócić do tego samego miejscu w tekście po pasujące Wyrażenie cząstkowe. Jest to przydatne do wyszukiwania w całym tekście, sprawdzając wielu wzorców, rozpoczynające się od tej samej pozycji. Umożliwia także aparatu sprawdzić, czy podciąg istnieje na końcu dopasowanie bez uwzględniania podciąg dopasowany tekst. W poniższym przykładzie użyto pozytywna asercja wyprzedzająca o wyodrębnić wyrazów w zdaniu, które nie następują znaki interpunkcyjne.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Wyrażenie regularne `\b[A-Z]+\b(?=\P{P})` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
    |`[A-Z]+`|Dopasuj dowolny znaku alfabetyczny jeden lub więcej razy. Ponieważ <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> opcji w porównaniu jest rozróżniana wielkość liter.|  
    |`\b`|Kończy dopasowanie na granicy wyrazu.|  
    |`(?=\P{P})`|Spoglądaj w celu ustalenia, czy następny znak jest symbolem interpunkcji. Jeśli nie jest dostępne, dopasowanie się powiedzie.|  
  
     Aby uzyskać więcej informacji na temat potwierdzeń pozytywna asercja wyprzedzająca o zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Negatywna asercja wyprzedzająca o: `(?!` *Podwyrażenie*`)`. Ta funkcja dodaje możliwość dopasowania wyrażenia tylko wtedy, gdy Podwyrażenie nie powiedzie się dopasować. Jest to szczególnie wydajna do usunięcia wyszukiwania, ponieważ jest często łatwiejsze w zapewnienie wyrażenia w przypadku, które powinny zostać usunięte niż wyrażenia w sytuacjach, które muszą być włączone. Na przykład jest trudne do pisania wyrażeń wyrazów, które nie zaczynają się od "non". W poniższym przykładzie użyto negatywna asercja wyprzedzająca o, aby je wykluczyć.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Definicję wzorca wyrażenia regularnego `\b(?!non)\w+\b` jest zdefiniowany jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
    |`(?!non)`|Spoglądaj w celu zapewnienia, że bieżący ciąg nie rozpoczyna się od "non". Jeśli tak jest, dopasowanie nie powiedzie się.|  
    |`(\w+)`|Dopasowuje co najmniej jeden znak słowa.|  
    |`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
     Aby uzyskać więcej informacji na temat potwierdzeń negatywna asercja wyprzedzająca o zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Warunkowe oceny: `(?(` *wyrażenie*`)`*tak*`|`*nie* `)` i `(?(` *nazwa*`)`*tak*`|`*nie*`)`, gdzie *wyrażenie* do dopasowania, Wyrażenie cząstkowe jest *nazwa* to nazwa grupy przechwytywania, *tak* ciąg do dopasowania, jeśli *wyrażenie* jest dopasowywany lub *nazwa* jest prawidłowy, pusty przechwyconej grupy i *nie* Podwyrażenie do dopasowania, jeśli jest *wyrażenie* nie jest takie samo lub *nazwa* nie jest prawidłowy, niepustym przechwyconej grupy. Ta funkcja umożliwia aparatowi wyszukiwania przy użyciu więcej niż jeden wzorzec alternatywny, w zależności od tego, czy wynik poprzedniego dopasowania Podwyrażenie lub wynik asercja o zerowej szerokości. Umożliwia to bardziej wydajne formie dopasowywania wstecznego, która pozwala na przykład dopasowywania podwyrażenia oparte na tego, czy zostały dopasowane do poprzednich podwyrażeń. Wyrażenie regularne w poniższym przykładzie pasuje do akapitów, które są przeznaczone do użycia zarówno publicznych, jak i wewnętrznych. Akapity przeznaczona tylko do użytku wewnętrznego zaczynają się od `<PRIVATE>` tagu. Definicję wzorca wyrażenia regularnego `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` przypisuje zawartość akapitów przeznaczone do publicznej i do użytku wewnętrznego oddzielić grupy przechwytywania przy użyciu warunkowego oceny. Te akapitów następnie mogą być obsługiwane inaczej.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Definicję wzorca wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`^`|Rozpoczyna dopasowanie na początku wiersza.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Pasuje do zera lub jednego wystąpienia ciągu `<PRIVATE>` następuje znak odstępu. Przypisz dopasowanie do grupa przechwytywania o nazwie `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Jeśli `Pvt` grupa przechwytywania istnieje, dopasowuje jeden lub więcej wystąpień jednego lub więcej znaków słowa, następuje zero lub jeden separator znaków interpunkcyjnych, następuje znak odstępu. Przypisz podciąg do pierwszej grupy przechwytywania.|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|Jeśli `Pvt` grupa przechwytywania nie istnieje, pasuje do jednej lub więcej wystąpień jednego lub więcej znaków słowa, następuje zero lub jeden separator znaków interpunkcyjnych, następuje znak odstępu. Przypisz podciąg do to trzecia grupa przechwytywania.|  
    |`\r?$`|Dopasowuje koniec wiersza lub końca ciągu.|  
  
     Aby uzyskać więcej informacji na temat warunkowego oceny zobacz [konstrukcje](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
- Równoważenie definicji grup: `(?<` *Nazwa1*`-`*Nazwa2* `>` *Podwyrażenie*`)`. Ta funkcja umożliwia aparatowi wyrażeń regularnych śledzić zagnieżdżonej konstrukcji, takich jak nawiasy lub otwierające i zamykające nawiasy kwadratowe. Aby uzyskać przykład, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Podwyrażenia bez nawrotów (znany także jako zachłanne podwyrażenia): `(?>` *Podwyrażenie*`)`. Ta funkcja umożliwia aparat wycofywania zagwarantować, że Podwyrażenie jest zgodne tylko pierwsze dopasowanie znalezione dla tego podwyrażenia, tak jakby wyrażenia były uruchamiane niezależnie od jej wyrażenia zawierającego. Jeśli nie zostanie użyta ta konstrukcja, wyszukiwań wycofywania z większego wyrażenia, można zmienić zachowanie podwyrażenia. Na przykład, wyrażenie regularne `(a+)\w` dopasowuje co najmniej jeden znaki "a, wraz ze znakiem słowa, które następuje sekwencja znaki"a", a następnie przypisuje sekwencji znaki"a"do pierwszej grupy przechwytywania, jednak", jeśli ostatni znak Ciąg wejściowy jest również "," it dorównuje `\w` element języka i nie są objęte przechwyconą grupę.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Wyrażenie regularne `((?>a+))\w` uniemożliwia to zachowanie. Ponieważ wszystkie kolejne znaki "a" są dopasowywane bez wycofywania, pierwszą grupę przechwytywania obejmuje wszystkie kolejne znaki "a". Jeśli znaki "a" nie zostanie zastosowane przez co najmniej jeden znak więcej niż "", dopasowanie zakończy się niepowodzeniem.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Aby uzyskać więcej informacji na temat podwyrażenia bez nawrotów zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
- Prawo do lewej dopasowanie, która jest określona przez dostarczenie <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> opcję <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statycznym metodę dopasowania wystąpienia. Ta funkcja jest przydatna, gdy wyszukiwanie od prawej do lewej zamiast od lewej do prawej lub w przypadkach, gdy jest bardziej wydajne, aby rozpocząć dopasowania w prawej części wzorca zamiast po lewej stronie. Tak jak pokazano w poniższym przykładzie, zachowanie zachłanne Kwantyfikatory można zmienić za pomocą dopasowywania od prawej do lewej. Przykład wykonuje dwa wyszukuje zdanie, które kończy się liczbą. Wyszukiwanie od lewej do prawej, które używa zachłanne kwantyfikator `+` zgodny z jednym z sześciu cyfr w zdaniu, natomiast wyszukiwanie od prawej do lewej dopasowuje wszystkie sześć cyfr. Opis wzorzec wyrażenia regularnego Zobacz przykład, który ilustruje Kwantyfikatory opóźniające we wcześniejszej części tej sekcji.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Aby uzyskać więcej informacji na temat dopasowywania od prawej do lewej, zobacz [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).  
  
- Dodatnie i ujemne wsteczne: `(?<=` *Podwyrażenie* `)` dla pozytywna asercja wsteczna o i `(?<!` *Podwyrażenie* `)` dla negatywna asercja wsteczna o. Ta funkcja jest podobne do wyprzedzenia, co zostało omówione wcześniej w tym temacie. Ponieważ aparat wyrażeń regularnych pozwala na pełne dopasowanie od prawej do lewej, wyrażenia regularne umożliwiają nieograniczony wybieganie wstecz. Dodatnie i ujemne wsteczna, co oznacza również można uniknąć zagnieżdżania kwantyfikatorów zagnieżdżonych cząstkowe jest nadzbiorem wyrażenie zewnętrzne. Wyrażeń regularnych bez znaczących takich zagnieżdżone Kwantyfikatory często oferują pogorszenia wydajności. Na przykład poniższy przykład sprawdza, czy ciąg zaczyna się i kończy się znakiem alfanumerycznym i że jakikolwiek inny znak w ciągu jest jednym z większych podzbioru. Stanowi ona część wyrażenie regularne służące do sprawdzania poprawności adresów e-mail; Aby uzyskać więcej informacji, zobacz [jak: Verify that Strings Are w prawidłowym formacie adresu E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Wyrażenie regularne `^[A-Z0-9]([-!#$%&'.*+/=?^` {}| ~ \w])* (? < = [A-Z0-9]) $"jest zdefiniowany jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`^`|Rozpoczyna dopasowanie na początku ciągu.|  
    |`[A-Z0-9]`|Dopasowuje dowolny znak numeryczne lub alfanumeryczne. (Porównanie jest rozróżniana wielkość liter).|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])*<code>|Match zero or more occurrences of any word character, or any of the following characters:  -, !, #, $, %, &, ', ., *, +, /, =, ?, ^, \`, {, }, &#124;, or ~.|  
    |`(?<=[A-Z0-9])`|Spoglądanie wstecz do poprzedniego znaku, który musi być numeryczne lub alfanumeryczne. (Porównanie jest rozróżniana wielkość liter).|  
    |`$`|Dopasowywanie kończy się na końcu ciągu.|  
  
     Aby uzyskać więcej informacji na temat pozytywnych i negatywnych wsteczna, co oznacza, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Zawiera informacje o jak wyrażenie wycofywania, aby znaleźć alternatywne dopasowania.|  
|[Kompilacja i ponowne używanie](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Informacje na temat kompilowania i ponowne używanie wyrażeń regularnych w celu zwiększenia wydajności.|  
|[Bezpieczeństwo wątków](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Zawiera informacje o bezpieczeństwo wątkowe wyrażeń regularnych i wyjaśniono, kiedy należy zsynchronizować dostęp do obiektów wyrażeń regularnych.|  
|[Wyrażeń regularnych programu .NET framework](../../../docs/standard/base-types/regular-expressions.md)|Zawiera omówienie programowania aspektów języka wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu ilustrujące sposób użycia klasy wyrażeń regularnych.|  
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, które pokazują korzystanie z wyrażeń regularnych w typowych aplikacjach.|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Informacje o zestawie znaków, operatorów i konstrukcji, które służą do definiowania wyrażeń regularnych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
