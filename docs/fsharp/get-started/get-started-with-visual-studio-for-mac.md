---
title: Wprowadzenie do F# w programie Visual Studio dla komputerów Mac
description: Dowiedz się, jak używać języka F# za pomocą programu Visual Studio dla komputerów Mac.
ms.date: 07/03/2018
ms.openlocfilehash: 6aceec299c29e04aecd7999cd1dda6a56dd2779a
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042336"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="af8ef-103">Wprowadzenie do F# w programie Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="af8ef-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="af8ef-104">Język F# i narzędzi Visual F# są obsługiwane w programie Visual Studio dla komputerów Mac środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="af8ef-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="af8ef-105">Upewnij się, że masz [Visual Studio for Mac zainstalowane](install-fsharp.md#install-f-with-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="af8ef-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="af8ef-106">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="af8ef-106">Creating a console application</span></span>

<span data-ttu-id="af8ef-107">Jednym z najprostszych projektów w programie Visual Studio dla komputerów Mac jest aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="af8ef-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="af8ef-108">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="af8ef-108">Here's how to do it.</span></span>  <span data-ttu-id="af8ef-109">Po otwarciu programu Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="af8ef-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="af8ef-110">Na **pliku** menu wskaż **nowe rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="af8ef-110">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="af8ef-111">W oknie dialogowym Nowy projekt istnieją 2 różnych szablonów dla aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="af8ef-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="af8ef-112">Jest węzłem Other -> .NET, który jest przeznaczony dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af8ef-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="af8ef-113">Ten szablon jest w ramach platformy .NET Core -> Aplikacja, która jest przeznaczony dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="af8ef-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="af8ef-114">Albo szablonu powinny działać na potrzeby tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="af8ef-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="af8ef-115">W obszarze aplikacji konsolowej w języku C# F# w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="af8ef-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="af8ef-116">Wybierz **dalej** przycisk umożliwiający przenoszenie do przodu!</span><span class="sxs-lookup"><span data-stu-id="af8ef-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="af8ef-117">Nadaj projektowi nazwę, a następnie wybierz odpowiednie opcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af8ef-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="af8ef-118">Powiadomienia w okienku podglądu, aby stronie ekranu, pokazujące strukturę katalogu, który zostanie utworzony w oparciu o wybrane opcje.</span><span class="sxs-lookup"><span data-stu-id="af8ef-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="af8ef-119">Kliknij przycisk **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="af8ef-119">Click **Create**.</span></span>  <span data-ttu-id="af8ef-120">Powinien zostać wyświetlony projektu języka F# w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="af8ef-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="af8ef-121">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="af8ef-121">Writing your code</span></span>

<span data-ttu-id="af8ef-122">Zacznijmy napisanie kodu.</span><span class="sxs-lookup"><span data-stu-id="af8ef-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="af8ef-123">Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="af8ef-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="af8ef-124">W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje dane wejściowe o nazwie `x` i mnożona przez siebie.</span><span class="sxs-lookup"><span data-stu-id="af8ef-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="af8ef-125">Ponieważ F# używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.</span><span class="sxs-lookup"><span data-stu-id="af8ef-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="af8ef-126">Kompilator F# rozumie typów, gdzie mnożenie jest nieprawidłowy i spowoduje przypisanie typu `x` zależnie od `square` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="af8ef-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="af8ef-127">Po umieszczeniu wskaźnika myszy nad `square`, powinny pojawić się następujące:</span><span class="sxs-lookup"><span data-stu-id="af8ef-127">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="af8ef-128">Jest to, co jest nazywane podpisu typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="af8ef-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="af8ef-129">Może zostać odczytany następująco: "kwadratu jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".</span><span class="sxs-lookup"><span data-stu-id="af8ef-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="af8ef-130">Należy zauważyć, że kompilator nadaje `square` `int` typu teraz — jest to spowodowane mnożenie nie jest ogólna między *wszystkich* typów, ale raczej jest ogólny w zestawie zamknięte typy.</span><span class="sxs-lookup"><span data-stu-id="af8ef-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="af8ef-131">Kompilator F# pobrane `int` tej punkt, ale skoryguje sygnatura typu Jeśli wywołasz `square` przy użyciu innego typu danych wejściowych, takich jak `float`.</span><span class="sxs-lookup"><span data-stu-id="af8ef-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="af8ef-132">Inną funkcję, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, aby poinformować kompilator F# wykonanie tego programu.</span><span class="sxs-lookup"><span data-stu-id="af8ef-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="af8ef-133">Jest zgodna z tej samej Konwencji co inne [języków programowania stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazywane do tej funkcji i zostanie zwrócony kod liczby całkowitej (zazwyczaj `0`).</span><span class="sxs-lookup"><span data-stu-id="af8ef-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="af8ef-134">Znajduje się w tej funkcji, które nazywamy `square` funkcji z argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="af8ef-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="af8ef-135">Kompilator F# następnie przypisuje typ `square` jako `int -> int` (oznacza to, że funkcja, która przyjmuje `int` i tworzy `int`).</span><span class="sxs-lookup"><span data-stu-id="af8ef-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="af8ef-136">Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobny do języków programowania w stylu języka C, parametry, które odnoszą się do tych określonych w ciągu formatu, a następnie drukuje wyniki i nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="af8ef-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="af8ef-137">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="af8ef-137">Running your code</span></span>

