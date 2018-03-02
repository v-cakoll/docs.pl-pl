---
title: "Rozpoczynanie pracy z F # w programie Visual Studio dla komputerów Mac"
description: "Dowiedz się, jak używać F # za pomocą programu Visual Studio dla komputerów Mac."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: mizzle-mo
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 776a2ddf5563a954e462b3888ebf05da90241e4b
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="a59d9-104">Rozpoczynanie pracy z F # w programie Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="a59d9-104">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="a59d9-105">F # i narzędzia Visual F # są obsługiwane w programie Visual Studio dla komputerów Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="a59d9-105">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="a59d9-106">Aby rozpocząć, należy [pobierania programu Visual Studio dla komputerów Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), jeśli nie jest jeszcze.</span><span class="sxs-lookup"><span data-stu-id="a59d9-106">To begin, you should [download Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="a59d9-107">W tym artykule wykorzystano 2017 społeczności usługi Visual Studio dla komputerów Mac, ale może użyć F # z wersją wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a59d9-107">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="a59d9-108">Instalowanie F #</span><span class="sxs-lookup"><span data-stu-id="a59d9-108">Installing F#</span></span> #

<span data-ttu-id="a59d9-109">Po pobraniu programu Visual Studio dla komputerów Mac, wyświetli monit dotyczący o wybranie co chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="a59d9-109">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="a59d9-110">Na potrzeby tego artykułu firma Microsoft będzie można pozostawienia wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="a59d9-110">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="a59d9-111">W przeciwieństwie do programu Visual Studio dla systemu Windows nie trzeba jawnie zainstalowany Obsługa F #.</span><span class="sxs-lookup"><span data-stu-id="a59d9-111">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="a59d9-112">Naciśnij przycisk Zainstaluj, aby kontynuować.</span><span class="sxs-lookup"><span data-stu-id="a59d9-112">Press "Install" to proceed.</span></span>

<span data-ttu-id="a59d9-113">Po zakończeniu instalacji wybierz pozycję "Uruchom Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="a59d9-113">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="a59d9-114">Można również uruchomić go za pomocą wyszukiwania na macOS.</span><span class="sxs-lookup"><span data-stu-id="a59d9-114">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="a59d9-115">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="a59d9-115">Creating a console application</span></span>

<span data-ttu-id="a59d9-116">Jednym z najprostszych projekty w programie Visual Studio for Mac jest aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="a59d9-116">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="a59d9-117">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="a59d9-117">Here's how to do it.</span></span>  <span data-ttu-id="a59d9-118">Po otwarciu programu Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="a59d9-118">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="a59d9-119">Na **pliku** menu wskaż **nowe rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="a59d9-119">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="a59d9-120">W oknie dialogowym Nowy projekt są 2 różnych szablonów dla aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="a59d9-120">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="a59d9-121">Istnieje Other -> .NET, który jest przeznaczony dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a59d9-121">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="a59d9-122">Ten szablon podlega .NET Core -> aplikacji, który jest przeznaczony dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a59d9-122">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="a59d9-123">Albo szablonu powinny działać na potrzeby tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="a59d9-123">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="a59d9-124">W obszarze aplikacji konsoli w języku C# F # w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a59d9-124">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="a59d9-125">Wybierz **dalej** przycisk, aby przejść do przodu!</span><span class="sxs-lookup"><span data-stu-id="a59d9-125">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="a59d9-126">Nadaj nazwę projektu, a następnie wybierz odpowiednie opcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a59d9-126">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="a59d9-127">Powiadomienia i w okienku podglądu przy krawędzi ekranu, który będzie informować o struktury katalogów, która zostanie utworzona na podstawie opcji wybrany.</span><span class="sxs-lookup"><span data-stu-id="a59d9-127">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="a59d9-128">Kliknij przycisk **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="a59d9-128">Click **Create**.</span></span>  <span data-ttu-id="a59d9-129">Powinna zostać wyświetlona projektów F # w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="a59d9-129">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="a59d9-130">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="a59d9-130">Writing your code</span></span>

