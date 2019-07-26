---
title: Korzystanie z przestrzeni C# nazw — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: abd4c34661d96d8c3188e92dd2d76f847e17aae7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433532"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="50bd9-102">Używanie przestrzeni nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="50bd9-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="50bd9-103">Przestrzenie nazw są intensywnie używane w C# programach na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="50bd9-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="50bd9-104">Po pierwsze klasy .NET Framework używają przestrzeni nazw do organizowania wielu klas.</span><span class="sxs-lookup"><span data-stu-id="50bd9-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="50bd9-105">Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.</span><span class="sxs-lookup"><span data-stu-id="50bd9-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="50bd9-106">Uzyskiwanie dostępu do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="50bd9-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="50bd9-107">Większość C# aplikacji rozpoczyna się od sekcji `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="50bd9-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="50bd9-108">Ta sekcja zawiera listę przestrzeni nazw, których aplikacja będzie często używać, i zapisuje programistę w celu określenia w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.</span><span class="sxs-lookup"><span data-stu-id="50bd9-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="50bd9-109">Na przykład, dołączając wiersz:</span><span class="sxs-lookup"><span data-stu-id="50bd9-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="50bd9-110">Na początku programu programista może użyć kodu:</span><span class="sxs-lookup"><span data-stu-id="50bd9-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="50bd9-111">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="50bd9-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="50bd9-112">Aliasy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="50bd9-112">Namespace Aliases</span></span>  
 <span data-ttu-id="50bd9-113">[Dyrektywy using](../../../csharp/language-reference/keywords/using-directive.md) można także użyć do utworzenia aliasu dla [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="50bd9-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="50bd9-114">Na przykład jeśli używasz wcześniej zapisywanej przestrzeni nazw, która zawiera zagnieżdżone przestrzenie nazw, możesz chcieć zadeklarować alias w celu zapewnienia skróconego sposobu odwoływania się do jednego w szczególności, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="50bd9-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="50bd9-115">Używanie przestrzeni nazw do sterowania zakresem</span><span class="sxs-lookup"><span data-stu-id="50bd9-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="50bd9-116">`namespace` Słowo kluczowe jest używane do deklarowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="50bd9-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="50bd9-117">Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie.</span><span class="sxs-lookup"><span data-stu-id="50bd9-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="50bd9-118">W poniższym przykładzie Klasa zatytułowana `SampleClass` jest zdefiniowana w dwóch przestrzeniach nazw, jedna zagnieżdżona w drugim.</span><span class="sxs-lookup"><span data-stu-id="50bd9-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="50bd9-119">[Operator `.` dostępu do elementów członkowskich](../../language-reference/operators/member-access-operators.md#member-access-operator-) jest używany do odróżnienia metody wywoływanej.</span><span class="sxs-lookup"><span data-stu-id="50bd9-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="50bd9-120">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="50bd9-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="50bd9-121">Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy wskazujące hierarchię logiczną.</span><span class="sxs-lookup"><span data-stu-id="50bd9-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="50bd9-122">Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typem, i `B` jest zagnieżdżona wewnątrz niej.</span><span class="sxs-lookup"><span data-stu-id="50bd9-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="50bd9-123">W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="50bd9-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="50bd9-124">W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.</span><span class="sxs-lookup"><span data-stu-id="50bd9-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="50bd9-125">W poprzednim segmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="50bd9-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="50bd9-126">Przestrzeń nazw `N1` jest członkiem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="50bd9-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="50bd9-127">Jego w pełni kwalifikowana nazwa `N1`jest.</span><span class="sxs-lookup"><span data-stu-id="50bd9-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="50bd9-128">Przestrzeń nazw `N2` jest `N1`członkiem.</span><span class="sxs-lookup"><span data-stu-id="50bd9-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="50bd9-129">Jego w pełni kwalifikowana nazwa `N1.N2`jest.</span><span class="sxs-lookup"><span data-stu-id="50bd9-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="50bd9-130">Klasa `C1` jest`N1`członkiem.</span><span class="sxs-lookup"><span data-stu-id="50bd9-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="50bd9-131">Jego w pełni kwalifikowana nazwa `N1.C1`jest.</span><span class="sxs-lookup"><span data-stu-id="50bd9-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="50bd9-132">Nazwa `C2` klasy jest używana dwa razy w tym kodzie.</span><span class="sxs-lookup"><span data-stu-id="50bd9-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="50bd9-133">Jednak w pełni kwalifikowane nazwy są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="50bd9-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="50bd9-134">Pierwsze wystąpienie `C2` jest zadeklarowane wewnątrz `C1`; w związku z tym jego w pełni kwalifikowana nazwa `N1.C1.C2`to:.</span><span class="sxs-lookup"><span data-stu-id="50bd9-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="50bd9-135">Drugie wystąpienie `C2` jest zadeklarowane wewnątrz przestrzeni nazw `N2`; w związku z tym jego w pełni kwalifikowana `N1.N2.C2`nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="50bd9-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="50bd9-136">Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski `C3`klasy,, do przestrzeni nazw `N1.N2` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="50bd9-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="50bd9-137">Ogólnie rzecz biorąc służy `::` do odwoływania się do aliasu przestrzeni nazw lub `global::` odwoływania `.` się do globalnej przestrzeni nazw oraz do kwalifikowania typów lub członków.</span><span class="sxs-lookup"><span data-stu-id="50bd9-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="50bd9-138">Jest to błąd używany `::` z aliasem, który odwołuje się do typu zamiast przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="50bd9-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="50bd9-139">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="50bd9-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="50bd9-140">Należy pamiętać, że `global` słowo nie jest wstępnie zdefiniowanym aliasem `global.X` ; w związku z tym nie ma żadnych specjalnych znaczenia.</span><span class="sxs-lookup"><span data-stu-id="50bd9-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="50bd9-141">Uzyskuje specjalne znaczenie tylko wtedy, gdy jest używany z `::`.</span><span class="sxs-lookup"><span data-stu-id="50bd9-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="50bd9-142">Ostrzeżenie kompilatora CS0440 jest generowany, jeśli zdefiniujesz alias o nazwie Global `global::` , ponieważ zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu.</span><span class="sxs-lookup"><span data-stu-id="50bd9-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="50bd9-143">Na przykład poniższy wiersz generuje ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="50bd9-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="50bd9-144">Korzystanie `::` z aliasów jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów.</span><span class="sxs-lookup"><span data-stu-id="50bd9-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="50bd9-145">Rozważmy na przykład ten przykład:</span><span class="sxs-lookup"><span data-stu-id="50bd9-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="50bd9-146">To działa, ale jeśli typ nazwany `Alias` miał zostać później wprowadzony, `Alias.` zostałby powiązać z tym typem.</span><span class="sxs-lookup"><span data-stu-id="50bd9-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="50bd9-147">Użycie `Alias::Exception` gwarantuje, `Alias` że jest traktowany jako alias przestrzeni nazw i nie zostanie pomylony z typem.</span><span class="sxs-lookup"><span data-stu-id="50bd9-147">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="50bd9-148">Zapoznaj się [z tematem How to: Aby uzyskać więcej informacji na](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) `global` temat aliasu, Użyj globalnego aliasu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="50bd9-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50bd9-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50bd9-149">See also</span></span>

- [<span data-ttu-id="50bd9-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50bd9-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="50bd9-151">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="50bd9-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="50bd9-152">. operator</span><span class="sxs-lookup"><span data-stu-id="50bd9-152">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="50bd9-153">:: operator</span><span class="sxs-lookup"><span data-stu-id="50bd9-153">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="50bd9-154">extern</span><span class="sxs-lookup"><span data-stu-id="50bd9-154">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
