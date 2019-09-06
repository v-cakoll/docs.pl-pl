---
title: Typy niezarządzane — C# odwołanie
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374117"
---
# <a name="unmanaged-types-c-reference"></a>Typy niezarządzane (C# odwołanie)

Typ jest **typem niezarządzanym** , jeśli jest dowolnego z następujących typów:

- `sbyte`, `byte` `short` ,`uint` ,,`float`,, ,`long` ,,`decimal`, ,`double`lub `ushort` `ulong` `int` `char``bool`
- Dowolny typ [wyliczeniowy](../keywords/enum.md)
- Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Dowolny zdefiniowany przez użytkownika typ [struktury](../keywords/struct.md) , który zawiera pola tylko typy niezarządzane i, w C# 7,3 i wcześniejszych, nie jest typem skonstruowanym (typ, który zawiera co najmniej jeden argument typu)

Począwszy od C# 7,3, można użyć [ `unmanaged` ograniczenia](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , aby określić, że parametr typu jest typem niezarządzanym wskaźnika.

Począwszy od C# 8,0, *skonstruowany* typ struktury, który zawiera pola typów niezarządzanych, również jest niezarządzany, jak pokazano w poniższym przykładzie:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Struktura generyczna może być źródłem zarówno typów niezarządzanych, jak i niezarządzanych. W poprzednim przykładzie zdefiniowano strukturę `Coords<T>` generyczną i przedstawiono przykłady niezarządzanych typów skonstruowanych. Przykładem niezarządzanego typu jest `Coords<object>`. Nie jest ona zarządzana, ponieważ zawiera pola `object` typu, które nie są zarządzane. Jeśli chcesz, aby *wszystkie* skonstruowane typy były typami niezarządzanymi, `unmanaged` Użyj ograniczenia w definicji generycznej struktury:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [sizeof — Operator](../operators/sizeof.md)
- [operator stackalloc](../operators/stackalloc.md)
