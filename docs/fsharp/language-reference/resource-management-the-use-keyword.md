---
title: "Zarządzanie zasobami: use — Słowo kluczowe (F#)"
description: "Więcej informacji na temat języka F # — słowo kluczowe \"use\" i \"przy użyciu\" funkcji, która może kontrolować inicjowania i zwolnienia zasobów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="b02f9-104">Zarządzanie zasobami: use — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="b02f9-104">Resource Management: The use Keyword</span></span>

<span data-ttu-id="b02f9-105">W tym temacie opisano kluczowego `use` i `using` funkcji, która może kontrolować inicjowania i zwolnienia zasobów.</span><span class="sxs-lookup"><span data-stu-id="b02f9-105">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="b02f9-106">Resources</span><span class="sxs-lookup"><span data-stu-id="b02f9-106">Resources</span></span>
<span data-ttu-id="b02f9-107">Termin *zasobów* są używane w więcej niż jeden sposób.</span><span class="sxs-lookup"><span data-stu-id="b02f9-107">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="b02f9-108">Tak, zasoby mogą być danych przy użyciu aplikacji, takich jak ciągów, grafiki i podobne, ale w tym kontekście *zasobów* odwołuje się do zasobów oprogramowania lub systemu operacyjnego, takie jak konteksty urządzenia grafiki, dojścia do plików w sieci i bazy danych połączenia, współbieżności obiekty, takie jak uchwyty oczekiwania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b02f9-108">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="b02f9-109">Korzystanie z tych zasobów przez aplikacje obejmuje nabywania zasobów z system operacyjny lub inne dostawcy zasobów, a następnie w nowszej wersji zasobu do puli, dzięki czemu może zostać dostarczona do innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b02f9-109">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="b02f9-110">Problemy występują, jeśli aplikacje nie zwalnia wspólnej puli zasobów.</span><span class="sxs-lookup"><span data-stu-id="b02f9-110">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="b02f9-111">Zarządzanie zasobami</span><span class="sxs-lookup"><span data-stu-id="b02f9-111">Managing Resources</span></span>
<span data-ttu-id="b02f9-112">Aby wydajnie i odpowiedzialne zarządzać zasobami w aplikacji, należy zwolnić zasoby szybko i w sposób przewidywalny.</span><span class="sxs-lookup"><span data-stu-id="b02f9-112">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="b02f9-113">.NET Framework ułatwia to zrobić, podając `System.IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b02f9-113">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="b02f9-114">Typ, który implementuje `System.IDisposable` ma `System.IDisposable.Dispose` metodę, która poprawnie zwalnia zasoby.</span><span class="sxs-lookup"><span data-stu-id="b02f9-114">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="b02f9-115">Dobrze napisanych aplikacji zagwarantować, że `System.IDisposable.Dispose` jest wywoływana natychmiast po każdym obiekcie, który przechowuje ograniczonych zasobów nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b02f9-115">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="b02f9-116">Na szczęście większość języków .NET obsługuje ułatwić, i F # nie jest wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="b02f9-116">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="b02f9-117">Istnieją dwa konstrukcji języka przydatne, które obsługują wzorzec dispose: `use` powiązania i `using` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b02f9-117">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="b02f9-118">Użyj powiązania</span><span class="sxs-lookup"><span data-stu-id="b02f9-118">use Binding</span></span>
<span data-ttu-id="b02f9-119">`use` — Słowo kluczowe ma formę, przypominający `let` powiązania:</span><span class="sxs-lookup"><span data-stu-id="b02f9-119">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="b02f9-120">Użyj *wartość* = *wyrażenia*</span><span class="sxs-lookup"><span data-stu-id="b02f9-120">use *value* = *expression*</span></span>

<span data-ttu-id="b02f9-121">Zapewnia te same funkcje co `let` powiązania, ale dodaje wywołanie `Dispose` na wartość, jeśli wartość wykracza poza zakres.</span><span class="sxs-lookup"><span data-stu-id="b02f9-121">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="b02f9-122">Należy pamiętać, że kompilator wstawia sprawdzania wartości null dla wartości, tak, że jeśli wartość jest `null`, wywołanie `Dispose` nie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="b02f9-122">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="b02f9-123">Poniższy przykład przedstawia sposób automatycznie zamknąć plik za pomocą `use` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b02f9-123">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="b02f9-124">Można użyć `use` w wyrażeniach obliczeń, w którym to przypadku dostosowaną wersję `use` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="b02f9-124">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="b02f9-125">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b02f9-125">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="using-function"></a><span data-ttu-id="b02f9-126">przy użyciu funkcji</span><span class="sxs-lookup"><span data-stu-id="b02f9-126">using Function</span></span>
<span data-ttu-id="b02f9-127">`using` Funkcja ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="b02f9-127">The `using` function has the following form:</span></span>

<span data-ttu-id="b02f9-128">`using`(*wyrażenie1*) *funkcji lub lambda*</span><span class="sxs-lookup"><span data-stu-id="b02f9-128">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="b02f9-129">W `using` wyrażenie *wyrażenie1* tworzy obiekt, który musi zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="b02f9-129">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="b02f9-130">Wynik *wyrażenie1* (obiekt, który musi zostać usunięty) staje się argument *wartość*, do *funkcji lub lambda*, która jest funkcja, która oczekuje pojedynczy pozostały argumentu typu, która jest zgodna z wartością utworzonego przez *wyrażenie1*, lub wyrażenie lambda, które oczekuje argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="b02f9-130">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="b02f9-131">Po zakończeniu wykonywania funkcji wymaga środowiska uruchomieniowego `Dispose` i zwalnia zasoby (chyba, że wartość jest `null`, w którym to przypadku nie jest wykonywane wywołanie metody Dispose).</span><span class="sxs-lookup"><span data-stu-id="b02f9-131">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="b02f9-132">W poniższym przykładzie pokazano `using` wyrażenie za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b02f9-132">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="b02f9-133">W następnym przykładzie pokazano `using` wyrażenie przy użyciu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b02f9-133">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="b02f9-134">Należy pamiętać, że funkcja może być funkcję, która zawiera niektóre argumenty już stosowane.</span><span class="sxs-lookup"><span data-stu-id="b02f9-134">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="b02f9-135">W poniższym przykładzie kodu pokazano to.</span><span class="sxs-lookup"><span data-stu-id="b02f9-135">The following code example demonstrates this.</span></span> <span data-ttu-id="b02f9-136">Tworzy plik, który zawiera ciąg `XYZ`.</span><span class="sxs-lookup"><span data-stu-id="b02f9-136">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="b02f9-137">`using` Funkcji i `use` powiązania są prawie równoważne sposobów, aby osiągnąć ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="b02f9-137">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="b02f9-138">`using` — Słowo kluczowe zapewnia większą kontrolę nad tym, kiedy `Dispose` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b02f9-138">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="b02f9-139">Jeśli używasz `using`, `Dispose` jest wywoływane na końcu wyrażenia funkcji lub lambda, gdy używasz `use` — słowo kluczowe, `Dispose` jest wywoływana po zakończeniu zawierający go blok kodu.</span><span class="sxs-lookup"><span data-stu-id="b02f9-139">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="b02f9-140">Ogólnie rzecz biorąc, powinien wolisz użyć `use` zamiast `using` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b02f9-140">In general, you should prefer to use `use` instead of the `using` function.</span></span>


## <a name="see-also"></a><span data-ttu-id="b02f9-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b02f9-141">See Also</span></span>
[<span data-ttu-id="b02f9-142">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="b02f9-142">F# Language Reference</span></span>](index.md)
