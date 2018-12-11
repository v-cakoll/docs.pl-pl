---
title: Klasy częściowe i metody - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 222a47989537f09fd78c4a3b17fa8c1a5478d73f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243468"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="bdde1-102">Klasy częściowe i metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bdde1-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="bdde1-103">Umożliwia dzielenie definicji [klasy](../../../csharp/language-reference/keywords/class.md), [struktury](../../../csharp/language-reference/keywords/struct.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md) lub metody za pośrednictwem dwóch lub więcej plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="bdde1-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="bdde1-104">Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie elementy są łączone, podczas kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bdde1-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="bdde1-105">Klasy częściowe</span><span class="sxs-lookup"><span data-stu-id="bdde1-105">Partial Classes</span></span>  
 <span data-ttu-id="bdde1-106">Istnieje kilka sytuacji, gdy wskazane jest dzielenie definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="bdde1-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="bdde1-107">Podczas pracy z dużymi projektami, rozmieszczanie klasę za pośrednictwem osobnych plikach umożliwia wielu programistów pracować nad nim, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="bdde1-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="bdde1-108">Podczas pracy z automatycznie wygenerowanego źródła, można dodać kodu do klasy bez konieczności ponownego tworzenia pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bdde1-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="bdde1-109">Visual Studio używa tego podejścia, podczas tworzenia formularzy Windows, kodu otoki usługi sieci Web i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bdde1-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="bdde1-110">Możesz utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku tworzone przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bdde1-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="bdde1-111">Aby podzielić definicji klasy, należy użyć [częściowe](../../../csharp/language-reference/keywords/partial-type.md) modyfikator — słowo kluczowe, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="bdde1-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 <span data-ttu-id="bdde1-112">`partial` Słowo kluczowe wskazuje, że inne części klasy, struktury, lub interfejsu może być zdefiniowany w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bdde1-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="bdde1-113">Wszystkie części muszą używać `partial` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="bdde1-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="bdde1-114">Wszystkie części muszą być dostępne w kompilacji do końcowego typu formularza.</span><span class="sxs-lookup"><span data-stu-id="bdde1-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="bdde1-115">Wszystkie części muszą mieć identyczną dostępność, takich jak `public`, `private`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bdde1-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="bdde1-116">Jeśli jakakolwiek część został zadeklarowany jako abstrakcyjny, cały typ będzie traktowany abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="bdde1-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="bdde1-117">Jeśli jakakolwiek część zadeklarowano sealed, a następnie cały typ jest traktowany jako zapieczętowany.</span><span class="sxs-lookup"><span data-stu-id="bdde1-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="bdde1-118">Jeśli jakakolwiek część deklaruje typu podstawowego, cały typ dziedziczy tej klasy.</span><span class="sxs-lookup"><span data-stu-id="bdde1-118">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="bdde1-119">Musisz zaakceptować wszystkie elementy, które określają klasy bazowej, ale części, które pominięto klasę bazową nadal dziedziczą typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="bdde1-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="bdde1-120">Części można określić różne interfejsy podstawowe, a końcowe typ implementuje wszystkie interfejsy, które są wyświetlane według częściowe deklaracje.</span><span class="sxs-lookup"><span data-stu-id="bdde1-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="bdde1-121">Wszystkie klasy, struktury lub interfejsu elementów członkowskich zadeklarowanych w definicji częściowej są dostępne dla wszystkich innych części.</span><span class="sxs-lookup"><span data-stu-id="bdde1-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="bdde1-122">Typ końcowego jest kombinacją wszystkie elementy w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bdde1-122">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdde1-123">`partial` Modyfikator nie jest dostępny na delegata lub wyliczenie deklaracji.</span><span class="sxs-lookup"><span data-stu-id="bdde1-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="bdde1-124">Poniższy przykład pokazuje, że zagnieżdżone typy mogą być częściowe, nawet jeśli są one zagnieżdżone w obrębie typu nie jest częściowe sam.</span><span class="sxs-lookup"><span data-stu-id="bdde1-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 <span data-ttu-id="bdde1-125">W czasie kompilacji atrybuty z definicji typu częściowego są scalane.</span><span class="sxs-lookup"><span data-stu-id="bdde1-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="bdde1-126">Na przykład należy wziąć pod uwagę następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="bdde1-126">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 <span data-ttu-id="bdde1-127">Są one równoważnymi następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="bdde1-127">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 <span data-ttu-id="bdde1-128">Poniżej są scalane z definicji typu częściowego:</span><span class="sxs-lookup"><span data-stu-id="bdde1-128">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="bdde1-129">komentarze XML</span><span class="sxs-lookup"><span data-stu-id="bdde1-129">XML comments</span></span>  
  
-   <span data-ttu-id="bdde1-130">interfejsy</span><span class="sxs-lookup"><span data-stu-id="bdde1-130">interfaces</span></span>  
  
-   <span data-ttu-id="bdde1-131">atrybuty parametru typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="bdde1-131">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="bdde1-132">class — Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bdde1-132">class attributes</span></span>  
  
