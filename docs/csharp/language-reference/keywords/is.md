---
title: is (odwołanie w C#)
keywords: to — słowo kluczowe (C#), (C#)
ms.date: 02/17/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f0242439caa21268a6c314409f41587890c4126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="is-c-reference"></a>is (odwołanie w C#) #

Sprawdza, czy obiekt jest zgodny z danego typu, lub (począwszy od C# 7) testów wyrażenia do wzorca.

## <a name="testing-for-type-compatibility"></a>Testowanie zgodności typu ##

`is` — Słowo kluczowe ocenia zgodność typu w czasie wykonywania. Określa, czy wystąpienie obiektu lub można przekonwertować na określony typ wyniku wyrażenia. Ma ona składni

```csharp
   expr is type
```

gdzie *wyrażenie* wyrażenie obliczane do wystąpienia typu, i *typu* jest nazwa typu, do którego wynik *wyrażenie* do konwertowania. `is` Instrukcja jest `true` Jeśli *wyrażenie* jest inne niż null i wyniki z obliczenie wyrażenia można przekonwertować na obiekt *typu*; w przeciwnym razie zwraca `false`.

Na przykład następujący kod określa, czy `obj` mogą być rzutowane na wystąpienie `Person` typu:

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

`is` Instrukcja jest wartość true, jeśli:

- *wyrażenie* jest wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu pochodzącego od *typu*. Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.

- *wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu* . *Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

W poniższym przykładzie pokazano, że `is` wyrażenie ma `true` dla każdego z tych konwersji.

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

`is` — Słowo kluczowe generuje ostrzeżenie kompilacji, jeśli wiadomo, że wyrażenie zawsze być `true` lub `false`. Traktuje tylko konwersje odwołań, konwersje boxing i konwersji unboxing; nie traktuje konwersje zdefiniowane przez użytkownika lub konwersje zdefiniowane przez określony typ [niejawne](implicit.md) i [jawne](explicit.md) operatorów. Poniższy przykład generuje ostrzeżenia, ponieważ wynik konwersji jest znany w czasie kompilacji. Należy pamiętać, że `is` wyrażenie dla konwersji z `int` do `long` i `double` zwraca wartość false, ponieważ te konwersje są obsługiwane przez [niejawne](implicit.md) operatora.

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr`może być dowolnym wyrażenie zwracające wartość, z wyjątkiem metody anonimowe i wyrażenia lambda. W poniższym przykładzie użyto `is` do oceny, zwracana wartość wywołania metody.   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Począwszy od C# 7, można użyć dopasowywanie do wzorca za [wzorzec typu](#type) do pisania kodu bardziej zwięzły, który używa `is` instrukcji.

## <a name="pattern-matching-with-is"></a>Dopasowywanie do wzorca z`is` ##

Począwszy od C# 7, `is` i [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcje obsługuje dopasowywania do wzorca. `is` — Słowo kluczowe obsługuje następujące wzorce:

- [Wzorzec typu](#type), która sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu.

- [Stałe wzorzec](#constant), która sprawdza, czy wyrażenie ma określoną wartość stałą.

- [var — wzorzec](#var), dopasowanie, która zawsze kończy się powodzeniem i wiąże wartość wyrażenia do zmiennej lokalnej. 

### <a name="type" />Wzorzec typu</a>

Korzystając ze wzorcem typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu. Jest prosta rozszerzenie `is` instrukcji, która umożliwia ocenę zwięzła, typ i konwersji. Ogólny kształt `is` typu wzorzec jest:

```csharp
   expr is type varname 
```

gdzie *wyrażenie* wyrażenie obliczane do wystąpienia typu niektórych *typu* jest nazwa typu, do którego wynik *wyrażenie* należy skonwertować i *nazwa_zmiennej* obiektu, do którego wynik *wyrażenie* przekonwertowaniu Jeśli `is` testu jest `true`. 

`is` Wyrażenie jest `true` Jeśli jest spełniony jeden z następujących czynności:

- *wyrażenie* jest wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu pochodzącego od *typu*. Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.

- *wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu* . *Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Jeśli *exp* jest `true` i `is` jest używany z `if` instrukcji, *nazwa_zmiennej* przypisano i ma zasięg lokalny w `if` tylko instrukcji.

W poniższym przykładzie użyto `is` typu wzorzec do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez wzorca dopasowania, ten kod może być zapisana w następujący sposób. Użycie typu dopasowanie wzorca tworzy kodu mniejszych, który może zostać odczytany, eliminując konieczność, aby sprawdzić, czy wynik konwersji jest `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Wzorzec typu tworzy również mniejszych kodu podczas określania typu typu wartości. W poniższym przykładzie użyto `is` typu wzorzec do ustalenia, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości. 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Odpowiednik kodu bez dopasowywania do wzorca wymaga oddzielnych przypisania, która obejmuje jawnego rzutowania.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" />Stałe wzorzec ###

Podczas wykonywania dopasowywanie do wzorca z wzorcem stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej. W języku C# 6 i wcześniejszych wersjach stałe wzorzec jest obsługiwany przez [przełącznika](switch.md) instrukcji. Począwszy od C# 7, nie jest obsługiwany przez `is` również instrukcji. Składnia to:

```csharp
   expr is constant
```

gdzie *wyrażenie* jest wyrażenie do oceny, i *stałej* jest wartość do testowania. *Stała* może być dowolny z następujących wyrażenia stałe: 

- Wartość literału.

- Nazwy deklarowanych `const` zmiennej.

- Stała wyliczenia.

Stałe wyrażenie jest obliczane w następujący sposób:

- Jeśli *wyrażenie* i *stałej* są typy całkowite operator równości C# Określa, czy wyrażenie zwraca `true` (to znaczy czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie do statycznego [Object.Equals (wyrażenie stałej)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

Poniższy przykład łączy wzorce typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość zbiorczego selekcji jest 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" />var — wzorzec</a>

Wzorzec dopasowania wzorca var zawsze kończy się powodzeniem. Składnia może się

```csharp 
   expr is var varname
```

Jeżeli wartość *wyrażenie* jest zawsze przypisywana do zmiennej lokalnej o nazwie *nazwa_zmiennej*. *nazwa_zmiennej* jest zmienna statyczna tego samego typu co *wyrażenie*. Poniższy przykład korzysta ze wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`. Następnie wyświetla wartości i typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Należy pamiętać, że jeśli *wyrażenie* jest `null`, `is` wyrażenie nadal ma wartość true i przypisuje `null` do *nazwa_zmiennej*. 

# <a name="c-language-specification"></a>Specyfikacja języka C#
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [TypeOf](../../../csharp/language-reference/keywords/typeof.md)  
 [jako](../../../csharp/language-reference/keywords/as.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
