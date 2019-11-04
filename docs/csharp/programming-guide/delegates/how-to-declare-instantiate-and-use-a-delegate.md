---
title: 'Instrukcje: deklarowanie, tworzenie wystąpienia i używanie przewodnika po C# programowaniu delegata'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: bd3d80023f6cb382f057e976dba01daf5e28db50
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423319"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="a1a08-102">Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a1a08-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="a1a08-103">W C# 1,0 i nowszych można zadeklarować delegatów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a1a08-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="a1a08-104">C#2,0 zapewnia prostszy sposób pisania poprzedniej deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a1a08-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="a1a08-105">W C# 2,0 i nowszych jest również możliwe użycie anonimowej metody do zadeklarowania i zainicjowania [delegata](../../language-reference/builtin-types/reference-types.md), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a1a08-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="a1a08-106">W C# 3,0 i nowszych Delegaty mogą być również deklarowane i tworzone przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a1a08-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="a1a08-107">Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a1a08-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a1a08-108">Poniższy przykład ilustruje deklarowanie, Tworzenie wystąpień i Używanie delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="a1a08-109">Klasa `BookDB` hermetyzuje bazę danych księgarni, która obsługuje bazę danych książek.</span><span class="sxs-lookup"><span data-stu-id="a1a08-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="a1a08-110">Udostępnia ona metodę `ProcessPaperbackBooks`, która znajduje wszystkie książki drukowanego podręcznika w bazie danych i wywołuje delegata dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="a1a08-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="a1a08-111">Używany typ `delegate` ma nazwę `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="a1a08-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="a1a08-112">Klasa `Test` używa tej klasy do drukowania tytułów i średniej ceny książek drukowanego podręcznika.</span><span class="sxs-lookup"><span data-stu-id="a1a08-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="a1a08-113">Użycie delegatów promuje dobre rozdzielenie funkcjonalności między bazą danych księgarni i kodem klienta.</span><span class="sxs-lookup"><span data-stu-id="a1a08-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="a1a08-114">Kod klienta nie ma informacji o tym, w jaki sposób są przechowywane książki lub jak kod księgarni znajduje książki drukowanego podręcznika.</span><span class="sxs-lookup"><span data-stu-id="a1a08-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="a1a08-115">Kod księgarni nie ma informacji o tym, jakie przetwarzanie jest wykonywane w książkach drukowanego podręcznika po ich znalezieniu.</span><span class="sxs-lookup"><span data-stu-id="a1a08-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1a08-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a08-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a1a08-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a1a08-117">Robust Programming</span></span>  
  
- <span data-ttu-id="a1a08-118">Deklarowanie delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="a1a08-119">Poniższa instrukcja deklaruje nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="a1a08-120">Każdy typ delegata zawiera informacje o liczbie i typach argumentów oraz typ zwracanej wartości metod, które mogą być hermetyzowane.</span><span class="sxs-lookup"><span data-stu-id="a1a08-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="a1a08-121">Zawsze, gdy wymagany jest nowy zestaw typów argumentów lub typ wartości zwracanej, musi zostać zadeklarowany nowy typ delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="a1a08-122">Utworzenie wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="a1a08-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="a1a08-123">Po zadeklarowaniu typu delegata należy utworzyć obiekt delegata i skojarzyć go z określoną metodą.</span><span class="sxs-lookup"><span data-stu-id="a1a08-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="a1a08-124">W poprzednim przykładzie należy to zrobić, przekazując metodę `PrintTitle` do metody `ProcessPaperbackBooks`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a1a08-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="a1a08-125">Spowoduje to utworzenie nowego obiektu delegata skojarzonego z metodą [statyczną](../../language-reference/keywords/static.md) `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="a1a08-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="a1a08-126">Podobnie Metoda niestatyczna `AddBookToTotal` na obiekcie `totaller` jest przenoszona jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a1a08-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="a1a08-127">W obu przypadkach nowy obiekt delegowany jest przesyłany do metody `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="a1a08-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="a1a08-128">Po utworzeniu delegata Metoda jest skojarzona z nigdy zmianami; obiekty delegatów są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="a1a08-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="a1a08-129">Wywoływanie delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="a1a08-130">Po utworzeniu obiektu delegowanego obiekt delegata jest zwykle przenoszona do innego kodu, który wywoła delegata.</span><span class="sxs-lookup"><span data-stu-id="a1a08-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="a1a08-131">Obiekt delegata jest wywoływany przy użyciu nazwy obiektu delegata, a następnie argumentów ujętych w nawiasy, które mają być przekazane do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="a1a08-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="a1a08-132">Poniżej znajduje się przykład wywołania delegata:</span><span class="sxs-lookup"><span data-stu-id="a1a08-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="a1a08-133">Delegat może być wywołany synchronicznie, jak w tym przykładzie lub asynchronicznie przy użyciu metod `BeginInvoke` i `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="a1a08-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a08-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a08-134">See also</span></span>

- [<span data-ttu-id="a1a08-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1a08-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a1a08-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a1a08-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="a1a08-137">Delegaci</span><span class="sxs-lookup"><span data-stu-id="a1a08-137">Delegates</span></span>](./index.md)
