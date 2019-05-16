---
title: Try... CATCH... Finally — instrukcja - Visual Basic
description: Dowiedz się użyć obsługi wyjątków za pomocą instrukcji języka Visual Basic Try/Catch/Finally.
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.custom: seodec18
ms.openlocfilehash: 126f20c86bb47e8002382e069ce6236600394aba
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638770"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally — Instrukcja (Visual Basic)

Zapewnia sposób obsługi niektórych lub wszystkich możliwych błędów, które mogą wystąpić w danym bloku kodu, bez przerywania działania kodu.

## <a name="syntax"></a>Składnia

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`tryStatements`|Opcjonalna. Instrukcji, w których może wystąpić błąd. Może być instrukcję złożonego.|
|`Catch`|Opcjonalna. Wiele `Catch` dozwolonych bloków. Jeśli wystąpi wyjątek podczas przetwarzania `Try` zablokować, każdy `Catch` instrukcji jest badany w tekstową kolejności w celu ustalenia, czy obsługuje wyjątek, za pomocą `exception` reprezentujący wyjątek, który został zgłoszony.|
|`exception`|Opcjonalna. Dowolna nazwa zmiennej. Początkowa wartość `exception` jest wartością wyrzuconego błędu. Używane z `Catch` do określenia błąd przechwycono. W przypadku pominięcia `Catch` instrukcji przechwytuje wszystkie wyjątki.|
|`type`|Opcjonalna. Określa typ Filtr klasy. Jeśli wartość `exception` typu określonego przez `type` lub typu pochodnego, identyfikator staje się powiązany obiekt wyjątku.|
|`When`|Opcjonalna. A `Catch` instrukcję, określając `When` klauzula przechwytuje wyjątki tylko wtedy, gdy `expression` daje w wyniku `True`. A `When` klauzula jest stosowana tylko po sprawdzanie typu wyjątku, i `expression` mogą odwoływać się do identyfikatora reprezentujący wyjątek.|
|`expression`|Opcjonalna. Musi umożliwiać niejawną konwersję `Boolean`. Dowolne wyrażenie filtru uniwersalnego. Zwykle używane do filtrowania według numer błędu. Używane z `When` — słowo kluczowe, aby określić okoliczności, w których zostanie przechwycony błąd.|
|`catchStatements`|Opcjonalna. Liczba zapytań: do obsługi błędów występujących w skojarzonym `Try` bloku. Może być instrukcję złożonego.|
|`Exit Try`|Opcjonalna. Słowo kluczowe, które przerywa poza `Try...Catch...Finally` struktury. Wykonanie zostanie wznowione kod bezpośrednio po `End Try` instrukcji. `Finally` Nadal będzie można wykonać instrukcji. Nie są dozwolone w `Finally` bloków.|
|`Finally`|Opcjonalna. A `Finally` bloku jest zawsze wykonywana podczas wykonywania pozostawi dowolnej części `Try...Catch` instrukcji.|
|`finallyStatements`|Opcjonalna. Instrukcji, które są wykonywane po przeprowadzeniu przetwarzanie wszystkich innych błędów.|
|`End Try`|Kończy `Try...Catch...Finally` struktury.|

## <a name="remarks"></a>Uwagi

Jeśli spodziewasz się, że określony wyjątek może odbywały się w określonej sekcji kodu, umieść kod `Try` blokowania i użyj `Catch` bloku, aby zachować kontrolę i obsłużyć wyjątek, jeśli występuje.

A `Try…Catch` instrukcji składa się z `Try` bloku, po której następuje co najmniej jeden `Catch` zdań, która określa programy obsługi dla różnych wyjątków. Gdy wyjątek jest zgłaszany w `Try` zablokować, Visual Basic szuka `Catch` instrukcję, która obsługuje dany wyjątek. Jeśli pasujący obiekt typu `Catch` instrukcja nie zostanie znaleziony, Visual Basic sprawdza metody, która wywołała bieżącą metodę, i tak dalej w górę stosu wywołań. Jeśli nie `Catch` blok zostanie znaleziony, Visual Basic wyświetli komunikat nieobsługiwany wyjątek użytkownikowi i zatrzymuje wykonywanie programu.

Można użyć więcej niż jednej `Catch` instrukcji w `Try…Catch` instrukcji. Jeśli to zrobisz, kolejność `Catch` klauzule ma znaczenie, ponieważ są one badane w kolejności. Rejestrować bardziej szczegółowe wyjątki przed mniej określone z nich.

