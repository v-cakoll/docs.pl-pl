---
title: Main () zwracane wartości — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1be04f98a4dec1317c485c7e482568cfe48ea9bf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588879"
---
# <a name="main-return-values-c-programming-guide"></a>Main () — zwracane wartościC# (Przewodnik programowania)

Metoda może zwracać `void`: `Main`

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Może również zwrócić `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Jeśli wartość zwracana z `Main` nie jest używana, zwracający `void` umożliwia nieznacznie łatwiejszy kod. Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny. Wartość zwracana z `Main` jest traktowana jako kod zakończenia procesu. Jeśli `void` jest zwracana z `Main` kodu zakończenia, będzie niejawnie `0`. Poniższy przykład pokazuje, w jaki sposób `Main` można uzyskać dostęp do zwracanej wartości.

## <a name="example"></a>Przykład

Ten przykład używa narzędzi wiersza polecenia [platformy .NET Core](../../../core/index.md) . Jeśli nie znasz narzędzi wiersza polecenia platformy .NET Core, możesz zapoznać się z nimi w [temacie](../../../core/tutorials/using-with-xplat-cli.md)wprowadzenie.

Zmodyfikuj metodę w program.cs w następujący sposób: `Main`

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Gdy program jest wykonywany w systemie Windows, wszelkie wartości zwrócone przez `Main` funkcję są przechowywane w zmiennej środowiskowej. Tę zmienną środowiskową można pobrać przy `ERRORLEVEL` użyciu pliku wsadowego lub `$LastExitCode` z programu PowerShell.

Aplikację można skompilować przy użyciu polecenia [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` .

Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik. Wklej następujący kod do pliku tekstowego i Zapisz go jako `test.ps1` folder zawierający projekt. Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu polecenia programu PowerShell.

Ponieważ kod zwraca zero, plik wsadowy będzie zgłaszał powodzenie. Jeśli jednak zmienisz MainReturnValTest.cs w taki sposób, aby zwracał wartość różną od zera, a następnie ponownie skompilujesz program, kolejne wykonanie skryptu programu PowerShell zgłosi błąd.

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

## <a name="async-main-return-values"></a>Asynchroniczne główne wartości zwracane

Asynchroniczne główne wartości zwracane umożliwiają przenoszenie kodu standardowego niezbędnego do wywołania metod asynchronicznych w programie `Main` do kodu wygenerowanego przez kompilator. Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do momentu ukończenia operacji asynchronicznej:

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

Teraz można je zastąpić:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.

## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator

Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji. Przy założeniu, że ten punkt `$GeneratedMain`wejścia jest wywoływany, kompilator generuje następujący kod dla tych punktów wejścia:

- `static Task Main()`powoduje, że kompilator emituje odpowiednik`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`powoduje, że kompilator emituje odpowiednik`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`powoduje, że kompilator emituje odpowiednik`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`powoduje, że kompilator emituje odpowiednik`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli przykłady użyto `async` modyfikatora `Main` metody, kompilator wygeneruje ten sam kod.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Dokumentacja języka C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Instrukcje: Wyświetlanie argumentów wiersza polecenia](./how-to-display-command-line-arguments.md)
