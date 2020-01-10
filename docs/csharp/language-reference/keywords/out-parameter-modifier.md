---
title: modyfikator parametru out — C# odwołanie
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713271"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="33c27-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="33c27-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="33c27-103">Słowo kluczowe `out` powoduje, że argumenty są przekazane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="33c27-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="33c27-104">Sprawia, że parametr formalny jest aliasem dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="33c27-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="33c27-105">Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie.</span><span class="sxs-lookup"><span data-stu-id="33c27-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="33c27-106">Jest to podobne do słowa kluczowego [ref](ref.md) , z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="33c27-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="33c27-107">Jest on również podobny do słowa kluczowego [in](in-parameter-modifier.md) , z wyjątkiem tego, że `in` nie zezwala metodzie wywoływanej na modyfikowanie wartości argumentu.</span><span class="sxs-lookup"><span data-stu-id="33c27-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="33c27-108">Aby użyć parametru `out`, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie użyć słowa kluczowego `out`.</span><span class="sxs-lookup"><span data-stu-id="33c27-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="33c27-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="33c27-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="33c27-110">Za pomocą słowa kluczowego `out` można także użyć parametru typu ogólnego, aby określić, że parametr typu jest współwariantem.</span><span class="sxs-lookup"><span data-stu-id="33c27-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="33c27-111">Aby uzyskać więcej informacji na temat używania słowa kluczowego `out` w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="33c27-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="33c27-112">Zmienne przekazane jako argumenty `out` nie muszą być inicjowane przed przekazywaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="33c27-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="33c27-113">Jednak wywoływana metoda jest wymagana do przypisania wartości przed zwróceniem metody.</span><span class="sxs-lookup"><span data-stu-id="33c27-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="33c27-114">Słowa kluczowe `in`, `ref`i `out` nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="33c27-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="33c27-115">W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda przyjmuje argument `ref` lub `in`, a drugi przyjmuje argument `out`.</span><span class="sxs-lookup"><span data-stu-id="33c27-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="33c27-116">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="33c27-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="33c27-117">Przeciążanie jest dozwolone, jednak jeśli jedna metoda przyjmuje argument `ref`, `in`lub `out`, a drugi nie ma żadnego z tych modyfikatorów, takich jak:</span><span class="sxs-lookup"><span data-stu-id="33c27-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="33c27-118">Kompilator wybiera najlepsze Przeciążenie przez dopasowanie modyfikatorów parametrów w miejscu wywołania do modyfikatorów parametrów używanych w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="33c27-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="33c27-119">Właściwości nie są zmiennymi i w związku z tym nie można ich przekazywać jako parametrów `out`.</span><span class="sxs-lookup"><span data-stu-id="33c27-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="33c27-120">Nie można użyć słów kluczowych `in`, `ref`i `out` dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="33c27-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="33c27-121">Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](./async.md) .</span><span class="sxs-lookup"><span data-stu-id="33c27-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="33c27-122">Metody iteratorów, które zawierają instrukcję [yield return](./yield.md) lub `yield break`.</span><span class="sxs-lookup"><span data-stu-id="33c27-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="33c27-123">Deklarowanie parametrów `out`</span><span class="sxs-lookup"><span data-stu-id="33c27-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="33c27-124">Deklarowanie metody z argumentami `out` jest klasycznym obejściem do zwrócenia wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="33c27-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="33c27-125">Począwszy od C# 7,0, rozważ zastosowanie [krotek](../../tuples.md) dla podobnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="33c27-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="33c27-126">Poniższy przykład używa `out`, aby zwrócić trzy zmienne z pojedynczym wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="33c27-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="33c27-127">Zwróć uwagę, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="33c27-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="33c27-128">Dzięki temu metody mogą zwracać wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="33c27-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="33c27-129">Wywoływanie metody z argumentem `out`</span><span class="sxs-lookup"><span data-stu-id="33c27-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="33c27-130">W C# 6 i wcześniejszych wersjach należy zadeklarować zmienną w oddzielnej instrukcji przed przekazaniem jej jako argumentu `out`.</span><span class="sxs-lookup"><span data-stu-id="33c27-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="33c27-131">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , która próbuje skonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="33c27-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="33c27-132">Począwszy od C# 7,0, można zadeklarować zmienną `out` na liście argumentów wywołania metody, a nie w oddzielnej deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="33c27-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="33c27-133">Daje to bardziej zwarty, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="33c27-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="33c27-134">Poniższy przykład przypomina poprzedni przykład, z tą różnicą, że definiuje zmienną `number` w wywołaniu metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .</span><span class="sxs-lookup"><span data-stu-id="33c27-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="33c27-135">W poprzednim przykładzie zmienna `number` jest silnie wpisana jako `int`.</span><span class="sxs-lookup"><span data-stu-id="33c27-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="33c27-136">Można również zadeklarować niejawnie wpisaną zmienną lokalną, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="33c27-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="33c27-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33c27-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33c27-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33c27-138">See also</span></span>

- [<span data-ttu-id="33c27-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33c27-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="33c27-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33c27-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="33c27-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="33c27-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="33c27-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="33c27-142">Method Parameters</span></span>](./method-parameters.md)
