---
title: Dim — Instrukcja
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
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744724"
---
# <a name="dim-statement-visual-basic"></a>Dim — Instrukcja (Visual Basic)

Deklaruje i przydziela miejsce do magazynowania dla co najmniej jednej zmiennej.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).

- `accessmodifier`

  Opcjonalny. Może to być jeden z następujących modyfikatorów dostępu:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `Shared`

  Opcjonalny. Zobacz [udostępnianie](../modifiers/shared.md).

- `Shadows`

  Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).

- `Static`

  Opcjonalny. Zobacz [static](../modifiers/static.md).

- `ReadOnly`

  Opcjonalny. Zobacz [tylko do odczytu](../modifiers/readonly.md).

- `WithEvents`

  Opcjonalny. Określa, że są to zmienne obiektów odwołujące się do wystąpień klasy, które mogą zgłaszać zdarzenia. Zobacz [WithEvents](../modifiers/withevents.md).

- `variablelist`

  Wymagany. Lista zmiennych, które są zadeklarowane w tej instrukcji.

  `variable [ , variable ... ]`

  Każda `variable` ma następującą składnię i części:

  `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`

  |Części|Opis|
  |---|---|
  |`variablename`|Wymagany. Nazwa zmiennej. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
  |`boundslist`|Opcjonalny. Lista granic każdego wymiaru zmiennej tablicowej.|
  |`New`|Opcjonalny. Tworzy nowe wystąpienie klasy podczas uruchamiania instrukcji `Dim`.|
  |`datatype`|Opcjonalny. Typ danych zmiennej.|
  |`With`|Opcjonalny. Wprowadza listę inicjatora obiektów.|
  |`propertyname`|Opcjonalny. Nazwa właściwości w klasie, dla której tworzysz wystąpienie.|
  |`propinitializer`|Wymagane po `propertyname` =. Wyrażenie, które jest oceniane i przypisywane do nazwy właściwości.|
  |`initializer`|Opcjonalne, jeśli nie określono `New`. Wyrażenie, które jest oceniane i przypisywane do zmiennej podczas jej tworzenia.|

## <a name="remarks"></a>Uwagi

Kompilator Visual Basic używa instrukcji `Dim` do określenia typu danych zmiennej i innych informacji, takich jak kod, który może uzyskać dostęp do zmiennej. Poniższy przykład deklaruje zmienną do przechowywania wartości `Integer`.

```vb
Dim numberOfStudents As Integer
```

Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

Dla typu referencyjnego za pomocą słowa kluczowego `New` można utworzyć nowe wystąpienie klasy lub struktury, która jest określona przez typ danych. Jeśli używasz `New`, nie używasz wyrażenia inicjatora. Zamiast tego należy podać argumenty, jeśli są wymagane, do konstruktora klasy, z której tworzysz zmienną.

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

Można zadeklarować zmienną w procedurze, bloku, klasie, strukturze lub module. Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeni nazw lub interfejsie. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Zmienna zadeklarowana na poziomie modułu, poza żadną procedurą, to zmienna lub *pole* *Członkowskie* . Zmienne składowe znajdują się w zakresie w całej klasy, strukturze lub module. Zmienna zadeklarowana na poziomie procedury jest *zmienną lokalną*. Zmienne lokalne znajdują się w zakresie tylko w obrębie procedury lub bloku.

