---
title: operator await — odwołanie w C#
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 83ee51fcbcc5911c688e30542cefb1c56578a578
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141026"
---
# <a name="await-operator-c-reference"></a>await — operator (odwołanie w C#)

`await` Operator wstrzymuje Obliczanie otaczającej metody [asynchronicznej](../keywords/async.md) do momentu zakończenia operacji asynchronicznej reprezentowanej przez operand. Po zakończeniu operacji asynchronicznej `await` operator zwraca wynik operacji (jeśli istnieje). Gdy `await` operator jest stosowany do operandu, który reprezentuje już ukończoną operację, zwraca wynik operacji natychmiast bez zawieszania otaczającej metody. `await` Operator nie blokuje wątku, który szacuje metodę asynchroniczną. Gdy `await` operator zawiesza otaczającą metodę Async, formant wraca do obiektu wywołującego metody.

W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> Metoda zwraca `Task<byte[]>` wystąpienie, które reprezentuje operację asynchroniczną, która generuje tablicę bajtową po jej zakończeniu. Do momentu ukończenia operacji, `await` operator zawiesza `DownloadDocsMainPageAsync` metodę. Gdy `DownloadDocsMainPageAsync` jest wstrzymana, formant jest zwracany do `Main` metody, która jest obiektem wywołującym `DownloadDocsMainPageAsync`. Metoda `Main` jest wykonywana do momentu, gdy nie będzie potrzebowała wyniku operacji asynchronicznej wykonywanej przez `DownloadDocsMainPageAsync` metodę. Gdy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> pobiera wszystkie bajty, pozostała część `DownloadDocsMainPageAsync` metody jest szacowana. Następnie zostanie oceniona pozostała `Main` część metody.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

Poprzedni przykład używa [metody asynchronicznej `Main` ](../../programming-guide/main-and-command-args/index.md), która jest możliwa od języka C# 7,1. Aby uzyskać więcej informacji, zobacz [operator await w sekcji metody Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md). Programowanie asynchroniczne przy `async` użyciu `await` i następuje po [wzorcu asynchronicznym opartym na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

`await` Operatora można używać tylko w metodzie, [wyrażeniu lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metodzie anonimowej](delegate-operator.md) , która jest modyfikowana przez słowo kluczowe [Async](../keywords/async.md) . W metodzie asynchronicznej nie można użyć `await` operatora w treści funkcji synchronicznej, wewnątrz bloku [instrukcji lock](../keywords/lock-statement.md)i w [niebezpiecznym](../keywords/unsafe.md) kontekście.

`await` Operand operatora ma zwykle jeden z następujących typów .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, lub. <xref:System.Threading.Tasks.ValueTask%601> Jednak każde oczekiwane wyrażenie może być argumentem operacji `await` operatora. Aby uzyskać więcej informacji, zobacz sekcję [oczekiwane wyrażenia](~/_csharplang/spec/expressions.md#awaitable-expressions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

Począwszy od języka C# 8,0, można użyć `await foreach` instrukcji, aby wykorzystać asynchroniczny strumień danych. Aby uzyskać więcej informacji, zobacz artykuł [ `foreach` instrukcja](../keywords/foreach-in.md) i [strumienie asynchroniczne](../../whats-new/csharp-8.md#asynchronous-streams) [w artykule Co nowego w języku C# 8,0](../../whats-new/csharp-8.md) .

`await t` Typ wyrażenia jest `TResult` , jeśli typem wyrażenia `t` jest <xref:System.Threading.Tasks.Task%601> lub. <xref:System.Threading.Tasks.ValueTask%601> `t` Jeśli typ jest <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.ValueTask>, typem `await t` jest. `void` W obu przypadkach, jeśli `t` zgłasza wyjątek, `await t` ponownie generuje wyjątek. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz sekcję [wyjątki w metodach asynchronicznych](../keywords/try-catch.md#exceptions-in-async-methods) artykułu [instrukcji try-catch](../keywords/try-catch.md) .

Słowa `async` kluczowe `await` i są dostępne w języku C# 5 i nowszych.

## <a name="await-operator-in-the-main-method"></a>operator await w metodzie Main

Począwszy od języka C# 7,1, [ `Main` Metoda](../../programming-guide/main-and-command-args/index.md), która jest punktem wejścia aplikacji, może zwracać `Task` lub `Task<int>`, aby umożliwić jej asynchroniczne, aby można było użyć `await` operatora w jego treści. W starszych wersjach języka C#, aby upewnić `Main` się, że metoda czeka na zakończenie operacji asynchronicznej, możesz pobrać wartość <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości <xref:System.Threading.Tasks.Task%601> wystąpienia zwracanego przez odpowiadającą metodę asynchroniczną. W przypadku operacji asynchronicznych, które nie generują wartości, można <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> wywołać metodę. Aby uzyskać informacje o sposobach wybierania wersji językowej, zobacz [wersja języka C#](../configure-language-version.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [asynchroniczne](../keywords/async.md)
- [Model programowania asynchronicznego zadań (APM)](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programowanie asynchroniczne](../../async.md)
- [Na poziomie Async](../../../standard/async-in-depth.md)
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Samouczek: generowanie strumieni asynchronicznych i korzystanie z nich przy użyciu języków C# 8,0 i .NET Core 3,0](../../tutorials/generate-consume-asynchronous-stream.md)
