---
title: operator [] — C# odwołania
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689596"
---
# <a name="-operator-c-reference"></a>[] — operator (C# odwołania)

Nawiasy kwadratowe `[]`, są zwykle używane do dostępu do elementu tablicy, indeksator lub wskaźnika.

Aby uzyskać więcej informacji o dostępie do elementu wskaźnika, zobacz [porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Nawiasy kwadratowe również służy do określania [atrybuty](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>Dostęp do tablicy

Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

Jeśli indeks tablicy jest poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> zgłaszany.

Jak pokazano na poprzednim przykładzie, możesz także użyć nawiasy kwadratowe w deklaracji typu tablicowego i konkretyzacji wystąpień tablicy.

Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).

## <a name="indexer-access"></a>Dostęp indeksatora

W poniższym przykładzie użyto .NET <xref:System.Collections.Generic.Dictionary%602> typu, aby zademonstrować dostęp indeksatora:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

Indeksatory pozwalają na indeks wystąpienia typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy. W przeciwieństwie do tablicy wskaźników, które musi być liczbą całkowitą, argumenty indeksator może być zadeklarowana jako dowolnego typu.

Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Dostęp do elementu `[]` nie jest uważany za z możliwością przeciążenia operatora. Użyj [indeksatory](../../programming-guide/indexers/index.md) do obsługi indeksowanie z typami zdefiniowanymi przez użytkownika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [dostępu do elementu](~/_csharplang/spec/expressions.md#element-access) i [wskaźnika elementu dostępu](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Tablice](../../programming-guide/arrays/index.md)
- [Indeksatory](../../programming-guide/indexers/index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Atrybuty](../../programming-guide/concepts/attributes/index.md)
- [?. i? Operatory]](null-conditional-operators.md)