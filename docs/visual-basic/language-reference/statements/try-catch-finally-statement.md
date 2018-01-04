---
title: "Try...Catch...Finally — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "69"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c297a84b37b455a4b30b1848aa9bdd30dc567ec1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally — Instrukcja (Visual Basic)
Zapewnia sposób obsługi niektórych lub wszystkich możliwych błędów, które mogą wystąpić w danym bloku kodu, w trakcie wykonywania kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`tryStatements`|Opcjonalny. Instrukcji, w których może wystąpić błąd. Może być złożonej instrukcji.|  
|`Catch`|Opcjonalny. Wiele `Catch` bloki dozwolone. Jeśli wystąpi wyjątek podczas przetwarzania `Try` zablokować każdego `Catch` instrukcji jest sprawdzany w kolejności tekstowej w celu ustalenia, czy obsługuje wyjątek, z `exception` reprezentujący wyjątek, który został wygenerowany.|  
|`exception`|Opcjonalny. Dowolna nazwa zmiennej. Początkowa wartość `exception` jest wartością zgłoszenia błędu. Używane z `Catch` do określenia błąd przechwycony. Pominięcie `Catch` instrukcji przechwytuje żadnych wyjątków.|  
|`type`|Opcjonalny. Określa typ klasy filtru. Jeśli wartość `exception` jest typu określonego przez `type` lub typu pochodnego identyfikator staje się powiązany obiekt wyjątku.|  
|`When`|Opcjonalny. A `Catch` instrukcji z `When` klauzula przechwytuje wyjątków tylko wtedy, gdy `expression` daje w wyniku `True`. A `When` tylko po sprawdzanie typu wyjątku, stosowana jest klauzula i `expression` mogą odwoływać się do identyfikatora reprezentujący wyjątek.|  
|`expression`|Opcjonalny. Musi istnieć możliwość niejawnego przekonwertowania na `Boolean`. Dowolne wyrażenie filtru ogólnego. Zwykle używane do filtrowania według numer błędu. Używane z `When` — słowo kluczowe, aby określić okoliczności, w których zostanie przechwycony błąd.|  
|`catchStatements`|Opcjonalny. Instrukcji do obsługi błędów występujących w skojarzonym `Try` bloku. Może być złożonej instrukcji.|  
|`Exit Try`|Opcjonalny. Słowo kluczowe, która dzieli poza `Try...Catch...Finally` struktury. Wznawia wykonywanie kodu bezpośrednio po `End Try` instrukcji. `Finally` Nadal będzie można wykonać instrukcji. Nie są dozwolone w `Finally` bloków.|  
|`Finally`|Opcjonalny. A `Finally` bloku jest zawsze wykonywana podczas wykonywania pozostawia dowolną część `Try...Catch` instrukcji.|  
|`finallyStatements`|Opcjonalny. Instrukcji, które są wykonywane po zakończeniu wszystkich innych wystąpił błąd podczas przetwarzania.|  
|`End Try`|Kończy `Try...Catch...Finally` struktury.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli przypuszczasz, że określonego wyjątku mogą wystąpić w określonej sekcji kodu, umieść kod `Try` blokować i użyj `Catch` bloku, aby zachować kontrolę i obsłużyć wyjątek, jeśli występuje.  
  
 A `Try…Catch` instrukcji składa się z `Try` bloku, po której następuje co najmniej jeden `Catch` postanowienia Określ obsługę różne wyjątki. Jeśli wyjątek jest zgłaszany `Try` bloku, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] szuka `Catch` instrukcji, która obsługuje wyjątek. Jeśli odpowiadającego mu `Catch` instrukcja nie zostanie znaleziony, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sprawdza metodę, która wywołuje bieżącej metody i tak dalej górę stosu wywołań. Jeśli nie `Catch` bloku zostanie znaleziony, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jest wyświetlany komunikat nieobsługiwany wyjątek i zatrzymuje wykonywanie programu.  
  
 Można użyć więcej niż jednej `Catch` instrukcji w `Try…Catch` instrukcji. Jeśli to zrobisz, kolejność `Catch` klauzule jest ważna, ponieważ są one sprawdzane w kolejności. CATCH bardziej szczegółowe wyjątki przed mniej określonych zadań.  
  
 Następujące `Catch` warunków instrukcji najmniej specyficznych i będzie przechwytywać wszystkie wyjątki pochodzące z <xref:System.Exception> klasy. Zwykle należy użyć jednej z tych zmian ostatnio `Catch` blok w `Try...Catch...Finally` struktury po Przechwytywanie wszystkich wyjątków szczególne spodziewasz się. Przepływ sterowania, nigdy nie może nawiązać połączenie `Catch` bloku poniżej jedną z tych zmian.  
  
