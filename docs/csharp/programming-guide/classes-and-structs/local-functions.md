---
title: Funkcje lokalne — C# Przewodnik programowania
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 2036e576a44aa3e1e7829e2091e5a9243d6b6010
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705525"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="b7931-102">Funkcje lokalne (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="b7931-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="b7931-103">Począwszy od C# 7,0, C# obsługuje *funkcje lokalne*.</span><span class="sxs-lookup"><span data-stu-id="b7931-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="b7931-104">Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="b7931-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="b7931-105">Mogą być wywoływane tylko z ich składowych.</span><span class="sxs-lookup"><span data-stu-id="b7931-105">They can only be called from their containing member.</span></span> <span data-ttu-id="b7931-106">Funkcje lokalne można zadeklarować w i wywołać z:</span><span class="sxs-lookup"><span data-stu-id="b7931-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="b7931-107">Metody, zwłaszcza metody iteratorów i metody asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b7931-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="b7931-108">Konstruktorzy</span><span class="sxs-lookup"><span data-stu-id="b7931-108">Constructors</span></span>
- <span data-ttu-id="b7931-109">Metody dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="b7931-109">Property accessors</span></span>
- <span data-ttu-id="b7931-110">Metody dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b7931-110">Event accessors</span></span>
- <span data-ttu-id="b7931-111">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="b7931-111">Anonymous methods</span></span>
- <span data-ttu-id="b7931-112">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="b7931-112">Lambda expressions</span></span>
- <span data-ttu-id="b7931-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="b7931-113">Finalizers</span></span>
- <span data-ttu-id="b7931-114">Inne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="b7931-114">Other local functions</span></span>

<span data-ttu-id="b7931-115">Jednak funkcji lokalnych nie można deklarować wewnątrz elementu członkowskiego będącego w posiadaniu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b7931-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="b7931-116">W niektórych przypadkach można użyć wyrażenia lambda, aby zaimplementować funkcje również obsługiwane przez funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="b7931-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="b7931-117">Aby zapoznać się z porównaniem, zobacz [funkcje lokalne w porównaniu z wyrażeniami lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="b7931-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="b7931-118">Funkcje lokalne sprawiają, że zamiar kodu jest przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="b7931-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="b7931-119">Każda osoba odczytująca kod może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b7931-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="b7931-120">W przypadku projektów zespołowych uniemożliwiają one również innym deweloperom błędne wywoływanie metody bezpośrednio z innych miejsc w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="b7931-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="b7931-121">Składnia funkcji lokalnych</span><span class="sxs-lookup"><span data-stu-id="b7931-121">Local function syntax</span></span>

<span data-ttu-id="b7931-122">Funkcja lokalna jest definiowana jako metoda zagnieżdżona wewnątrz składowej zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b7931-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="b7931-123">Jego definicja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="b7931-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="b7931-124">Funkcje lokalne mogą używać modyfikatorów [Async](../../language-reference/keywords/async.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="b7931-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="b7931-125">Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w składowej zawierającej, łącznie z parametrami metody, są dostępne w funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b7931-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="b7931-126">W przeciwieństwie do definicji metody lokalnej definicja funkcji nie może zawierać modyfikatora dostępu do składowej.</span><span class="sxs-lookup"><span data-stu-id="b7931-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="b7931-127">Ponieważ wszystkie funkcje lokalne są prywatne, w tym modyfikator dostępu, taki jak `private` słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator" Private "jest nieprawidłowy dla tego elementu".</span><span class="sxs-lookup"><span data-stu-id="b7931-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="b7931-128">Przed C# 8,0 funkcja lokalna nie może zawierać modyfikatora `static`.</span><span class="sxs-lookup"><span data-stu-id="b7931-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="b7931-129">W tym `static` słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator" static "jest nieprawidłowy dla tego elementu".</span><span class="sxs-lookup"><span data-stu-id="b7931-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="b7931-130">Ponadto atrybuty nie mogą być stosowane do funkcji lokalnej ani do jej parametrów i parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b7931-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="b7931-131">W poniższym przykładzie zdefiniowano funkcję lokalną o nazwie `AppendPathSeparator`, która jest prywatna dla metody o nazwie `GetText`:</span><span class="sxs-lookup"><span data-stu-id="b7931-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="b7931-132">Lokalne funkcje i wyjątki</span><span class="sxs-lookup"><span data-stu-id="b7931-132">Local functions and exceptions</span></span>

<span data-ttu-id="b7931-133">Jedną z użytecznych funkcji lokalnych funkcji jest możliwość natychmiastowego zezwolenia na korzystanie z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b7931-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="b7931-134">W przypadku iteratorów metod wyjątki są nakierowane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie podczas pobierania iteratora.</span><span class="sxs-lookup"><span data-stu-id="b7931-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="b7931-135">W przypadku metod asynchronicznych wszystkie wyjątki zgłoszone w metodzie asynchronicznej są zaobserwowane, gdy zwracane zadanie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="b7931-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="b7931-136">W poniższym przykładzie zdefiniowano metodę `OddSequence`, która wylicza nieparzyste liczby między określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="b7931-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="b7931-137">Ponieważ przekazuje liczbę większą niż 100 do metody modułu wyliczającego `OddSequence` Metoda generuje <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="b7931-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="b7931-138">Ponieważ dane wyjściowe z przykładu pokazują, powierzchnie wyjątków tylko w przypadku iteracji liczby, a nie podczas pobierania modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b7931-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="b7931-139">Zamiast tego można zgłosić wyjątek podczas sprawdzania poprawności i przed pobraniem iteratora, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7931-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="b7931-140">Funkcji lokalnych można używać w podobny sposób, aby obsługiwać wyjątki poza operacją asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="b7931-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="b7931-141">Zwykle wyjątki zgłoszone w metodzie asynchronicznej wymagają sprawdzenia wewnętrznych wyjątków <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="b7931-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="b7931-142">Funkcje lokalne umożliwiają szybkie i niepowodzenie wykonywania kodu oraz umożliwiają synchroniczną i zaobserwowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b7931-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="b7931-143">Poniższy przykład używa metody asynchronicznej o nazwie `GetMultipleAsync`, aby wstrzymywać przez określoną liczbę sekund i zwracać wartość, która jest losowo wielokrotnością tej liczby sekund.</span><span class="sxs-lookup"><span data-stu-id="b7931-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="b7931-144">Maksymalne opóźnienie wynosi 5 sekund; wyniki <xref:System.ArgumentOutOfRangeException>, jeśli wartość jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="b7931-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="b7931-145">Jak pokazano na poniższym przykładzie, wyjątek, który jest generowany, gdy wartość 6 jest przekazana do metody `GetMultipleAsync` jest opakowany w <xref:System.AggregateException> po rozpoczęciu wykonywania metody `GetMultipleAsync`.</span><span class="sxs-lookup"><span data-stu-id="b7931-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="b7931-146">Podobnie jak w iteratorze metody, możemy resłużyć kod z tego przykładu, aby przeprowadzić walidację przed wywołaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="b7931-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="b7931-147">Jak pokazano na poniższym przykładzie, <xref:System.ArgumentOutOfRangeException> nie jest opakowany w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="b7931-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="b7931-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7931-148">See also</span></span>

- [<span data-ttu-id="b7931-149">Metody</span><span class="sxs-lookup"><span data-stu-id="b7931-149">Methods</span></span>](methods.md)
