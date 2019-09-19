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
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116125"
---
# <a name="member-access-operators-c-reference"></a>Operatory dostępu do elementówC# członkowskich (odwołanie)

Podczas uzyskiwania dostępu do elementu członkowskiego typu mogą być używane następujące operatory:

- [(dostęp do elementu członkowskiego): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu `.` ](#member-access-operator-)
- [(dostęp do elementu tablicy lub indeksatora): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu `[]` ](#indexer-operator-)
- [and (operatorywarunkoweowartościnull):dowykonywaniaoperacjidostępudoelementuczłonkowskiegolubelementówtylkowtedy,gdyoperandmawartośćróżnąodnull`?[]` `?.` ](#null-conditional-operators--and-)
- (wywołanie): aby wywołać metodę dostępu lub wywołać delegata [ `()` ](#invocation-operator-)
- [(indeks od końca): wskazuje, że pozycja elementu jest z końca sekwencji `^` ](#index-from-end-operator-)
- (zakres): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji [ `..` ](#range-operator-)

## <a name="member-access-operator-"></a>Operator dostępu do elementów członkowskich.

`.` Token służy do uzyskiwania dostępu do składowej przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:

- Użyj `.` , aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [ `using` dyrektywy](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Użyj `.` , aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Użyj dyrektywy, aby użyć kwalifikujących się nazw jako opcjonalnych. [ `using` ](../keywords/using-directive.md)

- Służy `.` do uzyskiwania dostępu do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)statycznego i niestatycznego, jak pokazano w poniższym kodzie:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Można również użyć `.` , aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Indeksator — operator []

Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.

### <a name="array-access"></a>Dostęp do tablicy

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> jest zgłaszany.

Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.

Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp indeksatora

Poniższy przykład używa typu .NET <xref:System.Collections.Generic.Dictionary%602> do zademonstrowania dostępu indeksatora:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy. W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, argumenty indeksatora mogą być zadeklarowane jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Inne użycie []

Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .

Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operatory warunkowe o wartości null?. lub? []

Operator warunkowy, który jest dostępny w C# wartości 6 i nowszych, ma zastosowanie do `?.`elementu członkowskiego, lub `?[]`dostępu do elementów, operacji do jego operandu tylko wtedy, gdy ten operand ma wartość różną od null. Jeśli argument ma wartość `null`, wynik zastosowania operatora to. `null` Operator `?.` dostępu warunkowego o wartości null jest również znany jako operator Elvis.

Operatory warunkowe `null` skracają łańcuch wykonywania operacji. Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub `null`dostępu do elementu zwraca, reszta łańcucha nie jest wykonywana. W poniższym przykładzie nie jest `B` oceniana, jeśli `A` jest obliczana wartość `null` i `C` nie jest szacowana, `A` Jeśli `B` lub szacuje `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Poniższy przykład ilustruje użycie `?.` operatorów i: `?[]`

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

W poprzednim przykładzie pokazano także użycie [operatora łączenia wartości null](null-coalescing-operator.md). Możesz użyć operatora łączenia wartości null, aby podać alternatywne wyrażenie do obliczenia w przypadku, gdy wynikiem operacji warunkowej jest `null`wartość null.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegowania bezpiecznego wątku

Użyj operatora `?.` , aby sprawdzić, czy delegat ma wartość różną od null i wywołać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:

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

Użyj nawiasów, `()`,, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).

Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą [`new`](new-operator.md) operatora należy również użyć nawiasów.

### <a name="other-usages-of-"></a>Inne użycie ()

Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu. Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).

[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.

## <a name="index-from-end-operator-"></a>Indeks z operatora końcowego ^

Dostępne w C# 8,0 i nowszych, `^` operator wskazuje położenie elementu od końca sekwencji. Dla sekwencji o długości `length` `^n` wskazuje element z przesunięciem `length - n` od początku sekwencji. Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

Jak pokazano w powyższym przykładzie `^e` , wyrażenie jest <xref:System.Index?displayProperty=nameWithType> typu. W wyrażeniu `^e` `e` wynik musi być niejawnie konwertowany na `int`.

Można też użyć `^` operatora z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów. Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operator zakresu..

Dostępne w C# 8,0 i nowszych, `..` operator określa początek i koniec zakresu indeksów jako operandy. Argument operacji po lewej stronie *jest początkową* częścią zakresu. Prawy operand jest *wyłącznym* końcem zakresu. Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

Jak pokazano w powyższym przykładzie `a..b` , wyrażenie jest <xref:System.Range?displayProperty=nameWithType> typu. W wyrażeniu `a..b` `a` wyniki i `b` muszą być niejawnie konwertowane na `int` lub <xref:System.Index>.

Możesz pominąć dowolny operand `..` operatora, aby uzyskać otwarty zakres:

- `a..`jest równoważne`a..^0`
- `..b`jest równoważne`0..b`
- `..`jest równoważne`0..^0`

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `.`, `()`, `^`i niemogąbyćprzeciążone.`..` `[]` Operator jest również traktowany jako operator niepodlegający obciążeniu. Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementu](~/_csharplang/spec/expressions.md#element-access)
- [Operator warunkowy o wartości null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [?? (operator łączenia wartości null)](null-coalescing-operator.md)
- [:: operator](namespace-alias-qualifier.md)
