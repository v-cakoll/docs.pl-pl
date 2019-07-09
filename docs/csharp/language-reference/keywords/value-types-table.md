---
title: Tabela typów wartości - C# odwołania
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 81f85ce60f423cad8aecccad8f97e90897ba86db
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661602"
---
# <a name="value-types-table-c-reference"></a>Tabela typów wartości (odwołanie w C#)

W poniższej tabeli przedstawiono C# typów wartości:

|Typ wartości|Kategoria|Sufiksem typu|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|`byte`|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)
)||
|`decimal`|Numeryczne, [zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)|M lub m|
|`double`|Numeryczne, [zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)|D lub d|
|[enum](enum.md)|Wyliczenie||
|`float`|Numeryczne, [zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)|F lub f|
|`int`|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|`long`|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|L lub l|
|`sbyte`|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|`short`|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Struktura zdefiniowanych przez użytkownika||
|`uint`|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|U lub u|
|`ulong`|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU lub lu|
|`ushort`|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Uwagi

Sufiksem typu umożliwia określenie typu literał wartości liczbowych. Na przykład:

```csharp
decimal a = 0.1M;
```

Jeśli [literał numeryczny liczby całkowitej](~/_csharplang/spec/lexical-structure.md#integer-literals) nie sufiks ma pierwszy następujące typy, w których jej wartość może być reprezentowana: `int`, `uint`, `long`, `ulong`.

Jeśli [literał liczby rzeczywistej wartości liczbowych](~/_csharplang/spec/lexical-structure.md#real-literals) nie sufiks jest typu `double`.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Typy wartości](value-types.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