<span data-ttu-id="af8ef-138">Można uruchomić kod i wyświetlić wyniki, klikając **Uruchom** menu najwyższego poziomu i następnie **Rozpocznij bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="af8ef-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="af8ef-139">To spowoduje Uruchom program bez debugowania i pozwala wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="af8ef-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="af8ef-140">Powinien zostać wyświetlony wypisywane w oknie konsoli, które program Visual Studio for Mac pojawiające się następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="af8ef-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="af8ef-141">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="af8ef-141">Congratulations!</span></span>  <span data-ttu-id="af8ef-142">Został utworzony pierwszego projektu F# w programie Visual Studio dla komputerów Mac, napisane, że funkcja języka F# drukowany wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.</span><span class="sxs-lookup"><span data-stu-id="af8ef-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="af8ef-143">Używanie F# Interactive</span><span class="sxs-lookup"><span data-stu-id="af8ef-143">Using F# Interactive</span></span>

<span data-ttu-id="af8ef-144">Jednym z najlepszych funkcji programu Visual F# narzędzia w programie Visual Studio dla komputerów Mac jest okno interaktywne języka F#.</span><span class="sxs-lookup"><span data-stu-id="af8ef-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="af8ef-145">Pozwala ona do wysłania kodu do procesu, w którym można wywołać ten kod i interaktywnie wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="af8ef-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="af8ef-146">Aby zacząć z niego korzystać, wyróżnij `square` funkcję zdefiniowaną w kodzie.</span><span class="sxs-lookup"><span data-stu-id="af8ef-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="af8ef-147">Przejdź do menu **Edytuj** menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="af8ef-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="af8ef-148">Następnie wybierz pozycję **Wyślij zaznaczenie do programu F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="af8ef-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="af8ef-149">To wykonuje kod w oknie interaktywnym F#.</span><span class="sxs-lookup"><span data-stu-id="af8ef-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="af8ef-150">Alternatywnie, kliknij zaznaczenie prawym przyciskiem myszy i wybierz polecenie **Wyślij zaznaczenie do programu F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="af8ef-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="af8ef-151">Powinny zostać wyświetlone F# Interactive okna pojawiają się z następujących czynności w nim:</span><span class="sxs-lookup"><span data-stu-id="af8ef-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="af8ef-152">Pokazuje to taki sam podpis funkcji dla `square` funkcji, tak aby był wyświetlany po najechaniu za pośrednictwem funkcji.</span><span class="sxs-lookup"><span data-stu-id="af8ef-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="af8ef-153">Ponieważ `square` jest teraz zdefiniowana w F# Interactive procesu, można wywołać go z różnymi wartościami:</span><span class="sxs-lookup"><span data-stu-id="af8ef-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="af8ef-154">To wykonuje funkcję, łączy wynik pod nową nazwą `it`i wyświetla typ i wartość `it`.</span><span class="sxs-lookup"><span data-stu-id="af8ef-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="af8ef-155">Należy pamiętać, że musi kończyć się każdy wiersz z `;;`.</span><span class="sxs-lookup"><span data-stu-id="af8ef-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="af8ef-156">Jest to, jak F# Interactive wie, po zakończeniu wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="af8ef-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="af8ef-157">Można również definiować nowe funkcje w F# Interactive:</span><span class="sxs-lookup"><span data-stu-id="af8ef-157">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="af8ef-158">Powyższe definiuje nową funkcję `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta!</span><span class="sxs-lookup"><span data-stu-id="af8ef-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="af8ef-159">Możesz wywołać tę funkcję, aby zobaczyć zwróceniem przy użyciu różnych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="af8ef-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="af8ef-160">Można wywołać funkcji w ramach wywołania funkcji:</span><span class="sxs-lookup"><span data-stu-id="af8ef-160">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="af8ef-161">Można również użyć [operatora potoku — przekazywanie](../language-reference/symbol-and-operator-reference/index.md) do potoku wartość w dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="af8ef-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="af8ef-162">Operator do przodu potoku i innych zostały omówione w kolejnych samouczkach.</span><span class="sxs-lookup"><span data-stu-id="af8ef-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="af8ef-163">Jest to tylko programistyczne do działania z F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="af8ef-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="af8ef-164">Aby dowiedzieć się więcej, zapoznaj się z [interaktywne programowania w języku F#](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="af8ef-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="af8ef-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="af8ef-165">Next steps</span></span>

<span data-ttu-id="af8ef-166">Jeśli jeszcze nie, zapoznaj się z [samouczek programu F#](../tour.md), które obejmują niektóre z podstawowych funkcji języka F#.</span><span class="sxs-lookup"><span data-stu-id="af8ef-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="af8ef-167">Spowoduje przedstawienie niektórych funkcji języka F# i podać przykłady wystarczającą ilość kodu, które można skopiować do programu Visual Studio dla komputerów Mac i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="af8ef-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="af8ef-168">Dostępne są także kilka wspaniałych zasobów zewnętrznych, można użyć, pokazywane w [Podręcznik języka F#](../index.md).</span><span class="sxs-lookup"><span data-stu-id="af8ef-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af8ef-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af8ef-169">See also</span></span>

- [<span data-ttu-id="af8ef-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="af8ef-170">Visual F#</span></span>](../index.md)  
- [<span data-ttu-id="af8ef-171">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="af8ef-171">Tour of F#</span></span>](../tour.md)  
- [<span data-ttu-id="af8ef-172">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="af8ef-172">F# language reference</span></span>](../language-reference/index.md)  
- [<span data-ttu-id="af8ef-173">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="af8ef-173">Type inference</span></span>](../language-reference/type-inference.md)  
- [<span data-ttu-id="af8ef-174">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="af8ef-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
