---
title: where — Ograniczenie typu ogólnego (odwołanie w C#)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 94db10c81af55030dfcf6e210a86658c84868e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="4ea39-102">where — Ograniczenie typu ogólnego (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4ea39-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="4ea39-103">`where` w ogólną definicję klauzuli określa ograniczenia dotyczące typów, które są używane jako argumenty dla parametrów typu w typu ogólnego, metody, delegat lub funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="4ea39-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="4ea39-104">Ograniczenia można określić interfejsów, klas podstawowych lub wymagają ogólnego typu odwołania, wartości ani typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4ea39-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="4ea39-105">Zadeklarować ich możliwości, które musi posiadać argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="4ea39-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="4ea39-106">Na przykład można zadeklarować klasy ogólnej, `MyGenericClass`, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4ea39-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="4ea39-107">Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzuli](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4ea39-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="4ea39-108">`where` Klauzuli mogą również obejmować ograniczenia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4ea39-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="4ea39-109">Ograniczenie klasy podstawowej stwierdza, że typ ma być używany jako typ argumentu dla tego typu ogólnego ma określonej klasy jako klasę podstawową (lub jest to, że klasa podstawowa) ma być używany jako typ argumentu dla tego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4ea39-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="4ea39-110">Jeśli używane jest ograniczenie klasy podstawowej, musi występować przed wszystkimi innymi ograniczeniami dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="4ea39-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="4ea39-111">Niektóre typy są niedozwolone jako ograniczenie klasy podstawowej: <xref:System.Object>, <xref:System.Array>, i <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4ea39-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="4ea39-112">Przed C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, i <xref:System.MulticastDelegate> zostały również zgłoszenia ograniczenia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4ea39-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="4ea39-113">W poniższym przykładzie przedstawiono typy, które teraz mogą być określone jako klasy podstawowej:</span><span class="sxs-lookup"><span data-stu-id="4ea39-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="4ea39-114">`where` Klauzuli można określić, czy ten typ jest `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="4ea39-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="4ea39-115">`struct` Ograniczenia usuwa konieczności określania z ograniczeniem klasy podstawowej `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="4ea39-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="4ea39-116">`System.ValueType` Typu nie może być używany jako ograniczenie klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4ea39-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="4ea39-117">W poniższym przykładzie przedstawiono oba `class` i `struct` ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4ea39-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="4ea39-118">`where` Klauzuli mogą również obejmować `unmanaged` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4ea39-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="4ea39-119">`unmanaged` Ograniczenia ogranicza parametr typu do typów znany jako **niezarządzanych typy**.</span><span class="sxs-lookup"><span data-stu-id="4ea39-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="4ea39-120">**Niezarządzany typ** jest typ, który nie jest typem referencyjnym i nie zawiera odwołanie do pola typu na dowolnym poziomie zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="4ea39-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="4ea39-121">`unmanaged` Ograniczenia ułatwia pisanie niskiego poziomu międzyoperacyjnego kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="4ea39-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="4ea39-122">To ograniczenie umożliwia wielokrotnego użytku procedury wszystkich typów niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="4ea39-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="4ea39-123">`unmanaged` Ograniczenia nie można połączyć z `class` lub `struct` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4ea39-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="4ea39-124">`unmanaged` Ograniczenie wymusza musi być typu `struct`:</span><span class="sxs-lookup"><span data-stu-id="4ea39-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="4ea39-125">`where` Klauzuli mogą również obejmować ograniczenie konstruktora `new()`.</span><span class="sxs-lookup"><span data-stu-id="4ea39-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="4ea39-126">Czy ograniczenia umożliwia utworzenie wystąpienia parametru typu przy użyciu `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="4ea39-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="4ea39-127">[Ograniczenia new()](new-constraint.md) umożliwia kompilatora wiedzieć, że wszelkie argumentu typu dostarczonego musi mieć dostęp bez parametrów--lub konstruktora domyślnego —.</span><span class="sxs-lookup"><span data-stu-id="4ea39-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="4ea39-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4ea39-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="4ea39-129">`new()` Ograniczenia pojawia się w ostatniej `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4ea39-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="4ea39-130">`new()` Ograniczenia nie można połączyć z `struct` lub `unmanaged` ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4ea39-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="4ea39-131">Wszystkie typy spełniające te ograniczenia musi mieć konstruktora bez parametrów dostępny, przez co `new()` nadmiarowe ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="4ea39-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="4ea39-132">Wiele parametrów typu, za pomocą jednego `where` klauzula dla każdego parametru typu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="4ea39-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="4ea39-133">Można również dołączyć ograniczenia na parametry metody ogólne typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4ea39-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="4ea39-134">Zauważ, że opis ograniczenia parametru typu delegatów składni jest takie samo jak w przypadku metod:</span><span class="sxs-lookup"><span data-stu-id="4ea39-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="4ea39-135">Informacje ogólne delegatów, zobacz [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4ea39-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="4ea39-136">Aby uzyskać więcej informacji o składni i użycia ograniczenia, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4ea39-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4ea39-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4ea39-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4ea39-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ea39-138">See also</span></span>

 [<span data-ttu-id="4ea39-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4ea39-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4ea39-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4ea39-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4ea39-141">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="4ea39-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="4ea39-142">new, ograniczenie</span><span class="sxs-lookup"><span data-stu-id="4ea39-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="4ea39-143">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="4ea39-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
