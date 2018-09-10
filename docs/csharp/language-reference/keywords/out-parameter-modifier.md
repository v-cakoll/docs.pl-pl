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
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Jest on podobny do [ref](ref.md) — słowo kluczowe, chyba że `ref` wymaga zainicjowanej zmiennej przed przekazaniem jej. Jest również, jak [w](in-parameter-modifier.md) — słowo kluczowe, chyba że `in` nie zezwala na o nazwie metody zmodyfikować wartość argumentu. Aby użyć `out` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `out` — słowo kluczowe. Na przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kowariantny. Aby uzyskać więcej informacji na temat użytkowania `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).
  
Zmienne są przekazywane jako `out` argumentów nie muszą być zainicjowane przed przesłaniem w wywołaniu metody. Metoda wywoływana jest jednak wymagana do przypisania wartości przed powrotem z metody.  
  
Mimo że `in`, `ref`, i `out` słowa kluczowe powodować różne zachowanie w czasie wykonywania, ich nie są uważane za część podpisu metody w czasie kompilacji. W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu. Poniższy kod, na przykład, nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążenie jest legalny, jest jednak, jeśli jedna metoda przyjmuje strukturę `ref`, `in`, lub `out` argument, a druga nie ma żadnego z tych modyfikatorów, następująco:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilator wybiera najlepsze przeciążenie, dopasowując Modyfikatory parametrów do lokacji wywołanie Modyfikatory parametrów używane w wywołaniu metody.
 
Właściwości nie są zmienne i nie można przekazać jako `out` parametrów.
  
 Aby uzyskać informacji na temat przekazywania tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
-   Metody asynchroniczne, które można zdefiniować przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
-   Metody iteratora, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

## <a name="declaring-out-arguments"></a>Deklarowanie `out` argumentów   

 Deklarowanie metody z `out` argumentów jest przydatne w przypadku, gdy chcesz, aby metoda zwracanie wielu wartości. W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z pojedynczym wywołaniu metody. Należy pamiętać, że trzeci argument jest przypisany do wartości null. Umożliwia to metody zwrócić wartości opcjonalnie.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 [Wzorzec spróbuj](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) obejmuje zwracanie `bool` aby wskazać, czy operacji zakończonych powodzeniem lub niepowodzeniem i zwracania wartości generowane przez operację w `out` argumentu. Liczba analizowania metod, takich jak [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metody, użyj tego wzorca.
   
## <a name="calling-a-method-with-an-out-argument"></a>Wywołanie metody z `out` argumentu

W języku C# 6 i starszych musi zadeklarować zmienną w osobnych instrukcji, następnie przekazać go jako `out` argumentu. Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem jej do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody, która stara się przekonwertować ciąg na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od języka C# 7.0, możesz zadeklarować `out` zmiennej na liście argumentów wywołania metody, a nie w oddzielnych deklaracji zmiennej. Generuje kod w bardziej zwarty, czytelne i uniemożliwia także przypadkowo przypisywania wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest podobnie jak w poprzednim przykładzie, z tą różnicą, że definiuje on `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
W poprzednim przykładzie `number` zmienna jest silnie typizowane jako `int`. Można również zadeklarować niejawnie typizowanej zmiennej lokalnej, tak jak w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