Poniższe Modyfikatory dostępu są używane do deklarowania zmiennych poza procedurą: `Public`, `Protected`, `Friend`, `Protected Friend`i `Private`. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Słowo kluczowe `Dim` jest opcjonalne i zwykle pomijane, jeśli określisz dowolny z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`lub `WithEvents`.

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

Jeśli `Option Explicit` jest włączone (wartość domyślna), kompilator wymaga deklaracji dla każdej używanej zmiennej. Aby uzyskać więcej informacji, zobacz [Option Explicit](option-explicit-statement.md).

## <a name="specifying-an-initial-value"></a>Określanie wartości początkowej

Podczas tworzenia można przypisać wartość do zmiennej. Dla typu wartości należy użyć *inicjatora* , aby podać wyrażenie, które ma zostać przypisane do zmiennej. Wyrażenie musi obliczyć stałą, którą można obliczyć w czasie kompilacji.

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

Jeśli inicjator jest określony i typ danych nie jest określony w klauzuli `As`, *wnioskowanie typu* jest używane do wywnioskowania typu danych z inicjatora. W poniższym przykładzie zarówno `num1`, jak i `num2` są silnie wpisane jako liczby całkowite. W drugiej deklaracji typ wnioskowania wnioskuje typ z wartości 3.

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

Wnioskowanie o typie ma zastosowanie na poziomie procedury. Nie ma zastosowania poza procedurą w klasie, strukturze, module lub interfejsie. Aby uzyskać więcej informacji na temat wnioskowania o typie, zobacz [instrukcja wnioskowania](option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).

Aby uzyskać informacje o tym, co się stanie, gdy nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](dim-statement.md#default) w dalszej części tego tematu.

*Inicjatora obiektów* można użyć do deklarowania wystąpień typów nazwanych i anonimowych. Poniższy kod tworzy wystąpienie klasy `Student` i używa inicjatora obiektów do inicjowania właściwości.

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [How to: DECLARE a Object przy użyciu inicjatora obiektów](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) [: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)oraz [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="declaring-multiple-variables"></a>Deklarowanie wielu zmiennych

Można zadeklarować kilka zmiennych w jednej instrukcji deklaracji, określając nazwę zmiennej dla każdej z nich i po każdej nazwie tablicy z nawiasami. Wiele zmiennych rozdziela się przecinkami.

```vb
Dim lastTime, nextTime, allTimes() As Date
```

W przypadku deklarowania więcej niż jednej zmiennej z jedną klauzulą `As` nie można dostarczyć inicjatora dla tej grupy zmiennych.

Można określić różne typy danych dla różnych zmiennych przy użyciu oddzielnej klauzuli `As` dla każdej zadeklarowanej zmiennej. Każda zmienna przyjmuje typ danych określony w pierwszej klauzuli `As` napotkanej po jego części `variablename`.

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a>Tablice

Można zadeklarować zmienną do przechowywania *tablicy*, która może zawierać wiele wartości. Aby określić, że zmienna przechowuje tablicę, obserwuj jej `variablename` bezpośrednio z nawiasami. Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).

Można określić dolną i górną granicę każdego wymiaru tablicy. W tym celu należy uwzględnić `boundslist` wewnątrz nawiasów. Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolną granicę. Dolna granica jest zawsze równa zero, niezależnie od tego, czy została określona, czy nie. Każdy indeks może się różnić od zera za pośrednictwem jego górnej wartości powiązanej.

Poniższe dwie instrukcje są równoważne. Każda instrukcja deklaruje tablicę z 21 `Integer` elementów. Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

Poniższa instrukcja deklaruje dwuwymiarową tablicę typu `Double`. Tablica zawiera 4 wiersze (3 + 1) z 6 kolumn (5 + 1) każdy. Należy zauważyć, że górna granica reprezentuje najwyższe możliwe wartości dla indeksu, a nie długość wymiaru. Wymiar jest długością górnej granicy powiększonej o jeden.

```vb
Dim matrix2(3, 5) As Double
```

Tablica może mieć od 1 do 32 wymiarów.

Wszystkie granice można pozostawić puste w deklaracji tablicy. W takim przypadku tablica ma określoną liczbę wymiarów, ale nie została zainicjowana. Ma wartość `Nothing`, dopóki nie zostanie zainicjowana co najmniej część jej elementów. Instrukcja `Dim` musi określać granice dla wszystkich wymiarów lub dla żadnych wymiarów.

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

Jeśli tablica ma więcej niż jeden wymiar, musisz uwzględnić przecinki między nawiasami, aby wskazać liczbę wymiarów.

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

*Tablicę o zerowej długości* można zadeklarować przez zadeklarowanie jednego z wymiarów tablicy jako-1. Zmienna, która przechowuje tablicę o zerowej długości, nie ma wartości `Nothing`. Tablice o zerowej długości są wymagane przez niektóre funkcje środowiska uruchomieniowego języka wspólnego. Jeśli spróbujesz uzyskać dostęp do takiej tablicy, wystąpi wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).

Można zainicjować wartości tablicy przy użyciu literału tablicy. W tym celu należy ująć wartości inicjujące za pomocą nawiasów klamrowych (`{}`).

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

W przypadku tablic wielowymiarowych Inicjalizacja dla każdego oddzielnego wymiaru jest ujęta w nawiasy klamrowe w zewnętrznym wymiarze. Elementy są określone w kolejności wierszy — główne.

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

Aby uzyskać więcej informacji na temat literałów tablicowych, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).

## <a name="default"></a>Domyślne typy danych i wartości

W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w instrukcji `Dim`.

|Określono typ danych?|Określono inicjator?|Przykład|Wynik|
|---|---|---|---|
|Nie|Nie|`Dim qty`|Jeśli [opcja Strict](option-strict-statement.md) jest wyłączona (wartość domyślna), zmienna jest ustawiona na `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|
|Nie|Tak|`Dim qty = 5`|Jeśli [opcja wnioskowanie](option-infer-statement.md) jest włączona (wartość domyślna), zmienna Pobiera typ danych inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączone i `Option Strict` jest wyłączone, zmienna Pobiera typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|
|Tak|Nie|`Dim qty As Integer`|Zmienna jest inicjowana do wartości domyślnej dla typu danych. Zapoznaj się z tabelą w dalszej części tej sekcji.|
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.|

