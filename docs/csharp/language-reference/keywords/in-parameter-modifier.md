---
title: modyfikator parametru- C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715252"
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikatorze parametruC# (odwołanie)

Słowo kluczowe `in` powoduje, że argumenty są przekazane przez odwołanie. Sprawia, że parametr formalny jest aliasem dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie. Przypomina słowa kluczowe [ref](ref.md) lub [out](out-parameter-modifier.md) , z tą różnicą, że `in` argumenty nie mogą być modyfikowane przez wywołaną metodę. `ref` argumenty mogą być modyfikowane, `out` argumenty muszą być modyfikowane przez wywołaną metodę, a te modyfikacje są zauważalne w kontekście wywołującym.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

W poprzednim przykładzie pokazano, że modyfikator `in` jest zwykle zbędny w odróżnieniu od lokacji wywołania. Jest to wymagane tylko w deklaracji metody.

> [!NOTE] 
> Słowa kluczowego `in` można również użyć z parametrem typu ogólnego, aby określić, że parametr typu jest kontrawariantne, jako część instrukcji `foreach` lub jako część klauzuli `join` w zapytaniu LINQ. Aby uzyskać więcej informacji na temat używania słowa kluczowego `in` w tych kontekstach, zobacz sekcję [w](in.md)temacie, która zawiera linki do wszystkich tych celów.
  
Zmienne przekazane jako argumenty `in` muszą być inicjowane przed przekazaniem w wywołaniu metody. Jednak wywołana metoda nie może przypisywać wartości ani modyfikować argumentu.  

Modyfikator parametru `in` jest dostępny w C# 7,2 i nowszych. Poprzednie wersje generują błędy kompilatora `CS8107` ("funkcja" odwołania tylko do odczytu "jest C# niedostępna w 7,0. Użyj języka w wersji 7,2 lub nowszej. ") Aby skonfigurować wersję języka kompilatora, zobacz [Wybieranie wersji C# językowej](../configure-language-version.md).

Słowa kluczowe `in`, `ref`i `out` nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia. W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda przyjmuje argument `ref` lub `in`, a drugi przyjmuje argument `out`. Poniższy kod, na przykład, nie zostanie skompilowany:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Przeciążanie na podstawie obecności `in` jest dozwolone:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Reguły rozpoznawania przeciążenia

Można zrozumieć reguły rozpoznawania przeciążeń dla metod za pomocą wartości przez wartość i `in` argumenty przez zrozumienie motywacji argumentów `in`. Definiowanie metod przy użyciu parametrów `in` jest potencjalną optymalizacją wydajności. Niektóre argumenty typu `struct` mogą być duże, a gdy metody są wywoływane przy użyciu ścisłych pętli lub ścieżek kodu krytycznego, koszt kopiowania tych struktur jest krytyczny. Metody deklarują `in` parametry, aby określić, że argumenty mogą być przekazane przez odwołanie bezpiecznie, ponieważ wywołana metoda nie modyfikuje stanu tego argumentu. Przekazanie tych argumentów przez odwołanie pozwala uniknąć (potencjalnie) kosztownego kopiowania. 

Określanie `in` dla argumentów w miejscu wywołania jest zwykle opcjonalne. Między przekazywaniem argumentów przez wartość i przekazaniem ich przez odwołanie przy użyciu modyfikatora `in` nie ma różnicy semantycznej. Modyfikator `in` w miejscu wywołania jest opcjonalny, ponieważ nie trzeba wskazywać, że wartość argumentu może zostać zmieniona. Należy jawnie dodać modyfikator `in` w miejscu wywołania, aby upewnić się, że argument jest przenoszona przez odwołanie, a nie przez wartość. Jawnie używanie `in` ma dwa następujące efekty:

Najpierw Określanie `in` w witrynie wywołania wymusza, aby kompilator wybierał metodę zdefiniowaną za pomocą pasującego parametru `in`. W przeciwnym razie, gdy dwie metody różnią się tylko w obecności `in`, Przeciążenie przez wartość jest lepszym dopasowaniem.

Po drugie, określenie `in` deklaruje intencję przekazania argumentu przez odwołanie. Argument używany z `in` musi reprezentować lokalizację, do której może odwoływać się bezpośrednio. Te same reguły ogólne dla argumentów `out` i `ref` mają zastosowanie: nie można użyć stałych, zwykłych właściwości ani innych wyrażeń, które tworzą wartości. W przeciwnym razie pominięcie `in` w witrynie wywołania informuje kompilator, że umożliwi to utworzenie zmiennej tymczasowej do przekazania przez odwołanie tylko do odczytu do metody. Kompilator tworzy zmienną tymczasową, aby przezwyciężyć kilka ograniczeń z `in` argumentami:

- Zmienna tymczasowa dopuszcza stałe w czasie kompilacji jako parametry `in`.
- Zmienna tymczasowa zezwala na właściwości lub inne wyrażenia dla `in` parametrów.
- Zmienna tymczasowa zezwala na argumenty, w których istnieje niejawna konwersja z typu argumentu na typ parametru.

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

Teraz Załóżmy, że jest dostępna inna metoda używająca argumentów wartości. Wyniki są zmieniane, jak pokazano w poniższym kodzie:

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

Jedyne wywołanie metody, do którego argument jest przenoszona przez odwołanie jest ostatnim z nich.

> [!NOTE]
> Poprzedni kod używa `int` jako typ argumentu dla uproszczenia. Ponieważ `int` nie jest większy niż odwołanie w większości nowoczesnych maszyn, nie ma korzyści, aby przekazywać pojedynczy `int` jako odwołanie tylko do odczytu. 

## <a name="limitations-on-in-parameters"></a>Ograniczenia dotyczące parametrów `in`

Nie można użyć słów kluczowych `in`, `ref`i `out` dla następujących rodzajów metod:  
  
- Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](async.md) .  
- Metody iteratorów, które zawierają instrukcję [yield return](yield.md) lub `yield break`.  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Parametry metody](method-parameters.md)
- [Zapisz bezpieczny wydajny kod](../../write-safe-efficient-code.md)
