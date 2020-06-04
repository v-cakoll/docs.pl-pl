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
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391771"
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
|`Catch`|Opcjonalny. `Catch`Dozwolonych jest wiele bloków. Jeśli wystąpi wyjątek podczas przetwarzania `Try` bloku, każda `Catch` instrukcja jest sprawdzana w kolejności tekstowej, aby określić, czy obsługuje wyjątek, `exception` przedstawiając wyjątek, który został zgłoszony.|
|`exception`|Opcjonalny. Dowolna nazwa zmiennej. Wartość początkowa `exception` to wartość zgłoszonego błędu. Używane z `Catch` , aby określić błąd przechwycony. W przypadku pominięcia `Catch` instrukcja przechwytuje dowolny wyjątek.|
|`type`|Opcjonalny. Określa typ filtru klas. Jeśli wartość `exception` jest typu określonego przez `type` lub typu pochodnego, identyfikator zostanie powiązany z obiektem wyjątku.|
|`When`|Opcjonalny. `Catch`Instrukcja z `When` klauzulą przechwytuje wyjątki tylko wtedy `expression` , gdy szacuje wartość `True` . `When`Klauzula jest stosowana tylko po sprawdzeniu typu wyjątku i `expression` może odwoływać się do identyfikatora reprezentującego wyjątek.|
|`expression`|Opcjonalny. Musi być niejawnie przekonwertowana na `Boolean` . Dowolne wyrażenie opisujące filtr generyczny. Zwykle używany do filtrowania według numeru błędu. Używany ze `When` słowem kluczowym, aby określić sytuacje, w których błąd jest przechwytywany.|
|`catchStatements`|Opcjonalny. Instrukcje do obsługi błędów występujących w skojarzonym `Try` bloku. Może być instrukcją złożoną.|
|`Exit Try`|Opcjonalny. Słowo kluczowe, które jest rozdzielony poza `Try...Catch...Finally` strukturę. Wykonywanie jest wznawiane z kodem bezpośrednio po `End Try` instrukcji. `Finally`Instrukcja nadal będzie wykonywana. Niedozwolone w `Finally` blokach.|
|`Finally`|Opcjonalny. `Finally`Blok jest zawsze wykonywany, gdy wykonanie opuszcza jakąkolwiek część `Try...Catch` instrukcji.|
|`finallyStatements`|Opcjonalny. Instrukcje, które są wykonywane po wystąpieniu wszystkie inne błędy.|
|`End Try`|Kończy `Try...Catch...Finally` strukturę.|

## <a name="remarks"></a>Uwagi

Jeśli spodziewasz się, że konkretny wyjątek może wystąpić w określonej sekcji kodu, umieść kod w `Try` bloku i Użyj `Catch` bloku, aby zachować kontrolę i obsłużyć wyjątek, jeśli wystąpi.

`Try…Catch`Instrukcja składa się z `Try` bloku, po którym następuje co najmniej jedna `Catch` klauzula, która określa programy obsługi dla różnych wyjątków. Gdy wyjątek jest zgłaszany w `Try` bloku, Visual Basic szuka `Catch` instrukcji, która obsługuje wyjątek. Jeśli `Catch` nie znaleziono zgodnej instrukcji, Visual Basic analizuje metodę, która wywołała bieżącą metodę, i tak dalej na stosie wywołań. Jeśli nie `Catch` zostanie znaleziony żaden blok, Visual Basic wyświetli komunikat o nieobsługiwanym wyjątku dla użytkownika i zakończy wykonywanie programu.

W instrukcji można użyć więcej niż jednej `Catch` instrukcji `Try…Catch` . W takim przypadku kolejność `Catch` klauzul jest istotna, ponieważ są one badane w kolejności. Przechwyć bardziej szczegółowe wyjątki przed bardziej szczegółowymi.

Poniższe `Catch` warunki instrukcji są najmniej określone i przechwytuje wszystkie wyjątki, które pochodzą od <xref:System.Exception> klasy. Należy zwykle użyć jednej z tych odmian jako ostatniego `Catch` bloku w `Try...Catch...Finally` strukturze, po przechwyceniu wszystkich oczekiwanych wyjątków. Przepływ sterowania nigdy nie dociera do `Catch` bloku, który następuje po którejkolwiek z tych różnic.

