---
title: "try-catch (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 753beb554796ad0aa2c5e15c715240453de9a3e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="try-catch-c-reference"></a>try-catch (odwołanie w C#)
Instrukcji try-catch składa się z `try` bloku, po której następuje co najmniej jeden `catch` postanowienia Określ obsługę różnych wyjątków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wyjątek szuka środowisko uruchomieniowe języka wspólnego (CLR) `catch` instrukcji, która obsługuje ten wyjątek. Jeśli aktualnie wykonywane — metoda nie zawiera takie `catch` zablokować wygląda CLR w metodę, która wywołuje bieżącej metody i tak dalej górę stosu wywołań. Jeśli nie `catch` bloku zostanie znaleziony, a następnie CLR jest wyświetlany komunikat nieobsługiwany wyjątek i zatrzymuje wykonywanie programu.  
  
 `try` Blok zawiera ochroną kod, który może spowodować wyjątek. Blok jest wykonywana do czasu zgłoszenia wyjątku lub zakończyło się powodzeniem. Na przykład następujące próba rzutowania `null` obiekt zgłasza <xref:System.NullReferenceException> wyjątek:  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 Mimo że `catch` bez argumentów można użyć klauzuli w celu efektywnej dowolnego typu wyjątku, to użycie nie jest zalecane. Ogólnie rzecz biorąc powinien catch tylko te wyjątki, które należy znać sposób odzyskanie. W związku z tym należy zawsze podać argument obiektu pochodną <xref:System.Exception?displayProperty=nameWithType> na przykład:  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 Można użyć więcej niż jednej określonej `catch` klauzuli w tej samej instrukcji try-catch. W tym przypadku kolejność `catch` klauzule ważne jest, ponieważ `catch` klauzule są sprawdzane w kolejności. CATCH bardziej szczegółowe wyjątki przed mniej określonych zadań. Kompilator generuje błąd jeśli kolejność się, że Twoje catch blokuje tak, aby nigdy nie można połączyć się z blokiem nowsze.  
  
 Przy użyciu `catch` argumentów jest jednym ze sposobów Filtruj wyjątki mają być obsługiwane.  Umożliwia także wyrażenie predykatu, dalsze badający wyjątku, aby zdecydować, czy do jego obsługi.  Jeśli wyrażenie predykatu zwraca wartość false, jest tworzona wyszukiwania dla programu obsługi.  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 Filtry wyjątków są preferowane przechwytywanie i ponowne generowanie (wyjaśniono poniżej), ponieważ stos nieokaleczone pozostaw filtrów.  Nowsze obsługi zrzuty stosu, widać gdzie wyjątek pierwotnie pochodzeniu, a nie tylko ostatnie miejsce, który został wywołany ponownie.  Rejestrowanie zdarzeń użycia wyrażeń filtru wyjątków.  Można utworzyć predykatu funkcję, która zawsze zwraca wartość false, również zapisującego w dzienniku można rejestrować wyjątki, jak komputery przechodzą bez konieczności ich i ponownego zgłoszenia.  
  
 A [throw](../../../csharp/language-reference/keywords/throw.md) instrukcja może być używana w `catch` bloku, aby można było ponownie zgłosić wyjątek, który zostanie przechwycony przez `catch` instrukcji. Poniższy przykład wyodrębnia informacje o źródle <xref:System.IO.IOException> wyjątek, a następnie zgłasza wyjątek do nadrzędnej metody.  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 Można przechwytywać elementu exception jednego i zgłoszenie wyjątku różnych. Gdy to zrobisz, określ wyjątek, który Przechwycono wewnętrzny wyjątek, jak pokazano w poniższym przykładzie.  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 Użytkownik może również ponownie Zgłoś wyjątek podczas określony warunek ma wartość true, jak pokazano w poniższym przykładzie.  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 Z wewnątrz `try` bloków, zainicjować tylko zmienne, które są zadeklarowane w nim. W przeciwnym razie wyjątek może wystąpić przed zakończeniem wykonywania bloku. Na przykład w poniższym przykładzie kodu zmiennej `n` zainicjowano wewnątrz `try` bloku. Próba użycia tej zmiennej poza `try` blok w `Write(n)` instrukcji wygeneruje błąd kompilatora.  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 Aby uzyskać więcej informacji na temat catch, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
