---
title: modyfikator parametru out — C# odwołanie
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713271"
---
# <a name="out-parameter-modifier-c-reference"></a>out — Modyfikator parametrów (odwołanie w C#)
Słowo kluczowe `out` powoduje, że argumenty są przekazane przez odwołanie. Sprawia, że parametr formalny jest aliasem dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie. Jest to podobne do słowa kluczowego [ref](ref.md) , z tą różnicą, że `ref` wymaga, aby zmienna została zainicjowana przed przekazaniem. Jest on również podobny do słowa kluczowego [in](in-parameter-modifier.md) , z wyjątkiem tego, że `in` nie zezwala metodzie wywoływanej na modyfikowanie wartości argumentu. Aby użyć parametru `out`, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie użyć słowa kluczowego `out`. Na przykład:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> Za pomocą słowa kluczowego `out` można także użyć parametru typu ogólnego, aby określić, że parametr typu jest współwariantem. Aby uzyskać więcej informacji na temat używania słowa kluczowego `out` w tym kontekście, zobacz [out (modyfikator ogólny)](out-generic-modifier.md).
  
Zmienne przekazane jako argumenty `out` nie muszą być inicjowane przed przekazywaniem w wywołaniu metody. Jednak wywoływana metoda jest wymagana do przypisania wartości przed zwróceniem metody.  
  
Słowa kluczowe `in`, `ref`i `out` nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia. W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda przyjmuje argument `ref` lub `in`, a drugi przyjmuje argument `out`. Poniższy kod, na przykład, nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążanie jest dozwolone, jednak jeśli jedna metoda przyjmuje argument `ref`, `in`lub `out`, a drugi nie ma żadnego z tych modyfikatorów, takich jak:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilator wybiera najlepsze Przeciążenie przez dopasowanie modyfikatorów parametrów w miejscu wywołania do modyfikatorów parametrów używanych w wywołaniu metody.
 
Właściwości nie są zmiennymi i w związku z tym nie można ich przekazywać jako parametrów `out`.
  
Nie można użyć słów kluczowych `in`, `ref`i `out` dla następujących rodzajów metod:  
  
- Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](./async.md) .  
  
- Metody iteratorów, które zawierają instrukcję [yield return](./yield.md) lub `yield break`.  

## <a name="declaring-out-parameters"></a>Deklarowanie parametrów `out`   

Deklarowanie metody z argumentami `out` jest klasycznym obejściem do zwrócenia wielu wartości. Począwszy od C# 7,0, rozważ zastosowanie [krotek](../../tuples.md) dla podobnych scenariuszy. Poniższy przykład używa `out`, aby zwrócić trzy zmienne z pojedynczym wywołaniem metody. Zwróć uwagę, że trzeci argument jest przypisany do wartości null. Dzięki temu metody mogą zwracać wartości opcjonalnie.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Wywoływanie metody z argumentem `out`

W C# 6 i wcześniejszych wersjach należy zadeklarować zmienną w oddzielnej instrukcji przed przekazaniem jej jako argumentu `out`. Poniższy przykład deklaruje zmienną o nazwie `number` przed przekazaniem do metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , która próbuje skonwertować ciąg na liczbę.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Począwszy od C# 7,0, można zadeklarować zmienną `out` na liście argumentów wywołania metody, a nie w oddzielnej deklaracji zmiennej. Daje to bardziej zwarty, czytelny kod, a także zapobiega przypadkowemu przypisaniu wartości do zmiennej przed wywołaniem metody. Poniższy przykład przypomina poprzedni przykład, z tą różnicą, że definiuje zmienną `number` w wywołaniu metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
W poprzednim przykładzie zmienna `number` jest silnie wpisana jako `int`. Można również zadeklarować niejawnie wpisaną zmienną lokalną, jak pokazano w poniższym przykładzie.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Specyfikacja języka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Parametry metody](./method-parameters.md)
