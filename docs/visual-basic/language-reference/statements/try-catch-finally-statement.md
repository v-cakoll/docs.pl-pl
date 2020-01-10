---
title: Spróbuj... Catch... Finally — instrukcja
description: Dowiedz się, jak korzystać z obsługi wyjątków przy użyciu instrukcji Visual Basic try/catch/finally.
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
ms.openlocfilehash: bb6f17f7ce88caea0b9d30ec880194f2bb71c6a6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705772"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally — Instrukcja (Visual Basic)

Zapewnia sposób obsługi niektórych lub wszystkich możliwych błędów, które mogą wystąpić w danym bloku kodu, podczas gdy nadal działa kod.

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
|`tryStatements`|Opcjonalny. Instrukcje, w których może wystąpić błąd. Może być instrukcją złożoną.|
|`Catch`|Opcjonalny. Dozwolonych jest wiele bloków `Catch`. Jeśli wystąpi wyjątek podczas przetwarzania bloku `Try`, każda instrukcja `Catch` zostanie zbadana w kolejności tekstowej, aby określić, czy obsługuje wyjątek, z `exception` reprezentującą zgłoszony wyjątek.|
|`exception`|Opcjonalny. Dowolna nazwa zmiennej. Wartość początkowa `exception` jest wartością zgłoszonego błędu. Używane z `Catch`, aby określić błąd przechwycony. W przypadku pominięcia instrukcja `Catch` przechwytuje dowolny wyjątek.|
|`type`|Opcjonalny. Określa typ filtru klas. Jeśli wartość `exception` jest typu określonego przez `type` lub typu pochodnego, identyfikator zostanie powiązany z obiektem wyjątku.|
|`When`|Opcjonalny. Instrukcja `Catch` z klauzulą `When` przechwytuje wyjątki tylko wtedy, gdy `expression` oblicza `True`. Klauzula `When` jest stosowana tylko po sprawdzeniu typu wyjątku, a `expression` może odwoływać się do identyfikatora reprezentującego wyjątek.|
|`expression`|Opcjonalny. Należy niejawnie przekonwertować na `Boolean`. Dowolne wyrażenie opisujące filtr generyczny. Zwykle używany do filtrowania według numeru błędu. Używany z słowem kluczowym `When`, aby określić sytuacje, w których błąd jest przechwytywany.|
|`catchStatements`|Opcjonalny. Instrukcje do obsługi błędów występujących w skojarzonym bloku `Try`. Może być instrukcją złożoną.|
|`Exit Try`|Opcjonalny. Słowo kluczowe, które jest rozdzielony poza strukturę `Try...Catch...Finally`. Wykonywanie jest wznawiane z kodem bezpośrednio po instrukcji `End Try`. Instrukcja `Finally` nadal będzie wykonywana. Niedozwolone w blokach `Finally`.|
|`Finally`|Opcjonalny. Blok `Finally` jest zawsze wykonywany, gdy wykonanie opuszcza każdą część instrukcji `Try...Catch`.|
|`finallyStatements`|Opcjonalny. Instrukcje, które są wykonywane po wystąpieniu wszystkie inne błędy.|
|`End Try`|Kończy strukturę `Try...Catch...Finally`.|

## <a name="remarks"></a>Uwagi

Jeśli spodziewasz się, że konkretny wyjątek może wystąpić w określonej sekcji kodu, umieść kod w bloku `Try` i użyj bloku `Catch`, aby zachować kontrolę i obsłużyć wyjątek, jeśli wystąpi.

Instrukcja `Try…Catch` składa się z bloku `Try`, po którym następuje co najmniej jedna klauzula `Catch`, która określa programy obsługi dla różnych wyjątków. Gdy wyjątek jest zgłaszany w bloku `Try`, Visual Basic szuka instrukcji `Catch`, która obsługuje wyjątek. Jeśli nie odnaleziono zgodnej instrukcji `Catch`, Visual Basic analizuje metodę, która wywołała bieżącą metodę, i tak dalej na stosie wywołań. Jeśli nie zostanie znaleziony żaden blok `Catch`, Visual Basic wyświetli komunikat o nieobsługiwanym wyjątku dla użytkownika i zakończy wykonywanie programu.

W instrukcji `Try…Catch` można użyć więcej niż jednej instrukcji `Catch`. W takim przypadku kolejność klauzul `Catch` jest istotna, ponieważ są one badane w kolejności. Przechwyć bardziej szczegółowe wyjątki przed bardziej szczegółowymi.

