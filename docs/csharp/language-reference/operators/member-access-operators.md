---
title: Operatory dostępu do elementów członkowskich — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można użyć do uzyskiwania dostępu do elementów członkowskich typu.
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
ms.openlocfilehash: 4d4bc0c192912b5fa87a8e91bc5ba0e1d4ce3598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399512"
---
# <a name="member-access-operators-c-reference"></a>Operatory dostępu do elementów członkowskich (odwołanie do języka C#)

Podczas uzyskiwania dostępu do elementu członkowskiego typu można używać następujących operatorów:

- (dostęp do członków): aby uzyskać dostęp do elementu członkowskiego obszaru nazw lub typu [ `.` ](#member-access-operator-)
- [(array element lub dostęp do indeksatora) : aby uzyskać dostęp do elementu tablicy lub indeksatora typów `[]` ](#indexer-operator-)
- [oraz `?[]` (operatory warunkowe null): do wykonywania operacji dostępu do elementu członkowskiego lub elementu tylko wtedy, gdy argument jest niezerowy `?.` ](#null-conditional-operators--and-)
- (wywołanie) : wywołanie metody, do której uzyskaliśmy dostęp, lub wywołanie pełnomocnika [ `()` ](#invocation-operator-)
- (indeks od końca): aby wskazać, że pozycja elementu jest od końca sekwencji [ `^` ](#index-from-end-operator-)
- (zakres): aby określić zakres indeksów, których można użyć do uzyskania szeregu elementów sekwencji [ `..` ](#range-operator-)

## <a name="member-access-operator-"></a>Operator dostępu do elementów członkowskich .

Token służy `.` do uzyskiwania dostępu do elementu członkowskiego obszaru nazw lub typu, jak pokazują poniższe przykłady:

- Służy `.` do uzyskiwania dostępu do zagnieżdżonego obszaru nazw w obszarze nazw, jak pokazano w poniższym [ `using` przykładzie dyrektywy:](../keywords/using-directive.md)

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Użyj `.` do utworzenia *kwalifikowanej nazwy,* aby uzyskać dostęp do typu w obszarze nazw, jak pokazano w poniższym kodzie:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Użyj [ `using` dyrektywy,](../keywords/using-directive.md) aby używać kwalifikowanych nazw opcjonalne.

- Użyj `.` dostępu do [elementów członkowskich typu](../../programming-guide/classes-and-structs/index.md#members), statyczne i niestatyczne, jak pokazano w poniższym kodzie:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Można również `.` użyć dostępu do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Operator indeksatora []

Nawiasy kwadratowe , `[]`są zwykle używane do dostępu do tablicy, indeksatora lub elementu wskaźnika.

### <a name="array-access"></a>Dostęp do macierzy

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Jeśli indeks tablicy znajduje się poza granicami odpowiedniego <xref:System.IndexOutOfRangeException> wymiaru tablicy, zgłaszany jest an.

Jak pokazano w poprzednim przykładzie, należy również użyć nawiasów kwadratowych podczas deklarowania typu tablicy lub wystąpienia wystąpienia tablicy.

Aby uzyskać więcej informacji o tablicach, zobacz [Tablice](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dostęp do indeksatora

W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602> użyto typu .NET do zademonstrowania dostępu do indeksatora:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablic. W przeciwieństwie do indeksów tablicowych, które muszą być liczbą całkowitą, parametry indeksatora można zadeklarować jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [Indeksatory](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Inne zastosowania []

Aby uzyskać informacje na temat dostępu do elementu wskaźnika, zobacz [Pointer element dostępu operator []](pointer-related-operators.md#pointer-element-access-operator-) wskaźnik powiązanych [operatorów](pointer-related-operators.md) artykułu.

Nawiasy kwadratowe można również użyć do określenia [atrybutów:](../../programming-guide/concepts/attributes/index.md)

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Operatory warunkowe null?. I? []

Dostępne w języku C# 6 i nowszych, `?.`operator null warunkowy stosuje dostęp do elementu [członkowskiego](#member-access-operator-), lub dostęp do [elementu](#indexer-operator-), `?[]`, operacja do jego operand tylko wtedy, gdy argumentuje non-null; w przeciwnym `null`razie zwraca . Czyli

- Jeśli `a` zostanie `null`oceniona , `a?.x` `a?[x]` wynik `null`lub jest .
- Jeśli `a` oblicza non-null, wynik `a?.x` lub `a?[x]` jest taka sama `a.x` jak `a[x]`wynik lub , odpowiednio.

  > [!NOTE]
  > Jeśli `a.x` `a[x]` lub zgłasza wyjątek `a?.x` `a?[x]` lub zgłasza ten sam wyjątek `a`dla innych niż null . Na przykład `a` jeśli jest wystąpienie tablicy `x` non-null i `a` `a?[x]` znajduje się <xref:System.IndexOutOfRangeException>poza granicami , będzie rzucać .

Operatory warunkowe null są zwarcia. Oznacza to, że jeśli jedna operacja w łańcuchu `null`warunkowego elementu członkowskiego lub operacji dostępu do elementu zwraca , reszta łańcucha nie jest wykonywana. W poniższym `B` przykładzie nie jest `A` oceniana, `C` jeśli ocenia `A` się `B` `null` i `null`nie jest oceniana, jeśli lub ocenia:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

W poniższym przykładzie przedstawiono `?.` użycie `?[]` operatorów i operatorów:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

W poprzednim przykładzie użyto również [operatora `??` łączenia wartości null,](null-coalescing-operator.md) aby określić wyrażenie alternatywne do oceny w `null`przypadku, gdy wynikiem operacji null-conditional jest .

Operator `?.` dostępu członkowskiego warunkowego null jest również znany jako operator Elvis.

### <a name="thread-safe-delegate-invocation"></a>Wywołanie delegata bezpieczne dla wątków

Użyj `?.` operatora, aby sprawdzić, czy pełnomocnik nie jest null i wywołać go w sposób bezpieczny dla wątków (na przykład podczas [wywoływania zdarzenia),](../../../standard/events/how-to-raise-and-consume-events.md)jak pokazano w poniższym kodzie:

```csharp
PropertyChanged?.Invoke(…)
```

Ten kod jest odpowiednikiem następującego kodu, który będzie używany w języku C# 5 lub starszym:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Operator wywołania ()

Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [pełnomocnika](../../programming-guide/delegates/index.md).

W poniższym przykładzie pokazano, jak wywołać metodę, z lub bez argumentów i wywołać delegata:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Nawiasy są również używane podczas wywoływania [konstruktora](../../programming-guide/classes-and-structs/constructors.md) z operatorem. [`new`](new-operator.md)

### <a name="other-usages-of-"></a>Inne zastosowania ()

Nawiasy można również użyć, aby dostosować kolejność, w jakiej do oceny operacji w wyrażeniu. Aby uzyskać więcej informacji, zobacz [Operatory języka C#.](index.md)

[Rzutowania wyrażeń](type-testing-and-cast.md#cast-operator-), które wykonują konwersje typu jawnego, również użyć nawiasów.

## <a name="index-from-end-operator-"></a>Indeks od operatora końcowego ^

Dostępne w języku C# 8.0 i nowszych, `^` operator wskazuje pozycję elementu od końca sekwencji. Dla sekwencji `length`długości `^n` wskazuje element z `length - n` przesunięciem od początku sekwencji. Na przykład `^1` wskazuje ostatni element sekwencji `^length` i wskazuje pierwszy element sekwencji.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Jak pokazano w poprzednim `^e` przykładzie <xref:System.Index?displayProperty=nameWithType> wyrażenie jest typu. W `^e`wyrażeniu `e` wynik musi być `int`niejawnie konwertowalny na .

Operator można również `^` użyć operatora z [operatorem zakresu,](#range-operator-) aby utworzyć zakres indeksów. Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Operator zakresu ..

Dostępne w języku `..` C# 8.0 i nowszych operator określa początek i koniec zakresu indeksów jako jego operands. Lewy operand jest *integracyjnym* początkiem szeregu. Poprawny operand to *ekskluzywny* koniec serii. Operandy może być indeks od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Jak pokazano w poprzednim `a..b` przykładzie <xref:System.Range?displayProperty=nameWithType> wyrażenie jest typu. W `a..b`wyrażeniu `a` `b` wyniki i muszą być `int` <xref:System.Index>niejawnie konwertowalne do lub .

Można pominąć dowolne argumenty operatora, `..` aby uzyskać zakres otwarty:

- `a..`odpowiada`a..^0`
- `..b`odpowiada`0..b`
- `..`odpowiada`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Przeciążenie operatora

`.`Operatory `()` `^`, `..` i operatory nie mogą być przeciążone. Operator `[]` jest również uważany za operatora nie przeładowalnego. [Indeksatory](../../programming-guide/indexers/index.md) służy do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Dostęp do członków](~/_csharplang/spec/expressions.md#member-access)
- [Dostęp do elementu](~/_csharplang/spec/expressions.md#element-access)
- [Operator warunkowy zerowy](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions)

Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [notę propozycji funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [?? (operator łączenia zerowego)](null-coalescing-operator.md)
- [:: operator](namespace-alias-qualifier.md)
