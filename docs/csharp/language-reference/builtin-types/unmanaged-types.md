---
title: Typy niezarządzane — odwołanie do języka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 9dd2ab4e044b8a86bfe72a6fcf2481b8e1e80bf4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507233"
---
# <a name="unmanaged-types-c-reference"></a>Typy niezarządzane (odwołanie do języka C#)

Typ jest **typem niezarządzanym,** jeśli jest to jeden z następujących typów:

- `sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , , , , , , lub`bool`
- Dowolny typ [wyliczenia](enum.md)
- Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Każdy zdefiniowany przez użytkownika typ [struktury,](struct.md) który zawiera tylko pola typów niezarządzanych i w języku C# 7.3 i wcześniejszych nie jest typem skonstruowanym (typ, który zawiera co najmniej jeden argument typu)

Począwszy od języka C# 7.3, można użyć [ `unmanaged` ograniczenia,](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) aby określić, że parametr typu jest nie-wskaźnik, non-null typu niezarządzanego.

Począwszy od języka C# 8.0, *skonstruowany* typ struktury, który zawiera tylko pola typów niezarządzanych, jest również niezarządzany, jak pokazano w poniższym przykładzie:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Struktura rodzajowa może być źródłem typów bez mana i niezarządzanych. W poprzednim przykładzie definiuje strukturę `Coords<T>` rodzajową i przedstawia przykłady niezarządzanych typów skonstruowanych. Przykładem typu niezarządzanego `Coords<object>`jest . Nie jest niezarządzane, ponieważ ma `object` pola typu, który nie jest niezarządzane. Jeśli *chcesz,* aby wszystkie typy skonstruowane były `unmanaged` typami niezarządzanym, użyj ograniczenia w definicji struktury ogólnej:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [sizeof, operator](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
