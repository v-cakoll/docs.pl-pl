---
title: Funkcje lokalne - C# Programming Guide
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e91069c25ebe6c2a22927391734e5030a908e4ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663930"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="08bc7-102">Funkcje lokalne (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="08bc7-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="08bc7-103">Począwszy od C# 7.0, C# obsługuje *funkcje lokalne*.</span><span class="sxs-lookup"><span data-stu-id="08bc7-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="08bc7-104">Funkcje lokalne są metody prywatne typu, które są osadzone w innym elemencie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="08bc7-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="08bc7-105">One może być wywołana tylko z ich nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="08bc7-105">They can only be called from their containing member.</span></span> <span data-ttu-id="08bc7-106">Funkcje lokalne może być zadeklarowana w i wywoływane z:</span><span class="sxs-lookup"><span data-stu-id="08bc7-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="08bc7-107">Metody, szczególnie metody iteratorów i metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="08bc7-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="08bc7-108">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="08bc7-108">Constructors</span></span>
- <span data-ttu-id="08bc7-109">Metod dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="08bc7-109">Property accessors</span></span>
- <span data-ttu-id="08bc7-110">Metod dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="08bc7-110">Event accessors</span></span>
- <span data-ttu-id="08bc7-111">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="08bc7-111">Anonymous methods</span></span>
- <span data-ttu-id="08bc7-112">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="08bc7-112">Lambda expressions</span></span>
- <span data-ttu-id="08bc7-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="08bc7-113">Finalizers</span></span>
- <span data-ttu-id="08bc7-114">Inne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="08bc7-114">Other local functions</span></span>

<span data-ttu-id="08bc7-115">Jednak funkcje lokalne nie można deklarować wewnątrz elementu członkowskiego z wyrażeniem w treści.</span><span class="sxs-lookup"><span data-stu-id="08bc7-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="08bc7-116">W niektórych przypadkach można użyć wyrażenia lambda do implementacji funkcji również są obsługiwane przez funkcję lokalnego.</span><span class="sxs-lookup"><span data-stu-id="08bc7-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="08bc7-117">Dla porównania, zobacz [funkcje lokalne w porównaniu do wyrażenia Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="08bc7-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="08bc7-118">Funkcje lokalne upewnij celem zwykłego kodu.</span><span class="sxs-lookup"><span data-stu-id="08bc7-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="08bc7-119">Kto czyta kodu możesz zobaczyć, że metoda nie jest wywoływane z wyjątkiem przez zawierającego metodę.</span><span class="sxs-lookup"><span data-stu-id="08bc7-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="08bc7-120">W przypadku projektów zespołowych, one również spowodować, że inny deweloper może je przez pomyłkę wywołać metodę bezpośrednio z innego miejsca w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="08bc7-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="08bc7-121">Składnia funkcji lokalnej</span><span class="sxs-lookup"><span data-stu-id="08bc7-121">Local function syntax</span></span>

<span data-ttu-id="08bc7-122">Funkcja lokalna jest zdefiniowany jako metodę zagnieżdżone wewnątrz nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="08bc7-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="08bc7-123">Jego definicja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="08bc7-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="08bc7-124">Można użyć funkcji lokalnych [async](../../language-reference/keywords/async.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="08bc7-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="08bc7-125">Należy pamiętać, że wszystkie zmienne lokalne, które są zdefiniowane w nadrzędnego elementu członkowskiego, łącznie z jego parametrów metody są dostępne w funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="08bc7-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="08bc7-126">W przeciwieństwie do definicji metody definicja funkcji lokalnej nie może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="08bc7-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="08bc7-127">Modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="08bc7-127">The member access modifier.</span></span> <span data-ttu-id="08bc7-128">Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatora dostępu, takich jak `private` — słowo kluczowe, generuje błąd kompilatora CS0106, "modyfikator"private"jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="08bc7-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="08bc7-129">[Statyczne](../../language-reference/keywords/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="08bc7-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="08bc7-130">W tym `static` — słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator"static"jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="08bc7-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="08bc7-131">Ponadto atrybuty nie można zastosować do funkcji lokalnej lub jego parametry i parametry typu.</span><span class="sxs-lookup"><span data-stu-id="08bc7-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="08bc7-132">W poniższym przykładzie zdefiniowano funkcji lokalnej o nazwie `AppendPathSeparator` jest oznaczony jako prywatny metodę o nazwie `GetText`:</span><span class="sxs-lookup"><span data-stu-id="08bc7-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="08bc7-133">Funkcje lokalne i wyjątki</span><span class="sxs-lookup"><span data-stu-id="08bc7-133">Local functions and exceptions</span></span>

<span data-ttu-id="08bc7-134">Jest jednym z przydatnych funkcji funkcje lokalne, czy ich zezwalają na wyjątki, aby od razu powierzchni.</span><span class="sxs-lookup"><span data-stu-id="08bc7-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="08bc7-135">Dla metody iteratorów wyjątki są udostępniane tylko wtedy, gdy są wyliczane zwracanej sekwencji, a nie w przypadku, gdy są pobierane iteratora.</span><span class="sxs-lookup"><span data-stu-id="08bc7-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="08bc7-136">Do metod asynchronicznych wyjątki zgłaszane w metodzie asynchronicznej są przestrzegane, gdy zwracane zadanie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="08bc7-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="08bc7-137">W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza nieparzystej liczby z zakresu od określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="08bc7-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="08bc7-138">Ponieważ przekazuje liczbę większą niż 100 do `OddSequence` metody modułu wyliczającego, metoda zgłasza <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="08bc7-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="08bc7-139">Dane wyjściowe z przykładu pokazują, wyjątek wydobywa informacje dotyczące tylko wtedy, gdy iteracji numery, a nie w przypadku, gdy pobieranie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="08bc7-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="08bc7-140">Zamiast tego może zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iteratora, zwracając iteratora, z funkcją lokalną, w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="08bc7-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="08bc7-141">Funkcje lokalne może służyć w podobny sposób, aby obsłużyć wyjątki poza operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="08bc7-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="08bc7-142">Zazwyczaj wyjątki zgłaszane w metodzie asynchronicznej wymagają badania wewnętrznych wyjątków z <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="08bc7-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="08bc7-143">Funkcje lokalne zezwalają na kodzie w celu szybkiego kończenia działania i Zezwalaj na wyjątek zarówno wygenerowany i zaobserwowanie synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="08bc7-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="08bc7-144">W poniższym przykładzie użyto metody asynchronicznej o nazwie `GetMultipleAsync` wstrzymać określoną liczbę sekund i zwracają wartość, która jest wielokrotnością losowe tę liczbę sekund.</span><span class="sxs-lookup"><span data-stu-id="08bc7-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="08bc7-145">Maksymalne opóźnienie to 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="08bc7-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="08bc7-146">Jak pokazano na poniższym przykładzie, wyjątek, który jest zgłaszany, gdy wartość 6 jest przekazywany do `GetMultipleAsync` metody jest opakowana w <xref:System.AggregateException> po `GetMultipleAsync` metoda rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="08bc7-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="08bc7-147">Ile My mieliśmy z metody iteratora, możemy refaktoryzować kod z tego przykładu w celu sprawdzenia poprawności przed wywołaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="08bc7-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="08bc7-148">Jako dane wyjściowe w poniższym przykładzie przedstawiono <xref:System.ArgumentOutOfRangeException> nie jest ujęty w <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="08bc7-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="08bc7-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08bc7-149">See also</span></span>

- [<span data-ttu-id="08bc7-150">Metody</span><span class="sxs-lookup"><span data-stu-id="08bc7-150">Methods</span></span>](methods.md)