-   <span data-ttu-id="bdde1-133">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bdde1-133">members</span></span>  
  
 <span data-ttu-id="bdde1-134">Na przykład należy wziąć pod uwagę następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="bdde1-134">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 <span data-ttu-id="bdde1-135">Są one równoważnymi następujące deklaracje:</span><span class="sxs-lookup"><span data-stu-id="bdde1-135">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a><span data-ttu-id="bdde1-136">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="bdde1-136">Restrictions</span></span>  
 <span data-ttu-id="bdde1-137">Istnieje kilka reguł, które należy wykonać podczas pracy z częściowych definicji klasy:</span><span class="sxs-lookup"><span data-stu-id="bdde1-137">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="bdde1-138">Wszystkie definicje typu częściowego, należy traktować jako części tego samego typu, muszą zostać zmodyfikowane za pomocą `partial`.</span><span class="sxs-lookup"><span data-stu-id="bdde1-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="bdde1-139">Na przykład następujące deklaracje klas wygenerowanie błędu:</span><span class="sxs-lookup"><span data-stu-id="bdde1-139">For example, the following class declarations generate an error:</span></span>  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   <span data-ttu-id="bdde1-140">`partial` Modyfikator może się pojawić tylko bezpośrednio przed słowa kluczowe `class`, `struct`, lub `interface`.</span><span class="sxs-lookup"><span data-stu-id="bdde1-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="bdde1-141">Zagnieżdżone typy częściowe są dozwolone w definicji typu częściowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bdde1-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   <span data-ttu-id="bdde1-142">Wszystkie definicje typu częściowego, należy traktować jako części tego samego typu musi być zdefiniowany w tym samym zestawie i tego samego modułu (plik .exe lub .dll).</span><span class="sxs-lookup"><span data-stu-id="bdde1-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="bdde1-143">Definicje częściowe nie mogą obejmować wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="bdde1-143">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="bdde1-144">Nazwa klasy i parametry typu ogólnego muszą być zgodne na wszystkich definicji typu częściowego.</span><span class="sxs-lookup"><span data-stu-id="bdde1-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="bdde1-145">Typy rodzajowe mogą być częściowe.</span><span class="sxs-lookup"><span data-stu-id="bdde1-145">Generic types can be partial.</span></span> <span data-ttu-id="bdde1-146">Każdy częściowa deklaracja należy użyć tej samej nazwy parametrów w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bdde1-146">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="bdde1-147">Następujące słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli jest obecny na jedną definicję typu częściowego, nie może powodować konfliktu ze słowami kluczowymi, określone w innej definicji częściowej dla tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="bdde1-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="bdde1-148">public</span><span class="sxs-lookup"><span data-stu-id="bdde1-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="bdde1-149">private</span><span class="sxs-lookup"><span data-stu-id="bdde1-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="bdde1-150">protected</span><span class="sxs-lookup"><span data-stu-id="bdde1-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="bdde1-151">internal</span><span class="sxs-lookup"><span data-stu-id="bdde1-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="bdde1-152">abstract</span><span class="sxs-lookup"><span data-stu-id="bdde1-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="bdde1-153">sealed</span><span class="sxs-lookup"><span data-stu-id="bdde1-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="bdde1-154">klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="bdde1-154">base class</span></span>  
  
    -   <span data-ttu-id="bdde1-155">[nowe](../../../csharp/language-reference/keywords/new.md) modyfikator (zagnieżdżonych części)</span><span class="sxs-lookup"><span data-stu-id="bdde1-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="bdde1-156">ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="bdde1-156">generic constraints</span></span>  
  
         <span data-ttu-id="bdde1-157">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="bdde1-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="bdde1-158">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="bdde1-158">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="bdde1-159">Opis</span><span class="sxs-lookup"><span data-stu-id="bdde1-159">Description</span></span>  
 <span data-ttu-id="bdde1-160">W poniższym przykładzie, pola i Konstruktor klasy `CoOrds`, są deklarowane w jedną definicję klasy częściowe i elementu członkowskiego, `PrintCoOrds`, jest zadeklarowany w innej definicji częściowej klasy.</span><span class="sxs-lookup"><span data-stu-id="bdde1-160">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bdde1-161">Kod</span><span class="sxs-lookup"><span data-stu-id="bdde1-161">Code</span></span>  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="bdde1-162">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="bdde1-162">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="bdde1-163">Opis</span><span class="sxs-lookup"><span data-stu-id="bdde1-163">Description</span></span>  
 <span data-ttu-id="bdde1-164">Poniższy przykład pokazuje, że możesz również tworzyć częściowej struktury i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="bdde1-164">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bdde1-165">Kod</span><span class="sxs-lookup"><span data-stu-id="bdde1-165">Code</span></span>  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a><span data-ttu-id="bdde1-166">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="bdde1-166">Partial Methods</span></span>  
 <span data-ttu-id="bdde1-167">Częściowe klasy lub struktury może zawierać metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="bdde1-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="bdde1-168">Jedną część klasy zawiera podpis metody.</span><span class="sxs-lookup"><span data-stu-id="bdde1-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="bdde1-169">Opcjonalne wdrożenia może być zdefiniowana w części tej samej lub innej części.</span><span class="sxs-lookup"><span data-stu-id="bdde1-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="bdde1-170">Jeśli wdrożenia nie jest podany, następnie metoda i wszystkie wywołania do metody są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bdde1-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="bdde1-171">Metody częściowe umożliwiają implementujący jednej części klasy zdefiniować metodę, podobne do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bdde1-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="bdde1-172">Implementujący części klasy zdecydować, czy wdrożyć metodę, czy nie.</span><span class="sxs-lookup"><span data-stu-id="bdde1-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="bdde1-173">Jeśli metoda nie jest zaimplementowana, a następnie kompilator usuwa metodę podpisu i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="bdde1-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="bdde1-174">Wywołania do metody, w tym żadnych wyników, które wystąpiłyby oceny argumenty w wywołaniach, nie mają wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bdde1-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="bdde1-175">W związku z tym, każdy kod w klasie częściowej bez ograniczeń wykorzystywać metody częściowej, nawet jeśli nie podano wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bdde1-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="bdde1-176">Jeśli metoda jest wywoływana, ale nie zaimplementowana spowoduje, że żadne błędy kompilacji lub czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bdde1-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="bdde1-177">Metody częściowe są szczególnie przydatne, jako sposób dostosować wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="bdde1-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="bdde1-178">Pozwalają one na nazwę metody i podpisu do zarezerwowania, tak aby wygenerowanego kodu można wywołać metodę, ale deweloper może zdecydować, czy do implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="bdde1-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="bdde1-179">Znacznie takich jak klasy częściowe metod częściowych Włącz kod utworzony przez generator kodu i kod utworzony przez ludzi dla deweloperów do współpracują ze sobą bez kosztów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="bdde1-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="bdde1-180">Deklaracji metody częściowej składa się z dwóch części: definicję i implementację.</span><span class="sxs-lookup"><span data-stu-id="bdde1-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="bdde1-181">Może to być w osobnych części klasy częściowej lub w tej samej części.</span><span class="sxs-lookup"><span data-stu-id="bdde1-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="bdde1-182">Jeśli istnieje żadna deklaracja wdrożenia, a następnie kompilator optymalizuje natychmiast zarówno Definiowanie deklaracji i wszystkie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="bdde1-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="bdde1-183">Deklaracje metody częściowej musi zaczynać się od kontekstowego słowa kluczowego [częściowe](../../../csharp/language-reference/keywords/partial-type.md) i metoda musi zwracać [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="bdde1-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="bdde1-184">Metody częściowe mogą mieć [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) , ale nie [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.</span><span class="sxs-lookup"><span data-stu-id="bdde1-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
-   <span data-ttu-id="bdde1-185">Metody częściowe są niejawną kolekcją [prywatnej](../../../csharp/language-reference/keywords/private.md), i dlatego nie może być [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="bdde1-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="bdde1-186">Metody częściowe nie może być [extern](../../../csharp/language-reference/keywords/extern.md), ponieważ obecność treści Określa, czy są one Definiowanie lub wdrażania.</span><span class="sxs-lookup"><span data-stu-id="bdde1-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="bdde1-187">Metody częściowe mogą mieć [statyczne](../../../csharp/language-reference/keywords/static.md) i [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="bdde1-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="bdde1-188">Metody częściowe mogą być ogólne.</span><span class="sxs-lookup"><span data-stu-id="bdde1-188">Partial methods can be generic.</span></span> <span data-ttu-id="bdde1-189">Ograniczenia są nakładane na definiowanie deklaracji metody częściowej i opcjonalnie może być powtarzany na architekturze implementującej.</span><span class="sxs-lookup"><span data-stu-id="bdde1-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="bdde1-190">Parametr i typ nazwy parametru nie muszą być takie same, w deklaracji implementującej jak definiowanie jeden.</span><span class="sxs-lookup"><span data-stu-id="bdde1-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="bdde1-191">Możesz wprowadzić [delegować](../../../csharp/language-reference/keywords/delegate.md) do metody częściowej, które zostały zdefiniowane i zaimplementowane, ale nie do metody częściowej, który tylko został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="bdde1-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bdde1-192">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bdde1-192">C# Language Specification</span></span>  

<span data-ttu-id="bdde1-193">Aby uzyskać więcej informacji, zobacz [typów częściowych](~/_csharplang/spec/classes.md#partial-types) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bdde1-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="bdde1-194">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="bdde1-194">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bdde1-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdde1-195">See Also</span></span>

- [<span data-ttu-id="bdde1-196">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bdde1-196">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bdde1-197">Klasy</span><span class="sxs-lookup"><span data-stu-id="bdde1-197">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [<span data-ttu-id="bdde1-198">Struktury</span><span class="sxs-lookup"><span data-stu-id="bdde1-198">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [<span data-ttu-id="bdde1-199">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="bdde1-199">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="bdde1-200">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="bdde1-200">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