Następujące `Catch` warunków instrukcji najmniej specyficznych i przechwytywać wszystkie wyjątki, które wynikają z <xref:System.Exception> klasy. Zazwyczaj należy użyć jednego z tych zmian jako ostatni `Catch` blok w `Try...Catch...Finally` struktury po Przechwytywanie określonych wyjątków oczekujesz. Przepływ sterowania nigdy nie może osiągnąć `Catch` blok, który następuje po jednej z tych zmian.

- `type` Jest `Exception`, na przykład: `Catch ex As Exception`

- Wykonywanie instrukcji nie ma przypisanego `exception` zmiennej, na przykład: `Catch`

Gdy `Try…Catch…Finally` instrukcji jest zagnieżdżona w innej `Try` bloku, Visual Basic najpierw sprawdza, czy każdy `Catch` instrukcji w najbardziej wewnętrzną funkcją `Try` bloku. Jeśli brak zgodności `Catch` instrukcji zostanie znaleziony, wyszukiwanie rozpoczynające się `Catch` instrukcji zewnętrznego `Try…Catch…Finally` bloku.

Zmienne lokalne z `Try` nie są dostępne w bloku `Catch` bloku, ponieważ są one osobnych blokach. Jeśli chcesz użyć zmiennej w więcej niż jednego bloku, Zadeklaruj zmienną poza `Try...Catch...Finally` struktury.

> [!TIP]
> `Try…Catch…Finally` Instrukcja jest dostępny jako fragment kodu IntelliSense. W Menedżerze fragmentów kodu, rozwiń **wzorce kodu - Jeśli For Each, Try Catch, właściwości, etc**, a następnie **obsługę błędów (wyjątki)**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Jeśli masz jedną lub więcej instrukcji, które muszą zostać uruchomione przed zakończeniem pracy `Try` struktury, należy użyć `Finally` bloku. Kontrola przechodzi do `Finally` block przed przekazaniem poza `Try…Catch` struktury. Ta zasada obowiązuje nawet, jeśli wystąpi wyjątek, dowolne miejsce wewnątrz `Try` struktury.

A `Finally` bloku jest przydatne w przypadku uruchomieniem jakiegokolwiek kodu, które musi wykonać, nawet jeśli występuje wyjątek. Sterowanie jest przekazywane do `Finally` bloku niezależnie od tego, jak `Try...Catch` block wyjść.

Kod w `Finally` block przebiegów, nawet wtedy, gdy napotka kodu `Return` instrukcji w `Try` lub `Catch` bloku. Kontrola przechodzi z `Try` lub `Catch` block do odpowiednich `Finally` bloku w następujących przypadkach:

- [End — instrukcja](end-statement.md) zostanie napotkany w `Try` lub `Catch` bloku.

- A <xref:System.StackOverflowException> jest zgłaszany w `Try` lub `Catch` bloku.

Nie jest prawidłową jawnie przenieść wykonania do `Finally` bloku. Transferowanie wykonywania z `Finally` bloku jest nieprawidłowy, z wyjątkiem za pośrednictwem wyjątek.

Jeśli `Try` instrukcji nie zawiera co najmniej jeden `Catch` bloku, musi ono zawierać `Finally` bloku.

> [!TIP]
> Jeśli nie masz określonych wyjątków catch `Using` instrukcji zachowuje się jak `Try…Finally` bloku i gwarancje usuwania zasobów, niezależnie od tego, jak zamknąć blok. Ta zasada obowiązuje nawet w przypadku nieobsługiwanego wyjątku. Aby uzyskać więcej informacji, zobacz [instrukcji Using](using-statement.md).

## <a name="exception-argument"></a>Wyjątek argumentu

`Catch` Bloku `exception` argument jest wystąpieniem <xref:System.Exception> klasy lub klasy, która pochodzi od klasy `Exception` klasy. `Exception` Wystąpienia klasy odnosi się do błędu, który wystąpił w `Try` bloku.

