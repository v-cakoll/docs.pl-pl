---
title: . Operator - C# odwołania
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836464"
---
# <a name="-operator-c-reference"></a>. operator (odwołanie w C#)

Kropki (.), `.`, jest zwykle używany podczas dostępu do elementu członkowskiego.

Możesz użyć `.` token w celu uzyskania dostępu do członka przestrzeni nazw lub typ, jak w poniższych przykładach pokazano:

- Użyj `.` dostępu zagnieżdżone przestrzenie nazw w przestrzeni nazw, w poniższym przykładzie z do [ `using` dyrektywy](../keywords/using-directive.md) pokazuje:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- Użyj `.` do formularza *kwalifikowana nazwa* uzyskiwać dostęp do typu, w przestrzeni nazw, co ilustruje poniższy kod:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  Użyj [ `using` dyrektywy](../keywords/using-directive.md) powoduje użycie kwalifikowane nazwy są opcjonalne.

- Użyj `.` dostęp do [elementy członkowskie typu](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, co ilustruje poniższy kod:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

Można również użyć `.` do wywołania [— metoda rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Operator `.` nie mogą być przeciążone.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [dostęp do elementu członkowskiego](~/_csharplang/spec/expressions.md#member-access) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [?. i? Operatory]](null-conditional-operators.md)