---
title: Instrukcje
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400891"
---
# <a name="statements-in-visual-basic"></a>Instrukcje w Visual Basic

Instrukcja w języku Visual Basic jest pełną instrukcją. Może zawierać słowa kluczowe, operatory, zmienne, stałe i wyrażenia. Każda instrukcja należy do jednej z następujących kategorii:

- **Instrukcje deklaracji**, które nazwę zmiennej, stałej lub procedury, a także można określić typ danych.

- **Instrukcje wykonywalne**, które inicjują akcje. Te instrukcje można wywołać metodę lub funkcję i mogą pętli lub rozgałęzić za pośrednictwem bloków kodu. Instrukcje wykonywalne obejmują **instrukcje przypisania,** które przypisują wartość lub wyrażenie do zmiennej lub stałej.

W tym temacie opisano każdą kategorię. Ponadto w tym temacie opisano sposób łączenia wielu instrukcji w jednym wierszu i jak kontynuować instrukcję w wielu wierszach.

## <a name="declaration-statements"></a>Oświadczenia deklaracji

Instrukcji deklaracji służy do nazwy i definiowania procedur, zmiennych, właściwości, tablic i stałych. Podczas deklarowania elementu programowania można również zdefiniować jego typ danych, poziom dostępu i zakres. Aby uzyskać więcej informacji, zobacz [Deklarowane charakterystyki elementu](./declared-elements/declared-element-characteristics.md).

Poniższy przykład zawiera trzy deklaracje.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

Pierwsza deklaracja `Sub` jest instrukcja. Wraz z `End Sub` jego pasujące oświadczenie, `applyFormat`deklaruje procedurę o nazwie . Określa również, `applyFormat` że `Public`jest , co oznacza, że każdy kod, który może odwoływać się do niego można wywołać.

Druga deklaracja `Const` jest instrukcja, która `limit`deklaruje stałą , określając typ `Integer` danych i wartość 33.

Trzecia deklaracja `Dim` jest instrukcja, która `thisWidget`deklaruje zmienną . Typ danych jest określonym obiektem, a mianowicie `Widget` obiektem utworzonym z klasy. Można zadeklarować zmienną dowolnego typu danych elementarnych lub dowolnego typu obiektu, który jest narażony w używanej aplikacji.

### <a name="initial-values"></a>Wartości początkowe

Po uruchomieniu kodu zawierającego instrukcję deklaracji Visual Basic zastrzega pamięć wymaganą dla zadeklarowanego elementu. Jeśli element posiada wartość, Visual Basic inicjuje go do wartości domyślnej dla jego typu danych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [dim instrukcji](../../language-reference/statements/dim-statement.md).

Można przypisać wartość początkową do zmiennej jako część jej deklaracji, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Jeśli zmienna jest zmienną obiektową, można jawnie utworzyć wystąpienie jej klasy podczas deklarowania go przy użyciu słowa kluczowego [Nowy operator,](../../../visual-basic/language-reference/operators/new-operator.md) jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Należy zauważyć, że wartość początkowa określona w instrukcji deklaracji nie jest przypisana do zmiennej, dopóki wykonanie nie osiągnie instrukcji deklaracji. Do tego czasu zmienna zawiera wartość domyślną dla swojego typu danych.

## <a name="executable-statements"></a>Instrukcje wykonywalne

Instrukcja wykonywalna wykonuje akcję. Można wywołać procedurę, oddział do innego miejsca w kodzie, pętli przez kilka instrukcji lub oceny wyrażenia. Instrukcja przypisania jest szczególnym przypadkiem instrukcji wykonywalnej.

W poniższym przykładzie `If...Then...Else` użyto struktury kontroli do uruchamiania różnych bloków kodu na podstawie wartości zmiennej. W ramach każdego bloku `For...Next` kodu pętla uruchamia określoną liczbę razy.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