- Na `type` `Exception` przykład:`Catch ex As Exception`

- Instrukcja nie ma `exception` zmiennej, na przykład:`Catch`

Gdy `Try…Catch…Finally` instrukcja jest zagnieżdżona w innym `Try` bloku, Visual Basic najpierw analizuje każdą `Catch` instrukcję w wewnętrznym `Try` bloku. Jeśli nie `Catch` zostanie znaleziona zgodna instrukcja, wyszukiwanie przechodzi do `Catch` instrukcji `Try…Catch…Finally` bloku zewnętrznego.

Zmienne lokalne z `Try` bloku nie są dostępne w bloku, `Catch` ponieważ są oddzielnymi blokami. Jeśli chcesz użyć zmiennej w więcej niż jednym bloku, zadeklaruj zmienną poza `Try...Catch...Finally` strukturą.

> [!TIP]
> `Try…Catch…Finally`Instrukcja jest dostępna jako fragment kodu IntelliSense. W Menedżerze fragmentów kodu rozwiń węzeł **wzorce kodu — IF, for each, try catch, Property itp**., a następnie **Obsługa błędów (wyjątki)**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).

## <a name="finally-block"></a>Blok finally

Jeśli masz co najmniej jedną instrukcję, która musi zostać uruchomiona przed wyjściem ze `Try` struktury, użyj `Finally` bloku. Kontrolka przechodzi do `Finally` bloku tuż przed przekazaniem jej do `Try…Catch` struktury. Jest to prawdziwe, nawet jeśli wystąpi wyjątek w dowolnym miejscu wewnątrz `Try` struktury.

`Finally`Blok jest przydatny do uruchamiania dowolnego kodu, który musi zostać wykonany, nawet jeśli wystąpi wyjątek. Kontrolka jest przenoszona do `Finally` bloku, niezależnie od tego, w jaki sposób `Try...Catch` zamykany jest blok.

Kod w `Finally` bloku działa nawet wtedy, gdy kod napotka `Return` instrukcję w `Try` `Catch` bloku lub. Formant nie przeszedł z `Try` bloku lub `Catch` do odpowiadającego `Finally` bloku w następujących przypadkach:

- W bloku lub występuje [instrukcja End](end-statement.md) `Try` `Catch` .

- Element <xref:System.StackOverflowException> jest generowany w `Try` bloku lub `Catch` .

Nie można jawnie przetransferować wykonywania do `Finally` bloku. Przenoszenie wykonywania poza `Finally` blok jest nieprawidłowe, z wyjątkiem wyjątku.

Jeśli `Try` instrukcja nie zawiera co najmniej jednego `Catch` bloku, musi zawierać `Finally` blok.

> [!TIP]
> Jeśli nie ma potrzeby przechwytywania określonych wyjątków, `Using` instrukcja zachowuje się jak `Try…Finally` blok i gwarantuje usunięcie zasobów, niezależnie od sposobu opuszczenia bloku. Dotyczy to nawet nieobsłużonego wyjątku. Aby uzyskać więcej informacji, zobacz [using instrukcji](using-statement.md).

## <a name="exception-argument"></a>Argument wyjątku

`Catch`Argument bloku `exception` jest wystąpieniem <xref:System.Exception> klasy lub klasy, która pochodzi od `Exception` klasy. `Exception`Wystąpienie klasy odnosi się do błędu, który wystąpił w `Try` bloku.

Właściwości `Exception` obiektu pomagają zidentyfikować przyczynę i lokalizację wyjątku. Na przykład <xref:System.Exception.StackTrace%2A> Właściwość zawiera listę wywoływanych metod, które doprowadziły do wyjątku, pomagając znaleźć miejsce wystąpienia błędu w kodzie. <xref:System.Exception.Message%2A>zwraca komunikat, który opisuje wyjątek. <xref:System.Exception.HelpLink%2A>zwraca link do skojarzonego pliku pomocy. <xref:System.Exception.InnerException%2A>zwraca `Exception` obiekt, który spowodował bieżący wyjątek lub zwraca, `Nothing` Jeśli nie istnieje oryginalny `Exception` .

## <a name="considerations-when-using-a-trycatch-statement"></a>Zagadnienia dotyczące korzystania z try... Catch — instrukcja

