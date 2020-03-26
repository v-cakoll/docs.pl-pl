---
title: w modyfikatorze parametrów - Odwołanie do języka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 20956f9e25b6830a8876824a4c9dad1dbc4c4f3e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249373"
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikatorze parametrów (odwołanie do języka C#)

Słowo `in` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie. Sprawia, że parametr formalny alias dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametr jest na argument. Jest jak [ref](ref.md) lub [out](out-parameter-modifier.md) słowa `in` kluczowe, z tą różnicą, że argumenty nie mogą być modyfikowane przez metodę wywołaną. Argumenty `ref` mogą być modyfikowane, `out` argumenty muszą być modyfikowane przez metodę wywołaną, a te modyfikacje są obserwowalne w kontekście wywołującym.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

W poprzednim przykładzie pokazano, że `in` modyfikator jest zwykle niepotrzebne w witrynie wywołania. Jest to wymagane tylko w deklaracji metody.

> [!NOTE]
> Słowo `in` kluczowe może być również używane z parametrem typu ogólnego, aby określić, `foreach` że parametr typu `join` jest kontrawariant, jako część instrukcji lub jako część klauzuli w kwerendzie LINQ. Aby uzyskać więcej informacji `in` na temat używania słowa kluczowego w tych kontekstach, zobacz [w](in.md)programie , który zawiera linki do wszystkich tych zastosowań.
  
Zmienne przekazywane `in` jako argumenty muszą być zainicjowane przed przekazaniem w wywołaniu metody. Jednak wywołana metoda nie może przypisać wartość lub zmodyfikować argument.  

Modyfikator `in` parametrów jest dostępny w języku C# 7.2 i nowszych. Poprzednie wersje generują `CS8107` błąd kompilatora ("Funkcja 'tylko do odczytu odwołania' nie jest dostępna w języku C# 7.0. Użyj wersji językowej 7.2 lub większej.") Aby skonfigurować wersję językową kompilatora, zobacz [Wybieranie wersji języka języka C#.](../configure-language-version.md)

Programy `in` `ref`, `out` i słowa kluczowe nie są uważane za część podpisu metody w celu rozwiązania przeciążenia. W związku z tym metody nie mogą być przeciążone, `in` jeśli jedyną `out` różnicą jest to, że jedna metoda przyjmuje `ref` argument lub, a druga przyjmuje argument. Poniższy kod, na przykład, nie będzie kompilować:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążenie w oparciu `in` o obecność jest dozwolone:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Reguły rozpoznawania przeciążenia

Można zrozumieć reguły rozpoznawania przeciążenia dla `in` metod z argumentami `in` według wartości i, rozumiejąc motywację argumentów. Definiowanie metod `in` przy użyciu parametrów jest potencjalną optymalizacją wydajności. Niektóre `struct` argumenty typu mogą mieć duży rozmiar, a gdy metody są wywoływane w ciasnych pętlach lub krytycznych ścieżkach kodu, koszt kopiowania tych struktur jest krytyczny. Metody `in` deklarują parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie, ponieważ wywołana metoda nie modyfikuje stan tego argumentu. Przekazywanie tych argumentów przez odwołanie pozwala uniknąć (potencjalnie) kosztownej kopii.

Określanie `in` argumentów w lokacji wywołania jest zazwyczaj opcjonalne. Nie ma żadnej różnicy semantycznej między przekazywaniem argumentów przez wartość a przekazywaniem ich przez odwołanie przy użyciu modyfikatora. `in` Modyfikator `in` w witrynie wywołania jest opcjonalny, ponieważ nie trzeba wskazać, że wartość argumentu może zostać zmieniona. Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, że argument jest przekazywany przez odwołanie, a nie przez wartość. Jawnie `in` przy użyciu ma następujące dwa efekty:

Najpierw określenie `in` w lokacji wywołania wymusza kompilatora, aby wybrać metodę zdefiniowaną z pasującym `in` parametrem. W przeciwnym razie, gdy dwie `in`metody różnią się tylko w obecności , przeciążenie przez wartość jest lepsze dopasowanie.

Po drugie, `in` określenie deklaruje zamiar przekazania argumentu przez odwołanie. Argument używany `in` z musi reprezentować lokalizację, która może być bezpośrednio odwoływana. Te same ogólne `out` `ref` reguły i argumenty mają zastosowanie: Nie można używać stałych, zwykłych właściwości lub innych wyrażeń, które tworzą wartości. W przeciwnym razie `in` pominięcie w witrynie wywołania informuje kompilator, że pozwoli mu utworzyć zmienną tymczasową do przekazywania przez odwołanie tylko do odczytu do metody. Kompilator tworzy zmienną tymczasową, `in` aby przezwyciężyć kilka ograniczeń z argumentami:

- Zmienna tymczasowa umożliwia kompilacji `in` w czasie stałych jako parametry.
- Zmienna tymczasowa zezwala na właściwości `in` lub inne wyrażenia dla parametrów.
- Zmienna tymczasowa umożliwia argumenty, w których istnieje niejawna konwersja z typu argumentu do typu parametru.

We wszystkich poprzednich wystąpieniach kompilator tworzy zmienną tymczasową, która przechowuje wartość stałej, właściwości lub innego wyrażenia.

Poniższy kod ilustruje następujące reguły:

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

Teraz załóżmy, że inna metoda przy użyciu argumentów wartości była dostępna. Wyniki zmieniają się, jak pokazano w poniższym kodzie:

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

Wywołanie jedyną metodą, w której argument jest przekazywany przez odwołanie, jest ostatnim.

> [!NOTE]
> Poprzedni kod używa `int` jako typ argumentu dla uproszczenia. Ponieważ `int` nie jest większy niż odwołanie w większości nowoczesnych maszyn, `int` nie ma żadnych korzyści z przekazywania pojedynczego jako readonly odniesienia.

## <a name="limitations-on-in-parameters"></a>Ograniczenia `in` parametrów

Nie można użyć `in`programu `ref`, `out` i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)  
- Metody iteratora, które zawierają `yield break` [zwrotu wydajności](yield.md) lub instrukcji.
- Pierwszy argument metody rozszerzenia nie `in` może mieć modyfikatora, chyba że ten argument jest strukturą.
- Pierwszy argument metody rozszerzenia, w którym ten argument jest typem rodzajowym (nawet wtedy, gdy ten typ jest ograniczony do struktury.)

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Parametry metody](method-parameters.md)
- [Napisz bezpieczny skuteczny kod](../../write-safe-efficient-code.md)
