---
title: Funkcje lokalne (C# przewodnik programowania w języku)
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac18aa57f443f28f55779ff9c92a5349b9b39fd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="10cf8-102">Funkcje lokalne (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="10cf8-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="10cf8-103">Począwszy od C# 7.0, C# obsługuje *funkcje lokalne*.</span><span class="sxs-lookup"><span data-stu-id="10cf8-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="10cf8-104">Funkcje lokalne są prywatnych metod typu, które są zagnieżdżone w innym elemencie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="10cf8-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="10cf8-105">Mogą one można wywołać tylko z ich zawierającego element członkowski.</span><span class="sxs-lookup"><span data-stu-id="10cf8-105">They can only be called from their containing member.</span></span> <span data-ttu-id="10cf8-106">Funkcje lokalne może być zadeklarowana w i wywoływać z:</span><span class="sxs-lookup"><span data-stu-id="10cf8-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="10cf8-107">Metody szczególnie metody iteracyjne i metod asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="10cf8-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="10cf8-108">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="10cf8-108">Constructors</span></span>
- <span data-ttu-id="10cf8-109">Metod dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="10cf8-109">Property accessors</span></span>
- <span data-ttu-id="10cf8-110">Metod dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="10cf8-110">Event accessors</span></span>
- <span data-ttu-id="10cf8-111">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="10cf8-111">Anonymous methods</span></span>
- <span data-ttu-id="10cf8-112">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="10cf8-112">Lambda expressions</span></span>
- <span data-ttu-id="10cf8-113">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="10cf8-113">Finalizers</span></span>
- <span data-ttu-id="10cf8-114">Inne funkcje lokalne</span><span class="sxs-lookup"><span data-stu-id="10cf8-114">Other local functions</span></span>

<span data-ttu-id="10cf8-115">Jednak funkcje lokalne nie może być deklarowane w zabudowanych wyrażenie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="10cf8-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="10cf8-116">W niektórych przypadkach wyrażenia lambda służy do implementowania również obsługiwane przez funkcję lokalnego.</span><span class="sxs-lookup"><span data-stu-id="10cf8-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="10cf8-117">Porównanie, zobacz [funkcje lokalne w porównaniu do wyrażenia Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="10cf8-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="10cf8-118">Funkcje lokalne należy celem wyczyść kodu.</span><span class="sxs-lookup"><span data-stu-id="10cf8-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="10cf8-119">Odczytywanie programowanie można stwierdzić, że każdy użytkownik metoda nie jest można wywołać z wyjątkiem przez metodę zawierającego.</span><span class="sxs-lookup"><span data-stu-id="10cf8-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="10cf8-120">Dla projektów zespołowych one również uniemożliwić innym deweloperowi przez pomyłkę Wywołaj metodę bezpośrednio w innym miejscu w klasie lub stuct.</span><span class="sxs-lookup"><span data-stu-id="10cf8-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or stuct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="10cf8-121">Składnia funkcji lokalnej</span><span class="sxs-lookup"><span data-stu-id="10cf8-121">Local function syntax</span></span>

<span data-ttu-id="10cf8-122">Funkcja lokalna jest zdefiniowany jako metodę zagnieżdżone wewnątrz zawierającego element członkowski.</span><span class="sxs-lookup"><span data-stu-id="10cf8-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="10cf8-123">Jego definicja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="10cf8-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="10cf8-124">Można użyć funkcji lokalnej [async](../../language-reference/keywords/async.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="10cf8-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="10cf8-125">Należy pamiętać, że wszystkie zmienne lokalne, zdefiniowane w zawierającym elementu członkowskiego, w tym jego parametrów metody są dostępne w funkcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="10cf8-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="10cf8-126">W odróżnieniu od definicję metody definicji funkcji lokalnego nie może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="10cf8-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="10cf8-127">Modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="10cf8-127">The member access modifier.</span></span> <span data-ttu-id="10cf8-128">Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatora dostępu, takich jak `private` — słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator"private"jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="10cf8-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="10cf8-129">[Statycznych](../../language-reference/keywords/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="10cf8-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="10cf8-130">W tym `static` — słowo kluczowe generuje błąd kompilatora CS0106, "modyfikator"static"jest nieprawidłowy dla tego elementu."</span><span class="sxs-lookup"><span data-stu-id="10cf8-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="10cf8-131">Ponadto atrybuty nie można zastosować do funkcji lokalnej lub jego parametrów i parametry typu.</span><span class="sxs-lookup"><span data-stu-id="10cf8-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="10cf8-132">W poniższym przykładzie zdefiniowano lokalnym funkcji o nazwie `AppendPathSeparator` jest oznaczony jako prywatny metodę o nazwie `GetText`:</span><span class="sxs-lookup"><span data-stu-id="10cf8-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="10cf8-133">Funkcje lokalne i wyjątków</span><span class="sxs-lookup"><span data-stu-id="10cf8-133">Local functions and exceptions</span></span>

<span data-ttu-id="10cf8-134">Jednym z przydatnych funkcji funkcje lokalne jest czy umożliwiają one wyjątki, aby natychmiast powierzchni.</span><span class="sxs-lookup"><span data-stu-id="10cf8-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="10cf8-135">Dla metody Iteratory wyjątki są udostępniane tylko wtedy, gdy zwrócony sekwencji jest wyliczone i nie w przypadku, gdy są pobierane iteratora.</span><span class="sxs-lookup"><span data-stu-id="10cf8-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="10cf8-136">Dla metody asynchroniczne wszelkie wyjątki zgłaszane w metodzie asynchronicznej są przestrzegane, gdy zadanie zwracane jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="10cf8-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="10cf8-137">W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza nieparzystej liczby z zakresu określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="10cf8-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="10cf8-138">Ponieważ przekazaniem liczbą większą od 100 do `OddSequence` metoda modułu wyliczającego, metoda zgłasza <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="10cf8-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="10cf8-139">Jak pokazano na dane wyjściowe z przykładu, wyjątek powierzchni tylko wtedy, gdy iteracyjne numery, a nie w przypadku, gdy pobieranie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="10cf8-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="10cf8-140">Zamiast tego można zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iteratora zwracając iteratora z funkcji lokalnej, jak w poniższym przykładzie przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="10cf8-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="10cf8-141">Funkcje lokalne można w sposób podobny do obsługi wyjątków poza operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="10cf8-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="10cf8-142">Zwykle wyjątki zgłaszane w metodzie asynchronicznej wymagają, że należy zbadać wyjątków wewnętrznych z <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="10cf8-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="10cf8-143">Zezwalaj na funkcje lokalne swój kod, aby szybko zakończyć się niepowodzeniem i umożliwić wyjątku zarówno zgłoszony i obserwowanych synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="10cf8-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="10cf8-144">W poniższym przykładzie użyto metody asynchronicznej o nazwie `GetMultipleAsync` wstrzymać określoną liczbę sekund i zwracać wartość, która jest wielokrotnością losowe podanej liczby sekund.</span><span class="sxs-lookup"><span data-stu-id="10cf8-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="10cf8-145">Maksymalne opóźnienie to 5 sekund; <xref:System.ArgumentOutOfRangeException> wyniki, jeśli wartość jest większa niż 5.</span><span class="sxs-lookup"><span data-stu-id="10cf8-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="10cf8-146">Jak pokazano na poniższym przykładzie, wyjątek zgłaszany, gdy wartość 6 jest przekazywana do `GetMultipleAsync` metody jest ujęte w <xref:System.AggregateException> po `GetMultipleAsync` metody rozpoczyna się wykonanie.</span><span class="sxs-lookup"><span data-stu-id="10cf8-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="10cf8-147">Jak robiliśmy z metody iteracyjne, firma Microsoft zrefaktoryzuj kod w tym przykładzie do sprawdzania poprawności przed wywołaniem metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="10cf8-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="10cf8-148">Jako dane wyjściowe w poniższym przykładzie przedstawiono <xref:System.ArgumentOutOfRangeException> nie jest ujęte w < x:System.AggregateException >.</span><span class="sxs-lookup"><span data-stu-id="10cf8-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <x:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="10cf8-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10cf8-149">See also</span></span>
[<span data-ttu-id="10cf8-150">Metody</span><span class="sxs-lookup"><span data-stu-id="10cf8-150">Methods</span></span>](methods.md)
