---
title: "Szczegóły zachowania dotyczącego wyrażeń regularnych"
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
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c875fee667639923faf44c79afd6488cfc205e20
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="details-of-regular-expression-behavior"></a>Szczegóły zachowania dotyczącego wyrażeń regularnych
Aparat wyrażenia regularnego programu .NET Framework jest backtracking dopasowania wyrażenia regularnego, uwzględniająca tradycyjnych aparat niedeterministyczne skończoną Automaton ds takim Perl, Python, Emacs i Tcl. To odróżnia go od szybsze, ale bardziej ograniczone, czysty wyrażenia regularnego aparaty deterministyczne Automaton ograniczone (DFA) takich jak awk, egrep lub lex. Ma to również odróżniać z znormalizowanych, ale wolniej, POSIX NFAs. Poniższej sekcji opisano trzy typy aparatów wyrażenia regularnego i objaśniono, dlaczego wyrażeń regularnych w programie .NET Framework są implementowane przy użyciu tradycyjnych aparat NFA.  
  
## <a name="benefits-of-the-nfa-engine"></a>Korzyści wynikające z aparatu NFA  
 Podczas dopasowywania do wzorca aparaty DFA, ich kolejność przetwarzania jest wymuszany przez ciąg wejściowy. Aparat zaczyna się od początku ciągu wejściowego i będzie kontynuowana sekwencyjnie, aby określić, czy następny znak jest zgodny ze wzorcem wyrażenia regularnego. Gwarantują można zgodny z ciągiem najdłuższym możliwe. Ponieważ nigdy nie sprawdzają one ten sam znak dwa razy, aparaty DFA nie obsługują śledzenie wsteczne. Jednak ponieważ aparat DFA zawiera tylko skończoną stanu, nie można dopasować wzorca zawierającego odwołania wstecznego, a ponieważ go nie skonstruować jawne rozszerzenie, zakresie nie przechwytywania.  
  
 W odróżnieniu od aparaty DFA tradycyjnych NFA aparatów wykonywania dopasowywania do wzorca ich kolejność przetwarzania jest wymuszany przez wzorzec wyrażenia regularnego. Podczas przetwarzania elementu konkretnego języka, aparat używa intensywnie dopasowania; oznacza to, że jest on zgodny tyle ciąg wejściowy jako prawdopodobnie można. Jednak również zapisuje swój stan po pomyślnie dopasowywania podwyrażenia. Jeśli dopasowanie ostatecznie zakończy się niepowodzeniem, aparat można powrócić do zapisanego stanu, można spróbować dodatkowe dopasowań. Porzucanie dopasowanie pomyślnie Podwyrażenie tak, aby nowsze elementy języka w wyrażeniu regularnym może być również zgodna ten proces nazywa się *śledzenie wsteczne*. Aparaty NFA umożliwia śledzenie wsteczne przetestować wszystkie możliwe rozszerzenia wyrażeń regularnych w określonej kolejności i zaakceptuj pierwsze dopasowanie. Ponieważ tradycyjnych aparat NFA konstruuje rozwinięciem określonego wyrażenia regularnego dopasowanie się pomyślnie, go przechwycić dopasowań Podwyrażenie i pasującego odwołania wstecznego. Jednak ponieważ tradycyjnych NFA zapoznawanie, jego mogą odwiedzać takim samym stanie wielokrotnie jeśli dociera stan przez różne ścieżki. W związku z tym można go uruchomić wykładniczo powoli w najgorszym przypadku. Ponieważ tradycyjnych aparat NFA akceptuje pierwszy znalezione dopasowanie, można także pozostawić innych niewykrytych dopasowań (prawdopodobnie dłużej).  
  
 Aparaty POSIX NFA przypominają tradycyjnych aparaty NFA, z tą różnicą, że nadal śledzenie wsteczne, dopóki nie może zagwarantować, że zostały uznane najdłuższe dopasowanie możliwe. W związku z tym aparat POSIX NFA jest mniejsza niż tradycyjne aparat NFA i korzystając z aparatu POSIX NFA, za pośrednictwem dłużej jeden, zmieniając ich kolejność wyszukiwania backtracking nie Preferuj krótszą dopasowania.  
  
 Tradycyjny aparaty NFA są ich drużyna jest faworytem przez programistów ponieważ oferują one większą kontrolę nad ciąg dopasowania niż aparaty DFA lub POSIX NFA. Mimo że w najgorszym przypadku mogą uruchamiać powoli, można je, aby znaleźć dopasowań w czasie liniowego lub wielomianu za pomocą wzorców, które zmniejszyć niejednoznaczności i ograniczyć śledzenie wsteczne kierowania. Innymi słowy mimo że aparaty NFA handlu wydajność możliwościach i elastyczności, w większości przypadków oferują dobrej na akceptowalną wydajność, jeśli wyrażenie regularne jest dobrze napisane i pozwala uniknąć przypadkach, w których śledzenie wsteczne powoduje spadek wydajności wykładniczo.  
  
