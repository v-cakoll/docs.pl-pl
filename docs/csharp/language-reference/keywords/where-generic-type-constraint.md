---
title: gdzie (ograniczenie typu ogólnego) - C# odwołania
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 8d6c1fba87ef1c4344bd150b2af2f5d1ad019695
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235722"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="8a9ce-102">where — Ograniczenie typu ogólnego (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8a9ce-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="8a9ce-103">`where` Klauzula w ogólne definicji określa ograniczenia na typy, które są używane jako argumenty dla parametrów typu w typ ogólny, metoda, delegata lub funkcja lokalna.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="8a9ce-104">Ograniczenia można określić interfejsy, klasy bazowe lub wymaga użycia typu ogólnego być odwołaniem, wartością lub typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="8a9ce-105">Które deklarują funkcje, które musi posiadać argument typu.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="8a9ce-106">Na przykład, można zadeklarować klasy ogólnej `MyGenericClass`, w taki sposób, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="8a9ce-107">Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzula](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8a9ce-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="8a9ce-108">`where` Klauzuli mogą również zawierać ograniczenia klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="8a9ce-109">Ograniczenie klasy bazowej stwierdzający, że typ ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę bazową (lub jest to, że klasa bazowa) ma być używany jako argument typu dla tego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="8a9ce-110">Jeśli jest używany do ograniczenia klasy bazowej, musi znajdować się przed wszystkimi innymi ograniczeniami dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="8a9ce-111">Niektóre typy są niedozwolone jako ograniczenie klasy bazowej: <xref:System.Object>, <xref:System.Array>, i <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="8a9ce-112">Przed C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, i <xref:System.MulticastDelegate> zostały również niedozwolone jako warunki ograniczające klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="8a9ce-113">Poniższy przykład przedstawia typy, które można teraz określić jako klasa bazowa:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="8a9ce-114">`where` Klauzuli można określić, czy typ jest `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="8a9ce-115">`struct` Ograniczenie usuwa potrzebę określenia ograniczenie klasy bazowej `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="8a9ce-116">`System.ValueType` Typ nie może być używany jako ograniczenie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="8a9ce-117">W poniższym przykładzie pokazano oba `class` i `struct` ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="8a9ce-118">`where` Klauzuli mogą również obejmować `unmanaged` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="8a9ce-119">`unmanaged` Ograniczenie ogranicza parametr typu dla typów znane jako **niezarządzanych typów**.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="8a9ce-120">**Niezarządzany typ** to typ, który nie jest typem odwołania i nie zawiera pola typu odwołania na każdym poziomie zagnieżdżania.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="8a9ce-121">`unmanaged` Ograniczenie ułatwia pisanie niskiego poziomu międzyoperacyjnego kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="8a9ce-122">Pozwala to uzyskać wielokrotnego użytku procedury dla wszystkich typów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="8a9ce-123">`unmanaged` Ograniczenia nie można łączyć z `class` lub `struct` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="8a9ce-124">`unmanaged` Ograniczenie wymusza na to, że typ musi być `struct`:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="8a9ce-125">`where` Klauzuli mogą również obejmować ograniczenie konstruktora `new()`.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="8a9ce-126">Czy ograniczenie sprawia, że można utworzyć wystąpienia typu parametru przy użyciu `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="8a9ce-127">[Ograniczenia new()](new-constraint.md) informuje kompilator, wiedzieć, że wszelkie podany argument typu musi mieć dostępne bez parametrów — lub konstruktora domyślnego —.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="8a9ce-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="8a9ce-129">`new()` Ograniczenia pojawia się ostatni w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="8a9ce-130">`new()` Ograniczenia nie można łączyć z `struct` lub `unmanaged` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="8a9ce-131">Wszystkie typy spełniającej te ograniczenia musi być dostępny konstruktora bez parametrów, dzięki czemu `new()` ograniczenie nadmiarowe.</span><span class="sxs-lookup"><span data-stu-id="8a9ce-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="8a9ce-132">Z wieloma parametrami typu, użyj jednej `where` klauzulę dla każdego parametru typu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="8a9ce-133">Można również dołączyć ograniczenia na parametry metod rodzajowych typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="8a9ce-134">Zauważ, że opis ograniczenia parametru typu delegatów składni takie same jak w przypadku metod:</span><span class="sxs-lookup"><span data-stu-id="8a9ce-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="8a9ce-135">Aby uzyskać informacji na temat delegatów, zobacz [delegatów ogólnych](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="8a9ce-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="8a9ce-136">Aby uzyskać szczegółowe informacje o składni i użycia ograniczeń, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8a9ce-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8a9ce-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a9ce-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8a9ce-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a9ce-138">See also</span></span>

- [<span data-ttu-id="8a9ce-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a9ce-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8a9ce-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a9ce-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8a9ce-141">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="8a9ce-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="8a9ce-142">new, ograniczenie</span><span class="sxs-lookup"><span data-stu-id="8a9ce-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
- [<span data-ttu-id="8a9ce-143">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="8a9ce-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
