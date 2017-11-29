---
title: Metody (F#)
description: "Dowiedz się, jak metoda F # jest skojarzony z typem służą do ujawnia i implementuje funkcje i zachowanie obiektów i typów funkcji."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a><span data-ttu-id="244d2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="244d2-104">Methods</span></span>

<span data-ttu-id="244d2-105">A *metody* to funkcja, która jest skojarzona z typem.</span><span class="sxs-lookup"><span data-stu-id="244d2-105">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="244d2-106">W programowanie zorientowane obiektowo metody są używane ujawnia i wdrażanie funkcji oraz zachowanie obiektów i typów.</span><span class="sxs-lookup"><span data-stu-id="244d2-106">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="244d2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="244d2-107">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="244d2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="244d2-108">Remarks</span></span>
<span data-ttu-id="244d2-109">W poprzednich składni widać różne formy — metoda deklaracje i definicje.</span><span class="sxs-lookup"><span data-stu-id="244d2-109">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="244d2-110">W treści metody dłużej podział wiersza następuje znak równości (=) i tworzone jest wcięcie całej treści.</span><span class="sxs-lookup"><span data-stu-id="244d2-110">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="244d2-111">Atrybuty można zastosować do dowolnego deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-111">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="244d2-112">One poprzedzać składnia definicję metody i zazwyczaj są wyświetlane w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="244d2-112">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="244d2-113">Aby uzyskać więcej informacji, zobacz [atrybutów](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="244d2-113">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="244d2-114">Można oznaczyć metody `inline`.</span><span class="sxs-lookup"><span data-stu-id="244d2-114">Methods can be marked `inline`.</span></span> <span data-ttu-id="244d2-115">Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="244d2-115">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="244d2-116">Inne niż wbudowane metody mogą być używane rekursywnie w ramach typu; nie istnieje potrzeba aby jawnie używać `rec` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="244d2-116">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="244d2-117">Wystąpienie metody</span><span class="sxs-lookup"><span data-stu-id="244d2-117">Instance Methods</span></span>
<span data-ttu-id="244d2-118">Metody wystąpienia są deklarowane jako z `member` — słowo kluczowe i *własny identyfikator*, a następnie kropki (.) oraz nazwę metody i parametry.</span><span class="sxs-lookup"><span data-stu-id="244d2-118">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="244d2-119">Podobnie jak w przypadku dla `let` powiązań, *listy parametrów* może być wzorcem.</span><span class="sxs-lookup"><span data-stu-id="244d2-119">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="244d2-120">Zwykle to ująć metodę, której parametry w nawiasach w postaci spójnej kolekcji, czyli metody sposób są wyświetlane w języku F # tworzona w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="244d2-120">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="244d2-121">Jednak rozwinięte formularza (rozdzielone spacjami parametry) jest również typowe i innymi wzorami są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="244d2-121">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="244d2-122">Poniższy przykład przedstawia definicja oraz wykorzystanie metody wystąpienia nieabstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="244d2-122">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="244d2-123">Wewnątrz metody wystąpienia nie należy używać własnego identyfikatora do pola dostępu zdefiniowane za pomocą powiązania let.</span><span class="sxs-lookup"><span data-stu-id="244d2-123">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="244d2-124">Użyć własnego identyfikatora podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.</span><span class="sxs-lookup"><span data-stu-id="244d2-124">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="244d2-125">Metody statyczne</span><span class="sxs-lookup"><span data-stu-id="244d2-125">Static Methods</span></span>
<span data-ttu-id="244d2-126">Słowo kluczowe `static` służy do określania, czy można wywołać metody bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="244d2-126">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="244d2-127">W przeciwnym razie metody to metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="244d2-127">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="244d2-128">W przykładzie w następnej sekcji przedstawiono pola zadeklarowana z `let` — słowo kluczowe, właściwości elementów członkowskich zadeklarowanych za pomocą `member` — słowo kluczowe i metody statycznej zadeklarowana z `static` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="244d2-128">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="244d2-129">Poniższy przykład przedstawia definicję i korzystanie z metod statycznych.</span><span class="sxs-lookup"><span data-stu-id="244d2-129">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="244d2-130">Załóżmy, że te metody definicje znajdują się w `SomeType` klasy w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="244d2-130">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="244d2-131">Metody abstrakcyjna i wirtualna</span><span class="sxs-lookup"><span data-stu-id="244d2-131">Abstract and Virtual Methods</span></span>
<span data-ttu-id="244d2-132">Słowo kluczowe `abstract` wskazuje metodę miejsca wysyłania wirtualnego i nie może mieć definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="244d2-132">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="244d2-133">A *miejsca wysyłania wirtualnego* jest odwołuje się do wpisu w tabeli obsługiwanej wewnętrznie funkcji używany w czasie wykonywania do odszukania funkcji wirtualnej zorientowane obiektowo typu.</span><span class="sxs-lookup"><span data-stu-id="244d2-133">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="244d2-134">Mechanizm wysyłania wirtualnego jest mechanizm, który implementuje *polimorfizm*, ważna cecha programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="244d2-134">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="244d2-135">Klasa, która ma co najmniej jednej metody abstrakcyjnej bez definicji jest *klasy abstrakcyjnej*, co oznacza, że nie można utworzyć jego wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="244d2-135">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="244d2-136">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klas abstrakcyjnych](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="244d2-136">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="244d2-137">Deklaracje metody abstrakcyjnej nie zawierają treści metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-137">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="244d2-138">Zamiast tego nazwę metody następuje dwukropkiem (:) i podpis typu metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-138">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="244d2-139">Podpis typu metody jest taka sama, jak te wyświetlane przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwę metody w Visual Studio edytorze kodu, z wyjątkiem bez nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="244d2-139">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="244d2-140">Typ podpisy są również wyświetlane przez interpretera fsi.exe, podczas pracy w trybie interakcyjnym.</span><span class="sxs-lookup"><span data-stu-id="244d2-140">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="244d2-141">Podpis typu metody jest tworzony przez listę się typami parametrów, następuje typ zwracany przy użyciu odpowiednich separatora symboli.</span><span class="sxs-lookup"><span data-stu-id="244d2-141">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="244d2-142">Rozwinięte parametry są oddzielone `->` i spójnej kolekcji parametry są oddzielone `*`.</span><span class="sxs-lookup"><span data-stu-id="244d2-142">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="244d2-143">Zwracana wartość jest zawsze oddzielony od argumenty `->` symbolu.</span><span class="sxs-lookup"><span data-stu-id="244d2-143">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="244d2-144">Nawiasy może służyć do grupowania złożonych parametrów, na przykład gdy typ funkcji jest parametrem, lub aby wskazać, kiedy Krotka jest traktowany jako jeden parametr, a nie dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="244d2-144">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="244d2-145">Definicje domyślne metody abstrakcyjne mogą również dawać przez dodanie definicji klasy i przy użyciu `default` — słowo kluczowe, jak pokazano w bloku składni, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="244d2-145">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="244d2-146">Metoda abstrakcyjna o definicję w tej samej klasy jest odpowiednikiem wirtualnej metody w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="244d2-146">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="244d2-147">Określa, czy istnieje definicja `abstract` — słowo kluczowe tworzy nowe miejsce wysyłania w tabeli funkcji wirtualnych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="244d2-147">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="244d2-148">Niezależnie od tego, czy klasa podstawowa implementuje jego metody abstrakcyjne klas pochodnych może dostarczyć implementacje metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="244d2-148">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="244d2-149">Aby zaimplementować metoda abstrakcyjna w klasie pochodnej, zdefiniuj metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` lub `default` — słowo kluczowe i podaj treści metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-149">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="244d2-150">Słowa kluczowe `override` i `default` oznacza dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="244d2-150">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="244d2-151">Użyj `override` Jeśli nowa metoda zastępuje implementację klasy podstawowej; użyj `default` podczas tworzenia wdrożenia w tej samej klasy jako oryginalnej deklaracji abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="244d2-151">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="244d2-152">Nie używaj `abstract` — słowo kluczowe dla metody, która implementuje metodę, która została zadeklarowana jako abstrakcyjna w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="244d2-152">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="244d2-153">Poniższy przykład przedstawia metody abstrakcyjnej `Rotate` mający Domyślna implementacja odpowiednikiem metody wirtualnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="244d2-153">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="244d2-154">Poniższy przykład przedstawia klasy pochodnej, która zastępuje metodę klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="244d2-154">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="244d2-155">W takim przypadku zastąpienie zmienia zachowanie tak, aby metody nie działają.</span><span class="sxs-lookup"><span data-stu-id="244d2-155">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="244d2-156">Metody przeciążane</span><span class="sxs-lookup"><span data-stu-id="244d2-156">Overloaded Methods</span></span>
<span data-ttu-id="244d2-157">Przeciążone metody są metody, które mają identyczne nazwy w danym typie, ale mają różne argumentów.</span><span class="sxs-lookup"><span data-stu-id="244d2-157">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="244d2-158">W F # Argumenty opcjonalne są zazwyczaj używane zamiast przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-158">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="244d2-159">Jednak przeciążonej metody są dozwolone w języku, pod warunkiem, że argumenty są w postaci spójnej kolekcji, nie rozwinięte formularza.</span><span class="sxs-lookup"><span data-stu-id="244d2-159">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="244d2-160">Argumenty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="244d2-160">Optional Arguments</span></span>

<span data-ttu-id="244d2-161">Począwszy od 4.1 F #, może także zawierać Argumenty opcjonalne, wartość domyślna parametru metody.</span><span class="sxs-lookup"><span data-stu-id="244d2-161">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="244d2-162">To, aby ułatwić współdziałanie z kodem C#.</span><span class="sxs-lookup"><span data-stu-id="244d2-162">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="244d2-163">Poniższy przykład przedstawia składnię:</span><span class="sxs-lookup"><span data-stu-id="244d2-163">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="244d2-164">Należy pamiętać, że wartość przekazana dla `DefaultParameterValue` musi być zgodny typ danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="244d2-164">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="244d2-165">W powyższym przykładzie jest `int`.</span><span class="sxs-lookup"><span data-stu-id="244d2-165">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="244d2-166">Próba przekazania wartość nie jest liczbą całkowitą w `DefaultParameterValue` spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="244d2-166">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="244d2-167">Przykład: Właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="244d2-167">Example: Properties and Methods</span></span>
<span data-ttu-id="244d2-168">Poniższy przykład zawiera typ, który zawiera przykłady pola, prywatnej funkcji, właściwości i metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="244d2-168">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="244d2-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="244d2-169">See Also</span></span>
[<span data-ttu-id="244d2-170">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="244d2-170">Members</span></span>](index.md)