<span data-ttu-id="a59d9-131">Rozpocznijmy pisząc kodu.</span><span class="sxs-lookup"><span data-stu-id="a59d9-131">Let's get started by writing some code first.</span></span>  <span data-ttu-id="a59d9-132">Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a59d9-132">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="a59d9-133">W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje danych wejściowych o nazwie `x` i mnożona przez samego siebie.</span><span class="sxs-lookup"><span data-stu-id="a59d9-133">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="a59d9-134">Ponieważ F # używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.</span><span class="sxs-lookup"><span data-stu-id="a59d9-134">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="a59d9-135">Kompilator języka F # rozumie typy, których mnożenia jest prawidłowy i przypisze typu na `x` zależy od `square` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a59d9-135">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="a59d9-136">Jeśli w ustawieniu kursora `square`, należy znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="a59d9-136">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="a59d9-137">Jest to określane jako podpis typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="a59d9-137">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="a59d9-138">Mogą być odczytywane następująco: "kwadratowa jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".</span><span class="sxs-lookup"><span data-stu-id="a59d9-138">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="a59d9-139">Należy pamiętać, że kompilator nadać `square` `int` typu teraz — jest to ponieważ mnożenie nie jest rodzajowa między *wszystkie* typów, ale raczej jest rodzajowy zamkniętego zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="a59d9-139">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="a59d9-140">Kompilator języka F # pobrane `int` dla tego punktu, ale dostosuje podpis typu połączeń `square` z innym typem wejściowych, takich jak `float`.</span><span class="sxs-lookup"><span data-stu-id="a59d9-140">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="a59d9-141">Innej funkcji, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, sprawdzić kompilator języka F #, wykonanie tego programu.</span><span class="sxs-lookup"><span data-stu-id="a59d9-141">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="a59d9-142">Wynika z tej samej Konwencji, jak inne [języków programowania w stylu języka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą zostać przekazane do tej funkcji i zostanie zwrócony kod liczba całkowita (zazwyczaj `0`).</span><span class="sxs-lookup"><span data-stu-id="a59d9-142">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="a59d9-143">W tej funkcji, które nazywamy `square` funkcji z argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="a59d9-143">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="a59d9-144">Kompilator języka F # następnie przypisuje typ `square` jako `int -> int` (to znaczy funkcję, która przyjmuje `int` i tworzy `int`).</span><span class="sxs-lookup"><span data-stu-id="a59d9-144">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="a59d9-145">Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobnie jak języków programowania w stylu języka C, parametry, które odpowiadają na określone w ciągu formatu, a następnie drukuje wyniki i znakiem nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="a59d9-145">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="a59d9-146">Wykonywanie kodu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a59d9-146">Running your code</span></span>

<span data-ttu-id="a59d9-147">Można uruchomić kod i wyświetlić wyniki, klikając **Uruchom** z menu najwyższego poziomu, a następnie **uruchomić bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="a59d9-147">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="a59d9-148">To spowoduje uruchomienie programu bez debugowania i służy do wyświetlenia wyników.</span><span class="sxs-lookup"><span data-stu-id="a59d9-148">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="a59d9-149">Teraz powinny być widoczne następujące wypisywane w oknie konsoli, które tam pojawi programu Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="a59d9-149">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="a59d9-150">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a59d9-150">Congratulations!</span></span>  <span data-ttu-id="a59d9-151">Utworzeniu pierwszego projektu F # w programie Visual Studio dla komputerów Mac, zapisywać funkcja F # drukowane wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.</span><span class="sxs-lookup"><span data-stu-id="a59d9-151">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="a59d9-152">Przy użyciu interakcyjne F #</span><span class="sxs-lookup"><span data-stu-id="a59d9-152">Using F# Interactive</span></span>