-   `type` Jest `Exception`, na przykład:`Catch ex As Exception`  
  
-   Wykonywanie instrukcji nie ma `exception` zmiennej, na przykład:`Catch`  
  
 Gdy `Try…Catch…Finally` instrukcji jest zagnieżdżony w innym `Try` bloku, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] najpierw sprawdza każdego `Catch` instrukcji w najbardziej wewnętrzną funkcją `Try` bloku. Jeśli pasujących `Catch` instrukcji zostanie znaleziony, wyszukiwanie będzie kontynuowane do `Catch` instrukcje zewnętrznego `Try…Catch…Finally` bloku.  
  
 Zmienne lokalne z `Try` nie są dostępne w bloku `Catch` zablokować, ponieważ są one oddzielne bloków. Jeśli chcesz użyć zmiennej w bloku więcej niż jeden, należy zadeklarować zmienną poza `Try...Catch...Finally` struktury.  
  
> [!TIP]
>  `Try…Catch…Finally` Instrukcja jest dostępna jako fragmentu kodu IntelliSense. W Menedżerze fragmentów kodu, rozwiń węzeł **wzorce kodu - Jeśli, For Each, Try Catch, właściwości, itd**, a następnie **obsługi błędu (wyjątki)**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="finally-block"></a>Bloku finally  
 Jeśli masz jedną lub więcej instrukcji, które muszą zostać uruchomione przed zakończeniem pracy `Try` struktury, użyj `Finally` bloku. Kontrola przechodzi do `Finally` zablokować tuż przed przekazaniem poza `Try…Catch` struktury. Dotyczy to nawet, jeśli w dowolnym miejscu wystąpi wyjątek `Try` struktury.  
  
 A `Finally` blok jest przydatne do uruchomienia dowolnego kodu, który należy wykonać, nawet jeśli dostępny jest wyjątek. Kontrola jest przekazywana do `Finally` bloku niezależnie od tego, jak `Try...Catch` zablokować wyjścia.  
  
 Kod w `Finally` blokowanie działa nawet wtedy, gdy wystąpi kodu `Return` instrukcji w `Try` lub `Catch` bloku. Formant nie przejdzie z `Try` lub `Catch` zablokować do odpowiednich `Finally` blok w następujących przypadkach:  
  
-   [Instrukcji End](../../../visual-basic/language-reference/statements/end-statement.md) napotkano w `Try` lub `Catch` bloku.  
  
-   A <xref:System.StackOverflowException> jest zgłaszany `Try` lub `Catch` bloku.  
  
 Nie jest prawidłową jawnie przekazanie wykonywania w `Finally` bloku. Transferowanie wykonywania z `Finally` bloku jest nieprawidłowy, z wyjątkiem przez wyjątek.  
  
 Jeśli `Try` instrukcji nie zawiera co najmniej jeden `Catch` bloku, musi ona zawierać `Finally` bloku.  
  
