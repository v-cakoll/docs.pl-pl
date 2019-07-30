---
title: Metody
description: Dowiedz się F# , jak metoda jest funkcją skojarzoną z typem, który służy do uwidaczniania i implementowania funkcji i zachowań obiektów i typów.
ms.date: 05/16/2016
ms.openlocfilehash: 13503690a59ace13dacba93b6fce9ea3240c5cc2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627439"
---
# <a name="methods"></a><span data-ttu-id="3ce89-103">Metody</span><span class="sxs-lookup"><span data-stu-id="3ce89-103">Methods</span></span>

<span data-ttu-id="3ce89-104">*Metoda* jest funkcją, która jest skojarzona z typem.</span><span class="sxs-lookup"><span data-stu-id="3ce89-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="3ce89-105">W programowaniu zorientowanym na obiekty metody są używane do ujawniania i implementowania funkcji i zachowań obiektów i typów.</span><span class="sxs-lookup"><span data-stu-id="3ce89-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ce89-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ce89-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="3ce89-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ce89-107">Remarks</span></span>

<span data-ttu-id="3ce89-108">W poprzedniej składni, można zobaczyć różne formy deklaracji i definicji metod.</span><span class="sxs-lookup"><span data-stu-id="3ce89-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="3ce89-109">W większej liczbie metod, podział wiersza następuje po znaku równości (=), a cała treść metody jest wcięty.</span><span class="sxs-lookup"><span data-stu-id="3ce89-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="3ce89-110">Atrybuty mogą być stosowane do dowolnej deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="3ce89-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="3ce89-111">Poprzedzają one składnię definicji metody i są zwykle wyświetlane w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="3ce89-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="3ce89-112">Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3ce89-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="3ce89-113">Metody mogą być oznaczone `inline`.</span><span class="sxs-lookup"><span data-stu-id="3ce89-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="3ce89-114">Aby uzyskać informacje `inline`na temat, zobacz [funkcje wbudowane](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3ce89-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="3ce89-115">Metody inne niż śródwierszowe mogą być używane rekursywnie w obrębie typu; nie ma potrzeby jawnego używania `rec` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="3ce89-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="3ce89-116">Metody wystąpień</span><span class="sxs-lookup"><span data-stu-id="3ce89-116">Instance Methods</span></span>

<span data-ttu-id="3ce89-117">Metody wystąpień są zadeklarowane za `member` pomocą słowa kluczowego i samodzielnego *identyfikatora*, po którym następuje kropka (.) oraz nazwa metody i parametry.</span><span class="sxs-lookup"><span data-stu-id="3ce89-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="3ce89-118">Podobnie jak w przypadku `let` powiązań, *Lista parametrów* może być wzorcem.</span><span class="sxs-lookup"><span data-stu-id="3ce89-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="3ce89-119">Zwykle parametry metody są umieszczane w nawiasach w postaci spójnej kolekcji, która jest sposobem, w F# jaki metody są wyświetlane, gdy są tworzone w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ce89-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="3ce89-120">Jednak formularz rozwinięte (parametry oddzielone spacjami) jest również powszechny, a także inne wzorce są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3ce89-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="3ce89-121">Poniższy przykład ilustruje definicję i użycie nieabstrakcyjnej metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3ce89-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="3ce89-122">W ramach metod wystąpień nie należy używać samego identyfikatora do uzyskiwania dostępu do pól zdefiniowanych przy użyciu let bindings.</span><span class="sxs-lookup"><span data-stu-id="3ce89-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="3ce89-123">Użyj własnego identyfikatora podczas uzyskiwania dostępu do innych członków i właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ce89-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="3ce89-124">Metody statyczne</span><span class="sxs-lookup"><span data-stu-id="3ce89-124">Static Methods</span></span>