Instrukcja `If` w poprzednim przykładzie sprawdza wartość `clockwise`parametru . Jeśli wartość `True`jest , `spinClockwise` wywołuje `aWidget`metodę . Jeśli wartość `False`jest , `spinCounterClockwise` wywołuje `aWidget`metodę . Struktura `If...Then...Else` sterowania kończy `End If`się na .

Pętla `For...Next` w każdym bloku wywołuje odpowiednią metodę liczbę razy `revolutions` równą wartości parametru.

## <a name="assignment-statements"></a>Instrukcje przypisania

Instrukcje przypisania wykonują operacje przypisania, które polegają na przyjęciu`=`wartości po prawej stronie operatora przypisania ( ) i przechowywaniu jej w elemencie po lewej stronie, jak w poniższym przykładzie.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

W poprzednim przykładzie instrukcja przypisania przechowuje wartość literału 42 w zmiennej `v`.

### <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programowania

Element programowania po lewej stronie operatora przypisania musi być w stanie zaakceptować i przechowywać wartość. Oznacza to, że musi być zmienną lub właściwością, która nie jest [readonly](../../../visual-basic/language-reference/modifiers/readonly.md)lub musi być elementem tablicy. W kontekście instrukcji przypisania taki element jest czasami nazywany *lvalue*, dla "wartości lewej".

Wartość po prawej stronie operatora przypisania jest generowana przez wyrażenie, które może składać się z dowolnej kombinacji literałów, stałych, zmiennych, właściwości, elementów tablicy, innych wyrażeń lub wywołań funkcji. Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

W poprzednim przykładzie dodaje wartość `y` utrzymywaną w `z`zmiennej do wartości przechowywanej w `findResult`zmiennej, a następnie dodaje wartość zwróconą przez wywołanie funkcji . Całkowita wartość tego wyrażenia jest następnie `x`przechowywana w zmiennej .

### <a name="data-types-in-assignment-statements"></a>Typy danych w instrukcjach przydziału

Oprócz wartości liczbowych operator przypisania można `String` również przypisać wartości, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Można również `Boolean` przypisać wartości, używając `Boolean` dosłownego lub `Boolean` wyrażenia, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Podobnie można przypisać odpowiednie wartości do elementów `Date`programowania `Object` `Char`, lub typu danych. Można również przypisać wystąpienie obiektu do elementu zadeklarowanego jako klasa, z której jest tworzone to wystąpienie.

### <a name="compound-assignment-statements"></a>Instrukcje przypisania złożonego

*Instrukcje przypisania złożonego* najpierw wykonują operację na wyrażeniu przed przypisaniem jej do elementu programowania. Poniższy przykład ilustruje jeden `+=`z tych operatorów, który zwiększa wartość zmiennej po lewej stronie operatora o wartość wyrażenia po prawej stronie.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

W poprzednim przykładzie dodaje się `n`1 do wartości , `n`a następnie przechowuje tę nową wartość w . Jest to skrócony odpowiednik następującej instrukcji:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Różne operacje przypisania złożonego mogą być wykonywane przy użyciu operatorów tego typu. Aby uzyskać listę tych operatorów i więcej informacji na ich temat, zobacz [Operatory przypisań](../../../visual-basic/language-reference/operators/assignment-operators.md).

Operator przypisania łączenia`&=`( ) jest przydatny do dodawania ciągu na końcu już istniejących ciągów, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Typ konwersji w instrukcjach przypisania

Wartość przypisywana do zmiennej, właściwości lub elementu tablicy musi mieć typ danych odpowiedni dla tego elementu docelowego. Ogólnie rzecz biorąc należy spróbować wygenerować wartość tego samego typu danych, jak element docelowy. Jednak niektóre typy mogą być konwertowane na inne typy podczas przypisywania.

Aby uzyskać informacje na temat konwertowania między typami danych, zobacz [Typy konwersji w języku Visual Basic](./data-types/type-conversions.md). W skrócie Visual Basic automatycznie konwertuje wartość danego typu do innego typu, do którego rozszerza. *Konwersja rozszerzająca* jest taka, która zawsze powiedzie się w czasie wykonywania i nie traci żadnych danych. Na przykład visual basic `Integer` konwertuje wartość `Double` `Integer` w razie `Double`potrzeby, ponieważ rozszerza się na . Aby uzyskać więcej informacji, zobacz [Rozszerzanie i zawężanie konwersji](./data-types/widening-and-narrowing-conversions.md).

