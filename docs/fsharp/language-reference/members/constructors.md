---
title: Konstruktorów
description: Dowiedz się, jak definiować i używać F# konstruktorów w programie w celu tworzenia i inicjowania obiektów klasy i struktury.
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736845"
---
# <a name="constructors"></a><span data-ttu-id="75e34-103">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="75e34-103">Constructors</span></span>

<span data-ttu-id="75e34-104">W tym artykule opisano sposób definiowania i używania konstruktorów do tworzenia i inicjowania obiektów klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="75e34-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="75e34-105">Konstrukcja obiektów klasy</span><span class="sxs-lookup"><span data-stu-id="75e34-105">Construction of class objects</span></span>

<span data-ttu-id="75e34-106">Obiekty typów klas mają konstruktory.</span><span class="sxs-lookup"><span data-stu-id="75e34-106">Objects of class types have constructors.</span></span> <span data-ttu-id="75e34-107">Istnieją dwa rodzaje konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="75e34-107">There are two kinds of constructors.</span></span> <span data-ttu-id="75e34-108">Jeden jest konstruktorem podstawowym, którego parametry są wyświetlane w nawiasach tuż po nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="75e34-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="75e34-109">Należy określić inne, opcjonalne konstruktory za pomocą słowa kluczowego `new`.</span><span class="sxs-lookup"><span data-stu-id="75e34-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="75e34-110">Wszelkie takie dodatkowe konstruktory muszą wywołać Konstruktor podstawowy.</span><span class="sxs-lookup"><span data-stu-id="75e34-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="75e34-111">Konstruktor podstawowy zawiera powiązania `let` i `do`, które pojawiają się na początku definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="75e34-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="75e34-112">Powiązanie `let` deklaruje prywatne pola i metody klasy; powiązanie `do` wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="75e34-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="75e34-113">Aby uzyskać więcej informacji na temat powiązań `let` w konstruktorach klas, zobacz [`let` powiązania w klasach](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="75e34-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="75e34-114">Aby uzyskać więcej informacji na temat powiązań `do` w konstruktorach, zobacz [`do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="75e34-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="75e34-115">Niezależnie od tego, czy Konstruktor, który ma być wywoływany, jest konstruktorem podstawowym, czy dodatkowym konstruktorem, można tworzyć obiekty przy użyciu wyrażenia `new` z lub bez słowa kluczowego Optional `new`.</span><span class="sxs-lookup"><span data-stu-id="75e34-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="75e34-116">Obiekty są inicjowane razem z argumentami konstruktora, przez wystawienie argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="75e34-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="75e34-117">Możesz również ustawić właściwości obiektu podczas konstruowania obiektu, używając nazw właściwości i przypisując wartości tak samo jak w przypadku używania nazwanych argumentów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75e34-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="75e34-118">Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów:</span><span class="sxs-lookup"><span data-stu-id="75e34-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="75e34-119">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="75e34-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="75e34-120">Konstrukcja struktur</span><span class="sxs-lookup"><span data-stu-id="75e34-120">Construction of structures</span></span>

<span data-ttu-id="75e34-121">Struktury są zgodne ze wszystkimi regułami klas.</span><span class="sxs-lookup"><span data-stu-id="75e34-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="75e34-122">W związku z tym, można mieć konstruktora podstawowego i można dostarczyć dodatkowych konstruktorów przy użyciu `new`.</span><span class="sxs-lookup"><span data-stu-id="75e34-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="75e34-123">Istnieje jednak jedna ważna różnica między strukturami i klasami: struktury mogą mieć Konstruktor bez parametrów (czyli jeden bez argumentów), nawet jeśli żaden Konstruktor podstawowy nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="75e34-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="75e34-124">Konstruktor bez parametrów inicjuje wszystkie pola do wartości domyślnej dla tego typu, zazwyczaj zero lub jego odpowiednikiem.</span><span class="sxs-lookup"><span data-stu-id="75e34-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="75e34-125">Wszystkie konstruktory zdefiniowane dla struktur muszą mieć co najmniej jeden argument, aby nie powodowały konfliktów z konstruktorem bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="75e34-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="75e34-126">Ponadto struktury często zawierają pola, które są tworzone za pomocą słowa kluczowego `val`; klasy mogą również mieć te pola.</span><span class="sxs-lookup"><span data-stu-id="75e34-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="75e34-127">Struktury i klasy, które mają pola zdefiniowane za pomocą słowa kluczowego `val`, można również zainicjować w dodatkowych konstruktorach przy użyciu wyrażeń rekordów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="75e34-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="75e34-128">Aby uzyskać więcej informacji, zobacz [pola jawne: słowo kluczowe `val`](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="75e34-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="75e34-129">Wykonywanie efektów ubocznych w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="75e34-129">Executing side effects in constructors</span></span>

<span data-ttu-id="75e34-130">Konstruktor podstawowy w klasie może wykonać kod w powiązaniu `do`.</span><span class="sxs-lookup"><span data-stu-id="75e34-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="75e34-131">Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze bez powiązania `do`?</span><span class="sxs-lookup"><span data-stu-id="75e34-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="75e34-132">W tym celu należy użyć słowa kluczowego `then`.</span><span class="sxs-lookup"><span data-stu-id="75e34-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="75e34-133">Efekty uboczne konstruktora podstawowego nadal są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="75e34-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="75e34-134">W związku z tym dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="75e34-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="75e34-135">Identyfikatory własne w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="75e34-135">Self identifiers in constructors</span></span>

<span data-ttu-id="75e34-136">W innych elementach członkowskich należy podać nazwę bieżącego obiektu w definicji każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="75e34-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="75e34-137">Możesz również umieścić własny identyfikator w pierwszym wierszu definicji klasy, używając słowa kluczowego `as` bezpośrednio po parametrach konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75e34-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="75e34-138">Poniższy przykład ilustruje tę składnię.</span><span class="sxs-lookup"><span data-stu-id="75e34-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="75e34-139">W dodatkowych konstruktorach można również zdefiniować samodzielny identyfikator, umieszczając klauzulę `as` bezpośrednio po parametrach konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75e34-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="75e34-140">Poniższy przykład ilustruje następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="75e34-140">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="75e34-141">Problemy mogą wystąpić podczas próby użycia obiektu, zanim zostanie on w pełni zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="75e34-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="75e34-142">W związku z tym użycie identyfikatora samodzielnego może spowodować, że kompilator emituje ostrzeżenie i wstawi dodatkowe sprawdzenia, aby upewnić się, że elementy członkowskie obiektu nie są dostępne przed zainicjowaniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e34-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="75e34-143">Samego identyfikatora można używać tylko w powiązaniach `do` konstruktora podstawowego lub po słowie kluczowym `then` w dodatkowych konstruktorach.</span><span class="sxs-lookup"><span data-stu-id="75e34-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="75e34-144">Nazwa identyfikatora własnego nie musi być `this`.</span><span class="sxs-lookup"><span data-stu-id="75e34-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="75e34-145">Może być dowolnym prawidłowym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="75e34-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="75e34-146">Przypisywanie wartości do właściwości podczas inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="75e34-146">Assigning values to properties at initialization</span></span>

<span data-ttu-id="75e34-147">Można przypisać wartości do właściwości obiektu klasy w kodzie inicjującym, dołączając listę przypisań formularza `property = value` do listy argumentów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75e34-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="75e34-148">Jest to pokazane w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="75e34-148">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="75e34-149">Poniższa wersja poprzedniego kodu ilustruje kombinację zwykłych argumentów, argumentów opcjonalnych i ustawień właściwości w jednym wywołaniu konstruktora:</span><span class="sxs-lookup"><span data-stu-id="75e34-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="75e34-150">Konstruktory w dziedziczonej klasie</span><span class="sxs-lookup"><span data-stu-id="75e34-150">Constructors in inherited class</span></span>

<span data-ttu-id="75e34-151">Podczas dziedziczenia z klasy podstawowej, która ma konstruktora, należy określić jej argumenty w klauzuli Inherits.</span><span class="sxs-lookup"><span data-stu-id="75e34-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="75e34-152">Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="75e34-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="75e34-153">Konstruktory statyczne lub konstruktory typów</span><span class="sxs-lookup"><span data-stu-id="75e34-153">Static constructors or type constructors</span></span>

<span data-ttu-id="75e34-154">Oprócz określania kodu do tworzenia obiektów, statyczne powiązania `let` i `do` mogą być tworzone w typach klas, które wykonują przed pierwszym użyciem typu do wykonania inicjalizacji na poziomie typu.</span><span class="sxs-lookup"><span data-stu-id="75e34-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="75e34-155">Aby uzyskać więcej informacji, zobacz [powiązania `let` w klasach](let-bindings-in-classes.md) i [powiązaniach `do` w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="75e34-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75e34-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75e34-156">See also</span></span>

- [<span data-ttu-id="75e34-157">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="75e34-157">Members</span></span>](index.md)
