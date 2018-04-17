---
title: Wartości zwracane ref i ref zmienne lokalne (Przewodnik C#)
description: Dowiedz się, jak zdefiniować i użyć zwracane ref i wartości lokalnej ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 57fa8f52320b30a1cb228b41e3f5e6655c235561
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="1c500-103">Zwraca ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="1c500-103">Ref returns and ref locals</span></span>

<span data-ttu-id="1c500-104">Począwszy od C# 7, C# obsługuje zwracanych wartości odwołanie (ref zwraca).</span><span class="sxs-lookup"><span data-stu-id="1c500-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="1c500-105">Odwołanie zwracać wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="1c500-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="1c500-106">Obiekt wywołujący możliwość traktować zwrócony zmiennej tak, jakby zwrócono według wartości lub według odwołania.</span><span class="sxs-lookup"><span data-stu-id="1c500-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="1c500-107">Obiekt wywołujący może utworzyć nową zmienną, która jest elementem odwołania do zwrócona wartość ref o nazwie lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1c500-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="1c500-108">Co to jest wartością zwracaną odwołania?</span><span class="sxs-lookup"><span data-stu-id="1c500-108">What is a reference return value?</span></span>

<span data-ttu-id="1c500-109">Deweloperzy większość zapoznali się z przekazywaniem argumentu metody wywołane *przez odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="1c500-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="1c500-110">Lista argumentów wywołaną metodę zawiera zmienną przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1c500-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="1c500-111">Wszelkie zmiany wprowadzone przez metodę o nazwie jej wartość są przestrzegane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="1c500-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="1c500-112">A *odwołania do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub alias) do niektórych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c500-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="1c500-113">Zakres zmiennej musi zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="1c500-113">That variable's scope must include the method.</span></span> <span data-ttu-id="1c500-114">Okres istnienia tej zmiennej musi wykraczać poza zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="1c500-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="1c500-115">Do wartości zwracanej przez metodę przez obiekt wywołujący się zmiany do zmiennej, który jest zwracany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1c500-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="1c500-116">Deklarowanie metody zwracające *odwołania zwracana wartość* wskazuje, że ta metoda zwraca alias do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c500-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="1c500-117">Celem projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do jej modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="1c500-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="1c500-118">Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.</span><span class="sxs-lookup"><span data-stu-id="1c500-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="1c500-119">Istnieją pewne ograniczenia na wyrażenie, które może zwracać metoda jako wartości zwracane odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1c500-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="1c500-120">Ograniczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="1c500-120">Restrictions include:</span></span>

- <span data-ttu-id="1c500-121">Zwracana wartość musi mieć okresu istnienia, która wykracza poza wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="1c500-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="1c500-122">Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go.</span><span class="sxs-lookup"><span data-stu-id="1c500-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="1c500-123">Można instancji lub pola statycznego w klasie lub może być argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="1c500-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="1c500-124">Próby zwracać zmiennej lokalnej generuje błąd kompilatora CS8168, "nie może zwracać lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."</span><span class="sxs-lookup"><span data-stu-id="1c500-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="1c500-125">Wartość zwrotna nie może być literał `null`.</span><span class="sxs-lookup"><span data-stu-id="1c500-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="1c500-126">Zwracanie `null` generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="1c500-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="1c500-127">Metody z ref zwracany alias można było powrócić do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typ dopuszczający wartość null](../nullable-types/index.md) dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="1c500-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="1c500-128">Wartość zwrotna nie może być stałą, elementu członkowskiego wyliczenia, wartość zwracana przez wartości z właściwości lub metody `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="1c500-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="1c500-129">Naruszenie ta zasada generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="1c500-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="1c500-130">Ponadto odwołanie zwracać wartości nie są dozwolone w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="1c500-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="1c500-131">Zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany, mogą zwracać metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="1c500-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="1c500-132">Definiowanie wartości zwracanej ref</span><span class="sxs-lookup"><span data-stu-id="1c500-132">Defining a ref return value</span></span>

