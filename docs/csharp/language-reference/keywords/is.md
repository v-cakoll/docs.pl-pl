---
title: is (odwołanie w C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 037144c47a97a44cad504882fdf8c88caf4918d7
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121313"
---
# <a name="is-c-reference"></a>is (odwołanie w C#) #

Sprawdza, czy obiekt jest zgodny z danego typu, lub (rozpoczynający się znakami języka C# 7.0) sprawdza się wyrażenie do wzorca.

## <a name="testing-for-type-compatibility"></a>Testowanie zgodności typu ##

`is` — Słowo kluczowe ocenia zgodność z typem w czasie wykonywania. Określa, czy wystąpienie obiektu lub wyniku wyrażenia można przekonwertować na określony typ. Ma składnię

```csharp
   expr is type
```

gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu i *typu* jest nazwą typu, do której wynik *expr* do przekonwertowania. `is` Instrukcja jest `true` Jeśli *expr* jest inna niż null i wyniki z obliczając wartość wyrażenia można przekonwertować na obiekt *typu*; w przeciwnym razie zwraca `false`.

Na przykład, poniższy kod określa, czy `obj` mogą być rzutowane na wystąpienie `Person` typu:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Instrukcja jest wartość true, jeśli:

- *wyrażenie* to wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*. Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.

- *wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*. *Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Poniższy przykład pokazuje, że `is` wyrażenie daje w wyniku `true` dla każdej takiej konwersji.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` — Słowo kluczowe generuje ostrzeżenie kompilacji, jeśli wiadomo, że wyrażenie zawsze być `true` lub `false`. Analizuje ona tylko konwersje odwołań, konwersje boxing i konwersji unboxing; nie traktuje konwersje zdefiniowane przez użytkownika lub konwersje zdefiniowane przez typ [niejawne](implicit.md) i [jawne](explicit.md) operatorów. Poniższy przykład generuje ostrzeżenia, ponieważ wynik konwersji jest znany w czasie kompilacji. Należy pamiętać, że `is` wyrażenia w przypadku konwersji z typu `int` do `long` i `double` zwraca wartość FAŁSZ, ponieważ te konwersje są obsługiwane przez [niejawne](implicit.md) operatora.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` może to być wyrażenie zwracające wartość, z wyjątkiem metod anonimowych, jak i o wyrażenia lambda. W poniższym przykładzie użyto `is` można obliczyć wartość zwracaną przez wywołanie metody.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Począwszy od języka C# 7.0, można użyć dopasowywania do wzorca z [wpisz wzór](#type) napisać bardziej zwięzły widok kodu, który używa `is` instrukcji.

## <a name="pattern-matching-with-is"></a>Dopasowywanie wzorca z `is` ##

Począwszy od C# 7.0, `is` i [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcje obsługują dopasowywania do wzorca. `is` — Słowo kluczowe obsługuje następujące wzorce:

- [Wpisz wzór](#type), który sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.

- [Wzór stałej](#constant), która sprawdza, czy wyrażenie ma określoną wartość stałą.

- [wzorzec var](#var), dopasowania zawsze zakończy się pomyślnie i Nowa zmienna lokalna jest powiązana wartość wyrażenia. 

### <a name="type" /> Wpisz wzór </a>

W przypadku używania wzorca typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu. To proste rozszerzenie `is` instrukcję, która umożliwia ocenę zwięzły typ i konwersji. Ogólna postać `is` typu wzorzec jest:

```csharp
   expr is type varname 
```

gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu *typu* nazwę typu, do którego jest wynikiem *wyrażenie* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr* jest konwertowany, jeśli `is` test jest `true`. 

`is` Wyrażenie jest `true` Jeśli *expr* nie `null`, i jest spełniony jeden z następujących czynności:

- *wyrażenie* to wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*. Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.

- *wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*. *Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Jeśli *expr* jest `true` i `is` jest używana z `if` instrukcji, *nazwa_zmiennej* przypisano i ma zakres lokalny w ramach `if` tylko instrukcji.

W poniższym przykładzie użyto `is` wpisz wzór do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób. Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Wpisz wzór również generuje kod bardziej zwarty podczas określania typu o typie wartości. W poniższym przykładzie użyto `is` wpisz wzór, aby ustalić, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Równoważny kod bez dopasowywania do wzorca wymaga oddzielnych przypisania, które obejmuje jawnego rzutowania.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Wzór stałej ###

Podczas przeprowadzania dopasowywanie wzorca za wzór stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej. W języku C# 6 i starszych wersji wzór stałej jest obsługiwana przez [Przełącz](switch.md) instrukcji. Począwszy od języka C# 7.0 nie jest obsługiwany przez `is` także instrukcji. Jego składnia jest następująca:

```csharp
   expr is constant
```

gdzie *expr* jest wyrażenie do oceny, i *stałej* jest wartością do testowania. *Stała* może być dowolną z następujących stałych wyrażeń: 

- Wartość literału.

- Nazwa deklarowanej `const` zmiennej.

- Stała wyliczenia.

Stałe wyrażenie jest obliczane w następujący sposób:

- Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

Poniższy przykład łączy wzorców typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość skumulowane dice to 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Sprawdzanie `null` mogą być wykonywane przy użyciu wzorca stałej. `null` — Słowo kluczowe jest obsługiwana przez `is` instrukcji. Jego składnia jest następująca:

```csharp 
   expr is null
```

W poniższym przykładzie przedstawiono porównanie `null` sprawdza, czy:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <a name="var" /> wzorzec var </a>

Dopasowanie do wzorca za pomocą wzorca var zawsze kończy się powodzeniem. Jest jego składni

```csharp 
   expr is var varname
```

gdy wartość *expr* jest zawsze przypisywana do zmiennej lokalnej o nazwie *nazwa_zmiennej*. *nazwa_zmiennej* jest zmienna statyczna tego samego typu co *expr*. W poniższym przykładzie użyto wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`. Następnie wyświetla wartość i typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Należy pamiętać, że jeśli *expr* jest `null`, `is` wyrażenie nadal ma wartość true, przypisuje `null` do *nazwa_zmiennej*. 

## <a name="c-language-specification"></a>Specyfikacja języka C#
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
- [as](../../../csharp/language-reference/keywords/as.md)  
- [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
