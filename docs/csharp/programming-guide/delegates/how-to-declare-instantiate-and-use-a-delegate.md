---
title: 'Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 19e5883135d65a648bb6afb74a475b761f572a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="afcc1-102">Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="afcc1-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="afcc1-103">W języku C# 1.0 lub nowszego oraz delegatów mogą być deklarowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="afcc1-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="afcc1-104">2.0 C# zapewnia prostszy sposób zapisu poprzedniej deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="afcc1-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="afcc1-105">W języku C# 2.0 lub nowszy, jest również możliwe metody anonimowej zadeklarować i zainicjuj [delegować](../../../csharp/language-reference/keywords/delegate.md), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="afcc1-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="afcc1-106">W języku C# 3.0 lub nowszego oraz delegatów również można zadeklarować i utworzone za pomocą wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="afcc1-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="afcc1-107">Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="afcc1-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="afcc1-108">Poniższy przykład przedstawia deklarowanie, tworzenie wystąpień i przy użyciu delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="afcc1-109">`BookDB` Klasa hermetyzuje księgarni bazy danych, który obsługuje bazę danych książek.</span><span class="sxs-lookup"><span data-stu-id="afcc1-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="afcc1-110">Udostępnia ona metodę, `ProcessPaperbackBooks`, która wyszukuje wszystkie paperback książki w bazie danych i wywołuje delegata dla każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="afcc1-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="afcc1-111">`delegate` Nosi nazwę typu, który jest używany `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="afcc1-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="afcc1-112">`Test` Do drukowania tytułów i średniej ceny paperback książek klasa korzysta z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="afcc1-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="afcc1-113">Używanie delegatów zamienia dobre rozdzielanie funkcji między bazą danych księgarni i kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="afcc1-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="afcc1-114">Kod klienta nie ma informacji o przechowywania podręcznikach lub sposób odnajdowania paperback książki w księgarni kodu.</span><span class="sxs-lookup"><span data-stu-id="afcc1-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="afcc1-115">Kod księgarni nie ma informacji o jakie przetwarzanie jest realizowane w podręcznikach paperback, po ich znalezienia.</span><span class="sxs-lookup"><span data-stu-id="afcc1-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afcc1-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="afcc1-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="afcc1-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="afcc1-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="afcc1-118">Deklarowanie delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="afcc1-119">Następująca instrukcja deklaruje nowy typ obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="afcc1-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="afcc1-120">Każdy typ delegata opisuje liczbę i typy argumentów i typ zwracana wartość metody hermetyzacji przez go.</span><span class="sxs-lookup"><span data-stu-id="afcc1-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="afcc1-121">Zawsze, gdy potrzebna jest nowy zestaw typy argumentów lub typ zwracanej wartości, musi być zadeklarowany nowy typ obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="afcc1-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="afcc1-122">Tworzenia wystąpienia delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="afcc1-123">Po został zadeklarowany typ delegowany, obiektu delegowanego należy utworzyć i skojarzone z określonym — metoda.</span><span class="sxs-lookup"><span data-stu-id="afcc1-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="afcc1-124">W poprzednim przykładzie, możesz to zrobić przez przekazanie `PrintTitle` metodę `ProcessPaperbackBooks` metodę jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="afcc1-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="afcc1-125">Spowoduje to utworzenie nowego obiektu delegowanego skojarzone z [statycznych](../../../csharp/language-reference/keywords/static.md) metody `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="afcc1-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="afcc1-126">Podobnie, Metoda niestatyczna `AddBookToTotal` w obiekcie `totaller` jest przekazywany jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="afcc1-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="afcc1-127">W obu przypadkach nowego obiektu delegowanego jest przekazywany do `ProcessPaperbackBooks` metody.</span><span class="sxs-lookup"><span data-stu-id="afcc1-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="afcc1-128">Po utworzeniu delegata metoda nie jest skojarzona z nigdy nie zmiany. Delegat obiekty są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="afcc1-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="afcc1-129">Wywołanie delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="afcc1-130">Po utworzeniu obiektu delegowanego obiektu delegowanego zwykle są przekazywane do innego kodu, który wywoła delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="afcc1-131">Obiektu delegowanego jest wywoływana przy użyciu nazwy obiektu delegowanego, a po niej ujętego w nawiasy argumenty do przekazania do delegata.</span><span class="sxs-lookup"><span data-stu-id="afcc1-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="afcc1-132">Poniżej przedstawiono przykładowy wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="afcc1-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="afcc1-133">Delegat można albo wywołać synchronicznie, jak w poniższym przykładzie lub asynchronicznie za pomocą `BeginInvoke` i `EndInvoke` metody.</span><span class="sxs-lookup"><span data-stu-id="afcc1-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afcc1-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afcc1-134">See Also</span></span>  
 [<span data-ttu-id="afcc1-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="afcc1-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="afcc1-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="afcc1-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="afcc1-137">Delegaci</span><span class="sxs-lookup"><span data-stu-id="afcc1-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
