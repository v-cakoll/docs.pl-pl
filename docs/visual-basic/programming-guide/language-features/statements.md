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
ms.openlocfilehash: 9953fb949c58c074169596dcf48b6df5e7b8f0af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655724"
---
# <a name="statements-in-visual-basic"></a>Instrukcje w Visual Basic
Instrukcji w języku Visual Basic jest pełną instrukcję. Może zawierać słów kluczowych, operatory, zmienne, stałe i wyrażenia. Każda instrukcja należy do jednej z następujących kategorii:  
  
-   **Instrukcje deklaracji**, której nazwę zmiennej, stałej lub procedury i można również określić typ danych.  
  
-   **Instrukcje wykonywalne**, który rozpocząć działania. Instrukcje te można wywołać metody lub funkcji, a ich w pętli lub gałęzi przy użyciu bloków kodu. Instrukcje wykonywalne obejmują **instrukcje przypisania**, wartość lub wyrażenie, które przypisać do zmiennej lub stała.  
  
 W tym temacie opisano każdej kategorii. Ponadto w tym temacie opisano, jak połączyć wiele instrukcji w jednym wierszu i jak można kontynuować instrukcję przez wiele wierszy.  
  
## <a name="declaration-statements"></a>Instrukcje deklaracji  
 Instrukcje deklaracji służy do nazwy i definiowanie procedur, zmiennych, właściwości, tablic i stałe. Deklaracja elementu programistycznego można także zdefiniować jego typu danych, poziom dostępu i zakres. Aby uzyskać więcej informacji, zobacz [zadeklarowana Charakterystyka elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 Poniższy przykład zawiera trzy deklaracje.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 Jest pierwszą deklaracją `Sub` instrukcji. Wraz z jego dopasowania `End Sub` instrukcji, deklaruje procedurę o nazwie `applyFormat`. Określa również który `applyFormat` jest `Public`, co oznacza, że kodu, który może odwoływać się do niej można wywołać ją.  
  
 Druga deklaracja jest `Const` instrukcja, która deklaruje stała `limit`, określania `Integer` typu danych i wartości 33.  
  
 Trzeci deklaracja jest `Dim` instrukcja, która deklaruje zmienną `thisWidget`. Typ danych określonego obiektu, a mianowicie obiektu utworzone na podstawie `Widget` klasy. Można zadeklarować zmiennej, aby być dowolnego typu danych podstawowych lub dowolnego typu obiektu, która jest widoczna w aplikacji, którego używasz.  
  
### <a name="initial-values"></a>Wartości początkowe  
 Po uruchomieniu kodu zawierającego instrukcji deklaracji Visual Basic rezerwuje ilość pamięci wymaganej dla elementu zadeklarowane. Jeśli element zawiera wartość, Visual Basic inicjuje na wartość domyślną dla tego typu danych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Wartość początkowa można przypisać do zmiennej jako części swojej deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Jeśli zmienna jest zmienna obiektu, można jawnie utworzyć wystąpienia klasy jego przy deklarowaniu przy użyciu [operatora New](../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, jak w poniższym przykładzie przedstawiono.  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Należy pamiętać, że wartość początkowa, które określisz w instrukcji deklaracji nie jest przypisany do zmiennej, dopóki nie osiągnie wykonywania jej instrukcji deklaracji. Do tego czasu zmienna zawiera domyślną wartość dla tego typu danych.  
  
## <a name="executable-statements"></a>Instrukcje wykonywalne  
 Instrukcji wykonywalnej wykonuje akcję. Możesz wywoływanie procedury gałąź do innego miejsca w kodzie pętli za pośrednictwem kilku instrukcji lub obliczyć wyrażenia. Instrukcji przypisania jest szczególnych przypadkach instrukcji pliku wykonywalnego.  
  
 W poniższym przykładzie użyto `If...Then...Else` kontrolowanie struktury do uruchomienia różnych bloków kodu na podstawie wartości zmiennej. W ramach każdego bloku kodu `For...Next` pętli uruchamia określoną liczbę razy.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If` Instrukcji w poprzednim przykładzie sprawdza wartość parametru `clockwise`. Jeśli wartość jest `True`, wywołuje `spinClockwise` metody `aWidget`. Jeśli wartość jest `False`, wywołuje `spinCounterClockwise` metody `aWidget`. `If...Then...Else` Kończy Struktura kontroli `End If`.  
  
 `For...Next` Pętli w ramach każdego bloku wywołuje odpowiednią metodę wiele razy równa wartości `revolutions` parametru.  
  
## <a name="assignment-statements"></a>Instrukcje przypisania  
 Instrukcje przypisania przeprowadzania operacji przypisania, które składają się z pobieranie wartości po prawej stronie operatora przypisania (`=`) i przechowywaniu jej w elemencie po lewej stronie, jak w poniższym przykładzie.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 W powyższym przykładzie w instrukcji przypisania przechowuje wartość literału 42 w zmiennej `v`.  
  
### <a name="eligible-programming-elements"></a>Kwalifikujące się elementy programowania  
 Elementu programistycznego po lewej stronie operatora przypisania musi mieć możliwość akceptuje i przechowywanie wartości. Oznacza to, musi to być zmienna lub właściwość, która nie jest [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md), lub musi być elementu tablicy. W kontekście instrukcji przypisania, jest czasem nazywany takiego elementu *l-wartością*, "wartości po lewej stronie".  
  
 Wartość po prawej stronie operatora przypisania jest generowany przez wyrażenie, które może zawierać dowolną kombinację literały, stałe, zmiennych, właściwości, elementy tablicy, wyrażenia lub wywołania funkcji. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 Poprzedni przykład, dodaje wartość przechowywana w zmiennej `y` wartość przechowywana w zmiennej `z`, a następnie dodaje wartość zwrócona przez wywołanie funkcji `findResult`. Łączna wartość tego wyrażenia jest następnie przechowywane w zmiennej `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Typy danych w instrukcje przypisania  
 Oprócz wartości liczbowe można także przypisać operator przypisania `String` wartości, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Można także przypisać `Boolean` wartości, przy użyciu `Boolean` literału lub `Boolean` wyrażenia, jak w poniższym przykładzie przedstawiono.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 Podobnie można przypisać odpowiednie wartości do elementów programowania `Char`, `Date`, lub `Object` typu danych. Wystąpienie obiektu można także przypisać do określonych jako klasy, z której jest tworzone wystąpienie tego elementu.  
  
### <a name="compound-assignment-statements"></a>Złożone instrukcje przypisania  
 *Złożone instrukcje przypisania* najpierw wykonać operację na wyrażeniu przed przypisaniem go do elementu programowania. Poniższy przykład przedstawia jeden z tych operatorów `+=`, która zwiększa wartość zmiennej po lewej stronie operatora przez wartość wyrażenie po prawej stronie.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 Powyższy przykład dodaje 1 z wartością `n`, a następnie zapisanie tej nowej wartości w `n`. Jest skróconą równoważne następujących instrukcji:  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Różnych operacji przydział złożony mogą być wykonywane przy użyciu operatorów tego typu. Listę tych operatorów i uzyskać więcej informacji o nich, zobacz [operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 Operator przypisania łączenia (`&=`) jest przydatne w przypadku dodawania ciąg w celu już istniejących ciągów, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Konwersje typów w instrukcje przypisania  
 Wartość, którą należy przypisać do zmienną, właściwością lub element tablicy musi być typu danych, które jest odpowiednie dla elementu docelowego. Ogólnie rzecz biorąc należy spróbować generowania wartości tego samego typu danych, jak element docelowy. Jednak niektóre typy mogą być konwertowane na inne typy podczas przypisywania.  
  
 Aby uzyskać informacje o konwersji typów danych, zobacz [konwersje typów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). Krótko mówiąc Visual Basic automatycznie konwertuje wartość danego typu na inny typ, którego rozszerzenie. A *rozszerzanie konwersji* jest jeden w tym zawsze zakończy się pomyślnie w czasie wykonywania, a nie utracić żadnych danych. Na przykład konwertuje Visual Basic `Integer` do wartości `Double` Jeśli jest to możliwe, ponieważ `Integer` rozszerzenie do `Double`. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Zawężanie konwersji* (te, które nie są rozszerzanie) przenoszenia ryzyko awarii w czasie wykonywania, lub utraty danych. Można wykonać konwersji zawężającej jawnie przy użyciu funkcji konwersji typu lub może bezpośrednia kompilator, aby wykonać wszystkie konwersje niejawnie przez ustawienie `Option Strict Off`. Aby uzyskać więcej informacji, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Umieszczanie użycie wielu instrukcji w jednym wierszu  
 Może mieć wiele instrukcji w jednym wierszu rozdzielone dwukropkiem (`:`) znaków. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Chociaż jest to czasami wygodny ten formularz składni sprawia, że kod trudne do odczytu i obsługa. W związku z tym zaleca się pozostawienie jedną instrukcję do wiersza.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Kontynuowanie instrukcję przez wiele wierszy  
 Instrukcja zazwyczaj mieści się w jednym wierszu, ale gdy jest zbyt długa, można kontynuować go do następnego wiersza przy użyciu sekwencja kontynuacji wiersza, który składa się z miejsca, a następnie znaku podkreślenia (`_`) następuje znak powrotu karetki. W poniższym przykładzie `MsgBox` instrukcji wykonywalnej jest kontynuowane ponad dwa wiersze.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Kontynuacja wiersza niejawne  
 W wielu przypadkach można nadal instrukcji w następnym wierszu kolejnych bez użycia znaku podkreślenia (_). W poniższej tabeli wymieniono elementy składni, które niejawnie kontynuować instrukcji w następnym wierszu kodu.  
  
|Element składni|Przykład|  
|---|---|  
|Po przecinku (`,`).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Po nawias otwierający (`(`) lub przed nawiasem zamykającym (`)`).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Po otwierający nawias klamrowy nawiasy (`{`) lub przed zamykający nawias klamrowy (`}`).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) lub [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Po open osadzone wyrażenie (`<%=`) lub przed zamknięcia wyrażenia osadzonego (`%>`) wewnątrz literału XML.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Po operatora łączenia (`&`).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [wymienione operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po operatory przypisania (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [wymienione operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po operatorów binarnych (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) w wyrażeniu.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [wymienione operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po `Is` i `IsNot` operatorów.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [wymienione operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Po znaku kwalifikator elementu członkowskiego (`.`) i przed nazwą elementu członkowskiego. Jednak musi zawierać znak kontynuacji wiersza (_), po wprowadzeniu znaku kwalifikator elementu członkowskiego, gdy używana jest `With` instrukcji lub podając wartości na liście inicjowania dla typu. Podziel linię po operator przypisania (na przykład `=`) w przypadku używania `With` instrukcji lub list inicjowania obiektu.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md) lub [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Po kwalifikator właściwości osi XML (`.` lub `.@` lub `...`). Jednak w przypadku określenia kwalifikatora — członek, gdy używasz muszą zawierać znak kontynuacji wiersza (_) `With` — słowo kluczowe.|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Po <-znaku (<) lub przed większy-znak większości (`>`) po określeniu atrybutu. Również po większy-znak większości (`>`) po określeniu atrybutu. Po określeniu atrybuty poziomu zestawu lub modułu poziomu musi jednak zawierać znak kontynuacji wiersza (_).|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Przed i po operatorach kwerendy (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, i `Descending`). Nie można przerwać linii między słowa kluczowe operatorów zapytań, które składają się z wieloma słowami kluczowymi (`Order By`, `Group Join`, `Take While`, i `Skip While`).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [zapytania](../../../visual-basic/language-reference/queries/queries.md).|  
|Po `In` — słowo kluczowe w `For Each` instrukcji.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Po `From` — słowo kluczowe w inicjatora kolekcji.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Dodawanie komentarzy  
 Kod źródłowy nie zawsze jest oczywiste, nawet do programisty, jej autorze. Aby ułatwić ich kod dokumentów, w związku z tym większość programistów upewnij rozległych stosowania osadzonych komentarze. Komentarze w kodzie opisano procedury lub instrukcję określonym osobom odczytywania lub korzystania z niego później. Visual Basic ignoruje komentarzy podczas kompilacji, a nie wpływają na skompilowanego kodu.  
  
 Wiersze komentarza zaczynać apostrof (`'`) lub `REM` spację. Będzie możliwe ich dodanie dowolne miejsce w kodzie, z wyjątkiem ciągu. Aby dołączyć komentarz do instrukcji, wstawić apostrof lub `REM` po instrukcji, a następnie komentarz. Komentarze można także przejść na ich własnych w osobnym wierszu. W poniższym przykładzie pokazano tych możliwości.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Sprawdzanie błędów kompilacji  
 Jeśli po wpisaniu wiersz kodu, wiersz zostanie wyświetlony z faliste podkreślenie na niebiesko (wyświetlony komunikat o błędzie może również), występuje błąd składni w instrukcji. Należy dowiedzieć się, co to jest problem z instrukcji (przez wyszukiwania na liście zadań lub aktywowaniu błąd umieść wskaźnik myszy i odczytywania komunikat o błędzie) i popraw go. Dopóki wszystkie błędy składniowe wyeliminowaniu w kodzie, program zakończy się niepowodzeniem do poprawnej kompilacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Termin|Definicja|  
|---|---|  
|[Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)|Zawiera łącza do stron odwołania języka, takich jak obejmujące operatory przypisania `=`, `*=`, i `&=`.|  
|[Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Pokazuje, jak połączyć elementy z operatorami umożliwiające uzyskanie nowych wartości.|  
|[Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Pokazuje sposób Podziel jednej instrukcji na wiele wierszy i umieść użycie wielu instrukcji w tym samym wierszu.|  
|[Instrukcje: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Pokazuje, jak etykietę wiersz kodu.|
