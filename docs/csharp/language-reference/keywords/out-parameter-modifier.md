---
title: modyfikator parametrów out - Odwołanie do języka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 57308992268e1285cfeb82b28e2abf213e7a831b
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805860"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="91135-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="91135-102">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="91135-103">Słowo `out` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="91135-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="91135-104">Sprawia, że parametr formalny alias dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="91135-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="91135-105">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="91135-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="91135-106">Jest jak [ref](ref.md) słowa kluczowego, z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="91135-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="91135-107">Jest również jak [w](in-parameter-modifier.md) słowa `in` kluczowego, z tą różnicą, że nie zezwala na wywołaną metodę, aby zmodyfikować wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="91135-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="91135-108">Aby użyć `out` parametru, zarówno definicja metody, jak `out` i metoda wywołująca należy jawnie użyć słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="91135-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="91135-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="91135-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="91135-110">Słowo `out` kluczowe może być również używane z parametrem typu ogólnego, aby określić, że parametr typu jest kowariancją.</span><span class="sxs-lookup"><span data-stu-id="91135-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="91135-111">Aby uzyskać więcej informacji `out` na temat używania słowa kluczowego w tym kontekście, zobacz [out (Generic Modifier)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="91135-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="91135-112">Zmienne przekazywane `out` jako argumenty nie muszą być inicjowane przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="91135-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="91135-113">Jednak wywołana metoda jest wymagana do przypisania wartości przed zwracana metoda.</span><span class="sxs-lookup"><span data-stu-id="91135-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="91135-114">Programy `in` `ref`, `out` i słowa kluczowe nie są uważane za część podpisu metody w celu rozwiązania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="91135-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="91135-115">W związku z tym metody nie mogą być przeciążone, `in` jeśli jedyną `out` różnicą jest to, że jedna metoda przyjmuje `ref` argument lub, a druga przyjmuje argument.</span><span class="sxs-lookup"><span data-stu-id="91135-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="91135-116">Poniższy kod, na przykład, nie będzie kompilować:</span><span class="sxs-lookup"><span data-stu-id="91135-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="91135-117">Przeciążenie jest jednak legalne, jeśli `ref` `in`jedna `out` metoda przyjmuje argument , lub argument, a druga nie ma żadnego z tych modyfikatorów, takich jak ten:</span><span class="sxs-lookup"><span data-stu-id="91135-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="91135-118">Kompilator wybiera najlepsze przeciążenie, dopasowując modyfikatory parametrów w witrynie wywołania do modyfikatorów parametrów używanych w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="91135-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="91135-119">Właściwości nie są zmiennymi i dlatego `out` nie mogą być przekazywane jako parametry.</span><span class="sxs-lookup"><span data-stu-id="91135-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="91135-120">Nie można użyć `in`programu `ref`, `out` i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="91135-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="91135-121">Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](./async.md)</span><span class="sxs-lookup"><span data-stu-id="91135-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="91135-122">Metody iteratora, które zawierają `yield break` [zwrotu wydajności](./yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="91135-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="91135-123">Ponadto [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="91135-123">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="91135-124">Nie `out` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="91135-124">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="91135-125">Nie `ref` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia, gdy argument nie jest strukturą lub typem rodzajowym, który nie jest ograniczony do struktury.</span><span class="sxs-lookup"><span data-stu-id="91135-125">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="91135-126">Nie `in` można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="91135-126">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="91135-127">Słowo `in` kluczowe nie może być używane dla dowolnego typu rodzajowego, nawet jeśli jest ograniczona do struktury.</span><span class="sxs-lookup"><span data-stu-id="91135-127">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="91135-128">Deklarowanie `out` parametrów</span><span class="sxs-lookup"><span data-stu-id="91135-128">Declaring `out` parameters</span></span>

<span data-ttu-id="91135-129">Deklarowanie metody `out` z argumentami jest klasycznym obejściem, aby zwrócić wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="91135-129">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="91135-130">Począwszy od języka C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="91135-130">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="91135-131">Poniższy przykład `out` służy do zwrócenia trzech zmiennych za pomocą wywołania pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="91135-131">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="91135-132">Trzeci argument jest przypisany do null.</span><span class="sxs-lookup"><span data-stu-id="91135-132">The third argument is assigned to null.</span></span> <span data-ttu-id="91135-133">Dzięki temu metody do zwracania wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="91135-133">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="91135-134">Wywoływanie metody `out` z argumentem</span><span class="sxs-lookup"><span data-stu-id="91135-134">Calling a method with an `out` argument</span></span>

<span data-ttu-id="91135-135">W języku C# 6 i wcześniej należy zadeklarować zmienną w `out` osobnej instrukcji przed przekazaniem go jako argument.</span><span class="sxs-lookup"><span data-stu-id="91135-135">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="91135-136">Poniższy przykład deklaruje zmienną o nazwie, `number` zanim zostanie przekazana do metody [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) która próbuje przekonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="91135-136">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="91135-137">Począwszy od języka C# 7.0, można zadeklarować zmienną na `out` liście argumentów wywołania metody, a nie w deklaracji oddzielnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="91135-137">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="91135-138">Daje to bardziej kompaktowy, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="91135-138">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="91135-139">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że definiuje zmienną `number` w wywołaniu metody [Int32.TryParse.](xref:System.Int32.TryParse(System.String,System.Int32@))</span><span class="sxs-lookup"><span data-stu-id="91135-139">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="91135-140">W poprzednim przykładzie `number` zmienna jest silnie `int`wpisywany jako .</span><span class="sxs-lookup"><span data-stu-id="91135-140">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="91135-141">Można również zadeklarować niejawnie wpisaną zmienną lokalną, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="91135-141">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="91135-142">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="91135-142">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91135-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91135-143">See also</span></span>

- [<span data-ttu-id="91135-144">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="91135-144">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="91135-145">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="91135-145">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="91135-146">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="91135-146">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="91135-147">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="91135-147">Method Parameters</span></span>](./method-parameters.md)
