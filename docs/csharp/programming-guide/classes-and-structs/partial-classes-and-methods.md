---
title: Częściowe klasy i metody — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399820"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="afc99-102">Klasy częściowe i metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="afc99-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="afc99-103">Istnieje możliwość podzielenia definicji [klasy,](../../language-reference/keywords/class.md) [struktury,](../../language-reference/builtin-types/struct.md) [interfejsu](../../language-reference/keywords/interface.md) lub metody na dwa lub więcej plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="afc99-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="afc99-104">Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie części są łączone po skompilowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afc99-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="afc99-105">Klasy częściowe</span><span class="sxs-lookup"><span data-stu-id="afc99-105">Partial Classes</span></span>

<span data-ttu-id="afc99-106">Istnieje kilka sytuacji, gdy dzielenie definicji klasy jest pożądane:</span><span class="sxs-lookup"><span data-stu-id="afc99-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="afc99-107">Podczas pracy nad dużymi projektami rozłożenie klasy na oddzielne pliki umożliwia wielu programistom pracę nad nią w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="afc99-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="afc99-108">Podczas pracy z automatycznie generowanym źródłem kod można dodać do klasy bez konieczności ponownego tworzenia pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="afc99-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="afc99-109">Visual Studio używa tej metody, gdy tworzy formularze systemu Windows, kod otoki usługi sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="afc99-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="afc99-110">Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="afc99-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="afc99-111">Aby podzielić definicję klasy, użyj modyfikatora [częściowego](../../language-reference/keywords/partial-type.md) słowa kluczowego, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="afc99-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="afc99-112">Słowo `partial` kluczowe wskazuje, że inne części klasy, struktury lub interfejsu można zdefiniować w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="afc99-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="afc99-113">Wszystkie części muszą `partial` używać słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="afc99-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="afc99-114">Wszystkie części muszą być dostępne w czasie kompilacji, aby utworzyć ostateczny typ.</span><span class="sxs-lookup"><span data-stu-id="afc99-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="afc99-115">Wszystkie części muszą mieć taką samą dostępność, taką jak `public`, `private`, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="afc99-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="afc99-116">Jeśli dowolna część jest zadeklarowana jako abstrakcyjna, cały typ jest uważany za abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="afc99-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="afc99-117">Jeśli jakakolwiek część jest zadeklarowana jako zapieczętowana, cały typ jest uważany za zapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="afc99-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="afc99-118">Jeśli dowolna część deklaruje typ podstawowy, cały typ dziedziczy tę klasę.</span><span class="sxs-lookup"><span data-stu-id="afc99-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="afc99-119">Wszystkie części, które określają klasę podstawową musi zgadzać się, ale części, które pomijają klasę podstawową nadal dziedziczą typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="afc99-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="afc99-120">Części można określić różne interfejsy podstawowe, a ostateczny typ implementuje wszystkie interfejsy wymienione przez wszystkie deklaracje częściowe.</span><span class="sxs-lookup"><span data-stu-id="afc99-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="afc99-121">Wszystkie klasy, struktury lub elementy członkowskie interfejsu zadeklarowane w definicji częściowej są dostępne dla wszystkich innych części.</span><span class="sxs-lookup"><span data-stu-id="afc99-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="afc99-122">Typ końcowy jest kombinacją wszystkich części w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="afc99-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="afc99-123">Modyfikator `partial` nie jest dostępny na deklaracje delegata lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="afc99-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="afc99-124">W poniższym przykładzie pokazano, że typy zagnieżdżone mogą być częściowe, nawet jeśli typ, w których są zagnieżdżone, nie jest sam częściowy.</span><span class="sxs-lookup"><span data-stu-id="afc99-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="afc99-125">W czasie kompilacji atrybuty definicji typu częściowego są scalane.</span><span class="sxs-lookup"><span data-stu-id="afc99-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="afc99-126">Rozważmy na przykład następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="afc99-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="afc99-127">Są one równoważne następującym deklaracjom:</span><span class="sxs-lookup"><span data-stu-id="afc99-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="afc99-128">Ze wszystkich definicji typu częściowego są scalane następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="afc99-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="afc99-129">komentarze XML</span><span class="sxs-lookup"><span data-stu-id="afc99-129">XML comments</span></span>

- <span data-ttu-id="afc99-130">interfejsy</span><span class="sxs-lookup"><span data-stu-id="afc99-130">interfaces</span></span>

- <span data-ttu-id="afc99-131">atrybuty parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="afc99-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="afc99-132">class — Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afc99-132">class attributes</span></span>

- <span data-ttu-id="afc99-133">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="afc99-133">members</span></span>

