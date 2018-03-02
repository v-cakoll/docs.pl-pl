---
title: 'Rozpoczynanie pracy z F # w programie Visual Studio'
description: "Dowiedz się, jak używać F # za pomocą programu Visual Studio."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 818bf50507a88e1d765da8d0505ed8da4790b71f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="1fa71-104">Rozpoczynanie pracy z F # w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1fa71-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="1fa71-105">F # i narzędzia Visual F # są obsługiwane w programie Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="1fa71-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="1fa71-106">Aby rozpocząć, należy [pobierania programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), jeśli nie jest jeszcze.</span><span class="sxs-lookup"><span data-stu-id="1fa71-106">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="1fa71-107">W tym artykule wykorzystano program Visual Studio 2017 Community Edition, ale może użyć F # z wersją wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1fa71-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="1fa71-108">Instalowanie F #</span><span class="sxs-lookup"><span data-stu-id="1fa71-108">Installing F#</span></span> #

<span data-ttu-id="1fa71-109">Jeśli po raz pierwszy jest pobranie Visual Studio, najpierw zainstaluje Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1fa71-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="1fa71-110">Zainstaluj wszelkie wersje programu Visual Studio 2017 z Instalatora.</span><span class="sxs-lookup"><span data-stu-id="1fa71-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="1fa71-111">Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="1fa71-112">Następnie wyświetlona lista obciążeń.</span><span class="sxs-lookup"><span data-stu-id="1fa71-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="1fa71-113">Można zainstalować F # za pomocą dowolnej z następujących obciążenia:</span><span class="sxs-lookup"><span data-stu-id="1fa71-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="1fa71-114">Obciążenie</span><span class="sxs-lookup"><span data-stu-id="1fa71-114">Workload</span></span>|<span data-ttu-id="1fa71-115">Akcja</span><span class="sxs-lookup"><span data-stu-id="1fa71-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="1fa71-116">Programowanie wieloplatformowych .NET core</span><span class="sxs-lookup"><span data-stu-id="1fa71-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="1fa71-117">Żadna akcja - F # jest instalowany domyślnie</span><span class="sxs-lookup"><span data-stu-id="1fa71-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="1fa71-118">ASP.NET i sieć web development</span><span class="sxs-lookup"><span data-stu-id="1fa71-118">ASP.NET and web development</span></span> | <span data-ttu-id="1fa71-119">Żadna akcja - F # jest instalowany domyślnie</span><span class="sxs-lookup"><span data-stu-id="1fa71-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="1fa71-120">Programowanie Azure</span><span class="sxs-lookup"><span data-stu-id="1fa71-120">Azure development</span></span> | <span data-ttu-id="1fa71-121">Żadna akcja - F # jest instalowany domyślnie</span><span class="sxs-lookup"><span data-stu-id="1fa71-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="1fa71-122">Programowanie przenośnych z platformą .NET</span><span class="sxs-lookup"><span data-stu-id="1fa71-122">Mobile development with .NET</span></span> | <span data-ttu-id="1fa71-123">Żadna akcja - F # jest instalowany domyślnie</span><span class="sxs-lookup"><span data-stu-id="1fa71-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="1fa71-124">Aplikacje do analizy i przetwarzania danych</span><span class="sxs-lookup"><span data-stu-id="1fa71-124">Data science and analytical applications</span></span> | <span data-ttu-id="1fa71-125">Żadna akcja - F # jest instalowany domyślnie</span><span class="sxs-lookup"><span data-stu-id="1fa71-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="1fa71-126">.NET — rozwój pulpitu</span><span class="sxs-lookup"><span data-stu-id="1fa71-126">.NET desktop development</span></span> | <span data-ttu-id="1fa71-127">Wybierz **obsługi pulpitu języka F #** z prawej</span><span class="sxs-lookup"><span data-stu-id="1fa71-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="1fa71-128">Magazynowanie i przetwarzanie danych</span><span class="sxs-lookup"><span data-stu-id="1fa71-128">Data storage and processing</span></span> | <span data-ttu-id="1fa71-129">Wybierz **obsługi pulpitu języka F #** z prawej</span><span class="sxs-lookup"><span data-stu-id="1fa71-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="1fa71-130">Następnie kliknij przycisk **Modyfikuj** w prawej dolnej.</span><span class="sxs-lookup"><span data-stu-id="1fa71-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="1fa71-131">Spowoduje to zainstalowanie wszystko, co jest wybrane.</span><span class="sxs-lookup"><span data-stu-id="1fa71-131">This will install everything you have selected.</span></span>  <span data-ttu-id="1fa71-132">Następnie możesz otworzyć programu Visual Studio 2017 z obsługą języka F #, klikając **uruchamianie**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="1fa71-133">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="1fa71-133">Creating a console application</span></span>

