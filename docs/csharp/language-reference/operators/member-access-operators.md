---
title: Operatory dostępu do elementów członkowskich — C# odwołania
description: Dowiedz się więcej o C# operatorów, które umożliwiają dostęp do elementów członkowskich typu.
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
ms.openlocfilehash: eec70f5446eec11fa4e241b86eed4ed8d6146f85
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195780"
---
# <a name="member-access-operators-c-reference"></a>Operatory dostępu do składowych (C# odwołania)

Gdy uzyskujesz dostęp do składowej typu można używać następujących operatorów:

- [`.` (dostęp do elementu członkowskiego) ](#member-access-operator-): do uzyskania dostępu do członka przestrzeni nazw lub typ
- [`[]` (element lub indeksator dostęp do tablicy) ](#indexer-operator-): Aby uzyskać dostęp do elementu tablicy i indeksatora typu
- [`?.` i `?[]` (operatorów warunkowych działających z wartością null)](#null-conditional-operators--and-): do wykonywania operacji dostępu do elementu członkowskiego lub elementu, tylko wtedy, gdy argument jest różna od null
- [`()` (wywołanie) ](#invocation-operator-): wywoływanie metody dostępu lub wywołanie delegata

## <a name="member-access-operator-"></a>Operator dostępu do elementu członkowskiego.

Możesz użyć `.` token w celu uzyskania dostępu do członka przestrzeni nazw lub typ, jak w poniższych przykładach pokazano:

- Użyj `.` dostępu zagnieżdżone przestrzenie nazw w przestrzeni nazw, w poniższym przykładzie z do [ `using` dyrektywy](../keywords/using-directive.md) pokazuje:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Użyj `.` do formularza *kwalifikowana nazwa* uzyskiwać dostęp do typu, w przestrzeni nazw, co ilustruje poniższy kod:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Użyj [ `using` dyrektywy](../keywords/using-directive.md) powoduje użycie kwalifikowane nazwy są opcjonalne.

- Użyj `.` dostęp do [elementy członkowskie typu](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, co ilustruje poniższy kod:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Można również użyć `.` dostęp do [— metoda rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Indeksator operator]

Nawiasy kwadratowe `[]`, są zwykle używane do dostępu do elementu tablicy, indeksator lub wskaźnika.

### <a name="array-access"></a>Dostęp do tablicy

Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy jest poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> zgłaszany.

Jak pokazano na poprzednim przykładzie, możesz także użyć nawiasami kwadratowymi podczas deklarowania typu tablicowego lub tworzy wystąpienie tablicy.

Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp indeksatora

W poniższym przykładzie użyto .NET <xref:System.Collections.Generic.Dictionary%602> typu, aby zademonstrować dostęp indeksatora:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Indeksatory pozwalają na indeks wystąpienia typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy. W przeciwieństwie do tablicy wskaźników, które musi być liczbą całkowitą, argumenty indeksator może być zadeklarowana jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Inne sposoby użycia]

Uzyskać informacji o dostępie do elementu wskaźnika, zobacz [wskaźnika elementu dostępu operator []](pointer-related-operators.md#pointer-element-access-operator-) części [wskaźnik związane z operatorów](pointer-related-operators.md) artykułu.

Nawiasy kwadratowe również służy do określania [atrybuty](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operatory warunkowe null? i? []

Dostępne w C# 6 i nowsze, operatorów warunkowych działających z wartością null dotyczy dostęp do elementu członkowskiego `?.`, lub dostęp do elementu `?[]`, operacja argumentem operacji tylko wtedy, gdy ten argument operacji ma inną niż null. Jeśli argument daje w wyniku `null`, wynik zastosowania operatora jest `null`. Operator dostępu do elementu członkowskiego warunkowe null `?.` jest także znana jako Elvis operator.

Operatory warunkowe `null` skracają łańcuch wykonywania operacji. Oznacza to, jeśli jedna operacja w łańcuchu warunkowa składowa lub elementu dostępu do operacji zwraca `null`, pozostała część łańcucha nie jest wykonywany. W poniższym przykładzie `B` nie jest oceniany, jeśli `A` daje w wyniku `null` i `C` nie jest oceniany, jeśli `A` lub `B` daje w wyniku `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

W poniższym przykładzie pokazano użycie `?.` i `?[]` operatory:

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Powyższy przykład pokazuje również użycie [operatorem łączenia wartości null](null-coalescing-operator.md). Można na przykład operatora łączenia wartości null do zapewnienia alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem operacji warunkowych działających z wartością null `null`.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegata metodą o bezpiecznych wątkach

Użyj `?.` operatora, sprawdź, czy obiekt delegowany jest inna niż null i wywoływać ją w sposób wątkowo (na przykład, gdy użytkownik [wywołać zdarzenie](../../../standard/events/how-to-raise-and-consume-events.md)), jak pokazano w poniższym kodzie:

```csharp
PropertyChanged?.Invoke(…)
```

Czy kod jest odpowiednikiem następujący kod, który zostanie wykorzystany w C# 5 lub starszy:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Wywołanie — operator)

Użyj nawiasów, `()`, aby wywołać [metoda](../../programming-guide/classes-and-structs/methods.md) lub wywołaj [delegować](../../programming-guide/delegates/index.md).

Poniższy przykład pokazuje sposób wywołania metody, z lub bez argumentów i wywołanie delegata:

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Można także użyć nawiasów podczas wywołujesz [Konstruktor](../../programming-guide/classes-and-structs/constructors.md) z [ `new` ](../keywords/new-operator.md) operatora.

### <a name="other-usages-of-"></a>Inne sposoby użycia)

Możesz także użyć nawiasów, aby określić kolejność, w którym ma być operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu. Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).

[Rzutowane wyrażenia,](invocation-operator.md#cast-expression), który wywołać operatora konwersji, należy również użyć nawiasów.

## <a name="operator-overloadability"></a>Overloadability — operator

`.` i `()` nie mogą być przeciążone operatory. `[]` Operator jest traktowana jako inne niż z możliwością przeciążenia operatora. Użyj [indeksatory](../../programming-guide/indexers/index.md) do obsługi indeksowanie z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementu](~/_csharplang/spec/expressions.md#element-access)
- [Operatorów warunkowych działających z wartością null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [?? (z operatorem łączenia wartości null)](null-coalescing-operator.md)
