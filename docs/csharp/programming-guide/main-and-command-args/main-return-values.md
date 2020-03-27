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
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="40378-102">Main() wartości zwracane (Przewodnik programowania języka C#)</span><span class="sxs-lookup"><span data-stu-id="40378-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="40378-103">Metoda `Main` może `void`zwrócić:</span><span class="sxs-lookup"><span data-stu-id="40378-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="40378-104">Może również `int`zwrócić:</span><span class="sxs-lookup"><span data-stu-id="40378-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="40378-105">Jeśli zwracana `Main` wartość z nie `void` jest używana, zwracanie umożliwia nieco prostszy kod.</span><span class="sxs-lookup"><span data-stu-id="40378-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="40378-106">Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="40378-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="40378-107">Zwracana wartość `Main` z jest traktowana jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="40378-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="40378-108">Jeśli `void` jest `Main` zwracany z kodu `0`zakończenia będzie niejawnie .</span><span class="sxs-lookup"><span data-stu-id="40378-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="40378-109">Poniższy przykład pokazuje, jak `Main` można uzyskać dostęp do zwracanej wartości z.</span><span class="sxs-lookup"><span data-stu-id="40378-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="40378-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="40378-110">Example</span></span>

<span data-ttu-id="40378-111">W tym przykładzie użyto narzędzi wiersza polecenia [.NET Core.](../../../core/index.yml)</span><span class="sxs-lookup"><span data-stu-id="40378-111">This example uses [.NET Core](../../../core/index.yml) command line tools.</span></span> <span data-ttu-id="40378-112">Jeśli nie znasz narzędzi wiersza polecenia .NET Core, możesz dowiedzieć się o nich w tym [temacie Wprowadzenie](../../../core/tutorials/cli-create-console-app.md).</span><span class="sxs-lookup"><span data-stu-id="40378-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="40378-113">Zmodyfikuj `Main` metodę w *program.cs* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="40378-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="40378-114">Gdy program jest wykonywany w systemie Windows, każda wartość zwrócona `Main` z funkcji jest przechowywana w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="40378-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="40378-115">Tę zmienną środowiskową `ERRORLEVEL` można pobrać z `$LastExitCode` pliku wsadowego lub z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40378-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="40378-116">Aplikację można utworzyć za pomocą polecenia [dotnet CLI.](../../../core/tools/dotnet.md) `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="40378-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="40378-117">Następnie utwórz skrypt programu Powershell, aby uruchomić aplikację i wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="40378-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="40378-118">Wklej następujący kod do pliku tekstowego `test.ps1` i zapisz go tak jak w folderze zawierającym projekt.</span><span class="sxs-lookup"><span data-stu-id="40378-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="40378-119">Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu programu powershell.</span><span class="sxs-lookup"><span data-stu-id="40378-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="40378-120">Ponieważ kod zwraca zero, plik wsadowy zgłosi sukces.</span><span class="sxs-lookup"><span data-stu-id="40378-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="40378-121">Jeśli jednak zmienisz MainReturnValTest.cs, aby zwrócić wartość niezerową, a następnie ponownie skompilować program, późniejsze wykonanie skryptu programu powershell spowoduje zgłoszenie awarii.</span><span class="sxs-lookup"><span data-stu-id="40378-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="40378-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="40378-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="40378-123">Główne wartości zwracane Asynchronii</span><span class="sxs-lookup"><span data-stu-id="40378-123">Async Main return values</span></span>

<span data-ttu-id="40378-124">Wartości zwracane asynchroniczne główne przenoszą kod standardowy niezbędny `Main` do wywoływania metod asynchronicznych do kodu wygenerowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="40378-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="40378-125">Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczne i upewnić się, że program działał do czasu zakończenia operacji asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="40378-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="40378-126">Teraz można to zastąpić:</span><span class="sxs-lookup"><span data-stu-id="40378-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="40378-127">Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.</span><span class="sxs-lookup"><span data-stu-id="40378-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="40378-128">Wygenerowany kod kompilatora</span><span class="sxs-lookup"><span data-stu-id="40378-128">Compiler generated code</span></span>

<span data-ttu-id="40378-129">Gdy punkt wejścia aplikacji `Task` `Task<int>`zwraca lub , kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40378-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="40378-130">Zakładając, że ten `$GeneratedMain`punkt wejścia jest wywoływany, kompilator generuje następujący kod dla tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="40378-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="40378-131">`static Task Main()`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="40378-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="40378-132">`static Task Main(string[])`powoduje, że kompilator emituje równowartość`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="40378-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="40378-133">`static Task<int> Main()`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="40378-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="40378-134">`static Task<int> Main(string[])`powoduje, że kompilator emituje równowartość`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="40378-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="40378-135">Jeśli przykłady `async` używane modyfikator na `Main` metodę, kompilator wygeneruje ten sam kod.</span><span class="sxs-lookup"><span data-stu-id="40378-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="40378-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40378-136">See also</span></span>

- [<span data-ttu-id="40378-137">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="40378-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="40378-138">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="40378-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40378-139">Main() i Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="40378-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="40378-140">Jak wyświetlić argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="40378-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
