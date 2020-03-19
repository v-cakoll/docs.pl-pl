---
title: Metody
description: Dowiedz się, jak Metoda F# jest funkcją skojarzoną z typem, które są używane do uwidaczniania i implementowania funkcji i zachowania obiektów i typów.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400212"
---
# <a name="methods"></a><span data-ttu-id="b1de3-103">Metody</span><span class="sxs-lookup"><span data-stu-id="b1de3-103">Methods</span></span>

<span data-ttu-id="b1de3-104">*Metoda* jest funkcją skojarzoną z typem.</span><span class="sxs-lookup"><span data-stu-id="b1de3-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="b1de3-105">W programowaniu obiektowym metody są używane do uwidaczniania i implementowania funkcji i zachowania obiektów i typów.</span><span class="sxs-lookup"><span data-stu-id="b1de3-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1de3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1de3-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b1de3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1de3-107">Remarks</span></span>

<span data-ttu-id="b1de3-108">W poprzedniej składni można zobaczyć różne formy deklaracji metod i definicji.</span><span class="sxs-lookup"><span data-stu-id="b1de3-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="b1de3-109">W obiektach metody dłuższej podział wiersza następuje po znaku równości (=), a cała treść metody jest wcięta.</span><span class="sxs-lookup"><span data-stu-id="b1de3-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="b1de3-110">Atrybuty mogą być stosowane do dowolnej deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="b1de3-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="b1de3-111">Poprzedzają one składnię definicji metody i są zwykle wyświetlane w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="b1de3-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="b1de3-112">Aby uzyskać więcej informacji, zobacz [Atrybuty](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b1de3-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="b1de3-113">Metody mogą być `inline`oznaczone .</span><span class="sxs-lookup"><span data-stu-id="b1de3-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="b1de3-114">Aby uzyskać `inline`informacje na temat , zobacz [Funkcje inline](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b1de3-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="b1de3-115">Metody niewinna mogą być używane cyklicznie w obrębie typu; nie ma potrzeby jawnego `rec` używania słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="b1de3-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="b1de3-116">Metody wystąpień</span><span class="sxs-lookup"><span data-stu-id="b1de3-116">Instance Methods</span></span>

<span data-ttu-id="b1de3-117">Metody wystąpienia są deklarowane za pomocą słowa kluczowego `member` i *samoidentyfikatora,* po którym następuje kropka (.) oraz nazwa i parametry metody.</span><span class="sxs-lookup"><span data-stu-id="b1de3-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="b1de3-118">Jak w przypadku `let` powiązań, *lista parametrów* może być wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b1de3-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="b1de3-119">Zazwyczaj należy ująć parametry metody w nawiasy w formularzu krotki, który jest sposób metody są wyświetlane w F#, gdy są one tworzone w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1de3-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="b1de3-120">Jednak forma curried (parametry oddzielone spacjami) jest również powszechna, a inne wzorce są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b1de3-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="b1de3-121">W poniższym przykładzie przedstawiono definicję i użycie metody wystąpienia nieabstrakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b1de3-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="b1de3-122">W ramach metody wystąpienia nie należy używać identyfikatora siebie, aby uzyskać dostęp do pól zdefiniowanych przy użyciu let powiązania.</span><span class="sxs-lookup"><span data-stu-id="b1de3-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="b1de3-123">Użyj identyfikatora siebie podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1de3-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="b1de3-124">Metody statyczne</span><span class="sxs-lookup"><span data-stu-id="b1de3-124">Static Methods</span></span>

<span data-ttu-id="b1de3-125">Słowo `static` kluczowe służy do określenia, że metoda może być wywoływana bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="b1de3-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="b1de3-126">W przeciwnym razie metody są metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b1de3-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="b1de3-127">W przykładzie w następnej sekcji `let` przedstawiono pola zadeklarowane `member` za pomocą słowa kluczowego, `static` członków właściwości zadeklarowanych za pomocą słowa kluczowego i metodę statyczną zadeklarowaną za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="b1de3-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="b1de3-128">Poniższy przykład ilustruje definicję i stosowanie metod statycznych.</span><span class="sxs-lookup"><span data-stu-id="b1de3-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="b1de3-129">Załóżmy, że te `SomeType` definicje metod znajdują się w klasie w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b1de3-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="b1de3-130">Metody abstrakcyjne i wirtualne</span><span class="sxs-lookup"><span data-stu-id="b1de3-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="b1de3-131">Słowo `abstract` kluczowe wskazuje, że metoda ma gniazdo wirtualnej wysyłki i może nie mieć definicji w klasie.</span><span class="sxs-lookup"><span data-stu-id="b1de3-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="b1de3-132">Gniazdo *wirtualnej wysyłki* jest wpisem w wewnętrznie obsługiwanej tabeli funkcji, która jest używana w czasie wykonywania do wyszukiwania wywołań funkcji wirtualnych w typie obiektowym.</span><span class="sxs-lookup"><span data-stu-id="b1de3-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="b1de3-133">Mechanizm wirtualnej wysyłki to mechanizm, który implementuje *polimorfizm*, ważną cechę programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="b1de3-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="b1de3-134">Klasa, która ma co najmniej jedną metodę abstrakcyjną bez definicji jest *klasą abstrakcyjną,* co oznacza, że nie można utworzyć żadnych wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="b1de3-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="b1de3-135">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b1de3-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="b1de3-136">Deklaracje metody abstrakcyjne nie zawierają treści metody.</span><span class="sxs-lookup"><span data-stu-id="b1de3-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="b1de3-137">Zamiast tego po nazwie metody następuje dwukropek (:) i podpis typu dla metody.</span><span class="sxs-lookup"><span data-stu-id="b1de3-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="b1de3-138">Podpis typu metody jest taka sama jak pokazana przez IntelliSense po wstrzymaniu wskaźnika myszy nad nazwą metody w Edytorze kodu programu Visual Studio, z wyjątkiem bez nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="b1de3-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="b1de3-139">Podpisy typów są również wyświetlane przez interpretera fsi.exe, gdy pracujesz interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="b1de3-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="b1de3-140">Podpis typu metody jest tworzony przez listę typów parametrów, a następnie typu zwracanego, z odpowiednimi symbolami separatora.</span><span class="sxs-lookup"><span data-stu-id="b1de3-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="b1de3-141">Parametry curried są `->` oddzielone, a parametry krotki są oddzielone . `*`</span><span class="sxs-lookup"><span data-stu-id="b1de3-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="b1de3-142">Zwracana wartość jest zawsze oddzielona `->` od argumentów symbolem.</span><span class="sxs-lookup"><span data-stu-id="b1de3-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="b1de3-143">Nawiasy mogą służyć do grupowania złożonych parametrów, takich jak, gdy typ funkcji jest parametrem, lub do wskazania, kiedy krotka jest traktowana jako pojedynczy parametr, a nie jako dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="b1de3-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="b1de3-144">Można również podać metody abstrakcyjne domyślne definicje, dodając definicję do klasy i przy użyciu słowa kluczowego, `default` jak pokazano w bloku składni w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="b1de3-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="b1de3-145">Metoda abstrakcyjna, która ma definicję w tej samej klasie jest odpowiednikiem metody wirtualnej w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1de3-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="b1de3-146">Niezależnie od tego, czy `abstract` istnieje definicja, słowo kluczowe tworzy nowe gniazdo wysyłki w tabeli funkcji wirtualnych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="b1de3-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="b1de3-147">Niezależnie od tego, czy klasa podstawowa implementuje swoje metody abstrakcyjne, klasy pochodne może zapewnić implementacje metod abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="b1de3-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="b1de3-148">Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, należy zdefiniować metodę, która ma `override` taką `default` samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia lub słowa kluczowego i podać treść metody.</span><span class="sxs-lookup"><span data-stu-id="b1de3-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="b1de3-149">Słowa kluczowe `override` `default` i oznaczają dokładnie to samo.</span><span class="sxs-lookup"><span data-stu-id="b1de3-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="b1de3-150">Użyj, `override` jeśli nowa metoda zastępuje implementację klasy podstawowej; użyj `default` podczas tworzenia implementacji w tej samej klasie, co oryginalna deklaracja abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="b1de3-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="b1de3-151">Nie należy `abstract` używać słowa kluczowego na metodę, która implementuje metodę, która została zadeklarowana jako abstrakcyjna w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b1de3-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="b1de3-152">W poniższym przykładzie przedstawiono `Rotate` metodę abstrakcyjną, która ma implementację domyślną, odpowiednik metody wirtualnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1de3-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="b1de3-153">W poniższym przykładzie przedstawiono klasę pochodną, która zastępuje metodę klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b1de3-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="b1de3-154">W takim przypadku zastąpienie zmienia zachowanie tak, aby metoda nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="b1de3-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="b1de3-155">Metody przeciążone</span><span class="sxs-lookup"><span data-stu-id="b1de3-155">Overloaded Methods</span></span>

<span data-ttu-id="b1de3-156">Przeciążone metody są metody, które mają identyczne nazwy w danym typu, ale które mają różne argumenty.</span><span class="sxs-lookup"><span data-stu-id="b1de3-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="b1de3-157">W F#, opcjonalne argumenty są zwykle używane zamiast przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="b1de3-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="b1de3-158">Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty są w formie krotki, a nie curried formie.</span><span class="sxs-lookup"><span data-stu-id="b1de3-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="b1de3-159">Argumenty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="b1de3-159">Optional Arguments</span></span>

<span data-ttu-id="b1de3-160">Począwszy od F# 4.1, można również mieć opcjonalne argumenty z wartością parametru domyślnego w metodach.</span><span class="sxs-lookup"><span data-stu-id="b1de3-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="b1de3-161">Ma to ułatwić współdziałanie z kodem Języka C#.</span><span class="sxs-lookup"><span data-stu-id="b1de3-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="b1de3-162">W poniższym przykładzie przedstawiono składnię:</span><span class="sxs-lookup"><span data-stu-id="b1de3-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="b1de3-163">Należy zauważyć, że `DefaultParameterValue` wartość przekazywana dla musi odpowiadać typowi wejściowemu.</span><span class="sxs-lookup"><span data-stu-id="b1de3-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="b1de3-164">W powyższej próbce `int`jest to .</span><span class="sxs-lookup"><span data-stu-id="b1de3-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="b1de3-165">Próba przekazania wartości niecałkowitej do `DefaultParameterValue` spowodowałoby błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b1de3-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="b1de3-166">Przykład: Właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="b1de3-166">Example: Properties and Methods</span></span>

<span data-ttu-id="b1de3-167">Poniższy przykład zawiera typ, który zawiera przykłady pól, funkcje prywatne, właściwości i metodę statyczną.</span><span class="sxs-lookup"><span data-stu-id="b1de3-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="b1de3-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1de3-168">See also</span></span>

- [<span data-ttu-id="b1de3-169">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b1de3-169">Members</span></span>](index.md)
