---
title: w modyfikator parametru - C# odwołania
ms.custom: seodec18
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: d08b135c92cab176e402fec73999083fe4309362
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236300"
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikator parametrów (odwołanie w C#)

`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Jest on podobny do [ref](ref.md) lub [się](out-parameter-modifier.md) słów kluczowych, poza tym, że `in` argumentów nie można zmodyfikować przez metodę o nazwie. Natomiast `ref` argumentów może być modyfikowany, `out` argumenty muszą zostać zmodyfikowane przez metodę o nazwie, a te zmiany są obserwowalnymi w kontekst wywołania.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Poprzedni przykład pokazuje, że `in` modyfikator jest zazwyczaj zbędna w witrynie wywołania. Jest wymagany tylko w deklaracji metody.

> [!NOTE] 
> `in` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu LINQ. Aby uzyskać więcej informacji na temat użytkowania `in` Zobacz — słowo kluczowe w tych kontekstach [w](in.md), który zawiera łącza do wszystkich tych zastosowań.
  
 Zmienne są przekazywane jako `in` argumentów musi zostać zainicjowany przed przesłaniem w wywołaniu metody. Jednak wywoływanej metody nie może przypisać wartość lub zmodyfikuj argumentu.  
  
 Mimo że `in`, `ref`, i `out` słowa kluczowe powodować różne zachowanie w czasie wykonywania, ich nie są uważane za część podpisu metody w czasie kompilacji. W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu. Poniższy kod, na przykład, nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążenie oparte na obecność `in` jest dozwolony:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Zasad rozpoznawania przeciążenia

Rozumiesz reguły rozdzielczość przeciążenia dla metod z według wartości a `in` argumenty dzięki zrozumieniu motywacją `in` argumentów. Definiowanie metody przy użyciu `in` parametry są potencjalnymi optymalizacji wydajności. Niektóre `struct` argumentów typu może być duży, rozmiar i metody wywołanego w ścisłej pętli lub ścieżek kodu krytycznego koszt kopiowania tych konstrukcji jest krytyczny. Zadeklaruj metody `in` parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie ponieważ wywoływanej metody nie powoduje modyfikacji stanu tego argumentu. Przekazywanie tych argumentów poprzez odwołanie pozwala uniknąć kopiowania (potencjalnie). 

Określanie `in` dla argumentów w wywołaniu witryny jest zazwyczaj opcjonalna. Nie ma żadnej różnicy semantycznego między przekazywanie argumentów według wartości i przekazywania ich za pomocą odwołania `in` modyfikator. `in` Modyfikator lokacji wywołanie jest opcjonalny, ponieważ nie wymaga wskazać, że wartość argumentu może ulec zmianie. Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, argument jest przekazywany przez odwołanie, nie przez wartość. Lepiej nie używać `in` ma następujące dwa skutki:

Po pierwsze, określając `in` w wywołaniu witryny wymusza na kompilatorze o wybranie metody zdefiniowane przy użyciu zgodnego `in` parametru. W przeciwnym razie, gdy dwie metody różnią się tylko w obecności właściwości `in`, według wartości przeciążenia ma lepsze dopasowanie.

Po drugie, określając `in` deklaruje zgodne z zamiarami użytkownika do przekazywania argumentu przez odwołanie. Argument używane z `in` musi reprezentować lokalizacji, która może być bezpośrednio określonych. Ten sam ogólne reguły `out` i `ref` stosowanie argumentów: Nie można używać stałych, właściwości zwykłych lub innych wyrażeń, które generują wartości. W przeciwnym razie pominięcie `in` w wywołaniu witryny informuje kompilator, będą mogli go, aby utworzyć zmiennej tymczasowej, aby przekazać tylko do odczytu odwołanie do metody. Kompilator tworzy zmienną tymczasową celu wyeliminowanie kilku ograniczeń za pomocą `in` argumenty:

- Zmienna tymczasowa umożliwia stałe kompilacji jako `in` parametrów.
- Zmienna tymczasowa umożliwia właściwości lub innych wyrażeń dla `in` parametrów.
- Zmienna tymczasowa zezwala argumenty w przypadku, gdy istnieje niejawna konwersja z typu argumentu z typem parametru.

We wszystkich wystąpieniach poprzedniej kompilator tworzy zmiennej tymczasowej, która przechowuje wartość stałą, właściwość lub innego wyrażenia.

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

Teraz załóżmy, że innej metody, używając wartości argumentów była dostępna. Wyniki zmiany, jak pokazano w poniższym kodzie:

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

Wywołanie metody tylko wtedy, gdy argument jest przekazywany przez odwołanie jest ostatecznej.

> [!NOTE]
> W poprzednim kodzie użyto `int` jako typ argumentu dla uproszczenia. Ponieważ `int` jest nie większy niż odwołanie w większości współczesnych komputerów jest przekazanie pojedynczej żadnych korzyści `int` jako odwołanie tylko do odczytu. 

## <a name="limitations-on-in-parameters"></a>Ograniczenia dotyczące `in` parametrów

Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które można zdefiniować przy użyciu [async](async.md) modyfikator.  
- Metody iteratora, które obejmują [yield return](yield.md) lub `yield break` instrukcji.  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Parametry metody](method-parameters.md)  
- [Pisanie kodu efektywne bezpieczne](../../write-safe-efficient-code.md)  
