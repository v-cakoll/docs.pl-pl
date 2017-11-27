---
title: Konstruktorzy (F#)
description: "Dowiedz się, jak zdefiniować i użyć konstruktorów w języku F # do tworzenia i inicjowania klasy i struktury obiektów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a><span data-ttu-id="0433c-104">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="0433c-104">Constructors</span></span>

<span data-ttu-id="0433c-105">W tym temacie opisano sposób definiowania i konstruktory umożliwia tworzenie i Inicjowanie obiektów klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="0433c-105">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="0433c-106">Konstrukcja obiektów klasy</span><span class="sxs-lookup"><span data-stu-id="0433c-106">Construction of Class Objects</span></span>
<span data-ttu-id="0433c-107">Obiekty typu klasy mieć konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="0433c-107">Objects of class types have constructors.</span></span> <span data-ttu-id="0433c-108">Istnieją dwa rodzaje konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="0433c-108">There are two kinds of constructors.</span></span> <span data-ttu-id="0433c-109">Jedna jest podstawowego konstruktora, którego parametry są wyświetlane w nawiasach zaraz po nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="0433c-109">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="0433c-110">Określ inne, opcjonalne dodatkowe konstruktorów przy użyciu `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0433c-110">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="0433c-111">Wszelkie dodatkowe konstruktorów należy wywołać konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="0433c-111">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="0433c-112">Zawiera podstawowego konstruktora `let` i `do` powiązania, które pojawiają się na początku definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="0433c-112">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="0433c-113">A `let` powiązanie deklaruje pól prywatnych i metod klasy; `do` powiązania wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="0433c-113">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="0433c-114">Aby uzyskać więcej informacji na temat `let` powiązania konstruktorów klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0433c-114">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="0433c-115">Aby uzyskać więcej informacji na temat `do` powiązania w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0433c-115">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="0433c-116">Niezależnie od tego, czy chcesz wywołać konstruktora podstawowego konstruktora lub konstruktora dodatkowe, można tworzyć obiektów przy użyciu `new` wyrażenia, lub bez opcjonalny `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0433c-116">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="0433c-117">Inicjowanie obiektów wraz z argumentów konstruktora przez listę argumentów w kolejności i oddzielone przecinkami i ujęte w nawiasy lub przy użyciu argumentów nazwanych i wartości w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="0433c-117">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="0433c-118">Można również ustawiać właściwości obiektu podczas konstruowania obiektu przy użyciu nazw właściwości i przypisywanie wartości, tak samo, jak używasz nazwane argumenty konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0433c-118">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="0433c-119">Poniższy kod przedstawia klasę, która ma Konstruktor i różne sposoby tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="0433c-119">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="0433c-120">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0433c-120">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="0433c-121">Konstrukcja struktury</span><span class="sxs-lookup"><span data-stu-id="0433c-121">Construction of Structures</span></span>
<span data-ttu-id="0433c-122">Struktury wykonaj wszystkie reguły klas.</span><span class="sxs-lookup"><span data-stu-id="0433c-122">Structures follow all the rules of classes.</span></span> <span data-ttu-id="0433c-123">W związku z tym może mieć podstawowego konstruktora i możesz podać dodatkowe konstruktorów przy użyciu `new`.</span><span class="sxs-lookup"><span data-stu-id="0433c-123">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="0433c-124">Istnieje jednak jedną istotną różnicą między struktury i klasy: struktury może mieć konstruktora domyślnego (tzn bez argumentów), nawet jeśli żaden konstruktor podstawowy jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="0433c-124">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="0433c-125">Konstruktor domyślny inicjuje wszystkie pola na wartość domyślną dla tego typu, zazwyczaj zero lub jego odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="0433c-125">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="0433c-126">Wszystkie konstruktory zdefiniowane dla struktury musi mieć co najmniej jednego argumentu, tak aby nie powodują konfliktów z konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="0433c-126">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="0433c-127">Ponadto struktury często mają pola, które są tworzone za pomocą `val` — słowo kluczowe; klas ma także te pola.</span><span class="sxs-lookup"><span data-stu-id="0433c-127">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="0433c-128">Struktury i klasy, które są zdefiniowane przy użyciu pola `val` — słowo kluczowe również można zainicjować w konstruktorach dodatkowe przy użyciu wyrażenia rekordów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0433c-128">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="0433c-129">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="0433c-129">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="0433c-130">Wykonywanie efekty uboczne w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="0433c-130">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="0433c-131">Podstawowy Konstruktor w klasie może uruchomić kod w `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="0433c-131">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="0433c-132">Niemniej jednak, co zrobić, jeśli należy wykonać kod w dodatkowych konstruktora bez `do` powiązanie?</span><span class="sxs-lookup"><span data-stu-id="0433c-132">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="0433c-133">Aby to zrobić, należy użyć `then` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0433c-133">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="0433c-134">Efekty uboczne podstawowego konstruktora nadal wykonywać.</span><span class="sxs-lookup"><span data-stu-id="0433c-134">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="0433c-135">W związku z tym dane wyjściowe ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0433c-135">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="0433c-136">Samoidentyfikatory w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="0433c-136">Self Identifiers in Constructors</span></span>
<span data-ttu-id="0433c-137">W innych elementach członkowskich należy podać nazwę dla bieżącego obiektu w definicji dla każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0433c-137">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="0433c-138">Można również wprowadzić własnego identyfikatora w pierwszym wierszu definicji klasy, za pomocą `as` — słowo kluczowe bezpośrednio po parametrami konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0433c-138">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="0433c-139">Poniższy przykład przedstawia tej składni.</span><span class="sxs-lookup"><span data-stu-id="0433c-139">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="0433c-140">W konstruktorach dodatkowe istnieje także możliwość zdefiniowania własnego identyfikatora ustawiając `as` klauzuli bezpośrednio po parametrami konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0433c-140">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="0433c-141">Poniższy przykład przedstawia tej składni.</span><span class="sxs-lookup"><span data-stu-id="0433c-141">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="0433c-142">Podczas próby użycia obiektu przed jest całkowicie zdefiniowane, mogą wystąpić problemy.</span><span class="sxs-lookup"><span data-stu-id="0433c-142">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="0433c-143">W związku z tym używa własnego identyfikatora może spowodować kompilator, aby emitować ostrzeżenie i Wstaw dodatkowe kontrole w celu zapewnienia, że elementów członkowskich obiektu nie są dostępne, przed zainicjowaniem obiektu.</span><span class="sxs-lookup"><span data-stu-id="0433c-143">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="0433c-144">Należy używać tylko własnego identyfikatora w `do` powiązania podstawowego konstruktora lub po `then` — słowo kluczowe w dodatkowych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="0433c-144">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="0433c-145">Nazwę własnego identyfikatora nie ma być `this`.</span><span class="sxs-lookup"><span data-stu-id="0433c-145">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="0433c-146">Może to być dowolny poprawny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="0433c-146">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="0433c-147">Przypisywanie wartości do właściwości podczas inicjowania</span><span class="sxs-lookup"><span data-stu-id="0433c-147">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="0433c-148">Można przypisać wartości do właściwości obiektu klasy w kodzie inicjowania przez dołączenie listę przypisań formularza `property = value` do listy argumentów dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0433c-148">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="0433c-149">Przedstawiono to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="0433c-149">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="0433c-150">Następująca wersja poprzedni kod ilustruje kombinacja argumentów zwykłej, argumenty opcjonalne i ustawienia właściwości w wywołaniu jeden konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0433c-150">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="0433c-151">Konstruktory w dziedziczonej klasie</span><span class="sxs-lookup"><span data-stu-id="0433c-151">Constructors in inherited class</span></span>
<span data-ttu-id="0433c-152">Podczas dziedziczenia z klasy podstawowej, która ma Konstruktor, należy określić argumenty w klauzuli dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="0433c-152">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="0433c-153">Aby uzyskać więcej informacji, zobacz [konstruktory i dziedziczenie](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="0433c-153">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="0433c-154">Konstruktory statyczne lub konstruktorów typu</span><span class="sxs-lookup"><span data-stu-id="0433c-154">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="0433c-155">Oprócz określenia kodu do tworzenia obiektów statycznych `let` i `do` powiązania można tworzyć w typach klas, które są wykonywane przed typem najpierw służy do wykonywania inicjowania na poziomie typu.</span><span class="sxs-lookup"><span data-stu-id="0433c-155">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="0433c-156">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0433c-156">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0433c-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0433c-157">See Also</span></span>
[<span data-ttu-id="0433c-158">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0433c-158">Members</span></span>](index.md)
