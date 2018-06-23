---
title: Klasy częściowe i metody (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: aa0baf50b9e4aabf0bb5dfa229ecd245db391a8b
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314737"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="3cd6e-102">Klasy częściowe i metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3cd6e-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="3cd6e-103">Umożliwia dzielenie definicji [klasy](../../../csharp/language-reference/keywords/class.md), [struktury](../../../csharp/language-reference/keywords/struct.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md) lub metody za pośrednictwem dwóch lub więcej plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="3cd6e-104">Każdy plik źródłowy zawiera sekcja definicji typu lub metody, a wszystkie elementy są łączone podczas kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="3cd6e-105">Klasy częściowe</span><span class="sxs-lookup"><span data-stu-id="3cd6e-105">Partial Classes</span></span>  
 <span data-ttu-id="3cd6e-106">Istnieje kilka sytuacji, gdy pożądane jest podział definicję klasy:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="3cd6e-107">Podczas pracy w przypadku dużych projektów, rozpowszechniania się klasę oddzielnych plików umożliwia wielu programistom na nim pracować, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="3cd6e-108">Podczas pracy ze źródłem wygenerowanej automatycznie, można dodać kod do klasy bez konieczności ponownego tworzenia pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="3cd6e-109">Visual Studio korzysta z tej metody podczas tworzenia formularzy systemu Windows, kodu otoki usługi sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="3cd6e-110">Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="3cd6e-111">Aby podzielić definicję klasy, należy użyć [częściowe](../../../csharp/language-reference/keywords/partial-type.md) modyfikator — słowo kluczowe, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 <span data-ttu-id="3cd6e-112">`partial` — Słowo kluczowe wskazuje, że inne części klasy, struktury, lub interfejs można zdefiniować w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="3cd6e-113">Wszystkie części muszą używać `partial` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="3cd6e-114">Wszystkie części muszą być dostępne w kompilacji do końcowego typu formularza.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="3cd6e-115">Wszystkie części muszą mieć tą samą dostępnością, takie jak `public`, `private`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="3cd6e-116">Jeśli żadnej części jest zadeklarowany jako abstrakcyjny, następnie całego typu jest określana jako abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="3cd6e-117">Części zadeklarowana zapieczętowanym, następnie całego typ jest traktowany jako zapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="3cd6e-118">Jeśli któraś deklaruje typ podstawowy, całe typ dziedziczy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-118">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="3cd6e-119">Zaakceptować wszystkie części, które Określ klasę podstawową, ale elementy, które Pomiń klasę podstawową nadal dziedziczą typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="3cd6e-120">Części można określić różnych interfejsach podstawowych i końcowe typ implementuje wszystkich interfejsów, które są wyświetlane według częściowe deklaracje.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="3cd6e-121">Wszystkie klasy, struktury lub elementy członkowskie interfejsu zadeklarowany w definicji częściowej są dostępne dla wszystkich innych części.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="3cd6e-122">Końcowy Typ jest kombinacją wszystkie części w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-122">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cd6e-123">`partial` Modyfikator nie jest dostępna w deklaracjach delegata lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="3cd6e-124">W poniższym przykładzie pokazano, że zagnieżdżone typy mogą być częściowe, nawet jeśli są one zagnieżdżone w obrębie typu nie jest częściowe sam.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 <span data-ttu-id="3cd6e-125">W czasie kompilacji atrybutów typu częściowego definicje zostały scalone.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="3cd6e-126">Na przykład wziąć pod uwagę następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-126">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 <span data-ttu-id="3cd6e-127">Są one odpowiednikiem następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-127">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 <span data-ttu-id="3cd6e-128">Poniżej są łączone ze wszystkich definicji typu częściowego:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-128">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="3cd6e-129">komentarze XML</span><span class="sxs-lookup"><span data-stu-id="3cd6e-129">XML comments</span></span>  
  
-   <span data-ttu-id="3cd6e-130">interfejsy</span><span class="sxs-lookup"><span data-stu-id="3cd6e-130">interfaces</span></span>  
  
-   <span data-ttu-id="3cd6e-131">atrybuty parametru typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="3cd6e-131">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="3cd6e-132">class — Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3cd6e-132">class attributes</span></span>  
  
-   <span data-ttu-id="3cd6e-133">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3cd6e-133">members</span></span>  
  
 <span data-ttu-id="3cd6e-134">Na przykład wziąć pod uwagę następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-134">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 <span data-ttu-id="3cd6e-135">Są one odpowiednikiem następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-135">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a><span data-ttu-id="3cd6e-136">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="3cd6e-136">Restrictions</span></span>  
 <span data-ttu-id="3cd6e-137">Istnieje kilka reguł, które należy wykonać podczas pracy z definicjami częściowej klasy:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-137">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="3cd6e-138">Wszystkie definicje typu częściowego przeznaczone do części tego samego typu muszą zostać zmodyfikowane z `partial`.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="3cd6e-139">Na przykład następujące deklaracje klas generuje błąd:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-139">For example, the following class declarations generate an error:</span></span>  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   <span data-ttu-id="3cd6e-140">`partial` Modyfikator może występować tylko bezpośrednio przed słowa kluczowe `class`, `struct`, lub `interface`.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="3cd6e-141">Zagnieżdżone typy częściowe są dozwolone w definicji typu częściowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   <span data-ttu-id="3cd6e-142">Wszystkie definicje typu częściowego przeznaczone do części tego samego typu muszą być zdefiniowane w tym samym zestawie i tym samym module (plik .exe lub .dll).</span><span class="sxs-lookup"><span data-stu-id="3cd6e-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="3cd6e-143">Definicje z częściowa nie może obejmować wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-143">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="3cd6e-144">Nazwa klasy i parametry typu ogólnego muszą odpowiadać na wszystkie definicje typu częściowego.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="3cd6e-145">Typy ogólne mogą być częściowe.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-145">Generic types can be partial.</span></span> <span data-ttu-id="3cd6e-146">Każdy z częściowa deklaracja musi używać takie same nazwy parametrów w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-146">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="3cd6e-147">Poniższe słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli jest obecny w jednej definicji typu częściowego, nie powodują konflikt z słów kluczowych określonych w innej definicji częściowej dla tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="3cd6e-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="3cd6e-148">public</span><span class="sxs-lookup"><span data-stu-id="3cd6e-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="3cd6e-149">private</span><span class="sxs-lookup"><span data-stu-id="3cd6e-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="3cd6e-150">protected</span><span class="sxs-lookup"><span data-stu-id="3cd6e-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="3cd6e-151">internal</span><span class="sxs-lookup"><span data-stu-id="3cd6e-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="3cd6e-152">abstract</span><span class="sxs-lookup"><span data-stu-id="3cd6e-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="3cd6e-153">sealed</span><span class="sxs-lookup"><span data-stu-id="3cd6e-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="3cd6e-154">klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="3cd6e-154">base class</span></span>  
  
    -   <span data-ttu-id="3cd6e-155">[nowe](../../../csharp/language-reference/keywords/new.md) modyfikator (części zagnieżdżonych)</span><span class="sxs-lookup"><span data-stu-id="3cd6e-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="3cd6e-156">ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="3cd6e-156">generic constraints</span></span>  
  
         <span data-ttu-id="3cd6e-157">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3cd6e-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="3cd6e-158">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="3cd6e-158">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="3cd6e-159">Opis</span><span class="sxs-lookup"><span data-stu-id="3cd6e-159">Description</span></span>  
 <span data-ttu-id="3cd6e-160">W poniższym przykładzie, pola, konstruktora klasy `CoOrds`, są zadeklarowane w jednej definicji klasy częściowe i element członkowski, `PrintCoOrds`, jest zadeklarowany w innej definicji częściowej klasy.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-160">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3cd6e-161">Kod</span><span class="sxs-lookup"><span data-stu-id="3cd6e-161">Code</span></span>  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="3cd6e-162">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="3cd6e-162">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="3cd6e-163">Opis</span><span class="sxs-lookup"><span data-stu-id="3cd6e-163">Description</span></span>  
 <span data-ttu-id="3cd6e-164">W poniższym przykładzie pokazano, że można również zaprojektować częściowej struktury i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-164">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3cd6e-165">Kod</span><span class="sxs-lookup"><span data-stu-id="3cd6e-165">Code</span></span>  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a><span data-ttu-id="3cd6e-166">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="3cd6e-166">Partial Methods</span></span>  
 <span data-ttu-id="3cd6e-167">Częściowej klasy lub struktury może zawierać metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="3cd6e-168">Jedną część klasy zawiera podpis metody.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="3cd6e-169">Opcjonalne wdrożenia może być zdefiniowana w tej samej części lub innej części.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="3cd6e-170">Jeśli nie podano implementacji, następnie metoda i wszystkie wywołania metody są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="3cd6e-171">Metody częściowe Włącz implementujący jednej części klasy w celu zdefiniowania metody, podobnie jak zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="3cd6e-172">Realizator z drugiej strony klasy można zdecydować, czy do implementacji metody, czy nie.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="3cd6e-173">Jeśli metoda nie jest zaimplementowana, a następnie usuwa kompilator metodę podpisu i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="3cd6e-174">Wywołania do metody, w tym jakiekolwiek wyniki, które wystąpiłyby ewaluacyjną argumentów wywołań, nie obowiązują w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="3cd6e-175">W związku z tym dowolny kod w klasie częściowej za darmo można użyć metody częściowej, nawet, jeśli nie podano implementacji.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="3cd6e-176">Jeśli metoda jest wywoływana, ale nie zaimplementowano spowoduje, że żadne błędy kompilacji lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="3cd6e-177">Metody częściowe są szczególnie użyteczne jako sposobem dostosowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="3cd6e-178">Pozwalają one na nazwę metody i podpis do zarezerwowania, dzięki czemu kod wygenerowany przez można wywołać metody, ale deweloper może zdecydować, czy do implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="3cd6e-179">Znacznie takich jak klasy częściowe metody częściowe umożliwiają kod tworzony przez generator kodu i kod utworzony przez człowieka dewelopera współdziałają ze sobą bez kosztów czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="3cd6e-180">Deklaracji metody częściowej składa się z dwóch części: definicja i wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="3cd6e-181">Mogą one w oddzielnych części częściowej klasy lub w tej samej części.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="3cd6e-182">Jeśli istnieje nie deklaracji w implementacji, a następnie kompilator optymalizuje optymalizacji zarówno Definiowanie deklaracji i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="3cd6e-183">Deklaracje metody częściowej musi rozpoczynać się od kontekstowe słowo kluczowe [częściowe](../../../csharp/language-reference/keywords/partial-type.md) i metoda musi zwracać [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="3cd6e-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="3cd6e-184">Metody częściowe mogą mieć [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) , ale nie [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
-   <span data-ttu-id="3cd6e-185">Metody częściowe są niejawnie [prywatnej](../../../csharp/language-reference/keywords/private.md), i dlatego nie może być [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="3cd6e-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="3cd6e-186">Metody częściowe nie może być [extern](../../../csharp/language-reference/keywords/extern.md), ponieważ obecności treści Określa, czy są one Definiowanie lub wykonania.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="3cd6e-187">Metody częściowe mogą mieć [statycznych](../../../csharp/language-reference/keywords/static.md) i [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="3cd6e-188">Metody częściowe mogą być ogólne.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-188">Partial methods can be generic.</span></span> <span data-ttu-id="3cd6e-189">Ograniczenia są umieszczone w deklaracji metody częściowej definiującej i opcjonalnie może zostać powtórzony na jeden implementującej.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="3cd6e-190">Parametr i typ nazwy parametru muszą być takie same, w deklaracji implementującej jak definiująca jeden.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="3cd6e-191">Możesz wprowadzić [delegować](../../../csharp/language-reference/keywords/delegate.md) metody częściowej, który został zdefiniowany i wdrożone, ale nie tylko zdefiniowanego metodą częściową.</span><span class="sxs-lookup"><span data-stu-id="3cd6e-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3cd6e-192">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3cd6e-192">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3cd6e-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cd6e-193">See Also</span></span>  
 [<span data-ttu-id="3cd6e-194">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3cd6e-194">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3cd6e-195">Klasy</span><span class="sxs-lookup"><span data-stu-id="3cd6e-195">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [<span data-ttu-id="3cd6e-196">Struktury</span><span class="sxs-lookup"><span data-stu-id="3cd6e-196">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="3cd6e-197">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3cd6e-197">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="3cd6e-198">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="3cd6e-198">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