Jeśli określisz typ danych, ale nie określisz inicjatora, Visual Basic inicjuje zmienną do wartości domyślnej dla tego typu danych. W poniższej tabeli przedstawiono domyślne wartości inicjujące.

|Typ danych|Wartość domyślna|
|---|---|
|Wszystkie typy liczbowe (w tym `Byte` i `SByte`)|0|
|`Char`|Plik binarny 0|
|Wszystkie typy odwołań (w tym `Object`, `String`i wszystkie tablice)|`Nothing`|
|`Boolean`|`False`|
|`Date`|12:00 AM 1 stycznia roku 1 (01/01/0001 12:00:00 AM)|

Każdy element struktury jest inicjowany tak, jakby była to odrębna zmienna. Jeśli deklarujesz długość tablicy, ale nie zainicjujesz jej elementów, każdy element jest inicjowany tak, jakby był oddzielną zmienną.

## <a name="static-local-variable-lifetime"></a>Okres istnienia statycznej zmiennej lokalnej

`Static` zmienna lokalna ma dłuższy okres istnienia niż procedura, w której jest zadeklarowana. Granice okresu istnienia zmiennej zależą od tego, gdzie procedura została zadeklarowana, oraz od tego, czy jest ona `Shared`.

|Deklaracja procedury|Zmienna została zainicjowana|Zmienna przerywa istniejące|
|---|---|---|
|W module|Przy pierwszym wywołaniu procedury|Gdy program zatrzyma wykonywanie|
|W klasie lub strukturze, procedura jest `Shared`|Przy pierwszym wywołaniu procedury w konkretnym wystąpieniu lub w samej klasie lub strukturze|Gdy program zatrzyma wykonywanie|
|W klasie lub strukturze procedura nie jest `Shared`|Przy pierwszym wywołaniu procedury w określonym wystąpieniu|Gdy wystąpienie zostanie wydane na potrzeby wyrzucania elementów bezużytecznych (GC)|

## <a name="attributes-and-modifiers"></a>Atrybuty i Modyfikatory

