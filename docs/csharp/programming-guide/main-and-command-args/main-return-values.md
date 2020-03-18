---
title: Main() Return Values - Przewodnik programowania C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: eaa78c33613093bb0e108870669392d07d346a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503999"
---
# <a name="main-return-values-c-programming-guide"></a>Wartości zwracane main() (Przewodnik programowania C#)

Metoda `Main` może `void`zwrócić:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Może również zwrócić `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Jeśli wartość zwracana z `Main` nie `void` jest używany, zwracanie pozwala na nieco prostszy kod. Jednak zwracanie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie innym programom lub skryptom wywołującym plik wykonywalny. Wartość zwracana `Main` z jest traktowana jako kod zakończenia procesu. Jeśli `void` zostanie zwrócony z `Main` kodu zakończenia `0`będzie niejawnie . W poniższym przykładzie pokazano, jak można uzyskać dostęp do wartości zwracanej. `Main`

## <a name="example"></a>Przykład

W tym przykładzie użyto narzędzi wiersza polecenia [.NET Core.](../../../core/index.md) Jeśli nie znasz narzędzi wiersza polecenia .NET Core, możesz dowiedzieć się o nich w tym [temacie Wprowadzenie](../../../core/tutorials/cli-create-console-app.md).

Zmodyfikuj `Main` metodę w *program.cs* w następujący sposób:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Gdy program jest wykonywany w systemie Windows, każda wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej. Tę zmienną środowiskową `ERRORLEVEL` można pobrać przy `$LastExitCode` użyciu pliku wsadowego lub z programu PowerShell.

Aplikację można utworzyć przy użyciu polecenia [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`

Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik. Wklej poniższy kod do pliku tekstowego `test.ps1` i zapisz go tak, jak w folderze zawierającym projekt. Uruchom skrypt programu PowerShell, wpisując `test.ps1` monit programu PowerShell.

Ponieważ kod zwraca zero, plik wsadowy zgłosi powodzenie. Jeśli jednak zmienisz MainReturnValTest.cs, aby zwrócić wartość różną od zera, a następnie ponownie skompilować program, późniejsze wykonanie skryptu programu PowerShell spowoduje niepowodzenie.

```dotnetcli
dotnet run
```

```powershell
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

## <a name="async-main-return-values"></a>Główne wartości zwracane asynchronii

Async Główne wartości zwracane przenieść standardowy kod niezbędny do `Main` wywoływania metod asynchronicznych w do kodu generowanego przez kompilator. Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do czasu zakończenia operacji asynchronicznej:

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

Teraz można to zastąpić:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.

## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator

Gdy punkt wejścia aplikacji `Task` `Task<int>`zwraca a lub , kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji. Zakładając, że ten `$GeneratedMain`punkt wejścia jest wywoływana, kompilator generuje następujący kod dla tych punktów wejścia:

- `static Task Main()`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli przykłady używane `async` modyfikator na `Main` metodę, kompilator będzie generować ten sam kod.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Odwołanie do języka C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Jak wyświetlić argumenty wiersza polecenia](./how-to-display-command-line-arguments.md)
