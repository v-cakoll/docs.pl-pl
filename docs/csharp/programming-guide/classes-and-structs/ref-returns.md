---
title: Ref zwraca wartości i ref locals (C# Przewodnik)
description: Dowiedz się, jak definiować i używać wartości ref return i ref local
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170076"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="039d5-103">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="039d5-103">Ref returns and ref locals</span></span>

<span data-ttu-id="039d5-104">Począwszy od Języka C# 7.0, C# obsługuje wartości zwracane odwołania (ref zwraca).</span><span class="sxs-lookup"><span data-stu-id="039d5-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="039d5-105">Wartość zwracana odwołania umożliwia metody, aby zwrócić odwołanie do zmiennej, a nie wartość, z powrotem do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="039d5-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="039d5-106">Obiekt wywołujący może następnie traktować zwróconą zmienną tak, jakby została zwrócona przez wartość lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="039d5-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="039d5-107">Obiekt wywołujący można utworzyć nową zmienną, która sama odwołuje się do zwracanej wartości, o nazwie ref local.</span><span class="sxs-lookup"><span data-stu-id="039d5-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="039d5-108">Co to jest wartość zwracana odwołania?</span><span class="sxs-lookup"><span data-stu-id="039d5-108">What is a reference return value?</span></span>

<span data-ttu-id="039d5-109">Większość deweloperów są zaznajomieni z przekazywanie argumentu do metody wywoływanej *przez odwołanie*.</span><span class="sxs-lookup"><span data-stu-id="039d5-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="039d5-110">Lista argumentów metody o nazwie zawiera zmienną przekazaną przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="039d5-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="039d5-111">Wszelkie zmiany wprowadzone do jego wartości przez wywoływaną metodę są obserwowane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="039d5-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="039d5-112">*Wartość zwracana odwołania* oznacza, że metoda zwraca *odwołanie* (lub alias) do niektórych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="039d5-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="039d5-113">Zakres tej zmiennej musi zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="039d5-113">That variable's scope must include the method.</span></span> <span data-ttu-id="039d5-114">Okres istnienia tej zmiennej musi wykraczać poza zwrot metody.</span><span class="sxs-lookup"><span data-stu-id="039d5-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="039d5-115">Modyfikacje wartości zwracanej metody przez obiekt wywołujący są dokonywane do zmiennej, która jest zwracana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="039d5-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="039d5-116">Deklarowanie, że metoda zwraca *wartość zwracaną odwołanie* wskazuje, że metoda zwraca alias do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="039d5-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="039d5-117">Intencją projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pośrednictwem aliasu, w tym do modyfikowania go.</span><span class="sxs-lookup"><span data-stu-id="039d5-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="039d5-118">Wynika z tego, że metody zwracane przez odwołanie `void`nie mogą mieć typu zwracanego .</span><span class="sxs-lookup"><span data-stu-id="039d5-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="039d5-119">Istnieją pewne ograniczenia dotyczące wyrażenia, które metoda może zwrócić jako wartość zwracana odwołania.</span><span class="sxs-lookup"><span data-stu-id="039d5-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="039d5-120">Ograniczenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="039d5-120">Restrictions include:</span></span>

- <span data-ttu-id="039d5-121">Wartość zwracana musi mieć okres istnienia, który wykracza poza wykonanie metody.</span><span class="sxs-lookup"><span data-stu-id="039d5-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="039d5-122">Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go.</span><span class="sxs-lookup"><span data-stu-id="039d5-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="039d5-123">Może to być wystąpienie lub statyczne pole klasy lub może to być argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="039d5-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="039d5-124">Próba zwrócenia zmiennej lokalnej generuje błąd kompilatora CS8168, "Nie można zwrócić lokalnego 'obj' przez odwołanie, ponieważ nie jest ref lokalny."</span><span class="sxs-lookup"><span data-stu-id="039d5-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="039d5-125">Wartość zwracana nie `null`może być literałem .</span><span class="sxs-lookup"><span data-stu-id="039d5-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="039d5-126">Zwracanie `null` generuje błąd kompilatora CS8156, "Wyrażenie nie może być używany w tym kontekście, ponieważ nie może być zwracany przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="039d5-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="039d5-127">Metoda z ref return może zwrócić alias do zmiennej, której wartość jest obecnie wartość null (uninstantiated) lub [typu wartości null](../../language-reference/builtin-types/nullable-value-types.md) dla typu wartości.</span><span class="sxs-lookup"><span data-stu-id="039d5-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../../language-reference/builtin-types/nullable-value-types.md) for a value type.</span></span>

