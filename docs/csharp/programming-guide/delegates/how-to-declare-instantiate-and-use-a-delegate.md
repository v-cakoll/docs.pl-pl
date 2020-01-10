---
title: Jak zadeklarować, utworzyć wystąpienie i korzystać z przewodnika C# dotyczącego programowania delegatów
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712367"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="12bf1-102">Sposób deklarowania, tworzenia wystąpienia i używania delegata (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="12bf1-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="12bf1-103">W C# 1,0 i nowszych można zadeklarować delegatów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12bf1-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="12bf1-104">C#2,0 zapewnia prostszy sposób pisania poprzedniej deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12bf1-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="12bf1-105">W C# 2,0 i nowszych jest również możliwe użycie anonimowej metody do zadeklarowania i zainicjowania [delegata](../../language-reference/builtin-types/reference-types.md), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12bf1-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="12bf1-106">W C# 3,0 i nowszych Delegaty mogą być również deklarowane i tworzone przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12bf1-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="12bf1-107">Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="12bf1-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="12bf1-108">Poniższy przykład ilustruje deklarowanie, Tworzenie wystąpień i Używanie delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="12bf1-109">Klasa `BookDB` hermetyzuje bazę danych księgarni, która obsługuje bazę danych książek.</span><span class="sxs-lookup"><span data-stu-id="12bf1-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="12bf1-110">Udostępnia ona metodę `ProcessPaperbackBooks`, która znajduje wszystkie książki drukowanego podręcznika w bazie danych i wywołuje delegata dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="12bf1-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="12bf1-111">Używany typ `delegate` ma nazwę `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="12bf1-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="12bf1-112">Klasa `Test` używa tej klasy do drukowania tytułów i średniej ceny książek drukowanego podręcznika.</span><span class="sxs-lookup"><span data-stu-id="12bf1-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="12bf1-113">Użycie delegatów promuje dobre rozdzielenie funkcjonalności między bazą danych księgarni i kodem klienta.</span><span class="sxs-lookup"><span data-stu-id="12bf1-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="12bf1-114">Kod klienta nie ma informacji o tym, w jaki sposób są przechowywane książki lub jak kod księgarni znajduje książki drukowanego podręcznika.</span><span class="sxs-lookup"><span data-stu-id="12bf1-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="12bf1-115">Kod księgarni nie ma informacji o tym, jakie przetwarzanie jest wykonywane w książkach drukowanego podręcznika po ich znalezieniu.</span><span class="sxs-lookup"><span data-stu-id="12bf1-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12bf1-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="12bf1-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="12bf1-117">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="12bf1-117">Robust Programming</span></span>  
  
- <span data-ttu-id="12bf1-118">Deklarowanie delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="12bf1-119">Poniższa instrukcja deklaruje nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="12bf1-120">Każdy typ delegata zawiera informacje o liczbie i typach argumentów oraz typ zwracanej wartości metod, które mogą być hermetyzowane.</span><span class="sxs-lookup"><span data-stu-id="12bf1-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="12bf1-121">Zawsze, gdy wymagany jest nowy zestaw typów argumentów lub typ wartości zwracanej, musi zostać zadeklarowany nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="12bf1-122">Utworzenie wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="12bf1-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="12bf1-123">Po zadeklarowaniu typu delegata należy utworzyć obiekt delegata i skojarzyć go z określoną metodą.</span><span class="sxs-lookup"><span data-stu-id="12bf1-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="12bf1-124">W poprzednim przykładzie należy to zrobić, przekazując metodę `PrintTitle` do metody `ProcessPaperbackBooks`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="12bf1-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="12bf1-125">Spowoduje to utworzenie nowego obiektu delegata skojarzonego z metodą [statyczną](../../language-reference/keywords/static.md) `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="12bf1-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="12bf1-126">Podobnie Metoda niestatyczna `AddBookToTotal` na obiekcie `totaller` jest przenoszona jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="12bf1-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="12bf1-127">W obu przypadkach nowy obiekt delegowany jest przesyłany do metody `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="12bf1-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="12bf1-128">Po utworzeniu delegata Metoda jest skojarzona z nigdy zmianami; obiekty delegatów są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="12bf1-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="12bf1-129">Wywoływanie delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="12bf1-130">Po utworzeniu obiektu delegowanego obiekt delegata jest zwykle przenoszona do innego kodu, który wywoła delegata.</span><span class="sxs-lookup"><span data-stu-id="12bf1-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="12bf1-131">Obiekt delegata jest wywoływany przy użyciu nazwy obiektu delegata, a następnie argumentów ujętych w nawiasy, które mają być przekazane do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="12bf1-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="12bf1-132">Poniżej znajduje się przykład wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="12bf1-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="12bf1-133">Delegat może być wywołany synchronicznie, jak w tym przykładzie lub asynchronicznie przy użyciu metod `BeginInvoke` i `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="12bf1-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bf1-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12bf1-134">See also</span></span>

- [<span data-ttu-id="12bf1-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="12bf1-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="12bf1-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="12bf1-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="12bf1-137">Delegaci</span><span class="sxs-lookup"><span data-stu-id="12bf1-137">Delegates</span></span>](./index.md)
