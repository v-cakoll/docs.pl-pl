---
title: 'Wprowadzenie do F # w programie Visual Studio'
description: 'Dowiedz się, jak używać języka F # za pomocą programu Visual Studio.'
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799702"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="03c07-103">Wprowadzenie do F # w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03c07-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="03c07-104">Język F # i narzędzi Visual F # są obsługiwane w środowisku IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03c07-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="03c07-105">Aby rozpocząć, upewnij się, że [programu Visual Studio z F #](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="03c07-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="03c07-106">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="03c07-106">Creating a console application</span></span>

<span data-ttu-id="03c07-107">Jednym z najprostszych projektów w programie Visual Studio jest aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="03c07-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="03c07-108">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="03c07-108">Here's how to do it.</span></span>  <span data-ttu-id="03c07-109">Po otwarciu programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="03c07-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="03c07-110">Na **pliku** menu wskaż **New**, a następnie wybierz **projektu**.</span><span class="sxs-lookup"><span data-stu-id="03c07-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="03c07-111">W nowym projekcie okno dialogowe, w obszarze **szablony**, powinien zostać wyświetlony **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="03c07-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="03c07-112">Wybierz tę opcję, aby wyświetlić szablony języka F #.</span><span class="sxs-lookup"><span data-stu-id="03c07-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="03c07-113">Wybierz opcję **.NET Core w aplikacji Konsolowej** lub **aplikacja Konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="03c07-113">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="03c07-114">Wybierz **OK** przycisk, aby utworzyć projekt języka F #!</span><span class="sxs-lookup"><span data-stu-id="03c07-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="03c07-115">Powinien zostać wyświetlony projektu języka F # w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="03c07-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="03c07-116">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="03c07-116">Writing your code</span></span>

<span data-ttu-id="03c07-117">Zacznijmy napisanie kodu.</span><span class="sxs-lookup"><span data-stu-id="03c07-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="03c07-118">Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="03c07-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="03c07-119">W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje dane wejściowe o nazwie `x` i mnożona przez siebie.</span><span class="sxs-lookup"><span data-stu-id="03c07-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="03c07-120">Ponieważ F # używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.</span><span class="sxs-lookup"><span data-stu-id="03c07-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="03c07-121">Kompilator F # rozumie typów, gdzie mnożenie jest nieprawidłowy i spowoduje przypisanie typu `x` zależnie od `square` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="03c07-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="03c07-122">Po umieszczeniu wskaźnika myszy nad `square`, powinny pojawić się następujące:</span><span class="sxs-lookup"><span data-stu-id="03c07-122">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="03c07-123">Jest to, co jest nazywane podpisu typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="03c07-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="03c07-124">Może zostać odczytany następująco: "kwadratu jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".</span><span class="sxs-lookup"><span data-stu-id="03c07-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="03c07-125">Należy zauważyć, że kompilator nadaje `square` `int` typu teraz — jest to spowodowane mnożenie nie jest ogólna między *wszystkich* typów, ale raczej jest ogólny w zestawie zamknięte typy.</span><span class="sxs-lookup"><span data-stu-id="03c07-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="03c07-126">Kompilator F # pobrane `int` tej punkt, ale skoryguje sygnatura typu Jeśli wywołasz `square` przy użyciu innego typu danych wejściowych, takich jak `float`.</span><span class="sxs-lookup"><span data-stu-id="03c07-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="03c07-127">Inną funkcję, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, aby poinformować kompilator F # wykonanie tego programu.</span><span class="sxs-lookup"><span data-stu-id="03c07-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="03c07-128">Jest zgodna z tej samej Konwencji co inne [języków programowania stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazywane do tej funkcji i zostanie zwrócony kod liczby całkowitej (zazwyczaj `0`).</span><span class="sxs-lookup"><span data-stu-id="03c07-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="03c07-129">Znajduje się w tej funkcji, które nazywamy `square` funkcji z argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="03c07-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="03c07-130">Kompilator F # następnie przypisuje typ `square` jako `int -> int` (oznacza to, że funkcja, która przyjmuje `int` i tworzy `int`).</span><span class="sxs-lookup"><span data-stu-id="03c07-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="03c07-131">Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobny do języków programowania w stylu języka C, parametry, które odnoszą się do tych określonych w ciągu formatu, a następnie drukuje wyniki i nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="03c07-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="03c07-132">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="03c07-132">Running your code</span></span>

<span data-ttu-id="03c07-133">Można uruchomić kod i wyświetlić wyniki, naciskając klawisz **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="03c07-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="03c07-134">To uruchamia program bez debugowania i pozwala wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="03c07-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="03c07-135">Alternatywnie można wybrać **debugowania** menu najwyższego poziomu elementu w programie Visual Studio i wybierz polecenie **Rozpocznij bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="03c07-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="03c07-136">Powinien zostać wyświetlony wypisywane w oknie konsoli programu Visual Studio pojawiające się następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="03c07-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="03c07-137">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="03c07-137">Congratulations!</span></span>  <span data-ttu-id="03c07-138">Utworzeniu pierwszego projektu F # w programie Visual Studio, napisane, że funkcja języka F # drukowany wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.</span><span class="sxs-lookup"><span data-stu-id="03c07-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="03c07-139">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="03c07-139">Next steps</span></span>

<span data-ttu-id="03c07-140">Jeśli jeszcze nie, zapoznaj się z [samouczek programu F #](../tour.md), które obejmują niektóre z podstawowych funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="03c07-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="03c07-141">Spowoduje przedstawienie niektórych funkcji języka F # i udostępnić przykłady kodu wystarczającą, które można skopiować do programu Visual Studio i uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="03c07-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="03c07-142">Dostępne są także kilka wspaniałych zasobów zewnętrznych, można użyć, pokazywane w [Podręcznik języka F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="03c07-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03c07-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03c07-143">See also</span></span>

- [<span data-ttu-id="03c07-144">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="03c07-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="03c07-145">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="03c07-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="03c07-146">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="03c07-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="03c07-147">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="03c07-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
