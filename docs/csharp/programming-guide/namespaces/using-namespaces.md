---
title: Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847480"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="45e1a-102">Używanie przestrzeni nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="45e1a-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="45e1a-103">Przestrzenie nazw są intensywnie używane w programach języka C# na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="45e1a-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="45e1a-104">Po pierwsze klas .NET Framework umożliwia organizowanie jego wiele klas przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="45e1a-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="45e1a-105">Po drugie deklarowania własne przestrzenie nazw może kontrolować zakres klasy i metody nazwy w dużych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="45e1a-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="45e1a-106">Uzyskiwanie dostępu do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="45e1a-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="45e1a-107">Większość aplikacji C# zaczynają się od sekcji `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="45e1a-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="45e1a-108">Ta sekcja zawiera przestrzenie nazw, aplikacja będzie najczęściej używana i zapisuje programistę z określania każdym użyciu metody, która jest zawarta w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="45e1a-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="45e1a-109">Na przykład, w tym wierszu:</span><span class="sxs-lookup"><span data-stu-id="45e1a-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="45e1a-110">Na początku programu programisty należy użyć kodu:</span><span class="sxs-lookup"><span data-stu-id="45e1a-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="45e1a-111">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="45e1a-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="45e1a-112">Aliasy Namespace</span><span class="sxs-lookup"><span data-stu-id="45e1a-112">Namespace Aliases</span></span>  
 <span data-ttu-id="45e1a-113">[Użycie dyrektywy](../../../csharp/language-reference/keywords/using-directive.md) może również służyć do tworzenia aliasów [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="45e1a-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="45e1a-114">Na przykład jeśli używasz poprzednio wpisaną przestrzeni nazw, która zawiera zagnieżdżone przestrzenie nazw, możesz zechcieć do deklarowania aliasem, aby umożliwić odwoływanie się do jednego w szczególności, jak w poniższym przykładzie skrót:</span><span class="sxs-lookup"><span data-stu-id="45e1a-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="45e1a-115">Używanie przestrzeni nazw do zakresu kontroli</span><span class="sxs-lookup"><span data-stu-id="45e1a-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="45e1a-116">`namespace` Słowo kluczowe jest używane do deklarowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="45e1a-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="45e1a-117">Możliwość tworzenia zakresów w obrębie projektu ułatwia organizowanie kodu i pozwala na tworzenie typów globalnie unikatowa.</span><span class="sxs-lookup"><span data-stu-id="45e1a-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="45e1a-118">W poniższym przykładzie klasę o nazwie `SampleClass` jest zdefiniowany w dwie przestrzenie nazw, jednej zagnieżdżone wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="45e1a-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="45e1a-119">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) jest używany do odróżnienia, która metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="45e1a-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="45e1a-120">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="45e1a-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="45e1a-121">Obszary nazw i typy mają unikatowe tytuły opisanego przez w pełni kwalifikowanych nazw, które wskazują logicznej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="45e1a-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="45e1a-122">Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typu, i `B` zagnieździć go.</span><span class="sxs-lookup"><span data-stu-id="45e1a-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="45e1a-123">W poniższym przykładzie istnieją zagnieżdżonych klas i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="45e1a-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="45e1a-124">W pełni kwalifikowana nazwa jest wskazywane jako komentarz następujące każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="45e1a-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="45e1a-125">W poprzednim segment kodu:</span><span class="sxs-lookup"><span data-stu-id="45e1a-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="45e1a-126">Przestrzeń nazw `N1` jest elementem członkowskim globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="45e1a-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="45e1a-127">Jego w pełni kwalifikowana nazwa to `N1`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="45e1a-128">Przestrzeń nazw `N2` jest elementem członkowskim `N1`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="45e1a-129">Jego w pełni kwalifikowana nazwa to `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="45e1a-130">Klasa `C1` jest elementem członkowskim `N1`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="45e1a-131">Jego w pełni kwalifikowana nazwa to `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="45e1a-132">Nazwa klasy `C2` jest używany na dwa razy, w tym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45e1a-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="45e1a-133">Jednak w pełni kwalifikowane nazwy są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="45e1a-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="45e1a-134">Pierwsze wystąpienie `C2` jest zadeklarowana wewnątrz `C1`; w związku z tym, jego w pełni kwalifikowana nazwa to: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="45e1a-135">Drugie wystąpienie `C2` jest zadeklarowany wewnątrz przestrzeni nazw `N2`; w związku z tym, jego w pełni kwalifikowana nazwa to `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="45e1a-136">Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski klasy `C3`, do przestrzeni nazw `N1.N2` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="45e1a-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="45e1a-137">Ogólnie rzecz biorąc, użyj `::` można odwoływać się do aliasu przestrzeni nazw lub `global::` można odwoływać się do globalnej przestrzeni nazw i `.` kwalifikowania typów ani elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="45e1a-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="45e1a-138">Jest to błąd, aby użyć `::` z aliasem, który odwołuje się do typu, a nie przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="45e1a-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="45e1a-139">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="45e1a-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="45e1a-140">Należy pamiętać, że wyraz `global` nie jest wstępnie zdefiniowanej w alias; w związku z tym, `global.X` nie ma żadnego specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="45e1a-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="45e1a-141">Uzyskuje, specjalne, co oznacza tylko wtedy, gdy jest używana z `::`.</span><span class="sxs-lookup"><span data-stu-id="45e1a-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="45e1a-142">Kompilator ostrzeżenie CS0440 jest generowany, jeśli zdefiniujesz aliasu o nazwie global ponieważ `global::` zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu.</span><span class="sxs-lookup"><span data-stu-id="45e1a-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="45e1a-143">Na przykład następujące polecenie generuje ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="45e1a-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="45e1a-144">Za pomocą `::` dobrym pomysłem jest z użyciem aliasów i chroni przed nieoczekiwanego wprowadzenia dodatkowych typów.</span><span class="sxs-lookup"><span data-stu-id="45e1a-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="45e1a-145">Na przykład rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="45e1a-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="45e1a-146">To działa, ale jeśli typu o nazwie `Alias` zostały następnie zostać wprowadzony `Alias.` czy zamiast tego powiązania do tego typu.</span><span class="sxs-lookup"><span data-stu-id="45e1a-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="45e1a-147">Za pomocą `Alias::Exception` ubezpieczycielom, `Alias` jest traktowana jako alias przestrzeni nazw, a nie mylone z typem.</span><span class="sxs-lookup"><span data-stu-id="45e1a-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="45e1a-148">Zobacz temat [instrukcje: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Aby uzyskać więcej informacji dotyczących `global` alias.</span><span class="sxs-lookup"><span data-stu-id="45e1a-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e1a-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45e1a-149">See Also</span></span>

- [<span data-ttu-id="45e1a-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45e1a-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="45e1a-151">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="45e1a-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="45e1a-152">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="45e1a-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="45e1a-153">. operator</span><span class="sxs-lookup"><span data-stu-id="45e1a-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="45e1a-154">::, operator</span><span class="sxs-lookup"><span data-stu-id="45e1a-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="45e1a-155">extern</span><span class="sxs-lookup"><span data-stu-id="45e1a-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
