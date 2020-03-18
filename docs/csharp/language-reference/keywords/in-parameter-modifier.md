---
title: w modyfikatorze parametrów - Odwołanie do języka C#
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: cbde7a571fb71ed7577077c77a5c61db553ec859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173617"
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikatorze parametrów (odwołanie do języka C#)

Słowo `in` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie. To sprawia, że formalny parametr alias dla argumentu, który musi być zmienna. Innymi słowy, każda operacja na parametr jest na argument. Jest jak [ref](ref.md) lub [out](out-parameter-modifier.md) słów `in` kluczowych, z tą różnicą, że argumenty nie mogą być modyfikowane przez wywoływana metoda. `ref` Argumenty mogą być `out` modyfikowane, argumenty muszą być modyfikowane przez wywoływaną metodę, a te modyfikacje są obserwowalne w kontekście wywołującym.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

W poprzednim przykładzie pokazano, że `in` modyfikator jest zwykle niepotrzebne w witrynie wywołania. Jest to wymagane tylko w deklaracji metody.

> [!NOTE]
> Słowo `in` kluczowe może być również używany z parametrem typu ogólnego, aby określić, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji lub jako część `join` klauzuli w kwerendzie LINQ. Aby uzyskać więcej informacji `in` na temat używania słowa kluczowego w tych kontekstach, zobacz [w](in.md), który zawiera łącza do wszystkich tych zastosowań.
  
Zmienne przekazywane `in` jako argumenty muszą zostać zainicjowane przed przekazaniem w wywołaniu metody. Jednak wywoływana metoda nie może przypisać wartość lub zmodyfikować argument.  

Modyfikator `in` parametrów jest dostępny w języku C# 7.2 i nowszych. Poprzednie wersje generują `CS8107` błąd kompilatora ("Funkcja "odwołania tylko do odczytu" nie jest dostępna w języku C# 7.0. Proszę użyć wersji językowej 7.2 lub większej.") Aby skonfigurować wersję językową kompilatora, zobacz [Wybieranie wersji języka Języka C#.](../configure-language-version.md)

Słowa `in` `ref`kluczowe `out` , i słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia. W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda ma `ref` lub `in` argument, a druga przyjmuje argument. `out` Poniższy kod, na przykład, nie skompiluje:  
  
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

## <a name="overload-resolution-rules"></a>Reguły rozpoznawania przeciążeń

Można zrozumieć reguły rozpoznawania przeciążenia dla metod `in` z argumentami `in` według wartości i przez zrozumienie motywacji argumentów. Definiowanie metod `in` przy użyciu parametrów jest potencjalną optymalizacją wydajności. Niektóre `struct` argumenty typu mogą mieć duży rozmiar, a gdy metody są wywoływane w ciasnych pętlach lub krytycznych ścieżkach kodu, koszt kopiowania tych struktur jest krytyczny. Metody deklarują `in` parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie, ponieważ wywoływana metoda nie modyfikuje stanu tego argumentu. Przekazywanie tych argumentów przez odwołanie pozwala uniknąć (potencjalnie) drogiej kopii.

Określanie `in` argumentów w witrynie wywołania jest zazwyczaj opcjonalne. Nie ma żadnej różnicy semantyczne między przekazywanie argumentów `in` przez wartość i przekazywanie ich przez odwołanie za pomocą modyfikatora. Modyfikator `in` w witrynie wywołania jest opcjonalny, ponieważ nie trzeba wskazywać, że wartość argumentu może zostać zmieniona. Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, że argument jest przekazywany przez odwołanie, a nie przez wartość. Jawnie `in` przy użyciu ma następujące dwa efekty:

Najpierw określenie `in` w witrynie wywołania wymusza kompilator, aby `in` wybrać metodę zdefiniowaną z parametrem dopasowania. W przeciwnym razie, gdy dwie metody `in`różnią się tylko w obecności , przeciążenie przez wartość jest lepsze dopasowanie.

Po drugie, `in` określenie deklaruje zamiar przekazania argumentu przez odwołanie. Argument używany `in` z musi reprezentować lokalizację, która może być bezpośrednio odwoływać się do. Te same ogólne `out` `ref` reguły i argumenty mają zastosowanie: Nie można używać stałych, zwykłych właściwości lub innych wyrażeń, które generują wartości. W przeciwnym razie `in` pominięcie w witrynie wywołania informuje kompilator, że pozwolisz mu utworzyć zmienną tymczasową do przekazywania przez odwołanie tylko do odczytu do metody. Kompilator tworzy zmienną tymczasową, aby pokonać kilka ograniczeń za pomocą `in` argumentów:

- Zmienna tymczasowa umożliwia skompilowanie `in` w czasie jako parametry.
- Zmienna tymczasowa umożliwia właściwości lub `in` inne wyrażenia dla parametrów.
- Zmienna tymczasowa zezwala na argumenty, w których istnieje niejawna konwersja z typu argumentu na typ parametru.

We wszystkich poprzednich wystąpieniach kompilator tworzy zmienną tymczasową, która przechowuje wartość wyrażenia stała, właściwość lub inne.

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

Teraz załóżmy, że dostępna była inna metoda używająca argumentów wartości. Wyniki zmieniają się, jak pokazano w następującym kodzie:

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

Jedyną metodą wywołania, gdzie argument jest przekazywany przez odwołanie jest ostateczna.

> [!NOTE]
> Poprzedni kod używa `int` jako typ argumentu dla uproszczenia. Ponieważ `int` nie jest większy niż odwołanie w większości nowoczesnych maszyn, `int` nie ma żadnych korzyści z przekazywania jednego jako odwołanie tylko do odczytu.

## <a name="limitations-on-in-parameters"></a>Ograniczenia `in` parametrów

Nie można używać `in`słów `ref` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)  
- Metody iterator, które obejmują zwrot `yield break` [uchylić](yield.md) lub instrukcji.  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Parametry metody](method-parameters.md)
- [Napisz bezpieczny, wydajny kod](../../write-safe-efficient-code.md)