> [!NOTE]
>  Informacje o spadek wydajności spowodowany nadmiernym wykorzystaniem algorytmu wycofywania i sposoby sformułować wyrażenia regularnego do nich obejść, zobacz [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="net-framework-engine-capabilities"></a>Możliwości aparatu programu .NET framework  
 Aby skorzystać z zalet tradycyjnych aparat NFA, aparatu wyrażeń regularnych programu .NET Framework zawiera kompletny zestaw konstrukcji umożliwiają deweloperom kierowania backtracking aparatu. Tych konstrukcji można odnaleźć dopasowań szybciej lub preferować rozszerzenia określonych przez innych użytkowników.  
  
 Inne funkcje aparatu wyrażeń regularnych programu .NET Framework są następujące:  
  
-   Kwantyfikatory opóźniające: `??`, `*?`, `+?`, `{`  *n*  `,` *m*`}?`. Te konstrukcje Poinformuj backtracking aparat wyszukiwania z minimalną liczbą powtórzeń najpierw. Z kolei zwykłej Kwantyfikatory intensywnie spróbuj odpowiadające maksymalną liczbę powtórzeń. Poniższy przykład przedstawia różnice między nimi. Wyrażenie regularne dopasowuje zdania, które kończy się liczbą i przechwytywania grupy jest przeznaczony do wyodrębnienia ten numer. Wyrażenie regularne `.+(\d+)\.` obejmuje intensywnie kwantyfikatora `.+`, co powoduje, że aparat wyrażeń regularnych do przechwytywania tylko ostatnich cyfr numeru. Z drugiej strony, wyrażenie regularne `.+?(\d+)\.` obejmuje opóźnieniem kwantyfikatora `.+?`, co powoduje, że aparat wyrażeń regularnych do przechwytywania całą liczbę.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Wersje intensywnie i opóźnieniem tego wyrażenia regularnego są zdefiniowane zgodnie z poniższą tabelą. "  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`.+`(intensywnie kwantyfikatora)|Zgodne z co najmniej jednego wystąpienia dowolnego znaku. Powoduje to, że aparat wyrażenia regularnego do dopasowania cały ciąg, a następnie Aby cofnąć jako potrzebne do pozostałej części wzorca dopasowania.|  
    |`.+?`(tzw)|Dopasować co najmniej jedno wystąpienie dowolny znak, ale odpowiadać jak kupić.|  
    |`(\d+)`|Zgodne z co najmniej jednego znaku numerycznego i przypisz je do pierwszej grupy przechwytywania.|  
    |`\.`|Odpowiada danym okresie.|  
  
     Aby uzyskać więcej informacji na temat Kwantyfikatory opóźniające, zobacz [Kwantyfikatory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Dodatnia wyprzedzenia: `(?=` *Podwyrażenie*`)`. Ta funkcja umożliwia backtracking aparatu powrócić do tego samego miejsca w tekście po odpowiadającym podwyrażenia. Jest to przydatne w przypadku wyszukiwania w całym tekście weryfikując wielu wzorców, uruchamianych z tej samej pozycji. Umożliwia także aparat Sprawdź, czy podciągu istnieje na końcu dopasowania, bez uwzględniania podciąg w tekście dopasowany. W poniższym przykładzie użyto wyprzedzenia dodatnią, aby wyodrębnić wyrazów w zdaniu, które nie są wykonywane przez znaki interpunkcyjne.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     Wyrażenie regularne `\b[A-Z]+\b(?=\P{P})` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
    |`[A-Z]+`|Dopasowuje dowolny znak alfabetyczne jeden lub więcej razy. Ponieważ <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda jest wywoływana z <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> opcja porównanie jest rozróżniana wielkość liter.|  
    |`\b`|Kończy dopasowanie na granicy wyrazu.|  
    |`(?=\P{P})`|Wyszukiwać czy następny znak jest symbol interpunkcyjny. Jeśli nie jest, dopasowania zakończy się pomyślnie.|  
  
     Aby uzyskać więcej informacji na temat potwierdzenia dodatnią wyprzedzenia zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Ujemna wyprzedzenia: `(?!` *Podwyrażenie*`)`. Ta funkcja dodaje możliwość pasuje do wyrażenia tylko wtedy, gdy Podwyrażenie nie odpowiada. Jest to szczególnie wydajna do usunięcia wyszukiwania, ponieważ często jest prostsze zapewnienie wyrażenia dla przypadek, który powinien zostać usunięte niż wyrażenia dla przypadków, które muszą być włączone. Na przykład jest trudne do wyrażenia słowa, które nie rozpoczynają się "nie". W poniższym przykładzie użyto wyprzedzenia ujemna, aby wykluczyć je.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Wzorzec wyrażenia regularnego `\b(?!non)\w+\b` jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`\b`|Rozpoczyna dopasowanie na granicy wyrazu.|  
    |`(?!non)`|Szukaj dalej, aby upewnić się, że bieżący ciąg nie zaczyna się od "nie". Jeśli tak, dopasowania kończy się niepowodzeniem.|  
    |`(\w+)`|Dopasowuje co najmniej jeden znak słowa.|  
    |`\b`|Kończy dopasowanie na granicy wyrazu.|  
  
     Aby uzyskać więcej informacji o potwierdzenia wyprzedzenia ujemna, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Ocena warunkowe: `(?(` *wyrażenie*`)`*tak*`|`*nie* `)` i `(?(` *nazwa*`)`*tak*`|`*nie*`)`, gdzie *wyrażenie* jest Podwyrażenie do dopasowania, *nazwa* jest nazwą grupy przechwytywania *tak* ciągu do dopasowania, jeśli jest *wyrażenie* dopasowaniu lub *nazwa* jest prawidłowy, pusty przechwyconej grupy i *nie* Podwyrażenie do dopasowania, jeśli jest *wyrażenia* jest niezgodne lub *nazwa* nie jest prawidłowe, niepuste pole przechwyconej grupy. Ta funkcja umożliwia aparat wyszukiwania przy użyciu więcej niż jeden wzorzec alternatywne, w zależności od wyniku poprzedniego dopasowania Podwyrażenie lub wynik potwierdzenia zerowej szerokości. Umożliwia to bardziej zaawansowanych formę dopasowań, która pozwala na przykład dopasowywania podwyrażenia oparte na czy poprzedniej Podwyrażenie został uzyskany. Wyrażenie regularne w poniższym przykładzie dopasowuje akapitów, które są przeznaczone dla publicznych i wewnętrznych. Zaczynać akapitów przeznaczone tylko do użytku wewnętrznego `<PRIVATE>` tagu. Wzorzec wyrażenia regularnego `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` używa warunkowego oceny można przypisać zawartość akapitów przeznaczonych do publicznego do użytku wewnętrznego oddzielić grup przechwytywania. Te akapitów następnie mogą być obsługiwane inaczej.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Wzorzec wyrażenia regularnego jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`^`|Rozpocznij dopasowania na początku wiersza.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Zgodne zero lub jeden wystąpienie ciągu `<PRIVATE>` następuje biały znak. Przypisz dopasowania do przechwytywania grupę o nazwie `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Jeśli `Pvt` Przechwytywanie grupy istnieje, zgodne z jednego lub więcej wystąpień co najmniej jeden znak słowa następuje zero lub jeden separatora znaki interpunkcyjne, następuje biały znak. Przypisz podciąg do pierwszej grupy przechwytywania.|  
    |`&#124;((\w+\p{P}?\s)+))`|Jeśli `Pvt` Przechwytywanie grupa nie istnieje, pasuje do jednej lub więcej wystąpień co najmniej jeden znak słowa następuje zero lub jeden separatora znaki interpunkcyjne, następuje biały znak. Przypisz podciąg do trzeciego grupy przechwytywania.|  
    |`\r?$`|Zgodne koniec wiersza lub końca ciągu.|  
  
     Aby uzyskać więcej informacji na temat oceny warunkowego zobacz [konstrukcje Alternacyjne](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
-   Równoważenie definicje grup: `(?<` *Nazwa1*`-`*Nazwa2* `>` *Podwyrażenie*`)`. Ta funkcja umożliwia aparat wyrażeń regularnych do śledzenia zagnieżdżonych elementów składowych, takich jak nawiasy lub otwierające i zamykające nawiasy kwadratowe. Na przykład zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Użyto nonbacktracking (znanej także jako intensywnie użyto): `(?>` *Podwyrażenie*`)`. Ta funkcja umożliwia aparat backtracking zagwarantowanie, czy Podwyrażenie jest zgodna tylko pierwszego dopasowania znaleziono dla tego podwyrażenia tak, jakby wyrażenie, które były uruchomione niezależnie od jej zawierające wyrażenia. Jeśli ta konstrukcja nie jest używany, śledzenie wsteczne wyszukiwania z większego wyrażenia można zmienić to zachowanie podwyrażenia. Na przykład, wyrażenie regularne `(a+)\w` odpowiada co najmniej jeden "" znaków, wraz z literą, sekwencja znaków "", i przypisuje sekwencja znaków "" do pierwszej grupy przechwytywania, jednak, jeśli ostatni znak Ciąg wejściowy jest również "," it równoważona `\w` element języka, a nie jest uwzględniony w przechwyconej grupy.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     Wyrażenie regularne `((?>a+))\w` zapobiega to zachowanie. Ponieważ wszystkich kolejnych znaków "" są dopasowywane bez śledzenie wsteczne, pierwsza grupa Przechwytywanie obejmuje wszystkie kolejne znaki "". Jeśli znaki "", nie zostaną wykonane przez co najmniej jeden znak więcej niż "", dopasowania kończy się niepowodzeniem.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Aby uzyskać więcej informacji o zakresie nonbacktracking, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Prawo do lewej dopasowania, które jest określone, podając <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> opcji w celu <xref:System.Text.RegularExpressions.Regex> konstruktora klasy lub statyczna metoda zgodnego wystąpienia. Ta funkcja jest przydatna podczas wyszukiwania od prawej do lewej strony zamiast od lewej do prawej lub w przypadkach, gdy jest bardziej wydajne, aby rozpocząć dopasowania w prawej części wzorca zamiast po lewej stronie. Jak pokazano w poniższym przykładzie, zachowanie intensywnie Kwantyfikatory można zmieniać za pomocą dopasowywania od prawej do lewej. Przykład prowadzi dwóch wyszukuje zdania, które kończy się liczbą. Wyszukiwanie od lewej do prawej, które używa intensywnie kwantyfikatora `+` zgodny z jednym z sześciu cyfr w zdaniu, natomiast wyszukiwanie od prawej do lewej dopasowuje wszystkie sześć cyfr. Aby uzyskać opis wzorzec wyrażenia regularnego Zobacz przykład ilustrujący Kwantyfikatory opóźniające we wcześniejszej części tej sekcji.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Aby uzyskać więcej informacji na temat dopasowywania od prawej do lewej, zobacz [opcje wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-options.md).  
  
-   Dodatnie i ujemne wybieganie wstecz: `(?<=` *Podwyrażenie* `)` dla dodatnie wybieganie wstecz, i `(?<!` *Podwyrażenie* `)` dla ujemne wybieganie wstecz. Ta funkcja jest podobny do wyprzedzenia, który został omówiony wcześniej w tym temacie. Ponieważ aparat wyrażeń regularnych umożliwia pełne dopasowanie od prawej do lewej, wyrażenia regularne umożliwiają nieograniczony wybieganie wstecz. Dodatnie i ujemne wybieganie wstecz można także uniknąć zagnieżdżenia Kwantyfikatory zagnieżdżonych Podwyrażenie jest nadzbiorem zewnętrzne wyrażenia. Wyrażenia regularne z takich kwantyfikatorami zagnieżdżonymi często oferują pogorszenie wydajności. Na przykład poniższy przykład sprawdza, czy ciąg rozpoczyna się i kończy się znakiem alfanumerycznym i innych znaków w ciągu jest jedną z podzbioru większy. Stanowi ona część wyrażenie regularne służące do sprawdzania poprawności adresów e-mail; Aby uzyskać więcej informacji, zobacz [porady: Sprawdź, czy ciągów jest prawidłowy Format wiadomości E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     Wyrażenie regularne `^[A-Z0-9]([-!#$%&'.*+/=?^`{} | ~ \w])* (? < = [A-Z0-9]) $"jest zdefiniowany, jak pokazano w poniższej tabeli.  
  
    |Wzorzec|Opis|  
    |-------------|-----------------|  
    |`^`|Rozpocznij dopasowania na początku ciąg.|  
    |`[A-Z0-9]`|Dopasowuje dowolny znak numeryczne lub alfanumeryczne. (Porównanie jest bez uwzględniania wielkości liter).|  
    |`([-!#$%&'.*+/=?^`{} &#124; ~\w]) * "|Zgodne zero lub więcej wystąpień dowolny znak słowa lub dowolny z następujących znaków:-,!, #, $, % &, ',., *, +, /, =,?, ^, ", {,}, &#124; lub ~.|  
    |`(?<=[A-Z0-9])`|Szukaj za do poprzedniego znaku, który musi być numeryczne lub alfanumeryczne. (Porównanie jest bez uwzględniania wielkości liter).|  
    |`$`|Zakończenie dopasowuje koniec ciągu.|  
  
     Aby uzyskać więcej informacji na temat dodatnie i ujemne wybieganie wstecz, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Śledzenie wsteczne](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Zawiera informacje dotyczące sposobu wyrażenie_regularne śledzenie wsteczne gałęzie, które mają znaleźć alternatywne dopasowania.|  
|[Kompilacja i ponowne używanie](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Zawiera informacje dotyczące kompilowania i ponowne używanie wyrażeń regularnych w celu zwiększenia wydajności.|  
|[Bezpieczeństwo wątków](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Zawiera informacje o bezpieczeństwo wątków wyrażenia regularnego wraz z wyjaśnieniem, kiedy należy synchronizować dostęp do obiektów wyrażeń regularnych.|  
|[.NET framework — nieprawidłowe wyrażenia](../../../docs/standard/base-types/regular-expressions.md)|Omówienie programowania aspekt język wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, pokazujący sposób użycia klasy wyrażeń regularnych.|  
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, ilustrujące używanie wyrażeń regularnych w typowych zastosowań.|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje o zestawie znaków, Operatorzy i konstrukcji, których można użyć do zdefiniowania wyrażeń regularnych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
