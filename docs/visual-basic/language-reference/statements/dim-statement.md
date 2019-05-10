---
title: Dim — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 5a16060efc45cc0642aa6612d02644e252cd53d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751798"
---
# <a name="dim-statement-visual-basic"></a>Dim — Instrukcja (Visual Basic)

Deklaruje i alokuje magazyn przechowywania dla co najmniej jednej zmiennej.

## <a name="syntax"></a>Składnia

```
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).

- `accessmodifier`

  Opcjonalna. Może to być jeden z następujących elementów:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `Shared`

  Opcjonalna. Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Static`

  Opcjonalna. Zobacz [statyczne](../../../visual-basic/language-reference/modifiers/static.md).

- `ReadOnly`

  Opcjonalna. Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).

- `WithEvents`

Opcjonalna. Określa, że są one zmienne obiektów, które odwołują się do wystąpienia klasy, które może wywoływać zdarzenia. Zobacz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).

- `variablelist`

  Wymagana. Lista zmiennych został zadeklarowany w tej instrukcji.

  `variable [ , variable ... ]`

  Każdy `variable` ma następujące składni i części:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Część|Opis|
  |---|---|
  |`variablename`|Wymagana. Nazwa zmiennej. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|Opcjonalna. Lista granic dla każdego wymiaru zmiennej tablicy.|
  |`New`|Opcjonalna. Tworzy nowe wystąpienie klasy po `Dim` uruchomienia instrukcji.|
  |`datatype`|Opcjonalna. Typ danych zmiennej.|
  |`With`|Opcjonalna. Wprowadza na liście inicjatora obiektu.|
  |`propertyname`|Opcjonalna. Nazwa właściwości w klasie wykonujesz wystąpienia.|
  |`propinitializer`|Wymagany po `propertyname` =. Wyrażenie, które jest obliczane i ma przypisaną nazwę właściwości.|
  |`initializer`|Opcjonalny Jeśli `New` nie zostanie określony. Wyrażenie jest obliczane i przypisana do zmiennej podczas jego tworzenia.|

## <a name="remarks"></a>Uwagi

Kompilator języka Visual Basic używa `Dim` instrukcię, aby określić typ danych zmiennej i inne informacje, takie jak jaki kod mają dostęp do zmiennej. Poniższy przykład deklaruje zmienną do przechowywania `Integer` wartość.

```vb
Dim numberOfStudents As Integer
```

Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Typ odwołania, możesz użyć `New` — słowo kluczowe, aby utworzyć nowe wystąpienie klasy lub struktury, która jest określona przez typ danych. Jeśli używasz `New`, wyrażenie inicjatora nie jest używana. Zamiast tego podajesz argumentów, jeśli są wymagane, do konstruktora klasy, w którym tworzysz zmienną.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Można zadeklarować zmienną w procedurze, blok, klasy, struktury lub modułu. Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeń nazw lub interfejsu. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Zmienna, które są zadeklarowane na poziomie modułu, poza każda procedura jest *zmiennej składowej* lub *pola*. Zmienne Członkowskie znajdują się w zakresie ich klasy, struktury lub modułu. Zmienna, która jest zadeklarowana na poziomie procedura jest *zmienna lokalna*. Zmienne lokalne są w zakresie tylko w ramach ich procedurą lub blokiem.