<span data-ttu-id="1fa71-134">Jednym z najprostszych projekty w programie Visual Studio jest aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="1fa71-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="1fa71-135">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1fa71-135">Here's how to do it.</span></span>  <span data-ttu-id="1fa71-136">Po otwarciu programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1fa71-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="1fa71-137">Na **pliku** menu wskaż **nowy**, a następnie wybierz pozycję **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="1fa71-138">W nowy projekt okna dialogowego, w obszarze **szablony**, powinny pojawić się **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="1fa71-139">Wybierz tę opcję, aby wyświetlić szablony F #.</span><span class="sxs-lookup"><span data-stu-id="1fa71-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="1fa71-140">Wybierz opcję **.NET Core aplikacji konsoli** lub **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="1fa71-141">Wybierz **OK** przycisk, aby utworzyć projekt F #!</span><span class="sxs-lookup"><span data-stu-id="1fa71-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="1fa71-142">Powinna zostać wyświetlona projektów F # w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="1fa71-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="1fa71-143">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="1fa71-143">Writing your code</span></span>

<span data-ttu-id="1fa71-144">Rozpocznijmy pisząc kodu.</span><span class="sxs-lookup"><span data-stu-id="1fa71-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="1fa71-145">Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fa71-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="1fa71-146">W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje danych wejściowych o nazwie `x` i mnożona przez samego siebie.</span><span class="sxs-lookup"><span data-stu-id="1fa71-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="1fa71-147">Ponieważ F # używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.</span><span class="sxs-lookup"><span data-stu-id="1fa71-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="1fa71-148">Kompilator języka F # rozumie typy, których mnożenia jest prawidłowy i przypisze typu na `x` zależy od `square` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1fa71-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="1fa71-149">Jeśli w ustawieniu kursora `square`, należy znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="1fa71-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="1fa71-150">Jest to określane jako podpis typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="1fa71-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="1fa71-151">Mogą być odczytywane następująco: "kwadratowa jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".</span><span class="sxs-lookup"><span data-stu-id="1fa71-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="1fa71-152">Należy pamiętać, że kompilator nadać `square` `int` typu teraz — jest to ponieważ mnożenie nie jest rodzajowa między *wszystkie* typów, ale raczej jest rodzajowy zamkniętego zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="1fa71-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="1fa71-153">Kompilator języka F # pobrane `int` dla tego punktu, ale dostosuje podpis typu połączeń `square` z innym typem wejściowych, takich jak `float`.</span><span class="sxs-lookup"><span data-stu-id="1fa71-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="1fa71-154">Innej funkcji, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, sprawdzić kompilator języka F #, wykonanie tego programu.</span><span class="sxs-lookup"><span data-stu-id="1fa71-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="1fa71-155">Wynika z tej samej Konwencji, jak inne [języków programowania w stylu języka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą zostać przekazane do tej funkcji i zostanie zwrócony kod liczba całkowita (zazwyczaj `0`).</span><span class="sxs-lookup"><span data-stu-id="1fa71-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="1fa71-156">W tej funkcji, które nazywamy `square` funkcji z argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="1fa71-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="1fa71-157">Kompilator języka F # następnie przypisuje typ `square` jako `int -> int` (to znaczy funkcję, która przyjmuje `int` i tworzy `int`).</span><span class="sxs-lookup"><span data-stu-id="1fa71-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="1fa71-158">Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobnie jak języków programowania w stylu języka C, parametry, które odpowiadają na określone w ciągu formatu, a następnie drukuje wyniki i znakiem nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="1fa71-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="1fa71-159">Wykonywanie kodu użytkownika</span><span class="sxs-lookup"><span data-stu-id="1fa71-159">Running your code</span></span>

