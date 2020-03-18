---
title: Funkcje lokalne - Przewodnik programowania C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170238"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="a7e15-102">Funkcje lokalne (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="a7e15-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="a7e15-103">Począwszy od języka C# 7.0, C# obsługuje *funkcje lokalne*.</span><span class="sxs-lookup"><span data-stu-id="a7e15-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="a7e15-104">Funkcje lokalne są metodami prywatnymi typu, które są zagnieżdżone w innym etece.</span><span class="sxs-lookup"><span data-stu-id="a7e15-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="a7e15-105">Można je wywołać tylko z ich zawierającego członka.</span><span class="sxs-lookup"><span data-stu-id="a7e15-105">They can only be called from their containing member.</span></span> <span data-ttu-id="a7e15-106">Funkcje lokalne mogą być deklarowane i wywoływane z:</span><span class="sxs-lookup"><span data-stu-id="a7e15-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="a7e15-107">Metody, zwłaszcza metody iteratori i metody asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="a7e15-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="a7e15-108">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="a7e15-108">Constructors</span></span>
- <span data-ttu-id="a7e15-109">Akcesory</span><span class="sxs-lookup"><span data-stu-id="a7e15-109">Property accessors</span></span>
- <span data-ttu-id="a7e15-110">Akcesory zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a7e15-110">Event accessors</span></span>
- <span data-ttu-id="a7e15-111">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="a7e15-111">Anonymous methods</span></span>
- <span data-ttu-id="a7e15-112">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="a7e15-112">Lambda expressions</span></span>
- <span data-ttu-id="a7e15-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="a7e15-113">Finalizers</span></span>
- <span data-ttu-id="a7e15-114">Inne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="a7e15-114">Other local functions</span></span>