<span data-ttu-id="a59d9-153">Jednym z najlepszych funkcji programu Visual F # narzędzi w programie Visual Studio for Mac jest okno interaktywne F #.</span><span class="sxs-lookup"><span data-stu-id="a59d9-153">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="a59d9-154">Umożliwia ona wysłania kodu do procesu, gdy wywołanie kodu i interakcyjnie zobaczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="a59d9-154">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="a59d9-155">Aby rozpocząć używanie go, zaznacz `square` funkcji zdefiniowanej w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a59d9-155">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="a59d9-156">Przejdź do menu **Edytuj** z menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a59d9-156">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="a59d9-157">Następnie wybierz **Wyślij zaznaczenie do narzędzia F # Interactive**.</span><span class="sxs-lookup"><span data-stu-id="a59d9-157">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a59d9-158">Wykonuje kod okno interaktywne F #.</span><span class="sxs-lookup"><span data-stu-id="a59d9-158">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="a59d9-159">Alternatywnie kliknij zaznaczenie prawym przyciskiem myszy i wybierz polecenie **Wyślij zaznaczenie do narzędzia F # Interactive**.</span><span class="sxs-lookup"><span data-stu-id="a59d9-159">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a59d9-160">Powinny pojawić się F # Interactive okna są wyświetlane następujące w niej:</span><span class="sxs-lookup"><span data-stu-id="a59d9-160">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="a59d9-161">Ta operacja wyświetla tę samą sygnaturę funkcji dla `square` funkcji, który został wcześniej wyświetlony po aktywowany przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="a59d9-161">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="a59d9-162">Ponieważ `square` jest teraz zdefiniowana w proces narzędzia F # Interactive, można wywołać ją z różnymi wartościami:</span><span class="sxs-lookup"><span data-stu-id="a59d9-162">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="a59d9-163">To wykonuje funkcję, wiąże wynik na nową nazwę `it`i wyświetla typ i wartość `it`.</span><span class="sxs-lookup"><span data-stu-id="a59d9-163">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="a59d9-164">Należy pamiętać, że należy zakończyć każdego wiersza `;;`.</span><span class="sxs-lookup"><span data-stu-id="a59d9-164">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="a59d9-165">Jest to, jak F # Interactive wie, po zakończeniu wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="a59d9-165">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="a59d9-166">Istnieje także możliwość zdefiniowania nowych funkcji w F # Interactive:</span><span class="sxs-lookup"><span data-stu-id="a59d9-166">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="a59d9-167">Powyższy kod definiuje nową funkcję, `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta!</span><span class="sxs-lookup"><span data-stu-id="a59d9-167">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="a59d9-168">Możesz wywołać tę funkcję, aby sprawdzić, jakie zwraca z różnych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a59d9-168">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="a59d9-169">Można wywołać funkcji w ramach wywołania funkcji:</span><span class="sxs-lookup"><span data-stu-id="a59d9-169">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="a59d9-170">Można również użyć [operatora potoku następny](../language-reference/symbol-and-operator-reference/index.md) do potoku wartość do dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="a59d9-170">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="a59d9-171">Operator do przodu potoku i inne, znajdują się w kolejnych samouczkach.</span><span class="sxs-lookup"><span data-stu-id="a59d9-171">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="a59d9-172">Jest to tylko glimpse do czego z F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="a59d9-172">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="a59d9-173">Aby dowiedzieć się więcej, zapoznaj się [interakcyjne programowania w języku F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="a59d9-173">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a59d9-174">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a59d9-174">Next steps</span></span>

<span data-ttu-id="a59d9-175">Jeśli nie jest jeszcze, zapoznaj się [samouczek programu F #](../tour.md), która obejmuje niektóre podstawowe funkcje języka F #.</span><span class="sxs-lookup"><span data-stu-id="a59d9-175">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="a59d9-176">Zostanie zawiera przegląd niektórych funkcji języka F # i zapewnić wystarczającą przykłady, które można skopiować do programu Visual Studio dla komputerów Mac i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="a59d9-176">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="a59d9-177">Są także niektóre dużą zasobów zewnętrznych można używać, pokazywane w [przewodnik F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="a59d9-177">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a59d9-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a59d9-178">See also</span></span>
 [<span data-ttu-id="a59d9-179">Visual F#</span><span class="sxs-lookup"><span data-stu-id="a59d9-179">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="a59d9-180">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="a59d9-180">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="a59d9-181">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="a59d9-181">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="a59d9-182">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="a59d9-182">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="a59d9-183">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="a59d9-183">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
