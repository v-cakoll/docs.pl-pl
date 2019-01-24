---
title: 'Instrukcje: Deklarowanie, tworzenie wystąpień i użycie delegowania - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 8ecbac4608cfd42aa099a0cd66d7d22241a93265
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557711"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="1669d-102">Instrukcje: Deklarowanie, tworzenie wystąpień i użycie delegowania (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1669d-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="1669d-103">W języku C# 1.0 lub nowszy można zadeklarować delegatów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1669d-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="1669d-104">C# w wersji 2.0 zapewnia prostszy sposób zapisu poprzedniej deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1669d-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="1669d-105">W języku C# w wersji 2.0 lub nowszy, jest również możliwość użycia metodę anonimową do zadeklarowania i zainicjowania [delegować](../../../csharp/language-reference/keywords/delegate.md), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1669d-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="1669d-106">W języku C# 3.0 i nowszych delegatów również można zadeklarować i tworzone przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1669d-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="1669d-107">Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1669d-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="1669d-108">Poniższy przykład ilustruje deklarowanie, tworzenie wystąpienia i za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="1669d-109">`BookDB` Klasa hermetyzuje księgarni bazy danych, który obsługuje bazę danych książek.</span><span class="sxs-lookup"><span data-stu-id="1669d-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="1669d-110">Udostępnia metody, `ProcessPaperbackBooks`, który umożliwia znalezienie wszystkich drukowanego podręcznika książek w bazie danych i wywołuje delegata dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="1669d-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="1669d-111">`delegate` Nosi nazwę typu, który jest używany `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1669d-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="1669d-112">`Test` Klasy do drukowania, tytuły i średnia cena drukowanego podręcznika książek, które korzysta z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="1669d-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="1669d-113">Użyj obiektów delegowanych promuje dobre rozdzielanie funkcji między księgarni bazy danych i kod klienta.</span><span class="sxs-lookup"><span data-stu-id="1669d-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="1669d-114">Kod klienta nie ma informacji o jak książki są przechowywane lub jak kod księgarni znajduje drukowanego podręcznika książki.</span><span class="sxs-lookup"><span data-stu-id="1669d-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="1669d-115">Kod księgarni nie ma informacji o jakie przetwarzanie jest realizowane na książki drukowanego podręcznika, po nich znajdzie.</span><span class="sxs-lookup"><span data-stu-id="1669d-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1669d-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1669d-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1669d-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1669d-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="1669d-118">Deklarowanie delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="1669d-119">Poniższa instrukcja deklaruje nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="1669d-120">Każdy typ delegata opisuje liczbę i typy argumentów oraz typ wartość zwracaną metody, które można hermetyzacji.</span><span class="sxs-lookup"><span data-stu-id="1669d-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="1669d-121">Zawsze, gdy będzie potrzebny nowy zestaw typów argumentów lub typ zwracanej wartości, musi być zadeklarowany nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="1669d-122">Utworzenie wystąpienia delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="1669d-123">Po zadeklarowany typ delegata obiektu delegowanego muszą być tworzone i skojarzonych z konkretną metodę.</span><span class="sxs-lookup"><span data-stu-id="1669d-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="1669d-124">W poprzednim przykładzie, możesz to zrobić, przekazując `PrintTitle` metody `ProcessPaperbackBooks` metodę jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1669d-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="1669d-125">Spowoduje to utworzenie nowego obiektu delegowanego skojarzone z [statyczne](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="1669d-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="1669d-126">Podobnie, niestatycznej metody `AddBookToTotal` obiektu `totaller` jest przekazywana tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1669d-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="1669d-127">W obu przypadkach nowy obiekt delegowany jest przekazywany do `ProcessPaperbackBooks` metody.</span><span class="sxs-lookup"><span data-stu-id="1669d-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="1669d-128">Po utworzeniu delegata, metoda jest skojarzony z nigdy nie zmiany. Delegat obiekty są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1669d-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="1669d-129">Podczas wywoływania delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="1669d-130">Po utworzeniu obiektu delegowanego, obiektu delegowanego jest zazwyczaj przekazywany do innego kodu, który wywoła delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="1669d-131">Obiekt delegowany jest wywoływany przez przy użyciu nazwy obiektu delegowanego, następuje argumenty ujęty w nawiasy, które zostaną przekazane do delegata.</span><span class="sxs-lookup"><span data-stu-id="1669d-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="1669d-132">Poniżej znajduje się przykład wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="1669d-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="1669d-133">Delegat może być albo wywoływana synchronicznie, jak w poniższym przykładzie lub asynchronicznie przy użyciu `BeginInvoke` i `EndInvoke` metody.</span><span class="sxs-lookup"><span data-stu-id="1669d-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1669d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1669d-134">See also</span></span>

- [<span data-ttu-id="1669d-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1669d-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1669d-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1669d-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="1669d-137">Delegaty</span><span class="sxs-lookup"><span data-stu-id="1669d-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