Właściwości `Exception` obiektu pomoc, aby zidentyfikować przyczynę i lokalizacja wyjątku. Na przykład <xref:System.Exception.StackTrace%2A> listy właściwości o nazwie metody, które doprowadziły do niego, pomagając Ci znaleźć, w którym wystąpił błąd w kodzie. <xref:System.Exception.Message%2A> Zwraca komunikat opisujący wyjątek. <xref:System.Exception.HelpLink%2A> Zwraca łącze do skojarzonego pliku pomocy. <xref:System.Exception.InnerException%2A> Zwraca `Exception` zwraca obiekt, który spowodował bieżący wyjątek lub jest on `Nothing` przypadku nie oryginału `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Uwagi dotyczące korzystania z Try... CATCH — instrukcja

Użyj `Try…Catch` instrukcji tylko do sygnalizowania wystąpienia zdarzenia programu nietypowe lub nieoczekiwany. Ze względu na to m.in:

- Przechwytywanie wyjątków w czasie wykonywania tworzy dodatkowe obciążenie i może być wolniejsze niż wstępnie sprawdzanie w celu uniknięcia wyjątków.

- Jeśli `Catch` blok nie jest obsługiwany poprawnie, wyjątek może nie być zgłaszany prawidłowo dla użytkowników.

- Obsługa wyjątków sprawia, że program jest bardziej złożone.

Nie należy zawsze `Try…Catch` instrukcję, aby sprawdzać występowanie warunku, który może nastąpić. Poniższy przykład sprawdza, czy istnieje plik przed podjęciem próby go otworzyć. Zmniejsza to potrzebę przechwytywanie wyjątku wyrzuconego przez <xref:System.IO.File.OpenText%2A> metody.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Upewnij się, że kod w `Catch` bloki prawidłowo może zgłaszać wyjątków dla użytkowników, poprzez rejestrowanie metodą o bezpiecznych wątkach lub odpowiednie komunikaty. W przeciwnym razie wyjątki mogą pozostać nieznany.

## <a name="async-methods"></a>Metody asynchroniczne

Po oznaczeniu metody z [Async](../modifiers/async.md) modyfikator, można użyć [Await](../operators/await-operator.md) operatora w metodzie. Instrukcja zawierająca `Await` operator zawiesza wykonywanie metody, dopóki nie zakończy się oczekiwane zadanie. Zadanie reprezentuje pracę w toku. Gdy zadanie, które jest skojarzone z `Await` operator zakończy pracę, wznawia wykonanie w tej samej metody. Aby uzyskać więcej informacji, zobacz [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Zadanie zwracane przez metody asynchronicznej może zakończyć się w nieprawidłowym stanie, wskazującą, czy zakończyła się z powodu nieobsługiwanego wyjątku. Zadanie może również zakończyć stanem anulowane, co skutkuje `OperationCanceledException` zgłaszane poza wyrażenie await. Aby przechwycić wyjątek dowolnego typu, umieść `Await` wyrażenia, która jest skojarzona z zadaniem w `Try` zablokować, a następnie przechwycić wyjątek w `Catch` bloku. Przykład znajduje się w dalszej części tego tematu.

Zadanie może być w nieprawidłowym stanie, ponieważ wiele wyjątków były odpowiedzialne za jego powodujący błąd. Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. W przypadku takiego zadania, zgłoszony wyjątek jest tylko jeden z wyjątków, a nie można przewidzieć, który wyjątek zostanie zgłoszony. Przykład znajduje się w dalszej części tego tematu.

`Await` Wyrażenie nie może być wewnątrz `Catch` bloku lub `Finally` bloku.

## <a name="iterators"></a>Iteratory

Funkcji iteratora lub `Get` akcesor wykonuje niestandardowych iteracji przez kolekcję. Używa iteratora [uzyskanie](yield-statement.md) instrukcja zwraca każdy element kolekcji naraz. Wywołanie funkcji iteratora przy użyciu [For Each... Następna instrukcja](for-each-next-statement.md).

A `Yield` instrukcji może znajdować się wewnątrz `Try` bloku. A `Try` blok, który zawiera `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku. Zobacz sekcję "wypróbuj bloków w języku Visual Basic" [Iteratory](../../programming-guide/concepts/iterators.md) przykład.

A `Yield` instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.

Jeśli `For Each` treści (poza funkcji iteratora) zgłasza wyjątek, `Catch` nie jest wykonywany blok w funkcji iteratora, ale `Finally` wykonaniu bloku w funkcji iteratora. A `Catch` bloku sterującego funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.

