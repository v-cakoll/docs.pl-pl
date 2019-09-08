---
title: Funkcje lokalne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f572f683511fe90951f841c80eae448a9cb6054b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785092"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="b00a2-102">Funkcje lokalne (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="b00a2-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="b00a2-103">Począwszy od C# 7,0, C# obsługuje *funkcje lokalne*.</span><span class="sxs-lookup"><span data-stu-id="b00a2-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="b00a2-104">Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="b00a2-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="b00a2-105">Mogą być wywoływane tylko z ich składowych.</span><span class="sxs-lookup"><span data-stu-id="b00a2-105">They can only be called from their containing member.</span></span> <span data-ttu-id="b00a2-106">Funkcje lokalne można zadeklarować w i wywołać z:</span><span class="sxs-lookup"><span data-stu-id="b00a2-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="b00a2-107">Metody, zwłaszcza metody iteratorów i metody asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b00a2-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="b00a2-108">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="b00a2-108">Constructors</span></span>
- <span data-ttu-id="b00a2-109">Metody dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="b00a2-109">Property accessors</span></span>
- <span data-ttu-id="b00a2-110">Metody dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b00a2-110">Event accessors</span></span>
- <span data-ttu-id="b00a2-111">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="b00a2-111">Anonymous methods</span></span>
- <span data-ttu-id="b00a2-112">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="b00a2-112">Lambda expressions</span></span>
- <span data-ttu-id="b00a2-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="b00a2-113">Finalizers</span></span>
- <span data-ttu-id="b00a2-114">Inne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="b00a2-114">Other local functions</span></span>

<span data-ttu-id="b00a2-115">Jednak funkcji lokalnych nie można deklarować wewnątrz elementu członkowskiego będącego w posiadaniu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b00a2-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="b00a2-116">W niektórych przypadkach można użyć wyrażenia lambda, aby zaimplementować funkcje również obsługiwane przez funkcję lokalną.</span><span class="sxs-lookup"><span data-stu-id="b00a2-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="b00a2-117">Aby zapoznać się z porównaniem, zobacz [funkcje lokalne w porównaniu z wyrażeniami lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="b00a2-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="b00a2-118">Funkcje lokalne sprawiają, że zamiar kodu jest przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="b00a2-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="b00a2-119">Każda osoba odczytująca kod może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b00a2-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="b00a2-120">W przypadku projektów zespołowych uniemożliwiają one również innym deweloperom błędne wywoływanie metody bezpośrednio z innych miejsc w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="b00a2-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="b00a2-121">Składnia funkcji lokalnych</span><span class="sxs-lookup"><span data-stu-id="b00a2-121">Local function syntax</span></span>

<span data-ttu-id="b00a2-122">Funkcja lokalna jest definiowana jako metoda zagnieżdżona wewnątrz składowej zawierającej.</span><span class="sxs-lookup"><span data-stu-id="b00a2-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="b00a2-123">Jego definicja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="b00a2-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="b00a2-124">Funkcje lokalne mogą używać modyfikatorów [Async](../../language-reference/keywords/async.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="b00a2-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="b00a2-125">Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w składowej zawierającej, łącznie z parametrami metody, są dostępne w funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b00a2-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="b00a2-126">W przeciwieństwie do definicji metody lokalnej definicja funkcji nie może zawierać następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="b00a2-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="b00a2-127">Modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="b00a2-127">The member access modifier.</span></span> <span data-ttu-id="b00a2-128">Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatorem dostępu, takim jak `private` słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator" Private "jest nieprawidłowy dla tego elementu".</span><span class="sxs-lookup"><span data-stu-id="b00a2-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="b00a2-129">[Static](../../language-reference/keywords/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b00a2-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="b00a2-130">`static` Włączenie słowa kluczowego generuje błąd kompilatora CS0106, "modyfikator" static "jest nieprawidłowy dla tego elementu".</span><span class="sxs-lookup"><span data-stu-id="b00a2-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="b00a2-131">Ponadto atrybuty nie mogą być stosowane do funkcji lokalnej ani do jej parametrów i parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b00a2-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="b00a2-132">W poniższym przykładzie zdefiniowano funkcję lokalną o `AppendPathSeparator` nazwie, która jest prywatna dla `GetText`metody o nazwie:</span><span class="sxs-lookup"><span data-stu-id="b00a2-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="b00a2-133">Lokalne funkcje i wyjątki</span><span class="sxs-lookup"><span data-stu-id="b00a2-133">Local functions and exceptions</span></span>

<span data-ttu-id="b00a2-134">Jedną z użytecznych funkcji lokalnych funkcji jest możliwość natychmiastowego zezwolenia na korzystanie z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b00a2-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="b00a2-135">W przypadku iteratorów metod wyjątki są nakierowane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie podczas pobierania iteratora.</span><span class="sxs-lookup"><span data-stu-id="b00a2-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="b00a2-136">W przypadku metod asynchronicznych wszystkie wyjątki zgłoszone w metodzie asynchronicznej są zaobserwowane, gdy zwracane zadanie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="b00a2-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="b00a2-137">W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza liczby nieparzyste między określonym zakresem.</span><span class="sxs-lookup"><span data-stu-id="b00a2-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="b00a2-138">Ponieważ przekazuje liczbę większą niż 100 do `OddSequence` metody Enumerator, Metoda <xref:System.ArgumentOutOfRangeException>zgłasza.</span><span class="sxs-lookup"><span data-stu-id="b00a2-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="b00a2-139">Ponieważ dane wyjściowe z przykładu pokazują, powierzchnie wyjątków tylko w przypadku iteracji liczby, a nie podczas pobierania modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b00a2-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="b00a2-140">Zamiast tego można zgłosić wyjątek podczas sprawdzania poprawności i przed pobraniem iteratora, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b00a2-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="b00a2-141">Funkcji lokalnych można używać w podobny sposób, aby obsługiwać wyjątki poza operacją asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="b00a2-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="b00a2-142">Zwykle wyjątki zgłoszone w metodzie asynchronicznej wymagają sprawdzenia wyjątków <xref:System.AggregateException>wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b00a2-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="b00a2-143">Funkcje lokalne umożliwiają szybkie i niepowodzenie wykonywania kodu oraz umożliwiają synchroniczną i zaobserwowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b00a2-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="b00a2-144">W poniższym przykładzie zastosowano metodę asynchroniczną `GetMultipleAsync` o nazwie do pauzy przez określoną liczbę sekund i zwracają wartość, która jest losowo wielokrotnością tej liczby sekund.</span><span class="sxs-lookup"><span data-stu-id="b00a2-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="b00a2-145">Maksymalne opóźnienie wynosi 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="b00a2-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="b00a2-146">Jak pokazano na poniższym przykładzie, wyjątek, który jest generowany, gdy wartość 6 jest przekazana do `GetMultipleAsync` metody jest opakowany <xref:System.AggregateException> w po `GetMultipleAsync` rozpoczęciu wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="b00a2-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="b00a2-147">Podobnie jak w iteratorze metody, możemy resłużyć kod z tego przykładu, aby przeprowadzić walidację przed wywołaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="b00a2-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="b00a2-148">Jak pokazano na poniższym przykładzie, <xref:System.ArgumentOutOfRangeException> nie jest opakowany <xref:System.AggregateException>w.</span><span class="sxs-lookup"><span data-stu-id="b00a2-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="b00a2-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b00a2-149">See also</span></span>

- [<span data-ttu-id="b00a2-150">Metody</span><span class="sxs-lookup"><span data-stu-id="b00a2-150">Methods</span></span>](methods.md)
