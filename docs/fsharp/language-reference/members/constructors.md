---
title: Konstruktory
description: 'Dowiedz się, jak definiować i używać konstruktorów w języku F # do tworzenia i inicjowania obiektów klasy i struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303442"
---
# <a name="constructors"></a><span data-ttu-id="2ec63-103">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="2ec63-103">Constructors</span></span>

<span data-ttu-id="2ec63-104">W tym artykule opisano sposób definiowania i używania konstruktorów do tworzenia i inicjowania obiektów klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="2ec63-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="2ec63-105">Konstrukcja obiektów klasy</span><span class="sxs-lookup"><span data-stu-id="2ec63-105">Construction of class objects</span></span>

<span data-ttu-id="2ec63-106">Obiekty typów klas mają konstruktory.</span><span class="sxs-lookup"><span data-stu-id="2ec63-106">Objects of class types have constructors.</span></span> <span data-ttu-id="2ec63-107">Istnieją dwa rodzaje konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="2ec63-107">There are two kinds of constructors.</span></span> <span data-ttu-id="2ec63-108">Jeden jest konstruktorem podstawowym, którego parametry są wyświetlane w nawiasach tuż po nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="2ec63-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="2ec63-109">Należy określić inne, opcjonalne konstruktory, używając `new` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="2ec63-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="2ec63-110">Wszelkie takie dodatkowe konstruktory muszą wywołać Konstruktor podstawowy.</span><span class="sxs-lookup"><span data-stu-id="2ec63-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="2ec63-111">Konstruktor podstawowy zawiera `let` i `do` powiązania, które pojawiają się na początku definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="2ec63-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="2ec63-112">`let`Powiązanie deklaruje prywatne pola i metody klasy; `do` powiązanie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="2ec63-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="2ec63-113">Aby uzyskać więcej informacji na temat `let` powiązań w konstruktorach klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="2ec63-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="2ec63-114">Aby uzyskać więcej informacji na temat `do` powiązań w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="2ec63-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="2ec63-115">Niezależnie od tego, czy Konstruktor, który ma być wywoływany, jest konstruktorem podstawowym, czy dodatkowym konstruktorem, można tworzyć obiekty przy użyciu `new` wyrażenia z lub bez `new` słowa kluczowego Optional.</span><span class="sxs-lookup"><span data-stu-id="2ec63-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="2ec63-116">Obiekty są inicjowane razem z argumentami konstruktora, przez wystawienie argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="2ec63-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="2ec63-117">Możesz również ustawić właściwości obiektu podczas konstruowania obiektu, używając nazw właściwości i przypisując wartości tak samo jak w przypadku używania nazwanych argumentów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2ec63-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="2ec63-118">Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów:</span><span class="sxs-lookup"><span data-stu-id="2ec63-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="2ec63-119">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="2ec63-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="2ec63-120">Konstrukcja struktur</span><span class="sxs-lookup"><span data-stu-id="2ec63-120">Construction of structures</span></span>

