---
title: Wartości zwracane ref i ref zmienne lokalne (Przewodnik C#)
description: Dowiedz się, jak zdefiniować i użyć zwracane ref i wartości lokalnej ref
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="a8cb6-103">Zwraca ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="a8cb6-103">Ref returns and ref locals</span></span>

<span data-ttu-id="a8cb6-104">Począwszy od C# 7, C# obsługuje zwracanych wartości odwołanie (ref zwraca).</span><span class="sxs-lookup"><span data-stu-id="a8cb6-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="a8cb6-105">Odwołanie zwracać wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="a8cb6-106">Obiekt wywołujący możliwość traktować zwrócony zmiennej tak, jakby zwrócono według wartości lub według odwołania.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="a8cb6-107">Obiekt wywołujący może utworzyć nową zmienną, która jest elementem odwołania do zwrócona wartość ref o nazwie lokalnej.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="a8cb6-108">Co to jest wartością zwracaną odwołania?</span><span class="sxs-lookup"><span data-stu-id="a8cb6-108">What is a reference return value?</span></span>

<span data-ttu-id="a8cb6-109">Deweloperzy większość zapoznali się z przekazywaniem argumentu metody wywołane *przez odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="a8cb6-110">Argument wywołaną metodę się, że lista zawiera zmienną przekazywane przez odwołanie, a wszelkie zmiany wprowadzone do jego wartości przez metodę o nazwie są przestrzegane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="a8cb6-111">A *odwołania do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub alias) do niektórych zmiennej którego zakres obejmuje metodę i którego okres istnienia muszą być rozszerzane poza zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="a8cb6-112">Do wartości zwracanej przez metodę przez obiekt wywołujący się zmiany do zmiennej, który jest zwracany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="a8cb6-113">Deklarowanie metody zwracające *odwołania zwracana wartość* wskazuje, że ta metoda zwraca alias do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="a8cb6-114">Celem projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do jej modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="a8cb6-115">Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="a8cb6-116">Istnieją pewne ograniczenia na wyrażenie, które może zwracać metoda jako wartości zwracane odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="a8cb6-117">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-117">These include:</span></span>

