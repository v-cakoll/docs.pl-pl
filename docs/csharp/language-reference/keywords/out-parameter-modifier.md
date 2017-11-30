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
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Przypomina to [ref](../../../csharp/language-reference/keywords/ref.md) — słowo kluczowe, z wyjątkiem `ref` wymaga zainicjowanej zmiennej przed przekazaniem. Aby użyć `out` jawnie należy użyć parametru definicję metody i wywołanie metody `out` — słowo kluczowe. Na przykład:  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> `out` — Słowo kluczowe można również z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny. Aby uzyskać więcej informacji dotyczących korzystania z `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](../../../csharp/language-reference/keywords/out-generic-modifier.md).
  
 Zmienne przekazany jako `out` argumenty nie muszą zostać zainicjowany przed przekazaniem w wywołaniu metody. Wywołana metoda jest jednak wymagana do przypisania wartości przed metoda zwraca.  
  
 Mimo że `ref` i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji. W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` argument i innych przyjmuje `out` argumentu. Następujący kod, na przykład nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążanie jest dozwolony, jednak jeśli jedna metoda przyjmuje `ref` lub `out` argument, a drugi używa ani w następujący sposób:  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 Właściwości nie są zmiennymi i nie można przekazać jako `out` parametrów.  
  
 Aby uzyskać informacje o przekazywanie tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nie można użyć `ref` i `out` słowa kluczowe dla następujących rodzajów metod:  
  
-   Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
-   Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

## <a name="declaring-out-arguments"></a>Deklarowanie `out` argumentów   

 Deklarowanie metodę o `out` argumentów jest przydatne, gdy ma metodę zwraca wiele wartości. W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z wywołaniem pojedynczej metody. Należy pamiętać, że trzeci argument jest przypisany do wartości null. Dzięki temu metody opcjonalnie zwracać wartości.  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 [Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` wskazująca, czy operacja powiodła się i nie powiodło się i zwracanie wartości utworzone przez operację w `out` argumentu. Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.
   
## <a name="calling-a-method-with-an-out-argument"></a>Wywoływanie metody z `out` argumentu

W języku C# 6 i starszych należy zadeklarować zmienną w oddzielną instrukcję przed przekazujesz ją jako `out` argumentu. Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodę, która podejmuje próbę przekonwertowania ciągu na liczbę.

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

Począwszy od C# 7, mogą zadeklarować `out` zmiennej w liście argumentów w wywołaniu metody, a nie w oddzielnych deklaracja zmiennej. Tworzy mniejszych, który może zostać odczytany kodu i uniemożliwia także przypadkowo przypisywanie wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest tak jak w poprzednim przykładzie, ale definiuje `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
W poprzednim przykładzie `number` zmiennej jest silnie typizowane jako `int`. Niejawnie wpisane zmienna lokalna może deklarować także, tak jak w poniższym przykładzie.

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