*Zawężenie konwersji* (te, które nie są rozszerzające) niosą ze sobą ryzyko awarii w czasie wykonywania lub utraty danych. Konwersję zawężającą można jawnie wykonać za pomocą funkcji konwersji typu lub skierować `Option Strict Off`kompilator do wykonywania wszystkich konwersji w sposób niejawny, ustawiając polecenie . Aby uzyskać więcej informacji, zobacz [konwersje niejawne i jawne](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Umieszczanie wielu instrukcji w jednym wierszu

W jednym wierszu można mieć wiele instrukcji`:`oddzielonych znakiem dwukropka ( ). Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Choć od czasu do czasu wygodne, ta forma składni sprawia, że kod trudno odczytać i utrzymać. W związku z tym zaleca się, aby zachować jedną instrukcję do wiersza.

## <a name="continuing-a-statement-over-multiple-lines"></a>Kontynuowanie instrukcji w wielu wierszach

Instrukcja zwykle mieści się w jednym wierszu, ale gdy jest zbyt długa, można ją kontynuować do następnego wiersza za pomocą sekwencji kontynuacji wiersza, która składa się z spacji, po której następuje znak podkreślenia (`_`), po którym następuje zwrot karetki. W poniższym przykładzie instrukcja wykonywalna `MsgBox` jest kontynuowana w dwóch wierszach.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Niejawna kontynuacja wiersza

W wielu przypadkach można kontynuować instrukcję w następnym wierszu`_`z rzędu bez użycia znaku podkreślenia ( ). Następujące elementy składni niejawnie kontynuować instrukcję w następnym wierszu kodu.

- Po przecince`,`( ). Przykład:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Po otwartym nawiasie`(`( ) lub przed nawiasem zamykającym (`)`). Przykład:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Po otwartej klamrze`{`kęsowej ( ) lub`}`przed zamknięciem klamry kręconej ( ). Przykład:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów: Typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md) lub [Inicjatory kolekcji](./collection-initializers/index.md).

- Po otwartym wyrażeniu osadzonym (`<%=`) lub`%>`przed zamknięciem osadzonego wyrażenia ( ) w literacie XML. Przykład:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Aby uzyskać więcej informacji, zobacz [Wyrażenia osadzone w języku XML](./xml/embedded-expressions-in-xml.md).

