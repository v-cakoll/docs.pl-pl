---
title: Klasy częściowe i metody — Przewodnik programowania w języku C#
description: Klasy częściowe i metody w języku C# dzielą definicję klasy, struktury, interfejsu lub metody na ponad dwa pliki źródłowe.
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 792159786131654d6ee0363f7ab7b87ac50d32bb
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864751"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="13509-103">Klasy częściowe i metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="13509-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="13509-104">Istnieje możliwość podziału definicji [klasy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md), [interfejsu](../../language-reference/keywords/interface.md) lub metody na więcej niż dwa pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="13509-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="13509-105">Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie części są łączone podczas kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13509-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="13509-106">Klasy częściowe</span><span class="sxs-lookup"><span data-stu-id="13509-106">Partial Classes</span></span>

<span data-ttu-id="13509-107">Istnieje kilka sytuacji, w których pożądana jest podział definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="13509-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="13509-108">Podczas pracy nad dużymi projektami rozłożenie klasy na osobne pliki umożliwia wielu programistom jednoczesną pracę nad nią.</span><span class="sxs-lookup"><span data-stu-id="13509-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="13509-109">Podczas pracy z automatycznie generowanym źródłem kod można dodać do klasy bez konieczności ponownego tworzenia pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="13509-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="13509-110">Program Visual Studio używa tego podejścia, gdy tworzy Windows Forms, kod otoki usługi sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="13509-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="13509-111">Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13509-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="13509-112">Aby podzielić definicję klasy, użyj modyfikatora [częściowego](../../language-reference/keywords/partial-type.md) słowa kluczowego, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="13509-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="13509-113">`partial`Słowo kluczowe wskazuje, że w przestrzeni nazw można definiować inne części klasy, struktury lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="13509-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="13509-114">Wszystkie części muszą używać `partial` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="13509-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="13509-115">Wszystkie części muszą być dostępne w czasie kompilacji w celu utworzenia typu końcowego.</span><span class="sxs-lookup"><span data-stu-id="13509-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="13509-116">Wszystkie części muszą mieć tę samą dostępność, taką jak `public` , `private` , i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="13509-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="13509-117">Jeśli jakakolwiek część jest zadeklarowana jako abstract, cały typ jest uznawany za abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="13509-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="13509-118">Jeśli jakakolwiek część jest zadeklarowana jako Sealed, cały typ jest uznawany za zapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="13509-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="13509-119">Jeśli jakakolwiek część deklaruje typ podstawowy, cały typ dziedziczy tę klasę.</span><span class="sxs-lookup"><span data-stu-id="13509-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="13509-120">Wszystkie części określające klasę bazową muszą wyrazić zgodę, ale części, które pomijają klasę bazową, nadal dziedziczą typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="13509-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="13509-121">Części mogą określać różne interfejsy podstawowe, a końcowy typ implementuje wszystkie interfejsy wymienione przez wszystkie częściowe deklaracje.</span><span class="sxs-lookup"><span data-stu-id="13509-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="13509-122">Każdy element członkowski klasy, struktury lub interfejsu zadeklarowany w częściowej definicji jest dostępny dla wszystkich innych części.</span><span class="sxs-lookup"><span data-stu-id="13509-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="13509-123">Ostatni typ to kombinacja wszystkich części w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13509-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="13509-124">`partial`Modyfikator nie jest dostępny w deklaracjach delegata lub wyliczania.</span><span class="sxs-lookup"><span data-stu-id="13509-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="13509-125">Poniższy przykład pokazuje, że zagnieżdżone typy mogą być częścią, nawet jeśli typ, w którym są zagnieżdżone, nie jest częścią.</span><span class="sxs-lookup"><span data-stu-id="13509-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="13509-126">W czasie kompilacji atrybuty częściowych definicji typu są scalane.</span><span class="sxs-lookup"><span data-stu-id="13509-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="13509-127">Rozważmy na przykład następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="13509-127">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="13509-128">Są one równoważne z następującymi deklaracjami:</span><span class="sxs-lookup"><span data-stu-id="13509-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="13509-129">Następujące elementy zostały scalone ze wszystkich definicji typów częściowych:</span><span class="sxs-lookup"><span data-stu-id="13509-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="13509-130">Komentarze XML</span><span class="sxs-lookup"><span data-stu-id="13509-130">XML comments</span></span>

- <span data-ttu-id="13509-131">interfejsy</span><span class="sxs-lookup"><span data-stu-id="13509-131">interfaces</span></span>

- <span data-ttu-id="13509-132">atrybuty parametru typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="13509-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="13509-133">class — Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13509-133">class attributes</span></span>

