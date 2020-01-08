---
title: Operatory dostępu do elementów C# członkowskich — odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można użyć w celu uzyskania dostępu do elementów członkowskich typu.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: e69cc5a9634f0b5232562782557645894f94ce2e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345303"
---
# <a name="member-access-operators-c-reference"></a>Operatory dostępu do elementówC# członkowskich (odwołanie)

Podczas uzyskiwania dostępu do elementu członkowskiego typu można użyć następujących operatorów:

- [`.` (dostęp do elementu członkowskiego)](#member-access-operator-): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu
- [`[]` (dostęp do elementu tablicy lub indeksatora)](#indexer-operator-): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu
- [`?.` i `?[]` (operatory warunkowe o wartości null)](#null-conditional-operators--and-): Aby wykonać operację dostępu do elementu członkowskiego lub tylko wtedy, gdy operand ma wartość różną od null
- [`()` (wywołanie)](#invocation-operator-): aby wywołać metodę dostępu lub wywołać delegata
- [`^` (indeks od końca)](#index-from-end-operator-): wskazuje, że pozycja elementu jest z końca sekwencji
- [`..` (zakres)](#range-operator-): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji

## <a name="member-access-operator-"></a>Operator dostępu do elementów członkowskich.

Token `.` służy do uzyskiwania dostępu do elementu członkowskiego przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:

- Użyj `.`, aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [dyrektywy`using`](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Użyj `.`, aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Użyj [dyrektywy`using`](../keywords/using-directive.md) , aby użyć kwalifikowanych nazw jako opcjonalnych.

- Użyj `.`, aby uzyskać dostęp do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)static i unstatic, jak pokazano w poniższym kodzie:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Możesz również użyć `.`, aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Indeksator — operator []

Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.

### <a name="array-access"></a>Dostęp do tablicy

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, zostanie zgłoszony <xref:System.IndexOutOfRangeException>.

Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.

Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp indeksatora

Poniższy przykład używa typu <xref:System.Collections.Generic.Dictionary%602> .NET do zademonstrowania dostępu indeksatora:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy. W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, parametry indeksatora mogą być zadeklarowane jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Inne użycie []

Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .

Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operatory warunkowe o wartości null?. lub? []

W C# wersji 6 i nowszych operator warunkowy o wartości null stosuje dostęp do elementu [członkowskiego](#member-access-operator-), `?.`lub [dostęp do elementów](#indexer-operator-), `?[]`, operacji do operandu tylko wtedy, gdy ten operand zwróci wartość różną od null; w przeciwnym razie zwraca `null`. Czyli

- Jeśli `a` oblicza `null`, wynik `a?.x` lub `a?[x]` jest `null`.
- Jeśli `a` ma wartość różną od null, wynik `a?.x` lub `a?[x]` jest taki sam jak wynik `a.x` lub `a[x]`.

  > [!NOTE]
  > Jeśli `a.x` lub `a[x]` zgłasza wyjątek, `a?.x` lub `a?[x]` zgłosi ten sam wyjątek dla niezerowego `a`. Na przykład jeśli `a` jest wystąpieniem tablicy o wartości innej niż null i `x` wykracza poza granice `a`, `a?[x]` spowodowałaby zgłoszenie <xref:System.IndexOutOfRangeException>.

Operatory warunkowe `null` skracają łańcuch wykonywania operacji. Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub dostępu do elementu zwraca `null`, reszta łańcucha nie zostanie wykonana. W poniższym przykładzie `B` nie zostanie oceniona, jeśli `A` szacuje się w `null` i `C` nie zostanie oceniona, jeśli `A` lub `B` oblicza `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Poniższy przykład ilustruje użycie operatorów `?.` i `?[]`:

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Powyższy przykład używa również [operatora łączenia wartości null `??`](null-coalescing-operator.md) , aby określić alternatywne wyrażenie do obliczenia w przypadku, gdy wynik operacji warunkowej o wartości null jest `null`.

Operator dostępu warunkowego o wartości null `?.` jest również znany jako operator Elvis.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegowania bezpiecznego wątku

Użyj operatora `?.`, aby sprawdzić, czy delegat ma wartość różną od null i wywoływać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:

```csharp
PropertyChanged?.Invoke(…)
```

Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w C# 5 lub wcześniejszych wersjach:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Operator wywołania ()

Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).

Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą operatora [`new`](new-operator.md) należy również użyć nawiasów.

### <a name="other-usages-of-"></a>Inne użycie ()

Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu. Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).

[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.

## <a name="index-from-end-operator-"></a>Indeks z operatora końcowego ^

Dostępne w C# 8,0 i nowszych `^` operator wskazuje położenie elementu od końca sekwencji. Dla sekwencji `^n` `length`długość wskazuje element z przesunięciem `length - n` od początku sekwencji. Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

Jak pokazano w poprzednim przykładzie, `^e` Expression jest typu <xref:System.Index?displayProperty=nameWithType>. W `^e`Expression wynik `e` musi być niejawnie konwertowany na `int`.

Można też użyć operatora `^` z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów. Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operator zakresu..

Dostępne w C# 8,0 i nowszych operator `..` określa początek i koniec zakresu indeksów jako operandy. Argument operacji po lewej stronie *jest początkową* częścią zakresu. Prawy operand jest *wyłącznym* końcem zakresu. Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

Jak pokazano w poprzednim przykładzie, `a..b` Expression jest typu <xref:System.Range?displayProperty=nameWithType>. W `a..b`wyrażeń wyniki `a` i `b` muszą być niejawnie konwertowane na `int` lub <xref:System.Index>.

Możesz pominąć dowolny operand operatora `..`, aby uzyskać otwarty zakres:

- `a..` jest równoznaczna z `a..^0`
- `..b` jest równoznaczna z `0..b`
- `..` jest równoznaczna z `0..^0`

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `.`, `()`, `^`i `..` nie mogą być przeciążone. Operator `[]` jest również traktowany jako operator niepodlegający obciążeniu. Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementu](~/_csharplang/spec/expressions.md#element-access)
- [Operator warunkowy o wartości null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [?? (operator łączenia wartości null)](null-coalescing-operator.md)
- [:: operator](namespace-alias-qualifier.md)
