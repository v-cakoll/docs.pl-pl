---
title: Wartości zwracane ref i zmienne lokalne ref (Przewodnik C#)
description: Dowiedz się, jak zdefiniować i zastosować zwracane ref i wartości lokalnych typu ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: 6250d2b0c3490cce18623d6b06d5e1a352f22c09
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616143"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="e1b06-103">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="e1b06-103">Ref returns and ref locals</span></span>

<span data-ttu-id="e1b06-104">Począwszy od języka C# 7.0, C# obsługuje wartości zwracane odwołanie (ref zwraca).</span><span class="sxs-lookup"><span data-stu-id="e1b06-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="e1b06-105">Odwołanie zwracana wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e1b06-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="e1b06-106">Obiekt wywołujący możliwość traktować zwrócone zmiennej tak, jakby zostały zwrócone, przez wartość lub przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e1b06-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="e1b06-107">Obiekt wywołujący, można utworzyć nową zmienną, która sama jest odwołaniem do wartości zwracane ref o nazwie lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="e1b06-108">Co to jest zwracana wartość odniesienia?</span><span class="sxs-lookup"><span data-stu-id="e1b06-108">What is a reference return value?</span></span>

<span data-ttu-id="e1b06-109">Większość programistów zaczynasz przekazywanie argumentu metody o nazwie *przez odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="e1b06-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="e1b06-110">Listy argumentów o nazwie metody zawiera zmienną przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e1b06-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="e1b06-111">Wszelkie zmiany wprowadzone do jego wartości przez metodę o nazwie są przestrzegane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e1b06-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="e1b06-112">A *odwoływać się do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub aliasem) do niektórych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="e1b06-113">Tę zmienną zakresu musi zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="e1b06-113">That variable's scope must include the method.</span></span> <span data-ttu-id="e1b06-114">Okres istnienia tej zmiennej musi wykraczać poza zwrotu metody.</span><span class="sxs-lookup"><span data-stu-id="e1b06-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="e1b06-115">Do metody wartości zwracanej przez obiekt wywołujący modyfikacje wprowadza do zmiennej, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="e1b06-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="e1b06-116">Deklarowanie, metoda zwraca *odwoływać się do wartości zwracanej* wskazuje, że metoda zwraca alias do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="e1b06-117">Celem projektu jest często, że kod wywołujący powinni mieć dostęp do tej zmiennej za pomocą aliasu, włączając go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="e1b06-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="e1b06-118">Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="e1b06-119">Istnieją pewne ograniczenia na wyrażenie, które metoda może zwracać jako odwołanie do wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="e1b06-120">Ograniczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="e1b06-120">Restrictions include:</span></span>

- <span data-ttu-id="e1b06-121">Zwracana wartość musi mieć okresu istnienia, który wykracza poza wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="e1b06-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="e1b06-122">Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go.</span><span class="sxs-lookup"><span data-stu-id="e1b06-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="e1b06-123">Może to być wystąpienia lub pole statyczne klasy lub może być argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="e1b06-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="e1b06-124">Podjęto próbę zwracanych zmienną lokalną generuje błąd kompilatora CS8168, "nie może zwrócić lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."</span><span class="sxs-lookup"><span data-stu-id="e1b06-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="e1b06-125">Zwracana wartość nie może być literał `null`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="e1b06-126">Zwracanie `null` generuje błąd kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="e1b06-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="e1b06-127">Metoda z zwracane ref może zwracać alias do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typu dopuszczającego wartość null](../nullable-types/index.md) dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="e1b06-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="e1b06-128">Zwracana wartość nie może być stała, elementu członkowskiego wyliczenia, wartość zwracana przez wartość właściwości lub metody `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="e1b06-129">Naruszenie tej zasady generuje błąd kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="e1b06-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="e1b06-130">Ponadto odwołania zwracanych wartości nie są dozwolone w metodach async.</span><span class="sxs-lookup"><span data-stu-id="e1b06-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="e1b06-131">Metoda asynchroniczna może zwracać, zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany.</span><span class="sxs-lookup"><span data-stu-id="e1b06-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="e1b06-132">Definiowanie wartości zwracane ref</span><span class="sxs-lookup"><span data-stu-id="e1b06-132">Defining a ref return value</span></span>

<span data-ttu-id="e1b06-133">Metoda, która zwraca *odwoływać się do wartości zwracanej* musi spełniać następujące dwa warunki:</span><span class="sxs-lookup"><span data-stu-id="e1b06-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="e1b06-134">Podpis metody zawiera [ref](../../language-reference/keywords/ref.md) — słowo kluczowe przed zwracanym typem.</span><span class="sxs-lookup"><span data-stu-id="e1b06-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="e1b06-135">Każdy [zwracają](../../language-reference/keywords/return.md) instrukcja w treści metody zawiera [ref](../../language-reference/keywords/ref.md) — słowo kluczowe przed nazwą zwracanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e1b06-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="e1b06-136">W poniższym przykładzie pokazano metodę, która spełnia te warunki i zwraca odwołanie do `Person` obiektu o nazwie `p`:</span><span class="sxs-lookup"><span data-stu-id="e1b06-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="e1b06-137">Korzystanie z wartością zwracaną ref</span><span class="sxs-lookup"><span data-stu-id="e1b06-137">Consuming a ref return value</span></span>

<span data-ttu-id="e1b06-138">Odwołania zwracana wartość jest alias do innej zmiennej w zakresie wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="e1b06-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="e1b06-139">Może interpretować jakiekolwiek użycie zwracane ref, używając zmiennej go aliasy:</span><span class="sxs-lookup"><span data-stu-id="e1b06-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="e1b06-140">Po przypisaniu jej wartość są przypisywania wartości do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="e1b06-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="e1b06-141">Podczas odczytywania wartości odczytujesz wartość zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="e1b06-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="e1b06-142">Jeśli przywrócić go *przez odwołanie*, alias jest zwracany do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="e1b06-143">W przypadku przekazania do innej metody *przez odwołanie*, kończy się sukcesem odwołania do zmiennej go aliasów.</span><span class="sxs-lookup"><span data-stu-id="e1b06-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="e1b06-144">Po ustawieniu [odwołanie lokalne](#ref-locals) alias, należy wprowadzić nowy alias tę samą zmienną.</span><span class="sxs-lookup"><span data-stu-id="e1b06-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="e1b06-145">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="e1b06-145">Ref locals</span></span>

<span data-ttu-id="e1b06-146">Załóżmy `GetContactInformation` metody jest zadeklarowany jako ref zwracany:</span><span class="sxs-lookup"><span data-stu-id="e1b06-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="e1b06-147">Przypisania przez wartość odczytuje wartość zmiennej, a następnie przypisuje go do nowej zmiennej:</span><span class="sxs-lookup"><span data-stu-id="e1b06-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e1b06-148">Deklaruje poprzedniego przypisania `p` jako zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="e1b06-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="e1b06-149">Wartość początkowa jest kopiowany z odczytywania wartości zwracanej przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="e1b06-150">Wszystkie przyszłe przypisania do `p` nie zmieni się wartość zmiennej zwrócony przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="e1b06-151">Zmienna `p` nie jest już aliasem do zmiennej, zwracany.</span><span class="sxs-lookup"><span data-stu-id="e1b06-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="e1b06-152">Możesz deklarować *odwołanie lokalne* zmiennej, aby skopiować alias do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="e1b06-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="e1b06-153">W następujących przypisaniu `p` alias dla zmiennej zwróciło `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e1b06-154">Kolejne użycie `p` jest taka sama jak za pomocą zmiennej zwrócony przez `GetContactInformation` ponieważ `p` jest aliasem dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e1b06-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="e1b06-155">Zmienia się na `p` również zmienić zmienną zwróciło `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e1b06-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="e1b06-156">`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="e1b06-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="e1b06-157">Dostępne wartości przez odwołanie, w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="e1b06-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="e1b06-158">W niektórych przypadkach uzyskiwanie dostępu do wartości przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="e1b06-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="e1b06-159">Na przykład następująca instrukcja pokazuje, jak jeden można zdefiniować wartości lokalnej ref, służący do odwoływać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="e1b06-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="e1b06-160">`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wartością w drugim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e1b06-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="e1b06-161">Niepodanie zarówno `ref` słów kluczowych w deklaracji zmiennej i przydziałów w obu przykładach skutkuje błąd kompilatora CS8172, "nie można zainicjować zmiennej o wartości przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="e1b06-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="e1b06-162">Przed C# 7.3 zmienne lokalne ref nie można ponownie przypisać do odwoływania się do innego magazynu zostały już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="e1b06-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="e1b06-163">Tego ograniczenia zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="e1b06-163">That restriction has been removed.</span></span> <span data-ttu-id="e1b06-164">Poniższy przykład przedstawia ponowne przypisanie:</span><span class="sxs-lookup"><span data-stu-id="e1b06-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="e1b06-165">Zmienne lokalne REF nadal musi być inicjowana, gdy są one zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="e1b06-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="e1b06-166">Wartości zwracane ref i zmienne lokalne ref: przykład</span><span class="sxs-lookup"><span data-stu-id="e1b06-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="e1b06-167">W poniższym przykładzie zdefiniowano `NumberStore` klasę, która przechowuje tablicę wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e1b06-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="e1b06-168">`FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazywany jako argument.</span><span class="sxs-lookup"><span data-stu-id="e1b06-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="e1b06-169">Jeśli żadna liczba nie jest większa lub równa wartości argumentu, metoda zwraca numer indeksu 0.</span><span class="sxs-lookup"><span data-stu-id="e1b06-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="e1b06-170">Poniższy przykład wywołuje `NumberStore.FindNumber` metodę, która pobierze pierwszą wartość, która jest większa niż lub równe 16.</span><span class="sxs-lookup"><span data-stu-id="e1b06-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="e1b06-171">Obiekt wywołujący podwaja się następnie wartość zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="e1b06-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="e1b06-172">Dane wyjściowe z przykładu przedstawia zmiany zostaną uwzględnione w wartości elementów tablicy `NumberStore` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e1b06-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="e1b06-173">Bez obsługi wartości zwracane odwołanie taka operacja jest wykonywana przez zwraca indeks elementu tablicy, wraz z jego wartość.</span><span class="sxs-lookup"><span data-stu-id="e1b06-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="e1b06-174">Obiekt wywołujący do modyfikowania wartości w wywołaniu metody oddzielne, następnie można użyć tego indeksu.</span><span class="sxs-lookup"><span data-stu-id="e1b06-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="e1b06-175">Jednak obiekt wywołujący, można również zmodyfikować indeks, aby uzyskać dostęp i możliwie zmodyfikować pozostałe wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e1b06-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="e1b06-176">W poniższym przykładzie pokazano sposób, w jaki `FindNumber` metody, które można dopasować po języka C# 7.3 do użycia lokalnego ponowne przypisanie atrybutu ref:</span><span class="sxs-lookup"><span data-stu-id="e1b06-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="e1b06-177">Ta druga wersja jest bardziej wydajne, za pomocą sekwencji dłużej w scenariuszach, gdzie numer poszukiwane jest bliżej końca tablicy.</span><span class="sxs-lookup"><span data-stu-id="e1b06-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1b06-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1b06-178">See also</span></span>

- [<span data-ttu-id="e1b06-179">ref keyword</span><span class="sxs-lookup"><span data-stu-id="e1b06-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
- [<span data-ttu-id="e1b06-180">Semantyka odwołań z typami wartości</span><span class="sxs-lookup"><span data-stu-id="e1b06-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
