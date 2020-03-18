---
title: await operator - odwołanie C#
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 9f541ae9c26eb12acdcf9a8c59bab98c4772c3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173448"
---
# <a name="await-operator-c-reference"></a>await operator (odwołanie C#)

Operator `await` zawiesza ocenę otaczającej metody [asynchronicznej](../keywords/async.md) do czasu zakończenia operacji asynchronicznej reprezentowanej przez jej operand. Po zakończeniu operacji asynchronicznej `await` operator zwraca wynik operacji, jeśli istnieje. Gdy `await` operator jest stosowany do operandu, który reprezentuje już ukończoną operację, zwraca wynik operacji natychmiast bez zawieszenia otaczającej metody. Operator `await` nie blokuje wątku, który ocenia metodę asynchronia. Gdy `await` operator zawiesza otaczającej metody asynchronicznej, formant zwraca do obiektu wywołującego metody.

W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda `Task<byte[]>` zwraca wystąpienie, które reprezentuje operację asynchroniczną, która tworzy tablicę bajtów po jej zakończeniu. Do czasu zakończenia operacji `await` operator zawiesza `DownloadDocsMainPageAsync` metodę. Gdy `DownloadDocsMainPageAsync` zostanie zawieszony, kontrola jest `Main` zwracana do metody, która jest obiektem wywołującym . `DownloadDocsMainPageAsync` Metoda `Main` jest wykonywana, dopóki nie potrzebuje wyniku operacji asynchronicznej wykonywanej `DownloadDocsMainPageAsync` przez metodę. Gdy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> pobiera wszystkie bajty, reszta `DownloadDocsMainPageAsync` metody jest oceniana. Następnie oceniana jest `Main` reszta metody.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

W poprzednim przykładzie użyto [metody asynchronicznej `Main` ](../../programming-guide/main-and-command-args/index.md), która jest możliwa począwszy od Języka C# 7.1. Aby uzyskać więcej informacji, zobacz [await operatora w Main metody](#await-operator-in-the-main-method) sekcji.

> [!NOTE]
> Aby zapoznać się z wprowadzeniem do programowania asynchronicznego, zobacz [Programowanie asynchroniczne z async i czekam .](../../programming-guide/concepts/async/index.md) Programowanie asynchroniczne `async` `await` z [wzorcem asynchronicznym opartym na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)i zgodne z nimi .

Operatora można `await` używać tylko w metodzie, [wyrażeniu lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metodzie anonimowej](delegate-operator.md) zmodyfikowanej przez słowo kluczowe [asynchroniczne.](../keywords/async.md) W ramach metody asynchronicznej nie `await` można użyć operatora w treści funkcji synchronicznej, wewnątrz bloku [instrukcji lock](../keywords/lock-statement.md)i w [niebezpiecznym](../keywords/unsafe.md) kontekście.

Operand `await` operatora jest zwykle jednym z następujących typów <xref:System.Threading.Tasks.Task>.NET: , <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, lub <xref:System.Threading.Tasks.ValueTask%601>. Jednak każde oczekiwane wyrażenie może być operand `await` operatora. Aby uzyskać więcej informacji, zobacz [awaitable expressions](~/_csharplang/spec/expressions.md#awaitable-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

Począwszy od języka C# 8.0, można użyć `await foreach` instrukcji do korzystania z asynchronicznego strumienia danych. Aby uzyskać więcej informacji, zobacz artykuł [ `foreach` instrukcji](../keywords/foreach-in.md) i [asynchroniczne strumienisekcji](../../whats-new/csharp-8.md#asynchronous-streams) [Co nowego w języku C# 8.0](../../whats-new/csharp-8.md) artykułu.

Typ `await t` wyrażenia jest, `TResult` jeśli typ `t` <xref:System.Threading.Tasks.Task%601> wyrażenia <xref:System.Threading.Tasks.ValueTask%601>jest lub . Jeśli typ `t` jest <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.ValueTask>lub , `await t` typ `void`jest . W obu przypadkach `t` jeśli zgłasza `await t` wyjątek, ponownie zgłasza wyjątek. Aby uzyskać więcej informacji na temat obsługi [wyjątków, zobacz wyjątki w metodach asynchronicznej](../keywords/try-catch.md#exceptions-in-async-methods) sekcji [instrukcji try-catch.](../keywords/try-catch.md)

Słowa `async` `await` kluczowe i są dostępne w języku C# 5 i nowszych.

## <a name="await-operator-in-the-main-method"></a>czekają na operatora w metodzie głównej

Począwszy od Języka C# 7.1, [ `Main` metoda](../../programming-guide/main-and-command-args/index.md), która `Task` `Task<int>`jest punktem wejścia aplikacji, może zwrócić `await` lub , włączając go do async, dzięki czemu można użyć operatora w jego treści. We wcześniejszych wersjach języka C#, aby upewnić się, że `Main` metoda czeka na zakończenie operacji <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> asynchronicznej, można pobrać wartość właściwości <xref:System.Threading.Tasks.Task%601> wystąpienia, który jest zwracany przez odpowiednią metodę asynchroniczną. W przypadku operacji asynchronicznych, które nie generują <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> wartości, można wywołać metodę. Aby uzyskać informacje dotyczące wybierania wersji językowej, zobacz [Przechowywanie wersji językowej języka Języka C#](../configure-language-version.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Await expressions](~/_csharplang/spec/expressions.md#await-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [async](../keywords/async.md)
- [Model programowania asynchronicznego zadań (APM)](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programowanie asynchroniczne](../../async.md)
- [Async w głębi](../../../standard/async-in-depth.md)
- [Instruktaż: uzyskiwanie dostępu do sieci Web za pomocą asynchronii i oczekiwanie](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Samouczek: Generowanie i używanie strumieni asynchronicznyprzy użyciu plików C# 8.0 i .NET Core 3.0](../../tutorials/generate-consume-asynchronous-stream.md)
