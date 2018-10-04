---
title: Delegaty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 96de5601c60dd309fe5467414affd20b8bc93d87
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584212"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="ab175-102">Delegaty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ab175-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="ab175-103">A [delegować](../../../csharp/language-reference/keywords/delegate.md) to typ, który reprezentuje odwołania do metod z określoną listą parametrów i typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="ab175-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="ab175-104">Podczas tworzenia wystąpienia delegata można skojarzyć jego wystąpienie z dowolną metodą mającą zgodny podpis i zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="ab175-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="ab175-105">Za pośrednictwem wystąpienia delegata można wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="ab175-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="ab175-106">Delegaty służą do przekazywania metod jako argumentów do innych metod.</span><span class="sxs-lookup"><span data-stu-id="ab175-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="ab175-107">Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów.</span><span class="sxs-lookup"><span data-stu-id="ab175-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ab175-108">Użytkownik tworzy metodę niestandardową, a klasa, taka jak formant systemu Windows, może wywołać tę metodę, gdy wystąpi określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ab175-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="ab175-109">W poniższym przykładzie pokazano deklarację delegata:</span><span class="sxs-lookup"><span data-stu-id="ab175-109">The following example shows a delegate declaration:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="ab175-110">Do delegata można przypisać każdą metodę z dowolnej dostępnej klasy lub struktury, która pasuje do typu delegata.</span><span class="sxs-lookup"><span data-stu-id="ab175-110">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="ab175-111">Może to być metoda statyczna lub metoda wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab175-111">The method can be either static or an instance method.</span></span> <span data-ttu-id="ab175-112">Umożliwia to programowe zmienianie wywołań metod, a także podłączanie nowego kodu do istniejących klas.</span><span class="sxs-lookup"><span data-stu-id="ab175-112">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab175-113">W kontekście przeciążania metod podpis metody nie zawiera wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="ab175-113">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="ab175-114">Jednak w kontekście delegatów podpis zawiera wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="ab175-114">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="ab175-115">Innymi słowy metoda musi mieć taki sam zwracany typ jak delegat.</span><span class="sxs-lookup"><span data-stu-id="ab175-115">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="ab175-116">Ta możliwość odwoływania się do metody jak do parametru sprawia, że delegaty idealnie nadają się do definiowania metod wywoływania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab175-116">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="ab175-117">Na przykład odwołanie do metody, która porównuje dwa obiekty można przekazać jako argument do algorytmu sortowania.</span><span class="sxs-lookup"><span data-stu-id="ab175-117">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="ab175-118">Kod porównania znajduje się w osobnej procedurze, więc algorytm sortowania można napisać w bardziej ogólny sposób.</span><span class="sxs-lookup"><span data-stu-id="ab175-118">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="ab175-119">Omówienie delegatów</span><span class="sxs-lookup"><span data-stu-id="ab175-119">Delegates Overview</span></span>  
 <span data-ttu-id="ab175-120">Delegaty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab175-120">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="ab175-121">Delegaty są podobne do wskaźników funkcji języka C++, ale obiekty delegowane są w pełni zorientowane obiektowo, a w przeciwieństwie do języka C++ wskaźników do składowych, delegatów hermetyzacji zarówno w przypadku wystąpienia obiektu, jak i metody.</span><span class="sxs-lookup"><span data-stu-id="ab175-121">Delegates are similar to C++ function pointers, but delegates are fully object-oriented, and unlike C++ pointers to member functions, delegates encapsulate both an object instance and a method.</span></span>
  
-   <span data-ttu-id="ab175-122">Delegaty zezwalają na przekazywanie metod jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="ab175-122">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="ab175-123">Delegatów można używać do definiowania metod wywoływania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab175-123">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="ab175-124">Delegaty można łączyć w łańcuch; na przykład w jednym zdarzeniu można wywołać wiele metod.</span><span class="sxs-lookup"><span data-stu-id="ab175-124">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="ab175-125">Metody nie muszą dokładnie pasować do typu delegata.</span><span class="sxs-lookup"><span data-stu-id="ab175-125">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="ab175-126">Aby uzyskać więcej informacji, zobacz [przy użyciu wariancje w Delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="ab175-126">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="ab175-127">C# w wersji 2.0 wprowadzono koncepcję [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), które umożliwiają bloków kodu, które zostaną przekazane jako parametry, zamiast oddzielnie definiowanej metody.</span><span class="sxs-lookup"><span data-stu-id="ab175-127">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="ab175-128">W języku C# 3.0 wprowadzono wyrażenia lambda, które stanową wygodniejszy sposób pisania bloków kodu w tekście.</span><span class="sxs-lookup"><span data-stu-id="ab175-128">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="ab175-129">Zarówno metody anonimowe, jak i wyrażenia lambda (w pewnych kontekstach) są kompilowane na typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="ab175-129">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="ab175-130">Te funkcje są obecnie nazywane łącznie funkcjami anonimowymi.</span><span class="sxs-lookup"><span data-stu-id="ab175-130">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="ab175-131">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ab175-131">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab175-132">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ab175-132">In This Section</span></span>  
  
-   [<span data-ttu-id="ab175-133">Używanie delegatów</span><span class="sxs-lookup"><span data-stu-id="ab175-133">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="ab175-134">Kiedy należy używać obiektów delegowanych zamiast interfejsów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="ab175-134">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](https://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="ab175-135">Delegaci z metodami nazwanymi lub anonimowymi</span><span class="sxs-lookup"><span data-stu-id="ab175-135">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="ab175-136">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="ab175-136">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="ab175-137">Korzystanie z wariancji w delegatach</span><span class="sxs-lookup"><span data-stu-id="ab175-137">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="ab175-138">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)</span><span class="sxs-lookup"><span data-stu-id="ab175-138">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="ab175-139">Instrukcje: deklarowanie, tworzenie wystąpień i użycie delegowania</span><span class="sxs-lookup"><span data-stu-id="ab175-139">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ab175-140">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ab175-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="ab175-141">Polecane rozdziały książki</span><span class="sxs-lookup"><span data-stu-id="ab175-141">Featured Book Chapters</span></span>  
 <span data-ttu-id="ab175-142">[Delegatów, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, wydanie trzecie: ponad 250 rozwiązań dla programistów C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="ab175-142">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="ab175-143">[Delegaci i zdarzenia](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) w [Nauka języka C# 3.0: Opanuj podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="ab175-143">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab175-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab175-144">See Also</span></span>

- <xref:System.Delegate>  
- [<span data-ttu-id="ab175-145">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ab175-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ab175-146">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ab175-146">Events</span></span>](../../../csharp/programming-guide/events/index.md)
