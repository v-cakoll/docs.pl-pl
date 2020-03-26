---
title: modyfikator parametrów out - Odwołanie do języka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: c713aa929673e51e8e9986c536bae782121c7756
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249347"
---
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
Słowo `out` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie. Sprawia, że parametr formalny alias dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametr jest na argument. Jest jak [ref](ref.md) słowa kluczowego, z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed przekazaniem. Jest również jak [w](in-parameter-modifier.md) słowa `in` kluczowego, z tą różnicą, że nie zezwala na wywołaną metodę, aby zmodyfikować wartość argumentu. Aby użyć `out` parametru, zarówno definicja metody, jak `out` i metoda wywołująca należy jawnie użyć słowa kluczowego. Przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> Słowo `out` kluczowe może być również używane z parametrem typu ogólnego, aby określić, że parametr typu jest kowariancją. Aby uzyskać więcej informacji `out` na temat używania słowa kluczowego w tym kontekście, zobacz [out (Generic Modifier)](out-generic-modifier.md).
  
Zmienne przekazywane `out` jako argumenty nie muszą być inicjowane przed przekazaniem w wywołaniu metody. Jednak wywołana metoda jest wymagana do przypisania wartości przed zwracana metoda.  
  
Programy `in` `ref`, `out` i słowa kluczowe nie są uważane za część podpisu metody w celu rozwiązania przeciążenia. W związku z tym metody nie mogą być przeciążone, `in` jeśli jedyną `out` różnicą jest to, że jedna metoda przyjmuje `ref` argument lub, a druga przyjmuje argument. Poniższy kod, na przykład, nie będzie kompilować:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążenie jest jednak legalne, jeśli `ref` `in`jedna `out` metoda przyjmuje argument , lub argument, a druga nie ma żadnego z tych modyfikatorów, takich jak ten:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilator wybiera najlepsze przeciążenie, dopasowując modyfikatory parametrów w witrynie wywołania do modyfikatorów parametrów używanych w wywołaniu metody.

Właściwości nie są zmiennymi i dlatego `out` nie mogą być przekazywane jako parametry.
  
Nie można użyć `in`programu `ref`, `out` i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](./async.md)  
  
- Metody iteratora, które zawierają `yield break` [zwrotu wydajności](./yield.md) lub instrukcji.  

Ponadto [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:

- Nie `out` można użyć klucza klucza w pierwszym argumencie metody rozszerzenia.
- Nie `ref` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia, gdy argument nie jest strukturą lub typem rodzajowym, który nie jest ograniczony do struktury.
- Nie `in` można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą. Słowo `in` kluczowe nie może być używane dla dowolnego typu rodzajowego, nawet jeśli jest ograniczona do struktury.

## <a name="declaring-out-parameters"></a>Deklarowanie `out` parametrów

Deklarowanie metody `out` z argumentami jest klasycznym obejściem, aby zwrócić wiele wartości. Począwszy od języka C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy. Poniższy przykład `out` służy do zwrócenia trzech zmiennych za pomocą wywołania pojedynczej metody. Należy zauważyć, że trzeci argument jest przypisany do wartości null. Dzięki temu metody do zwracania wartości opcjonalnie.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Wywoływanie metody `out` z argumentem

W języku C# 6 i wcześniej należy zadeklarować zmienną w `out` osobnej instrukcji przed przekazaniem go jako argument. Poniższy przykład deklaruje zmienną o nazwie, `number` zanim zostanie przekazana do metody [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) która próbuje przekonwertować ciąg na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od języka C# 7.0, można zadeklarować zmienną na `out` liście argumentów wywołania metody, a nie w deklaracji oddzielnej zmiennej. Daje to bardziej kompaktowy, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że definiuje zmienną `number` w wywołaniu metody [Int32.TryParse.](xref:System.Int32.TryParse(System.String,System.Int32@))

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

W poprzednim przykładzie `number` zmienna jest silnie `int`wpisywany jako . Można również zadeklarować niejawnie wpisaną zmienną lokalną, tak jak w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](./index.md)
- [Parametry metody](./method-parameters.md)
