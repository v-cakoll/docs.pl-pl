---
title: Konstruktorzy (F#)
description: 'Dowiedz się, jak zdefiniować i używać konstruktorów języka F # do tworzenia i inicjowania obiektów klasy i struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227132"
---
# <a name="constructors"></a><span data-ttu-id="c8abd-103">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="c8abd-103">Constructors</span></span>

<span data-ttu-id="c8abd-104">W tym temacie opisano sposób definiowania i tworzenie i Inicjowanie obiektów klasy i struktury za pomocą konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c8abd-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="c8abd-105">Konstrukcja klasy obiektów</span><span class="sxs-lookup"><span data-stu-id="c8abd-105">Construction of Class Objects</span></span>

<span data-ttu-id="c8abd-106">Obiekty typów klas mieć konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c8abd-106">Objects of class types have constructors.</span></span> <span data-ttu-id="c8abd-107">Istnieją dwa rodzaje konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c8abd-107">There are two kinds of constructors.</span></span> <span data-ttu-id="c8abd-108">Jeden jest podstawowy Konstruktor, której parametry są wyświetlane w nawiasach zaraz po nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="c8abd-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="c8abd-109">Określ inne, opcjonalne konstruktory dodatkowe za pomocą `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c8abd-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="c8abd-110">Wszelkie dodatkowe konstruktory musi wywołać konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c8abd-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="c8abd-111">Zawiera podstawowy Konstruktor `let` i `do` powiązania, które pojawiają się na początku definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="c8abd-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="c8abd-112">A `let` powiązanie deklaruje, prywatnych pola i metody klasy; `do` powiązania wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="c8abd-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="c8abd-113">Aby uzyskać więcej informacji na temat `let` powiązania w konstruktorów klas, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c8abd-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="c8abd-114">Aby uzyskać więcej informacji na temat `do` powiązania w konstruktorach, zobacz [ `do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c8abd-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="c8abd-115">Niezależnie od tego, czy konstruktora, aby wywołać konstruktor podstawowym lub dodatkowym konstruktorze, możesz tworzyć obiekty używając `new` wyrażenia, z lub bez opcjonalnego `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c8abd-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="c8abd-116">Inicjowanie obiektów wraz z argumentów konstruktora, wyświetlając listę argumentów w porządku i rozdzielone przecinkami i ujęte w nawiasy, lub za pomocą nazwanych argumentów i wartości w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="c8abd-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="c8abd-117">Można można również ustawić właściwości dla obiektu podczas konstruowania obiektu za pomocą nazwy właściwości i przypisywania wartości, tak jak używasz nazwane argumenty konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8abd-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="c8abd-118">Poniższy kod ilustruje klasę, która ma Konstruktor i różne sposoby tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="c8abd-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="c8abd-119">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="c8abd-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="c8abd-120">Konstrukcja struktury</span><span class="sxs-lookup"><span data-stu-id="c8abd-120">Construction of Structures</span></span>

<span data-ttu-id="c8abd-121">Struktury postępuj zgodnie z regułami klasy.</span><span class="sxs-lookup"><span data-stu-id="c8abd-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="c8abd-122">W związku z tym, może mieć konstruktora podstawowego i możesz podać dodatkowe konstruktory przy użyciu `new`.</span><span class="sxs-lookup"><span data-stu-id="c8abd-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="c8abd-123">Istnieje jednak jedną istotną różnicą między strukturami i klasami: struktury mogą mieć domyślnego konstruktora (czyli jeden bez argumentów), nawet jeśli żaden konstruktor podstawowy jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="c8abd-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="c8abd-124">Konstruktor domyślny inicjuje wszystkie pola na wartość domyślną dla tego typu, zwykle zero lub jej odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="c8abd-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="c8abd-125">Żadnych konstruktorów, zdefiniowanych przez użytkownika w strukturach muszą mieć co najmniej jeden argument, tak, aby nie wchodziły przy użyciu domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8abd-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="c8abd-126">Ponadto struktury często mają pola, które są tworzone za pomocą `val` słowo kluczowe klasy mogą także mieć tych pól.</span><span class="sxs-lookup"><span data-stu-id="c8abd-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="c8abd-127">Struktur i klas, które mają pola zdefiniowane przy użyciu `val` — słowo kluczowe może również być inicjowane w konstruktorach dodatkowe przy użyciu wyrażeń rekordów jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c8abd-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="c8abd-128">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="c8abd-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="c8abd-129">Wykonywanie efekty uboczne w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="c8abd-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="c8abd-130">Podstawowy Konstruktor w klasie może wykonać kod w `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="c8abd-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="c8abd-131">Jednak co zrobić, jeśli trzeba wykonać kod w dodatkowym konstruktorze, bez `do` powiązanie?</span><span class="sxs-lookup"><span data-stu-id="c8abd-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="c8abd-132">Aby to zrobić, należy użyć `then` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c8abd-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="c8abd-133">Efekty uboczne konstruktora podstawowego nadal wykonywać.</span><span class="sxs-lookup"><span data-stu-id="c8abd-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="c8abd-134">W związku z tym dane wyjściowe wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="c8abd-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="c8abd-135">Samoidentyfikatory w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="c8abd-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="c8abd-136">Inne elementy członkowskie służy do Podaj nazwę dla bieżącego obiektu w definicji każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c8abd-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="c8abd-137">Własny identyfikator można umieścić w pierwszym wierszu definicji klasy, za pomocą `as` — słowo kluczowe natychmiast po parametry konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8abd-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="c8abd-138">W poniższym przykładzie pokazano tej składni.</span><span class="sxs-lookup"><span data-stu-id="c8abd-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="c8abd-139">W konstruktorach dodatkowych można zdefiniować własny identyfikator, umieszczając `as` klauzuli od razu po parametry konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8abd-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="c8abd-140">W poniższym przykładzie pokazano tej składni.</span><span class="sxs-lookup"><span data-stu-id="c8abd-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="c8abd-141">Podczas próby użycia obiektu przed jest w pełni zdefiniowana, mogą wystąpić problemy.</span><span class="sxs-lookup"><span data-stu-id="c8abd-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="c8abd-142">W związku z tym wykorzystuje własny identyfikator może spowodować aby kompilator emituje ostrzeżenia i wstawić dodatkowe kontrole w celu zapewnienia, że elementów członkowskich obiektu nie są dostępne, zanim obiekt jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="c8abd-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="c8abd-143">Należy używać tylko własny identyfikator w `do` powiązania konstruktora podstawowego lub po `then` — słowo kluczowe w konstruktorach dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="c8abd-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="c8abd-144">Nazwa identyfikatora self nie ma być `this`.</span><span class="sxs-lookup"><span data-stu-id="c8abd-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="c8abd-145">Może być dowolnym prawidłowym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="c8abd-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="c8abd-146">Przypisywanie wartości do właściwości podczas inicjowania</span><span class="sxs-lookup"><span data-stu-id="c8abd-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="c8abd-147">Można przypisać wartości do właściwości obiektu klasy w kodzie inicjowania, dodając listę przypisań formularza `property = value` do listy argumentów dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8abd-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="c8abd-148">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c8abd-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="c8abd-149">Następująca wersja poprzedniego kodu ilustruje kombinacji zwykłych argumenty, opcjonalne argumenty i ustawienia właściwości w wywołaniu jeden konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c8abd-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="c8abd-150">Konstruktorów w klasie dziedziczonej</span><span class="sxs-lookup"><span data-stu-id="c8abd-150">Constructors in inherited class</span></span>

<span data-ttu-id="c8abd-151">Gdy dziedziczy z klasy podstawowej, która ma Konstruktor, należy określić argumenty w klauzuli dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="c8abd-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="c8abd-152">Aby uzyskać więcej informacji, zobacz [konstruktorów i dziedziczenie](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="c8abd-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="c8abd-153">Konstruktory statyczne lub konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="c8abd-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="c8abd-154">Oprócz określenia kodu do tworzenia obiektów statycznych `let` i `do` powiązania można tworzyć w typach klasy, które są wykonywane przed typ najpierw jest używany do wykonywania Inicjalizacja na poziomie typu.</span><span class="sxs-lookup"><span data-stu-id="c8abd-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="c8abd-155">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](let-bindings-in-classes.md) i [ `do` powiązania w klasach](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c8abd-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8abd-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8abd-156">See also</span></span>

- [<span data-ttu-id="c8abd-157">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c8abd-157">Members</span></span>](index.md)