> [!TIP]
>  Jeśli nie masz przechwytują wyjątki określonych `Using` instrukcji zachowuje się jak `Try…Finally` bloku i usuwania gwarancje zasobów, niezależnie od tego, jak zakończyć bloku. Dotyczy to nawet w przypadku nieobsługiwany wyjątek. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="exception-argument"></a>Argument wyjątku  
 `Catch` Bloku `exception` argument jest wystąpieniem <xref:System.Exception> klasy lub klasą pochodzącą z `Exception` klasy. `Exception` Wystąpienie klasy odpowiada błędu, który wystąpił w `Try` bloku.  
  
 Właściwości `Exception` obiekt pomoc, aby zidentyfikować przyczynę i lokalizacji wyjątku. Na przykład <xref:System.Exception.StackTrace%2A> listy właściwości wywoływane metody, które doprowadziły do wyjątku, pomaga znaleźć, w którym wystąpił błąd w kodzie. <xref:System.Exception.Message%2A>Zwraca komunikat opisujący wyjątek. <xref:System.Exception.HelpLink%2A>Zwraca łącze do skojarzony plik pomocy. <xref:System.Exception.InnerException%2A>Zwraca `Exception` zwraca obiekt, który spowodował bieżącego wyjątku lub `Nothing` przypadku nie oryginału `Exception`.  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Uwagi dotyczące korzystania z bloku Try... CATCH — instrukcja  
 Użyj `Try…Catch` oświadczenie tylko w celu zasygnalizowania wystąpienia zdarzeń nietypowe lub nieprzewidziane programu. Dostępne są następujące przyczyny to:  
  
-   Przechwytywanie wyjątków w czasie wykonywania tworzy dodatkowe obciążenie i może być mniejsza niż Sprawdzanie wstępnie, aby uniknąć wyjątków.  
  
-   Jeśli `Catch` bloku nie jest obsługiwana prawidłowo, wyjątek może nie być prawidłowo raportowane dla użytkowników.  
  
-   Obsługa wyjątków sprawia, że program jest bardziej złożone.  
  
 Zawsze nie trzeba `Try…Catch` instrukcji, aby sprawdzić, czy warunek, który może nastąpić. Poniższy przykład umożliwia sprawdzenie, czy istnieje plik przed podjęciem próby go otworzyć. Zmniejsza to potrzebę przechwytywanie wyjątków zgłaszanych przez <xref:System.IO.File.OpenText%2A> metody.  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 Upewnij się, że kod w `Catch` bloki prawidłowo zgłosić wyjątki dla użytkowników, poprzez rejestrowanie wątkowo lub odpowiednie wiadomości. W przeciwnym razie wyjątki mogą pozostać nieznany.  
  