<span data-ttu-id="afc99-134">Rozważmy na przykład następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="afc99-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="afc99-135">Są one równoważne następującym deklaracjom:</span><span class="sxs-lookup"><span data-stu-id="afc99-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="afc99-136">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="afc99-136">Restrictions</span></span>

<span data-ttu-id="afc99-137">Podczas pracy z definicjami klas częściowych należy przestrzegać kilku reguł:</span><span class="sxs-lookup"><span data-stu-id="afc99-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="afc99-138">Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być modyfikowane za pomocą `partial`.</span><span class="sxs-lookup"><span data-stu-id="afc99-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="afc99-139">Na przykład następujące deklaracje klas generują błąd:</span><span class="sxs-lookup"><span data-stu-id="afc99-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="afc99-140">`partial` Modyfikator może pojawić się `class`tylko `struct`bezpośrednio `interface`przed słowami kluczowymi , lub .</span><span class="sxs-lookup"><span data-stu-id="afc99-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="afc99-141">Zagnieżdżone typy częściowe są dozwolone w definicjach typu częściowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="afc99-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="afc99-142">Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być zdefiniowane w tym samym zestawie i tym samym module (plik exe lub dll).</span><span class="sxs-lookup"><span data-stu-id="afc99-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="afc99-143">Definicje częściowe nie mogą obejmujeć wielu modułów.</span><span class="sxs-lookup"><span data-stu-id="afc99-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="afc99-144">Nazwa klasy i parametry typu ogólnego muszą być zgodne we wszystkich definicjach typu częściowego.</span><span class="sxs-lookup"><span data-stu-id="afc99-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="afc99-145">Typy ogólne mogą być częściowe.</span><span class="sxs-lookup"><span data-stu-id="afc99-145">Generic types can be partial.</span></span> <span data-ttu-id="afc99-146">Każda deklaracja częściowa musi używać tych samych nazw parametrów w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="afc99-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="afc99-147">Następujące słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli są obecne w jednej definicji typu częściowego, nie może kolidować ze słowami kluczowymi określonymi w innej definicji częściowej dla tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="afc99-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="afc99-148">Publicznego</span><span class="sxs-lookup"><span data-stu-id="afc99-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="afc99-149">Prywatny</span><span class="sxs-lookup"><span data-stu-id="afc99-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="afc99-150">protected</span><span class="sxs-lookup"><span data-stu-id="afc99-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="afc99-151">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="afc99-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="afc99-152">Abstrakcja</span><span class="sxs-lookup"><span data-stu-id="afc99-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="afc99-153">sealed</span><span class="sxs-lookup"><span data-stu-id="afc99-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="afc99-154">klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="afc99-154">base class</span></span>

  - <span data-ttu-id="afc99-155">[nowy](../../language-reference/keywords/new-modifier.md) modyfikator (zagnieżdżone części)</span><span class="sxs-lookup"><span data-stu-id="afc99-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="afc99-156">ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="afc99-156">generic constraints</span></span>

