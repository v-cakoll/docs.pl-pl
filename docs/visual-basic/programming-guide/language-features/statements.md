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
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401982"
---
# <a name="statements-in-visual-basic"></a>Instrukcje w Visual Basic

Instrukcja w Visual Basic jest kompletną instrukcją. Może zawierać słowa kluczowe, operatory, zmienne, stałe i wyrażenia. Każda instrukcja należy do jednej z następujących kategorii:

- **Instrukcje deklaracji**, które nazwiją zmienną, stałą lub procedurę, i mogą również określać typ danych.

- **Instrukcje wykonywalne**, które inicjują akcje. Te instrukcje mogą wywołać metodę lub funkcję i mogą być pętlą lub gałęzią przez bloki kodu. Instrukcje wykonywalne zawierają **instrukcje przypisania**, które przypisują wartość lub wyrażenie do zmiennej lub stałej.

W tym temacie opisano każdą kategorię. Ponadto w tym temacie opisano sposób łączenia wielu instrukcji w jednym wierszu i sposób kontynuowania instrukcji na wielu wierszach.

## <a name="declaration-statements"></a>Deklaracje deklaracji

Używaj instrukcji deklaracji do nazwy i definiowania procedur, zmiennych, właściwości, tablic i stałych. Podczas deklarowania elementu programistycznego można także zdefiniować jego typ danych, poziom dostępu i zakres. Aby uzyskać więcej informacji, zobacz [deklarowane cechy elementu](./declared-elements/declared-element-characteristics.md).

Poniższy przykład zawiera trzy deklaracje.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

Pierwsza deklaracja jest `Sub` instrukcją. Wraz z odpowiadającą jej `End Sub` instrukcją deklaruje procedurę o nazwie `applyFormat` . Określa również, że `applyFormat` jest `Public` , co oznacza, że każdy kod, który może odwoływać się do niego, może go wywołać.

Druga deklaracja jest `Const` instrukcją, która deklaruje stałą `limit` , określając `Integer` Typ danych i wartość 33.

Trzecia deklaracja jest `Dim` instrukcją, która deklaruje zmienną `thisWidget` . Typ danych jest określonym obiektem, a mianowicie obiektem utworzonym z `Widget` klasy. Można zadeklarować zmienną jako dowolnego typu danych podstawowych lub dowolnego typu obiektu, który jest dostępny w używanej aplikacji.

### <a name="initial-values"></a>Wartości początkowe

Gdy jest uruchamiany kod zawierający instrukcję deklaracji, Visual Basic rezerwuje pamięć wymaganą dla zadeklarowanego elementu. Jeśli element posiada wartość, Visual Basic inicjuje ją jako wartość domyślną dla tego typu danych. Aby uzyskać więcej informacji, zobacz "zachowanie" w [instrukcji Dim](../../language-reference/statements/dim-statement.md).

Można przypisać wartość początkową do zmiennej w ramach swojej deklaracji, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Jeśli zmienna jest zmienną obiektu, można jawnie utworzyć wystąpienie jej klasy podczas deklarowania jej przy użyciu słowa kluczowego [new operatora](../../language-reference/operators/new-operator.md) , jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Należy zauważyć, że wartość początkowa określona w instrukcji deklaracji nie jest przypisana do zmiennej, dopóki wykonanie nie osiągnie swojej instrukcji deklaracji. Do tego czasu zmienna będzie zawierać wartość domyślną dla tego typu danych.

## <a name="executable-statements"></a>Instrukcje wykonywalne

Instrukcja wykonywalna wykonuje akcję. Może wywoływać procedurę, gałąź do innego miejsca w kodzie, pętlę przez kilka instrukcji lub oszacować wyrażenie. Instrukcja przypisania jest specjalnym przypadkiem instrukcji wykonywalnej.