## <a name="async-methods"></a>Metody asynchroniczne  
 Po zaznaczeniu metodę o [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w metodzie. Instrukcja zawierająca `Await` operator wstrzymuje wykonywanie metody do momentu ukończenia zadania oczekiwano. Zadanie reprezentuje pracy w toku. Gdy zadanie, z którym skojarzony jest `Await` operator zakończeniu wznawia wykonywanie w tej samej metody. Aby uzyskać więcej informacji, zobacz [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Zadanie zwrócone przez metody asynchronicznej może zakończyć się stan, wskazującą, czy zakończyła się z powodu nieobsługiwanego wyjątku. Zadania mogą również kończyć się w stanie anulowane, co powoduje `OperationCanceledException` zgłaszane poza wyrażenie await. Aby przechwycić albo typu wyjątku, zaznacz `Await` wyrażenia, który został skojarzony z zadaniem w `Try` zablokować, a także catch wyjątku w `Catch` bloku. Przykład znajduje się w dalszej części tego tematu.  
  
 Zadanie może być stan, ponieważ wiele wyjątków są odpowiedzialne za jego spowodowaniem błędu. Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Gdy await takie zadania, zgłoszony wyjątek jest tylko jeden z wyjątków i nie można przewidzieć który wyjątek zostanie przechwycony. Przykład znajduje się w dalszej części tego tematu.  
  
 `Await` Wyrażenie nie może być wewnątrz `Catch` bloku lub `Finally` bloku.  
  
## <a name="iterators"></a>Iteratory  
 Funkcji iteracyjnej lub `Get` akcesor wykonuje niestandardowych iteracji w kolekcji. Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element kolekcji jednym naraz. Wywołania funkcji iteratora przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 A `Yield` instrukcja może być wewnątrz `Try` bloku. A `Try` bloku, który zawiera `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku. Zobacz sekcję "Spróbuj bloków w języku Visual Basic" [Iteratory](../../programming-guide/concepts/iterators.md) przykład.  
  
 A `Yield` instrukcja nie może być wewnątrz `Catch` bloku lub `Finally` bloku.  
  
 Jeśli `For Each` treści (poza funkcją iteratora) zgłasza wyjątek, `Catch` bloku w funkcji iteracyjnej nie została wykonana, ale `Finally` wykonaniu bloku w funkcji iteracyjnej. A `Catch` bloku wewnątrz funkcji iteracyjnej przechwytuje tylko wyjątki, które występuje wewnątrz funkcji iteracyjnej.  
  
## <a name="partial-trust-situations"></a>Sytuacjach częściowego zaufania  
 W sytuacjach częściowego zaufania, takich jak aplikacji hostowanej w udziale sieciowym `Try...Catch...Finally` nie przechwytuje wyjątków zabezpieczeń, które występują przed wywoływana jest metoda, która zawiera wywołanie. W poniższym przykładzie, po umieszczeniu go w udziale serwera i uruchom stamtąd generuje błąd "System.Security.SecurityException: żądanie nie powiodło się." Aby uzyskać więcej informacji na temat wyjątki zabezpieczeń, zobacz <xref:System.Security.SecurityException> klasy.  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 W takiej sytuacji częściowego zaufania, należy umieścić `Process.Start` instrukcji w oddzielnej `Sub`. Wywołanie początkowej `Sub` zakończy się niepowodzeniem. Dzięki temu `Try...Catch` do wychwytywania go przed `Sub` zawierający `Process.Start` została uruchomiona i wyprodukowanych wyjątek zabezpieczeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia struktury `Try...Catch...Finally` instrukcji.  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `CreateException` metoda zgłasza `NullReferenceException`. Kod, który generuje wyjątek nie znajduje się w `Try` bloku. W związku z tym `CreateException` — metoda nie obsługuje wyjątek. `RunSample` Metody obsługi wyjątku, ponieważ wywołanie `CreateException` metoda znajduje się w `Try` bloku.  
  
 Przykład obejmuje `Catch` instrukcje dla kilku typów wyjątków, uporządkowanych z najbardziej specyficzne dla najbardziej ogólnym.  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Catch When` instrukcji do filtrowania wyrażenia warunkowego. Jeśli wyrażenia warunkowego `True`, kod w `Catch` blokowanie działa.  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Try…Catch` instrukcji, która jest zawarta w `Try` bloku. Wewnętrzny `Catch` bloku zgłasza wyjątek, który ma jego `InnerException` właściwość pierwotny wyjątek. Zewnętrznego `Catch` bloku raporty własną wyjątek i wyjątek wewnętrzny.  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia obsługi dla metod asynchronicznych wyjątków. Aby przechwytywać wyjątku, który dotyczy zadania asynchronicznego `Await` wyrażenie `Try` bloku wywołującego i wyjątek zostanie przechwycony w `Catch` bloku.  
  
 Usuń znaczniki komentarza `Throw New Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków. Wyjątek w `Catch` zablokować zadania `IsFaulted` właściwość jest ustawiona na `True`i zadania `Exception.InnerException` właściwość jest ustawiona na wyjątek.  
  
 Usuń znaczniki komentarza `Throw New OperationCancelledException` wiersza, aby zademonstrować, co się stanie w przypadku anulowania proces asynchroniczny. Wyjątek w `Catch` bloku i zadania `IsCanceled` właściwość jest ustawiona na `True`. Jednak w niektórych warunkach, które nie dotyczą w tym przykładzie `IsFaulted` ustawiono `True` i `IsCanceled` ma ustawioną wartość `False`.  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia obsługi wyjątków, gdzie wiele zadań może spowodować wiele wyjątków. `Try` Blok ma `Await` wyrażenia do zadania, który <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> zwrócony. Zadanie zostało ukończone, gdy trzy zadań, do którego <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> jest stosowane są spełnione.  
  
 Wszystkie trzy zadania powoduje zgłoszenie wyjątku. `Catch` Bloku iteruje wyjątki, które znajdują się w `Exception.InnerExceptions` właściwość zadania który `Task.WhenAll` zwracane.  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:System.Exception>  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](/visualstudio/ide/best-practices-for-using-code-snippets)  
 [Obsługa wyjątków](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)  
 [Throw, instrukcja](../../../visual-basic/language-reference/statements/throw-statement.md)
