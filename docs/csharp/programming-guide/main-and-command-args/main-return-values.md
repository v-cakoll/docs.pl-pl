---
title: Main () zwracane wartości — C# Przewodnik programowania
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 21e780470f455ac133fd4d11ae43c63a4b18c582
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712042"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="faa31-102">Main () — zwracane wartościC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="faa31-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="faa31-103">Metoda `Main` może zwracać `void`:</span><span class="sxs-lookup"><span data-stu-id="faa31-103">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="faa31-104">Może również zwracać `int`:</span><span class="sxs-lookup"><span data-stu-id="faa31-104">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="faa31-105">Jeśli wartość zwracana z `Main` nie jest używana, zwracanie `void` umożliwia nieznacznie łatwiejszy kod.</span><span class="sxs-lookup"><span data-stu-id="faa31-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="faa31-106">Jednak zwrócenie liczby całkowitej umożliwia programowi przekazywanie informacji o stanie do innych programów lub skryptów, które wywołują plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="faa31-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="faa31-107">Wartość zwracana z `Main` jest traktowana jako kod zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="faa31-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="faa31-108">Jeśli `void` jest zwracana z `Main` kod zakończenia będzie niejawnie `0`.</span><span class="sxs-lookup"><span data-stu-id="faa31-108">If `void` is returned from `Main` the exit code will be implicitly `0`.</span></span> <span data-ttu-id="faa31-109">Poniższy przykład pokazuje, jak można uzyskać dostęp do wartości zwracanej z `Main`.</span><span class="sxs-lookup"><span data-stu-id="faa31-109">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="faa31-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="faa31-110">Example</span></span>

<span data-ttu-id="faa31-111">Ten przykład używa narzędzi wiersza polecenia [platformy .NET Core](../../../core/index.md) .</span><span class="sxs-lookup"><span data-stu-id="faa31-111">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="faa31-112">Jeśli nie znasz narzędzi wiersza polecenia platformy .NET Core, możesz zapoznać się z nimi w [temacie](../../../core/tutorials/cli-create-console-app.md)wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="faa31-112">If you are unfamiliar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/cli-create-console-app.md).</span></span>

<span data-ttu-id="faa31-113">Zmodyfikuj metodę `Main` w *program.cs* w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="faa31-113">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="faa31-114">Gdy program jest wykonywany w systemie Windows, wszelkie wartości zwrócone przez funkcję `Main` są przechowywane w zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="faa31-114">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="faa31-115">Tę zmienną środowiskową można pobrać przy użyciu `ERRORLEVEL` z pliku wsadowego lub `$LastExitCode` z programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa31-115">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="faa31-116">Aplikację można skompilować za pomocą polecenia `dotnet build` [interfejsu wiersza poleceń dotnet](../../../core/tools/dotnet.md) .</span><span class="sxs-lookup"><span data-stu-id="faa31-116">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="faa31-117">Następnie utwórz skrypt programu PowerShell, aby uruchomić aplikację i wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="faa31-117">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="faa31-118">Wklej następujący kod do pliku tekstowego i Zapisz go jako `test.ps1` w folderze zawierającym projekt.</span><span class="sxs-lookup"><span data-stu-id="faa31-118">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="faa31-119">Uruchom skrypt programu PowerShell, wpisując `test.ps1` w wierszu polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="faa31-119">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="faa31-120">Ponieważ kod zwraca zero, plik wsadowy będzie zgłaszał powodzenie.</span><span class="sxs-lookup"><span data-stu-id="faa31-120">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="faa31-121">Jeśli jednak zmienisz MainReturnValTest.cs w taki sposób, aby zwracał wartość różną od zera, a następnie ponownie skompilujesz program, kolejne wykonanie skryptu programu PowerShell zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="faa31-121">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="faa31-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="faa31-122">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="faa31-123">Asynchroniczne główne wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="faa31-123">Async Main return values</span></span>

<span data-ttu-id="faa31-124">Asynchroniczne główne wartości zwracane umożliwiają przenoszenie kodu standardowego niezbędnego do wywoływania metod asynchronicznych w `Main` do kodu wygenerowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="faa31-124">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="faa31-125">Wcześniej należy napisać tę konstrukcję, aby wywołać kod asynchroniczny i upewnić się, że program został uruchomiony do momentu ukończenia operacji asynchronicznej:</span><span class="sxs-lookup"><span data-stu-id="faa31-125">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

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

<span data-ttu-id="faa31-126">Teraz można je zastąpić:</span><span class="sxs-lookup"><span data-stu-id="faa31-126">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="faa31-127">Zaletą nowej składni jest to, że kompilator zawsze generuje poprawny kod.</span><span class="sxs-lookup"><span data-stu-id="faa31-127">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="faa31-128">Kod wygenerowany przez kompilator</span><span class="sxs-lookup"><span data-stu-id="faa31-128">Compiler generated code</span></span>

<span data-ttu-id="faa31-129">Gdy punkt wejścia aplikacji zwraca `Task` lub `Task<int>`, kompilator generuje nowy punkt wejścia, który wywołuje metodę punktu wejścia zadeklarowaną w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faa31-129">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="faa31-130">Przy założeniu, że ten punkt wejścia jest nazywany `$GeneratedMain`, kompilator generuje następujący kod dla tych punktów wejścia:</span><span class="sxs-lookup"><span data-stu-id="faa31-130">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="faa31-131">`static Task Main()` powoduje, że kompilator emituje odpowiednik `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="faa31-131">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="faa31-132">`static Task Main(string[])` powoduje, że kompilator emituje odpowiednik `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="faa31-132">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="faa31-133">`static Task<int> Main()` powoduje, że kompilator emituje odpowiednik `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="faa31-133">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="faa31-134">`static Task<int> Main(string[])` powoduje, że kompilator emituje odpowiednik `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="faa31-134">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="faa31-135">Jeśli przykłady użyto `async` modyfikatora metody `Main`, kompilator wygeneruje ten sam kod.</span><span class="sxs-lookup"><span data-stu-id="faa31-135">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="faa31-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faa31-136">See also</span></span>

- [<span data-ttu-id="faa31-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="faa31-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="faa31-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="faa31-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="faa31-139">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="faa31-139">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="faa31-140">Wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="faa31-140">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
