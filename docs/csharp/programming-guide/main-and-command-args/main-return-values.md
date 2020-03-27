---
title: Main() Return Values - Przewodnik programowania języka C#
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 3d97ab2b3f53179cb184f2ad3944ea29ff5566a2
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345126"
---
# <a name="main-return-values-c-programming-guide"></a>Main() wartości zwracane (Przewodnik programowania języka C#)

Metoda `Main` może `void`zwrócić:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Może również `int`zwrócić:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Jeśli zwracana `Main` wartość z nie `void` jest używana, zwracanie umożliwia nieco prostszy kod. Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny. Zwracana wartość `Main` z jest traktowana jako kod zakończenia procesu. Jeśli `void` jest `Main` zwracany z kodu `0`zakończenia będzie niejawnie . Poniższy przykład pokazuje, jak `Main` można uzyskać dostęp do zwracanej wartości z.

## <a name="example"></a>Przykład

W tym przykładzie użyto narzędzi wiersza polecenia [.NET Core.](../../../core/index.yml) Jeśli nie znasz narzędzi wiersza polecenia .NET Core, możesz dowiedzieć się o nich w tym [temacie Wprowadzenie](../../../core/tutorials/cli-create-console-app.md).

Zmodyfikuj `Main` metodę w *program.cs* w następujący sposób:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Gdy program jest wykonywany w systemie Windows, każda wartość zwrócona `Main` z funkcji jest przechowywana w zmiennej środowiskowej. Tę zmienną środowiskową `ERRORLEVEL` można pobrać z `$LastExitCode` pliku wsadowego lub z programu PowerShell.

Aplikację można utworzyć za pomocą polecenia [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`

Następnie utwórz skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wynik. Wklej następujący kod do pliku tekstowego `test.ps1` i zapisz go tak jak w folderze zawierającym projekt. Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu programu powershell.

Ponieważ kod zwraca zero, plik wsadowy zgłosi sukces. Jeśli jednak zmienisz MainReturnValTest.cs, aby zwrócić wartość niezerową, a następnie ponownie skompilować program, późniejsze wykonanie skryptu programu powershell spowoduje zgłoszenie awarii.

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

## <a name="async-main-return-values"></a>Główne wartości zwracane Asynchronii

Wartości zwracane asynchroniczne główne przenoszą kod standardowy niezbędny `Main` do wywoływania metod asynchronicznych do kodu wygenerowanego przez kompilator. Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczne i upewnić się, że program działał do czasu zakończenia operacji asynchronicznie:

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

## <a name="compiler-generated-code"></a>Wygenerowany kod kompilatora

Gdy punkt wejścia aplikacji `Task` `Task<int>`zwraca lub , kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji. Zakładając, że ten `$GeneratedMain`punkt wejścia jest wywoływany, kompilator generuje następujący kod dla tych punktów wejścia:

- `static Task Main()`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Jeśli przykłady `async` używane modyfikator na `Main` metodę, kompilator wygeneruje ten sam kod.

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Odwołanie do języka C#](../index.md)
- [Main() i Argumenty wiersza polecenia](index.md)
- [Jak wyświetlić argumenty wiersza polecenia](./how-to-display-command-line-arguments.md)
