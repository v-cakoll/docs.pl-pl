---
title: Typy odwołań — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744518"
---
# <a name="reference-types-c-reference"></a>Typy odwołań (C# odwołanie)

Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem w przypadku zmiennych parametrów ref i out; zobacz [w](in-parameter-modifier.md), modyfikator parametru [ref](ref.md) i [out](out-parameter-modifier.md) ).

 Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:

- [class](class.md)

- [interface](interface.md)

- [delegate](../builtin-types/reference-types.md)

 W języku C# są także dostępne następujące wbudowane typy referencyjne:

- [dynamic](../builtin-types/reference-types.md)

- [object](../builtin-types/reference-types.md)

- [string](../builtin-types/reference-types.md)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy wartości](../builtin-types/value-types.md)