Poniższe warunki instrukcji `Catch` są najmniej określone i przechwytuje wszystkie wyjątki, które pochodzą z klasy <xref:System.Exception>. Należy zwykle użyć jednej z tych odmian jako ostatniego bloku `Catch` w strukturze `Try...Catch...Finally`, po przechwyceniu wszystkich oczekiwanych wyjątków. Przepływ sterowania nigdy nie może dotrzeć do bloku `Catch`, który następuje po którejkolwiek z tych różnic.

- `type` jest `Exception`, na przykład: `Catch ex As Exception`

- Instrukcja nie ma `exception` zmiennej, na przykład: `Catch`

Gdy instrukcja `Try…Catch…Finally` jest zagnieżdżona w innym bloku `Try`, Visual Basic najpierw analizuje każdą `Catch` instrukcję w najbardziej wewnętrznym bloku `Try`. Jeśli nie zostanie znaleziona zgodna instrukcja `Catch`, wyszukiwanie przechodzi do instrukcji `Catch` zewnętrznego bloku `Try…Catch…Finally`.

Zmienne lokalne z bloku `Try` nie są dostępne w bloku `Catch`, ponieważ są to osobne bloki. Jeśli chcesz użyć zmiennej w więcej niż jednym bloku, zadeklaruj zmienną poza strukturą `Try...Catch...Finally`.

> [!TIP]
> Instrukcja `Try…Catch…Finally` jest dostępna jako fragment kodu IntelliSense. W Menedżerze fragmentów kodu rozwiń węzeł **wzorce kodu — IF, for each, try catch, Property itp**., a następnie **Obsługa błędów (wyjątki)** . Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Jeśli masz co najmniej jedną instrukcję, która musi zostać uruchomiona przed wyjściem ze struktury `Try`, użyj bloku `Finally`. Kontrolka przechodzi do bloku `Finally` tuż przed przekazaniem ze struktury `Try…Catch`. Jest to prawdziwe, nawet jeśli wystąpi wyjątek w dowolnym miejscu w strukturze `Try`.

Blok `Finally` jest przydatny do uruchamiania dowolnego kodu, który musi zostać wykonany, nawet jeśli wystąpi wyjątek. Kontrolka jest przenoszona do bloku `Finally`, niezależnie od tego, jak zamykany jest blok `Try...Catch`.

Kod w bloku `Finally` działa nawet wtedy, gdy kod napotka instrukcję `Return` w bloku `Try` lub `Catch`. Formant nie przeszedł z bloku `Try` lub `Catch` do odpowiedniego bloku `Finally` w następujących przypadkach:

- W bloku `Try` lub `Catch` wystąpił [instrukcja End](end-statement.md) .

- <xref:System.StackOverflowException> jest generowany w bloku `Try` lub `Catch`.

Nie można jawnie przetransferować wykonywania do bloku `Finally`. Transferowanie wykonywania z bloku `Finally` jest nieprawidłowe, z wyjątkiem wyjątku.

Jeśli instrukcja `Try` nie zawiera co najmniej jednego bloku `Catch`, musi zawierać blok `Finally`.

> [!TIP]
> Jeśli nie ma potrzeby przechwytywania określonych wyjątków, instrukcja `Using` zachowuje się jak blok `Try…Finally` i gwarantuje usunięcie zasobów, niezależnie od sposobu opuszczenia bloku. Dotyczy to nawet nieobsłużonego wyjątku. Aby uzyskać więcej informacji, zobacz [using instrukcji](using-statement.md).

## <a name="exception-argument"></a>Argument wyjątku

`Catch` bloku `exception` jest wystąpieniem klasy <xref:System.Exception> lub klasy, która pochodzi od klasy `Exception`. Wystąpienie klasy `Exception` odnosi się do błędu, który wystąpił w bloku `Try`.

Właściwości obiektu `Exception` ułatwiają zidentyfikowanie przyczyny i lokalizacji wyjątku. Na przykład właściwość <xref:System.Exception.StackTrace%2A> wyświetla listę wywoływanych metod, które doprowadziły do wyjątku, pomagając w znalezieniu, gdzie wystąpił błąd w kodzie. <xref:System.Exception.Message%2A> zwraca komunikat, który opisuje wyjątek. <xref:System.Exception.HelpLink%2A> zwraca link do skojarzonego pliku pomocy. <xref:System.Exception.InnerException%2A> zwraca obiekt `Exception`, który spowodował bieżący wyjątek lub zwraca `Nothing`, jeśli nie ma oryginalnego `Exception`.

