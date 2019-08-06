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
ms.openlocfilehash: 06ebb9edfaf4753b98c3305a90b52e93ee7b4486
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796635"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="e900a-102">Używanie przestrzeni nazwC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="e900a-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="e900a-103">Przestrzenie nazw są intensywnie używane w C# programach na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="e900a-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="e900a-104">Po pierwsze klasy .NET Framework używają przestrzeni nazw do organizowania wielu klas.</span><span class="sxs-lookup"><span data-stu-id="e900a-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="e900a-105">Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.</span><span class="sxs-lookup"><span data-stu-id="e900a-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="e900a-106">Uzyskiwanie dostępu do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="e900a-106">Accessing namespaces</span></span>

 <span data-ttu-id="e900a-107">Większość C# aplikacji rozpoczyna się od sekcji `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="e900a-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="e900a-108">Ta sekcja zawiera listę przestrzeni nazw, których aplikacja będzie często używać, i zapisuje programistę w celu określenia w pełni kwalifikowanej nazwy za każdym razem, gdy używana jest metoda, która jest zawarta w.</span><span class="sxs-lookup"><span data-stu-id="e900a-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="e900a-109">Na przykład, dołączając wiersz:</span><span class="sxs-lookup"><span data-stu-id="e900a-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="e900a-110">Na początku programu programista może użyć kodu:</span><span class="sxs-lookup"><span data-stu-id="e900a-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="e900a-111">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="e900a-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="e900a-112">Aliasy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="e900a-112">Namespace aliases</span></span>

 <span data-ttu-id="e900a-113">Możesz również użyć [ `using` dyrektywy](../../language-reference/keywords/using-directive.md) , aby utworzyć alias dla przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="e900a-114">Użyj [kwalifikatora `::` aliasu przestrzeni nazw](../../language-reference/operators/namespace-alias-qualifier.md) , aby uzyskać dostęp do elementów członkowskich aliasu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="e900a-115">Poniższy przykład przedstawia sposób tworzenia i używania aliasu przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="e900a-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="e900a-116">Używanie przestrzeni nazw do sterowania zakresem</span><span class="sxs-lookup"><span data-stu-id="e900a-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="e900a-117">`namespace` Słowo kluczowe jest używane do deklarowania zakresu.</span><span class="sxs-lookup"><span data-stu-id="e900a-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="e900a-118">Możliwość tworzenia zakresów w projekcie pomaga organizować kod i umożliwia tworzenie typów unikatowych globalnie.</span><span class="sxs-lookup"><span data-stu-id="e900a-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="e900a-119">W poniższym przykładzie Klasa zatytułowana `SampleClass` jest zdefiniowana w dwóch przestrzeniach nazw, jedna zagnieżdżona w drugim.</span><span class="sxs-lookup"><span data-stu-id="e900a-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="e900a-120">[Operator `.` dostępu do elementów członkowskich](../../language-reference/operators/member-access-operators.md#member-access-operator-) jest używany do odróżnienia metody wywoływanej.</span><span class="sxs-lookup"><span data-stu-id="e900a-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="e900a-121">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="e900a-121">Fully qualified names</span></span>

 <span data-ttu-id="e900a-122">Przestrzenie nazw i typy mają unikatowe tytuły opisane przez w pełni kwalifikowane nazwy wskazujące hierarchię logiczną.</span><span class="sxs-lookup"><span data-stu-id="e900a-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="e900a-123">Na przykład instrukcja `A.B` oznacza, że `A` jest nazwą przestrzeni nazw lub typem, i `B` jest zagnieżdżona wewnątrz niej.</span><span class="sxs-lookup"><span data-stu-id="e900a-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="e900a-124">W poniższym przykładzie istnieją zagnieżdżone klasy i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="e900a-125">W pełni kwalifikowana nazwa jest wskazywana jako komentarz po każdej jednostce.</span><span class="sxs-lookup"><span data-stu-id="e900a-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="e900a-126">W poprzednim segmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="e900a-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="e900a-127">Przestrzeń nazw `N1` jest członkiem globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="e900a-128">Jego w pełni kwalifikowana nazwa `N1`jest.</span><span class="sxs-lookup"><span data-stu-id="e900a-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="e900a-129">Przestrzeń nazw `N2` jest `N1`członkiem.</span><span class="sxs-lookup"><span data-stu-id="e900a-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="e900a-130">Jego w pełni kwalifikowana nazwa `N1.N2`jest.</span><span class="sxs-lookup"><span data-stu-id="e900a-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="e900a-131">Klasa `C1` jest`N1`członkiem.</span><span class="sxs-lookup"><span data-stu-id="e900a-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="e900a-132">Jego w pełni kwalifikowana nazwa `N1.C1`jest.</span><span class="sxs-lookup"><span data-stu-id="e900a-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="e900a-133">Nazwa `C2` klasy jest używana dwa razy w tym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e900a-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="e900a-134">Jednak w pełni kwalifikowane nazwy są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="e900a-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="e900a-135">Pierwsze wystąpienie `C2` jest zadeklarowane wewnątrz `C1`; w związku z tym jego w pełni kwalifikowana nazwa `N1.C1.C2`to:.</span><span class="sxs-lookup"><span data-stu-id="e900a-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="e900a-136">Drugie wystąpienie `C2` jest zadeklarowane wewnątrz przestrzeni nazw `N2`; w związku z tym jego w pełni kwalifikowana `N1.N2.C2`nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="e900a-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="e900a-137">Korzystając z poprzedniego segmentu kodu, można dodać nowy element członkowski `C3`klasy,, do przestrzeni nazw `N1.N2` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e900a-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="e900a-138">Ogólnie rzecz biorąc służy `::` do odwoływania się do aliasu przestrzeni nazw lub `global::` odwoływania `.` się do globalnej przestrzeni nazw oraz do kwalifikowania typów lub członków.</span><span class="sxs-lookup"><span data-stu-id="e900a-138">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="e900a-139">Jest to błąd używany `::` z aliasem, który odwołuje się do typu zamiast przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="e900a-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e900a-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="e900a-141">Należy pamiętać, że `global` słowo nie jest wstępnie zdefiniowanym aliasem `global.X` ; w związku z tym nie ma żadnych specjalnych znaczenia.</span><span class="sxs-lookup"><span data-stu-id="e900a-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="e900a-142">Uzyskuje specjalne znaczenie tylko wtedy, gdy jest używany z `::`.</span><span class="sxs-lookup"><span data-stu-id="e900a-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="e900a-143">Ostrzeżenie kompilatora CS0440 jest generowany, jeśli zdefiniujesz alias o nazwie Global `global::` , ponieważ zawsze odwołuje się do globalnej przestrzeni nazw, a nie do aliasu.</span><span class="sxs-lookup"><span data-stu-id="e900a-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="e900a-144">Na przykład poniższy wiersz generuje ostrzeżenie:</span><span class="sxs-lookup"><span data-stu-id="e900a-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="e900a-145">Korzystanie `::` z aliasów jest dobrym pomysłem i chroni przed nieoczekiwanym wprowadzeniem dodatkowych typów.</span><span class="sxs-lookup"><span data-stu-id="e900a-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="e900a-146">Rozważmy na przykład ten przykład:</span><span class="sxs-lookup"><span data-stu-id="e900a-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="e900a-147">To działa, ale jeśli typ nazwany `Alias` miał zostać później wprowadzony, `Alias.` zostałby powiązać z tym typem.</span><span class="sxs-lookup"><span data-stu-id="e900a-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="e900a-148">Użycie `Alias::Exception` gwarantuje, `Alias` że jest traktowany jako alias przestrzeni nazw i nie zostanie pomylony z typem.</span><span class="sxs-lookup"><span data-stu-id="e900a-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="e900a-149">Zapoznaj się [z tematem How to: Aby uzyskać więcej informacji na](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) `global` temat aliasu, Użyj globalnego aliasu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e900a-149">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e900a-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e900a-150">See also</span></span>

- [<span data-ttu-id="e900a-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e900a-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e900a-152">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="e900a-152">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="e900a-153">. zakład</span><span class="sxs-lookup"><span data-stu-id="e900a-153">. operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="e900a-154">:: operator</span><span class="sxs-lookup"><span data-stu-id="e900a-154">:: operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="e900a-155">extern alias</span><span class="sxs-lookup"><span data-stu-id="e900a-155">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
