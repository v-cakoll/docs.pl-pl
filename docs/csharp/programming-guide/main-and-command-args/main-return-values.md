---
title: Zwracane wartości Main() (Przewodnik programowania w języku C#)
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 8ac0d70458d7c3762ae9dc5fc90058f0caafc4ab
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071365"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="0bd0a-102">Main() — zwracane wartości (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0bd0a-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="0bd0a-103">`Main` Metoda może zwracać `void`:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="0bd0a-104">Może również zwracać `int`:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="0bd0a-105">Jeśli wartość zwracana z `Main` nie jest używany, zwracając `void` umożliwia nieco prostsze kodu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="0bd0a-106">Jednak zwracanie całkowitą Włącza program do komunikowania się informacje o stanie do innych programów lub skryptów, które wywołują pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="0bd0a-107">Wartość zwrotną z elementu `Main` jest traktowany jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="0bd0a-108">W poniższym przykładzie pokazano, jak wartość zwracana z `Main` można uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="0bd0a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bd0a-109">Example</span></span>

<span data-ttu-id="0bd0a-110">W tym przykładzie użyto [platformy .NET Core](../../../core/index.md) narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="0bd0a-111">Jeśli jesteś unfamilar za pomocą narzędzia wiersza polecenia platformy .NET Core, informacje na temat ich w tym [temacie wprowadzenie Get](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="0bd0a-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="0bd0a-112">Modyfikowanie `Main` method in Class metoda *program.cs* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="0bd0a-113">Gdy program jest wykonywana w Windows, wszelkie wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="0bd0a-114">Ta zmienna środowiskowa można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` za pomocą programu powershell.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="0bd0a-115">Możesz tworzyć aplikacji przy użyciu [wiersz polecenia dotnet](../../../core/tools/dotnet.md) `dotnet build` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="0bd0a-116">Następnie należy utworzyć skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="0bd0a-117">Wklej następujący kod do pliku tekstowego i zapisz go jako `test.ps1` w folderze, który zawiera projekt.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="0bd0a-118">Uruchom skrypt programu powershell, wpisując `test.ps1` w wierszu polecenia programu powershell.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="0bd0a-119">Ponieważ kod zwraca zero, plik wsadowy zakomunikuje sukces.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="0bd0a-120">Jednak w przypadku zmiany MainReturnValTest.cs zwracają wartość różna od zera i ponownie skompilować program późniejszego wykonania skryptu programu powershell zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="0bd0a-121">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="0bd0a-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="0bd0a-122">Wartości zwracane Async Main</span><span class="sxs-lookup"><span data-stu-id="0bd0a-122">Async Main return values</span></span>

<span data-ttu-id="0bd0a-123">Async Main zwraca wartości powodują standardowy kod niezbędne w przypadku wywoływania metod asynchronicznych `Main` kod wygenerowany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="0bd0a-124">Wcześniej należy zapisać tej konstrukcji, aby wywołać kodu asynchronicznego i upewnij się, że program został uruchomiony, aż do zakończenia operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="0bd0a-125">Teraz to może być zastąpiony:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="0bd0a-126">Korzystać z nowej składni jest, czy kompilator generuje zawsze prawidłowego kodu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="0bd0a-127">Kodu wygenerowanego przez kompilator</span><span class="sxs-lookup"><span data-stu-id="0bd0a-127">Compiler generated code</span></span>

<span data-ttu-id="0bd0a-128">Gdy zwraca punkt wejścia aplikacji `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metody punktu wejścia, które są zadeklarowane w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="0bd0a-129">Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod dla tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="0bd0a-130">`static Task Main()` wyniki w kompilatorze emitowania odpowiednik `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0bd0a-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0bd0a-131">`static Task Main(string[])` wyniki w kompilatorze emitowania odpowiednik `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0bd0a-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0bd0a-132">`static Task<int> Main()` wyniki w kompilatorze emitowania odpowiednik `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0bd0a-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="0bd0a-133">`static Task<int> Main(string[])` wyniki w kompilatorze emitowania odpowiednik `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="0bd0a-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="0bd0a-134">Jeśli używane przykłady `async` modyfikator na `Main` metody, kompilator może wygenerować tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bd0a-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bd0a-135">See Also</span></span>
- [<span data-ttu-id="0bd0a-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0bd0a-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0bd0a-137">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0bd0a-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0bd0a-138">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0bd0a-138">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="0bd0a-139">Instrukcje: wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0bd0a-139">How to: Display Command Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="0bd0a-140">Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="0bd0a-140">How to: Access Command-Line Arguments Using foreach</span></span>](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
