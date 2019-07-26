---
title: Typy niezarządzane — C# odwołanie
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 5b08b55f5c52fe2ad20cb25bca0449eb26e333ca
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440237"
---
# <a name="unmanaged-types-c-reference"></a>Typy niezarządzane (C# odwołanie)

**Typem** niezarządzanym jest dowolny typ, który nie jest typem referencyjnym lub typem konstruowanym (typ, który zawiera co najmniej jeden argument typu) i nie zawiera pól typu referencyjnego lub typu złożonego na dowolnym poziomie zagnieżdżania. Innymi słowy, niezarządzany typ jest jednym z następujących:

- `sbyte`, `byte` `short` ,`uint` ,,`float`,, ,`long` ,,`decimal`, ,`double`lub `ushort` `ulong` `int` `char``bool`
- Dowolny typ [wyliczeniowy](../keywords/enum.md)
- Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Dowolny zdefiniowany przez użytkownika typ [struktury](../keywords/struct.md) , który nie jest typem skonstruowanym i zawiera pola tylko typów niezarządzanych

Począwszy od C# 7,3, można użyć [ `unmanaged` ograniczenia](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , aby określić, że parametr typu jest typem niezarządzanym wskaźnika.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [sizeof — Operator](../keywords/sizeof.md)
- [operator stackalloc](../operators/stackalloc.md)
