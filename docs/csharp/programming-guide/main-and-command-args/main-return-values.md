---
title: Main () zwracane wartości — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 13d1eda178a4c2580af67ef5a7198e7f0884a7d6
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884400"
---
# <a name="main-return-values-c-programming-guide"></a>Main () — zwracane wartościC# (Przewodnik programowania)

Metoda `Main` może zwracać `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Może również zwracać `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Jeśli wartość zwracana z `Main` nie jest używana, zwracanie `void` umożliwia nieznacznie łatwiejszy kod. Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny. Wartość zwracana z `Main` jest traktowana jako kod zakończenia procesu. Jeśli `void` jest zwracana z `Main` kod zakończenia będzie niejawnie `0`. Poniższy przykład pokazuje, jak można uzyskać dostęp do wartości zwracanej z `Main`.

## <a name="example"></a>Przykład

Ten przykład używa narzędzi wiersza polecenia [platformy .NET Core](../../../core/index.md) . Jeśli nie znasz narzędzi wiersza polecenia platformy .NET Core, możesz zapoznać się z nimi w [temacie](../../../core/tutorials/cli-create-console-app.md)wprowadzenie.

Zmodyfikuj metodę `Main` w *program.cs* w następujący sposób:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Gdy program jest wykonywany w systemie Windows, wszelkie wartości zwrócone przez funkcję `Main` są przechowywane w zmiennej środowiskowej. Tę zmienną środowiskową można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` z programu PowerShell.

Aplikację można skompilować za pomocą polecenia `dotnet build` [interfejsu wiersza poleceń dotnet](../../../core/tools/dotnet.md) .

Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik. Wklej następujący kod do pliku tekstowego i Zapisz go jako `test.ps1` w folderze zawierającym projekt. Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu polecenia programu PowerShell.

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

Asynchroniczne główne wartości zwracane umożliwiają przenoszenie kodu standardowego niezbędnego do wywoływania metod asynchronicznych w `Main` do kodu wygenerowanego przez kompilator. Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do momentu ukończenia operacji asynchronicznej:

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

Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji. Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod dla tych punktów wejścia:

- `static Task Main()` powoduje, że kompilator emituje odpowiednik `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` powoduje, że kompilator emituje odpowiednik `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` powoduje, że kompilator emituje odpowiednik `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` powoduje, że kompilator emituje odpowiednik `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli przykłady użyto `async` modyfikatora metody `Main`, kompilator wygeneruje ten sam kod.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Dokumentacja języka C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Instrukcje: wyświetlanie argumentów wiersza polecenia](./how-to-display-command-line-arguments.md)
