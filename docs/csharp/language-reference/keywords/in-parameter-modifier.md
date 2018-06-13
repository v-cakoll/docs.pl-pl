---
title: w modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311913"
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikator parametrów (odwołanie w C#)

`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Przypomina to [ref](ref.md) lub [limit](out-parameter-modifier.md) słów kluczowych, z wyjątkiem, że `in` argumentów nie można zmodyfikować przez metodę o nazwie. Podczas gdy `ref` argumenty mogą zostać zmodyfikowane, `out` argumenty muszą zostać zmodyfikowane przez obiekt wywołujący, a te zmiany są według w kontekście wywołującego.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

W poprzednim przykładzie pokazano, które `in` modyfikator zazwyczaj nie jest wykorzystywana w miejsce wywołania. Wymagane jest tylko w deklaracji metody.

> [!NOTE] 
> `in` — Słowo kluczowe można również z parametrem typu ogólnego w celu wskazania, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu składnika LINQ. Aby uzyskać więcej informacji dotyczących korzystania z `in` — słowo kluczowe w tych kontekstach, zobacz [w](in.md), który zawiera łącza do tych zastosowań.
  
 Zmienne przekazany jako `in` argumentów musi zostać zainicjowany przed przekazaniem w wywołaniu metody. Wywołana metoda nie może jednak przypisać wartość lub zmodyfikuj argument.  
  
 Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji. W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu. Następujący kod, na przykład nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążanie na podstawie obecności z `in` jest dozwolone:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Zasady rozpoznawania przeciążenia

Można zrozumieć zasady rozpoznawania przeciążenia metody z przez wartość a `in` argumenty zrozumienie motywacją `in` argumentów. Definiowanie przy użyciu metody `in` parametrów jest potencjalnych optymalizacji wydajności. Niektóre `struct` argumentów typu mogą być duże i metody wywołanego w pętli ścisłej lub ścieżek kodu krytycznego koszt kopiowania tych konstrukcji jest krytyczne. Metody deklarować `in` w celu określenia, że argumenty mogą być przekazywane przez odwołanie bezpiecznie ponieważ wywołana metoda nie modyfikuje stan tego argumentu. Przekazywanie tych argumentów przez odwołanie pozwala uniknąć kopiowania (potencjalnie) kosztowne. 

Określanie `in` dla argumentów w wywołaniu lokacji jest zwykle opcjonalne. Nie ma żadnej semantycznego różnicy między przekazywanie argumentów według wartości i przekazywanie ich przy użyciu odwołania `in` modyfikator. `in` Modyfikator w witrynie wywołanie jest opcjonalny, ponieważ nie ma potrzeby wskazywać, że wartość argumentu może ulec zmianie. Jawnie dodać `in` modyfikator w miejsce wywołania, aby upewnić się, argument jest przekazywana przez odwołanie, nie przez wartość. Jawnie za pomocą `in` ma dwa następujące skutki:

Po pierwsze, określając `in` w wywołaniu lokacji wymusza kompilator, aby wybrać metodę zdefiniowane z odpowiadającego mu `in` parametru. W przeciwnym razie, gdy dwie metody różnią się jedynie w związku z występowaniem `in`, przez wartość przeciążenia jest lepszym dopasowaniem.

Po drugie, określając `in` deklaruje zamiaru przekazywania argumentu przez odwołanie. Argument używany z `in` musi reprezentować lokalizacji, która może być bezpośrednio określonych. Zasady ogólne tej samej `out` i `ref` mają zastosowanie argumenty: nie można użyć stałe, właściwości zwykłych lub inne wyrażenia, które powodują powstanie wartości. W przeciwnym razie pominięcie `in` w wywołaniu lokacji informuje kompilator, że będą mogli go w celu utworzenia zmiennej tymczasowej przekazywane przez odwołanie tylko do odczytu do metody. Kompilator tworzy zmiennej tymczasowej, aby wyeliminować kilka ograniczeń z `in` argumentów:

- Stałe kompilacji jako umożliwia zmiennej tymczasowej `in` parametrów.
- Umożliwia zmiennej tymczasowej, właściwości lub inne wyrażenia `in` parametrów.
- Zmiennej tymczasowej umożliwia argumentów w przypadku, gdy istnieje niejawna konwersja z typu argumentu na typ parametru.

We wszystkich powyższych przypadkach kompilator tworzy zmiennej tymczasowej, która zawiera wartość stałą, właściwości lub innego wyrażenia.

Poniższy kod ilustruje te reguły:

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

Załóżmy, że innej metody, używając argumentów była dostępna. Wyniki zmiany, jak pokazano w poniższym kodzie:

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

Tylko wywołania metody, gdy argument jest przekazywana przez odwołanie, jest to końcowy.

> [!NOTE]
> W poprzednim kodzie użyto `int` jako typ argumentu dla uproszczenia. Ponieważ `int` jest nie większy niż odwołanie w najbardziej nowoczesne urządzenia jest żadnych korzyści przekazywanie pojedynczy `int` jako odwołanie tylko do odczytu. 

## <a name="limitations-on-in-parameters"></a>Ograniczenia dotyczące `in` parametrów

Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które definiują przy użyciu [async](async.md) modyfikator.  
- Metody iteracyjne, które obejmują [yield return](yield.md) lub `yield break` instrukcji.  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Słowa kluczowe języka C#](index.md)  
 [Parametry metody](method-parameters.md) [odwołania semantyka typów wartości](../../reference-semantics-with-value-types.md)
