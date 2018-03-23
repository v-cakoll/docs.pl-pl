---
title: w modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a>w modyfikator parametrów (odwołanie w C#)

`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie. Przypomina to [ref](ref.md) lub [limit](out-parameter-modifier.md) słów kluczowych, z wyjątkiem, że `in` argumentów nie można zmodyfikować przez metodę o nazwie, podczas gdy `ref` argumenty mogą zostać zmodyfikowane, `out` argumentów muszą zostać zmodyfikowane przez obiekt wywołujący, a te zmiany są według w kontekście wywołującego.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

W poprzednim przykładzie pokazano, które `in` modyfikator nie jest konieczne, w miejsce wywołania. Wymagane jest tylko w deklaracji metody.

> [!NOTE] 
> `in` — Słowo kluczowe można również z parametrem typu ogólnego w celu wskazania, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu składnika LINQ. Aby uzyskać więcej informacji dotyczących korzystania z `in` — słowo kluczowe w tych kontekstach, zobacz [w](in.md) zapewniające łącza do tych zastosowań.
  
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
  
Przeciążanie na podstawie obecności z `in` jest dozwolone, ale generuje ostrzeżenie kompilatora:  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

Właściwości lub stałe mogą być przekazywane jako `in` parametrów, ponieważ wywołanie metody nie mogą modyfikować wartości.
  
Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
- Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

Zwykle zadeklarować `in` argumentów, aby uniknąć wymaganych przez przekazywanie argumentów poprzez wartość operacje kopiowania. Jest to najbardziej przydatny w przypadku argumenty typów wartości, takich jak struktury gdzie operacje kopiowania są droższe niż przekazywanie poprzez odwołanie.

> [!WARNING]
>  `in` Parametry mogą być bardziej kosztowne niewłaściwego użycia. Kompilator może nie wiedzieć, jeśli element członkowski metod modyfikowania stanu struktury. Zawsze, gdy kompilator nie powiodło się, że obiekt nie jest modyfikowany, pamiętać o tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii. Wszystkie możliwe modyfikacje zostaną obrony ją. Są dwa sposoby, aby uniknąć tych kopii do przekazania `in` parametrów jako `in` argumentów lub definiowania struktury jako `readonly struct`.

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Semantykę odwołania z typami wartości](../../../csharp/reference-semantics-with-value-types.md)
