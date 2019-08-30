---
title: operator await — C# odwołanie
ms.custom: seodec18
ms.date: 08/30/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c2172f651dd106825680de3195e26f032225a9ab
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169391"
---
# <a name="await-operator-c-reference"></a>await — operatorC# (odwołanie)

Operator wstrzymuje Obliczanie otaczającej metody asynchronicznej do momentu zakończenia operacji asynchronicznej reprezentowanej przez operand. [](../keywords/async.md) `await` Po zakończeniu `await` operacji asynchronicznej operator zwraca wynik operacji (jeśli istnieje). `await` Gdy operator jest stosowany do operandu, który reprezentuje już wykonaną operację, zwraca wynik operacji natychmiast bez zawieszania otaczającej metody. `await` Operator nie blokuje wątku, który szacuje metodę asynchroniczną. `await` Gdy operator wstrzymuje otaczającą metodę, formant wraca do obiektu wywołującego metody.

W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> Metoda `Task<byte[]>` zwraca wystąpienie, które reprezentuje operację asynchroniczną, która generuje tablicę bajtową po jej zakończeniu. Do momentu ukończenia operacji, `await` operator zawiesza `DownloadDocsMainPageAsync` metodę. Gdy `DownloadDocsMainPageAsync` jest wstrzymana, formant jest zwracany `Main` do metody, `DownloadDocsMainPageAsync`która jest obiektem wywołującym. Metoda `Main` jest wykonywana do momentu, gdy nie będzie potrzebowała wyniku operacji asynchronicznej wykonywanej `DownloadDocsMainPageAsync` przez metodę. Gdy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> pobiera wszystkie bajty, pozostała `DownloadDocsMainPageAsync` część metody jest szacowana. Następnie zostanie oceniona pozostała `Main` część metody.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Poprzedni przykład używa [metody asynchronicznej `Main` ](../../programming-guide/main-and-command-args/index.md), która jest możliwa od C# 7,1. Aby uzyskać więcej informacji, zobacz [operator await w sekcji metody Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md). Programowanie asynchroniczne przy `async` użyciu `await` i następuje po [wzorcu asynchronicznym opartym na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

`await` Operatora można używać tylko w metodzie, wyrażeniu [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub metodzie [anonimowej](delegate-operator.md) , która jest modyfikowana przez słowo kluczowe [Async](../keywords/async.md) . W metodzie asynchronicznej nie można użyć `await` operatora w treści funkcji synchronicznej, wewnątrz bloku [instrukcji lock](../keywords/lock-statement.md)i w niebezpiecznym kontekście. [](../keywords/unsafe.md)
  
Operand `await` operatora ma zwykle jeden z następujących typów .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, lub <xref:System.Threading.Tasks.ValueTask%601>. Jednak każde oczekiwane wyrażenie może być argumentem operacji `await` operatora. Aby uzyskać więcej informacji, zobacz sekcję [oczekiwane wyrażenia](~/_csharplang/spec/expressions.md#awaitable-expressions) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

`await t` Typ wyrażenia <xref:System.Threading.Tasks.ValueTask%601>jest `TResult` , jeśli typem wyrażenia `t` jest <xref:System.Threading.Tasks.Task%601> lub. Jeśli typ `t` jest <xref:System.Threading.Tasks.Task> lub<xref:System.Threading.Tasks.ValueTask>,typem jest.`await t` `void` W obu przypadkach, jeśli `t` zgłasza wyjątek, `await t` ponownie generuje wyjątek. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz sekcję [wyjątki w metodach asynchronicznych](../keywords/try-catch.md#exceptions-in-async-methods) artykułu [instrukcji try-catch](../keywords/try-catch.md) .

Słowa kluczowe `await`isą dostępne od C# 5. `async`

## <a name="await-operator-in-the-main-method"></a>operator await w metodzie Main

Począwszy od C# 7,1, [ `Main` Metoda](../../programming-guide/main-and-command-args/index.md), która jest punktem wejścia aplikacji, może zwracać `Task` lub `Task<int>`, aby umożliwić jej asynchroniczne, aby można było użyć `await` operatora w jego treści. W starszych C# wersjach, aby upewnić się `Main` , że metoda czeka na ukończenie operacji asynchronicznej, możesz pobrać wartość <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości <xref:System.Threading.Tasks.Task%601> wystąpienia zwracanego przez odpowiednie asynchroniczne Method. W przypadku operacji asynchronicznych, które nie generują wartości, można <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> wywołać metodę. Aby uzyskać informacje o sposobach wybierania wersji językowej, zobacz [Wybieranie C# wersji językowej](../configure-language-version.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [async](../keywords/async.md)
- [Programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md)
- [Asynchroniczny model programowania zadań](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programowanie asynchroniczne](../../async.md)
- [Wzorzec asynchroniczny oparty na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Na poziomie Async](../../../standard/async-in-depth.md)
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
