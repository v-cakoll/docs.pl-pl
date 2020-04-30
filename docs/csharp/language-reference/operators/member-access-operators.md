---
title: Operatory dostępu do elementów członkowskich i wyrażenia — odwołanie w C#
description: Informacje na temat operatorów języka C#, których można użyć w celu uzyskania dostępu do elementów członkowskich typu.
ms.date: 04/17/2020
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
ms.openlocfilehash: 86c8cce79e447bee638e1c5c7cb2fdbc64f630f3
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595900"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Operatory i wyrażenia dostępu do składowych (odwołanie w C#)

Podczas uzyskiwania dostępu do elementu członkowskiego typu można użyć następujących operatorów i wyrażeń:

- [(dostęp do elementu członkowskiego): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu `.` ](#member-access-expression-)
- [(dostęp do elementu tablicy lub indeksatora): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu `[]` ](#indexer-operator-)
- [and `?[]` operatory warunkowe o wartości null): do wykonywania operacji dostępu do elementu członkowskiego lub elementów tylko wtedy, gdy operand ma wartość różną `?.` ](#null-conditional-operators--and-)od null
- (wywołanie): aby wywołać metodę dostępu lub wywołać delegata [ `()` ](#invocation-expression-)
- [(indeks od końca): wskazuje, że pozycja elementu jest z końca sekwencji `^` ](#index-from-end-operator-)
- (zakres): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Wyrażenie dostępu do elementu członkowskiego.

`.` Token służy do uzyskiwania dostępu do składowej przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:

- Użyj `.` , aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [ `using` dyrektywy](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Użyj `.` , aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Użyj [ `using` dyrektywy](../keywords/using-directive.md) , aby użyć kwalifikujących się nazw jako opcjonalnych.

- Służy `.` do uzyskiwania dostępu do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)statycznego i niestatycznego, jak pokazano w poniższym kodzie:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Można również użyć `.` , aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Indeksator — operator []

Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.

### <a name="array-access"></a>Dostęp do tablicy

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> jest zgłaszany.

Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.

Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp indeksatora

Poniższy przykład używa typu .NET <xref:System.Collections.Generic.Dictionary%602> do zademonstrowania dostępu indeksatora:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

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

W języku C# 6 i nowszych operator warunkowy o wartości null stosuje dostęp do elementu [Członkowskiego](#member-access-expression-), `?.`, lub dostęp `?[]`do [elementów](#indexer-operator-), operacji do operandu tylko wtedy, gdy ten operand ma wartość różną od null; w przeciwnym razie zwraca `null`. Czyli

- Jeśli `a` jest wynikiem obliczenia `null`, wynik `a?.x` lub `a?[x]` jest. `null`
- Jeśli `a` ma wartość różną od null, `a?.x` wynik lub `a?[x]` jest taki sam jak wynik `a.x` lub `a[x]`, odpowiednio.

  > [!NOTE]
  > Jeśli `a.x` lub `a[x]` zgłasza wyjątek `a?.x` lub `a?[x]` zgłosi ten sam wyjątek dla wartości innej niż null. `a` Na przykład `a` jeśli jest wystąpieniem tablicy o wartości innej niż null `x` i znajduje się poza granicami `a`, `a?[x]` zostałby zgłosić <xref:System.IndexOutOfRangeException>.

Operatory warunkowe o wartości null są krótkimi obwodami. Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub `null`dostępu do elementu zwraca, reszta łańcucha nie jest wykonywana. W poniższym przykładzie nie jest `B` oceniana, jeśli `A` jest obliczana wartość `null` i `C` nie jest szacowana, `A` Jeśli `B` lub szacuje `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Poniższy przykład ilustruje użycie operatorów `?.` i: `?[]`

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

Poprzedni przykład używa również [operatora `??` łączenia wartości null](null-coalescing-operator.md) , aby określić alternatywne wyrażenie do obliczenia w przypadku, gdy wynikiem operacji warunkowej jest `null`wartość null.

Jeśli `a.x` lub `a[x]` ma typ `T`wartości niedopuszczający `a?.x` wartości null lub `a?[x]` ma odpowiedni [Typ](../builtin-types/nullable-value-types.md) `T?`wartości null. Jeśli potrzebujesz wyrażenia typu `T`, Zastosuj operator `??` łączenia wartości null do wyrażenia warunkowego null, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

W powyższym przykładzie, `??` Jeśli nie używasz operatora, `numbers?.Length < 2` program oblicza wartość, `false` gdy `numbers` jest `null`.

Operator `?.` dostępu warunkowego o wartości null jest również znany jako operator Elvis.

> [!NOTE]
> W języku C# 8 operatory warunkowe o wartości null współdziałają z [operatorem łagodniejszej o wartości null](null-forgiving.md) w nieoczekiwany sposób. Na przykład wyrażenie `x?.y!.z` jest analizowane jako `(x?.y)!.z`. Ze względu na tę `z` interpretację, jest `x` oceniane `null`, nawet jeśli jest, co <xref:System.NullReferenceException>może skutkować.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegowania bezpiecznego wątku

Użyj operatora `?.` , aby sprawdzić, czy delegat ma wartość różną od null i wywołać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:

```csharp
PropertyChanged?.Invoke(…)
```

Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w języku C# 5 lub wcześniejszym:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

Jest to bezpieczny wątkowo sposób, aby upewnić się, że wywoływany `handler` jest tylko element inny niż null. Ponieważ wystąpienia delegatów są niezmienne, żaden wątek nie może zmienić wartości, `handler` do której odwołuje się zmienna lokalna. W szczególności, jeśli kod wykonywany przez inny wątek anuluje `PropertyChanged` subskrypcję zdarzenia i `PropertyChanged` pozostanie `null` przed `handler` wywołaniem, wartość, do której odwołuje się `handler` pozostanie nienaruszona. `?.` Operator oblicza swój argument operacji po lewej stronie nie więcej niż raz, gwarantując, że nie można go zmienić do `null` po sprawdzeniu wartości innej niż null.

## <a name="invocation-expression-"></a>Wyrażenie wywołania ()

Użyj nawiasów, `()`,, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).

Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą [`new`](new-operator.md) operatora należy również użyć nawiasów.

### <a name="other-usages-of-"></a>Inne użycie ()

Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu. Aby uzyskać więcej informacji, zobacz [operatory języka C#](index.md).

[Wyrażenia rzutowania](type-testing-and-cast.md#cast-expression), które wykonują jawne konwersje typów, również używają nawiasów.

## <a name="index-from-end-operator-"></a>Indeks z operatora końcowego ^

Dostępne w języku C# 8,0 i nowszych, `^` operator wskazuje położenie elementu od końca sekwencji. Dla sekwencji o długości `length` `^n` wskazuje element z przesunięciem `length - n` od początku sekwencji. Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Jak pokazano w powyższym przykładzie `^e` , wyrażenie jest <xref:System.Index?displayProperty=nameWithType> typu. W wyrażeniu `^e`wynik `e` musi być niejawnie konwertowany na. `int`

Można również użyć `^` operatora z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów. Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operator zakresu..

Dostępne w języku C# 8,0 i nowszych, `..` operator określa początek i koniec zakresu indeksów jako operandy. Argument operacji po lewej stronie *jest początkową* częścią zakresu. Prawy operand jest *wyłącznym* końcem zakresu. Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Jak pokazano w powyższym przykładzie `a..b` , wyrażenie jest <xref:System.Range?displayProperty=nameWithType> typu. W wyrażeniu `a..b`wyniki `a` i `b` muszą być niejawnie konwertowane na `int` lub. <xref:System.Index>

Możesz pominąć dowolny operand `..` operatora, aby uzyskać otwarty zakres:

- `a..`jest równoważne`a..^0`
- `..b`jest równoważne`0..b`
- `..`jest równoważne`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `.`, `()`, `^`i `..` nie mogą być przeciążone. `[]` Operator jest również traktowany jako operator niepodlegający obciążeniu. Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):

- [Dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementu](~/_csharplang/spec/expressions.md#element-access)
- [Operator warunkowy o wartości null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [?? (operator łączenia wartości null)](null-coalescing-operator.md)
- [:: — Operator](namespace-alias-qualifier.md)
