---
title: Main() — zwracane wartości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: f515268af13ef95b8b6d9a79f71c49d5d4a98d05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710943"
---
# <a name="main-return-values-c-programming-guide"></a>Main() — zwracane wartości (C# Programming Guide)

`Main` Metoda może zwracać `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Może również zwracać `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Jeśli wartość zwracana z `Main` nie jest używany, zwracając `void` umożliwia nieco prostsze kodu. Jednak zwracanie całkowitą Włącza program do komunikowania się informacje o stanie do innych programów lub skryptów, które wywołują pliku wykonywalnego. Wartość zwrotną z elementu `Main` jest traktowany jako kod zakończenia procesu. W poniższym przykładzie pokazano, jak wartość zwracana z `Main` można uzyskać dostęp.

## <a name="example"></a>Przykład

W tym przykładzie użyto [platformy .NET Core](../../../core/index.md) narzędzi wiersza polecenia. Jeśli jesteś zaznajomiony z narzędzi wiersza polecenia platformy .NET Core, informacje na temat ich w tym [temacie wprowadzenie Get](../../../core/tutorials/using-with-xplat-cli.md).

Modyfikowanie `Main` method in Class metoda *program.cs* w następujący sposób:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Gdy program jest wykonywana w Windows, wszelkie wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej. Ta zmienna środowiskowa można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` za pomocą programu powershell.

Możesz tworzyć aplikacji przy użyciu [wiersz polecenia dotnet](../../../core/tools/dotnet.md) `dotnet build` polecenia.

Następnie należy utworzyć skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wyniki. Wklej następujący kod do pliku tekstowego i zapisz go jako `test.ps1` w folderze, który zawiera projekt. Uruchom skrypt programu powershell, wpisując `test.ps1` w wierszu polecenia programu powershell.

Ponieważ kod zwraca zero, plik wsadowy zakomunikuje sukces. Jednak w przypadku zmiany MainReturnValTest.cs zwracają wartość różna od zera i ponownie skompilować program późniejszego wykonania skryptu programu powershell zgłosi błąd.

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

Async Main zwraca wartości powodują standardowy kod niezbędne w przypadku wywoływania metod asynchronicznych `Main` kod wygenerowany przez kompilator. Wcześniej należy zapisać tej konstrukcji, aby wywołać kodu asynchronicznego i upewnij się, że program został uruchomiony, aż do zakończenia operacji asynchronicznej:

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

Korzystać z nowej składni jest, czy kompilator generuje zawsze prawidłowego kodu.

## <a name="compiler-generated-code"></a>Kodu wygenerowanego przez kompilator

Gdy zwraca punkt wejścia aplikacji `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metody punktu wejścia, które są zadeklarowane w kodzie aplikacji. Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod dla tych punktów wejścia:

- `static Task Main()` wyniki w kompilatorze emitowania odpowiednik `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` wyniki w kompilatorze emitowania odpowiednik `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` wyniki w kompilatorze emitowania odpowiednik `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` wyniki w kompilatorze emitowania odpowiednik `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli używane przykłady `async` modyfikator na `Main` metody, kompilator może wygenerować tego samego kodu.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dokumentacja języka C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Instrukcje: Wyświetlanie argumentów wiersza poleceń](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
