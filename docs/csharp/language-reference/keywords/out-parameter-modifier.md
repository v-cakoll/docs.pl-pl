---
title: out — Modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: c9fb03560e30bab3cc71a6171c731d887e859f6c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138880"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="99457-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="99457-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="99457-103">`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="99457-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="99457-104">Jest on podobny do [ref](ref.md) — słowo kluczowe, chyba że `ref` wymaga zainicjowanej zmiennej przed przekazaniem jej.</span><span class="sxs-lookup"><span data-stu-id="99457-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="99457-105">Jest również, jak [w](in-parameter-modifier.md) — słowo kluczowe, chyba że `in` nie zezwala na o nazwie metody zmodyfikować wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="99457-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="99457-106">Aby użyć `out` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="99457-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="99457-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="99457-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="99457-108">`out` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="99457-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="99457-109">Aby uzyskać więcej informacji na temat użytkowania `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="99457-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="99457-110">Zmienne są przekazywane jako `out` argumentów nie muszą być zainicjowane przed przesłaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="99457-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="99457-111">Metoda wywoływana jest jednak wymagana do przypisania wartości przed powrotem z metody.</span><span class="sxs-lookup"><span data-stu-id="99457-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="99457-112">Mimo że `in`, `ref`, i `out` słowa kluczowe powodować różne zachowanie w czasie wykonywania, ich nie są uważane za część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="99457-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="99457-113">W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="99457-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="99457-114">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="99457-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="99457-115">Przeciążenie jest legalny, jest jednak, jeśli jedna metoda przyjmuje strukturę `ref`, `in`, lub `out` argument, a druga nie ma żadnego z tych modyfikatorów, następująco:</span><span class="sxs-lookup"><span data-stu-id="99457-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="99457-116">Kompilator wybiera najlepsze przeciążenie, dopasowując Modyfikatory parametrów do lokacji wywołanie Modyfikatory parametrów używane w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="99457-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="99457-117">Właściwości nie są zmienne i nie można przekazać jako `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="99457-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="99457-118">Aby uzyskać informacji na temat przekazywania tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="99457-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="99457-119">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="99457-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="99457-120">Metody asynchroniczne, które można zdefiniować przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="99457-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="99457-121">Metody iteratora, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99457-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="99457-122">Deklarowanie `out` argumentów</span><span class="sxs-lookup"><span data-stu-id="99457-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="99457-123">Deklarowanie metody z `out` argumentów jest przydatne w przypadku, gdy chcesz, aby metoda zwracanie wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="99457-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="99457-124">W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z pojedynczym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="99457-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="99457-125">Należy pamiętać, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="99457-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="99457-126">Umożliwia to metody zwrócić wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="99457-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="99457-127">[Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` aby wskazać, czy operacji zakończonych powodzeniem lub niepowodzeniem i zwracania wartości generowane przez operację w `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="99457-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded or failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="99457-128">Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="99457-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="99457-129">Wywołanie metody z `out` argumentu</span><span class="sxs-lookup"><span data-stu-id="99457-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="99457-130">W języku C# 6 i starszych musi zadeklarować zmienną w osobnych instrukcji, następnie przekazać go jako `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="99457-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="99457-131">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem jej do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody, która stara się przekonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="99457-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="99457-132">Począwszy od języka C# 7.0, możesz zadeklarować `out` zmiennej na liście argumentów wywołania metody, a nie w oddzielnych deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99457-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="99457-133">Generuje kod w bardziej zwarty, czytelne i uniemożliwia także przypadkowo przypisywania wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="99457-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="99457-134">Poniższy przykład jest podobnie jak w poprzednim przykładzie, z tą różnicą, że definiuje on `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="99457-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="99457-135">W poprzednim przykładzie `number` zmienna jest silnie typizowane jako `int`.</span><span class="sxs-lookup"><span data-stu-id="99457-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="99457-136">Można również zadeklarować niejawnie typizowanej zmiennej lokalnej, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="99457-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="99457-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99457-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99457-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99457-138">See Also</span></span>

- [<span data-ttu-id="99457-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99457-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="99457-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="99457-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="99457-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="99457-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="99457-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="99457-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
