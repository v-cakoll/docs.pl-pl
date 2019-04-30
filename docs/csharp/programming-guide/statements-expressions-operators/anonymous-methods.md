---
title: Metody anonimowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 94e9f7133c9a78ece7df5bd10cfc27c79d0652c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710007"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="385d3-102">Metody anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="385d3-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="385d3-103">W wersjach C# przed 2.0, jedynym sposobem, aby zadeklarować [delegować](../../../csharp/language-reference/keywords/delegate.md) było jednoczesne używanie [o nazwie metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="385d3-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="385d3-104">C# w wersji 2.0 wprowadzono metod anonimowych, a w języku C# 3.0 i nowszych wyrażenia lambda zastępują metody anonimowe jako preferowanym sposobem pisania kodu wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="385d3-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="385d3-105">Jednak informacje dotyczące metod anonimowych, w tym temacie dotyczą także wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="385d3-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="385d3-106">Istnieje jeden przypadek, w którym metoda anonimowa udostępnia funkcje, nie można odnaleźć w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="385d3-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="385d3-107">Metody anonimowe umożliwiają pominąć listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="385d3-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="385d3-108">Oznacza to, że metoda anonimowa mogą być konwertowane na obiektów delegowanych z różnymi podpisami.</span><span class="sxs-lookup"><span data-stu-id="385d3-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="385d3-109">Nie jest to możliwe za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="385d3-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="385d3-110">Aby uzyskać konkretne informacje na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="385d3-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="385d3-111">Tworzenie metod anonimowych jest zasadniczo sposób przekazania bloku kodu jako parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="385d3-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="385d3-112">Poniżej przedstawiono dwa przykłady:</span><span class="sxs-lookup"><span data-stu-id="385d3-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 <span data-ttu-id="385d3-113">Za pomocą metod anonimowych, zmniejszasz kodowanie obciążenie, przy użyciu programu Tworzenie wystąpień obiektów delegowanych, ponieważ nie trzeba tworzyć oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="385d3-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="385d3-114">Na przykład określając blok kodu, zamiast delegata może być przydatne w sytuacji, mając do utworzenia metody mogą wydawać się niepotrzebne koszty.</span><span class="sxs-lookup"><span data-stu-id="385d3-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="385d3-115">Dobrym przykładem może być, po uruchomieniu nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="385d3-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="385d3-116">Ta klasa tworzy wątek i również zawiera kod, który wątek wykonuje bez tworzenia dodatkową metodę dla delegata.</span><span class="sxs-lookup"><span data-stu-id="385d3-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a><span data-ttu-id="385d3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="385d3-117">Remarks</span></span>  
 <span data-ttu-id="385d3-118">Zakres parametry metoda anonimowa jest *anonimowe bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="385d3-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="385d3-119">Jest błędem instrukcja skoku, takiej jak [goto](../../../csharp/language-reference/keywords/goto.md), [podziału](../../../csharp/language-reference/keywords/break.md), lub [nadal](../../../csharp/language-reference/keywords/continue.md), wewnątrz bloku metody anonimowej, jeśli element docelowy znajduje się poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="385d3-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="385d3-120">Warto również błędem instrukcja skoku, takiej jak `goto`, `break`, lub `continue`, poza bloku metody anonimowej, jeśli element docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="385d3-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="385d3-121">Zmienne lokalne i parametry, których zakres zawiera deklarację metody anonimowej, są nazywane *zewnętrzne* zmienne metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="385d3-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="385d3-122">Na przykład w następujących segment kodu `n` jest zewnętrzna zmienna:</span><span class="sxs-lookup"><span data-stu-id="385d3-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 <span data-ttu-id="385d3-123">Odwołanie do zewnętrznej zmiennej `n` jest nazywany *przechwycone* po utworzeniu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="385d3-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="385d3-124">W przeciwieństwie do zmiennych lokalnych okres istnienia zmiennej przechwyconej rozszerza, dopóki nie kwalifikuje się do wyrzucania elementów bezużytecznych delegatów, które odwołują się metody anonimowe.</span><span class="sxs-lookup"><span data-stu-id="385d3-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="385d3-125">Nie ma dostępu do metody anonimowej [w](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry zakresu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="385d3-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="385d3-126">Nie niebezpieczny kod jest możliwy w ciągu *anonimowe bloku metody*.</span><span class="sxs-lookup"><span data-stu-id="385d3-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="385d3-127">Metody anonimowe nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="385d3-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="385d3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="385d3-128">Example</span></span>  
 <span data-ttu-id="385d3-129">Poniższy przykład przedstawia dwa sposoby tworzenia wystąpienia delegata:</span><span class="sxs-lookup"><span data-stu-id="385d3-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
- <span data-ttu-id="385d3-130">Skojarzenie obiektu delegowanego z metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="385d3-130">Associating the delegate with an anonymous method.</span></span>  
  
- <span data-ttu-id="385d3-131">Skojarzenie obiektu delegowanego z metody nazwanej (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="385d3-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="385d3-132">W obu przypadkach komunikat jest wyświetlane, gdy obiekt delegowany jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="385d3-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="385d3-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="385d3-133">See also</span></span>

- [<span data-ttu-id="385d3-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="385d3-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="385d3-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="385d3-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="385d3-136">Delegaty</span><span class="sxs-lookup"><span data-stu-id="385d3-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="385d3-137">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="385d3-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="385d3-138">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="385d3-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="385d3-139">Metody</span><span class="sxs-lookup"><span data-stu-id="385d3-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="385d3-140">Delegaci z metodami nazwanymi lub anonimowymi</span><span class="sxs-lookup"><span data-stu-id="385d3-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
