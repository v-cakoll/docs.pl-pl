---
title: Operatory dostępu do elementów C# członkowskich — odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można użyć w celu uzyskania dostępu do elementów członkowskich typu.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 5ff5e68fbce320076e6d18e9e139b418a15bba77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924641"
---
# <a name="member-access-operators-c-reference"></a>Operatory dostępu do elementówC# członkowskich (odwołanie)

Podczas uzyskiwania dostępu do elementu członkowskiego typu mogą być używane następujące operatory:

- [(dostęp do elementu członkowskiego): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu `.` ](#member-access-operator-)
- [(dostęp do elementu tablicy lub indeksatora): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu `[]` ](#indexer-operator-)
- [and (operatory warunkowe o wartości null): do wykonywania operacji dostępu do elementu członkowskiego lub elementów tylko wtedy, gdy operand ma wartość różną od null `?[]` `?.` ](#null-conditional-operators--and-)
- (wywołanie): aby wywołać metodę dostępu lub wywołać delegata [ `()` ](#invocation-operator-)

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

Aby uzyskać więcej informacji na temat indeksatorów [](../../programming-guide/indexers/index.md), zobacz indeksatory.

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

Użyj operatora `?.` , aby sprawdzić, czy delegat ma wartość różną od null i wywołać go w sposób bezpieczny dla wątków (na przykład po podniesieniu [zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:

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

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `.` i`()` nie mogą być przeciążone. `[]` Operator jest również traktowany jako operator niepodlegający obciążeniu. Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

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