## <a name="considerations-when-using-a-trycatch-statement"></a>Zagadnienia dotyczące korzystania z try... Catch — instrukcja

Użyj instrukcji `Try…Catch` tylko do sygnalizowania wystąpienia nietypowych lub nieoczekiwanych zdarzeń programu. Poniżej przedstawiono następujące przyczyny:

- Przechwytywanie wyjątków w środowisku uruchomieniowym powoduje utworzenie dodatkowych obciążeń i może być wolniejsze niż wstępne sprawdzanie, aby uniknąć wyjątków.

- Jeśli blok `Catch` nie jest obsługiwany prawidłowo, wyjątek może nie być poprawnie raportowany dla użytkowników.

- Obsługa wyjątków sprawia, że program jest bardziej skomplikowany.

Nie zawsze potrzebujesz instrukcji `Try…Catch`, aby sprawdzić warunek, który prawdopodobnie wystąpi. Poniższy przykład sprawdza, czy plik istnieje przed próbą jego otwarcia. Pozwala to ograniczyć potrzebę do przechwytywania wyjątku zgłoszonego przez metodę <xref:System.IO.File.OpenText%2A>.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Upewnij się, że kod w blokach `Catch` może poprawnie zgłosić wyjątki dla użytkowników, niezależnie od tego, czy jest to bezpieczne dla wątków rejestrowanie czy odpowiednie komunikaty. W przeciwnym razie wyjątki mogą pozostać nieznane.

## <a name="async-methods"></a>Metody asynchroniczne

Jeśli oznaczesz metodę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../operators/await-operator.md) w metodzie. Instrukcja z operatorem `Await` wstrzymuje wykonywanie metody do momentu zakończenia zadania oczekiwania. Zadanie reprezentuje trwającą prace. Gdy zadanie skojarzone z operatorem `Await` zakończy się, wykonywanie jest wznawiane w tej samej metodzie. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem w programach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

Zadanie zwrócone przez metodę asynchroniczną może zakończyć się niepowodzeniem, wskazując, że zostało zakończone z powodu nieobsługiwanego wyjątku. Zadanie może także zakończyć się w stanie anulowanym, co powoduje wyrzucanie `OperationCanceledException` w wyrażeniu await. Aby przechwytywać każdy typ wyjątku, umieść wyrażenie `Await` skojarzone z zadaniem w bloku `Try` i Przechwyć wyjątek w bloku `Catch`. Przykład znajduje się w dalszej części tego tematu.

Zadanie może być w stanie awarii, ponieważ wiele wyjątków jest odpowiedzialnych za jego awarię. Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Po oczekiwaniu na takie zadanie przechwycony wyjątek jest tylko jednym z wyjątków i nie można przewidzieć, który wyjątek zostanie przechwycony. Przykład znajduje się w dalszej części tego tematu.

Wyrażenie `Await` nie może znajdować się wewnątrz bloku `Catch` lub bloku `Finally`.

## <a name="iterators"></a>Iteratory

Funkcja iteratora lub metoda dostępu `Get` wykonuje iterację niestandardową w kolekcji. Iterator używa instrukcji [Yield](yield-statement.md) do zwrócenia każdego elementu kolekcji pojedynczo. Wywoływana jest funkcja iteratora przy użyciu [for each... Next — instrukcja](for-each-next-statement.md).

Instrukcja `Yield` może znajdować się wewnątrz bloku `Try`. Blok `Try` zawierający instrukcję `Yield` może mieć bloki `Catch` i może mieć blok `Finally`. Zapoznaj się z sekcją "Wypróbuj bloki w Visual Basic" [iteratorów](../../programming-guide/concepts/iterators.md) na przykład.

Instrukcja `Yield` nie może znajdować się wewnątrz bloku `Catch` lub bloku `Finally`.

Jeśli treść `For Each` (poza funkcją iteratora) zgłasza wyjątek, blok `Catch` w funkcji iteratora nie zostanie wykonany, ale jest wykonywany blok `Finally` w funkcji iteratora. Blok `Catch` wewnątrz funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.

## <a name="partial-trust-situations"></a>Sytuacje częściowej relacji zaufania

