---
title: "Metody anonimowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d942e0f3245f6404c896173b2c7ca6f1090a8c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="2decb-102">Metody anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2decb-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="2decb-103">W wersjach C# przed 2.0, jedynym sposobem, aby zadeklarować [delegować](../../../csharp/language-reference/keywords/delegate.md) było jednoczesne używanie [o nazwie metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2decb-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="2decb-104">C# 2.0 wprowadzono metody anonimowe i w języku C# 3.0 lub nowszej, wyrażenia lambda zastępują metod anonimowych jako preferowany sposób pisania kodu wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="2decb-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="2decb-105">Jednak informacje o metodach anonimowy w tym temacie dotyczą również wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="2decb-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="2decb-106">Istnieje jeden przypadek, w którym metody anonimowej udostępnia funkcje nie znaleziono w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="2decb-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="2decb-107">Metody anonimowe umożliwiają Pomiń listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="2decb-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="2decb-108">Oznacza to, że metody anonimowej można przekonwertować na delegatów o różnych podpisów.</span><span class="sxs-lookup"><span data-stu-id="2decb-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="2decb-109">To nie jest możliwe za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="2decb-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="2decb-110">Aby uzyskać więcej informacji, w szczególności o wyrażenia lambda, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2decb-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="2decb-111">Tworzenie metody anonimowe to zasadniczo sposób przekazać jako parametru delegowanego blok kodu.</span><span class="sxs-lookup"><span data-stu-id="2decb-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="2decb-112">Poniżej przedstawiono dwa przykłady:</span><span class="sxs-lookup"><span data-stu-id="2decb-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="2decb-113">Za pomocą metody anonimowe, można zmniejszyć kodowanie nakładów pracy, w tworzenie wystąpień obiektów delegowanych, ponieważ nie należy utworzyć oddzielny — metoda.</span><span class="sxs-lookup"><span data-stu-id="2decb-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="2decb-114">Na przykład określenie blok kodu zamiast Delegat może być przydatne w sytuacji, gdy konieczności tworzenia metody mogą wydawać się niepotrzebne koszty.</span><span class="sxs-lookup"><span data-stu-id="2decb-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="2decb-115">Dobrym przykładem może być, po uruchomieniu nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="2decb-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="2decb-116">Tworzy wątku tej klasy, a także zawiera kod, który wykonuje wątek bez tworzenia dodatkową metodę dla obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="2decb-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="2decb-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2decb-117">Remarks</span></span>  
 <span data-ttu-id="2decb-118">Zakres parametrów metody anonimowej jest *anonimowych bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="2decb-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="2decb-119">Błąd ma zestawienie szybkiego dostępu, takich jak [goto](../../../csharp/language-reference/keywords/goto.md), [podziału](../../../csharp/language-reference/keywords/break.md), lub [kontynuować](../../../csharp/language-reference/keywords/continue.md), wewnątrz bloku metody anonimowej, jeśli element docelowy jest poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="2decb-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="2decb-120">Istnieje również błąd ma zestawienie szybkiego dostępu, takich jak `goto`, `break`, lub `continue`, spoza bloku metody anonimowej, jeśli element docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="2decb-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="2decb-121">Zmienne lokalne i parametrów, których zakres zawiera deklarację metody anonimowej są nazywane *zewnętrzne* zmienne metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="2decb-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="2decb-122">Na przykład w następujących segment kodu `n` jest zmienną zewnętrznych:</span><span class="sxs-lookup"><span data-stu-id="2decb-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="2decb-123">Odwołanie do zmiennej zewnętrzne `n` jest określany jako *przechwycone* utworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="2decb-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="2decb-124">W przeciwieństwie do zmiennych lokalnych okres istnienia przechwyconej zmiennej rozszerza do momentu przyznania wyrzucanie elementów bezużytecznych delegatów, które odwołują się metody anonimowe.</span><span class="sxs-lookup"><span data-stu-id="2decb-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="2decb-125">Nie ma dostępu do metody anonimowej [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametry zewnętrznym zakresie.</span><span class="sxs-lookup"><span data-stu-id="2decb-125">An anonymous method cannot access the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="2decb-126">Nie niebezpieczny kod jest dostępny w ramach *anonimowych bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="2decb-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="2decb-127">Metody anonimowe nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="2decb-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2decb-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="2decb-128">Example</span></span>  
 <span data-ttu-id="2decb-129">Poniższy przykład przedstawia dwa sposoby tworzenia wystąpienia delegata:</span><span class="sxs-lookup"><span data-stu-id="2decb-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="2decb-130">Skojarzenie delegata z metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="2decb-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="2decb-131">Skojarzenie delegata z metodę o nazwie (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="2decb-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="2decb-132">W każdym przypadku gdy jest wywoływany delegat zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="2decb-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2decb-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2decb-133">See Also</span></span>  
 [<span data-ttu-id="2decb-134">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2decb-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2decb-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2decb-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2decb-136">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="2decb-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="2decb-137">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2decb-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="2decb-138">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="2decb-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="2decb-139">Metody</span><span class="sxs-lookup"><span data-stu-id="2decb-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="2decb-140">Obiekty delegowane z nazwanego vs. Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="2decb-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
