---
title: modyfikator parametru out — odwołanie w C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 30946c85d2b64ead3f42e03da61108fa5b367779
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174812"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="dfebe-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dfebe-102">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="dfebe-103">`out`Słowo kluczowe powoduje, że argumenty są przekazane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="dfebe-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="dfebe-104">Sprawia, że parametr formalny jest aliasem dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="dfebe-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="dfebe-105">Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie.</span><span class="sxs-lookup"><span data-stu-id="dfebe-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="dfebe-106">Jest to podobne do słowa kluczowego [ref](ref.md) , z wyjątkiem tego, że `ref` wymaga, aby zmienna została zainicjowana przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="dfebe-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="dfebe-107">Jest on również podobny do słowa kluczowego [in](in-parameter-modifier.md) , z wyjątkiem tego, że `in` wywołana metoda nie zezwala na modyfikowanie wartości argumentu.</span><span class="sxs-lookup"><span data-stu-id="dfebe-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="dfebe-108">Aby użyć `out` parametru, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie użyć `out` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="dfebe-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="dfebe-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="dfebe-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="dfebe-110">`out`Słowo kluczowe może być również używane z parametrem typu ogólnego, aby określić, że parametr typu jest współvariant.</span><span class="sxs-lookup"><span data-stu-id="dfebe-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="dfebe-111">Aby uzyskać więcej informacji na temat używania `out` słowa kluczowego w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="dfebe-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="dfebe-112">Zmienne przekazane jako `out` argumenty nie muszą być inicjowane przed przekazywaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="dfebe-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="dfebe-113">Jednak wywoływana metoda jest wymagana do przypisania wartości przed zwróceniem metody.</span><span class="sxs-lookup"><span data-stu-id="dfebe-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="dfebe-114">`in` `ref` Słowa kluczowe, i `out` nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="dfebe-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="dfebe-115">W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` argument lub, `in` a druga przyjmuje `out` argument.</span><span class="sxs-lookup"><span data-stu-id="dfebe-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="dfebe-116">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="dfebe-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="dfebe-117">Przeciążanie jest dozwolone, jednak jeśli jedna metoda przyjmuje `ref` `in` argument, lub, `out` a drugi nie ma żadnego z tych modyfikatorów, takich jak:</span><span class="sxs-lookup"><span data-stu-id="dfebe-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="dfebe-118">Kompilator wybiera najlepsze Przeciążenie przez dopasowanie modyfikatorów parametrów w miejscu wywołania do modyfikatorów parametrów używanych w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="dfebe-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="dfebe-119">Właściwości nie są zmiennymi i w związku z tym nie można ich przesłać jako `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="dfebe-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="dfebe-120">Nie można używać `in` `ref` słów kluczowych, i `out` dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="dfebe-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="dfebe-121">Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](./async.md) .</span><span class="sxs-lookup"><span data-stu-id="dfebe-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="dfebe-122">Metody iteratorów, które zawierają instrukcję [yield return](./yield.md) lub `yield break` .</span><span class="sxs-lookup"><span data-stu-id="dfebe-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="dfebe-123">Ponadto [metody rozszerzające](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfebe-123">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="dfebe-124">`out`Nie można użyć słowa kluczowego dla pierwszego argumentu metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="dfebe-124">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="dfebe-125">`ref`Nie można użyć słowa kluczowego dla pierwszego argumentu metody rozszerzenia, jeśli argument nie jest strukturą lub typ ogólny nie jest ograniczony do struktury.</span><span class="sxs-lookup"><span data-stu-id="dfebe-125">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="dfebe-126">`in`Nie można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="dfebe-126">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="dfebe-127">`in`Nie można użyć słowa kluczowego w żadnym typie ogólnym, nawet jeśli jest to struktura.</span><span class="sxs-lookup"><span data-stu-id="dfebe-127">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="dfebe-128">Deklarowanie `out` parametrów</span><span class="sxs-lookup"><span data-stu-id="dfebe-128">Declaring `out` parameters</span></span>

<span data-ttu-id="dfebe-129">Deklarowanie metody z `out` argumentami jest klasycznym obejściem do zwrócenia wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="dfebe-129">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="dfebe-130">Począwszy od języka C# 7,0, należy wziąć pod uwagę [krotki wartości](../builtin-types/value-tuples.md) dla podobnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="dfebe-130">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="dfebe-131">Poniższy przykład używa `out` do zwracania trzech zmiennych z pojedynczym wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="dfebe-131">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="dfebe-132">Trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="dfebe-132">The third argument is assigned to null.</span></span> <span data-ttu-id="dfebe-133">Dzięki temu metody mogą zwracać wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="dfebe-133">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="dfebe-134">Wywoływanie metody z `out` argumentem</span><span class="sxs-lookup"><span data-stu-id="dfebe-134">Calling a method with an `out` argument</span></span>

<span data-ttu-id="dfebe-135">W języku C# 6 i wcześniejszych należy zadeklarować zmienną w oddzielnej instrukcji przed przekazaniem jej jako `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="dfebe-135">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="dfebe-136">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , która próbuje skonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="dfebe-136">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="dfebe-137">Począwszy od języka C# 7,0, można zadeklarować `out` zmienną na liście argumentów wywołania metody, a nie w oddzielnej deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dfebe-137">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="dfebe-138">Daje to bardziej zwarty, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="dfebe-138">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="dfebe-139">Poniższy przykład przypomina poprzedni przykład, z tą różnicą, że definiuje `number` zmienną w wywołaniu metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .</span><span class="sxs-lookup"><span data-stu-id="dfebe-139">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="dfebe-140">W poprzednim przykładzie `number` zmienna jest silnie wpisana jako `int` .</span><span class="sxs-lookup"><span data-stu-id="dfebe-140">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="dfebe-141">Można również zadeklarować niejawnie wpisaną zmienną lokalną, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dfebe-141">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="dfebe-142">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dfebe-142">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dfebe-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfebe-143">See also</span></span>

- [<span data-ttu-id="dfebe-144">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="dfebe-144">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfebe-145">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dfebe-145">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfebe-146">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dfebe-146">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="dfebe-147">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="dfebe-147">Method Parameters</span></span>](./method-parameters.md)