- <span data-ttu-id="13509-134">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="13509-134">members</span></span>

<span data-ttu-id="13509-135">Rozważmy na przykład następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="13509-135">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="13509-136">Są one równoważne z następującymi deklaracjami:</span><span class="sxs-lookup"><span data-stu-id="13509-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="13509-137">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="13509-137">Restrictions</span></span>

<span data-ttu-id="13509-138">Istnieje kilka reguł, które należy wykonać podczas pracy ze częściowymi definicjami klas:</span><span class="sxs-lookup"><span data-stu-id="13509-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="13509-139">Wszystkie definicje typu częściowego, które powinny być częściami tego samego typu, muszą być modyfikowane przy użyciu `partial` .</span><span class="sxs-lookup"><span data-stu-id="13509-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="13509-140">Na przykład następujące deklaracje klas generują błąd:</span><span class="sxs-lookup"><span data-stu-id="13509-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="13509-141">`partial`Modyfikator może występować tylko bezpośrednio przed słowami kluczowymi `class` , `struct` lub `interface` .</span><span class="sxs-lookup"><span data-stu-id="13509-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="13509-142">Zagnieżdżone typy częściowe są dozwolone w definicjach typów częściowych, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="13509-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="13509-143">Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być zdefiniowane w tym samym zestawie i w tym samym module (pliku exe lub. dll).</span><span class="sxs-lookup"><span data-stu-id="13509-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="13509-144">Definicje częściowe nie mogą obejmować wielu modułów.</span><span class="sxs-lookup"><span data-stu-id="13509-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="13509-145">Parametry nazwy klasy i typu ogólnego muszą być zgodne ze wszystkimi definicjami częściowych typów.</span><span class="sxs-lookup"><span data-stu-id="13509-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="13509-146">Typy ogólne mogą być częściowe.</span><span class="sxs-lookup"><span data-stu-id="13509-146">Generic types can be partial.</span></span> <span data-ttu-id="13509-147">Każda deklaracja częściowa musi używać tych samych nazw parametrów w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="13509-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="13509-148">Następujące słowa kluczowe w definicji częściowej typu są opcjonalne, ale jeśli są obecne w jednej definicji częściowej, nie mogą powodować konfliktu ze słowami kluczowymi określonymi w innej definicji częściowej dla tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="13509-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="13509-149">public</span><span class="sxs-lookup"><span data-stu-id="13509-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="13509-150">private</span><span class="sxs-lookup"><span data-stu-id="13509-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="13509-151">protected</span><span class="sxs-lookup"><span data-stu-id="13509-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="13509-152">internal</span><span class="sxs-lookup"><span data-stu-id="13509-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="13509-153">streszczeń</span><span class="sxs-lookup"><span data-stu-id="13509-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="13509-154">sealed</span><span class="sxs-lookup"><span data-stu-id="13509-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="13509-155">klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="13509-155">base class</span></span>

  - <span data-ttu-id="13509-156">[New](../../language-reference/keywords/new-modifier.md) — modyfikator (części zagnieżdżone)</span><span class="sxs-lookup"><span data-stu-id="13509-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="13509-157">Ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="13509-157">generic constraints</span></span>

<span data-ttu-id="13509-158">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="13509-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="13509-159">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="13509-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="13509-160">Opis</span><span class="sxs-lookup"><span data-stu-id="13509-160">Description</span></span>

<span data-ttu-id="13509-161">W poniższym przykładzie pola i Konstruktor klasy, `Coords` ,, są zadeklarowane w jednej częściowej definicji klasy, a element członkowski, `PrintCoords` , jest zadeklarowany w innej definicji klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="13509-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="13509-162">Kod</span><span class="sxs-lookup"><span data-stu-id="13509-162">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="13509-163">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="13509-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="13509-164">Opis</span><span class="sxs-lookup"><span data-stu-id="13509-164">Description</span></span>

<span data-ttu-id="13509-165">Poniższy przykład pokazuje, że można również opracowywać częściowe struktury i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="13509-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="13509-166">Kod</span><span class="sxs-lookup"><span data-stu-id="13509-166">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="13509-167">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="13509-167">Partial Methods</span></span>

