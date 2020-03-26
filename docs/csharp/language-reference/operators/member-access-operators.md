---
title: Operatory i wyrażenia dostępu do elementów członkowskich — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można użyć do uzyskania dostępu do elementów członkowskich typu.
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
ms.openlocfilehash: da2ca4517bd007678d74ae9b76e10cad4c2696b4
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546643"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Operatory i wyrażenia dostępu do elementów członkowskich (odwołanie do języka C#)

Podczas uzyskiwania dostępu do elementu członkowskiego typu można używać następujących operatorów i wyrażeń:

- (dostęp członkowski) : aby uzyskać dostęp do członka obszaru nazw lub typu [ `.` ](#member-access-expression-)
- [(dostęp do elementu tablicy lub indeksatora): aby uzyskać dostęp do elementu tablicy lub indeksatora typów `[]` ](#indexer-operator-)
- [i `?[]` (operatory warunkowe zerowe): aby wykonać operację dostępu do elementu członkowskiego lub elementu tylko wtedy, gdy operand jest nieuprawny `?.` ](#null-conditional-operators--and-)
- (wywołanie) : wywołać metodę dostępną lub wywołać pełnomocnika [ `()` ](#invocation-expression-)
- (indeks od końca) : aby wskazać, że pozycja elementu znajduje się od końca sekwencji [ `^` ](#index-from-end-operator-)
- (zakres) : określenie zakresu wskaźników, których można użyć do uzyskania zakresu elementów sekwencji [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Wyrażenie dostępu do elementu członkowskiego .

Token służy `.` do uzyskiwania dostępu do elementu członkowskiego obszaru nazw lub typu, jak pokazano w poniższych przykładach:

- Służy `.` do uzyskiwania dostępu do zagnieżdżonego obszaru nazw w obszarze nazw, zgodnie z poniższym przykładem [ `using` dyrektywy:](../keywords/using-directive.md)

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Służy `.` do tworzenia *nazwy kwalifikowanej,* aby uzyskać dostęp do typu w obszarze nazw, jak pokazano w następującym kodzie:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Użyj [ `using` dyrektywy,](../keywords/using-directive.md) aby używać kwalifikowanych nazw opcjonalnie.

- Służy `.` do uzyskiwania dostępu do [elementów członkowskich typu,](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, jak pokazuje następujący kod:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Można również `.` użyć, aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operator indeksatora []

Nawiasy kwadratowe , `[]`są zwykle używane dla dostępu do tablicy, indeksatora lub elementu wskaźnika.

### <a name="array-access"></a>Dostęp do tablicy

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy znajduje się poza granicami odpowiedniego <xref:System.IndexOutOfRangeException> wymiaru tablicy, jest generowany.

Jak pokazano w poprzednim przykładzie, należy również użyć nawiasów kwadratowych podczas deklarowania typu tablicy lub wystąpienia wystąpienia tablicy.

Aby uzyskać więcej informacji o tablicach, zobacz [Tablice](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp do indeksatora

W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602> użyto typu .NET, aby zademonstrować dostęp do indeksatora:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy. W przeciwieństwie do indeksów tablicowych, które muszą być liczby całkowitej, parametry indeksatora mogą być zadeklarowane jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [Indeksatory](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Inne zastosowania []

Aby uzyskać informacje na temat dostępu do elementu wskaźnika, zobacz [operator dostępu do elementu wskaźnik []](pointer-related-operators.md#pointer-element-access-operator-) sekcji [operatorów związanych z wskaźnikiem.](pointer-related-operators.md)

Nawiasy kwadratowe są również używane do określania [atrybutów:](../../programming-guide/concepts/attributes/index.md)

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operatory warunkowe zerowe?. I? []

Dostępne w języku C# 6 i nowszych, operator `?.`warunkowy null stosuje dostęp elementu [członkowskiego](#member-access-expression-), lub [dostęp do elementu](#indexer-operator-), `?[]`operacji do jego operand tylko wtedy, gdy operand ocenia non-null; w przeciwnym `null`razie zwraca . Czyli

- Jeśli `a` ocenia `null`się , `a?.x` wynik `a?[x]` `null`lub jest .
- Jeśli `a` ma wartość `a?.x` nienawiązaną, `a?[x]` wynik lub jest `a.x` taki `a[x]`sam jak wynik lub , odpowiednio.

  > [!NOTE]
  > Jeśli `a.x` `a[x]` lub zgłasza `a?.x` wyjątek `a?[x]` lub zgłosić ten sam `a`wyjątek dla innych niż null . Na przykład, `a` jeśli jest instancją tablicy `a`innej `a?[x]` niż <xref:System.IndexOutOfRangeException>null i `x` znajduje się poza granicami , będzie rzutować .

Operatory warunkowe zerowe są zwarcie. Oznacza to, że jeśli jedna operacja w łańcuchu `null`operacji dostępu do elementu warunkowego lub elementu zwraca, reszta łańcucha nie jest wykonywana. W poniższym `B` przykładzie nie `A` jest `null` oceniana, jeśli ocenia `C` i nie jest oceniana, jeśli `A` lub `B` `null`ocenia:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Poniższy przykład pokazuje użycie `?.` i `?[]` operatorów:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

W poprzednim przykładzie użyto również [operatora `??` scalania null,](null-coalescing-operator.md) aby określić alternatywne wyrażenie do oceny `null`w przypadku, gdy wynikiem operacji warunkowej zerowej jest .

Operator `?.` dostępu warunkowego null jest również znany jako operator Elvis.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegata bezpieczne dla wątków

`?.` Operator służy do sprawdzania, czy pełnomocnik jest nie-null i wywołać go w sposób bezpieczny dla wątków (na przykład podczas wywoływania zdarzenia ), jak pokazano w [poniższym](../../../standard/events/how-to-raise-and-consume-events.md)kodzie:

```csharp
PropertyChanged?.Invoke(…)
```

Ten kod jest odpowiednikiem następującego kodu, który można użyć w języku C# 5 lub wcześniej:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a>Wyrażenie wywołania ()

Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [pełnomocnika](../../programming-guide/delegates/index.md).

W poniższym przykładzie pokazano, jak wywołać metodę, z argumentami lub bez argumentów i wywołać delegata:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Nawiasy są również używane podczas wywoływania [konstruktora](../../programming-guide/classes-and-structs/constructors.md) z operatorem. [`new`](new-operator.md)

### <a name="other-usages-of-"></a>Inne zastosowania ()

Nawiasy są również używane do dostosowywania kolejności, w jakiej mają być oceniane operacje w wyrażeniu. Aby uzyskać więcej informacji, zobacz [operatory języka C#.](index.md)

[Wyrażenia rzutowe,](type-testing-and-cast.md#cast-operator-)które wykonują jawne konwersje typu, również używają nawiasów.

## <a name="index-from-end-operator-"></a>Indeks od operatora końcowego ^

Dostępne w języku C# 8.0 i nowszych, `^` operator wskazuje położenie elementu od końca sekwencji. Dla sekwencji `length`długości `^n` wskazuje element z `length - n` przesunięciem od początku sekwencji. Na przykład `^1` wskazuje ostatni element sekwencji `^length` i wskazuje na pierwszy element sekwencji.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Jak pokazano w poprzednim `^e` przykładzie, <xref:System.Index?displayProperty=nameWithType> wyrażenie jest typu. W `^e`wyrażeniu `e` wynik musi być `int`niejawnie wymienialny na .

Operator z `^` [operatorem zakresu](#range-operator-) służy również do tworzenia zakresu indeksów. Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operator zasięgu ..

Dostępne w języku C# 8.0 i nowszych, `..` operator określa początek i koniec zakresu indeksów jako jego operandy. Po lewej stronie operand jest *integracyjnym* początkiem zakresu. Operand po prawej stronie to *ekskluzywny* koniec szeregu. Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Jak pokazano w poprzednim `a..b` przykładzie, <xref:System.Range?displayProperty=nameWithType> wyrażenie jest typu. W `a..b`wyrazie , `a` `b` wyniki i muszą być `int` <xref:System.Index>w sposób dorozumiany wymienialne lub .

Można pominąć dowolny z argumentów `..` operatora, aby uzyskać zakres otwarty:

- `a..`jest równoznaczne z`a..^0`
- `..b`jest równoznaczne z`0..b`
- `..`jest równoznaczne z`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Przeciążenie operatora

`.`Operatory `()` `^`, `..` , i nie mogą być przeciążone. Operator `[]` jest również uważany za operatora niedościsty. Użyj [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Dostęp do członków](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementów](~/_csharplang/spec/expressions.md#element-access)
- [Operator warunkowy zerowy](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [notatkę dotyczącą propozycji funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [?? (operator zrzekania się wartości null)](null-coalescing-operator.md)
- [:: operator](namespace-alias-qualifier.md)