<span data-ttu-id="2ec63-121">Struktury są zgodne ze wszystkimi regułami klas.</span><span class="sxs-lookup"><span data-stu-id="2ec63-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="2ec63-122">W związku z tym, można mieć konstruktora podstawowego i można dostarczyć dodatkowych konstruktorów przy użyciu `new` .</span><span class="sxs-lookup"><span data-stu-id="2ec63-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="2ec63-123">Istnieje jednak jedna ważna różnica między strukturami i klasami: struktury mogą mieć Konstruktor bez parametrów (czyli jeden bez argumentów), nawet jeśli żaden Konstruktor podstawowy nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2ec63-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="2ec63-124">Konstruktor bez parametrów inicjuje wszystkie pola do wartości domyślnej dla tego typu, zazwyczaj zero lub jego odpowiednikiem.</span><span class="sxs-lookup"><span data-stu-id="2ec63-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="2ec63-125">Wszystkie konstruktory zdefiniowane dla struktur muszą mieć co najmniej jeden argument, aby nie powodowały konfliktów z konstruktorem bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ec63-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="2ec63-126">Ponadto struktury często zawierają pola, które są tworzone za pomocą `val` słowa kluczowego; klasy mogą także mieć te pola.</span><span class="sxs-lookup"><span data-stu-id="2ec63-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="2ec63-127">Struktury i klasy, które mają pola zdefiniowane za pomocą `val` słowa kluczowego, można również zainicjować w dodatkowych konstruktorach przy użyciu wyrażeń rekordów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2ec63-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="2ec63-128">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` słowo kluczowe](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="2ec63-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="2ec63-129">Wykonywanie efektów ubocznych w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="2ec63-129">Executing side effects in constructors</span></span>

<span data-ttu-id="2ec63-130">Konstruktor podstawowy w klasie może wykonać kod w `do` powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="2ec63-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="2ec63-131">Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze bez `do` powiązania?</span><span class="sxs-lookup"><span data-stu-id="2ec63-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="2ec63-132">W tym celu należy użyć `then` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="2ec63-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="2ec63-133">Efekty uboczne konstruktora podstawowego nadal są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="2ec63-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="2ec63-134">W związku z tym dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="2ec63-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

<span data-ttu-id="2ec63-135">Przyczyną tego problemu `then` jest to `do` , że słowo kluczowe jest wymagane, a nie inne, ma `do` swoje standardowe znaczenie dla nieograniczonego `unit` wyrażenia zwracającego wartość, gdy występuje w treści dodatkowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2ec63-135">The reason why `then` is required instead of another `do` is that the `do` keyword has its standard meaning of delimiting a `unit`-returning expression when present in the body of an additional constructor.</span></span> <span data-ttu-id="2ec63-136">Ma on tylko specjalne znaczenie w kontekście konstruktorów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="2ec63-136">It only has special meaning in the context of primary constructors.</span></span>

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="2ec63-137">Identyfikatory własne w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="2ec63-137">Self identifiers in constructors</span></span>

<span data-ttu-id="2ec63-138">W innych elementach członkowskich należy podać nazwę bieżącego obiektu w definicji każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2ec63-138">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="2ec63-139">Można również umieścić własny identyfikator w pierwszym wierszu definicji klasy za pomocą `as` słowa kluczowego bezpośrednio po parametrach konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2ec63-139">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="2ec63-140">Poniższy przykład ilustruje tę składnię.</span><span class="sxs-lookup"><span data-stu-id="2ec63-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="2ec63-141">W dodatkowych konstruktorach można również zdefiniować samodzielny identyfikator, umieszczając `as` klauzulę bezpośrednio po parametrach konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2ec63-141">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="2ec63-142">Poniższy przykład ilustruje następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="2ec63-142">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="2ec63-143">Problemy mogą wystąpić podczas próby użycia obiektu, zanim zostanie on w pełni zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2ec63-143">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="2ec63-144">W związku z tym użycie identyfikatora samodzielnego może spowodować, że kompilator emituje ostrzeżenie i wstawi dodatkowe sprawdzenia, aby upewnić się, że elementy członkowskie obiektu nie są dostępne przed zainicjowaniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ec63-144">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="2ec63-145">Samego identyfikatora można używać tylko w `do` powiązaniach konstruktora podstawowego lub po `then` słowie kluczowym w dodatkowych konstruktorach.</span><span class="sxs-lookup"><span data-stu-id="2ec63-145">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="2ec63-146">Nazwa identyfikatora własnego nie musi być `this` .</span><span class="sxs-lookup"><span data-stu-id="2ec63-146">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="2ec63-147">Może być dowolnym prawidłowym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="2ec63-147">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="2ec63-148">Przypisywanie wartości do właściwości podczas inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="2ec63-148">Assigning values to properties at initialization</span></span>

<span data-ttu-id="2ec63-149">Można przypisać wartości do właściwości obiektu klasy w kodzie inicjalizacji, dołączając listę przypisań formularza `property = value` do listy argumentów konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2ec63-149">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="2ec63-150">Jest to pokazane w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="2ec63-150">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="2ec63-151">Poniższa wersja poprzedniego kodu ilustruje kombinację zwykłych argumentów, argumentów opcjonalnych i ustawień właściwości w jednym wywołaniu konstruktora:</span><span class="sxs-lookup"><span data-stu-id="2ec63-151">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="2ec63-152">Konstruktory w dziedziczonej klasie</span><span class="sxs-lookup"><span data-stu-id="2ec63-152">Constructors in inherited class</span></span>

<span data-ttu-id="2ec63-153">Podczas dziedziczenia z klasy podstawowej, która ma konstruktora, należy określić jej argumenty w klauzuli Inherits.</span><span class="sxs-lookup"><span data-stu-id="2ec63-153">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="2ec63-154">Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="2ec63-154">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="2ec63-155">Konstruktory statyczne lub konstruktory typów</span><span class="sxs-lookup"><span data-stu-id="2ec63-155">Static constructors or type constructors</span></span>

<span data-ttu-id="2ec63-156">Oprócz określania kodu do tworzenia obiektów, statyczne `let` i `do` powiązania mogą być tworzone w typach klas, które wykonują przed pierwszym użyciem typu do wykonania inicjalizacji na poziomie typu.</span><span class="sxs-lookup"><span data-stu-id="2ec63-156">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="2ec63-157">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązaniach w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="2ec63-157">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ec63-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ec63-158">See also</span></span>

- [<span data-ttu-id="2ec63-159">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2ec63-159">Members</span></span>](index.md)
