---
title: operator await — C# odwołanie
ms.custom: seodec18
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 36cb4a5def6b75281edbe878d89af0c18ab226ec
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140658"
---
# <a name="await-operator-c-reference"></a>await — operatorC# (odwołanie)

Operator `await` wstrzymuje Obliczanie otaczającej metody [asynchronicznej](../keywords/async.md) do momentu zakończenia operacji asynchronicznej reprezentowanej przez operand. Po zakończeniu operacji asynchronicznej operator `await` zwraca wynik operacji (jeśli istnieje). Gdy operator `await` jest stosowany do operandu, który reprezentuje już wykonaną operację, zwraca wynik operacji natychmiast bez zawieszania otaczającej metody. Operator `await` nie blokuje wątku, który szacuje metodę asynchroniczną. Gdy operator `await` zawiesza otaczającą metodę asynchroniczną, formant powraca do obiektu wywołującego metody.

W poniższym przykładzie metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> zwraca wystąpienie `Task<byte[]>`, które reprezentuje operację asynchroniczną, która generuje tablicę bajtową po jej zakończeniu. Do momentu ukończenia operacji, operator `await` zawiesza metodę `DownloadDocsMainPageAsync`. Gdy `DownloadDocsMainPageAsync` jest wstrzymana, formant jest zwracany do metody `Main`, która jest obiektem wywołującym `DownloadDocsMainPageAsync`. Metoda `Main` jest wykonywana do momentu, gdy nie będzie potrzebowała wyniku operacji asynchronicznej wykonywanej przez metodę `DownloadDocsMainPageAsync`. Gdy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> pobiera wszystkie bajty, zostanie oceniona pozostała część metody `DownloadDocsMainPageAsync`. Następnie zostanie oceniona pozostała część metody `Main`.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Poprzedni przykład używa [metody `Main` asynchronicznej](../../programming-guide/main-and-command-args/index.md), która jest możliwa od C# 7,1. Aby uzyskać więcej informacji, zobacz [operator await w sekcji metody Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md). Programowanie asynchroniczne przy użyciu `async` i `await` następuje po [wzorcu asynchronicznym opartym na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Operatora `await` można używać tylko w metodzie, [wyrażeniu lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metodzie anonimowej](delegate-operator.md) , która jest modyfikowana przez słowo kluczowe [Async](../keywords/async.md) . W metodzie asynchronicznej nie można użyć operatora `await` w treści funkcji synchronicznej, wewnątrz bloku [instrukcji lock](../keywords/lock-statement.md)i w [niebezpiecznym](../keywords/unsafe.md) kontekście.

Operand operatora `await` ma zazwyczaj jeden z następujących typów .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>lub <xref:System.Threading.Tasks.ValueTask%601>. Jednak każde oczekiwane wyrażenie może być argumentem operacji operatora `await`. Aby uzyskać więcej informacji, zobacz sekcję [oczekiwane wyrażenia](~/_csharplang/spec/expressions.md#awaitable-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Począwszy od C# 8,0, można użyć instrukcji `await foreach`, aby wykorzystać asynchroniczny strumień danych. Aby uzyskać więcej informacji, zobacz sekcję " [strumienie asynchroniczne](../../whats-new/csharp-8.md#asynchronous-streams) " [w artykule co C# nowego w 8,0](../../whats-new/csharp-8.md) .

Typ wyrażenia `await t` jest `TResult`, jeśli typem wyrażenia `t` jest <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.ValueTask%601>. Jeśli typ `t` jest <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.ValueTask>, typ `await t` jest `void`. W obu przypadkach, jeśli `t` zgłasza wyjątek, `await t` ponownie generuje wyjątek. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz sekcję [wyjątki w metodach asynchronicznych](../keywords/try-catch.md#exceptions-in-async-methods) artykułu [instrukcji try-catch](../keywords/try-catch.md) .

Słowa kluczowe `async` i `await` są dostępne w C# 5 i nowszych wersjach.

## <a name="await-operator-in-the-main-method"></a>operator await w metodzie Main

Począwszy od C# 7,1, [Metoda`Main`](../../programming-guide/main-and-command-args/index.md), która jest punktem wejścia aplikacji, może zwracać`Task`lub`Task<int>`, umożliwiając jej asynchroniczne, aby można było użyć operatora`await`w swojej treści. W starszych C# wersjach, aby upewnić się, że metoda `Main` czeka na ukończenie operacji asynchronicznej, możesz pobrać wartość właściwości <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> wystąpienia <xref:System.Threading.Tasks.Task%601>, która jest zwracana przez odpowiadającą metodę asynchroniczną. W przypadku operacji asynchronicznych, które nie generują wartości, można wywołać metodę <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Aby uzyskać informacje o sposobach wybierania wersji językowej, zobacz [ C# przechowywanie wersji języka](../configure-language-version.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [async](../keywords/async.md)
- [Asynchroniczny model programowania zadań](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programowanie asynchroniczne](../../async.md)
- [Na poziomie Async](../../../standard/async-in-depth.md)
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Samouczek: generowanie i używanie strumieni asynchronicznych C# przy użyciu 8,0 i .net Core 3,0](../../tutorials/generate-consume-asynchronous-stream.md)
