---
title: Instrukcje w Visual Basic
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
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931788"
---
# <a name="statements-in-visual-basic"></a>Instrukcje w Visual Basic

Instrukcji w języku Visual Basic jest pełną instrukcję. Może zawierać słów kluczowych, operatorów, zmienne, stałe i wyrażeń. Każda instrukcja należy do jednej z następujących kategorii:

- **Instrukcje deklaracji**, której nazwę zmiennej, stałej lub procedury, a można również określić typu danych.

- **Instrukcje wykonywalne**, który zainicjować akcje. Tych instrukcji, można wywołać metody lub funkcji, a ich pętli lub korzystając z bloków kodu. Instrukcje wykonywalne obejmują **instrukcje przypisania**, wartość lub wyrażenie, którego przypisać do zmiennej lub stała.

W tym temacie opisano każdej kategorii. Ponadto w tym temacie opisano sposób łączenia wielu instrukcji w jednym wierszu i kontynuować instrukcję w wielu wierszach.

## <a name="declaration-statements"></a>Instrukcje deklaracji

Instrukcje deklaracji służy do nazwy i definiowanie procedur, zmiennych, właściwości, tablic i stałe. Kiedy Deklarujesz element programowania, można także zdefiniować jego typu danych, poziom dostępu i zakresu. Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](./declared-elements/declared-element-characteristics.md).

Poniższy przykład zawiera trzy deklaracje.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

Pierwszej deklaracji jest `Sub` instrukcji. Wraz z jego dopasowania `End Sub` instrukcja deklaruje procedurę o nazwie `applyFormat`. Określa również, `applyFormat` jest `Public`, co oznacza, że wszelki kod, który może odwoływać się do niego go wywoływać.

Drugi deklaracja jest `Const` instrukcję, która deklaruje stała `limit`, określanie `Integer` typu danych i wartości 33.

Trzeci deklaracja jest `Dim` instrukcję, która deklaruje zmienną `thisWidget`. Typ danych określonego obiektu, to znaczy obiekt utworzony z `Widget` klasy. Można zadeklarować zmiennej, aby być dowolnego typu danych podstawowych lub dowolnego typu obiektu, która jest widoczna w aplikacji, którego używasz.

### <a name="initial-values"></a>Wartości początkowe

Po uruchomieniu kodu zawierające instrukcji deklaracji, Visual Basic rezerwuje ilość pamięci wymaganej dla zadeklarowanych elementów. Jeśli element przechowuje wartość, Visual Basic inicjuje ją na wartość domyślną dla tego typu danych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Dim](../../language-reference/statements/dim-statement.md).

