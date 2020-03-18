---
title: is - C# Odwołanie
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399638"
---
# <a name="is-c-reference"></a>is (odwołanie w C#)

Operator `is` sprawdza, czy wynik wyrażenia jest zgodny z danym typem lub (począwszy od Języka C# 7.0) testuje wyrażenie względem wzorca. Aby uzyskać informacje na `is` temat operatora testowania typu zobacz [jest operator](../operators/type-testing-and-cast.md#is-operator) sekcji [typ testowania i odlewane operatorów](../operators/type-testing-and-cast.md) artykułu.

## <a name="pattern-matching-with-is"></a>Dopasowanie wzorca z`is`

Począwszy od języka C# `is` 7.0, i [switch](switch.md) instrukcje obsługują dopasowanie wzorca. Słowo `is` kluczowe obsługuje następujące wzorce:

- [Wzorzec typu](#type-pattern), który sprawdza, czy wyrażenie może być konwertowane na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu.

- [Wzorzec stały](#constant-pattern), który sprawdza, czy wyrażenie oblicza określoną wartość stałą.

- [var pattern](#var-pattern), dopasowanie, które zawsze powiedzie się i wiąże wartość wyrażenia z nową zmienną lokalną.

### <a name="type-pattern"></a>Wzorzec tekstu

Korzystając z wzorca typu do `is` wykonywania dopasowania wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu. Jest to proste rozszerzenie `is` instrukcji, która umożliwia zwięzłe oceny typu i konwersji. Ogólna forma `is` wzorca typu jest:

```csharp
   expr is type varname
```

W przypadku *gdy expr* jest wyrażeniem, które oblicza wystąpienie pewnego typu, *typ* jest nazwą typu, na który ma zostać przekonwertowany wynik *expr,* `is` a `true` *varname* jest obiektem, na który jest konwertowany wynik *expr,* jeśli test jest .

Wyrażenie `is` jest, `true` jeśli *expr* nie `null`jest , a którykolwiek z następujących jest true:

- *expr* jest wystąpieniem tego samego typu co *typ*.

- *expr* jest wystąpieniem typu, który pochodzi od *typu*. Innymi słowy wynik *expr* może być rzutnie na wystąpienie *typu*.

- *expr* ma typ kompilacji w czasie, który jest klasą podstawową *typu*, a *expr* ma typ czasu wykonywania, który jest *typem* lub pochodzi od *typu*. *Typ czasu kompilacji* zmiennej jest typem zmiennej zdefiniowanym w jej deklaracji. *Typ czasu wykonywania* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.

- *expr* jest wystąpieniem typu, który implementuje interfejs *typu.*

Począwszy od języka C# 7.1, *expr* może mieć typ kompilacji zdefiniowany przez parametr typu ogólnego i jego ograniczenia.

Jeśli *expr* `true` jest i `is` `if` jest używany z instrukcją, `if` *varname* jest przypisany tylko w instrukcji. Zakres *varname* jest od `is` wyrażenia do końca bloku otaczającego `if` instrukcji. Użycie *varname* w dowolnej innej lokalizacji generuje błąd czasu kompilacji dla użycia zmiennej, która nie została przypisana.

W poniższym `is` przykładzie użyto wzorca typu, <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> aby zapewnić implementację metody typu.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez dopasowywania wzorców ten kod może być napisany w następujący sposób. Użycie dopasowywania wzorców typów daje bardziej kompaktowy, czytelny kod, eliminując konieczność testowania, czy wynikiem konwersji jest . `null`  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Wzorzec `is` typu tworzy również bardziej kompaktowy kod podczas określania typu typu wartości. W poniższym `is` przykładzie użyto wzorca typu, aby określić, czy obiekt jest lub `Person` `Dog` wystąpienie przed wyświetleniem wartości odpowiedniej właściwości.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Równoważny kod bez dopasowywania wzorców wymaga oddzielnego przypisania, które zawiera jawną rzutowanie.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Stały wzór

Podczas wykonywania wzorca pasującego do wzorca stałego sprawdza, `is` czy wyrażenie jest równe określonej stałej. W języku C# 6 i wcześniejszych wersjach wzorzec stałej jest obsługiwany przez [switch](switch.md) instrukcji. Począwszy od języka C# 7.0, `is` jest również obsługiwana przez instrukcję. Jego składnia jest:

```csharp
   expr is constant
```

gdzie *expr* jest wyrażeniem do oceny, a *stała* jest wartością do przetestowania. *stała* może być dowolne z następujących wyrażeń stałych:

- Wartość dosłowna.

- Nazwa zadeklarowanej `const` zmiennej.

- Stała wyliczenia.

Wyrażenie stałe jest oceniane w następujący sposób:

- Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości Języka C# określa, czy wyrażenie zwraca (czyli czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [Object.Equals(expr, stała)](xref:System.Object.Equals(System.Object,System.Object)) metoda.  

Poniższy przykład łączy typu i stałych wzorców, aby `Dice` sprawdzić, czy obiekt jest wystąpienie i, jeśli jest, aby ustalić, czy wartość rzutu kości jest 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Sprawdzanie `null` można wykonać przy użyciu stałego wzorca. Słowo `null` kluczowe jest obsługiwane `is` przez instrukcję. Jego składnia jest:

```csharp
   expr is null
```

W poniższym przykładzie `null` przedstawiono porównanie kontroli:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>wzór var

Dopasowanie wzorca `var` do wzorca zawsze kończy się pomyślnie. Jego składnia jest:

```csharp
   expr is var varname
```

Gdzie wartość *expr* jest zawsze przypisana do zmiennej lokalnej o nazwie *varname*. *varname* jest zmienną tego samego typu co typ *kompie typu expr.*

Jeśli *expr* oblicza `null`, `is` wyrażenie `true` generuje i `null` przypisuje *varname*. Var wzorzec jest jednym `is` z `true` niewielu `null` zastosowań, które produkuje dla wartości.

`var` Wzorzec służy do tworzenia zmiennej tymczasowej w wyrażenie logiczne, jak pokazano w poniższym przykładzie:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

W poprzednim przykładzie zmienna tymczasowa jest używana do przechowywania wyniku kosztownej operacji. Zmienna może być następnie używana wiele razy.

## <a name="c-language-specification"></a>specyfikacja języka C#
  
Aby uzyskać więcej informacji, zobacz [jest operator](~/_csharplang/spec/expressions.md#the-is-operator) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i następujące propozycje języka C#:

- [Dopasowanie do wzorca](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Dopasowywanie wzorca do typów ogólnych](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Operatory testowania typu i rzutowania](../operators/type-testing-and-cast.md)
