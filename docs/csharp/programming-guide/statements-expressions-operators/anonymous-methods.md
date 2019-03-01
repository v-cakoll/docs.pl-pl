---
title: Metody anonimowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 55a39bb311d4f0a71f111db4975abf317d63d479
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979674"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="a283e-102">Metody anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a283e-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="a283e-103">W wersjach C# przed 2.0, jedynym sposobem, aby zadeklarować [delegować](../../../csharp/language-reference/keywords/delegate.md) było jednoczesne używanie [o nazwie metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a283e-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="a283e-104">C# w wersji 2.0 wprowadzono metod anonimowych, a w języku C# 3.0 i nowszych wyrażenia lambda zastępują metody anonimowe jako preferowanym sposobem pisania kodu wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="a283e-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="a283e-105">Jednak informacje dotyczące metod anonimowych, w tym temacie dotyczą także wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="a283e-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="a283e-106">Istnieje jeden przypadek, w którym metoda anonimowa udostępnia funkcje, nie można odnaleźć w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="a283e-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="a283e-107">Metody anonimowe umożliwiają pominąć listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="a283e-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="a283e-108">Oznacza to, że metoda anonimowa mogą być konwertowane na obiektów delegowanych z różnymi podpisami.</span><span class="sxs-lookup"><span data-stu-id="a283e-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="a283e-109">Nie jest to możliwe za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a283e-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="a283e-110">Aby uzyskać konkretne informacje na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a283e-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a283e-111">Tworzenie metod anonimowych jest zasadniczo sposób przekazania bloku kodu jako parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="a283e-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="a283e-112">Poniżej przedstawiono dwa przykłady:</span><span class="sxs-lookup"><span data-stu-id="a283e-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 <span data-ttu-id="a283e-113">Za pomocą metod anonimowych, zmniejszasz kodowanie obciążenie, przy użyciu programu Tworzenie wystąpień obiektów delegowanych, ponieważ nie trzeba tworzyć oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="a283e-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="a283e-114">Na przykład określając blok kodu, zamiast delegata może być przydatne w sytuacji, mając do utworzenia metody mogą wydawać się niepotrzebne koszty.</span><span class="sxs-lookup"><span data-stu-id="a283e-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="a283e-115">Dobrym przykładem może być, po uruchomieniu nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="a283e-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="a283e-116">Ta klasa tworzy wątek i również zawiera kod, który wątek wykonuje bez tworzenia dodatkową metodę dla delegata.</span><span class="sxs-lookup"><span data-stu-id="a283e-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a><span data-ttu-id="a283e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a283e-117">Remarks</span></span>  
 <span data-ttu-id="a283e-118">Zakres parametry metoda anonimowa jest *anonimowe bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="a283e-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="a283e-119">Jest błędem instrukcja skoku, takiej jak [goto](../../../csharp/language-reference/keywords/goto.md), [podziału](../../../csharp/language-reference/keywords/break.md), lub [nadal](../../../csharp/language-reference/keywords/continue.md), wewnątrz bloku metody anonimowej, jeśli element docelowy znajduje się poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="a283e-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="a283e-120">Warto również błędem instrukcja skoku, takiej jak `goto`, `break`, lub `continue`, poza bloku metody anonimowej, jeśli element docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="a283e-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="a283e-121">Zmienne lokalne i parametry, których zakres zawiera deklarację metody anonimowej, są nazywane *zewnętrzne* zmienne metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="a283e-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="a283e-122">Na przykład w następujących segment kodu `n` jest zewnętrzna zmienna:</span><span class="sxs-lookup"><span data-stu-id="a283e-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 <span data-ttu-id="a283e-123">Odwołanie do zewnętrznej zmiennej `n` jest nazywany *przechwycone* po utworzeniu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="a283e-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="a283e-124">W przeciwieństwie do zmiennych lokalnych okres istnienia zmiennej przechwyconej rozszerza, dopóki nie kwalifikuje się do wyrzucania elementów bezużytecznych delegatów, które odwołują się metody anonimowe.</span><span class="sxs-lookup"><span data-stu-id="a283e-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="a283e-125">Nie ma dostępu do metody anonimowej [w](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry zakresu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="a283e-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="a283e-126">Nie niebezpieczny kod jest możliwy w ciągu *anonimowe bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="a283e-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="a283e-127">Metody anonimowe nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="a283e-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a283e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="a283e-128">Example</span></span>  
 <span data-ttu-id="a283e-129">Poniższy przykład przedstawia dwa sposoby tworzenia wystąpienia delegata:</span><span class="sxs-lookup"><span data-stu-id="a283e-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="a283e-130">Skojarzenie obiektu delegowanego z metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="a283e-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="a283e-131">Skojarzenie obiektu delegowanego z metody nazwanej (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="a283e-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="a283e-132">W obu przypadkach komunikat jest wyświetlane, gdy obiekt delegowany jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="a283e-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a283e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a283e-133">See also</span></span>

- [<span data-ttu-id="a283e-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a283e-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a283e-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a283e-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a283e-136">Delegaty</span><span class="sxs-lookup"><span data-stu-id="a283e-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="a283e-137">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="a283e-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="a283e-138">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="a283e-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="a283e-139">Metody</span><span class="sxs-lookup"><span data-stu-id="a283e-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="a283e-140">Delegaci z metodami nazwanymi lub anonimowymi</span><span class="sxs-lookup"><span data-stu-id="a283e-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
