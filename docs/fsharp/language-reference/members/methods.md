---
title: Metody (F#)
description: 'Dowiedz się, jak metoda F # jest skojarzony z typem, które są używane do udostępnienia i wdrażaniu funkcji i zachowanie obiektów i typy funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 02d5a7d22d1ce79a06e15462637c373b33623f61
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44253211"
---
# <a name="methods"></a><span data-ttu-id="f9604-103">Metody</span><span class="sxs-lookup"><span data-stu-id="f9604-103">Methods</span></span>

<span data-ttu-id="f9604-104">A *metoda* jest funkcją, która jest skojarzona z typem.</span><span class="sxs-lookup"><span data-stu-id="f9604-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="f9604-105">W programowanie zorientowane obiektowo metody są używane do udostępnienia i wdrażaniu funkcji i zachowanie obiektów i typy.</span><span class="sxs-lookup"><span data-stu-id="f9604-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9604-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9604-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="f9604-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9604-107">Remarks</span></span>

<span data-ttu-id="f9604-108">W poprzedniej składni można zobaczyć różne rodzaje definicje i deklaracje metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="f9604-109">W treści metod dłużej podział wiersza następuje znak równości (=) i tworzone jest wcięcie treści całej metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="f9604-110">Atrybuty można zastosować do dowolnego deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="f9604-111">One poprzedzać Składnia definicji metody i zazwyczaj są wyświetlane w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f9604-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="f9604-112">Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f9604-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="f9604-113">Można oznaczyć metody `inline`.</span><span class="sxs-lookup"><span data-stu-id="f9604-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="f9604-114">Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f9604-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="f9604-115">Inne niż wbudowane metody mogą być używane cyklicznie w ramach typu; nie trzeba jawnie użyć `rec` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f9604-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="f9604-116">Metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="f9604-116">Instance Methods</span></span>

<span data-ttu-id="f9604-117">Metody wystąpienia są uznane za pomocą `member` — słowo kluczowe i *własny identyfikator*, a następnie kropka (.) i nazwy metody i parametrów.</span><span class="sxs-lookup"><span data-stu-id="f9604-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="f9604-118">Podobnie jak w przypadku dla `let` powiązań *listy parametrów* może być wzorca.</span><span class="sxs-lookup"><span data-stu-id="f9604-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="f9604-119">Zazwyczaj uwzględnisz metodę, której parametry w nawiasach w formularzu krotki, czyli metody sposób są wyświetlane w języku F #, gdy są one tworzone w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9604-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="f9604-120">Rozwinięte formularza (rozdzielone spacjami parametry) jest również typowe i inne wzorce są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9604-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="f9604-121">Poniższy przykład ilustruje definicja oraz wykorzystanie metody wystąpienia nieabstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="f9604-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="f9604-122">W ramach metody wystąpienia nie należy używać własny identyfikator do dostępu do pola zdefiniowane przy użyciu powiązania let.</span><span class="sxs-lookup"><span data-stu-id="f9604-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="f9604-123">Użyj identyfikatora samodzielnie, podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9604-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="f9604-124">Metody statyczne</span><span class="sxs-lookup"><span data-stu-id="f9604-124">Static Methods</span></span>

<span data-ttu-id="f9604-125">Słowo kluczowe `static` służy do określania, czy metoda może być wywołana bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9604-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="f9604-126">W przeciwnym razie przedstawiono metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f9604-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="f9604-127">W przykładzie w następnej sekcji przedstawiono zadeklarowane za pomocą pola `let` właściwości elementów członkowskich zadeklarowanych za pomocą słowa kluczowego, `member` — słowo kluczowe, a metoda statyczna zadeklarowana za pomocą `static` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f9604-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="f9604-128">Poniższy przykład ilustruje definicja oraz wykorzystanie metody statyczne.</span><span class="sxs-lookup"><span data-stu-id="f9604-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="f9604-129">Przyjęto założenie, że te definicje metod znajdują się w `SomeType` klasy w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f9604-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="f9604-130">Metody abstrakcyjne i wirtualnych</span><span class="sxs-lookup"><span data-stu-id="f9604-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="f9604-131">Słowo kluczowe `abstract` wskazuje, że metoda ma miejsce wysyłania wirtualnego i nie może mieć definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="f9604-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="f9604-132">A *wysyłania wirtualnego miejsca* to wpis w obsługiwanej wewnętrznie tabeli funkcji używane w czasie wykonywania, aby wyszukać funkcji wirtualnej wywołuje typu zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="f9604-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="f9604-133">Mechanizm wysyłania wirtualnej to mechanizm, który implementuje *polimorfizm*, ważną funkcją programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="f9604-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="f9604-134">Jest klasą, która ma co najmniej jedną metodę abstrakcyjną bez definicji *abstrakcyjna klasa*, co oznacza, że nie można utworzyć jego wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f9604-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="f9604-135">Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [klasy abstrakcyjne](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="f9604-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="f9604-136">Deklaracje metody abstrakcyjnej nie zawierają treści metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="f9604-137">Zamiast tego nazwę metody następuje dwukropek (:) i typ podpisu dla metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="f9604-138">Sygnatura typu metody jest taka sama, jak pokazano w przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwy metody w edytorze programu Visual Studio Code z wyjątkiem bez nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f9604-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="f9604-139">Podpisy typu są również wyświetlane przez interpretera fsi.exe podczas pracy w interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="f9604-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="f9604-140">Sygnatura typu metody jest tworzony przez listę się typy parametrów, następuje zwracany typ, a symbole separatorów odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="f9604-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="f9604-141">Rozwinięte parametry są rozdzielane `->` i krotki parametry są rozdzielane `*`.</span><span class="sxs-lookup"><span data-stu-id="f9604-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="f9604-142">Wartość zwracana zawsze jest oddzielony od argumentów przez `->` symboli.</span><span class="sxs-lookup"><span data-stu-id="f9604-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="f9604-143">Nawiasów może służyć do grupowania złożonych parametrów, na przykład gdy typ funkcji jest parametr, lub, aby wskazać, kiedy krotki jest traktowany jako jeden parametr, a nie jako dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="f9604-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="f9604-144">Definicje domyślne metody abstrakcyjne mogą również dawać przez dodanie definicji klasy i za pomocą `default` — słowo kluczowe, jak pokazano w bloku składni, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f9604-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="f9604-145">Metoda abstrakcyjna, który zawiera definicję w tej samej klasie jest odpowiednikiem wirtualnej metody w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9604-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="f9604-146">Określa, czy definicja istnieje, `abstract` — słowo kluczowe tworzy nowe gniazdo wysyłania w tabeli funkcji wirtualnych dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f9604-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="f9604-147">Niezależnie od tego, czy klasa bazowa implementuje jego metody abstrakcyjne klasach pochodnych można podać implementacji metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="f9604-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="f9604-148">Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, należy zdefiniować metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` lub `default` — słowo kluczowe i podaj treści metody.</span><span class="sxs-lookup"><span data-stu-id="f9604-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="f9604-149">Słowa kluczowe `override` i `default` oznacza dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="f9604-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="f9604-150">Użyj `override` Jeśli nowa metoda zastępuje implementacji klasy podstawowej; użyj `default` podczas tworzenia implementacji w tej samej klasy jako abstrakcyjnej pierwotnej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f9604-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="f9604-151">Nie używaj `abstract` — słowo kluczowe w metodzie, która implementuje metodę, która został zadeklarowany jako abstrakcyjny w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="f9604-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="f9604-152">W poniższym przykładzie pokazano metodę abstrakcyjną `Rotate` zawierający implementacji domyślnej, odpowiednik metody wirtualnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9604-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="f9604-153">Poniższy przykład ilustruje klasę pochodną, która zastępuje metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="f9604-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="f9604-154">W tym przypadku zastąpienie zmienia zachowanie, tak aby nie robi nic, metoda.</span><span class="sxs-lookup"><span data-stu-id="f9604-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="f9604-155">Przeciążone metody</span><span class="sxs-lookup"><span data-stu-id="f9604-155">Overloaded Methods</span></span>

<span data-ttu-id="f9604-156">Przeciążone metody są metody, które mają identyczne nazwy w danego typu, ale mają różnymi argumentami.</span><span class="sxs-lookup"><span data-stu-id="f9604-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="f9604-157">W języku F # Argumenty opcjonalne są zwykle używane zamiast przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="f9604-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="f9604-158">Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty znajdują się w formularzu krotki i nie rozwinięte formularza.</span><span class="sxs-lookup"><span data-stu-id="f9604-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="f9604-159">Argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f9604-159">Optional Arguments</span></span>

<span data-ttu-id="f9604-160">Począwszy od F # 4.1, również masz Argumenty opcjonalne z wartością domyślną parametru za pomocą metod.</span><span class="sxs-lookup"><span data-stu-id="f9604-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="f9604-161">To, aby ułatwić współdziałanie z kodem C#.</span><span class="sxs-lookup"><span data-stu-id="f9604-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="f9604-162">Poniższy przykład pokazuje składnię:</span><span class="sxs-lookup"><span data-stu-id="f9604-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="f9604-163">Należy zauważyć, że wartość przekazywana w dla `DefaultParameterValue` musi odpowiadać typowi danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f9604-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="f9604-164">W powyższym przykładzie jest `int`.</span><span class="sxs-lookup"><span data-stu-id="f9604-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="f9604-165">Próba przekazania wartości niebędące liczbami całkowitymi, do `DefaultParameterValue` mogłoby spowodować błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9604-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="f9604-166">Przykład: Właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="f9604-166">Example: Properties and Methods</span></span>

<span data-ttu-id="f9604-167">Poniższy przykład zawiera typ, który zawiera przykłady pola, prywatne funkcje, właściwości i metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="f9604-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="f9604-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9604-168">See also</span></span>

- [<span data-ttu-id="f9604-169">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f9604-169">Members</span></span>](index.md)