Użyj `Try…Catch` instrukcji tylko do sygnalizowania wystąpienia nietypowych lub nieoczekiwanych zdarzeń programu. Poniżej przedstawiono następujące przyczyny:

- Przechwytywanie wyjątków w środowisku uruchomieniowym powoduje utworzenie dodatkowych obciążeń i może być wolniejsze niż wstępne sprawdzanie, aby uniknąć wyjątków.

- Jeśli `Catch` blok nie jest prawidłowo obsługiwany, wyjątek może nie być poprawnie raportowany dla użytkowników.

- Obsługa wyjątków sprawia, że program jest bardziej skomplikowany.

Nie zawsze potrzebujesz `Try…Catch` instrukcji, aby sprawdzić warunek, który prawdopodobnie wystąpi. Poniższy przykład sprawdza, czy plik istnieje przed próbą jego otwarcia. Zmniejsza to potrzebę przechwycenia wyjątku zgłoszonego przez <xref:System.IO.File.OpenText%2A> metodę.

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

Upewnij się, że kod w `Catch` blokach może prawidłowo raportować wyjątki do użytkowników, niezależnie od tego, czy jest to bezpieczne dla wątków rejestrowanie czy odpowiednie komunikaty. W przeciwnym razie wyjątki mogą pozostać nieznane.

## <a name="async-methods"></a>Metody asynchroniczne

Jeśli oznaczesz metodę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../operators/await-operator.md) w metodzie. Instrukcja z `Await` operatorem wstrzymuje wykonywanie metody do momentu zakończenia zadania oczekiwania. Zadanie reprezentuje trwającą prace. Gdy zadanie skojarzone z `Await` operatorem zakończy się, wykonywanie jest wznawiane w tej samej metodzie. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md).

Zadanie zwrócone przez metodę asynchroniczną może zakończyć się niepowodzeniem, wskazując, że zostało zakończone z powodu nieobsługiwanego wyjątku. Zadanie może również zakończyć się w stanie anulowanym, co powoduje `OperationCanceledException` wyrzucanie wyników w wyrażeniu await. Aby przechwytywać każdy typ wyjątku, umieść `Await` wyrażenie skojarzone z zadaniem w `Try` bloku i Przechwyć wyjątek w `Catch` bloku. Przykład znajduje się w dalszej części tego tematu.

Zadanie może być w stanie awarii, ponieważ wiele wyjątków jest odpowiedzialnych za jego awarię. Na przykład zadanie może być wynikiem wywołania metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> . Po oczekiwaniu na takie zadanie przechwycony wyjątek jest tylko jednym z wyjątków i nie można przewidzieć, który wyjątek zostanie przechwycony. Przykład znajduje się w dalszej części tego tematu.

`Await`Wyrażenie nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.

## <a name="iterators"></a>Iteratory

Funkcja iteratora lub `Get` metoda dostępu wykonuje iterację niestandardową w kolekcji. Iterator używa instrukcji [Yield](yield-statement.md) do zwrócenia każdego elementu kolekcji pojedynczo. Wywoływana jest funkcja iteratora przy użyciu [for each... Next — instrukcja](for-each-next-statement.md).

`Yield`Instrukcja może znajdować się wewnątrz `Try` bloku. `Try`Blok zawierający `Yield` instrukcję może mieć `Catch` bloki i może mieć `Finally` blok. Zapoznaj się z sekcją "Wypróbuj bloki w Visual Basic" [iteratorów](../../programming-guide/concepts/iterators.md) na przykład.

`Yield`Instrukcja nie może znajdować się wewnątrz `Catch` bloku lub `Finally` bloku.

Jeśli `For Each` treść (poza funkcją iteratora) zgłasza wyjątek, `Catch` blok w funkcji iteratora nie jest wykonywany, ale `Finally` jest wykonywany blok w funkcji iteratora. `Catch`Blok wewnątrz funkcji iteratora przechwytuje tylko wyjątki, które występują wewnątrz funkcji iteratora.

## <a name="partial-trust-situations"></a>Sytuacje częściowej relacji zaufania

