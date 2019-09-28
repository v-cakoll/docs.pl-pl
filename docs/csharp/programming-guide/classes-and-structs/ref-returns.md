---
title: Wartości zwracane ref i lokalne elementy ref (C# przewodnik)
description: Dowiedz się, jak definiować i używać lokalnych wartości zwrotnych i ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e23007deffea0f542d623be918cd1c61496d1362
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353885"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="f5686-103">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="f5686-103">Ref returns and ref locals</span></span>

<span data-ttu-id="f5686-104">Począwszy od C# 7,0, C# obsługuje zwracane wartości odwołania (zwroty ref).</span><span class="sxs-lookup"><span data-stu-id="f5686-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="f5686-105">Wartość zwracana przez odwołanie umożliwia metodzie zwracanie odwołania do zmiennej, a nie wartości, z powrotem do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f5686-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="f5686-106">Obiekt wywołujący może następnie traktować zwracaną zmienną, tak jakby była zwracana przez wartość lub przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f5686-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="f5686-107">Obiekt wywołujący może utworzyć nową zmienną, która sama jest odwołaniem do zwracanej wartości o nazwie ref Local.</span><span class="sxs-lookup"><span data-stu-id="f5686-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="f5686-108">Co to jest zwrócona wartość odwołania?</span><span class="sxs-lookup"><span data-stu-id="f5686-108">What is a reference return value?</span></span>

<span data-ttu-id="f5686-109">Większość deweloperów zna przekazywanie argumentu do wywoływanej metody *przez odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="f5686-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="f5686-110">Lista argumentów wywoływanej metody zawiera zmienną przekazaną przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f5686-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="f5686-111">Wszystkie zmiany wprowadzone do jego wartości przez wywołaną metodę są obserwowane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f5686-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="f5686-112">*Wartość zwracana przez odwołanie* oznacza, że metoda zwraca *odwołanie* (lub alias) do pewnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="f5686-113">Zakres tej zmiennej musi zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="f5686-113">That variable's scope must include the method.</span></span> <span data-ttu-id="f5686-114">Okres istnienia tej zmiennej musi przekraczać wartość zwracaną przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f5686-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="f5686-115">Modyfikacje wartości zwracanej metody przez obiekt wywołujący są wprowadzane do zmiennej, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f5686-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="f5686-116">Deklarowanie, że metoda zwraca *odwołanie* do zwracanej wartości wskazuje, że metoda zwraca alias do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="f5686-117">Zamiarem projektowania często jest to, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="f5686-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="f5686-118">Wynika to z tego, że metody zwracające przez odwołanie nie mogą mieć zwracanego typu `void`.</span><span class="sxs-lookup"><span data-stu-id="f5686-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="f5686-119">Istnieją pewne ograniczenia dotyczące wyrażenia, które Metoda może zwrócić jako wartość zwracana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f5686-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="f5686-120">Ograniczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="f5686-120">Restrictions include:</span></span>

- <span data-ttu-id="f5686-121">Wartość zwracana musi mieć okres istnienia wykraczający poza wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="f5686-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="f5686-122">Innymi słowy, nie może być zmienną lokalną w metodzie, która zwraca ją.</span><span class="sxs-lookup"><span data-stu-id="f5686-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="f5686-123">Może to być wystąpienie lub statyczne pole klasy albo argument przeszedł do metody.</span><span class="sxs-lookup"><span data-stu-id="f5686-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="f5686-124">Próba zwrócenia zmiennej lokalnej powoduje wygenerowanie błędu kompilatora CS8168, "nie można zwrócić lokalnego elementu" obj "przez odwołanie, ponieważ nie jest to lokalne odwołanie".</span><span class="sxs-lookup"><span data-stu-id="f5686-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="f5686-125">Zwracana wartość nie może być literałem `null`.</span><span class="sxs-lookup"><span data-stu-id="f5686-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="f5686-126">Zwrócenie `null` generuje błąd kompilatora CS8156 "wyrażenie nie może być używane w tym kontekście, ponieważ może nie zostać zwrócone przez odwołanie".</span><span class="sxs-lookup"><span data-stu-id="f5686-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="f5686-127">Metoda ze zwróceniem ref może zwracać alias do zmiennej, której wartość jest obecnie wartością null (niebędącą wystąpieniem) lub [typem wartości null](../nullable-types/index.md) dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="f5686-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../nullable-types/index.md) for a value type.</span></span>

- <span data-ttu-id="f5686-128">Zwracana wartość nie może być stałą, składową wyliczenia, wartością zwracaną przez wartość z właściwości lub metodą `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="f5686-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="f5686-129">Naruszenie tej reguły powoduje wygenerowanie błędu kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ może ono nie zostać zwrócone przez odwołanie".</span><span class="sxs-lookup"><span data-stu-id="f5686-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="f5686-130">Dodatkowo odwołania do zwracanych wartości nie są dozwolone w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f5686-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="f5686-131">Metoda asynchroniczna może zostać zwrócona przed zakończeniem wykonywania, podczas gdy jej wartość zwracana jest nadal nieznana.</span><span class="sxs-lookup"><span data-stu-id="f5686-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="f5686-132">Definiowanie wartości zwracanej ref</span><span class="sxs-lookup"><span data-stu-id="f5686-132">Defining a ref return value</span></span>

<span data-ttu-id="f5686-133">Metoda zwracająca *wartość zwracaną przez odwołanie* musi spełniać następujące dwa warunki:</span><span class="sxs-lookup"><span data-stu-id="f5686-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="f5686-134">Podpis metody zawiera słowo kluczowe [ref](../../language-reference/keywords/ref.md) przed typem zwracanym.</span><span class="sxs-lookup"><span data-stu-id="f5686-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="f5686-135">Każda instrukcja [Return](../../language-reference/keywords/return.md) w treści metody zawiera słowo kluczowe [ref](../../language-reference/keywords/ref.md) przed nazwą zwracanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f5686-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="f5686-136">Poniższy przykład przedstawia metodę, która spełnia te warunki i zwraca odwołanie do obiektu `Person` o nazwie `p`:</span><span class="sxs-lookup"><span data-stu-id="f5686-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="f5686-137">Zużywanie referencyjnej wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="f5686-137">Consuming a ref return value</span></span>

<span data-ttu-id="f5686-138">Zwracana wartość Ref jest aliasem innej zmiennej w zakresie wywołanej metody.</span><span class="sxs-lookup"><span data-stu-id="f5686-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="f5686-139">Można interpretować dowolne użycie Return ref jako przy użyciu zmiennej aliasu IT:</span><span class="sxs-lookup"><span data-stu-id="f5686-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="f5686-140">Po przypisaniu jego wartości przypisujesz wartość do zmiennej aliasu IT.</span><span class="sxs-lookup"><span data-stu-id="f5686-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="f5686-141">Podczas odczytywania wartości, odczytywana jest wartość zmiennej aliasu IT.</span><span class="sxs-lookup"><span data-stu-id="f5686-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="f5686-142">Jeśli zwracasz ją *przez odwołanie*, zwracasz alias do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="f5686-143">Jeśli przekażesz go do innej metody *przez odwołanie*, przekazujesz odwołanie do zmiennej aliasu IT.</span><span class="sxs-lookup"><span data-stu-id="f5686-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="f5686-144">Po wprowadzeniu aliasu [lokalnego ref](#ref-locals) należy utworzyć nowy alias do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="f5686-145">Odwołania lokalne</span><span class="sxs-lookup"><span data-stu-id="f5686-145">Ref locals</span></span>

<span data-ttu-id="f5686-146">Załóżmy, że metoda `GetContactInformation` jest zadeklarowana jako zwrot ref:</span><span class="sxs-lookup"><span data-stu-id="f5686-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="f5686-147">Przypisanie przez wartość odczytuje wartość zmiennej i przypisuje ją do nowej zmiennej:</span><span class="sxs-lookup"><span data-stu-id="f5686-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="f5686-148">Poprzednie przypisanie deklaruje `p` jako zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="f5686-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="f5686-149">Jego początkowa wartość jest kopiowana z odczytywania wartości zwracanej przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f5686-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="f5686-150">Wszelkie przyszłe przypisania do `p` nie zmienią wartości zmiennej zwracanej przez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f5686-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="f5686-151">Zmienna `p` nie jest już aliasem zwracanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="f5686-152">Zadeklaruj zmienną *lokalną ref* , aby skopiować alias do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="f5686-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="f5686-153">W poniższym przypisaniu `p` jest aliasem zmiennej zwracanej z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f5686-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="f5686-154">Kolejne użycie `p` jest takie samo jak przy użyciu zmiennej zwracanej przez `GetContactInformation`, ponieważ `p` jest aliasem dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f5686-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="f5686-155">Zmiany `p` zmieniają również zmienną zwróconą z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f5686-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="f5686-156">Słowo kluczowe `ref` jest używane przed deklaracją zmiennej lokalnej *i* przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="f5686-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="f5686-157">Możesz uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f5686-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="f5686-158">W niektórych przypadkach uzyskanie dostępu do wartości przez odwołanie zwiększa wydajność poprzez uniknięcie potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="f5686-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="f5686-159">Na przykład poniższa instrukcja pokazuje, jak jedna z nich może definiować wartość lokalna ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="f5686-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="f5686-160">Słowo kluczowe `ref` jest używane przed deklaracją zmiennej lokalnej *i* przed wartością w drugim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f5686-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="f5686-161">Nie można dołączyć słów kluczowych `ref` w deklaracji zmiennej i przypisaniu w obu przykładach skutkuje błędem kompilatora CS8172 ".</span><span class="sxs-lookup"><span data-stu-id="f5686-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="f5686-162">Przed C# 7,3, nie można ponownie przypisać odwołań do zmiennych lokalnych w celu odwoływania się do innego magazynu po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="f5686-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="f5686-163">To ograniczenie zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="f5686-163">That restriction has been removed.</span></span> <span data-ttu-id="f5686-164">W poniższym przykładzie przedstawiono ponowne przypisanie:</span><span class="sxs-lookup"><span data-stu-id="f5686-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="f5686-165">Po zadeklarowaniu należy nadal inicjować zmienne lokalne ref.</span><span class="sxs-lookup"><span data-stu-id="f5686-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="f5686-166">Zwroty ref i lokalne elementy ref: przykład</span><span class="sxs-lookup"><span data-stu-id="f5686-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="f5686-167">W poniższym przykładzie zdefiniowano klasę `NumberStore`, która przechowuje tablicę wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="f5686-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="f5686-168">Metoda `FindNumber` zwraca przez odwołanie do pierwszej liczby, która jest większa lub równa liczbie przesłanej jako argument.</span><span class="sxs-lookup"><span data-stu-id="f5686-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="f5686-169">Jeśli żadna liczba nie jest większa lub równa argumentowi, metoda zwraca liczbę w indeksie 0.</span><span class="sxs-lookup"><span data-stu-id="f5686-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="f5686-170">Poniższy przykład wywołuje metodę `NumberStore.FindNumber` w celu pobrania pierwszej wartości, która jest większa lub równa 16.</span><span class="sxs-lookup"><span data-stu-id="f5686-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="f5686-171">Obiekt wywołujący następnie podwaja wartość zwróconą przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f5686-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="f5686-172">Dane wyjściowe z przykładu przedstawiają zmianę odzwierciedloną w wartości elementów tablicy wystąpienia `NumberStore`.</span><span class="sxs-lookup"><span data-stu-id="f5686-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="f5686-173">Bez obsługi wartości zwracanych odwołań, taka operacja jest wykonywana przez zwrócenie indeksu elementu tablicy wraz z jego wartością.</span><span class="sxs-lookup"><span data-stu-id="f5686-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="f5686-174">Obiekt wywołujący może następnie użyć tego indeksu do zmodyfikowania wartości w osobnym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="f5686-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="f5686-175">Jednak obiekt wywołujący może także zmodyfikować indeks, aby uzyskać dostęp do innych wartości tablicy i prawdopodobnie je zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="f5686-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="f5686-176">W poniższym przykładzie pokazano, jak można ponownie napisać metodę `FindNumber` po C# 7,3, aby użyć lokalnego ponownego przypisania odwołania:</span><span class="sxs-lookup"><span data-stu-id="f5686-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="f5686-177">Ta druga wersja jest wydajniejsza z dłuższymi sekwencjami w scenariuszach, w których liczba poszukiwanych elementów jest bliżej końca tablicy.</span><span class="sxs-lookup"><span data-stu-id="f5686-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5686-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5686-178">See also</span></span>

- [<span data-ttu-id="f5686-179">ref keyword</span><span class="sxs-lookup"><span data-stu-id="f5686-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="f5686-180">Zapisz bezpieczny wydajny kod</span><span class="sxs-lookup"><span data-stu-id="f5686-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