## <a name="exceptions-in-async-methods"></a>Wyjątki w metodach asynchronicznych  
 Metody asynchronicznej zostało oznaczone przez [async](../../../csharp/language-reference/keywords/async.md) modyfikator i zwykle zawiera jeden lub więcej await wyrażenia lub instrukcji. Stosuje wyrażenie await [await](../../../csharp/language-reference/keywords/await.md) operatora <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.  
  
 Gdy kontrolować osiągnie `await` w metodzie asynchronicznej postęp w metodzie jest wstrzymana, aż do zakończenia oczekiwano zadań. Po zakończeniu zadania wykonywania można wznowić w metodzie. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md) i [przepływ sterowania w aplikacjach asynchronicznych](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
 Zakończone zadanie, do którego `await` zastosowano może być stan z powodu nieobsługiwany wyjątek w metodzie, która zwraca zadanie. Oczekiwanie na zadanie zgłasza wyjątek. Zadania można także zakończyć w stanie Anulowane Jeśli proces asynchroniczny, która zwraca go została anulowana. Oczekiwanie na zadanie anulowane zgłasza `OperationCanceledException`. Aby uzyskać więcej informacji o sposobie anulować proces asynchroniczny, zobacz [Fine-Tuning Twoja aplikacja Async](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Aby catch wyjątku, await zadanie w `try` zablokować, a także przechwytywanie wyjątków w skojarzonych `catch` bloku. Na przykład zobacz sekcję "Example".  
  
 Zadanie może być stan, ponieważ w metodzie asynchronicznej oczekiwano wystąpił wiele wyjątków. Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Await takie zadania, tylko jeden wyjątek zostanie przechwycony i nie można przewidzieć który wyjątek zostanie przechwycony. Na przykład zobacz sekcję "Example".  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `try` blok zawiera wywołanie `ProcessString` metodę, która może spowodować wyjątek. `catch` Klauzula zawiera program obsługi wyjątku, który właśnie na ekranie zostanie wyświetlony komunikat. Gdy `throw` instrukcji jest wywoływana z wewnątrz `MyMethod`, system wyszukuje `catch` instrukcji i wyświetlany jest komunikat `Exception caught`.  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie używane są dwa bloki catch, a specyficzny wyjątek, który zostanie osiągnięty jako pierwszy, zostanie przechwycony.  
  
 Aby przechwytywać elementu exception najmniej specyficznych, można zastąpić w instrukcji throw `ProcessString` z następujących instrukcji: `throw new Exception()`.  
  
 Jeśli najpierw umieścić blok catch do najmniej specyficznych w przykładzie zostanie wyświetlony następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia obsługi dla metod asynchronicznych wyjątków. Aby przechwytywać wyjątku, który zgłasza zadania asynchronicznego, umieść `await` wyrażenie w `try` zablokować, a także catch wyjątku w `catch` bloku.  
  
 Usuń znaczniki komentarza `throw new Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków. Zadania `IsFaulted` właściwość jest ustawiona na `True`, zadania `Exception.InnerException` właściwość jest ustawiona na wyjątek i wyjątek w `catch` bloku.  
  
 Usuń znaczniki komentarza `throw new OperationCancelledException` wiersza, aby zademonstrować, co się stanie w przypadku anulowania proces asynchroniczny. Zadania `IsCanceled` właściwość jest ustawiona na `true`, i wyjątek w `catch` bloku. W niektórych warunkach, które nie dotyczą w tym przykładzie zadanie w `IsFaulted` właściwość jest ustawiona na `true` i `IsCanceled` ma ustawioną wartość `false`.  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia obsługi wyjątków, gdzie wiele zadań może spowodować wiele wyjątków. `try` Bloku oczekujące na zadanie, które jest zwracany przez wywołanie do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Zadanie zostało ukończone, po zakończeniu trzech zadań, do których zastosowano WhenAll.  
  
 Wszystkie trzy zadania powoduje zgłoszenie wyjątku. `catch` Bloku iteruje wyjątki, które znajdują się w `Exception.InnerExceptions` właściwość zadania, który został zwrócony przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Spróbuj, throw i catch instrukcji (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [Porady: jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
