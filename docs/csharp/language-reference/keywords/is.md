---
title: '- C# odwołanie'
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a72f3b87e7558c594ef8a94bd0eadcc4664206b9
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239654"
---
# <a name="is-c-reference"></a>is (odwołanie w C#)

Operator `is` sprawdza, czy wynik wyrażenia jest zgodny z danym typem, lub (Zaczynając od C# 7,0) testuje wyrażenie względem wzorca. Aby uzyskać informacje o operatorze `is` testowania typu, zobacz sekcję [operator is](../operators/type-testing-and-cast.md#is-operator) w artykule [test typu i Operatory rzutowania](../operators/type-testing-and-cast.md) .

## <a name="pattern-matching-with-is"></a>Dopasowanie wzorca do `is`

Począwszy od C# 7,0, instrukcje `is` i [Switch](switch.md) obsługują dopasowanie do wzorca. Słowo kluczowe `is` obsługuje następujące wzorce:

- [Wzorzec typu](#type-pattern), który sprawdza, czy wyrażenie może być konwertowane do określonego typu i, jeśli może, przerzutuje go do zmiennej tego typu.

- [Wzorzec stałej](#constant-pattern), który sprawdza, czy wyrażenie daje w wyniku określoną wartość stałą.

- [wzorzec var](#var-pattern), dopasowanie, które zawsze powiedzie się i wiąże wartość wyrażenia z nową zmienną lokalną.

### <a name="type-pattern"></a>Wzorzec typu

W przypadku używania wzorca typu do dopasowania do wzorca, `is` sprawdza, czy wyrażenie może być konwertowane do określonego typu i, jeśli to możliwe, rzutuje go na zmienną tego typu. Jest to proste rozszerzenie instrukcji `is`, które umożliwia ocenę i konwersję typu zwięzłego. Ogólna forma wzorca typu `is`:

```csharp
   expr is type varname
```

Gdzie *Expr* jest wyrażeniem, którego wynikiem jest wystąpienie pewnego typu, *Typ* jest nazwą typu, do którego zostanie przekonwertowany wynik *wyrażenia* , a *nazwa_zmiennej* jest obiektem, do którego jest konwertowany wynik *wyrażenia* , jeśli test `is` jest `true`. 

Wyrażenie `is` jest `true` Jeśli *wyrażenie* nie jest `null`i spełnione są wszystkie następujące warunki:

- *wyrażenie* jest wystąpieniem tego samego typu co *Typ*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy, wynik *wyrażenia* może być rzutowany na wystąpienie *typu*.

- *wyrażenie* ma typ czasu kompilacji, który jest klasą bazową *typu*, a *wyrażenie* ma typ środowiska uruchomieniowego, który jest *typem* lub pochodzi od *typu*. *Typ czasu kompilacji* zmiennej to typ zmiennej, zgodnie z definicją w swojej deklaracji. *Typ środowiska uruchomieniowego* zmiennej to typ wystąpienia, które jest przypisane do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje interfejs *typu* .

Począwszy od C# 7,1, *wyrażenie* może mieć typ czasu kompilacji zdefiniowany przez parametr typu ogólnego i jego ograniczenia.

Jeśli *wyrażenie* jest `true` i `is` jest używany z instrukcją `if`, *nazwa_zmiennej* jest przypisywana tylko w instrukcji `if`. Zakres elementu *nazwa_zmiennej* pochodzi z wyrażenia `is` do końca bloku zawierającego instrukcję `if`. Użycie elementu *nazwa_zmiennej* w dowolnej innej lokalizacji generuje błąd czasu kompilacji do użycia zmiennej, która nie została przypisana.

Poniższy przykład używa wzorca typu `is`, aby zapewnić implementację metody <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> typu.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez dopasowania do wzorca ten kod może być zapisany w następujący sposób. Użycie dopasowania wzorca typu daje bardziej zwarty, czytelny kod, eliminując konieczność sprawdzenia, czy wynikiem konwersji jest `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Wzorzec typu `is` generuje również bardziej zwarty kod podczas określania typu wartości. Poniższy przykład używa wzorca typu `is`, aby określić, czy obiekt jest wystąpieniem `Person` czy `Dog` przed wyświetleniem wartości odpowiedniej właściwości.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Odpowiedni kod bez dopasowania do wzorca wymaga oddzielnego przypisania zawierającego jawne rzutowanie.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Wzorzec stałej

Podczas dopasowywania wzorców do wzorca stałego `is` sprawdza, czy wyrażenie jest równe określonej stałej. W C# 6 i wcześniejszych wersjach wzorzec stałej jest obsługiwany przez instrukcję [Switch](switch.md) . Począwszy od C# 7,0, jest to również obsługiwane przez instrukcję `is`. Jego składnia to:

```csharp
   expr is constant
```

gdzie *Expr* jest wyrażeniem, które ma zostać obliczone, a *stała* jest wartością do przetestowania. *stała* może być dowolnym z następujących wyrażeń stałych:

- Wartość literału.

- Nazwa zadeklarowanej zmiennej `const`.

- Stała wyliczenia.

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *wyrażenie* i *stała* są typami całkowitymi, C# operator równości określa, czy wyrażenie zwróci `true` (to znaczy czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody static [obiektu. Equals (wyrażenie, stała)](xref:System.Object.Equals(System.Object,System.Object)) .  

Poniższy przykład łączy typ i wzorce stałe, aby sprawdzić, czy obiekt jest wystąpieniem `Dice` i, jeśli jest, aby określić, czy wartość rzutowania indeksu to 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Sprawdzanie `null` można wykonać przy użyciu wzorca stałego. Słowo kluczowe `null` jest obsługiwane przez instrukcję `is`. Jego składnia to:

```csharp
   expr is null
```

Poniższy przykład przedstawia porównanie `null` sprawdzenia:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>wzorzec wariancji

Dopasowanie wzorca ze wzorcem `var` zawsze powiedzie się. Jego składnia to:

```csharp
   expr is var varname
```

Gdzie wartość *wyrażenia* jest zawsze przypisana do zmiennej lokalnej o nazwie *nazwa_zmiennej*. *nazwa_zmiennej* jest zmienną tego samego typu co typ *wyrażenia*w czasie kompilacji. 

Jeśli *wyrażenie* zwróci wartość `null`, wyrażenie `is` generuje `true` i przypisuje `null` do *nazwa_zmiennej*. Wzorzec var jest jednym z kilku zastosowania `is`, które wytwarza `true` dla wartości `null`.

Możesz użyć wzorca `var`, aby utworzyć zmienną tymczasową w ramach wyrażenia logicznego, jak pokazano na poniższym przykładzie:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

W poprzednim przykładzie zmienna tymczasowa jest używana do przechowywania wyniku kosztownej operacji. Zmienna może być używana wiele razy.

## <a name="c-language-specification"></a>specyfikacja języka C#
  
Aby uzyskać więcej informacji, zapoznaj się z sekcją [operatora is](~/_csharplang/spec/expressions.md#the-is-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) i następujących C# propozycjach języka:

- [Dopasowanie do wzorca](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Dopasowywanie wzorca do typów ogólnych](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Operatory testowania typu i rzutowania](../operators/type-testing-and-cast.md)
