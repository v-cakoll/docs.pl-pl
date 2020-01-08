---
title: Wprowadzenie F# do programu Visual Studio
description: Dowiedz się, F# jak korzystać z programu Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337348"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="4f672-103">Wprowadzenie F# do programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4f672-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="4f672-104">F#narzędzia wizualne F# są obsługiwane w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f672-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="4f672-105">Aby rozpocząć, upewnij się, że masz [zainstalowany program Visual F# Studio z obsługą techniczną](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4f672-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4f672-106">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="4f672-106">Create a console application</span></span>

<span data-ttu-id="4f672-107">Jednym z najpopularniejszych projektów w programie Visual Studio jest Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="4f672-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="4f672-108">Oto jak utworzyć:</span><span class="sxs-lookup"><span data-stu-id="4f672-108">Here's how to create one:</span></span>

1. <span data-ttu-id="4f672-109">Open Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="4f672-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="4f672-110">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="4f672-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="4f672-111">Na stronie **Tworzenie nowego projektu** wybierz **F#** z listy język.</span><span class="sxs-lookup"><span data-stu-id="4f672-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="4f672-112">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="4f672-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="4f672-113">Na stronie **Konfiguruj nowy projekt** wprowadź nazwę w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="4f672-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="4f672-114">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="4f672-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="4f672-115">Program Visual Studio tworzy nowy F# projekt.</span><span class="sxs-lookup"><span data-stu-id="4f672-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="4f672-116">Można go wyświetlić w oknie Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="4f672-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="4f672-117">Tworzenie kodu</span><span class="sxs-lookup"><span data-stu-id="4f672-117">Write the code</span></span>

<span data-ttu-id="4f672-118">Zacznijmy od pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="4f672-118">Let's get started by writing some code.</span></span> <span data-ttu-id="4f672-119">Upewnij się, że plik `Program.fs` jest otwarty, a następnie zastąp jego zawartość następującym:</span><span class="sxs-lookup"><span data-stu-id="4f672-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="4f672-120">Poprzedni przykład kodu definiuje funkcję o nazwie `square`, która przyjmuje dane wejściowe o nazwie `x` i mnoży ją przez siebie.</span><span class="sxs-lookup"><span data-stu-id="4f672-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="4f672-121">Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), nie trzeba określać typu `x`.</span><span class="sxs-lookup"><span data-stu-id="4f672-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="4f672-122">F# Kompilator rozumie typy, w których mnożenie jest prawidłowe, i przypisuje typ do `x` w zależności od tego, jak `square` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4f672-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="4f672-123">Po umieszczeniu wskaźnika myszy na `square`należy zobaczyć następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="4f672-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="4f672-124">Jest to element znany jako podpis typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f672-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="4f672-125">Można go odczytać w następujący sposób: "kwadrat jest funkcją, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą".</span><span class="sxs-lookup"><span data-stu-id="4f672-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="4f672-126">Kompilator nadał teraz `square` typ `int`; wynika to z faktu, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej do zamkniętego zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="4f672-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="4f672-127">F# Kompilator dostosowuje podpis typu w przypadku wywołania `square` z innym typem danych wejściowych, takim jak `float`.</span><span class="sxs-lookup"><span data-stu-id="4f672-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="4f672-128">Inna funkcja, `main`, jest zdefiniowana z atrybutem `EntryPoint`.</span><span class="sxs-lookup"><span data-stu-id="4f672-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="4f672-129">Ten atrybut informuje kompilator F# , że wykonanie programu powinno zacząć się w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4f672-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="4f672-130">Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zwykle `0`).</span><span class="sxs-lookup"><span data-stu-id="4f672-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="4f672-131">Znajduje się w funkcji punktu wejścia, `main`, że wywoływana jest funkcja `square` z argumentem `12`.</span><span class="sxs-lookup"><span data-stu-id="4f672-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="4f672-132">Następnie F# kompilator przypisuje typ `square` do `int -> int` (to jest funkcja, która pobiera `int` i tworzy `int`).</span><span class="sxs-lookup"><span data-stu-id="4f672-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="4f672-133">Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu i drukuje wynik (i nowy wiersz).</span><span class="sxs-lookup"><span data-stu-id="4f672-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="4f672-134">Ciąg formatu, podobny do języków programowania w stylu C, ma parametry (`%d`) odpowiadające argumentom, które są do niego przekazane, w tym przypadku `12` i `(square 12)`.</span><span class="sxs-lookup"><span data-stu-id="4f672-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="4f672-135">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="4f672-135">Run the code</span></span>

<span data-ttu-id="4f672-136">Możesz uruchomić kod i zobaczyć wyniki, naciskając klawisz **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="4f672-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="4f672-137">Alternatywnie można wybrać **debugowanie** > **rozpocząć bez debugowania** z paska menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4f672-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="4f672-138">Spowoduje to uruchomienie programu bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="4f672-138">This runs the program without debugging.</span></span>

<span data-ttu-id="4f672-139">Następujące dane wyjściowe są drukowane do okna konsoli, który został otwarty przez program Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4f672-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="4f672-140">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="4f672-140">Congratulations!</span></span> <span data-ttu-id="4f672-141">Utworzono pierwszy F# projekt w programie Visual Studio, zapisał F# funkcję, która oblicza i drukuje wartość i uruchamia projekt, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="4f672-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f672-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4f672-142">Next steps</span></span>

<span data-ttu-id="4f672-143">Jeśli jeszcze tego nie zrobiono, zapoznaj się [ F#z przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka.</span><span class="sxs-lookup"><span data-stu-id="4f672-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="4f672-144">Zawiera przegląd niektórych możliwości F# i większość przykładów kodu, które można skopiować do programu Visual Studio i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="4f672-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f672-145">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="4f672-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="4f672-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f672-146">See also</span></span>

- [<span data-ttu-id="4f672-147">F#Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="4f672-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="4f672-148">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="4f672-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="4f672-149">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="4f672-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
