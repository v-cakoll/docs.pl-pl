---
title: Dim — Instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c051572e83b915346d48ec12fb5d97f77b47e4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dim-statement-visual-basic"></a>Dim — Instrukcja (Visual Basic)
Deklaruje i alokuje magazyn przechowywania dla co najmniej jedną zmienną.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `accessmodifier`  
  
     Opcjonalna. Może to być jeden z następujących elementów:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     Opcjonalna. Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     Opcjonalna. Zobacz [statycznych](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     Opcjonalna. Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     Opcjonalna. Określa, że są one zmienne obiektów, które odwołują się do wystąpienia klasy, które może wywoływać zdarzenia. Zobacz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Wymagana. Lista zmiennych został zadeklarowany w tej instrukcji.  
  
     `variable [ , variable ... ]`  
  
     Każdy `variable` ma następujące składni i części:  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Część|Opis|  
    |---|---|  
    |`variablename`|Wymagana. Nazwa zmiennej. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|Opcjonalna. Lista granic dla każdego wymiaru tablicy zmiennej.|  
    |`New`|Opcjonalna. Tworzy nowe wystąpienie klasy po `Dim` uruchamia instrukcji.|  
    |`datatype`|Opcjonalna. Typ danych zmiennej.|  
    |`With`|Opcjonalna. Wprowadza na liście inicjatora obiektu.|  
    |`propertyname`|Opcjonalna. Nazwa właściwości w klasie tworzysz wystąpienia.|  
    |`propinitializer`|Wymagany po `propertyname` =. Wyrażenie, które jest obliczane i ma przypisaną nazwę właściwości.|  
    |`initializer`|Opcjonalny w przypadku `New` nie jest określona. Wyrażenie, które jest obliczane i przypisaną do zmiennej podczas jego tworzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilator Visual Basic używa `Dim` instrukcji do określenia typu danych i inne informacje, takie jak kodu, jakie mają dostęp do zmiennej. Poniższy przykład deklaruje zmienną do przechowywania `Integer` wartość.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Dla typu odwołania, możesz użyć `New` — słowo kluczowe, aby utworzyć nowe wystąpienie klasy lub struktury, który jest określony przez typ danych. Jeśli używasz `New`, nie należy używać wyrażenia inicjatora. Zamiast tego należy podać argumenty, jeśli są wymagane do konstruktora klasy, z którego tworzysz zmiennej.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Można zadeklarować zmiennej w procedurze, blok, klasy, struktury lub modułu. Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeni nazw lub interfejs. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Zmienna, która jest zadeklarowana na poziomie modułu, poza każda procedura jest *zmiennej członkowskiej* lub *pola*. Zmienne Członkowskie znajdują się w zakresie w całym ich klasy, struktury lub modułu. Zmienna, która jest zadeklarowana na poziomie procedura jest *zmiennej lokalnej*. Zmienne lokalne są w zakresie tylko w ramach ich procedurę lub blok.  
  
 Następujące modyfikatory dostępu są używane do deklarowania zmiennych poza procedurą: `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private`. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Dim` — Słowo kluczowe jest opcjonalna i zwykle pominąć, jeśli określono żadnego z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, lub `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Jeśli `Option Explicit` jest na (ustawienie domyślne), kompilator wymaga deklaracji dla każdej zmiennej można użyć. Aby uzyskać więcej informacji, zobacz [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Określanie wartości początkowej  
 Można przypisać wartości do zmiennej podczas jego tworzenia. Dla typu wartości, możesz użyć *inicjatora* umożliwiają określanie wartości wyrażenia do przypisania do zmiennej. Wyrażenia musi być stała, który może zostać obliczona w czasie kompilacji.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Jeśli określono inicjatora i typu danych nie została określona w `As` klauzuli *wnioskowanie* służy do wnioskować o typie danych z inicjatora. W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi. W drugim deklaracji wnioskowanie o typie wnioskuje typ z wartość 3.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 Wnioskowanie o typie stosowana na poziomie procedury. Nie ma zastosowania poza procedury w klasy, struktury, modułu lub interfejs. Aby uzyskać więcej informacji na temat wnioskowanie o typie, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Aby dowiedzieć, co się stanie, jeśli nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](../../../visual-basic/language-reference/statements/dim-statement.md#default) dalszej części tego tematu.  
  
 Można użyć *obiekt inicjatora* Aby zadeklarować wystąpień typy nazwane i anonimowe. Poniższy kod tworzy wystąpienie `Student` klasy i używa inicjatora obiektów, aby zainicjować właściwości.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Aby uzyskać więcej informacji na temat inicjatory obiektów, zobacz [porady: deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), i [typy anonimowe ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Deklarowanie zmiennych wielu  
 Można zadeklarować kilku zmiennych w jednej deklaracji instrukcji, określając nazwę zmiennej, dla każdej z nich, a następnie po każdej nazwy tablicy w nawiasach. Wiele zmiennych są oddzielone przecinkami.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 W przypadku więcej niż jedną zmienną z jednym `As` klauzuli, nie można podać inicjatora dla tej grupy zmiennych.  
  
 Można określić różne typy danych dla różnych zmiennych, przy użyciu oddzielnej `As` klauzula dla każdej zmiennej można zadeklarować. Każda zmienna ma typ danych określony w pierwszym `As` klauzuli napotkano po jego `variablename` części.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Tablice  
 Należy zadeklarować zmienną do przechowywania *tablicy*, która zawiera wiele wartości. Aby określić, że zmienna posiada tablicy, wykonaj jego `variablename` natychmiast w nawiasach. Aby uzyskać więcej informacji dotyczących tablic, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Można określić dolną i górną granicę każdego wymiaru tablicy. Aby to zrobić, należy uwzględnić `boundslist` wewnątrz nawiasów. Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolnej granicy. Dolna granica jest zawsze zero, czy została ona określona lub nie. Każdy indeks może różnić się od zera za pośrednictwem jego górna granica wartości.  
  
 Dwa poniższe instrukcje są równoważne. Każda instrukcja deklaruje tablicę 21 `Integer` elementów. Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 Następująca instrukcja deklaruje jest tablicą dwuwymiarową typu `Double`. Tablica ma 4 wiersze (3 + 1) 6 kolumn (5 + 1) każdego. Należy pamiętać, że górna granica reprezentuje najwyższą możliwą wartość indeksu nie długość wymiaru. Wymiar jest górna granica plus jeden.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Tablica może mieć od 1 do 32 wymiarów.  
  
 Wszystkie granice może pozostać puste deklaracji tablicy. Jeśli to zrobisz, tablica ma liczbę wymiarów, które określisz, ale jest niezainicjowany. Ma ona wartość `Nothing` do momentu zainicjowania w co najmniej niektóre z jego elementów. `Dim` Instrukcja musi określać granice wszystkie wymiary lub nie wymiarów.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Jeśli tablica ma więcej niż jednym wymiarze, musi zawierać przecinków między nawiasy, aby wskazać liczbę wymiarów.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Można zadeklarować *o zerowej długości tablicy* przez zadeklarowanie jedną wymiary tablicy jako wartość -1. Zmienna, która przechowuje tablicą o zerowej długości nie ma wartości `Nothing`. Tablice o zerowej długości są wymagane przez niektóre typowe funkcje środowiska uruchomieniowego języka. Próba dostępu do tych tablicy wystąpi wyjątek czasu wykonywania. Aby uzyskać więcej informacji, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Wartości w tablicy można zainicjować za pomocą literału tablicy. Aby to zrobić, należy ująć inicjowania wartości ujęte w nawiasy klamrowe (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Dla wielowymiarowych tablic inicjowania dla każdego wymiaru oddzielne jest ujęta w nawiasy klamrowe w wymiarze zewnętrzne. Elementy są określone w kolejności wierszy.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Aby uzyskać więcej informacji na temat Literały tablicy, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
##  <a name="default"></a> Dane domyślne typy i wartości  
 W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji `Dim` instrukcji.  
  
|Określony typ danych?|Inicjator określona?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.|  
|Nie|Tak|`Dim qty = 5`|Jeśli [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Zobacz tabelę w dalszej części tej sekcji.|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.|  
  
 Jeśli można określić typu danych, ale nie należy określać inicjatora, Visual Basic inicjuje zmiennej na wartość domyślną dla tego typu danych. W poniższej tabeli przedstawiono domyślne wartości inicjowania.  
  
|Typ danych|Wartość domyślna|  
|---|---|  
|Wszystkie typy liczbowe (łącznie z `Byte` i `SByte`)|0|  
|`Char`|Binarny 0|  
|Wszystkie typy odwołań (łącznie z `Object`, `String`, a wszystkie tablice)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|00:00:00 1 stycznia 1 roku (0001-01/01 00:00:00: 00)|  
  
 Każdy element struktury został zainicjowany, tak jakby był on osobnej zmiennej. Czy zadeklarować długość tablicy, ale nie zainicjować swoich elementów, każdy element została zainicjowana, tak jakby był on osobnej zmiennej.  
  
## <a name="static-local-variable-lifetime"></a>Statyczne okres istnienia zmiennej lokalnej  
 A `Static` zmiennej lokalnej ma dłuższy okres istnienia niż procedury, w którym jest zadeklarowany. Granice istnienia zmiennej zależą od którym jest zadeklarowany jako procedura oraz czy jest `Shared`.  
  
|Deklaracja procedury|Zmienna została zainicjowana|Zmienna zatrzymuje istniejących|  
|---|---|---|  
|W module|Procedura jest wywoływana po raz pierwszy|Gdy program zatrzymuje wykonywanie|  
|W klasie lub strukturze jest procedury `Shared`|Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu lub dla klasy lub struktury, sama|Gdy program zatrzymuje wykonywanie|  
|W klasie lub strukturze nie jest procedurą `Shared`|Procedura jest wywoływana na określonym wystąpieniu po raz pierwszy|Po zwolnieniu wystąpienie dla wyrzucanie elementów bezużytecznych (GC)|  
  
## <a name="attributes-and-modifiers"></a>Atrybuty i Modyfikatory  
 Atrybuty można stosować tylko do zmiennych Członkowskich, a nie do zmiennych lokalnych. Atrybut przyczynia się informacji metadanych zestawu, która nie jest zrozumiały dla tymczasowego magazynu, takich jak zmiennych lokalnych.  
  
 Na poziomie modułu, nie można użyć `Static` modyfikator do deklarowania zmiennych Członkowskich. Na poziomie procedury nie można użyć `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, lub dowolnego dostępu Modyfikatory do deklarowania zmiennych lokalnych.  
  
 Można określić, jaki kod uzyskać dostęp do zmiennej, podając `accessmodifier`. Klasy i moduł domyślny zmienne (poza dowolnej procedury) elementu członkowskiego o dostępie prywatnym i domyślnie zmienne Członkowskie struktury dostępu publicznego. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Nie można używać modyfikatorów dostępu na zmienne lokalne (wewnątrz procedury).  
  
 Można określić `WithEvents` tylko dla zmiennych Członkowskich, a nie na zmiennych lokalnych wewnątrz procedury. Jeśli określisz `WithEvents`, typ danych zmiennej musi być typem określonej klasy nie `Object`. Nie można zadeklarować tablicy o `WithEvents`. Aby uzyskać więcej informacji o zdarzeniach, zobacz [zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Kod poza klasą, strukturą lub modułu muszą nazwy zmiennej członkowskiej z nazwą tej klasy, struktury lub modułu. Kod poza procedurę lub blok nie może odwoływać się do żadnych zmiennych lokalnych w ramach tej procedury lub bloku.  
  
## <a name="releasing-managed-resources"></a>Zwolnienie zasobów zarządzanych  
 Moduł zbierający elementy bezużyteczne .NET Framework usuwa zasoby zarządzane bez żadnych dodatkowych kodowania ze strony użytkownika. Można jednak wymusić usuwania zarządzanych zasobów, zamiast czekać na moduł garbage collector.  
  
 Jeśli klasa jest przechowywana na szczególnie cenne i ograniczonych zasobów (takich jak dojścia połączenia lub pliku bazy danych), może nie chcesz czekać do następnego wyrzucanie elementów bezużytecznych wyczyścić wystąpienia klasy, która nie jest już używana. Klasa może zawierać implementację <xref:System.IDisposable> interfejsu sposób, aby zwolnić zasoby przed wyrzucania elementów bezużytecznych. Udostępnia klasy, która implementuje ten interfejs `Dispose` metody, który można wywołać, aby wymusić cenne zasoby pozostają dostępne do zwolnienia natychmiast.  
  
 `Using` Instrukcji automatyzuje proces pobierania zasobu, wykonywania zbiór instrukcji i następnie Usuwanie zasobu. Jednak zasobu musi implementować <xref:System.IDisposable> interfejsu. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje zmienne przy użyciu `Dim` instrukcji z różnymi opcjami.  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera listę liczb pierwszych od 1 do 30. Zakres zmiennych lokalnych jest opisany w komentarze w kodzie.  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `speedValue` deklaracji zmiennej na poziomie klasy. `Private` Słowo kluczowe jest używane w celu zadeklarowania zmiennej. Procedury w programie można można uzyskać dostępu do zmiennej `Car` klasy.  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
