---
title: Korzystanie z obszarów nazw — przewodnik po programowaniu języka C#
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 0947e597da93d6db1c5965b3685a509961778586
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507051"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="8a084-102">Korzystanie z obszarów nazw (Przewodnik programowania języka C#)</span><span class="sxs-lookup"><span data-stu-id="8a084-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="8a084-103">Przestrzenie nazw są intensywnie używane w programach Języka C# na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="8a084-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="8a084-104">Po pierwsze klasy .NET Framework używają obszarów nazw do organizowania wielu klas.</span><span class="sxs-lookup"><span data-stu-id="8a084-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="8a084-105">Po drugie, deklarowanie własnych obszarów nazw może pomóc kontrolować zakres nazw klas i metod w większych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="8a084-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="8a084-106">Uzyskiwanie dostępu do obszarów nazw</span><span class="sxs-lookup"><span data-stu-id="8a084-106">Accessing namespaces</span></span>

 <span data-ttu-id="8a084-107">Większość aplikacji Języka C# `using` rozpoczyna się od sekcji dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="8a084-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="8a084-108">W tej sekcji wymieniono obszary nazw, które aplikacja będzie często używać i zapisuje programistę z określania w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.</span><span class="sxs-lookup"><span data-stu-id="8a084-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="8a084-109">Na przykład, dołączając wiersz:</span><span class="sxs-lookup"><span data-stu-id="8a084-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="8a084-110">Na początku programu programista może użyć kodu:</span><span class="sxs-lookup"><span data-stu-id="8a084-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="8a084-111">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="8a084-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="8a084-112">Aliasy obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="8a084-112">Namespace aliases</span></span>

 <span data-ttu-id="8a084-113">Można również użyć [ `using` dyrektywy](../../language-reference/keywords/using-directive.md) do utworzenia aliasu dla obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="8a084-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="8a084-114">Użyj [kwalifikatora `::` aliasu obszaru nazw,](../../language-reference/operators/namespace-alias-qualifier.md) aby uzyskać dostęp do członków aliasowanego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="8a084-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="8a084-115">W poniższym przykładzie pokazano, jak utworzyć i używać aliasu obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="8a084-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="8a084-116">Sterowanie zakresem za pomocą obszarów nazw</span><span class="sxs-lookup"><span data-stu-id="8a084-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="8a084-117">Słowo `namespace` kluczowe służy do deklarowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="8a084-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="8a084-118">Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie.</span><span class="sxs-lookup"><span data-stu-id="8a084-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="8a084-119">W poniższym przykładzie klasa `SampleClass` zatytułowana jest zdefiniowana w dwóch obszarach nazw, jeden zagnieżdżony wewnątrz drugiego.</span><span class="sxs-lookup"><span data-stu-id="8a084-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="8a084-120">[ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) jest używany do rozróżniania, która metoda zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="8a084-120">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="8a084-121">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="8a084-121">Fully qualified names</span></span>

 <span data-ttu-id="8a084-122">Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy, które wskazują hierarchię logiczną.</span><span class="sxs-lookup"><span data-stu-id="8a084-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="8a084-123">Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą obszaru nazw `B` lub typu i jest zagnieżdżona wewnątrz niego.</span><span class="sxs-lookup"><span data-stu-id="8a084-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="8a084-124">W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="8a084-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="8a084-125">W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.</span><span class="sxs-lookup"><span data-stu-id="8a084-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="8a084-126">W poprzednim segmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="8a084-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="8a084-127">Obszar `N1` nazw jest członkiem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8a084-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="8a084-128">Jego w pełni `N1`kwalifikowana nazwa to .</span><span class="sxs-lookup"><span data-stu-id="8a084-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="8a084-129">Obszar `N2` nazw jest członkiem programu `N1`.</span><span class="sxs-lookup"><span data-stu-id="8a084-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="8a084-130">Jego w pełni `N1.N2`kwalifikowana nazwa to .</span><span class="sxs-lookup"><span data-stu-id="8a084-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="8a084-131">Klasa `C1` jest członkiem `N1`.</span><span class="sxs-lookup"><span data-stu-id="8a084-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="8a084-132">Jego w pełni `N1.C1`kwalifikowana nazwa to .</span><span class="sxs-lookup"><span data-stu-id="8a084-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="8a084-133">Nazwa `C2` klasy jest używana dwa razy w tym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8a084-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="8a084-134">Jednak w pełni kwalifikowane nazwy są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="8a084-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="8a084-135">Pierwsza instancja `C2` jest `C1`zadeklarowana wewnątrz ; w związku z tym jego `N1.C1.C2`w pełni kwalifikowana nazwa to: .</span><span class="sxs-lookup"><span data-stu-id="8a084-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="8a084-136">Drugie wystąpienie `C2` jest zadeklarowane `N2`wewnątrz obszaru nazw; w związku z tym `N1.N2.C2`jego w pełni kwalifikowana nazwa jest .</span><span class="sxs-lookup"><span data-stu-id="8a084-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="8a084-137">Korzystając z poprzedniego segmentu kodu, można `C3`dodać nowy element `N1.N2` członkowski klasy do obszaru nazw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8a084-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="8a084-138">Ogólnie rzecz biorąc, należy użyć [kwalifikatora `::` aliasu obszaru nazw,](../../language-reference/operators/namespace-alias-qualifier.md) aby odwołać się do aliasu obszaru nazw lub `global::` odwołać się do globalnego obszaru nazw i `.` zakwalifikować typy lub elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="8a084-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="8a084-139">Jest to błąd `::` do użycia z aliasem, który odwołuje się do typu zamiast obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="8a084-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="8a084-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="8a084-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="8a084-141">Należy pamiętać, `global` że słowo nie jest wstępnie zdefiniowanym aliasem; w związku `global.X` z tym nie ma żadnego szczególnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="8a084-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="8a084-142">Nabiera specjalnego znaczenia tylko wtedy, gdy `::`jest używany z .</span><span class="sxs-lookup"><span data-stu-id="8a084-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="8a084-143">Ostrzeżenie kompilatora CS0440 jest generowane, jeśli `global::` zdefiniowano alias o nazwie globalny, ponieważ zawsze odwołuje się do globalnej przestrzeni nazw, a nie aliasu.</span><span class="sxs-lookup"><span data-stu-id="8a084-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="8a084-144">Na przykład następujący wiersz generuje ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="8a084-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="8a084-145">Używanie `::` z aliasami jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów.</span><span class="sxs-lookup"><span data-stu-id="8a084-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="8a084-146">Rozważmy na przykład:</span><span class="sxs-lookup"><span data-stu-id="8a084-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="8a084-147">To działa, ale jeśli `Alias` typ o nazwie `Alias.` zostały następnie wprowadzone, będzie powiązana z tego typu zamiast.</span><span class="sxs-lookup"><span data-stu-id="8a084-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="8a084-148">Korzystanie `Alias::Exception` zapewnia, `Alias` że jest traktowany jako alias obszaru nazw i nie mylone z typem.</span><span class="sxs-lookup"><span data-stu-id="8a084-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="8a084-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a084-149">See also</span></span>

- [<span data-ttu-id="8a084-150">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="8a084-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8a084-151">Namespaces</span><span class="sxs-lookup"><span data-stu-id="8a084-151">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="8a084-152">Wyrażenie dostępu do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8a084-152">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="8a084-153">:: operator</span><span class="sxs-lookup"><span data-stu-id="8a084-153">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="8a084-154">extern alias</span><span class="sxs-lookup"><span data-stu-id="8a084-154">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
