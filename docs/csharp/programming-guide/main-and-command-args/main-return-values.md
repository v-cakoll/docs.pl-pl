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
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="c273c-102">Wartości zwracane main() (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="c273c-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="c273c-103">Metoda `Main` może `void`zwrócić:</span><span class="sxs-lookup"><span data-stu-id="c273c-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="c273c-104">Może również zwrócić `int`:</span><span class="sxs-lookup"><span data-stu-id="c273c-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="c273c-105">Jeśli wartość zwracana z `Main` nie `void` jest używany, zwracanie pozwala na nieco prostszy kod.</span><span class="sxs-lookup"><span data-stu-id="c273c-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="c273c-106">Jednak zwracanie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie innym programom lub skryptom wywołującym plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="c273c-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="c273c-107">Wartość zwracana `Main` z jest traktowana jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="c273c-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="c273c-108">Jeśli `void` zostanie zwrócony z `Main` kodu zakończenia `0`będzie niejawnie .</span><span class="sxs-lookup"><span data-stu-id="c273c-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="c273c-109">W poniższym przykładzie pokazano, jak można uzyskać dostęp do wartości zwracanej. `Main`</span><span class="sxs-lookup"><span data-stu-id="c273c-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="c273c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c273c-110">Example</span></span>

<span data-ttu-id="c273c-111">W tym przykładzie użyto narzędzi wiersza polecenia [.NET Core.](../../../core/index.md)</span><span class="sxs-lookup"><span data-stu-id="c273c-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="c273c-112">Jeśli nie znasz narzędzi wiersza polecenia .NET Core, możesz dowiedzieć się o nich w tym [temacie Wprowadzenie](../../../core/tutorials/cli-create-console-app.md).</span><span class="sxs-lookup"><span data-stu-id="c273c-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="c273c-113">Zmodyfikuj `Main` metodę w *program.cs* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c273c-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="c273c-114">Gdy program jest wykonywany w systemie Windows, każda wartość zwracana z `Main` funkcji jest przechowywana w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="c273c-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="c273c-115">Tę zmienną środowiskową `ERRORLEVEL` można pobrać przy `$LastExitCode` użyciu pliku wsadowego lub z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c273c-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="c273c-116">Aplikację można utworzyć przy użyciu polecenia [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="c273c-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="c273c-117">Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="c273c-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="c273c-118">Wklej poniższy kod do pliku tekstowego `test.ps1` i zapisz go tak, jak w folderze zawierającym projekt.</span><span class="sxs-lookup"><span data-stu-id="c273c-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="c273c-119">Uruchom skrypt programu PowerShell, wpisując `test.ps1` monit programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c273c-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="c273c-120">Ponieważ kod zwraca zero, plik wsadowy zgłosi powodzenie.</span><span class="sxs-lookup"><span data-stu-id="c273c-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="c273c-121">Jeśli jednak zmienisz MainReturnValTest.cs, aby zwrócić wartość różną od zera, a następnie ponownie skompilować program, późniejsze wykonanie skryptu programu PowerShell spowoduje niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="c273c-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="c273c-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c273c-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="c273c-123">Główne wartości zwracane asynchronii</span><span class="sxs-lookup"><span data-stu-id="c273c-123">Async Main return values</span></span>

<span data-ttu-id="c273c-124">Async Główne wartości zwracane przenieść standardowy kod niezbędny do `Main` wywoływania metod asynchronicznych w do kodu generowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="c273c-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="c273c-125">Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do czasu zakończenia operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="c273c-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="c273c-126">Teraz można to zastąpić:</span><span class="sxs-lookup"><span data-stu-id="c273c-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="c273c-127">Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.</span><span class="sxs-lookup"><span data-stu-id="c273c-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="c273c-128">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="c273c-128">Compiler generated code</span></span>

<span data-ttu-id="c273c-129">Gdy punkt wejścia aplikacji `Task` `Task<int>`zwraca a lub , kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c273c-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="c273c-130">Zakładając, że ten `$GeneratedMain`punkt wejścia jest wywoływana, kompilator generuje następujący kod dla tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="c273c-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="c273c-131">`static Task Main()`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c273c-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c273c-132">`static Task Main(string[])`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c273c-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c273c-133">`static Task<int> Main()`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c273c-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c273c-134">`static Task<int> Main(string[])`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c273c-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="c273c-135">Jeśli przykłady używane `async` modyfikator na `Main` metodę, kompilator będzie generować ten sam kod.</span><span class="sxs-lookup"><span data-stu-id="c273c-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c273c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c273c-136">See also</span></span>

- [<span data-ttu-id="c273c-137">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="c273c-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c273c-138">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c273c-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c273c-139">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c273c-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="c273c-140">Jak wyświetlić argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c273c-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
