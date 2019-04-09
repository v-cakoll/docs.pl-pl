---
title: out — modyfikator parametrów - C# odwołania
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 769d1ac0b6266c87e99605c76a25e016f15eb11c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125756"
---
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
`out` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. To sprawia, że parametr formalny alias dla argumentu, który musi być zmienną. Innymi słowy żadnych operacji na parametr składa się od argumentu. Jest on podobny do [ref](ref.md) — słowo kluczowe, chyba że `ref` wymaga zainicjowanej zmiennej przed przekazaniem jej. Jest również, jak [w](in-parameter-modifier.md) — słowo kluczowe, chyba że `in` nie zezwala na o nazwie metody zmodyfikować wartość argumentu. Aby użyć `out` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `out` — słowo kluczowe. Na przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kowariantny. Aby uzyskać więcej informacji na temat użytkowania `out` — słowo kluczowe, w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).
  
Zmienne są przekazywane jako `out` argumentów nie muszą być zainicjowane przed przesłaniem w wywołaniu metody. Metoda wywoływana jest jednak wymagana do przypisania wartości przed powrotem z metody.  
  
`in`, `ref`, I `out` słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozwiązania przeciążenia. W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu. Poniższy kod, na przykład, nie zostanie skompilowany:  
  
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
  
Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
-   Metody asynchroniczne, które można zdefiniować przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
-   Metody iteratora, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

## <a name="declaring-out-parameters"></a>Deklarowanie `out` parametrów   

Deklarowanie metody z `out` argumentów jest klasycznego obejście zwracanie wielu wartości. Począwszy od C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy. W poniższym przykładzie użyto `out` do zwrócenia trzech zmiennych z pojedynczym wywołaniu metody. Należy pamiętać, że trzeci argument jest przypisany do wartości null. Umożliwia to metody zwrócić wartości opcjonalnie.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Wywołanie metody z `out` argumentu

W języku C# 6 i starszych musi zadeklarować zmienną w osobnych instrukcji, następnie przekazać go jako `out` argumentu. Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem jej do [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody, która stara się przekonwertować ciąg na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od języka C# 7.0, możesz zadeklarować `out` zmiennej na liście argumentów wywołania metody, a nie w oddzielnych deklaracji zmiennej. Generuje kod w bardziej zwarty, czytelne i uniemożliwia także przypadkowo przypisywania wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest podobnie jak w poprzednim przykładzie, z tą różnicą, że definiuje on `number` zmiennej w wywołaniu [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
W poprzednim przykładzie `number` zmienna jest silnie typizowane jako `int`. Można również zadeklarować niejawnie typizowanej zmiennej lokalnej, tak jak w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie w C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
