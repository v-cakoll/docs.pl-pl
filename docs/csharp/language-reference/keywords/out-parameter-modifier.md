---
title: out — Modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 052416f97c1fe9ed3aa1a3bafa7410e602096991
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="7f545-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7f545-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="7f545-103">`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7f545-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="7f545-104">Przypomina to [ref](ref.md) — słowo kluczowe, z wyjątkiem `ref` wymaga zainicjowanej zmiennej przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="7f545-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="7f545-105">Istnieje również tak samo, jak [w](in-parameter-modifier.md) — słowo kluczowe, z wyjątkiem `in` wywołaną metodę zmodyfikować wartość argumentu nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="7f545-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="7f545-106">Aby użyć `out` jawnie należy użyć parametru definicję metody i wywołanie metody `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="7f545-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="7f545-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f545-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="7f545-108">`out` — Słowo kluczowe można również z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="7f545-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="7f545-109">Aby uzyskać więcej informacji dotyczących korzystania z `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="7f545-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="7f545-110">Zmienne przekazany jako `out` argumenty nie muszą zostać zainicjowany przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="7f545-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="7f545-111">Wywołana metoda jest jednak wymagana do przypisania wartości przed metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="7f545-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="7f545-112">Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7f545-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="7f545-113">W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7f545-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="7f545-114">Następujący kod, na przykład nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="7f545-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="7f545-115">Przeciążanie jest dozwolony, jednak jeśli jedna metoda przyjmuje `ref`, `in`, lub `out` argument, a druga ma żadna z tych Modyfikatory następująco:</span><span class="sxs-lookup"><span data-stu-id="7f545-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="7f545-116">Kompilator wybiera najlepsze przeciążenie przez dopasowanie modyfikatorów parametrów w tej lokacji wywołania modyfikatorów parametrów używane w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="7f545-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="7f545-117">Właściwości nie są zmiennymi i nie można przekazać jako `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f545-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="7f545-118">Aby uzyskać informacje o przekazywanie tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="7f545-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="7f545-119">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="7f545-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="7f545-120">Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="7f545-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="7f545-121">Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7f545-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="7f545-122">Deklarowanie `out` argumentów</span><span class="sxs-lookup"><span data-stu-id="7f545-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="7f545-123">Deklarowanie metodę o `out` argumentów jest przydatne, gdy ma metodę zwraca wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="7f545-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="7f545-124">W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z wywołaniem pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="7f545-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="7f545-125">Należy pamiętać, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="7f545-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="7f545-126">Dzięki temu metody opcjonalnie zwracać wartości.</span><span class="sxs-lookup"><span data-stu-id="7f545-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="7f545-127">[Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` wskazująca, czy operacja powiodła się i nie powiodło się i zwracanie wartości utworzone przez operację w `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7f545-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="7f545-128">Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="7f545-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="7f545-129">Wywoływanie metody z `out` argumentu</span><span class="sxs-lookup"><span data-stu-id="7f545-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="7f545-130">W języku C# 6 i starszych należy zadeklarować zmienną w oddzielną instrukcję przed przekazujesz ją jako `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7f545-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="7f545-131">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodę, która podejmuje próbę przekonwertowania ciągu na liczbę.</span><span class="sxs-lookup"><span data-stu-id="7f545-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="7f545-132">Począwszy od wersji 7.0 C#, mogą zadeklarować `out` zmiennej w liście argumentów w wywołaniu metody, a nie w oddzielnych deklaracja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7f545-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="7f545-133">Tworzy mniejszych, który może zostać odczytany kodu i uniemożliwia także przypadkowo przypisywanie wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="7f545-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="7f545-134">Poniższy przykład jest tak jak w poprzednim przykładzie, ale definiuje `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="7f545-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="7f545-135">W poprzednim przykładzie `number` zmiennej jest silnie typizowane jako `int`.</span><span class="sxs-lookup"><span data-stu-id="7f545-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="7f545-136">Niejawnie wpisane zmienna lokalna może deklarować także, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7f545-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="7f545-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7f545-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f545-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f545-138">See Also</span></span>  
 [<span data-ttu-id="7f545-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="7f545-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f545-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7f545-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f545-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7f545-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7f545-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="7f545-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