<span data-ttu-id="13509-168">Częściowa Klasa lub struktura mogą zawierać metodę częściową.</span><span class="sxs-lookup"><span data-stu-id="13509-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="13509-169">Jedna część klasy zawiera podpis metody.</span><span class="sxs-lookup"><span data-stu-id="13509-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="13509-170">Opcjonalna implementacja może być zdefiniowana w tej samej części lub innej części.</span><span class="sxs-lookup"><span data-stu-id="13509-170">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="13509-171">Jeśli implementacja nie zostanie podana, Metoda i wszystkie wywołania metody są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13509-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="13509-172">Metody częściowe umożliwiają implementowanie jednej części klasy w celu zdefiniowania metody, podobnej do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13509-172">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="13509-173">Realizator drugiej części klasy może zdecydować, czy zaimplementować metodę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="13509-173">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="13509-174">Jeśli metoda nie jest zaimplementowana, kompilator usuwa sygnaturę metody i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="13509-174">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="13509-175">Wywołania metody, w tym wszelkie wyniki, które byłyby wynikiem oceny argumentów w wywołaniach, nie mają wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13509-175">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="13509-176">W związku z tym, każdy kod w klasie częściowej może swobodnie korzystać z metody częściowej, nawet jeśli implementacja nie została podana.</span><span class="sxs-lookup"><span data-stu-id="13509-176">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="13509-177">Jeśli metoda zostanie wywołana, ale nie została zaimplementowana, nie zostaną wykryte błędy w czasie kompilacji ani w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13509-177">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="13509-178">Metody częściowe są szczególnie przydatne jako sposób dostosowywania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="13509-178">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="13509-179">Umożliwiają one zarezerwowanie nazwy metody i podpisu, aby wygenerowany kod mógł wywołać metodę, ale deweloper może zdecydować, czy zaimplementować metodę.</span><span class="sxs-lookup"><span data-stu-id="13509-179">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="13509-180">Podobnie jak klasy częściowe, metody częściowe umożliwiają kod utworzony przez generator kodu i kod utworzony przez dewelopera ludzkiego do pracy bez kosztów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13509-180">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="13509-181">Deklaracja metody częściowej składa się z dwóch części: definicji i implementacji.</span><span class="sxs-lookup"><span data-stu-id="13509-181">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="13509-182">Mogą one znajdować się w osobnych częściach klasy częściowej lub w tej samej części.</span><span class="sxs-lookup"><span data-stu-id="13509-182">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="13509-183">W przypadku braku deklaracji implementacji kompilator optymalizuje zarówno deklarację definiującą, jak i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="13509-183">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="13509-184">Deklaracje metody częściowej muszą zaczynać się od kontekstowego słowa kluczowego [częściowego](../../language-reference/keywords/partial-type.md) , a metoda musi zwracać [typ void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="13509-184">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="13509-185">Metody częściowe mogą mieć parametry [in](../../language-reference/keywords/in-parameter-modifier.md) lub [ref](../../language-reference/keywords/ref.md) , ale nie [out](../../language-reference/keywords/out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="13509-185">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="13509-186">Metody częściowe są niejawnie [prywatne](../../language-reference/keywords/private.md)i dlatego nie mogą być [wirtualne](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="13509-186">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="13509-187">Metody częściowe nie mogą być [extern](../../language-reference/keywords/extern.md), ponieważ obecność treści określa, czy są one definiowane lub implementowane.</span><span class="sxs-lookup"><span data-stu-id="13509-187">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="13509-188">Metody częściowe mogą mieć Modyfikatory [static](../../language-reference/keywords/static.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="13509-188">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="13509-189">Metody częściowe mogą być ogólne.</span><span class="sxs-lookup"><span data-stu-id="13509-189">Partial methods can be generic.</span></span> <span data-ttu-id="13509-190">Ograniczenia są umieszczane w deklaracji metody częściowej i opcjonalnie mogą być powtórzone na implementującej ją.</span><span class="sxs-lookup"><span data-stu-id="13509-190">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="13509-191">Nazwy parametrów parametrów i typów nie muszą być takie same w deklaracji implementującej, jak w definicji.</span><span class="sxs-lookup"><span data-stu-id="13509-191">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="13509-192">Można utworzyć [Delegat](../../language-reference/builtin-types/reference-types.md) do metody częściowej, która została zdefiniowana i zaimplementowana, ale nie do metody częściowej, która została zdefiniowana tylko.</span><span class="sxs-lookup"><span data-stu-id="13509-192">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="13509-193">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="13509-193">C# Language Specification</span></span>

<span data-ttu-id="13509-194">Aby uzyskać więcej informacji, zobacz [typy częściowe](~/_csharplang/spec/classes.md#partial-types) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="13509-194">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="13509-195">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="13509-195">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="13509-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13509-196">See also</span></span>

- [<span data-ttu-id="13509-197">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13509-197">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13509-198">Klasy</span><span class="sxs-lookup"><span data-stu-id="13509-198">Classes</span></span>](./classes.md)
- [<span data-ttu-id="13509-199">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="13509-199">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="13509-200">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="13509-200">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="13509-201">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="13509-201">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
