---
title: Jak deklarować, utworzyć wystąpienia i używać pełnomocnika — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712367"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="92f9d-102">Jak deklarować, utworzyć wystąpienia i używać delegata (Przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="92f9d-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="92f9d-103">W języku C# 1.0 i nowszych delegatów można zadeklarować, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92f9d-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="92f9d-104">C# 2.0 zapewnia prostszy sposób pisania poprzedniej deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92f9d-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="92f9d-105">W języku C# 2.0 i nowszych jest również możliwe użycie metody anonimowej do deklarowania i inicjowania [delegata](../../language-reference/builtin-types/reference-types.md), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92f9d-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="92f9d-106">W języku C# 3.0 i nowszych delegatów można również zadeklarować i utworzyć wystąpienia przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92f9d-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="92f9d-107">Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="92f9d-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="92f9d-108">Poniższy przykład ilustruje deklarowanie, tworzenie wystąpień i korzystanie z pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="92f9d-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="92f9d-109">Klasa `BookDB` hermetyzuje bazę danych księgarni, która prowadzi bazę książek.</span><span class="sxs-lookup"><span data-stu-id="92f9d-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="92f9d-110">Udostępnia metodę, `ProcessPaperbackBooks`która znajduje wszystkie książki w kopii zapasowej w bazie danych i wywołuje delegata dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="92f9d-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="92f9d-111">Typ, `delegate` który jest `ProcessBookDelegate`używany nosi nazwę .</span><span class="sxs-lookup"><span data-stu-id="92f9d-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="92f9d-112">Klasa `Test` używa tej klasy do drukowania tytułów i średniej ceny książek w wersji papierowej.</span><span class="sxs-lookup"><span data-stu-id="92f9d-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="92f9d-113">Użycie delegatów promuje dobre oddzielenie funkcji między bazą danych księgarni a kodem klienta.</span><span class="sxs-lookup"><span data-stu-id="92f9d-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="92f9d-114">Kod klienta nie ma wiedzy o tym, jak książki są przechowywane lub jak kod księgarni znajdzie książki w wersji papierowej.</span><span class="sxs-lookup"><span data-stu-id="92f9d-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="92f9d-115">Kod księgarni nie ma wiedzy o tym, jakie przetwarzanie jest wykonywane na książkach miękkich po ich znalezieniu.</span><span class="sxs-lookup"><span data-stu-id="92f9d-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f9d-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="92f9d-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="92f9d-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="92f9d-117">Robust Programming</span></span>  
  
- <span data-ttu-id="92f9d-118">Deklarowanie pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="92f9d-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="92f9d-119">Następująca instrukcja deklaruje nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="92f9d-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="92f9d-120">Każdy typ delegata opisuje liczbę i typy argumentów oraz typ zwracanej wartości metod, które można hermetyzować.</span><span class="sxs-lookup"><span data-stu-id="92f9d-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="92f9d-121">Zawsze, gdy potrzebny jest nowy zestaw typów argumentów lub typ wartości zwracanej, należy zadeklarować nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="92f9d-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="92f9d-122">Tworzenie wystąpienia delegata.</span><span class="sxs-lookup"><span data-stu-id="92f9d-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="92f9d-123">Po zadeklarowaniu typu delegata obiekt delegata musi zostać utworzony i skojarzony z określoną metodą.</span><span class="sxs-lookup"><span data-stu-id="92f9d-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="92f9d-124">W poprzednim przykładzie można to zrobić, przekazując `PrintTitle` metodę do `ProcessPaperbackBooks` metody, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="92f9d-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="92f9d-125">Spowoduje to utworzenie nowego obiektu delegata `Test.PrintTitle`skojarzonego z metodą [statyczną](../../language-reference/keywords/static.md) .</span><span class="sxs-lookup"><span data-stu-id="92f9d-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="92f9d-126">Podobnie metoda `AddBookToTotal` niestatyczna na obiekcie `totaller` jest przekazywana jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="92f9d-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="92f9d-127">W obu przypadkach nowy obiekt delegata `ProcessPaperbackBooks` jest przekazywany do metody.</span><span class="sxs-lookup"><span data-stu-id="92f9d-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="92f9d-128">Po utworzeniu pełnomocnika metoda, z której jest skojarzona, nigdy się nie zmienia; obiekty delegata są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="92f9d-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="92f9d-129">Wywoływanie delegata.</span><span class="sxs-lookup"><span data-stu-id="92f9d-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="92f9d-130">Po utworzeniu obiektu pełnomocnika obiekt delegata jest zazwyczaj przekazywany do innego kodu, który wywoła pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="92f9d-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="92f9d-131">Obiekt delegata jest wywoływana przy użyciu nazwy obiektu delegata, a następnie nawiasy argumenty mają być przekazywane do delegata.</span><span class="sxs-lookup"><span data-stu-id="92f9d-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="92f9d-132">Poniżej przedstawiono przykład wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="92f9d-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="92f9d-133">Delegat może być wywoływany synchronicznie, jak w tym przykładzie, lub `BeginInvoke` `EndInvoke` asynchronicznie za pomocą i metod.</span><span class="sxs-lookup"><span data-stu-id="92f9d-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f9d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92f9d-134">See also</span></span>

- [<span data-ttu-id="92f9d-135">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="92f9d-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="92f9d-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92f9d-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="92f9d-137">Delegaty</span><span class="sxs-lookup"><span data-stu-id="92f9d-137">Delegates</span></span>](./index.md)