<span data-ttu-id="3ce89-125">Słowo kluczowe `static` jest używane do określania, że metoda może być wywoływana bez wystąpienia i nie jest skojarzona z wystąpieniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ce89-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="3ce89-126">W przeciwnym razie metody są metodami wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3ce89-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="3ce89-127">W przykładzie w następnej sekcji przedstawiono pola zadeklarowane za pomocą `let` słowa kluczowego, członków właściwości zadeklarowanych `member` za pomocą słowa kluczowego i `static` statycznej metody zadeklarowanej za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="3ce89-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="3ce89-128">Poniższy przykład ilustruje definicję i użycie metod statycznych.</span><span class="sxs-lookup"><span data-stu-id="3ce89-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="3ce89-129">Załóżmy, że te definicje metod znajdują `SomeType` się w klasie w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3ce89-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="3ce89-130">Metody abstrakcyjne i wirtualne</span><span class="sxs-lookup"><span data-stu-id="3ce89-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="3ce89-131">Słowo kluczowe `abstract` wskazuje, że metoda ma wirtualne gniazdo wysyłkowe i może nie mieć definicji w klasie.</span><span class="sxs-lookup"><span data-stu-id="3ce89-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="3ce89-132">*Wirtualne miejsce wysyłki* to wpis w wewnętrznie obsługiwanej tabeli funkcji, który jest używany w czasie wykonywania do wyszukiwania wywołań funkcji wirtualnych w typie zorientowanym obiektowo.</span><span class="sxs-lookup"><span data-stu-id="3ce89-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="3ce89-133">Mechanizm wysyłania wirtualnego jest mechanizmem, który implementuje *polimorfizm*, ważną funkcję programowania zorientowanego na obiekt.</span><span class="sxs-lookup"><span data-stu-id="3ce89-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="3ce89-134">Klasa, która ma co najmniej jedną metodę abstrakcyjną bez definicji, jest *klasą abstrakcyjną*, co oznacza, że nie można tworzyć wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3ce89-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="3ce89-135">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3ce89-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="3ce89-136">Deklaracje metody abstrakcyjnej nie zawierają treści metody.</span><span class="sxs-lookup"><span data-stu-id="3ce89-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="3ce89-137">Zamiast tego, nazwa metody następuje dwukropek (:) i podpis typu dla metody.</span><span class="sxs-lookup"><span data-stu-id="3ce89-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="3ce89-138">Sygnatura typu metody jest taka sama jak pokazana przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwą metody w edytorze Visual Studio Code, z wyjątkiem nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="3ce89-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="3ce89-139">Sygnatury typów są również wyświetlane przez interpreter, FSI. exe, gdy pracujesz interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="3ce89-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="3ce89-140">Podpis typu metody jest tworzony przez wystawienie typów parametrów, po których następuje zwracany typ, z odpowiednimi symbolami separatora.</span><span class="sxs-lookup"><span data-stu-id="3ce89-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="3ce89-141">Parametry rozwinięte są rozdzielone `->` , a parametry krotki są rozdzielone przez. `*`</span><span class="sxs-lookup"><span data-stu-id="3ce89-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="3ce89-142">Wartość zwracana jest zawsze oddzielona od argumentów przez `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="3ce89-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="3ce89-143">Nawiasy mogą służyć do grupowania parametrów złożonych, takich jak, gdy typ funkcji jest parametrem lub aby wskazać, kiedy Krotka jest traktowana jako pojedynczy parametr, a nie jako dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="3ce89-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="3ce89-144">Można również nadać abstrakcyjnym metodom definicje domyślne przez dodanie definicji do klasy i użycie `default` słowa kluczowego, jak pokazano w bloku składni w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="3ce89-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="3ce89-145">Metoda abstrakcyjna, która ma definicję w tej samej klasie, jest równoważna z metodą wirtualną w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ce89-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="3ce89-146">Niezależnie od tego `abstract` , czy definicja istnieje, słowo kluczowe tworzy nowe miejsce wysyłki w tabeli funkcji wirtualnych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="3ce89-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="3ce89-147">Niezależnie od tego, czy klasa bazowa implementuje metody abstrakcyjne, klasy pochodne mogą dostarczać implementacje metod abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="3ce89-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="3ce89-148">Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, zdefiniuj metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` słowa kluczowego or `default` i podaj treść metody.</span><span class="sxs-lookup"><span data-stu-id="3ce89-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="3ce89-149">Słowa kluczowe `override` i `default` oznaczają dokładnie te same rzeczy.</span><span class="sxs-lookup"><span data-stu-id="3ce89-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="3ce89-150">Użyj `override` , jeśli nowa metoda przesłania implementację klasy bazowej; Użyj `default` , gdy tworzysz implementację w tej samej klasie co oryginalna deklaracja abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="3ce89-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="3ce89-151">Nie należy używać `abstract` słowa kluczowego na metodzie implementującej metodę, która została zadeklarowana jako abstract w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="3ce89-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="3ce89-152">Poniższy przykład ilustruje metodę `Rotate` abstrakcyjną, która ma implementację domyślną, równoważnej metody wirtualnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ce89-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="3ce89-153">Poniższy przykład ilustruje klasę pochodną, która zastępuje metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="3ce89-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="3ce89-154">W takim przypadku zastąpienie zmieni zachowanie, tak aby Metoda niczego nie robi.</span><span class="sxs-lookup"><span data-stu-id="3ce89-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="3ce89-155">Przeciążone metody</span><span class="sxs-lookup"><span data-stu-id="3ce89-155">Overloaded Methods</span></span>

<span data-ttu-id="3ce89-156">Przeciążone metody to metody, które mają identyczne nazwy w danym typie, ale które mają różne argumenty.</span><span class="sxs-lookup"><span data-stu-id="3ce89-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="3ce89-157">W F#programie argumenty opcjonalne są zwykle używane zamiast przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="3ce89-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="3ce89-158">Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty są w postaci krotki, nie rozwinięte form.</span><span class="sxs-lookup"><span data-stu-id="3ce89-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="3ce89-159">Argumenty opcjonalne</span><span class="sxs-lookup"><span data-stu-id="3ce89-159">Optional Arguments</span></span>

<span data-ttu-id="3ce89-160">Począwszy od F# 4,1, można także mieć opcjonalne argumenty z domyślną wartością parametru w metodach.</span><span class="sxs-lookup"><span data-stu-id="3ce89-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="3ce89-161">W ten sposób można ułatwić współdziałanie C# z kodem.</span><span class="sxs-lookup"><span data-stu-id="3ce89-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="3ce89-162">Poniższy przykład ilustruje składnię:</span><span class="sxs-lookup"><span data-stu-id="3ce89-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="3ce89-163">Należy zauważyć, że wartość przeniesiona `DefaultParameterValue` dla elementu musi być zgodna z typem danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3ce89-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="3ce89-164">W powyższym przykładzie jest `int`to.</span><span class="sxs-lookup"><span data-stu-id="3ce89-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="3ce89-165">Próba przekazania wartości `DefaultParameterValue` innej niż całkowita spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3ce89-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="3ce89-166">Przykład: Właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="3ce89-166">Example: Properties and Methods</span></span>

<span data-ttu-id="3ce89-167">Poniższy przykład zawiera typ, który ma przykłady pól, funkcji prywatnych, właściwości i metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="3ce89-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="3ce89-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ce89-168">See also</span></span>

- [<span data-ttu-id="3ce89-169">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3ce89-169">Members</span></span>](index.md)
