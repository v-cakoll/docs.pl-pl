---
title: out — modyfikator parametrów - C# odwołania
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 769d1ac0b6266c87e99605c76a25e016f15eb11c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125756"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="c9c1e-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c9c1e-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="c9c1e-103">`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="c9c1e-104">To sprawia, że parametr formalny alias dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="c9c1e-105">Innymi słowy żadnych operacji na parametr składa się od argumentu.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="c9c1e-106">Jest on podobny do [ref](ref.md) — słowo kluczowe, chyba że `ref` wymaga zainicjowanej zmiennej przed przekazaniem jej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="c9c1e-107">Jest również, jak [w](in-parameter-modifier.md) — słowo kluczowe, chyba że `in` nie zezwala na o nazwie metody zmodyfikować wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="c9c1e-108">Aby użyć `out` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="c9c1e-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c9c1e-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="c9c1e-110">`out` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="c9c1e-111">Aby uzyskać więcej informacji na temat użytkowania `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="c9c1e-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="c9c1e-112">Zmienne są przekazywane jako `out` argumentów nie muszą być zainicjowane przed przesłaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="c9c1e-113">Metoda wywoływana jest jednak wymagana do przypisania wartości przed powrotem z metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="c9c1e-114">`in`, `ref`, I `out` słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozwiązania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="c9c1e-115">W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="c9c1e-116">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="c9c1e-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="c9c1e-117">Przeciążenie jest legalny, jest jednak, jeśli jedna metoda przyjmuje strukturę `ref`, `in`, lub `out` argument, a druga nie ma żadnego z tych modyfikatorów, następująco:</span><span class="sxs-lookup"><span data-stu-id="c9c1e-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="c9c1e-118">Kompilator wybiera najlepsze przeciążenie, dopasowując Modyfikatory parametrów do lokacji wywołanie Modyfikatory parametrów używane w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="c9c1e-119">Właściwości nie są zmienne i nie można przekazać jako `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="c9c1e-120">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="c9c1e-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="c9c1e-121">Metody asynchroniczne, które można zdefiniować przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-121">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="c9c1e-122">Metody iteratora, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-122">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="c9c1e-123">Deklarowanie `out` parametrów</span><span class="sxs-lookup"><span data-stu-id="c9c1e-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="c9c1e-124">Deklarowanie metody z `out` argumentów jest klasycznego obejście zwracanie wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="c9c1e-125">Począwszy od C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="c9c1e-126">W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z pojedynczym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="c9c1e-127">Należy pamiętać, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="c9c1e-128">Umożliwia to metody zwrócić wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="c9c1e-129">Wywołanie metody z `out` argumentu</span><span class="sxs-lookup"><span data-stu-id="c9c1e-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="c9c1e-130">W języku C# 6 i starszych musi zadeklarować zmienną w osobnych instrukcji, następnie przekazać go jako `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="c9c1e-131">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem jej do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody, która stara się przekonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="c9c1e-132">Począwszy od języka C# 7.0, możesz zadeklarować `out` zmiennej na liście argumentów wywołania metody, a nie w oddzielnych deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="c9c1e-133">Generuje kod w bardziej zwarty, czytelne i uniemożliwia także przypadkowo przypisywania wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="c9c1e-134">Poniższy przykład jest podobnie jak w poprzednim przykładzie, z tą różnicą, że definiuje on `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="c9c1e-135">W poprzednim przykładzie `number` zmienna jest silnie typizowane jako `int`.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="c9c1e-136">Można również zadeklarować niejawnie typizowanej zmiennej lokalnej, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c9c1e-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="c9c1e-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9c1e-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c9c1e-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9c1e-138">See also</span></span>

- [<span data-ttu-id="c9c1e-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9c1e-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c9c1e-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9c1e-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c9c1e-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c9c1e-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="c9c1e-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="c9c1e-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
