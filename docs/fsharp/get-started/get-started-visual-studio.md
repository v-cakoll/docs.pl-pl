---
title: Wprowadzenie F# do programu Visual Studio
description: Dowiedz się, F# jak korzystać z programu Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629767"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="7b980-103">Wprowadzenie F# do programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b980-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="7b980-104">F#narzędzia wizualne F# są obsługiwane w środowisku IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b980-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="7b980-105">Aby rozpocząć, upewnij się, że masz [zainstalowany program Visual F#Studio z programem ](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7b980-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="7b980-106">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="7b980-106">Creating a console application</span></span>

<span data-ttu-id="7b980-107">Jednym z najpopularniejszych projektów w programie Visual Studio jest Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="7b980-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="7b980-108">Oto jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7b980-108">Here's how to do it.</span></span>  <span data-ttu-id="7b980-109">Po otwarciu programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="7b980-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="7b980-110">W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz **projekt**.</span><span class="sxs-lookup"><span data-stu-id="7b980-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="7b980-111">W oknie dialogowym Nowy projekt w obszarze **Szablony**powinna zostać wyświetlona wartość **Visual F#** .</span><span class="sxs-lookup"><span data-stu-id="7b980-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="7b980-112">Wybierz tę opcję, aby F# wyświetlić szablony.</span><span class="sxs-lookup"><span data-stu-id="7b980-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="7b980-113">Wybierz **aplikację konsolową .NET Core** lub **aplikację konsolową**.</span><span class="sxs-lookup"><span data-stu-id="7b980-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="7b980-114">Wybierz przycisk **OK** , aby utworzyć F# projekt.</span><span class="sxs-lookup"><span data-stu-id="7b980-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="7b980-115">Powinien być teraz widoczny F# projekt w Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="7b980-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="7b980-116">Pisanie kodu</span><span class="sxs-lookup"><span data-stu-id="7b980-116">Writing your code</span></span>

<span data-ttu-id="7b980-117">Zacznijmy od zapisania najpierw kodu.</span><span class="sxs-lookup"><span data-stu-id="7b980-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="7b980-118">Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym:</span><span class="sxs-lookup"><span data-stu-id="7b980-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="7b980-119">W poprzednim przykładzie kodu zdefiniowano funkcję `square` , która przyjmuje `x` dane wejściowe i mnoży ją przez siebie.</span><span class="sxs-lookup"><span data-stu-id="7b980-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="7b980-120">Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), `x` nie trzeba określać typu.</span><span class="sxs-lookup"><span data-stu-id="7b980-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="7b980-121">F# Kompilator rozumie typy, w których mnożenie jest prawidłowe i przypisuje typ `x` na podstawie sposobu wywoływania metody `square` .</span><span class="sxs-lookup"><span data-stu-id="7b980-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="7b980-122">Po umieszczeniu wskaźnika myszy `square`na stronie powinny zostać wyświetlone następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7b980-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="7b980-123">Jest to element znany jako podpis typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b980-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="7b980-124">Można go odczytać w następujący sposób: "Square to funkcja, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą".</span><span class="sxs-lookup"><span data-stu-id="7b980-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="7b980-125">Należy zauważyć, że kompilator `square` nadał `int` teraz typ. jest to spowodowane tym, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej jest ogólny w przypadku zamkniętego zestawu typów.</span><span class="sxs-lookup"><span data-stu-id="7b980-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="7b980-126">F# Kompilator jest wybierany `int` w tym momencie, ale dopasowuje podpis typu w przypadku wywołania `square` z `float`innym typem danych wejściowych, na przykład.</span><span class="sxs-lookup"><span data-stu-id="7b980-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="7b980-127">Inna funkcja `main`,,, jest zdefiniowana `EntryPoint` z atrybutem, aby poinformować F# kompilator, że wykonanie programu powinno się uruchomić w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="7b980-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="7b980-128">Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zazwyczaj `0`).</span><span class="sxs-lookup"><span data-stu-id="7b980-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="7b980-129">Jest to funkcja, która wywołuje `square` funkcję z `12`argumentem.</span><span class="sxs-lookup"><span data-stu-id="7b980-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="7b980-130">Następnie F# `square` kompilator przypisuje typ do `int -> int` (czyli `int`funkcję, która przyjmuje `int` i tworzy).</span><span class="sxs-lookup"><span data-stu-id="7b980-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="7b980-131">Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu, podobnego do języków programowania w stylu C, parametrów, które odpowiadają określonym w ciągu formatu, a następnie drukuje wynik i nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="7b980-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="7b980-132">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="7b980-132">Running your code</span></span>

<span data-ttu-id="7b980-133">Możesz uruchomić kod i zobaczyć wyniki, naciskając klawisz **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="7b980-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="7b980-134">Spowoduje to uruchomienie programu bez debugowania i pozwala zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="7b980-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="7b980-135">Alternatywnie możesz wybrać element menu **najwyższego** poziomu w programie Visual Studio i wybrać polecenie **Uruchom bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="7b980-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="7b980-136">W oknie konsoli programu Visual Studio należy teraz zobaczyć następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7b980-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="7b980-137">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="7b980-137">Congratulations!</span></span>  <span data-ttu-id="7b980-138">Został utworzony pierwszy F# projekt w programie Visual Studio, a F# funkcja zapisała wyniki wywołania tej funkcji i uruchomi projekt, aby zobaczyć niektóre wyniki.</span><span class="sxs-lookup"><span data-stu-id="7b980-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7b980-139">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7b980-139">Next steps</span></span>

<span data-ttu-id="7b980-140">Jeśli jeszcze tego nie zrobiono, zapoznaj się [z F#przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka.</span><span class="sxs-lookup"><span data-stu-id="7b980-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="7b980-141">Udostępnimy przegląd niektórych możliwości programu F#i udostępniamy dużo przykładów kodu, które można skopiować do programu Visual Studio i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="7b980-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="7b980-142">Istnieją również pewne doskonałe zasoby zewnętrzne, których można użyć w [ F# przewodniku](../index.md).</span><span class="sxs-lookup"><span data-stu-id="7b980-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b980-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b980-143">See also</span></span>

- [<span data-ttu-id="7b980-144">Przewodnik po F#</span><span class="sxs-lookup"><span data-stu-id="7b980-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="7b980-145">F#Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="7b980-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="7b980-146">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="7b980-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="7b980-147">Odwołanie do symbolu i operatora</span><span class="sxs-lookup"><span data-stu-id="7b980-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
