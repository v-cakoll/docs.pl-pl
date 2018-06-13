---
title: Używanie przestrzeni nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 773add221317a2154ac620acf766607ec22c629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329550"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="39180-102">Używanie przestrzeni nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="39180-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="39180-103">Przestrzenie nazw silnie są używane w ramach programów C# na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="39180-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="39180-104">Po pierwsze klas .NET Framework umożliwia organizowanie jego wiele klas przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="39180-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="39180-105">Po drugie deklarowanie własnych przestrzeni nazw można kontrolować zakres klasy i metody nazwy w większych projektów programowania.</span><span class="sxs-lookup"><span data-stu-id="39180-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="39180-106">Uzyskiwanie dostępu do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="39180-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="39180-107">Większość aplikacji C# zaczynać sekcję `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="39180-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="39180-108">Ta sekcja zawiera listę nazw często można za pomocą aplikacji i zapisuje programisty z określania każdym użyciu metody, która jest zawarta w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="39180-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="39180-109">Na przykład umieszczając w niej wiersz:</span><span class="sxs-lookup"><span data-stu-id="39180-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="39180-110">Na początku programu programistę można użyć kodu:</span><span class="sxs-lookup"><span data-stu-id="39180-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="39180-111">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="39180-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="39180-112">Aliasy Namespace</span><span class="sxs-lookup"><span data-stu-id="39180-112">Namespace Aliases</span></span>  
 <span data-ttu-id="39180-113">[Dyrektywa using](../../../csharp/language-reference/keywords/using-directive.md) może również służyć do tworzenia aliasu dla [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="39180-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="39180-114">Na przykład jeśli używasz wcześniej zapisany przestrzeni nazw, która zawiera zagnieżdżone przestrzeni nazw można deklarować aliasu, aby zapewnić sposób skrócona odwołujące się do jednego w szczególności, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39180-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="39180-115">Używanie przestrzeni nazw do zakresu kontroli</span><span class="sxs-lookup"><span data-stu-id="39180-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="39180-116">`namespace` — Słowo kluczowe służy do deklarowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="39180-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="39180-117">Możliwość tworzenia zakresów w ramach projektu ułatwia organizowanie kodu i umożliwia utworzenie typów globalnie unikatowe.</span><span class="sxs-lookup"><span data-stu-id="39180-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="39180-118">W poniższym przykładzie klasa zatytułowany `SampleClass` jest zdefiniowany w dwóch obszarach nazw jedną zagnieżdżone w innych.</span><span class="sxs-lookup"><span data-stu-id="39180-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="39180-119">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) służy do rozróżnienia, która metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="39180-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="39180-120">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="39180-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="39180-121">Obszary nazw i typy mają unikatowe tytułów opisanego przez w pełni kwalifikowane nazwy wskazujące logicznej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="39180-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="39180-122">Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typu, i `B` jest zagnieżdżony w nim.</span><span class="sxs-lookup"><span data-stu-id="39180-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="39180-123">W poniższym przykładzie są zagnieżdżone klasy i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="39180-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="39180-124">W pełni kwalifikowana nazwa jest oznaczony jako komentarz po każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="39180-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="39180-125">W poprzednich segment kodu:</span><span class="sxs-lookup"><span data-stu-id="39180-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="39180-126">Przestrzeń nazw `N1` jest członkiem grupy globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="39180-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="39180-127">Jest w pełni kwalifikowanej nazwy `N1`.</span><span class="sxs-lookup"><span data-stu-id="39180-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="39180-128">Przestrzeń nazw `N2` jest elementem członkowskim `N1`.</span><span class="sxs-lookup"><span data-stu-id="39180-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="39180-129">Jest w pełni kwalifikowanej nazwy `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="39180-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="39180-130">Klasa `C1` jest elementem członkowskim `N1`.</span><span class="sxs-lookup"><span data-stu-id="39180-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="39180-131">Jest w pełni kwalifikowanej nazwy `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="39180-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="39180-132">Nazwa klasy `C2` służy dwa razy w tym kodzie.</span><span class="sxs-lookup"><span data-stu-id="39180-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="39180-133">Jednak w pełni kwalifikowane nazwy są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="39180-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="39180-134">Pierwsze wystąpienie `C2` jest zadeklarowana wewnątrz `C1`; w związku z tym jest w pełni kwalifikowanej nazwy: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="39180-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="39180-135">Drugie wystąpienie parametru `C2` jest zadeklarowany wewnątrz przestrzeni nazw `N2`; w związku z tym jest w pełni kwalifikowanej nazwy `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="39180-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="39180-136">Używając poprzedniego segmentu kodu, można dodać nowy element członkowski klasy `C3`, do przestrzeni nazw `N1.N2` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="39180-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="39180-137">Ogólnie rzecz biorąc, użyj `::` do odwołania aliasu przestrzeni nazw lub `global::` do odwołania globalnej przestrzeni nazw i `.` na kwalifikować się do typów albo elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="39180-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="39180-138">Jest błędem `::` z aliasem odwołuje się do typu zamiast przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="39180-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="39180-139">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="39180-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="39180-140">Należy pamiętać, że wyraz `global` nie jest wstępnie zdefiniowanej alias; w związku z tym `global.X` nie ma żadnego specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="39180-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="39180-141">Uzyskuje, specjalne, co oznacza tylko wtedy, gdy jest używany z `::`.</span><span class="sxs-lookup"><span data-stu-id="39180-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="39180-142">Kompilator ostrzeżenie CS0440 jest generowany w przypadku definiowania aliasu o nazwie global ponieważ `global::` zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu.</span><span class="sxs-lookup"><span data-stu-id="39180-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="39180-143">Na przykład poniższy wiersz generuje ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="39180-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="39180-144">Przy użyciu `::` z aliasami dobrym pomysłem jest i chroni przed wprowadzeniem nieoczekiwany dodatkowe typy.</span><span class="sxs-lookup"><span data-stu-id="39180-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="39180-145">Rozważmy na przykład w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="39180-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="39180-146">To działa, ale jeśli typu o nazwie `Alias` były następnie zostać wprowadzony, `Alias.` czy zamiast tego powiązania dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="39180-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="39180-147">Przy użyciu `Alias::Exception` temu, że `Alias` jest traktowane jako alias przestrzeni nazw i nie pomylone typu.</span><span class="sxs-lookup"><span data-stu-id="39180-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="39180-148">Zobacz temat [porady: użycie globalnych aliasów Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Aby uzyskać więcej informacji dotyczących `global` alias.</span><span class="sxs-lookup"><span data-stu-id="39180-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39180-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39180-149">See Also</span></span>  
 [<span data-ttu-id="39180-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="39180-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39180-151">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="39180-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="39180-152">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="39180-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="39180-153">. operator</span><span class="sxs-lookup"><span data-stu-id="39180-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="39180-154">::, operator</span><span class="sxs-lookup"><span data-stu-id="39180-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="39180-155">extern</span><span class="sxs-lookup"><span data-stu-id="39180-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