Atrybuty można stosować tylko do zmiennych składowych, nie do zmiennych lokalnych. Atrybut zawiera informacje dotyczące metadanych zestawu, który nie ma znaczenia dla magazynu tymczasowego, takiego jak zmienne lokalne.

Na poziomie modułu nie można użyć modyfikatora `Static`, aby zadeklarować zmienne składowe. Na poziomie procedury nie można używać `Shared`, `Shadows`, `ReadOnly`, `WithEvents`ani modyfikatorów dostępu do deklarowania zmiennych lokalnych.

Możesz określić, jaki kod może uzyskać dostęp do zmiennej, dostarczając `accessmodifier`. Zmienne składowe klasy i modułu (poza jakąkolwiek procedurą) domyślnie są dostępem prywatnym, a zmienne składowe struktury domyślnie mają dostęp publiczny. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Nie można używać modyfikatorów dostępu dla zmiennych lokalnych (wewnątrz procedury).

Można określić `WithEvents` tylko w zmiennych składowych, a nie na zmiennych lokalnych wewnątrz procedury. Jeśli określisz `WithEvents`, typem danych zmiennej musi być określony typ klasy, a nie `Object`. Nie można zadeklarować tablicy przy użyciu `WithEvents`. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [zdarzenia](../../programming-guide/language-features/events/index.md).

> [!NOTE]
> Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę zmiennej składowej o nazwie tej klasy, struktury lub modułu. Kod poza procedurą lub blok nie może odwoływać się do żadnych zmiennych lokalnych w ramach tej procedury lub bloku.

## <a name="releasing-managed-resources"></a>Zwalnianie zasobów zarządzanych

.NET Framework Moduł wyrzucania elementów bezużytecznych usuwa zarządzane zasoby bez żadnego dodatkowego kodowania w Twojej części. Można jednak wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.

Jeśli klasa jest zastosowana do szczególnie cennych i niedozwolonych zasobów (takich jak połączenie z bazą danych lub dojście do pliku), możesz nie czekać, aż następne odzyskiwanie pamięci zostanie oczyszczone wystąpienie klasy, które nie jest już używane. Klasa może zaimplementować interfejs <xref:System.IDisposable>, aby zapewnić możliwość zwolnienia zasobów przed wyrzucaniem elementów bezużytecznych. Klasa implementująca ten interfejs uwidacznia metodę `Dispose`, która może zostać wywołana, aby wymusić natychmiastowe wydanie cennych zasobów.

Instrukcja `Using` automatyzuje proces pozyskiwania zasobu, wykonywania zestawu instrukcji, a następnie usuwania zasobu. Jednak zasób musi implementować interfejs <xref:System.IDisposable>. Aby uzyskać więcej informacji, zobacz [using instrukcji](using-statement.md).

## <a name="example"></a>Przykład

Poniższy przykład deklaruje zmienne przy użyciu instrukcji `Dim` z różnymi opcjami.

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a>Przykład

Poniższy przykład zawiera listę numerów pierwszych z zakresu od 1 do 30. Zakres zmiennych lokalnych został opisany w komentarzach do kodu.

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a>Przykład

W poniższym przykładzie zmienna `speedValue` jest zadeklarowana na poziomie klasy. Słowo kluczowe `Private` jest używane do deklarowania zmiennej. Do zmiennej można uzyskać dostęp za pomocą procedury w klasie `Car`.

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a>Zobacz także

- [Const, instrukcja](const-statement.md)
- [ReDim, instrukcja](redim-statement.md)
- [Option Explicit, instrukcja](option-explicit-statement.md)
- [Option Infer, instrukcja](option-infer-statement.md)
- [Option Strict, instrukcja](option-strict-statement.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Deklaracja zmiennej](../../programming-guide/language-features/variables/variable-declaration.md)
- [Tablice](../../programming-guide/language-features/arrays/index.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [Wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md)