- <span data-ttu-id="a8cb6-118">Zwracana wartość musi mieć okresu istnienia, która wykracza poza wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="a8cb6-119">Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="a8cb6-120">Można instancji lub pola statycznego w klasie lub może być argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="a8cb6-121">Próby zwracać zmiennej lokalnej generuje błąd kompilatora CS8168, "nie może zwracać lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."</span><span class="sxs-lookup"><span data-stu-id="a8cb6-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="a8cb6-122">Wartość zwrotna nie może być literał `null`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="a8cb6-123">Podjęto próbę zwracać `null` generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="a8cb6-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="a8cb6-124">Metody z ref zwracany alias można było powrócić do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typ dopuszczający wartość null](../nullable-types/index.md) dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="a8cb6-125">Wartość zwrotna nie może być stałą, elementu członkowskiego wyliczenia, wartość zwracana przez wartości z właściwości lub metody `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="a8cb6-126">Próba zwrócić te generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="a8cb6-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="a8cb6-127">Ponadto ponieważ może zwracać metodę asynchroniczną, zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany, odwołanie zwracane wartości są niedozwolone w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="a8cb6-128">Definiowanie wartości zwracanej ref</span><span class="sxs-lookup"><span data-stu-id="a8cb6-128">Defining a ref return value</span></span>

<span data-ttu-id="a8cb6-129">Zdefiniuj ref wartości zwracanej przez dodanie [ref](../../language-reference/keywords/ref.md) — słowo kluczowe na zwracany typ sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="a8cb6-130">Na przykład następująca sygnatura wskazuje, że `GetContactInformation` właściwość zwraca odwołanie do `Person` obiektu do obiektu wywołującego:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="a8cb6-131">Ponadto nazwa obiektu zwracaną przez każdy [zwracać](../../language-reference/keywords/return.md) instrukcji w treści metody musi być poprzedzona [ref](../../language-reference/keywords/ref.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="a8cb6-132">Na przykład następująca `return` instrukcja zwraca odwołanie do `Person` obiektu o nazwie `p`:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="a8cb6-133">Korzystanie z wartością zwracaną ref</span><span class="sxs-lookup"><span data-stu-id="a8cb6-133">Consuming a ref return value</span></span>

<span data-ttu-id="a8cb6-134">Ref zwracać wartość jest alias do innej zmiennej w zakresie wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="a8cb6-135">Można odnaleźć żadnego użycie ref zwracany jako przy użyciu zmiennej go aliasy:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="a8cb6-136">Po przypisaniu jej wartość są przypisywanie wartości do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="a8cb6-137">Podczas czytania wartość odczytywania wartości zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="a8cb6-138">Jeśli powraca *przez odwołanie* alias jest zwracany do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="a8cb6-139">W przypadku przekazania do innej metody *przez odwołanie* przekazywane odwołanie do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="a8cb6-140">Po dokonaniu [lokalnej typu ref](#ref-local) aliasu, możesz wprowadzić nowy alias tę samą zmienną.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="a8cb6-141">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="a8cb6-141">Ref locals</span></span>

<span data-ttu-id="a8cb6-142">Załóżmy `GetContactInformation` metoda jest zadeklarowana jako wartości ref zwrotu:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="a8cb6-143">Przypisania przez wartość odczytuje wartość zmiennej i przypisuje go do nowej zmiennej:</span><span class="sxs-lookup"><span data-stu-id="a8cb6-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="a8cb6-144">Deklaruje poprzedniego przypisania `p` jako zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="a8cb6-145">Swojej wartości początkowej zostanie skopiowana ze odczytywania wartości zwróconej przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="a8cb6-146">Przyszłe przydziały w celu `p` nie zmieni się wartość zmiennej zwrócony przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="a8cb6-147">Zmienna `p` nie jest już alias do zmiennej zwracane.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="a8cb6-148">Należy zadeklarować *lokalnej typu ref* zmiennej, aby skopiować alias do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="a8cb6-149">W następujących przypisania `p` jest alias do zmiennej zwrócony z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="a8cb6-150">Użycie kolejnych `p` jest taka sama jak przy użyciu zmiennej zwrócony przez `GetContactInformation` ponieważ `p` jest aliasu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="a8cb6-151">Zmienia się na `p` również zmienić zmiennej zwrócony z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="a8cb6-152">Należy pamiętać, że `ref` słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="a8cb6-153">Dostępne wartości przez odwołanie w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-153">You can access a value by reference in the same way.</span></span> <span data-ttu-id="a8cb6-154">W niektórych przypadkach dostępu do wartość przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-154">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="a8cb6-155">Na przykład następująca instrukcja pokazuje, jak jedną można zdefiniować wartości lokalnej ref, służący do odwołać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-155">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="a8cb6-156">Należy pamiętać, że `ref` słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wartością w drugim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-156">Note that the `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="a8cb6-157">Błąd zawiera zarówno `ref` słów kluczowych w deklaracji zmiennej i przydziałów w obu przykłady powoduje błąd kompilatora CS8172, "nie można zainicjować zmiennej dostępnej przez odwołanie o wartości."</span><span class="sxs-lookup"><span data-stu-id="a8cb6-157">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="a8cb6-158">Zwraca ref i zmienne lokalne ref: przykład</span><span class="sxs-lookup"><span data-stu-id="a8cb6-158">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="a8cb6-159">W poniższym przykładzie zdefiniowano `NumberStore` klasy, która przechowuje tablicę wartości będące liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-159">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="a8cb6-160">`FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazanego jako argument.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-160">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="a8cb6-161">Jeśli żadna liczba jest większa niż lub równy argumentowi, metoda zwraca numer indeksu 0.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-161">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="a8cb6-162">Następujące przykładowe wywołania `NumberStore.FindNumber` metoda pobierania pierwsza wartość, która jest większa niż lub równa 16.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-162">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="a8cb6-163">Obiekt wywołujący następnie podwaja wartość zwrócona przez metodę.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-163">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="a8cb6-164">Jak dane wyjściowe w przykładzie pokazano, ta zmiana ta jest uwzględniana w wartości elementów tablicy `NumberStore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-164">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="a8cb6-165">Takie działanie bez obsługi zwracanych wartości odwołania, zwykle odbywa się zwracając indeks elementu tablicy wraz z jego wartość.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-165">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="a8cb6-166">Obiekt wywołujący następnie można użyć tego indeksu można zmodyfikować wartości w wywołaniu metody oddzielne.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-166">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="a8cb6-167">Jednak wywołującego można również zmodyfikować indeks dostępu i możliwie zmodyfikować inne wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8cb6-167">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="a8cb6-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8cb6-168">See also</span></span>

[<span data-ttu-id="a8cb6-169">ref keyword</span><span class="sxs-lookup"><span data-stu-id="a8cb6-169">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="a8cb6-170">Semantykę odwołania z typami wartości</span><span class="sxs-lookup"><span data-stu-id="a8cb6-170">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