Poniższy przykład używa `If...Then...Else` struktury kontroli do uruchamiania różnych bloków kodu na podstawie wartości zmiennej. W każdym bloku kodu `For...Next` Pętla uruchamia określoną liczbę razy.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If`Instrukcja w powyższym przykładzie sprawdza wartość parametru `clockwise` . Jeśli wartość jest `True` , wywołuje `spinClockwise` metodę `aWidget` . Jeśli wartość jest `False` , wywołuje `spinCounterClockwise` metodę `aWidget` . `If...Then...Else`Struktura kontrolki zaczyna się od `End If` .

`For...Next`Pętla w obrębie każdego bloku wywołuje odpowiednią metodę o liczbie razy równej wartości `revolutions` parametru.

## <a name="assignment-statements"></a>Instrukcje przypisania

Instrukcje przypisania wykonują operacje przypisania, które obejmują pobieranie wartości z prawej strony operatora przypisania ( `=` ) i przechowywanie go w elemencie po lewej stronie, jak w poniższym przykładzie.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

W poprzednim przykładzie instrukcja przypisania przechowuje wartość literału 42 w zmiennej `v` .

### <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programistyczne

Element programowania po lewej stronie operatora przypisania musi być w stanie zaakceptować i zapisać wartość. Oznacza to, że musi to być zmienna lub właściwość, która nie jest [tylko do odczytu](../../language-reference/modifiers/readonly.md)lub musi być elementem tablicy. W kontekście instrukcji przypisania taki element jest czasami nazywany *lvalue*, dla "Left Value".

Wartość po prawej stronie operatora przypisania jest generowana przez wyrażenie, które może składać się z dowolnej kombinacji literałów, stałych, zmiennych, właściwości, elementów tablicy, innych wyrażeń lub wywołań funkcji. Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Poprzedni przykład dodaje wartość przechowywaną w zmiennej `y` do wartości przechowywanej w zmiennej `z` , a następnie dodaje wartość zwróconą przez wywołanie funkcji `findResult` . Łączna wartość tego wyrażenia jest następnie przechowywana w zmiennej `x` .

### <a name="data-types-in-assignment-statements"></a>Typy danych w instrukcjach przypisania

Oprócz wartości liczbowych, operator przypisania może również przypisywać `String` wartości, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Można również przypisywać `Boolean` wartości przy użyciu `Boolean` literału lub `Boolean` wyrażenia, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Analogicznie, można przypisać odpowiednie wartości do elementów programistycznych `Char` , `Date` , lub `Object` typu danych. Można również przypisać wystąpienie obiektu do elementu zadeklarowanego jako należącego do klasy, z której to wystąpienie jest tworzone.

### <a name="compound-assignment-statements"></a>Instrukcje przypisania złożonego

*Instrukcje przypisania złożonego* najpierw wykonują operację na wyrażeniu przed przypisaniem go do elementu programowania. Poniższy przykład ilustruje jeden z tych operatorów, `+=` , który zwiększa wartość zmiennej po lewej stronie operatora przez wartość wyrażenia po prawej.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Poprzedni przykład dodaje 1 do wartości `n` , a następnie zapisuje nową wartość w `n` . Jest to skrócony skrót następującej instrukcji:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Różne operacje przypisania złożonego można wykonać przy użyciu operatorów tego typu. Aby uzyskać listę tych operatorów i więcej informacji na ich temat, zobacz [Operatory przypisania](../../language-reference/operators/assignment-operators.md).

Operator przypisania łączenia ( `&=` ) jest przydatny do dodawania ciągu do końca istniejących ciągów, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Konwersje typów w instrukcjach przypisania

Wartość przypisana do zmiennej, właściwości lub elementu tablicy musi być typem danych odpowiednim dla tego elementu docelowego. Ogólnie rzecz biorąc, należy spróbować wygenerować wartość tego samego typu danych co element docelowy. Jednak niektóre typy mogą być konwertowane na inne typy podczas przypisywania.

Aby uzyskać informacje na temat konwertowania typów danych, zobacz [konwersje typów w Visual Basic](./data-types/type-conversions.md). W skrócie Visual Basic automatycznie konwertuje wartość danego typu na dowolny inny typ, do którego się rozszerza. *Konwersja rozszerzająca* jest taka, która zawsze kończy się pomyślnie w czasie wykonywania i nie utraci żadnych danych. Na przykład Visual Basic konwertuje `Integer` wartość do `Double` , gdy jest to konieczne, ponieważ `Integer` poszerza do `Double` . Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](./data-types/widening-and-narrowing-conversions.md).

*Konwersje wąskie* (te, które nie są rozszerzane) mogą stanowić ryzyko wystąpienia awarii w czasie wykonywania lub utraty danych. Konwersję można wykonać jawnie za pomocą funkcji konwersji typów lub skierować kompilator, aby wykonywał wszystkie konwersje niejawnie przez ustawienie `Option Strict Off` . Aby uzyskać więcej informacji, zobacz [konwersje niejawne i jawne](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Umieszczanie wielu instrukcji w jednym wierszu

Można mieć wiele instrukcji w pojedynczym wierszu oddzielonym znakiem dwukropka ( `:` ). Ilustruje to poniższy przykład.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Chociaż czasami jest to wygodne, ta forma składni sprawia, że kod trudno odczytać i zachować. W tym celu zaleca się zachowanie jednej instrukcji w wierszu.

## <a name="continuing-a-statement-over-multiple-lines"></a>Kontynuowanie instrukcji na wielu wierszach

Instrukcja zwykle mieści się w jednym wierszu, ale gdy jest zbyt długa, można kontynuować ją w następnym wierszu przy użyciu sekwencji kontynuacji wiersza, która składa się z odstępu, po którym następują znaki podkreślenia ( `_` ), po którym następuje znak powrotu karetki. W poniższym przykładzie `MsgBox` instrukcja wykonywalna jest kontynuowana w dwóch wierszach.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Kontynuacja niejawnego wiersza

W wielu przypadkach można kontynuować instrukcję w następnym kolejnym wierszu bez użycia znaku podkreślenia ( `_` ). Następujące elementy składni niejawnie kontynuują instrukcję w następnym wierszu kodu.

- Po przecinku ( `,` ). Przykład:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Po otwierającym nawiasie ( `(` ) lub przed nawiasem zamykającym ( `)` ). Przykład:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Po otwierającym nawiasie klamrowym ( `{` ) lub przed zamykającym nawiasem klamrowym ( `}` ). Przykład:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów: typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md) lub [Inicjatory kolekcji](./collection-initializers/index.md).

- Po otwartym wyrażeniu osadzonym ( `<%=` ) lub przed zamknięciem osadzonego wyrażenia ( `%>` ) w literale XML. Przykład:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).

- Po operator łączenia ( `&` ). Przykład:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [Operatory wymienione przez funkcję](../../language-reference/operators/operators-listed-by-functionality.md).

- Po operatorach przypisania (,,,,,,,,, `=` `&=` `:=` `+=` `-=` `*=` `/=` `\=` `^=` `<<=` , `>>=` ). Przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Aby uzyskać więcej informacji, zobacz [Operatory wymienione przez funkcję](../../language-reference/operators/operators-listed-by-functionality.md).

- Po operatorach binarnych (,,,,,,,,, `+` `-` `/` `*` `Mod` `<>` `<` `>` `<=` `>=` , `^` , `>>` , `<<` , `And` , `AndAlso` , `Or` , `OrElse` `Like` `Xor` ) w obrębie wyrażenia. Przykład:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Aby uzyskać więcej informacji, zobacz [Operatory wymienione przez funkcję](../../language-reference/operators/operators-listed-by-functionality.md).

- Po `Is` `IsNot` operatorach i. Przykład:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Aby uzyskać więcej informacji, zobacz [Operatory wymienione przez funkcję](../../language-reference/operators/operators-listed-by-functionality.md).

- Po znaku kwalifikatora elementu członkowskiego ( `.` ) i przed nazwą elementu członkowskiego. Przykład:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Jednakże należy uwzględnić znak kontynuacji wiersza ( `_` ) po znaku kwalifikatora elementu członkowskiego, gdy używasz `With` instrukcji lub dostarczania wartości na liście inicjalizacji dla typu. Rozważ przerwanie wiersza po operatorze przypisania (na przykład `=` ) w przypadku używania `With` instrukcji lub list inicjalizacji obiektów. Przykład:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Aby uzyskać więcej informacji, zobacz temat [with... Kończy z](../../language-reference/statements/with-end-with-statement.md) [inicjatorami instrukcji lub obiektów: typy nazwane i anonimowe](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Po kwalifikatorze właściwości osi XML ( `.` lub `.@` lub `...` ). Należy jednak uwzględnić znak kontynuacji wiersza ( `_` ), gdy podczas używania `With` słowa kluczowego zostanie określony kwalifikator elementu członkowskiego. Przykład:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Aby uzyskać więcej informacji, zobacz [Właściwości osi XML](../../language-reference/xml-axis/index.md).

- Po określeniu atrybutu jest znak mniejszości (<) lub przed znakiem większości ( `>` ). Po określeniu atrybutu również po znaku większości ( `>` ). Jednak `_` podczas określania atrybutów na poziomie zestawu lub modułu należy uwzględnić znak kontynuacji wiersza (). Przykład:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Aby uzyskać więcej informacji, zobacz [Omówienie atrybutów](../concepts/attributes/index.md).

- Przed i po operatorach zapytań ( `Aggregate` ,,,, `Distinct` `From` `Group By` `Group Join` ,,,,, `Join` `Let` `Order By` `Select` `Skip` ,,,,,,, `Skip While` `Take` `Take While` `Where` `In` `Into` `On` , `Ascending` i `Descending` ). Nie można przerwać wiersza między słowami kluczowymi operatorów zapytań, które składają się z wielu słów kluczowych ( `Order By` , `Group Join` , `Take While` i `Skip While` ). Przykład:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Aby uzyskać więcej informacji, zobacz [zapytania](../../language-reference/queries/index.md).

- Po `In` słowie kluczowym w `For Each` instrukcji. Przykład:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Aby uzyskać więcej informacji, zobacz [dla każdej z nich... Next — instrukcja](../../language-reference/statements/for-each-next-statement.md).

- Po `From` słowie kluczowym inicjatora kolekcji. Przykład:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Aby uzyskać więcej informacji, zobacz [Inicjatory kolekcji](collection-initializers/index.md).

## <a name="adding-comments"></a>Dodawanie komentarzy

Kod źródłowy nie zawsze jest nieoczywisty, nawet programisty, który go zapisał. Aby ułatwić dokumentowanie kodu, w związku z tym większość programistów może korzystać z zliberalizowanych komentarzy osadzonych. Komentarze w kodzie mogą wyjaśnić procedury lub konkretne instrukcje dla każdego odczytu lub pracy z nim później. Visual Basic ignoruje komentarze podczas kompilacji i nie ma wpływu na skompilowany kod.

Wiersze komentarzy zaczynają się od apostrofu ( `'` ) lub `REM` po nim spacja. Mogą być dodawane gdziekolwiek w kodzie, z wyjątkiem ciągu. Aby dołączyć komentarz do instrukcji, Wstaw apostrof lub `REM` po instrukcji, po którym następuje komentarz. Komentarze mogą również przechodzić do oddzielnej linii. Poniższy przykład ilustruje te możliwości.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Sprawdzanie błędów kompilacji

