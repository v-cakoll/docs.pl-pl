---
title: Typy niezarządzane — odwołanie do języka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846470"
---
# <a name="unmanaged-types-c-reference"></a>Typy niezarządzane (odwołanie do języka C#)

Typ jest **typem niezarządzanym,** jeśli jest to którykolwiek z następujących typów:

- `sbyte``byte`, `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , lub`bool`
- Dowolny typ [wyliczenia](enum.md)
- Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Każdy typ [struktury](struct.md) zdefiniowany przez użytkownika, który zawiera pola tylko typów niezarządzanych i w języku C# 7.3 i starszym nie jest typem konstruowanym (typem zawierającym co najmniej jeden argument typu)

Począwszy od Języka C# 7.3, można użyć [ `unmanaged` ograniczenia,](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) aby określić, że parametr typu jest niewskaźnik, nienullable niezarządzane typu.

Począwszy od Języka C# 8.0, *skonstruowany* typ struktury, który zawiera pola tylko typy niezarządzane jest również niezarządzane, jak pokazano w poniższym przykładzie:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Struktura ogólna może być źródłem typów skonstruowanych niezarządzanych i niezarządzanych. W poprzednim przykładzie definiuje strukturę `Coords<T>` rodzajową i przedstawia przykłady typów skonstruowanych niezarządzanych. Przykładem nie typu niezarządzanego `Coords<object>`jest . Nie jest niezarządzany, ponieważ ma pola `object` typu, który nie jest niezarządzany. Jeśli chcesz, aby *wszystkie* typy skonstruowane `unmanaged` były typami niezarządzanymi, należy użyć ograniczenia w definicji struktury ogólnej:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [pointer typy](~/_csharplang/spec/unsafe-code.md#pointer-types) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [sizeof, operator](../operators/sizeof.md)
- [stackalloc, operator](../operators/stackalloc.md)
