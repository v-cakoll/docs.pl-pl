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
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="6fb80-102">Main () — zwracane wartościC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="6fb80-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="6fb80-103">Metoda może zwracać `void`: `Main`</span><span class="sxs-lookup"><span data-stu-id="6fb80-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="6fb80-104">Może również zwrócić `int`:</span><span class="sxs-lookup"><span data-stu-id="6fb80-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="6fb80-105">Jeśli wartość zwracana z `Main` nie jest używana, zwracający `void` umożliwia nieznacznie łatwiejszy kod.</span><span class="sxs-lookup"><span data-stu-id="6fb80-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="6fb80-106">Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="6fb80-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="6fb80-107">Wartość zwracana z `Main` jest traktowana jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="6fb80-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="6fb80-108">Jeśli `void` jest zwracana z `Main` kodu zakończenia, będzie niejawnie `0`.</span><span class="sxs-lookup"><span data-stu-id="6fb80-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="6fb80-109">Poniższy przykład pokazuje, w jaki sposób `Main` można uzyskać dostęp do zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="6fb80-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="6fb80-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fb80-110">Example</span></span>

<span data-ttu-id="6fb80-111">Ten przykład używa narzędzi wiersza polecenia [platformy .NET Core](../../../core/index.md) .</span><span class="sxs-lookup"><span data-stu-id="6fb80-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="6fb80-112">Jeśli nie znasz narzędzi wiersza polecenia platformy .NET Core, możesz zapoznać się z nimi w [temacie](../../../core/tutorials/using-with-xplat-cli.md)wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="6fb80-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="6fb80-113">Zmodyfikuj metodę w program.cs w następujący sposób: `Main`</span><span class="sxs-lookup"><span data-stu-id="6fb80-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="6fb80-114">Gdy program jest wykonywany w systemie Windows, wszelkie wartości zwrócone przez `Main` funkcję są przechowywane w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="6fb80-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="6fb80-115">Tę zmienną środowiskową można pobrać przy `ERRORLEVEL` użyciu pliku wsadowego lub `$LastExitCode` z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fb80-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="6fb80-116">Aplikację można skompilować przy użyciu polecenia [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="6fb80-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="6fb80-117">Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="6fb80-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="6fb80-118">Wklej następujący kod do pliku tekstowego i Zapisz go jako `test.ps1` folder zawierający projekt.</span><span class="sxs-lookup"><span data-stu-id="6fb80-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="6fb80-119">Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fb80-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="6fb80-120">Ponieważ kod zwraca zero, plik wsadowy będzie zgłaszał powodzenie.</span><span class="sxs-lookup"><span data-stu-id="6fb80-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="6fb80-121">Jeśli jednak zmienisz MainReturnValTest.cs w taki sposób, aby zwracał wartość różną od zera, a następnie ponownie skompilujesz program, kolejne wykonanie skryptu programu PowerShell zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="6fb80-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="6fb80-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6fb80-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="6fb80-123">Asynchroniczne główne wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="6fb80-123">Async Main return values</span></span>

<span data-ttu-id="6fb80-124">Asynchroniczne główne wartości zwracane umożliwiają przenoszenie kodu standardowego niezbędnego do wywołania metod asynchronicznych w programie `Main` do kodu wygenerowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="6fb80-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="6fb80-125">Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do momentu ukończenia operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="6fb80-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="6fb80-126">Teraz można je zastąpić:</span><span class="sxs-lookup"><span data-stu-id="6fb80-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="6fb80-127">Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.</span><span class="sxs-lookup"><span data-stu-id="6fb80-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="6fb80-128">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="6fb80-128">Compiler generated code</span></span>

<span data-ttu-id="6fb80-129">Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fb80-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="6fb80-130">Przy założeniu, że ten punkt `$GeneratedMain`wejścia jest wywoływany, kompilator generuje następujący kod dla tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="6fb80-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="6fb80-131">`static Task Main()`powoduje, że kompilator emituje odpowiednik`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="6fb80-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="6fb80-132">`static Task Main(string[])`powoduje, że kompilator emituje odpowiednik`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="6fb80-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="6fb80-133">`static Task<int> Main()`powoduje, że kompilator emituje odpowiednik`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="6fb80-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="6fb80-134">`static Task<int> Main(string[])`powoduje, że kompilator emituje odpowiednik`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="6fb80-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="6fb80-135">Jeśli przykłady użyto `async` modyfikatora `Main` metody, kompilator wygeneruje ten sam kod.</span><span class="sxs-lookup"><span data-stu-id="6fb80-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fb80-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fb80-136">See also</span></span>

- [<span data-ttu-id="6fb80-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6fb80-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6fb80-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6fb80-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6fb80-139">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="6fb80-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="6fb80-140">Instrukcje: Wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="6fb80-140">How to: Display Command Line Arguments</span></span>](./how-to-display-command-line-arguments.md)