## <a name="partial-trust-situations"></a>Sytuacjach częściowego zaufania

W sytuacjach częściowego zaufania, takich jak z aplikacją hostowaną w udziale sieciowym `Try...Catch...Finally` nie przechwytuje wyjątków zabezpieczeń, które występują przed wywołaniem metody, która zawiera wywołanie. Poniższy przykład w przypadku umieścić go w udziale serwera i uruchomienia w tym miejscu, powoduje błąd "System.Security.SecurityException: Żądanie nie powiodło się." Aby uzyskać więcej informacji na temat wyjątków zabezpieczeń, zobacz <xref:System.Security.SecurityException> klasy.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

W takiej sytuacji częściowego zaufania, należy umieścić `Process.Start` instrukcji w osobnym `Sub`. Początkowe wywołanie `Sub` zakończy się niepowodzeniem. Dzięki temu `Try...Catch` do przechwytywania przed `Sub` zawierający `Process.Start` została uruchomiona i generowane wyjątek zabezpieczeń.

## <a name="examples"></a>Przykłady

### <a name="the-structure-of-trycatchfinally"></a>Struktury Try... CATCH... Na koniec

W poniższym przykładzie pokazano strukturę `Try...Catch...Finally` instrukcji.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Wyjątek w metodzie wywoływane z blokiem Try

W poniższym przykładzie `CreateException` metoda zgłasza wyjątek `NullReferenceException`. Kod, który generuje wyjątek nie znajduje się w `Try` bloku. W związku z tym `CreateException` metoda nie zapewnia obsługi wyjątku. `RunSample` Metoda obsłużyć wyjątek, ponieważ wywołanie `CreateException` jest metoda `Try` bloku.

Przykład zawiera `Catch` instrukcji pod kątem kilku typów wyjątków, uporządkowane od najbardziej specyficznych do najbardziej ogólną.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Instrukcja Catch, gdy

Poniższy przykład pokazuje, jak używać `Catch When` instrukcji do filtrowania wyrażenia warunkowego. Jeśli wynikiem obliczenia wyrażenia warunkowego jest `True`, kod w `Catch` block przebiegów.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Zagnieżdżonych instrukcji Try

W poniższym przykładzie przedstawiono `Try…Catch` instrukcję, która jest zawarta w `Try` bloku. Wewnętrzny `Catch` bloku zgłasza wyjątek, który ma jej `InnerException` właściwość ustawioną na oryginalnego wyjątku. Zewnętrzny `Catch` bloku raporty swój własny wyjątek i wyjątek wewnętrzny.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Obsługa do metod asynchronicznych wyjątków

Poniższy przykład ilustruje wyjątków, obsługa do metod asynchronicznych. Aby przechwytywać wyjątek, który ma zastosowanie do zadania asynchronicznego `Await` wyrażenie `Try` blok wywołującego, po czym wyjątek zostaje przechwycony w `Catch` bloku.

Usuń znaczniki komentarza `Throw New Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków. Wyjątek w `Catch` block zadania podrzędnego `IsFaulted` właściwość jest ustawiona na `True`i zadania podrzędnego `Exception.InnerException` właściwość jest ustawiona na wyjątek.

Usuń znaczniki komentarza `Throw New OperationCancelledException` wiersz, aby zademonstrować, co się stanie, gdy anulujesz proces asynchroniczny. Wyjątek w `Catch` bloku i zadania podrzędnego `IsCanceled` właściwość jest ustawiona na `True`. Jednak w niektórych warunkach, które nie mają zastosowania do tego przykładu `IsFaulted` ustawiono `True` i `IsCanceled` ustawiono `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Obsługa wielu wyjątków w metodach asynchronicznych

Poniższy przykład ilustruje wyjątków, gdzie wiele zadań może spowodować wiele wyjątków. `Try` Blok ma `Await` wyrażenia dla zadania, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> zwracane. Zadanie zostało ukończone, gdy trzy zadania, do którego <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> są stosowane są kompletne.

Każdy z trzech zadań, powoduje wyjątek. `Catch` Bloku wykonuje iterację przez wyjątki, które znajdują się w `Exception.InnerExceptions` właściwości zadania, `Task.WhenAll` zwracane.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit, instrukcja](exit-statement.md)
- [On Error, instrukcja](on-error-statement.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Obsługa wyjątków](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw, instrukcja](throw-statement.md)