<span data-ttu-id="a7e15-115">Jednak nie można zadeklarować funkcji lokalnych wewnątrz elementu członkowskiego zabudowanego wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="a7e15-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="a7e15-116">W niektórych przypadkach można użyć wyrażenia lambda do zaimplementowania funkcji również obsługiwane przez funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="a7e15-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="a7e15-117">Aby uzyskać porównanie, zobacz [Funkcje lokalne w porównaniu z wyrażeniami Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="a7e15-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="a7e15-118">Funkcje lokalne sprawiają, że intencja kodu jest wyczyszczona.</span><span class="sxs-lookup"><span data-stu-id="a7e15-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="a7e15-119">Każdy, kto czyta kod, może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej.</span><span class="sxs-lookup"><span data-stu-id="a7e15-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="a7e15-120">W przypadku projektów zespołowych uniemożliwiają one również innemu deweloperowi omyłkowo wywołanie metody bezpośrednio z innego miejsca w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="a7e15-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="a7e15-121">Składnia funkcji lokalnej</span><span class="sxs-lookup"><span data-stu-id="a7e15-121">Local function syntax</span></span>

<span data-ttu-id="a7e15-122">Funkcja lokalna jest zdefiniowana jako zagnieżdżona metoda wewnątrz elementu członkowskiego zawierającego.</span><span class="sxs-lookup"><span data-stu-id="a7e15-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="a7e15-123">Jego definicja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="a7e15-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="a7e15-124">Funkcje lokalne mogą używać [modyfikatorów asynchronicznych](../../language-reference/keywords/async.md) i [niebezpiecznych.](../../language-reference/keywords/unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="a7e15-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

<span data-ttu-id="a7e15-125">Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w dołączanym elementem członkowskim, w tym jego parametry metody, są dostępne w funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="a7e15-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span>

<span data-ttu-id="a7e15-126">W przeciwieństwie do definicji metody definicja funkcji lokalnej nie może zawierać modyfikatora dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a7e15-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="a7e15-127">Ponieważ wszystkie funkcje lokalne są prywatne, w tym `private` modyfikator dostępu, takie jak słowo kluczowe, generuje błąd kompilatora CS0106, "Modyfikator "prywatny" jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="a7e15-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="a7e15-128">Przed c# 8.0 funkcje lokalne `static` nie może zawierać modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a7e15-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="a7e15-129">W `static` tym słowo kluczowe generuje błąd kompilatora CS0106, "Modyfikator "statyczne" jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="a7e15-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="a7e15-130">Ponadto atrybutów nie można zastosować do funkcji lokalnej lub do jej parametrów i parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="a7e15-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span>

<span data-ttu-id="a7e15-131">W poniższym przykładzie zdefiniowano funkcję lokalną o nazwie, `AppendPathSeparator` która jest prywatna dla metody o nazwie: `GetText`</span><span class="sxs-lookup"><span data-stu-id="a7e15-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="a7e15-132">Funkcje lokalne i wyjątki</span><span class="sxs-lookup"><span data-stu-id="a7e15-132">Local functions and exceptions</span></span>

<span data-ttu-id="a7e15-133">Jedną z przydatnych funkcji funkcji lokalnych jest to, że mogą one zezwolić na wyjątki do powierzchni natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a7e15-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="a7e15-134">Dla iteratorów metody wyjątki są wyświetlane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie po pobraniu iteratora.</span><span class="sxs-lookup"><span data-stu-id="a7e15-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="a7e15-135">W przypadku metod asynchronicznej wszelkie wyjątki generowane w metodzie asynchronicznej są obserwowane, gdy oczekuje się zwróconego zadania.</span><span class="sxs-lookup"><span data-stu-id="a7e15-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="a7e15-136">W poniższym `OddSequence` przykładzie zdefiniowano metodę, która wylicza liczby nieparzyste między określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="a7e15-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="a7e15-137">Ponieważ przekazuje liczbę większą niż 100 do metody `OddSequence` wyliczania, metoda zgłasza . <xref:System.ArgumentOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="a7e15-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="a7e15-138">Jak pokazuje dane wyjściowe z przykładu, powierzchnie wyjątków tylko wtedy, gdy iterate liczb, a nie podczas pobierania wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="a7e15-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

<span data-ttu-id="a7e15-139">Zamiast tego można zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iterator, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7e15-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="a7e15-140">Funkcje lokalne mogą służyć w podobny sposób do obsługi wyjątków poza operacją asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="a7e15-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="a7e15-141">Zwykle wyjątki generowane w metodzie asynchronicznej wymagają zbadania wewnętrznych <xref:System.AggregateException>wyjątków .</span><span class="sxs-lookup"><span data-stu-id="a7e15-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="a7e15-142">Funkcje lokalne umożliwiają kod szybko nie powiedzie się i pozwalają na wyjątek być generowane i obserwowane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a7e15-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="a7e15-143">W poniższym przykładzie użyto metody `GetMultipleAsync` asynchronicznej o nazwie, aby wstrzymać na określoną liczbę sekund i zwrócić wartość, która jest losową wielokrotnością tej liczby sekund.</span><span class="sxs-lookup"><span data-stu-id="a7e15-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="a7e15-144">Maksymalne opóźnienie wynosi 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="a7e15-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="a7e15-145">Jak pokazano w poniższym przykładzie, wyjątek, który jest `GetMultipleAsync` generowany, gdy wartość <xref:System.AggregateException> 6 `GetMultipleAsync` jest przekazywana do metody jest opakowany w po rozpoczęciu wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="a7e15-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

<span data-ttu-id="a7e15-146">Tak jak w przypadku iterator metody, możemy refaktoryzacji kodu z tego przykładu, aby wykonać sprawdzanie poprawności przed wywołaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a7e15-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="a7e15-147">Jak pokazuje dane wyjściowe z <xref:System.ArgumentOutOfRangeException> poniższego przykładu, nie jest zawinięte w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="a7e15-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a><span data-ttu-id="a7e15-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7e15-148">See also</span></span>

- [<span data-ttu-id="a7e15-149">Metody</span><span class="sxs-lookup"><span data-stu-id="a7e15-149">Methods</span></span>](methods.md)
