---
title: "Zwracane wartości Main() (Przewodnik programowania w języku C#)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a>Main() — zwracane wartości (C# przewodnik programowania w języku)

`Main` Może być zwracany przez metodę `void`:

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

Można także wrócić `int`:

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

Jeśli wartość zwrotu z `Main` nie jest używany, zwracając `void` umożliwia prostsze nieco kodu. Jednak zwracanie całkowitą umożliwia programowi komunikacji informacji o stanie do innych programów lub skryptów, które wywołują pliku wykonywalnego. Wartość zwrócona przez `Main` jest traktowany jako kod zakończenia procesu. W poniższym przykładzie pokazano, jak wartość zwrotu z `Main` są dostępne.

## <a name="example"></a>Przykład

W tym przykładzie użyto [.NET Core](../../../core/index.md) narzędzi wiersza polecenia. Jeśli unfamilar z narzędzi wiersza polecenia platformy .NET Core, możesz dowiedzieć się o nich w tym [tematu Uruchomiono Get](../../../core/tutorials/using-with-xplat-cli.md).

Modyfikowanie `Main` metody w *program.cs* w następujący sposób:

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

Gdy program jest wykonywana w systemie Windows, wszystkie wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej. Tej zmiennej środowiskowej można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` z programu powershell.

Można utworzyć aplikacji przy użyciu [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` polecenia.

Następnie należy utworzyć skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wyniki. Wklej następujący kod do pliku tekstowego i zapisz go jako `test.ps1` w folderze, który zawiera projekt. Uruchom skrypt programu powershell, wpisując `test.ps1` w wierszu polecenia programu powershell.

Ponieważ kod zwraca zero, pliku wsadowego zgłosi Powodzenie. Jednak jeśli zmienisz MainReturnValTest.cs zwracać wartość inną niż zero i ponownie skompiluj program kolejnych wykonywania skryptu środowiska powershell zgłosi błąd.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Wartości zwracane Async Main

Async Main zwracać wartości Przenieś schematyczny kod wymaganych przez wywołanie metod asynchronicznych `Main` do kod wygenerowany przez kompilator. Wcześniej musisz zapisać tej konstrukcji, aby wywoływać kod asynchroniczne i upewnij się, że program został uruchomiony, aż do zakończenia operacji asynchronicznej:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Teraz to może być zastąpiony:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Zaletą nowej składni jest, że kompilator generuje zawsze prawidłowego kodu.

## <a name="compiler-generated-code"></a>Kod wygenerowanego przez kompilator

Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowany w kodzie aplikacji. Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod do tych punktów wejścia:

- `static Task Main()`wyniki w kompilatorze emitowanie odpowiednikiem`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`wyniki w kompilatorze emitowanie odpowiednikiem`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`wyniki w kompilatorze emitowanie odpowiednikiem`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`wyniki w kompilatorze emitowanie odpowiednikiem`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli używane przykłady `async` modyfikator na `Main` metody, kompilator może wygenerować tego samego kodu.

## <a name="see-also"></a>Zobacz także
[Przewodnik programowania w języku C#](../../programming-guide/index.md)
[odwołanie w C#](../index.md)
[Main() i argumenty wiersza polecenia](index.md)
[porady: wyświetlanie wiersza polecenia Argumenty](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
