---
title: Zwracane wartości Main() (Przewodnik programowania w języku C#)
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 51a7d821b5705c0ddda96a34663ba0288e0f1da9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339959"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="daf80-102">Main() — zwracane wartości (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="daf80-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="daf80-103">`Main` Może być zwracany przez metodę `void`:</span><span class="sxs-lookup"><span data-stu-id="daf80-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="daf80-104">Można także wrócić `int`:</span><span class="sxs-lookup"><span data-stu-id="daf80-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="daf80-105">Jeśli wartość zwrotu z `Main` nie jest używany, zwracając `void` umożliwia prostsze nieco kodu.</span><span class="sxs-lookup"><span data-stu-id="daf80-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="daf80-106">Jednak zwracanie całkowitą umożliwia programowi komunikacji informacji o stanie do innych programów lub skryptów, które wywołują pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="daf80-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="daf80-107">Wartość zwrócona przez `Main` jest traktowany jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="daf80-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="daf80-108">W poniższym przykładzie pokazano, jak wartość zwrotu z `Main` są dostępne.</span><span class="sxs-lookup"><span data-stu-id="daf80-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="daf80-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="daf80-109">Example</span></span>

<span data-ttu-id="daf80-110">W tym przykładzie użyto [.NET Core](../../../core/index.md) narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="daf80-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="daf80-111">Jeśli unfamilar z narzędzi wiersza polecenia platformy .NET Core, możesz dowiedzieć się o nich w tym [tematu Uruchomiono Get](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="daf80-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="daf80-112">Modyfikowanie `Main` metody w *program.cs* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="daf80-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="daf80-113">Gdy program jest wykonywana w systemie Windows, wszystkie wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="daf80-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="daf80-114">Tej zmiennej środowiskowej można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` z programu powershell.</span><span class="sxs-lookup"><span data-stu-id="daf80-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="daf80-115">Można utworzyć aplikacji przy użyciu [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="daf80-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="daf80-116">Następnie należy utworzyć skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="daf80-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="daf80-117">Wklej następujący kod do pliku tekstowego i zapisz go jako `test.ps1` w folderze, który zawiera projekt.</span><span class="sxs-lookup"><span data-stu-id="daf80-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="daf80-118">Uruchom skrypt programu powershell, wpisując `test.ps1` w wierszu polecenia programu powershell.</span><span class="sxs-lookup"><span data-stu-id="daf80-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="daf80-119">Ponieważ kod zwraca zero, pliku wsadowego zgłosi Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="daf80-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="daf80-120">Jednak jeśli zmienisz MainReturnValTest.cs zwracać wartość inną niż zero i ponownie skompiluj program kolejnych wykonywania skryptu środowiska powershell zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="daf80-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="daf80-121">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="daf80-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="daf80-122">Wartości zwracane Async Main</span><span class="sxs-lookup"><span data-stu-id="daf80-122">Async Main return values</span></span>

<span data-ttu-id="daf80-123">Async Main zwracać wartości Przenieś schematyczny kod wymaganych przez wywołanie metod asynchronicznych `Main` do kod wygenerowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="daf80-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="daf80-124">Wcześniej musisz zapisać tej konstrukcji, aby wywoływać kod asynchroniczne i upewnij się, że program został uruchomiony, aż do zakończenia operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="daf80-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="daf80-125">Teraz to może być zastąpiony:</span><span class="sxs-lookup"><span data-stu-id="daf80-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="daf80-126">Zaletą nowej składni jest, że kompilator generuje zawsze prawidłowego kodu.</span><span class="sxs-lookup"><span data-stu-id="daf80-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="daf80-127">Kod wygenerowanego przez kompilator</span><span class="sxs-lookup"><span data-stu-id="daf80-127">Compiler generated code</span></span>

<span data-ttu-id="daf80-128">Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowany w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="daf80-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="daf80-129">Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod do tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="daf80-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="daf80-130">`static Task Main()` wyniki w kompilatorze emitowanie odpowiednikiem `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="daf80-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="daf80-131">`static Task Main(string[])` wyniki w kompilatorze emitowanie odpowiednikiem `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="daf80-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="daf80-132">`static Task<int> Main()` wyniki w kompilatorze emitowanie odpowiednikiem `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="daf80-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="daf80-133">`static Task<int> Main(string[])` wyniki w kompilatorze emitowanie odpowiednikiem `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="daf80-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="daf80-134">Jeśli używane przykłady `async` modyfikator na `Main` metody, kompilator może wygenerować tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="daf80-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="daf80-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daf80-135">See also</span></span>
<span data-ttu-id="daf80-136">[Przewodnik programowania w języku C#](../../programming-guide/index.md)
[odwołanie w C#](../index.md)
[Main() i argumenty wiersza polecenia](index.md)
[porady: wyświetlanie wiersza polecenia Argumenty](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span><span class="sxs-lookup"><span data-stu-id="daf80-136">[C# Programming Guide](../../programming-guide/index.md)
[C# Reference](../index.md)
[Main() and Command-Line Arguments](index.md)
[How to: Display Command Line Arguments](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[How to: Access Command-Line Arguments Using foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span></span>