Jeśli po wpisaniu wiersza kodu linia zostanie wyświetlona z niebieską linią falistą (może również pojawić się komunikat o błędzie), w instrukcji występuje błąd składniowy. Należy dowiedzieć się, co jest nieprawidłowe w instrukcji (przez wyszukanie listy zadań lub umieszczenie wskaźnika myszy nad błędem i przeczytanie komunikatu o błędzie) i poprawienie go. Dopóki nie zostaną naprawione wszystkie błędy składniowe w kodzie, program nie zostanie prawidłowo skompilowany.

## <a name="related-sections"></a>Sekcje pokrewne

|Termin|Definicja|
|---|---|
|[Operatory przypisania](../../language-reference/operators/assignment-operators.md)|Zawiera łącza do stron referencyjnych języka obejmujących operatory przypisania `=` , takie jak, `*=` i `&=` .|
|[Operatory i wyrażenia](./operators-and-expressions/index.md)|Pokazuje, w jaki sposób połączyć elementy z operatorami w celu uzyskania nowych wartości.|
|[Instrukcje: Przerywanie i łączenie instrukcji w kodzie](../program-structure/how-to-break-and-combine-statements-in-code.md)|Pokazuje, jak przerwać pojedynczą instrukcję w wielu wierszach i jak umieścić wiele instrukcji w tym samym wierszu.|
|[Instrukcje: Etykietowanie instrukcji](../program-structure/how-to-label-statements.md)|Pokazuje, jak oznaczyć wiersz kodu.|
