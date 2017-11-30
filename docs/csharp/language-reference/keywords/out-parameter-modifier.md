---
title: "out — Modyfikator parametrów (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="db133-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="db133-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="db133-103">`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="db133-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="db133-104">Przypomina to [ref](../../../csharp/language-reference/keywords/ref.md) — słowo kluczowe, z wyjątkiem `ref` wymaga zainicjowanej zmiennej przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="db133-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="db133-105">Aby użyć `out` jawnie należy użyć parametru definicję metody i wywołanie metody `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="db133-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="db133-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="db133-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="db133-107">`out` — Słowo kluczowe można również z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="db133-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="db133-108">Aby uzyskać więcej informacji dotyczących korzystania z `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="db133-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="db133-109">Zmienne przekazany jako `out` argumenty nie muszą zostać zainicjowany przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="db133-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="db133-110">Wywołana metoda jest jednak wymagana do przypisania wartości przed metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="db133-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="db133-111">Mimo że `ref` i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db133-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="db133-112">W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` argument i innych przyjmuje `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="db133-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="db133-113">Następujący kod, na przykład nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="db133-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="db133-114">Przeciążanie jest dozwolony, jednak jeśli jedna metoda przyjmuje `ref` lub `out` argument, a drugi używa ani w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="db133-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="db133-115">Właściwości nie są zmiennymi i nie można przekazać jako `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="db133-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="db133-116">Aby uzyskać informacje o przekazywanie tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="db133-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="db133-117">Nie można użyć `ref` i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="db133-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="db133-118">Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="db133-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="db133-119">Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="db133-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="db133-120">Deklarowanie `out` argumentów</span><span class="sxs-lookup"><span data-stu-id="db133-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="db133-121">Deklarowanie metodę o `out` argumentów jest przydatne, gdy ma metodę zwraca wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="db133-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="db133-122">W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z wywołaniem pojedynczej metody.</span><span class="sxs-lookup"><span data-stu-id="db133-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="db133-123">Należy pamiętać, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="db133-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="db133-124">Dzięki temu metody opcjonalnie zwracać wartości.</span><span class="sxs-lookup"><span data-stu-id="db133-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="db133-125">[Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` wskazująca, czy operacja powiodła się i nie powiodło się i zwracanie wartości utworzone przez operację w `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="db133-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="db133-126">Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="db133-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="db133-127">Wywoływanie metody z `out` argumentu</span><span class="sxs-lookup"><span data-stu-id="db133-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="db133-128">W języku C# 6 i starszych należy zadeklarować zmienną w oddzielną instrukcję przed przekazujesz ją jako `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="db133-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="db133-129">Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodę, która podejmuje próbę przekonwertowania ciągu na liczbę.</span><span class="sxs-lookup"><span data-stu-id="db133-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="db133-130">Począwszy od C# 7, mogą zadeklarować `out` zmiennej w liście argumentów w wywołaniu metody, a nie w oddzielnych deklaracja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="db133-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="db133-131">Tworzy mniejszych, który może zostać odczytany kodu i uniemożliwia także przypadkowo przypisywanie wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="db133-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="db133-132">Poniższy przykład jest tak jak w poprzednim przykładzie, ale definiuje `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="db133-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="db133-133">W poprzednim przykładzie `number` zmiennej jest silnie typizowane jako `int`.</span><span class="sxs-lookup"><span data-stu-id="db133-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="db133-134">Niejawnie wpisane zmienna lokalna może deklarować także, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="db133-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="db133-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db133-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db133-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db133-136">See Also</span></span>  
 [<span data-ttu-id="db133-137">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="db133-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="db133-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="db133-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db133-139">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="db133-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="db133-140">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="db133-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