<span data-ttu-id="1fa71-160">Można uruchomić kod i wyświetlić wyniki naciskając **ctrl-f5**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="1fa71-161">To spowoduje uruchomienie programu bez debugowania i służy do wyświetlenia wyników.</span><span class="sxs-lookup"><span data-stu-id="1fa71-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="1fa71-162">Alternatywnie można wybrać **debugowania** menu najwyższego poziomu elementu w programie Visual Studio i wybierz polecenie **uruchomić bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="1fa71-163">Powinien zostać wyświetlony poniższy wypisywane w oknie konsoli, które tam pojawi Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1fa71-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="1fa71-164">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="1fa71-164">Congratulations!</span></span>  <span data-ttu-id="1fa71-165">Utworzeniu pierwszego projektu F # w programie Visual Studio, zapisywać funkcja F # drukowane wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.</span><span class="sxs-lookup"><span data-stu-id="1fa71-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="1fa71-166">Przy użyciu interakcyjne F #</span><span class="sxs-lookup"><span data-stu-id="1fa71-166">Using F# Interactive</span></span>

<span data-ttu-id="1fa71-167">Jednym z najlepszych funkcji programu Visual F # narzędzi w programie Visual Studio jest okno interaktywne F #.</span><span class="sxs-lookup"><span data-stu-id="1fa71-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="1fa71-168">Umożliwia ona wysłania kodu do procesu, gdy wywołanie kodu i interakcyjnie zobaczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="1fa71-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="1fa71-169">Aby rozpocząć używanie go, zaznacz `square` funkcji zdefiniowanej w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1fa71-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="1fa71-170">Następnie przytrzymać **Alt** i naciśnij **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1fa71-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="1fa71-171">Wykonuje kod okno interaktywne F #.</span><span class="sxs-lookup"><span data-stu-id="1fa71-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="1fa71-172">Powinny pojawić się F # Interactive okna są wyświetlane następujące w niej:</span><span class="sxs-lookup"><span data-stu-id="1fa71-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="1fa71-173">Ta operacja wyświetla tę samą sygnaturę funkcji dla `square` funkcji, który został wcześniej wyświetlony po aktywowany przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="1fa71-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="1fa71-174">Ponieważ `square` jest teraz zdefiniowana w proces narzędzia F # Interactive, można wywołać ją z różnymi wartościami:</span><span class="sxs-lookup"><span data-stu-id="1fa71-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="1fa71-175">To wykonuje funkcję, wiąże wynik na nową nazwę `it`i wyświetla typ i wartość `it`.</span><span class="sxs-lookup"><span data-stu-id="1fa71-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="1fa71-176">Należy pamiętać, że należy zakończyć każdego wiersza `;;`.</span><span class="sxs-lookup"><span data-stu-id="1fa71-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="1fa71-177">Jest to, jak F # Interactive wie, po zakończeniu wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="1fa71-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="1fa71-178">Istnieje także możliwość zdefiniowania nowych funkcji w F # Interactive:</span><span class="sxs-lookup"><span data-stu-id="1fa71-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="1fa71-179">Powyższy kod definiuje nową funkcję, `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta!</span><span class="sxs-lookup"><span data-stu-id="1fa71-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="1fa71-180">Możesz wywołać tę funkcję, aby sprawdzić, jakie zwraca z różnych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1fa71-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="1fa71-181">Można wywołać funkcji w ramach wywołania funkcji:</span><span class="sxs-lookup"><span data-stu-id="1fa71-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="1fa71-182">Można również użyć [operatora potoku następny](../language-reference/symbol-and-operator-reference/index.md) do potoku wartość do dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="1fa71-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="1fa71-183">Operator do przodu potoku i inne, znajdują się w kolejnych samouczkach.</span><span class="sxs-lookup"><span data-stu-id="1fa71-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="1fa71-184">Jest to tylko glimpse do czego z F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="1fa71-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="1fa71-185">Aby dowiedzieć się więcej, zapoznaj się [interakcyjne programowania w języku F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="1fa71-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1fa71-186">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1fa71-186">Next steps</span></span>

<span data-ttu-id="1fa71-187">Jeśli nie jest jeszcze, zapoznaj się [samouczek programu F #](../tour.md), która obejmuje niektóre podstawowe funkcje języka F #.</span><span class="sxs-lookup"><span data-stu-id="1fa71-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="1fa71-188">Zostanie zawiera przegląd niektórych funkcji języka F # i zapewnić wystarczającą przykłady, które można skopiować do programu Visual Studio i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="1fa71-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="1fa71-189">Są także niektóre dużą zasobów zewnętrznych można używać, pokazywane w [przewodnik F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="1fa71-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1fa71-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fa71-190">See also</span></span>
 [<span data-ttu-id="1fa71-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="1fa71-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="1fa71-192">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="1fa71-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="1fa71-193">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="1fa71-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="1fa71-194">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="1fa71-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="1fa71-195">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="1fa71-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