- Po operatorze łączenia`&`( ). Przykład:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [Operatorzy wymienieni według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po operatorach`=` `&=`przydziału `-=`( `*=` `/=`, `\=` `^=`, `<<=` `:=` `>>=`, `+=`, , , , , , , , . Przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Aby uzyskać więcej informacji, zobacz [Operatorzy wymienieni według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po operatorach`+` `-`binarnych `Mod` `<>`( `<` `>`, `<=` `>=`, `^` `/` `*`, `<<` `And`, `AndAlso`, , , , , , `>>`, , , , `Or` `OrElse`, , `Like`, `Xor`) w wyrażeniu. Przykład:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Aby uzyskać więcej informacji, zobacz [Operatorzy wymienieni według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po `Is` i `IsNot` operatorów. Przykład:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Aby uzyskać więcej informacji, zobacz [Operatorzy wymienieni według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po znaku kwalifikatora elementu członkowskiego (`.`) i przed nazwą elementu członkowskiego. Przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Jednak należy dołączyć znak kontynuacji`_`wiersza ( ) po znaku `With` kwalifikatora elementu członkowskiego podczas korzystania z instrukcji lub dostarczanie wartości na liście inicjowania dla typu. Należy rozważyć przerwanie wiersza po `=`operatorze przypisania `With` (na przykład) podczas korzystania z instrukcji lub list inicjowania obiektów. Przykład:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Aby uzyskać więcej informacji, zobacz [With... Zakończ za pomocą instrukcji](../../../visual-basic/language-reference/statements/with-end-with-statement.md) lub [inicjatorów obiektu: typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Po kwalifikatorze`.` właściwości `.@` `...`osi XML ( lub ). Jednak należy dołączyć znak kontynuacji`_`wiersza ( ) podczas określania `With` kwalifikatora elementu członkowskiego podczas korzystania ze słowa kluczowego. Przykład:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Po znaku mniej niż (<) lub przed znakiem większym`>`niż ( ) po określeniu atrybutu. Również po znaku większa`>`niż ( ) po określeniu atrybutu. Jednak należy dołączyć znak kontynuacji`_`wiersza ( ) podczas określania atrybutów na poziomie zestawu lub na poziomie modułu. Przykład:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Aby uzyskać więcej informacji, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Przed i po`Aggregate`operatory zapytań `Let`( `Order By` `Select`, `Skip` `Skip While`, `Take` `Distinct`, `From` `Group By`, `Into` `On` `Ascending` `Take While` `Where` `In` `Group Join` `Join`, , `Descending`, , , , , , , , , , , , , i ). Nie można przerwać linii między słowami kluczowymi operatorów zapytań, `Take While`które `Skip While`są złożone z wielu słów kluczowych (`Order By`, `Group Join`, , , i ). Przykład:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Aby uzyskać więcej informacji, zobacz [Kwerendy](../../../visual-basic/language-reference/queries/index.md).

- Po `In` słowie `For Each` kluczowym w instrukcji. Przykład:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Aby uzyskać więcej informacji, zobacz [Dla każdego... Następne oświadczenie](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Po `From` słowo kluczowe w kolekcji inicjatora. Przykład:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Aby uzyskać więcej informacji, zobacz [Inicjalizatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Dodawanie komentarzy

Kod źródłowy nie zawsze jest oczywisty, nawet dla programisty, który go napisał. Aby pomóc udokumentować swój kod, w związku z tym większość programistów liberalne wykorzystanie osadzonych komentarzy. Komentarze w kodzie mogą wyjaśniać procedurę lub konkretną instrukcję każdemu, kto czyta lub pracuje z nią później. Visual Basic ignoruje komentarze podczas kompilacji i nie mają one wpływu na skompilowany kod.

Wiersze komentarza zaczynają się od`'`apostrofu ( ) lub `REM` po spacji. Można je dodać w dowolnym miejscu w kodzie, z wyjątkiem ciągu. Aby dołączyć komentarz do instrukcji, wstaw apostrof lub `REM` po instrukcji, a następnie komentarz. Komentarze mogą również przejść na osobnej linii. Poniższy przykład pokazuje te możliwości.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Sprawdzanie błędów kompilacji

Jeśli po wpisaniu wiersza kodu wiersz jest wyświetlany z falistym niebieskim podkreśleniem (może pojawić się również komunikat o błędzie), w instrukcji pojawia się błąd składniowy. Musisz dowiedzieć się, co jest nie tak z instrukcją (patrząc na liście zadań lub najeżdżając kursorem na błąd za pomocą wskaźnika myszy i czytając komunikat o błędzie) i poprawić go. Dopóki nie zostały ustalone wszystkie błędy składni w kodzie, program nie będzie kompilować poprawnie.

## <a name="related-sections"></a>Powiązane sekcje

|Termin|Definicja|
|---|---|
|[Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)|Zawiera łącza do stron referencyjnych `=`języka `*=`obejmujących operatory przypisań, takie jak , i `&=`.|
|[Operatory i wyrażenia](./operators-and-expressions/index.md)|Pokazuje, jak połączyć elementy z operatorami, aby uzyskać nowe wartości.|
|[Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Pokazuje, jak podzielić pojedynczą instrukcję na wiele wierszy i jak umieścić wiele instrukcji w tym samym wierszu.|
|[Instrukcje: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Pokazuje, jak oznaczyć wiersz kodu.|