W sytuacjach częściowej relacji zaufania, takich jak aplikacja hostowana w udziale sieciowym, `Try...Catch...Finally` nie przechwytuje wyjątków zabezpieczeń, które występują przed wywołaniem metody, która jest wywoływana. Poniższy przykład, gdy umieścisz go w udziale serwera i uruchamiasz z tego miejsca, generuje błąd "System. Security. SecurityException: żądanie nie powiodło się." Aby uzyskać więcej informacji na temat wyjątków zabezpieczeń, zobacz Klasa <xref:System.Security.SecurityException>.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

W takiej sytuacji z częściowym zaufaniem należy umieścić instrukcję `Process.Start` w osobnym `Sub`. Początkowe wywołanie do `Sub` zakończy się niepowodzeniem. Dzięki temu `Try...Catch` przechwycenia, zanim `Sub`, który zawiera `Process.Start` zostanie uruchomiony i zostanie utworzony wyjątek zabezpieczeń.

## <a name="examples"></a>Przykłady

### <a name="the-structure-of-trycatchfinally"></a>Struktura try... Catch... Ostateczny

Poniższy przykład ilustruje strukturę instrukcji `Try...Catch...Finally`.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Wyjątek w metodzie wywoływanej z bloku try

W poniższym przykładzie metoda `CreateException` zgłasza `NullReferenceException`. Kod generujący wyjątek nie znajduje się w bloku `Try`. W związku z tym, Metoda `CreateException` nie obsługuje wyjątku. Metoda `RunSample` obsługuje wyjątek, ponieważ wywołanie metody `CreateException` znajduje się w bloku `Try`.

Przykład zawiera instrukcje `Catch` dla kilku typów wyjątków uporządkowanych od najbardziej do najbardziej ogólnego.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Instrukcja catch When

Poniższy przykład pokazuje, jak użyć instrukcji `Catch When`, aby odfiltrować wyrażenie warunkowe. Jeśli wyrażenie warunkowe oblicza `True`, kod w bloku `Catch` zostanie uruchomiony.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Zagnieżdżone Instrukcje try

Poniższy przykład zawiera instrukcję `Try…Catch`, która jest zawarta w bloku `Try`. Blok `Catch` wewnętrzny zgłasza wyjątek, który ma właściwość `InnerException` ustawioną na oryginalny wyjątek. Blok zewnętrzny `Catch` raportuje swój własny wyjątek i wewnętrzny wyjątek.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Obsługa wyjątków dla metod asynchronicznych

Poniższy przykład ilustruje obsługę wyjątków dla metod asynchronicznych. Aby przechwytywać wyjątek dotyczący zadania asynchronicznego, wyrażenie `Await` znajduje się w bloku `Try` obiektu wywołującego, a wyjątek jest przechwytywany w bloku `Catch`.

Usuń znaczniki komentarza z wiersza `Throw New Exception` w przykładzie, aby zademonstrować obsługę wyjątków. Wyjątek jest przechwytywany w bloku `Catch`, właściwość `IsFaulted` zadania jest ustawiona na `True`i Właściwość `Exception.InnerException` zadania jest ustawiona na wyjątek.

Usuń znaczniki komentarza z wiersza `Throw New OperationCancelledException`, aby zademonstrować, co się dzieje po anulowaniu procesu asynchronicznego. Wyjątek jest przechwytywany w bloku `Catch`, a właściwość `IsCanceled` zadania jest ustawiona na `True`. Jednakże w niektórych warunkach, które nie dotyczą tego przykładu, `IsFaulted` jest ustawiona na `True` i `IsCanceled` jest ustawiona na `False`.

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Obsługa wielu wyjątków w metodach asynchronicznych

Poniższy przykład ilustruje obsługę wyjątków, gdy wiele zadań może skutkować wieloma wyjątkami. Blok `Try` ma `Await` wyrażenie dla zadania, które <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> zwrócone. Zadanie zostanie ukończone, gdy zostaną wykonane trzy zadania, do których zastosowano <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.

Każdy z tych trzech zadań powoduje wyjątek. Blok `Catch` wykonuje iterację przez wyjątki, które znajdują się we właściwości `Exception.InnerExceptions` zadania, które `Task.WhenAll` zwrócone.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit, instrukcja](exit-statement.md)
- [On Error, instrukcja](on-error-statement.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Obsługa wyjątków](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw, instrukcja](throw-statement.md)
