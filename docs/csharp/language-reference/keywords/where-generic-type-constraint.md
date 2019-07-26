---
title: WHERE (ograniczenie typu ogólnego) — C# odwołanie
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: bccc22f5362b22540dadf08e6b21a07cbc578327
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433866"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="5a53a-102">where — Ograniczenie typu ogólnego (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a53a-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="5a53a-103">`where` Klauzula w definicji ogólnej określa ograniczenia dotyczące typów, które są używane jako argumenty parametrów typu w typie ogólnym, metodzie, delegatze lub funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5a53a-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="5a53a-104">Ograniczenia mogą określać interfejsy, klasy bazowe lub wymagać typu ogólnego, aby być odwołaniem, wartością lub typem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5a53a-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="5a53a-105">Deklarują możliwości, że argument typu musi mieć wartość.</span><span class="sxs-lookup"><span data-stu-id="5a53a-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="5a53a-106">Na przykład można zadeklarować klasę `MyGenericClass`generyczną, w taki sposób, aby parametr `T` typu implementuje <xref:System.IComparable%601> interfejs:</span><span class="sxs-lookup"><span data-stu-id="5a53a-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="5a53a-107">Aby uzyskać więcej informacji na temat klauzuli WHERE w wyrażeniu zapytania, zobacz [klauzula WHERE](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5a53a-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="5a53a-108">`where` Klauzula może również zawierać ograniczenie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5a53a-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="5a53a-109">Ograniczenie klasy bazowej określa, że typ, który ma być używany jako argument typu dla tego typu ogólnego ma określoną klasę jako klasę bazową (lub jest tą klasą bazową), która ma być używana jako argument typu dla tego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="5a53a-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="5a53a-110">Jeśli jest używane ograniczenie klasy bazowej, musi ono znajdować się przed innymi ograniczeniami tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="5a53a-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="5a53a-111">Niektóre typy są niedozwolone jako ograniczenie klasy bazowej: <xref:System.Object>, <xref:System.Array>, i <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="5a53a-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="5a53a-112">Przed C# 7,3, <xref:System.Enum> <xref:System.Delegate>, i<xref:System.MulticastDelegate> były również niedozwolone jako ograniczenia klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="5a53a-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="5a53a-113">W poniższym przykładzie przedstawiono typy, które można teraz określić jako klasę bazową:</span><span class="sxs-lookup"><span data-stu-id="5a53a-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="5a53a-114">Klauzula może określać, że typem `class` jest lub `struct`. `where`</span><span class="sxs-lookup"><span data-stu-id="5a53a-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="5a53a-115">Ograniczenie eliminuje konieczność określenia `System.ValueType`ograniczenia klasy bazowej. `struct`</span><span class="sxs-lookup"><span data-stu-id="5a53a-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="5a53a-116">`System.ValueType` Typ nie może być używany jako ograniczenie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5a53a-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="5a53a-117">W poniższym przykładzie przedstawiono zarówno `class` warunek, jak i: `struct`</span><span class="sxs-lookup"><span data-stu-id="5a53a-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="5a53a-118">Klauzula może również `unmanaged` zawierać ograniczenie. `where`</span><span class="sxs-lookup"><span data-stu-id="5a53a-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="5a53a-119">Ograniczenie ogranicza parametr typu do typów znanych jako [typy niezarządzane.](../builtin-types/unmanaged-types.md) `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="5a53a-119">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="5a53a-120">To `unmanaged` ograniczenie ułatwia zapisanie kodu międzyoperacyjności niskiego poziomu w C#programie.</span><span class="sxs-lookup"><span data-stu-id="5a53a-120">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="5a53a-121">To ograniczenie umożliwia wykonywanie procedur wielokrotnego użytku we wszystkich typach niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="5a53a-121">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="5a53a-122">Nie można połączyć `class` `struct` ograniczenia z ograniczeniem or. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="5a53a-122">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="5a53a-123">Ograniczenie wymusza, że typ musi `struct`być: `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="5a53a-123">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="5a53a-124">Klauzula może również zawierać `new()`ograniczenie konstruktora. `where`</span><span class="sxs-lookup"><span data-stu-id="5a53a-124">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="5a53a-125">To ograniczenie umożliwia utworzenie wystąpienia parametru typu za pomocą `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="5a53a-125">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="5a53a-126">To [ograniczenie New ()](new-constraint.md) umożliwia kompilatorowi, że każdy dostarczony argument typu musi mieć dostępny bez parametrów--lub default--konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5a53a-126">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="5a53a-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5a53a-127">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="5a53a-128">Ograniczenie jest wyświetlane jako ostatnie `where` w klauzuli. `new()`</span><span class="sxs-lookup"><span data-stu-id="5a53a-128">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="5a53a-129">Nie można połączyć `struct` `unmanaged` ograniczenia z ograniczeniami lub. `new()`</span><span class="sxs-lookup"><span data-stu-id="5a53a-129">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="5a53a-130">Wszystkie typy spełniające te ograniczenia muszą mieć dostępny Konstruktor bez parametrów, co sprawia, `new()` że ograniczenie jest nadmiarowe.</span><span class="sxs-lookup"><span data-stu-id="5a53a-130">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="5a53a-131">W przypadku wielu parametrów typu należy użyć `where` jednej klauzuli dla każdego parametru typu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="5a53a-131">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="5a53a-132">Można również dołączyć ograniczenia do parametrów typu metod ogólnych, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5a53a-132">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="5a53a-133">Zauważ, że składnia opisująca ograniczenia parametru typu dla delegatów jest taka sama jak w przypadku metod:</span><span class="sxs-lookup"><span data-stu-id="5a53a-133">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="5a53a-134">Aby uzyskać informacje na temat delegatów ogólnych, zobacz [Delegaty ogólne](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="5a53a-134">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="5a53a-135">Aby uzyskać szczegółowe informacje na temat składni i użycia ograniczeń, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5a53a-135">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5a53a-136">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a53a-136">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5a53a-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a53a-137">See also</span></span>

- [<span data-ttu-id="5a53a-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a53a-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="5a53a-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5a53a-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5a53a-140">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="5a53a-140">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="5a53a-141">new, ograniczenie</span><span class="sxs-lookup"><span data-stu-id="5a53a-141">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
- [<span data-ttu-id="5a53a-142">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="5a53a-142">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