Następujące modyfikatory dostępu są używane do deklarowania zmiennych na zewnątrz procedury: `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private`. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`Dim` — Słowo kluczowe jest opcjonalna i zazwyczaj pominąć, jeśli określisz dowolną z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, lub `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

Jeśli `Option Explicit` jest włączone (ustawienie domyślne), kompilator wymaga deklaracji dla każdej zmiennej, możesz użyć. Aby uzyskać więcej informacji, zobacz [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Określając wartość początkową

Można przypisać wartość do zmiennej, podczas jego tworzenia. Typ wartości, możesz użyć *inicjatora* umożliwiają określanie wartości wyrażenia można przypisać do zmiennej. Wyrażenia musi być stałą, która może być obliczona w czasie kompilacji.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Jeśli określono inicjatora i typu danych nie jest określony w `As` klauzuli *wnioskowanie o typie* można wywnioskować typu danych z inicjatora. W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane jako liczby całkowite. W drugim deklaracji wnioskowanie o typie wnioskuje typ z znajduje się wartość 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Wnioskowanie o typie ma zastosowanie na poziomie procedury. Nie ma zastosowania poza procedury w klasie, strukturze, modułu lub interfejs. Aby uzyskać więcej informacji na temat wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

Aby dowiedzieć się, jak co się stanie, jeśli nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](../../../visual-basic/language-reference/statements/dim-statement.md#default) w dalszej części tego tematu.

Możesz użyć *inicjatora obiektu* do deklarowania wystąpień nazwanych i anonimowych typów. Poniższy kod tworzy wystąpienie `Student` klasy i używa inicjatora obiektu można zainicjować właściwości.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Aby uzyskać więcej informacji na temat inicjatorów obiektów zobacz [jak: Deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicjatorach obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), i [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Deklarowanie wiele zmiennych

Można zadeklarować wiele zmiennych w jednej deklaracji instrukcji, określając nazwę zmiennej dla każdego z nich, a także następujące nazwy tablicy za pomocą nawiasów. Wiele zmiennych rozdziela się przecinkami.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

Jeśli zadeklarujesz więcej niż jedną zmienną z jednym `As` klauzuli nie może dostarczyć inicjatora dla tej grupy zmiennych.

Można określić różne typy danych dla różnych zmiennych, przy użyciu oddzielnego `As` klauzula dla każdej zmiennej można zadeklarować. Każda zmienna ma typ danych określonego w pierwszym `As` klauzuli napotkały po jego `variablename` części.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Tablice

Można zadeklarować zmienną do przechowywania *tablicy*, który może zawierać wiele wartości. Aby określić, że zmienna zawiera tablicę, postępuj zgodnie z jego `variablename` natychmiast za pomocą nawiasów. Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Można określić dolną i górną granicę każdego wymiaru tablicy. Aby to zrobić, należy dołączyć `boundslist` wewnątrz nawiasów. Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolną granicę. Dolna granica zawsze wynosi zero, czy została ona określona lub nie. Każdy indeks może się różnić od zera za pośrednictwem jego wartość górnej granicy.

Następujące dwie instrukcje są równoważne. Każda instrukcja deklaruje tablicę 21 `Integer` elementów. Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Poniższa instrukcja deklaruje tablicę dwuwymiarową typu `Double`. Tablica ma 4 wiersze (3 + 1) 6 kolumn (5 + 1) każdego. Należy pamiętać, że górna granica reprezentuje najwyższą możliwą wartość indeksu nie długość drugiego wymiaru. Długość drugiego wymiaru jest górną granicę plus jeden.

```vb
Dim matrix2(3, 5) As Double
```

Tablica może mieć od 1 do 32 wymiarów.

Wszystkie granice można pozostawić puste deklaracji tablicy. Jeśli to zrobisz, tablica ma liczbę wymiarów, które określisz, ale jest niezainicjowany. Ma ona wartość `Nothing` do momentu zainicjowania w co najmniej niektóre z jego elementów. `Dim` Instrukcja musi określać granice dla wszystkich wymiarów lub żadnych wymiarów.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Jeśli tablica zawiera więcej niż jednym wymiarze, musi zawierać przecinków w nawiasach, aby wskazać liczbę wymiarów.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

Można zadeklarować *tablicę o zerowej długości* deklarując jedną z wymiarów tablicy na-1. Zmienna, która zawiera tablicę o zerowej długości nie ma wartości `Nothing`. Tablice o zerowej długości są wymagane przez niektóre typowe funkcje środowiska uruchomieniowego języka. Jeśli próbujesz uzyskać dostęp z takiej tablicy, wystąpi wyjątek czasu wykonywania. Aby uzyskać więcej informacji, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Wartości w tablicy można zainicjować za pomocą literału tablicowego. Aby to zrobić, należy otoczyć Inicjowanie wartości ujęte w nawiasy klamrowe (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

Dla tablic wielowymiarowych inicjowania dla każdego wymiaru oddzielne jest ujęte w nawiasy klamrowe w wymiarze zewnętrznego. Elementy są określone w kolejności wierszy.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Aby uzyskać więcej informacji na temat literały tablicowe, zobacz [tablic](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="default"></a> Dane domyślne typy i wartości

W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w `Dim` instrukcji.

|Określony typ danych?|Inicjatora określona?|Przykład|Wynik|
|---|---|---|---|
|Nie|Nie|`Dim qty`|Jeśli [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd kompilacji.|
|Nie|Yes|`Dim qty = 5`|Jeśli [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) znajduje się na (ustawienie domyślne), zmienna przyjmuje dane typu inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączone, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd kompilacji.|
|Yes|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Zobacz tabelę w dalszej części tej sekcji.|
|Yes|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest konwertowany na określony typ danych, wystąpi błąd kompilacji.|

W przypadku określenia typu danych, ale nie należy określać inicjatora, Visual Basic inicjuje zmienną wartością domyślną dla jego typu danych. W poniższej tabeli przedstawiono domyślne wartości inicjowania.

|Typ danych|Wartość domyślna|
|---|---|
|Wszystkie typy liczbowe (w tym `Byte` i `SByte`)|0|
|`Char`|Binarny 0|
|Wszystkie typy odwołań (w tym `Object`, `String`i wszystkie tablice)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00:00 1 stycznia 1 rok (01/01/0001 12:00:00 AM)|

Każdy element struktury jest inicjowany, tak jakby osobnej zmiennej. Jeśli zadeklarować długość tablicy, ale nie zainicjować jej elementy, każdy element jest inicjowany, tak jakby osobnej zmiennej.

## <a name="static-local-variable-lifetime"></a>Statyczny okres istnienia zmiennych lokalnych

A `Static` zmienna lokalna ma dłuższy okres istnienia niż procedury, w którym jest zdeklarowana. Granice okresu istnienia zmiennej są zależne od której jest zadeklarowana procedury i czy jest `Shared`.

|Deklaracja procedury|Zmienna została zainicjowana|Zmienna zatrzymuje istniejące|
|---|---|---|
|W module|Procedura jest wywoływana po raz pierwszy|Gdy program zatrzymuje wykonywanie|
|W klasie lub strukturze procedura jest `Shared`|Po raz pierwszy procedura jest wywoływana na konkretne wystąpienie lub klasa lub struktura|Gdy program zatrzymuje wykonywanie|
|W klasie lub strukturze nie jest procedurą `Shared`|Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu|Po zwolnieniu wystąpienie do wyrzucania elementów bezużytecznych (GC)|

## <a name="attributes-and-modifiers"></a>Atrybuty i modyfikatorów

Atrybuty można zastosować tylko do zmiennych składowych, a nie do zmiennych lokalnych. Atrybut przyczynia się informacji metadanych zestawu, który nie jest zrozumiały dla magazynu tymczasowego, takie jak zmienne lokalne.

Na poziomie modułu, nie można użyć `Static` modyfikator, aby zadeklarować zmienne elementu członkowskiego. Na poziomie procedury nie można użyć `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, lub dostępu dowolną Modyfikatory do deklarowania zmiennych lokalnych.

