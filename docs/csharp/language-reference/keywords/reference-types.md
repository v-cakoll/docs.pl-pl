---
title: Typy odwołań — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744518"
---
# <a name="reference-types-c-reference"></a>Typy odwołań (odwołanie do języka C#)

Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. W przypadku typów wartości każda zmienna ma własną kopię danych i nie jest możliwe, aby operacje na jednej zmiennej wpływały na drugą (z wyjątkiem zmiennych parametrów in, ref i out; patrz [w](in-parameter-modifier.md), [ref](ref.md) i [out](out-parameter-modifier.md) parameter modifier).

 Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:

- [Klasa](class.md)

- [Interfejs](interface.md)

- [delegate](../builtin-types/reference-types.md)

 W języku C# są także dostępne następujące wbudowane typy referencyjne:

- [Dynamiczne](../builtin-types/reference-types.md)

- [obiekt](../builtin-types/reference-types.md)

- [ciąg](../builtin-types/reference-types.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy wartości](../builtin-types/value-types.md)