W sytuacjach częściowej relacji zaufania, takich jak aplikacja hostowana w udziale sieciowym, program `Try...Catch...Finally` nie przechwytuje wyjątków zabezpieczeń, które wystąpiły przed wywołaniem metody, która jest wywoływana. Poniższy przykład, gdy umieścisz go w udziale serwera i uruchamiasz z tego miejsca, generuje błąd "System. Security. SecurityException: żądanie nie powiodło się." Aby uzyskać więcej informacji na temat wyjątków zabezpieczeń, zobacz <xref:System.Security.SecurityException> Klasa.

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

W takiej sytuacji z częściowym zaufaniem należy umieścić `Process.Start` instrukcję w oddzielnym `Sub` . Początkowe wywołanie do `Sub` nie powiedzie się. Umożliwia to `Try...Catch` przechwycenie tego programu przed `Sub` `Process.Start` rozpoczęciem działania, a wygenerowany wyjątek zabezpieczeń.

## <a name="examples"></a>Przykłady

### <a name="the-structure-of-trycatchfinally"></a>Struktura try... Catch... Ostateczny

Poniższy przykład ilustruje strukturę `Try...Catch...Finally` instrukcji.

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Wyjątek w metodzie wywoływanej z bloku try

W poniższym przykładzie `CreateException` Metoda generuje `NullReferenceException` . Kod generujący wyjątek nie znajduje się w `Try` bloku. W związku z tym `CreateException` Metoda nie obsługuje wyjątku. `RunSample`Metoda obsługuje wyjątek, ponieważ wywołanie `CreateException` metody znajduje się w `Try` bloku.

Przykład zawiera `Catch` instrukcje dla kilku typów wyjątków, uporządkowane od najbardziej do najbardziej ogólnego.

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>Instrukcja catch When

Poniższy przykład pokazuje, jak używać `Catch When` instrukcji do filtrowania wyrażenia warunkowego. Jeśli wyrażenie warunkowe oblicza wartość `True` , kod w `Catch` bloku zostanie uruchomiony.

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>Zagnieżdżone Instrukcje try

Poniższy przykład zawiera `Try…Catch` instrukcję, która jest zawarta w `Try` bloku. Blok wewnętrzny `Catch` zgłasza wyjątek, który ma `InnerException` ustawioną właściwość na oryginalny wyjątek. W bloku zewnętrznym są `Catch` raportowane własne wyjątki i wewnętrzny wyjątek.

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>Obsługa wyjątków dla metod asynchronicznych

Poniższy przykład ilustruje obsługę wyjątków dla metod asynchronicznych. Aby przechwytywać wyjątek, który ma zastosowanie do zadania asynchronicznego, `Await` wyrażenie jest w `Try` bloku obiektu wywołującego, a wyjątek jest przechwytywany w `Catch` bloku.

Usuń komentarz `Throw New Exception` wiersza z przykładu, aby zademonstrować obsługę wyjątków. Wyjątek jest przechwytywany w `Catch` bloku, `IsFaulted` Właściwość zadania jest ustawiona na `True` , a `Exception.InnerException` Właściwość zadania jest ustawiona na wyjątek.

Usuń komentarz z `Throw New OperationCancelledException` wiersza, aby zademonstrować, co się dzieje po anulowaniu procesu asynchronicznego. Wyjątek jest przechwytywany w `Catch` bloku, a `IsCanceled` Właściwość zadania jest ustawiona na `True` . Jednak w pewnych warunkach, które nie dotyczą tego przykładu, `IsFaulted` jest ustawiona na `True` i `IsCanceled` jest ustawiona na `False` .

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>Obsługa wielu wyjątków w metodach asynchronicznych

Poniższy przykład ilustruje obsługę wyjątków, gdy wiele zadań może skutkować wieloma wyjątkami. `Try`Blok zawiera `Await` wyrażenie dla <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> zwracanego zadania. Zadanie zostanie ukończone, gdy zostaną zakończone trzy zadania, do których <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> zastosowano.

Każdy z tych trzech zadań powoduje wyjątek. `Catch`Blok wykonuje iterację w wyjątkach, które znajdują się we `Exception.InnerExceptions` właściwości zadania, które zostało `Task.WhenAll` zwrócone.

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit, instrukcja](exit-statement.md)
- [On Error, instrukcja](on-error-statement.md)
- [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](/visualstudio/ide/best-practices-for-using-code-snippets)
- [Obsługa wyjątków](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw — Instrukcja](throw-statement.md)
