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
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
Słowo `out` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie. To sprawia, że formalny parametr alias dla argumentu, który musi być zmienna. Innymi słowy, każda operacja na parametr jest na argument. Jest jak [ref](ref.md) słowo kluczowe, z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed jej przekazaniem. Jest również jak [w](in-parameter-modifier.md) słowa `in` kluczowego, z wyjątkiem, że nie zezwala wywoływana metoda do modyfikowania wartości argumentu. Aby użyć `out` parametru, zarówno definicji metody, jak i `out` metody wywołującej należy jawnie użyć słowa kluczowego. Przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> Słowo `out` kluczowe może być również używane z parametrem typu ogólnego, aby określić, że parametr typu jest kowariantny. Aby uzyskać więcej informacji `out` na temat użycia słowa kluczowego w tym kontekście, zobacz [(Modyfikator ogólny)](out-generic-modifier.md).
  
Zmienne przekazywane `out` jako argumenty nie muszą być inicjowane przed przekazaniem w wywołaniu metody. Jednak wywoływana metoda jest wymagana do przypisania wartości przed zwracaniem metody.  
  
Słowa `in` `ref`kluczowe `out` , i słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia. W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda ma `ref` lub `in` argument, a druga przyjmuje argument. `out` Poniższy kod, na przykład, nie skompiluje:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążenie jest legalne, jednak, `ref`jeśli `in`jedna `out` metoda ma , lub argument, a druga nie ma żadnego z tych modyfikatorów, jak to:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilator wybiera najlepsze przeciążenie, dopasowując modyfikatory parametrów w witrynie wywołania do modyfikatorów parametrów używanych w wywołaniu metody.

Właściwości nie są zmienne i dlatego `out` nie mogą być przekazywane jako parametry.
  
Nie można używać `in`słów `ref` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](./async.md)  
  
- Metody iterator, które obejmują zwrot `yield break` [uchylić](./yield.md) lub instrukcji.  

## <a name="declaring-out-parameters"></a>Deklarowanie `out` parametrów

Deklarowanie metody `out` z argumentami jest klasycznym obejściem zwracającym wiele wartości. Począwszy od języka C# 7.0, należy wziąć pod uwagę [krotek](../../tuples.md) dla podobnych scenariuszy. W poniższym `out` przykładzie użyto do zwrócenia trzech zmiennych z wywołaniem jednej metody. Należy zauważyć, że trzeci argument jest przypisany do wartości null. Dzięki temu metody do zwracania wartości opcjonalnie.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Wywoływanie metody `out` z argumentem

W języku C# 6 i wcześniejszych, należy zadeklarować zmienną `out` w oddzielnej instrukcji przed przekazaniem go jako argument. W poniższym przykładzie zadeklarowano zmienną o nazwie `number` przed przekazaniem do Metody [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) która próbuje przekonwertować ciąg na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od języka C# 7.0, można zadeklarować `out` zmienną na liście argumentów wywołania metody, a nie w deklaracji zmiennej oddzielnej. Daje to bardziej kompaktowy, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody. Poniższy przykład jest podobny do poprzedniego przykładu, `number` z tą różnicą, że definiuje zmienną w wywołaniu [Metody Int32.TryParse.](xref:System.Int32.TryParse(System.String,System.Int32@))

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

W poprzednim przykładzie `number` zmienna jest silnie `int`wpisana jako . Można również zadeklarować niejawnie wpisaną zmienną lokalną, tak jak w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Parametry metody](./method-parameters.md)
