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
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Przypomina to [ref](ref.md) — słowo kluczowe, z wyjątkiem `ref` wymaga zainicjowanej zmiennej przed przekazaniem. Istnieje również tak samo, jak [w](in-parameter-modifier.md) — słowo kluczowe, z wyjątkiem `in` wywołaną metodę zmodyfikować wartość argumentu nie jest możliwe. Aby użyć `out` jawnie należy użyć parametru definicję metody i wywołanie metody `out` — słowo kluczowe. Na przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` — Słowo kluczowe można również z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny. Aby uzyskać więcej informacji dotyczących korzystania z `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).
  
Zmienne przekazany jako `out` argumenty nie muszą zostać zainicjowany przed przekazaniem w wywołaniu metody. Wywołana metoda jest jednak wymagana do przypisania wartości przed metoda zwraca.  
  
Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji. W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu. Następujący kod, na przykład nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążanie jest dozwolony, jednak jeśli jedna metoda przyjmuje `ref`, `in`, lub `out` argument, a druga ma żadna z tych Modyfikatory następująco:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilator wybiera najlepsze przeciążenie przez dopasowanie modyfikatorów parametrów w tej lokacji wywołania modyfikatorów parametrów używane w wywołaniu metody.
 
Właściwości nie są zmiennymi i nie można przekazać jako `out` parametrów.
  
 Aby uzyskać informacje o przekazywanie tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
-   Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
-   Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

## <a name="declaring-out-arguments"></a>Deklarowanie `out` argumentów   

 Deklarowanie metodę o `out` argumentów jest przydatne, gdy ma metodę zwraca wiele wartości. W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z wywołaniem pojedynczej metody. Należy pamiętać, że trzeci argument jest przypisany do wartości null. Dzięki temu metody opcjonalnie zwracać wartości.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 [Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` wskazująca, czy operacja powiodła się i nie powiodło się i zwracanie wartości utworzone przez operację w `out` argumentu. Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.
   
## <a name="calling-a-method-with-an-out-argument"></a>Wywoływanie metody z `out` argumentu

W języku C# 6 i starszych należy zadeklarować zmienną w oddzielną instrukcję przed przekazujesz ją jako `out` argumentu. Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodę, która podejmuje próbę przekonwertowania ciągu na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od wersji 7.0 C#, mogą zadeklarować `out` zmiennej w liście argumentów w wywołaniu metody, a nie w oddzielnych deklaracja zmiennej. Tworzy mniejszych, który może zostać odczytany kodu i uniemożliwia także przypadkowo przypisywanie wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest tak jak w poprzednim przykładzie, ale definiuje `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
W poprzednim przykładzie `number` zmiennej jest silnie typizowane jako `int`. Niejawnie wpisane zmienna lokalna może deklarować także, tak jak w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