<span data-ttu-id="1c500-133">Zdefiniuj ref wartości zwracanej przez dodanie [ref](../../language-reference/keywords/ref.md) — słowo kluczowe na zwracany typ sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="1c500-133">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="1c500-134">Na przykład następująca sygnatura wskazuje, że `GetContactInformation` właściwość zwraca odwołanie do `Person` obiektu do obiektu wywołującego:</span><span class="sxs-lookup"><span data-stu-id="1c500-134">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="1c500-135">Ponadto nazwa obiektu zwracaną przez każdy [zwracać](../../language-reference/keywords/return.md) instrukcji w treści metody musi być poprzedzona [ref](../../language-reference/keywords/ref.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1c500-135">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="1c500-136">Na przykład następująca `return` instrukcja zwraca odwołanie do `Person` obiektu o nazwie `p`:</span><span class="sxs-lookup"><span data-stu-id="1c500-136">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="1c500-137">Korzystanie z wartością zwracaną ref</span><span class="sxs-lookup"><span data-stu-id="1c500-137">Consuming a ref return value</span></span>

<span data-ttu-id="1c500-138">Ref zwracać wartość jest alias do innej zmiennej w zakresie wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="1c500-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="1c500-139">Można odnaleźć żadnego użycie ref zwracany jako przy użyciu zmiennej go aliasy:</span><span class="sxs-lookup"><span data-stu-id="1c500-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="1c500-140">Po przypisaniu jej wartość są przypisywanie wartości do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="1c500-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="1c500-141">Podczas czytania wartość odczytywania wartości zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="1c500-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="1c500-142">Jeśli powraca *przez odwołanie*, jest zwracany alias do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c500-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="1c500-143">W przypadku przekazania do innej metody *przez odwołanie*, jest przekazywany odwołanie do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="1c500-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="1c500-144">Po dokonaniu [lokalnej typu ref](#ref-local) aliasu, możesz wprowadzić nowy alias tę samą zmienną.</span><span class="sxs-lookup"><span data-stu-id="1c500-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="1c500-145">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="1c500-145">Ref locals</span></span>

<span data-ttu-id="1c500-146">Załóżmy `GetContactInformation` metoda jest zadeklarowana jako wartości ref zwrotu:</span><span class="sxs-lookup"><span data-stu-id="1c500-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="1c500-147">Przypisania przez wartość odczytuje wartość zmiennej i przypisuje go do nowej zmiennej:</span><span class="sxs-lookup"><span data-stu-id="1c500-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="1c500-148">Deklaruje poprzedniego przypisania `p` jako zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1c500-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="1c500-149">Swojej wartości początkowej zostanie skopiowana ze odczytywania wartości zwróconej przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="1c500-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="1c500-150">Przyszłe przydziały w celu `p` nie zmieni się wartość zmiennej zwrócony przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="1c500-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="1c500-151">Zmienna `p` nie jest już alias do zmiennej zwracane.</span><span class="sxs-lookup"><span data-stu-id="1c500-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="1c500-152">Należy zadeklarować *lokalnej typu ref* zmiennej, aby skopiować alias do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="1c500-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="1c500-153">W następujących przypisania `p` jest alias do zmiennej zwrócony z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="1c500-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="1c500-154">Użycie kolejnych `p` jest taka sama jak przy użyciu zmiennej zwrócony przez `GetContactInformation` ponieważ `p` jest aliasu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1c500-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="1c500-155">Zmienia się na `p` również zmienić zmiennej zwrócony z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="1c500-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="1c500-156">`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="1c500-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="1c500-157">Dostępne wartości przez odwołanie w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="1c500-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="1c500-158">W niektórych przypadkach dostępu do wartość przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="1c500-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="1c500-159">Na przykład następująca instrukcja pokazuje, jak jedną można zdefiniować wartości lokalnej ref, służący do odwołać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="1c500-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="1c500-160">`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wartością w drugim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c500-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="1c500-161">Błąd zawiera zarówno `ref` słów kluczowych w deklaracji zmiennej i przydziałów w obu przykłady powoduje błąd kompilatora CS8172, "nie można zainicjować zmiennej dostępnej przez odwołanie o wartości."</span><span class="sxs-lookup"><span data-stu-id="1c500-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="1c500-162">Przed C# 7.3 zmienne lokalne ref nie były ponownie przypisywane do odwołuje się do innego magazynu zostały już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="1c500-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="1c500-163">Ograniczenia zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="1c500-163">That restriction has been removed.</span></span> <span data-ttu-id="1c500-164">W poniższym przykładzie przedstawiono ponownego przypisania:</span><span class="sxs-lookup"><span data-stu-id="1c500-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="1c500-165">Zmienna lokalna REF nadal musi zostać zainicjowany, jeśli są deklarowane jako.</span><span class="sxs-lookup"><span data-stu-id="1c500-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="1c500-166">Zwraca ref i zmienne lokalne ref: przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="1c500-167">W poniższym przykładzie zdefiniowano `NumberStore` klasy, która przechowuje tablicę wartości będące liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="1c500-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="1c500-168">`FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazanego jako argument.</span><span class="sxs-lookup"><span data-stu-id="1c500-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="1c500-169">Jeśli żadna liczba jest większa niż lub równy argumentowi, metoda zwraca numer indeksu 0.</span><span class="sxs-lookup"><span data-stu-id="1c500-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="1c500-170">Następujące przykładowe wywołania `NumberStore.FindNumber` metoda pobierania pierwsza wartość, która jest większa niż lub równa 16.</span><span class="sxs-lookup"><span data-stu-id="1c500-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="1c500-171">Obiekt wywołujący następnie podwaja wartość zwrócona przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1c500-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="1c500-172">Dane wyjściowe z przykładu zawierają zmiany zostaną uwzględnione w wartości elementów tablicy `NumberStore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1c500-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="1c500-173">Bez obsługi odwołanie zwracane wartości takie działanie jest wykonywane przez zwrócenie indeks elementu tablicy wraz z jego wartość.</span><span class="sxs-lookup"><span data-stu-id="1c500-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="1c500-174">Obiekt wywołujący następnie można użyć tego indeksu można zmodyfikować wartości w wywołaniu metody oddzielne.</span><span class="sxs-lookup"><span data-stu-id="1c500-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="1c500-175">Jednak wywołującego można również zmodyfikować indeks dostępu i możliwie zmodyfikować inne wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="1c500-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="1c500-176">W poniższym przykładzie przedstawiono sposób `FindNumber` metody może ulegną po 7.3 C# do użycia lokalnego ponownego przypisania ref:</span><span class="sxs-lookup"><span data-stu-id="1c500-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="1c500-177">Ta druga wersja jest bardziej wydajny dłużej sekwencja w scenariuszach, w których liczba poszukiwane jest zbliżonej do końca tablicy.</span><span class="sxs-lookup"><span data-stu-id="1c500-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c500-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c500-178">See also</span></span>

[<span data-ttu-id="1c500-179">ref keyword</span><span class="sxs-lookup"><span data-stu-id="1c500-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="1c500-180">Semantykę odwołania z typami wartości</span><span class="sxs-lookup"><span data-stu-id="1c500-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