Początkowa wartość można przypisać do zmiennej jako części swojej deklaracji, tak jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Jeśli zmienna jest zmienna obiektu, możesz jawnie utworzyć wystąpienia klasy przy deklarowaniu przy użyciu [operatora New](../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, w poniższym przykładzie pokazano.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Należy pamiętać o tym, czy wartość początkowa, którą określisz w instrukcji deklaracji nie został przypisany do zmiennej, dopóki nie osiągnie wykonywania instrukcji w jego deklaracji. Do tego czasu zmienna zawiera wartość domyślna dla jego typu danych.

## <a name="executable-statements"></a>Instrukcje wykonywalne

Instrukcji wykonywalnej wykonuje akcję. Możesz wywołać procedurę gałęzi do innej lokalizacji w kodzie pętlę na skutek kilka instrukcji lub ocena wyrażenia. Instrukcja przypisania jest przypadkiem szczególnym instrukcji pliku wykonywalnego.

W poniższym przykładzie użyto `If...Then...Else` kontrolowanie struktury, aby uruchomić różne bloki kodu na podstawie wartości zmiennej. W ramach każdego bloku kodu `For...Next` pętli jest uruchamiany określoną liczbę razy.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If` Instrukcja w powyższym przykładzie sprawdza, czy wartość parametru `clockwise`. Jeśli wartość jest `True`, wywoływanych przez nią `spinClockwise` metody `aWidget`. Jeśli wartość jest `False`, wywoływanych przez nią `spinCounterClockwise` metody `aWidget`. `If...Then...Else` Struktury sterowania kończy się `End If`.

`For...Next` Pętli w ramach każdego bloku wywołuje odpowiednią metodę kilka razy równa wartości `revolutions` parametru.

## <a name="assignment-statements"></a>Instrukcje przypisania

Instrukcje przypisania przeprowadzania operacji przypisania, które składają się z podjęciem wartość po prawej stronie operatora przypisania (`=`) i przechowywaniu jej w elemencie po lewej stronie, jak w poniższym przykładzie.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

W powyższym przykładzie instrukcja przypisania przechowuje wartość literału 42 w zmiennej `v`.

### <a name="eligible-programming-elements"></a>Kwalifikujących się elementów programowania

Aby zaakceptować i przechowywać wartości musi umożliwiać elementu programistycznego po lewej stronie operatora przypisania. Oznacza to, musi być zmienną lub właściwość, która jest [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md), lub musi być elementu tablicy. W kontekście instrukcji przypisania, takiego elementu jest czasami nazywane *l-wartości*, "wartości po lewej stronie."

Wartość po prawej stronie operatora przypisania jest generowany przez wyrażenie, które może zawierać dowolną kombinację literały, stałe, zmiennych, właściwości, elementów tablicy, innych wyrażeń lub wywołania funkcji. Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Poprzedni przykład dodaje wartość przechowywaną w zmiennej `y` wartości przechowywane w zmiennej `z`, a następnie dodaje wartość zwrócona przez wywołanie funkcji `findResult`. Łączna wartość tego wyrażenia następnie jest przechowywany w zmiennej `x`.

### <a name="data-types-in-assignment-statements"></a>Typy danych w instrukcjach przypisania

Oprócz wartości liczbowych, operator przypisania można również przypisywać `String` wartości, tak jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Można także przypisać `Boolean` wartości, przy użyciu `Boolean` literału lub `Boolean` wyrażenia w poniższym przykładzie pokazano.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Podobnie, można przypisać odpowiednie wartości do elementów programowania `Char`, `Date`, lub `Object` typu danych. Można także przypisać wystąpienie obiektu do elementu zadeklarowane jako klasy, z którego jest tworzony tego wystąpienia.

### <a name="compound-assignment-statements"></a>Złożone instrukcje przypisania

*Złożone instrukcje przypisania* najpierw wykonać operacji na wyrażeniu przed przypisaniem go do elementu programowania. W poniższym przykładzie pokazano jeden z tych operatorów `+=`, która zwiększa wartość zmiennej po lewej stronie operatora przez wartość wyrażenia po prawej stronie.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Poprzedni przykład dodaje 1 wartość `n`, a następnie przechowanie tej nowej wartości w `n`. Jest skrótem równoważny następującej instrukcji:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Korzystanie z operatorów tego typu można wykonać wiele operacji przypisania złożonego. Aby uzyskać listę tych operatorów i dowiedzieć się więcej o nich, zobacz [operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md).

Operator przypisania łączenia (`&=`) jest przydatne w przypadku dodawania ciąg na końcu już istniejących ciągów, tak jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Konwersje typów w instrukcjach przypisania

Wartość, które można przypisać do zmiennej, właściwości lub elementu tablicy musi być typu danych, które jest odpowiednie dla tego elementu docelowego. Ogólnie rzecz biorąc należy spróbować do generowania wartości tego samego typu danych, jak w przypadku elementu docelowego. Jednak niektóre typy mogą być konwertowane na inne typy podczas przypisywania.

Aby uzyskać informacje o konwersji między typami danych, zobacz [konwersje typów w języku Visual Basic](./data-types/type-conversions.md). Krótko mówiąc Visual Basic automatycznie konwertuje wartość danego typu na dowolny inny typ, który rozszerza się. A *poszerzenie konwersji* jest jeden w tym zawsze zakończy się pomyślnie w czasie wykonywania i nie tracić żadnych danych. Na przykład, Visual Basic konwertuje `Integer` wartość `Double` Jeśli jest to możliwe, ponieważ `Integer` rozszerza się na `Double`. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](./data-types/widening-and-narrowing-conversions.md).

*Zawężających* (te, które nie są rozszerzanie) wykonuje ryzyko awarii w czasie wykonywania lub utraty danych. Można przeprowadzić konwersji zawężającej jawnie przy użyciu funkcji konwersji typu, lub można nakazać kompilatorowi wykonanie wszystkie konwersje niejawne, ustawiając `Option Strict Off`. Aby uzyskać więcej informacji, zobacz [Konwersje jawne i niejawne](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Umieszczenie wielu instrukcji w jednym wierszu

Można użyć wielu instrukcji w jednym wierszu rozdzielone dwukropkiem (`:`) znaków. Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Chociaż czasami wygodne ta forma składni sprawia, że Twój kod trudne do odczytania i obsługa. W związku z tym zaleca się utrzymywanie używana jedna instrukcja do wiersza.

## <a name="continuing-a-statement-over-multiple-lines"></a>Kontynuowanie instrukcję w wielu wierszach

Instrukcja zazwyczaj mieści się w jednym wierszu, ale gdy jest to zbyt długo, można kontynuować go do następnego wiersza przy użyciu sekwencji kontynuacji wiersza, który składa się z miejsca, w którym następuje znak podkreślenia (`_`) następuje znak powrotu karetki. W poniższym przykładzie `MsgBox` instrukcji wykonywalnej jest kontynuowane na dwa wiersze.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Niejawnej kontynuacji wiersza

W wielu przypadkach można kontynuować instrukcję w następnym wierszu kolejnych bez użycia znaku podkreślenia (`_`). Następujące elementy składni niejawnie continue, instrukcja w następnym wierszu kodu.

- Po przecinku (`,`). Na przykład:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Po nawias otwierający (`(`) lub przed zamykającym (`)`). Na przykład:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Po otwierający nawias klamrowy nawias (`{`) lub przed zamykający nawias klamrowy (`}`). Na przykład:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md) lub [inicjatory kolekcji](./collection-initializers/index.md).

- Po otwartą osadzone wyrażenie (`<%=`) lub przed zamknięciem wyrażenia osadzone (`%>`) w ramach literał XML. Na przykład:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](./xml/embedded-expressions-in-xml.md).

- Po operatorze łączenia (`&`). Na przykład:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po operatory przypisania (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Na przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Aby uzyskać więcej informacji, zobacz [operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po operatorach dwuargumentowych (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) w wyrażeniu. Na przykład:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Aby uzyskać więcej informacji, zobacz [operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po `Is` i `IsNot` operatorów. Na przykład:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Aby uzyskać więcej informacji, zobacz [operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Po znaku kwalifikatora elementu członkowskiego (`.`) i przed nazwę elementu członkowskiego. Na przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Jednak musi zawierać znak kontynuacji wiersza (`_`) po wprowadzeniu znaku kwalifikatora elementu członkowskiego, przy zastosowaniu `With` instrukcji lub podanie wartości z listy inicjowania dla typu. Weź pod uwagę przerwanie wiersz po operator przypisania (na przykład `=`) w przypadku korzystania `With` instrukcji lub listy inicjowania obiektu. Na przykład:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Aby uzyskać więcej informacji, zobacz [za pomocą... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md) lub [inicjatorach obiektów: typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Po kwalifikator właściwości osi XML (`.` lub `.@` lub `...`). Jednak musi zawierać znak kontynuacji wiersza (`_`) po określeniu kwalifikatora elementu członkowskiego przy zastosowaniu `With` — słowo kluczowe. Na przykład:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Po mniej-niż (<) lub przed większy-znak większości (`>`) po określeniu atrybutu. Również po większą-niż znak (`>`) po określeniu atrybutu. Jednak musi zawierać znak kontynuacji wiersza (`_`) po określeniu poziomu zestawu lub modułu na poziomie atrybutów. Na przykład:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Aby uzyskać więcej informacji, zobacz [atrybuty Przegląd](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Przed i po operatorach zapytań (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, i `Descending`). Nie można przerwać linię między słów kluczowych, operatorów zapytań, które składają się z wielu słów kluczowych (`Order By`, `Group Join`, `Take While`, i `Skip While`). Na przykład:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Aby uzyskać więcej informacji, zobacz [zapytania](../../../visual-basic/language-reference/queries/index.md).

- Po `In` — słowo kluczowe w `For Each` instrukcji. Na przykład:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Aby uzyskać więcej informacji, zobacz [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Po `From` — słowo kluczowe w inicjatorze kolekcji. Na przykład:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Dodawanie komentarzy

Kod źródłowy nie zawsze jest oczywiste, nawet w przypadku programisty, który napisał go. Aby pomóc w dokumentowanie kodu, w związku z tym, większość programistów Wykorzystaj liberalne osadzone komentarzy. Komentarze w kodzie można wyjaśnić procedurę lub określonej instrukcji dla każdego, kto odczytu lub korzystania z niego później. Języka Visual Basic ignoruje komentarzy podczas kompilacji, a nie wpływają na skompilowany kod.

Wiersze komentarzy zaczynają się od apostrof (`'`) lub `REM` następuje spacja. Można ich dodać dowolne miejsce w kodzie, z wyjątkiem wewnątrz ciągu. Aby dołączyć komentarz do instrukcji, wstawić apostrof lub `REM` po instrukcji, następuje komentarz. Komentarze, można także przejść na ich własnych w osobnym wierszu. W poniższym przykładzie pokazano tych możliwości.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Sprawdzanie błędów kompilacji

Jeśli po pisania choćby wiersza kodu, wierszu jest wyświetlany z linią falistą niebieski (komunikat o błędzie mogą być również wyświetlane), występuje błąd składni w instrukcji. Musisz dowiedzieć się, czym jest problem z instrukcją (przez wyszukiwanie na liście zadań lub przenosząc kursor myszy nad błędem, umieść wskaźnik myszy i odczytanie komunikatu o błędzie) i popraw go. Dopóki wszystkie błędy składniowe naprawiona w kodzie, program zakończy się niepowodzeniem skompilować poprawnie.

## <a name="related-sections"></a>Sekcje pokrewne

|Termin|Definicja|
|---|---|
|[Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)|Zawiera łącza do stron odwołanie do języka, takich jak obejmujących operatory przypisania `=`, `*=`, i `&=`.|
|[Operatory i wyrażenia](./operators-and-expressions/index.md)|Pokazuje, jak połączyć elementy z operatorami umożliwiające uzyskanie nowych wartości.|
|[Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Pokazuje sposób Podziel pojedynczej instrukcji na wiele wierszy i umieścić użycie wielu instrukcji w tym samym wierszu.|
|[Instrukcje: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Pokazuje, jak etykieta wiersza kodu.|