- <span data-ttu-id="039d5-128">Wartość zwracana nie może być stała, element członkowski wyliczenia, wartość zwracana według wartości z właściwości lub metody `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="039d5-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="039d5-129">Naruszenie tej reguły generuje błąd kompilatora CS8156, "Wyrażenie nie może być używane w tym kontekście, ponieważ nie może być zwracany przez odwołanie."</span><span class="sxs-lookup"><span data-stu-id="039d5-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="039d5-130">Ponadto wartości zwracane odwołania nie są dozwolone w metodach asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="039d5-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="039d5-131">Metoda asynchroniczna może zwrócić przed zakończeniem wykonywania, podczas gdy jego wartość zwracana jest nadal nieznany.</span><span class="sxs-lookup"><span data-stu-id="039d5-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="039d5-132">Definiowanie wartości zwracanej ref</span><span class="sxs-lookup"><span data-stu-id="039d5-132">Defining a ref return value</span></span>

<span data-ttu-id="039d5-133">Metoda zwracająca *wartość zwracaną odwołanie* musi spełniać następujące dwa warunki:</span><span class="sxs-lookup"><span data-stu-id="039d5-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="039d5-134">Podpis metody zawiera [ref](../../language-reference/keywords/ref.md) słowa kluczowego przed typem zwracanego.</span><span class="sxs-lookup"><span data-stu-id="039d5-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="039d5-135">Każda [instrukcja return](../../language-reference/keywords/return.md) w treści metody zawiera [ref](../../language-reference/keywords/ref.md) słowa kluczowego przed nazwą zwróconego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="039d5-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="039d5-136">W poniższym przykładzie przedstawiono metodę, która spełnia te `Person` warunki `p`i zwraca odwołanie do obiektu o nazwie:</span><span class="sxs-lookup"><span data-stu-id="039d5-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="039d5-137">Zużywanie wartości zwracanej ref</span><span class="sxs-lookup"><span data-stu-id="039d5-137">Consuming a ref return value</span></span>

<span data-ttu-id="039d5-138">Wartość zwracana ref jest aliasem do innej zmiennej w zakresie metody o nazwie.</span><span class="sxs-lookup"><span data-stu-id="039d5-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="039d5-139">Można interpretować dowolne użycie ref return jako przy użyciu zmiennej aliases:</span><span class="sxs-lookup"><span data-stu-id="039d5-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="039d5-140">Po przypisaniu jego wartości przypisuje stwierdzono, że wartość jest przypisywana do zmiennej, którą aliasuje.</span><span class="sxs-lookup"><span data-stu-id="039d5-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="039d5-141">Podczas odczytywania jego wartości odczytywasz wartość zmiennej, którą aliases.</span><span class="sxs-lookup"><span data-stu-id="039d5-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="039d5-142">Jeśli zwrócisz go *przez odwołanie,* zwracasz alias do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="039d5-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="039d5-143">Jeśli przekażesz go do innej metody *przez odwołanie,* przekazujesz odwołanie do zmiennej, którą aliasuje.</span><span class="sxs-lookup"><span data-stu-id="039d5-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="039d5-144">Po wprowadzeniu [aliasu lokalnego ref](#ref-locals) wprowadzasz nowy alias do tej samej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="039d5-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="039d5-145">Ref miejscowi</span><span class="sxs-lookup"><span data-stu-id="039d5-145">Ref locals</span></span>

<span data-ttu-id="039d5-146">Załóżmy, że `GetContactInformation` metoda jest zadeklarowana jako ref return:</span><span class="sxs-lookup"><span data-stu-id="039d5-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="039d5-147">Przypisanie według wartości odczytuje wartość zmiennej i przypisuje ją do nowej zmiennej:</span><span class="sxs-lookup"><span data-stu-id="039d5-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="039d5-148">Poprzednie przypisanie deklaruje `p` jako zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="039d5-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="039d5-149">Jego wartość początkowa jest kopiowana `GetContactInformation`z odczytu wartości zwracanej przez .</span><span class="sxs-lookup"><span data-stu-id="039d5-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="039d5-150">Wszelkie przyszłe przypisania nie `p` zmienią wartości zmiennej `GetContactInformation`zwróconej przez .</span><span class="sxs-lookup"><span data-stu-id="039d5-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="039d5-151">Zmienna `p` nie jest już aliasem zwróconej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="039d5-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="039d5-152">Deklarujesz zmienną *lokalną ref,* aby skopiować alias do oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="039d5-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="039d5-153">W poniższym `p` przypisaniu jest aliasem `GetContactInformation`zmiennej zwróconej z .</span><span class="sxs-lookup"><span data-stu-id="039d5-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="039d5-154">Kolejne użycie `p` jest taka sama jak przy `GetContactInformation` `p` użyciu zmiennej zwracanej przez ponieważ jest aliasdla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="039d5-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="039d5-155">Zmiany, `p` aby również zmienić `GetContactInformation`zmienną zwróconą z .</span><span class="sxs-lookup"><span data-stu-id="039d5-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="039d5-156">Słowo `ref` kluczowe jest używane zarówno przed deklaracją zmiennej *lokalnej, jak i* przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="039d5-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span>

<span data-ttu-id="039d5-157">Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="039d5-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="039d5-158">W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="039d5-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="039d5-159">Na przykład w poniższej instrukcji pokazano, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="039d5-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="039d5-160">Słowo `ref` kluczowe jest używane zarówno przed deklaracją zmiennej *lokalnej, jak i* przed wartością w drugim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="039d5-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="039d5-161">Nieuwzględnienie obu `ref` słów kluczowych w deklaracji zmiennej i przypisania w obu przykładach powoduje błąd kompilatora CS8172, "Nie można zainicjować zmiennej przez odwołanie z wartością."</span><span class="sxs-lookup"><span data-stu-id="039d5-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="039d5-162">Przed C# 7.3 ref zmiennych lokalnych nie można ponownie przypisać do odwoływania się do innego magazynu po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="039d5-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="039d5-163">Ograniczenie to zostało zniesione.</span><span class="sxs-lookup"><span data-stu-id="039d5-163">That restriction has been removed.</span></span> <span data-ttu-id="039d5-164">W poniższym przykładzie przedstawiono ponowne przypisanie:</span><span class="sxs-lookup"><span data-stu-id="039d5-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="039d5-165">Ref zmienne lokalne muszą być nadal inicjowane, gdy są deklarowane.</span><span class="sxs-lookup"><span data-stu-id="039d5-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="039d5-166">Ref zwraca i ref locals: przykład</span><span class="sxs-lookup"><span data-stu-id="039d5-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="039d5-167">W poniższym `NumberStore` przykładzie zdefiniowano klasę, która przechowuje tablicę wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="039d5-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="039d5-168">Metoda `FindNumber` zwraca przez odwołanie pierwszy numer, który jest większy lub równy liczbie przekazywanej jako argument.</span><span class="sxs-lookup"><span data-stu-id="039d5-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="039d5-169">Jeśli żadna liczba nie jest większa lub równa argumentowi, metoda zwraca liczbę w indeksie 0.</span><span class="sxs-lookup"><span data-stu-id="039d5-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="039d5-170">Poniższy przykład wywołuje `NumberStore.FindNumber` metodę, aby pobrać pierwszą wartość, która jest większa lub równa 16.</span><span class="sxs-lookup"><span data-stu-id="039d5-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="039d5-171">Następnie obiekt wywołujący podwaja wartość zwracaną przez metodę.</span><span class="sxs-lookup"><span data-stu-id="039d5-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="039d5-172">Dane wyjściowe z przykładu pokazuje zmiany odzwierciedlone w wartości `NumberStore` elementów tablicy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="039d5-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="039d5-173">Bez obsługi dla wartości zwracanych odniesienia, taka operacja jest wykonywana przez zwrócenie indeksu elementu tablicy wraz z jego wartością.</span><span class="sxs-lookup"><span data-stu-id="039d5-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="039d5-174">Obiekt wywołujący można następnie użyć tego indeksu, aby zmodyfikować wartość w wywołaniu metody oddzielne.</span><span class="sxs-lookup"><span data-stu-id="039d5-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="039d5-175">Jednak obiekt wywołujący można również zmodyfikować indeks, aby uzyskać dostęp i ewentualnie zmodyfikować inne wartości tablicy.</span><span class="sxs-lookup"><span data-stu-id="039d5-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="039d5-176">W poniższym przykładzie `FindNumber` pokazano, jak metoda może być przepisany po C# 7.3 do korzystania ref lokalnego ponownego przypisania:</span><span class="sxs-lookup"><span data-stu-id="039d5-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="039d5-177">Ta druga wersja jest bardziej efektywne z dłuższych sekwencji w scenariuszach, w których żądana liczba jest bliżej końca tablicy.</span><span class="sxs-lookup"><span data-stu-id="039d5-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="039d5-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="039d5-178">See also</span></span>

- [<span data-ttu-id="039d5-179">ref — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="039d5-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="039d5-180">Napisz bezpieczny, wydajny kod</span><span class="sxs-lookup"><span data-stu-id="039d5-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
