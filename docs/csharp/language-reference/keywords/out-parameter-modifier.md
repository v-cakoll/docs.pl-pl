---
title: modyfikator parametrów out - Odwołanie do języka C#
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f963188d77685bb81f7dc9fb3794e343114fe3c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173565"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="d1e3d-102">out — Modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d1e3d-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="d1e3d-103">Słowo `out` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="d1e3d-104">To sprawia, że formalny parametr alias dla argumentu, który musi być zmienna.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="d1e3d-105">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="d1e3d-106">Jest jak [ref](ref.md) słowo kluczowe, z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed jej przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="d1e3d-107">Jest również jak [w](in-parameter-modifier.md) słowa `in` kluczowego, z wyjątkiem, że nie zezwala wywoływana metoda do modyfikowania wartości argumentu.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="d1e3d-108">Aby użyć `out` parametru, zarówno definicji metody, jak i `out` metody wywołującej należy jawnie użyć słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="d1e3d-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d1e3d-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="d1e3d-110">Słowo `out` kluczowe może być również używane z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="d1e3d-111">Aby uzyskać więcej informacji `out` na temat użycia słowa kluczowego w tym kontekście, zobacz [(Modyfikator ogólny)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d1e3d-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="d1e3d-112">Zmienne przekazywane `out` jako argumenty nie muszą być inicjowane przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="d1e3d-113">Jednak wywoływana metoda jest wymagana do przypisania wartości przed zwracaniem metody.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="d1e3d-114">Słowa `in` `ref`kluczowe `out` , i słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="d1e3d-115">W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda ma `ref` lub `in` argument, a druga przyjmuje argument. `out`</span><span class="sxs-lookup"><span data-stu-id="d1e3d-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="d1e3d-116">Poniższy kod, na przykład, nie skompiluje:</span><span class="sxs-lookup"><span data-stu-id="d1e3d-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="d1e3d-117">Przeciążenie jest legalne, jednak, `ref`jeśli `in`jedna `out` metoda ma , lub argument, a druga nie ma żadnego z tych modyfikatorów, jak to:</span><span class="sxs-lookup"><span data-stu-id="d1e3d-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="d1e3d-118">Kompilator wybiera najlepsze przeciążenie, dopasowując modyfikatory parametrów w witrynie wywołania do modyfikatorów parametrów używanych w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="d1e3d-119">Właściwości nie są zmienne i dlatego `out` nie mogą być przekazywane jako parametry.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="d1e3d-120">Nie można używać `in`słów `ref` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="d1e3d-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="d1e3d-121">Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](./async.md)</span><span class="sxs-lookup"><span data-stu-id="d1e3d-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="d1e3d-122">Metody iterator, które obejmują zwrot `yield break` [uchylić](./yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="d1e3d-123">Deklarowanie `out` parametrów</span><span class="sxs-lookup"><span data-stu-id="d1e3d-123">Declaring `out` parameters</span></span>

<span data-ttu-id="d1e3d-124">Deklarowanie metody `out` z argumentami jest klasycznym obejściem zwracającym wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="d1e3d-125">Począwszy od języka C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="d1e3d-126">W poniższym `out` przykładzie użyto do zwrócenia trzech zmiennych z wywołaniem jednej metody.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="d1e3d-127">Należy zauważyć, że trzeci argument jest przypisany do wartości null.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="d1e3d-128">Dzięki temu metody do zwracania wartości opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="d1e3d-129">Wywoływanie metody `out` z argumentem</span><span class="sxs-lookup"><span data-stu-id="d1e3d-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="d1e3d-130">W języku C# 6 i wcześniejszych, należy zadeklarować zmienną `out` w oddzielnej instrukcji przed przekazaniem go jako argument.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="d1e3d-131">W poniższym przykładzie zadeklarowano zmienną o nazwie `number` przed przekazaniem do Metody [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) która próbuje przekonwertować ciąg na liczbę.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="d1e3d-132">Począwszy od języka C# 7.0, można zadeklarować `out` zmienną na liście argumentów wywołania metody, a nie w deklaracji zmiennej oddzielnej.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="d1e3d-133">Daje to bardziej kompaktowy, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="d1e3d-134">Poniższy przykład jest podobny do poprzedniego przykładu, `number` z tą różnicą, że definiuje zmienną w wywołaniu [Metody Int32.TryParse.](xref:System.Int32.TryParse(System.String,System.Int32@))</span><span class="sxs-lookup"><span data-stu-id="d1e3d-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="d1e3d-135">W poprzednim przykładzie `number` zmienna jest silnie `int`wpisana jako .</span><span class="sxs-lookup"><span data-stu-id="d1e3d-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="d1e3d-136">Można również zadeklarować niejawnie wpisaną zmienną lokalną, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1e3d-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="d1e3d-137">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d1e3d-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1e3d-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1e3d-138">See also</span></span>

- [<span data-ttu-id="d1e3d-139">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="d1e3d-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d1e3d-140">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d1e3d-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d1e3d-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d1e3d-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d1e3d-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="d1e3d-142">Method Parameters</span></span>](./method-parameters.md)