<span data-ttu-id="afc99-157">Aby uzyskać więcej informacji, zobacz [Ograniczenia parametrów typu](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="afc99-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="afc99-158">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="afc99-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="afc99-159">Opis</span><span class="sxs-lookup"><span data-stu-id="afc99-159">Description</span></span>

<span data-ttu-id="afc99-160">W poniższym przykładzie pola i konstruktor `Coords`klasy , są zadeklarowane w jednej `PrintCoords`definicji klasy częściowej, a element członkowski , jest zadeklarowany w innej definicji klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="afc99-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="afc99-161">Code</span><span class="sxs-lookup"><span data-stu-id="afc99-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="afc99-162">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="afc99-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="afc99-163">Opis</span><span class="sxs-lookup"><span data-stu-id="afc99-163">Description</span></span>

<span data-ttu-id="afc99-164">W poniższym przykładzie pokazano, że można również opracować częściowe struktury i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="afc99-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="afc99-165">Code</span><span class="sxs-lookup"><span data-stu-id="afc99-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="afc99-166">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="afc99-166">Partial Methods</span></span>

<span data-ttu-id="afc99-167">Klasa częściowa lub struktura może zawierać metodę częściową.</span><span class="sxs-lookup"><span data-stu-id="afc99-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="afc99-168">Jedna część klasy zawiera podpis metody.</span><span class="sxs-lookup"><span data-stu-id="afc99-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="afc99-169">Opcjonalna implementacja może być zdefiniowana w tej samej części lub innej części.</span><span class="sxs-lookup"><span data-stu-id="afc99-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="afc99-170">Jeśli implementacja nie jest dostarczana, a następnie metody i wszystkie wywołania metody są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="afc99-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="afc99-171">Metody częściowe umożliwiają realizatorowi jednej części klasy zdefiniowanie metody, podobnej do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="afc99-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="afc99-172">Realizator drugiej części klasy może zdecydować, czy zaimplementować metodę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="afc99-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="afc99-173">Jeśli metoda nie jest zaimplementowana, kompilator usuwa podpis metody i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="afc99-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="afc99-174">Wywołania metody, w tym wszystkie wyniki, które mogłyby wystąpić z oceny argumentów w wywołaniach, nie mają wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="afc99-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="afc99-175">W związku z tym dowolny kod w klasie częściowej można swobodnie używać metody częściowej, nawet jeśli implementacja nie jest dostarczana.</span><span class="sxs-lookup"><span data-stu-id="afc99-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="afc99-176">Brak błędów w czasie kompilacji lub w czasie wykonywania spowoduje, jeśli metoda jest wywoływana, ale nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="afc99-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="afc99-177">Metody częściowe są szczególnie przydatne jako sposób dostosowywania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="afc99-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="afc99-178">Umożliwiają one nazwę metody i podpis do zarezerwowania, dzięki czemu wygenerowany kod można wywołać metodę, ale deweloper może zdecydować, czy zaimplementować metodę.</span><span class="sxs-lookup"><span data-stu-id="afc99-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="afc99-179">Podobnie jak klasy częściowe, metody częściowe włączyć kod utworzony przez generator kodu i kod utworzony przez dewelopera ludzkiego do współpracy bez kosztów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="afc99-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="afc99-180">Deklaracja metody częściowej składa się z dwóch części: definicji i implementacji.</span><span class="sxs-lookup"><span data-stu-id="afc99-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="afc99-181">Mogą one znajdować się w oddzielnych częściach klasy częściowej lub w tej samej części.</span><span class="sxs-lookup"><span data-stu-id="afc99-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="afc99-182">Jeśli nie ma deklaracji implementacji, kompilator optymalizuje zarówno definiowanie deklaracji i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="afc99-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="afc99-183">Częściowe deklaracje metody muszą zaczynać się od kontekstowego słowa kluczowego [częściowego,](../../language-reference/keywords/partial-type.md) a metoda musi zwracać [void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="afc99-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="afc99-184">Metody częściowe mogą mieć [w](../../language-reference/keywords/in-parameter-modifier.md) lub [ref,](../../language-reference/keywords/ref.md) ale nie [obecnie](../../language-reference/keywords/out-parameter-modifier.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="afc99-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="afc99-185">Metody częściowe są niejawnie [prywatne](../../language-reference/keywords/private.md)i dlatego nie mogą być [wirtualne.](../../language-reference/keywords/virtual.md)</span><span class="sxs-lookup"><span data-stu-id="afc99-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="afc99-186">Metody częściowe nie mogą być [extern](../../language-reference/keywords/extern.md), ponieważ obecność treści określa, czy są one definiowania lub realizacji.</span><span class="sxs-lookup"><span data-stu-id="afc99-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="afc99-187">Metody częściowe mogą mieć [statyczne](../../language-reference/keywords/static.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatory.</span><span class="sxs-lookup"><span data-stu-id="afc99-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="afc99-188">Metody częściowe mogą być ogólne.</span><span class="sxs-lookup"><span data-stu-id="afc99-188">Partial methods can be generic.</span></span> <span data-ttu-id="afc99-189">Ograniczenia są umieszczane na definiowanie deklaracji metody częściowej i opcjonalnie mogą być powtarzane na implementacji jeden.</span><span class="sxs-lookup"><span data-stu-id="afc99-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="afc99-190">Nazwy parametrów i parametrów typu nie muszą być takie same w deklaracji wykonawczej, jak w definiowaniu.</span><span class="sxs-lookup"><span data-stu-id="afc99-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="afc99-191">Można dokonać [delegata](../../language-reference/builtin-types/reference-types.md) do metody częściowej, który został zdefiniowany i zaimplementowany, ale nie do metody częściowej, która została tylko zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="afc99-191">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="afc99-192">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="afc99-192">C# Language Specification</span></span>

<span data-ttu-id="afc99-193">Aby uzyskać więcej informacji, zobacz [Typy częściowe](~/_csharplang/spec/classes.md#partial-types) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="afc99-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="afc99-194">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="afc99-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="afc99-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afc99-195">See also</span></span>

- [<span data-ttu-id="afc99-196">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="afc99-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="afc99-197">Klasy</span><span class="sxs-lookup"><span data-stu-id="afc99-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="afc99-198">Typy konstrukcji</span><span class="sxs-lookup"><span data-stu-id="afc99-198">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="afc99-199">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="afc99-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="afc99-200">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="afc99-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