Można określić, jaki kod może dostęp do zmiennej, podając `accessmodifier`. Klasy i moduł domyślny zmienne (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie zmienne elementu członkowskiego struktury dostępu publicznego. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu. Nie można używać modyfikatorów dostępu w zmiennych lokalnych (wewnątrz procedury).

Można określić `WithEvents` tylko w zmiennych elementu członkowskiego, a nie na zmiennych lokalnych wewnątrz procedury. Jeśli określisz `WithEvents`, typ danych zmiennej musi być typu określonej klasy nie `Object`. Nie można zadeklarować tablicy o liczbie `WithEvents`. Aby uzyskać więcej informacji o zdarzeniach zobacz [zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md).

> [!NOTE]
> Kod poza klasą, struktury lub modułu musi kwalifikować nazwy zmiennej członkowskiej z nazwą tej klasy, struktury lub modułu. Kod poza terenem procedurą lub blokiem nie może odwoływać się do żadnych zmiennych lokalnych, w tym procedurę lub blok.

## <a name="releasing-managed-resources"></a>Przy zwalnianiu zasobów zarządzanych

Moduł zbierający elementy bezużyteczne .NET Framework usuwa zasoby zarządzane bez żadnych dodatkowych kodowania ze strony użytkownika. Możesz jednak wymusić likwidacji zasobów zarządzanych, zamiast czekać, aż moduł odśmiecania pamięci.

Jeśli klasa przechowuje na szczególnie cenne i ograniczonych zasobów (takich jak połączenie lub plik dojście do bazy danych), może nie chcesz czekać aż do następnego wyrzucania elementów bezużytecznych aby wyczyścić wystąpienie klasy, która nie jest już używana. Klasa może implementować <xref:System.IDisposable> interfejs zapewnia metodę, aby zwolnić zasoby przed wyrzucania elementów bezużytecznych. Udostępnia klasę, która implementuje ten interfejs `Dispose` metodę, która może być wywoływana w celu wymuszenia cenne zasoby mogą być wprowadzane natychmiast.

`Using` Instrukcji automatyzuje proces pobierania zasobu, wykonywanie zbiór instrukcji i następnie Usuwanie zasobu. Jednak zasobu musi implementować <xref:System.IDisposable> interfejsu. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../visual-basic/language-reference/statements/using-statement.md).

## <a name="example"></a>Przykład

Poniższy przykład deklaruje zmienne przy użyciu `Dim` instrukcji z różnymi opcjami.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Przykład

Poniższy przykład wyświetla listę liczb pierwszych, od 1 do 30. Zakres zmiennych lokalnych jest opisane w komentarzach do kodu.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Przykład

W poniższym przykładzie `speedValue` zmienna została zgłoszona na poziomie klasy. `Private` — Słowo kluczowe jest używane do deklarowania zmiennej. Zmienna może zostać oceniony przez każda procedura w `Car` klasy.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Zobacz także

- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
